---
document_id: DOC-07
title: Engenharia e Arquitetura
status: canonical-example
version: 1.1.0
depends_on:
  - DOC-02
  - DOC-03
  - DOC-05
  - DOC-06
governs:
  - engineering
  - architecture
  - repository-structure
  - boundaries
  - technology-selection-inputs
  - infrastructure-needs
---

# 07 — Engenharia e Arquitetura

## 1. Forças de engenharia

### ENG-001 — Multi-tenant corporativo

Dados de uma empresa nunca podem ser expostos a outra por erro de consulta, navegação ou autorização.

### ENG-002 — Operação por equipe pequena

O Beta será mantido por uma equipe pequena. Baixa complexidade operacional possui prioridade alta.

### ENG-003 — Conteúdo reutilizável

Cursos e materiais precisam existir independentemente da turma e do cliente para serem reutilizados com controle de versão e atribuição contextual.

### ENG-004 — Progresso auditável

Conclusões, avaliações e certificados precisam possuir histórico suficiente para explicar o estado exibido.

### ENG-005 — Evolução para integrações

O sistema deve permitir futura integração com OMEM sem acoplar o domínio de aprendizagem a detalhes internos do CRM no Beta.

### ENG-006 — Deploy independente de web e API

Frontend e backend devem poder evoluir e ser implantados separadamente quando necessário.

### ENG-007 — Experiência responsiva

Administração prioriza desktop/tablet; aluno deve conseguir consumir a trilha em mobile web.

### ENG-008 — Segurança por contexto autenticado

Tenant e permissões devem derivar de identidade autenticada e vínculos persistidos, não de campos confiados ao cliente.

### ENG-009 — Crescimento inicial moderado

Beta esperado abaixo de 500 usuários, mas a modelagem não deve depender de um único cliente ou turma.

## 2. Alternativas arquiteturais consideradas

### Microservices

**Rejeitado no Beta.** A escala e o tamanho da equipe não justificam custo operacional, contratos distribuídos e observabilidade adicional.

### Aplicação monolítica única sem fronteiras

**Rejeitada.** Seria simples inicialmente, mas aumentaria risco de misturar conteúdo, tenant, aprendizagem e infraestrutura.

### Modular Monolith com web e API separadas

**Escolhida.** Mantém operação simples, permite boundaries de domínio claras e preserva deploy independente do frontend e backend.

Essa decisão é arquitetural. A linguagem, os runtimes e os frameworks concretos serão escolhidos depois pela Visão do Tech Lead.

## 3. Estratégia de repositório

**Monorepo.**

Motivos:

- web e API compartilham contratos;
- regras de domínio e contratos precisam permanecer consistentes;
- um único CI pode validar boundaries e contratos;
- equipe pequena se beneficia de mudanças atômicas;
- deploy continua podendo ser independente por aplicação.

Estrutura lógica inicial:

```text
/apps
  /web
  /api
/packages
  /domain
  /contracts
  /design-tokens
  /config
/infra
/tooling
/docs
```

Pastas específicas de provider não são decisão deste documento. Se a infraestrutura aprovada exigir organização adicional, ela deve respeitar essas boundaries e ser reconciliada sem transformar provider em dependência do domínio.

A estrutura física final pode ser refinada na Fundação sem alterar silenciosamente o modelo arquitetural.

## 4. Módulos de domínio

### Identity & Access

Autenticação, memberships, roles e permissões.

### Tenancy

Empresas/clientes e vínculo de usuários.

### Catalog

Cursos, módulos, aulas e materiais.

### Learning Paths

Trilhas, critérios de atribuição e versão aplicável.

### Cohorts

Turmas, instrutores, participantes e datas.

### Enrollment & Progress

Matrículas, progresso, retomada e conclusão.

### Assessments

Quizzes, tentativas, regras de aprovação e tarefas práticas.

### Certification

Elegibilidade, emissão e registro de certificados.

### Notifications

Convites e mensagens transacionais essenciais.

## 5. Fronteiras de dependência

```text
UI / Controllers
      ↓
Application services
      ↓
Domain
      ↓
Ports
      ↓
Infrastructure adapters
```

`packages/domain` não deve importar framework web, SDK de banco, SDK de autenticação ou provider de e-mail.

`apps/web` não acessa credenciais administrativas nem superfícies privadas por mecanismo privilegiado.

A API resolve autorização usando identidade autenticada e memberships persistidos.

## 6. API

Estilo inicial: REST JSON com contratos explícitos e versionados por código quando necessário.

Regras:

- endpoints de tenant validam contexto autenticado;
- paginação em coleções potencialmente grandes;
- validação de entrada na borda;
- erros previsíveis possuem códigos estáveis;
- idempotência para operações em que retry possa duplicar efeito, como convite ou emissão de certificado.

O framework HTTP concreto pertence à Visão do Tech Lead.

## 7. Dados

A arquitetura exige **persistência relacional** para o núcleo transacional do produto.

Motivos:

- relações fortes entre organização, membership, turma, matrícula e progresso;
- constraints de integridade;
- transações para operações críticas;
- consultas auditáveis e paginação previsível;
- índices coerentes com isolamento por tenant.

Entidades principais esperadas:

```text
users
organizations
organization_memberships
courses
course_modules
lessons
learning_paths
learning_path_items
organization_modules
cohorts
cohort_members
course_enrollments
lesson_progress
assessments
assessment_attempts
practical_assignments
assignment_submissions
certificates
```

A tecnologia relacional concreta, driver/query layer e mecanismo de migrations são decisões da Visão do Tech Lead. O provider é decisão de Infraestrutura.

A nomenclatura final deve seguir o Documento 06 e o modelo de dados executável.

## 8. Consistência e auditoria

- progresso de aula deve ser idempotente;
- certificado só é emitido após critérios canônicos satisfeitos;
- mudanças críticas de permissões e validações manuais precisam de trilha de auditoria mínima;
- alterações de schema são feitas por migrations versionadas.

## 9. Segurança

Trust boundary simplificada:

```text
Browser
   ↓ user session
Web/API pública
   ↓ authorized service identity
Database / private services
```

Regras:

- secrets apenas no servidor;
- autorização não depende apenas da UI;
- acesso a tenant é verificado no backend e, quando aplicável, reforçado na camada de dados;
- least privilege em serviços;
- arquivos privados usam URLs assinadas ou mecanismo equivalente quando necessário;
- logs evitam dados pessoais desnecessários.

## 10. Frontend

- composição por feature/domínio, não por pasta genérica de componentes;
- server/client boundaries explícitas se a tecnologia escolhida possuir essa distinção;
- estado global apenas quando houver necessidade real;
- cache e invalidação seguem semântica de dados;
- componentes visuais seguem Documento 04 e Princípios.

O framework de frontend, router, mecanismo de server state e bibliotecas concretas pertencem à Visão do Tech Lead.

## 11. Decisões verificáveis

```text
Decisão: packages/domain não depende de frameworks
→ boundary check

Decisão: tenant vem do contexto autorizado
→ testes negativos de acesso cross-tenant

Decisão: cliente não possui segredo administrativo
→ secret scan + check de env pública

Decisão: bugs de autorização não regressam
→ testes de integração cross-tenant
```

## 12. ADRs iniciais

### ADR-001 — Monorepo

**Aceita.** Compartilhamento de contratos e equipe pequena justificam um único repositório.

### ADR-002 — Modular Monolith

**Aceita.** Menor custo operacional com boundaries preservadas.

### ADR-003 — API separada do frontend

**Aceita.** Permite deploy independente e prepara integrações futuras sem adotar polyrepo.

### ADR-004 — Sem integração OMEM no Beta

**Aceita.** O domínio de aprendizagem deve estabilizar antes de automatizar validação externa.

## 13. Saída para a Visão do Tech Lead

A arquitetura produz restrições para seleção tecnológica, sem escolher a stack por preferência.

```text
TL-NEED-001 — Web e API devem compartilhar contratos tipados sem acoplar o domínio a framework.
TL-NEED-002 — packages/domain precisa permanecer executável/testável sem UI, HTTP, banco ou SDK de provider.
TL-NEED-003 — web e API precisam de build e deploy independentes dentro do mesmo monorepo.
TL-NEED-004 — boundaries externas precisam de validação de runtime além de tipos estáticos.
TL-NEED-005 — a persistência principal deve ser relacional, com transações, constraints e índices.
TL-NEED-006 — a stack deve sustentar testes unitários, integração, E2E e boundary checks automatizados.
TL-NEED-007 — equipe pequena favorece toolchain coesa e baixa quantidade de frameworks sobrepostos.
TL-NEED-008 — frontend responsivo não possui requisito de SSR no Beta; não adicionar SSR apenas por hábito.
TL-NEED-009 — API deve operar de forma stateless na superfície HTTP.
TL-NEED-010 — integrações futuras com OMEM devem entrar por adapters/ports, sem contaminar domínio.
```

Essas necessidades devem ser consumidas por `Visao_do_Tech_Lead.md` antes da escolha de linguagens, runtimes, frameworks e bibliotecas.

## 14. Inventário de necessidades de infraestrutura

```text
INF-NEED-001 — repositório Git com CI
INF-NEED-002 — hosting web com HTTPS/CDN
INF-NEED-003 — runtime gerenciado compatível com a stack aprovada para API
INF-NEED-004 — banco relacional gerenciado
INF-NEED-005 — autenticação
INF-NEED-006 — storage privado para materiais quando necessário
INF-NEED-007 — envio de e-mail transacional
INF-NEED-008 — secrets por ambiente
INF-NEED-009 — logs e rastreamento de erros
INF-NEED-010 — staging compartilhável
INF-NEED-011 — backup/restore compatível com o estágio
```

Arquitetura define **o que tecnicamente precisamos e quais fronteiras devem existir**. O Tech Lead define **com quais tecnologias essas decisões serão implementadas**. Infraestrutura define **onde a stack aprovada será executada**.

## Critério de qualidade

Outra equipe deve conseguir ler este documento e compreender:

- forças de engenharia;
- modelo arquitetural;
- estratégia de repositório;
- módulos;
- boundaries;
- requisitos de dados;
- trust boundaries;
- critérios que a stack precisa satisfazer;
- necessidades de infraestrutura.

Ela não deve precisar inventar a arquitetura, mas também não deve encontrar framework, library ou provider escolhido prematuramente por preferência.
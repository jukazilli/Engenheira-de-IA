---
document_id: DOC-07
title: Engenharia e Arquitetura
status: canonical-example
version: 1.0.0
depends_on:
  - DOC-02
  - DOC-03
  - DOC-05
  - DOC-06
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

## 3. Estratégia de repositório

**Monorepo.**

Motivos:

- web e API compartilham contratos;
- regras de domínio e tipos precisam permanecer consistentes;
- um único CI pode validar boundaries e contratos;
- equipe pequena se beneficia de mudanças atômicas;
- deploy continua podendo ser independente por aplicação.

Estrutura inicial:

```text
/apps
  /web
  /api
/packages
  /domain
  /contracts
  /design-tokens
  /config
/supabase
/infra
/tooling
/docs
```

A estrutura final pode ser ajustada na Fundação sem violar as boundaries descritas.

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

`packages/domain` não deve importar framework web, SDK de banco ou provider de e-mail.

`apps/web` não acessa credenciais administrativas nem tabelas privadas por mecanismo privilegiado.

A API resolve autorização usando identidade autenticada e memberships persistidos.

## 6. API

Estilo inicial: REST JSON com contratos versionados por código quando necessário.

Regras:

- endpoints de tenant validam contexto autenticado;
- paginação em coleções potencialmente grandes;
- validação de entrada na borda;
- erros previsíveis possuem códigos estáveis;
- idempotência para operações em que retry possa duplicar efeito, como convite ou emissão de certificado.

## 7. Dados

Banco relacional PostgreSQL.

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

A nomenclatura final deve seguir o Documento 06 e o modelo de dados executável.

## 8. Consistência e auditoria

- progresso de aula deve ser idempotente;
- certificado só é emitido após critérios canônicos satisfeitos;
- mudanças críticas de permissões e validações manuais precisam de trilha de auditoria mínima;
- alterações de schema são feitas por migrations.

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
- acesso a tenant é verificado no backend/banco;
- least privilege em serviços;
- arquivos privados usam URLs assinadas ou mecanismo equivalente quando necessário;
- logs evitam dados pessoais desnecessários.

## 10. Frontend

- composição por feature/domínio, não por pasta genérica de componentes;
- server/client boundaries explícitas quando o framework exigir;
- estado global apenas quando houver necessidade real;
- cache e invalidação seguem semântica de dados;
- componentes visuais seguem Documento 04 e Princípios.

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

## 13. Inventário de necessidades de infraestrutura

```text
INF-NEED-001 — repositório Git com CI
INF-NEED-002 — hosting web com HTTPS/CDN
INF-NEED-003 — runtime gerenciado para API
INF-NEED-004 — PostgreSQL gerenciado
INF-NEED-005 — autenticação
INF-NEED-006 — storage privado para materiais quando necessário
INF-NEED-007 — envio de e-mail transacional
INF-NEED-008 — secrets por ambiente
INF-NEED-009 — logs e rastreamento de erros
INF-NEED-010 — staging compartilhável
INF-NEED-011 — backup/restore compatível com o estágio
```

## Critério de qualidade

Outra equipe deve conseguir ler este documento e montar o esqueleto do repositório sem inventar o modelo arquitetural, os módulos ou as trust boundaries.
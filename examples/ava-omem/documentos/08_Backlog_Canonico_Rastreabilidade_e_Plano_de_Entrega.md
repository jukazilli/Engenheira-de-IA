---
document_id: DOC-08
title: Backlog Canônico, Rastreabilidade e Plano de Entrega
status: canonical-example
version: 1.0.0
depends_on:
  - DOC-06
  - DOC-07
  - Infraestrutura_e_Plano_de_Fundacao
---

# 08 — Backlog Canônico, Rastreabilidade e Plano de Entrega

## Regras

- cada item possui ID estável;
- nenhum item pode ser considerado `Done` sem testes/evidência aplicáveis;
- FND prepara a base antes das funcionalidades;
- dependências precisam ser respeitadas;
- itens devem ser pequenos o suficiente para revisão e prova.

## Estados

```text
Planned
In Progress
Blocked
Implemented
Validated
Done
```

---

# Fundação

## FND-001 — Inicializar monorepo

**Origem:** DOC-06, DOC-07  
**Objetivo:** criar estrutura física alinhada à arquitetura.

### Critérios de aceite

- `apps/web` criado;
- `apps/api` criado;
- packages compartilhados criados sem dependências indevidas;
- workspace funciona com instalação única;
- estrutura documentada no README técnico do projeto.

### Testes/evidência

- instalação limpa;
- build mínimo dos apps;
- boundary check inicial.

**Dependências:** nenhuma.

---

## FND-002 — Fixar toolchain

**Origem:** DOC-06  
**Objetivo:** garantir reprodutibilidade.

### Critérios

- Node LTS definido;
- pnpm fixado;
- lockfile versionado;
- TypeScript strict;
- formatter e lint configurados.

**Dependência:** FND-001.

---

## FND-003 — Criar quality gates locais

### Critérios

Comandos equivalentes a:

```text
format:check
lint
typecheck
test
build
check:boundaries
```

**Dependência:** FND-002.

---

## FND-004 — Configurar CI

### Critérios

- pull/commit candidato executa gates;
- falha bloqueia promoção;
- pipeline não imprime secrets.

**Dependência:** FND-003.

---

## FND-005 — Criar banco/auth de staging

**Origem:** Infraestrutura  
**Critérios:**

- projeto/instância aprovado pelo humano;
- credenciais não transitam pelo chat;
- conexão da API validada;
- ambiente identificado como staging.

**Dependência:** FND-004.

---

## FND-006 — Migrations baseline de identidade e tenant

### Critérios

- migrations versionadas;
- organizações e memberships modeladas;
- constraints mínimas;
- política de autorização inicial;
- teste negativo cross-tenant.

**Dependência:** FND-005.

---

## FND-007 — Publicar web em staging

### Critérios

- HTTPS;
- build imutável/reproduzível;
- health/smoke page acessível;
- variáveis públicas revisadas.

**Dependência:** FND-004.

---

## FND-008 — Publicar API em staging

### Critérios

- health endpoint;
- conexão autorizada com banco;
- secrets apenas no runtime;
- logs básicos;
- CORS/origins conforme ambiente.

**Dependências:** FND-005, FND-006.

---

## FND-009 — Configurar e-mail transacional de teste

### Critérios

- provider aprovado;
- domínio/remetente de teste validado;
- secret armazenado fora do código;
- mensagem de teste enviada sem expor credencial.

**Dependência:** FND-004.

---

## FND-010 — Smoke test da Fundação

### Critérios

- web acessível;
- API saudável;
- banco responde;
- migration state válido;
- auth baseline funciona;
- CI aprovado;
- teste cross-tenant negativo passa.

**Dependências:** FND-006, FND-007, FND-008.

### Evidência

CI + staging + registro de execução.

---

# Identidade e Tenancy

## AUTH-001 — Primeiro acesso por convite

**Origem:** DOC-02, DOC-05  
**Objetivo:** permitir que aluno aceite convite e acesse o contexto correto.

### Critérios

- convite associa e-mail à empresa/turma prevista;
- usuário autenticado não escolhe tenant arbitrário;
- convite expirado possui tratamento claro;
- usuário existente pode aceitar novo vínculo permitido.

### Testes

- sucesso;
- convite inválido;
- convite expirado;
- tentativa de usar convite de outro destinatário quando aplicável.

**Dependência:** FND-010.

---

## TEN-001 — Criar empresa

### Critérios

- somente papel autorizado da consultoria cria;
- nome obrigatório;
- duplicidade provável sinalizada;
- empresa nasce sem expor dados de outras organizações.

**Dependência:** AUTH-001.

---

## TEN-002 — Configurar módulos OMEM contratados

### Critérios

- módulos podem ser associados/removidos por usuário autorizado;
- histórico de mudança crítica é auditável;
- configuração alimenta atribuição de trilhas.

**Dependência:** TEN-001.

---

## TEN-003 — Gestor vê somente sua empresa

### Critérios

- acesso cross-tenant é negado no backend;
- UI não apresenta seletor de outras empresas;
- testes negativos cobrem leitura e mutação.

**Dependência:** AUTH-001.

---

# Conteúdo e Trilhas

## CNT-001 — Criar curso reutilizável

### Critérios

- título, descrição e status;
- curso não pertence a uma turma específica;
- edição respeita permissões;
- exclusão não é ação primária.

**Dependência:** AUTH-001.

---

## CNT-002 — Organizar módulos e aulas

### Critérios

- curso possui módulos ordenados;
- módulo possui aulas ordenadas;
- aula suporta conteúdo previsto pelo Beta;
- ordem é persistida de forma determinística.

**Dependência:** CNT-001.

---

## CNT-003 — Adicionar materiais por link/PDF

### Critérios

- validação de tipo/tamanho quando upload existir;
- arquivos privados não se tornam públicos por padrão;
- link externo é validado como URL.

**Dependência:** CNT-002.

---

## TRL-001 — Criar trilha

### Critérios

- trilha possui itens ordenados;
- pode reutilizar cursos;
- critérios de público são legíveis;
- publicação exige conteúdo válido.

**Dependência:** CNT-001.

---

## TRL-002 — Sugerir trilha compatível com empresa/perfil

### Critérios

- critérios usados são visíveis ao consultor;
- sugestão não é aplicada silenciosamente;
- módulos contratados incompatíveis são sinalizados.

**Dependências:** TRL-001, TEN-002.

---

# Turmas e Matrículas

## CLS-001 — Criar turma

### Critérios

- vinculada a uma empresa;
- instrutor e período opcionais/conforme regra;
- turma não duplica conteúdo-base;
- só usuários autorizados criam.

**Dependência:** TEN-001.

---

## CLS-002 — Matricular usuários e atribuir trilha

### Critérios

- usuário deve pertencer à empresa correta;
- trilha é revisada antes da confirmação;
- operação repetida não duplica matrícula.

**Dependências:** CLS-001, TRL-002.

---

# Experiência de Aprendizagem

## LRN-001 — Exibir Minha trilha

### Critérios

- aluno vê trilha atual;
- próxima atividade fica evidente;
- concluídos e pendentes são distinguíveis sem depender só de cor;
- nenhum dado de outro tenant aparece.

**Dependência:** CLS-002.

---

## LRN-002 — Registrar conclusão de aula

### Critérios

- conclusão é idempotente;
- data/usuário são registrados;
- progresso recalculado de forma consistente;
- próxima atividade é apresentada.

**Dependência:** LRN-001.

---

## ASM-001 — Realizar quiz

### Critérios

- tentativa persiste respostas conforme política;
- envio calcula resultado;
- regra de aprovação é explícita;
- falha de rede não deve apagar respostas quando evitável.

**Dependência:** LRN-001.

---

## ASM-002 — Registrar tarefa prática

### Critérios

- instrução é clara;
- aluno registra submissão permitida;
- status pode exigir validação manual;
- Beta não consulta OMEM automaticamente.

**Dependência:** LRN-001.

---

## ASM-003 — Validar tarefa prática

### Critérios

- somente instrutor/consultoria autorizada valida;
- aprovação/reprovação registra ator e data;
- devolução pode conter orientação;
- aluno é informado do novo estado.

**Dependência:** ASM-002.

---

# Acompanhamento e Certificação

## OBS-001 — Consultor acompanha turma

### Critérios

- identifica não iniciados, em andamento, bloqueados e concluídos;
- tarefas aguardando validação recebem prioridade;
- filtros não cruzam tenants;
- dados agregados correspondem ao estado individual.

**Dependências:** LRN-002, ASM-001.

---

## OBS-002 — Gestor acompanha equipe

### Critérios

- somente sua empresa;
- visualização por turma/trilha;
- sem acesso a autoria de conteúdo;
- permissões de convite respeitam configuração da consultoria.

**Dependências:** TEN-003, LRN-002.

---

## CERT-001 — Emitir certificado elegível

### Critérios

- sistema verifica todos os requisitos da trilha;
- emissão repetida não duplica certificado;
- registro possui identificador estável;
- aluno consegue acessar comprovante.

**Dependências:** LRN-002, ASM-001, ASM-003 quando aplicável.

---

# Plano de entrega inicial

```text
M0 — Fundação
FND-001 → FND-010

M1 — Identidade/Tenant
AUTH-001 → TEN-001 → TEN-002 → TEN-003

M2 — Conteúdo/Trilhas
CNT-001 → CNT-002 → CNT-003
TRL-001 → TRL-002

M3 — Turmas/Aluno
CLS-001 → CLS-002 → LRN-001 → LRN-002

M4 — Avaliação
ASM-001 → ASM-002 → ASM-003

M5 — Acompanhamento/Certificação
OBS-001 → OBS-002 → CERT-001
```

## Primeira ação executável

No estado inicial deste exemplo, o primeiro item elegível é `FND-001`. Nenhuma funcionalidade de produto deve ser marcada como iniciada antes da Fundação mínima ou de exceção explicitamente aprovada.
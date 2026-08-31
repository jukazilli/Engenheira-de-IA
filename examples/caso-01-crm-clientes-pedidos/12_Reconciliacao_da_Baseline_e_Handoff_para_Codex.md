---
document_id: CASE-01-DOC-12
title: Reconciliação da Baseline e Handoff para Codex — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: reconciliacao-handoff-codex
baseline_id: BL-CASE-01-CRM-1
baseline_version: 1.0.0
baseline_input_commit: 338de72d913dd3fb86373ca666832de147457a6d
baseline_readiness: READY_FOR_CODEX
handoff_readiness: SUFFICIENT
baseline_freeze: ACTIVE
codex_trigger: CODEX_CANONICAL_START_V1
continuation_policy: MANUAL_EACH_ITEM
execution_authorization: NOT_GRANTED
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
  - Principios_de_UX_UI.md
  - 04_Direcao_de_UI_e_Design_System.md
  - 05_Especificacao_de_UX.md
  - 06_Tecnicas_de_Desenvolvimento.md
  - 07_Engenharia_e_Arquitetura.md
  - Visao_do_Tech_Lead.md
  - 08_DevOps_e_Infraestrutura.md
  - 09_Plano_de_Fundacao.md
  - 10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
  - 11_Matriz_Operacional_de_Rastreabilidade.md
next_stage: Execução Canônica pelo Codex
---

# Reconciliação da Baseline e Handoff para Codex — CRM para gestão de clientes e pedidos

## 1. Propósito

Este documento encerra a cadeia documental do Caso 01 e verifica se a baseline formada pelas etapas anteriores é suficientemente coerente, completa e segura para ser consumida por um agente de implementação sem que ele precise inventar intenção de produto, regra de negócio, experiência, arquitetura, stack, infraestrutura, gate ou critério de aceite.

A pergunta central é:

> **O próximo item elegível pode ser executado pelo Codex a partir das fontes canônicas existentes, com escopo, restrições, testes, evidências esperadas e condições de parada suficientemente claros?**

A resposta técnica desta reconciliação é:

```text
BASELINE_READINESS: READY_FOR_CODEX
HANDOFF_READINESS: SUFFICIENT
```

Isso não significa autorização humana para iniciar execução.

```text
BASELINE TECNICAMENTE READY
!=
EXECUÇÃO HUMANA AUTORIZADA
```

O estado desta baseline é:

```text
EXECUTION_AUTHORIZATION: NOT_GRANTED
```

---

## 2. Manifesto da baseline

```text
BASELINE_ID: BL-CASE-01-CRM-1
BASELINE_VERSION: 1.0.0
BASELINE_INPUT_COMMIT: 338de72d913dd3fb86373ca666832de147457a6d
BASELINE_FREEZE: ACTIVE
BASELINE_READINESS: READY_FOR_CODEX
HANDOFF_READINESS: SUFFICIENT
CODEX_TRIGGER: CODEX_CANONICAL_START_V1
CONTINUATION_POLICY: MANUAL_EACH_ITEM
EXECUTION_AUTHORIZATION: NOT_GRANTED
```

`BASELINE_INPUT_COMMIT` identifica o commit imediatamente anterior à canonização deste documento, no qual todos os documentos 00–11 já coexistiam.

O commit que adiciona este próprio documento é, por definição, o primeiro commit em que a baseline documental 00–12 completa existe. O identificador desse commit é externo ao conteúdo deste arquivo para evitar uma referência circular impossível de ser autocontida no próprio hash do commit.

---

## 3. Documentos canônicos participantes

A baseline executável é composta por:

```text
00_Discovery.md
01_Pesquisa_e_Viabilidade.md
02_Briefing_de_Produto_e_Escopo.md
03_Visao_de_Product_Owner.md
Principios_de_UX_UI.md
04_Direcao_de_UI_e_Design_System.md
05_Especificacao_de_UX.md
06_Tecnicas_de_Desenvolvimento.md
07_Engenharia_e_Arquitetura.md
Visao_do_Tech_Lead.md
08_DevOps_e_Infraestrutura.md
09_Plano_de_Fundacao.md
10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
11_Matriz_Operacional_de_Rastreabilidade.md
12_Reconciliacao_da_Baseline_e_Handoff_para_Codex.md
```

Os documentos genéricos de `docs/processo/` continuam sendo metodologia.

Na execução do Caso 01, as decisões concretas estão nos documentos deste diretório de exemplo.

---

## 4. Hierarquia de autoridade

Quando houver divergência durante execução, aplicar a autoridade da fonte responsável pelo tema.

Ordem prática:

```text
LEI / SEGURANÇA / OBRIGAÇÃO EXTERNA VINCULANTE
↓
BRIEFING / PRODUCT OWNER
↓
PRINCÍPIOS / UI / UX
↓
ENGENHARIA E ARQUITETURA
↓
VISÃO DO TECH LEAD
↓
DEVOPS E INFRAESTRUTURA
↓
TÉCNICAS DE DESENVOLVIMENTO
↓
PLANO DE FUNDAÇÃO
↓
BACKLOG / MATRIZ
↓
ISSUE / PROMPT / INFERÊNCIA DO AGENTE
```

Uma Issue ou prompt não pode redefinir silenciosamente uma decisão de produto, UX, arquitetura, tecnologia ou infraestrutura.

Quando nova evidência invalida decisão canônica:

```text
EVIDÊNCIA NOVA
↓
CLASSIFICAR IMPACTO
↓
IDENTIFICAR FONTE DE AUTORIDADE
↓
REABRIR FONTE
↓
RECONCILIAR BACKLOG
↓
RECONCILIAR MATRIZ
↓
RECONCILIAR DOC 12
↓
NOVA BASELINE
```

---

## 5. Auditoria transversal final

### 5.1. Produto

**Resultado:** PASS.

A baseline possui:

- problema e contexto;
- usuários;
- produto e promessa;
- core;
- P0, P1, P2 e fora de escopo;
- outcomes;
- hipóteses;
- regras de negócio;
- jornadas;
- épicos;
- histórias;
- experimentos;
- gates de produto;
- business case e guardrails.

Não foi encontrada história P0 cuja intenção precise ser inventada pelo agente.

### 5.2. UX e UI

**Resultado:** PASS.

A baseline possui:

- princípios transversais;
- princípios específicos do CRM;
- direção visual;
- hierarquia;
- design system conceitual;
- jornadas;
- estados;
- recuperação;
- conectividade;
- acessibilidade;
- comportamento desktop/mobile;
- política de indisponibilidade do Protheus;
- critérios de UX e testes esperados.

### 5.3. Engenharia e arquitetura

**Resultado:** PASS.

As decisões estruturais permanecem coerentes:

```text
MONÓLITO MODULAR
+
BANCO CANÔNICO DO DOMÍNIO CRM
+
PROTHEUS COMO AUTORIDADE ERP
+
ADAPTER / ANTI-CORRUPTION LAYER
+
AUTORIZAÇÃO SERVER-SIDE
+
IDEMPOTÊNCIA
+
CONTROLE EXPLÍCITO DE CONCORRÊNCIA
+
FRESHNESS DE DADOS ERP
```

Nenhum microserviço, event sourcing, cache distribuído ou offline-first foi introduzido sem driver.

### 5.4. Tech Lead

**Resultado:** PASS.

A stack do horizonte atual está suficientemente definida:

```text
TypeScript 6.0
Node.js 24 LTS
React 19.2
Vite 8.1
React Router 8
TanStack Query 5
React Aria
NestJS 11
REST / JSON + OpenAPI
Zod 4 / Standard Schema
PostgreSQL 18
Prisma 8
OIDC / OAuth2 + PKCE
Vitest 4.1
Playwright
OpenTelemetry backend
npm workspaces
ESLint 10
Prettier 3.9
```

As POCs registradas no Tech Lead são explicitamente **simuladas para validação da metodologia**.

```text
SIMULATED POC PASS
!=
REAL FOUNDATION EVIDENCE
```

### 5.5. DevOps e infraestrutura

**Resultado:** PASS com gates operacionais futuros.

Para a simulação, foi deliberadamente adotado:

```text
PROTHEUS_HOSTING: ON_PREMISES
PRIMARY_CLOUD: MICROSOFT_AZURE
PRIMARY_REGION: BRAZIL_SOUTH
IDENTITY_PROVIDER: MICROSOFT_ENTRA_ID
HOSTING: AZURE_CONTAINER_APPS
DATABASE_PROVIDER: AZURE_POSTGRESQL_FLEXIBLE_SERVER
CONNECTIVITY: VNET + SITE_TO_SITE_VPN
SECRETS: KEY_VAULT + MANAGED_IDENTITY
CI_CD: GITHUB_ACTIONS + OIDC
REGISTRY: AZURE_CONTAINER_REGISTRY
IAC: BICEP
OBSERVABILITY: AZURE_MONITOR / APPLICATION_INSIGHTS
DR: LEVEL_2
MULTI_REGION: NO
```

A premissa `Protheus on-premises` é fato **simulado do caso**, não inferência sobre um cliente real.

Se em uma execução real o Protheus estiver em TCloud ou outra topologia, a decisão de conectividade e eventualmente provider precisa ser reaberta.

### 5.6. Fundação

**Resultado:** PASS como planejamento.

Existem `FND-001...FND-042`, dependências, caminho crítico, gates, evidências esperadas e condições de parada.

Todos permanecem:

```text
PLANNED
```

Nenhum foi marcado como `IMPLEMENTED` ou `VERIFIED`.

### 5.7. Backlog

**Resultado:** PASS.

A entrega foi estruturada em:

```text
M0 — Fundação
M1 — Continuidade comercial mínima
M2 — Cliente, carteira e Protheus essencial
M3 — Pilot Ready
M4 — Piloto e aprendizado
M5 — P0 condicionado
M6 — Expansão comercial
```

O backlog possui NFRs, gates operacionais, decisões de reconciliação, dependências e critérios de prontidão.

### 5.8. Matriz operacional

**Resultado:** PASS.

Estado auditado:

```text
MATERIAL_ORPHAN_REQUIREMENTS: 0
ORPHAN_IMPLEMENTATIONS: 0
CRITICAL_TRACE_CONFLICTS: 0
DONE_WITHOUT_EVIDENCE: 0
STALE_TRACES: 0
```

A ausência de implementação e evidência real é compatível com o estado greenfield.

---

## 6. Decisões de reconciliação aplicadas

As decisões `DEC-*` do backlog resolvem tensões materiais da baseline.

### DEC-001 — POC simulada não fecha FND real

Uma POC executada como simulação metodológica pode confirmar coerência de desenho, mas não substitui prova do ambiente real.

Consequência:

```text
TL-POC PASS
!=
FND VERIFIED
```

### DEC-002 — Metadata Protheus é consumida, não clonada

O CRM não possui um dicionário canônico próprio de campos do Protheus.

Direção:

```text
PROTHEUS
↓
metadata suportada
↓
adapter
↓
contrato normalizado
↓
backend validation
↓
frontend preventive validation
```

Metadados cacheados pelo CRM continuam derivados.

### DEC-003 — Banco próprio do CRM não replica autoridade ERP

O PostgreSQL existe porque há estado cuja autoridade pertence ao CRM:

- prospect;
- histórico comercial;
- próxima ação;
- ownership;
- transferência;
- auditoria CRM;
- idempotência;
- estado técnico próprio.

Ele não transforma pedido, estoque, financeiro, cliente formal ou metadata ERP em segunda verdade canônica.

### DEC-004 — Fundação produtiva completa não bloqueia desenvolvimento em staging

O backlog pode liberar M1 quando `GAT-001 — Staging Core Ready` estiver satisfeito.

Produção continua bloqueada por gate próprio.

### DEC-005 — Mobile P0 é web responsivo

Nenhum item do P0 possui autorização implícita para introduzir runtime nativo.

### DEC-006 — MUST GATE não significa MUST NOW

Histórias condicionadas continuam no P0, mas só avançam quando seus gates e evidências forem satisfeitos.

---

## 7. Pendências aceitas e blockers explícitos

A baseline possui incertezas deliberadamente não inventadas.

### BLK-001 — Owners reais

**Origem:** `FND-001`.

**Estado:** BLOCKED_UNTIL_HUMAN_DECISION.

**Owner da resolução:** organização/sponsor do projeto real.

**Necessário definir:**

- owner do repositório;
- owner técnico;
- owner Azure/billing;
- owner de DNS;
- owner Entra;
- responsável Protheus;
- owner de produção;
- owner de recuperação.

**Retomar quando:** humanos responsáveis forem definidos e registrados.

### BLK-002 — Ambiente Protheus real

**Origem:** `EXP-002`, `FND-019...023`, `GAT-002`.

**Faltam numa execução real:**

- release exato;
- customizações;
- endpoints;
- autenticação;
- empresa/filial;
- contrato de metadata real;
- payloads reais;
- topologia e regras de homologação.

**Retomar:** antes de fechar `GAT-002`.

### BLK-003 — Retenção de dados

**Origem:** `NFR-006`, `GAT-006`.

**Estado:** NEEDS_RECONCILIATION_BEFORE_REAL_DATA.

Nenhum prazo foi inventado.

**Retomar:** antes de autorizar dados reais.

### BLK-004 — Algoritmo de atenção

**Origem:** `HYP-004`, `HYP-007`, `BR-010`, `US-014`.

Não existe prazo universal como 60 ou 90 dias aprovado.

**Retomar:** quando evidência de produto permitir definir sinal útil sem ruído excessivo.

### BLK-005 — Estoque e financeiro

**Origem:** `US-010`, `US-011`.

Continuam no P0, mas dependem de contrato ERP, freshness, minimização, autorização e gate de produto.

Esses blockers são aceitáveis porque não exigem que o agente invente respostas para executar itens independentes.

---

## 8. Requisitos e implementações órfãos

```text
MATERIAL_ORPHAN_REQUIREMENTS: 0
ORPHAN_IMPLEMENTATIONS: 0
```

A segunda contagem é zero porque o caso permanece greenfield e não possui implementação funcional.

Não interpretar isso como auditoria positiva de um runtime inexistente.

---

## 9. Cobertura da matriz

A Matriz Operacional registra:

- traces de produto `TRACE-0001...TRACE-0018`;
- traces estruturais para repo/toolchain, Azure, Protheus, metadata, banco CRM, autorização, recuperação, promoção e business case;
- herança de NFR;
- gates;
- evidência esperada separada de evidência real;
- pendências com disposição explícita.

Estado recebido:

```text
TRACEABILITY_READINESS: SUFFICIENT_WITH_OPEN_ITEMS
CRITICAL_TRACE_CONFLICTS: 0
STALE_TRACES: 0
```

Isso é suficiente para o handoff porque itens abertos possuem disposição e momento de resolução.

---

## 10. Estado do backlog

```text
BACKLOG_READINESS: SUFFICIENT
OPERATIONAL_TARGET: GITHUB
ISSUES_PUBLISHED: NO
PROJECT_CREATED: NO
CONTINUITY_POLICY: MANUAL
```

Nenhuma Issue, milestone ou Project foi criado durante a validação documental.

Isso preserva a distinção:

```text
BACKLOG CANÔNICO
!=
TRACKER PUBLICADO
```

---

## 11. Estado da fundação

```text
FOUNDATION_READINESS: SUFFICIENT
FOUNDATION_STATUS: PLANNED
PROVISIONING_EXECUTED: NO
```

O caminho de fundação está planejado, mas nenhum recurso real foi provisionado.

Ações sensíveis continuam exigindo autorização explícita, especialmente:

- billing;
- Azure;
- VPN;
- produção;
- secrets;
- DNS;
- banco produtivo;
- conexão ao Protheus produtivo;
- dados reais.

---

## 12. Gates humanos

### HUMAN-GATE-001 — Ownership

Bloqueia materialização de `FND-001`.

### HUMAN-GATE-002 — Custos e recursos pagos

Bloqueia criação material de recursos que ativem cobrança fora da autorização recebida.

### HUMAN-GATE-003 — Production Foundation

Bloqueia `FND-031+` até staging e aprovação humana.

### HUMAN-GATE-004 — Real Data

Bloqueia dados reais até política de retenção, segurança e autorização apropriadas.

### HUMAN-GATE-005 — DNS produtivo

Bloqueia alteração de domínio crítico sem owner.

### HUMAN-GATE-006 — Protheus production

Bloqueia credenciais e conectividade ao ambiente produtivo sem autorização.

### HUMAN-GATE-007 — Mudança canônica

Bloqueia qualquer decisão que altere produto, UX, ADR, TDR ou IDR fora do item.

---

## 13. Segurança e dados

O handoff preserva:

```text
DADOS SINTÉTICOS POR PADRÃO
SECRETS FORA DE PROMPT / COMMIT / ISSUE / DOC / FIXTURE
AUTHORIZATION SERVER-SIDE
CARTEIRA COMO CONTEXTO DE AUTORIZAÇÃO
PROTHEUS CREDENTIALS SOMENTE BACKEND
ERP AUTHORITY PRESERVED
TELEMETRIA MINIMIZADA
PRODUÇÃO POR GATE
```

O Codex não possui autorização para solicitar que segredos sejam colados no prompt.

Se um item precisar de secret ausente:

```text
STOP
→ solicitar ação humana segura
```

---

## 14. Gates do handoff

| Gate | Resultado | Nota |
| --- | --- | --- |
| HOFF-01 Baseline | PASS | documentos necessários 00–12 definidos |
| HOFF-02 Authority | PASS | nenhuma contradição material sem disposição |
| HOFF-03 Backlog | PASS | próximo trabalho lógico conhecido; blockers explícitos |
| HOFF-04 Trace | PASS | itens resolvem fontes pela matriz |
| HOFF-05 Architecture | PASS | ADRs e requisitos estruturais suficientes |
| HOFF-06 Stack | PASS | stack concreta suficiente para o horizonte |
| HOFF-07 Infra | PASS | decisões de infra suficientes para planejar execução |
| HOFF-08 Foundation | PASS | FNDs, dependências e gates claros |
| HOFF-09 Quality | PASS | NFRs, verificações e evidências esperadas definidas |
| HOFF-10 Security | PASS | secrets, dados, authz e produção protegidos por política/gates |
| HOFF-11 AI Scope | PASS | stop conditions e limites explícitos |
| HOFF-12 Continuity | PASS | `MANUAL_EACH_ITEM` declarado |

Resultado:

```text
HOFF_GATES: 12/12 PASS
```

---

## 15. Política de continuidade

Para o Caso 01:

```text
CONTINUATION_POLICY: MANUAL_EACH_ITEM
```

Isso significa:

```text
ITEM VERIFIED DONE
↓
PRÓXIMO ITEM PODE SE TORNAR ELEGÍVEL
↓
AGUARDAR NOVA AUTORIZAÇÃO HUMANA
```

O agente não deve avançar automaticamente para o próximo item apenas porque a dependência anterior foi concluída.

Esta política foi escolhida porque o Caso 01 é a primeira validação ponta a ponta da metodologia e queremos observar explicitamente os handoffs e gates.

---

## 16. Próximo item lógico

O primeiro item do caminho é:

```text
FND-001 — Definir ownership organizacional
```

Entretanto:

```text
ITEM_EXECUTION_MODE: HUMAN_LED
HUMAN_ACTION_REQUIRED_NOW: YES
MUTATION_AUTHORIZED: NO
```

O Codex pode ajudar a produzir uma matriz ou checklist de ownership, mas não pode escolher pessoas, contas ou responsabilidades reais em nome da organização.

Depois da resolução de `FND-001`, os primeiros itens materiais incluem, conforme dependências e autorização:

```text
FND-003 — Repositório operacional
FND-004 — Governança da branch principal
FND-005 — Toolchain
FND-006 — Skeleton
FND-007 — CI
```

Azure não precisa ser a primeira mutação do projeto.

---

## 17. Pacote inicial de contexto do Codex

Ao iniciar um item futuro, o agente deve montar o recorte:

```text
ITEM ID
OBJETIVO
OUTCOME
ESCOPO
FORA DE ESCOPO
FONTES CANÔNICAS
TRACE IDs
BRs
JORNADAS / ESTADOS UX
UI APLICÁVEL
ADRs
TECH-REQs
TDRs
IDRs
NFRs
DEPENDÊNCIAS
GATES
TESTES / VERIFICAÇÃO
EVIDÊNCIA ESPERADA
ROLLOUT
ROLLBACK
STOP CONDITIONS
```

A Matriz existe para localizar essas fontes sem despejar todo o repositório indiscriminadamente no contexto do agente.

---

## 18. Stop conditions específicas do Caso 01

Além das stop conditions gerais da metodologia, o agente deve interromper se precisar:

- inventar regra Protheus;
- inventar metadata do ERP;
- criar dicionário Protheus canônico próprio no CRM;
- usar acesso direto a tabelas internas como atalho sem decisão aprovada;
- transformar snapshot ERP em autoridade;
- escolher quais dados financeiros vendedores podem ver;
- inventar regra de 60/90 dias para atenção;
- escolher owner humano;
- usar dado real não autorizado;
- usar credencial de produção;
- criar ou revelar secret;
- criar produção antes do gate;
- alterar DNS produtivo;
- ativar gasto não aprovado;
- executar migration destrutiva não autorizada;
- trocar framework, banco, cloud ou boundary;
- criar app nativo sem reabrir Tech Lead/produto;
- adicionar cache, broker ou microserviço por preferência;
- ignorar indisponibilidade/freshness do Protheus;
- reduzir autorização a controle visual;
- avançar ao próximo item sem nova autorização sob `MANUAL_EACH_ITEM`.

---

## 19. Descobertas durante execução

Qualquer descoberta do Codex deve ser classificada antes de alterar a baseline.

```text
IMPLEMENTATION_DETAIL
DEFECT
NEW_CONSTRAINT
ARCHITECTURAL_IMPACT
PRODUCT_IMPACT
SECURITY_INCIDENT
EXTERNAL_CHANGE
```

### IMPLEMENTATION_DETAIL

Pode ser resolvido dentro do item quando não altera contrato.

### DEFECT

Pode produzir `COR-xxx` quando material e comprovado.

### NEW_CONSTRAINT

Pode exigir gate, TDR, IDR ou outra reconciliação.

### ARCHITECTURAL_IMPACT

Reabrir `07_Engenharia_e_Arquitetura.md` e ADR aplicável.

### PRODUCT_IMPACT

Reabrir PO/Briefing conforme materialidade.

### SECURITY_INCIDENT

Interromper trabalho incompatível e aplicar contenção apropriada.

### EXTERNAL_CHANGE

Rever API, provider, licença, preço, política ou integração afetada.

Regra:

```text
DESCOBERTA
!=
AUTORIZAÇÃO PARA REESCREVER A BASELINE
```

---

## 20. Reconciliação após POCs e evidência real

O Caso 01 demonstrou explicitamente que POCs podem refinar decisões anteriores.

Fluxo obrigatório quando isso acontecer:

```text
POC / EVIDÊNCIA
↓
resultado contradiz ou refina decisão
↓
identificar fonte proprietária
↓
reabrir ADR / TDR / IDR / produto quando necessário
↓
canonizar mudança
↓
reconciliar DOC 10
↓
reconciliar DOC 11
↓
reconciliar DOC 12
↓
nova baseline versionada
```

Não esconder mudança arquitetural dentro de um PR.

---

## 21. Handshake futuro do Codex

Ao receber a chave de execução com autorização adequada, a resposta inicial esperada antes de mutação é equivalente a:

```text
CODEX_PROCESS: ACTIVE
TRIGGER: CODEX_CANONICAL_START_V1
BASELINE_ID: BL-CASE-01-CRM-1
BASELINE_READINESS: READY_FOR_CODEX
CURRENT_ITEM: <id>
ITEM_STATUS: READY
MILESTONE: <id>
TRACE: <ids>
DEPENDENCIES: SATISFIED
ENTRY_GATES: SATISFIED
HUMAN_ACTION_REQUIRED_NOW: <YES/NO>
EXPECTED_EVIDENCE: <resumo>
STOP_CONDITIONS: LOADED
```

Se um campo crítico não puder ser preenchido sem inventar:

```text
STOP
```

---

## 22. Chave canônica

A chave de protocolo é:

```text
CODEX_CANONICAL_START_V1
```

Prompt curto permitido quando a baseline estiver disponível:

```text
CODEX_CANONICAL_START_V1
Execute a baseline canônica deste projeto.
```

A chave não é segredo.

Ela não concede autorização irrestrita.

```text
CODEX_CANONICAL_START_V1
!=
AUTORIZAR PRODUÇÃO
!=
AUTORIZAR GASTO
!=
AUTORIZAR DADO REAL
!=
AUTORIZAR MUDANÇA DE PRODUTO
```

---

## 23. Estado da publicação operacional

```text
GITHUB_ISSUES_PUBLISHED: NO
GITHUB_PROJECT_CREATED: NO
MILESTONES_CREATED: NO
PRODUCT_CODE_IMPLEMENTED: NO
INFRA_PROVISIONED: NO
PRODUCTION_CREATED: NO
```

A baseline pode estar `READY_FOR_CODEX` mesmo sem o tracker operacional publicado, desde que o primeiro item e os blockers estejam claramente definidos.

Antes de usar GitHub como tracker real, a publicação deverá seguir a política do documento 10 e autorização correspondente.

---

## 24. Evidência existente nesta baseline

### Evidência documental real

Existe evidência real de que a metodologia foi aplicada e canonizada no repositório do processo.

### Evidência técnica do CRM real

Não existe, porque o CRM não foi implementado.

### POCs técnicas

Existem resultados explicitamente classificados como **simulação metodológica** no Tech Lead.

Portanto:

```text
DOCUMENTATION_EVIDENCE: REAL
SIMULATION_EVIDENCE: PRESENT
CRM_RUNTIME_EVIDENCE: NONE
```

Essa separação precisa sobreviver a qualquer leitura futura do caso.

---

## 25. Readiness final

Após a auditoria transversal:

```text
FINAL_RECONCILIATION: PASS

PRODUCT: COHERENT
UX_UI: COHERENT
ENGINEERING: COHERENT
ARCHITECTURE: COHERENT
TECH_STACK: COHERENT
INFRASTRUCTURE: COHERENT
FOUNDATION: PLANNED_AND_TRACEABLE
BACKLOG: SUFFICIENT
TRACEABILITY: SUFFICIENT_WITH_OPEN_ITEMS

CRITICAL_CONTRADICTIONS: 0
MATERIAL_ORPHAN_REQUIREMENTS: 0
ORPHAN_IMPLEMENTATIONS: 0
STALE_TRACES: 0

HOFF_GATES: 12/12 PASS

BASELINE_READINESS: READY_FOR_CODEX
HANDOFF_READINESS: SUFFICIENT
BASELINE_FREEZE: ACTIVE
CODEX_TRIGGER: CODEX_CANONICAL_START_V1
CONTINUATION_POLICY: MANUAL_EACH_ITEM
EXECUTION_AUTHORIZATION: NOT_GRANTED
```

A baseline é tecnicamente consumível pelo Codex.

O agente, porém, não deve executar enquanto não existir uma autorização humana inequívoca para iniciar o protocolo e o item em questão.

---

## 26. Estado do Caso 01

O Caso 01 percorreu integralmente a metodologia:

```text
DISCOVERY
↓
PESQUISA E VIABILIDADE
↓
BRIEFING
↓
PRODUCT OWNER
↓
PRINCÍPIOS UX/UI
↓
DIREÇÃO UI / DESIGN SYSTEM
↓
ESPECIFICAÇÃO UX
↓
TÉCNICAS DE DESENVOLVIMENTO
↓
ENGENHARIA E ARQUITETURA
↓
TECH LEAD
↓
DEVOPS / INFRA
↓
PLANO DE FUNDAÇÃO
↓
BACKLOG CANÔNICO
↓
MATRIZ DE RASTREABILIDADE
↓
RECONCILIAÇÃO FINAL / HANDOFF
```

Resultado do caso:

```text
CASE_END_TO_END_DOCUMENT_FLOW: PASS
CASE_IMPLEMENTATION_EXECUTED: NO
CASE_USED_AS_METHODOLOGY_VALIDATION: YES
```

---

## 27. Handoff final

```text
CASE_ID: CASE-01-CRM-CLIENTES-PEDIDOS
BASELINE_ID: BL-CASE-01-CRM-1
BASELINE_VERSION: 1.0.0
BASELINE_READINESS: READY_FOR_CODEX
HANDOFF_READINESS: SUFFICIENT
BASELINE_FREEZE: ACTIVE
CODEX_TRIGGER: CODEX_CANONICAL_START_V1
CONTINUATION_POLICY: MANUAL_EACH_ITEM
NEXT_LOGICAL_ITEM: FND-001
NEXT_LOGICAL_ITEM_EXECUTION: HUMAN_LED
HUMAN_ACTION_REQUIRED_NOW: YES
EXECUTION_AUTHORIZATION: NOT_GRANTED
CASE_DOCUMENTATION_STATUS: COMPLETE
```

O Caso 01 está documentalmente encerrado.

Qualquer execução futura passa a ser uma nova fase: **execução da baseline**, com produção de código, testes, infraestrutura e evidências reais, seguida de reconciliação contínua.

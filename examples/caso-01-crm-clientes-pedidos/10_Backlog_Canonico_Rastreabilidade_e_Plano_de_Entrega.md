---
document_id: CASE-01-DOC-10
title: Backlog Canônico, Rastreabilidade e Plano de Entrega — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: backlog-canonico
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
next_document: 11_Matriz_Operacional_de_Rastreabilidade.md
backlog_readiness: SUFFICIENT
operational_target: GITHUB
continuity_policy: MANUAL
issues_published: false
project_created: false
ready_for_codex: false
---

# Backlog Canônico, Rastreabilidade e Plano de Entrega — CRM para gestão de clientes e pedidos

## 1. Decisão executiva

Este documento transforma a baseline aprovada do Caso 01 em uma ordem operacional única de entrega sem substituir as fontes canônicas que originaram produto, UX, arquitetura, stack, infraestrutura e fundação.

A pergunta central é:

> **Como transformar produto, experiência, arquitetura, stack, infraestrutura, fundação, qualidade, riscos e gates já aprovados em uma única ordem operacional de entrega, mantendo cada item ligado à sua origem, dependências, critérios de aceite e evidências necessárias para considerá-lo concluído?**

A regra central permanece:

```text
DOCUMENTAÇÃO CANÔNICA
= intenção e contrato

BACKLOG CANÔNICO
= tradução operacional

GITHUB
= estado futuro da execução

CÓDIGO / TESTE / DEPLOY
= evidência
```

Nenhuma dessas camadas substitui silenciosamente as demais.

A canonização deste documento não autoriza implementação funcional, provisionamento, criação de produção, publicação de Issues, criação de GitHub Project ou execução pelo Codex.

---

## 2. Handshake e estado

```text
PROCESS_STATUS: ACTIVE
CURRENT_STAGE: BACKLOG_CANONICO
INPUT_BASELINE: DOCUMENTOS_00_A_09
OPERATIONAL_TARGET: GITHUB
BROWNFIELD_TRACKER: ABSENT
ISSUES_PUBLISHED: NO
PROJECT_CREATED: NO
BACKLOG_READINESS: SUFFICIENT
READY_FOR_CODEX: NO
```

---

## 3. Hierarquia de autoridade

Conflitos futuros devem ser resolvidos pela fonte que possui autoridade sobre o tema.

Ordem prática:

```text
1. LEI / SEGURANÇA / OBRIGAÇÃO EXTERNA VINCULANTE
2. BRIEFING / PRODUCT OWNER
3. PRINCÍPIOS / UI / UX
4. ENGENHARIA E ARQUITETURA
5. VISÃO DO TECH LEAD
6. DEVOPS E INFRAESTRUTURA
7. TÉCNICAS DE DESENVOLVIMENTO
8. PLANO DE FUNDAÇÃO
9. BACKLOG / ISSUE / PROMPT / AGENTE
```

Quando uma nova evidência invalida decisão superior, a Issue não possui autoridade para corrigi-la isoladamente.

Fluxo:

```text
EVIDÊNCIA NOVA
↓
IDENTIFICAR FONTE RESPONSÁVEL
↓
REABRIR PO / UX / ADR / TDR / IDR
↓
RECONCILIAR
↓
ATUALIZAR BACKLOG
```

---

## 4. Método de canonização aplicado

Foram executados os cinco passes previstos pela metodologia.

### PASS 1 — Inventário

Inventariados:

- 7 épicos de produto;
- 18 histórias funcionais;
- 42 itens de fundação `FND-*`;
- 4 experimentos `EXP-*`;
- 6 gates de produto `G-*`;
- 7 POCs técnicas simuladas `TL-POC-*`;
- requisitos não funcionais transversais;
- decisões arquiteturais, tecnológicas e operacionais;
- riscos, dependências, waves e evidências esperadas;
- itens P1/P2 explicitamente deferidos.

Correções comprovadas abertas no momento:

```text
COR_OPEN: NONE
```

### PASS 2 — Normalização

Os tipos foram mantidos semanticamente separados:

- `E-*` — épicos;
- `US-*` — histórias de produto;
- `FND-*` — fundação/habilitador;
- `NFR-*` — requisito não funcional transversal;
- `GAT-*` — gate operacional;
- `EXP-*` — experimento;
- `TL-POC-*` — POC técnica;
- `DEC-*` — decisão de reconciliação;
- `COR-*` — correção comprovada futura;
- `P1/P2` — horizonte deferido.

IDs canônicos não foram renumerados.

### PASS 3 — Reconciliação

As tensões relevantes foram resolvidas e registradas em `DEC-*`.

### PASS 4 — Sequenciamento

Foram definidos:

- dependências;
- caminho crítico;
- marcos `M0...M6`;
- gates de entrada e saída;
- atividades paralelizáveis;
- progressão de staging para produção;
- progressão de piloto para expansão.

### PASS 5 — Publicação

A publicação operacional ainda não foi executada.

```text
DOCUMENTO 10: CANONICAL
GITHUB ISSUES: NOT PUBLISHED
GITHUB PROJECT: NOT CREATED
MILESTONES: NOT CREATED
LABELS: NOT CREATED
```

A mutação operacional depende de autorização posterior.

---

## 5. Taxonomia e gramática de IDs

IDs preservados:

```text
OUT-xxx   outcomes
HYP-xxx   hipóteses
BR-xxx    regras de negócio
J-xxx     jornadas de PO
E-xxx     épicos
US-xxx    histórias
G-xxx     gates de produto
EXP-xxx   experimentos
UX-*      contratos de experiência
UI-*      contratos de direção visual
ARCH-*    arquitetura
ADR-*     decisões arquiteturais
TECH-REQ-* requisitos para stack
TDR-*     decisões tecnológicas
TL-POC-*  provas técnicas
IDR-*     decisões de infraestrutura
FND-*     fundação
NFR-*     requisitos não funcionais do backlog
GAT-*     gates operacionais
DEC-*     reconciliações
COR-*     correções comprovadas futuras
```

Regras:

1. ID removido não é reutilizado;
2. item supersedido preserva histórico;
3. FND não renumera US;
4. NFR não vira story apenas para caber em tracker;
5. gate não é tratado como tarefa comum;
6. correção futura usa `COR-*` sem ocupar lacuna de outro tipo.

---

## 6. Portfólio por épico

### E-001 — Prioridades comerciais

Objetivo: dar ao vendedor clareza sobre o que exige atenção.

Histórias:

- `US-001` Ver prioridades;
- `US-014` Identificar clientes sem atenção.

### E-002 — Cliente e prospect

Objetivo: localizar e criar entidades comerciais sem duplicidade indevida.

Histórias:

- `US-002` Localizar cliente;
- `US-003` Descobrir cliente de outra carteira;
- `US-004` Criar prospect.

### E-003 — Histórico e próxima ação

Objetivo: preservar continuidade comercial.

Histórias:

- `US-005` Ver histórico;
- `US-006` Registrar interação;
- `US-007` Definir próxima ação.

### E-004 — Carteira e responsabilidade

Objetivo: organizar responsabilidade comercial sem quebrar histórico.

Histórias:

- `US-012` Ver carteira;
- `US-013` Transferir responsabilidade.

### E-005 — Contexto Protheus

Objetivo: trazer contexto ERP necessário sem recriar operação transacional.

Histórias:

- `US-008` Ver contexto de compra;
- `US-009` Ver situação de pedido;
- `US-010` Ver disponibilidade comercial necessária;
- `US-011` Consultar restrição financeira permitida;
- `US-018` Reconhecer indisponibilidade do ERP.

### E-006 — Gestão comercial

Objetivo: permitir intervenção gerencial com evidência suficiente.

Histórias:

- `US-015` Acompanhar equipe;
- `US-016` Visão executiva mínima.

### E-007 — Governança e auditabilidade

Objetivo: preservar autoria, acesso, continuidade e responsabilidade.

História diretamente associada:

- `US-017` Preservar histórico após desligamento.

Diversas histórias de outros épicos também herdam NFRs de segurança, auditabilidade e privacidade.

---

## 7. Histórias funcionais do horizonte P0

| ID | Título | Prioridade PO | Marco operacional inicial |
| --- | --- | --- | --- |
| US-001 | Ver prioridades | MUST CORE | M1 |
| US-002 | Localizar cliente | MUST CORE | M2 |
| US-003 | Descobrir cliente de outra carteira | MUST CORE | M2 |
| US-004 | Criar prospect | MUST CORE | M1 |
| US-005 | Ver histórico | MUST CORE | M2 |
| US-006 | Registrar interação | MUST CORE | M1 |
| US-007 | Definir próxima ação | MUST CORE | M1 |
| US-008 | Ver contexto de compra | MUST CORE | M2 |
| US-009 | Ver situação de pedido | MUST CORE | M2 |
| US-010 | Ver disponibilidade comercial necessária | MUST GATE | M5 |
| US-011 | Consultar restrição financeira permitida | MUST GATE | M5 |
| US-012 | Ver carteira | MUST CORE | M2 |
| US-013 | Transferir responsabilidade | MUST CORE | M2 |
| US-014 | Identificar clientes sem atenção | MUST GATE | M5 |
| US-015 | Acompanhar equipe | MUST CORE | M3 |
| US-016 | Visão executiva mínima | MUST CORE | M5 |
| US-017 | Preservar histórico após desligamento | MUST CORE | M2 |
| US-018 | Reconhecer indisponibilidade do ERP | MUST CORE | M2 |

`MUST GATE` significa essencial condicionado a prova/decisão, não execução imediata.

---

## 8. Fundação / FNDs

Os 42 itens de `09_Plano_de_Fundacao.md` permanecem canônicos e `PLANNED`.

### FND-001...FND-030 — Fundação de staging e provas

Cobrem:

- ownership;
- billing/budget;
- repositório;
- proteção de branch;
- toolchain;
- skeleton;
- CI;
- OIDC GitHub→Azure;
- staging;
- Key Vault;
- VNet;
- PostgreSQL;
- migrations;
- Container Apps;
- ACR/digests;
- deploy;
- observabilidade;
- VPN;
- Protheus homologação;
- metadata contract;
- validação orientada por metadata;
- read contracts;
- degradação Protheus;
- backup;
- restore;
- Entra ID;
- autorização server-side;
- rollback;
- lifecycle de migrations;
- runbooks.

### FND-031...FND-042 — Fundação produtiva e consolidação

Cobrem:

- ambiente production;
- workload identity production;
- Key Vault production;
- VPN Protheus production;
- PostgreSQL production;
- workloads production;
- observabilidade/budget;
- promoção do mesmo digest;
- rollback produtivo;
- DNS/TLS;
- restore production-like;
- documentação operacional.

Regra operacional:

```text
FND PLANNED
≠
FND AUTHORIZED
```

---

## 9. NFRs transversais normalizados

### NFR-001 — Acessibilidade

**Fontes:** Princípios UX/UI, Direção de UI, Especificação UX, Técnicas de Desenvolvimento.

Exige, quando aplicável:

- teclado;
- foco previsível;
- semântica;
- zoom/text scale;
- alvos de toque;
- reader smoke;
- estado sem depender apenas de cor;
- alternativa a gesto;
- jornada completa acessível.

### NFR-002 — Autorização e privacidade de carteira

**Fontes:** `BR-004`, `BR-005`, `BR-007`, arquitetura e threat model.

Decisão autoritativa considera:

```text
SUJEITO
+
PAPEL
+
AÇÃO
+
RECURSO
+
OWNERSHIP
+
ESCOPO ORGANIZACIONAL
```

UI nunca é a única barreira.

### NFR-003 — Autoridade e confiança Protheus

**Fontes:** `BR-001`, `BR-011`, `BR-012`, ADRs e UX.

Inclui:

- Protheus como autoridade ERP;
- CRM não mantém dicionário Protheus canônico próprio;
- metadata é derivada do ERP por contrato suportado;
- estados externos distinguem `CURRENT`, `REFRESHING`, `STALE`, `UNAVAILABLE` ou equivalentes;
- dado antigo não é apresentado como confirmação atual.

### NFR-004 — Idempotência e concorrência

Aplica principalmente a:

- criação de prospect;
- registro de interação;
- transferência de ownership;
- futuras escritas externas.

Transferência concorrente não pode produzir `last-write-wins` acidental.

### NFR-005 — Auditabilidade

Ações materiais preservam ator, momento, alvo e resultado apropriados.

### NFR-006 — Minimização e proteção de dados

Inclui:

- dados comerciais;
- dados pessoais;
- financeiro;
- logs;
- analytics;
- prompts;
- evidências.

### NFR-007 — Recuperabilidade e conectividade

Inclui:

- rede instável não apagar rascunho válido;
- Protheus indisponível não derrubar core CRM;
- backup/restore compatíveis com targets aprovados.

### NFR-008 — Compatibilidade e migrations

Contratos e schema evoluem progressivamente, com estratégia compatível e reversível.

### NFR-009 — Observabilidade e operabilidade

Logs, métricas, traces, audit logs e runbooks provam comportamento sem copiar conteúdo sensível desnecessário.

### NFR-010 — Business case e custo

Complexidade e custo continuam condicionados pelo business case aprovado.

---

## 10. Gates operacionais

### GAT-001 — Staging Core Ready

**Origem:** Plano de Fundação.

**Condição:** fundação mínima de staging permite desenvolvimento funcional seguro.

**Evidência:** repo, toolchain, CI, banco, deploy, auth baseline, secrets e observabilidade básicos provados.

**Libera:** M1.

### GAT-002 — Protheus Staging Ready

**Origem:** `G-001`, FND-018...FND-023.

**Condição:** rede, homologação, metadata, validação, read contracts e failure mode aprovados.

**Libera:** histórias do M2 dependentes do ERP.

### GAT-003 — Data Authority Preserved

**Origem:** `BR-001`, `BR-011`, arquitetura, Tech Lead e Foundation Gate de autoridade.

**Condição:** banco CRM persiste domínio CRM sem virar segunda autoridade de SA1/SC5/SC6 ou equivalentes.

### GAT-004 — Portfolio Security

**Origem:** `G-004`.

**Condição:** acesso horizontal indevido é negado e descoberta mínima permanece separada do histórico restrito.

**Falha:** HOLD.

### GAT-005 — Production Foundation Authorized

**Origem:** gate humano do Plano de Fundação.

**Condição:** staging fundacional suficientemente verificado + aprovação humana.

### GAT-006 — Real Data Authorized

**Condição:** uso de dados reais foi autorizado após fundação produtiva e controles aplicáveis.

### GAT-007 — No Relevant Double Operation

**Origem:** `G-002`, `GR-001`.

**Condição:** piloto não exige manutenção material da mesma informação em CRM + controles paralelos/ERP.

### GAT-008 — Operational Adoption

**Origem:** `G-003`.

**Condição:** vendedores piloto usam o CRM como ferramenta principal do core.

### GAT-009 — Parallel Controls Abandonment

**Origem:** `G-006`.

**Condição:** planilha paralela de carteira/follow-up deixa de ser dependência sistemática do piloto.

### GAT-010 — Business Case Healthy

**Origem:** `G-005`, `OUT-006`, `NFR-010`.

**Condição:** TCO e benefício permanecem dentro dos limites aceitos.

**Falha:** reabrir BUILD × BUY × HYBRID.

### GAT-011 — Expansion Authorized

**Condição:** segurança, adoção, abandono de paralelos, integração e business case estão saudáveis.

**Libera:** expansão de coorte.

---

## 11. Experimentos e validações

### EXP-001 — Baseline operacional real

Objetivo: validar a estimativa de aproximadamente 234 h/mês associadas à fragmentação.

Alimenta:

- `OUT-004`;
- `OUT-006`;
- `GAT-010`.

### EXP-002 — Integração real Protheus

Objetivo: provar contratos relevantes do ambiente real e customizações.

Alimenta:

- `OUT-005`;
- `GAT-002`.

### EXP-003 — Fluxo diário do vendedor

Pergunta: vendedor consegue prioridade → contexto → ação → registro → próxima ação sem retornar a controles paralelos?

Alimenta:

- `HYP-001`;
- `HYP-002`;
- `HYP-003`.

### EXP-004 — Piloto controlado

Objetivo: medir adoção, duplicidade, continuidade e redução de fragmentação numa coorte pequena.

Alimenta:

- `GAT-007`;
- `GAT-008`;
- `GAT-009`;
- `GAT-010`;
- `GAT-011`.

---

## 12. POCs técnicas

POCs simuladas já executadas no Tech Lead:

- `TL-POC-001` PostgreSQL 18 + Prisma 8;
- `TL-POC-002` metadata-driven validation Protheus;
- `TL-POC-003` ERP read contract;
- `TL-POC-004` degradação Protheus;
- `TL-POC-005` OIDC/session model;
- `TL-POC-006` OpenAPI/codegen;
- `TL-POC-007` experiência web/framework capability.

Regra de reconciliação:

```text
POC SIMULADA PASS
!=
EVIDÊNCIA REAL DE FND
```

As POCs validam a coerência da stack na simulação, mas não marcam FNDs reais como `VERIFIED`.

---

## 13. Decisões de reconciliação

### DEC-001 — POC simulada não fecha Fundação real

**Fontes em tensão:** Tech Lead × Plano de Fundação.

**Resolução:** resultados simulados preservam `TL-POC-*`, mas todos os FNDs dependentes permanecem `PLANNED` até execução real.

**Itens afetados:** FND-013, FND-020, FND-021, FND-022, FND-023, FND-026 e outros de prova.

---

### DEC-002 — Metadata Protheus não exige dicionário próprio no CRM

**Fontes:** `BR-001`, `BR-011`, Tech Lead, Plano de Fundação.

**Resolução:** metadata é consumida do Protheus por adapter/contrato suportado; cache normalizado pode existir, mas não vira autoridade.

Não há alteração de produto.

---

### DEC-003 — Banco próprio CRM não replica ERP por padrão

**Fontes:** Arquitetura, Tech Lead e Plano de Fundação.

**Resolução:** PostgreSQL existe para estado cuja autoridade pertence ao CRM.

Snapshot/materialização ERP futura precisa justificar:

- autoridade;
- freshness;
- retenção;
- reconstruibilidade;
- segurança;
- finalidade.

---

### DEC-004 — M0 não bloqueia todo desenvolvimento até produção existir

**Tensão:** Plano de Fundação inclui produção, mas aprendizado funcional pode começar em staging.

**Resolução:** `GAT-001` libera M1 em staging enquanto M0 continua aberto para itens produtivos.

Produção permanece bloqueada por `GAT-005`.

---

### DEC-005 — Web responsivo satisfaz mobile no P0

**Fonte:** TDR do Tech Lead.

**Resolução:** nenhuma Issue do P0 pode introduzir runtime mobile nativo sem reabrir TDR correspondente.

---

### DEC-006 — MUST GATE não significa MUST NOW

**Fonte:** Product Owner.

**Resolução:** `US-010`, `US-011` e `US-014` permanecem P0, porém só entram após gates/evidências apropriadas.

`US-014` não pode assumir arbitrariamente prazo universal como 60 ou 90 dias.

---

## 14. Itens deferidos

### P1

Mantidos visíveis, sem contrato executável automático:

- dashboards avançados;
- métricas refinadas;
- importação estruturada de planilhas;
- automações adicionais;
- regras de atenção sofisticadas;
- novas origens de leads;
- propostas/anexos;
- WhatsApp mais profundo;
- automação prospect → cliente;
- eventual criação de pedido pelo CRM.

### P2

- inteligência de carteira;
- recomendações;
- priorização preditiva;
- forecasting;
- automações maduras;
- novas integrações.

Regra:

```text
DEFERRED
!=
FORGOTTEN
```

Mas itens deferidos não competem com o horizonte P0.

---

## 15. Dependências principais

O backlog é um grafo, não uma lista numérica.

### Fundação

```text
FND-001
↓
FND-003 / FND-005
↓
FND-006
↓
FND-007
↓
FND-008 / FND-009
↓
DB + CONTAINER + DEPLOY + AUTH + OBS
↓
GAT-001
```

### Protheus

```text
FND-011
↓
FND-018
↓
FND-019
↓
FND-020 / 021 / 022 / 023
↓
GAT-002 + GAT-003
```

### Produto

```text
GAT-001
↓
M1
↓
GAT-002 / 003
↓
M2
↓
GAT-004
↓
M3
↓
M4 piloto
↓
GAT-007 / 008 / 009 / 010
↓
M5
↓
GAT-011
↓
M6
```

---

## 16. Caminho crítico global

```text
FND-001
↓
repositório / toolchain / CI
↓
staging
↓
banco + auth + deploy + observabilidade
↓
GAT-001
↓
M1 core comercial

EM PARALELO
VPN
↓
metadata
↓
read contracts
↓
failure proof
↓
GAT-002 / GAT-003

↓
M2 cliente + carteira + Protheus
↓
GAT-004
↓
fundação production
↓
GAT-005 / GAT-006
↓
M3 pilot ready
↓
M4 piloto
↓
GAT-007 / 008 / 009 / 010
↓
M5 P0 condicionado
↓
GAT-011
↓
M6 expansão
```

---

## 17. Marcos e plano de entrega

### M0 — Fundação

**Objetivo:** criar e provar base suficiente para desenvolvimento, integração e posterior produção.

**Itens:** `FND-001...FND-042`.

**Subgates:**

- `M0-G1` → `GAT-001 Staging Core Ready`;
- `M0-G2` → `GAT-002 + GAT-003 Protheus/Data Authority`;
- `M0-G3` → `GAT-005 Production Foundation Authorized`.

**Critério:** M0 pode permanecer parcialmente aberto enquanto M1/M2 avançam em staging, desde que o subgate necessário esteja aprovado.

---

### M1 — Continuidade comercial mínima

**Objetivo:** provar o domínio próprio do CRM antes de deixar integração ERP dominar o produto.

**Fatia vertical principal:**

```text
US-004 Criar prospect
↓
US-006 Registrar interação
↓
US-007 Definir próxima ação
↓
US-001 Ver prioridades
```

**Entrada:** `GAT-001`.

**Saída:** vendedor simulado consegue criar prospect, registrar contato, definir próxima ação e reencontrá-la, com idempotência, recuperação e acessibilidade básicas.

**NFRs dominantes:** NFR-001, 004, 005, 006, 007, 009.

---

### M2 — Cliente, carteira e contexto Protheus essencial

**Objetivo:** conectar o core ao ERP e às regras de carteira.

**Histórias principais:**

- US-002;
- US-003;
- US-005;
- US-008;
- US-009;
- US-012;
- US-013;
- US-017;
- US-018.

**Entrada:** `GAT-001 + GAT-002 + GAT-003`.

**Saída:**

- cliente ERP localizável;
- descoberta de cliente alheio sem vazamento de histórico;
- carteira própria utilizável;
- transferência preserva histórico e trata concorrência;
- pedido/contexto Protheus funciona;
- ERP indisponível degrada corretamente sem derrubar core.

**Gate de saída:** `GAT-004`.

---

### M3 — Pilot Ready

**Objetivo:** deixar uma pequena coorte tecnicamente apta a usar o núcleo real.

**Principal história adicional:** `US-015`.

**Entrada:** M1 + M2 aceitos, GAT-004, GAT-005 e GAT-006.

**Coorte simulada inicial:** 3 vendedores + 1 gerente.

**Saída:** operação mínima do piloto pronta com observabilidade e rollback.

---

### M4 — Piloto e aprendizado

**Objetivo:** produzir evidência real/simulada de comportamento, não volume de código.

**Executa:** `EXP-003` e `EXP-004`.

**Avalia:**

- GAT-007;
- GAT-008;
- GAT-009;
- GAT-010;
- continuidade do GAT-004.

**HOLD/PIVOT se:**

- planilhas paralelas continuam indispensáveis;
- CRM aumenta trabalho relevante;
- integração produz divergência;
- segurança falha;
- registro é burocrático;
- prioridades geram ruído excessivo;
- business case deixa de ser defensável.

---

### M5 — Completar capacidades P0 condicionais

**Objetivo:** implementar capacidades úteis que carregam maior risco de regra, exposição ou burocracia somente após aprendizado do piloto.

**Histórias:**

- US-010;
- US-011;
- US-014;
- US-016.

**Entrada:** evidências do M4 e gates aplicáveis.

**Saída:** capacidades condicionais aprovadas sem violar autoridade ERP, privacidade, ruído ou business case.

---

### M6 — Expansão comercial

**Objetivo:** expandir coorte de forma governada.

**Entrada:** `GAT-011`.

**Sequência:**

```text
Onda 2
→ mais vendedores + segundo gerente

NOVA EVIDÊNCIA
↓
Onda 3
→ 18 vendedores + gestores
```

Expansão não é consequência automática de deploy.

---

## 18. Gate de entrada e saída por marco

| Marco | Entrada | Saída principal |
| --- | --- | --- |
| M0 | baseline aprovada para planejamento | subgates fundacionais correspondentes |
| M1 | GAT-001 | core CRM vertical comprovável em staging |
| M2 | GAT-001/002/003 | GAT-004 + jornada cliente/ERP estável |
| M3 | M1/M2 + GAT-004/005/006 | piloto tecnicamente pronto |
| M4 | M3 | GAT-007/008/009/010 avaliados |
| M5 | M4 saudável | P0 condicionado aceito |
| M6 | GAT-011 | expansão por coorte e nova evidência |

---

## 19. Modelo operacional de status

Quando o tracker for publicado:

```text
Backlog
Ready
In Progress
Blocked
Review
Done
Superseded
Removed
```

No momento:

```text
FND-* = PLANNED
US-* = CANONICAL / NOT AUTHORIZED
GAT-* = DEFINED
ISSUES = NOT PUBLISHED
```

O primeiro item lógico do caminho crítico é `FND-001`, mas ele não está `READY_FOR_CODEX`.

---

## 20. Definition of Ready do item

Antes de um item entrar em `Ready`, precisa possuir quando aplicável:

- objetivo observável;
- fonte canônica;
- escopo;
- fora de escopo;
- dependências;
- gate;
- aceite;
- NFRs;
- dados e autoridade;
- risco;
- ambiente;
- evidência esperada;
- rollout;
- rollback;
- condição de parada;
- owner;
- executor permitido.

Para IA, deve existir ainda:

- recorte explícito;
- invariantes;
- verificações;
- proibições;
- stop conditions.

---

## 21. Definition of Done do item

`Done` exige evidência proporcional ao risco.

Quando aplicável:

### Produto

- comportamento e aceite cumpridos;
- regra preservada;
- guardrails avaliados.

### Código

- implementação revisável;
- tipos/contratos adequados;
- boundaries preservados;
- review concluído.

### Testes

- camadas adequadas;
- casos negativos;
- retry/falha;
- flakiness tratada.

### UX/A11y

- estados;
- teclado/toque;
- foco;
- zoom;
- leitor/semântica quando aplicável;
- aceite humano quando requerido.

### Dados/API

- autoridade;
- autorização;
- idempotência;
- compatibilidade;
- migration.

### Segurança/privacidade

- threat model quando necessário;
- segredo protegido;
- minimização;
- abuso relevante testado.

### Operação

- observabilidade;
- rollback;
- runbook quando material;
- hosted evidence.

### Documentação

- fonte superior reconciliada se a realidade mudou.

Regra:

```text
MERGED
!=
DONE
```

---

## 22. Exemplo de contrato executável — US-006

```text
ID: US-006
TÍTULO: Registrar interação
TIPO: Story
ÉPICO: E-003
MARCO: M1

OBJETIVO:
permitir que o vendedor preserve o resultado de um contato
com esforço proporcional ao valor gerado.

FONTES:
US-006
BR-008
OUT-001
J-002
UX-JRN-002
CRM-UX-04

DEPENDÊNCIAS:
GAT-001
identidade
persistência CRM

ACEITE:
- registro possui autor e momento;
- não exige campos sem finalidade clara;
- retry não duplica;
- falha recuperável não apaga trabalho válido;
- sucesso usa feedback proporcional;
- fluxo preserva contexto útil.

NFRs:
NFR-001
NFR-004
NFR-005
NFR-006
NFR-007
NFR-009

EVIDÊNCIA:
unit
integration
component
E2E staging
a11y
human UX acceptance

PARAR SE:
- nova regra comercial for necessária;
- dado Protheus passar a ser obrigatório sem contrato;
- autorização estiver indefinida;
- persistência exigir violar ADR/TDR;
- escopo extrapolar o item.
```

O exemplo demonstra o contrato esperado, mas não publica Issue.

---

## 23. Política para IA

```text
AI_POLICY:
IA PROPÕE
AUTOMAÇÃO VERIFICA
HUMANO RESPONDE
```

### Continuidade

```text
CONTINUITY_POLICY: MANUAL
```

Logo:

```text
ITEM DONE
↓
PRÓXIMO ITEM ELEGÍVEL
↓
AGUARDAR AUTORIZAÇÃO
```

Atos que exigem humano, salvo política posterior explicitamente aprovada:

- produção;
- dados reais;
- DNS;
- segredos;
- VPN;
- migrations materiais;
- aceite visual/UX;
- risco residual;
- mudança de escopo;
- ADR/TDR/IDR material;
- expansão de coorte;
- release produtivo.

O agente não pode:

- inventar API;
- inventar regra;
- escolher stack fora de TDR;
- alterar arquitetura sem ADR;
- criar recurso cloud não aprovado;
- usar dado real ou secret em prompt;
- marcar o próprio trabalho como aceito quando exige humano;
- avançar além do recorte autorizado.

---

## 24. Modelo futuro de Issues e Project

### Issue

Campos mínimos quando aplicáveis:

```text
ID
Tipo
Épico/Trilha
Marco
Objetivo
Escopo
Fora de escopo
Fontes canônicas
Dependências
Gates
Aceite
NFRs
Evidência
Risco
Rollout
Rollback
Condição de parada para IA
```

### Labels sugeridos

```text
type:story
type:foundation
type:correction
type:nfr
type:gate
type:experiment

priority:must
priority:must-gate
priority:should
priority:could

risk:security
risk:privacy
risk:data
risk:provider
risk:ux
risk:ops
```

### Project fields sugeridos

```text
ID
Status
Type
Epic
Priority
Milestone
Owner
Risk
Gate
Dependencies
Environment
Evidence State
```

Nenhum desses artefatos foi criado nesta etapa.

---

## 25. Evidências

Tipos possíveis conforme item:

- teste automatizado;
- teste manual;
- staging;
- browser/device real;
- CI run;
- SHA;
- migration result;
- PostgreSQL test;
- security scan;
- restore test;
- screenshot/vídeo quando apropriado;
- logs redigidos;
- dashboard;
- aceite humano;
- validação legal/comercial.

Evidência esperada é definida antes da execução.

Distinção:

```text
LOCAL
HOSTED
HUMAN
```

Deploy isolado não é aceite automático.

---

## 26. Controle de mudança da baseline

Quando execução revelar diferença material:

```text
BASELINE 1.0
↓
REALIDADE OBSERVADA
↓
CLASSIFICAR MUDANÇA
↓
ATUALIZAR FONTE RESPONSÁVEL
↓
RECONCILIAR ADR/TDR/IDR QUANDO NECESSÁRIO
↓
ATUALIZAR BACKLOG
↓
ATUALIZAR RASTREABILIDADE
↓
BASELINE 1.1
```

Classes:

- CORREÇÃO;
- APRENDIZADO;
- MUDANÇA DE ESCOPO;
- MUDANÇA UX/UI;
- MUDANÇA ARQUITETURAL;
- MUDANÇA DE STACK;
- MUDANÇA DE INFRA.

A descoberta sobre metadata Protheus demonstrou justamente esse mecanismo: nova evidência pode refinar camadas técnicas sem apagar a história da baseline anterior.

---

## 27. Brownfield

Não aplicável ao CRM simulado enquanto produto novo.

```text
BROWNFIELD_TRACKER: ABSENT
BROWNFIELD_CODEBASE: ABSENT
```

Se implementação futura já existir antes da próxima reconciliação, a etapa deverá inventariar código/issues reais em vez de presumir greenfield.

---

## 28. Pendências

Pontos ainda dependentes de futura realidade do projeto:

- owners humanos reais;
- conta/subscription real;
- domínio real;
- configuração real da VPN;
- release/customizações reais do Protheus;
- políticas reais de identidade corporativa;
- custos medidos;
- baseline operacional real do EXP-001;
- evidência real das POCs/FNDs;
- política final de retenção LGPD;
- contrato final de estoque/financeiro para US-010/US-011;
- algoritmo/regra validada para US-014.

Essas pendências possuem gate/momento de resolução e não impedem a auditoria da etapa 11.

---

## 29. Backlog Readiness

```text
BL-01 Coverage: PASS
BL-02 Identity: PASS
BL-03 Reconciliation: PASS
BL-04 Dependency: PASS
BL-05 Milestones: PASS
BL-06 Gates: PASS
BL-07 Item Contract: PASS
BL-08 NFR: PASS
BL-09 AI Safety: PASS
BL-10 Operations: PASS
BL-11 Change Control: PASS
BL-12 Handoff: PASS
```

Resultado:

```text
BACKLOG_METHOD_VALIDATION: PASS
PORTFOLIO_INVENTORY: COMPLETE
RECONCILIATION: COMPLETE
MILESTONES: DEFINED
DEPENDENCY_GRAPH: DEFINED
NFR_INHERITANCE: DEFINED
GATES: DEFINED
FIRST_LOGICAL_ITEM: FND-001
GITHUB_PUBLICATION: NOT_AUTHORIZED
BACKLOG_READINESS: SUFFICIENT
READY_FOR_CODEX: NO
```

---

## 30. Handoff para Matriz Operacional

A próxima etapa recebe:

```text
PORTFÓLIO
IDs
FONTES
DEPENDÊNCIAS
MARCOS
GATES
NFRs
EVIDÊNCIAS ESPERADAS
OWNERS POR PAPEL
STATUS MODEL
CHANGE CONTROL
```

E deve responder:

> **Existe uma ligação auditável e completa entre cada decisão relevante da baseline e a forma como ela será implementada, testada, evidenciada e acompanhada operacionalmente?**

A etapa 11 deve auditar lacunas; não redesenhar este backlog por preferência.

```text
BACKLOG_EXECUTION: COMPLETE
CLIENT_REVIEW: APPROVED_FOR_SIMULATION
BACKLOG_READINESS: SUFFICIENT
ISSUES_PUBLISHED: NO
PROJECT_CREATED: NO
READY_FOR_CODEX: NO
NEXT_STAGE: 11 — Matriz Operacional de Rastreabilidade
```

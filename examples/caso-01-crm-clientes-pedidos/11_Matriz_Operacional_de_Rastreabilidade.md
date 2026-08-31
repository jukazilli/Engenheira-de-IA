---
document_id: CASE-01-DOC-11
title: Matriz Operacional de Rastreabilidade — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: matriz-operacional-rastreabilidade
baseline_ref: 9a8b40ea535e277222909954a6aa7944a1e9ed9a
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
next_document: 12_Reconciliacao_da_Baseline_e_Handoff_para_Codex.md
traceability_readiness: SUFFICIENT_WITH_OPEN_ITEMS
ready_for_codex: false
---

# Matriz Operacional de Rastreabilidade — CRM para gestão de clientes e pedidos

## 1. Escopo e baseline

Esta matriz conecta as decisões materiais da baseline do Caso 01 ao backlog executável, às verificações esperadas e, futuramente, à implementação e às evidências reais.

```text
BASELINE_REF: 9a8b40ea535e277222909954a6aa7944a1e9ed9a
TRACEABILITY_STATUS: CANONICAL
IMPLEMENTATION_EXISTS: NO
ISSUES_EXIST: NO
PRS_EXIST: NO
ACTUAL_PROJECT_EVIDENCE_EXISTS: NO
```

A ausência de implementação é esperada neste greenfield.

```text
RASTREÁVEL
!=
IMPLEMENTADO
```

Nenhuma coluna de implementação, teste real, PR ou evidência é preenchida ficticiamente.

---

## 2. Convenções

### 2.1. Estados de disposição

- `MAPPED` — existe caminho explícito para disposição operacional;
- `CONTEXT_ONLY` — informação contextual, sem item próprio;
- `CONSOLIDATED` — decisão absorvida por fonte posterior de maior autoridade;
- `DEFERRED` — fora do horizonte atual, mas preservada;
- `BLOCKED` — exige gate ou evidência antes de avanço;
- `NEEDS_RECONCILIATION` — decisão material ainda precisa ser resolvida;
- `SUPERSEDED` — substituída de forma explícita;
- `NOT_APPLICABLE` — não aplicável ao horizonte atual.

### 2.2. Estados de trace

- `CURRENT` — coerente com a baseline atual;
- `STALE` — fonte ou relação mudou e precisa reconciliar;
- `CONFLICT` — fontes materiais incompatíveis;
- `PARTIAL` — relação conhecida, mas falta parte necessária à execução.

### 2.3. Evidência esperada versus evidência real

```text
EXPECTED_EVIDENCE
= prova definida antes da execução

ACTUAL_EVIDENCE
= prova observada depois da execução
```

As POCs do Tech Lead são evidências da **simulação metodológica**, não evidências do ambiente real do futuro CRM.

---

## 3. Cobertura documental

| Documento | Autoridade predominante | Disposição | Cobertura principal |
| --- | --- | --- | --- |
| `00_Discovery.md` | Discovery | `CONSOLIDATED / CONTEXT_ONLY` | dores, atores, contexto e restrições absorvidos pelas etapas posteriores |
| `01_Pesquisa_e_Viabilidade.md` | Pesquisa | `MAPPED` | build vs buy, business case, Protheus e riscos |
| `02_Briefing_de_Produto_e_Escopo.md` | Produto | `MAPPED` | escopo, P0/P1/P2 e contrato de produto |
| `03_Visao_de_Product_Owner.md` | Produto | `MAPPED` | OUT, HYP, BR, J, E, US, G e EXP |
| `Principios_de_UX_UI.md` | UX/UI | `MAPPED` | princípios transversais e específicos CRM |
| `04_Direcao_de_UI_e_Design_System.md` | UI | `MAPPED` | tese visual, tokens, superfícies e componentes |
| `05_Especificacao_de_UX.md` | UX | `MAPPED` | jornadas, estados, recuperação, validações e testes UX |
| `06_Tecnicas_de_Desenvolvimento.md` | Engenharia | `MAPPED` | práticas, segurança, testes, CI, DoR/DoD e IA |
| `07_Engenharia_e_Arquitetura.md` | Arquitetura | `MAPPED` | drivers, QA, domínios, ADRs e TECH-REQs |
| `Visao_do_Tech_Lead.md` | Tech Lead | `MAPPED` | TDRs, stack e POCs simuladas |
| `08_DevOps_e_Infraestrutura.md` | Infra | `MAPPED` | Azure, rede, ambientes, IDRs, backup e operação |
| `09_Plano_de_Fundacao.md` | Fundação | `MAPPED` | FND-001 a FND-042 e gates fundacionais |
| `10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md` | Operação | `MAPPED` | NFRs, GATs, DECs, marcos e sequenciamento |

```text
MATERIAL_DOCUMENTS_WITHOUT_DISPOSITION: 0
```

---

## 4. Matriz principal — produto

| Trace | Fonte | Item | UX/UI | Arquitetura/Tech | Gate | Verificação esperada | Evidência real | Disposição | Trace |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `TRACE-0001` | `OUT-001`, `J-001` | `US-001` | `UX-JRN-001`, `UI-SCR-001` | `ARCH-DOM-005` | `GAT-001` | UX-TST-001 + estados de prioridade | — | MAPPED | CURRENT |
| `TRACE-0002` | `OUT-004`, `J-002` | `US-002` | `UX-JRN-002`, `UI-SCR-002/003` | `ARCH-DOM-002/006`, `ADR-003` | `GAT-002` | busca + contrato ERP | — | MAPPED | CURRENT |
| `TRACE-0003` | `BR-004`, `BR-014` | `US-003` | descoberta controlada | `ADR-008` | `GAT-004` | acesso horizontal negativo | — | MAPPED | CURRENT |
| `TRACE-0004` | `BR-002`, `J-003` | `US-004` | `UX-JRN-003`, `UI-SCR-004` | `ADR-002`, `TDR-005/006` | `GAT-001` | duplicidade + idempotência | — | MAPPED | CURRENT |
| `TRACE-0005` | `OUT-001`, `OUT-002` | `US-005` | `UX-JRN-002`, `UI-SCR-003` | `ARCH-DOM-004` | `GAT-001` | continuidade de histórico | — | MAPPED | CURRENT |
| `TRACE-0006` | `BR-008` | `US-006` | `UX-JRN-002`, `UX-STA-002` | `ADR-002` | `GAT-001` | registro, retry, draft, a11y | — | MAPPED | CURRENT |
| `TRACE-0007` | `BR-009` | `US-007` | `UX-JRN-002` | `ARCH-DOM-004` | `GAT-001` | relógio controlado + vencimento | — | MAPPED | CURRENT |
| `TRACE-0008` | `OUT-004`, `OUT-005` | `US-008` | `UX-JRN-004` | `ADR-003/004/006`, `TDR-007` | `GAT-002` | contrato + freshness | — | MAPPED | CURRENT |
| `TRACE-0009` | `OUT-004`, `OUT-005` | `US-009` | `UX-JRN-004`, `UI-SCR-006` | `ADR-003/004/005/006` | `GAT-002` | contract + ERP failure | — | MAPPED | CURRENT |
| `TRACE-0010` | `OUT-004`, `OUT-005` | `US-010` | `UX-JRN-004` | `ADR-003/006` | P0 condicionado | estoque/freshness/escopo | — | BLOCKED | CURRENT |
| `TRACE-0011` | `BR-013` | `US-011` | `UX-JRN-004` | `ADR-008` | P0 condicionado | authz + minimização + freshness | — | BLOCKED | CURRENT |
| `TRACE-0012` | `OUT-001` | `US-012` | carteira | `ARCH-DOM-003` | `GAT-004` | ownership e listagem | — | MAPPED | CURRENT |
| `TRACE-0013` | `BR-005/006/007` | `US-013` | `UX-JRN-006` | `ADR-007/008/009` | `GAT-004` | conflito, autorização e auditabilidade | — | MAPPED | CURRENT |
| `TRACE-0014` | `HYP-004/007`, `BR-010` | `US-014` | `UX-JRN-001/005` | `ARCH-DOM-005` | M5 / evidência de produto | sinal x ruído | — | BLOCKED | CURRENT |
| `TRACE-0015` | `OUT-003` | `US-015` | `UX-JRN-005`, `UI-SCR-005` | `ARCH-DOM-007` | `GAT-004` | UX-TST-006 | — | MAPPED | CURRENT |
| `TRACE-0016` | `OUT-003/006` | `US-016` | gestão visual | `ARCH-DOM-007` | M5 | aceite gerencial sem dupla coleta | — | MAPPED | CURRENT |
| `TRACE-0017` | `OUT-002`, `BR-006` | `US-017` | `J-006` | `ARCH-DOM-003/008`, `ADR-009` | `GAT-004` | continuidade + audit trail | — | MAPPED | CURRENT |
| `TRACE-0018` | `BR-012`, `OUT-005` | `US-018` | `UX-STA-003…006` | `ADR-004/006`, `TDR-007` | `GAT-002` | QA-002/006 + UX-TST-004 | — | MAPPED | CURRENT |

---

## 5. Traces estruturais

### TRACE-0019 — Repositório, toolchain e CI

```text
06 Técnicas
↓
TDR-001 / TDR-002 / TDR-012
↓
FND-003…007
↓
GAT-001
↓
M1
```

**Verificação esperada:** clone limpo, install reproduzível, build/test/CI e branch protection.

### TRACE-0020 — Azure staging

```text
TECH-REQs operacionais
↓
IDR-001 / 002 / 003 / 007 / 008 / 010
↓
FND-008…017
↓
GAT-001
```

**Verificação esperada:** staging isolado, OIDC, secrets, banco, workloads, deploy e observabilidade.

### TRACE-0021 — Integração Protheus

```text
BR-001 / BR-011 / BR-012
↓
ARCH-DRV-001 / 002 / 007 / 011
↓
ADR-003 / 004 / 005 / 006
↓
TDR-007
↓
IDR-006
↓
FND-018…023
↓
GAT-002
↓
US-002 / 008 / 009 / 010 / 011 / 018
```

### TRACE-0022 — Metadata Protheus

```text
BR-001 / BR-011
↓
ADR-003
↓
TDR-007
↓
TL-POC-002 [simulada]
↓
DEC-002
↓
FND-020 / FND-021
↓
GAT-002
```

**Invariante:** `metadata cache CRM != autoridade do dicionário`.

**Verificação real futura:** tamanho 8 aceita 8/rejeita 9; alteração controlada para 10 é refletida sem hardcode CRM.

### TRACE-0023 — Banco próprio CRM

```text
BR-001
↓
ARCH-DRV-001
↓
ADR-002
↓
TDR-005 / TDR-006
↓
DEC-003
↓
FND-012 / FND-013
↓
GAT-003
```

**Invariante:** PostgreSQL persiste autoridade CRM; não transforma SA1/SC5/SC6 em segunda verdade canônica.

### TRACE-0024 — Autorização

```text
BR-004 / BR-005 / BR-007 / BR-013
↓
QA-001
↓
ADR-008
↓
TDR-008
↓
IDR-004 / IDR-007
↓
FND-026 / FND-027
↓
GAT-004
```

### TRACE-0025 — Backup e recuperação

```text
ARCH RPO/RTO
↓
IDR-011
↓
FND-024 / 025 / 035 / 041
↓
restore test
↓
evidência real futura
```

### TRACE-0026 — Build once / promote many

```text
06 Técnicas
↓
08 Infra
↓
IDR-008
↓
FND-015 / 016 / 038 / 039
↓
artifact digest
↓
rollback
```

### TRACE-0027 — Business case

```text
OUT-006
↓
HYP-ROI-001
↓
NFR-010
↓
FND-002 / FND-037
↓
GAT-010
↓
GAT-011
```

---

## 6. Herança de NFR

### TRACE-RULE-NFR-001 — Interfaces autenticadas

Todas as histórias visíveis autenticadas herdam, conforme materialidade:

- `NFR-001 — Acessibilidade`;
- `NFR-002 — Autorização e privacidade de carteira` quando houver controle de acesso;
- `NFR-006 — Minimização e proteção de dados`;
- `NFR-009 — Observabilidade e operabilidade` quando material.

### TRACE-RULE-NFR-002 — Escritas do domínio CRM

Itens que criam ou alteram estado relevante herdam:

- `NFR-004 — Idempotência e concorrência`;
- `NFR-005 — Auditabilidade` quando material;
- `NFR-007 — Recuperabilidade e conectividade`;
- `NFR-008 — Compatibilidade e migrations` quando schema/contrato for afetado.

### TRACE-RULE-NFR-003 — Dados Protheus

Histórias que apresentam dado ERP herdam:

- `NFR-003 — Autoridade e confiança Protheus`;
- `NFR-006 — Minimização`;
- `NFR-007 — Resiliência`;
- `NFR-009 — Observabilidade`.

A herança é `APPLIES_BY_RULE`; não duplica o texto do NFR em cada Issue futura.

---

## 7. Matriz de gates

| Gate | Owner por papel | Estado atual | Condição resumida | Bloqueia |
| --- | --- | --- | --- | --- |
| `GAT-001` | Tech Lead + Infra | OPEN | staging core fundacional verificado | M1 |
| `GAT-002` | TI Protheus + Tech Lead | OPEN | VPN + homologação + metadata + read contracts + degradação | M2 ERP |
| `GAT-003` | Arquitetura + Tech Lead | OPEN | autoridade CRM x ERP preservada | snapshots/modelos ERP |
| `GAT-004` | PO + segurança/negócio | OPEN | isolamento de carteira comprovado | piloto |
| `GAT-005` | owner humano production | OPEN | staging suficiente + autorização humana | production |
| `GAT-006` | owner dados/privacidade | OPEN | política e autorização para dado real | dados reais |
| `GAT-007` | PO + gerente | OPEN | sem dupla operação relevante | expansão |
| `GAT-008` | PO | OPEN | adoção operacional | expansão |
| `GAT-009` | gerente + PO | OPEN | abandono de controles paralelos | expansão |
| `GAT-010` | sponsor/diretor | OPEN | business case saudável | continuidade |
| `GAT-011` | PO + sponsor | OPEN | gates de piloto saudáveis | M6 |

Nenhum gate é fechado por evidência simulada.

---

## 8. Matriz de marcos

| Marco | Objetivo | Itens principais | Gate de saída / evidência | Estado |
| --- | --- | --- | --- | --- |
| M0 | fundação | `FND-001…042` | staging, Protheus e production gates conforme corte | PLANNED |
| M1 | continuidade comercial mínima | `US-004`, `US-006`, `US-007`, `US-001` | jornada vertical em staging | PLANNED |
| M2 | cliente, carteira e Protheus | `US-002/003/005/008/009/012/013/017/018` | `GAT-004` + evidência ERP | PLANNED |
| M3 | pilot ready | core M1/M2 + `US-015` | production foundation + real data authorization | PLANNED |
| M4 | piloto e aprendizado | `EXP-003`, `EXP-004` | `GAT-007/008/009/010` | PLANNED |
| M5 | P0 condicionado | `US-010/011/014/016` | evidências/gates específicos | PLANNED |
| M6 | expansão | Onda 2 e depois Onda 3 | `GAT-011` | PLANNED |

---

## 9. POCs simuladas e evidência real

POCs canônicas do Tech Lead:

- `TL-POC-001` — PostgreSQL/Prisma;
- `TL-POC-002` — metadata Protheus;
- `TL-POC-003` — read contract ERP;
- `TL-POC-004` — degradação Protheus;
- `TL-POC-005` — OIDC/session model;
- `TL-POC-006` — OpenAPI/codegen;
- `TL-POC-007` — capacidade web/a11y.

Classificação nesta matriz:

```text
EVIDENCE_CLASS: SIMULATED_METHOD_EVIDENCE
```

Elas suportam a coerência da baseline do caso simulado.

Não fecham automaticamente `FND-*`, `GAT-*` ou evidência de ambiente real.

```text
SIMULATED_POC_PASS
!=
REAL_FOUNDATION_EVIDENCE
```

---

## 10. Implementação e PRs

Estado greenfield atual:

```text
ISSUES: 0
PRS: 0
FUNCTIONAL_COMMITS: 0
REAL_MIGRATIONS: 0
CRM_DEPLOYMENTS: 0
REAL_TESTS: 0
REAL_EVIDENCE: 0
```

Logo:

```text
ORPHAN_IMPLEMENTATIONS: 0
ITEMS_DONE_WITHOUT_EVIDENCE: 0
```

Não existe implementação funcional para auditar nesta etapa.

---

## 11. Verificação esperada

A prova deve ser definida antes da execução.

Exemplos principais:

### US-006 — Registrar interação

- unit/domain: regra de registro e autoria;
- integration: persistência e transação;
- idempotency: mesma intenção não duplica;
- UX/component: feedback e rascunho;
- E2E staging: registrar contato → próxima ação;
- accessibility: teclado/foco/semântica;
- human acceptance: fricção proporcional.

### US-013 — Transferir responsabilidade

- authorization negative tests;
- optimistic concurrency/conflict;
- audit record;
- history preservation;
- E2E gerencial;
- human acceptance da consequência.

### Protheus boundary

- contract tests;
- timeout/unavailable;
- stale/freshness;
- metadata contract;
- metadata-driven validation;
- observabilidade sem payload sensível.

### Backup / restore

- backup/PITR existente;
- restore isolado;
- smoke pós-restore;
- RPO/RTO medidos.

---

## 12. Itens abertos rastreados

### OPEN-TRACE-001 — Política de retenção LGPD

```text
STATUS: NEEDS_RECONCILIATION_BEFORE_REAL_DATA
LINKS: NFR-006, GAT-006
```

Nenhum prazo é inventado nesta baseline.

### OPEN-TRACE-002 — Mapeamento do Protheus real

Faltam no projeto real:

- release exato;
- customizações;
- endpoints;
- autenticação;
- empresa/filial;
- payloads reais.

Disposição:

```text
EXP-002
+
FND-019…023
+
GAT-002
```

### OPEN-TRACE-003 — Estoque e financeiro

`US-010` e `US-011` estão `MAPPED / GATED`.

Detalhe definitivo só é permitido quando contratos e autorização forem suficientes.

### OPEN-TRACE-004 — Algoritmo de atenção

`US-014` permanece ligado a `HYP-004`, `HYP-007`, `BR-010`.

```text
DISPOSITION: BLOCKED_BY_PRODUCT_EVIDENCE
```

Nenhum prazo universal de dias é inventado.

### OPEN-TRACE-005 — Owners reais

A simulação usa owners por papel.

`FND-001` deve materializar nomes/contas reais antes da execução.

---

## 13. Órfãos e conflitos

Auditoria desta baseline:

```text
MATERIAL_ORPHAN_REQUIREMENTS: 0
ORPHAN_IMPLEMENTATIONS: 0
CRITICAL_TRACE_CONFLICTS: 0
DONE_WITHOUT_EVIDENCE: 0
STALE_TRACES: 0
BROKEN_CRITICAL_REFERENCES: 0
```

Os `OPEN-TRACE-*` não são órfãos porque possuem disposição, owner por papel ou gate e momento de resolução.

---

## 14. Forward trace demonstrado — transferência de carteira

```text
OUT-002
↓
BR-005 / BR-006 / BR-007
↓
J-006
↓
US-013
↓
UX-JRN-006
↓
ARCH-DOM-003
↓
QA-004 / QA-005
↓
ADR-007 / ADR-008 / ADR-009
↓
TDR-005 / TDR-006 / TDR-008
↓
FND-012 / 013 / 026 / 027
↓
GAT-004
↓
M2
↓
EXPECTED TESTS
concorrência + autorização + auditabilidade + UX
↓
ACTUAL EVIDENCE
—
```

---

## 15. Forward trace demonstrado — metadata Protheus

```text
BR-001 / BR-011
↓
ARCH-DRV-001 / ARCH-DRV-011
↓
ADR-003
↓
TDR-007
↓
TL-POC-002 [simulada]
↓
DEC-002
↓
FND-020 / FND-021
↓
GAT-002
↓
US dependentes de campos Protheus
↓
EXPECTED VERIFICATION
metadata 8 → 9 rejeitado
metadata 10 → 10 aceito sem hardcode
↓
ACTUAL EVIDENCE
—
```

---

## 16. Backward trace futuro

Quando existir PR real, a matriz deverá permitir percurso inverso.

Exemplo ilustrativo, não evidência atual:

```text
PR #51
↑
US-006
↑
TRACE-0006
↑
UX-JRN-002
↑
BR-008
↑
OUT-001
↑
03_Visao_de_Product_Owner.md
```

Se o percurso não puder ser feito:

```text
TRACE_GAP
```

---

## 17. Política de atualização da matriz

Revisar rastreabilidade quando ocorrer:

- `ISSUE_READY`;
- `PR_OPENED`;
- `PR_MERGED`;
- `STAGING_DEPLOYED`;
- `GATE_ACCEPTED`;
- `CORRECTION_OPENED`;
- `ADR_CHANGED`;
- `TDR_CHANGED`;
- `IDR_CHANGED`;
- `BASELINE_CHANGED`;
- `RELEASED`.

Automação pode identificar relações ou referências quebradas, mas não inventa semântica.

---

## 18. Condições de parada para agentes

Um agente deve parar quando:

- item não possuir fonte;
- duas fontes materiais conflitarem;
- gate estiver fechado;
- tecnologia necessária não estiver aprovada;
- nova dependência estrutural for necessária;
- boundary precisar mudar;
- critério de aceite estiver ambíguo;
- evidência depender de decisão humana;
- secret não autorizado for necessário;
- dado real for necessário fora do gate;
- o trace relevante estiver stale.

---

## 19. Gates da etapa 11

| Gate metodológico | Resultado |
| --- | --- |
| TRACE-01 Inventário | PASS |
| TRACE-02 Cobertura | PASS |
| TRACE-03 Backlog | PASS |
| TRACE-04 Arquitetura | PASS |
| TRACE-05 Tecnologia | PASS |
| TRACE-06 Infra | PASS |
| TRACE-07 UX/UI | PASS |
| TRACE-08 Verificação esperada | PASS |
| TRACE-09 Evidência | PASS / NOT_APPLICABLE_YET — nenhum item está Done |
| TRACE-10 Gates | PASS |
| TRACE-11 Órfãos | PASS |
| TRACE-12 Freshness | PASS |

---

## 20. Métricas de cobertura

Não foi usada porcentagem artificial de cobertura.

Contadores atuais:

```text
MATERIAL_ORPHAN_REQUIREMENTS: 0
ORPHAN_IMPLEMENTATIONS: 0
CRITICAL_CONFLICTS: 0
STALE_TRACES: 0
DONE_WITHOUT_EVIDENCE: 0
OPEN_TRACKED_ITEMS: 5
```

`100% de links` não seria tratado como prova de qualidade semântica.

---

## 21. Traceability Readiness

```text
TRACEABILITY_METHOD_VALIDATION: PASS

FORWARD_TRACE: PASS
BACKWARD_TRACE_MODEL: PASS
DOCUMENT_COVERAGE: PASS
NFR_INHERITANCE: PASS
FOUNDATION_TRACE: PASS
ARCHITECTURE_TRACE: PASS
TECH_TRACE: PASS
INFRA_TRACE: PASS
PRODUCT_TRACE: PASS
ORPHAN_DETECTION: PASS
NO_FAKE_EVIDENCE: PASS

TRACEABILITY_READINESS:
SUFFICIENT_WITH_OPEN_ITEMS

READY_FOR_CODEX:
NO
```

`SUFFICIENT_WITH_OPEN_ITEMS` é adequado porque ainda existem itens não implementados e gates abertos, mas sua disposição é conhecida e nenhuma lacuna material de origem impede a reconciliação final.

---

## 22. Handoff para reconciliação final

A etapa 12 recebe:

```text
BASELINE_REF
COBERTURA DOCUMENTAL
BACKLOG CANÔNICO
TRACE IDS
GATES
OPEN-TRACE ITEMS
CONFLITOS = 0
ÓRFÃOS MATERIAIS = 0
EXPECTED EVIDENCE
ACTUAL EVIDENCE = NONE YET
TRACEABILITY_READINESS = SUFFICIENT_WITH_OPEN_ITEMS
```

A próxima etapa deve decidir se existe um recorte **executável sem invenção**, distinguir baseline tecnicamente pronta de autorização humana e produzir o contrato de handoff ao Codex.

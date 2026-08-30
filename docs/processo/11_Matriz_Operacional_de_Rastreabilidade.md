---
document_id: PROCESS-11-MATRIZ-RASTREABILIDADE
title: Matriz Operacional de Rastreabilidade
status: draft-methodology
version: 0.1.0
stage: matriz-operacional-rastreabilidade
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
produces: 11_Matriz_Operacional_de_Rastreabilidade.md
next_stage: 12_Reconciliacao_da_Baseline_e_Handoff_para_Codex.md
---

# 11 — Matriz Operacional de Rastreabilidade

## 1. Propósito

A **Matriz Operacional de Rastreabilidade** prova que a baseline do projeto pode ser percorrida nos dois sentidos:

```text
INTENÇÃO
    ↓
DECISÃO
    ↓
REQUISITO
    ↓
ITEM EXECUTÁVEL
    ↓
IMPLEMENTAÇÃO
    ↓
TESTE
    ↓
EVIDÊNCIA
```

E também:

```text
COMMIT / PR / DEPLOYMENT / TESTE
    ↑
ITEM EXECUTÁVEL
    ↑
REQUISITO
    ↑
DECISÃO
    ↑
FONTE CANÔNICA
```

A pergunta central desta etapa é:

> **Conseguimos provar, sem depender de memória ou interpretação oral, de onde veio cada trabalho executável, o que ele precisa preservar, como será validado e qual evidência demonstra que a intenção original foi atendida?**

Esta etapa não existe para duplicar o backlog.

Ela existe para **conectar as camadas**.

A saída deve permitir responder perguntas como:

- qual decisão originou esta Issue?
- quais regras e jornadas esta entrega implementa?
- qual ADR, TDR ou IDR condiciona este item?
- quais NFRs se aplicam?
- qual gate impede avanço?
- quais testes provam a entrega?
- qual evidência encerrou o item?
- qual requisito fica sem implementação?
- qual código existe sem requisito conhecido?
- qual documento precisa ser reaberto se uma mudança for necessária?

A matriz não substitui nenhuma fonte anterior.

Ela funciona como **índice de ligação e cobertura**.

---

## 2. Formato canônico obrigatório

O artefato canônico desta etapa é **Markdown**.

```text
11_Matriz_Operacional_de_Rastreabilidade.md
```

Não utilizar planilha Excel como fonte canônica desta etapa.

Ferramentas tabulares podem ser usadas temporariamente para:

- análise;
- importação;
- transformação;
- conferência;
- geração automática;

mas o resultado persistente da metodologia deve ser `.md` versionado junto das demais documentações.

A razão é estrutural:

```text
MARKDOWN
↓
versionável por Git
↓
diff legível
↓
revisão por PR
↓
referência direta por agentes
↓
mesma linguagem documental do processo
```

Enquanto uma planilha binária tende a dificultar:

- diff humano;
- revisão granular;
- citação estável;
- leitura por agentes;
- resolução de conflitos;
- auditoria de mudanças.

Regra:

> **Se uma visão tabular for necessária, ela deve ser expressa como tabela Markdown ou seção Markdown derivada da fonte canônica.**

---

## 3. Origem desta etapa na reconstrução da metodologia

No processo utilizado como evidência prática, a função desta etapa foi materializada em uma planilha operacional com visões separadas para:

- visão geral;
- backlog canônico;
- rastreabilidade;
- marcos;
- gates;
- decisões;
- métricas;
- labels;
- preparação de Issues.

A reconstrução preserva as capacidades que se provaram úteis, mas redistribui responsabilidades.

O documento 10 já é responsável por:

- backlog canônico;
- taxonomia dos itens;
- prioridades;
- marcos;
- modelo operacional;
- DoR/DoD;
- regras de publicação.

O documento 11 passa a ser responsável principalmente por:

```text
COBERTURA
+
LIGAÇÃO ENTRE CAMADAS
+
PROVA DE IMPLEMENTAÇÃO
+
PROVA DE VALIDAÇÃO
+
AUDITORIA DA BASELINE
```

Assim evitamos que a Matriz vire uma segunda cópia completa do backlog.

---

## 4. Posição no processo

```text
00 Discovery
        ↓
01 Pesquisa e Viabilidade
        ↓
02 Briefing de Produto e Escopo
        ↓
03 Visão de Product Owner
        ↓
Princípios de UX/UI
        ↓
04 Direção de UI e Design System
        ↓
05 Especificação de UX
        ↓
06 Técnicas de Desenvolvimento
        ↓
07 Engenharia e Arquitetura
        ↓
Visão do Tech Lead
        ↓
08 DevOps e Infraestrutura
        ↓
09 Plano de Fundação
        ↓
10 Backlog Canônico
        ↓
11 MATRIZ OPERACIONAL DE RASTREABILIDADE
        ↓
12 Reconciliação da Baseline e Handoff para Codex
```

O documento 10 responde:

> **O que será executado, em qual ordem, sob quais critérios?**

O documento 11 responde:

> **Como provamos que cada item está conectado às decisões corretas e que nenhuma obrigação da baseline desapareceu entre documentação e execução?**

---

## 5. Regra fundamental

```text
RASTREÁVEL
≠
IMPLEMENTADO
```

Um requisito pode estar perfeitamente rastreado e ainda estar:

- Backlog;
- Blocked;
- Deferred;
- Removed;
- Not Applicable;
- aguardando gate.

Da mesma forma:

```text
IMPLEMENTADO
≠
RASTREÁVEL
```

Código funcionando sem origem conhecida é dívida de governança.

A matriz precisa mostrar ambos os problemas.

---

## 6. Tipos de rastreabilidade

A metodologia exige pelo menos quatro dimensões.

### 6.1. Rastreabilidade de origem

```text
FONTE
→ requisito / decisão / regra
→ item executável
```

Pergunta:

> Por que este trabalho existe?

### 6.2. Rastreabilidade de realização

```text
ITEM EXECUTÁVEL
→ código / migration / configuração / conteúdo / infraestrutura
```

Pergunta:

> Onde este trabalho foi materializado?

### 6.3. Rastreabilidade de verificação

```text
ITEM EXECUTÁVEL
→ teste / inspeção / POC / gate
→ evidência
```

Pergunta:

> Como sabemos que está correto?

### 6.4. Rastreabilidade de mudança

```text
MUDANÇA OBSERVADA
→ requisito afetado
→ fonte de autoridade
→ itens impactados
→ testes impactados
→ nova evidência
```

Pergunta:

> Se isso mudar, o que precisa ser reconciliado?

---

## 7. Rastreabilidade bidirecional

Uma matriz madura deve funcionar para frente e para trás.

### 7.1. Forward trace

```text
BR-021
↓
UX-FLOW-008
↓
ARCH-DRV-004
↓
ADR-006
↓
TECH-REQ-012
↓
TDR-004
↓
INFRA-REQ-007
↓
FND-031
↓
US-014
↓
PR #42
↓
TEST-087
↓
EVID-052
```

### 7.2. Backward trace

Dado:

```text
commit abc123
```

precisamos conseguir descobrir:

```text
qual PR?
qual item?
qual requisito?
qual regra?
qual jornada?
qual decisão?
qual fonte?
```

Se não for possível responder, existe uma lacuna.

---

## 8. Unidades rastreáveis

A matriz deve reconhecer os IDs definidos pelas etapas anteriores.

Exemplos:

```text
DOC-xxx
OUT-xxx
HYP-xxx
BR-xxx
J-xxx
UX-FLOW-xxx
UI-DEC-xxx
UI-CMP-xxx
UI-SCR-xxx
ARCH-DRV-xxx
QA-xxx
ARCH-DOM-xxx
ARCH-INV-xxx
ADR-xxx
TECH-REQ-xxx
TDR-xxx
TL-DEC-xxx
INFRA-REQ-xxx
IDR-xxx
FND-xxx
FND-GAT-xxx
E...
US-xxx
COR-xxx
NFR-xxx
GAT-xxx
EXP-xxx
P1-xxx
P2-xxx
```

Nem todo projeto usará todos os tipos.

Não inventar IDs apenas para preencher a matriz.

---

## 9. `TRACE-xxx`

A própria matriz pode utilizar um identificador estável por linha lógica:

```text
TRACE-0001
TRACE-0002
TRACE-0003
```

O Trace ID identifica a **relação rastreável**, não o requisito.

Exemplo:

```text
TRACE-0042
SOURCE: BR-021
WORK_ITEM: US-014
TEST: TEST-087
EVIDENCE: EVID-052
```

Se uma mesma regra alimenta três itens diferentes, podem existir três traces.

---

## 10. Matriz principal

A visão mínima recomendada é:

| Trace | Fonte | Referência | Requisito / decisão | Item | Arquitetura / tecnologia | Gate | Verificação | Evidência | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TRACE-001 | DOC-03 | BR-021 | publicação exige confirmação | US-014 | ADR-006 / TDR-004 | GAT-003 | TEST-087 | EVID-052 | VERIFIED |

A tabela real deve usar apenas colunas necessárias ao projeto.

Entretanto, as seguintes informações não podem desaparecer:

```text
ORIGEM
O QUE
ONDE EXECUTA
O QUE BLOQUEIA
COMO PROVAR
QUAL EVIDÊNCIA
QUAL ESTADO
```

---

## 11. Matriz de cobertura documental

Além da matriz principal, o artefato deve possuir uma visão de cobertura das fontes.

Exemplo:

| Trace | Documento | Seção / ID | Autoridade | Cobertura | Disposição | Nota |
| --- | --- | --- | --- | --- | --- | --- |
| TRACE-D03-021 | DOC-03 | BR-021 | produto | US-014, GAT-003 | MAPPED | detalhe permanece na fonte |

Esta visão responde:

> **Existe alguma parte material da documentação que não possui disposição explícita?**

---

## 12. Estados de disposição

Toda unidade relevante encontrada nas fontes deve receber uma disposição explícita.

Vocabulário recomendado:

```text
MAPPED
CONTEXT_ONLY
CONSOLIDATED
DEFERRED
BLOCKED
SUPERSEDED
REMOVED
NOT_APPLICABLE
RESEARCH_ONLY
DUPLICATE_OF:<ID>
NEEDS_RECONCILIATION
```

Nunca deixar célula lógica vazia para significar:

```text
“não sabemos”
```

Se não sabemos:

```text
NEEDS_RECONCILIATION
```

---

## 13. Cobertura não exige uma Issue para cada heading

Um erro comum seria transformar cada título documental em Issue.

Exemplo:

```text
DOC:
## Contexto de mercado
```

não precisa necessariamente produzir:

```text
US-044
Implementar contexto de mercado
```

Pode ter disposição:

```text
CONTEXT_ONLY
```

Outro exemplo:

```text
## Regra de revogação
```

pode estar coberta por:

```text
BR-018
+ US-023
+ NFR-014
+ GAT-006
```

A matriz existe para provar cobertura, não para multiplicar tarefas.

---

## 14. Nível de granularidade

A granularidade deve permitir encontrar uma decisão material sem produzir milhares de linhas inúteis.

Normalmente rastrear:

- headings com decisão;
- regras de negócio;
- jornadas;
- requisitos funcionais;
- requisitos não funcionais;
- atributos de qualidade;
- invariantes;
- ADRs;
- TDRs;
- IDRs;
- gates;
- hipóteses críticas;
- riscos materiais;
- itens de fundação;
- itens executáveis.

Não é obrigatório rastrear frases meramente explicativas.

---

## 15. Matriz item → implementação

Para itens em execução ou concluídos, registrar a materialização.

Exemplo:

| Item | Issue | Branch / PR | Artefatos | Testes | Ambiente | Evidência | Estado |
| --- | --- | --- | --- | --- | --- | --- | --- |
| US-014 | #42 | PR #51 | `src/...`, migration X | TEST-087 | staging | EVID-052 | VERIFIED |

`Artefatos` pode apontar para:

- arquivos de código;
- packages;
- migrations;
- contracts;
- config;
- workflows;
- IaC;
- runbooks;
- assets;
- documentação operacional.

Não precisa listar cada arquivo alterado se o PR já é uma referência confiável.

---

## 16. Matriz item → testes

Testes também precisam ser rastreáveis.

Exemplo:

```text
US-014
↓
AC-01
↓
TEST-087 unit
TEST-088 contract
TEST-089 E2E
TEST-090 manual staging
```

Uma história pode possuir vários tipos de prova.

---

## 17. IDs de teste

Quando o projeto precisar de alta rastreabilidade, utilizar:

```text
TEST-xxx
```

ou IDs mais específicos:

```text
UT-xxx
CT-xxx
IT-xxx
E2E-xxx
SEC-xxx
A11Y-xxx
OPS-xxx
```

O objetivo não é burocratizar cada assertion.

O ID deve representar um cenário de prova relevante.

---

## 18. Evidências

Evidência é a prova observável produzida depois da execução.

Pode incluir:

- SHA;
- PR;
- run de CI;
- deployment;
- migration aplicada;
- resultado de teste;
- captura de staging;
- teste em device real;
- relatório de acessibilidade;
- restore executado;
- aprovação humana;
- relatório de segurança;
- métrica pós-rollout;
- decisão de gate.

Quando útil, usar IDs:

```text
EVID-xxx
```

---

## 19. Evidência não pode ser uma promessa

Não registrar:

```text
EVIDÊNCIA:
“os testes deverão passar”
```

Isso é **evidência esperada**, não evidência real.

Distinguir:

```text
EXPECTED_EVIDENCE
ACTUAL_EVIDENCE
```

Exemplo:

```text
EXPECTED
restore smoke com dados sintéticos

ACTUAL
run #8921
restore concluído em 17 min
integridade verificada
```

---

## 20. Maturidade da evidência

Estados recomendados:

```text
NONE
EXPECTED
LOCAL
CI_VERIFIED
STAGING_VERIFIED
HUMAN_ACCEPTED
PRODUCTION_OBSERVED
```

Nem todo item precisa chegar a `PRODUCTION_OBSERVED` para ser Done.

Isso depende do contrato do item.

---

## 21. Status de rastreabilidade

Separar status do backlog de status da relação.

Um item pode estar:

```text
US-014 STATUS = IN_PROGRESS
```

Enquanto sua rastreabilidade pode estar:

```text
TRACE_STATUS = COMPLETE
```

Vocabulário sugerido:

```text
TRACE_COMPLETE
TRACE_PARTIAL
TRACE_MISSING_SOURCE
TRACE_MISSING_ITEM
TRACE_MISSING_TEST
TRACE_MISSING_EVIDENCE
TRACE_CONFLICT
TRACE_STALE
```

---

## 22. Cobertura para frente

Pergunta:

> Tudo que precisa gerar trabalho possui destino?

Auditar, por exemplo:

```text
BR sem US/FND/NFR/GAT
Jornada sem item
ADR sem TECH-REQ ou implementação
TECH-REQ obrigatório sem TDR
INFRA-REQ obrigatório sem IDR/FND
FND sem backlog
Gate sem item afetado
```

Nem toda ausência é erro.

Mas toda ausência precisa ser explicada.

---

## 23. Cobertura para trás

Pergunta:

> Tudo que será executado possui origem legítima?

Auditar:

```text
Issue sem fonte
PR sem item
migration sem requisito
provider sem IDR
biblioteca estruturante sem TDR
NFR criado apenas dentro da Issue
feature flag sem módulo/gate
telemetria sem catálogo autorizado
```

Esses casos são especialmente importantes em desenvolvimento assistido por IA.

---

## 24. Código órfão

Código órfão é implementação relevante sem origem rastreável.

Exemplo:

```text
nova tabela
+
novo endpoint
+
novo botão
```

sem:

```text
US
FND
COR
NFR
ou decisão autorizada
```

Deve ser classificado como:

```text
ORPHAN_IMPLEMENTATION
```

até reconciliação.

Não canonizar automaticamente o código como requisito.

---

## 25. Requisito órfão

Requisito órfão é obrigação aprovada sem disposição operacional.

Exemplo:

```text
BR-033
“revogação deve ser imediata”
```

mas nenhum:

```text
US
NFR
Gate
Teste
```

cobre o comportamento.

Classificação:

```text
ORPHAN_REQUIREMENT
```

Isso bloqueia baseline reconciliada quando material.

---

## 26. Gates na matriz

A matriz deve mostrar quais gates se aplicam a cada item material.

Exemplo:

| Item | Gate | Condição | Owner | Estado | Evidência |
| --- | --- | --- | --- | --- | --- |
| US-020 | GAT-004 | moderação aprovada | Trust & Safety | BLOCKED | — |

Regra:

```text
FLAG
≠
GATE
```

Feature flag controla exposição.

Gate autoriza avanço.

---

## 27. Dependências

A matriz deve permitir distinguir:

```text
DEPENDÊNCIA DE ENTREGA
DEPENDÊNCIA DE DECISÃO
DEPENDÊNCIA EXTERNA
DEPENDÊNCIA DE GATE
DEPENDÊNCIA DE DADO
DEPENDÊNCIA DE INFRA
```

Exemplo:

```text
US-014
DEPENDS_ON:
FND-022
GAT-003
PROVIDER_APPROVAL
```

Não esconder dependência externa dentro de `In Progress`.

---

## 28. Estado `Blocked`

Para toda relação bloqueada registrar:

- causa;
- owner;
- próxima ação;
- condição de retomada;
- itens afetados.

Exemplo:

```text
BLOCKED_BY:
licença do provider

OWNER:
Produto + Jurídico

NEXT_ACTION:
validar contrato comercial

RESUME_WHEN:
uso comercial confirmado
```

---

## 29. Rastreabilidade de NFR

NFRs raramente pertencem a uma única história.

A matriz precisa permitir:

```text
NFR-003
→ US-001
→ US-005
→ US-007
→ FND-013
→ Release M1
```

Não duplicar o texto do NFR em todas as Issues.

As Issues referenciam a fonte.

---

## 30. Herança de NFR

Pode existir uma regra de herança.

Exemplo:

```text
TODAS AS HISTÓRIAS AUTENTICADAS
HERDAM:
NFR-SEC-01
NFR-A11Y-01
NFR-OBS-01
```

A matriz pode registrar:

```text
APPLIES_BY_RULE
```

em vez de gerar dezenas de linhas manuais idênticas.

A regra de herança precisa ser explícita e auditável.

---

## 31. Rastreabilidade de arquitetura

Uma decisão arquitetural durável precisa ter caminho até execução.

Exemplo:

```text
ARCH-DRV-004
↓
QA-003
↓
ADR-006
↓
TECH-REQ-012
↓
TDR-004
↓
FND-017
↓
US-009
↓
TEST-044
```

Se o ADR não possui consequência operacional alguma, verificar se ele é realmente necessário.

---

## 32. Rastreabilidade de tecnologia

Uma escolha tecnológica estrutural deve apontar para:

```text
TECH-REQ
↓
TDR
↓
TL-DEC
↓
package / runtime / engine
↓
FND ou item de implementação
```

Isso permite responder:

> Qual requisito justifica esta dependência?

---

## 33. Rastreabilidade de infraestrutura

Exemplo:

```text
QA-RPO-01
↓
INFRA-REQ-008
↓
IDR-005
↓
FND-025
↓
OPS-TEST-004
↓
EVID-088
```

Assim backup e restore deixam de ser apenas configuração de painel.

---

## 34. Rastreabilidade de UX/UI

Para entregas visíveis, a matriz deve conseguir ligar:

```text
US
↓
JORNADA
↓
UX-FLOW
↓
UI-SCR / UI-CMP
↓
implementação
↓
teste de interação
↓
evidência visual / device
```

Isso evita que uma Issue de UI seja implementada apenas a partir de uma captura isolada.

---

## 35. Referências visuais

Quando uma imagem, protótipo ou asset for referência:

registrar:

- referência;
- autoridade;
- o que preservar;
- o que não copiar;
- quais dados são ilustrativos;
- qual item usa a referência.

Uma captura não é fonte de dados de runtime.

---

## 36. Rastreabilidade de pesquisa

Pesquisa normalmente possui autoridade menor que decisões posteriores.

Exemplo:

```text
EVIDÊNCIA DE PESQUISA
↓
HIPÓTESE
↓
DECISÃO DE BRIEFING
↓
ITEM
```

A matriz deve permitir marcar uma fonte antiga como:

```text
SUPERSEDED_BY: BR-014
```

sem apagar seu valor histórico.

---

## 37. Autoridade

Cada trace pode registrar a autoridade predominante.

Categorias possíveis:

```text
LEGAL
PRODUCT
UX
UI
ENGINEERING
ARCHITECTURE
TECH_LEAD
INFRA
OPERATIONS
EVIDENCE
```

A hierarquia real deve seguir o processo e as decisões do projeto.

A matriz não inventa precedência nova.

---

## 38. Conflitos

Se duas fontes incompatíveis apontam para o mesmo item:

```text
TRACE_CONFLICT
```

Não selecionar silenciosamente a versão mais recente ou a mais conveniente.

Fluxo:

```text
CONFLITO
↓
identificar autoridade
↓
DEC-xxx
↓
atualizar fonte adequada
↓
atualizar backlog
↓
atualizar matriz
```

---

## 39. Relação com `DEC-xxx`

Decisões de reconciliação precisam aparecer na matriz quando alteram caminho de execução.

Exemplo:

```text
DEC-004
↓
M1
↓
US-005
↓
GAT-002
```

Isso permite explicar por que um item está naquele marco.

---

## 40. Mudança de baseline

Quando a realidade mudar:

```text
EVIDÊNCIA NOVA
↓
classificar impacto
↓
fonte de autoridade
↓
reconciliação
↓
backlog
↓
matriz
↓
testes / evidências
```

Nunca atualizar apenas a matriz.

A matriz aponta para a realidade canônica; ela não substitui a fonte da decisão.

---

## 41. `TRACE_STALE`

Um trace fica stale quando:

- fonte foi alterada;
- item foi supersedido;
- ADR mudou;
- TDR mudou;
- implementação mudou;
- teste deixou de existir;
- evidência não corresponde à versão atual;
- gate foi redefinido.

A reconciliação precisa atualizá-lo.

---

## 42. Versão da evidência

Quando importante, a evidência deve apontar para versão imutável:

```text
commit SHA
artifact digest
migration ID
deployment ID
run ID
release tag
```

Evitar referência apenas a:

```text
“staging atual”
“último deploy”
“branch main”
```

porque o alvo muda.

---

## 43. Evidência hospedada

Quando a validação depende de ambiente real, registrar separadamente:

```text
LOCAL_VERIFICATION
CI_VERIFICATION
HOSTED_VERIFICATION
HUMAN_ACCEPTANCE
```

Exemplo:

```text
LOCAL
unit + contract green

CI
run 4451 green

STAGING
deployment d-123
route 200

HUMAN
owner accepted on 2026-08-30
```

---

## 44. Aprovação humana

Nem toda prova é automatizável.

Pode ser necessário aceite humano para:

- UI;
- conteúdo;
- fluxos críticos;
- decisão jurídica;
- operação;
- dispositivo físico;
- acessibilidade manual;
- recuperação;
- publicação em loja.

A matriz deve registrar esse aceite como evidência, não como comentário informal perdido no chat.

---

## 45. Conversa não é evidência canônica por padrão

Uma mensagem como:

```text
“aceito, pode seguir”
```

é autorização válida no contexto da conversa.

Mas quando ela encerra um gate material, o resultado precisa ser persistido em uma fonte rastreável:

- Issue;
- PR;
- decisão documental;
- registro de gate;
- seção de evidência.

O chat não deve ser o único local onde a decisão existe.

---

## 46. Matriz e GitHub Issues

A matriz não deve reproduzir todo o corpo das Issues.

Ela registra ligações.

Exemplo:

```text
US-014
ISSUE: #42
PR: #51
```

A Issue continua responsável por:

- contexto executável;
- critérios;
- dependências;
- conversa operacional;
- progresso.

---

## 47. Matriz e GitHub Project

Project é visão operacional de:

- status;
- ordem;
- marco;
- owner;
- bloqueio.

A Matriz é visão de:

- origem;
- realização;
- verificação;
- evidência;
- cobertura.

Não transformar Project em fonte de requisito.

---

## 48. Matriz e PR

Todo PR material deve apontar para item executável.

Ideal:

```text
PR #51
implements US-014
related FND-022
satisfies NFR-005
```

A matriz pode usar o PR como elo de realização.

---

## 49. Matriz e commits

Não é necessário mapear cada commit.

Mapear quando:

- commit é candidato imutável;
- commit encerra evidência;
- hotfix precisa de prova específica;
- ausência de PR exige rastreabilidade temporária.

Preferir PR + SHA final quando disponível.

---

## 50. Matriz e CI

CI deve provar requisitos conhecidos.

A matriz pode associar:

```text
TEST-xxx
→ workflow/job/check
```

Exemplo:

```text
SEC-004
→ security gate

CONTRACT-012
→ contract-test job
```

Não tratar `CI green` como prova genérica de tudo.

---

## 51. Matriz e staging

Staging pode provar:

- integração;
- migration;
- deploy;
- comportamento hospedado;
- smoke;
- UI;
- fluxo de terceiro sandbox;
- observabilidade;
- rollback.

Registrar exatamente o que foi provado.

---

## 52. Matriz e produção

Produção deve ser usada como evidência somente quando apropriado.

Exemplos:

- métrica real;
- comportamento de rollout;
- custo;
- SLO;
- incidente;
- performance;
- compatibilidade.

Não usar dado real para provar algo que poderia ser validado com sintético quando isso aumenta risco.

---

## 53. Dados sensíveis

A matriz não deve armazenar:

- secrets;
- tokens;
- credenciais;
- dados pessoais reais;
- payloads sensíveis;
- conteúdo privado de usuário.

Evidência deve ser sanitizada ou referenciada em local apropriado.

---

## 54. Matriz de gates

Para projetos complexos, incluir uma seção-resumo:

| Gate | Tipo | Itens bloqueados | Owner | Condição | Estado | Evidência |
| --- | --- | --- | --- | --- | --- | --- |

Isso não substitui o detalhamento no documento de origem.

---

## 55. Matriz de decisões

Também pode existir uma visão compacta:

| Decisão | Tema | Origem | Itens afetados | Estado |
| --- | --- | --- | --- | --- |

Usar principalmente para `DEC`, `ADR`, `TDR` e `IDR` que alteram execução.

---

## 56. Matriz de marcos

Não repetir todo o plano de entrega.

Apenas permitir responder:

```text
M1
→ quais itens?
→ quais gates?
→ quais evidências de saída?
```

Exemplo:

| Marco | Itens | Gate de saída | Evidência | Estado |
| --- | --- | --- | --- | --- |

---

## 57. Métricas

Métricas permanecem definidas nas fontes de produto/PO.

A Matriz pode ligar:

```text
OUT-xxx
↓
METRIC-xxx
↓
EXP-xxx / US-xxx
↓
EVENT-xxx
↓
EVID-xxx
```

Não redefinir fórmula de métrica nesta etapa.

---

## 58. Eventos e analytics

Quando eventos forem necessários para provar outcome:

registrar:

- ID semântico;
- finalidade;
- item relacionado;
- métrica relacionada;
- dados proibidos;
- implementação;
- evidência.

Exemplo:

```text
EVENT-021
set_completed
```

Não escolher ferramenta de analytics nesta etapa.

---

## 59. Recortes incrementais

Quando um item é dividido:

```text
US-014
↓
UX-R3.1
UX-R3.2
UX-R3.3
```

A matriz precisa preservar a relação pai-filho.

O recorte não substitui a história.

Estados possíveis:

```text
PARTIAL_IMPLEMENTATION
```

até todos os critérios necessários serem satisfeitos.

---

## 60. Correções

Correções `COR-xxx` devem apontar para o requisito que regrediu ou para o item cuja evidência foi invalidada.

Exemplo:

```text
COR-004
AFFECTS:
US-001
FND-013
TEST-004
```

Depois do fechamento:

```text
NEW_EVIDENCE:
EVID-071
```

---

## 61. Hotfix

Hotfix não elimina rastreabilidade.

Fluxo mínimo:

```text
INCIDENTE
↓
COR/HOTFIX
↓
mudança
↓
teste
↓
evidência
↓
reconciliação posterior se necessário
```

Se foi necessário agir antes de atualizar documentação, registrar dívida explícita.

---

## 62. Brownfield

Em projeto existente, a matriz precisa mapear o que já existe.

Classificar:

```text
EXISTING_VALID
EXISTING_UNVERIFIED
LEGACY_REQUIRED
LEGACY_TO_MIGRATE
ORPHAN_IMPLEMENTATION
TO_REMOVE
```

Não assumir que cada rota ou tabela existente possui requisito vigente.

---

## 63. Descoberta de implementação existente

Pode-se começar pelo código e voltar para a intenção:

```text
route /x
↓
handler
↓
tabela
↓
teste
↓
qual Issue?
↓
qual requisito?
```

Se não houver fonte:

```text
ORPHAN_IMPLEMENTATION
```

até decisão humana.

---

## 64. Greenfield

Em greenfield, a matriz nasce inicialmente com muitas colunas de implementação vazias.

Isso é esperado.

Exemplo:

```text
SOURCE ✅
WORK ITEM ✅
IMPLEMENTATION —
TEST EXPECTED ✅
ACTUAL EVIDENCE —
```

Não preencher com valores fictícios apenas para parecer completa.

---

## 65. Matriz viva

A matriz não é documento criado uma vez e abandonado.

Ela deve evoluir quando:

- backlog muda;
- item entra em execução;
- PR abre;
- teste é criado;
- gate fecha;
- evidence é produzida;
- item é removido;
- arquitetura muda;
- tecnologia muda;
- infra muda;
- release acontece.

Mas mudanças precisam preservar histórico e autoridade.

---

## 66. Atualização por evento

Eventos recomendados que exigem revisão da matriz:

```text
ISSUE_READY
PR_OPENED
PR_MERGED
STAGING_DEPLOYED
GATE_ACCEPTED
CORRECTION_OPENED
ADR_CHANGED
TDR_CHANGED
IDR_CHANGED
BASELINE_CHANGED
RELEASED
```

Não significa editar manualmente em todos os eventos se houver automação confiável.

---

## 67. Automação da matriz

É permitido gerar partes do Markdown automaticamente.

Exemplos:

- extrair IDs de docs;
- cruzar Issues;
- cruzar PRs;
- identificar links ausentes;
- gerar índice;
- validar duplicidade de IDs;
- verificar references quebradas;
- calcular cobertura.

Mas:

```text
AUTOMAÇÃO
≠
AUTORIDADE PARA CRIAR RELAÇÃO
```

Se a relação semântica não for clara, marcar para revisão humana.

---

## 68. Validador automático recomendado

Projetos maduros podem possuir script que verifique:

- IDs duplicados;
- item sem fonte;
- item Done sem evidência;
- gate sem owner;
- trace apontando para ID inexistente;
- evidência sem item;
- requisito material sem disposição;
- PR sem Issue;
- TDR sem TECH-REQ;
- IDR sem INFRA-REQ;
- FND sem origem;
- link quebrado.

O script não decide se uma regra de negócio está correta.

---

## 69. Métricas de cobertura

Podem ser calculadas métricas como:

```text
source_coverage
work_item_source_coverage
verified_item_coverage
orphan_requirement_count
orphan_implementation_count
stale_trace_count
```

Cuidado:

> **100% de links não significa 100% de qualidade.**

A métrica serve para encontrar lacunas, não para premiar quantidade de relacionamento.

---

## 70. Fórmula conceitual de cobertura

Exemplo:

```text
SOURCE_COVERAGE =
fontes materiais com disposição explícita
/
fontes materiais inventariadas
```

Mas a metodologia não fixa uma fórmula universal.

Cada projeto define quais unidades entram no denominador.

---

## 71. Critério de materialidade

Nem todo conteúdo documental precisa entrar no denominador.

Normalmente entram:

- decisões;
- regras;
- requisitos;
- gates;
- jornadas materiais;
- riscos aceitos/não aceitos;
- invariantes;
- escolhas técnicas duráveis.

Textos introdutórios podem ser `CONTEXT_ONLY`.

---

## 72. Markdown e escala

Projetos grandes podem produzir centenas ou milhares de linhas.

Ainda assim a fonte canônica permanece Markdown.

Para manter legibilidade:

- usar headings por domínio;
- ordenar por ID;
- criar índice;
- usar tabelas menores por categoria;
- usar links internos;
- evitar uma tabela horizontal com 30 colunas;
- separar visões de cobertura, execução e evidência em seções.

---

## 73. Não usar tabela gigante como banco de dados

Uma única tabela com:

```text
35 colunas
x
1500 linhas
```

pode ser formalmente Markdown e ainda ser inutilizável.

Preferir:

```text
SEÇÃO A — Cobertura de fontes
SEÇÃO B — Produto
SEÇÃO C — UX/UI
SEÇÃO D — Arquitetura
SEÇÃO E — Fundação
SEÇÃO F — Execução
SEÇÃO G — Gates
SEÇÃO H — Evidências
```

mantendo IDs que permitem cruzamento.

---

## 74. Um arquivo canônico

Por padrão, produzir:

```text
11_Matriz_Operacional_de_Rastreabilidade.md
```

Se o projeto atingir escala em que um único arquivo fique impraticável, pode haver anexos Markdown gerados, por exemplo:

```text
11_Matriz_Operacional_de_Rastreabilidade.md
11_matriz/produto.md
11_matriz/arquitetura.md
11_matriz/fundacao.md
11_matriz/evidencias.md
```

Mas o arquivo principal deve continuar sendo o índice canônico e explicar a partição.

Nunca migrar a fonte canônica para XLSX apenas por volume.

---

## 75. Estrutura recomendada da matriz principal

Cada projeto deve adaptar, mas uma estrutura útil é:

```text
Trace
Source
Source Ref
Authority
Requirement / Decision
Work Item
Dependencies
Gate
UX/UI Ref
Architecture Ref
Technology Ref
Infrastructure Ref
Implementation Ref
Verification Ref
Evidence Ref
Disposition
Trace Status
Last Reconciled
Notes
```

Não exigir colunas sem uso real.

---

## 76. Exemplo completo

```markdown
| Trace | Fonte | Regra | Item | UX | Arquitetura | Tech | Infra | Gate | Verificação | Evidência | Estado |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TRACE-0042 | DOC-03 | BR-021 | US-014 | UX-FLOW-008 | ADR-006 | TDR-004 | FND-031 | GAT-003 | TEST-087 | EVID-052 | VERIFIED |
```

A linha não precisa reproduzir o conteúdo de cada ID.

Ela conecta as fontes.

---

## 77. Exemplo de requisito ainda não implementado

```markdown
| TRACE-0051 | DOC-03 | BR-033 | US-020 | UX-FLOW-015 | ADR-012 | — | — | GAT-004 | TEST-EXPECTED-021 | — | BLOCKED |
```

Isso é uma linha válida.

Não preencher `TDR`, `FND` ou evidência ficticiamente.

---

## 78. Exemplo de item removido

```markdown
| TRACE-0060 | DOC-03 | US-006 | US-006 | — | — | — | — | — | — | DEC-014 | REMOVED |
```

O ID permanece para preservar histórico.

---

## 79. Exemplo de decisão supersedida

```markdown
| TRACE-0070 | DOC-01 | HYP-008 | — | — | — | — | — | — | — | BR-014 | SUPERSEDED |
```

A pesquisa continua auditável.

---

## 80. Exemplo de implementação órfã

```markdown
| TRACE-ORPHAN-003 | CODE | endpoint /internal/x | — | — | — | — | — | — | existing tests | deployment abc | ORPHAN_IMPLEMENTATION |
```

Depois da revisão humana:

```text
remover
ou
mapear para requisito existente
ou
criar decisão canônica apropriada
```

Nunca criar retrospectivamente uma história só para justificar o código sem avaliação.

---

## 81. Rastreabilidade e Codex

A Matriz é uma das fontes essenciais para o handoff.

Antes de executar um item, o Codex deve conseguir descobrir:

```text
ITEM
↓
FONTES
↓
REGRAS
↓
UX/UI
↓
ARQUITETURA
↓
STACK
↓
INFRA
↓
NFRs
↓
GATES
↓
TESTES
↓
EVIDÊNCIA ESPERADA
```

Se uma relação material estiver ausente:

```text
STOP
```

em vez de inventar.

---

## 82. Condições de parada para agentes

O agente deve interromper quando:

- item não possui fonte;
- duas fontes entram em conflito;
- gate está fechado;
- tecnologia necessária não está aprovada;
- nova dependência estrutural seria necessária;
- implementação exigiria alterar boundary;
- critério de aceite é ambíguo;
- evidência necessária depende de ação humana;
- segredo não autorizado seria necessário;
- dados reais seriam necessários fora do gate;
- a matriz está stale no trecho afetado.

---

## 83. Não usar a matriz como prompt integral

Não despejar milhares de linhas no agente para cada tarefa.

O handoff deve selecionar apenas o recorte relevante.

Fluxo:

```text
ITEM
↓
resolver Trace IDs aplicáveis
↓
carregar fontes necessárias
↓
executar
```

Isso reduz ruído e contradição.

---

## 84. Reconciliation timestamp

Cada seção ou trace material pode registrar:

```text
LAST_RECONCILED: YYYY-MM-DD
```

ou commit da baseline:

```text
BASELINE_COMMIT: <sha>
```

Isso ajuda a detectar matriz desatualizada.

---

## 85. Baseline commit

Antes do handoff final, o projeto deve possuir um commit identificável contendo a baseline documental reconciliada.

A Matriz deve poder declarar:

```text
BASELINE_REF: <commit/tag>
```

Não usar uma branch mutável como única referência do handoff.

---

## 86. Release e rastreabilidade

Ao promover release:

```text
RELEASE
↓
quais itens?
↓
quais PRs?
↓
quais evidências?
↓
quais gates?
↓
quais riscos residuais?
```

A matriz deve permitir reconstruir esse conjunto.

---

## 87. Incidente e rastreabilidade

Após incidente:

```text
INCIDENTE
↓
qual versão?
↓
qual item originou?
↓
qual teste não detectou?
↓
qual requisito foi violado?
↓
qual mudança de processo é necessária?
```

Essa ligação transforma incidente em aprendizado da metodologia.

---

## 88. Requisito vs evidência histórica

Um comportamento pode ter sido provado em uma versão e quebrado depois.

Portanto:

```text
EVIDENCE_VALID_FOR: <sha / release>
```

quando material.

Não considerar evidência antiga automaticamente válida para código novo.

---

## 89. Evidência supersedida

Estados possíveis:

```text
ACTIVE
SUPERSEDED
INVALIDATED_BY_REGRESSION
HISTORICAL
```

Preservar evidência histórica em vez de apagá-la.

---

## 90. Relação com DoR

Antes de `Ready`, o item precisa ter rastreabilidade suficiente para execução.

No mínimo:

```text
SOURCE ✅
OBJECTIVE ✅
ACCEPTANCE ✅
DEPENDENCIES ✅
NFRs ✅
GATES ✅
UX/UI ✅ quando aplicável
ARCH ✅ quando aplicável
TECH ✅ quando aplicável
INFRA ✅ quando aplicável
EXPECTED EVIDENCE ✅
STOP CONDITIONS ✅
```

---

## 91. Relação com DoD

Antes de `Done`, a matriz deve possuir:

```text
IMPLEMENTATION REF ✅
VERIFICATION REF ✅
ACTUAL EVIDENCE ✅
GATES CLOSED ✅ quando aplicável
DOC IMPACT RECONCILED ✅
```

Se isso não existe, `Done` precisa ser contestado.

---

## 92. Relação com Fundação

FNDs são cidadãos de primeira classe na matriz.

Exemplo:

```text
IDR-003
↓
FND-015
↓
CI / IaC / config
↓
OPS-TEST-004
↓
EVID-081
```

Não rastrear apenas features visíveis.

---

## 93. Relação com decisões humanas

Uma decisão humana que altera execução precisa ficar persistente.

Pode originar:

```text
DEC-xxx
```

ou alteração na fonte correspondente.

A matriz deve apontar para o resultado persistido, não apenas para a conversa onde ocorreu.

---

## 94. Revisão humana da matriz

Antes da canonização, apresentar ao humano:

```text
COBERTURA DAS FONTES
REQUISITOS ÓRFÃOS
IMPLEMENTAÇÕES ÓRFÃS
TRACES PARCIAIS
CONFLITOS
GATES ABERTOS
NFRs SEM HERANÇA
ADRs SEM CONSEQUÊNCIA
TECH-REQs SEM TDR
INFRA-REQs SEM IDR/FND
ITENS DONE SEM EVIDÊNCIA
EVIDÊNCIAS STALE
```

O objetivo é revisão de lacunas, não leitura linha por linha de toda a matriz.

---

## 95. Readiness da matriz

Estados:

```text
TRACEABILITY_READINESS: INSUFFICIENT
TRACEABILITY_READINESS: SUFFICIENT_WITH_OPEN_ITEMS
TRACEABILITY_READINESS: SUFFICIENT
```

`SUFFICIENT_WITH_OPEN_ITEMS` significa que existem itens ainda não implementados, mas sua disposição e rastreabilidade estão claras.

Isso é normal antes de iniciar desenvolvimento funcional.

---

## 96. O que bloqueia `SUFFICIENT`

Exemplos:

- requisito material órfão;
- item P0 sem fonte;
- conflito de autoridade não resolvido;
- gate crítico sem owner;
- arquitetura obrigatória sem ligação ao item;
- stack não aprovada para item que precisa dela;
- FND obrigatório ausente;
- item marcado Done sem qualquer prova;
- matriz baseada em baseline antiga;
- referência quebrada em requisito crítico.

---

## 97. Gates desta etapa

| Gate | Critério |
| --- | --- |
| TRACE-01 Inventário | Fontes materiais inventariadas. |
| TRACE-02 Cobertura | Toda unidade material possui disposição. |
| TRACE-03 Backlog | Todo item executável possui origem rastreável. |
| TRACE-04 Arquitetura | ADRs/TECH-REQs materiais possuem consequência rastreada. |
| TRACE-05 Tecnologia | TDRs e decisões estruturais apontam para requisitos. |
| TRACE-06 Infra | IDRs/FNDs apontam para requisitos operacionais. |
| TRACE-07 UX/UI | Entregas visíveis apontam para jornada e direção aplicável. |
| TRACE-08 Verificação | Itens Ready possuem prova esperada definida. |
| TRACE-09 Evidência | Itens Done possuem evidência real. |
| TRACE-10 Gates | Bloqueios possuem owner e condição de retomada. |
| TRACE-11 Órfãos | Órfãos materiais foram reconciliados ou explicitamente bloqueados. |
| TRACE-12 Freshness | Matriz corresponde à baseline atual. |

---

## 98. Anti-padrões

### 98.1. Excel como fonte canônica

Evitar.

Pode ser ferramenta de apoio, mas não artefato final da metodologia.

### 98.2. Copiar todo documento para a matriz

A matriz aponta; não duplica.

### 98.3. Uma Issue por heading

Cobertura não significa explosão de tarefas.

### 98.4. `Done` sem evidência

Merge não basta.

### 98.5. Evidência genérica

```text
“CI passou”
```

sem dizer o que foi provado é insuficiente para requisitos materiais.

### 98.6. Criar requisito a partir do código

Código existente é evidência, não autoridade automática.

### 98.7. Gate sem owner

Bloqueio sem responsável tende a nunca ser resolvido.

### 98.8. Matriz desatualizada

Uma matriz stale cria falsa confiança.

### 98.9. Link sem semântica

Apenas listar dez IDs numa célula sem dizer a relação reduz utilidade.

### 98.10. Rastrear somente features

Fundação, segurança, arquitetura, operação e correções também precisam ser rastreadas.

---

## 99. Qualidade da matriz

Uma boa matriz permite que uma pessoa nova no projeto responda:

1. por que este item existe?
2. qual fonte manda?
3. que comportamento deve preservar?
4. quais decisões técnicas se aplicam?
5. o que bloqueia?
6. como será testado?
7. qual prova encerra?
8. qual parte da baseline muda se precisarmos alterar isso?

Sem depender de conhecimento oral.

---

## 100. Estrutura mínima do artefato de projeto

O projeto deve produzir `11_Matriz_Operacional_de_Rastreabilidade.md` com estrutura equivalente a:

```markdown
---
document_id: DOC-11
title: Matriz Operacional de Rastreabilidade
status: canonical
version: 1.0.0
baseline_ref: <sha/tag>
next_document: 12_Reconciliacao_da_Baseline_e_Handoff_para_Codex.md
---

# Matriz Operacional de Rastreabilidade

## 1. Escopo e baseline
## 2. Convenções e estados
## 3. Cobertura documental
## 4. Matriz principal de rastreabilidade
## 5. Produto e regras
## 6. UX/UI
## 7. Engenharia e arquitetura
## 8. Tecnologia
## 9. DevOps e infraestrutura
## 10. Fundação
## 11. NFRs e heranças
## 12. Gates e bloqueios
## 13. Implementação e PRs
## 14. Testes e verificação
## 15. Evidências
## 16. Correções e regressões
## 17. Órfãos e conflitos
## 18. Métricas de cobertura
## 19. Pendências de reconciliação
## 20. Traceability Readiness
## 21. Handoff para reconciliação final
```

Adaptar ao tamanho do projeto.

Não criar seções vazias apenas para obedecer template.

---

## 101. Exemplo de cabeçalho operacional

```text
BASELINE_REF: abc123
TRACEABILITY_STATUS: IN_PROGRESS
SOURCE_COVERAGE: 94%
ORPHAN_REQUIREMENTS: 2
ORPHAN_IMPLEMENTATIONS: 1
STALE_TRACES: 3
CRITICAL_CONFLICTS: 0
NEXT_ACTION: reconciliar BR-021 e FND-018
```

Percentuais são opcionais.

Os contadores podem ser mais úteis do que porcentagens.

---

## 102. Síntese antes da canonização

Antes de finalizar, o ChatGPT deve apresentar:

```text
BASELINE ANALISADA
COBERTURA
TRACES COMPLETOS
TRACES PARCIAIS
REQUISITOS ÓRFÃOS
IMPLEMENTAÇÕES ÓRFÃS
CONFLITOS
GATES ABERTOS
ITENS DONE SEM EVIDÊNCIA
TRACES STALE
DECISÕES A RECONCILIAR
TRACEABILITY_READINESS
```

O humano pode:

- corrigir relações;
- declarar item não aplicável;
- resolver conflito;
- exigir evidência adicional;
- reabrir etapa anterior;
- aceitar pendência não bloqueante.

---

## 103. Canonização

Fluxo:

```text
INVENTÁRIO
↓
MAPEAMENTO
↓
AUDITORIA
↓
RECONCILIAÇÃO
↓
REVISÃO HUMANA
↓
CANONIZAÇÃO
↓
11_Matriz_Operacional_de_Rastreabilidade.md
```

A matriz canonizada deve apontar para uma baseline identificável.

---

## 104. Handoff para reconciliação final

Após a matriz estar suficiente, a próxima etapa recebe:

```text
BASELINE_REF
COBERTURA DOCUMENTAL
BACKLOG
TRACES
GATES
CONFLITOS RESOLVIDOS
CONFLITOS ABERTOS
ORPHANS
EVIDÊNCIAS
READINESS
```

A próxima etapa deve responder:

> **A baseline inteira está coerente e suficientemente completa para entregar um recorte executável ao Codex sem exigir que o agente invente produto, UX, arquitetura, stack, infraestrutura ou critério de aceite?**

---

## 105. Regra para o handoff futuro

O Codex não deve consumir o repositório inteiro indiscriminadamente.

O handoff selecionará, por item:

```text
ITEM
+
TRACE IDS
+
FONTES REFERENCIADAS
+
CONTRATOS
+
TESTES
+
GATES
+
CONDIÇÕES DE PARADA
```

A Matriz torna essa seleção possível.

---

## 106. Princípio final

> **Rastreabilidade não é provar que existem muitos links. É conseguir demonstrar, de forma auditável, que cada decisão material chega até uma entrega verificável e que nenhuma implementação relevante existe sem uma origem legítima. A fonte canônica desta prova deve permanecer legível, versionável e revisável — por isso, neste processo, a Matriz Operacional é Markdown.**

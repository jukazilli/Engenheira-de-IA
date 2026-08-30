---
document_id: PROCESS-10-BACKLOG-CANONICO
 title: Backlog Canônico, Rastreabilidade e Plano de Entrega
status: draft-methodology
version: 0.1.0
stage: backlog-canonico
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
produces: 10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
next_stage: 11_Matriz_Operacional_de_Rastreabilidade.md
---

# 10 — Backlog Canônico, Rastreabilidade e Plano de Entrega

## 1. Propósito

A etapa **Backlog Canônico, Rastreabilidade e Plano de Entrega** transforma todas as decisões aprovadas das etapas anteriores em uma **baseline operacional única, sequenciada, rastreável e executável**, sem substituir as fontes canônicas que deram origem a essas decisões.

A pergunta central desta etapa é:

> **Como transformar produto, experiência, arquitetura, stack, infraestrutura, fundação, qualidade, riscos e gates já aprovados em uma única ordem operacional de entrega, mantendo cada item ligado à sua origem, às suas dependências, aos seus critérios de aceite e às evidências necessárias para considerá-lo concluído?**

Esta etapa existe porque:

```text
DOCUMENTAÇÃO APROVADA
        +
HISTÓRIAS DE PRODUTO
        +
REQUISITOS TRANSVERSAIS
        +
FUNDAÇÃO
        +
GATES
        +
DECISÕES TÉCNICAS

NÃO SIGNIFICA

ORDEM DE EXECUÇÃO PRONTA
```

As etapas anteriores respondem **o que deve existir, por quê, como deve se comportar, como deve ser estruturado e com quais tecnologias e operação**.

Esta etapa responde:

```text
O QUE ENTRA NO PORTFÓLIO EXECUTÁVEL?
        ↓
O QUE DEPENDE DO QUÊ?
        ↓
QUAL É O PRÓXIMO ITEM ELEGÍVEL?
        ↓
O QUE BLOQUEIA?
        ↓
QUAL EVIDÊNCIA FECHA O ITEM?
        ↓
QUAL GATE LIBERA O PRÓXIMO MARCO?
```

O resultado ainda **não autoriza implementação funcional pelo Codex**.

Antes do handoff final, a baseline ainda deve passar pela etapa `11_Matriz_Operacional_de_Rastreabilidade.md`.

---

## 2. Posição no processo

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
10 BACKLOG CANÔNICO,
   RASTREABILIDADE E PLANO DE ENTREGA
        ↓
11 Matriz Operacional de Rastreabilidade
        ↓
BASELINE RECONCILIADA
        ↓
HANDOFF PARA CODEX
```

A etapa 09 define **quais capacidades fundacionais precisam ser preparadas**.

A etapa 10 coloca essas capacidades no mesmo sistema operacional de entrega que:

- histórias de produto;
- correções;
- requisitos não funcionais;
- experimentos executáveis;
- gates;
- itens deferidos;
- recortes incrementais aprovados.

A etapa 11 fará a auditoria transversal final da ligação:

```text
ORIGEM
→ REQUISITO
→ ITEM
→ IMPLEMENTAÇÃO
→ TESTE
→ EVIDÊNCIA
→ STATUS
```

---

## 3. Origem desta etapa

Esta etapa foi formalizada a partir do backlog operacional real do DayGym.

O processo real demonstrou três comportamentos importantes:

1. documentos de produto, UX, engenharia e arquitetura não devem ser tratados como listas paralelas de trabalho;
2. o backlog precisa reconciliar divergências antes de gerar Issues;
3. o tracker operacional controla execução, mas não substitui a autoridade da documentação canônica.

No caso real, a canonização foi executada por inventário, normalização, reconciliação, sequenciamento e publicação.

A metodologia preserva essa lógica, mas a adapta à nova cadeia documental, que agora possui separadamente:

- Engenharia e Arquitetura;
- Visão do Tech Lead;
- DevOps e Infraestrutura;
- Plano de Fundação.

Por isso, a etapa reconstruída recebe mais fontes e possui uma fronteira mais explícita entre **baseline normativa**, **tracker operacional** e **prova executável**.

---

## 4. Princípio central: backlog não é cópia da documentação

Canonizar não significa copiar parágrafos dos documentos anteriores para centenas de Issues.

Canonizar significa:

```text
PRESERVAR A DECISÃO
NA FONTE DE AUTORIDADE

        +

CRIAR UM ITEM EXECUTÁVEL
COM ESCOPO CLARO

        +

LIGAR ORIGEM,
IMPLEMENTAÇÃO E PROVA
```

Portanto:

```text
DOCUMENTO CANÔNICO
≠
ISSUE
```

A Issue referencia o contrato.

Ela não deve reconstruí-lo de memória.

---

## 5. Separação das fontes de verdade

A metodologia usa fontes diferentes para responsabilidades diferentes.

### 5.1. Documentação canônica

Responsável por:

- intenção;
- escopo;
- regra de negócio;
- decisão de produto;
- comportamento de UX;
- sistema visual;
- política de engenharia;
- arquitetura;
- stack;
- infraestrutura;
- fundação;
- gates e restrições.

### 5.2. ADRs, TDRs e IDRs

Responsáveis por decisões duráveis específicas:

```text
ADR
arquitetura

TDR
tecnologia

IDR
infraestrutura
```

### 5.3. GitHub Issues

Responsáveis pela unidade operacional de execução:

- item;
- owner;
- status;
- dependências;
- escopo do corte;
- discussão da execução;
- PRs;
- evidências.

### 5.4. GitHub Project

Responsável por:

- ordem operacional;
- status;
- marco;
- bloqueios;
- prioridade operacional;
- owner;
- visão de fluxo.

O Project **não redefine escopo silenciosamente**.

### 5.5. Código, migrations, contratos e testes

Responsáveis pela prova implementada e reproduzível.

### 5.6. Runbooks, dashboards e registros operacionais

Responsáveis pela prova de operabilidade, recuperação e comportamento em execução.

---

## 6. Hierarquia de autoridade

A etapa 10 deve reconstruir a hierarquia a partir da cadeia documental aprovada.

Uma ordem genérica é:

```text
1. LEI / SEGURANÇA / OBRIGAÇÃO EXTERNA VINCULANTE
2. BRIEFING E PRODUCT OWNER
3. PRINCÍPIOS / UI / UX
4. ENGENHARIA E ARQUITETURA
5. TECH LEAD
6. DEVOPS E INFRAESTRUTURA
7. TÉCNICAS DE DESENVOLVIMENTO
8. PLANO DE FUNDAÇÃO
9. BACKLOG / ISSUE / PROMPT / AGENTE
```

A ordem concreta deve considerar o tipo de conflito.

Exemplo:

```text
ISSUE diz:
“salvar automaticamente”

UX diz:
“ação exige confirmação explícita”

        ↓
ISSUE NÃO PODE PREVALECER
```

Outro:

```text
TECH LEAD escolheu tecnologia X

ARQUITETURA exige propriedade Y

novo teste comprova que X não atende Y

        ↓
NÃO ALTERAR ARQUITETURA NA ISSUE

        ↓
REABRIR TDR / ADR
```

---

## 7. Pré-requisitos obrigatórios

Antes de iniciar esta etapa, o ChatGPT deve consumir integralmente a baseline aprovada anterior.

No mínimo:

- Discovery;
- Pesquisa e Viabilidade;
- Briefing;
- Visão de Product Owner;
- Princípios UX/UI;
- Direção de UI;
- Especificação de UX;
- Técnicas de Desenvolvimento;
- Engenharia e Arquitetura;
- Visão do Tech Lead;
- DevOps e Infraestrutura;
- Plano de Fundação.

Também deve considerar, quando existirem:

- ADRs;
- TDRs;
- IDRs;
- threat models;
- contratos de API;
- dicionários de dados;
- inventários UX;
- protótipos aprovados;
- decisões posteriores formalmente registradas;
- backlog existente em brownfield.

Se algum documento obrigatório estiver contraditório ou incompleto a ponto de impedir sequenciamento responsável:

```text
BACKLOG_READINESS: INSUFFICIENT
```

Não inventar uma resolução silenciosa.

---

## 8. Handshake da etapa

Ao iniciar a execução desta etapa em um projeto, o ChatGPT deve declarar algo equivalente a:

```text
PROCESS_STATUS: ACTIVE
CURRENT_STAGE: BACKLOG_CANONICO
INPUT_BASELINE: DOCUMENTOS_00_A_09
CANONIZATION_STATUS: IN_PROGRESS
OPERATIONAL_TARGET: GITHUB
CANONICAL_OUTPUT: 10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
NEXT_STAGE: 11_Matriz_Operacional_de_Rastreabilidade.md
```

Se já existir tracker:

```text
BROWNFIELD_TRACKER: PRESENT
```

Se não existir:

```text
BROWNFIELD_TRACKER: ABSENT
```

---

## 9. Método de canonização em cinco passes

A metodologia usa cinco passes.

### PASS 1 — Inventário

Extrair de todas as fontes:

- épicos;
- histórias;
- capacidades;
- FNDs;
- NFRs;
- gates;
- experimentos;
- decisões;
- riscos;
- dependências;
- recortes;
- métricas;
- requisitos de segurança;
- requisitos de operação;
- obrigações de release;
- pendências.

Objetivo:

> garantir cobertura antes de ordenar.

### PASS 2 — Normalização

Separar claramente os tipos de item.

Não tratar tudo como "task".

### PASS 3 — Reconciliação

Resolver conflitos usando a hierarquia de autoridade.

Toda resolução material deve ser registrada.

### PASS 4 — Sequenciamento

Construir:

- dependências;
- caminho crítico;
- marcos;
- gates de entrada;
- gates de saída;
- itens paralelizáveis;
- itens bloqueados;
- horizontes posteriores.

### PASS 5 — Publicação

Após revisão humana:

- consolidar o documento 10;
- preparar Issues;
- preparar Project;
- preparar labels;
- preparar milestones;
- preparar visão operacional estruturada;
- encaminhar para auditoria da Matriz Operacional.

---

## 10. Regra de cobertura

A etapa deve perseguir duas condições simultâneas:

```text
NENHUM REQUISITO
SEM DISPOSIÇÃO
```

E:

```text
NENHUM ITEM EXECUTÁVEL
SEM ORIGEM
```

Uma disposição pode ser:

```text
IMPLEMENTAR
DEFERIR
BLOQUEAR
EXPERIMENTAR
VALIDAR
DESCARTAR
NÃO APLICÁVEL
SUPERCEDER
```

Não é obrigatório que todo requisito vire uma Issue própria.

Ele pode ser herdado por outros itens.

Mas não pode desaparecer.

---

## 11. Classes de item

A metodologia reconhece classes diferentes porque elas possuem semânticas diferentes.

### 11.1. Épico de produto

Prefixo já definido na Visão de PO.

Exemplo:

```text
E01
E02
...
```

Épico não é necessariamente uma Issue executável.

Ele organiza valor e ownership.

### 11.2. História funcional

```text
US-xxx
```

Representa valor ou comportamento de produto aprovado.

### 11.3. Fundação / habilitador

```text
FND-xxx
```

Vem principalmente de `09_Plano_de_Fundacao.md`.

### 11.4. Correção comprovada

```text
COR-xxx
```

Representa regressão ou falha observada.

Ela não renumera histórias.

### 11.5. Requisito não funcional

```text
NFR-xxx
```

Exemplos:

- acessibilidade;
- segurança;
- privacidade;
- performance;
- disponibilidade;
- recuperação;
- compatibilidade;
- observabilidade.

NFR normalmente é herdado por vários itens.

### 11.6. Gate

```text
GAT-xxx
```

Representa condição de liberação.

Pode depender de:

- evidência;
- contrato;
- licença;
- validação humana;
- segurança;
- jurídico;
- provider;
- operação;
- custo;
- resultado de experimento.

### 11.7. Experimento

Quando já existe ID canônico:

```text
EXP-xxx
```

Um experimento pode virar item operacional se ainda precisar ser executado.

### 11.8. Item deferido

Pode preservar os horizontes:

```text
P1-xxx
P2-xxx
```

ou outro prefixo já aprovado pelo projeto.

Deferido não significa esquecido.

### 11.9. POC técnica

POCs já definidas na Visão do Tech Lead preservam seus IDs:

```text
TL-POC-xxx
```

Se ainda estiverem abertas, a baseline deve explicar por que a stack já pôde ser canonizada ou bloqueá-la.

### 11.10. Recorte incremental

Quando uma história ou programa precisa ser quebrado em cortes menores, pode existir uma família de IDs específica.

Exemplos:

```text
UX-R6.1
MIG-03.2
SEC-R2.4
```

Regra:

> recorte não substitui a história ou requisito de origem; ele herda e referencia o item pai.

---

## 12. IDs são contratos estáveis

IDs aprovados não devem ser renumerados apenas para deixar a lista "bonita".

Regras:

1. ID removido não é reutilizado;
2. item supersedido preserva histórico;
3. correção não ocupa ID de história removida;
4. recorte não renumera épico;
5. FND não renumera US;
6. NFR não vira Story apenas para caber no tracker;
7. Gate não é confundido com tarefa.

Exemplo:

```text
US-006 REMOVIDA

NÃO FAZER

US-007 → US-006
US-008 → US-007
```

A lacuna histórica faz parte da rastreabilidade.

---

## 13. Decisões de reconciliação — DEC

Quando duas fontes aprovadas gerarem interpretações concorrentes, criar uma decisão de reconciliação:

```text
DEC-xxx
```

Estrutura mínima:

```text
ID
Tema
Fontes em tensão
Hierarquia aplicada
Resolução canônica
Itens afetados
Risco
Aprovação humana
```

Exemplo:

```text
PO coloca capacidade X na onda inicial.

Arquitetura coloca X depois por dependência técnica.

        ↓

DEC-004
X permanece parte do horizonte inicial de produto,
mas só entra no marco M2 após FND-017 e GAT-003.
```

A decisão deve resolver a tensão.

Não apagar a existência dela.

---

## 14. O backlog canônico preserva as fontes

Um item não precisa copiar todo o conteúdo que o suporta.

Ele deve apontar para referências como:

```text
BR-021
OUT-004
HYP-003
UX-FLOW-008
UI-SCR-012
ARCH-DRV-004
QA-003
ADR-006
TECH-REQ-012
TDR-004
INFRA-REQ-007
IDR-003
FND-031
```

A Issue herda essas fontes.

---

## 15. Contrato mínimo de um item executável

Todo item executável precisa possuir, quando aplicável:

```text
ID
Título
Tipo
Épico / trilha
Objetivo observável
Resultado esperado
Escopo
Fora de escopo
Prioridade
Marco
Owner
Executor permitido
Status
Fontes canônicas
Dependências
Dependentes
Gate de entrada
Gate de saída
Critérios de aceite
Evidência esperada
NFRs herdados
Dados afetados
Riscos
Feature flag
Rollout
Rollback
Observabilidade
Condição de parada
Notas para IA
```

Nem todo campo precisa ser longo.

Mas campos relevantes não podem ficar implícitos.

---

## 16. Objetivo observável

Evitar itens como:

```text
“Criar tela de progresso”
```

Preferir:

```text
“Permitir que o usuário consulte
seu histórico de evolução com
os estados e unidades já aprovados,
sem misturar métricas incompatíveis.”
```

Para enabler:

```text
“Permitir que um clone limpo
execute migrations de staging
de forma reproduzível.”
```

O objetivo deve deixar claro por que o item existe.

---

## 17. Dependências formam um grafo

O backlog não é uma lista linear.

Ele é um grafo.

Exemplo:

```text
FND-001
   ↓
FND-002
   ↓
FND-005
   ↓
FND-006
   ↓
FND-014

US-001
   ↓
US-004
   ↓
US-009
```

Itens diferentes podem ocorrer em paralelo.

A ordem visual do Project não pode substituir dependências reais.

---

## 18. Tipos de dependência

Quando útil, classificar:

```text
HARD
não pode iniciar

SOFT
pode iniciar, mas não concluir

GATE
pode desenvolver, mas não expor

EXTERNAL
depende de terceiro

HUMAN
depende de decisão/ação humana

EVIDENCE
depende de prova
```

Isso reduz o uso indiscriminado de `Blocked`.

---

## 19. Caminho crítico

Identificar itens que determinam o início do valor funcional.

Exemplo:

```text
OWNERSHIP
↓
REPOSITÓRIO
↓
WORKSPACE
↓
CI
↓
STAGING
↓
AUTH
↓
PRIMEIRA JORNADA
```

Um item importante pode não estar no caminho crítico.

Não usar prioridade como sinônimo de dependência.

---

## 20. Prioridade, marco e status são dimensões diferentes

Exemplo:

```text
PRIORIDADE: MUST
MARCO: M4
STATUS: BLOCKED
```

Isso é válido.

Uma capacidade pode ser essencial ao beta, mas depender de um gate que só será resolvido depois do core.

Evitar:

```text
“MUST”
→ implementar imediatamente
```

---

## 21. Marcos canônicos

A metodologia recomenda:

```text
M0
Fundação

M1...Mn
Marcos de entrega e aprendizado
```

`M0` é reservado para a fundação quando `09_Plano_de_Fundacao.md` se aplica.

A quantidade de marcos posteriores é específica do projeto.

Não copiar `M1-M6` de outro produto por hábito.

---

## 22. Marco não é sprint

Marco representa uma condição de produto/engenharia.

Sprint representa uma janela de trabalho.

Portanto:

```text
M2
pode durar 1, 2 ou 4 sprints
```

E:

```text
SPRINT 8
pode conter itens de dois marcos
somente se as dependências permitirem
```

A metodologia não obriga Scrum.

---

## 23. Estrutura mínima de um marco

Cada marco deve possuir:

```text
ID
Nome
Objetivo
Hipótese ou resultado
Itens principais
Público/coorte quando aplicável
Gate de entrada
Gate de saída
Evidência
Riscos
Critério de interrupção
```

Exemplo:

```text
M1 — Core funcional

Objetivo:
provar a principal jornada ponta a ponta

Entrada:
Foundation Gate aprovado

Saída:
jornada executável em staging,
sem perda de dado crítico,
com evidência de UX e operação
```

---

## 24. Regra de passagem entre marcos

Marco não abre apenas porque chegou uma data.

O fluxo é:

```text
GATE DE ENTRADA
        ↓
EVIDÊNCIA PRESENTE?
        ↓
OWNER CONFIRMOU?
        ↓
SIM
        ↓
MARCO ELEGÍVEL
```

Da mesma forma:

```text
DEPLOY FEITO
≠
MARCO ACEITO
```

Aceite depende da evidência definida.

---

## 25. Gates fazem parte do backlog

Um gate é um item operacional rastreável.

Exemplos:

```text
GAT-001 — autorização jurídica
GAT-002 — validação de provider
GAT-003 — prova de restore
GAT-004 — aceite UX
GAT-005 — autorização para dados reais
GAT-006 — decisão de release
```

Gate precisa declarar:

- condição;
- owner;
- evidência;
- itens bloqueados;
- data de reconfirmação quando fato externo envelhece;
- resultado.

---

## 26. Feature flag não substitui gate

```text
FEATURE FLAG
= controla exposição

GATE
= autoriza avanço
```

Uma feature pode estar implementada e desligada.

Isso não significa que seus requisitos jurídicos, de segurança ou de produto estejam atendidos.

---

## 27. Política de bloqueio

`Blocked` exige:

```text
CAUSA
OWNER
PRÓXIMA AÇÃO
CONDIÇÃO DE RETOMADA
```

Não usar:

```text
Blocked
“aguardando”
```

sem explicar o quê.

Bloqueio externo não deve ser mascarado como `In Progress`.

---

## 28. Status operacional mínimo

A taxonomia padrão é:

| Status | Definição |
| --- | --- |
| `Backlog` | Item canônico, ainda não elegível para execução imediata. |
| `Ready` | DoR satisfeito, dependências disponíveis e owner conhecido. |
| `In Progress` | Execução ativa com branch/PR/artefato vinculado quando aplicável. |
| `Blocked` | Dependência impede avanço e a causa está explícita. |
| `Review` | Artefato, código ou decisão aguarda validação. |
| `Done` | Aceite e evidências obrigatórias foram verificados. |
| `Superseded` | Outro item/decisão substituiu explicitamente este contrato. |
| `Removed` | Retirado por decisão canônica; ID permanece reservado. |

Projetos podem adicionar estados, mas devem manter semântica inequívoca.

---

## 29. Done não significa “mergeado”

Um item pode ter PR mergeado e ainda estar em:

```text
Review
```

ou:

```text
In Progress
```

se faltarem:

- staging;
- teste em dispositivo;
- restore;
- aceite visual;
- prova de integração;
- documentação;
- gate humano.

Regra:

> **Merge é evidência de alteração. Não é evidência suficiente de conclusão.**

---

## 30. Definition of Ready do item

Antes de `Ready`, verificar:

### Problema / objetivo

- usuário, ator ou habilitador está claro;
- resultado está claro;
- razão da prioridade está clara.

### Aceite

- critérios observáveis;
- regras sem contradição;
- estados de erro e recuperação relevantes.

### UX/UI

Quando visível:

- fluxo;
- estados;
- conteúdo;
- componentes/tokens;
- acessibilidade.

### Dados

Quando aplicável:

- entrada;
- saída;
- autoridade;
- sensibilidade;
- consentimento;
- retenção.

### Arquitetura

- boundary;
- contrato;
- consistência;
- idempotência;
- compatibilidade;
- ADR aplicável.

### Stack

- tecnologia aprovada;
- versão/política de versão;
- TDR aplicável.

### Infra

- ambiente disponível;
- segredo autorizado;
- provider aprovado;
- IDR aplicável.

### Risco

- segurança;
- privacidade;
- fraude;
- parceiro;
- offline;
- moderação;
- operação.

### Dependências

- dependências explícitas;
- gate explícito;
- owner disponível.

### Entrega

- evidência esperada;
- rollout;
- rollback;
- flag quando aplicável.

### IA

- escopo;
- invariantes;
- verificações;
- condição de parada.

---

## 31. Ready de produto, Ready técnico e Ready for Codex

A metodologia mantém distinções:

```text
READY DE PRODUTO
contexto suficiente para UX/técnica

READY TÉCNICO
arquitetura/stack/infra suficientes

READY DO ITEM
DoR da Issue satisfeito

READY FOR CODEX
item + baseline + matriz operacional
permitem execução assistida por IA
```

Na etapa 10, um item pode estar `Ready` operacionalmente.

Mas o processo como um todo ainda não está necessariamente `READY_FOR_CODEX` até a etapa 11.

---

## 32. Definition of Done do item

Aplicar de forma proporcional ao risco.

### Produto

- comportamento validado;
- critérios de aceite atendidos;
- outcome/hipótese atualizado quando aplicável.

### Código

- legível;
- tipado quando aplicável;
- modular;
- sem dependência proibida;
- revisão exigida concluída.

### Testes

- camadas adequadas ao risco;
- negativos quando necessários;
- retry/falha testados;
- flakiness tratada.

### UX / acessibilidade

- estados definidos;
- teclado/toque quando aplicável;
- contraste;
- zoom/text scale;
- reduced motion quando material;
- device/browser real quando exigido.

### Dados / API

- contrato;
- migration;
- autorização;
- idempotência;
- compatibilidade;
- retenção.

### Segurança

- threat model atualizado quando necessário;
- segredo protegido;
- dependência revisada;
- abuso relevante testado.

### Operação

- logs/métricas;
- dashboard;
- alerta;
- runbook;
- backup/restore quando afetado.

### Release

- flag/coorte;
- rollout;
- rollback;
- comunicação;
- changelog quando necessário.

### Documentação

- fonte canônica reconciliada se a realidade mudou.

### Evidência

- artefato, SHA, run, teste, screenshot, relatório ou aceite humano registrado conforme o contrato.

---

## 33. NFRs são herdados

Um NFR pode valer para dezenas de histórias.

Não copiar manualmente um texto enorme para cada Issue.

Usar ligação explícita:

```text
US-014
inherits:
  - NFR-001
  - NFR-004
  - NFR-011
```

A etapa 11 verificará se essa herança está coberta.

---

## 34. NFR não é checklist decorativo

Se um NFR é aplicável, sua prova precisa aparecer no DoD.

Exemplo:

```text
NFR-ACCESSIBILITY
        ↓
US-012
        ↓
DoD exige teclado + zoom + leitor
        ↓
EVIDÊNCIA
```

Sem evidência, o NFR continua aberto.

---

## 35. Correções emergenciais — COR

Falha comprovada durante execução pode gerar:

```text
COR-xxx
```

Ela deve registrar:

```text
problema comprovado
impacto
causa conhecida ou hipótese
itens afetados
prioridade
aceite
regressão
status
```

Correção pode interromper a sequência funcional quando o risco exigir.

Exemplo:

```text
US-007 READY
        ↓
COR-004 CRÍTICA DESCOBERTA
        ↓
US-007 PAUSA
        ↓
COR-004 FECHA
        ↓
SEQUÊNCIA RETORNA À US-007
```

Não renumerar histórias por causa disso.

---

## 36. Hotfix não remove governança

Um incidente pode justificar um fluxo menor.

Mas não justifica:

- remover controle de autorização;
- usar segredo em prompt;
- alterar banco sem plano;
- pular evidência mínima;
- esconder mudança de baseline.

Após estabilização, reconciliar documentação.

---

## 37. Recortes incrementais

História grande ou redesign brownfield pode exigir recortes menores.

Cada recorte precisa possuir:

```text
ID
parent
objetivo
preservar
melhorar
adiar
fontes
aceite
fora de escopo
dependências
evidência
```

Regra:

```text
RECORTE N
NÃO PODE ANTECIPAR
O ESCOPO DE N+1
```

Essa regra é particularmente importante em execução assistida por IA.

---

## 38. Um recorte pode ser documental

Nem todo recorte implementa código.

Exemplos:

```text
DISCOVERY FOCAL
AUDITORIA BROWNFIELD
CONTRATO
MAPA DE DADOS
POC
PLANO DE MIGRAÇÃO
```

Um recorte documental não deve ser marcado como implementação funcional concluída.

---

## 39. Evidência por item

A evidência esperada deve ser definida **antes** da execução.

Tipos possíveis:

```text
TESTE AUTOMATIZADO
TESTE MANUAL
STAGING
DEVICE REAL
BROWSER REAL
CI RUN
SHA
MIGRATION RESULT
PG TEST
SECURITY SCAN
RESTORE TEST
SCREENSHOT
VÍDEO
LOG REDIGIDO
DASHBOARD
ACEITE HUMANO
CONTRATO ASSINADO
VALIDAÇÃO LEGAL
```

Não exigir todos em todos os itens.

Exigir os necessários para provar o contrato.

---

## 40. Evidência local, hospedada e humana

Quando material, distinguir:

```text
LOCAL
prova de desenvolvimento

HOSTED
prova no ambiente relevante

HUMAN
aceite que automação não pode fornecer
```

Exemplo:

```text
TESTES LOCAIS VERDES
≠
ACEITE VISUAL EM STAGING
```

---

## 41. Deploy não significa aceite

O fluxo preferido:

```text
IMPLEMENTAÇÃO
        ↓
AUTOMAÇÃO
        ↓
DEPLOY CONTROLADO
        ↓
EVIDÊNCIA
        ↓
ACEITE NECESSÁRIO
        ↓
DONE
```

Se o item exige aceite humano, deploy apenas move o item para `Review`.

---

## 42. Modelo operacional no GitHub

No ambiente atualmente homologado pela metodologia:

```text
GITHUB ISSUES
= unidade operacional

GITHUB PROJECT
= ordem e estado

PULL REQUEST
= mudança revisável

ACTIONS
= prova automatizada

RELEASE / DEPLOYMENT
= evidência de promoção
```

Se outro tracker for adotado, deve preservar contratos equivalentes.

---

## 43. Campos obrigatórios da Issue

Modelo recomendado:

```markdown
# <ID> — <Título>

## Tipo
<Story | FND | COR | NFR | GAT | EXP | Slice>

## Épico / trilha
<referências>

## Marco
<Mx>

## Objetivo
<resultado observável>

## Escopo
- ...

## Fora de escopo
- ...

## Fontes canônicas
- DOC / seção
- ADR
- TDR
- IDR
- UX / UI

## Dependências
- ...

## Gates
- ...

## Critérios de aceite
- [ ] ...

## NFRs aplicáveis
- ...

## Evidência esperada
- ...

## Risco
- ...

## Rollout
- ...

## Rollback
- ...

## Condição de parada para IA
- ...
```

---

## 44. Labels

Labels devem servir filtragem, não substituir campos canônicos.

Famílias úteis:

```text
type:story
type:foundation
type:correction
type:nfr
type:gate
type:experiment
type:slice

priority:must
priority:must-gate
priority:should
priority:could

status:blocked
status:review

risk:security
risk:privacy
risk:data
risk:provider
risk:ux
risk:ops
```

Evitar dezenas de labels redundantes.

---

## 45. Project fields

Campos recomendados:

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

O texto completo do contrato permanece na Issue e nas fontes.

---

## 46. Milestones no GitHub

Milestone operacional pode refletir:

```text
M0
M1
M2
...
```

Não usar milestone para esconder dependências.

Um item só entra em `Ready` se suas condições reais estiverem disponíveis.

---

## 47. Fonte operacional de status

Depois da publicação da baseline:

```text
DOCUMENTOS
= intenção e contrato

GITHUB
= estado operacional
```

Portanto:

```text
Issue: Done
Documento: ainda diz “planejado”
```

não exige que todo documento histórico seja reescrito em tempo real.

Mas se a implementação **alterou a decisão**, a fonte canônica precisa ser reconciliada.

---

## 48. Reality update não reescreve história

Quando a execução revela algo diferente:

```text
BASELINE 1.0
        ↓
REALIDADE OBSERVADA
        ↓
DECISÃO
        ↓
BASELINE 1.1
```

Não apagar a baseline anterior como se nunca tivesse existido.

---

## 49. Controle de mudança da baseline

Quando um aprendizado altera contrato material:

1. identificar a fonte afetada;
2. classificar a mudança;
3. atualizar a fonte correta;
4. criar/superseder ADR, TDR ou IDR quando necessário;
5. atualizar item;
6. atualizar dependências;
7. atualizar gates;
8. atualizar testes;
9. atualizar rastreabilidade;
10. atualizar versão da baseline;
11. comunicar impacto em marco, risco, custo e release.

Nunca alterar apenas a Issue quando a decisão superior mudou.

---

## 50. Classificação de mudança

Sugestão:

```text
CORREÇÃO
realidade violava contrato existente

APRENDIZADO
nova evidência muda recomendação

MUDANÇA DE ESCOPO
produto decidiu mudar

MUDANÇA DE UX/UI
experiência canônica mudou

MUDANÇA ARQUITETURAL
ADR precisa mudar

MUDANÇA DE STACK
TDR precisa mudar

MUDANÇA DE INFRA
IDR precisa mudar
```

Cada classe possui fonte de autoridade diferente.

---

## 51. Brownfield

Em projeto existente, esta etapa precisa comparar:

```text
BACKLOG CANÔNICO NOVO
        vs
ISSUES EXISTENTES
        vs
CÓDIGO REAL
        vs
INCIDENTES
```

Classificar itens existentes:

```text
KEEP
já representa contrato válido

REWRITE
Issue existe, mas o contrato está incorreto

SPLIT
escopo grande demais

MERGE
itens duplicados

SUPERSEDE
nova decisão substitui

CLOSE_OBSOLETE
não é mais necessário

CREATE
lacuna real
```

Não recriar todas as Issues só para padronizar nomes.

---

## 52. Itens já implementados

Se a metodologia entra em um projeto existente, um item pode nascer como:

```text
Done — evidence imported
```

somente se houver prova suficiente.

Caso contrário:

```text
Review — evidence missing
```

Código existente sem evidência não recebe automaticamente status `Done`.

---

## 53. Segurança e informação sensível no tracker

Issues não devem receber:

- secret;
- token;
- dado pessoal real;
- credencial;
- conteúdo privado desnecessário;
- payload sensível;
- dump de produção.

Referenciar secret por nome lógico.

Evidência sensível deve permanecer em local autorizado.

---

## 54. Pública versus privada

Se o repositório for público:

- não publicar arquitetura sensível além do necessário;
- não publicar detalhes exploráveis de segurança antes de correção;
- não publicar contratos comerciais restritos;
- não publicar dados reais;
- não publicar credenciais;
- usar Issues privadas ou sistema separado quando necessário.

O backlog operacional pode precisar de uma superfície privada mesmo quando o código é público.

---

## 55. Plano de entrega

O plano deve equilibrar:

```text
DEPENDÊNCIA
RISCO
APRENDIZADO
VALOR
REVERSIBILIDADE
CUSTO
GATE
```

Evitar ordenar apenas por:

```text
“o que é mais fácil”
```

ou:

```text
“o que fica mais bonito na demo”
```

---

## 56. Ordem recomendada de raciocínio

Para sequenciar:

1. resolver bloqueadores fundacionais;
2. provar o principal caminho crítico;
3. fechar riscos irreversíveis cedo;
4. colocar aprendizado importante antes de investimento grande;
5. manter fatias verticais demonstráveis;
6. adiar complexidade sem evidência;
7. preservar gates de confiança;
8. manter rollback possível.

---

## 57. Vertical slice

Quando possível, preferir:

```text
pequeno comportamento real
UI
contrato
dado
segurança
teste
observabilidade
staging
```

em vez de:

```text
3 meses de backend
↓
2 meses de frontend
↓
integração no final
```

A fatia deve ser pequena sem destruir boundaries arquiteturais.

---

## 58. Não antecipar módulos bloqueados

Se um módulo depende de discovery, gate ou terceiro:

```text
MÓDULO BLOQUEADO
        ↓
NÃO INVENTAR PLACEHOLDER FUNCIONAL
NÃO INVENTAR DADO
NÃO INVENTAR API
NÃO CRIAR CONTRATO IRREVERSÍVEL
```

É permitido preparar infraestrutura genérica apenas quando ela já possui justificativa independente.

---

## 59. P1 e P2 permanecem visíveis

Itens fora do horizonte atual não devem desaparecer.

Mas também não competem com o P0.

Exemplo:

```text
P1-003
STATUS: Backlog
MILESTONE: Future
GATE: hipótese ainda não validada
```

---

## 60. Métricas de entrega

A etapa pode definir métricas operacionais como:

- lead time;
- cycle time;
- change fail rate;
- blocked time;
- rework;
- escaped defects;
- gate failure rate;
- restore success;
- flakiness;
- rollback rate.

Não usar:

- linhas de código;
- commits;
- número de PRs;
- tokens de IA;
- porcentagem de código gerado por IA

como métrica de produtividade individual.

---

## 61. Métricas de produto continuam vindo do PO

North Star, outcomes e guardrails não são reinventados aqui.

A etapa 10 apenas liga itens e marcos às métricas já aprovadas.

Exemplo:

```text
US-011
        ↓
OUT-003
        ↓
metric: qualified_action_rate
```

---

## 62. Regra para código assistido por IA

Mantém-se:

```text
IA PROPÕE
AUTOMAÇÃO VERIFICA
HUMANO RESPONDE
```

No backlog, isso vira contrato operacional.

O agente não pode:

- inventar dependência;
- inventar API;
- escolher stack fora do TDR;
- alterar arquitetura sem ADR;
- criar recurso cloud não aprovado;
- usar dado real;
- usar segredo em prompt;
- marcar o próprio trabalho como aceito quando exige humano;
- avançar além do item atual sem autorização da política operacional.

---

## 63. Condição de parada obrigatória

Uma Issue para IA deve dizer quando parar.

Exemplos:

```text
PARAR SE:
- requisito contraditório;
- migration irreversível não prevista;
- provider não disponível;
- secret ausente;
- gate fechado;
- dado real necessário;
- nova arquitetura necessária;
- teste crítico não pode ser executado;
- escopo extrapola o recorte;
- decisão humana é necessária.
```

---

## 64. Política de continuidade automática

A metodologia não assume continuidade automática por padrão.

Estados distintos:

```text
ITEM DONE
        ↓
PRÓXIMO ITEM READY
```

não significam necessariamente:

```text
INICIAR AUTOMATICAMENTE
```

O projeto pode escolher uma política:

```text
MANUAL
sempre aguardar autorização

SEMI_AUTOMATIC
continuar quando item estiver Ready e não houver gate humano

AUTOMATIC_WITH_GUARDS
continuar dentro de uma sequência previamente autorizada
```

Essa política precisa ser registrada.

---

## 65. Aprovação humana e automação

Atos que normalmente exigem humano:

- aceitar UX visual;
- aprovar release;
- aceitar risco residual;
- aceitar contrato comercial;
- liberar produção;
- autorizar dados reais;
- aprovar mudança de escopo;
- aprovar ADR/TDR/IDR material.

Automação pode comprovar fatos.

Ela não substitui autoridade humana quando o processo exige decisão.

---

## 66. Artefato estruturado opcional

Além do Markdown canônico, projetos podem gerar:

```text
CSV
XLSX
JSON
YAML
```

para:

- importação no GitHub;
- auditoria;
- filtros;
- dashboards;
- geração de Issues.

Esse artefato é **derivado**.

O documento canônico continua sendo a fonte normativa desta etapa.

---

## 67. Planilha não deve virar segunda baseline

Se existir planilha:

```text
MARKDOWN CANÔNICO
        ↓
GERAÇÃO / RECONCILIAÇÃO
        ↓
PLANILHA OPERACIONAL
```

Não manter duas fontes divergentes manualmente por meses.

Quando houver mudança relevante, regenerar ou reconciliar de forma rastreável.

---

## 68. Publicação das Issues

A criação de Issues é uma mutação operacional.

Portanto:

```text
ANÁLISE
↓
SÍNTESE
↓
REVISÃO HUMANA
↓
APROVAÇÃO DO BACKLOG
↓
AUTORIZAÇÃO DE PUBLICAÇÃO
↓
ISSUES / PROJECT / MILESTONES
```

Não publicar centenas de Issues antes do aceite do portfólio.

---

## 69. Baseline Freeze

Após aprovação desta etapa:

```text
IDs
MARCOS
DEPENDÊNCIAS
GATES
PRIORIDADES
FONTES
```

não devem mudar silenciosamente.

Mudança é permitida.

Mudança sem rastreabilidade não é.

---

## 70. Backlog Readiness

Estados:

```text
BACKLOG_READINESS: INSUFFICIENT
BACKLOG_READINESS: SUFFICIENT_WITH_OPEN_QUESTIONS
BACKLOG_READINESS: SUFFICIENT
```

`SUFFICIENT_WITH_OPEN_QUESTIONS` é válido quando:

- as pendências possuem owner;
- seus itens estão explicitamente bloqueados/deferidos;
- elas não impedem a auditoria da baseline restante.

---

## 71. Critérios para `SUFFICIENT`

A baseline está suficientemente pronta quando conseguimos responder:

1. quais são os épicos;
2. quais histórias pertencem ao horizonte atual;
3. quais FNDs existem;
4. quais NFRs são transversais;
5. quais gates bloqueiam avanço;
6. quais itens estão deferidos;
7. quais correções estão abertas;
8. quais IDs são estáveis;
9. qual item depende de qual;
10. qual é o caminho crítico;
11. quais marcos existem;
12. qual gate abre cada marco;
13. qual gate fecha cada marco;
14. qual é o próximo item elegível;
15. qual evidência fecha cada item;
16. quem é owner;
17. qual tracker será operacional;
18. como mudança de baseline funciona;
19. quais itens são seguros para execução por IA;
20. quais itens exigem ação humana.

---

## 72. Gates da etapa 10

| Gate | Evidência |
| --- | --- |
| `BL-01 Coverage` | Toda fonte anterior possui disposição explícita. |
| `BL-02 Identity` | IDs preservados, sem colisão ou reutilização indevida. |
| `BL-03 Reconciliation` | Tensões materiais possuem DEC ou resolução na fonte correta. |
| `BL-04 Dependency` | Grafo de dependências e caminho crítico identificados. |
| `BL-05 Milestones` | Marcos possuem entrada, saída e evidência. |
| `BL-06 Gates` | Bloqueios possuem owner, condição e retomada. |
| `BL-07 Item Contract` | Itens executáveis possuem objetivo, aceite, fontes e evidência. |
| `BL-08 NFR` | Requisitos transversais possuem herança visível. |
| `BL-09 AI Safety` | Itens elegíveis possuem limites e condição de parada. |
| `BL-10 Operations` | Modelo de GitHub, status e ownership definidos. |
| `BL-11 Change Control` | Política de atualização da baseline definida. |
| `BL-12 Handoff` | Material pronto para auditoria da Matriz Operacional. |

---

## 73. Síntese antes da canonização

Antes de gerar o artefato final do projeto, apresentar ao humano:

```text
PORTFÓLIO EXECUTÁVEL
ÉPICOS
STORIES
FNDs
NFRs
GATES
CORREÇÕES
DEFERRED
EXPERIMENTOS
DECISÕES DE RECONCILIAÇÃO
MARCOS
DEPENDÊNCIAS
CAMINHO CRÍTICO
BLOQUEIOS
ITENS READY
ITENS HUMAN-REQUIRED
POLÍTICA DE CONTINUIDADE
MODELO GITHUB
MUDANÇA DE BASELINE
PENDÊNCIAS
BACKLOG_READINESS
```

O humano pode:

- mudar prioridade;
- rejeitar um recorte;
- alterar marco;
- exigir gate;
- reabrir etapa anterior;
- corrigir dependência;
- remover item;
- adiar item;
- aprovar publicação operacional.

---

## 74. Aprovação e canonização

Fluxo:

```text
INVENTÁRIO
        ↓
NORMALIZAÇÃO
        ↓
RECONCILIAÇÃO
        ↓
SEQUENCIAMENTO
        ↓
SÍNTESE
        ↓
REVISÃO HUMANA
        ↓
CORREÇÕES
        ↓
APROVAÇÃO
        ↓
10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
```

A publicação de Issues pode ocorrer depois de autorização adicional quando necessário.

---

## 75. Estrutura mínima do artefato de projeto

O projeto deve produzir `10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md` com estrutura equivalente a:

```markdown
---
document_id: DOC-10
title: Backlog Canônico, Rastreabilidade e Plano de Entrega
status: canonical
version: 1.0.0
next_document: 11_Matriz_Operacional_de_Rastreabilidade.md
---

# Backlog Canônico, Rastreabilidade e Plano de Entrega

## 1. Decisão executiva
## 2. Baseline consumida
## 3. Hierarquia de autoridade
## 4. Método de canonização
## 5. Decisões de reconciliação
## 6. Taxonomia e gramática de IDs
## 7. Portfólio por épico
## 8. Histórias funcionais
## 9. Fundação / FNDs
## 10. Correções / CORs
## 11. NFRs
## 12. Gates
## 13. Experimentos e validações
## 14. Itens deferidos
## 15. Dependências
## 16. Caminho crítico
## 17. Marcos e plano de entrega
## 18. Gate de entrada/saída por marco
## 19. Modelo operacional de status
## 20. Definition of Ready
## 21. Definition of Done
## 22. Política para IA
## 23. Modelo de Issues e Project
## 24. Evidências
## 25. Controle de mudança
## 26. Brownfield, quando aplicável
## 27. Pendências
## 28. Backlog Readiness
## 29. Handoff para Matriz Operacional
```

A estrutura pode ser adaptada ao projeto sem perder os contratos essenciais.

---

## 76. O que não deve acontecer

### 76.1. Copiar documentos para Issues

Gera duplicação e divergência.

### 76.2. Issue sem fonte

```text
“fazer tela X”
```

sem contrato canônico não entra em `Ready`.

### 76.3. Story técnica fantasiada de produto

Não usar US apenas porque todo tracker conhece Story.

FND e NFR possuem semântica própria.

### 76.4. Gate escondido em comentário

Gate deve ser item/condição rastreável.

### 76.5. Dependência implícita

Ordem visual não substitui grafo.

### 76.6. Done por merge

Merge não fecha aceite operacional/humano automaticamente.

### 76.7. Backlog por calendário

Marco abre por gate, não por data arbitrária.

### 76.8. Renumerar história

Quebra rastreabilidade.

### 76.9. Corrigir só a Issue

Quando o contrato canônico mudou, atualizar a fonte certa.

### 76.10. Agente seguir para o próximo item por entusiasmo

Continuidade precisa respeitar política aprovada.

---

## 77. Relação com o Plano de Fundação

`09_Plano_de_Fundacao.md` define capacidades como:

```text
FND-001
FND-002
FND-003
...
```

A etapa 10 decide:

- marco;
- dependências cruzadas;
- prioridade operacional;
- gates;
- relação com as histórias;
- sequência real.

Assim:

```text
PLANO DE FUNDAÇÃO
= catálogo e ordem fundacional

BACKLOG CANÔNICO
= ordem global do produto
```

---

## 78. Relação com a Visão do Product Owner

A Visão de PO já possui histórias e outcomes.

A etapa 10 não reescreve produto.

Ela transforma:

```text
OUTCOME
↓
ÉPICO
↓
HISTÓRIA
```

em:

```text
HISTÓRIA
+
DEPENDÊNCIAS TÉCNICAS
+
NFRs
+
GATES
+
EVIDÊNCIA
+
MARCO
```

---

## 79. Relação com UX/UI

Um item visível deve apontar para o contrato UX/UI aplicável.

Exemplo:

```text
US-014
↓
UX-FLOW-008
↓
UI-SCR-012
↓
UI-CMP-004
```

A Issue não pode improvisar experiência diferente.

---

## 80. Relação com Engenharia e Arquitetura

Itens técnicos e funcionais devem respeitar:

- boundaries;
- invariantes;
- ADRs;
- consistência;
- contratos;
- requisitos de segurança;
- compatibilidade.

Uma Issue não possui autoridade para alterar boundary arquitetural silenciosamente.

---

## 81. Relação com Tech Lead

O backlog referencia:

- TDRs;
- stack aprovada;
- versões/políticas;
- toolchain;
- POCs relevantes.

Não cabe ao agente escolher framework alternativo porque parece mais conveniente para o item.

---

## 82. Relação com DevOps e Infraestrutura

Itens que afetem:

- ambiente;
- provider;
- pipeline;
- segredo;
- backup;
- observabilidade;
- custo;
- rollout

referenciam `INFRA-REQ`, `IDR` e FNDs aplicáveis.

---

## 83. Handoff para a Matriz Operacional

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
OWNERS
STATUS MODEL
CHANGE CONTROL
```

E deve responder:

> **Existe uma ligação auditável e completa entre cada decisão relevante da baseline e a forma como ela será implementada, testada, evidenciada e acompanhada operacionalmente?**

A etapa 11 não deve redesenhar o backlog por preferência.

Ela audita e fecha lacunas.

---

## 84. Princípio final

> **O backlog canônico não é uma lista de tarefas. É a tradução operacional da baseline aprovada. Cada item precisa saber de onde veio, o que libera, o que o bloqueia, como será provado e qual decisão deve ser reaberta se a realidade contrariar o plano.**

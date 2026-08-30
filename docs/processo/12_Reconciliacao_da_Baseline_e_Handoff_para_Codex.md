---
document_id: PROCESS-12-RECONCILIACAO-HANDOFF-CODEX
title: Reconciliação da Baseline e Handoff para Codex
status: draft-methodology
version: 0.1.0
stage: reconciliacao-handoff-codex
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
produces: 12_Reconciliacao_da_Baseline_e_Handoff_para_Codex.md
next_stage: Execução Canônica pelo Codex
---

# 12 — Reconciliação da Baseline e Handoff para Codex

## 1. Propósito

A etapa **Reconciliação da Baseline e Handoff para Codex** é o último checkpoint documental antes de permitir que um agente de implementação consuma o projeto como uma baseline executável.

Sua pergunta central é:

> **As decisões de produto, experiência, engenharia, arquitetura, tecnologia, infraestrutura, fundação, backlog e rastreabilidade formam um conjunto coerente, suficientemente completo e seguro para que o Codex execute o próximo item elegível sem precisar inventar intenção, regra ou tecnologia?**

Esta etapa não cria novas funcionalidades.

Ela não redesenha UX.

Ela não escolhe uma nova stack.

Ela não reorganiza arquitetura por preferência.

Ela não transforma pendência em decisão.

Ela verifica se a cadeia já aprovada pode ser executada sem ambiguidade material.

O resultado esperado é um estado explícito:

```text
BASELINE_READINESS: READY_FOR_CODEX
```

ou um bloqueio explícito:

```text
BASELINE_READINESS: NOT_READY_FOR_CODEX
```

Não existe estado implícito.

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
10 Backlog Canônico
        ↓
11 Matriz Operacional de Rastreabilidade
        ↓
12 RECONCILIAÇÃO DA BASELINE E HANDOFF PARA CODEX
        ↓
EXECUÇÃO CANÔNICA PELO CODEX
        ↓
FUNDAÇÃO / FATIAS FUNCIONAIS
        ↓
TESTES / EVIDÊNCIAS / STAGING
        ↓
ACEITE
        ↓
PRÓXIMO ITEM ELEGÍVEL
```

Até esta etapa, o ChatGPT atua predominantemente como facilitador de Discovery, pesquisa, síntese, especificação, reconciliação e planejamento.

Depois desta etapa, o Codex passa a consumir a baseline para implementar o que já foi decidido.

A fronteira é deliberada:

```text
CHATGPT
ajuda a definir e canonizar

CODEX
consome e executa
```

O Codex pode descobrir restrições reais durante a execução.

Ele não pode usar essa descoberta como autorização para reescrever silenciosamente a intenção do produto.

---

## 3. Princípio central do handoff

O Codex não recebe apenas uma tarefa solta.

Ele recebe uma cadeia rastreável:

```text
FONTE
   ↓
DECISÃO
   ↓
REGRA / JORNADA / REQUISITO
   ↓
ARQUITETURA
   ↓
TECNOLOGIA
   ↓
INFRAESTRUTURA
   ↓
ITEM DE BACKLOG
   ↓
TESTES
   ↓
EVIDÊNCIA ESPERADA
```

Portanto:

```text
“implemente a tela X”
```

não é handoff suficiente.

O handoff precisa permitir ao agente responder:

- por que este item existe?
- qual resultado ele busca?
- quais documentos são vinculantes?
- quais IDs ele implementa?
- quais regras não podem ser violadas?
- quais fluxos e estados são obrigatórios?
- quais decisões arquiteturais o limitam?
- qual stack foi aprovada?
- em qual infraestrutura essa stack opera?
- quais NFRs se aplicam?
- quais gates ainda estão abertos?
- quais ações exigem humano?
- quais testes são necessários?
- qual evidência demonstra conclusão?
- quando o agente deve parar?

---

## 4. A chave canônica de ativação do Codex

A metodologia define uma chave textual estável para iniciar a execução canônica:

```text
CODEX_CANONICAL_START_V1
```

Ela funciona como um **gatilho de protocolo**, não como uma senha nem como segredo.

A chave significa:

> Leia a baseline canônica deste projeto, confirme seu estado, consuma o backlog e a matriz de rastreabilidade, identifique o próximo item elegível e comece a execução seguindo exclusivamente as decisões aprovadas e as condições de parada documentadas.

### 4.1. Prompt recomendado de ativação

O humano pode iniciar uma sessão de Codex com:

```text
CODEX_CANONICAL_START_V1

Consuma a baseline canônica deste projeto conforme
12_Reconciliacao_da_Baseline_e_Handoff_para_Codex.md.

Leia as documentações do projeto na ordem definida pelo processo,
valide BASELINE_READINESS e execute o próximo item elegível do
10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md usando
11_Matriz_Operacional_de_Rastreabilidade.md para resolver todas as fontes,
restrições, testes, gates e evidências aplicáveis.

Não invente requisito, tecnologia, contrato, dado ou decisão.
Pare quando uma condição de parada ou gate humano for encontrada.
```

Uma versão curta também é válida:

```text
CODEX_CANONICAL_START_V1
Execute a baseline canônica deste projeto.
```

A versão curta só é suficiente quando o próprio projeto contém este documento e a baseline está marcada como `READY_FOR_CODEX`.

---

## 5. O que a chave autoriza

A chave autoriza o Codex a:

- iniciar o protocolo de leitura;
- verificar a baseline;
- identificar o item elegível;
- criar plano de execução do item;
- modificar o repositório dentro do escopo autorizado;
- executar verificações locais permitidas;
- criar ou atualizar testes necessários ao item;
- produzir evidências técnicas previstas;
- atualizar status operacional quando a política do projeto permitir;
- prosseguir para o próximo item quando a política de continuidade autorizar.

A chave **não** autoriza automaticamente:

- gasto financeiro não aprovado;
- compra de serviço;
- aceitar termos jurídicos em nome do owner;
- inserir cartão;
- usar credenciais pessoais;
- revelar ou registrar secrets;
- alterar produção sem gate;
- usar dados reais sem autorização;
- publicar em loja;
- alterar DNS crítico;
- revogar usuários reais;
- apagar recursos irreversivelmente;
- modificar produto, UX, arquitetura ou stack fora do item;
- criar uma integração não aprovada;
- ignorar um gate humano.

Logo:

```text
CODEX_CANONICAL_START_V1
≠
AUTORIZAÇÃO IRRESTRITA
```

---

## 6. Artefatos de projeto versus metodologia

O Codex deve consumir os **artefatos canônicos do projeto em execução**.

Ele não deve substituir os documentos do projeto pelos documentos genéricos do repositório da metodologia.

A metodologia ensina como produzir os documentos.

O projeto contém as decisões concretas.

Exemplo:

```text
METODOLOGIA
“o Tech Lead deve selecionar uma engine de banco
contra TECH-REQs.”

PROJETO
“TDR-004 selecionou PostgreSQL 17.”
```

Na execução, o documento de projeto é a fonte concreta.

---

## 7. Bootstrap obrigatório da sessão Codex

Ao receber `CODEX_CANONICAL_START_V1`, o agente deve executar um bootstrap antes de editar código.

### 7.1. Confirmar o repositório

Registrar:

```text
REPOSITORY
BRANCH
HEAD_SHA
WORKTREE_STATE
```

Se a branch estiver errada ou houver mudança local inesperada que possa conflitar com o item:

```text
STOP
```

até reconciliação.

### 7.2. Localizar a baseline

O agente deve localizar os artefatos canônicos declarados pelo projeto.

Preferencialmente:

```text
docs/
```

ou o diretório canônico explicitamente declarado.

Não presumir nomes diferentes sem evidência.

### 7.3. Ler o documento 12 primeiro

O primeiro documento operacional de bootstrap é:

```text
12_Reconciliacao_da_Baseline_e_Handoff_para_Codex.md
```

Ele informa:

- readiness;
- versão da baseline;
- commit de referência;
- documentos participantes;
- pendências aceitas;
- gates;
- política de continuidade;
- chave de ativação;
- regras de parada.

### 7.4. Ler a baseline canônica

Na primeira sessão de execução de uma baseline nova, o Codex deve ler os documentos canônicos na ordem declarada.

Padrão:

```text
00
01
02
03
Princípios
04
05
06
07
Tech Lead
08
09
10
11
12
```

A leitura não precisa carregar todos os documentos simultaneamente no mesmo contexto.

Ela pode ser sequencial.

Mas não pode ser substituída por adivinhação baseada apenas nos títulos.

### 7.5. Construir um índice interno da baseline

Após a leitura, o agente deve conseguir resolver pelo menos:

```text
DOC IDs
VERSÕES
STATUS
DECISÕES
BRs
JORNADAS
UI/UX
ADRs
TECH-REQs
TDRs
INFRA-REQs
IDRs
FNDs
NFRs
GATES
BACKLOG
TRACE IDs
```

Esse índice é memória operacional da sessão, não uma nova fonte canônica.

---

## 8. Leitura integral versus leitura por recorte

Há dois níveis.

### 8.1. Bootstrap da baseline

Em uma nova baseline ou nova sessão sem contexto confiável:

> ler os artefatos canônicos necessários para compreender o conjunto.

### 8.2. Execução de cada item

Para cada item, reler em detalhe somente as fontes aplicáveis apontadas pelo Backlog e pela Matriz.

Exemplo:

```text
US-014
        ↓
TRACE-0042
        ↓
BR-021
UX-FLOW-008
UI-SCR-012
ADR-006
TECH-REQ-012
TDR-004
NFR-003
GAT-006
```

O agente precisa reabrir essas fontes antes de implementar.

Isso evita dois erros:

```text
ERRO A
não ler a documentação

ERRO B
jogar toda a documentação no contexto
e perder o recorte da tarefa
```

---

## 9. Manifesto da baseline

Antes do handoff, o projeto deve produzir um manifesto dentro deste documento.

Estrutura recomendada:

```text
BASELINE_ID: BL-2026-08-30-01
BASELINE_VERSION: 1.0.0
BASELINE_COMMIT: <sha>
BASELINE_READINESS: READY_FOR_CODEX
BACKLOG_DOCUMENT: 10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
TRACE_DOCUMENT: 11_Matriz_Operacional_de_Rastreabilidade.md
HANDOFF_DOCUMENT: 12_Reconciliacao_da_Baseline_e_Handoff_para_Codex.md
CODEX_TRIGGER: CODEX_CANONICAL_START_V1
CONTINUATION_POLICY: AUTO_UNTIL_HUMAN_GATE
```

O commit deve apontar para uma versão em que todos os documentos participantes coexistam de forma consistente.

---

## 10. Estados de readiness

Usar somente:

```text
BASELINE_READINESS: NOT_READY_FOR_CODEX
BASELINE_READINESS: READY_WITH_EXPLICIT_BLOCKERS
BASELINE_READINESS: READY_FOR_CODEX
```

### NOT_READY_FOR_CODEX

Existe contradição ou lacuna que impede execução responsável.

### READY_WITH_EXPLICIT_BLOCKERS

A baseline é executável em partes, mas existem itens intencionalmente bloqueados.

Os itens livres podem avançar.

Os bloqueados precisam possuir:

- ID;
- causa;
- owner;
- próxima ação;
- condição de retomada.

### READY_FOR_CODEX

O backlog elegível pode ser executado sem inventar decisões.

Isso não significa que todos os itens do produto estão liberados.

Um projeto pode estar `READY_FOR_CODEX` e conter vários itens `BLOCKED`.

---

## 11. Reconciliação da baseline

Antes de declarar readiness, executar uma auditoria transversal.

### 11.1. Produto

Verificar:

- promessa;
- público;
- core;
- P0/P1/P2;
- fora de escopo;
- outcomes;
- regras críticas;
- hipóteses;
- gates.

Nenhuma Issue pode contradizer essas decisões silenciosamente.

### 11.2. UX/UI

Verificar:

- jornadas;
- estados;
- erros;
- recuperação;
- acessibilidade;
- responsividade por form factor;
- visual states;
- design tokens;
- referências válidas;
- ausência de dados fictícios tratados como runtime.

### 11.3. Engenharia e arquitetura

Verificar:

- drivers;
- quality attributes;
- boundaries;
- invariantes;
- dados canônicos;
- consistência;
- idempotência;
- offline/sync;
- integrações;
- trust boundaries;
- ADRs;
- TECH-REQs.

### 11.4. Tech Lead

Verificar:

- todas as tecnologias concretas necessárias ao item inicial;
- versões aprovadas;
- TDRs;
- licenças;
- compatibilidade;
- política de atualização;
- POCs exigidas.

### 11.5. DevOps e Infraestrutura

Verificar:

- ambientes;
- providers;
- identidade;
- secrets;
- deploy;
- rollback;
- observabilidade;
- backup/restore;
- custos;
- ownership;
- IDRs;
- INFRA-REQs.

### 11.6. Fundação

Verificar:

- FNDs;
- dependências;
- caminho crítico;
- ações humanas;
- gates de fundação;
- runway;
- evidências.

### 11.7. Backlog

Verificar:

- IDs únicos;
- status;
- dependências;
- prioridade;
- milestone;
- DoR;
- DoD;
- owner;
- gates;
- rollback;
- evidência esperada;
- stop condition.

### 11.8. Matriz

Verificar:

- requisitos órfãos;
- implementações órfãs conhecidas;
- cobertura documental;
- TRACE IDs;
- NFRs herdados;
- testes previstos;
- evidências;
- supersessões;
- itens removidos.

---

## 12. Regra contra contradição silenciosa

Quando duas fontes divergem:

```text
NÃO ESCOLHER UMA NO SILÊNCIO
```

Aplicar:

```text
CONTRADIÇÃO
        ↓
IDENTIFICAR AUTORIDADE
        ↓
EXISTE DEC-xxx?
        ↓
SIM → aplicar
NÃO  → bloquear reconciliação
```

Se uma contradição material não possui resolução canônica:

```text
BASELINE_READINESS: NOT_READY_FOR_CODEX
```

---

## 13. Pendências aceitáveis

Uma baseline não precisa eliminar toda incerteza do universo.

Pendências podem permanecer quando:

- não afetam o próximo trabalho elegível;
- possuem ID;
- possuem owner;
- possuem gate;
- possuem momento de resolução;
- não exigem que o agente invente comportamento.

Exemplo:

```text
SOC-DISC-01
BLOCKED
Owner: Product Owner
Retomar antes de qualquer feature social real
```

Isso não precisa impedir uma história independente de autenticação.

---

## 14. Escolha do próximo item

Depois do bootstrap, o Codex deve resolver o próximo item executável pelo Backlog Canônico.

Um item só é elegível quando:

```text
STATUS = READY
+
DEPENDÊNCIAS SATISFEITAS
+
GATES DE ENTRADA SATISFEITOS
+
MILESTONE ABERTO
+
BASELINE APLICÁVEL
+
AÇÃO HUMANA NÃO PENDENTE PARA O INÍCIO
```

Prioridade sozinha não basta.

Exemplo:

```text
US-025
priority: MUST
status: BLOCKED

US-007
priority: MUST
status: READY
```

O agente executa `US-007`.

---

## 15. Ordem entre Fundação e funcionalidades

O Backlog Canônico governa a ordem real.

Não assumir:

```text
“feature visual é mais interessante,
logo começo por ela”
```

Se o próximo item elegível for:

```text
FND-003
```

é esse o trabalho.

A fundação é parte do backlog executável.

---

## 16. Handshake obrigatório do Codex

Antes da primeira alteração de cada item, o agente deve produzir um handshake operacional curto.

Formato:

```text
CODEX_PROCESS: ACTIVE
TRIGGER: CODEX_CANONICAL_START_V1
BASELINE_ID: <id>
BASELINE_COMMIT: <sha>
BASELINE_READINESS: <estado>
CURRENT_ITEM: <id>
ITEM_STATUS: READY
MILESTONE: <id>
TRACE: <ids>
DEPENDENCIES: SATISFIED
ENTRY_GATES: SATISFIED
HUMAN_ACTION_REQUIRED_NOW: NO
EXPECTED_EVIDENCE: <resumo>
STOP_CONDITIONS: <resumo>
```

Se qualquer campo crítico não puder ser preenchido sem inventar:

```text
STOP
```

---

## 17. Pacote mínimo de contexto do item

Antes de codificar, o Codex deve montar um pacote de execução contendo:

```text
ITEM ID
OBJETIVO
OUTCOME
ESCOPO
FORA DE ESCOPO
FONTES CANÔNICAS
TRACE IDs
REGRAS DE NEGÓCIO
JORNADAS / ESTADOS UX
UI APLICÁVEL
ADRs
TECH-REQs
TDRs
INFRA-REQs
IDRs
NFRs
DEPENDÊNCIAS
GATES
TESTES
EVIDÊNCIA ESPERADA
ROLLOUT
ROLLBACK
CONDIÇÕES DE PARADA
```

Esse pacote não substitui as fontes.

Ele apenas delimita o recorte.

---

## 18. Plano antes da mutação

Para itens não triviais, o agente deve apresentar um plano curto antes de editar.

Exemplo:

```text
1. localizar contrato atual
2. criar teste que prova o comportamento esperado
3. implementar a menor mudança
4. executar testes focados
5. executar gates canônicos
6. validar build
7. produzir evidência
8. atualizar rastreabilidade operacional
```

O plano não pode aumentar escopo.

---

## 19. Condições de parada globais

O Codex deve parar quando:

- falta requisito necessário;
- duas fontes canônicas contradizem-se sem DEC;
- tecnologia necessária não foi aprovada;
- precisa mudar ADR/TDR/IDR fora do item;
- uma API ou provider não foi verificado;
- seria necessário inventar schema;
- seria necessário criar regra de negócio;
- seria necessário usar dado real não autorizado;
- precisa de secret ausente;
- precisa de ação humana;
- um gate está fechado;
- a mudança ultrapassa o escopo da Issue;
- o risco mudou materialmente;
- a prova esperada não pode ser produzida;
- surgiu possível incidente de segurança;
- a alteração exigiria operação destrutiva não autorizada;
- o estado observado do sistema contradiz a baseline de forma material.

A resposta correta nesses casos é expor o bloqueio.

Não improvisar.

---

## 20. Descoberta durante execução

O Codex pode descobrir realidade que não estava conhecida na documentação.

Classificar:

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

Pode ser resolvido dentro do item quando não muda contrato.

### DEFECT

Pode gerar `COR-xxx` quando comprovado e material.

### NEW_CONSTRAINT

Pode exigir atualização técnica ou gate.

### ARCHITECTURAL_IMPACT

Reabrir documento 07 e ADR aplicável.

### PRODUCT_IMPACT

Reabrir a fonte de produto apropriada.

### SECURITY_INCIDENT

Aplicar protocolo de segurança e interromper trabalho incompatível.

### EXTERNAL_CHANGE

Rever provider, API, preço, licença, política ou contrato.

---

## 21. O Codex não canoniza decisões de produto sozinho

Durante implementação, o agente pode sugerir:

```text
“para resolver X, existem A e B.”
```

Mas não pode converter automaticamente:

```text
SUGESTÃO
→ DECISÃO CANÔNICA
```

Se a escolha muda comportamento, escopo, arquitetura ou risco material:

```text
STOP
→ decisão humana
→ atualizar fonte adequada
→ reconciliar
→ retomar
```

---

## 22. Política de continuidade

O projeto deve escolher uma política.

Valores recomendados:

```text
MANUAL_EACH_ITEM
AUTO_AFTER_VERIFIED_DONE
AUTO_UNTIL_HUMAN_GATE
```

### MANUAL_EACH_ITEM

Cada novo item exige autorização humana.

### AUTO_AFTER_VERIFIED_DONE

Quando o item chega a Done com evidência, o próximo Ready pode iniciar automaticamente.

### AUTO_UNTIL_HUMAN_GATE

O agente continua por itens elegíveis e para somente em gate humano, bloqueio material ou condição de parada.

A metodologia recomenda que essa política seja declarada no manifesto da baseline.

Não inferir.

---

## 23. Continuidade não significa execução paralela indiscriminada

Mesmo quando a política é automática, respeitar:

- dependências;
- conflitos de arquivos;
- migrations;
- limites operacionais;
- gates;
- capacidade de revisão;
- risco.

Não abrir dez mudanças simultâneas só porque estão `Ready`.

Preferir fatias pequenas e verificáveis.

---

## 24. Relação com GitHub Issues e Project

Quando o projeto usa GitHub como superfície operacional:

```text
DOC 10
= contrato do backlog

DOC 11
= ligação entre as camadas

ISSUE
= unidade executável

PROJECT
= ordem/status

PR
= mudança

CI
= prova automatizada

DEPLOYMENT
= prova hospedada
```

A Issue deve referenciar o ID canônico.

O status no Project não redefine o documento silenciosamente.

---

## 25. Regra de source-of-truth durante execução

Aplicar:

```text
DOCUMENTO CANÔNICO
> Issue resumida
> comentário
> prompt ad hoc
> inferência do agente
```

Quando existir fonte legal, política de plataforma ou controle de segurança mais restritivo, ela continua bloqueando interpretação incompatível.

---

## 26. Evidência de execução

Cada item deve declarar antes da implementação que evidência será esperada.

Possibilidades:

- teste unitário;
- contract test;
- integration test;
- E2E;
- build;
- lint/typecheck;
- migration proof;
- screenshot hospedado quando visual;
- vídeo curto quando interação exigir;
- device real;
- browser real;
- smoke HTTP;
- log sanitizado;
- métrica;
- restore test;
- runbook exercise;
- aceite humano;
- deployment imutável;
- commit SHA;
- CI run.

Não coletar evidência sensível desnecessária.

---

## 27. Maturidade da evidência

Usar, quando útil:

```text
EXPECTED
LOCAL_VERIFIED
CI_VERIFIED
STAGING_VERIFIED
HUMAN_ACCEPTED
PRODUCTION_OBSERVED
```

O item define qual nível é necessário para `Done`.

---

## 28. Atualização da rastreabilidade durante execução

Ao concluir um item, registrar os vínculos reais:

```text
ITEM
→ PR
→ COMMIT
→ TESTS
→ CI
→ DEPLOYMENT
→ EVIDENCE
→ ACCEPTANCE
```

Não criar uma segunda matriz em XLSX.

A fonte canônica permanece em Markdown e/ou em referências operacionais versionadas que o Markdown indexa.

---

## 29. Baseline Freeze

Quando o handoff é aprovado, registrar:

```text
BASELINE_FREEZE: ACTIVE
```

Isso significa:

- documentos têm versões conhecidas;
- IDs estão estabilizados;
- backlog elegível possui significado conhecido;
- agentes não podem alterar intenção silenciosamente.

Não significa que o produto nunca mais muda.

Mudança material segue controle de versão e reconciliação.

---

## 30. Mudança após o handoff

Fluxo:

```text
EXECUÇÃO
        ↓
NOVA EVIDÊNCIA / DECISÃO
        ↓
QUAL FONTE É AUTORIDADE?
        ↓
ATUALIZAR FONTE
        ↓
ATUALIZAR BACKLOG
        ↓
ATUALIZAR MATRIZ
        ↓
RECONCILIAR 12
        ↓
NOVA BASELINE VERSION
        ↓
RETOMAR CODEX
```

Nunca corrigir apenas o prompt do agente quando a mudança é canônica.

---

## 31. Versão da baseline

Sugestão:

```text
1.0.0
```

Mudanças:

- PATCH: esclarecimento sem mudar contrato;
- MINOR: novo item compatível, novo recorte ou decisão adicionada;
- MAJOR: mudança incompatível de produto, arquitetura, dados ou operação.

A política pode ser adaptada pelo projeto.

---

## 32. Brownfield

Em projeto existente, antes de `READY_FOR_CODEX` verificar também:

- estado real do código;
- migrations já aplicadas;
- recursos hospedados;
- branches;
- CI real;
- secrets existentes;
- rotas;
- APIs;
- contratos;
- incidentes conhecidos;
- divergências entre documentação e runtime.

Classificar divergências:

```text
DOC_OUTDATED
CODE_OUT_OF_CONTRACT
KNOWN_DEBT
INTENTIONAL_COMPATIBILITY
UNKNOWN
```

`UNKNOWN` material bloqueia o handoff.

---

## 33. Greenfield

Em projeto novo, a reconciliação precisa provar pelo menos:

- qual é o primeiro FND;
- onde o repositório será criado;
- quais tecnologias foram aprovadas;
- qual ambiente inicial é permitido;
- quais segredos serão necessários, sem seus valores;
- qual é o primeiro gate;
- qual item funcional só poderá iniciar depois da fundação mínima.

Não é obrigatório provisionar tudo antes de declarar o plano pronto.

---

## 34. Verificação de código existente sem requisito

Antes do handoff brownfield, usar a Matriz para detectar:

```text
ORPHAN_IMPLEMENTATION
```

Esses casos precisam ser:

```text
MAPEADOS
ACEITOS COMO LEGADO
ENCAPSULADOS
REMOVIDOS
OU TRANSFORMADOS EM ITEM DE RECONCILIAÇÃO
```

Código inexplicável não deve virar regra automaticamente.

---

## 35. Verificação de requisito sem execução

Detectar:

```text
ORPHAN_REQUIREMENT
```

Cada requisito material precisa possuir ao menos uma disposição:

```text
ITEM
GATE
DEFERRED
BLOCKED
NOT_APPLICABLE
SUPERSEDED
REMOVED
```

---

## 36. Gates mínimos do handoff

| Gate | Pergunta |
| --- | --- |
| HOFF-01 Baseline | Todos os documentos canônicos necessários existem e possuem versão/status? |
| HOFF-02 Authority | Contradições materiais possuem resolução ou autoridade inequívoca? |
| HOFF-03 Backlog | Existe ao menos um item elegível ou bloqueios estão explicitamente justificados? |
| HOFF-04 Trace | Itens executáveis resolvem suas fontes pela matriz? |
| HOFF-05 Architecture | ADRs e requisitos arquiteturais aplicáveis estão definidos? |
| HOFF-06 Stack | Tecnologias concretas necessárias foram aprovadas? |
| HOFF-07 Infra | Requisitos de execução do item inicial possuem decisão suficiente? |
| HOFF-08 Foundation | Fundação necessária ao item possui FNDs e gates claros? |
| HOFF-09 Quality | NFRs, testes e evidências esperadas estão definidos? |
| HOFF-10 Security | Secrets, dados, autorização e condições humanas estão protegidos? |
| HOFF-11 AI Scope | Cada item possui condição de parada e escopo suficiente para agente? |
| HOFF-12 Continuity | Política de continuidade foi declarada explicitamente? |

Qualquer gate material não atendido impede `READY_FOR_CODEX`.

---

## 37. Auditoria final antes da canonização

O ChatGPT deve apresentar uma síntese semelhante a:

```text
BASELINE ID
BASELINE VERSION
DOCUMENTOS CANÔNICOS
CONTRADIÇÕES RESOLVIDAS
CONTRADIÇÕES ABERTAS
REQUISITOS ÓRFÃOS
IMPLEMENTAÇÕES ÓRFÃS
ITENS READY
ITENS BLOCKED
GATES HUMANOS
STACK STATUS
INFRA STATUS
FOUNDATION STATUS
TRACE COVERAGE
SECURITY STATUS
NEXT ELIGIBLE ITEM
CONTINUATION POLICY
BASELINE_READINESS
```

O humano revisa antes da canonização final.

---

## 38. Estrutura mínima do artefato de projeto

O projeto deve produzir `12_Reconciliacao_da_Baseline_e_Handoff_para_Codex.md` com estrutura equivalente a:

```markdown
---
document_id: DOC-12
status: canonical
version: 1.0.0
baseline_id: BL-...
baseline_commit: <sha>
baseline_readiness: READY_FOR_CODEX
codex_trigger: CODEX_CANONICAL_START_V1
continuation_policy: AUTO_UNTIL_HUMAN_GATE
---

# Reconciliação da Baseline e Handoff para Codex

## 1. Manifesto da baseline
## 2. Documentos canônicos e versões
## 3. Hierarquia de autoridade
## 4. Contradições e DEC aplicadas
## 5. Pendências aceitas
## 6. Requisitos órfãos
## 7. Implementações órfãs
## 8. Cobertura da matriz
## 9. Estado do backlog
## 10. Estado da fundação
## 11. Stack e infraestrutura aprovadas
## 12. Gates humanos
## 13. Segurança e dados
## 14. Política de continuidade
## 15. Próximo item elegível
## 16. Pacote inicial de contexto
## 17. Condições de parada
## 18. Handoff handshake
## 19. Baseline Readiness
```

---

## 39. Exemplo de manifesto pronto

```text
BASELINE_ID: BL-2026-08-30-01
BASELINE_VERSION: 1.0.0
BASELINE_COMMIT: 1234567890abcdef
BASELINE_READINESS: READY_FOR_CODEX
CODEX_TRIGGER: CODEX_CANONICAL_START_V1
CONTINUATION_POLICY: AUTO_UNTIL_HUMAN_GATE
NEXT_ELIGIBLE_ITEM: FND-001
HUMAN_GATE_BEFORE_START: NO
```

---

## 40. Exemplo de bootstrap do Codex

Entrada humana:

```text
CODEX_CANONICAL_START_V1
Execute a baseline canônica deste projeto.
```

Resposta esperada do agente antes de alterar arquivos:

```text
CODEX_PROCESS: ACTIVE
BASELINE_ID: BL-2026-08-30-01
BASELINE_COMMIT: 1234567890abcdef
BASELINE_READINESS: READY_FOR_CODEX
CURRENT_ITEM: FND-001
DEPENDENCIES: SATISFIED
ENTRY_GATES: SATISFIED
HUMAN_ACTION_REQUIRED_NOW: NO
TRACE: TRACE-0001, TRACE-0002
STOP_CONDITIONS: loaded
EXPECTED_EVIDENCE: ownership manifest + access verification

Vou executar FND-001 dentro deste escopo.
```

Só então a mutação começa.

---

## 41. Quando a chave deve falhar

Se o humano enviar:

```text
CODEX_CANONICAL_START_V1
```

mas o projeto não possui baseline válida, o agente deve responder com um bloqueio objetivo.

Exemplo:

```text
CODEX_PROCESS: BLOCKED
BASELINE_READINESS: NOT_READY_FOR_CODEX
REASON: 10_Backlog_Canonico... não encontrado
NEXT_ACTION: concluir/canonizar a baseline antes da implementação
```

A chave não serve para pular o processo.

---

## 42. AGENTS / instruções de repositório

Quando o ambiente de desenvolvimento utilizado pelo projeto oferecer um mecanismo de instruções persistentes para agentes no próprio repositório, a metodologia recomenda materializar um loader mínimo que aponte para este documento.

Exemplo conceitual:

```text
Ao receber CODEX_CANONICAL_START_V1:
1. leia DOC-12;
2. valide BASELINE_READINESS;
3. carregue DOC-10 e DOC-11;
4. resolva o próximo item;
5. leia as fontes rastreadas;
6. aplique as stop conditions;
7. só então modifique código.
```

Esse loader não deve duplicar a baseline.

Ele apenas aponta para ela.

Se o repositório possuir `AGENTS.md` ou mecanismo equivalente aprovado, ele pode conter essa instrução curta.

A fonte canônica continua sendo a documentação do projeto.

---

## 43. Regra contra duplicação do processo no prompt

Não copiar milhares de linhas da documentação para cada prompt do Codex.

Preferir:

```text
CODEX_CANONICAL_START_V1
CURRENT_ITEM: US-014
```

O agente resolve as fontes pelo repositório.

Se toda regra precisar ser repetida manualmente no prompt, o handoff não está funcionando.

---

## 44. Regra de atualização do item atual

Ao iniciar:

```text
READY → IN_PROGRESS
```

somente quando a superfície operacional autorizada estiver disponível.

Ao bloquear:

```text
IN_PROGRESS → BLOCKED
```

registrar:

- causa;
- evidência;
- owner;
- próxima ação;
- condição de retomada.

Ao concluir:

```text
IN_PROGRESS → REVIEW → DONE
```

ou fluxo equivalente definido pelo projeto.

---

## 45. Done do item e continuidade

Antes de considerar `Done`, verificar:

```text
ACEITE FUNCIONAL
TESTES
NFRs
SEGURANÇA
BUILD
OPERAÇÃO
DOCUMENTAÇÃO
EVIDÊNCIA
TRACE
```

Somente depois aplicar a política de continuidade.

---

## 46. Falha de teste durante execução

Teste falhando pode significar:

```text
IMPLEMENTAÇÃO ERRADA
TESTE DESATUALIZADO
BASELINE CONTRADITÓRIA
AMBIENTE INDISPONÍVEL
DEFEITO PRÉ-EXISTENTE
```

Não apagar teste apenas para ficar verde.

Classificar a causa.

Se o teste representa requisito canônico, corrigir implementação.

Se o requisito mudou, atualizar a fonte antes.

---

## 47. Dependência externa

Quando um item depende de terceiro:

```text
NÃO INVENTAR RESPOSTA
NÃO SIMULAR APROVAÇÃO
NÃO MARCAR DONE
```

Registrar `BLOCKED` ou executar apenas a parte explicitamente permitida.

---

## 48. Dados e privacidade no Codex

O agente deve operar, por padrão, com:

- dados sintéticos;
- fixtures;
- contas de teste;
- secrets via store autorizado;
- logs sanitizados.

Nunca incluir segredo em:

- prompt;
- commit;
- issue;
- documentação;
- screenshot;
- fixture;
- log persistido.

---

## 49. Produção

A existência da chave de handoff não libera produção.

Produção continua governada por gates próprios.

Exemplo:

```text
CODEX_CANONICAL_START_V1
+
GAT-PROD CLOSED
=
NÃO PUBLICAR EM PRODUÇÃO
```

---

## 50. Rastreabilidade do próprio handoff

O handoff pode possuir IDs:

```text
HOFF-xxx
```

Exemplos:

```text
HOFF-001 baseline reconciliada
HOFF-002 backlog validado
HOFF-003 trace coverage aprovada
HOFF-004 security gate aprovado
HOFF-005 Codex trigger habilitado
```

---

## 51. Handoff readiness

Usar:

```text
HANDOFF_READINESS: INSUFFICIENT
HANDOFF_READINESS: SUFFICIENT_WITH_BLOCKERS
HANDOFF_READINESS: SUFFICIENT
```

`SUFFICIENT_WITH_BLOCKERS` é válido quando há trabalho elegível independente dos bloqueios.

---

## 52. Aprovação humana final

A etapa deve terminar com um ato explícito de aprovação.

Exemplo:

```text
BASELINE APPROVED FOR CODEX EXECUTION
```

ou equivalente inequívoco.

Sem isso:

```text
BASELINE_READINESS
```

pode estar tecnicamente suficiente, mas o agente não deve assumir autorização de execução.

---

## 53. Estado final recomendado

```text
BASELINE_READINESS: READY_FOR_CODEX
HANDOFF_READINESS: SUFFICIENT
BASELINE_FREEZE: ACTIVE
CODEX_TRIGGER: CODEX_CANONICAL_START_V1
EXECUTION_AUTHORIZATION: APPROVED
CONTINUATION_POLICY: <valor aprovado>
```

---

## 54. Resultado esperado da metodologia

A metodologia completa produz uma transformação:

```text
IDEIA
        ↓
CONVERSA E DESCOBERTA
        ↓
EVIDÊNCIA
        ↓
DECISÃO DE PRODUTO
        ↓
EXPERIÊNCIA
        ↓
ENGENHARIA
        ↓
ARQUITETURA
        ↓
TECNOLOGIA
        ↓
INFRAESTRUTURA
        ↓
FUNDAÇÃO
        ↓
BACKLOG
        ↓
RASTREABILIDADE
        ↓
BASELINE RECONCILIADA
        ↓
CODEX_CANONICAL_START_V1
        ↓
EXECUÇÃO VERIFICÁVEL
```

O objetivo não é impedir o agente de pensar.

É impedir que ele precise adivinhar decisões que deveriam ter sido tomadas antes da implementação.

---

## 55. Princípio final

> **ChatGPT ajuda a transformar intenção em uma baseline canônica. O Codex não recebe a intenção bruta: recebe a baseline, lê suas fontes, resolve o próximo item pelo backlog e pela rastreabilidade, implementa apenas o que foi autorizado e devolve código, testes e evidências para que a realidade possa ser reconciliada novamente com a documentação.**

E a chave que abre essa fronteira é deliberadamente simples:

```text
CODEX_CANONICAL_START_V1
```

Simples de acionar.

Difícil de interpretar errado.

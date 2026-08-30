# Exemplos da metodologia

## Estado atual

Os exemplos oficiais desta metodologia devem reproduzir o processo **como trabalho real**, etapa por etapa.

A pasta existente:

```text
examples/ava-omem/
```

foi criada em uma iteração anterior da metodologia.

Ela permanece no repositório apenas como **evidência histórica / material legado** até ser migrada ou substituída.

Ela não deve ser usada por ChatGPT, Codex ou leitor humano como demonstração normativa da sequência atual.

---

## O que caracteriza um exemplo válido

Um exemplo atual não é uma coleção de documentos preenchidos retrospectivamente.

Ele precisa simular o trabalho real:

```text
ATIVAÇÃO DO PROCESSO
↓
ETAPA ATUAL
↓
CONVERSA / INVESTIGAÇÃO
↓
PROPOSTA DO CHATGPT
↓
REVISÃO HUMANA
↓
AJUSTES
↓
APROVAÇÃO
↓
CANONIZAÇÃO DO DOCUMENTO
↓
PRÓXIMA ETAPA
```

A etapa seguinte não deve ser produzida antes de a anterior estar suficientemente revisada e aprovada no cenário simulado.

---

## Regras obrigatórias para novos exemplos

1. seguir a ordem definida em `docs/processo/PROCESS_MANIFEST.md`;
2. gerar um documento por vez;
3. registrar o contexto que entrou em cada etapa;
4. mostrar perguntas e decisões materiais, sem transformar o exemplo em transcrição desnecessariamente longa;
5. separar hipótese, evidência, recomendação e decisão humana;
6. executar pesquisa atual quando a etapa depender de fatos mutáveis;
7. representar retornos ao cliente, owner ou stakeholder quando o cenário exigir aprovação externa;
8. não antecipar stack antes da Visão do Tech Lead;
9. não antecipar provider/operação antes de DevOps e Infraestrutura;
10. produzir Backlog, Matriz e Handoff somente depois das camadas anteriores;
11. manter todos os artefatos canônicos em Markdown;
12. concluir o cenário documental com o protocolo `CODEX_CANONICAL_START_V1` quando a baseline estiver realmente elegível.

---

## Estrutura recomendada de um caso

```text
examples/<caso>/
  README.md
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
  evidencias/
```

O diretório `evidencias/` é opcional e pode conter apenas materiais adequados ao repositório.

Segredos, dados pessoais reais ou material confidencial não devem ser incluídos.

---

## Casos brownfield

Quando o exemplo partir de um sistema existente, o cenário precisa mostrar explicitamente:

- o que já existia;
- o que é evidência operacional;
- o que foi preservado;
- o que foi considerado bug;
- o que precisou de reconciliação;
- por que uma mudança não foi tratada como reescrita total.

---

## Casos contratados por cliente

Quando houver cliente real ou simulado, o exemplo deve representar o ciclo de validação:

```text
ANALISTA / CONSULTORIA
↓
DISCOVERY
↓
PESQUISA / ANÁLISE
↓
PROPOSTA
↓
CLIENTE REVISA
↓
AJUSTES
↓
CLIENTE APROVA
↓
CANONIZAÇÃO
```

A aprovação da consultoria não substitui a aprovação do cliente quando a decisão pertence ao cliente.

---

## Objetivo dos casos

Os casos de uso existem para testar a própria metodologia.

Quando um caso revelar:

- etapa redundante;
- pergunta ausente;
- fronteira de responsabilidade confusa;
- documentação difícil de consumir;
- handoff insuficiente;
- excesso de processo;
- lacuna de rastreabilidade;

isso deve ser tratado como evidência para revisar a metodologia antes de declarar uma versão estável.
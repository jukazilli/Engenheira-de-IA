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

Ele precisa **executar a metodologia de verdade sobre um cenário simulado**.

O cenário, o cliente e as aprovações podem ser simulados; a execução do processo não é resumida nem reconstruída depois.

A regra é:

```text
ATIVAÇÃO DO PROCESSO
↓
DISCOVERY COMO CONVERSA SIMULADA REAL
↓
PROPOSTA DO 00_DISCOVERY
↓
REVISÃO / AJUSTE / APROVAÇÃO SIMULADA
↓
CANONIZAÇÃO DO 00
↓
PRÓXIMA ETAPA CONSOME O 00 CANÔNICO
↓
PRODUZ SUA PRÓPRIA PROPOSTA CONFORME A METODOLOGIA
↓
REVISÃO / APROVAÇÃO QUANDO EXIGIDA
↓
CANONIZAÇÃO
↓
ETAPA SEGUINTE CONSOME OS ARTEFATOS ANTERIORES
↓
...
↓
12 RECONCILIAÇÃO E HANDOFF
```

O **Discovery** deve aparecer como conversa simulada entre as partes do cenário, porque essa é a natureza operacional da etapa.

A partir daí, cada documento deve ser produzido consumindo os artefatos canônicos anteriores e executando exatamente o que a etapa correspondente determina. Não é necessário inventar uma nova conversa para toda etapa quando o próprio processo determina pesquisa, análise, síntese, comparação ou transformação documental.

Quando a etapa exigir uma decisão que pertence ao cliente, owner ou outro stakeholder, o caso deve simular o retorno a essa pessoa, registrar a resposta e só então canonizar o documento.

A etapa seguinte não deve ser produzida antes de a anterior estar suficientemente revisada e aprovada no cenário simulado.

---

## Regras obrigatórias para novos exemplos

1. seguir a ordem definida em `docs/processo/PROCESS_MANIFEST.md`;
2. gerar um documento por vez;
3. executar o Discovery como conversa simulada real do cenário;
4. depois do Discovery, fazer cada etapa consumir os documentos anteriores exigidos por seu contrato `consumes`;
5. registrar o contexto que entrou em cada etapa;
6. mostrar perguntas e decisões materiais quando a etapa realmente exigir interação humana, sem criar diálogo artificial apenas para preencher o exemplo;
7. separar hipótese, evidência, recomendação e decisão humana;
8. executar pesquisa atual quando a etapa depender de fatos mutáveis;
9. representar retornos ao cliente, owner ou stakeholder quando o cenário exigir aprovação externa;
10. não antecipar stack antes da Visão do Tech Lead;
11. não antecipar provider/operação antes de DevOps e Infraestrutura;
12. produzir Backlog, Matriz e Handoff somente depois das camadas anteriores;
13. manter todos os artefatos canônicos em Markdown;
14. concluir o cenário documental com o protocolo `CODEX_CANONICAL_START_V1` quando a baseline estiver realmente elegível;
15. nunca gerar todos os documentos em uma única resposta ou simular retrospectivamente que o processo foi seguido.

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

Quando houver cliente real ou simulado, o exemplo deve representar o ciclo de validação sempre que a autoridade da decisão pertencer ao cliente:

```text
ANALISTA / CONSULTORIA
↓
ETAPA EXECUTADA CONFORME O PROCESSO
↓
PROPOSTA / DECISÕES QUE EXIGEM CLIENTE
↓
CLIENTE REVISA
↓
AJUSTES
↓
CLIENTE APROVA
↓
CANONIZAÇÃO
↓
PRÓXIMA ETAPA CONSOME O DOCUMENTO APROVADO
```

A aprovação da consultoria não substitui a aprovação do cliente quando a decisão pertence ao cliente.

Isso não significa que toda etapa exige uma nova entrevista. A interação humana deve ocorrer quando a metodologia ou uma decisão material realmente exigir validação.

---

## Objetivo dos casos

Os casos de uso possuem **dois objetivos simultâneos**:

1. **demonstrar o uso da metodologia** de forma fiel, permitindo que outra pessoa veja como o processo funciona em um trabalho completo;
2. **validar a própria metodologia**, observando durante a execução se existem lacunas, redundâncias, excesso de processo, fronteiras confusas ou handoffs insuficientes.

Por isso, o documento de exemplo de cada etapa é consequência da execução da etapa, e não o ponto de partida.

A sequência correta é:

```text
EXECUTAR A ETAPA CONFORME A METODOLOGIA
↓
OBSERVAR SE O PROCESSO FUNCIONOU
↓
REGISTRAR EVENTUAIS PROBLEMAS OU AJUSTES
↓
APROVAR / CANONIZAR O RESULTADO DO CENÁRIO
↓
CRIAR O DOCUMENTO DE EXEMPLO A PARTIR DO QUE FOI REALMENTE PRODUZIDO
↓
USAR ESSE DOCUMENTO COMO ENTRADA CANÔNICA DA PRÓXIMA ETAPA
```

O exemplo final deve demonstrar o que realmente aconteceu durante o uso do processo. Ele não deve corrigir retrospectivamente a execução para fazê-la parecer mais limpa do que foi.

Quando um caso revelar:

- etapa redundante;
- pergunta ausente;
- fronteira de responsabilidade confusa;
- documentação difícil de consumir;
- handoff insuficiente;
- excesso de processo;
- lacuna de rastreabilidade;

isso deve ser tratado como evidência para revisar a metodologia antes de declarar uma versão estável.

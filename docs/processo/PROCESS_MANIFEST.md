---
document_id: PROCESS-MANIFEST-V1
title: Manifesto Canônico do Processo
status: draft-methodology
version: 0.1.0
type: process-index
canonical_format: markdown
execution_trigger: CODEX_CANONICAL_START_V1
---

# Manifesto Canônico do Processo

## Propósito

Este arquivo é o **índice operacional da metodologia**. Ele existe para remover ambiguidade sobre a ordem dos documentos, seus papéis e a fronteira entre documentação e execução.

Ele não substitui nenhum documento de etapa.

O conteúdo normativo continua nos arquivos específicos de cada etapa.

O README continua sendo a capa da metodologia.

Este manifesto responde apenas:

> **Em qual ordem o processo deve ser percorrido, qual documento é responsável por cada decisão e quando a execução pelo Codex pode começar?**

---

## Regra de formato

A fonte canônica dos documentos de processo e dos documentos gerados para um projeto é Markdown (`.md`) versionado em Git.

Planilhas, CSVs, bancos temporários, scripts e dataframes podem auxiliar análise ou geração, mas não substituem o artefato canônico quando a metodologia exigir um documento.

---

## Ordem canônica

A ordem abaixo prevalece sobre ordenação alfabética da pasta.

| Ordem | Arquivo | Responsabilidade principal | Autoriza código? |
| --- | --- | --- | --- |
| `00` | `00_Discovery.md` | Compreender intenção, contexto, problema, usuários, hipóteses, restrições e perguntas de investigação | Não |
| `01` | `01_Pesquisa_e_Viabilidade.md` | Confrontar a ideia com evidências, mercado, viabilidade, riscos e condicionantes | Não |
| `02` | `02_Briefing_de_Produto_e_Escopo.md` | Canonizar produto, promessa, limites, escopo e compromissos do horizonte | Não |
| `03` | `03_Visao_de_Product_Owner.md` | Transformar escopo em outcomes, comportamentos, regras, histórias e aceite de produto | Não |
| `03A` | `Principios_de_UX_UI.md` | Estabelecer a constituição transversal de decisões de experiência e interface | Não |
| `04` | `04_Direcao_de_UI_e_Design_System.md` | Materializar direção visual, tokens, componentes e linguagem visual reutilizável | Não |
| `05` | `05_Especificacao_de_UX.md` | Especificar jornadas, fluxos, estados, validações, recuperação e usabilidade | Não |
| `06` | `06_Tecnicas_de_Desenvolvimento.md` | Definir como o software deve ser desenvolvido, revisado, testado e mantido | Não |
| `07` | `07_Engenharia_e_Arquitetura.md` | Mensurar forças técnicas, atributos de qualidade, boundaries, dados, contratos e arquitetura | Não |
| `07A` | `Visao_do_Tech_Lead.md` | Selecionar stack, frameworks, bibliotecas, runtimes, persistência e toolchain contra requisitos técnicos | Não |
| `08` | `08_DevOps_e_Infraestrutura.md` | Decidir providers, ambientes, CI/CD concreto, secrets, observabilidade, backup, custos e operação | Não |
| `09` | `09_Plano_de_Fundacao.md` | Ordenar e provar a preparação fundacional por FNDs, dependências, gates e evidências | Não; planeja a execução |
| `10` | `10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md` | Produzir a ordem operacional global de entrega e os contratos dos itens executáveis | Não por si só |
| `11` | `11_Matriz_Operacional_de_Rastreabilidade.md` | Provar a ligação entre fontes, requisitos, backlog, implementação, testes e evidências | Não |
| `12` | `12_Reconciliacao_da_Baseline_e_Handoff_para_Codex.md` | Reconciliar a baseline e autorizar explicitamente o handoff de execução | Somente quando os estados e a aprovação exigidos estiverem satisfeitos |
| `EXEC` | `CODEX_CANONICAL_START_V1` | Ativar a execução canônica pelo Codex sobre uma baseline aprovada | Sim, dentro dos limites do backlog, gates e política de continuidade |

---

## Por que existem `03A` e `07A`

Dois documentos possuem nomes históricos sem prefixo numérico:

- `Principios_de_UX_UI.md`;
- `Visao_do_Tech_Lead.md`.

Para evitar renumerar todos os artefatos já reconstruídos, este manifesto lhes atribui posições lógicas estáveis:

```text
03
↓
03A PRINCÍPIOS UX/UI
↓
04
```

E:

```text
07
↓
07A VISÃO DO TECH LEAD
↓
08
```

Agentes não devem inferir ordem pela listagem alfabética de arquivos.

---

## Natureza transversal dos Princípios de UX/UI

`Principios_de_UX_UI.md` recebe baseline inicial após a Visão de Product Owner, porém permanece transversal durante o restante do processo.

Uma camada posterior não pode contrariá-lo silenciosamente.

Quando evidência técnica, operacional ou de uso real revelar conflito legítimo, a regra é:

```text
CONFLITO REAL
↓
REGISTRAR
↓
REABRIR A AUTORIDADE ADEQUADA
↓
RECONCILIAR
↓
APROVAÇÃO HUMANA
↓
PROPAGAR IMPACTO
```

---

## Fronteiras de responsabilidade

```text
PRODUCT OWNER
O que precisa gerar valor e qual comportamento prova isso?

PRINCÍPIOS UX/UI
Como julgamos uma decisão de experiência?

DIREÇÃO DE UI
Como o produto se expressa visualmente?

ESPECIFICAÇÃO DE UX
Como a pessoa realiza a tarefa ponta a ponta?

TÉCNICAS DE DESENVOLVIMENTO
Como o trabalho de software deve ser realizado com qualidade?

ENGENHARIA E ARQUITETURA
O que tecnicamente precisa ser verdade e como o sistema deve ser estruturado?

TECH LEAD
Quais tecnologias concretas materializam a arquitetura?

DEVOPS E INFRAESTRUTURA
Onde e como a stack é construída, entregue, executada e operada?

PLANO DE FUNDAÇÃO
Em qual ordem a base precisa ser criada e provada?

BACKLOG CANÔNICO
Qual é a ordem operacional global de entrega?

MATRIZ OPERACIONAL
Conseguimos provar a origem e a evidência de cada trabalho material?

RECONCILIAÇÃO E HANDOFF
A baseline está coerente e autorizada para execução?
```

---

## Regra de autoridade

Quando houver conflito, não escolher a informação mais recente apenas por ser mais recente.

A decisão deve voltar à camada que possui autoridade sobre o tema.

Em termos gerais:

1. lei, segurança, privacidade, obrigações regulatórias e políticas mandatórias bloqueiam decisões incompatíveis;
2. Briefing e Product Owner governam produto, escopo, prioridade, regras e aceite de produto;
3. Princípios UX/UI, Direção de UI e Especificação de UX governam experiência e interface nos seus respectivos níveis;
4. Engenharia e Arquitetura governam forças técnicas, boundaries, invariantes, dados e arquitetura;
5. Visão do Tech Lead governa seleção tecnológica concreta;
6. DevOps e Infraestrutura governam a materialização operacional da stack;
7. Plano de Fundação governa a sequência fundacional;
8. Backlog Canônico governa ordem operacional sem redefinir silenciosamente as fontes;
9. Matriz Operacional governa a prova de cobertura e ligação;
10. Issue, prompt, código existente ou preferência do agente nunca ganham autoridade para contradizer uma fonte superior sem reconciliação.

---

## Regra de evolução

Evolução do produto **não retorna automaticamente ao Discovery**.

Primeiro classificar a mudança.

```text
NOVA IDEIA / NOVO PROBLEMA
→ Discovery

MUDANÇA MATERIAL DE ESCOPO OU PROMESSA
→ Briefing

MUDANÇA DE PRIORIDADE, REGRA OU OUTCOME
→ Product Owner

MUDANÇA DE EXPERIÊNCIA
→ Princípios / UI / UX conforme autoridade

MUDANÇA DE ATRIBUTO TÉCNICO OU BOUNDARY
→ Engenharia e Arquitetura

MUDANÇA DE STACK
→ Tech Lead

MUDANÇA OPERACIONAL OU DE PROVIDER
→ DevOps e Infraestrutura

MUDANÇA DE BOOTSTRAP
→ Plano de Fundação

MUDANÇA DE ORDEM / DEPENDÊNCIA
→ Backlog Canônico

LACUNA DE COBERTURA
→ Matriz Operacional
```

Depois da reconciliação, atualizar os artefatos dependentes, a matriz e a baseline.

---

## Estados que não podem ser confundidos

```text
DISCUTIDO
≠
APROVADO
≠
CANONIZADO
```

```text
PLANEJADO
≠
AUTORIZADO
≠
EXECUTADO
≠
VERIFICADO
```

```text
MERGED
≠
DONE
```

```text
READY DE PRODUTO
≠
READY TÉCNICO
≠
READY DO ITEM
≠
READY FOR CODEX
```

---

## Handoff para Codex

O Codex só recebe autorização canônica quando o documento 12 declarar os estados exigidos e houver aprovação humana explícita.

O gatilho é:

```text
CODEX_CANONICAL_START_V1
```

Esse gatilho significa:

1. localizar a baseline aprovada do projeto;
2. ler o documento 12;
3. validar `BASELINE_READINESS`, `HANDOFF_READINESS`, `EXECUTION_AUTHORIZATION` e a política de continuidade;
4. ler o backlog e a matriz;
5. selecionar somente um item elegível conforme a política aprovada;
6. resolver suas fontes e contratos;
7. carregar gates, dependências, testes, evidências e condições de parada;
8. emitir o handshake de execução;
9. somente então alterar código ou infraestrutura dentro do escopo autorizado.

A chave não libera produção, billing, dados reais, ações humanas, alteração de stack, mudança de arquitetura ou expansão de escopo sem os respectivos gates.

---

## Regra para ChatGPT

Ao ativar a metodologia, o ChatGPT deve usar este manifesto para compreender a ordem, ler integralmente a etapa atual e consumir os artefatos anteriores exigidos por ela.

O ChatGPT produz propostas e documentos; o humano revisa e aprova; a versão aprovada é canonizada no projeto.

---

## Regra para exemplos

Exemplos oficiais da metodologia devem reproduzir o processo **como trabalho real**, documento por documento.

Não é válido gerar retrospectivamente todos os artefatos em uma única resposta e chamá-los de exemplo do processo.

Um exemplo atual deve preservar:

```text
ATIVAÇÃO
↓
CONVERSA / INVESTIGAÇÃO DA ETAPA
↓
PROPOSTA
↓
REVISÃO HUMANA
↓
AJUSTE
↓
APROVAÇÃO
↓
CANONIZAÇÃO DO DOCUMENTO
↓
PRÓXIMA ETAPA
```

---

## Estado deste manifesto

Este manifesto consolida a ordem da reconstrução atual.

A metodologia permanece em validação até que os casos de uso completos percorram o fluxo ponta a ponta e confirmem ou revelem ajustes necessários.
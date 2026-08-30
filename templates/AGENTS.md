# AGENTS.md — Loader do Processo Canônico

> Template para projetos que adotam o Processo de Desenvolvimento de Software com IA Assistida.
>
> Este arquivo não substitui a documentação canônica do projeto. Ele apenas ensina o agente a localizar e consumir a baseline aprovada.

## Regra principal

Não iniciar implementação funcional apenas porque este arquivo existe.

A execução canônica só começa quando o usuário ou mecanismo autorizado fornecer:

```text
CODEX_CANONICAL_START_V1
```

E o documento de handoff do projeto autorizar a execução.

---

## Ao receber `CODEX_CANONICAL_START_V1`

1. localize `12_Reconciliacao_da_Baseline_e_Handoff_para_Codex.md` na documentação canônica do projeto;
2. leia esse documento antes de alterar qualquer arquivo;
3. valide os estados declarados para baseline, handoff e autorização de execução;
4. identifique a versão/commit da baseline que deve ser consumida;
5. leia `10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md`;
6. leia `11_Matriz_Operacional_de_Rastreabilidade.md`;
7. identifique o próximo item elegível conforme status, dependências, gates e política de continuidade;
8. resolva todas as fontes apontadas pelos TRACE IDs e pelo contrato do item;
9. leia somente os documentos e trechos adicionais necessários para compreender integralmente o item, sem ignorar nenhuma fonte vinculante;
10. carregue critérios de aceite, NFRs, decisões arquiteturais, TDRs, IDRs, contratos UX/UI, FNDs, testes esperados, evidências esperadas e condições de parada aplicáveis;
11. emita o handshake de execução;
12. somente depois altere código, configuração ou infraestrutura dentro do escopo autorizado.

---

## Handshake mínimo

Antes da primeira alteração, declarar algo equivalente a:

```text
CODEX_PROCESS: ACTIVE
TRIGGER: CODEX_CANONICAL_START_V1
BASELINE_ID: <id>
BASELINE_VERSION: <version>
BASELINE_COMMIT: <sha>
BASELINE_READINESS: READY_FOR_CODEX
EXECUTION_AUTHORIZATION: APPROVED
CONTINUATION_POLICY: <policy>

CURRENT_ITEM: <id>
ITEM_STATUS: READY
TRACE_IDS: <ids>
DEPENDENCIES: SATISFIED
ENTRY_GATES: SATISFIED
HUMAN_ACTION_REQUIRED_NOW: NO
EXPECTED_EVIDENCE: <summary>
STOP_CONDITIONS: LOADED
```

Se algum campo material não puder ser preenchido sem inferência não autorizada, **pare**.

---

## Condições de parada

Pare e registre o bloqueio quando ocorrer qualquer situação equivalente a:

- baseline ausente ou não aprovada;
- item sem fonte canônica suficiente;
- dependência não satisfeita;
- gate aberto;
- decisão de produto necessária;
- decisão de UX/UI necessária;
- mudança arquitetural necessária;
- mudança de stack necessária;
- provider ou serviço não aprovado;
- secret ou dado real não autorizado;
- ação humana obrigatória;
- billing, contrato, termos ou compra não autorizados;
- necessidade de inventar API, schema, regra ou comportamento;
- conflito entre documentação e realidade que afete o contrato;
- impossibilidade de produzir a evidência exigida;
- escopo maior que o item autorizado.

Use o status `BLOCKED` ou o mecanismo equivalente definido no projeto.

---

## Autoridade

O agente não pode usar este arquivo para sobrescrever documentação do projeto.

Em caso de conflito:

```text
AGENTS.md
≠
fonte de produto
≠
fonte de arquitetura
≠
fonte de stack
≠
fonte de infraestrutura
```

Este arquivo é apenas um loader.

O conteúdo canônico está nos documentos do projeto e nas decisões rastreadas por eles.

---

## Leitura da baseline

Na primeira entrada de uma baseline nova, percorra a cadeia documental definida pelo processo e construa um índice operacional.

Nas execuções seguintes, não é necessário recarregar indiscriminadamente todos os documentos se a baseline não mudou.

Por item, use:

```text
ITEM
+
TRACE IDS
+
FONTES VINCULANTES
+
CONTRATOS
+
NFRs
+
GATES
+
TESTES
+
EVIDÊNCIAS
+
STOP CONDITIONS
```

Se a baseline mudou, invalide o contexto anterior e reconcilie a nova versão antes de continuar.

---

## Limites de autorização

`CODEX_CANONICAL_START_V1` não significa autorização irrestrita.

Não executar automaticamente:

- deploy em produção;
- uso de dados pessoais reais;
- criação de billing ou inserção de cartão;
- aceite de termos;
- alteração de DNS crítico;
- exclusão de recursos de produção;
- publicação em app stores;
- rotação de secrets sem procedimento aprovado;
- alteração de arquitetura ou stack;
- expansão de escopo.

Essas ações dependem dos gates e owners definidos na baseline.

---

## Regra de Done

Não marque item como `Done` apenas porque houve commit ou merge.

Antes de `Done`, confirme as evidências exigidas para:

- comportamento funcional;
- testes;
- NFRs;
- segurança;
- UX/a11y quando aplicável;
- dados e contratos;
- build;
- operação;
- documentação;
- rastreabilidade;
- aceite humano quando exigido.

---

## Continuidade

Respeite a política declarada na baseline:

```text
MANUAL_EACH_ITEM
AUTO_AFTER_VERIFIED_DONE
AUTO_UNTIL_HUMAN_GATE
```

Nunca escolha uma política mais permissiva por conta própria.

---

## Regra final

> **Leia antes de executar. Resolva a origem antes de alterar. Prove antes de concluir. Pare antes de inventar.**

---
document_id: CASE-01-DOC-05
title: Especificação de UX — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: especificacao-ux
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
  - Principios_de_UX_UI.md
  - 04_Direcao_de_UI_e_Design_System.md
next_document: 06_Tecnicas_de_Desenvolvimento.md
ux_readiness: SUFFICIENT_FOR_TECHNICAL_STAGE
---

# Especificação de UX — CRM para gestão de clientes e pedidos

## 1. Propósito

Este documento transforma os contratos de produto, princípios de UX/UI e direção visual do Caso 01 em uma experiência operacional ponta a ponta.

Ele especifica jornadas, fluxos, estados, validações, recuperação, comportamento de retorno, conectividade, permissões, microcopy operacional, acessibilidade da jornada, eventos semânticos e gates de UX.

A saída ainda não escolhe arquitetura, linguagem, framework, banco, fila, cache, SDK ou provider.

---

## 2. Contrato de experiência

> **O CRM deve permitir que o vendedor descubra o que precisa fazer, compreenda rapidamente o contexto de um cliente, execute ou registre a ação comercial e deixe a próxima ação clara, mesmo diante de interrupções ou indisponibilidade temporária do Protheus, sempre distinguindo o que foi efetivamente salvo, o que veio do ERP e o que ainda não pôde ser confirmado.**

Este contrato deve permanecer verdadeiro em desktop e mobile.

---

## 3. Base canônica consumida

A especificação consome integralmente:

- `00_Discovery.md`;
- `01_Pesquisa_e_Viabilidade.md`;
- `02_Briefing_de_Produto_e_Escopo.md`;
- `03_Visao_de_Product_Owner.md`;
- `Principios_de_UX_UI.md`;
- `04_Direcao_de_UI_e_Design_System.md`.

Regras especialmente relevantes:

- o vendedor é a persona primária do core;
- ação comercial tem precedência sobre dashboard;
- Protheus permanece autoridade ERP;
- o CRM não pode exigir dupla manutenção sistemática;
- histórico comercial pertence à empresa;
- descoberta de cliente de outra carteira não libera automaticamente seu histórico;
- informação financeira é proporcional ao papel;
- dados do Protheus precisam carregar estado de confiança;
- registro de interação precisa ser proporcional;
- lista de atenção excessivamente ruidosa é falha de produto;
- o produto atende desktop e mobile;
- offline completo não está aprovado no horizonte atual.

---

## 4. Arquitetura da experiência

### 4.1. Fluxo principal do vendedor

```text
HOJE
↓
PRIORIDADE
↓
CLIENTE
↓
CONTEXTO
↓
AÇÃO COMERCIAL
↓
REGISTRO
↓
PRÓXIMA AÇÃO
↓
RETORNO AO FLUXO
```

### 4.2. Entrada por busca direta

Quando o vendedor já sabe qual cliente deseja consultar:

```text
BUSCA
↓
CLIENTE
↓
CONTEXTO / AÇÃO
```

Ambas as entradas são válidas e devem convergir para o mesmo contexto do cliente.

### 4.3. Gestão

```text
GESTÃO
↓
EXCEÇÃO / SINAL
↓
CLIENTE / VENDEDOR
↓
CONTEXTO
↓
INTERVENÇÃO
```

A visão de gestão não é uma cópia ampliada da tela do vendedor.

---

## 5. Política de navegação e retorno

Regras transversais:

- voltar não deve pedir confirmação quando nada relevante será perdido;
- rascunho recuperável deve ser preservado quando seguro;
- saída com perda real de dado não persistido exige consequência clara;
- após ação simples concluída, a experiência deve retornar ou permanecer no contexto útil, não abrir uma tela de sucesso isolada;
- tarefas focadas podem reduzir navegação global enquanto estiverem ativas;
- retornar de um detalhe deve preservar a posição e o contexto anterior quando isso reduzir reconstrução mental;
- indisponibilidade de Protheus não deve expulsar o usuário do contexto comercial local.

---

# 6. UX-JRN-001 — Começar o trabalho comercial

## 6.1. Origem

- PO: `J-001`, `US-001`;
- outcomes: `OUT-001`, `OUT-004`;
- UI principal: `UI-SCR-001 — Hoje`.

## 6.2. Contexto

O vendedor inicia ou retoma sua rotina e precisa descobrir rapidamente o que merece atenção.

## 6.3. Gatilhos

- abertura do produto;
- retorno ao destino Hoje;
- conclusão de uma ação que altera a lista de prioridades.

## 6.4. Fluxo principal

```text
ENTRAR EM HOJE
↓
CARREGAR CONTEXTO DISPONÍVEL
↓
MOSTRAR PRIORIDADES REAIS
↓
USUÁRIO ESCOLHE ITEM
↓
ABRIR CLIENTE / AÇÃO RELACIONADA
```

## 6.5. Conteúdo prioritário

A superfície pode distinguir, quando aplicável:

- retornos previstos para hoje;
- retornos vencidos;
- clientes que merecem atenção;
- outras pendências explicitamente derivadas do produto.

Não criar uma tarefa artificial apenas para preencher a tela.

## 6.6. Estado vazio

Mensagem conceitual:

> **Nenhuma ação prioritária agora.**

Uma ação só deve aparecer se existir um próximo passo real.

## 6.7. Estado de ruído

`UX-STA-001 — ATTENTION_SIGNAL_OVERLOAD`

Existe quando a lógica de priorização produz volume tão alto que deixa de ajudar a decidir.

Esse estado é considerado falha de hipótese, não mero problema de layout.

## 6.8. Evidência de sucesso

- vendedor identifica uma prioridade sem ajuda relevante;
- não precisa consultar planilha paralela para descobrir sua lista principal;
- itens vencidos são reconhecíveis sem depender apenas de cor.

---

# 7. UX-JRN-002 — Trabalhar um cliente

## 7.1. Origem

- PO: `J-002`, `US-002`, `US-005`, `US-006`, `US-007`;
- outcomes: `OUT-001`, `OUT-002`, `OUT-004`;
- UI: `UI-SCR-003 — Cliente`.

## 7.2. Natureza

Esta é a jornada crítica principal do produto.

## 7.3. Menor caminho útil

```text
ABRIR CLIENTE
↓
RECONHECER SITUAÇÃO ATUAL
↓
LER CONTEXTO NECESSÁRIO
↓
EXECUTAR CONTATO / AÇÃO
↓
REGISTRAR RESULTADO
↓
DEFINIR PRÓXIMA AÇÃO, SE EXISTIR
↓
CONCLUIR
```

## 7.4. Entrada em modo de leitura

Ao abrir um cliente, o vendedor entra em contexto de leitura e decisão.

O produto não deve colocar o usuário automaticamente em edição integral.

A sequência conceitual preferida é:

```text
LISTA
↓
DETALHE
↓
EDIÇÃO QUANDO NECESSÁRIA
```

## 7.5. Registrar interação

A tarefa de registro deve ser curta.

Informações de experiência mínimas:

- tipo ou natureza da interação;
- resumo suficiente do resultado;
- próxima ação, quando aplicável.

Dados que o sistema já conhece, como autoria e momento do registro, não devem ser redigitados pelo vendedor.

## 7.6. Próxima ação

Depois do registro, o vendedor pode:

- definir próxima ação;
- declarar que não há próxima ação agora.

Não obrigar follow-up artificial apenas para permitir salvamento.

## 7.7. Conclusão

Sucesso simples deve:

- atualizar o estado;
- oferecer feedback discreto;
- permanecer ou retornar ao contexto útil.

Não abrir uma tela inteira de celebração ou confirmação rotineira.

---

# 8. Política de rascunho

## 8.1. Estado

`UX-STA-002 — INTERACTION_DRAFT`

Durante o registro de interação, conteúdo já digitado deve ser preservado quando seguro diante de:

- navegação acidental;
- interrupção temporária;
- perda transitória de conexão;
- retorno ao aplicativo.

## 8.2. Regra de saída

```text
NADA A PERDER
→ voltar normalmente

RASCUNHO RECUPERÁVEL
→ preservar e voltar

DADO NÃO PERSISTIDO E NÃO RECUPERÁVEL
→ avisar consequência
```

A UX não determina o mecanismo técnico de persistência.

---

# 9. Política de conectividade

Offline completo não faz parte do horizonte atual.

Porém rede ruim não pode produzir perda silenciosa de trabalho válido.

| Domínio | Comportamento esperado |
| --- | --- |
| leitura de dados do CRM já disponíveis | preservar conteúdo quando possível |
| texto ainda em edição | não perder por falha transitória |
| confirmação de gravação | somente declarar sucesso compatível com o estado real |
| consulta ao Protheus | pode ficar temporariamente indisponível |
| pedido/estoque/financeiro | nunca inventar dado atual como fallback |

Mensagens conceituais possíveis:

> **Salvando…**

> **Não foi possível concluir agora. Seu registro foi preservado.**

A implementação concreta será responsabilidade das camadas técnicas.

---

# 10. UX-JRN-003 — Trabalhar um prospect

## 10.1. Origem

- PO: `J-003`, `US-004`;
- regras: `BR-002`, `BR-014`;
- UI: `UI-SCR-004 — Prospect`.

## 10.2. Fluxo

```text
NOVO PROSPECT
↓
BUSCAR POSSÍVEL REGISTRO EXISTENTE
↓
NENHUM MATCH RELEVANTE
↓
CADASTRO MÍNIMO
↓
CONTEXTO COMERCIAL
↓
PRÓXIMA AÇÃO
```

## 10.3. Possível duplicidade

Quando houver registro potencialmente equivalente:

```text
POSSÍVEL DUPLICIDADE
↓
MOSTRAR REGISTRO ENCONTRADO
↓
VER REGISTRO
OU
CONTINUAR COMO DIFERENTE, QUANDO PERMITIDO
```

Mensagem conceitual:

> **Encontramos uma empresa que pode ser a mesma. Confira antes de criar outro registro.**

A possível duplicidade é uma validação de **REVISÃO**, não bloqueio universal por padrão.

---

# 11. UX-JRN-004 — Consultar pedido e contexto Protheus

## 11.1. Origem

- PO: `J-004`, `US-008`, `US-009`, `US-010`, `US-011`, `US-018`;
- regras: `BR-001`, `BR-003`, `BR-012`, `BR-013`;
- UI: `UI-SCR-003 — Cliente`, `UI-SCR-006 — Pedido`.

## 11.2. Fluxo

```text
CLIENTE
↓
RESUMO DE PEDIDOS / COMPRA
↓
INFORMAÇÃO SUFICIENTE?
├─ SIM → continuar trabalho comercial
└─ NÃO → abrir detalhe do pedido
```

## 11.3. Estados ERP

`UX-STA-003 — ERP_AVAILABLE`

Dado necessário foi confirmado no estado esperado.

`UX-STA-004 — ERP_REFRESHING`

Atualização está em curso.

`UX-STA-005 — ERP_STALE`

Existe dado conhecido, mas sua atualidade não pode ser assumida como suficiente.

`UX-STA-006 — ERP_UNAVAILABLE`

Não foi possível confirmar o dado externo.

## 11.4. Distinções obrigatórias

Estas situações não podem compartilhar o mesmo estado:

- não existe pedido;
- não foi possível consultar o Protheus;
- existe informação conhecida, mas potencialmente desatualizada.

## 11.5. Microcopy conceitual

> **Não foi possível confirmar os dados do Protheus agora. Tente novamente.**

Quando dado anterior puder ser mostrado com segurança:

> **Última atualização: 10:42**

O produto nunca deve afirmar um resultado externo que o Protheus não confirmou.

---

# 12. UX-JRN-005 — Gerenciar carteira

## 12.1. Origem

- PO: `J-005`, `US-014`, `US-015`;
- UI: `UI-SCR-005 — Gestão`.

## 12.2. Fluxo

```text
GESTÃO
↓
IDENTIFICAR EXCEÇÃO
↓
CLIENTE / VENDEDOR
↓
COMPREENDER CONTEXTO
↓
DECIDIR INTERVENÇÃO
```

Exceções podem incluir:

- retornos vencidos;
- cliente sem atenção;
- carteira sem atividade relevante;
- necessidade de redistribuição.

A UX não define o algoritmo que produz esses sinais.

---

# 13. UX-JRN-006 — Transferir responsabilidade

## 13.1. Origem

- PO: `J-006`, `US-013`;
- regras: `BR-005`, `BR-006`, `BR-007`.

## 13.2. Fluxo

```text
CLIENTE
↓
TRANSFERIR RESPONSABILIDADE
↓
ESCOLHER NOVO RESPONSÁVEL
↓
REVISAR CONSEQUÊNCIA
↓
CONFIRMAR
↓
RESPONSABILIDADE ALTERADA
↓
HISTÓRICO PRESERVADO
```

## 13.3. Confirmação

Evitar confirmação genérica como “Tem certeza?”.

Preferir mensagem que nomeie alvo e efeito:

> **Transferir este cliente para Maria?**  
> O histórico comercial será preservado.

A ação altera responsabilidade comercial, não propriedade do histórico.

---

# 14. Descoberta de cliente de outra carteira

Origem: `BR-004`, `US-003`.

O vendedor pode receber contexto suficiente para evitar duplicidade, por exemplo:

```text
Empresa ABC Ltda.
CNPJ …
Responsável: Maria
```

Ele não recebe automaticamente:

- timeline;
- observações;
- negociação;
- informações financeiras;
- histórico privado da carteira.

Mensagem conceitual de restrição:

> **Este cliente pertence à carteira de Maria. Informações comerciais detalhadas são restritas à equipe responsável.**

A política de acesso deve aparecer como comportamento compreensível, não como erro técnico genérico.

---

# 15. Validações

Taxonomia do caso:

### BLOQUEIO

Continuar produziria estado inválido, risco ou violação de regra.

Exemplo: transferir cliente sem novo responsável válido.

### REVISÃO

Possível inconsistência exige decisão humana.

Exemplo: prospect potencialmente duplicado.

### AVISO

É possível continuar, mas existe consequência ou incerteza.

Exemplo: dado do Protheus potencialmente desatualizado.

### INFORMATIVO

Contexto adicional sem bloqueio.

Exemplo: responsável atual pela carteira.

---

# 16. Repetição de ação e efeito duplicado

Ações especialmente protegidas:

- registrar interação;
- concluir próxima ação;
- transferir carteira;
- criar prospect.

Se o usuário repetir a mesma intenção por falta de resposta perceptível, o resultado esperado é **uma única intenção efetiva**, não efeitos duplicados.

A UX define a necessidade; Engenharia e Arquitetura definirão onde e como garanti-la.

---

# 17. Estados globais do caso

| Estado | Significado de UX | Regra |
| --- | --- | --- |
| Carregando | conteúdo ainda não disponível | não apagar contexto válido sem necessidade |
| Salvando | efeito ainda sendo confirmado | bloquear apenas o comando afetado quando possível |
| Rascunho preservado | conteúdo digitado continua recuperável | não declarar gravação remota concluída |
| Sucesso | efeito correspondente concluído | feedback proporcional |
| Erro recuperável | tarefa pode continuar ou ser repetida | preservar contexto e indicar próximo passo |
| ERP indisponível | dependência externa não confirmou dado | não transformar em “sem dados” |
| Dado desatualizado | informação conhecida pode não refletir o momento atual | comunicar momento/condição |
| Sem permissão | regra de acesso impede detalhe | explicar limite sem vazar conteúdo |
| Bloqueado | regra impede continuidade | explicar motivo quando permitido |

---

# 18. Microcopy operacional

Mensagens de referência:

> **Não foi possível confirmar os dados do Protheus agora.**

> **Seu registro foi preservado.**

> **Encontramos uma empresa que pode ser a mesma.**

> **Nenhuma ação prioritária agora.**

> **Este cliente pertence à carteira de Maria.**

> **Transferir este cliente para Maria? O histórico comercial será preservado.**

Regra estrutural:

```text
SITUAÇÃO
+
IMPACTO QUANDO NECESSÁRIO
+
PRÓXIMA AÇÃO
```

Evitar mensagens como:

- Erro 500;
- Falha na API;
- Operação inválida;
- Erro desconhecido.

---

# 19. Acessibilidade da jornada

Acessibilidade deve existir no fluxo completo.

Requisitos do caso:

- ao fechar dialog ou sheet, foco retorna a ponto coerente;
- erro de formulário é associado ao campo e anunciado quando aplicável;
- timeline mantém ordem semântica previsível;
- “vencido” possui texto ou semântica equivalente, não apenas cor;
- atualidade/indisponibilidade do Protheus possui equivalente textual;
- listas operacionais funcionam por teclado no desktop;
- mobile não depende de swipe para função essencial;
- atualizações dinâmicas relevantes podem ser anunciadas sem ruído excessivo;
- ação fixa não pode encobrir foco, erro ou conteúdo essencial;
- zoom, texto ampliado e reflow devem preservar a tarefa.

---

# 20. Responsividade da experiência

Mobile e desktop preservam:

- resultado;
- prioridade;
- semântica;
- segurança;
- acesso às capacidades.

Podem diferir em composição.

### Desktop

Pode aproveitar simultaneidade de lista + detalhe quando isso reduzir alternância.

### Mobile

Favorece superfícies sequenciais e foco por tarefa.

A UX não exige reprodução literal do mesmo layout entre form factors.

---

# 21. Instrumentação semântica

A UX define o significado do que precisa ser observável, sem escolher ferramenta concreta.

| ID | Evento semântico | Significado |
| --- | --- | --- |
| UX-EVT-001 | `priority_opened` | prioridade foi aberta a partir da rotina |
| UX-EVT-002 | `client_opened` | contexto de cliente foi acessado |
| UX-EVT-003 | `interaction_started` | registro de interação realmente começou |
| UX-EVT-004 | `interaction_completed` | interação foi concluída no estado esperado |
| UX-EVT-005 | `next_action_defined` | próxima ação foi explicitamente registrada |
| UX-EVT-006 | `prospect_created` | prospect novo foi concluído |
| UX-EVT-007 | `duplicate_review_shown` | revisão de possível duplicidade foi necessária |
| UX-EVT-008 | `erp_data_unavailable` | dado ERP necessário não pôde ser confirmado |
| UX-EVT-009 | `erp_data_retry` | usuário tentou novamente consulta externa |
| UX-EVT-010 | `ownership_transfer_completed` | responsabilidade comercial foi transferida |
| UX-EVT-011 | `parallel_control_reported` | evidência de controle paralelo foi registrada em pesquisa/piloto |

## 21.1. Minimização

Eventos não devem transportar sem necessidade:

- texto livre da interação;
- mensagem de cliente;
- payload do Protheus;
- dado financeiro completo;
- credenciais;
- conteúdo privado de carteira.

Preferir categorias, estados, IDs técnicos, duração agregada e códigos de razão.

---

# 22. Plano de validação

| ID | Perfil | Tarefa | Evidência desejada |
| --- | --- | --- | --- |
| UX-TST-001 | vendedor | encontrar próxima prioridade | conclui sem ajuda relevante |
| UX-TST-002 | vendedor | abrir cliente e explicar situação | reconhece contexto correto |
| UX-TST-003 | vendedor | registrar interação e próxima ação | conclui sem orientação externa |
| UX-TST-004 | vendedor | interpretar falha do Protheus | distingue indisponibilidade de ausência de dado |
| UX-TST-005 | vendedor | criar prospect com possível duplicidade | revisa sem confusão |
| UX-TST-006 | gerente | identificar cliente que exige intervenção | localiza sinal e contexto |
| UX-TST-007 | gerente | transferir carteira | entende consequência e preservação do histórico |
| UX-TST-008 | vendedor | falha simulada de rede durante registro | recupera sem perder conteúdo válido |
| UX-TST-009 | teclado/leitor | concluir jornada crítica | sem bloqueio de acessibilidade |

Amostra pequena deve ser interpretada com evidência qualitativa; não transformar teste inicial em prova estatística artificial.

---

# 23. Perguntas ainda testáveis

- o vendedor reconhece a próxima ação sem ajuda?;
- a lista de atenção reduz decisão ou cria ruído?;
- o registro de interação é curto o suficiente para uso real?;
- a equipe entende diferença entre dado atual, dado antigo e indisponibilidade do Protheus?;
- possível duplicidade é compreendida sem bloquear casos legítimos?;
- a restrição de carteira é entendida sem parecer falha do sistema?;
- o piloto abandona controles paralelos?;
- conectividade ruim produz perda de trabalho ou apenas degrada capacidades externas?;
- mobile preserva velocidade de retomada no contexto de campo?

---

# 24. Gates de UX

### UX-GATE-001 — Core

Vendedor consegue completar:

```text
prioridade → cliente → ação → registro → próxima ação
```

sem suporte relevante.

### UX-GATE-002 — Recuperação

Falhas recuperáveis não apagam trabalho válido nem exigem reconstrução integral da tarefa.

### UX-GATE-003 — Protheus

Indisponibilidade, atualidade e incerteza dos dados externos são compreensíveis.

### UX-GATE-004 — Duplicidade

Prospect potencialmente duplicado pode ser revisado sem confusão e sem bloqueio arbitrário.

### UX-GATE-005 — Permissão

Carteira alheia não vaza histórico e a restrição é compreensível.

### UX-GATE-006 — Acessibilidade

Fluxo crítico funciona com teclado, foco, texto e sem depender exclusivamente de cor ou gesto.

### UX-GATE-007 — Fricção

Registro comercial não exige coleta desproporcional ao valor produzido.

### UX-GATE-008 — Medição

Eventos necessários permitem avaliar o core sem transportar conteúdo operacional sensível.

---

# 25. Requisitos que seguem para as etapas técnicas

A UX produz necessidades técnicas sem escolher a solução:

- repetição da mesma intenção não pode duplicar efeito em ações materiais;
- falha transitória não deve apagar rascunho válido;
- dado externo precisa carregar condição de atualidade/confiabilidade;
- indisponibilidade do Protheus não deve ser representada como inexistência de informação;
- autorização precisa suportar descoberta controlada sem exposição do histórico alheio;
- histórico precisa preservar autoria e continuidade;
- telemetria deve ser minimizada;
- fluxos críticos precisam ser verificáveis por acessibilidade;
- retornos e timestamps precisam possuir semântica temporal coerente;
- erro recuperável precisa preservar contexto;
- contratos externos precisam permitir retry controlado e diagnóstico sem vazar conteúdo.

A materialização pertence a Técnicas de Desenvolvimento, Engenharia/Arquitetura, Tech Lead e DevOps/Infra conforme responsabilidade.

---

# 26. Definition of Ready para etapa técnica

A UX está pronta para alimentar a etapa técnica porque:

- jornadas P0 possuem gatilho e saída;
- fluxo principal está descrito;
- decisões relevantes estão explícitas;
- estados críticos estão definidos;
- validações possuem severidade semântica;
- recuperação está especificada;
- retorno e rascunho possuem política;
- conectividade está tratada sem inventar offline completo;
- permissões e privacidade visível estão cobertas;
- acessibilidade foi incorporada;
- Protheus possui estados de falha e incerteza;
- eventos semânticos necessários estão identificados;
- regras de PO permanecem rastreáveis;
- pendências técnicas continuam pendências, não foram resolvidas por suposição.

```text
UX_READINESS: SUFFICIENT_FOR_TECHNICAL_STAGE
READY_FOR_CODEX: NO
```

---

# 27. Validação da metodologia nesta etapa

A cadeia de refinamento funcionou como esperado:

```text
PO
US-006 — registrar interação
↓
PRINCÍPIOS
registro proporcional + preservação de contexto
↓
DIREÇÃO DE UI
hierarquia e componentes leves
↓
UX
entrada, campos mínimos, rascunho, sucesso,
falha, repetição, retorno e evidência
```

Nenhuma arquitetura, framework, banco, fila, provider ou mecanismo físico de sincronização foi escolhido.

```text
UX_METHOD_VALIDATION: PASS
PRODUCT_SCOPE_CHANGED: NO
BUSINESS_RULE_REINTERPRETED: NO
VISUAL_IDENTITY_REDEFINED: NO
TECHNOLOGY_SELECTED: NO
CORE_JOURNEYS: SPECIFIED
CRITICAL_STATES: SPECIFIED
RECOVERY: SPECIFIED
ERP_FAILURE_BEHAVIOR: SPECIFIED
VALIDATION_LEVELS: SPECIFIED
ACCESSIBILITY_FLOW: SPECIFIED
SEMANTIC_EVENTS: SPECIFIED
UX_GATES: SPECIFIED
```

---

# 28. Handoff

A próxima etapa é:

```text
06 — Técnicas de Desenvolvimento
```

Ela deve consumir esta especificação como contrato de comportamento e definir como o trabalho de engenharia deverá preservar, testar, revisar e verificar essas propriedades, sem escolher stack ou arquitetura prematuramente.

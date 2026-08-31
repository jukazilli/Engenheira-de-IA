---
document_id: CASE-01-DOC-04
title: Direção de UI e Design System — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: direcao-ui-design-system
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
  - Principios_de_UX_UI.md
next_document: 05_Especificacao_de_UX.md
ui_direction_readiness: SUFFICIENT
---

# Direção de UI e Design System — CRM para gestão de clientes e pedidos

## 1. Propósito

Este documento canoniza a direção visual do CRM comercial do Caso 01.

Ele transforma a intenção de produto, a hierarquia de valor e os princípios de UX/UI aprovados em uma linguagem visual reutilizável para desktop e mobile, sem definir ainda jornadas completas, regras de navegação ponta a ponta, arquitetura de software, framework ou implementação concreta do Design System.

A pergunta central desta etapa é:

> **Como o CRM deve parecer e organizar visualmente informação, ação, estado e confiança para funcionar como ferramenta comercial leve e precisa, em vez de parecer um console administrativo ou uma extensão visual do ERP?**

---

## 2. Base consumida

Esta etapa consumiu:

- `00_Discovery.md`;
- `01_Pesquisa_e_Viabilidade.md`;
- `02_Briefing_de_Produto_e_Escopo.md`;
- `03_Visao_de_Product_Owner.md`;
- `Principios_de_UX_UI.md`.

Decisões especialmente relevantes herdadas:

- vendedor é a persona primária de decisão do core;
- ação comercial tem precedência sobre dashboard gerencial;
- Protheus permanece autoridade dos dados e operações ERP canônicos;
- CRM não pode exigir dupla manutenção sistemática;
- histórico comercial pertence à empresa;
- informação financeira é proporcional ao papel;
- dado do Protheus precisa carregar estado de confiança;
- produto deve funcionar em desktop e mobile;
- registro de interação deve ser proporcional;
- lista de atenção ruidosa é falha de produto;
- interface deve parecer ferramenta para vendedor, não sistema administrativo.

---

## 3. Entrevista visual simulada

Como não existia identidade digital suficientemente definida nos documentos anteriores, a etapa conduziu uma entrevista visual simulada com os stakeholders.

### Diretor

A empresa possui herança visual com azul escuro e verde em materiais corporativos, mas não possui sistema digital consolidado. A direção deve preservar reconhecimento institucional sem copiar literalmente materiais existentes.

O diretor rejeitou explicitamente:

- aparência de ERP legado;
- dashboard excessivo;
- excesso de gráficos e cards;
- interface visualmente pesada.

### Gerente

Solicitou aparência profissional, leve e adequada para uso prolongado durante o dia.

### Vendedor

Priorizou leitura rápida e clareza sobre o que precisa fazer.

### Tema

Tema escuro não é requisito do primeiro horizonte.

Decisão:

```text
TEMA P0: CLARO
DARK MODE: FORA DO COMPROMISSO ATUAL
```

---

## 4. Tese visual

> **O CRM deve parecer uma ferramenta comercial precisa e leve, não um console administrativo. Neutros claros mantêm o ambiente calmo durante uso prolongado; azul profundo ancora confiança e identidade; teal concentra energia nas ações e estados que pedem decisão. O cliente e a próxima ação dominam a hierarquia, enquanto dados do Protheus aparecem como contexto secundário e confiável.**

Consequências:

```text
FUNDO
→ neutro, calmo e de baixa fadiga

AÇÃO
→ energia concentrada, não espalhada

DADOS
→ legíveis, contextualizados e disciplinados

CARDS
→ usados somente quando o agrupamento é semanticamente justificável

RELATÓRIOS
→ subordinados ao trabalho diário do vendedor

PROTHEUS
→ fornece contexto; não define a estética da interface
```

---

## 5. Personalidade visual

| Eixo | Expressar | Evitar |
| --- | --- | --- |
| Profissional | estrutura, alinhamento e consistência | burocracia visual |
| Humano | linguagem clara e respiro | formalidade excessiva |
| Operacional | próxima ação reconhecível | dashboard contemplativo |
| Confiável | estados claros e dados contextualizados | ambiguidade |
| Leve | superfícies simples e pouca decoração | cards dentro de cards |
| Atual | composição responsiva e tipografia limpa | estética de ERP legado |

Não fazem parte da direção:

- futurista;
- gamificado;
- premium como fim em si;
- excessivamente técnico;
- colorido por decoração.

---

## 6. Hierarquia visual canônica

### 6.1. Vendedor

```text
1. O QUE PRECISA DA MINHA ATENÇÃO
2. QUEM É O CLIENTE
3. CONTEXTO PARA DECIDIR
4. AÇÃO PRINCIPAL
5. HISTÓRICO / DETALHE
6. DADOS COMPLEMENTARES
```

### 6.2. Gerente

```text
1. EXCEÇÃO / PROBLEMA
2. CLIENTE / VENDEDOR
3. CONTEXTO
4. INTERVENÇÃO
5. INDICADORES COMPLEMENTARES
```

### 6.3. Diretor

```text
1. SINAL
2. TENDÊNCIA
3. CONTEXTO
4. DECISÃO
```

A interface não deve dar a um gráfico, KPI ou bloco administrativo maior peso do que a ação comercial relevante para o estado atual.

---

## 7. Densidade visual

A direção adota **densidade moderada e adaptativa**.

Não existe regra global de "baixa densidade sempre".

A densidade depende da tarefa mental.

```text
ENTIDADE REPETITIVA
→ row/lista eficiente

RESUMO AUTÔNOMO
→ card quando semanticamente útil

DECISÃO LOCAL
→ bloco contextual

DADO COMPLEMENTAR
→ revelação progressiva
```

Listas podem ser densas quando a comparação entre muitos itens é a tarefa principal.

Formulários, decisões e ações rápidas devem receber mais respiro.

---

## 8. Decisões visuais estáveis

### UI-DEC-001 — Ferramenta comercial, não console administrativo

A percepção dominante do produto deve ser de ferramenta de ação comercial.

### UI-DEC-002 — Row/lista é padrão de repetição

Cards exigem justificativa semântica.

### UI-DEC-003 — Azul profundo ancora identidade

Azul é utilizado para identidade, confiança e elementos estruturais selecionados.

### UI-DEC-004 — Teal concentra ação

A cor de maior energia visual deve permanecer concentrada em ação dominante e seleção relevante.

### UI-DEC-005 — Dado Protheus carrega confiança

Informações externas relevantes precisam ter vocabulário visual para atualidade, atualização, incerteza e indisponibilidade.

### UI-DEC-006 — Densidade varia pela tarefa

Densidade não é decidida isoladamente pelo dispositivo.

### UI-DEC-007 — Desktop aproveita simultaneidade; mobile preserva foco

Desktop pode exibir lista + detalhe quando isso reduz alternância. Mobile pode separar superfícies sem reduzir capacidade.

### UI-DEC-008 — Tema claro é o compromisso atual

Dark mode não bloqueia o primeiro horizonte.

---

## 9. Sistema de cores

### 9.1. Tokens iniciais

| Token | Valor inicial | Papel |
| --- | --- | --- |
| `color.brand.primary` | `#0F3D56` | identidade e confiança |
| `color.action.primary` | `#0F766E` | ação dominante |
| `color.text.primary` | `#17202A` | conteúdo principal |
| `color.text.secondary` | `#556273` | informação secundária |
| `color.surface.canvas` | `#F7F9FB` | fundo principal |
| `color.surface.raised` | `#FFFFFF` | superfície elevada |
| `color.surface.subtle` | `#EEF3F6` | agrupamento leve |
| `color.border.default` | `#D7E0E7` | separação |
| `color.feedback.success` | `#147D4C` | sucesso |
| `color.feedback.warning` | `#A15C00` | atenção |
| `color.feedback.danger` | `#B42318` | erro/risco |
| `color.feedback.info` | `#175CD3` | informação |

Valores são parte da direção visual inicial do caso e devem permanecer sujeitos aos gates de contraste e acessibilidade.

### 9.2. Regra de função

```text
NEUTROS
= estrutura

AZUL PROFUNDO
= identidade / confiança

TEAL
= ação e seleção relevante

CORES DE FEEDBACK
= estado semântico
```

Cor não deve ser o único meio de comunicar estado.

Se muitas áreas simultaneamente usam `color.action.primary`, a hierarquia está incorreta.

---

## 10. Tipografia

Família visual oficial proposta e aprovada no cenário:

**Inter**

Motivos:

- boa leitura em interfaces de densidade variável;
- boa legibilidade numérica;
- adequação a desktop e mobile;
- neutralidade suficiente para permitir que conteúdo e hierarquia dominem.

A forma concreta de carregamento, distribuição ou empacotamento da fonte pertence às etapas técnicas.

### 10.1. Escala inicial

| Papel | Tamanho / linha | Peso |
| --- | --- | --- |
| Display | 32 / 40 | 700 |
| Título principal | 24 / 32 | 600 |
| Título de seção | 18 / 24 | 600 |
| Corpo | 16 / 24 | 400 |
| Label | 14 / 20 | 500 |
| Corpo secundário | 14 / 20 | 400 |
| Meta | 12 / 16 | 500 |

### 10.2. Regras

- evitar caixa alta em blocos extensos;
- labels permanecem legíveis com texto ampliado;
- números devem preservar unidade e contexto;
- truncamento não pode esconder informação necessária à decisão;
- valores financeiros usam formatação local apropriada;
- informação temporal deve esclarecer momento ou período quando necessário.

---

## 11. Espaçamento, radius, borda e elevação

Unidade base:

```text
4 px
```

Escala inicial:

```text
space.1 = 4
space.2 = 8
space.3 = 12
space.4 = 16
space.6 = 24
space.8 = 32
space.10 = 40
space.12 = 48
```

Radius:

```text
radius.sm = 6
radius.md = 10
radius.lg = 14
```

Borda padrão:

```text
1 px
```

Elevação deve ser discreta e funcional.

Hierarquia deve vir prioritariamente de:

- posição;
- espaçamento;
- tipografia;
- agrupamento;
- contraste;
- somente depois, elevação.

---

## 12. Superfícies

Três níveis conceituais principais:

### Canvas

Plano estrutural do produto.

### Surface

Área funcional principal.

### Raised

Sobreposição ou contexto temporário que realmente precisa destacar-se do plano atual.

Não criar profundidade visual sem função.

---

## 13. Iconografia

Direção:

- estilo linear;
- traço consistente;
- linguagem única dentro da mesma superfície;
- estados ativo/inativo coerentes;
- rótulo quando o significado não for universalmente reconhecível;
- nome acessível obrigatório para controles baseados em ícone.

A etapa não escolhe pacote de implementação.

---

## 14. Movimento

Movimento possui função informativa.

Categorias:

```text
MICROFEEDBACK
→ curto e discreto

TRANSIÇÃO LOCAL
→ preserva orientação

TRANSIÇÃO DE SUPERFÍCIE
→ explica mudança de contexto

SUCESSO
→ confirmação proporcional, sem celebração exagerada
```

Movimento ornamental permanente é incompatível com a direção.

Redução de movimento deve possuir alternativa equivalente.

---

## 15. Estratégia por form factor

### 15.1. Desktop

Direção:

```text
SIDEBAR LEVE
+
ÁREA PRINCIPAL
+
CONTEXTO SECUNDÁRIO QUANDO ÚTIL
```

O desktop pode usar simultaneidade para reduzir alternância entre lista e detalhe.

A navegação global deve permanecer visualmente estável durante tarefas de exploração e pode ser reduzida ou retirada em fluxos realmente focados.

### 15.2. Mobile

Direção:

```text
NAVEGAÇÃO PRINCIPAL COMPACTA
+
SUPERFÍCIES SEQUENCIAIS
```

A composição pode mudar, mas deve preservar:

- prioridade;
- resultado;
- semântica;
- acesso às capacidades;
- segurança.

### 15.3. Tablet

Não possui composição canônica independente neste estágio. Deve herdar regras de identidade e adaptar composição conforme largura e contexto, sem assumir que é apenas desktop comprimido.

---

## 16. Arquitetura visual de navegação

Destinos globais derivados do produto:

- Hoje;
- Clientes;
- Prospects;
- Gestão, para perfis elegíveis.

Busca de cliente/prospect deve permanecer facilmente acessível.

A existência de espaço visual não autoriza novo destino.

---

## 17. Tela-chave: Hoje

**ID:** UI-SCR-001

**Objetivo:** permitir ao vendedor decidir o trabalho comercial imediato.

**Hierarquia:**

```text
CONTEXTO LEVE
↓
PRÓXIMAS AÇÕES
↓
CLIENTES QUE MERECEM ATENÇÃO
↓
RETORNOS / PENDÊNCIAS
↓
INFORMAÇÃO COMPLEMENTAR
```

**Evitar:**

- faturamento anual como primeiro bloco;
- ranking da equipe;
- conjunto de KPIs executivos dominando viewport;
- excesso de gráficos.

A superfície não é tratada como dashboard executivo.

---

## 18. Tela-chave: Clientes

**ID:** UI-SCR-002

**Objetivo:** encontrar e selecionar cliente com eficiência.

**Hierarquia:**

```text
BUSCA
↓
FILTROS NECESSÁRIOS
↓
ROWS DE CLIENTE
↓
CONTEXTO / ESTADO
```

Cada row pode conter, conforme necessidade validada:

- nome;
- identificador empresarial relevante;
- responsável;
- sinal de atenção;
- próxima ação;
- contexto curto.

Card grande por cliente não é padrão.

---

## 19. Tela-chave: Cliente

**ID:** UI-SCR-003

**Objetivo:** compreender relacionamento e continuar a ação comercial.

**Hierarquia:**

```text
IDENTIDADE DO CLIENTE
↓
PRÓXIMA AÇÃO / SITUAÇÃO ATUAL
↓
CONTEXTO COMERCIAL RESUMIDO
↓
HISTÓRICO
↓
CONTEXTO PROTHEUS
↓
DETALHES SECUNDÁRIOS
```

O Protheus permanece presente como contexto, não como reprodução de telas do ERP.

---

## 20. Tela-chave: Prospect

**ID:** UI-SCR-004

**Objetivo:** registrar e conduzir relação antes do cadastro formal no Protheus.

Hierarquia:

```text
IDENTIDADE MÍNIMA
↓
CONTEXTO
↓
AÇÃO
↓
HISTÓRICO
```

O visual não deve induzir o usuário a acreditar que prospect já é cliente formal do ERP.

---

## 21. Tela-chave: Gestão

**ID:** UI-SCR-005

**Objetivo:** identificar onde a intervenção gerencial é necessária.

Hierarquia:

```text
EXCEÇÕES
↓
CONTEXTO DE CARTEIRA
↓
ATIVIDADE
↓
INDICADORES
```

Esta superfície pode possuir densidade maior que a experiência do vendedor, desde que não contamine a tela operacional do vendedor.

---

## 22. Tela-chave: Pedido

**ID:** UI-SCR-006

**Objetivo:** consultar contexto de pedido quando o resumo do cliente não é suficiente.

Hierarquia:

```text
ESTADO
↓
RESUMO
↓
ITENS / CONTEXTO
↓
EVENTOS RELEVANTES
```

A superfície é consulta comercial, não rotina transacional do Protheus.

---

## 23. Histórico comercial

Direção visual:

```text
LINHA TEMPORAL LEVE
```

Cada entrada pode representar:

- tipo;
- autor;
- momento;
- resultado;
- próxima ação relacionada.

Não transformar cada evento em card pesado por padrão.

---

## 24. Domain Component: NextAction

**ID:** UI-CMP-001

Componente central para representar próxima ação comercial.

Deve manter semântica coerente em:

- Hoje;
- Cliente;
- Carteira;
- Gestão.

Estados conceituais:

- planejada;
- hoje;
- vencida;
- concluída;
- não aplicável.

Cor é reforço, não única diferenciação.

---

## 25. Domain Component: ERPDataStatus

**ID:** UI-CMP-002

Componente ou padrão destinado a comunicar confiabilidade/contexto de dados externos.

Estados conceituais:

- atual;
- atualizando;
- possivelmente desatualizado;
- indisponível.

Pode acompanhar informações como:

- pedido;
- estoque;
- financeiro permitido;
- histórico de compra.

Não deve expor jargão técnico desnecessário.

---

## 26. Domain Component: ClientRow

**ID:** UI-CMP-003

Unidade principal para representação repetitiva de cliente.

Propósito:

- permitir leitura rápida;
- permitir comparação entre itens;
- sinalizar contexto suficiente para seleção;
- evitar densidade causada por cards grandes.

---

## 27. Domain Component: ActivityItem

**ID:** UI-CMP-004

Representa evento do histórico comercial.

Deve permitir distinguir:

- natureza do evento;
- autoria;
- momento;
- resumo útil;
- relação com próxima ação quando existir.

---

## 28. Domain Component: OrderSummary

**ID:** UI-CMP-005

Resumo de pedido para contexto comercial.

Pode representar:

- identificação;
- data;
- valor quando autorizado;
- estado;
- indicador de confiança/atualidade.

Não deve reproduzir integralmente a rotina de pedido do ERP.

---

## 29. Domain Component: OwnershipBadge

**ID:** UI-CMP-006

Representa responsabilidade comercial quando relevante.

Não deve expor dados adicionais de carteira apenas por estar visível.

---

## 30. Componentes gerais conceituais

A estrutura conceitual do Design System é:

```text
FOUNDATION
↓
PRIMITIVES
↓
COMPONENTS
↓
DOMAIN COMPONENTS
↓
PATTERNS
↓
SCREENS
```

### Foundation

- cor;
- tipografia;
- spacing;
- radius;
- borda;
- elevação;
- movimento;
- iconografia.

### Primitives

Exemplos conceituais:

- Text;
- Icon;
- Surface;
- Divider;
- Stack;
- Inline;
- Pressable.

### Components

Exemplos conceituais:

- Button;
- Field;
- SearchField;
- Row;
- Badge;
- Banner;
- Dialog;
- Sheet;
- Tabs.

### Domain Components

- ClientRow;
- PriorityItem;
- ActivityItem;
- NextAction;
- OrderSummary;
- ERPDataStatus;
- OwnershipBadge.

### Patterns

- AttentionList;
- ClientTimeline;
- ERPContext;
- QuickInteraction;
- OwnershipTransfer.

### Screens

- Hoje;
- Clientes;
- Cliente;
- Prospect;
- Gestão;
- Pedido.

Esta organização não determina estrutura de pastas ou framework.

---

## 31. Regra para cards

> **Card não é o container padrão do CRM.**

Usar card quando representar:

- entidade suficientemente autônoma;
- resumo com decisão própria;
- grupo semântico realmente independente.

Não usar apenas para decorar ou separar visualmente conteúdo homogêneo.

---

## 32. Botões

Hierarquia conceitual:

```text
PRIMARY
→ ação dominante

SECONDARY
→ alternativa relevante

TERTIARY
→ ação auxiliar

DESTRUCTIVE
→ consequência explícita
```

Quando houver próximo passo claro, apenas uma ação deve parecer primária no estado atual.

---

## 33. Campos

Campos devem favorecer preenchimento curto e previsível.

Regras:

- label persistente;
- placeholder não substitui label;
- erro próximo do campo;
- texto já válido não deve ser perdido por falha recuperável;
- campos não recebem card individual sem necessidade;
- ajuda aparece somente quando reduz erro ou ambiguidade.

Estados conceituais:

- default;
- focus;
- filled;
- disabled;
- read-only;
- error.

---

## 34. Tags, pills e badges

Podem representar estados curtos, como:

- Hoje;
- Vencido;
- Prospect;
- Cliente.

Não devem substituir textos complexos nem criar uma cor saturada diferente para cada situação.

---

## 35. Dados financeiros

A linguagem visual deve permitir representar:

```text
INFORMAÇÃO DISPONÍVEL
INFORMAÇÃO RESTRITA
INFORMAÇÃO INDISPONÍVEL
```

O sistema visual não deve induzir exposição completa de dados financeiros quando o papel do usuário exige apenas um sinal operacional, como existência de restrição comercial.

---

## 36. Estados visuais transversais

| Estado | Direção |
| --- | --- |
| Loading | preservar geometria e contexto quando possível |
| Vazio | explicar sem decorar artificialmente |
| Erro local | próximo do contexto |
| ERP indisponível | explicar fonte e impacto quando útil |
| Dado antigo | sinal explícito de incerteza |
| Sem permissão | comportamento esperado, não erro técnico genérico |
| Ação vencida | texto + semântica visual |
| Sucesso | confirmação discreta |
| Operação parcial | distinguir confirmado de não confirmado |

---

## 37. Empty states

Estado vazio deve responder:

```text
O QUE ESTÁ AUSENTE?
HÁ UMA AÇÃO REAL POSSÍVEL?
```

Não usar ilustração ou CTA apenas para preencher espaço.

Exemplo: vendedor sem permissão para criar cliente formal não deve receber CTA visual de "Criar cliente" apenas porque a lista está vazia.

---

## 38. Acessibilidade visual e de interação

Direção obrigatória:

- contraste verificável;
- foco visível;
- labels persistentes;
- navegação por teclado no desktop;
- alvos de toque adequados;
- texto ampliável;
- zoom/reflow;
- informação não dependente apenas de cor;
- ícones com nome acessível;
- movimento reduzível;
- gráficos futuros com equivalente textual quando indispensáveis.

A paleta inicial não dispensa validação completa por estado e componente.

---

## 39. Microcopy visual

Vocabulário preferido:

- Cliente;
- Prospect;
- Carteira;
- Próxima ação;
- Pedido;
- Histórico;
- Responsável.

Evitar exposição ao usuário de termos como:

- entity;
- mutation;
- sync job;
- tenant;
- foreign key;
- erro HTTP.

A especificação completa de mensagens pertence à UX.

---

## 40. Inventário visual inicial

| Domínio | Superfícies |
| --- | --- |
| Trabalho diário | Hoje |
| Clientes | lista, detalhe |
| Prospects | lista, criação/detalhe |
| Relacionamento | histórico, interação, próxima ação |
| Protheus | resumos de pedido, compra, estoque e estado externo |
| Carteira | responsabilidade, transferência |
| Gestão | exceções, carteira, atividade, indicadores |
| Conta | autenticação e perfil ainda a detalhar em UX |

Inventário não define ordem de implementação.

---

## 41. Gates de UI

### UI-GATE-01 — Hierarquia

Core comercial e ação dominante aparecem corretamente.

### UI-GATE-02 — Foundation

Tokens, tipografia, spacing, radius, bordas e semântica de cores não possuem lacunas materiais.

### UI-GATE-03 — Componentes

Componentes centrais possuem variantes, estados e regras de acessibilidade suficientes para alimentar UX.

### UI-GATE-04 — Telas-chave

Hoje, Clientes e Cliente possuem anatomia aprovada.

### UI-GATE-05 — Dados Protheus

Atualidade, incerteza e indisponibilidade possuem linguagem visual própria.

### UI-GATE-06 — Estados

Loading, vazio, erro, permissão e operação parcial estão cobertos quando aplicáveis.

### UI-GATE-07 — Acessibilidade

Contraste, foco, toque, texto ampliado e não dependência de cor foram considerados.

### UI-GATE-08 — Form factors

Mobile e desktop possuem composição coerente com seus contextos.

### UI-GATE-09 — Rastreabilidade

Telas e componentes apontam para decisões de produto e princípios aplicáveis.

---

## 42. Revisão simulada com stakeholders

### Diretor

Aprovou a separação entre azul como identidade e teal como ação e reforçou que a interface não deve ser "toda colorida".

### Vendedor

Aprovou o uso de listas/rows para clientes por considerar cards grandes inadequados quando há muitos clientes para consultar.

### Gerente

Aprovou maior densidade na área de gestão desde que essa densidade não contamine a experiência principal do vendedor.

### TI

Reforçou a importância de representar visualmente a atualidade dos dados do Protheus, principalmente estoque e pedido.

---

## 43. Rastreabilidade principal

| Decisão visual | Origem |
| --- | --- |
| ferramenta comercial, não console | P-PROD-04, persona primária e Princípios UX/UI |
| ação domina dashboard | PO + CRM-UX-01 |
| row/lista para repetição | princípio de densidade proporcional |
| Protheus como contexto | Briefing + CRM-UX-02 |
| estado de confiança | BR-012 + CRM-UX-03 |
| registro leve | P-PROD-03 + CRM-UX-04 |
| gestão não cria burocracia | HYP-005 + CRM-UX-05 |
| ruído é falha | HYP-007 + CRM-UX-06 |
| mobile e desktop com composições próprias | P3 + responsividade dos Princípios |

---

## 44. Itens deliberadamente não definidos

Esta etapa não escolheu:

- framework;
- biblioteca de componentes;
- pacote de ícones;
- biblioteca de animação;
- linguagem;
- runtime;
- provider;
- arquitetura;
- banco;
- estratégia de sync;
- contrato físico da API Protheus;
- ordem detalhada de cada jornada;
- comportamento exato de Voltar;
- mensagens completas de erro;
- política de rascunho;
- algoritmo da lista de atenção.

Esses itens pertencem às etapas posteriores ou continuam como pendências canônicas.

---

## 45. Quality Gate

```text
UI_DIRECTION_METHOD_VALIDATION: PASS
PRODUCT_SCOPE_CHANGED: NO
BUSINESS_RULE_CHANGED: NO
DETAILED_UX_FLOW_CREATED: NO
TECH_STACK_SELECTED: NO
VISUAL_THESIS: DEFINED
FOUNDATION: DEFINED
FORM_FACTORS: DEFINED
DESIGN_SYSTEM_CONCEPT: DEFINED
KEY_SCREEN_ANATOMY: DEFINED
ACCESSIBILITY_DIRECTION: DEFINED
UI_DIRECTION_READINESS: SUFFICIENT
```

---

## 46. Handoff para Especificação de UX

A próxima etapa recebe:

- tese visual;
- personalidade;
- hierarquia visual;
- estratégia por form factor;
- tokens;
- tipografia;
- spacing, superfícies e radius;
- linguagem de iconografia e movimento;
- componentes conceituais;
- domain components;
- anatomia das telas-chave;
- estados visuais transversais;
- critérios de acessibilidade;
- inventário;
- gates de UI.

A Especificação de UX deve definir como as jornadas funcionam ponta a ponta sem redefinir silenciosamente a identidade ou o contrato visual aprovado.

```text
NEXT_STAGE: 05 — Especificação de UX
```

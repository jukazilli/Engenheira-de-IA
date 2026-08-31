---
document_id: CASE-01-UXUI-PRINCIPLES
title: Princípios de UX e UI — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: principios-ux-ui
type: transversal-constitution
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
next_document: 04_Direcao_de_UI_e_Design_System.md
principles_readiness: SUFFICIENT
---

# Princípios de UX e UI — CRM para gestão de clientes e pedidos

## 1. Propósito

Este documento estabelece a constituição transversal de experiência e interface do CRM comercial do Caso 01.

Ele transforma decisões já aprovadas de produto em regras para julgar futuras decisões de interface sem definir ainda layout final, wireflows completos, framework, biblioteca ou implementação.

A pergunta central é:

> **Como garantir que toda interface reduza o esforço para compreender e continuar uma relação comercial, em vez de transformar coleta de informação e operação de sistema em objetivo maior do que o próprio trabalho do vendedor?**

A principal ameaça de experiência identificada no caso é repetir a falha operacional já vivida pelo cliente:

```text
CRM
↓
mais campos e controles
↓
mais trabalho para o vendedor
↓
planilha e WhatsApp continuam existindo
↓
duplicidade operacional
↓
CRM é abandonado
```

A interface deve quebrar esse ciclo.

---

## 2. Base consumida

Esta baseline consome integralmente:

- `00_Discovery.md`;
- `01_Pesquisa_e_Viabilidade.md`;
- `02_Briefing_de_Produto_e_Escopo.md`;
- `03_Visao_de_Product_Owner.md`.

Decisões de produto especialmente relevantes para UX/UI:

- vendedor é a persona primária de decisão do core;
- ação comercial tem precedência sobre dashboard gerencial no fluxo operacional;
- Protheus permanece autoridade dos dados e processos ERP definidos como canônicos;
- o CRM não pode exigir dupla manutenção sistemática;
- histórico comercial pertence à empresa;
- descoberta de cliente de outra carteira não libera automaticamente seu histórico;
- informação financeira é proporcional ao papel;
- informação do Protheus precisa carregar estado de confiança;
- o produto precisa funcionar em desktop e mobile;
- offline completo ainda não é requisito aprovado;
- registro de interação precisa ser proporcional;
- uma lista de atenção excessivamente ruidosa é considerada falha de produto.

---

## 3. Regra-mãe de experiência

> **A interface deve reduzir o esforço para compreender e continuar uma relação comercial; nunca transformar a coleta de informação em objetivo maior que o próprio trabalho comercial.**

Essa regra prevalece sobre preferências visuais locais.

---

## 4. Tarefas mentais dominantes

### Vendedor

O vendedor entra no produto principalmente para responder:

```text
O que preciso fazer agora?
```

```text
O que aconteceu com este cliente?
```

```text
Qual deve ser meu próximo passo?
```

```text
O que está acontecendo com este pedido?
```

### Gerente

```text
Onde minha intervenção é necessária?
```

### Diretor

```text
A operação comercial está funcionando?
```

Regra derivada:

> Não tentar responder todas essas perguntas com a mesma hierarquia ou na mesma superfície.

---

## 5. Hierarquia funcional transversal

Para o vendedor:

```text
PRIORIDADE
↓
CLIENTE
↓
CONTEXTO
↓
AÇÃO
↓
RESULTADO
↓
PRÓXIMO PASSO
```

Para o gerente:

```text
EXCEÇÃO
↓
CONTEXTO
↓
INTERVENÇÃO
```

Para o diretor:

```text
SINAL
↓
TENDÊNCIA
↓
DECISÃO
```

Regra geral:

```text
AÇÃO COMERCIAL
>
CONTEXTO
>
DETALHE OPERACIONAL
>
RELATÓRIO
```

Essa hierarquia não determina posição física final dos elementos. Ela determina precedência cognitiva.

---

## 6. Aplicação dos princípios canônicos da metodologia

### P1 — Começar pelo problema e pela próxima decisão

Toda superfície deve permitir reconhecer rapidamente:

- onde o usuário está;
- o que importa agora;
- o que mudou;
- qual decisão precisa ser tomada;
- qual é o próximo passo.

Ao abrir um cliente, a prioridade não é expor todos os dados existentes. É permitir responder:

> O que aconteceu e o que preciso fazer agora?

---

### P2 — Uma ação dominante por estado

Quando houver um próximo passo claro, uma ação deve dominar visualmente.

Exemplo para retorno pendente:

```text
DOMINANTE
registrar contato / concluir ação

SECUNDÁRIO
reagendar

TERCIÁRIO
ver detalhes adicionais
```

Não apresentar edição, pedido, estoque, financeiro, histórico, tarefa, WhatsApp, transferência e demais ações com o mesmo peso.

Uma ação dominante não significa um único botão na tela; significa hierarquia inequívoca.

---

### P3 — Contexto real de uso primeiro

O vendedor pode estar:

- no escritório;
- em notebook;
- no celular;
- visitando cliente;
- falando ao telefone enquanto consulta o CRM;
- utilizando rede móvel;
- sofrendo interrupções frequentes.

Consequências:

- exigir pouca memória de trabalho;
- permitir retomada rápida;
- não pedir informação que o sistema já conhece;
- evitar depender de código interno do Protheus como memória do usuário;
- preservar contexto de cliente entre ações relacionadas;
- considerar toque, teclado e mouse conforme o form factor.

---

### P4 — Complexidade fica no sistema

O Protheus pode trabalhar com empresa, filial, código, loja, pedido, item, liberação, estoque, financeiro, nota, customizações e outros estados internos.

Essa estrutura não deve ser exposta integralmente apenas porque existe.

Exemplo de tradução adequada:

```text
Pedido 012345
Aguardando liberação
```

com detalhe progressivo quando necessário.

Regra vinculante:

> **A estrutura interna do Protheus não define automaticamente a arquitetura da informação do CRM.**

O CRM não deve parecer uma cópia simplificada das rotinas do ERP.

---

### P5 — Menor interrupção suficiente

Usar a superfície proporcional ao peso da tarefa.

Direções:

- validação de campo → feedback inline;
- escolha curta contextual → superfície local;
- poucas ações relacionadas → menu ou ação contextual;
- risco ou consequência relevante → confirmação proporcional;
- tarefa extensa ou independente → superfície focada;
- detalhe opcional curto → revelação progressiva.

Não transformar decisão curta em fluxo longo.

Não comprimir uma tarefa complexa em componente pequeno apenas para evitar navegação.

---

### P6 — Mudou a tarefa mental, mudou a superfície

Se o vendedor está compreendendo relacionamento com o cliente e consulta apenas status, data e valor de um pedido, a informação pode permanecer contextual.

Se passa a explorar itens, entregas, faturamentos, eventos ou histórico próprio do pedido, existe nova tarefa mental e uma superfície específica pode ser necessária.

Regra:

> **Não comprimir uma nova tarefa mental dentro da tela do cliente apenas para evitar navegação.**

---

### P7 — Estado e confiança são visíveis

Informações vindas do Protheus devem distinguir, quando relevante:

```text
DADO CONFIRMADO
DADO SENDO ATUALIZADO
DADO POSSIVELMENTE DESATUALIZADO
PROTHEUS TEMPORARIAMENTE INDISPONÍVEL
ERRO RECUPERÁVEL
SEM PERMISSÃO
```

A ausência de erro não equivale a confirmação de atualidade.

Quando isso afetar decisão comercial, a interface pode precisar apresentar informação equivalente a:

```text
Atualizado há 2 min
```

ou

```text
Não foi possível confirmar agora
```

Nunca expor jargão técnico como `HTTP 503`, timeout de API ou nome de job ao usuário comum.

O CRM não pode transformar falha de consulta em valores falsamente definitivos como `estoque 0`, `R$ 0` ou `sem pedidos`.

---

### P8 — Prevenir e recuperar antes de culpar

Se uma falha ocorrer durante registro, preservar conteúdo válido quando seguro.

Se houver possível duplicidade de empresa, orientar o usuário em vez de apenas rejeitar a ação.

Exemplo conceitual:

> Encontramos uma empresa que pode ser a mesma.

Com alternativas coerentes ao papel e à regra de negócio.

Mensagens devem explicar:

- o que aconteceu;
- o que foi preservado;
- o que pode ser feito agora.

Evitar linguagem de culpa.

---

### P9 — Acessibilidade integra a decisão

Desde o desenho, considerar:

- navegação por teclado no desktop;
- foco visível;
- ordem de leitura;
- semântica apropriada;
- leitor de tela;
- alvos de toque adequados;
- texto ampliado;
- zoom e reflow;
- redução de movimento;
- alternativa a gestos;
- informação que não dependa somente de cor.

Exemplo:

`cliente precisa de atenção` não pode ser comunicado apenas por uma bolinha vermelha. Deve existir texto, símbolo ou semântica equivalente, com cor como reforço.

---

### P10 — Consistência vem de comportamento compartilhado

Mesma intenção deve utilizar linguagem e comportamento compatíveis.

Exemplo: `definir próxima ação` não deve aparecer sem justificativa como `Agendar`, ícone isolado de relógio, `Criar tarefa` e item escondido em menu, cada um com comportamento diferente.

Consistência significa preservar semântica, não repetir o mesmo layout em todo lugar.

---

### P11 — Privacidade é padrão

Aplicar minimização visual.

#### Carteira de outro vendedor

O usuário pode precisar saber:

- empresa;
- CNPJ ou identificador necessário;
- responsável.

Isso não autoriza automaticamente acesso a:

- histórico;
- anotações;
- negociação;
- financeiro;
- contatos privados;
- demais contexto restrito.

#### Informação financeira

Se a necessidade for saber se existe impedimento comercial, isso não autoriza mostrar financeiro completo.

Perguntas obrigatórias para cada superfície:

- este dado precisa aparecer aqui?
- precisa aparecer completo?
- esse papel pode vê-lo?
- precisa permanecer visível depois da tarefa?
- pode ser ocultado por padrão?

---

### P12 — Identidade própria, aprendizado externo

Referências externas podem ensinar:

- hierarquia;
- ritmo;
- ergonomia;
- convenções;
- padrões de interação;
- acessibilidade.

Elas não autorizam copiar automaticamente:

- marca;
- navegação;
- layout;
- workflow;
- cor;
- linguagem;
- regras de domínio.

A solução deve pertencer ao CRM deste cliente.

---

## 7. Princípios específicos derivados do caso

### CRM-UX-01 — Próxima ação antes de volume de informação

Quando a tarefa for operacional, clareza sobre o próximo passo possui precedência sobre exposição de grande volume de dados.

---

### CRM-UX-02 — Protheus aparece como contexto, não como interface

O usuário não deve precisar compreender a estrutura interna do ERP para usar o CRM.

---

### CRM-UX-03 — Informação externa carrega confiança

Dado dependente do Protheus só pode parecer atual quando o produto possuir evidência suficiente disso.

---

### CRM-UX-04 — Registro deve ser proporcional

Quantidade de campos e decisões exigidos para registrar interação deve ser proporcional ao valor necessário para continuidade comercial, gestão e obrigação legítima.

Campos não entram apenas porque poderiam gerar relatório.

---

### CRM-UX-05 — Gestão observa o trabalho; não cria trabalho artificial

Necessidade gerencial não deve gerar coleta manual que não produza valor operacional suficiente para o vendedor ou para obrigação real da empresa.

---

### CRM-UX-06 — Ruído é falha de priorização

Uma lista de atenção que mostra quase todos os clientes deixa de ajudar a decidir prioridade.

Mais itens não significa melhor gestão.

---

### CRM-UX-07 — Permissão deve parecer comportamento, não erro técnico

Quando uma informação não pertence ao papel do usuário, a interface deve refletir a política de forma compreensível, sem parecer falha inesperada do sistema.

---

### CRM-UX-08 — Ferramenta de ação comercial, não console administrativo

A percepção dominante do produto para vendedores deve ser de ferramenta de trabalho comercial e continuidade de relacionamento, não de sistema administrativo orientado a relatório.

---

## 8. Densidade de informação

A direção de densidade deve ser contextual.

Regras:

```text
BAIXA DENSIDADE
≠ SEMPRE MELHOR

ALTA DENSIDADE
≠ SISTEMA MAIS EFICIENTE
```

- listas grandes podem exigir alta eficiência visual;
- registro rápido deve evitar peso visual desnecessário;
- detalhe de cliente pode usar resumo + revelação progressiva;
- cards só devem existir quando agrupamento e autonomia justificarem;
- conteúdo repetitivo e homogêneo deve preferir estruturas mais leves quando apropriado.

Objetivo: **densidade cognitiva adequada à decisão**.

---

## 9. Política inicial de superfícies

| Necessidade | Direção de UX |
| --- | --- |
| erro ou ajuda de campo | inline |
| salvar interação simples | feedback local/discreto |
| escolher data de retorno | escolha contextual |
| poucas ações sobre cliente | menu contextual |
| ação irreversível ou de impacto | dialog proporcional |
| cadastro mais longo de prospect | superfície focada |
| detalhe extenso de pedido | superfície própria quando mudar a tarefa mental |
| ação dominante estável em formulário longo | pode permanecer acessível se não encobrir conteúdo/erro |

A Especificação de UX decidirá a aplicação concreta por jornada.

---

## 10. Estados obrigatórios do domínio integrado

Quando uma jornada depender do Protheus, considerar conforme aplicável:

- carregando;
- sem dados confirmados;
- dado disponível;
- dado possivelmente desatualizado;
- Protheus indisponível;
- erro recuperável;
- sem permissão;
- operação parcial;
- atualização em andamento.

Regra:

> ausência de dado e falha de consulta são estados diferentes.

---

## 11. Empty states

Estado vazio deve responder:

```text
O QUE ESTÁ AUSENTE?
POR QUE ISSO IMPORTA?
EXISTE AÇÃO REAL AGORA?
```

Não inventar CTA para preencher espaço.

Não usar linguagem de marketing genérica em superfícies operacionais.

Exemplo adequado:

> Nenhum cliente nesta carteira.

Ação só aparece se o papel realmente puder executá-la.

---

## 12. Microcopy

Preferir vocabulário conhecido pelo público:

- Cliente;
- Prospect;
- Carteira;
- Próxima ação;
- Pedido;
- Histórico;
- Responsável.

Evitar jargão interno ou técnico:

- entity;
- record;
- mutation;
- ERP sync;
- tenant;
- foreign key;
- nome interno de API.

CTAs devem nomear resultado real.

Mensagens de erro devem indicar próxima ação quando possível.

---

## 13. Estratégia responsiva em nível de princípio

Mobile e desktop devem preservar:

- prioridade;
- resultado;
- semântica;
- acesso às capacidades;
- segurança;
- compreensão do estado.

Não precisam repetir a mesma composição.

Direção preliminar:

### Desktop

Pode aproveitar simultaneidade quando isso reduzir alternância de contexto, por exemplo lista + contexto + detalhe.

### Mobile

Pode decompor o mesmo trabalho em superfícies sucessivas, preservando continuidade e ação dominante.

Breakpoints não devem apenas comprimir conteúdo até caber.

---

## 14. Gestos

Gesto pode complementar uma tarefa, mas nunca ser o único meio de executar função essencial.

Se `swipe` futuramente concluir ação, deve existir alternativa visível ou equivalente acessível.

Tutorial não deve ser usado para compensar função essencial escondida.

---

## 15. Contrato mínimo de futuras superfícies

Toda tela ou superfície relevante deverá registrar, no mínimo:

```text
Origem canônica:
OUT / J / US / BR aplicáveis

Usuário e contexto:

Tarefa mental:

Entrada:

Saída / retorno:

Ação dominante:

Ações secundárias:

Dados necessários:

Dados que não devem aparecer:

Estado Protheus:
aplicável / não aplicável

Estados obrigatórios:

Sensibilidade / permissão:

Superfície escolhida e justificativa:

Acessibilidade:

Alternativa a gesto/cor:

Responsividade:

Fora do recorte:

Evidência de aceite:
```

---

## 16. Definition of Ready de UX/UI do caso

Uma superfície está pronta para design detalhado quando:

- possui origem em outcome, jornada ou história aprovada;
- usuário e contexto estão claros;
- tarefa mental está explícita;
- ação dominante foi identificada;
- dependência do Protheus está reconhecida quando aplicável;
- estados críticos são conhecidos;
- sensibilidade e permissão foram avaliadas;
- princípios aplicáveis foram identificados;
- superfície proposta possui justificativa;
- fora de escopo está registrado;
- acessibilidade mínima foi considerada;
- existe critério para avaliar o resultado.

```text
READY DE UX/UI
≠
READY FOR CODEX
```

---

## 17. Definition of Done de UX/UI do caso

Uma tela ou fluxo pode ser aceito no nível de UX/UI quando, conforme aplicável:

- tarefa mental é compreensível;
- ação dominante é reconhecível;
- não existe duplicação visual sem justificativa;
- superfície corresponde ao peso da tarefa;
- loading, vazio, erro, sucesso e recuperação foram definidos;
- estado do Protheus é verdadeiro e compreensível;
- permissões estão representadas sem vazamento de informação;
- valores válidos são preservados após falha quando seguro;
- acessibilidade foi validada no nível esperado;
- gesto possui alternativa;
- foco, teclado, toque, zoom e texto ampliado foram considerados;
- microcopy não expõe jargão interno;
- evidência de revisão/usabilidade existe;
- owner apropriado validou o comportamento.

A Definition of Done técnica pertence às etapas posteriores.

---

## 18. Evidências e revisão humana do cenário

A execução desta etapa foi revisada no cenário simulado com stakeholders.

### Vendedor

Reforçou que o produto não pode exigir muitos campos após cada contato e precisa permitir consulta rápida de histórico durante conversas com clientes.

Isso reforça:

- P3;
- P4;
- CRM-UX-04.

### Gerente

Confirmou que informação gerencial só é útil se a coleta for sustentável para o vendedor.

Isso reforça `CRM-UX-05`.

### TI

Confirmou que indisponibilidade ou desatualização de dados do Protheus precisa ser explicitada.

Isso reforça `CRM-UX-03` e P7.

### Diretor

Confirmou que o produto deve ser percebido como ferramenta para vendedor, não como sistema administrativo.

Isso originou `CRM-UX-08`.

---

## 19. Rastreabilidade principal

| Princípio / decisão | Origem principal |
| --- | --- |
| ação comercial acima de relatório | Briefing + OUT-001 + persona U1 |
| registro proporcional | P-PROD-03 + HYP-003 + US-006 |
| estado confiável do Protheus | BR-012 / regra equivalente da baseline de PO |
| minimização de carteira | BR-004 + regras de acesso |
| informação financeira proporcional | BR-013 |
| ruído como falha | HYP-007 + revisão do gerente |
| mobile e desktop com composições próprias | contexto de campo + princípios P3/P6 |
| preservar histórico após falha | continuidade comercial + P8 |

---

## 20. Validação da metodologia nesta etapa

A etapa produziu critérios de julgamento sem redefinir produto ou antecipar sistema visual final.

Exemplo da transformação observada:

```text
PO
US-006 — Registrar interação

↓

PRINCÍPIOS
registro proporcional
preservar contexto
feedback local quando suficiente
falha não apaga entrada válida
não pedir dado apenas por interesse gerencial
```

E ainda não foram definidos:

- layout final;
- paleta;
- tipografia;
- componentes visuais concretos;
- wireflow;
- arquitetura;
- framework;
- API.

Resultado:

```text
UX_UI_PRINCIPLES_METHOD_VALIDATION: PASS
PRODUCT_SCOPE_CHANGED: NO
NEW_BUSINESS_RULE_CREATED: NO
VISUAL_SYSTEM_DEFINED: NO
DETAILED_WIREFLOW_DEFINED: NO
TRANSVERSAL_PRINCIPLES: DEFINED
CRM_SPECIFIC_PRINCIPLES: DEFINED
PRIVACY_POSTURE: DEFINED
PROTHEUS_TRUST_POSTURE: DEFINED
ACCESSIBILITY_POSTURE: DEFINED
PRINCIPLES_READINESS: SUFFICIENT
```

---

## 21. Handoff

Este documento torna elegível a execução de:

```text
04_Direcao_de_UI_e_Design_System.md
```

A etapa seguinte deve materializar visualmente estes princípios sem alterar silenciosamente:

- prioridade do vendedor;
- regra de autoridade do Protheus;
- privacidade entre carteiras;
- proporcionalidade do registro;
- hierarquia ação > contexto > detalhe > relatório;
- postura de confiança dos dados externos;
- estratégia responsiva orientada a contexto;
- acessibilidade desde o desenho.

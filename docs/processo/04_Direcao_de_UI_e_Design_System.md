---
document_id: PROCESS-04-DIRECAO-UI-DESIGN-SYSTEM
title: Direção de UI e Design System
status: draft-methodology
version: 0.1.0
stage: direcao-ui-design-system
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
  - Principios_de_UX_UI.md
produces: 04_Direcao_de_UI_e_Design_System.md
next_stage: 05_Especificacao_de_UX.md
---

# 04 — Direção de UI e Design System

## 1. Propósito

A **Direção de UI e Design System** é a etapa responsável por transformar a intenção de produto, a hierarquia de valor e os princípios de experiência já aprovados em uma **linguagem visual vinculante e reutilizável**.

A pergunta central desta etapa é:

> **Como o produto deve parecer, organizar informação e expressar estado, prioridade, identidade e confiança de forma consistente em todas as superfícies relevantes, sem antecipar fluxos detalhados de UX nem decisões de tecnologia que pertencem às etapas posteriores?**

Esta etapa define a expressão visual do produto e o contrato conceitual do Design System.

Ela deve permitir que a Especificação de UX detalhe jornadas sem reinventar identidade, componentes, hierarquia visual ou anatomia básica de cada superfície.

A saída desta etapa ainda **não autoriza código**.

---

## 2. Posição no processo

```text
00_Discovery.md
        ↓
01_Pesquisa_e_Viabilidade.md
        ↓
02_Briefing_de_Produto_e_Escopo.md
        ↓
03_Visao_de_Product_Owner.md
        ↓
Principios_de_UX_UI.md
        ↓
04_DIRECAO_DE_UI_E_DESIGN_SYSTEM
        ↓
05_Especificacao_de_UX.md
        ↓
CAMADAS TÉCNICAS POSTERIORES
```

A Visão de Product Owner define **resultado, prioridade, regra de negócio e comportamento esperado**.

Os Princípios de UX/UI definem **como decisões de interface devem ser julgadas**.

A Direção de UI e Design System define **como esses princípios se materializam visualmente**.

A Especificação de UX definirá **como as jornadas funcionam ponta a ponta, com transições, validações, exceções, mensagens contextuais, recuperação e critérios de usabilidade**.

---

## 3. Origem desta etapa

Esta etapa foi formalizada a partir da documentação real utilizada no DayGym.

No processo original, a Direção de UI funcionava como **fonte visual vinculante para UX, prototipação, engenharia e QA**, com uma tese visual explícita, sistema de cores, tipografia, grid, componentes, anatomia das telas, estados, acessibilidade, inventário e gates de passagem para UX.

Esse processo mostrou que uma documentação visual madura precisa ir além de uma paleta ou de um conjunto de componentes.

Ela precisa conectar:

```text
IDENTIDADE
        ↓
HIERARQUIA
        ↓
TOKENS
        ↓
COMPONENTES
        ↓
ESTADOS
        ↓
ANATOMIA DE TELA
        ↓
ACESSIBILIDADE
        ↓
RASTREABILIDADE COM PRODUTO
```

A metodologia preserva essa estrutura.

Ao mesmo tempo, corrige responsabilidades que no documento original estavam misturadas com tecnologia concreta. Nomes de pacotes, bibliotecas, frameworks ou APIs de implementação não pertencem à Direção de UI quando a escolha ainda será feita pelo Tech Lead.

---

## 4. Pré-requisitos obrigatórios

Antes de iniciar esta etapa, o ChatGPT deve consumir integralmente:

1. `00_Discovery.md`;
2. `01_Pesquisa_e_Viabilidade.md`;
3. `02_Briefing_de_Produto_e_Escopo.md`;
4. `03_Visao_de_Product_Owner.md`;
5. `Principios_de_UX_UI.md`.

Também deve analisar, quando existirem:

- identidade visual existente;
- logotipo e assets de marca;
- telas atuais;
- protótipos anteriores;
- screenshots;
- sistema legado;
- materiais de marketing relevantes;
- referências visuais aprovadas pelo humano;
- restrições de plataforma já confirmadas;
- requisitos de acessibilidade ou marca;
- decisões específicas para mobile, tablet, desktop, TV, wearable ou outros form factors.

A etapa não deve presumir que todos os dispositivos receberão a mesma composição apenas em tamanhos diferentes.

---

## 5. Responsabilidade central

Esta etapa deve responder:

```text
COMO O PRODUTO DEVE PARECER?

COMO SUA IDENTIDADE SE MANIFESTA?

O QUE RECEBE MAIOR PESO VISUAL?

COMO ESTADO, RISCO, ÊXITO E INCERTEZA APARECEM?

QUAIS TOKENS GOVERNAM A INTERFACE?

QUAIS COMPONENTES SÃO CANÔNICOS?

QUAL É A ANATOMIA VISUAL DAS TELAS-CHAVE?

COMO DIFERENTES FORM FACTORS PRESERVAM A MESMA IDENTIDADE?
```

Não deve responder:

```text
QUAL FRAMEWORK IMPLEMENTA ISSO?
QUAL PACOTE DE ÍCONES SERÁ INSTALADO?
QUAL BIBLIOTECA DE ANIMAÇÃO SERÁ USADA?
QUAL SISTEMA DE COMPONENTES SERÁ IMPORTADO?
QUAL BANCO OU PROVIDER SERÁ USADO?
```

Essas perguntas pertencem às etapas técnicas posteriores.

---

## 6. O que esta etapa pode canonizar

A Direção de UI e Design System pode canonizar:

- tese visual;
- personalidade visual;
- linguagem de marca dentro do produto;
- hierarquia visual;
- densidade visual;
- papéis semânticos de cor;
- paleta e tokens de cor do projeto;
- tipografia de interface;
- escala tipográfica;
- comportamento visual de números e unidades;
- grid;
- espaçamento;
- radius;
- bordas;
- elevação;
- regras de superfície;
- estilo e semântica de iconografia;
- regras para fotografia e ilustração;
- vocabulário de movimento;
- feedback háptico no nível de intenção, quando aplicável;
- arquitetura visual da navegação;
- diferença de composição entre form factors;
- anatomia visual de componentes;
- variantes e estados de componentes;
- camadas conceituais do Design System;
- anatomia das telas-chave;
- estados visuais transversais;
- critérios visuais de acessibilidade;
- inventário de telas e superfícies;
- gates de UI;
- critérios para que UX possa começar.

---

## 7. O que esta etapa não pode canonizar

Esta etapa não deve definir silenciosamente:

- novo público;
- nova funcionalidade;
- novo módulo;
- nova regra de negócio;
- mudança de prioridade de produto;
- novo modelo de receita;
- permissão não aprovada;
- jornada completa;
- ordem definitiva de passos de um fluxo;
- algoritmo;
- arquitetura de software;
- schema de dados;
- linguagem de programação;
- runtime;
- framework;
- biblioteca concreta;
- pacote npm;
- provider;
- estratégia de armazenamento;
- estratégia de sincronização;
- CI/CD;
- infraestrutura;
- estrutura física do repositório;
- implementação do Design System no código.

Se uma escolha visual implicar uma necessidade técnica, ela deve produzir um requisito para as etapas técnicas posteriores, não uma seleção prematura de tecnologia.

Exemplo:

```text
CORRETO NA UI
“O ícone deve manter a mesma linguagem visual entre plataformas e possuir estados ativo/inativo consistentes.”

INCORRETO NA UI
“Instalar pacote X versão Y.”
```

Outro exemplo:

```text
CORRETO NA UI
“A confirmação de sucesso pode usar feedback háptico complementar quando o dispositivo oferecer suporte.”

INCORRETO NA UI
“Usar SDK Y para haptics.”
```

---

## 8. Limite entre UI e UX

A separação entre esta etapa e a próxima deve ser explícita.

| Direção de UI e Design System | Especificação de UX |
| --- | --- |
| identidade visual | jornada ponta a ponta |
| tokens | ordem de passos |
| grid | decisões e bifurcações |
| componentes | transições entre telas |
| hierarquia | validação operacional |
| anatomia visual | recuperação completa |
| estados visuais | comportamento detalhado dos estados |
| form factors | regras de retomada |
| sistema de navegação visual | wireflows |
| acessibilidade visual | testes de usabilidade |

Uma anatomia de tela pode dizer:

```text
TOPO
CONTEÚDO PRINCIPAL
SUPORTE
AÇÃO DOMINANTE
ESTADOS VISUAIS
```

mas não deve substituir o fluxo completo da pessoa entre superfícies.

---

## 9. Modo de condução com o humano

A etapa deve ser conduzida de forma iterativa.

Antes de consolidar a direção, o ChatGPT deve identificar o que já foi decidido nos documentos anteriores e perguntar apenas pelas lacunas materiais.

Perguntas possíveis:

- já existe identidade visual?
- existe logo aprovado?
- existem cores obrigatórias?
- existe alguma estética que deve ser evitada?
- quais produtos ou interfaces são boas referências e por quê?
- quais referências são consideradas ruins e por quê?
- o produto deve parecer mais técnico, humano, premium, utilitário, editorial, lúdico ou outra combinação?
- existem contextos físicos que afetam legibilidade e toque?
- quais form factors fazem parte do horizonte atual?
- mobile, web e tablet representam a mesma composição ou experiências distintas?
- existem telas legadas que precisam ser preservadas parcialmente?
- existe preferência de tema claro/escuro?

A IA não deve transformar preferências vagas em decisão canônica sem validar a interpretação.

---

## 10. Tese visual

Toda Direção de UI deve produzir uma tese visual curta.

Ela deve explicar a relação entre:

- personalidade;
- hierarquia;
- cor;
- energia;
- densidade;
- confiança;
- contexto de uso.

Formato recomendado:

```text
TESE VISUAL

“O produto deve parecer <atributos desejados>.
<elemento estrutural> reduz <risco ou ruído>.
<elemento de ênfase> aparece quando <condição>.
<parte central do produto> domina a hierarquia e
<elementos secundários> não compram atenção artificialmente.”
```

A tese não deve ser uma coleção de adjetivos sem consequência visual.

---

## 11. Personalidade visual

A personalidade deve ser traduzida em decisões concretas.

Estrutura recomendada:

| Eixo | Expressar | Evitar |
| --- | --- | --- |
| atributo | como aparece visualmente | distorção indesejada |

Exemplos de eixos possíveis:

- profissional;
- humano;
- técnico;
- energético;
- calmo;
- premium;
- comunitário;
- editorial;
- operacional;
- institucional.

A quantidade de eixos deve ser pequena o suficiente para orientar decisões reais.

---

## 12. Uso de referências externas

Referência não é cópia.

Quando o usuário apresentar um produto como referência, a documentação deve registrar:

```text
REFERÊNCIA
        ↓
QUAL PROBLEMA ELA RESOLVE BEM?
        ↓
QUAL PRINCÍPIO PODE SER APRENDIDO?
        ↓
COMO ISSO SE TRADUZ PARA A IDENTIDADE DO PROJETO?
```

Não copiar automaticamente:

- cor;
- layout;
- navegação;
- card;
- animação;
- linguagem;
- marca;
- iconografia;
- padrão de monetização.

Referências podem ensinar hierarquia, ritmo, composição ou comportamento sem determinar a solução final.

---

## 13. Auditoria de interfaces existentes

Em projetos brownfield, a Direção de UI deve analisar o que já existe.

Para cada tela, superfície ou família de componentes, classificar:

```text
PRESERVAR
CORRIGIR
SUBSTITUIR
```

### Preservar

Elementos que já respeitam produto, princípios e identidade desejada.

### Corrigir

Elementos com valor funcional, mas hierarquia, densidade, acessibilidade ou consistência inadequadas.

### Substituir

Elementos que contradizem a direção aprovada ou geram dívida visual significativa.

A auditoria visual não autoriza alteração silenciosa de contrato de produto ou comportamento existente.

---

## 14. Hierarquia e densidade

A Direção de UI deve materializar os princípios de carga cognitiva.

Regras recomendadas:

- uma decisão dominante por viewport quando houver uma ação principal clara;
- ações secundárias não competem em peso visual;
- no máximo poucos níveis simultâneos de ênfase;
- conteúdo repetitivo não deve virar uma coleção de cards pesados por conveniência;
- cards são reservados para decisão, resumo ou entidade suficientemente autônoma;
- listas, rows e divisores são preferidos quando o conteúdo é repetitivo e homogêneo;
- textos auxiliares aparecem quando reduzem erro ou dão contexto;
- destrutivos não devem dominar superfícies de navegação;
- dados críticos recebem unidade, período e contexto.

A quantidade exata de níveis, dimensões e componentes depende do projeto.

---

## 15. Sistema de cores

Cor deve possuir papel semântico.

A documentação deve separar pelo menos:

```text
MARCA / AÇÃO
NEUTROS
SUPERFÍCIES
TEXTO
BORDA
SUCESSO
ALERTA
PERIGO
INFORMAÇÃO
```

### 15.1 Tokens semânticos

Preferir tokens que expressem função.

Exemplos:

```text
color.action.primary
color.action.secondary
color.text.primary
color.text.secondary
color.surface.canvas
color.surface.raised
color.border.default
color.feedback.success
color.feedback.warning
color.feedback.danger
```

Valores base podem existir dentro do tema, mas telas não devem depender semanticamente de “orange-700”, “blue-500” ou outra cor literal para expressar função.

### 15.2 Regra de ênfase

A cor de maior energia do produto não deve se tornar revestimento indiscriminado.

Se tudo recebe a cor de ação, nada indica a próxima decisão.

### 15.3 Tema claro e escuro

Quando ambos fizerem parte do produto:

- cada tema deve ter tokens próprios;
- contraste deve ser validado novamente;
- gráficos devem ser testados novamente;
- estados não podem depender de simples inversão automática;
- um tema não precisa bloquear o lançamento do outro quando estiver explicitamente fora do horizonte atual.

---

## 16. Tipografia

A Direção de UI pode escolher a **família tipográfica visual oficial** do produto.

Essa é uma decisão de identidade.

Porém, como a fonte será carregada, empacotada, hospedada ou entregue pertence às etapas técnicas.

A documentação deve definir:

- família principal;
- fallback conceitual;
- pesos permitidos;
- escala tipográfica;
- line-height;
- uso de caixa alta;
- comportamento de texto ampliado;
- estilos para dados numéricos;
- regras para unidades;
- truncamento permitido ou proibido.

### 16.1 Dados técnicos legíveis

Número sem contexto costuma ser ambíguo.

Preferir:

```text
22 kg
48 min
32 g de proteína
+2,5 kg desde 21 jul
```

em vez de:

```text
22
00:48:00
32 P
+2,5
```

A interface deve expressar unidade, período, fonte ou incerteza quando esses elementos mudarem a interpretação.

---

## 17. Grid, espaçamento e superfícies

O Design System deve possuir uma escala consistente.

Definir:

- unidade base;
- escala de spacing;
- margens;
- gutters;
- largura de leitura;
- safe areas;
- radius;
- borda;
- elevação;
- regra de superfície.

Evitar valores locais criados apenas porque “couberam”.

Exemplo de convenção:

```text
space.1
space.2
space.3
space.4
...
```

O valor concreto pertence ao projeto.

---

## 18. Estratégia por form factor

Responsividade não significa expandir a mesma tela indefinidamente.

A etapa deve decidir se:

```text
MOBILE
TABLET
DESKTOP
```

compartilham apenas tokens e identidade ou também a mesma composição.

Uma estratégia válida pode ser:

```text
MESMA IDENTIDADE
        ↓
MESMOS PRINCÍPIOS
        ↓
MESMOS DADOS E REGRAS
        ↓
COMPOSIÇÕES DIFERENTES POR CONTEXTO
```

Quando tablet ou desktop exigirem outra tarefa mental, densidade, modo de navegação ou quantidade de informação simultânea, devem receber direção própria.

Breakpoints são gatilhos de composição, não licença para comprimir conteúdo até caber.

---

## 19. Iconografia

A Direção de UI deve especificar a **linguagem visual da iconografia**.

Pode definir:

- estilo;
- peso de traço;
- tamanhos;
- estado ativo/inativo;
- uso de ícones próprios;
- quando rótulo é obrigatório;
- quando ícone isolado é permitido;
- como símbolos de marca podem aparecer.

Se uma família externa de ícones for desejada, o documento pode registrá-la como **referência visual ou requisito de consistência**, mas a escolha do pacote concreto de implementação e sua versão pertence ao Tech Lead.

Não misturar famílias incompatíveis na mesma superfície sem justificativa.

---

## 20. Imagens e ilustrações

Definir por contexto:

- fotografia;
- ilustração;
- imagem de produto;
- avatar;
- demonstração funcional;
- empty state;
- conteúdo social;
- conteúdo comercial.

Para cada contexto, registrar:

```text
PODE USAR?
QUAL FUNÇÃO?
QUAL PROPORÇÃO?
QUAL ESTILO?
QUAL CONTEÚDO É PROIBIDO?
```

Imagens não devem ocupar espaço apenas para preencher uma composição vazia.

---

## 21. Movimento

Movimento deve ter função.

A documentação pode definir categorias:

```text
MICROFEEDBACK
TRANSIÇÃO DE SUPERFÍCIE
TRANSIÇÃO DE TELA
ÊXITO RELEVANTE
REDUCE MOTION
```

Para cada categoria, registrar:

- intenção;
- intensidade;
- duração aproximada ou faixa;
- comportamento com redução de movimento;
- quando não usar.

Não escolher biblioteca de animação nesta etapa.

---

## 22. Háptica

Quando aplicável, definir a semântica de feedback háptico:

- confirmação leve;
- sucesso;
- alerta;
- erro;
- ausência de suporte.

Háptica é complementar.

Nunca deve ser a única confirmação de estado.

A tecnologia concreta de implementação será definida posteriormente.

---

## 23. Arquitetura visual de navegação

Esta etapa pode definir a arquitetura visual da navegação, desde que preserve decisões do produto.

Pode especificar:

- destinos globais;
- peso visual entre destinos;
- shell autenticado;
- shell público;
- bottom navigation;
- sidebar;
- tabs;
- trilhos;
- áreas persistentes;
- quando a navegação global desaparece para um fluxo focado.

Não deve inventar um destino novo apenas porque existe espaço disponível.

### 23.1 Shell global e fluxo focado

Distinguir:

```text
SHELL GLOBAL
→ contexto permanente do produto

FLUXO FOCADO
→ tarefa com começo e fim próprios
```

A Direção de UI define como ambos se apresentam visualmente.

A Especificação de UX define a sequência detalhada e as regras de entrada/saída.

---

## 24. Design System conceitual

Uma estrutura útil de camadas é:

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
- iconografia;
- feedback.

### Primitives

Elementos fundamentais de composição e semântica.

Exemplos conceituais:

- Text;
- Icon;
- Surface;
- Divider;
- Stack;
- Inline;
- Pressable;
- SafeArea.

### Components

Elementos reutilizáveis com comportamento visual próprio.

Exemplos:

- Button;
- Field;
- Row;
- Card;
- Banner;
- Sheet;
- Dialog;
- Tabs;
- Progress.

### Domain Components

Composições ligadas ao vocabulário do produto.

### Patterns

Composições recorrentes que resolvem uma tarefa maior.

### Screens

Composição final.

Screens não devem criar tokens locais ou componentes paralelos sem justificativa.

Esta hierarquia é **conceitual**.

Ela não determina pastas, packages ou framework.

---

## 25. Contrato de componente

Todo componente relevante deve especificar:

```text
NOME
PROPÓSITO
ANATOMIA
VARIANTES
ESTADOS
HIERARQUIA
ACESSIBILIDADE
CONTEÚDO
REGRAS DE USO
NÃO USAR QUANDO
```

Estados mínimos variam por componente, mas devem considerar quando aplicável:

- default;
- hover;
- pressed;
- focused;
- selected;
- loading;
- disabled;
- error;
- warning;
- success;
- read-only;
- empty;
- offline;
- sync-pending;
- conflict.

Não criar estado apenas porque o framework oferece um pseudo-state.

Criar estado quando ele possui significado para a experiência.

---

## 26. Estados visuais transversais

A direção deve padronizar como estados recorrentes aparecem.

| Estado | Direção esperada |
| --- | --- |
| loading | preservar geometria e contexto quando possível |
| vazio | explicar situação e oferecer próximo passo real |
| offline | mostrar o que continua disponível |
| sync pendente | comunicar pendência sem transformar em erro quando os dados estão seguros |
| conflito | comparar e permitir resolução consciente |
| erro externo | identificar impacto e fonte quando isso ajudar a recuperação |
| permissão | explicar finalidade e alternativa |
| revogação | mostrar o que deixou de estar disponível e o que permanece |
| feature desligada | remover órfãos ou comunicar indisponibilidade de forma coerente |
| dado incerto | apresentar fonte, condição e possibilidade de correção |
| destrutivo | mostrar alvo, consequência e confirmação proporcional |

A Direção de UI define o vocabulário visual.

A Especificação de UX detalha comportamento e recuperação.

---

## 27. Anatomia de telas-chave

A Direção de UI deve especificar as telas mais importantes no nível de anatomia visual.

Template recomendado:

```text
TELA / SUPERFÍCIE

OBJETIVO
<qual decisão a superfície suporta>

HIERARQUIA
<ordem visual dos blocos>

AÇÃO DOMINANTE
<ação de maior peso>

ESTADOS VISUAIS OBRIGATÓRIOS
<estados que precisam possuir representação>

NOTAS VISUAIS
<regras que protegem identidade, clareza e acessibilidade>
```

Isso não substitui wireflow.

---

## 28. Inventário de telas

O documento deve conter um inventário por domínio.

Exemplo:

| Domínio | Telas / variações |
| --- | --- |
| Conta | acesso, recuperação, perfil |
| Core | lista, detalhe, edição, execução |
| Progresso | resumo, histórico, comparação |
| Administração | dashboard, lista, detalhe, auditoria |

Inventário não significa liberar tudo ao mesmo tempo.

Prioridade, ondas e feature flags continuam vindo da Visão de Product Owner.

---

## 29. Acessibilidade visual e de interação

A Direção de UI deve especificar critérios verificáveis.

Quando aplicável:

- contraste mínimo;
- tamanho de alvo;
- texto ampliado;
- zoom;
- leitor de tela;
- ordem de foco;
- navegação por teclado;
- cor acompanhada por texto, forma ou ícone;
- redução de movimento;
- safe areas;
- gráficos com resumo textual;
- unidades preservadas;
- labels persistentes;
- estados de erro específicos.

Os critérios devem respeitar o ambiente real do produto e as normas aplicáveis.

A UI não deve depender de uma auditoria tardia para descobrir que seu próprio sistema visual é inacessível.

---

## 30. Microcopy e conteúdo visual

A Direção de UI pode definir:

- tom visual do conteúdo;
- comprimento esperado;
- hierarquia de labels;
- comportamento de títulos;
- uso de unidades;
- representação de incerteza;
- linguagem proibida por identidade ou segurança;
- slots de conteúdo dos componentes.

A redação contextual completa e mensagens de fluxo pertencem principalmente à Especificação de UX.

Se uma frase for vinculante por produto, jurídico ou segurança, sua origem deve ser rastreada.

---

## 31. Design System e IA

Quando a implementação futura for assistida por IA, esta etapa deve reduzir espaço para invenção visual local.

O contrato conceitual deve orientar que, posteriormente:

- valores visuais sejam consumidos via tokens;
- screens componham componentes existentes;
- componente novo exija necessidade real;
- estados sejam reutilizados;
- mudança em foundation tenha impacto rastreável;
- testes cubram estados e acessibilidade;
- snapshot não substitua verificação de interação e legibilidade.

A Direção de UI não escolhe a ferramenta que implementará esses contratos.

---

## 32. Decisões visuais estáveis e IDs

Para rastreabilidade, decisões importantes podem usar IDs estáveis.

Taxonomia recomendada:

```text
UI-DEC-xxx   decisão visual
UI-TOK-xxx   token ou grupo de tokens
UI-CMP-xxx   componente
UI-PAT-xxx   pattern
UI-SCR-xxx   anatomia de tela
UI-GATE-xxx  gate visual
```

Não é obrigatório usar todos os prefixos.

O importante é permitir que UX, Engenharia, QA e backlog apontem para a decisão de origem.

IDs aposentados não devem ser reutilizados para outra decisão.

---

## 33. Evidências de UI

Antes da canonização, a direção deve possuir evidência suficiente para justificar escolhas materiais.

Pode incluir:

- comparação com telas existentes;
- referências externas;
- amostras de paleta;
- estudo de contraste;
- tipografia;
- composição de componentes;
- wireframes visuais de baixa ou alta fidelidade;
- protótipos estáticos;
- comparação entre form factors;
- screenshots de antes/depois;
- análise de densidade;
- teste visual com texto ampliado.

Referência não substitui justificativa.

---

## 34. Processo recomendado da etapa

```text
CONSUMIR DOCUMENTOS ANTERIORES
        ↓
RECUPERAR IDENTIDADE / ASSETS / LEGADO
        ↓
ENTREVISTAR SOBRE LACUNAS VISUAIS
        ↓
DEFINIR TESE VISUAL
        ↓
DEFINIR PERSONALIDADE
        ↓
AUDITAR REFERÊNCIAS E TELAS EXISTENTES
        ↓
DEFINIR HIERARQUIA E FORM FACTORS
        ↓
DEFINIR FOUNDATION
        ↓
DEFINIR COMPONENTES
        ↓
DEFINIR ESTADOS
        ↓
DEFINIR ANATOMIA DAS TELAS-CHAVE
        ↓
VALIDAR ACESSIBILIDADE
        ↓
CRIAR INVENTÁRIO
        ↓
RASTREAR PARA PO / PRINCÍPIOS
        ↓
REVISÃO HUMANA
        ↓
CANONIZAÇÃO
```

---

## 35. Revisão humana

A etapa não deve terminar com um documento unilateral da IA.

O ChatGPT deve apresentar ao humano, preferencialmente por blocos:

1. tese visual e personalidade;
2. referências e auditoria do legado;
3. hierarquia e estratégia por form factor;
4. foundation;
5. componentes e padrões;
6. anatomia das telas-chave;
7. acessibilidade e estados;
8. inventário e gates.

O humano pode corrigir, rejeitar ou pedir alternativas.

Somente depois da aprovação:

```text
“Pode gerar o 04_Direcao_de_UI_e_Design_System.md.”
```

é que o artefato do projeto deve ser canonizado.

---

## 36. Quality Gate da Direção de UI

Antes de propor canonização, verificar:

- documentos 00–03 foram respeitados;
- `Principios_de_UX_UI.md` foi consumido;
- nenhuma prioridade de produto foi reinventada;
- nenhuma regra de negócio nova foi escondida em decisão visual;
- existe tese visual compreensível;
- personalidade visual possui consequências concretas;
- referências externas foram traduzidas, não copiadas;
- telas existentes foram auditadas quando aplicável;
- hierarquia visual está explícita;
- form factors possuem estratégia clara;
- tokens possuem papel semântico;
- tipografia está definida;
- spacing, radius, borda e elevação não têm lacunas críticas;
- componentes principais possuem estados;
- dados numéricos têm unidade e contexto quando necessários;
- estados transversais estão representados;
- acessibilidade faz parte do sistema;
- telas-chave possuem anatomia suficiente;
- inventário de telas existe;
- nenhuma biblioteca, framework ou provider foi canonizado indevidamente;
- a Especificação de UX pode começar sem redefinir identidade visual.

---

## 37. Gates de UI

Um conjunto genérico de gates pode ser:

| Gate | Evidência |
| --- | --- |
| UI-GATE-01 Hierarquia | core e ações dominantes aparecem corretamente |
| UI-GATE-02 Tokens | foundation sem lacunas materiais |
| UI-GATE-03 Componentes | variantes, estados e acessibilidade definidos |
| UI-GATE-04 Telas-chave | anatomia principal aprovada |
| UI-GATE-05 Dados | unidade, contexto, tendência e incerteza coerentes |
| UI-GATE-06 Estados | loading, vazio, erro, offline, conflito e permissões cobertos quando aplicáveis |
| UI-GATE-07 Acessibilidade | contraste, texto ampliado, foco, toque e movimento avaliados |
| UI-GATE-08 Form factors | composição apropriada para cada plataforma do horizonte |
| UI-GATE-09 Rastreabilidade | telas e componentes apontam para decisões de produto |

Projetos menores podem consolidar gates.

Projetos de maior risco podem adicionar gates específicos de domínio.

---

## 38. Handoff para a Especificação de UX

A próxima etapa deve receber:

```text
TESE VISUAL
PERSONALIDADE
HIERARQUIA
ESTRATÉGIA POR FORM FACTOR
TOKENS
TIPOGRAFIA
GRID / SPACING / SUPERFÍCIES
ICONOGRAFIA
MOVIMENTO
COMPONENTES
PATTERNS
ESTADOS TRANSVERSAIS
ANATOMIA DAS TELAS-CHAVE
INVENTÁRIO
ACESSIBILIDADE
GATES
RASTREABILIDADE
```

A Especificação de UX não deve redefinir silenciosamente esses elementos.

Se a análise detalhada de jornada revelar um conflito real, ela deve abrir reconciliação.

Fluxo:

```text
04_Direcao_de_UI_e_Design_System.md
        ↓
05_Especificacao_de_UX.md
```

---

## 39. Anti-padrões

### Design System como paleta

Criar cores e tipografia sem hierarquia, estados ou componentes.

### Copiar concorrente

Reproduzir visual porque a referência “parece boa”.

### Mobile esticado

Transformar a UI de telefone em desktop apenas aumentando largura.

### Card para tudo

Encapsular cada item em superfície elevada sem necessidade semântica.

### Cor para tudo

Usar a cor de ação como decoração em múltiplos elementos concorrentes.

### UI vira UX

Descrever fluxos completos e exceções nesta etapa, eliminando responsabilidade da Especificação de UX.

### UI vira Tech Lead

Escolher pacote, framework ou biblioteca de implementação.

### Componentes sem estados

Documentar apenas o estado ideal.

### Acessibilidade tardia

Criar visual e deixar contraste, foco e texto ampliado para QA final.

### Inventar conteúdo para preencher tela

Criar cards, gráficos, avatares ou métricas fictícias porque a composição parece vazia.

### Design System sem rastreabilidade

Criar padrões que contradizem regras e prioridades de produto.

---

## 40. Gate para avançar

A etapa pode ser considerada concluída quando:

- a proposta visual foi apresentada ao humano;
- divergências com produto foram reconciliadas;
- a tese visual foi aprovada;
- foundation está suficientemente definida;
- componentes e estados principais estão cobertos;
- form factors do horizonte foram tratados;
- telas-chave possuem anatomia visual;
- acessibilidade está integrada;
- inventário foi registrado;
- os gates foram compreendidos;
- o humano aprovou o conteúdo;
- o humano autorizou a canonização;
- `04_Direcao_de_UI_e_Design_System.md` foi criado ou atualizado no destino definido;
- a Especificação de UX consegue avançar sem reinventar a identidade.

Somente então a próxima etapa é elegível:

```text
05 — Especificação de UX
```

---

## 41. Regra final da etapa

> **A Direção de UI e Design System existe para transformar identidade, prioridade e princípios de experiência em uma linguagem visual reutilizável e verificável. Ela decide como o produto se expressa visualmente, mas não usa essa autoridade para inventar produto, substituir UX detalhado ou escolher a tecnologia que implementará o sistema.**

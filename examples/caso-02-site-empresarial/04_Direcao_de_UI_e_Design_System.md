---
document_id: CASE-02-DOC-04
title: Direção de UI e Design System — Site empresarial para climatização
status: canonical
version: 1.0.0
case_id: CASE-02-SITE-EMPRESARIAL
methodology_stage: direcao-ui-design-system
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
  - Principios_de_UX_UI.md
next_document: 05_Especificacao_de_UX.md
ui_direction_readiness: SUFFICIENT
ready_for_codex: false
---

# Direção de UI e Design System — Site empresarial para climatização

## 1. Propósito

Este documento transforma o produto, os princípios de experiência e as decisões de marca já aprovadas do Caso 02 em uma linguagem visual vinculante e reutilizável.

Ele define tese visual, personalidade, hierarquia, cor, tipografia, fotografia, espaçamento, componentes conceituais, anatomia das superfícies-chave, estados visuais e critérios de acessibilidade.

Ele não define ainda wireflows completos, ordem final de transições, CMS, framework, biblioteca, hosting, analytics, provider ou implementação do Design System.

A pergunta central é:

> **Como a NorteSul deve parecer e organizar informação para transmitir competência, proximidade e confiança, priorizando serviço, prova e próximo passo sem parecer template genérico, software empresarial ou peça institucional burocrática?**

---

## 2. Base canônica e Scope Freeze

A base consumida preserva o core:

```text
DESCOBERTA
+
SERVIÇOS
+
REGIÃO
+
CONFIANÇA / PROVA
+
B2C + B2B
+
CONTATO
+
AUTONOMIA EDITORIAL
+
MENSURAÇÃO
+
PRIVACIDADE
+
MOBILE
```

Continuam fora:

```text
CRM
ERP
ORDEM DE SERVIÇO
E-COMMERCE
PORTAL DO CLIENTE
PAGAMENTO
APP NATIVO
CHATBOT DE IA
AGENDAMENTO COMPLEXO
REBRANDING COMPLETO
CMS PRÓPRIO DESENVOLVIDO DO ZERO
```

---

## 3. Entrevista visual simulada

Como o caso é fictício, as decisões desta seção são registradas como decisões simuladas de stakeholder para validar a metodologia.

### 3.1. Herança de marca

O proprietário informa que a marca existente utiliza predominantemente azul escuro e um azul mais claro próximo de turquesa.

O objetivo não é redesenhar a marca, mas melhorar sua aplicação digital.

### 3.2. Aparências a evitar

O cliente rejeita explicitamente:

- estética genérica de assistência técnica;
- excesso de azul usado como revestimento;
- flocos de neve e símbolos de climatização usados como decoração gratuita;
- stock photography como linguagem dominante;
- aparência de empresa de tecnologia/SaaS;
- efeitos excessivos;
- hero genérico com técnico sorrindo para a câmera;
- composição institucional burocrática.

### 3.3. Preferências operacionais

O comercial valoriza prova por trabalho real.

O administrativo precisa de padrões de case sustentáveis, que possam ser alimentados continuamente sem depender de uma produção editorial complexa.

---

# 4. Tese visual

> **A NorteSul deve parecer uma empresa técnica, confiável e próxima. Superfícies claras e muito espaço mantêm leitura simples; azul profundo ancora identidade e competência; o turquesa concentra ação e energia; fotografia real demonstra capacidade. O serviço e sua prova dominam a hierarquia, enquanto a história institucional aparece como sustentação, nunca como protagonista automática.**

Consequências:

```text
CLAREZA
antes de ornamentação

SERVIÇO
antes de institucional

PROVA REAL
antes de adjetivo

FOTOGRAFIA
antes de ilustração genérica

COR DE AÇÃO
concentrada

MOVIMENTO
contido

MOBILE
primeira classe
```

---

# 5. Personalidade visual

| Eixo | Expressar | Evitar |
| --- | --- | --- |
| Técnico | precisão, alinhamento, informação clara | software industrial frio |
| Confiável | consistência, prova, informação verdadeira | slogans exagerados |
| Humano | pessoas e contexto real quando autorizados | stock artificial |
| Local | atuação e projetos concretos | estética de corporação global fictícia |
| Atual | tipografia limpa, composição generosa | visual de assistência técnica legado |
| Comercial | próximo passo reconhecível | pressão excessiva por CTA |

Não são direcionadores:

```text
luxuoso
futurista
disruptivo
gamer
startup
```

---

# 6. Decisão perceptiva central

## UI-DEC-001 — Empresa de serviço real, não template de marketing

> **A percepção dominante precisa ser de empresa que executa trabalho técnico real, e não de template comprado que recebeu um logo.**

Isso governa fotografia, ritmo, componentes, quantidade de efeitos e tom visual.

---

# 7. Hierarquia visual por contexto

## 7.1. Visitante residencial

```text
NECESSIDADE / SERVIÇO
↓
ADERÊNCIA
↓
REGIÃO
↓
PROVA
↓
CONTATO
↓
DETALHE
↓
INSTITUCIONAL
```

## 7.2. Comprador empresarial

```text
CAPACIDADE EMPRESARIAL
↓
SERVIÇO / CONTEXTO
↓
PROVA
↓
CONFIANÇA
↓
CONTATO / PROPOSTA
↓
DETALHE
```

A densidade e a profundidade podem mudar, mas a identidade permanece a mesma.

---

# 8. Sistema de cores

Paleta inicial canônica da simulação:

| Token | Valor inicial | Função |
| --- | ---: | --- |
| `color.brand.primary` | `#0E2A47` | identidade / autoridade |
| `color.action.primary` | `#0B7285` | ação dominante |
| `color.action.hover` | `#0B5E6D` | hover/pressed equivalente |
| `color.text.primary` | `#17202A` | texto principal |
| `color.text.secondary` | `#596775` | conteúdo secundário |
| `color.surface.canvas` | `#F7FAFC` | fundo principal |
| `color.surface.default` | `#FFFFFF` | superfície |
| `color.surface.subtle` | `#EAF3F5` | agrupamento suave |
| `color.border.default` | `#D5DEE5` | divisão |
| `color.feedback.success` | `#16724A` | sucesso |
| `color.feedback.warning` | `#9A5B00` | atenção |
| `color.feedback.danger` | `#B42318` | erro |
| `color.feedback.info` | `#175CD3` | informação |

O valor de ação proposto possui contraste adequado contra branco para uso textual normal em condições apropriadas, mas a conformidade final depende do componente real, tamanho, estado, foco e contexto.

---

# 9. Regra de uso da cor

```text
AZUL PROFUNDO
= marca / estrutura / autoridade

TURQUESA
= ação / seleção / energia

NEUTROS
= leitura e estrutura

FEEDBACK
= estado semântico
```

Não usar cor de marca como revestimento indiscriminado.

Se tudo é azul/turquesa, a hierarquia perde sentido.

---

# 10. WhatsApp e identidade

O WhatsApp é canal importante, mas não define a paleta da NorteSul.

A interface pode usar o texto explícito:

> Falar pelo WhatsApp

sem transformar verde da plataforma em cor estrutural do site.

Qualquer uso de marca externa deve preservar regras da marca correspondente.

---

# 11. Tema

```text
P0
LIGHT ONLY
```

Dark mode não possui necessidade comprovada e não será criado por completude.

---

# 12. Tipografia

Família visual proposta:

**Inter**

Motivos:

- alta legibilidade;
- boa leitura mobile;
- números claros;
- hierarquia previsível;
- baixo ruído estilístico;
- permite que fotografia e conteúdo carreguem personalidade.

Escala conceitual:

| Papel | Desktop aproximado | Mobile aproximado |
| --- | ---: | ---: |
| Display | 48–56 | 36–40 |
| H1 | 40–48 | 32–36 |
| H2 | 30–36 | 26–30 |
| H3 | 22–24 | 20–22 |
| Body large | 18–20 | 18 |
| Body | 16–18 | 16 |
| Small | 14 | 14 |
| Meta | 12–13 | 12–13 |

A implementação ou fonte de carregamento não é decidida aqui.

---

# 13. Semântica e aparência tipográfica

Hierarquia visual e hierarquia semântica precisam ser coerentes, mas não acopladas de maneira ingênua.

Um estilo visual de título não autoriza quebrar a estrutura semântica do documento.

---

# 14. Espaçamento

Unidade-base:

```text
4 px
```

Escala conceitual:

```text
space.1  = 4
space.2  = 8
space.3  = 12
space.4  = 16
space.6  = 24
space.8  = 32
space.10 = 40
space.12 = 48
space.16 = 64
space.20 = 80
space.24 = 96
```

Páginas públicas podem usar espaçamento maior que a superfície editorial/admin.

---

# 15. Grid e largura

Direção:

```text
DESKTOP
12 colunas

TABLET
8 colunas

MOBILE
4 colunas
```

Largura máxima visual aproximada:

```text
1200–1280 px
```

Texto corrido deve permanecer em largura de leitura confortável, evitando linhas excessivamente longas.

---

# 16. Radius, borda e elevação

```text
radius.sm = 6
radius.md = 10
radius.lg = 16
```

Borda padrão conceitual:

```text
1 px
```

Hierarquia preferida:

```text
ESPAÇAMENTO
↓
TIPOGRAFIA
↓
CONTRASTE
↓
AGRUPAMENTO
↓
BORDA
↓
SOMBRA, quando realmente necessária
```

Grandes sombras não fazem parte da identidade.

---

# 17. Fotografia como sistema de prova

> **Trabalho real tem precedência sobre fotografia genérica.**

Categorias desejadas:

- instalação concluída;
- detalhe técnico relevante;
- ambiente atendido;
- processo de trabalho;
- equipe quando autorizada;
- contexto empresarial;
- antes/depois somente quando honesto, útil e autorizado.

A fotografia deve demonstrar capacidade e contexto.

---

# 18. Governança de fotografia

Uma foto de case não pode expor indevidamente:

- rosto sem autorização;
- endereço residencial;
- placa;
- documento;
- informação interna do cliente;
- número de série sensível;
- tela de sistema;
- identidade de empresa quando não autorizada.

Logo:

```text
FOTO DE CASE
=
ATIVO EDITORIAL
+
ATIVO DE PRIVACIDADE
```

---

# 19. Tratamento de imagem

Direção:

```text
cor natural
contraste moderado
sem filtros pesados
sem azul artificial
sem “efeito tecnológico”
```

A consistência vem de enquadramento, seleção e edição, não de filtro agressivo.

O sistema visual precisa funcionar mesmo quando não houver fotografia hero de alta qualidade.

---

# 20. Iconografia

Linguagem desejada:

```text
linear
simples
geometria limpa
traço consistente
```

Ícone precisa ter função.

Evitar decoração repetitiva com flocos de neve, termômetros, engrenagens, raios e ferramentas apenas para sinalizar climatização.

Nenhum pacote concreto é escolhido nesta etapa.

---

# 21. Movimento

Vocabulário:

```text
MICROINTERAÇÃO
curta

ENTRADA DE CONTEÚDO
discreta

HOVER
informativo

TRANSIÇÃO
preserva orientação
```

Não fazem parte da direção:

- scroll-jacking;
- parallax pesado;
- vídeo obrigatório em hero;
- cursor customizado;
- animação permanente;
- objetos flutuantes ornamentais.

Performance e compreensão têm precedência sobre espetáculo.

---

# 22. Arquitetura visual da navegação

Famílias conceituais reconhecíveis:

```text
Serviços
Empresas
Trabalhos
Região
Sobre
Contato
```

Os rótulos finais e URLs permanecem para UX/arquitetura de informação.

### Desktop

```text
LOGO
+
NAVEGAÇÃO
+
UMA AÇÃO DE CONTATO DE MAIOR ÊNFASE
```

### Mobile

```text
LOGO
+
CONTROLE DE NAVEGAÇÃO
+
ACESSO CLARO AO CONTATO
```

Não reproduzir simplesmente a navegação desktop comprimida.

---

# 23. Política de CTA

> **Não haverá múltiplos CTAs persistentes concorrentes.**

Regra:

```text
1 ação primária clara
+
ações contextuais secundárias
```

No desktop, não existe justificativa inicial para manter simultaneamente CTA primário no header, CTA flutuante e vários CTAs equivalentes na mesma viewport.

No mobile, ação persistente única pode existir somente quando UX demonstrar que a ação permanece válida durante a rolagem e não encobre conteúdo, foco ou teclado.

```text
FLOATING WHATSAPP EVERYWHERE
!=
PADRÃO AUTOMÁTICO
```

---

# 24. Botões e links

## Primary

Uso: ação comercial dominante.

## Secondary

Alternativa relevante, menor peso.

## Tertiary

Ação local ou link.

## Destructive

Principalmente em superfícies administrativas quando aplicável.

Links dentro de texto precisam parecer links e possuir estados claros de foco/hover; não depender apenas de diferença mínima de cor.

---

# 25. Política de cards

> **Card não é container padrão para todo conteúdo.**

Cards são adequados principalmente para:

- case;
- serviço resumido;
- prova autônoma;
- entrada editorial.

Seções podem existir sem uma coleção de retângulos.

---

# 26. Camadas conceituais do Design System

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
PAGE TEMPLATES
```

### Foundations

- cor;
- tipografia;
- grid;
- spacing;
- radius;
- movimento;
- fotografia.

### Primitives

- Text;
- Heading;
- Icon;
- Image;
- Surface;
- Divider;
- Stack;
- Inline.

### Components

- Button;
- Link;
- Navigation;
- Breadcrumb;
- Field;
- Textarea;
- Select quando necessário;
- Checkbox quando necessário;
- Alert;
- Accordion;
- Tag;
- Media;
- Dialog quando realmente necessário.

### Domain components

```text
ServiceSummary
ServiceArea
CasePreview
CaseEvidence
BusinessCapability
ContactCTA
QuoteRequest
Testimonial
ReviewSource
RegulatoryNotice
TrustFact
```

### Patterns

```text
ServiceIntro
ProofSection
CaseCollection
BusinessServiceSection
ContactBlock
QuoteRequestPattern
FAQGroup
RegionalContext
```

Os nomes são conceituais, não nomes futuros de arquivos ou componentes.

---

# 27. Home — anatomia visual

A Home precisa suportar visualmente:

```text
ORIENTAÇÃO IMEDIATA
↓
SERVIÇOS PRINCIPAIS
↓
ENTRADA EMPRESARIAL
↓
PROVA / TRABALHOS
↓
REGIÃO
↓
CONFIANÇA
↓
CONTATO
```

A ordem exata ainda pode ser refinada pela UX.

Regra vinculante:

> **Seção institucional longa não domina a abertura.**

---

# 28. Página de serviço residencial — anatomia visual

```text
NOME / NECESSIDADE
↓
RESUMO DE ADERÊNCIA
↓
REGIÃO
↓
PROVA
↓
CONTATO
↓
DETALHES
↓
FAQ RELACIONADA
↓
SERVIÇO / CASE RELACIONADO
```

Não transformar todo serviço em landing page agressiva com CTA em cada bloco.

---

# 29. Página empresarial — anatomia visual

```text
CAPACIDADE EMPRESARIAL
↓
CENÁRIOS ATENDIDOS
↓
SERVIÇOS
↓
PROVA
↓
PMOC / PREVENTIVA / CONTRATOS
↓
CONTEXTO / PROCESSO RELEVANTE
↓
SOLICITAÇÃO DE CONTATO
```

Maior densidade é permitida porque a tarefa possui maior necessidade de contexto.

---

# 30. PMOC — anatomia visual

A interface precisa diferenciar visual e semanticamente:

```text
SERVIÇO OFERECIDO
```

de:

```text
CONTEÚDO EDUCATIVO / REGULATÓRIO
```

Um padrão conceitual `RegulatoryNotice` pode contextualizar afirmações sem transformar tudo em alerta de risco.

---

# 31. Case — anatomia visual

```text
IMAGEM / PROVA PRINCIPAL
↓
CONTEXTO
↓
SERVIÇO EXECUTADO
↓
DETALHES SUFICIENTES
↓
OUTRAS EVIDÊNCIAS
↓
SERVIÇO RELACIONADO
↓
CONTATO
```

O case precisa continuar útil mesmo com conteúdo enxuto e sustentável.

---

# 32. Região atendida

A região possui tratamento próprio e não fica escondida apenas no rodapé.

Pode futuramente ser expressa por texto, lista, agrupamento regional ou mapa quando o mapa realmente ajudar a decisão.

Mapa não é requisito visual automático.

---

# 33. Formulário de contato/proposta

Direção:

```text
FOCO
+
POUCOS CAMPOS
+
LABELS PERSISTENTES
+
ERRO LOCAL
+
PRIVACIDADE PRÓXIMA DA COLETA
+
ALTERNATIVA DE CONTATO
```

Inputs devem ser leves, mas reconhecíveis.

Placeholder não substitui label.

---

# 34. Sucesso e erro de formulário

## Sucesso

```text
CONFIRMAÇÃO CLARA
+
EXPECTATIVA DO PRÓXIMO PASSO
+
AÇÃO SECUNDÁRIA REAL, se houver
```

Evitar celebração desproporcional.

## Erro

```text
campo específico
→ erro próximo do campo

falha global
→ mensagem persistente no contexto

valores válidos
→ preservados
```

Não concentrar erros relevantes em toast efêmero.

---

# 35. Avaliações e prova social

Tratamento visual precisa preservar origem e contexto.

Um componente de avaliação pode possuir:

- texto;
- autor permitido;
- origem;
- contexto;
- data quando relevante.

Não usar cinco estrelas decorativas para depoimento cuja origem não corresponda a uma plataforma de avaliação.

---

# 36. Administração editorial — superfície potencialmente herdada

A Pesquisa recomendou direção híbrida e a plataforma editorial ainda não foi selecionada.

Portanto distinguimos:

```text
SURFACES OWNED BY PROJECT
→ site público e experiências sob controle visual direto

SURFACES POTENTIALLY INHERITED
→ administração fornecida pelo CMS/plataforma
```

A marca NorteSul não precisa ser artificialmente imposta ao painel de um provider.

Para superfícies herdadas, os critérios prioritários passam a ser:

- clareza;
- acessibilidade suficiente;
- segurança;
- papéis e permissões;
- previsibilidade;
- eficiência;
- workflow compatível com o produto.

---

# 37. CASE-02-METHOD-FINDING-002

> **Quando BUILD × BUY × HYBRID leva a uma plataforma gerenciada com superfícies próprias, a Direção de UI precisa distinguir superfícies visualmente controladas pelo produto de superfícies herdadas do provider.**

Contrato derivado:

```text
OWNED SURFACE
→ Design System vinculante

INHERITED SURFACE
→ adequação funcional,
   acessibilidade,
   segurança,
   clareza e operação
```

Este finding permanece como evidência de caso; não altera sozinho a metodologia canônica nesta etapa.

---

# 38. Estados editoriais

Quando o modelo de plataforma realmente suportar e o produto necessitar, distinguir estados como:

```text
RASCUNHO
EM REVISÃO
PUBLICADO
NÃO PUBLICADO
```

Não criar workflow editorial complexo antes de existir necessidade.

---

# 39. Footer

O rodapé serve a:

- identidade;
- contato;
- região;
- navegação complementar;
- informação jurídica necessária;
- canais externos pertinentes.

Não é depósito de todo conteúdo que não coube em outras superfícies.

---

# 40. Hero e fotografia

O sistema não depende de fotografia hero específica para funcionar.

Boa fotografia real pode ser usada quando existir.

Quando não existir, composição tipográfica e superfícies de marca precisam continuar válidas.

---

# 41. Responsividade

## Desktop

Prioriza:

```text
composição ampla
hierarquia
prova simultânea
leitura confortável
```

## Mobile

Prioriza:

```text
sequência
serviço
região
prova
contato
```

## Tablet

É uma composição intermediária legítima, não breakpoint ignorado.

Prioridade, significado, capacidade, segurança e próximo passo permanecem equivalentes entre form factors.

---

# 42. Estados visuais transversais

| Estado | Direção |
| --- | --- |
| Loading | preservar estrutura quando necessário |
| Imagem carregando | evitar layout shift material |
| Form enviando | progresso claro |
| Form sucesso | confirmação persistente suficiente |
| Form erro | contexto + recuperação |
| Sem cases | não expor estado administrativo no público |
| Conteúdo ausente | composição continua válida |
| Link externo | comportamento previsível |
| Conteúdo regulatório | contexto visual próprio |
| CMS rascunho | dependente da plataforma escolhida |
| Conteúdo publicado | estado inequívoco na superfície editorial controlável |

---

# 43. Acessibilidade visual

A direção assume:

```text
contraste
foco visível
semântica previsível
labels persistentes
touch target adequado
zoom
reflow
texto ampliado
não depender somente de cor
movimento reduzível
links reconhecíveis
alt text com propósito
```

Texto sobre fotografia só é aceitável quando o contraste permanece robusto em diferentes imagens e estados, não apenas no mock escolhido.

---

# 44. Performance como restrição visual

> **A identidade não dependerá de ativos pesados para existir.**

Não são requisitos visuais:

- vídeo 4K autoplay;
- 3D;
- parallax complexo;
- múltiplas fontes sem necessidade;
- vários carrosséis;
- dezenas de imagens acima da dobra.

A tecnologia futura decide otimização; a UI não cria dependência pesada sem justificativa.

---

# 45. SEO como restrição visual

Conteúdo principal não deve depender de efeitos desnecessários para existir.

Evitar esconder todo conteúdo essencial atrás de tabs fechadas, carrosséis ou modais apenas para “limpar” a página.

Revelação progressiva continua permitida quando compatível com a tarefa.

---

# 46. Design System e conteúdo

Neste produto, padrões de conteúdo fazem parte do Design System.

O sistema precisa acomodar:

- título de serviço;
- descrição curta;
- case;
- legenda;
- prova;
- avaliação;
- região;
- FAQ;
- aviso regulatório;
- CTA;
- erro;
- sucesso.

Sem governança de conteúdo, o CMS degradará rapidamente a consistência visual.

---

# 47. Conteúdo editorial mínimo sustentável

O padrão de case precisa funcionar com algo como:

```text
título
serviço
local/contexto permitido
1 boa imagem
resumo curto
```

E poder enriquecer progressivamente.

O padrão não pode exigir produção editorial incompatível com a empresa.

---

# 48. Revisão simulada

O proprietário aprova a combinação de azul profundo e turquesa, reforçando que o site não deve ser “todo azul”.

O comercial aprova a ausência de saturação de WhatsApp.

O administrativo confirma que um case com uma boa imagem e explicação curta é sustentável.

O proprietário confirma fotografia real como principal linguagem de prova.

Nenhuma dessas decisões altera o Scope Freeze.

---

# 49. Decisões visuais canônicas

```text
UI-DEC-001
empresa de serviço real,
não template de marketing

UI-DEC-002
azul profundo ancora identidade

UI-DEC-003
turquesa concentra ação

UI-DEC-004
fotografia real é a principal
linguagem de prova

UI-DEC-005
institucional não domina a abertura

UI-DEC-006
não haverá saturação de CTA

UI-DEC-007
cases precisam ser editorialmente sustentáveis

UI-DEC-008
B2C e B2B compartilham identidade,
mas aceitam densidades diferentes

UI-DEC-009
mobile possui composição própria

UI-DEC-010
tema claro é o único compromisso atual

UI-DEC-011
Design System é vinculante
nas superfícies controladas pelo projeto

UI-DEC-012
superfície administrativa herdada
de plataforma será avaliada
por adequação, não por fidelidade visual
```

---

# 50. Gates de UI

```text
UI-GATE-01
serviço domina institucional
quando a tarefa exige

UI-GATE-02
paleta e tokens possuem papéis semânticos claros

UI-GATE-03
fotografia possui padrão sustentável

UI-GATE-04
Home, Serviço, Empresas,
Case e Contato possuem anatomia visual aprovada

UI-GATE-05
CTA possui hierarquia sem saturação

UI-GATE-06
mobile possui composição própria

UI-GATE-07
formulários possuem estados e acessibilidade visual

UI-GATE-08
conteúdo regulatório é visualmente contextualizável

UI-GATE-09
Design System suporta conteúdo editorial real

UI-GATE-10
superfícies provider-owned possuem critérios explícitos

UI-GATE-11
identidade não depende de performance pesada

UI-GATE-12
rastreabilidade com PO e Princípios está preservada
```

---

# 51. Handoff para UX

A Especificação de UX deverá definir, sem reinventar esta direção:

- arquitetura de informação final do ponto de vista do visitante;
- jornadas de entrada por busca, indicação e navegação;
- fluxo de serviço residencial;
- fluxo B2B;
- comportamento do WhatsApp e da saída para terceiro;
- fluxo e campos do contato estruturado;
- estados de formulário;
- comportamento de erro e recuperação;
- jornada editorial mínima;
- estados de publicação quando necessários;
- navegação/retorno;
- deep links e entradas diretas;
- instrumentação semântica;
- testes de clareza, confiança e autonomia editorial.

A UX não poderá mudar silenciosamente a paleta, a personalidade, a hierarquia de CTA ou a política de fotografia.

---

# 52. Validação da metodologia

Os Princípios disseram:

```text
necessidade antes da empresa
+
prova antes de adjetivo
+
conversão sem pressão
```

A Direção de UI materializou isso em:

```text
hierarquia
+
fotografia real
+
cor concentrada
+
CTA disciplinado
+
densidade por contexto
+
anatomia das páginas
+
sistema editorial sustentável
```

Ainda não foram decididos:

- qual clique leva para onde;
- campos finais do formulário;
- ordem exata do fluxo B2B;
- comportamento detalhado de retry;
- workflow físico do CMS;
- URL final de cada página;
- implementação de analytics;
- plataforma editorial;
- framework;
- hosting.

Resultado:

```text
UI_DIRECTION_METHOD_VALIDATION: PASS

PRODUCT_SCOPE_CHANGED: NO
BUSINESS_RULE_CHANGED: NO
DETAILED_UX_FLOW_CREATED: NO
TECH_STACK_SELECTED: NO
CMS_SELECTED: NO
HOSTING_SELECTED: NO

VISUAL_THESIS: DEFINED
PERSONALITY: DEFINED
COLOR_SYSTEM: DEFINED
TYPOGRAPHY: DEFINED
PHOTOGRAPHY_SYSTEM: DEFINED
GRID_AND_SPACING: DEFINED
COMPONENT_MODEL: DEFINED
KEY_PAGE_ANATOMY: DEFINED
FORM_FACTORS: DEFINED
ACCESSIBILITY_DIRECTION: DEFINED
EDITORIAL_VISUAL_MODEL: DEFINED
OWNED_VS_INHERITED_SURFACES: DEFINED

NEW_METHOD_FINDING:
CASE-02-METHOD-FINDING-002

UI_DIRECTION_READINESS: SUFFICIENT
READY_FOR_CODEX: NO
```

---

# 53. Estado de passagem

```text
UI_DIRECTION_EXECUTION: COMPLETE
CLIENT_REVIEW: APPROVED_FOR_SIMULATION
UI_DIRECTION_READINESS: SUFFICIENT
READY_FOR_CODEX: NO
NEXT_STAGE: 05 — Especificação de UX
```

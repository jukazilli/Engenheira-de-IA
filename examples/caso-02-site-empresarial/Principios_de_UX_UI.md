---
document_id: CASE-02-DOC-03A
title: Princípios de UX e UI — Site empresarial para climatização
status: canonical
version: 1.0.0
case_id: CASE-02-SITE-EMPRESARIAL
methodology_stage: principios-ux-ui
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
next_document: 04_Direcao_de_UI_e_Design_System.md
principles_readiness: SUFFICIENT
ready_for_codex: false
---

# Princípios de UX e UI — Site empresarial para climatização

## 1. Propósito

Este documento transforma a intenção de produto, o contexto de uso, os outcomes, os riscos e as regras aprovadas do Caso 02 em uma constituição transversal para decisões de interface.

Ele não define ainda o sistema visual final, wireflows, CMS, arquitetura, framework, hosting ou tecnologia.

A pergunta central é:

> **Quais princípios precisam orientar toda decisão de experiência para que a presença web da NorteSul ajude pessoas a entender, confiar e contatar sem transformar o site em brochura institucional, máquina de pressão comercial ou estrutura editorial impossível de manter?**

---

## 2. Base canônica consumida

Este documento consome:

```text
00_Discovery.md
01_Pesquisa_e_Viabilidade.md
02_Briefing_de_Produto_e_Escopo.md
03_Visao_de_Product_Owner.md
```

O Product Scope Freeze permanece:

```text
CORE =
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

Continuam fora do horizonte atual:

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

## 3. A ameaça central de UX

O principal risco de experiência neste tipo de produto é transformar o site em inventário de tudo que a empresa deseja comunicar:

```text
empresa quer mostrar tudo
↓
Home recebe tudo
↓
história
missão
valores
serviços
logos
fotos
depoimentos
FAQ
mapa
formulário
Instagram
certificações
conteúdo
...
↓
visitante não encontra
sua necessidade
```

A regra-mãe do Caso 02 é:

> **A interface deve ajudar o visitante a reduzir incerteza sobre necessidade, atendimento, confiança e próximo passo antes de tentar apresentar toda a empresa.**

---

## 4. Tarefas mentais principais

### U1 — Visitante residencial / necessidade imediata

```text
isso resolve meu problema?
↓
vocês atendem onde estou?
↓
posso confiar?
↓
como falo com vocês?
```

### U2 — Comprador empresarial

```text
vocês atendem empresas como a minha?
↓
têm capacidade?
↓
fazem o serviço necessário?
↓
existem provas?
↓
como solicito conversa/proposta?
```

### U3 — Administrativo / marketing

```text
o que mudou?
↓
onde atualizo?
↓
o que será publicado?
↓
está correto?
```

### U4/U5 — Comercial / proprietário

```text
o site está trazendo contatos?
↓
esses contatos são úteis?
↓
o que precisamos melhorar?
```

Essas tarefas não devem ser comprimidas em uma única superfície ou tratadas com a mesma densidade.

---

# 5. Aplicação dos princípios canônicos

## P1 — Começar pelo problema e pela próxima decisão

A primeira pergunta da experiência pública não é:

> “O que queremos contar sobre a empresa?”

É:

> “O que esta pessoa precisa reconhecer para tomar a próxima decisão?”

Em uma página de manutenção, por exemplo:

```text
necessidade
↓
serviço
↓
região
↓
prova suficiente
↓
contato
```

Informação institucional entra na medida em que reduz incerteza ou aumenta confiança.

---

## P2 — Uma ação dominante por estado

Quando existir uma ação principal clara, ela deve ser visualmente reconhecível.

Em contexto residencial, a ação dominante tende a ser iniciar contato rápido.

Em contexto empresarial, pode ser solicitar conversa ou proposta.

Isso não significa um único botão na tela; significa que WhatsApp, formulário, telefone, Instagram, mapa e menu não devem competir com o mesmo peso visual.

---

## P3 — Contexto real de uso primeiro

O site será frequentemente acessado:

- por celular;
- vindo do Google;
- após uma indicação;
- com pressa;
- durante um problema com equipamento;
- em rede móvel;
- com atenção parcial;
- sem conhecimento técnico;
- sem passar pela Home.

Portanto:

```text
entrada pela Home
NÃO É GARANTIDA

entrada por página de serviço
É NORMAL

entrada por case
É POSSÍVEL

entrada por busca
É CENTRAL
```

Toda página pública material precisa fornecer contexto suficiente para que a pessoa reconheça onde está, o que a empresa oferece e qual é o próximo passo.

---

## P4 — Complexidade fica no sistema

A empresa pode possuir classificações técnicas, procedimentos, normas, tipos de equipamento, marcas, escopos empresariais e regras comerciais complexas.

A pessoa não precisa compreender toda essa estrutura para decidir se vale iniciar contato.

Aplicar revelação progressiva.

No residencial, linguagem reconhecível como “Manutenção de ar-condicionado” pode ser mais útil que a taxonomia interna completa.

Em PMOC, maior profundidade pode ser necessária, mas ainda deve ser organizada por decisão e não por estrutura técnica interna.

---

## P5 — Menor interrupção suficiente

Escolher a menor superfície suficiente para a tarefa e o risco.

Exemplos conceituais:

```text
dúvida curta
→ resposta local / expansão

foto adicional
→ detalhe contextual

contato rápido
→ ação direta

solicitação empresarial mais extensa
→ tarefa focada própria

informação jurídica relevante
→ tratamento persistente e proporcional
```

Evitar modal para toda informação ou fluxo longo para ação simples.

---

## P6 — Mudou a tarefa mental, mudou a superfície

Entender um serviço e fornecer contexto detalhado para uma proposta são tarefas diferentes.

```text
PÁGINA DE SERVIÇO
objetivo: compreender aderência

↓ mudança real de tarefa

SOLICITAÇÃO EMPRESARIAL
objetivo: fornecer contexto para contato
```

Uma experiência dedicada pode ser apropriada quando existe começo, fim, vários campos ou retomada própria.

Detalhes curtos do mesmo serviço podem permanecer no contexto atual.

---

## P7 — Estado e confiança são visíveis

O site precisa comunicar estados técnicos e editoriais verdadeiros.

Exemplos:

```text
ENVIANDO
≠
ENVIADO
```

```text
AVALIAÇÃO EXTERNA
≠
DEPOIMENTO PRODUZIDO PELA EMPRESA
```

```text
INFORMAÇÃO REGULATÓRIA
≠
PROMESSA COMERCIAL
```

Case, avaliação, região, formulário, publicação e conteúdo sensível devem preservar contexto suficiente para gerar confiança adequada.

---

## P8 — Prevenir e recuperar antes de culpar

Formulários precisam validar perto do ponto de decisão, preservar valores válidos em falhas recuperáveis e explicar o próximo passo.

Preferir:

> “Informe um telefone com DDD.”

Evitar:

> “Você preencheu incorretamente.”

Se o envio falhar e o conteúdo for preservado, informar isso.

WhatsApp ou outro canal aprovado pode permanecer disponível como alternativa quando fizer sentido.

---

## P9 — Acessibilidade integra a decisão

Como o site é público, acessibilidade participa desde o início de:

- contraste;
- teclado;
- foco;
- semântica de headings;
- links compreensíveis;
- alt text pertinente;
- zoom e reflow;
- texto ampliado;
- alvos de toque;
- labels de formulário;
- mensagens de erro associadas;
- redução de movimento;
- estados não dependentes apenas de cor.

Imagem visualmente atraente não substitui conteúdo acessível.

Cases precisam possuir contexto textual suficiente quando a imagem comunica informação material.

---

## P10 — Consistência vem de comportamento compartilhado

Páginas de serviço podem possuir composições diferentes, mas intenções equivalentes precisam preservar semântica compatível.

Elementos como serviço, região, prova e contato devem continuar reconhecíveis.

“Case” deve representar prova de trabalho; não deve significar ora case, ora post, ora promoção.

---

## P11 — Privacidade é padrão

Não coletar ou expor dado pessoal por conveniência.

No primeiro contato, evitar solicitar documentos, dados financeiros, endereço completo ou informação extensa quando não forem necessários.

Analytics não deve enviar nome, telefone, e-mail, mensagem livre ou conteúdo integral de formulário como propriedade de evento.

---

## P12 — Identidade própria, aprendizado externo

Concorrentes, galerias de design e plataformas podem ensinar hierarquia, ritmo, composição, responsividade e padrões de interação.

Não autorizam copiar marca, mensagem, navegação, CTA, arquitetura da informação ou aparência genérica de determinada plataforma.

A solução final deve pertencer à NorteSul.

---

# 6. Princípios específicos do Caso 02

## SITE-UX-01 — Necessidade antes da empresa

> **O visitante deve reconhecer primeiro se a NorteSul pode resolver sua necessidade; informação institucional entra para sustentar essa decisão.**

“9 anos de história” não deve comprar mais atenção que “Manutenção de ar-condicionado” quando a intenção é operacional.

---

## SITE-UX-02 — Toda entrada pública deve possuir contexto suficiente

> **Nenhuma página material deve depender de a pessoa ter passado pela Home para compreender empresa, serviço, região e próximo passo.**

Esse princípio protege aquisição via busca, indicação e links diretos.

---

## SITE-UX-03 — Prova ocupa o lugar de adjetivo

> **Quando existir evidência real, preferir demonstrar capacidade a descrevê-la com adjetivos genéricos.**

Preferir trabalho executado, contexto e resultado factual permitido a frases como “excelência e qualidade” sem sustentação.

---

## SITE-UX-04 — Conversão não deve sequestrar a leitura

> **Contato deve ser fácil de encontrar sem transformar toda interação em pressão comercial.**

Popup imediato, barra fixa, chat, botão flutuante, formulário e múltiplos CTAs competindo simultaneamente não representam boa conversão.

---

## SITE-UX-05 — B2C pede velocidade; B2B pede confiança progressiva

B2C e B2B pertencem à mesma identidade, mas possuem profundidades diferentes de decisão.

```text
B2C
serviço → região → prova → contato

B2B
capacidade → contexto → prova → serviço → proposta
```

A UX detalhada poderá refinar a ordem, preservando a diferença mental.

---

## SITE-UX-06 — SEO não pode deformar a experiência humana

> **Conteúdo criado para descoberta só permanece válido quando também possui valor real para a pessoa que chega à página.**

Não repetir termos de busca artificialmente nem criar páginas locais vazias apenas para capturar consultas.

---

## SITE-UX-07 — Conteúdo precisa parecer mantível

> **A experiência editorial publicada precisa ser compatível com a capacidade real de manutenção da empresa.**

Um novo case não deve exigir direção de arte exclusiva, dez imagens, vídeo e texto longo se essa carga inviabiliza atualização recorrente.

---

## SITE-UX-08 — Contato mede intenção; não define valor sozinho

Clique em WhatsApp ou envio de formulário não é automaticamente lead qualificado, orçamento ou venda.

A experiência não deve pressionar artificialmente apenas para aumentar uma métrica de clique.

---

## SITE-UX-09 — Informação local deve ser inequívoca

Quando a região influencia a decisão, o visitante deve conseguir entender se:

```text
ATENDE
NÃO ATENDE
PRECISA CONFIRMAR
```

Região relevante não deve ficar escondida apenas em FAQ ou rodapé.

---

## SITE-UX-10 — Confiança digital exige coerência

Nome, telefone, região, serviços, identidade e provas não devem aparentar versões contraditórias entre páginas.

> **Contradição editorial é também falha de UX.**

---

# 7. Densidade por tarefa

A densidade visual não será uniforme.

### Serviço residencial

```text
BAIXA A MODERADA
```

Prioridade: escanear, reconhecer e decidir.

### Empresarial / PMOC

```text
MODERADA
```

Maior quantidade de contexto e prova pode ser necessária.

### Case

```text
VARIÁVEL
```

A quantidade de conteúdo deve servir à prova.

### Administração editorial

```text
MODERADA A EFICIENTE
```

É ferramenta operacional, não peça de marketing.

Regra:

> **A densidade é proporcional à decisão, não ao desejo de preencher a página.**

---

# 8. Hierarquia mental de conteúdo público

Uma página de serviço típica deve conseguir sustentar, conceitualmente:

```text
1. NECESSIDADE / SERVIÇO

2. ADERÊNCIA
   o que fazemos

3. REGIÃO / CONTEXTO

4. PROVA

5. PRÓXIMO PASSO

6. DETALHE ADICIONAL

7. INSTITUCIONAL COMPLEMENTAR
```

Essa sequência não é wireframe nem ordem obrigatória de blocos; é hierarquia de decisão.

---

# 9. Home

A Home possui uma responsabilidade principal:

> **Orientar rapidamente visitantes de intenções diferentes para um contexto útil sem obrigá-los a consumir apresentação institucional extensa.**

A Home não deve virar todas as páginas dentro de uma única página.

Também não deve ser tratada como única entrada válida do site.

---

# 10. Serviços

Cada serviço relevante deve ser compreensível como unidade de decisão.

Contrato conceitual mínimo:

```text
qual problema atende?
para quem?
qual escopo é comunicado?
onde é atendido?
que prova existe?
qual próximo passo?
```

A ordem visual será definida posteriormente.

---

# 11. Cases

Case é componente de confiança, não decoração.

Quando apropriado, precisa responder:

```text
o que foi feito?
em qual contexto?
qual serviço?
o que esta prova demonstra?
```

Fotos sem contexto podem ajudar estética, mas possuem menor valor de decisão.

---

# 12. Avaliações e depoimentos

Avaliação externa, depoimento fornecido e case são evidências distintas.

A origem/contexto precisa ser suficiente para evitar percepção enganosa.

Evitar transformar uma frase sem origem em prova equivalente a uma avaliação pública verificável.

---

# 13. PMOC e conteúdo regulatório

A experiência deve separar semanticamente:

```text
O QUE A NORTE SUL OFERECE
```

de:

```text
INFORMAÇÃO REGULATÓRIA / EDUCATIVA
```

A interface não deve fazer marketing parecer aconselhamento jurídico ou técnico definitivo.

Publicação continua condicionada a revisão adequada quando o claim exigir.

---

# 14. Contato rápido

Contato precisa ser fácil de encontrar, sobretudo no mobile.

A etapa atual não decide se isso será materializado por botão flutuante, CTA no header, barra fixa, CTA inline ou combinação proporcional.

Qualquer ação persistente futura deverá provar que permanece válida ao longo da rolagem, não cobre conteúdo, foco, mensagens de erro ou teclado e não compete com outras ações equivalentes.

---

# 15. Formulário empresarial

Quando o formulário possuir contexto relevante, ele representa tarefa mental própria.

Princípio:

```text
MENOS CAMPOS
+
MAIS RELEVÂNCIA
```

Campos futuros devem ser julgados por:

```text
UTILIDADE NA QUALIFICAÇÃO
×
CUSTO PARA PREENCHER
×
PRIVACIDADE
```

O produto não deve coletar tudo que o comercial “talvez um dia queira”.

---

# 16. Estados do formulário

Estados mínimos conhecidos:

```text
default
preenchimento
erro de campo
enviando
sucesso
falha recuperável
falha bloqueante
```

Sucesso precisa representar envio efetivamente confirmado.

Falha recuperável não deve apagar valores válidos quando a plataforma permitir preservá-los de forma segura.

---

# 17. Administração editorial

A tarefa editorial precisa priorizar:

```text
clareza
eficiência
previsibilidade
revisão
estado de publicação
```

A área administrativa pode ser mais operacional que o site público sem ser tecnicamente hostil.

Se a plataforma escolhida fornecer interface administrativa própria, etapas posteriores precisarão avaliar o quanto dessa experiência pode ser controlado ou aceito.

---

# 18. Estados editoriais

Quando o produto/plataforma justificar, distinguir:

```text
RASCUNHO
EM REVISÃO
PUBLICADO
NÃO PUBLICADO
```

Não criar workflow editorial complexo apenas por completude.

---

# 19. Mobile e desktop

Mobile não é desktop comprimido.

Desktop pode permitir mais simultaneidade.

Mobile pode organizar conteúdo sequencialmente.

O que permanece equivalente:

```text
prioridade
capacidade
segurança
significado
acesso ao próximo passo
```

---

# 20. Navegação

A navegação pública deve refletir necessidades reconhecíveis pelo visitante, não departamentos internos.

Termos como:

```text
Instalação
Manutenção
Empresas
PMOC
```

são conceitualmente mais próximos das tarefas do visitante do que estruturas organizacionais internas, quando corresponderem ao conteúdo real.

A arquitetura final de informação será especificada posteriormente.

---

# 21. Microcopy

Preferir linguagem reconhecível pelo público.

Exemplos adequados conceitualmente:

```text
Solicitar orçamento
Falar pelo WhatsApp
Ver serviços para empresas
Atendemos Joinville e região
```

Evitar jargão interno ou técnico quando não ajuda a decisão:

```text
Submeter solicitação
Abrir ticket
Unidade de negócio B2B
```

---

# 22. Empty states

Na administração, um estado vazio pode dizer:

> “Nenhum case publicado ainda.”

Se a pessoa puder agir, um CTA como “Adicionar primeiro case” pode ser legítimo.

No site público, não expor mensagens administrativas como “nenhum registro cadastrado”.

O comportamento público deve ser apropriado ao visitante.

---

# 23. Erros e recuperação

Uma mensagem de erro precisa explicar, quando pertinente:

- o que aconteceu;
- o que foi preservado;
- o que a pessoa pode fazer;
- qual alternativa existe.

Exemplo conceitual para formulário:

> “Não foi possível enviar agora. Suas informações continuam aqui.”

somente quando isso for verdadeiro.

A experiência não deve expor detalhes de API, provider ou implementação.

---

# 24. Privacidade e analytics

Contato comercial e mensuração são finalidades diferentes.

A pessoa não deve fornecer informação comercial adicional apenas para permitir analytics.

Tracking não essencial não pode tornar navegação, leitura ou contato indisponíveis.

---

# 25. Protocolo mínimo antes de desenhar uma superfície

Toda futura tela/superfície deve registrar:

```text
Origem:
US-xxx / J-xxx / OUT-xxx

Persona:
U1 / U2 / U3 / U4 / U5

Contexto de entrada:
Google / indicação / navegação / editorial / outro

Tarefa mental:
...

Ação dominante:
...

Informação necessária:
...

Prova necessária:
...

Conteúdo que não deve dominar:
...

Estados:
...

Dados pessoais:
sim / não

Claim sensível:
sim / não

Responsividade:
...

Acessibilidade:
...

SEO/indexação:
aplicável / não aplicável

Analytics:
necessário / não necessário

Fora do recorte:
...
```

---

# 26. Definition of Ready de UX/UI

Uma superfície não está pronta para design quando não sabemos:

- persona;
- outcome;
- jornada;
- origem possível da visita;
- tarefa mental;
- ação dominante;
- informação necessária;
- prova necessária;
- indexabilidade esperada;
- estados;
- dados pessoais;
- claim sensível;
- comportamento mobile;
- acessibilidade;
- conteúdo editável;
- evidência de compreensão.

---

# 27. Definition of Done de UX/UI

Quando uma experiência for especificada, só estará pronta quando, conforme aplicável:

```text
tarefa é compreensível
+
ação dominante é reconhecível
+
serviço/região não ficam ambíguos
+
prova possui função clara
+
contato é acessível sem pressão indevida
+
mobile possui composição adequada
+
teclado/foco/semântica funcionam
+
estado não depende apenas de cor
+
erro e recuperação estão definidos
+
dados pessoais são proporcionais
+
conteúdo não viola claims aprovados
+
SEO não deformou a experiência
+
edição é sustentável
+
evidência de validação está prevista
```

`Ready de UX/UI` ainda não significa `Ready for Code`.

---

# 28. Revisão simulada

### Proprietário

> “Eu gostei principalmente da ideia de não fazer o site ficar falando de nós antes de falar do que fazemos.”

Confirma `SITE-UX-01`.

### Comercial

> “Se a pessoa já entra numa página de manutenção pelo Google, ela não pode ter que voltar para a home para descobrir se atendemos Joinville.”

Confirma `SITE-UX-02`.

### Administrativo

> “Para case funcionar, precisa ser simples de publicar. Se cada um exigir um projeto inteiro, vou parar de atualizar.”

Confirma `SITE-UX-07`.

### Proprietário

> “E eu não quero aqueles sites que têm cinco botões de WhatsApp pulando na tela.”

Confirma `SITE-UX-04`.

---

# 29. Validação da metodologia

O Caso 02 demonstra que os princípios canônicos P1–P12 permanecem aplicáveis a um site público orientado a conteúdo e aquisição, mesmo tendo surgido originalmente em contextos fortemente interativos.

A manifestação muda:

```text
APP
estado transacional
retomada
sincronização

SITE
entrada por busca
credibilidade
conteúdo
indexação
conversão
```

A constituição permanece, enquanto princípios específicos acomodam o contexto do produto.

Não foi identificada nova falha metodológica que justifique alterar imediatamente a fonte da etapa.

Resultado:

```text
UX_UI_PRINCIPLES_METHOD_VALIDATION: PASS

PRODUCT_SCOPE_CHANGED: NO
NEW_PRODUCT_MODULE_CREATED: NO
NEW_BUSINESS_RULE_CREATED: NO

VISUAL_SYSTEM_DEFINED: NO
CMS_SELECTED: NO
WIREFLOW_DETAILED: NO
TECH_STACK_SELECTED: NO

CANONICAL_P1_P12: APPLIED
SITE_SPECIFIC_PRINCIPLES: 10
PUBLIC_ENTRY_POSTURE: DEFINED
CONTENT_HIERARCHY_POSTURE: DEFINED
CONVERSION_POSTURE: DEFINED
TRUST_POSTURE: DEFINED
B2C_B2B_POSTURE: DEFINED
EDITORIAL_POSTURE: DEFINED
PRIVACY_POSTURE: DEFINED
ACCESSIBILITY_POSTURE: DEFINED
MOBILE_POSTURE: DEFINED
SEO_UX_BOUNDARY: DEFINED

PRINCIPLES_READINESS: SUFFICIENT
READY_FOR_CODEX: NO
```

---

# 30. Handoff

```text
PRINCIPLES_EXECUTION: COMPLETE
CLIENT_REVIEW: APPROVED_FOR_SIMULATION
PRINCIPLES_READINESS: SUFFICIENT
PRODUCT_SCOPE_CHANGED: NO
READY_FOR_CODEX: NO
NEXT_STAGE: 04 — Direção de UI e Design System
```

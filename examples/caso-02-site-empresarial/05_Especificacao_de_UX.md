---
document_id: CASE-02-DOC-05
title: Especificação de UX — Site empresarial para climatização
status: canonical
version: 1.0.0
case_id: CASE-02-SITE-EMPRESARIAL
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
ready_for_codex: false
---

# Especificação de UX — Site empresarial para climatização

## 1. Propósito

Este documento transforma produto, regras, princípios de experiência e direção visual do Caso 02 em jornadas, fluxos, estados, recuperação, conteúdo operacional, acessibilidade, mensuração semântica e critérios de usabilidade verificáveis.

Ele descreve o comportamento que precisa ser preservado pelas etapas técnicas posteriores sem escolher CMS, framework, analytics, banco, provider ou arquitetura física.

---

## 2. Contrato de experiência

> **O site deve permitir que uma pessoa que chega pela Home, por busca direta, por indicação, por um serviço ou por um case entenda rapidamente se a NorteSul atende sua necessidade, encontre provas suficientes para decidir e alcance o canal de contato adequado sem precisar conhecer previamente a estrutura do site. Quando houver formulário, erro de rede ou saída para serviço externo, a experiência deve deixar claro o que aconteceu, o que foi preservado e qual é o próximo passo.**

Para o usuário editorial:

> **Conteúdo rotineiro aprovado deve poder ser atualizado com segurança, revisão e estado de publicação compreensível, sem exigir alteração de código.**

---

## 3. Arquitetura da experiência pública

A Home não é pré-condição de entendimento.

Entradas públicas válidas incluem:

- Home;
- serviço;
- empresas;
- PMOC;
- case;
- região;
- contato.

Toda página pública relevante deve funcionar como entrada independente e responder, quando aplicável:

```text
quem oferece?
o que é isto?
para quem serve?
onde atende?
por que confiar?
qual o próximo passo?
```

---

## 4. Navegação principal

Destinos conceituais:

```text
SERVIÇOS
EMPRESAS
TRABALHOS
REGIÃO
SOBRE
CONTATO
```

Os rótulos finais poderão ser refinados em validação de compreensão.

O comportamento de Voltar deve respeitar o navegador e o contexto anterior. Não forçar retorno à Home sem necessidade.

---

## 5. UX-JRN-001 — Resolver necessidade residencial

**Relacionada:** J-001, US-001, US-002, US-003, US-007, US-009.

**Contexto:** pessoa chega por busca, indicação, link ou navegação interna.

**Objetivo:** determinar aderência e iniciar contato quando fizer sentido.

```text
ENTRAR
↓
RECONHECER SERVIÇO
↓
CONFIRMAR ADERÊNCIA
↓
CONFIRMAR REGIÃO
↓
VER PROVA SUFICIENTE
↓
CONTATAR
```

A pessoa não precisa consumir História/Sobre antes de chegar ao valor.

---

## 6. Estado de aderência

A experiência deve diferenciar:

```text
SERVIÇO OFERECIDO
SERVIÇO NÃO OFERECIDO
NECESSIDADE AINDA AMBÍGUA
```

A terceira situação não deve virar falsa negativa. Contato pode permanecer como próximo passo quando a empresa precisa avaliar o caso.

---

## 7. UX-STA-001 — Região atendida

Estados conceituais:

```text
REGULARLY_SUPPORTED
NEEDS_CONFIRMATION
NOT_SUPPORTED
```

A UI pública usará linguagem natural equivalente.

Exemplo:

> Atendemos Joinville e esta região regularmente.

ou:

> Não encontrou sua cidade? Fale conosco para confirmar disponibilidade.

Nunca afirmar cobertura não confirmada.

---

## 8. Entrada direta por busca

Quem entra diretamente em uma página de serviço precisa encontrar contexto suficiente sem passar pela Home.

Isso materializa `SITE-UX-02`.

---

## 9. UX-JRN-002 — Avaliar fornecedor empresarial

**Relacionada:** J-002, US-010, US-011, US-012.

```text
ENTRADA
↓
RECONHECER CAPACIDADE B2B
↓
COMPREENDER SERVIÇOS
↓
AVALIAR PROVAS
↓
APROFUNDAR CONTEXTO
↓
ESCOLHER CONTATO
├─ WHATSAPP
└─ SOLICITAÇÃO ESTRUTURADA
```

O caminho B2B admite maior densidade e profundidade sem impor essa mesma carga ao residencial.

---

## 10. PMOC

A jornada deve distinguir claramente:

```text
SERVIÇO OFERECIDO PELA NORTESUL
```

versus

```text
INFORMAÇÃO EDUCACIONAL / REGULATÓRIA
```

O conteúdo geral não pode ser apresentado como garantia jurídica ou análise específica.

---

## 11. UX-JRN-003 — Validar indicação

**Relacionada:** J-003.

```text
RECEBE INDICAÇÃO
↓
PESQUISA NORTESUL
↓
CHEGA AO SITE
↓
CONFIRMA IDENTIDADE
↓
ENTENDE SERVIÇOS / REGIÃO
↓
AVALIA PROVA
↓
CONTATA
```

Neste contexto, Sobre, avaliações e cases podem ter peso maior que em uma demanda urgente.

---

## 12. UX-JRN-004 — Explorar trabalho realizado

**Relacionada:** J-004, US-005, US-014.

```text
CASE
↓
O QUE FOI FEITO
↓
EM QUAL CONTEXTO
↓
QUAL SERVIÇO ISSO PROVA
↓
SERVIÇO RELACIONADO
↓
CONTATO, quando pertinente
```

Case não é destino decorativo; participa da decisão.

---

## 13. Entrada direta por case

Um case acessado diretamente precisa preservar identidade, contexto, serviço e próximo passo sem depender da coleção anterior.

Conteúdo removido não deve gerar dead-end evitável. A estratégia física de redirect pertence às camadas técnicas.

---

## 14. UX-JRN-005 — Iniciar contato pelo WhatsApp

**Relacionada:** US-007.

WhatsApp é saída para terceiro.

```text
USUÁRIO ESCOLHE CONTATO
↓
SITE INICIA SAÍDA
↓
WHATSAPP / NAVEGADOR / APP ASSUME
```

O site pode medir intenção de abertura do canal.

O site não pode concluir sozinho:

```text
MENSAGEM ENVIADA
LEAD RECEBIDO
ATENDIMENTO INICIADO
VENDA GERADA
```

sem evidência externa correspondente.

---

## 15. Falha ao abrir canal externo

Quando existir alternativa real, outros meios de contato podem permanecer disponíveis.

A mensagem deve falar somente do que o site sabe.

Exemplo válido quando verificável:

> Não foi possível abrir o WhatsApp neste dispositivo. Use outra forma de contato.

---

## 16. UX-JRN-006 — Solicitar contato/proposta estruturada

**Relacionada:** US-008, US-012, US-020.

O formulário é tarefa focada e deve coletar somente informação útil ao retorno/qualificação.

Conjunto inicial simulado:

- Nome;
- Empresa no fluxo B2B;
- Cidade;
- Necessidade/serviço;
- Telefone/WhatsApp ou e-mail conforme política final;
- Detalhes adicionais opcionais.

Cada campo obrigatório precisa justificar seu valor.

---

## 17. Contato mínimo

Não exigir telefone e e-mail simultaneamente se um único canal suficiente resolver o retorno.

A política final pode usar pelo menos um contato utilizável.

---

## 18. Variantes B2C/B2B

Campo Empresa pode ser necessário no B2B e desnecessário no residencial.

Não forçar um formulário universal mais burocrático apenas para simplificar implementação.

---

## 19. Campo Cidade

Cidade existe por razão operacional: área de atendimento.

Se estiver fora da área regular conhecida, o produto pode emitir aviso e ainda permitir contato quando o negócio quiser confirmar disponibilidade.

---

## 20. UX-VAL — Validação proporcional

Níveis:

```text
BLOQUEIO
REVISÃO
AVISO
INFORMATIVO
```

Exemplos:

**Bloqueio:** nenhuma forma válida de retorno.

**Revisão:** claim editorial sensível antes da publicação.

**Aviso:** cidade fora da área regular conhecida.

**Informativo:** indicação do canal de retorno esperado.

---

## 21. Estados do formulário

```text
UX-STA-002 EDITING
UX-STA-003 VALIDATION_ERROR
UX-STA-004 SUBMITTING
UX-STA-005 SUBMITTED
UX-STA-006 SUBMIT_FAILED_RECOVERABLE
UX-STA-007 SUBMIT_FAILED_BLOCKING
```

A UI usará linguagem humana equivalente.

---

## 22. Repetição de envio

Uma única intenção do usuário não deve gerar múltiplos contatos apenas porque o comando foi repetido diante de resposta lenta.

A Engenharia definirá o mecanismo concreto.

---

## 23. Falha recuperável do formulário

Resultado esperado:

```text
CONTEÚDO VÁLIDO PRESERVADO
+
ERRO EXPLICADO
+
RETRY POSSÍVEL
+
ALTERNATIVA COMERCIAL DISPONÍVEL, quando pertinente
```

Não limpar o formulário após falha transitória.

---

## 24. Sucesso de envio

Só declarar recebimento quando o sistema tiver confirmado o recebimento correspondente.

Mensagem de referência:

> Solicitação enviada. A NorteSul recebeu seus dados para retorno.

Não prometer prazo de retorno sem acordo operacional real.

---

## 25. Política de rascunho

No P0:

- preservar valores na tentativa atual após falha recuperável;
- não há requisito de persistir rascunho entre sessões/dias.

Não criar complexidade offline-first para um formulário público de baixo risco.

---

## 26. Conectividade

```text
OFFLINE-FIRST: NO
```

Falha transitória de rede durante envio precisa possuir recuperação adequada sem escolher nesta etapa storage, service worker ou mecanismo de retry interno.

---

## 27. UX-JRN-007 — Atualizar conteúdo

**Relacionada:** J-005, US-013, US-014, US-015.

A tarefa pode ocorrer em superfície herdada do provider.

Fluxo mínimo:

```text
AUTENTICAR
↓
LOCALIZAR CONTEÚDO
↓
CRIAR / EDITAR
↓
REVISAR
↓
PUBLICAR
↓
CONFIRMAR ESTADO
```

A UX especifica a tarefa necessária; não impõe o layout do CMS.

---

## 28. Edição progressiva

Quando a plataforma permitir, preferir:

```text
LISTA
↓
DETALHE
↓
EDIÇÃO
```

O usuário precisa reconhecer objeto, estado e impacto da publicação.

---

## 29. UX-FLW-001 — Publicar case

Conteúdo mínimo operacional:

```text
TÍTULO
SERVIÇO RELACIONADO
CONTEXTO / LOCAL PERMITIDO
IMAGEM PRINCIPAL
RESUMO
DESCRIÇÃO/ACESSIBILIDADE DA IMAGEM
REVISÃO
PUBLICAÇÃO
```

O case não exige obrigatoriamente vídeo, grande galeria, texto longo ou nome do cliente.

---

## 30. Privacidade de case

Antes de publicar material identificável, a experiência editorial precisa deixar claro que o conteúdo será público e apoiar revisão de elementos como:

- cliente identificável;
- rosto;
- endereço;
- placa;
- documento;
- informação interna.

Não é necessário criar workflow jurídico completo no CMS.

---

## 31. Estados editoriais

Mínimo:

```text
PUBLICADO
NÃO PUBLICADO
```

Rascunho/revisão podem existir se a plataforma escolhida os suportar e o fluxo justificar.

Workflow multinível não é requisito P0.

---

## 32. Remoção de conteúdo publicado

A experiência precisa comunicar a consequência pública da remoção.

Se a URL for pública/indexada, a camada técnica deverá definir tratamento posterior.

A UX não escolhe redirect físico.

---

## 33. UX-JRN-008 — Aprender com a operação

**Relacionada:** J-006, US-016, US-017, US-018, OUT-007.

```text
DESCOBERTA
↓
VISITA
↓
INTERAÇÃO
↓
CONTATO
↓
QUALIFICAÇÃO COMERCIAL
↓
INTERPRETAÇÃO
↓
MELHORIA
```

O painel de análise pode ser provider-owned ou externo. O requisito é obter sinais suficientes, não construir analytics próprio.

---

## 34. Eventos semânticos

```text
UX-EVT-001 service_viewed
UX-EVT-002 business_services_viewed
UX-EVT-003 case_viewed
UX-EVT-004 whatsapp_contact_started
UX-EVT-005 quote_request_started
UX-EVT-006 quote_request_validation_error
UX-EVT-007 quote_request_submitted
UX-EVT-008 quote_request_failed
UX-EVT-009 contact_alternative_used
UX-EVT-010 editorial_content_published
```

`UX-EVT-011 lead_qualified` poderá existir quando houver ponte operacional com qualificação comercial.

---

## 35. Minimização da telemetria

Não enviar como propriedades comuns de analytics:

- nome;
- telefone;
- e-mail;
- mensagem livre;
- conteúdo integral do formulário.

Mensuração deve registrar semântica do evento, não copiar o lead.

---

## 36. Analytics não bloqueia o core

Se analytics falhar:

```text
SITE CONTINUA
NAVEGAÇÃO CONTINUA
WHATSAPP CONTINUA
FORMULÁRIO CONTINUA
```

---

## 37. Cookies e consentimento

Não criar banner universal por hábito.

Fluxo correto:

```text
TRACKER / COOKIE / FINALIDADE
↓
ANÁLISE DE NECESSIDADE E PRIVACIDADE
↓
EXPERIÊNCIA DE CONSENTIMENTO/INFORMAÇÃO CORRESPONDENTE
```

A tecnologia concreta definirá quais mecanismos realmente existem.

---

## 38. Privacidade no formulário

Próximo à coleta, explicar de forma suficiente a finalidade do uso dos dados.

A política completa permanece acessível.

Checkbox de “li e aceito” não é obrigatório por padrão; depende da base/fluxo aprovado posteriormente.

---

## 39. Página não encontrada

404 precisa:

- explicar ausência;
- preservar identidade e navegação;
- oferecer destinos reais úteis.

Não usar mensagem genérica sem contexto.

---

## 40. Busca interna

```text
SITE_SEARCH: NOT_JUSTIFIED_IN_P0
```

O corpus atual não exige busca interna.

---

## 41. FAQ

FAQ deve existir por dúvida real ou decisão útil, não por obrigação de SEO.

Accordion é possível, não obrigatório.

---

## 42. Navegação mobile

Menu deve funcionar com toque, teclado e foco previsível.

Nenhum gesto é requisito exclusivo.

A ação comercial pode permanecer destacada sem competir com todos os destinos.

---

## 43. CTA persistente mobile

```text
PERSISTENT_WHATSAPP_CTA:
TESTABLE_OPTION
NOT_CANONICAL_DEFAULT
```

Critérios:

- ação continua válida durante a rolagem;
- não cobre conteúdo/foco/teclado;
- não duplica CTA sem benefício;
- mantém acessibilidade;
- ocupa área proporcional.

---

## 44. Desktop e tablet

Desktop pode mostrar mais contexto simultaneamente, como serviço + prova + contato.

Tablet não será tratado como breakpoint esquecido.

Resultado, significado e segurança permanecem equivalentes entre form factors.

---

## 45. Acessibilidade da jornada

Validar, conforme aplicável:

- hierarchy de headings em entrada direta;
- menu por teclado;
- foco visível;
- skip link;
- accordion semântico;
- labels associados;
- erros ligados ao campo;
- foco após erro;
- sucesso anunciado semanticamente;
- alt text pertinente;
- links com nome claro;
- zoom/reflow;
- motion reduzível;
- CTA persistente sem cobrir foco;
- navegação mobile sem gesto obrigatório.

Acessibilidade é comportamento ponta a ponta, não somente atributo de componente.

---

## 46. Performance percebida

O texto principal não deve depender do carregamento de imagem pesada para aparecer.

Imagens não devem causar deslocamento material de layout.

A ação de contato não pode depender de efeitos visuais pesados.

A implementação concreta fica para Engenharia.

---

## 47. Falha de imagem

Se uma imagem não carregar, case/serviço ainda precisam manter conteúdo textual suficiente para compreensão.

Imagem não é única portadora da informação central.

---

## 48. Deep links e migração

URLs públicas importantes são entradas de produto.

A experiência exige:

- ausência de dead-end evitável;
- contexto suficiente em página isolada;
- retorno previsível;
- nenhuma dependência de sessão anterior.

A técnica definirá redirects, canonicals e sitemap.

---

## 49. Conteúdo desatualizado

Contradição editorial em informação crítica é defeito funcional do produto.

Região, serviço, contato e outras informações operacionais precisam possuir owner de atualização.

---

## 50. Spam e abuso

Proteção é necessária, mas a UX não escolhe CAPTCHA/provider.

Diretriz:

> **Aplicar a menor fricção possível para usuários legítimos, mantendo proteção proporcional ao abuso observado.**

Desafio explícito, se necessário, precisa ser acessível.

---

## 51. Microcopy operacional de referência

**Contato:**
> Informe como podemos retornar seu contato.

**Erro de campo:**
> Informe um telefone com DDD ou um e-mail válido.

**Falha recuperável:**
> Não foi possível enviar agora. Suas informações continuam preenchidas. Tente novamente ou fale conosco pelo WhatsApp.

**Sucesso:**
> Solicitação enviada. Entraremos em contato pelo canal informado.

Somente usar quando a operação real sustentar essa promessa.

**Região:**
> Não encontrou sua cidade? Fale conosco para confirmar disponibilidade.

**404:**
> Esta página não está disponível. Você pode continuar pelos nossos serviços ou entrar em contato.

---

## 52. Plano de testes de UX

### UX-TST-001 — Entrada residencial por busca

Usuário entra diretamente em serviço e, sem ver Home, consegue responder o que a empresa faz, se atende sua necessidade, onde atende e qual o próximo passo.

### UX-TST-002 — Entrada empresarial

Comprador identifica capacidade, serviços, provas e contato/proposta.

### UX-TST-003 — WhatsApp

Pessoa encontra e inicia o canal sem formulário obrigatório e entende que está saindo para serviço externo.

### UX-TST-004 — Formulário B2B

Pessoa envia solicitação sem dúvidas de preenchimento e sem campos desnecessários bloqueando.

### UX-TST-005 — Falha de rede

Valores permanecem, erro é compreensível, retry é possível e alternativa comercial permanece.

### UX-TST-006 — Case direto

Pessoa entra por case e chega ao serviço relacionado/contato.

### UX-TST-007 — Região

Pessoa reconhece cobertura ou necessidade de confirmar.

### UX-TST-008 — Publicar case

Administrativo publica case sem desenvolvedor.

### UX-TST-009 — Atualizar região/FAQ

Usuário interno altera conteúdo previsto e reconhece estado publicado.

### UX-TST-010 — Mobile

Executar serviço → prova → contato em celular.

### UX-TST-011 — Teclado

Concluir navegação e formulário sem mouse.

### UX-TST-012 — Screen reader smoke

Cobrir navegação, headings, links, form, erro, sucesso e case.

---

## 53. Gates de UX

```text
UX-GATE-001
entrada direta por serviço é compreensível sem Home

UX-GATE-002
visitante reconhece serviço + região + próximo passo

UX-GATE-003
B2B encontra capacidade e contato sem densidade desnecessária

UX-GATE-004
WhatsApp é acessível sem saturação comercial

UX-GATE-005
formulário coleta somente contexto necessário

UX-GATE-006
falha de formulário não apaga trabalho válido

UX-GATE-007
cases sustentam confiança e conectam ao serviço

UX-GATE-008
PMOC separa serviço e informação regulatória

UX-GATE-009
administrativo executa tarefas editoriais P0 sem desenvolvedor

UX-GATE-010
mobile e teclado preservam jornada crítica

UX-GATE-011
analytics não coleta conteúdo pessoal por conveniência

UX-GATE-012
migração não cria dead ends evitáveis
```

---

## 54. Superfícies controladas e herdadas

A decisão do estágio 04 continua vinculante.

Em superfície editorial herdada do provider, a UX não exige a mesma identidade visual da NorteSul.

Exige:

- tarefa concluível;
- estados compreensíveis;
- segurança;
- acessibilidade suficiente;
- publicação previsível.

Portanto:

```text
BUY
!=
FORA DO ESCOPO DE UX
```

O projeto pode não desenhar o CMS, mas precisa especificar o que o usuário deve conseguir fazer nele.

---

## 55. Critérios futuros de seleção de CMS derivados da UX

A plataforma futura precisa permitir adequadamente:

- editar serviço;
- editar região;
- editar FAQ;
- criar case;
- gerenciar imagem;
- revisar conteúdo;
- publicar;
- reconhecer estado de publicação;
- controlar acesso editorial.

Se essas tarefas exigirem desenvolvedor, a solução falha no produto mesmo que o site público seja visualmente bom.

---

## 56. Finding metodológico reforçado

### CASE-02-METHOD-FINDING-002

> **Em produtos híbridos, a UX precisa especificar tarefas e critérios mínimos das superfícies herdadas de um provider, mesmo quando não controla seu layout.**

O finding permanece como evidência do caso; a metodologia canônica não é alterada automaticamente nesta etapa.

---

## 57. Definition of Ready para etapa técnica

Uma jornada/superfície está suficientemente definida quando consegue responder, conforme aplicável:

- persona/contexto;
- outcome/story;
- entrada;
- tarefa mental;
- ação dominante;
- estados;
- validação;
- recuperação;
- dados pessoais;
- dependência externa;
- comportamento mobile;
- acessibilidade;
- SEO/indexação;
- eventos semânticos;
- prova de usabilidade;
- pendências.

Esse estado ainda não significa `READY_FOR_CODEX`.

---

## 58. Validação da metodologia

Exemplo de progressão:

```text
US-007
iniciar contato rápido
↓
Princípios
conversão sem sequestrar leitura
↓
UI
CTA disciplinado
↓
UX
saída para terceiro,
limites de confirmação,
fallback,
telemetria sem inferência falsa
```

Outro:

```text
US-014
publicar case
↓
UI
case editorialmente sustentável
↓
UX
conteúdo mínimo,
revisão,
publicação,
estado,
privacidade,
teste editorial
```

Nenhuma tecnologia foi selecionada.

Resultado:

```text
UX_METHOD_VALIDATION: PASS
PRODUCT_SCOPE_CHANGED: NO
BUSINESS_RULE_CHANGED: NO
VISUAL_IDENTITY_CHANGED: NO
TECHNOLOGY_SELECTED: NO
CMS_SELECTED: NO

EXPERIENCE_CONTRACT: DEFINED
PUBLIC_INFORMATION_ARCHITECTURE: DEFINED
DIRECT_ENTRY_BEHAVIOR: DEFINED
RESIDENTIAL_JOURNEY: DEFINED
B2B_JOURNEY: DEFINED
CASE_JOURNEY: DEFINED
WHATSAPP_HANDOFF: DEFINED
FORM_JOURNEY: DEFINED
FORM_STATES: DEFINED
RECOVERY: DEFINED
EDITORIAL_JOURNEY: DEFINED
PRIVACY_UX: DEFINED
ANALYTICS_SEMANTICS: DEFINED
ACCESSIBILITY_FLOW: DEFINED
UX_TEST_PLAN: DEFINED
UX_GATES: DEFINED

UX_READINESS: SUFFICIENT_FOR_TECHNICAL_STAGE
READY_FOR_CODEX: NO
```

---

## 59. Handoff

```text
UX_EXECUTION: COMPLETE
CLIENT_REVIEW: APPROVED_FOR_SIMULATION
UX_READINESS: SUFFICIENT_FOR_TECHNICAL_STAGE
READY_FOR_CODEX: NO
NEXT_STAGE: 06 — Técnicas de Desenvolvimento
```

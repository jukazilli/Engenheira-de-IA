---
document_id: PROCESS-02-BRIEFING-PRODUTO-ESCOPO
title: Briefing de Produto e Escopo
status: draft-methodology
version: 0.1.0
stage: briefing-produto-escopo
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
produces: 02_Briefing_de_Produto_e_Escopo.md
next_stage: Visão de Product Owner
---

# 02 — Briefing de Produto e Escopo

## 1. Propósito

O **Briefing de Produto e Escopo** é a terceira etapa operacional do Processo de Desenvolvimento de Software com IA Assistida.

Sua função é transformar a intenção amadurecida no Discovery e as evidências reunidas na Pesquisa e Viabilidade em um **contrato canônico de produto**, suficientemente claro para orientar as etapas seguintes sem antecipar o detalhamento que pertence ao Product Owner, UX/UI, Engenharia, Tech Lead ou Infraestrutura.

A pergunta central desta etapa é:

> **Qual produto estamos efetivamente decidindo construir agora, para quem, com qual promessa, qual núcleo de valor, quais limites e quais compromissos de escopo?**

O Briefing é o ponto em que o projeto deixa de trabalhar apenas com uma ideia investigada e passa a possuir uma definição de produto aprovada.

Ele não é backlog, especificação de tela, arquitetura, plano técnico nem documento de implementação.

Ele é o documento que fixa **o que o produto é e o que ele não é neste horizonte**.

---

## 2. Posição no processo

```text
00_Discovery.md
        ↓
01_Pesquisa_e_Viabilidade.md
        ↓
02_BRIEFING_DE_PRODUTO_E_ESCOPO
        ↓
03_VISÃO_DE_PRODUCT_OWNER
```

O Discovery registra intenção, hipóteses, contexto e perguntas.

A Pesquisa e Viabilidade confronta essa intenção com evidências, concorrência, riscos, restrições e viabilidade.

O Briefing decide o recorte de produto que sobreviveu à investigação.

A Visão de Product Owner transforma esse recorte em outcomes, capacidades priorizadas, épicos, critérios e lógica operacional mais detalhada.

---

## 3. Origem desta etapa

Esta etapa foi formalizada a partir do processo real do DayGym, no qual o Briefing foi tratado como **documento oficial do produto** e como o artefato que consolidou o escopo após a investigação.

O documento real cumpriu funções importantes que devem ser preservadas como padrão reutilizável:

```text
FIXAR A DEFINIÇÃO DO PRODUTO
        ↓
CONSOLIDAR DECISÕES
        ↓
DEFINIR PÚBLICO E PROMESSA
        ↓
ESTABELECER O LOOP PRINCIPAL
        ↓
ORGANIZAR ESCOPO POR HORIZONTE
        ↓
REGISTRAR LIMITES E RISCOS
        ↓
DEFINIR MÉTRICAS E GATES
        ↓
PREPARAR O HANDOFF PARA PRODUCT OWNER
```

Ao mesmo tempo, o processo refinado deve corrigir um risco observado nesse tipo de documento: o Briefing pode facilmente começar a absorver responsabilidades das etapas seguintes.

Por isso, esta metodologia estabelece limites explícitos de propriedade documental.

---

## 4. Pré-requisitos obrigatórios

Antes de iniciar o Briefing, o ChatGPT deve consumir integralmente:

1. `00_Discovery.md`;
2. `01_Pesquisa_e_Viabilidade.md`.

O Briefing não deve reconstruir esses documentos do zero.

Ele deve identificar:

### Do Discovery

- intenção original;
- problema percebido;
- usuários imaginados;
- valor esperado;
- restrições iniciais;
- decisões humanas;
- hipóteses;
- pendências;
- alternativas descartadas.

### Da Pesquisa e Viabilidade

- problema com evidência;
- público mais promissor;
- oportunidades;
- diferenciação possível;
- riscos;
- dependências externas;
- restrições regulatórias e operacionais;
- hipóteses críticas;
- recorte recomendado;
- gates;
- verdict de viabilidade;
- decisões em aberto.

O ChatGPT deve verificar se existe conflito entre os dois documentos antes de consolidar o Briefing.

---

## 5. Condição mínima para começar

O Briefing só deve começar quando a Pesquisa e Viabilidade tiver resultado compatível com avanço:

```text
GO
ou
GO CONDICIONAL
```

Se o resultado for:

```text
PESQUISAR MAIS
```

as lacunas críticas devem ser reduzidas antes de canonizar o Briefing.

Se o resultado for:

```text
NO-GO
```

o projeto deve retornar ao Discovery ou ser encerrado no recorte atual, salvo decisão humana explícita e registrada em contrário.

---

## 6. Responsabilidade do Briefing

O Briefing deve canonizar, quando aplicável:

- definição do produto;
- tese consolidada;
- problema central;
- público inicial;
- principais stakeholders;
- promessa de valor;
- posicionamento;
- princípios de produto;
- loop principal;
- hierarquia de valor;
- escopo por horizonte;
- capacidades obrigatórias do horizonte atual;
- limites e não objetivos;
- regras de produto que não podem ser reinterpretadas silenciosamente;
- modelo de receita ou direção comercial quando já decidido;
- métricas de produto de alto nível;
- gates de produto;
- dependências externas relevantes;
- riscos aceitos e não aceitos;
- decisões ainda pendentes;
- critérios para avançar à Visão de Product Owner.

---

## 7. O que o Briefing não deve fazer

O Briefing não deve ser usado para canonizar detalhamento pertencente a outras camadas.

### Não é responsabilidade do Briefing

```text
BACKLOG DETALHADO
HISTÓRIAS DE USUÁRIO COMPLETAS
CRITÉRIOS DE ACEITE DE IMPLEMENTAÇÃO
WIREFRAMES
DESIGN SYSTEM
COMPONENTES VISUAIS
FLUXOS DE INTERAÇÃO EXAUSTIVOS
MODELO ARQUITETURAL
ESTRUTURA DE REPOSITÓRIO
STACK
FRAMEWORKS
BIBLIOTECAS
PROVIDERS DE INFRAESTRUTURA
CI/CD
MIGRATIONS
SCHEMAS DE BANCO
CONTRATOS DE API
```

Esses elementos podem aparecer como **restrições, dependências ou evidências herdadas da Pesquisa**, mas não devem ser transformados em decisões canônicas prematuras.

---

## 8. Regra de propriedade documental

Quando uma informação aparecer no Briefing, deve ser possível responder:

> **Esta é uma decisão de produto ou uma decisão de outra camada?**

Exemplos:

```text
“o produto precisa funcionar durante a sessão mesmo com internet instável”
→ decisão de produto / experiência / qualidade esperada

“vamos usar SQLite local com fila X”
→ Engenharia / Tech Lead

“o usuário precisa receber o plano de três formas”
→ produto

“vamos usar biblioteca Y para upload”
→ Tech Lead

“a loja não pode usar dados de saúde para personalização”
→ produto / privacidade / política

“a separação será implementada com serviço Z”
→ Engenharia / Infraestrutura
```

O Briefing fixa a **necessidade e o limite**. As camadas técnicas definem a materialização.

---

## 9. Como conduzir o Briefing no ChatGPT

O Briefing deve ser conduzido como uma sessão de consolidação, não como nova Pesquisa.

Fluxo recomendado:

```text
CONSUMIR DISCOVERY
        ↓
CONSUMIR PESQUISA E VIABILIDADE
        ↓
LISTAR DECISÕES JÁ MADURAS
        ↓
LISTAR CONFLITOS E PENDÊNCIAS
        ↓
PERGUNTAR SOMENTE O QUE É NECESSÁRIO
        ↓
PROPOR O BRIEFING
        ↓
REVISÃO HUMANA
        ↓
CORREÇÕES
        ↓
APROVAÇÃO
        ↓
CANONIZAÇÃO
```

O ChatGPT não deve repetir perguntas já respondidas nos documentos anteriores sem motivo.

---

## 10. Perguntas que o Briefing precisa conseguir responder

Ao final, o documento deve permitir responder de forma clara:

1. O que é o produto?
2. Qual problema central ele resolve?
3. Para quem ele está sendo construído neste horizonte?
4. Qual promessa de valor deve orientar as decisões?
5. Qual comportamento ou loop representa o núcleo do produto?
6. Quais capacidades são obrigatórias agora?
7. Quais capacidades ficam para depois?
8. O que está explicitamente fora de escopo?
9. Quais regras de produto não podem ser reinterpretadas pela implementação?
10. Quais riscos são aceitos?
11. Quais riscos não são aceitos?
12. Quais módulos ou capacidades dependem de gates?
13. Quais métricas indicarão se o produto está gerando valor?
14. Quais dependências externas podem impedir ou alterar o escopo?
15. O que ainda permanece em aberto?
16. Qual é a próxima camada responsável por detalhar a execução do produto?

---

## 11. Definição do produto

O documento deve abrir com uma definição curta e inequívoca.

Formato recomendado:

```text
<Produto> é <categoria/tipo de solução> que <transformação principal>,
para <público/contexto>, preservando <restrição ou princípio essencial>.
```

A definição não deve ser slogan publicitário.

Ela deve permitir que outra pessoa entenda a essência do produto sem ler o documento inteiro.

---

## 12. Tese consolidada

A tese deve conectar:

```text
PROBLEMA OBSERVADO
        ↓
COMPORTAMENTO / CONTEXTO
        ↓
INTERVENÇÃO DO PRODUTO
        ↓
VALOR ESPERADO
```

Exemplo abstrato:

```text
Quando o esforço operacional para realizar X supera o benefício percebido,
os usuários abandonam Y.

O produto reduz esse esforço por meio de Z e torna o resultado visível,
permitindo que o usuário tome a próxima decisão com menos fricção.
```

A tese deve refletir o que sobreviveu à Pesquisa e Viabilidade, não apenas repetir a ideia inicial.

---

## 13. Decisões consolidadas

O Briefing deve possuir uma seção curta de decisões consolidadas para temas que poderiam voltar a ser reinterpretados.

Formato recomendado:

| Tema | Decisão | Implicação |
| --- | --- | --- |
| Público | Quem entra no horizonte atual | O que isso simplifica ou exige |
| Canal | Onde o produto será usado | Impacto de experiência |
| Núcleo | Qual é o core | O que deve dominar |
| Módulo secundário | Entra ou não entra | Sob qual gate |
| Receita | Modelo inicial | Limites e dependências |

A tabela não deve virar duplicação do documento inteiro.

Ela serve como mapa rápido das decisões de maior risco de regressão.

---

## 14. Público e stakeholders

O Briefing deve canonizar o público do horizonte atual.

Pode incluir:

- público primário;
- segmentos prioritários;
- atores secundários;
- operadores internos;
- profissionais ou parceiros;
- administradores;
- compradores ou responsáveis quando aplicável.

### Público não é persona detalhada

O Briefing define **quem está dentro do produto**.

A Visão de Product Owner poderá aprofundar comportamento, necessidades, outcomes e perfis operacionais.

---

## 15. JTBD ou trabalho principal

Quando aplicável, utilizar estrutura simples:

| Elemento | Pergunta |
| --- | --- |
| Quando | Em qual situação real? |
| Quero | O que a pessoa tenta realizar? |
| Para | Qual resultado ela busca? |
| Mesmo se / Sem | Qual obstáculo deve ser tolerado ou removido? |

O objetivo não é preencher um template por cerimônia.

É preservar o contexto em que o produto precisa gerar valor.

---

## 16. Promessa de valor

O Briefing deve fixar uma promessa operacional curta.

Uma boa promessa ajuda as próximas etapas a priorizar.

Ela deve ser verificável por comportamento do produto e não depender de linguagem vaga como:

```text
“revolucionário”
“inteligente”
“completo”
“a melhor experiência”
```

Pergunta de qualidade:

> **Se uma funcionalidade não ajuda a cumprir essa promessa, por que ela está no horizonte atual?**

---

## 17. Pilares ou princípios de produto

O Briefing pode fixar poucos princípios de produto que funcionam como filtros de decisão.

Exemplos abstratos:

```text
VALOR ANTES DE CONFIGURAÇÃO
AÇÃO PRINCIPAL VISÍVEL
AUTOMAÇÃO EXPLICÁVEL
CONTROLE REVOGÁVEL
PRIVACIDADE POR PADRÃO
CORE NÃO PODE SER BLOQUEADO POR MÓDULO SECUNDÁRIO
```

Esses princípios ainda não substituem os futuros documentos de UX/UI.

Eles representam regras de produto.

---

## 18. Posicionamento

Quando relevante, o documento deve registrar:

- para quem o produto existe;
- qual problema central resolve;
- como quer ser percebido;
- contra qual comportamento ou categoria não quer competir;
- quais promessas não deve fazer.

Pode incluir estrutura:

```text
Para <público>, que <situação/problema>,
<produto> é <categoria> que <valor principal>,
ao contrário de <alternativa/comportamento>, porque <diferenciação>.
```

O posicionamento não deve obrigar o produto a atacar concorrentes nominalmente.

---

## 19. Loop principal do produto

O Briefing deve tornar explícita a sequência que representa geração de valor.

Exemplo genérico:

```text
ENTRAR
  ↓
OBTER CONTEXTO
  ↓
REALIZAR TAREFA CENTRAL
  ↓
REGISTRAR / PRODUZIR RESULTADO
  ↓
RECEBER FEEDBACK
  ↓
DECIDIR PRÓXIMA AÇÃO
  ↓
RETORNAR
```

O loop principal serve como critério de prioridade.

Uma funcionalidade secundária não deve destruir o loop principal.

---

## 20. Hierarquia de valor

Quando o produto possui muitos módulos, o Briefing deve definir explicitamente a ordem de importância.

Formato recomendado:

| Prioridade | Camada | Regra |
| --- | --- | --- |
| 1 | Core | Deve dominar a experiência |
| 2 | Feedback / resultado | Explica valor |
| 3 | Colaboração | Apoia o core |
| 4 | Módulos auxiliares | Não competem com a ação principal |
| 5 | Engajamento | Nunca sequestra o objetivo |
| 6 | Receita adjacente | Não degrada confiança nem core |

Essa hierarquia será entrada importante para UX/UI.

---

## 21. Escopo por horizonte

O Briefing deve separar explicitamente o que pertence a cada horizonte.

Padrão recomendado:

```text
P0 — HORIZONTE ATUAL / BETA / MVP OPERACIONAL
P1 — APÓS SINAIS OU DEPENDÊNCIAS
P2 — MATURIDADE / EXPANSÃO
FORA DE ESCOPO
```

Os nomes podem mudar conforme o projeto.

O importante é não manter tudo como “futuro” sem prioridade.

---

## 22. O que significa P0

P0 é o **contrato de produto do horizonte atual**.

Não é automaticamente:

- ordem de implementação;
- sprint 1;
- backlog;
- uma autorização para desenvolver todos os módulos em paralelo;
- uma obrigação de dar o mesmo peso visual a todas as capacidades.

O backlog e o plano de execução serão definidos posteriormente.

---

## 23. Critério de entrada no horizonte atual

Uma capacidade deve entrar no horizonte atual quando uma ou mais condições forem verdadeiras:

- é necessária para cumprir a promessa principal;
- é necessária para completar o loop central;
- é requisito explícito aprovado pelo humano;
- é obrigatória para segurança, privacidade, operação ou distribuição;
- é necessária para validar uma hipótese crítica do modelo;
- sua ausência impede que o produto seja utilizável no contexto definido.

Não deve entrar apenas porque:

- concorrentes possuem;
- a IA sabe implementar;
- é tecnicamente interessante;
- parece “profissional”;
- cabe no documento.

---

## 24. Capacidades do horizonte atual

O Briefing pode agrupar o escopo por domínio de produto.

Exemplos:

```text
CONTA / IDENTIDADE
CORE OPERACIONAL
HISTÓRICO / PROGRESSO
COLABORAÇÃO
CONTEÚDO
COMUNIDADE
COMÉRCIO
ADMINISTRAÇÃO
SUPORTE
```

Para cada domínio, o Briefing deve registrar **o que precisa existir**, sem detalhar ainda como será implementado.

---

## 25. Regras de produto críticas

Algumas regras precisam aparecer no Briefing porque alterá-las mudaria a intenção do produto.

Exemplos:

```text
uma ação automática exige confirmação

um vínculo é revogável pelo usuário

um conteúdo privado não é publicado automaticamente

um módulo secundário pode ser desativado sem quebrar o core

um benefício econômico não depende de dado autodeclarado sem controle

um dado sensível não pode ser reutilizado para publicidade sem nova finalidade legítima
```

Essas regras devem ser formuladas em linguagem de produto, não como implementação.

---

## 26. Módulos condicionados por gates

Uma capacidade pode estar no P0 e ainda assim não estar liberada no primeiro momento.

Exemplo:

```text
CAPACIDADE P0
        ↓
IMPLEMENTAÇÃO
        ↓
FEATURE FLAG / CONTROLE DE LIBERAÇÃO
        ↓
GATE
        ↓
LIBERAÇÃO
```

Isso é útil para módulos com risco operacional, regulatório, comunitário ou comercial.

O Briefing pode fixar o gate sem definir sua implementação técnica.

---

## 27. Fora de escopo

O documento deve conter uma seção explícita de **fora de escopo**.

Essa seção reduz regressão de escopo e decisões silenciosas.

Pode incluir:

- públicos não atendidos;
- tipos de transação não suportados;
- comportamentos proibidos;
- funcionalidades adiadas;
- responsabilidades que o produto não assume;
- integrações ainda não autorizadas;
- tipos de dado que não serão utilizados;
- modelos de negócio não adotados.

Um fora de escopo pode ser revisado no futuro, mas não deve reaparecer por acidente.

---

## 28. Modelo de receita e sustentabilidade

Quando a Pesquisa e o humano já tiverem amadurecido a direção comercial, o Briefing pode registrar o modelo por fase.

Exemplo:

| Fase | Receita | Condição |
| --- | --- | --- |
| Inicial | Modelo A | Gate A |
| Seguinte | Modelo B | Retenção / demanda |
| Posterior | Modelo C | Maturidade operacional |

O Briefing não deve inventar preço final sem evidência ou decisão humana.

---

## 29. Dependências externas

O Briefing deve registrar dependências que podem alterar o produto.

Exemplos:

- aprovação de marketplace;
- conta de parceiro;
- licença de dados;
- registro de marca;
- verificação profissional;
- política de app store;
- autorização contratual;
- API ainda não aprovada;
- parecer jurídico;
- fornecedor de conteúdo;
- disponibilidade regional.

Cada dependência deve indicar seu impacto.

---

## 30. Dependência não é garantia

Regra obrigatória:

```text
PLANEJADO COM TERCEIRO
≠
DISPONÍVEL
≠
APROVADO
≠
CONTRATADO
```

Se o produto depende de autorização externa, o Briefing deve prever fallback ou declarar o bloqueio.

---

## 31. Requisitos de qualidade no nível de produto

O Briefing pode registrar requisitos não funcionais **como expectativa observável de produto**.

Exemplos:

| Qualidade | Expectativa de produto |
| --- | --- |
| Confiabilidade | A ação crítica não pode desaparecer após falha comum |
| Offline | Tarefa central precisa continuar em rede ruim, quando aplicável |
| Segurança | Acesso sensível exige controles compatíveis com o risco |
| Privacidade | Finalidades precisam permanecer separadas |
| Acessibilidade | A experiência deve atender o alvo definido |
| Operação | Módulos de risco precisam ser desabilitáveis |
| Auditabilidade | Ações críticas precisam deixar trilha |

O Briefing não escolhe a solução técnica para cumprir esses requisitos.

---

## 32. Métricas de produto

O Briefing deve registrar métricas que representem valor e saúde do produto, não apenas atividade superficial.

Podem existir:

```text
MÉTRICA NORTE
ATIVAÇÃO
TEMPO PARA VALOR
CONCLUSÃO DO LOOP PRINCIPAL
RETENÇÃO
FRICÇÃO
QUALIDADE
CONFIANÇA
CONVERSÃO
SAÚDE OPERACIONAL
```

Evitar métricas que incentivem comportamento contrário ao produto.

Exemplo:

```text
abertura diária
```

não é automaticamente boa métrica se o produto existe para concluir uma tarefa semanal.

---

## 33. Gates de produto

O Briefing deve manter gates materiais herdados da Pesquisa e consolidar novos gates que dependem da definição do escopo.

Formato recomendado:

| Gate | Condição de saída | O que libera |
| --- | --- | --- |
| G-PROD-01 | Critério observável | Capacidade / fase |

Gates podem existir para:

- core;
- integração;
- comunidade;
- privacidade;
- profissional;
- comércio;
- publicação;
- economia interna;
- público regulado.

---

## 34. Gate não é tarefa

Exemplo incorreto:

```text
Gate: implementar tela de cadastro
```

Exemplo correto:

```text
Gate: usuário consegue concluir cadastro e primeira ação crítica sem suporte externo relevante
```

O gate define condição de avanço.

A implementação que o satisfaz será definida depois.

---

## 35. Riscos aceitos e não aceitos

O Briefing deve tornar explícita a postura de produto frente a riscos materiais.

Formato recomendado:

| Risco | Postura | Tratamento esperado |
| --- | --- | --- |
| Risco A | Aceito | Guardrail |
| Risco B | Aceito com condição | Gate |
| Risco C | Não aceito | Proibição / bloqueio |

Isso ajuda etapas técnicas a não reinterpretarem tolerância ao risco.

---

## 36. Risco aceito não significa risco ignorado

Quando um risco é aceito, o documento deve registrar:

- por que é tolerável;
- qual limite foi aceito;
- que mitigação ainda é necessária;
- quando precisa ser reavaliado.

---

## 37. Decisões ainda dependentes de validação

O Briefing não precisa resolver tudo.

Uma seção explícita deve registrar decisões que permanecem condicionadas a:

- teste com usuário;
- pesquisa adicional;
- contrato;
- especialista;
- provider;
- política externa;
- validação técnica posterior.

Cada item deve indicar, quando possível, **em qual camada deverá ser resolvido**.

---

## 38. Relação com Pesquisa e Viabilidade

A Pesquisa pode recomendar:

```text
“o módulo X parece promissor após o core”
```

O Briefing pode decidir:

```text
“X será P1”
```

A Pesquisa pode indicar:

```text
“há risco regulatório relevante em Y”
```

O Briefing pode canonizar:

```text
“Y não entra no P0 sem Gate G”
```

Assim, a Pesquisa informa. O Briefing compromete o produto.

---

## 39. Relação com Product Owner

O Briefing não precisa responder como cada capacidade será entregue em detalhe.

A Visão de Product Owner será responsável por aprofundar, conforme aplicável:

- outcomes;
- perfis operacionais;
- jornadas funcionais de alto nível;
- capacidades priorizadas;
- épicos;
- regras de negócio mais detalhadas;
- critérios de aceite de produto;
- dependências funcionais;
- releases ou milestones de produto;
- rastreabilidade de requisitos.

Fluxo:

```text
BRIEFING
“o produto precisa permitir colaboração revogável”
        ↓
PRODUCT OWNER
“quem convida, quem aceita, quais permissões, quais estados e critérios?”
```

---

## 40. Relação com UX/UI

O Briefing pode fixar:

```text
“o core deve dominar a experiência”
“uma ação principal por contexto”
“módulo secundário não pode interromper a tarefa crítica”
```

Mas não deve fixar prematuramente:

```text
posição exata do botão
número final de abas
componente específico
cores definitivas
motion
wireflow detalhado
```

Essas decisões pertencem aos documentos de UX/UI, salvo quando uma restrição visual já for decisão de marca aprovada.

---

## 41. Relação com Engenharia, Tech Lead e Infraestrutura

O Briefing pode registrar:

```text
“sessão precisa tolerar perda de rede”
“módulo precisa poder ser desligado”
“dados sensíveis não podem vazar para analytics”
“histórico não pode ser reescrito silenciosamente”
```

Mas não deve escolher:

- arquitetura;
- banco;
- linguagem;
- framework;
- biblioteca;
- provider;
- região;
- CI;
- mecanismo de fila;
- ORM;
- tecnologia de observabilidade.

Essas decisões pertencem às camadas técnicas.

---

## 42. Conversão de recomendações técnicas da Pesquisa

Quando a Pesquisa trouxer uma recomendação concreta de tecnologia, o Briefing deve reescrevê-la como **necessidade ou dependência**, quando a tecnologia ainda não tiver sido escolhida pela camada responsável.

Exemplo:

```text
PESQUISA:
“Framework X suporta modo offline e é uma alternativa viável.”

BRIEFING:
“A tarefa crítica precisa permanecer utilizável em perda temporária de rede.”
```

Essa regra reduz acoplamento prematuro.

---

## 43. Inconsistências entre documentos

Se o Briefing encontrar conflito entre Discovery e Pesquisa:

```text
CONFLITO
        ↓
IDENTIFICAR A ORIGEM
        ↓
EXPLICAR AO HUMANO
        ↓
DECIDIR QUAL CAMADA PRECISA SER RECONCILIADA
        ↓
SÓ ENTÃO CONSOLIDAR O BRIEFING
```

O Briefing não deve esconder divergências para parecer definitivo.

---

## 44. Freeze de produto

A aprovação do Briefing cria um **Product Scope Freeze relativo ao horizonte definido**.

Isso significa:

- decisões de produto deixam de ser hipóteses livres;
- etapas seguintes devem respeitar o escopo;
- mudanças continuam possíveis;
- mudanças materiais precisam reconciliar o Briefing.

Não significa que o produto nunca mais pode mudar.

Significa que mudanças não podem acontecer silenciosamente.

---

## 45. Mudança material após aprovação

É material quando altera, por exemplo:

- público;
- promessa;
- core loop;
- P0/P1/P2;
- módulo principal;
- modelo de receita;
- risco aceito;
- dado sensível utilizado;
- ator com autoridade;
- dependência externa crítica;
- responsabilidade do produto;
- fora de escopo.

Mudanças desse tipo devem reconciliar o Briefing antes de continuarem sendo propagadas.

---

## 46. Como apresentar o Briefing antes da canonização

Antes de gerar o arquivo, o ChatGPT deve apresentar uma síntese revisável no chat contendo, no mínimo:

```text
DEFINIÇÃO DO PRODUTO
TESE CONSOLIDADA
PÚBLICO
PROMESSA
LOOP PRINCIPAL
HIERARQUIA DE VALOR
DECISÕES CONSOLIDADAS
P0
P1
P2
FORA DE ESCOPO
REGRAS CRÍTICAS DE PRODUTO
DEPENDÊNCIAS
MÉTRICAS
GATES
RISCOS ACEITOS
RISCOS NÃO ACEITOS
PENDÊNCIAS
READINESS PARA PRODUCT OWNER
```

O humano deve poder corrigir essa síntese antes da gravação.

---

## 47. Duas aprovações obrigatórias

Como nas etapas anteriores:

```text
APROVAÇÃO DO CONTEÚDO
        ↓
AUTORIZAÇÃO PARA CANONIZAR
```

Exemplo:

```text
“O briefing ficou correto. Ajuste apenas o P1.”
```

não autoriza gravação final ainda.

Exemplo:

```text
“Agora está aprovado. Gere o 02_Briefing_de_Produto_e_Escopo.md.”
```

autoriza canonização.

---

## 48. Estrutura recomendada do artefato de projeto

A saída canônica deve ser:

```text
02_Briefing_de_Produto_e_Escopo.md
```

Estrutura sugerida:

```text
---
document_id: DOC-02
status: canonical
version: 1.0.0
depends_on:
  - DOC-00
  - DOC-01
next_document: 03_Visao_de_Product_Owner.md
---

# Briefing de Produto e Escopo

## 1. Leitura executiva
## 2. Definição do produto
## 3. Decisões consolidadas
## 4. Tese e problema central
## 5. Público e stakeholders
## 6. JTBD / contexto de uso
## 7. Promessa e posicionamento
## 8. Pilares de produto
## 9. Loop principal
## 10. Hierarquia de valor
## 11. Escopo P0
## 12. Escopo P1
## 13. Escopo P2
## 14. Fora de escopo
## 15. Regras críticas de produto
## 16. Modelo de receita / sustentabilidade
## 17. Dependências externas
## 18. Qualidades esperadas do produto
## 19. Métricas
## 20. Gates
## 21. Riscos aceitos e não aceitos
## 22. Decisões pendentes
## 23. Definição de pronto para Product Owner
```

A estrutura pode ser adaptada ao produto sem perder a responsabilidade da etapa.

---

## 49. Definição de pronto do Briefing

O Briefing pode ser considerado suficientemente maduro quando:

- definição do produto está clara;
- problema central está coerente com a Pesquisa;
- público do horizonte atual está definido;
- promessa de valor está aprovada;
- loop principal está compreensível;
- hierarquia de valor está clara;
- P0/P1/P2 estão separados;
- fora de escopo está explícito;
- capacidades principais não dependem de decisões técnicas prematuras;
- dependências externas estão visíveis;
- métricas de produto estão registradas;
- gates materiais estão definidos;
- riscos aceitos e não aceitos estão explícitos;
- pendências possuem destino de resolução;
- o documento não contém contradições materiais conhecidas;
- o Product Owner pode consumi-lo sem reabrir a Pesquisa inteira.

---

## 50. Quality Gate do Briefing

Antes de propor canonização, o ChatGPT deve verificar:

- `00_Discovery.md` e `01_Pesquisa_e_Viabilidade.md` foram consumidos;
- o verdict da Pesquisa permite avanço;
- recomendações foram diferenciadas de decisões;
- decisões humanas relevantes foram preservadas;
- contradições foram apresentadas, não escondidas;
- a definição do produto não é slogan vazio;
- existe um core identificável;
- P0 não contém funcionalidades apenas por imitação competitiva;
- P1/P2 não são depósitos genéricos de “futuro”;
- fora de escopo está explícito;
- dependências externas não foram tratadas como garantias;
- requisitos de qualidade estão escritos como necessidade de produto, não solução técnica;
- stack e arquitetura não foram escolhidas prematuramente;
- gates são condições, não tarefas;
- riscos possuem postura definida;
- a próxima etapa está claramente indicada;
- o humano revisou e aprovou o conteúdo;
- a canonização foi explicitamente autorizada.

---

## 51. Anti-padrões

### Briefing como lista de features

Enumera funcionalidades sem explicar problema, promessa, hierarquia ou limites.

### Briefing como backlog

Cria dezenas de histórias de usuário antes da Visão de Product Owner.

### Briefing como arquitetura

Escolhe banco, framework, provider ou arquitetura definitiva.

### Briefing como wireframe

Decide componentes, posições e telas em detalhe antes das etapas de UX/UI.

### P0 infinito

Tudo que o usuário mencionou entra no beta sem critério de corte.

### P1 cemitério

Tudo que ficou de fora vai para P1 sem condição de entrada.

### Escopo sem fora de escopo

O documento diz o que entra, mas não protege o que foi explicitamente rejeitado.

### Dependência tratada como certeza

Assume aprovação de API, parceiro, licença ou contrato ainda inexistente.

### Requisito técnico disfarçado

Transforma uma necessidade de produto em escolha tecnológica precoce.

### Métricas de vaidade

Escolhe abertura, cliques ou tempo de tela sem relação causal com o valor principal.

### Gate como checklist de tarefa

Confunde “implementar X” com condição de qualidade ou avanço.

### Canonização sem revisão

Gera o arquivo definitivo assim que termina a proposta.

---

## 52. Handoff para Visão de Product Owner

A Visão de Product Owner deve iniciar consumindo integralmente:

```text
00_Discovery.md
01_Pesquisa_e_Viabilidade.md
02_Briefing_de_Produto_e_Escopo.md
```

O Briefing deve entregar ao PO:

```text
DEFINIÇÃO DO PRODUTO
PÚBLICO
PROMESSA
POSICIONAMENTO
CORE LOOP
HIERARQUIA DE VALOR
P0 / P1 / P2
FORA DE ESCOPO
REGRAS CRÍTICAS
DEPENDÊNCIAS
MÉTRICAS
GATES
RISCOS
PENDÊNCIAS
```

A Visão de Product Owner não deve rediscutir silenciosamente essas decisões.

Se precisar alterá-las, deve abrir reconciliação com o Briefing.

---

## 53. Gate para avançar

A etapa pode ser considerada concluída quando:

- o conteúdo foi apresentado ao humano;
- divergências foram discutidas;
- correções foram incorporadas;
- o humano aprovou o Briefing;
- o humano autorizou a canonização;
- `02_Briefing_de_Produto_e_Escopo.md` foi criado ou atualizado no destino definido;
- o documento está coerente com Discovery e Pesquisa;
- o escopo do horizonte atual está protegido contra reinterpretação silenciosa;
- a Visão de Product Owner pode começar sem reconstruir a definição do produto.

Somente então a próxima etapa é elegível:

```text
03 — Visão de Product Owner
```

---

## 54. Regra final da etapa

> **O Briefing não descreve tudo que o produto poderá ser. Ele fixa o produto que decidimos construir neste horizonte, preserva seus limites e entrega ao Product Owner um contrato de intenção que não pode ser reinterpretado silenciosamente.**

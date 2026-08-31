---
document_id: CASE-02-DOC-03
title: Visão de Product Owner — Site empresarial para climatização
status: canonical
version: 1.0.0
case_id: CASE-02-SITE-EMPRESARIAL
methodology_stage: visao-product-owner
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
next_document: Principios_de_UX_UI.md
product_readiness: SUFFICIENT
ready_for_codex: false
---

# Visão de Product Owner — Site empresarial para climatização

## 1. Propósito

Este documento transforma o produto aprovado no Briefing do Caso 02 em uma visão executável de produto, com outcomes, comportamentos, regras, hipóteses, jornadas, épicos, histórias, gates e critérios de produto suficientes para orientar UX/UI sem obrigar as etapas seguintes a reinterpretar o propósito do site.

A saída desta etapa ainda não autoriza implementação.

---

## 2. Missão do horizonte atual

> **Provar que pessoas que chegam à NorteSul por busca, indicação ou outro canal conseguem reconhecer rapidamente se a empresa atende sua necessidade, encontrar confiança suficiente para avançar e iniciar um contato comercial mensurável, enquanto a própria empresa consegue manter o conteúdo essencial atualizado sem depender do desenvolvedor.**

O valor possui duas faces inseparáveis:

```text
VALOR EXTERNO
visitante entende
→ confia
→ contata

+

VALOR INTERNO
empresa atualiza
→ mede
→ aprende
→ melhora
```

A missão não é “publicar todas as páginas do P0”.

---

## 3. Scope Freeze protegido

O Product Scope Freeze herdado permanece:

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

A Visão de Product Owner não adiciona nenhum desses módulos.

---

## 4. Personas comportamentais

### U1 — Visitante com necessidade de serviço relativamente imediata

**Papel:** persona primária de decisão.

Contexto típico:

```text
tenho uma necessidade
↓
quero saber se vocês resolvem
↓
quero confirmar região/confiança
↓
quero falar com alguém
```

Quando houver trade-off de hierarquia na experiência pública entre explicar a organização da empresa e ajudar alguém a reconhecer a solução para sua necessidade, a necessidade de U1 possui precedência.

Isso não torna o B2B secundário em valor comercial.

---

### U2 — Comprador empresarial

Busca fornecedor para manutenção preventiva, contratos, PMOC, múltiplos equipamentos ou operação empresarial mais estruturada.

Precisa de maior profundidade de contexto, capacidade e prova antes de avançar.

O produto deve servir esse contexto sem transformar toda a experiência pública em uma proposta corporativa densa.

---

### U3 — Administrativo / marketing

Mantém informações editoriais previstas.

Seu progresso é manter o site correto e atual sem depender de programação para alterações rotineiras.

---

### U4 — Comercial

Recebe e qualifica demanda.

Pode usar o site como referência durante atendimento e ajuda a distinguir contato de simples evento digital de lead comercial real.

---

### U5 — Proprietário / sponsor

Decide investimento, continuidade e evolução do produto.

Busca resultado comercial, confiança da marca e sustentabilidade operacional.

---

## 5. Anti-personas do horizonte atual

Anti-persona representa contexto não atendido neste produto, não uma pessoa indesejada.

### AP-01 — comprador que espera e-commerce

O produto não vende equipamentos online no horizonte atual.

### AP-02 — pessoa que espera agendamento automático

O produto não administra agenda operacional.

### AP-03 — cliente que espera portal de acompanhamento

O produto não oferece portal ou acompanhamento de ordem de serviço.

### AP-04 — operador que busca gerir execução técnica

O site não é ERP, CRM ou sistema de ordens de serviço.

---

## 6. Jobs to be Done

### JTBD-01 — Residencial

```text
QUANDO
eu tenho uma necessidade de climatização

QUERO
descobrir rapidamente se essa empresa atende
meu problema e minha região

PARA
decidir se vale iniciar contato
```

### JTBD-02 — Empresarial

```text
QUANDO
preciso avaliar uma empresa de climatização
para uma necessidade empresarial

QUERO
entender capacidade, serviços e experiência

PARA
decidir se devo solicitar uma conversa/proposta
```

### JTBD-03 — Indicação

```text
QUANDO
alguém me indica a NorteSul

QUERO
validar quem é a empresa e o que ela faz

PARA
sentir segurança antes de entrar em contato
```

### JTBD-04 — Administrativo

```text
QUANDO
serviço, região, case, foto ou informação mudar

QUERO
atualizar o conteúdo autorizado

PARA
manter o site correto sem depender de programação
```

### JTBD-05 — Comercial

```text
QUANDO
estou atendendo uma pessoa com dúvida específica

QUERO
usar o próprio site como referência confiável

PARA
reduzir explicações repetitivas e dar contexto
```

---

## 7. Outcomes

### OUT-001 — Clareza de aderência

Visitantes conseguem determinar rapidamente se a NorteSul atende sua necessidade.

**Evidência futura:** testes de compreensão e comportamento de navegação.

### OUT-002 — Confiança suficiente para avançar

Pessoas encontram provas adequadas antes da decisão de contato.

**Evidência futura:** testes qualitativos e comportamento subsequente.

### OUT-003 — Conversão comercial mensurável

O site passa a gerar contatos cujo início pode ser mensurado e, quando viável, relacionado à qualidade comercial.

### OUT-004 — Diferenciação B2C/B2B sem fragmentação

Residencial e empresarial encontram caminhos adequados dentro do mesmo produto.

### OUT-005 — Autonomia editorial

Conteúdo rotineiro previsto pode ser mantido pela empresa sem alteração de código.

### OUT-006 — Preservação e crescimento da descoberta digital

A migração não destrói ativos relevantes e o novo produto consegue participar adequadamente de busca/indexação.

### OUT-007 — Decisões orientadas por evidência

A empresa passa a compreender melhor:

```text
como o site é descoberto
↓
quais conteúdos geram interesse
↓
quais contatos começam no site
↓
quais desses contatos possuem qualidade comercial
```

### OUT-008 — Sustentabilidade operacional

O custo e o esforço contínuo permanecem proporcionais a uma pequena empresa regional.

---

## 8. Outcome Tree

```text
NEGÓCIO
├─ OUT-003 conversão mensurável
├─ OUT-007 capacidade de aprender
└─ OUT-008 operação sustentável

USUÁRIO
├─ OUT-001 clareza
├─ OUT-002 confiança
└─ OUT-004 caminho adequado por contexto

PRODUTO
├─ OUT-005 autonomia editorial
└─ OUT-006 preservação/descoberta digital
```

Pageviews, páginas por sessão e tempo de permanência não são outcomes por si mesmos.

---

## 9. North Star preliminar

### Taxa de Contato Comercial Qualificado — TCQ

```text
contatos atribuíveis ao site
que o comercial classifica como qualificados
/
sessões elegíveis
```

**Janela inicial de análise:** 30 dias móveis.

### Numerador

Contato originado ou atribuível ao site que posteriormente é reconhecido pelo comercial como demanda real compatível com os serviços atendidos.

### Denominador

Sessões consideradas elegíveis para análise de conversão.

A definição técnica de sessão pertence à instrumentação futura.

### Exclusões iniciais

Não contam automaticamente:

```text
spam
teste interno
envio duplicado
oferta comercial recebida
contato claramente fora dos serviços
contato fora da região quando inelegível
```

### Limitação

Essa métrica depende de uma ponte mínima entre evento digital e qualificação comercial.

Se essa ponte for operacionalmente desproporcional, a primeira proxy poderá ser uma taxa de início de contato, desde que o produto não trate todo clique como lead qualificado.

```text
NORTH_STAR_STATUS: PRELIMINARY
```

---

## 10. Guardrails

### GR-001 — Verdade comercial

Aumentar conversão usando afirmação enganosa não é sucesso.

### GR-002 — Privacidade

Mais dados coletados não significam melhor produto.

### GR-003 — Acessibilidade

Conversão não pode depender de experiência inacessível.

### GR-004 — Performance

Elementos de marketing não podem degradar materialmente o caminho principal.

### GR-005 — Ativos digitais

Melhoria visual não justifica perder domínio, URLs, e-mail ou sinais digitais relevantes.

### GR-006 — Operação editorial

Não criar estrutura editorial que a empresa não consiga manter.

### GR-007 — Regulatório

Conteúdo relacionado a PMOC não pode simplificar obrigação legal/técnica de forma materialmente enganosa.

### GR-008 — Ausência de dupla operação

Administrar o site não deve exigir atualizar desnecessariamente a mesma informação em múltiplos lugares sob controle do próprio produto.

### GR-009 — Conversão sem dark pattern

CTA, formulário ou consentimento não podem manipular a pessoa para melhorar uma métrica.

### GR-010 — Core independente de analytics

Navegação, leitura e contato permanecem funcionais mesmo se mensuração externa falhar.

---

## 11. Hipóteses de produto

### HYP-001 — Clareza aumenta progressão

Se serviços e região estiverem claros cedo, visitantes relevantes avançarão com menos incerteza.

### HYP-002 — Prova aumenta confiança

Cases, experiência e evidências reais melhoram confiança mais que slogans genéricos.

### HYP-003 — WhatsApp continua sendo melhor contato rápido

Para demanda residencial, um caminho direto ao WhatsApp reduz fricção.

### HYP-004 — B2B se beneficia de contato estruturado

Compradores empresariais fornecem contexto melhor quando existe uma solicitação estruturada além do WhatsApp.

### HYP-005 — Autonomia editorial será realmente utilizada

O administrativo conseguirá manter serviços, região, cases e demais conteúdos previstos sem depender do desenvolvedor.

### HYP-006 — Mensuração gera decisões melhores

A empresa utilizará dados de descoberta/conversão para decidir o que otimizar.

### HYP-007 — Conteúdo local e de serviço contribui para descoberta

Conteúdo específico e útil participa do crescimento de descoberta orgânica/local ao longo do tempo.

### HYP-008 — Meta de 15–20 leads pode se tornar plausível

Tráfego qualificado multiplicado pela conversão poderá aproximar o site da expectativa comercial.

A hipótese permanece não comprovada.

### HYP-009 — Operação editorial enxuta é suficiente

A empresa não precisa de uma operação de publicação intensa para manter valor no primeiro horizonte.

---

## 12. Condições de retirada e redução

Uma capacidade não adquire direito de permanência apenas porque foi construída.

### Formulário B2B

Se quase ninguém o utiliza e o WhatsApp captura melhor a intenção empresarial sem perda material de qualidade, simplificar ou retirar.

### Conteúdo recorrente / blog

Se não existir owner editorial ou não produzir aprendizado/valor, não expandir.

### Campo extra de formulário

Se não melhora qualificação ou roteamento, remover.

### Página local específica

Se não existir atuação real e conteúdo útil, não publicar apenas para captura de busca.

---

## 13. Ordem de aprendizado

A prioridade deste produto representa principalmente ordem de aprendizado:

```text
1. conseguimos explicar serviço + região?
2. conseguimos gerar confiança?
3. o caminho de contato funciona?
4. B2C e B2B precisam de quais diferenças reais?
5. a empresa consegue atualizar o conteúdo?
6. conseguimos medir descoberta → contato?
7. a presença digital melhora com o tempo?
8. qual expansão realmente merece investimento?
```

A ordem não é determinada pela posição futura de uma página na navegação.

---

## 14. Jornadas de valor

### J-001 — Resolver necessidade residencial

**Entrada:** visitante com necessidade concreta.

```text
descoberta
↓
serviço
↓
região
↓
confiança
↓
contato rápido
```

**Sucesso:** contato iniciado com contexto suficiente.

**Limite:** o site não agenda nem executa o atendimento.

---

### J-002 — Avaliar fornecedor empresarial

```text
descoberta
↓
capacidade empresarial
↓
serviços / PMOC
↓
provas
↓
solicitação de contato/proposta
```

**Sucesso:** empresa inicia contato suficientemente contextualizado.

---

### J-003 — Validar indicação

```text
nome da empresa recebido
↓
busca
↓
site
↓
empresa / serviço / prova
↓
contato
```

**Sucesso:** visitante valida aderência/confiança e toma decisão informada de contato.

---

### J-004 — Explorar trabalho realizado

```text
necessidade
↓
case relevante
↓
prova de capacidade
↓
serviço
↓
contato
```

Case participa da decisão; não é apenas galeria decorativa.

---

### J-005 — Atualizar conteúdo

```text
informação mudou
↓
usuário interno acessa área editorial
↓
altera conteúdo permitido
↓
revisa
↓
publica
↓
site reflete atualização
```

---

### J-006 — Aprender com a operação

```text
site recebe tráfego
↓
ações são medidas
↓
comercial qualifica contatos
↓
empresa interpreta resultado
↓
decide melhoria
```

---

## 15. Regras de negócio vinculantes

### BR-001 — Escopo

O produto não executa funções de CRM, ERP, ordem de serviço, e-commerce ou portal no horizonte atual.

### BR-002 — Região

Somente regiões efetivamente atendidas podem ser apresentadas como área de atuação.

### BR-003 — Serviço

Conteúdo só pode afirmar serviço/capacidade que a empresa realmente oferece.

### BR-004 — PMOC

Conteúdo técnico/regulatório sensível precisa possuir revisão adequada antes da publicação.

### BR-005 — WhatsApp

Contato rápido via WhatsApp permanece capacidade P0.

### BR-006 — Contato empresarial

Contato estruturado complementa WhatsApp e deve coletar somente contexto comercial necessário.

### BR-007 — Autonomia editorial

Conteúdos definidos como editáveis no P0 não podem exigir alteração de código para atualização rotineira.

### BR-008 — Publicação

Somente usuário autorizado pode publicar ou alterar conteúdo administrativo.

### BR-009 — Mensuração não bloqueia core

Falha de analytics/tracking não pode bloquear navegação, leitura ou contato.

### BR-010 — Dados pessoais

Formulário deve minimizar coleta conforme finalidade.

### BR-011 — Avaliações

Depoimento ou avaliação externa precisa preservar origem/contexto suficiente para não parecer declaração fabricada.

### BR-012 — Local SEO

Não criar páginas de cidades sem conteúdo e atuação legítimos apenas para capturar busca.

### BR-013 — Migração

Domínio, DNS, e-mail e URLs relevantes não podem ser alterados ou descartados sem avaliação explícita.

### BR-014 — Promessas

Produto não pode afirmar garantia de ranking, quantidade de leads ou vendas.

### BR-015 — B2C/B2B

Residencial e empresarial pertencem ao mesmo produto, mas podem exigir profundidades diferentes de informação e contato.

### BR-016 — Conteúdo editorial

Publicação recorrente só deve existir quando houver owner e finalidade reconhecível.

### BR-017 — Analytics

Eventos de mensuração não devem carregar conteúdo livre ou dado pessoal sem necessidade/finalidade aprovada.

### BR-018 — Contato alternativo

Falha de um mecanismo de contato específico não deve remover silenciosamente todas as formas de contato permitidas quando houver alternativa aprovada.

---

## 16. Épicos

### E-001 — Descoberta e serviços

Tornar clara a aderência da empresa à necessidade.

### E-002 — Confiança e prova

Demonstrar capacidade sem depender de slogans.

### E-003 — Conversão comercial

Levar visitante ao canal adequado.

### E-004 — Experiência empresarial

Atender necessidades de avaliação B2B.

### E-005 — Operação editorial

Manter conteúdo atualizado com autonomia.

### E-006 — Descoberta digital e mensuração

Tornar aquisição, indexação e conversão mensuráveis.

### E-007 — Governança digital

Preservar ativos, privacidade, conteúdo e migração.

---

## 17. Baseline de histórias de produto

### E-001 — Descoberta e serviços

#### US-001 — Reconhecer rapidamente a oferta

**Como** visitante,  
**quero** entender o que a NorteSul faz,  
**para** saber se devo continuar.

**Prioridade:** MUST CORE  
**Outcomes:** OUT-001

**Aceite de produto:** pessoa que não conhece a empresa consegue explicar corretamente quais necessidades principais ela atende sem orientação externa.

---

#### US-002 — Confirmar região atendida

**Como** visitante,  
**quero** saber se minha localidade é atendida,  
**para** não iniciar contato inútil.

**Prioridade:** MUST CORE  
**Outcomes:** OUT-001

**Aceite de produto:** região comunicada não contradiz a operação aprovada.

---

#### US-003 — Entender um serviço residencial

**Como** cliente residencial,  
**quero** compreender o serviço relevante,  
**para** decidir se devo pedir atendimento.

**Prioridade:** MUST CORE  
**Outcomes:** OUT-001, OUT-003

---

### E-002 — Confiança e prova

#### US-004 — Conhecer a empresa na medida necessária

**Como** visitante,  
**quero** entender quem está por trás do serviço,  
**para** avaliar confiança.

**Prioridade:** MUST CORE  
**Outcomes:** OUT-002

---

#### US-005 — Ver trabalhos realizados

**Como** visitante,  
**quero** visualizar trabalhos/cases relevantes,  
**para** avaliar capacidade prática.

**Prioridade:** MUST CORE  
**Outcomes:** OUT-002

---

#### US-006 — Ver prova social aprovada

**Como** visitante,  
**quero** encontrar avaliações ou depoimentos contextualizados,  
**para** reduzir incerteza.

**Prioridade:** MUST CORE  
**Outcomes:** OUT-002

---

### E-003 — Conversão comercial

#### US-007 — Iniciar contato rápido

**Como** visitante com necessidade simples/imediata,  
**quero** iniciar contato pelo WhatsApp,  
**para** continuar o atendimento sem fricção.

**Prioridade:** MUST CORE  
**Outcomes:** OUT-003

**Aceite de produto:** visitante consegue iniciar o canal previsto a partir de contexto relevante sem ser obrigado a preencher formulário.

---

#### US-008 — Solicitar contato estruturado

**Como** visitante com necessidade mais complexa,  
**quero** informar contexto suficiente,  
**para** que o comercial consiga retornar melhor preparado.

**Prioridade:** MUST CORE  
**Outcomes:** OUT-003, OUT-004

**Aceite de produto:** coleta somente informação aprovada como necessária; falha no formulário não bloqueia WhatsApp quando esse canal for aplicável.

---

#### US-009 — Encontrar resposta para dúvida recorrente

**Como** visitante,  
**quero** encontrar respostas úteis para dúvidas comuns,  
**para** decidir se ainda preciso falar com alguém.

**Prioridade:** SHOULD no core inicial, promovível a MUST se conteúdo real justificar.  
**Outcomes:** OUT-001, OUT-003

---

### E-004 — Experiência empresarial

#### US-010 — Entender capacidade B2B

**Como** comprador empresarial,  
**quero** compreender os serviços empresariais oferecidos,  
**para** avaliar aderência da NorteSul.

**Prioridade:** MUST CORE  
**Outcomes:** OUT-004

---

#### US-011 — Entender oferta relacionada a PMOC

**Como** comprador empresarial,  
**quero** compreender o que a empresa oferece relacionado a PMOC,  
**para** decidir se devo solicitar avaliação/proposta.

**Prioridade:** MUST GATE  
**Outcomes:** OUT-004  
**Gate:** G-007.

---

#### US-012 — Solicitar proposta empresarial

**Como** comprador empresarial,  
**quero** iniciar uma conversa fornecendo contexto comercial útil,  
**para** reduzir retrabalho no primeiro atendimento.

**Prioridade:** MUST CORE  
**Outcomes:** OUT-003, OUT-004

---

### E-005 — Operação editorial

#### US-013 — Atualizar informação comercial

**Como** usuário editorial autorizado,  
**quero** alterar conteúdo previsto,  
**para** manter informação correta sem desenvolvedor.

**Prioridade:** MUST CORE  
**Outcomes:** OUT-005

**Aceite de produto:** usuário editorial altera e publica conteúdo previsto sem modificação de código.

---

#### US-014 — Publicar case

**Como** usuário editorial,  
**quero** registrar trabalho realizado aprovado,  
**para** manter a prova de capacidade atualizada.

**Prioridade:** MUST CORE  
**Outcomes:** OUT-002, OUT-005

---

#### US-015 — Atualizar região e FAQ

**Como** usuário editorial,  
**quero** manter informações operacionais previstas,  
**para** evitar divergência entre site e operação real.

**Prioridade:** MUST CORE  
**Outcomes:** OUT-005

---

### E-006 — Descoberta digital e mensuração

#### US-016 — Possibilitar descoberta orgânica

**Como** empresa,  
**quero** que conteúdo público relevante possa ser corretamente descoberto/indexado,  
**para** participar da aquisição orgânica.

**Prioridade:** MUST CORE  
**Outcomes:** OUT-006

---

#### US-017 — Medir início de contato

**Como** proprietário/comercial,  
**quero** saber quais ações de contato começaram no site,  
**para** avaliar sua contribuição comercial.

**Prioridade:** MUST GATE  
**Outcomes:** OUT-003, OUT-007  
**Gate:** G-005.

---

#### US-018 — Avaliar desempenho orgânico

**Como** responsável pelo produto,  
**quero** interpretar descoberta orgânica por página, consulta e contexto disponível,  
**para** decidir otimizações.

**Prioridade:** MUST CORE em operação  
**Outcomes:** OUT-006, OUT-007

---

### E-007 — Governança digital

#### US-019 — Preservar ativos na migração

**Como** proprietário,  
**quero** substituir o legado sem perder ativos digitais relevantes,  
**para** não destruir valor acumulado.

**Prioridade:** MUST GATE  
**Outcomes:** OUT-006  
**Gate:** G-006.

**Aceite de produto:** nenhum ativo digital relevante é alterado sem inventário, decisão e plano correspondente.

---

#### US-020 — Comunicar tratamento de dados

**Como** visitante,  
**quero** compreender de forma adequada a coleta feita nos fluxos correspondentes,  
**para** tomar decisões informadas.

**Prioridade:** MUST GATE  
**Outcomes:** OUT-003, OUT-007  
**Gate:** G-005.

---

## 18. Estados críticos conhecidos no nível de produto

As etapas de UX/UI devem detalhar a representação, mas o PO já reconhece:

- serviço não disponível;
- região não atendida;
- case removido/não publicado;
- formulário inválido;
- formulário indisponível;
- WhatsApp indisponível ou canal não configurado;
- consentimento/medição não habilitado;
- tracker indisponível;
- conteúdo em revisão;
- usuário editorial sem permissão;
- publicação falhou;
- ativo legado não inventariado;
- conteúdo PMOC aguardando revisão;
- spam ou envio repetido.

---

## 19. Scorecard inicial

| Área | Indicador | Target inicial | Guardrail |
| --- | --- | --- | --- |
| Clareza | teste de entendimento | maioria da amostra compreende serviço/região sem ajuda | sem esconder limitações |
| Contato | início de contato | baseline → melhoria a medir | sem dark pattern |
| Qualidade | contatos qualificados | estabelecer baseline | não maximizar spam |
| Editorial | tarefas sem dev | tarefas P0 concluíveis internamente | não liberar acesso excessivo |
| Performance | experiência mobile | alvo técnico posterior | marketing não degrada core |
| Descoberta | impressões/cliques | baseline e tendência | sem conteúdo artificial |
| Privacidade | coleta | somente finalidade aprovada | conversão não justifica excesso |

Targets quantitativos finais permanecem hipóteses até existir baseline.

---

## 20. Experimentos

### EXP-001 — Baseline digital

Antes de substituir um legado real, medir ativos e desempenho existentes quando disponíveis.

**Alimenta:** OUT-006, OUT-007.

### EXP-002 — Teste de clareza

Pessoa recebe versão/protótipo sem explicação e precisa responder:

```text
o que a empresa faz?
atende o que eu preciso?
onde atende?
qual seria meu próximo passo?
```

**Alimenta:** HYP-001.

### EXP-003 — Confiança

Comparar qualitativamente comunicação genérica contra comunicação sustentada por cases/provas.

**Alimenta:** HYP-002.

### EXP-004 — Conversão mobile

Testar jornadas residenciais e empresariais em celular.

**Alimenta:** HYP-003, HYP-004.

### EXP-005 — Autonomia editorial

Usuário administrativo precisa concluir sem ajuda tarefas como atualizar região, alterar informação prevista e publicar case.

**Alimenta:** HYP-005, HYP-009.

### EXP-006 — Primeiros 90 dias

Após lançamento real:

```text
descoberta
→ visita
→ contato
→ qualificação
```

**Alimenta:** HYP-006, HYP-007, HYP-008.

---

## 21. Instrumentação semântica

Sem escolher ferramenta:

```text
service_viewed
business_services_viewed
case_viewed
whatsapp_contact_started
quote_request_started
quote_request_submitted
contact_error
editorial_content_published
```

Quando existir integração comercial futura:

```text
lead_qualified
```

pode ser necessário.

Eventos não devem copiar automaticamente para analytics:

- mensagem completa;
- telefone;
- e-mail;
- conteúdo livre;
- dados integrais do formulário.

---

## 22. Ondas de liberação

### Onda 0 — Prova interna

**Público:** proprietário, comercial, administrativo e testadores controlados.

**Objetivo:** clareza, conteúdo, confiança, mobile, autonomia editorial e migração.

### Onda 1 — Soft launch

Publicação controlada sem declarar sucesso comercial.

**Objetivo:** provar operação real, indexação, contato, tracking e erros.

### Onda 2 — Lançamento público

Migração/consolidação completa da presença web após gates.

### Onda 3 — Janela de aprendizado

Primeiros aproximadamente 90 dias de operação mensurada.

```text
estabelecer baseline real
↓
identificar gargalos
↓
decidir P1
```

Onda não é sprint.

---

## 23. Gates vinculantes

### G-001 — Ownership digital

**Condição:** domínio, DNS, e-mail, Google e demais ativos relevantes estão inventariados e possuem owner/acesso conhecido.  
**Owner:** proprietário / responsável digital.  
**Evidência:** inventário de ativos e acessos.  
**Falha:** HOLD.

### G-002 — Clareza comercial

**Condição:** visitante de teste consegue reconhecer serviço, aderência, região e próximo passo sem orientação externa relevante.  
**Owner:** Product Owner.  
**Evidência:** EXP-002.  
**Falha:** PIVOT de conteúdo/hierarquia.

### G-003 — Confiança

**Condição:** principais claims de capacidade possuem sustentação adequada.  
**Owner:** proprietário/comercial.  
**Evidência:** inventário/revisão das provas.  
**Falha:** HOLD da publicação correspondente.

### G-004 — Autonomia editorial

**Condição:** usuário interno consegue realizar tarefas editoriais P0 sem desenvolvedor.  
**Owner:** responsável administrativo.  
**Evidência:** EXP-005.  
**Falha:** PIVOT de modelo editorial/plataforma.

### G-005 — Privacidade e mensuração

**Condição:** formulários, eventos e trackers possuem finalidade, coleta e comportamento aprovados.  
**Owner:** produto + responsável por privacidade.  
**Evidência:** revisão de finalidade/coleta.  
**Falha:** tracker/form correspondente permanece desligado ou reduzido.

### G-006 — Migração

**Condição:** URLs, domínio, e-mail, indexação e demais ativos relevantes foram verificados antes da troca.  
**Owner:** responsável técnico + proprietário.  
**Evidência:** inventário + plano + recuperação/rollback aplicável.  
**Falha:** HOLD do lançamento.

### G-007 — PMOC

**Condição:** comunicação regulatória/técnica sensível foi revisada adequadamente.  
**Owner:** responsável por conteúdo + revisor adequado.  
**Evidência:** revisão registrada.  
**Falha:** conteúdo não publica.

### G-008 — Aprendizado comercial

**Condição:** existe janela suficiente de operação para avaliar descoberta → contato → qualidade.  
**Owner:** proprietário + PO.  
**Momento:** após janela suficiente de operação.  
**Decisão:** GO / GO LIMITADO / HOLD / PIVOT / KILL conforme evidência.

---

## 24. Tratamento da meta de 15–20 leads

A expectativa permanece sob `HYP-008`.

```text
15–20 LEADS/MÊS
= AMBIÇÃO / HIPÓTESE COMERCIAL

!=
CRITÉRIO DE ACEITE DO SOFTWARE

!=
GARANTIA
```

Antes de interpretar a meta, o negócio precisa conhecer:

```text
tráfego qualificado
+
intenção
+
conversão
+
qualidade do contato
```

---

## 25. Definition of Ready de produto

Uma capacidade só está pronta para UX/UI quando consegue responder, quando aplicável:

- qual `OUT-*` origina a necessidade;
- qual persona/contexto;
- qual JTBD/jornada;
- qual regra de negócio;
- qual comportamento demonstra valor;
- qual conteúdo é necessário;
- se existe dado pessoal;
- se existe claim sensível;
- se existe dependência externa;
- qual gate;
- o que está fora do recorte.

```text
READY_DE_PRODUTO
!=
READY_FOR_CODEX
```

---

## 26. Definition of Done de produto

Uma entrega só poderá ser considerada Done no nível de produto quando, conforme aplicável:

```text
comportamento aprovado existe
+
regra de produto foi preservada
+
estados críticos foram considerados
+
conteúdo possui owner
+
claim possui sustentação
+
métrica necessária existe
+
guardrail não foi violado
+
evidência de aceite foi registrada
```

Publicar uma página não significa automaticamente gerar valor.

---

## 27. Política de mudança

Nova necessidade deve ser classificada antes de entrar no produto.

```text
NOVA IDEIA
↓
PERTENCE AO CORE ATUAL?
├─ NÃO → P1/P2/OUT
└─ SIM → CONTRADIZ SCOPE FREEZE?
          ├─ NÃO → avaliar hipótese/outcome/gate
          └─ SIM → reabrir Briefing
```

UX/UI não possui autoridade para incluir módulo novo por conveniência de navegação ou composição.

---

## 28. Revisão simulada

### Proprietário

> Quem está procurando serviço precisa encontrar rápido. Mas empresa também precisa ter um caminho claro e legítimo.

Confirma a precedência de U1 sem remover U2 do P0.

### Comercial

> Prefiro receber menos campos, mas informações que realmente ajudem no atendimento.

Confirma `HYP-004` e `BR-006`.

### Administrativo

> Case provavelmente será o conteúdo que mais vamos atualizar, porque sempre temos trabalho novo.

Confirma a importância de `US-014`, sem definir formato visual ou CMS.

### Proprietário

> Depois de alguns meses quero conseguir enxergar se a mudança melhorou alguma coisa.

Confirma `OUT-007`, `EXP-006` e `G-008`.

---

## 29. Validação da metodologia

A etapa preservou a separação:

```text
OUTCOME
“visitante entende se a empresa atende”
↓
COMPORTAMENTO
“reconhece serviço/região e avança”
↓
ENTREGA
“capacidade/conteúdo correspondente”
```

Em vez de começar pela decisão arbitrária de criar determinada página.

Também preservou a cadeia:

```text
BRIEFING
“autonomia editorial”
↓
PO
US-013 / US-014 / US-015
↓
UX/UI
ainda decidirá como operar/perceber
↓
TECH LEAD
ainda decidirá a plataforma
```

Resultado:

```text
PO_METHOD_VALIDATION: PASS
PRODUCT_SCOPE_CHANGED: NO
MISSION: DEFINED
PRIMARY_DECISION_PERSONA: DEFINED
JTBD: DEFINED
OUTCOMES: DEFINED
NORTH_STAR: PRELIMINARY_DEFINED
GUARDRAILS: DEFINED
HYPOTHESES: DEFINED
LEARNING_ORDER: DEFINED
JOURNEYS: DEFINED
BUSINESS_RULES: DEFINED
EPICS: 7
PRODUCT_STORIES: 20
EXPERIMENTS: 6
RELEASE_WAVES: 4
PRODUCT_GATES: 8
INSTRUMENTATION_SEMANTICS: DEFINED
PRODUCT_DOR: DEFINED
PRODUCT_DOD: DEFINED
CMS_SELECTED: NO
TECH_STACK_SELECTED: NO
UX_LAYOUT_SELECTED: NO
PRODUCT_READINESS: SUFFICIENT
READY_FOR_CODEX: NO
```

---

## 30. Handoff

```text
PRODUCT_OWNER_EXECUTION: COMPLETE
PRODUCT_SCOPE_FREEZE: PRESERVED
PRODUCT_READINESS: SUFFICIENT
READY_FOR_CODEX: NO
NEXT_STAGE: Principios_de_UX_UI.md
```

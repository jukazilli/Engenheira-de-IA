---
document_id: PROCESS-01-PESQUISA-VIABILIDADE
title: Pesquisa e Viabilidade
status: draft-methodology
version: 0.1.0
stage: pesquisa-e-viabilidade
consumes: 00_Discovery.md
produces: 01_Pesquisa_e_Viabilidade.md
next_stage: Briefing de Produto e Escopo
---

# 01 — Pesquisa e Viabilidade

## 1. Propósito

A **Pesquisa e Viabilidade** é a segunda etapa operacional do Processo de Desenvolvimento de Software com IA Assistida.

Sua função é confrontar a intenção registrada no `00_Discovery.md` com o mundo real para responder, com evidências e incertezas explícitas:

> **Existe base suficiente para continuar investindo nesta ideia e, se sim, sob quais condições, recortes, riscos e hipóteses de validação?**

Esta etapa não existe para confirmar a ideia do usuário a qualquer custo.

Ela existe para reduzir ilusão de produto, antecipar riscos, identificar concorrência, testar coerência da proposta, investigar restrições técnicas e operacionais, levantar exigências regulatórias, analisar ativos existentes e produzir uma recomendação responsável antes de o Briefing transformar a ideia em escopo de produto.

A saída esperada é um relatório de investigação que permita ao humano decidir entre avançar, avançar com condições, pesquisar mais ou interromper a iniciativa.

---

## 2. Posição no processo

```text
00_Discovery.md aprovado
        ↓
PESQUISA E VIABILIDADE
        ↓
01_Pesquisa_e_Viabilidade.md
        ↓
BRIEFING DE PRODUTO E ESCOPO
```

O Discovery descreve **o que o humano acredita que quer criar**.

A Pesquisa e Viabilidade investiga **o que as evidências disponíveis permitem afirmar sobre essa ideia**.

O Briefing será responsável por transformar o que sobreviveu à investigação em um recorte de produto mais estável.

---

## 3. Origem desta etapa

A estrutura desta metodologia foi extraída do processo realmente utilizado no DayGym, no qual a Pesquisa e Viabilidade funcionou como investigação pré-Briefing e reuniu, em um único estudo, leitura executiva, tese de produto, desejabilidade, viabilidade técnica, viabilidade de negócio, risco regulatório, público, concorrentes, problemas priorizados, oportunidades, escopo recomendado, jornadas, integrações, UX, riscos, métricas, gates e decisões em aberto.

O processo reutilizável preserva essa profundidade, mas separa com mais rigor três tipos de resultado:

```text
EVIDÊNCIA
→ o que foi observado em fontes ou materiais

INFERÊNCIA / RECOMENDAÇÃO
→ leitura produzida a partir dessas evidências

DECISÃO CANÔNICA
→ só existe depois de aprovação humana
```

A pesquisa pode recomendar arquitetura, tecnologia, UX ou escopo preliminarmente quando isso for necessário para avaliar viabilidade, mas **não deve transformar essas recomendações em decisões canônicas das camadas posteriores**.

---

## 4. Pré-requisito obrigatório

A etapa deve começar consumindo integralmente o `00_Discovery.md` aprovado.

Antes de pesquisar, o ChatGPT deve identificar no Discovery:

- tese inicial;
- problema ou oportunidade percebida;
- usuários e stakeholders imaginados;
- situações de uso conhecidas;
- outcomes esperados;
- capacidades centrais imaginadas;
- limites preliminares;
- restrições conhecidas;
- ativos e referências existentes;
- decisões confirmadas;
- hipóteses;
- pendências;
- alternativas descartadas;
- perguntas explícitas para investigação.

Se o documento estiver ausente, incompleto ou contraditório a ponto de impedir uma investigação responsável, a Pesquisa e Viabilidade deve ser bloqueada e o fluxo deve retornar ao Discovery.

---

## 5. Como acionar a etapa

Depois que o Discovery estiver aprovado e canonizado, o usuário pode solicitar:

```text
Faça a Pesquisa e Viabilidade com base no Discovery aprovado.
```

Ou, de forma mais explícita:

```text
Consuma integralmente o 00_Discovery.md deste projeto e execute a etapa 01 — Pesquisa e Viabilidade conforme o processo canônico.
Primeiro apresente a análise no chat para minha revisão. Não gere o documento final ainda.
```

A segunda forma é recomendada quando a sessão foi retomada depois de algum tempo ou quando existe risco de perda de contexto.

---

## 6. Regra de ativação da pesquisa

Ao iniciar a etapa, o ChatGPT deve:

1. confirmar qual versão da metodologia está ativa;
2. localizar e ler o documento de Discovery do projeto;
3. recuperar os materiais de apoio citados no Discovery;
4. identificar quais perguntas exigem pesquisa externa;
5. separar o que é fato fornecido pelo usuário do que é hipótese;
6. planejar a investigação por temas;
7. pesquisar antes de propor conclusões materiais;
8. registrar incerteza quando a evidência for insuficiente;
9. não gerar o `.md` canônico antes da revisão humana.

Handshake recomendado:

```text
PROCESS_STATUS: ACTIVE
CURRENT_STAGE: PESQUISA_E_VIABILIDADE
INPUT_DOCUMENT: 00_Discovery.md
RESEARCH_STATUS: IN_PROGRESS
CANONICAL_OUTPUT: 01_Pesquisa_e_Viabilidade.md
NEXT_STAGE: Briefing de Produto e Escopo
```

---

## 7. Pergunta central e subperguntas

A pergunta central é:

> **A ideia possui fundamento suficiente para avançar, e qual é o recorte mais responsável para continuar?**

A investigação normalmente precisa responder um subconjunto relevante das seguintes perguntas:

### Produto e problema

- O problema parece real ou apenas imaginado?
- Ele ocorre com frequência suficiente para justificar um produto?
- Há evidência de fricção, retrabalho, custo, risco ou insatisfação?
- O problema já é resolvido por meios informais?
- O valor esperado pelo usuário é coerente com o problema?

### Público

- Quem apresenta o problema com maior intensidade?
- Em quais contextos ele aparece?
- Quem usa, quem paga, quem administra e quem pode bloquear a adoção?
- Existem segmentos com necessidades radicalmente diferentes?

### Mercado e concorrência

- Já existem soluções equivalentes?
- Qual é o centro de cada concorrente relevante?
- Onde eles são fortes?
- Quais lacunas parecem reais e quais são apenas diferenças superficiais?
- A ideia compete diretamente, complementa ou substitui processos manuais?

### Viabilidade técnica

- As capacidades centrais são tecnicamente possíveis com tecnologia madura?
- Existem dependências de APIs, dispositivos, plataformas ou provedores externos?
- Há limites de latência, offline, sincronização, volume, mídia ou integração?
- Existem dependências técnicas que podem bloquear o produto?

### Negócio e operação

- Existe um caminho plausível de geração de valor econômico ou operacional?
- O modelo depende de escala, parceiros, marketplace, comissão, vendas complexas ou suporte intenso?
- Existem custos ou processos humanos relevantes?
- Há risco de o produto exigir operação incompatível com a equipe disponível?

### Regulatório, segurança e confiança

- O produto lida com dados pessoais ou sensíveis?
- Existe atividade regulamentada?
- Há risco jurídico, financeiro, de saúde, conteúdo gerado por usuário ou marketplace?
- Existem políticas de app stores, marketplaces, publicidade ou terceiros que limitam o modelo?

### Experiência e adoção

- Quais são os pontos de maior atrito na jornada atual?
- Qual ação precisa gerar o primeiro valor rapidamente?
- Existem telas, processos ou produtos existentes que possam ser auditados?
- O produto corre risco de excesso de funcionalidades, densidade ou carga cognitiva?

### Validação

- Quais hipóteses são críticas antes de código de produção?
- Quais entrevistas, testes, POCs ou pilotos poderiam reduzir maior incerteza?
- Quais métricas permitiriam confirmar ou enfraquecer a tese?

---

## 8. A profundidade é proporcional ao risco

Nem todo projeto precisa da mesma quantidade de pesquisa.

A etapa deve ajustar profundidade conforme:

- novidade do problema;
- custo potencial de implementação;
- grau de regulamentação;
- uso de dados sensíveis;
- dependência de terceiros;
- necessidade de marketplace ou rede;
- criticidade da segurança;
- complexidade da operação;
- quantidade de stakeholders;
- irreversibilidade de decisões futuras.

Um aplicativo interno simples pode exigir uma investigação compacta.

Um produto de saúde, finanças, marketplace, comunidade aberta ou sistema que dependa de APIs comerciais pode exigir pesquisa extensa e múltiplas fontes primárias.

---

## 9. Pesquisa web é parte obrigatória quando a resposta envelhece

A Pesquisa e Viabilidade não deve depender apenas da memória do modelo quando a decisão envolver informação mutável.

Pesquisa atual é obrigatória para temas como:

- concorrentes e funcionalidades atuais;
- preços e planos;
- políticas de plataformas;
- APIs e SDKs;
- limites técnicos;
- versões de frameworks ou runtimes;
- disponibilidade regional;
- termos de programas parceiros;
- regras de app stores;
- legislação, regulamentação e orientações oficiais;
- licenças de dados ou software;
- requisitos de segurança;
- condições comerciais.

A data da investigação deve ser registrada no documento final quando a informação for temporalmente sensível.

---

## 10. Hierarquia de fontes

Fontes devem ser utilizadas de acordo com o tipo de afirmação.

### Nível 1 — fontes primárias / oficiais

Preferidas para:

- capacidades de produto;
- documentação técnica;
- políticas;
- preços;
- limites;
- legislação;
- requisitos de integração;
- termos de uso;
- segurança;
- suporte de plataforma.

Exemplos:

- documentação oficial;
- páginas oficiais de produto;
- leis e órgãos reguladores;
- termos oficiais;
- changelogs;
- documentação de APIs;
- políticas de app stores.

### Nível 2 — fontes técnicas ou institucionais confiáveis

Úteis para:

- comparação;
- estudos acadêmicos;
- análises setoriais;
- padrões de UX;
- benchmarks técnicos;
- evidência científica.

### Nível 3 — materiais fornecidos pelo usuário

Podem incluir:

- telas;
- processos internos;
- PDFs;
- planilhas;
- wireframes;
- briefings antigos;
- relatórios;
- dados operacionais;
- reclamações de clientes;
- produtos legados.

Esses materiais são evidência direta do contexto do projeto, mas não provam automaticamente comportamento de mercado.

### Nível 4 — comunidades e relatos públicos

São úteis para identificar:

- dores recorrentes;
- linguagem utilizada pelos usuários;
- migrações;
- frustrações;
- workarounds;
- necessidades não atendidas.

Relatos públicos são **sinais qualitativos**, não estimativas de prevalência.

Um conjunto de comentários não permite afirmar que “a maioria dos usuários” possui determinado problema sem evidência adicional.

### Nível 5 — inferência do modelo

Pode conectar evidências, comparar alternativas e propor recomendações, mas deve ser marcada como inferência quando não estiver diretamente sustentada por fonte.

---

## 11. Taxonomia obrigatória de afirmações

Toda conclusão material deve ser compreensível como um destes estados:

```text
EVIDÊNCIA
→ observado em fonte, ativo ou dado

SINAL QUALITATIVO
→ relato ou padrão indicativo, sem força estatística

INFERÊNCIA
→ interpretação derivada das evidências

RECOMENDAÇÃO
→ movimento sugerido

HIPÓTESE
→ precisa de validação

DECISÃO HUMANA
→ aprovada pelo usuário

PENDÊNCIA
→ ainda sem resposta suficiente
```

A IA não deve transformar automaticamente uma recomendação em decisão.

---

## 12. Leitura dos ativos do projeto

Quando o Discovery indicar materiais existentes, eles devem ser analisados antes de a pesquisa concluir que algo precisa ser criado do zero.

Podem ser avaliados:

- telas atuais;
- protótipos;
- documentos;
- planilhas;
- PDFs;
- bases de dados;
- processos manuais;
- fluxos em WhatsApp ou e-mail;
- integrações existentes;
- modelos de negócio atuais;
- relatórios ou métricas.

A análise deve procurar:

```text
O QUE JÁ FUNCIONA
O QUE GERA ATRITO
O QUE ESTÁ FALTANDO
O QUE É REDUNDANTE
O QUE É RISCO
O QUE PODE SER REUTILIZADO
```

O fato de existir uma solução legada não significa que sua estrutura deve ser preservada. Ela é uma evidência a ser analisada.

---

## 13. Estrutura recomendada da investigação

A pesquisa não precisa obedecer exatamente à mesma ordem em todos os projetos, mas normalmente deve cobrir os blocos relevantes abaixo.

### 13.1. Leitura executiva

Uma síntese de alto nível com:

- principal conclusão;
- maior oportunidade;
- maior risco;
- principal condicionante;
- recomendação de avanço.

Ela deve ser escrita depois da investigação, mesmo que apareça no início do relatório.

### 13.2. Tese do produto e viabilidade

Reformular a tese do Discovery à luz das evidências.

Avaliar dimensões como:

| Dimensão | Pergunta |
| --- | --- |
| Desejabilidade | Existe sinal suficiente de problema e valor? |
| Viabilidade técnica | As capacidades principais são factíveis? |
| Viabilidade de negócio | Existe caminho plausível de sustentabilidade? |
| Viabilidade operacional | A equipe consegue operar o modelo? |
| Risco regulatório | Existem restrições jurídicas ou profissionais relevantes? |
| Confiança / segurança | O modelo cria risco relevante para usuário ou plataforma? |

Nem toda dimensão precisa receber uma nota artificial. O objetivo é tornar as condições visíveis.

### 13.3. Público inicial e trabalho a ser feito

Refinar o público com base em evidências.

Quando útil, organizar o trabalho a ser feito:

```text
QUANDO <situação>
QUERO <ação / progresso>
PARA <resultado>
SEM <fricção principal>
```

Isso é uma síntese de pesquisa, não uma persona definitiva.

### 13.4. Mercado e concorrentes

Comparar concorrentes relevantes por:

- centro do produto;
- público;
- força principal;
- modelo de uso;
- features maduras;
- limitações;
- oportunidade de diferenciação;
- risco de paridade.

A pesquisa deve evitar duas falhas comuns:

1. listar concorrentes sem explicar o que isso muda para o projeto;
2. declarar como diferencial algo que já é comportamento padrão da categoria.

### 13.5. Problemas priorizados

Problemas podem ser organizados por:

| Campo | Significado |
| --- | --- |
| Problema | Fricção observada |
| Severidade | Impacto quando ocorre |
| Frequência | Com que recorrência aparece |
| Confiança | Força da evidência disponível |
| Movimento | Resposta de produto a investigar |

O campo “Movimento” é recomendação preliminar, não requisito aprovado.

### 13.6. Mapa de oportunidades

Separar oportunidades por horizonte reduz a tendência de transformar toda ideia em MVP.

Exemplo de estrutura:

```text
AGORA
→ validar hipótese crítica

PRÓXIMO CICLO
→ provar loop principal

PESQUISA MAIS PROFUNDA
→ explorar módulos ou riscos adicionais
```

### 13.7. Escopo recomendado

A Pesquisa pode recomendar um recorte como:

```text
CORE
P0 / BETA
P1 / APÓS CORE
P2 / MATURIDADE
FORA DO ESCOPO ATUAL
```

Essas classificações ajudam o Briefing, mas ainda são recomendações de pesquisa.

O Briefing será responsável por aprovar e canonizar o escopo.

### 13.8. Jornadas essenciais

Quando houver evidência suficiente, a pesquisa pode registrar jornadas de alto nível para provar viabilidade e localizar atrito.

Exemplo:

```text
situação
→ ação principal
→ decisão
→ resultado
```

A etapa não deve produzir uma Especificação de UX completa.

### 13.9. Viabilidade de integrações e dados

Para cada dependência externa relevante, investigar:

- existência de API/SDK;
- disponibilidade por região;
- autenticação;
- limites;
- preço;
- licenciamento;
- qualidade dos dados;
- rate limits;
- políticas;
- fallback;
- risco de dependência.

Quando uma API ainda não está aprovada ou contratada, o relatório deve tratar seu uso como dependência ou hipótese, não como garantia.

### 13.10. Auditoria preliminar de UX

Se existirem telas ou fluxos atuais, a Pesquisa pode avaliar:

- hierarquia;
- clareza da ação principal;
- estados vazios;
- densidade;
- risco de ação destrutiva;
- navegação;
- carga cognitiva;
- acessibilidade observável;
- coerência com a tarefa principal.

A saída deve indicar problemas e movimentos recomendados.

Ela não substitui os documentos específicos de Princípios, Direção de UI ou Especificação de UX.

### 13.11. Direção técnica preliminar

A Pesquisa pode verificar se a ideia é implementável e quais famílias de solução parecem adequadas.

Pode analisar:

- mobile nativo, multiplataforma ou web;
- necessidade de offline;
- banco relacional ou outro modelo;
- uso de storage;
- requisitos de autenticação;
- provedores candidatos;
- observabilidade;
- limites de plataforma;
- necessidade de filas, jobs, realtime ou integrações.

Mas a pesquisa não deve canonizar:

- linguagem;
- framework;
- biblioteca;
- arquitetura;
- provider final;
- organização de repositório.

Essas decisões pertencem às etapas de Engenharia/Arquitetura, Visão do Tech Lead e Infraestrutura.

Quando for necessário citar uma tecnologia para provar viabilidade, o texto deve usar linguagem como:

```text
“é tecnicamente viável com soluções maduras como...”

ou

“candidatos atuais incluem...”
```

em vez de:

```text
“o projeto usará...”
```

### 13.12. Fronteiras e invariantes preliminares

Algumas conclusões de pesquisa podem revelar propriedades que futuras decisões técnicas precisam preservar.

Exemplos:

- histórico não pode ser reescrito silenciosamente;
- integração deve ser idempotente;
- dados sensíveis não devem ir para analytics;
- conteúdo publicado exige consentimento;
- saldo econômico precisa de ledger;
- integração externa precisa de fallback.

Essas propriedades podem ser registradas como **restrições derivadas da pesquisa**, mas a arquitetura responsável por implementá-las será definida depois.

### 13.13. Privacidade, segurança e responsabilidade

A pesquisa deve identificar cedo quando o produto envolve:

- dados sensíveis;
- localização;
- saúde;
- menores;
- pagamentos;
- conteúdo gerado por usuário;
- marketplace;
- publicidade;
- profissionais regulamentados;
- ranking ou recompensa econômica;
- autenticação reforçada;
- risco de fraude.

Não é necessário produzir o threat model completo nesta etapa, mas riscos que alteram a viabilidade precisam aparecer.

### 13.14. Métricas e plano de validação

A etapa deve propor como reduzir incerteza.

Podem ser definidos:

- métrica norte preliminar;
- ativação;
- tempo para primeiro valor;
- qualidade da operação central;
- confiança / erro;
- retenção;
- métricas técnicas;
- métricas de fraude ou moderação quando aplicável.

Também deve recomendar experimentos antes de código de produção quando úteis:

- entrevistas;
- testes moderados;
- POCs;
- protótipos;
- análise de arquivos reais;
- pilotos;
- testes de integração;
- validação jurídica ou comercial.

### 13.15. Riscos e contramedidas

Riscos relevantes devem ser registrados com pelo menos:

| Campo | Conteúdo |
| --- | --- |
| Risco | O que pode dar errado |
| Nível | Severidade relativa |
| Efeito | Consequência |
| Contramedida | Movimento recomendado |
| Validação | Como reduzir incerteza |

### 13.16. Recomendação e gates

O relatório deve concluir com um dos estados:

```text
GO
GO CONDICIONAL
PESQUISAR MAIS
NO-GO
```

#### GO

As evidências atuais sustentam avanço sem bloqueador material identificado.

#### GO CONDICIONAL

A ideia pode avançar, mas depende de hipóteses, gates ou validações explicitamente registradas.

#### PESQUISAR MAIS

Não existe evidência suficiente para comprometer um Briefing responsável.

#### NO-GO

Existe evidência material de que o recorte atual não deve avançar.

`NO-GO` não significa necessariamente abandonar o problema. Pode significar reformular tese, público, canal, modelo ou escopo e retornar ao Discovery.

---

## 14. Gates não são cronograma

A Pesquisa pode definir condições para liberar decisões futuras.

Exemplos:

```text
GATE DE PRODUTO
→ confirmar que o problema possui intensidade suficiente

GATE DE UX
→ usuário conclui tarefa crítica sem ajuda relevante

GATE DE INTEGRAÇÃO
→ API possui cobertura e condições comerciais aceitáveis

GATE REGULATÓRIO
→ modelo revisado por especialista aplicável

GATE DE MERCADO
→ piloto demonstra retenção mínima
```

Um gate é uma condição de saída ou avanço.

Ele não deve ser confundido com data arbitrária ou promessa de entrega.

---

## 15. A Pesquisa pode corrigir o Discovery, mas não silenciosamente

A investigação pode encontrar evidências que contradizem hipóteses ou decisões anteriores.

Quando isso ocorrer:

```text
EVIDÊNCIA NOVA
        ↓
CONTRADIÇÃO IDENTIFICADA
        ↓
EXPLICAR A TENSÃO AO HUMANO
        ↓
DECIDIR SE O DISCOVERY PRECISA SER RECONCILIADO
```

A Pesquisa não deve editar retroativamente a intenção do usuário sem aprovação.

O relatório pode registrar:

```text
“a hipótese H-003 foi enfraquecida pelas evidências X e Y”
```

sem fingir que a hipótese nunca existiu.

---

## 16. Separação entre pesquisa e decisão das próximas camadas

O estudo do DayGym continha, corretamente para o contexto daquele momento, recomendações concretas de UI, stack e arquitetura.

Na metodologia refinada, essas recomendações permanecem úteis como **evidência de viabilidade**, mas a responsabilidade canônica é distribuída:

```text
PESQUISA E VIABILIDADE
→ investiga possibilidades, riscos e restrições

BRIEFING
→ canoniza produto e escopo

UX/UI
→ canoniza experiência e direção visual

ENGENHARIA E ARQUITETURA
→ canoniza forças, limites, módulos e arquitetura

VISÃO DO TECH LEAD
→ canoniza stack, frameworks e bibliotecas

INFRAESTRUTURA
→ canoniza providers, ambientes e fundação
```

Isso evita que uma recomendação feita durante a investigação vire dependência permanente sem passar pela camada responsável.

---

## 17. Processo de revisão humana

A Pesquisa e Viabilidade deve seguir duas aprovações distintas.

### Fase A — revisão do conteúdo

O ChatGPT apresenta a investigação no chat.

O usuário pode:

- corrigir entendimento;
- questionar fontes;
- pedir mais pesquisa;
- contestar prioridade;
- alterar uma hipótese;
- adicionar material;
- discordar da recomendação;
- solicitar aprofundamento.

Enquanto houver correções materiais, o arquivo canônico ainda não deve ser criado.

### Fase B — autorização para canonizar

Somente depois de o conteúdo estar aceito, o usuário autoriza a geração do documento.

Exemplo:

```text
A pesquisa está aprovada. Gere o 01_Pesquisa_e_Viabilidade.md e salve no projeto.
```

---

## 18. Estrutura esperada do artefato de projeto

A saída canônica do projeto deve ser:

```text
01_Pesquisa_e_Viabilidade.md
```

Estrutura recomendada:

```text
---
document_id: DOC-01
status: canonical
version: 1.0.0
depends_on:
  - DOC-00
research_date: YYYY-MM-DD
next_document: 02_Briefing_de_Produto_e_Escopo.md
---

# Pesquisa e Viabilidade

## 1. Decisão executiva
## 2. Leitura executiva
## 3. Tese do produto e viabilidade
## 4. Público inicial e trabalho a ser feito
## 5. Mercado e concorrentes
## 6. Problemas priorizados
## 7. Mapa de oportunidades
## 8. Escopo recomendado
## 9. Jornadas essenciais
## 10. Dependências, integrações e dados
## 11. Auditoria de ativos existentes, quando aplicável
## 12. Direções preliminares de UX, quando aplicável
## 13. Viabilidade técnica e restrições
## 14. Privacidade, segurança, regulação e responsabilidade
## 15. Métricas e plano de validação
## 16. Riscos e contramedidas
## 17. Recomendação e gates
## 18. Fontes e evidências
## 19. Hipóteses ainda abertas
## 20. Decisões humanas confirmadas durante a pesquisa
## 21. Handoff para Briefing
```

A estrutura deve ser adaptada ao projeto.

Um produto simples não precisa de seções artificiais vazias apenas para obedecer um template.

---

## 19. Mapa de fontes

O documento final deve permitir entender que tipos de fontes sustentaram cada grupo de conclusões.

Exemplo:

| Cluster | Fontes | Uso |
| --- | --- | --- |
| Mercado | concorrentes, estudos, relatórios | categoria e posicionamento |
| Usuários | entrevistas, comunidades, dados internos | dores e linguagem |
| Técnico | documentação oficial, SDKs, APIs | capacidade e limites |
| UX | padrões, auditoria de telas, testes | fricção e interação |
| Segurança | documentação oficial, normas | riscos e controles |
| Regulação | leis e órgãos competentes | obrigações e limites |
| Negócio | termos, preços, parceiros | sustentabilidade e dependências |

URLs, títulos ou referências suficientes para reencontrar a fonte devem ser preservados.

---

## 20. Decisões em aberto

A Pesquisa não deve esconder perguntas sem resposta para parecer mais completa.

O relatório deve manter uma seção explícita de decisões em aberto quando existirem.

Essas perguntas podem ser resolvidas:

- antes do Briefing;
- durante o Briefing;
- por experimento;
- por especialista;
- em etapa técnica posterior.

Cada pendência deve indicar, quando possível, **quem ou qual evidência pode resolvê-la**.

---

## 21. Quality Gate da Pesquisa e Viabilidade

Antes de propor canonização, o ChatGPT deve verificar:

- o `00_Discovery.md` foi consumido integralmente;
- hipóteses do Discovery foram investigadas de forma explícita;
- fontes atuais foram usadas onde necessário;
- afirmações materiais possuem sustentação ou estão marcadas como inferência;
- relatos públicos não foram tratados como prevalência estatística;
- concorrentes foram analisados além de uma lista superficial;
- riscos relevantes foram registrados;
- dependências externas foram tratadas como dependências, não garantias;
- recomendações de stack/arquitetura não foram transformadas em decisão canônica prematura;
- existe recomendação de avanço clara;
- condições e gates estão visíveis;
- decisões em aberto não foram escondidas;
- a próxima etapa pode consumir o documento sem precisar reconstruir a investigação inteira.

---

## 22. Anti-padrões

A etapa está incorreta quando a IA:

### Pesquisa para confirmar a ideia

Seleciona apenas fontes favoráveis e ignora evidência contrária.

### Copia features de concorrentes

Transforma análise competitiva em backlog por imitação.

### Confunde popularidade com necessidade

Declara um problema universal porque encontrou comentários sobre ele.

### Escolhe stack cedo demais

Converte uma prova de viabilidade técnica em arquitetura definitiva.

### Usa uma única fonte comercial

Aceita marketing de fornecedor como validação independente.

### Produz pesquisa sem decisão

Entrega dezenas de páginas sem explicar o que muda no projeto.

### Produz decisão sem evidência

Faz recomendações fortes baseadas apenas em conhecimento geral do modelo.

### Esconde incerteza

Preenche lacunas para o relatório parecer completo.

### Faz o Briefing dentro da Pesquisa

Canoniza escopo, personas, funcionalidades e roadmap sem revisão posterior.

### Faz arquitetura dentro da Pesquisa

Transforma sugestões preliminares em desenho técnico obrigatório.

### Gera o arquivo sem revisão

Confunde conclusão da análise com autorização para canonização.

---

## 23. Handoff para o Briefing

A Pesquisa e Viabilidade está pronta para entregar o projeto ao Briefing quando existe clareza suficiente sobre:

```text
PROBLEMA COM EVIDÊNCIA
PÚBLICO MAIS PROMISSOR
VALOR A TESTAR
CONCORRÊNCIA
OPORTUNIDADE
RISCOS
RESTRIÇÕES
HIPÓTESES CRÍTICAS
RECORTE RECOMENDADO
VALIDAÇÕES NECESSÁRIAS
DECISÕES EM ABERTO
VEREDITO DE VIABILIDADE
```

O Briefing não deve reexecutar toda a pesquisa.

Ele consome o relatório e transforma a recomendação aprovada em definição de produto e escopo.

Fluxo:

```text
00_Discovery.md
        ↓
01_Pesquisa_e_Viabilidade.md
        ↓
02_Briefing_de_Produto_e_Escopo.md
```

---

## 24. Gate para avançar

A etapa pode ser considerada concluída quando:

- a investigação foi apresentada ao humano;
- fontes e inferências são distinguíveis;
- correções e aprofundamentos solicitados foram incorporados;
- o verdict de viabilidade foi compreendido;
- condições e riscos foram aceitos ou explicitamente contestados;
- o humano aprovou o conteúdo;
- o humano autorizou a canonização;
- `01_Pesquisa_e_Viabilidade.md` foi criado ou atualizado no destino definido;
- o documento está apto a ser consumido pelo Briefing.

Somente então a próxima etapa é elegível:

```text
02 — Briefing de Produto e Escopo
```

---

## 25. Regra final da etapa

> **Pesquisa e Viabilidade não existe para provar que a ideia merece ser construída. Ela existe para descobrir se há evidência suficiente para continuar, qual hipótese merece ser testada primeiro e quais condições precisam ser verdadeiras para o produto avançar com responsabilidade.**

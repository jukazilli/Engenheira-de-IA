---
document_id: CASE-02-DOC-06
title: Técnicas de Desenvolvimento — Site empresarial NorteSul
status: canonical
version: 1.0.0
case_id: CASE-02-SITE-EMPRESARIAL
methodology_stage: tecnicas-desenvolvimento
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
  - Principios_de_UX_UI.md
  - 04_Direcao_de_UI_e_Design_System.md
  - 05_Especificacao_de_UX.md
next_document: 07_Engenharia_e_Arquitetura.md
dev_readiness: SUFFICIENT_FOR_ENGINEERING_AND_ARCHITECTURE
ready_for_codex: false
---

# Técnicas de Desenvolvimento — Site empresarial NorteSul

## 1. Propósito

Este documento define **como o trabalho técnico do Caso 02 deve ser desenvolvido, revisado, testado, documentado e mantido**, independentemente da plataforma, stack, CMS, hosting ou fornecedor que serão escolhidos posteriormente.

A pergunta central desta etapa é:

> **Quais políticas, práticas, gates e critérios de qualidade precisam governar a construção e manutenção deste produto para que descoberta, conteúdo, acessibilidade, conversão, indexabilidade, privacidade e autonomia editorial permaneçam verificáveis e sustentáveis?**

Este documento não escolhe:

- CMS;
- linguagem;
- runtime;
- framework;
- hosting;
- banco de dados;
- ferramenta de analytics;
- mecanismo de CI/CD;
- solução antispam;
- biblioteca de testes.

Ele cria o **sistema operacional de engenharia** que a solução futura deverá suportar.

```text
IA PROPÕE
AUTOMAÇÃO VERIFICA
HUMANO RESPONDE
```

A canonização deste documento não autoriza implementação pelo Codex.

---

## 2. Natureza técnica deste produto

Neste caso, “software” é maior que código.

O produto poderá ser composto por:

```text
CÓDIGO PRÓPRIO
+
CMS / PLATAFORMA
+
CONFIGURAÇÃO
+
CONTEÚDO
+
DOMÍNIO / DNS
+
FORMULÁRIOS
+
ANALYTICS
+
SEO
+
INTEGRAÇÕES EXTERNAS
```

Portanto, a governança técnica também precisa tratar mudanças como:

- alterar modelo de conteúdo;
- alterar slug/URL;
- remover página pública;
- mudar canonical;
- ativar `noindex`;
- alterar redirects;
- instalar plugin/app/extensão;
- adicionar script de terceiro;
- mudar formulário;
- alterar destino de lead;
- alterar permissão editorial;
- modificar domínio, DNS ou configuração de publicação;
- alterar defaults de SEO;
- alterar política de tracking.

Uma alteração feita em interface visual de provider pode possuir o mesmo risco de uma alteração feita em código.

---

## 3. Princípio dominante

> **Velocidade de publicação não é velocidade de produto.**

O ciclo desejado é:

```text
DECISÃO CORRETA
↓
MUDANÇA PEQUENA
↓
PROVA PROPORCIONAL AO RISCO
↓
REVISÃO COMPREENSÍVEL
↓
PUBLICAÇÃO CONTROLADA
↓
VALIDAÇÃO
↓
RECUPERAÇÃO SIMPLES SE NECESSÁRIO
```

Um site publicado rapidamente que perde URLs, acessibilidade, privacidade ou capacidade editorial não representa ganho real de velocidade.

---

## 4. Hierarquia de autoridade durante implementação futura

Quando houver conflito, a execução deve respeitar a precedência documental da metodologia.

Para este caso, de forma prática:

1. lei, segurança, privacidade e políticas obrigatórias;
2. `02_Briefing_de_Produto_e_Escopo.md` e `03_Visao_de_Product_Owner.md`;
3. `Principios_de_UX_UI.md`, `04_Direcao_de_UI_e_Design_System.md` e `05_Especificacao_de_UX.md`;
4. `07_Engenharia_e_Arquitetura.md` e ADRs futuros;
5. `Visao_do_Tech_Lead.md`;
6. `08_DevOps_e_Infraestrutura.md`;
7. este documento;
8. issue, prompt ou sugestão local.

Se uma implementação tecnicamente necessária contradizer documento superior, o caminho é **reconciliação**, não violação silenciosa.

---

## 5. Princípios de engenharia aplicados ao Caso 02

### DEV-SITE-P1 — Intenção antes de mecanismo

Código, configuração e modelo editorial devem revelar a finalidade do produto.

Uma pessoa competente precisa conseguir reconhecer conceitos como:

```text
serviço
região
case
contato
estado de publicação
```

sem reconstruir o prompt ou a ferramenta que originou a configuração.

### DEV-SITE-P2 — Correto antes de otimizado

Sequência preferida:

```text
CORRETO
↓
SIMPLES
↓
MENSURÁVEL
↓
OTIMIZADO QUANDO NECESSÁRIO
```

Não sacrificar clareza, acessibilidade ou indexabilidade por otimização sem evidência.

### DEV-SITE-P3 — Estado explícito

Estados materialmente diferentes não devem ser comprimidos em booleanos vagos.

Exemplos já definidos pela UX:

```text
EDITING
VALIDATION_ERROR
SUBMITTING
SUBMITTED
SUBMIT_FAILED_RECOVERABLE
SUBMIT_FAILED_BLOCKING
```

Para conteúdo editorial, quando aplicável:

```text
NOT_PUBLISHED
DRAFT
IN_REVIEW
PUBLISHED
```

### DEV-SITE-P4 — Regra crítica não vive apenas na UI

Claims sensíveis, autorização editorial, validação de formulário e regras de publicação não podem depender apenas de esconder controles visuais.

### DEV-SITE-P5 — Efeitos externos são controláveis

Rede, formulário, scripts de terceiros, analytics, publicação e integrações precisam ser isoláveis/testáveis na medida em que alteram comportamento relevante.

### DEV-SITE-P6 — Falha é caminho normal

Precisamos tratar, quando aplicável:

- timeout;
- falha de envio;
- double click;
- script externo indisponível;
- imagem ausente;
- link quebrado;
- conteúdo removido;
- falha de publicação;
- tracker indisponível;
- falha de deploy.

### DEV-SITE-P7 — Privacidade por construção

Coletar, transportar, logar, medir e reter somente o necessário.

### DEV-SITE-P8 — Compatibilidade progressiva

URLs públicas, modelos editoriais e contratos relevantes devem evoluir sem destruição desnecessária.

### DEV-SITE-P9 — Observável sem vazar

Falha de formulário e publicação precisa ser diagnosticável sem serializar conteúdo pessoal em telemetria comum.

### DEV-SITE-P10 — Reversibilidade por padrão

Mudança estrutural precisa possuir caminho de rollback, redirect, restauração ou reversão proporcional.

---

## 6. Classes de mudança

### 6.1 NORMAL

Exemplos:

- microcopy sem mudança de claim;
- spacing;
- ajuste visual local;
- teste adicional;
- refactor;
- documentação;
- atualização editorial rotineira dentro do contrato aprovado.

Tratamento:

```text
GATES NORMAIS
+
REVIEW NORMAL
```

### 6.2 SENSÍVEL

Exemplos:

- formulário;
- coleta de dado pessoal;
- analytics/cookies;
- scripts de terceiros;
- autenticação e permissões editoriais;
- PMOC;
- domínio/DNS;
- redirects de URLs indexadas;
- robots/noindex/canonical;
- migração;
- plugin/app/extensão;
- upload;
- alteração de modelo editorial;
- antispam;
- alteração produtiva.

Tratamento:

```text
OWNER APROPRIADO
+
RISCO EXPLÍCITO
+
PROVA
+
ROLLBACK
```

### 6.3 PROIBIDA SEM AUTORIZAÇÃO HUMANA EXPLÍCITA

- alterar DNS produtivo;
- substituir site legado real;
- apagar conteúdo indexado em massa;
- usar dados reais em prompts, fixtures ou screenshots de debug;
- publicar claim regulatório não aprovado;
- instalar tracker não aprovado;
- adicionar script de coleta sem avaliação;
- desativar controle de segurança;
- alterar produção sem trilha;
- incluir segredo em código;
- escolher CMS/hosting/stack antes da etapa responsável.

---

## 7. Desenvolvimento assistido por IA

### 7.1 Autoridade

Agentes podem, quando autorizados:

- investigar;
- mapear arquivos e configurações;
- propor plano;
- alterar código/configuração;
- criar testes;
- executar verificações;
- revisar diff;
- atualizar documentação.

Mas não podem:

- aprovar o próprio trabalho como prova final;
- assumir aprovação humana ausente;
- fabricar evidência;
- inventar conteúdo comercial;
- inventar serviço ou região;
- escolher tecnologia ainda não aprovada;
- promover produção sem autorização.

### 7.2 Pacote mínimo de contexto

Toda tarefa material deve informar:

| Campo | Pergunta |
|---|---|
| Objetivo | qual resultado observável buscamos? |
| Escopo | o que pode mudar? |
| Fora de escopo | o que não pode mudar? |
| Fontes | quais documentos/histórias/decisões governam? |
| Invariantes | o que nunca pode acontecer? |
| Estados | quais estados precisam permanecer válidos? |
| Dados | há informação pessoal/confidencial? |
| SEO | URL/indexabilidade podem ser afetadas? |
| Risco | auth, PMOC, terceiro, migração, a11y? |
| Verificação | que provas demonstram correção? |
| Rollback | como desfazer? |
| Parada | quando pedir decisão humana? |

### 7.3 Stop conditions específicas

O agente deve parar se precisar:

- inventar cidade atendida;
- inventar serviço;
- inventar certificação;
- inventar cliente/case;
- fabricar avaliação;
- afirmar obrigação PMOC sem fonte aprovada;
- criar campo de formulário sem justificativa de produto;
- adicionar tracker não aprovado;
- instalar extensão sem avaliação;
- quebrar URL antiga sem decisão;
- modificar DNS;
- acessar conta externa não autorizada;
- escolher CMS/framework;
- transformar template do provider em nova regra de UX;
- criar blog apenas porque “ajuda SEO”;
- criar páginas locais artificiais;
- copiar dados pessoais para logs/analytics.

---

## 8. Conteúdo como estado de produto

Neste projeto, conteúdo não é texto periférico.

Serviços, regiões, cases, avaliações e FAQs influenciam diretamente:

```text
PRODUTO
SEO
UX
PRIVACIDADE
CONVERSÃO
REPUTAÇÃO
```

Consequências:

- região atendida é dado comercial;
- serviço é capacidade de produto;
- case é evidência e pode carregar dado de terceiro;
- PMOC pode carregar claim sensível;
- FAQ pode alterar decisão do visitante;
- avaliação precisa preservar origem/contexto.

Mudanças críticas nesses conteúdos precisam respeitar os contratos canônicos.

---

## 9. Modelo editorial e estados válidos

Quando houver conteúdo estruturado, preferir modelos que tornem estados inválidos difíceis de representar.

Exemplo conceitual de case:

```text
title
service
summary
primaryImage
publicationState
```

Isso não canoniza schema físico.

A Arquitetura e o Tech Lead decidirão quais modelos, APIs ou mecanismos a plataforma suporta.

---

## 10. Formulário e idempotência

### DEV-SITE-IDEMP-001 — Submissão de contato

Quando uma mesma intenção puder ser enviada mais de uma vez por:

- double tap;
- retry;
- timeout;
- reconexão;
- comportamento do provider;

uma única intenção não deve produzir múltiplos contatos equivalentes por acidente.

A implementação futura precisa demonstrar esse comportamento quando a plataforma permitir controle suficiente.

---

## 11. WhatsApp e semântica de evento

`whatsapp_contact_started` significa intenção de abrir o canal.

Não significa:

```text
mensagem enviada
lead recebido
atendimento iniciado
venda gerada
```

Essa distinção precisa permanecer em analytics, documentação e interpretação comercial.

---

## 12. Analytics como dependência não crítica

Regra:

```text
ANALYTICS FAILS
↓
CORE CONTINUES
```

Falha de tracker não pode impedir:

- leitura;
- navegação;
- WhatsApp;
- formulário.

Isso precisa ser verificável posteriormente.

---

## 13. Scripts e integrações de terceiros

Qualquer script, widget, app, plugin ou extensão deve ser avaliado quanto a:

- finalidade;
- necessidade;
- origem;
- manutenção;
- licença;
- segurança;
- privacidade;
- performance;
- disponibilidade;
- lock-in;
- capacidade de remoção.

```text
“TEM UM PLUGIN”
!=
“DEVEMOS INSTALAR”
```

Não adicionar automaticamente:

- chat;
- heatmap;
- pixel;
- review widget;
- social embed;
- tag manager;
- biblioteca pesada.

---

## 14. SEO como contrato técnico

Mudanças podem precisar preservar:

```text
URL
HTTP STATUS
TITLE
DESCRIPTION
HEADING SEMANTICS
CANONICAL
ROBOTS
SITEMAP
STRUCTURED DATA
INTERNAL LINKS
REDIRECTS
INDEXABILITY
PERFORMANCE
```

Regressão nessas propriedades pode ser defeito funcional.

### 14.1 URLs públicas

Uma URL indexada ou compartilhada é um contrato externo.

```text
RENOMEAR SLUG
!=
REFATOR LOCAL
```

Pode exigir:

- inventário;
- redirect;
- canonical;
- teste;
- monitoramento;
- rollback.

### 14.2 Migração do legado

Em projeto real, antes de substituir o site:

```text
INVENTARIAR
↓
MAPEAR
↓
PUBLICAR COMPATIBILIDADE
↓
VALIDAR
↓
MIGRAR
↓
MONITORAR
↓
REMOVER LEGADO QUANDO SEGURO
```

Como o Caso 02 é simulado e não possui site real auditável, nenhuma evidência de legado é fabricada.

---

## 15. Git, branches e commits

Para artefatos versionáveis:

```text
main
= potencialmente promovível
```

quando infraestrutura correspondente existir.

Política:

- sem push direto quando a plataforma permitir;
- sem force push;
- checks obrigatórios proporcionais;
- review humano conforme risco;
- branch curta;
- commit coerente;
- evitar misturar refactor/formatação massiva com mudança funcional.

O padrão concreto de branch/commit será calibrado pela baseline técnica.

---

## 16. Conteúdo editorial não exige PR de código

Precisamos separar duas classes de alteração.

### Alteração editorial rotineira

```text
conteúdo dentro do contrato aprovado
→ workflow editorial do CMS
```

Exemplos:

- adicionar case;
- trocar foto aprovada;
- atualizar FAQ;
- corrigir texto;
- atualizar região dentro do processo autorizado.

### Alteração estrutural

```text
novo tipo de conteúdo
novo campo
novo template
novo script
nova permissão
nova integração
nova regra de publicação
```

→ governança técnica proporcional.

Não transformaremos a operação editorial diária em processo de PR sem necessidade.

---

## 17. Configuration as product state

Configuração estrutural da plataforma é ativo técnico.

Exemplos:

```text
modelo de conteúdo
papéis
redirect rules
form destination
scripts
SEO defaults
domains
publishing settings
```

Quando houver export/versionamento, preferir rastreabilidade.

Quando não houver, mudança material precisa de documentação/evidência equivalente.

Não é aceitável que configuração crítica exista apenas na memória de quem operou o painel.

---

## 18. Pull requests

Um PR material deve explicar:

- problema;
- fonte canônica;
- o que mudou;
- o que não mudou;
- risco;
- como testar;
- evidência;
- SEO/URL quando aplicável;
- privacidade quando aplicável;
- acessibilidade quando aplicável;
- rollback;
- uso de IA;
- pendências.

---

## 19. Revisão em duas passagens

### Passagem 1 — Intenção

Perguntas:

```text
isso pertence à entrega?
respeita produto e UX?
cria conteúdo/feature não aprovado?
a plataforma está impondo uma decisão?
há risco de SEO, privacidade ou migração?
```

### Passagem 2 — Implementação

Avaliar:

- correção;
- legibilidade;
- estados;
- erros;
- acessibilidade;
- performance;
- segurança;
- privacidade;
- SEO;
- testes;
- observabilidade;
- rollback.

### Severidade

```text
BLOCKER
MAJOR
MINOR
NIT
QUESTION
```

Exemplos de `BLOCKER`:

- formulário envia dado pessoal a analytics;
- deploy remove páginas indexadas sem redirect aprovado;
- usuário editorial consegue alterar configuração crítica indevida;
- claim sensível é publicado sem aprovação.

---

## 20. Estratégia de testes

A stack concreta será escolhida depois.

### 20.1 Conteúdo/contrato

Validar, quando aplicável:

- campos obrigatórios;
- slugs;
- links;
- publicação;
- relações case → serviço;
- metadata;
- structured data.

### 20.2 UI/componentes

- navegação;
- menu mobile;
- formulário;
- erro;
- loading;
- foco;
- CTA;
- accordion;
- imagens ausentes.

### 20.3 Integração

- destino do formulário;
- canal externo;
- CMS/provider;
- analytics quando habilitado;
- publicação.

### 20.4 E2E smoke

```text
serviço
→ prova
→ contato
```

```text
B2B
→ formulário
→ confirmação verdadeira
```

### 20.5 Editorial

```text
login
→ editar
→ revisar
→ publicar
→ confirmar publicação
```

quando automatização for compatível; caso contrário, prova operacional/manual.

### 20.6 SEO/migração

- URLs críticas;
- redirects;
- canonical;
- robots/noindex;
- sitemap;
- status HTTP;
- links internos;
- structured data quando aplicável.

### 20.7 Não funcional

- acessibilidade;
- performance;
- segurança;
- spam/abuso;
- mobile.

---

## 21. Bugs e provas

Para bug reproduzível:

```text
PROVAR FALHA
↓
CORRIGIR
↓
PROVAR VERDE
```

Exemplo:

> formulário limpa campos após timeout.

Primeiro reproduzir/provar.

Depois corrigir.

Não aceitar correção especulativa como evidência.

---

## 22. Flaky tests

```text
FLAKY
!=
REEXECUTAR ATÉ PASSAR
```

Teste instável precisa de:

- owner;
- diagnóstico;
- visibilidade;
- política de quarentena quando necessária;
- critério de remoção da quarentena.

---

## 23. Gates conceituais de CI

Em PR, quando aplicável:

```text
format
lint
type/schema validation
unit/component
links/contracts
build
security
dependency review
secret scan
a11y automatizável
SEO regressions automatizáveis
```

Em main/release:

```text
integration
artifact
E2E smoke
migration checks
redirect checks
performance smoke
```

Este documento define **tipos de prova**, não ferramenta de CI.

---

## 24. Performance

Performance é requisito comercial e de experiência.

Mudanças futuras precisam evitar regressões materiais causadas por:

- imagens;
- vídeos;
- fontes;
- scripts de terceiros;
- widgets;
- animações;
- excesso de JavaScript;
- embeds.

A Arquitetura e o Tech Lead poderão definir budgets mensuráveis posteriormente.

---

## 25. Acessibilidade na implementação

Evidências esperadas, conforme aplicável:

| Área | Prova |
|---|---|
| headings/semântica | inspeção + automação |
| contraste | tokens + teste |
| teclado | integração/E2E/manual |
| foco | integração |
| forms | labels + mensagens + associação |
| mobile/touch | dispositivo/emulação |
| imagens | alt/contexto |
| motion | preferência reduzida |
| zoom/reflow | teste |
| CMS herdado | avaliação operacional adequada |

Correção crítica de acessibilidade é defeito funcional.

---

## 26. Segurança

Threat model precisa ser considerado principalmente para:

- formulário;
- administração/CMS;
- autenticação editorial;
- upload;
- scripts de terceiros;
- migração/deploy;
- integrações externas.

### 26.1 Formulário

Proteção futura deve ser proporcional contra:

- spam;
- abuso;
- payload excessivo;
- injection;
- automação;
- exploração de endpoint;
- vazamento;
- enumeração quando relevante.

CAPTCHA agressivo não é default obrigatório.

### 26.2 Upload editorial

Quando existir upload, considerar:

- tipo;
- tamanho;
- metadata;
- privacidade;
- processamento seguro;
- permissão.

A capacidade pode ser oferecida pelo provider, desde que o contrato seja satisfeito.

---

## 27. Classificação inicial de dados

### Público

Conteúdo aprovado publicado.

### Interno

Rascunhos editoriais não sensíveis e configurações operacionais comuns.

### Confidencial

Leads, contatos comerciais e conteúdo não publicado que contenha informação de terceiro.

### Restrito

Credenciais, tokens, secrets e configurações administrativas sensíveis.

Regra:

```text
LEAD REAL
!=
FIXTURE
!=
PROMPT
!=
SCREENSHOT DE DEBUG
```

---

## 28. Privacidade

Coletar, transportar, retornar, logar e reter apenas o necessário.

Em especial:

```text
FORM BODY
```

não deve ser serializado integralmente em log comum.

Analytics deve usar allowlist de propriedades.

---

## 29. Dependências, plugins e supply chain

Toda dependência, plugin, theme, app, extensão ou script novo precisa ser avaliado quanto a:

- necessidade;
- origem;
- manutenção;
- licença;
- vulnerabilidades;
- privacidade;
- performance;
- lock-in;
- capacidade de teste;
- capacidade de remoção.

Quando a solução possuir código versionável, considerar:

- lockfile/manifests;
- resolução reproduzível;
- secret scanning;
- SAST;
- proveniência quando apropriado;
- permissões mínimas de automação.

Em SaaS, parte da supply chain pertence ao provider; extensões e scripts adicionados pela empresa continuam sob nossa governança.

---

## 30. Observabilidade

Precisamos conseguir diferenciar, quando aplicável:

```text
ERRO DE PÁGINA
ERRO DE BUILD/DEPLOY
ERRO DE FORMULÁRIO
ERRO DE PUBLICAÇÃO
ERRO DE INTEGRAÇÃO
ERRO DE ANALYTICS
```

sem copiar dados pessoais.

Não exigimos tracing distribuído por padrão.

A Arquitetura decidirá se existe complexidade que justifique isso.

### Eventos de produto != logs técnicos

`whatsapp_contact_started` é evento de produto.

`form_request_failed` pode ser sinal técnico.

Não usar log como analytics improvisado nem analytics como diagnóstico completo.

---

## 31. Documentação viva

O projeto deverá documentar proporcionalmente:

- como executar/testar;
- como publicar;
- como atualizar conteúdo;
- como reverter;
- como administrar domínio;
- como administrar redirects;
- como administrar scripts;
- como administrar permissões;
- como responder a falha de formulário;
- como operar a solução escolhida.

`Está configurado no painel` não substitui documentação.

Quando Codex entrar em uso, instruções versionadas devem registrar:

- comandos canônicos;
- convenções;
- limites;
- áreas sensíveis;
- hierarquia documental;
- testes;
- critérios de parada;
- formato de evidência.

---

## 32. Definition of Ready de engenharia

Uma entrega está pronta para desenho técnico quando, conforme aplicável, sabemos:

| Dimensão | Precisa estar claro |
|---|---|
| Problema | usuário, contexto e resultado |
| Aceite | cenários observáveis |
| UX | fluxo, estados, recuperação |
| Conteúdo | owner, claim e estrutura |
| Dados | entrada, saída, sensibilidade |
| SEO | URL/indexação podem ser afetadas? |
| Risco | auth, PMOC, terceiro, migração, spam etc. |
| Dependências | provider/contratos conhecidos ou explicitamente pendentes |
| Operação | impacto, rollback e evidência esperada |

Isso ainda não significa `READY_FOR_CODEX`.

---

## 33. Definition of Done de engenharia

Uma mudança futura só está concluída quando, conforme aplicável:

- comportamento aprovado existe;
- conteúdo aprovado está correto;
- estados previstos permanecem válidos;
- código/configuração é compreensível;
- testes proporcionais ao risco passam;
- acessibilidade foi verificada;
- segurança/privacidade foram avaliadas;
- URLs/SEO continuam corretos;
- performance não sofreu regressão material;
- scripts/dependências foram revisados;
- analytics está minimizado;
- rollback existe;
- documentação foi atualizada;
- nenhuma incerteza material está escondida.

```text
ABRIU NO NAVEGADOR
!=
DONE
```

---

## 34. Definition of Done de release

```text
MERGED
!=
DEPLOYED
!=
INDEXADO
!=
VALIDADO
!=
GERANDO VALOR
```

Release futuro precisa considerar, conforme risco:

- artefato/origem;
- smoke;
- redirects;
- domínio;
- forms;
- analytics;
- indexabilidade;
- observabilidade;
- rollback;
- owners.

---

## 35. Dívida técnica e editorial

Exemplos que precisam de owner/condição de remoção:

```text
redirect temporário
plugin temporário
script legado
campo editorial obsoleto
template antigo
feature flag
```

Segurança, privacidade e integridade não devem ser aceitas como atalho normal.

---

## 36. Métricas de engenharia

Podem ser observadas futuramente:

- lead time;
- change failure rate;
- rollback time;
- defeitos escapados;
- regressões de acessibilidade;
- regressões de performance;
- links quebrados;
- falhas de formulário;
- incidentes de publicação;
- dívida de dependências.

Não utilizar como produtividade individual:

- linhas de código;
- commits;
- PRs;
- prompts;
- tokens;
- percentual de código gerado por IA.

---

## 37. Playbook futuro

```text
ITEM CANÔNICO
↓
READY
↓
CLASSIFICAR RISCO
↓
MAPEAR IMPACTO
↓
IMPLEMENTAR MENOR FATIA
↓
TESTAR
↓
REVISAR
↓
PUBLICAR / PR
↓
GATES
↓
REVIEW HUMANO
↓
PROMOVER
↓
VALIDAR
↓
OBSERVAR
```

Para conteúdo editorial rotineiro haverá fluxo menor apropriado ao CMS.

Para alteração estrutural aplica-se governança técnica proporcional.

---

## 38. Finding metodológico do Caso 02

### CASE-02-METHOD-FINDING-003

> **Em produtos híbridos/Buy, Técnicas de Desenvolvimento precisa governar não apenas código, mas também configuração estrutural, extensões, scripts, modelos editoriais e outros estados técnicos mantidos dentro do provider.**

Isto complementa `CASE-02-METHOD-FINDING-002`:

```text
FINDING-002
UX precisa governar tarefas mínimas
nas superfícies herdadas

FINDING-003
Engenharia precisa governar
mudanças estruturais
nas plataformas herdadas
```

Ao mesmo tempo:

```text
CONTEÚDO EDITORIAL ROTINEIRO
!=
PR DE CÓDIGO OBRIGATÓRIO
```

O processo precisa permanecer proporcional.

Este finding permanece registrado no caso e não altera, sozinho, a metodologia canônica.

---

## 39. Gates DEV do Caso 02

### DEV-01 — Autoridade

Responsabilidade humana e limites de IA estão claros.

### DEV-02 — Código e configuração

Estado, erro, intenção e configuração estrutural são governados.

### DEV-03 — Git

Artefatos versionáveis possuem política de integração/revisabilidade.

### DEV-04 — Review

Intenção e implementação são revisadas separadamente.

### DEV-05 — Testes

Estratégia por camada e risco está definida.

### DEV-06 — Quality Gates

Tipos de checks obrigatórios estão definidos conceitualmente.

### DEV-07 — Segurança

Formulário, admin, upload e terceiros possuem política.

### DEV-08 — Privacidade

Leads, analytics e logs possuem minimização.

### DEV-09 — Acessibilidade

Prova integrada ao desenvolvimento está prevista.

### DEV-10 — Compatibilidade

URLs, migração e modelos editoriais são protegidos.

### DEV-11 — Observabilidade

Sinais técnicos e de produto são separados e minimizados.

### DEV-12 — Documentação

Código, provider e configuração material precisam ser documentados.

### DEV-13 — DoR / DoD

Critérios de entrada e saída de engenharia estão claros.

### DEV-14 — Operação

Deploy, publicação e rollback são tratados conceitualmente.

### DEV-15 — Métricas

Saúde do sistema de entrega é observável sem vanity metrics individuais.

---

## 40. Handoff para Engenharia e Arquitetura

A etapa seguinte recebe, entre outras, estas forças:

```text
SITE PÚBLICO
+
SEO / URLs COMO CONTRATO
+
FORMULÁRIO COM DADOS PESSOAIS
+
CMS / SUPERFÍCIE POSSIVELMENTE HERDADA
+
EDITORIAL ROTINEIRO SEM DEV
+
CONFIGURAÇÃO ESTRUTURAL GOVERNADA
+
ANALYTICS NÃO CRÍTICO
+
THIRD-PARTY CONTROLADO
+
ACESSIBILIDADE
+
PERFORMANCE
+
MIGRAÇÃO REVERSÍVEL
```

A Engenharia e Arquitetura deverá responder:

- quais boundaries técnicos realmente existem;
- quais dados precisam existir;
- se o site precisa de backend próprio;
- se existe banco próprio;
- que parte do conteúdo pertence ao provider;
- como separar owned surfaces de provider-owned surfaces;
- como tratar formulários e leads;
- como preservar URLs/indexação;
- que atributos de qualidade dominam;
- qual nível de arquitetura é realmente suficiente.

Ela **não** deve começar perguntando qual framework usar.

---

## 41. Validação metodológica

Este caso mostrou que uma solução potencialmente simples pode exigir engenharia disciplinada sem necessariamente exigir muita infraestrutura.

Exemplo:

```text
UX
“conteúdo é editável sem desenvolvedor”
↓
TÉCNICAS
“edição rotineira não exige PR,
mas configuração estrutural exige governança”
↓
ARQUITETURA
vai decidir o boundary entre projeto e provider
```

Outro:

```text
UX
“URL pública não vira dead-end”
↓
TÉCNICAS
“URL é contrato e mudança exige prova”
↓
ARQUITETURA / TECH LEAD
vão definir mecanismo de routing/redirect/hosting
```

Nenhuma tecnologia concreta foi selecionada nesta etapa.

```text
DEV_METHOD_VALIDATION: PASS

STACK_SELECTED: NO
CMS_SELECTED: NO
HOSTING_SELECTED: NO
ANALYTICS_VENDOR_SELECTED: NO
CI_VENDOR_SELECTED: NO

AI_POLICY: DEFINED
STOP_CONDITIONS: DEFINED
CODE_AND_CONFIG_POLICY: DEFINED
EDITORIAL_CHANGE_POLICY: DEFINED
IDEMPOTENCY_POLICY: DEFINED
GIT_REVIEW_POLICY: DEFINED
TEST_STRATEGY: DEFINED
SEO_CHANGE_POLICY: DEFINED
SECURITY_BASELINE: DEFINED
PRIVACY_POLICY: DEFINED
SUPPLY_CHAIN_POLICY: DEFINED
A11Y_POLICY: DEFINED
OBSERVABILITY_POLICY: DEFINED
DOR_DOD: DEFINED
DEV_GATES: DEFINED

NEW_METHOD_FINDING:
CASE-02-METHOD-FINDING-003

DEV_READINESS:
SUFFICIENT_FOR_ENGINEERING_AND_ARCHITECTURE

READY_FOR_CODEX:
NO
```

---

## 42. Handoff

```text
DEV_STAGE_EXECUTION: COMPLETE
CLIENT_REVIEW: APPROVED_FOR_SIMULATION
DEV_READINESS: SUFFICIENT_FOR_ENGINEERING_AND_ARCHITECTURE
READY_FOR_CODEX: NO
NEXT_STAGE: 07 — Engenharia e Arquitetura
```

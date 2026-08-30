---
document_id: PROCESS-TECH-LEAD
title: Visão do Tech Lead
status: draft-methodology
version: 0.1.0
stage: visao-tech-lead
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
  - Principios_de_UX_UI.md
  - 04_Direcao_de_UI_e_Design_System.md
  - 05_Especificacao_de_UX.md
  - 06_Tecnicas_de_Desenvolvimento.md
  - 07_Engenharia_e_Arquitetura.md
produces: Visao_do_Tech_Lead.md
next_stage: 08_DevOps_e_Infraestrutura.md
---

# Visão do Tech Lead

## 1. Propósito

A **Visão do Tech Lead** é a etapa responsável por transformar a arquitetura aprovada e a matriz `TECH-REQ` em uma **stack tecnológica concreta, coerente, verificável e sustentável**.

A pergunta central desta etapa é:

> **Quais tecnologias concretas satisfazem melhor os requisitos arquiteturais deste produto neste horizonte, com quais versões, trade-offs, provas, limites e regras de uso?**

Esta etapa existe para impedir que a stack seja escolhida por:

- preferência pessoal;
- hábito do time;
- tendência de mercado;
- popularidade isolada;
- sugestão de IA;
- familiaridade do autor;
- facilidade de gerar boilerplate;
- promessa comercial de fornecedor;
- arquitetura copiada de outro projeto.

O Tech Lead recebe um problema tecnológico já mensurado.

Ele não começa perguntando:

```text
QUAL FRAMEWORK EU GOSTO?
```

Ele começa perguntando:

```text
QUAIS REQUISITOS A STACK PRECISA SATISFAZER?
        ↓
QUAIS CANDIDATOS SATISFAZEM OS REQUISITOS OBRIGATÓRIOS?
        ↓
QUAIS TRADE-OFFS RESTAM?
        ↓
QUAL COMBINAÇÃO PRODUZ O MENOR CUSTO TOTAL
PARA O HORIZONTE APROVADO?
```

A saída desta etapa fixa **com quais tecnologias o sistema será construído**.

Ela ainda não define onde essas tecnologias serão hospedadas, como os ambientes serão provisionados ou qual pipeline concreto promoverá artefatos. Essas responsabilidades pertencem a DevOps e Infraestrutura.

A saída desta etapa **não autoriza implementação pelo Codex**.

---

## 2. Posição no processo

```text
00 Discovery
        ↓
01 Pesquisa e Viabilidade
        ↓
02 Briefing de Produto e Escopo
        ↓
03 Visão de Product Owner
        ↓
Princípios de UX/UI
        ↓
04 Direção de UI e Design System
        ↓
05 Especificação de UX
        ↓
06 Técnicas de Desenvolvimento
        ↓
07 Engenharia e Arquitetura
        ↓
VISÃO DO TECH LEAD
        ↓
08 DevOps e Infraestrutura
        ↓
Backlog canônico
        ↓
Matriz de rastreabilidade
        ↓
Handoff para Codex
```

A etapa `07_Engenharia_e_Arquitetura.md` define:

- drivers;
- atributos de qualidade;
- boundaries;
- invariantes;
- consistência;
- dados;
- contratos;
- segurança;
- confiabilidade;
- requisitos operacionais;
- ADRs;
- matriz `TECH-REQ`.

A Visão do Tech Lead escolhe a **materialização tecnológica** compatível com esse conjunto.

DevOps e Infraestrutura receberão a stack escolhida e decidirão **como ela será construída, hospedada, promovida, observada, protegida e operada**.

---

## 3. Origem desta etapa

Esta etapa não possuía um documento equivalente separado no processo original utilizado como referência para a reconstrução da metodologia.

No processo anterior, decisões de arquitetura, stack, ferramentas, providers e infraestrutura apareciam concentradas na mesma camada técnica.

A metodologia refinada separa essas responsabilidades deliberadamente:

```text
ENGENHARIA E ARQUITETURA
“o que tecnicamente precisa ser verdade?”
“como o sistema deve ser estruturado?”

TECH LEAD
“com quais tecnologias concretas
vamos materializar essa estrutura?”

DEVOPS / INFRA
“como essa stack será entregue,
executada e operada?”
```

Essa separação não é burocrática.

Ela existe para melhorar a qualidade da decisão.

Sem essa fronteira, é fácil transformar uma preferência tecnológica em premissa arquitetural e depois justificar a arquitetura a partir da tecnologia já escolhida.

O processo correto faz o caminho inverso.

---

## 4. Pré-requisitos obrigatórios

Antes de iniciar a Visão do Tech Lead, o ChatGPT deve consumir integralmente:

1. `06_Tecnicas_de_Desenvolvimento.md`;
2. `07_Engenharia_e_Arquitetura.md`;
3. todos os documentos anteriores necessários para compreender a origem de requisitos que influenciam a stack.

`07_Engenharia_e_Arquitetura.md` é a principal fonte canônica desta etapa.

A etapa não deve começar quando:

- os drivers arquiteturais ainda são vagos;
- atributos de qualidade materiais não possuem cenário verificável;
- boundaries estão indefinidos;
- dados críticos não possuem autoridade clara;
- requisitos de offline/sync ainda são contraditórios;
- não existe política suficiente de segurança;
- dependências externas críticas não foram reconhecidas;
- o horizonte de produto é desconhecido;
- a matriz `TECH-REQ` não está pronta;
- uma decisão arquitetural essencial ainda depende de escolha de produto.

Nesses casos:

```text
TECH_LEAD_READINESS: BLOCKED
```

E a etapa deve retornar à fonte responsável.

---

## 5. Handshake operacional

Ao iniciar esta etapa, o ChatGPT deve declarar algo equivalente a:

```text
PROCESS_STATUS: ACTIVE
CURRENT_STAGE: VISAO_TECH_LEAD
INPUT_DOCUMENT: 07_Engenharia_e_Arquitetura.md
TECH_RESEARCH_STATUS: IN_PROGRESS
TECH_LEAD_READINESS: IN_PROGRESS
CANONICAL_OUTPUT: Visao_do_Tech_Lead.md
NEXT_STAGE: 08_DevOps_e_Infraestrutura.md
```

A ativação não autoriza canonização automática.

Primeiro ocorre:

```text
CONSUMO DA ARQUITETURA
        ↓
PESQUISA TECNOLÓGICA ATUAL
        ↓
COMPARAÇÃO
        ↓
POCs QUANDO NECESSÁRIAS
        ↓
SÍNTESE
        ↓
REVISÃO HUMANA
        ↓
CANONIZAÇÃO
```

---

## 6. Mandato do Tech Lead

O Tech Lead deve:

- consumir os `TECH-REQs` sem reinterpretá-los silenciosamente;
- identificar decisões tecnológicas necessárias;
- pesquisar candidatos atuais;
- eliminar candidatos que falham requisitos obrigatórios;
- comparar alternativas restantes por critérios explícitos;
- avaliar maturidade, suporte, manutenção e segurança;
- verificar licenças;
- considerar custo total de manutenção, não apenas velocidade inicial;
- reduzir quantidade desnecessária de linguagens e runtimes;
- avaliar compatibilidade entre as peças da stack;
- provar riscos por POC quando documentação não for suficiente;
- decidir política de versões;
- definir estratégia de dependências;
- definir toolchain de desenvolvimento;
- escolher frameworks e bibliotecas estruturantes;
- escolher tecnologias de persistência quando a arquitetura deixou a engine aberta;
- escolher ferramentas de teste compatíveis com as técnicas aprovadas;
- registrar trade-offs;
- registrar alternativas rejeitadas;
- indicar lock-ins conscientes;
- preparar um handoff operacional claro para DevOps e Infraestrutura.

O Tech Lead não existe para maximizar quantidade de ferramentas.

Uma stack menor e coerente é preferível a um conjunto sofisticado de tecnologias sem necessidade demonstrada.

---

## 7. O que esta etapa pode canonizar

A Visão do Tech Lead pode canonizar, quando aplicável:

- linguagens de programação;
- runtimes;
- versões ou linhas de versão suportadas;
- frameworks de aplicação;
- framework mobile;
- framework web;
- framework/backend runtime;
- engine de banco de dados;
- tecnologia de persistência local;
- bibliotecas de acesso a dados;
- ferramentas de migrations;
- bibliotecas de contratos e validação;
- formato e biblioteca de serialização quando a arquitetura permitir escolha;
- bibliotecas de autenticação/protocolo no código;
- bibliotecas de autorização quando apropriado;
- estratégia tecnológica de cache;
- tecnologia de fila/broker quando a arquitetura exigir uma implementação concreta;
- bibliotecas de retry/circuit breaker quando não forem capacidades nativas escolhidas;
- SDKs de integração;
- bibliotecas de estado de interface;
- bibliotecas de data fetching;
- implementação tecnológica do Design System;
- bibliotecas de gráficos;
- bibliotecas de acessibilidade auxiliares;
- package manager;
- workspace/monorepo tool;
- compilador/transpiler/bundler quando aplicável;
- formatter;
- linter;
- static analysis local;
- gerenciador de tipos/schema/codegen;
- test runner;
- bibliotecas de component test;
- ferramenta de contract test;
- ferramenta de E2E;
- ferramentas de benchmark/fuzz/property testing quando necessárias;
- instrumentação de observabilidade no código;
- convenções tecnológicas que precisam ser uniformes no repositório;
- política de upgrade e depreciação da stack.

A decisão deve ser proporcional ao projeto.

Um site institucional simples não precisa preencher todas essas categorias.

---

## 8. O que esta etapa não pode canonizar

O Tech Lead não deve redefinir:

- público;
- promessa do produto;
- escopo;
- P0/P1/P2;
- regra de negócio;
- jornada;
- fluxo aprovado;
- hierarquia visual;
- requisito de acessibilidade;
- driver arquitetural;
- atributo de qualidade;
- boundary;
- autoridade de dados;
- política de consistência;
- política de privacidade;
- trust boundary;
- RTO/RPO;
- SLO arquitetural;
- decisão arquitetural aprovada em ADR.

Também não deve decidir sozinho:

- provedor de nuvem;
- região física de hospedagem;
- contas e organizações de cloud;
- topologia de rede;
- VPC/subnets;
- CDN concreta;
- DNS;
- secret store de provider;
- serviço gerenciado de backup;
- infraestrutura como código concreta;
- plataforma de CI/CD;
- ambiente de produção;
- política de autoscaling concreta;
- observability backend/provider;
- registry de imagens;
- política de cobrança do ambiente;
- plano comercial de provider.

Esses pontos pertencem a DevOps e Infraestrutura, salvo decisões conjuntas explicitamente classificadas.

---

## 9. A regra central: requisito antes da tecnologia

Toda escolha tecnológica deve apontar para um ou mais `TECH-REQs`.

Exemplo:

```text
TECH-REQ-002
Persistência local transacional obrigatória.

TECH-REQ-003
Dados locais precisam suportar migrations.

TECH-REQ-008
Build precisa rodar em iOS e Android.

        ↓

CANDIDATO A
satisfaz 002 / 003 / 008

CANDIDATO B
satisfaz 002 / 008
mas não possui estratégia madura de migration

        ↓

B É ELIMINADO
```

A metodologia não permite compensar falha de requisito obrigatório com popularidade.

```text
FALHOU REQUISITO OBRIGATÓRIO
        ↓
DESQUALIFICADO
```

Somente depois do filtro obrigatório entram pesos e trade-offs.

---

## 10. Transformar TECH-REQs em decisões tecnológicas

A primeira atividade é agrupar requisitos arquiteturais por decisão.

Exemplo:

| Grupo | TECH-REQs relacionados | Decisão necessária |
| --- | --- | --- |
| Linguagem | 004, 011, 018 | linguagem e sistema de tipos |
| Runtime | 005, 019, 027 | runtime e linha de suporte |
| Mobile | 001, 002, 003, 008 | framework e runtime mobile |
| Dados | 012, 013, 020 | engine e camada de persistência |
| Offline | 002, 014, 015 | persistência local e sync implementation |
| Contratos | 016, 017 | schema/validation/codegen |
| Testes | 021–025 | toolchain de testes |
| Observabilidade | 030–032 | APIs/SDKs de instrumentação |

Os IDs acima são apenas ilustrativos.

A matriz real vem da Arquitetura.

---

## 11. Pesquisa tecnológica atual é obrigatória

Tecnologia envelhece mais rápido do que princípios de arquitetura.

Portanto esta etapa exige pesquisa atual para decisões materiais.

Devem ser reconfirmados, conforme aplicável:

- status de manutenção;
- versão estável atual;
- linha LTS;
- data de EOL;
- matriz de compatibilidade;
- plataformas suportadas;
- política de segurança;
- advisories recentes relevantes;
- licença;
- mudança de licença;
- breaking changes;
- política de release;
- política de upgrade;
- requisitos de runtime;
- requisitos nativos;
- bundle/runtime constraints;
- documentação de migrations;
- suporte a testes;
- suporte de acessibilidade;
- limitações conhecidas que impactam `TECH-REQs`.

Quando houver materialidade temporal, registrar:

```text
TECH_RESEARCH_DATE: YYYY-MM-DD
```

Uma escolha baseada em informação de meses ou anos atrás deve ser marcada como potencialmente desatualizada até verificação.

---

## 12. Hierarquia de fontes para decisão tecnológica

Usar, em ordem de preferência:

1. documentação oficial da tecnologia;
2. repositório oficial;
3. release notes oficiais;
4. política oficial de suporte e segurança;
5. licença oficial;
6. documentação oficial de compatibilidade;
7. benchmarks reproduzíveis do próprio projeto;
8. POCs do projeto;
9. documentação técnica independente de alta qualidade;
10. relatos de comunidade como sinais qualitativos;
11. inferência do modelo.

Comunidade pode ajudar a encontrar problemas.

Ela não prova prevalência nem substitui documentação oficial para capability crítica.

IA não é fonte primária para versão, API, licença ou política de suporte.

---

## 13. Estado das afirmações tecnológicas

Toda afirmação relevante deve poder ser classificada como:

```text
VERIFICADO_EM_FONTE_OFICIAL
VERIFICADO_EM_POC
MEDIDO_NO_PROJETO
INFERÊNCIA
HIPÓTESE
PENDENTE
```

Exemplo:

```text
“Framework X suporta plataforma Y.”
→ VERIFICADO_EM_FONTE_OFICIAL

“Framework X sustentará 50 mil operações por minuto
no nosso workload.”
→ precisa MEDIÇÃO ou POC
```

Não converter capacidade genérica do fornecedor em garantia específica do projeto.

---

## 14. Descoberta de candidatos

Para cada decisão material, gerar uma shortlist pequena.

Normalmente:

```text
2 A 4 CANDIDATOS SÉRIOS
```

é mais útil do que listar vinte ferramentas superficialmente.

A shortlist deve incluir:

- candidato natural;
- alternativa madura;
- alternativa estruturalmente diferente quando isso puder revelar trade-off relevante;
- opção “não adicionar tecnologia” quando válida.

Exemplo:

```text
NECESSIDADE
fila de trabalho assíncrono de baixo volume

CANDIDATOS
A — mecanismo já presente na persistência escolhida
B — broker dedicado
C — serviço gerenciado específico
D — não usar fila; execução síncrona
```

A opção mais sofisticada não recebe vantagem automática.

---

## 15. Hard constraints antes de scoring

A avaliação possui duas fases.

### Fase A — Qualificação obrigatória

Perguntas de bloqueio:

- roda nas plataformas exigidas?
- atende a licença permitida?
- possui suporte de segurança suficiente?
- suporta atributo crítico?
- atende requisito de dados?
- possui caminho de upgrade aceitável?
- integra com o runtime escolhido?
- possui manutenção compatível com horizonte?
- viola algum ADR?
- exige provider proibido?
- cria lock-in incompatível com a Arquitetura?

Falhou requisito obrigatório:

```text
STATUS: REJECTED_HARD_CONSTRAINT
```

### Fase B — Comparação ponderada

Somente candidatos qualificados são pontuados.

---

## 16. Matriz de avaliação tecnológica

Os critérios devem derivar dos drivers reais.

Uma matriz possível:

| Critério | Peso | O que mede |
| --- | ---: | --- |
| Aderência aos TECH-REQs | variável | quantidade e qualidade dos requisitos satisfeitos |
| Segurança | variável | modelo, patches, hardening e superfície de risco |
| Manutenibilidade | variável | clareza, estabilidade, upgrade e dívida esperada |
| Compatibilidade | variável | integração com restante da stack |
| Testabilidade | variável | qualidade das provas automatizáveis |
| Maturidade | variável | estabilidade do ecossistema e histórico |
| Performance | variável | aderência às metas realmente necessárias |
| Portabilidade | variável | custo de saída aceitável |
| Operabilidade | variável | capacidade de observar, depurar e recuperar |
| Acessibilidade | quando aplicável | capacidade de materializar requisitos de UX |
| Experiência do time | variável | curva de aprendizado e risco humano |
| Custo total | variável | desenvolvimento + manutenção + operação induzida |

Os pesos devem ser definidos por projeto.

Não usar pesos padrão apenas porque aparecem neste documento.

---

## 17. Como pontuar sem criar falsa precisão

Uma escala simples é suficiente:

```text
0 — não atende
1 — atende mal / risco alto
2 — atende parcialmente
3 — atende de forma aceitável
4 — atende bem
5 — atende de forma excelente para este requisito
```

A nota precisa ter justificativa.

Evitar:

```text
Framework A = 4,73
Framework B = 4,69
```

quando as evidências são qualitativas.

A matriz ajuda a tornar raciocínio explícito.

Ela não substitui julgamento técnico.

---

## 18. Critério dominante: custo total de propriedade

Velocidade de bootstrap é apenas uma parte do custo.

Avaliar:

```text
CUSTO DE APRENDER
+
CUSTO DE IMPLEMENTAR
+
CUSTO DE TESTAR
+
CUSTO DE ATUALIZAR
+
CUSTO DE DEPURAR
+
CUSTO DE OPERAR
+
CUSTO DE CORRIGIR SEGURANÇA
+
CUSTO DE SUBSTITUIR
+
CUSTO COGNITIVO
```

Uma tecnologia pode reduzir três dias no início e criar anos de custo de manutenção.

Outra pode ser tecnicamente excelente, mas inadequada para o tamanho do produto e da equipe.

---

## 19. Coerência da stack

O Tech Lead deve avaliar a stack como sistema.

Não basta cada ferramenta ser boa isoladamente.

Perguntas:

- as versões são compatíveis?
- os tipos podem atravessar fronteiras com segurança?
- o modelo de erro é coerente?
- o modelo de async é coerente?
- o sistema de módulos é compatível?
- o processo de build é previsível?
- os debuggers funcionam?
- source maps são viáveis?
- a observabilidade atravessa as camadas?
- o modelo de testes é sustentável?
- o número de runtimes é justificado?
- o número de package managers é justificado?
- as escolhas exigem duplicação de domínio?

A soma de boas ferramentas pode formar uma stack ruim.

---

## 20. Orçamento de linguagens e runtimes

Cada linguagem e runtime adicional aumenta:

- contexto;
- atualização;
- segurança;
- build;
- testes;
- observabilidade;
- contratação;
- documentação;
- suporte de IA;
- incident response.

A regra é:

```text
ADICIONAR NOVA LINGUAGEM / RUNTIME
        ↓
QUAL NECESSIDADE REAL NÃO É BEM ATENDIDA
PELO CONJUNTO EXISTENTE?
```

Não buscar unificação a qualquer custo.

Um runtime adicional pode ser correto quando o domínio, plataforma ou performance realmente exigir.

Mas precisa de razão explícita.

---

## 21. Linguagem de programação

Ao escolher linguagem, avaliar:

- aderência aos runtimes necessários;
- sistema de tipos;
- modelagem de estados válidos;
- concorrência;
- ecossistema;
- tooling;
- testes;
- debugging;
- segurança;
- interoperabilidade;
- build e distribuição;
- curva de aprendizado;
- suporte de longo prazo;
- disponibilidade de profissionais;
- compatibilidade com o domínio;
- capacidade de compartilhar contratos sem acoplamento indevido.

Não escolher linguagem apenas porque permite “um código para tudo”.

Compartilhamento inadequado também cria acoplamento.

---

## 22. Runtime

O runtime deve ser avaliado por:

- política de suporte;
- LTS/EOL;
- segurança;
- consumo;
- startup quando relevante;
- concorrência;
- IO;
- ferramentas de profiling;
- compatibilidade com bibliotecas;
- distribuição;
- suporte de plataforma;
- integração com observabilidade;
- compatibilidade futura com DevOps/Infra.

A escolha deve registrar a linha de suporte esperada.

---

## 23. Frameworks de aplicação

Framework é uma dependência estrutural.

Avaliar:

- quanto domínio precisa conhecê-lo;
- capacidade de manter boundaries;
- testing story;
- acessibilidade;
- performance no workload real;
- suporte de plataforma;
- migrations entre versões;
- política de breaking change;
- tamanho e maturidade do ecossistema;
- escape hatches;
- compatibilidade com deploys esperados;
- lock-in arquitetural.

Uma regra importante:

> **O framework deve servir à arquitetura; a arquitetura não deve ser reescrita para caber no framework.**

---

## 24. Persistência canônica

Quando a Arquitetura define propriedades da persistência, mas não a engine concreta, o Tech Lead deve comparar engines capazes de atendê-las.

Avaliar:

- modelo de dados;
- transações;
- constraints;
- concorrência;
- consistência;
- índices;
- migrations;
- backup/restore compatível com requisitos;
- observabilidade;
- ecossistema de drivers;
- portability;
- tooling local;
- capacidade de testar;
- compatibilidade com carga esperada.

A engine não deve ser escolhida apenas pelo provider que a oferece.

Provider será tratado depois.

---

## 25. Persistência local

Quando offline ou continuidade local são requisitos, avaliar:

- transações;
- durabilidade;
- migrations;
- criptografia necessária;
- concorrência;
- tamanho esperado;
- consistência com sync;
- performance em dispositivo real;
- backup do sistema operacional;
- limpeza segura;
- corrupção e recuperação;
- debugging;
- suporte nas plataformas alvo.

Uma POC de persistência local crítica deve testar crash/restart, não apenas CRUD feliz.

---

## 26. Camada de acesso a dados

ORM, query builder ou driver direto são escolhas do Tech Lead quando a Arquitetura não fixa uma delas.

Avaliar:

- transparência de SQL/queries;
- suporte a transação;
- migrations;
- typing;
- performance;
- debug;
- compatibilidade com engine;
- capacidade de expressar queries complexas;
- lock-in;
- impacto em testes;
- geração de schema;
- risco de N+1 ou abstrações invisíveis.

Não escolher ORM para evitar aprender o modelo de dados.

---

## 27. Contratos, schemas e validação

A stack deve materializar os contratos definidos na Arquitetura.

O Tech Lead decide, quando necessário:

- schema language;
- biblioteca de validação;
- geração de tipos;
- serialização;
- compatibilidade;
- tooling de contract tests.

Regras:

```text
EXEMPLO
≠
SCHEMA

TIPO DE COMPILE TIME
≠
VALIDAÇÃO DE INPUT NÃO CONFIÁVEL
```

A fronteira externa precisa de validação executável adequada ao risco.

---

## 28. API e transporte

A Arquitetura define semântica, comandos, queries, eventos, versionamento e consistência.

O Tech Lead pode escolher tecnologias concretas de transporte e implementação quando ainda estiverem abertas.

Exemplos de categorias:

- HTTP/REST tooling;
- RPC;
- GraphQL;
- WebSocket;
- SSE;
- event protocol;
- schema/codegen.

A escolha precisa ser justificada pelos fluxos reais.

Não adotar GraphQL, RPC ou streaming apenas por sofisticação.

---

## 29. Async, fila e mensageria

Quando a Arquitetura exige processamento assíncrono, o Tech Lead avalia tecnologia de fila/broker contra:

- semântica de entrega;
- ordering;
- replay;
- idempotência;
- volume;
- atraso tolerável;
- dead letter;
- observabilidade;
- desenvolvimento local;
- operação induzida;
- portabilidade;
- custo cognitivo.

Se um mecanismo simples satisfaz o horizonte, não adicionar broker distribuído preventivamente.

---

## 30. Cache

Cache é uma tecnologia de performance e disponibilidade, não uma fonte canônica por conveniência.

A escolha precisa partir de requisito medido.

Avaliar:

- o que pode ficar stale;
- TTL;
- invalidação;
- consistência;
- cardinalidade;
- memória;
- eviction;
- observabilidade;
- comportamento de falha;
- segurança;
- se o cache precisa mesmo existir no P0.

`SEM CACHE` é uma decisão legítima.

---

## 31. Autenticação e autorização

A Arquitetura define trust boundaries, identidade, autorização e regras de revogação.

O Tech Lead escolhe bibliotecas, protocolos e integração no código compatíveis com esses contratos.

A escolha de um **identity provider comercial** pode cruzar a fronteira com Infraestrutura.

Nesse caso:

```text
TECH LEAD
requisitos de protocolo, SDK e integração
        +
DEVOPS / INFRA
provider, região, conta, disponibilidade e operação
        ↓
DECISÃO CONJUNTA
```

Nenhum provider pode enfraquecer a semântica de autorização aprovada.

---

## 32. UI e Design System — implementação tecnológica

A Direção de UI define a linguagem visual e os componentes conceituais.

O Tech Lead pode decidir:

- framework de componentes;
- primitives de plataforma;
- library de icons;
- biblioteca de animação;
- biblioteca de gráficos;
- implementação de tokens;
- solução de forms;
- data fetching;
- estado local/global;
- tooling visual;
- testes de componentes.

Mas não pode alterar a constituição visual para facilitar a biblioteca.

```text
DESIGN SYSTEM
“componente precisa suportar estado X”

TECH LEAD
“qual implementação concreta
sustenta X de forma acessível?”
```

---

## 33. Mobile e capacidades nativas

Quando existe aplicativo mobile, avaliar:

- acesso a APIs nativas;
- distribuição;
- updates;
- deep links;
- push;
- background execution;
- armazenamento seguro;
- biometria quando aplicável;
- acessibilidade nativa;
- builds reproduzíveis;
- debugging em device;
- escape hatch nativo;
- política de lojas;
- compatibilidade entre runtime e módulos.

Uma framework mobile não é aprovada apenas porque roda o “hello world”.

POCs devem testar a capacidade nativa mais arriscada do projeto.

---

## 34. Web

Avaliar:

- rendering necessário;
- SEO quando material;
- autenticação;
- acessibilidade;
- compatibilidade de browser;
- offline/PWA quando aplicável;
- forms;
- cache;
- bundle;
- hydration;
- data fetching;
- hosting compatibility como requisito, sem escolher provider prematuramente;
- observabilidade;
- testing.

SSR, SSG, SPA ou streaming não devem ser escolhidos como identidade arquitetural antes de existir necessidade.

---

## 35. Toolchain de qualidade

A etapa `06_Tecnicas_de_Desenvolvimento.md` define os gates conceituais.

O Tech Lead escolhe as ferramentas que os executam no repositório.

Exemplo:

```text
TÉCNICAS
“lint é obrigatório.”

TECH LEAD
“qual linter e quais rulesets?”
```

```text
TÉCNICAS
“contratos precisam de teste.”

TECH LEAD
“qual ferramenta implementa contract testing?”
```

DevOps posteriormente decidirá **onde e como** esses comandos rodam no pipeline.

---

## 36. Estratégia de testes concreta

O Tech Lead deve mapear cada camada de teste aprovada para ferramentas reais.

Tabela recomendada:

| Camada | Ferramenta escolhida | Motivo | TECH-REQ | Limite |
| --- | --- | --- | --- | --- |
| Unit | ... | ... | ... | ... |
| Component | ... | ... | ... | ... |
| Contract | ... | ... | ... | ... |
| Integration | ... | ... | ... | ... |
| E2E | ... | ... | ... | ... |
| A11y | ... | ... | ... | ... |
| Security | ... | ... | ... | ... |

A ferramenta não deve forçar a estratégia a ficar pior do que o contrato da etapa 06.

---

## 37. Observabilidade — instrumentação versus backend

A fronteira recomendada é:

```text
TECH LEAD
instrumentação no código
API/SDK de logs
API/SDK de métricas
API/SDK de traces
correlation context
redaction library

DEVOPS / INFRA
backend de observabilidade
retenção
storage
alertas
acesso
custos
```

Quando possível, preferir contratos portáveis.

Vendor SDK pode existir quando oferece benefício real, mas o lock-in precisa ser explícito.

---

## 38. Package manager, workspace e build

Quando o projeto possui mais de uma aplicação ou pacote, o Tech Lead deve decidir:

- package manager;
- lockfile policy;
- workspace;
- task runner;
- cache local/remoto como capability;
- compilação;
- codegen;
- versionamento interno;
- boundaries automatizáveis;
- comandos canônicos.

A escolha precisa simplificar o fluxo, não criar uma plataforma interna antes da hora.

---

## 39. Dependências: orçamento e governança

Cada dependência adiciona:

```text
CÓDIGO DE TERCEIRO
+
LICENÇA
+
SUPPLY CHAIN
+
PATCHES
+
BREAKING CHANGES
+
TRANSITIVAS
+
CONHECIMENTO
```

Antes de adicionar dependência estruturante, avaliar:

- problema que resolve;
- custo de implementar internamente;
- custo de manter externamente;
- maturidade;
- manutenção recente;
- bus factor quando observável;
- segurança;
- licença;
- tamanho/impacto;
- API pública;
- capacidade de substituir;
- testes;
- compatibilidade.

Não adicionar pacote para poucas linhas triviais sem justificativa.

Também não reimplementar criptografia, parser complexo ou protocolo de segurança por aversão irracional a dependência.

---

## 40. Licenciamento

Licença é requisito técnico-comercial.

Para cada dependência material:

- identificar licença;
- verificar compatibilidade com o modelo do produto;
- registrar obrigações relevantes;
- identificar dual licensing;
- verificar mudança recente de licença quando houver histórico;
- distinguir licença do código e licença do serviço hospedado.

Dependência com licença incompatível é hard blocker.

IA não deve presumir licença pelo nome do projeto.

---

## 41. Supply chain e segurança da stack

O Tech Lead deve verificar se a stack permite os controles definidos em Técnicas de Desenvolvimento.

Avaliar:

- lockfile;
- releases assinadas quando disponíveis;
- provenance;
- dependências transitivas;
- advisories;
- política de disclosure;
- tempo de correção histórico quando material;
- atualização automatizável;
- SAST compatível;
- secret scanning;
- SBOM;
- pinning possível;
- pacote oficial versus clone não oficial.

Não escolher biblioteca abandonada para função sensível apenas porque a API é conveniente.

---

## 42. Política de versões

A Visão do Tech Lead deve definir política explícita.

Exemplo:

```text
RUNTIME
usar linha LTS ativa

FRAMEWORK
usar versão estável suportada

DEPENDÊNCIAS ESTRUTURANTES
pin direto explícito

TRANSITIVAS
lockfile reproduzível

IMAGENS / FERRAMENTAS DE BUILD
referência imutável quando aplicável
```

Para cada tecnologia estrutural registrar:

| Campo | Conteúdo |
| --- | --- |
| Tecnologia | nome |
| Linha aprovada | major/minor/LTS |
| Verificado em | data |
| EOL conhecido | data/estado |
| Política de atualização | regra |
| Compatibilidade | restrições |
| Fonte oficial | referência |

---

## 43. Versão exata versus documentação durável

Existe uma tensão entre documentação e lockfile.

O princípio é:

```text
DOCUMENTO
canoniza tecnologia + linha suportada + política

BOOTSTRAP
resolve e fixa versões exatas
em manifests/lockfiles
```

Quando a implementação começar imediatamente, versões diretas podem ser canonizadas já de forma exata.

Quando houver intervalo relevante entre decisão e bootstrap:

```text
VERSION_STATUS: VERIFY_AT_BOOTSTRAP
```

E a versão deve ser reconfirmada antes de instalar.

Nunca executar:

```text
npm install pacote@latest
```

apenas porque a documentação ficou antiga.

---

## 44. Política de atualização

A stack precisa ter estratégia de evolução.

Definir:

- frequência de patch de segurança;
- política de minor;
- política de major;
- janela de EOL;
- owner;
- dependabot/renovate ou equivalente como capability, sem decidir CI provider aqui;
- compatibilidade antes de upgrade;
- canary quando necessário;
- rollback;
- tratamento de breaking changes.

Tecnologia sem estratégia de atualização se transforma em dívida programada.

---

## 45. Tecnologia “boring” versus tecnologia nova

A metodologia não exige tecnologia antiga.

Também não premia novidade.

Pergunta correta:

> **Qual nível de novidade é justificável pelo benefício específico que recebemos?**

Tecnologia nova pode ser adequada quando:

- resolve necessidade material melhor;
- possui suporte suficiente;
- risco é isolável;
- existe POC;
- existe fallback;
- curva de aprendizado é aceitável.

Tecnologia madura pode ser inadequada quando não atende um driver essencial.

---

## 46. Popularidade e comunidade

Popularidade pode reduzir risco em alguns contextos:

- disponibilidade de profissionais;
- quantidade de integração;
- conhecimento público;
- documentação comunitária;
- tempo para encontrar solução.

Mas popularidade é **critério secundário**.

Ela não substitui:

- adequação;
- segurança;
- compatibilidade;
- manutenção;
- requisitos obrigatórios.

---

## 47. Experiência do time

Conhecimento existente deve ser considerado.

Mas de forma explícita.

Exemplo:

```text
CANDIDATO A
melhor tecnicamente por pequena margem
curva de aprendizado alta

CANDIDATO B
atende todos os requisitos
já dominado pelo time

HORIZONTE
beta em 8 semanas
```

B pode ser a melhor escolha.

Isso é decisão baseada em contexto, não conservadorismo automático.

---

## 48. Compatibilidade com desenvolvimento assistido por IA

Como esta metodologia utiliza IA, o Tech Lead pode avaliar:

- qualidade da documentação oficial;
- APIs estáveis;
- tipos explícitos;
- testes determinísticos;
- mensagens de erro úteis;
- tooling reproduzível;
- capacidade de limitar blast radius;
- capacidade de verificar saída automaticamente.

Mas existe uma regra:

> **Uma tecnologia não deve ser escolhida apenas porque o modelo “conhece mais” sobre ela.**

Familiaridade estatística da IA não supera requisito arquitetural.

---

## 49. POCs e spikes tecnológicos

Documentação não prova tudo.

Quando existe risco material, criar POC limitada.

Situações típicas:

- módulo nativo sensível;
- persistência criptografada;
- migração local;
- offline/restart;
- compatibilidade entre framework e plataforma;
- performance de workload incomum;
- bundle excessivo;
- integração com SDK crítico;
- execução em ambiente requerido;
- acessibilidade difícil;
- streaming/realtime;
- geração de contrato;
- migration entre versões.

A POC deve responder uma pergunta.

Não deve virar produto paralelo.

---

## 50. Template de POC

```text
TL-POC-001

HIPÓTESE
A tecnologia X consegue satisfazer TECH-REQ-014.

RISCO
Sem isso, a decisão tecnológica é insegura.

CENÁRIO
Descrever workload e ambiente representativo.

PROVA
O que será executado.

MÉTRICA / CRITÉRIO
Condição de aprovação.

RESULTADO
PASS / FAIL / INCONCLUSIVE

EVIDÊNCIA
Logs, benchmark, build, teste ou artefato sanitizado.

LIMITAÇÕES
O que a POC não provou.

DECISÃO
Impacto na shortlist.
```

---

## 51. POC não é benchmark de marketing

Evitar decidir com base em benchmark que:

- usa workload diferente;
- foi produzido pelo fornecedor sem reprodução;
- mede somente happy path;
- ignora cold start relevante;
- ignora transação;
- ignora rede;
- ignora memória;
- ignora dispositivo real;
- usa versão diferente;
- compara configurações desiguais.

Quando performance for driver, medir cenário representativo.

---

## 52. Tecnologia e performance

Não otimizar por benchmark genérico quando a meta arquitetural já é atendida confortavelmente.

Exemplo:

```text
REQUISITO
p95 <= 500 ms

CANDIDATO A
p95 80 ms

CANDIDATO B
p95 120 ms
```

Se ambos atendem com margem, fatores como manutenção, segurança e operabilidade podem dominar.

Mais rápido não significa automaticamente melhor.

---

## 53. Lock-in

Nem todo lock-in é ruim.

A pergunta é:

```text
QUAL BENEFÍCIO RECEBEMOS?
QUAL CUSTO DE SAÍDA CRIAMOS?
A ARQUITETURA ACEITA ESSE CUSTO?
```

Classificar:

```text
LOCK_IN_ACCEPTABLE
LOCK_IN_CONDITIONAL
LOCK_IN_NOT_ACCEPTABLE
```

Registrar:

- superfície afetada;
- dados presos;
- código proprietário;
- caminho de exportação;
- custo de migração;
- gatilho de revisão.

---

## 54. Provider-neutral versus provider-bound

Uma das fronteiras mais importantes com Infraestrutura:

```text
POSTGRESQL
= tecnologia / engine

SERVIÇO GERENCIADO X DE POSTGRESQL
= materialização de infraestrutura
```

```text
OPENTELEMETRY
= tecnologia de instrumentação

BACKEND DE TELEMETRIA X
= provider operacional
```

```text
CONTAINER OCI
= formato/runtime capability

REGISTRY X
= infraestrutura
```

Sempre que possível, separar os dois níveis.

---

## 55. Decisões conjuntas com DevOps e Infraestrutura

Algumas tecnologias não podem ser separadas de provider.

Exemplos:

- identity as a service;
- serverless database com API proprietária;
- queue gerenciada com protocolo específico;
- edge runtime proprietário;
- workflow engine SaaS;
- search engine SaaS;
- feature flag SaaS com SDK intrusivo.

Nesses casos, classificar:

```text
DECISION_OWNER: JOINT_TECH_LEAD_INFRA
```

O Tech Lead avalia:

- impacto no código;
- SDK;
- contrato;
- portabilidade;
- testing;
- versão;
- lock-in.

Infra avalia:

- região;
- disponibilidade;
- segurança operacional;
- custo;
- SLA;
- backup;
- networking;
- account ownership;
- suporte.

A decisão só é canonizada após os dois lados estarem consistentes.

---

## 56. Feedback loop com Engenharia e Arquitetura

O Tech Lead não está autorizado a violar a arquitetura para fazer uma tecnologia caber.

Quando todas as opções razoáveis falham um requisito:

```text
TECH-REQ
        ↓
NENHUM CANDIDATO VIÁVEL
        ↓
O REQUISITO É REAL?
        ↓
SIM
        ↓
REABRIR 07 / ADR
OU RECONCILIAR ETAPA ANTERIOR
```

Exemplo:

```text
Arquitetura exige execução em ambiente A.

Framework escolhido só funciona em B.
```

A resposta não é esconder B na implementação.

É reabrir a decisão.

---

## 57. Tech Lead não reescreve arquitetura por conveniência

Anti-pattern:

```text
“Framework X já traz banco Y,
então vamos mudar nossa autoridade de dados.”
```

Errado.

Outro:

```text
“Biblioteca X não suporta offline,
então vamos remover offline.”
```

Errado se offline é requisito aprovado.

A tecnologia é substituível.

O contrato superior não é.

---

## 58. Brownfield

Em projeto existente, o Tech Lead deve diferenciar:

```text
STACK ATUAL
≠
STACK APROVADA PARA O FUTURO
```

Primeiro mapear:

- linguagens atuais;
- versões;
- runtimes;
- frameworks;
- bibliotecas estruturantes;
- package managers;
- build tools;
- engines;
- test frameworks;
- dependências abandonadas;
- versões EOL;
- incompatibilidades;
- vulnerabilidades conhecidas;
- código gerado;
- integrações específicas de provider.

Depois classificar:

```text
KEEP
UPGRADE
ENCAPSULATE
MIGRATE
REPLACE
REMOVE
```

Não reescrever uma aplicação inteira apenas para uniformizar stack.

---

## 59. Migração tecnológica incremental

Se uma tecnologia precisa ser substituída, registrar:

- origem;
- destino;
- motivo;
- compatibilidade temporária;
- estratégia de migração;
- risco;
- prova;
- rollback;
- critério de conclusão.

Preferir migração incremental quando o custo de big bang é alto.

Exemplo:

```text
TDR-014
Runtime antigo EOL
        ↓
compatibilidade dual
        ↓
upgrade módulo a módulo
        ↓
testes de contrato
        ↓
remoção do runtime antigo
```

---

## 60. Technology Decision Record — TDR

Decisões tecnológicas materiais devem possuir um registro próprio quando uma linha de tabela não for suficiente.

Usar:

```text
TDR-xxx
```

Um TDR registra a materialização tecnológica.

Um ADR continua registrando a decisão arquitetural.

Exemplo:

```text
ADR-006
Persistência canônica deve ser relacional,
transacional e com constraints.

        ↓

TDR-004
Selecionar PostgreSQL linha X
como engine concreta.
```

Se o TDR mudar uma decisão arquitetural, ele não substitui o ADR.

Ele dispara reconciliação.

---

## 61. Template de TDR

```markdown
# TDR-xxx — <decisão>

## Status
Proposto | Validado | Aceito | Rejeitado | Substituído

## Data da pesquisa
YYYY-MM-DD

## Owner
<responsável>

## TECH-REQs atendidos
- TECH-REQ-...

## Contexto
Por que a escolha é necessária.

## Hard constraints
Requisitos que não podem falhar.

## Candidatos
Opções avaliadas.

## Evidências
Fontes oficiais, POCs e medições.

## Decisão
Tecnologia escolhida e linha de versão.

## Trade-offs
Ganhos e custos.

## Segurança e licença
Resumo material.

## Lock-in
Tipo, custo de saída e mitigação.

## Política de atualização
Como manter a decisão viva.

## Condição de revisão
Quando reabrir.

## Consequências para Infra
Requisitos que a próxima etapa precisa materializar.
```

---

## 62. Status de decisão tecnológica

Usar estados explícitos:

```text
PROPOSED
UNDER_RESEARCH
POC_REQUIRED
VALIDATED
ACCEPTED
DEFERRED
REJECTED
SUPERSEDED
```

`DEFERRED` não significa “esquecido”.

Deve possuir condição de retomada.

---

## 63. Matriz da stack oficial

A saída deve conter uma tabela equivalente a:

| ID | Área | Tecnologia escolhida | Linha/versão | TECH-REQs | Status | Evidência |
| --- | --- | --- | --- | --- | --- | --- |
| TL-DEC-001 | Linguagem | ... | ... | ... | ACCEPTED | TDR-001 |
| TL-DEC-002 | Runtime | ... | ... | ... | ACCEPTED | TDR-002 |
| TL-DEC-003 | Mobile | ... | ... | ... | ACCEPTED | TDR-003 |
| TL-DEC-004 | Web | ... | ... | ... | ACCEPTED | TDR-004 |
| TL-DEC-005 | Banco | ... | ... | ... | ACCEPTED | TDR-005 |

A tabela não precisa ter todas as linhas em todos os projetos.

---

## 64. Taxonomia de IDs

Sugestão:

```text
TL-DEC-xxx   decisão tecnológica
TL-POC-xxx   prova de conceito
TL-RISK-xxx  risco tecnológico
TL-GATE-xxx  gate da etapa
TDR-xxx      technology decision record
```

`TECH-REQ-xxx` continua pertencendo à Arquitetura.

IDs removidos não devem ser reutilizados.

---

## 65. Rastreabilidade

Toda decisão deve poder ser explicada de trás para frente.

Exemplo:

```text
BR-021
        ↓
UX-FLOW-008
        ↓
ARCH-DRV-004
        ↓
QA-003
        ↓
ADR-006
        ↓
TECH-REQ-012
        ↓
TDR-004
        ↓
TL-DEC-007
        ↓
DevOps / Infra
        ↓
Implementação
```

Isso evita “por que usamos isso?” sem resposta.

---

## 66. Compatibilidade entre decisões

Depois das decisões individuais, executar uma revisão de conjunto.

Checklist:

- todas as versões convivem?
- peer dependencies são compatíveis?
- runtime suporta todos os frameworks?
- build tool entende todos os alvos?
- test tool cobre as plataformas?
- types/schema atravessam fronteiras corretamente?
- observabilidade funciona em todos os runtimes?
- migrations possuem tooling compatível?
- security scanning entende os manifests?
- package manager suporta workspace desejado?
- native modules suportam versões do mobile?
- SSR/edge/static requirements são coerentes?

Uma stack só está aprovada depois de passar a revisão de compatibilidade.

---

## 67. Matriz de compatibilidade

Quando houver múltiplas tecnologias estruturantes, produzir tabela:

| Tecnologia | Depende de | Versão mínima | Versão máxima conhecida | Prova |
| --- | --- | --- | --- | --- |
| A | Runtime X | ... | ... | fonte/POC |
| B | Framework A | ... | ... | build |
| C | Engine Y | ... | ... | integration test |

Não confiar apenas em instalação sem erro.

Build e testes precisam provar a combinação.

---

## 68. Segurança específica das escolhas

Para cada tecnologia estrutural, registrar riscos materiais.

Exemplos:

- sandbox insuficiente;
- parser de entrada não confiável;
- plugin system amplo;
- serialization perigosa;
- unsafe defaults;
- CORS/CSRF assumptions;
- sessão client-side;
- storage inseguro;
- template injection;
- supply chain extensa;
- atualização crítica frequente.

A decisão precisa indicar hardening ou compensação quando necessário.

---

## 69. Requisitos de acessibilidade da stack

Para tecnologias de interface, verificar:

- semântica nativa;
- foco;
- teclado;
- screen reader;
- dynamic type/zoom;
- motion preferences;
- high contrast quando aplicável;
- testes automatizáveis;
- escape hatches.

Se um framework dificulta requisito obrigatório de acessibilidade, isso pesa contra ele materialmente.

---

## 70. Internacionalização e localização

Quando o produto exigir, avaliar:

- Unicode;
- locale;
- datas;
- timezone;
- números;
- moeda;
- pluralização;
- RTL;
- collation;
- tooling de tradução.

Não adicionar framework de i18n pesado quando o escopo não exige.

Mas não escolher stack que torne requisito já aprovado inviável.

---

## 71. Dados e precisão numérica

Quando domínio possui moeda, medidas, pontos ou precisão relevante, a tecnologia deve suportar o modelo definido pela Arquitetura.

Avaliar:

- decimal versus floating point;
- integer scaled;
- serialization;
- database type;
- compatibilidade cliente/servidor;
- arredondamento;
- timezone;
- overflow.

Não delegar precisão de domínio ao comportamento padrão de uma linguagem sem decisão explícita.

---

## 72. Tempo, relógio e timezone

Quando tempo é relevante, escolher bibliotecas e tipos capazes de materializar o contrato arquitetural.

Avaliar:

- UTC;
- timezone do usuário;
- calendar arithmetic;
- DST;
- monotonic clock;
- testability;
- serialização;
- compatibilidade entre runtimes.

Evitar múltiplas bibliotecas de data sem necessidade.

---

## 73. Code generation

Codegen é permitido quando reduz divergência de contrato.

Mas deve ser:

- reproduzível;
- determinístico;
- versionado por fonte;
- regenerável;
- separado de código manual;
- validado no CI posteriormente;
- documentado.

Não editar manualmente artefato gerado como solução permanente.

---

## 74. Feature flags — tecnologia

Produto e Arquitetura definem onde flags são necessárias e quais propriedades devem possuir.

Tech Lead pode escolher SDK/modelo tecnológico no código.

DevOps/Infra decidirá backend, storage, operação e controle quando a solução for externa.

Flag de autorização ou segurança não deve depender de ferramenta de experimentação inadequada.

---

## 75. Tecnologia de criptografia

A arquitetura define necessidade de proteção.

O Tech Lead escolhe primitives e bibliotecas aprovadas pela plataforma quando necessário.

Regras:

- não criar criptografia própria;
- usar primitivas modernas e mantidas;
- separar key management da biblioteca de criptografia;
- permitir rotação quando exigida;
- testar falha;
- documentar formato/versionamento;
- não colocar segredo no código.

Key management concreto pertence a Infraestrutura.

---

## 76. Desenvolvimento local

O Tech Lead define o que o código precisa para rodar localmente:

- runtimes;
- package managers;
- versões;
- emuladores necessários;
- serviços substituíveis;
- seed/fakes;
- comandos canônicos;
- requisitos de hardware razoáveis.

DevOps/Infra pode fornecer containers, dev environments ou serviços remotos depois.

A stack não deve exigir credencial de produção para desenvolvimento local.

---

## 77. Developer Experience como qualidade de engenharia

DX não significa esconder arquitetura.

Boa DX reduz erro e tempo de feedback.

Avaliar:

- setup reproduzível;
- comandos previsíveis;
- erro legível;
- hot reload quando útil;
- type feedback;
- testes rápidos;
- documentação;
- debug;
- geração segura;
- consistência entre plataformas.

Uma ferramenta de DX que cria abstração opaca e impossível de depurar pode ser custo, não benefício.

---

## 78. Ferramentas de desenvolvimento assistido por IA

A metodologia pode usar Codex, ChatGPT ou outras ferramentas autorizadas.

A Visão do Tech Lead pode definir compatibilidade do repositório com agentes:

- comandos determinísticos;
- lint/test/build canônicos;
- arquivos de instrução;
- boundaries claros;
- generated code identificável;
- mocks/fakes seguros;
- dados sintéticos;
- condições de parada.

Mas não precisa escolher uma ferramenta de IA específica como parte da stack da aplicação.

---

## 79. Anti-patterns desta etapa

### 79.1. Stack por preferência

```text
“eu sempre uso X.”
```

Não é justificativa suficiente.

### 79.2. Stack por tendência

```text
“X está em alta.”
```

Não é requisito.

### 79.3. Stack por IA

```text
“ChatGPT recomendou X.”
```

Não é evidência.

### 79.4. Framework como arquitetura

```text
“nossa arquitetura é Next/React/Django/etc.”
```

Framework não substitui descrição arquitetural.

### 79.5. Popularidade vence hard constraint

Proibido.

### 79.6. Escolher tudo de uma vez

Não selecionar biblioteca para problema que ainda não existe.

### 79.7. Dependência sem owner

Tecnologia estrutural precisa de responsabilidade.

### 79.8. Latest sem controle

Não usar “latest” como política de versão.

### 79.9. POC que vira produção

POC não revisada não deve entrar silenciosamente no produto.

### 79.10. Copiar stack de outro projeto

Projetos diferentes possuem drivers diferentes.

---

## 80. Critério para “não escolher ainda”

Nem toda decisão precisa ser antecipada.

Usar:

```text
DEFERRED_UNTIL_NEEDED
```

quando:

- nenhuma história atual precisa da tecnologia;
- decisão pode ser adiada sem custo alto;
- requisitos ainda não estão maduros;
- provider ainda será decidido;
- escolher agora criaria lock-in sem benefício.

Registrar gatilho de decisão.

Exemplo:

```text
SEARCH_ENGINE
STATUS: DEFERRED_UNTIL_QUERY_VOLUME_OR_FEATURE_REQUIRES
```

---

## 81. Princípio de mínimo suficiente

A stack oficial deve ser a menor combinação que satisfaz os requisitos do horizonte com margem responsável.

```text
SIMPLES DEMAIS
→ falha requisito

COMPLEXO DEMAIS
→ aumenta custo sem evidência

MÍNIMO SUFICIENTE
→ atende contrato + evolução plausível
```

---

## 82. Riscos tecnológicos

Registrar riscos como:

| ID | Tecnologia | Risco | Probabilidade | Impacto | Contramedida | Gate |
| --- | --- | --- | --- | --- | --- | --- |
| TL-RISK-001 | ... | ... | ... | ... | ... | ... |

Risco aceito não desaparece.

Ele recebe owner e condição de revisão.

---

## 83. Gates por decisão tecnológica

Uma tecnologia estrutural só pode virar `ACCEPTED` quando:

- TECH-REQs mapeados;
- hard constraints passaram;
- fontes oficiais verificadas;
- licença verificada;
- segurança avaliada;
- compatibilidade avaliada;
- versão/política definida;
- trade-offs registrados;
- POC concluída quando necessária;
- lock-in registrado;
- owner definido;
- impacto em Infra identificado.

---

## 84. Readiness da Visão do Tech Lead

Usar estados:

```text
TECH_LEAD_READINESS: INSUFFICIENT
TECH_LEAD_READINESS: SUFFICIENT_WITH_OPEN_QUESTIONS
TECH_LEAD_READINESS: SUFFICIENT
```

`SUFFICIENT_WITH_OPEN_QUESTIONS` é válido quando:

- pendências não impedem Infraestrutura;
- cada pendência possui owner;
- existe momento de resolução;
- nenhum hard constraint está sem resposta.

---

## 85. Gates da etapa

| Gate | Evidência |
| --- | --- |
| TL-01 Inputs | Arquitetura e TECH-REQs consumidos integralmente. |
| TL-02 Research | Fontes atuais verificadas para decisões materiais. |
| TL-03 Hard constraints | Nenhuma tecnologia aceita falha requisito obrigatório. |
| TL-04 Alternatives | Decisões estruturantes possuem comparação suficiente. |
| TL-05 POCs | Riscos incertos foram provados quando necessário. |
| TL-06 Versions | Linha de versão e política de atualização definidas. |
| TL-07 Security | Segurança, licença e supply chain avaliadas. |
| TL-08 Compatibility | Stack passou revisão de compatibilidade de conjunto. |
| TL-09 Testing | Toolchain materializa a estratégia da Etapa 06. |
| TL-10 UX | Tecnologias de interface suportam UI, UX e acessibilidade aprovadas. |
| TL-11 Lock-in | Lock-ins materiais estão explícitos e aceitos. |
| TL-12 Traceability | Decisões apontam para TECH-REQs/TDRs. |
| TL-13 Infra Handoff | Requisitos operacionais da stack estão claros. |

---

## 86. Síntese antes da canonização

Antes de gerar o artefato final do projeto, apresentar ao humano:

```text
TECH_RESEARCH_DATE
TECH_LEAD_READINESS

TECH-REQs CONSUMIDOS

DECISÕES PROPOSTAS
- linguagem
- runtime
- frameworks
- persistência
- contratos
- toolchain
- testes
- observabilidade de código
- dependências estruturantes

ALTERNATIVAS REJEITADAS

POCs

VERSÕES / SUPORTE

LICENÇAS

RISCOS

LOCK-INS

PENDÊNCIAS

DECISÕES CONJUNTAS COM INFRA

REQUISITOS PARA DEVOPS / INFRA
```

O humano pode:

- aprovar;
- rejeitar tecnologia;
- pedir nova alternativa;
- pedir POC;
- reduzir complexidade;
- alterar tolerância de lock-in;
- exigir reconciliação arquitetural.

---

## 87. Aprovação e canonização

Fluxo:

```text
PESQUISA
        ↓
SHORTLIST
        ↓
QUALIFICAÇÃO
        ↓
COMPARAÇÃO
        ↓
POC SE NECESSÁRIO
        ↓
SÍNTESE
        ↓
REVISÃO HUMANA
        ↓
APROVAÇÃO
        ↓
Visao_do_Tech_Lead.md
```

Aprovação da stack não cria contas, repositório, providers ou infraestrutura automaticamente.

---

## 88. Estrutura mínima do artefato de projeto

O projeto deve produzir `Visao_do_Tech_Lead.md` com estrutura equivalente a:

```markdown
---
document_id: DOC-TECH-LEAD
title: Visão do Tech Lead
status: canonical
version: 1.0.0
research_date: YYYY-MM-DD
depends_on:
  - DOC-06
  - DOC-07
next_document: 08_DevOps_e_Infraestrutura.md
---

# Visão do Tech Lead

## 1. Decisão executiva de stack
## 2. Contexto e horizonte
## 3. TECH-REQs consumidos
## 4. Critérios e hard constraints
## 5. Pesquisa tecnológica e fontes
## 6. Linguagem e runtime
## 7. Frameworks de aplicação
## 8. Persistência canônica
## 9. Persistência local, quando aplicável
## 10. Acesso a dados e migrations
## 11. Contratos, validação e codegen
## 12. API, async, cache e integrações tecnológicas
## 13. UI e Design System — implementação
## 14. Toolchain de qualidade
## 15. Estratégia concreta de testes
## 16. Observabilidade no código
## 17. Package manager, workspace e build
## 18. Dependências estruturantes
## 19. Segurança, licenças e supply chain
## 20. Política de versões e upgrades
## 21. Compatibilidade da stack
## 22. POCs e benchmarks
## 23. TDRs
## 24. Lock-ins e portabilidade
## 25. Riscos tecnológicos
## 26. Decisões adiadas
## 27. Decisões conjuntas com Infra
## 28. Requisitos para DevOps e Infraestrutura
## 29. Gates e Tech Lead Readiness
## 30. Handoff
```

Não forçar seção irrelevante.

Registrar `não aplicável` quando a ausência for uma decisão relevante.

---

## 89. Handoff para DevOps e Infraestrutura

O Tech Lead deve entregar:

```text
STACK OFICIAL
LINGUAGENS
RUNTIMES
FRAMEWORKS
ENGINES
TOOLCHAIN
VERSÕES / POLÍTICA
DEPENDÊNCIAS ESTRUTURANTES
COMANDOS CANÔNICOS
REQUISITOS DE BUILD
REQUISITOS DE RUNTIME
REQUISITOS DE STORAGE
REQUISITOS DE NETWORKING
REQUISITOS DE SEGREDOS
REQUISITOS DE OBSERVABILIDADE
REQUISITOS DE BACKUP COMPATÍVEIS COM A ENGINE
ARTEFATOS A PRODUZIR
PORTAS / PROTOCOLOS
LOCK-INS ACEITOS
LICENÇAS
POCs
TDRs
PENDÊNCIAS
```

DevOps e Infraestrutura deverão responder:

> **Como construir, testar, promover, hospedar, proteger, observar, recuperar e operar essa stack dentro dos requisitos arquiteturais, de custo e de confiabilidade aprovados?**

---

## 90. O que DevOps e Infraestrutura não podem fazer silenciosamente

A próxima etapa não pode trocar por conveniência:

- linguagem;
- runtime;
- framework;
- engine;
- biblioteca estruturante;
- política de versão;
- contrato tecnológico aprovado.

Se uma limitação operacional real inviabilizar a stack:

```text
DEVOPS / INFRA
        ↓
RESTRIÇÃO REAL
        ↓
IMPACTA STACK?
        ↓
SIM
        ↓
REABRIR TDR / VISÃO DO TECH LEAD
        ↓
IMPACTA ARQUITETURA?
        ↓
SIM
        ↓
REABRIR ADR / 07
```

---

## 91. Ready for Foundation ainda não é Ready for Codex

Depois desta etapa teremos:

```text
PRODUTO
UX
UI
POLÍTICAS DE DESENVOLVIMENTO
ARQUITETURA
STACK
```

Ainda faltam materialização operacional e baseline de entrega.

Portanto:

```text
TECH_STACK_APPROVED
≠
READY_FOR_CODEX
```

Antes do handoff de implementação ainda precisam existir, conforme o processo:

- DevOps/Infraestrutura;
- plano de fundação;
- backlog canônico;
- rastreabilidade;
- critérios de execução;
- baseline reconciliada.

---

## 92. Checklist rápido do Tech Lead

Antes de considerar a etapa pronta, perguntar:

1. Consigo ligar cada tecnologia estrutural a um requisito real?
2. Alguma escolha existe só porque é familiar?
3. Alguma tecnologia falha hard constraint?
4. Pesquisamos versão e suporte atuais?
5. Licenças foram verificadas?
6. A stack é coerente como conjunto?
7. Existe runtime ou linguagem redundante?
8. POCs provaram os pontos realmente arriscados?
9. Dependências estruturantes estão mantidas?
10. A estratégia de testes funciona de verdade nessa stack?
11. A acessibilidade continua viável?
12. Segurança e supply chain são controláveis?
13. Lock-ins estão explícitos?
14. Existe política de upgrade?
15. Infra consegue entender o que precisa hospedar sem adivinhar?
16. Alguma decisão deveria continuar adiada?
17. Alguma descoberta exige reabrir Arquitetura?

Se várias respostas forem incertas, a etapa ainda não está pronta.

---

## 93. Exemplo conceitual completo

```text
ARQUITETURA

TECH-REQ-001
cliente mobile iOS + Android

TECH-REQ-002
persistência local transacional

TECH-REQ-003
migration local obrigatória

TECH-REQ-004
build reproduzível

TECH-REQ-005
regra de domínio independente de UI

TECH-REQ-006
contract tests obrigatórios

        ↓

TECH LEAD

DECISÃO 1 — linguagem
candidatos A / B
A atende todos e reduz duplicação de contrato
B exige stack adicional
→ A selecionada

DECISÃO 2 — mobile framework
candidatos C / D
C precisa POC para capability nativa crítica
POC passa
→ C selecionado

DECISÃO 3 — persistência local
E / F
E não suporta requisito de migration com segurança
→ eliminado
F passa crash/restart POC
→ F selecionado

DECISÃO 4 — testes
unit + component + E2E
ferramentas G / H / I
→ stack de testes aprovada

        ↓

DEVOPS / INFRA
agora escolhe ambientes,
providers,
build executors,
secrets,
registry,
CI/CD,
backup e operação
```

O exemplo é estrutural.

Não prescreve tecnologias específicas.

---

## 94. Regra para projetos pequenos

Projetos simples não precisam simular uma grande organização.

A mesma pessoa pode exercer:

```text
ARQUITETO
TECH LEAD
DEVOPS
```

Mas as **responsabilidades documentais continuam separadas**.

Isso força a pessoa a responder perguntas diferentes em momentos diferentes.

Mesmo quando o executor é o mesmo:

```text
PAPEL
≠
PESSOA
```

---

## 95. Regra para projetos grandes

Em projetos maiores, a etapa pode exigir participação de:

- Tech Lead;
- Staff/Principal Engineer;
- especialista mobile;
- especialista web;
- dados;
- segurança;
- QA;
- SRE/Infra;
- responsável por acessibilidade.

A decisão final deve continuar coerente e possuir owner.

Comitê não substitui responsabilidade.

---

## 96. Divergência entre especialistas

Quando especialistas discordarem:

```text
VOLTE AOS TECH-REQs
        ↓
HARD CONSTRAINTS
        ↓
EVIDÊNCIA
        ↓
POC
        ↓
TRADE-OFF
```

Evitar decidir por senioridade isolada quando a questão pode ser testada.

---

## 97. Mudança futura de stack

Tecnologia pode ser substituída.

A documentação deve permitir compreender:

- por que foi escolhida;
- que requisitos satisfazia;
- qual risco era aceito;
- que gatilho justificaria mudança;
- qual parte da arquitetura não pode mudar silenciosamente.

Quando uma tecnologia é substituída:

```text
TDR ANTIGO
STATUS: SUPERSEDED
        ↓
NOVO TDR
        ↓
PLANO DE MIGRAÇÃO
        ↓
RASTREABILIDADE ATUALIZADA
```

Não apagar a história da decisão.

---

## 98. Condições típicas de revisão tecnológica

Reabrir decisão quando:

- tecnologia entra em EOL;
- licença muda materialmente;
- vulnerabilidade estrutural aparece;
- maintainers abandonam projeto;
- requisito arquitetural muda;
- workload ultrapassa capacidade comprovada;
- nova plataforma precisa ser suportada;
- custo total cresce além do aceitável;
- provider torna lock-in incompatível;
- atualização obrigatória quebra integração crítica;
- tooling impede controles de segurança;
- POC ou produção prova hipótese falsa.

---

## 99. Não confundir decisão tecnológica com implementação

A Visão do Tech Lead pode dizer:

```text
usar framework X
usar biblioteca Y
usar engine Z
usar test runner W
```

Mas não deve escrever o produto.

Ainda não é a etapa de:

- bootstrap completo;
- migrations reais;
- componentes de produção;
- endpoints;
- schemas físicos definitivos;
- configuração de cloud;
- pipelines;
- contas;
- secrets;
- deploy.

POCs descartáveis são a exceção controlada.

---

## 100. Princípio final

> **O Tech Lead não escolhe a tecnologia que parece melhor em abstrato. Ele escolhe a combinação tecnológica que melhor satisfaz a arquitetura aprovada neste horizonte, prova os riscos que importam, registra os trade-offs e entrega uma stack que DevOps e Infraestrutura conseguem operar sem redefinir silenciosamente o sistema.**

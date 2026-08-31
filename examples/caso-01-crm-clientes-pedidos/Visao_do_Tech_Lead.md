---
document_id: CASE-01-DOC-TECH-LEAD
title: Visão do Tech Lead — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: visao-tech-lead
research_date: 2026-08-31
consumes:
  - 06_Tecnicas_de_Desenvolvimento.md
  - 07_Engenharia_e_Arquitetura.md
next_document: 08_DevOps_e_Infraestrutura.md
tech_lead_readiness: SUFFICIENT_WITH_OPEN_QUESTIONS
ready_for_codex: false
---

# Visão do Tech Lead — CRM para gestão de clientes e pedidos

## 1. Propósito

Este documento materializa tecnologicamente a arquitetura aprovada do Caso 01.

Ele escolhe tecnologias concretas para o horizonte atual sem redefinir produto, UX, autoridade de dados, boundaries ou business case.

A pergunta central desta etapa foi:

> **Qual é a menor stack tecnológica capaz de preservar autorização por carteira, domínio comercial próprio, integração desacoplada com o TOTVS Protheus, auditabilidade, transações, recuperação e boa experiência web desktop/mobile, com TCO compatível com o horizonte aprovado?**

A existência deste documento não autoriza implementação pelo Codex.

---

## 2. Estado da pesquisa

```text
TECH_RESEARCH_DATE: 2026-08-31
TECH_RESEARCH_STATUS: COMPLETE_FOR_CURRENT_HORIZON
TECH_LEAD_READINESS: SUFFICIENT_WITH_OPEN_QUESTIONS
READY_FOR_CODEX: NO
```

As informações temporais de versão foram verificadas em fontes oficiais quando materiais.

As POCs deste caso são **simulações executadas para validar a metodologia**. Seus resultados representam evidência do cenário simulado, não prova de um ambiente Protheus real de cliente.

---

## 3. TECH-REQs consumidos

A stack precisa atender, entre outros, os seguintes requisitos derivados da arquitetura:

- experiência adequada em desktop e mobile;
- domínio independente da UI;
- persistência relacional transacional;
- autorização server-side com papel, recurso, ownership e contexto;
- idempotência e controle de concorrência;
- integração externa com timeout, retry e contratos verificáveis;
- jobs assíncronos duráveis quando necessários;
- representação explícita de freshness de dados ERP;
- unidade, contrato, integração, UI e E2E testáveis;
- acessibilidade verificável;
- observabilidade e auditoria sem exposição de payload sensível;
- migrations e compatibilidade progressivas;
- TCO compatível com o business case;
- backup/restore futuro compatível com RTO/RPO definidos;
- credenciais Protheus nunca expostas ao browser;
- suporte e manutenção adequados ao horizonte empresarial.

---

## 4. Hard constraints

Uma tecnologia é desqualificada se:

- exigir mudança das autoridades de dados CRM × Protheus;
- impedir autorização server-side adequada;
- não oferecer transações/constraints necessárias;
- obrigar duplicação de domínio entre frontend e backend;
- não possuir caminho de teste suficiente;
- introduzir provider obrigatório antes da etapa de Infra;
- exigir app nativo sem driver de produto;
- exigir broker/cache distribuído sem workload que justifique;
- não tiver manutenção, licença ou suporte compatíveis;
- aumentar materialmente o TCO sem resolver driver arquitetural.

---

# 5. Decisão executiva de stack

```text
CLIENTE
Web app responsivo

LINGUAGEM PRINCIPAL
TypeScript 6.0

RUNTIME BACKEND / TOOLCHAIN
Node.js 24 LTS

WEB
React 19.2
Vite 8.1
React Router 8
TanStack Query 5
React Aria

BACKEND
NestJS 11

CONTRATOS
REST / JSON
OpenAPI
Zod 4 / Standard Schema
openapi-typescript 7.x

PERSISTÊNCIA CANÔNICA
PostgreSQL 18
Prisma 8

AUTH
OIDC / OAuth 2.0
Authorization Code + PKCE
provider ainda conjunto com Infra

PROTHEUS
HTTPS/REST atrás de adapter / anti-corruption layer
metadata contract derivado do Protheus

TESTES
Vitest 4.1
Playwright

OBSERVABILIDADE NO CÓDIGO
OpenTelemetry no backend para traces e métricas

WORKSPACE
npm 11 + npm workspaces

LINT / FORMAT
ESLint 10
Prettier 3.9
```

---

# 6. Aplicação web responsiva no P0

A arquitetura exige desktop e mobile, mas não exige app nativo, app stores, background execution, push nativo ou offline-first completo.

Decisão:

```text
TL-DEC-001
P0 = WEB APP RESPONSIVO
STATUS: ACCEPTED
```

A mesma aplicação deverá adaptar composição e densidade para desktop, tablet e celular.

Aplicativo nativo é `DEFERRED_UNTIL_NEEDED`.

Gatilhos de revisão:

- offline robusto torna-se requisito;
- push/background tornam-se centrais;
- capacidade nativa específica passa a governar jornada;
- distribuição corporativa exige runtime nativo.

---

# 7. Linguagem: TypeScript 6.0

Em 2026-07-08 o TypeScript 7.0 foi lançado como versão estável e utiliza o novo compilador nativo. Entretanto, o release oficial registra que o TypeScript 7.0 não fornece ainda uma API programática estável e recomenda convivência com a API do TypeScript 6 para ferramentas que dela dependem.

Na data desta pesquisa, `typescript-eslint` ainda declarava suporte oficial até TypeScript 6 e passou a avisar quando TypeScript 7 é detectado. Portanto, adotar TypeScript 7 agora exigiria exceção/dual toolchain justamente numa baseline que prioriza previsibilidade.

Decisão:

```text
TDR-001 — TypeScript 6.0
STATUS: ACCEPTED
```

Razões:

- suporte atual do toolchain de lint tipado;
- menor complexidade de bootstrap;
- sem necessidade de manter TypeScript 6 API + TypeScript 7 compiler lado a lado;
- sem perda de capability material para o CRM.

TypeScript 7 fica como candidato obrigatório de revisão quando o ecossistema estrutural adotado oferecer suporte oficial suficiente.

```text
TS7_REVIEW_TRIGGER:
typescript-eslint e tooling estrutural suportarem oficialmente TS7
ou linha posterior com API/ecossistema estabilizado
```

Fontes pesquisadas:

- https://devblogs.microsoft.com/typescript/announcing-typescript-7-0/
- https://devblogs.microsoft.com/typescript/announcing-typescript-6-0/
- https://github.com/typescript-eslint/typescript-eslint/blob/main/packages/typescript-eslint/CHANGELOG.md

---

# 8. Runtime: Node.js 24 LTS

Na data da pesquisa, Node.js 24 é linha LTS e `24.20.0` é a atualização LTS publicada em 2026-08-26. Node 26 permanece Current.

Decisão:

```text
TDR-002 — Node.js 24 LTS
STATUS: ACCEPTED
```

A produção deverá utilizar linha LTS ativa/manutenção suportada.

Fonte:

- https://nodejs.org/en/about/previous-releases

---

# 9. Frontend

## 9.1 React 19.2

React 19.2 é a linha documentada como latest na data da pesquisa.

```text
TL-DEC-002
React 19.2
STATUS: ACCEPTED
```

Fonte:

- https://react.dev/versions

## 9.2 Vite 8.1

Vite 8.1 foi publicado em 2026-06-23.

```text
TL-DEC-003
Vite 8.1
STATUS: ACCEPTED
```

Fonte:

- https://vite.dev/blog/announcing-vite8-1

## 9.3 Rendering

O CRM é um produto autenticado e operacional. SEO e conteúdo público não governam o P0.

Decisão:

```text
SPA
STATUS: ACCEPTED
```

SSR/SSG/streaming ficam adiados até existir requisito mensurado.

## 9.4 Routing

```text
React Router 8
STATUS: ACCEPTED
VERSION_STATUS: VERIFY_AT_BOOTSTRAP
```

## 9.5 Server state

```text
TanStack Query 5
STATUS: ACCEPTED
```

Estado local de UI permanece em React.

Redux, Zustand ou outro store global são:

```text
DEFERRED_UNTIL_NEEDED
```

---

# 10. Design System no código

A Direção de UI exige identidade própria e acessibilidade sem herdar estética genérica de biblioteca.

Decisão:

```text
React Aria
+
CSS Custom Properties
+
CSS Modules
```

React Aria entra como primitive/comportamento acessível.

Tokens visuais permanecem propriedade do Design System.

Uma biblioteca visual pronta não pode reescrever a constituição visual do produto.

---

# 11. Backend

Decisão:

```text
TDR-003 — NestJS 11
STATUS: ACCEPTED
```

Razões:

- boa adequação a Node/TypeScript;
- módulos explícitos compatíveis com monólito modular;
- guards/pipes/interceptors úteis para boundaries;
- OpenAPI e validação possuem suporte maduro;
- permite manter domínio fora de decorators/framework quando disciplinado.

A aplicação deve impedir que controllers/providers se tornem o próprio domínio.

O adapter HTTP padrão é suficiente no P0.

Fastify ou outro adapter só será avaliado se performance mensurada justificar.

---

# 12. API e contratos

Decisão:

```text
TDR-004 — REST / JSON + OpenAPI
STATUS: ACCEPTED
```

Não existe driver atual para GraphQL, gRPC, WebSocket ou protocolo binário no core.

Estratégia:

```text
BOUNDARY INPUT
↓
Zod / Standard Schema
↓
NestJS
↓
OpenAPI
↓
openapi-typescript
↓
cliente tipado
↓
TanStack Query
```

Regra:

```text
TIPO DE COMPILE TIME
≠
VALIDAÇÃO DE INPUT NÃO CONFIÁVEL
```

Contratos externos sempre passam por validação runtime proporcional ao risco.

---

# 13. Persistência canônica

A arquitetura já decidiu que os dados canônicos do CRM precisam de persistência relacional e transacional.

Decisão:

```text
TDR-005 — PostgreSQL 18
STATUS: ACCEPTED
```

Na data da pesquisa, PostgreSQL 18.6 é o minor corrente publicado em 2026-08-13.

O documento canoniza a linha `18.x`; o bootstrap fixa o minor suportado corrente.

Fonte:

- https://www.postgresql.org/docs/current/release-18-6.html

---

# 14. Por que o CRM possui banco próprio

O banco do CRM **não existe para espelhar o Protheus**.

Ele existe porque o CRM possui estado cuja autoridade não pertence ao ERP.

Dados canônicos do CRM incluem:

- prospect antes de se tornar cliente ERP;
- histórico comercial;
- próxima ação;
- ownership de carteira;
- transferência de responsabilidade;
- sinais de atenção derivados;
- auditoria de ações próprias do CRM;
- idempotência de comandos próprios;
- estado técnico necessário à integração;
- preferências e rascunhos quando aprovados.

Dados cuja autoridade permanece no Protheus incluem:

- cliente formal ERP;
- identidade/código/loja ERP;
- pedido;
- faturamento;
- estoque;
- situação financeira ERP;
- metadados/dicionário dos campos Protheus.

Regra tecnológica:

```text
CRM DATABASE
= estado canônico do domínio CRM

NÃO
= cópia canônica do ERP
```

Se todo estado do CRM fosse gravado no Protheus, a redução de um banco apenas deslocaria o domínio CRM para customizações, tabelas e releases do ERP, aumentaria acoplamento e impediria o core comercial de degradar separadamente durante indisponibilidade do Protheus.

---

# 15. Acesso a dados: Prisma 8

Na data da pesquisa, Prisma 8 é a linha atual e seus guias atuais para PostgreSQL requerem Node.js 24 ou superior.

A escolha foi submetida a POC simulada antes de aceitação.

```text
TDR-006 — Prisma 8
STATUS: ACCEPTED_AFTER_SIMULATED_POC
```

Fonte:

- https://www.prisma.io/docs/prisma-orm/quickstart/postgresql

O ORM não recebe autoridade para esconder SQL, constraints ou concorrência.

Escape hatch para SQL explícito permanece permitido quando a regra/consulta justificar.

---

# 16. POC simulada — persistência

## TL-POC-001 — PostgreSQL 18 + Prisma 8

**Natureza:** simulação metodológica.

**Pergunta:** a combinação escolhida consegue materializar as invariantes do CRM sem esconder transação, constraints ou concorrência?

Cenário executado na simulação:

- migration inicial;
- migration aditiva;
- transaction envolvendo ownership + audit record;
- unique constraint para idempotency key;
- optimistic concurrency por versão de ownership;
- rollback de transaction em falha;
- query complexa com escape hatch SQL;
- teste de migration em banco limpo.

Resultado simulado:

```text
TL-POC-001: PASS
```

Consequência:

- Prisma 8 passa de `POC_REQUIRED` para `ACCEPTED_AFTER_SIMULATED_POC`;
- PostgreSQL continua autoridade de constraints/transações;
- migrações destrutivas continuam exigindo estratégia explícita.

Limitação:

A POC não prova performance de produção nem substitui teste em infraestrutura real.

---

# 17. Protheus: metadata-driven validation sem dicionário próprio

O CRM não terá um dicionário canônico próprio dos campos Protheus.

Para campos cuja autoridade pertence ao ERP, o contrato deve ser derivado dos metadados do ambiente Protheus por uma fronteira suportada.

Direção:

```text
PROTHEUS
↓
metadata endpoint / serviço suportado
↓
Protheus Metadata Adapter
↓
contrato normalizado do CRM
↓
backend validation
↓
frontend validation preventiva
```

O CRM pode materializar/cachear o contrato normalizado para disponibilidade e performance, mas isso **não transforma o cache em autoridade**.

Campos simples podem derivar propriedades como:

- tipo;
- tamanho;
- decimal;
- obrigatoriedade;
- label/descrição;
- picture simples;
- opções enumeradas simples.

Regras complexas, gatilhos e validações específicas do Protheus não serão automaticamente transpiladas para TypeScript.

Para elas:

```text
PROTHEUS_FINAL_VALIDATION = AUTHORITATIVE
```

quando houver escrita ERP futura.

---

# 18. POC simulada — metadata contract

## TL-POC-002 — Protheus metadata-driven validation

**Natureza:** simulação metodológica.

**Pergunta:** o CRM consegue adaptar metadados reais do Protheus e ajustar validação sem clonar o dicionário?

Cenário simulado:

1. campo Protheus retorna tipo caractere e tamanho 8;
2. adapter normaliza para `type=string`, `maxLength=8`;
3. frontend impede/explica 9 caracteres;
4. backend rejeita request com 9 caracteres;
5. metadata do cenário é alterado controladamente para tamanho 10;
6. contrato é atualizado/invalidado;
7. frontend/backend passam a aceitar até 10 sem mudança do código de regra do CRM;
8. campo contendo validação complexa é marcado como `server_authoritative` em vez de ter expressão AdvPL copiada para o CRM.

Resultado simulado:

```text
TL-POC-002: PASS
```

Decisão resultante:

```text
TDR-007 — Metadata Protheus é consumido e normalizado;
CRM não mantém dicionário Protheus canônico próprio.
STATUS: ACCEPTED
```

---

# 19. POC simulada — read contract do Protheus

## TL-POC-003 — ERP read contract

**Natureza:** simulação metodológica.

Cenários:

- consultar cliente formal;
- consultar pedidos;
- obter última atualização;
- distinguir `CURRENT`, `STALE` e `UNAVAILABLE`;
- validar empresa/filial/código/loja no contrato;
- simular timeout;
- rejeitar payload incompatível na boundary;
- manter credencial somente no backend.

Resultado:

```text
TL-POC-003: PASS_WITH_ENVIRONMENT_MAPPING_PENDING
```

Interpretação:

A direção REST/HTTPS e o adapter são válidos.

O mapeamento exato de endpoints, autenticação e customizações continua dependente do ambiente Protheus real.

---

# 20. Protheus integration

Decisão:

```text
TDR-008 — HTTPS/REST atrás de adapter / anti-corruption layer
STATUS: ACCEPTED
```

O CRM não consulta tabelas Protheus diretamente como integração padrão.

O adapter deve:

- validar payload externo;
- normalizar identidade ERP;
- mapear estados de freshness;
- isolar códigos/nomes externos;
- aplicar timeouts e política de retry de leitura;
- impedir que credenciais cheguem ao browser;
- expor apenas capacidades necessárias ao domínio CRM.

No P0, a integração permanece predominantemente read-only em relação às operações ERP.

---

# 21. POC simulada — degradação Protheus

## TL-POC-004 — CRM core continua com ERP indisponível

**Natureza:** simulação metodológica.

Cenário:

```text
Protheus indisponível
↓
consulta de pedido = ERP_UNAVAILABLE
↓
registro de interação CRM continua
↓
próxima ação continua
↓
carteira e histórico CRM continuam
↓
nenhum dado stale é apresentado como atual
```

Resultado:

```text
TL-POC-004: PASS
```

Isso confirma o motivo arquitetural do banco próprio do CRM e o isolamento da integração.

---

# 22. Async e jobs

Nenhum broker dedicado é necessário no P0.

```text
Kafka: REJECTED_FOR_CURRENT_HORIZON
RabbitMQ: DEFERRED
Redis queue: DEFERRED
```

Quando existir o primeiro workload assíncrono durável material, a primeira candidata será um mecanismo compatível com PostgreSQL e baixo TCO, com Graphile Worker como opção inicial a avaliar.

```text
ASYNC_ENGINE:
DEFERRED_UNTIL_NEEDED
```

Não instalar tecnologia antes da história que a exige.

---

# 23. Cache

```text
DEDICATED_CACHE:
NO_P0
```

Não existe gargalo medido que justifique Redis ou equivalente.

Caches locais/reconstruíveis podem existir dentro de uma capacidade específica — principalmente metadata/freshness ERP — desde que tenham autoridade e invalidação explícitas.

---

# 24. Autenticação e sessão

Decisão tecnológica de protocolo:

```text
OIDC / OAuth 2.0
Authorization Code + PKCE
```

O browser não é autoridade de autorização.

Direção de sessão:

```text
browser
↓
cookie Secure / HttpOnly
↓
backend
↓
identidade autenticada
↓
autorização contextual CRM
```

O identity provider concreto cruza Tech Lead e Infra.

```text
IDENTITY_PROVIDER:
DECISION_OWNER: JOINT_TECH_LEAD_INFRA
STATUS: PENDING
```

---

# 25. POC simulada — OIDC/session model

## TL-POC-005

**Natureza:** simulação metodológica.

Foi simulado um issuer OIDC compatível com Authorization Code + PKCE para provar:

- login;
- callback;
- criação da sessão backend;
- cookie Secure/HttpOnly;
- logout;
- sessão expirada;
- revogação percebida pelo backend;
- ausência de token sensível exposto como autoridade no frontend.

Resultado:

```text
TL-POC-005: PASS_PROTOCOL_MODEL
```

Isso prova o modelo de protocolo, **não escolhe o provider**.

---

# 26. Toolchain de testes

Decisão:

```text
TDR-009 — Vitest + Playwright
STATUS: ACCEPTED
```

Camadas:

| Camada | Ferramenta / contrato |
| --- | --- |
| domínio | Vitest |
| aplicação/backend | Vitest |
| UI/componentes | Vitest + tooling de renderização apropriado |
| contratos | OpenAPI + schemas + contract tests |
| integração | Vitest + dependências controladas |
| E2E | Playwright |
| browsers | Chromium + Firefox + WebKit |
| mobile web | emulação + device real seletivo |

---

# 27. POC simulada — contrato OpenAPI e cliente

## TL-POC-006

**Natureza:** simulação metodológica.

Cenário:

- endpoint Nest gera contrato OpenAPI;
- schema de entrada possui validação runtime;
- `openapi-typescript` gera tipos/cliente;
- React consome contrato sem duplicar DTO manual;
- quebra incompatível do schema falha no teste/compilação apropriado.

Resultado:

```text
TL-POC-006: PASS
```

---

# 28. POC simulada — experiência web

## TL-POC-007

**Natureza:** simulação metodológica.

Spike da jornada crítica:

```text
Hoje
→ prioridade
→ cliente
→ registrar interação
→ próxima ação
```

Foi avaliado no cenário:

- desktop;
- viewport mobile;
- teclado;
- foco visível;
- touch;
- estado vencido sem depender de cor;
- dialog com retorno de foco;
- screen-reader smoke em componentes estruturais.

Resultado:

```text
TL-POC-007: PASS_FOR_FRAMEWORK_CAPABILITY
```

A POC prova capacidade da stack, não substitui validação de UX do produto final.

---

# 29. Observabilidade no código

Decisão:

```text
TDR-010 — OpenTelemetry no backend
STATUS: ACCEPTED
```

Na data da pesquisa:

- traces JavaScript: Stable;
- metrics JavaScript: Stable;
- logs JavaScript: Development;
- instrumentação browser: experimental.

Portanto:

```text
BACKEND
OpenTelemetry traces + metrics

FRONTEND
não usar OTel browser como dependência estrutural do P0
```

O backend/provedor que armazenará a telemetria pertence a Infra.

Fonte:

- https://opentelemetry.io/docs/languages/js/

---

# 30. Workspace e package manager

Decisão:

```text
TDR-011 — npm 11 + npm workspaces
STATUS: ACCEPTED
```

Não adicionar Nx/Turborepo no bootstrap sem problema mensurado.

Estrutura conceitual inicial:

```text
apps/
  web/
  api/

packages/
  ui/
  contracts/
  config/
```

Essa estrutura é direção de workspace, não licença para compartilhar entidades internas do domínio com a UI.

`packages/contracts` contém contratos deliberados, não todo o modelo do backend.

---

# 31. Lint e format

Direção:

```text
ESLint 10
Prettier 3.x
```

O bootstrap deverá fixar as versões exatas compatíveis.

A escolha de TypeScript 6 nesta baseline evita forçar `typescript-eslint` a uma combinação TypeScript 7 ainda não oficialmente suportada na data da pesquisa.

---

# 32. Política de versões

A documentação canoniza tecnologia e linha suportada.

O bootstrap fixa patch/minor exatos em manifests/lockfiles.

```text
VERSION_STATUS: VERIFY_AT_BOOTSTRAP
```

Política:

- Node: linha LTS ativa aprovada;
- TypeScript: 6.0 enquanto o gate TS7 estiver aberto;
- React: 19.2;
- Vite: 8.1;
- NestJS: 11.x;
- PostgreSQL: 18.x no minor suportado corrente;
- Prisma: 8.x compatível;
- demais dependências estruturantes: minor/patch reconfirmados no bootstrap.

`latest` não é política de versão.

---

# 33. TDRs

| TDR | Decisão | Status |
| --- | --- | --- |
| TDR-001 | TypeScript 6.0 | ACCEPTED |
| TDR-002 | Node.js 24 LTS | ACCEPTED |
| TDR-003 | React/Vite no cliente + NestJS backend | ACCEPTED |
| TDR-004 | REST/JSON + OpenAPI | ACCEPTED |
| TDR-005 | PostgreSQL 18 | ACCEPTED |
| TDR-006 | Prisma 8 | ACCEPTED_AFTER_SIMULATED_POC |
| TDR-007 | metadata Protheus consumido/normalizado; sem dicionário canônico duplicado | ACCEPTED |
| TDR-008 | HTTPS/REST + Protheus adapter | ACCEPTED |
| TDR-009 | Vitest + Playwright | ACCEPTED |
| TDR-010 | OpenTelemetry backend | ACCEPTED |
| TDR-011 | npm workspaces | ACCEPTED |
| TDR-012 | sem cache/broker dedicado no P0 | ACCEPTED |
| TDR-013 | OIDC/OAuth2 como protocolo; provider em Infra | ACCEPTED_PROTOCOL / PROVIDER_PENDING |

---

# 34. Alternativas rejeitadas ou adiadas

## TypeScript 7

```text
STATUS: DEFERRED
```

Motivo: versão estável, mas o tooling de lint tipado ainda exige compatibilidade com API TypeScript 6 na data desta decisão. Reavaliar após suporte oficial da cadeia estrutural.

## .NET / Spring

```text
STATUS: REJECTED_FOR_CURRENT_HORIZON
```

São alternativas maduras, mas introduzem linguagem/runtime adicional sem driver que compense o TCO neste produto pequeno.

## App nativo

```text
STATUS: DEFERRED
```

Não existe capability nativa obrigatória no P0.

## GraphQL

```text
STATUS: REJECTED_FOR_CURRENT_HORIZON
```

REST/OpenAPI atende os contratos atuais com menor complexidade.

## Redis

```text
STATUS: DEFERRED
```

Sem gargalo medido.

## Broker dedicado

```text
STATUS: DEFERRED
```

Sem workload que justifique.

## Event sourcing

Não pertence à stack porque já foi descartado arquiteturalmente no horizonte atual.

---

# 35. Metadata contract e consistência documental

As POCs simularam uma descoberta importante:

```text
METADATA-DRIVEN VALIDATION
≠
CLONAR DICIONÁRIO PROTHEUS
```

A descoberta **não contradiz** a arquitetura 07 vigente, porque a arquitetura já estabelece:

- Protheus como autoridade de seus dados;
- adapter/anti-corruption layer;
- contratos externos voláteis isolados;
- CRM com estado canônico próprio apenas para seu domínio.

Ela refina tecnologicamente essa fronteira.

Por isso não foi necessária uma reversão arquitetural imediata.

A reconciliação final deverá verificar se o `07_Engenharia_e_Arquitetura.md` merece uma versão editorial posterior para explicitar essa decisão, sem alterar sua autoridade substantiva.

---

# 36. Lock-ins

## PostgreSQL

```text
LOCK_IN: ACCEPTABLE
```

Engine madura, padrão aberto e ampla portabilidade entre providers.

## Prisma

```text
LOCK_IN: CONDITIONAL_ACCEPTABLE
```

O domínio não pode depender de tipos internos do ORM fora da camada de persistência.

## NestJS

```text
LOCK_IN: CONDITIONAL_ACCEPTABLE
```

Controllers/DI não podem invadir entidades/regras centrais.

## React

```text
LOCK_IN: ACCEPTABLE_FOR_UI
```

A arquitetura visual e regras de produto permanecem independentes.

## Identity provider

Ainda não avaliado porque pertence à decisão conjunta com Infra.

---

# 37. Segurança e supply chain

A stack precisa permitir:

- lockfile reproduzível;
- secret scanning;
- dependency review;
- SAST compatível;
- SBOM quando exigido;
- atualização automatizável;
- pinning de dependências estruturantes;
- ausência de segredo no bundle;
- redaction de telemetria;
- validação runtime de input externo.

Nenhuma biblioteca estrutural pode ser adicionada sem licença e manutenção verificadas.

---

# 38. Decisões conjuntas com Infra

A próxima etapa ainda precisa decidir:

- provider de hospedagem web/API;
- serviço gerenciado de PostgreSQL;
- região;
- identity provider;
- modelo de conectividade entre CRM e Protheus;
- DNS/TLS;
- secret store;
- CI/CD;
- observability backend;
- backups/PITR concretos;
- ambientes;
- custo e budgets;
- mecanismo de acesso ao Protheus quando ele estiver em rede privada;
- política operacional de refresh/cache do metadata Protheus.

---

# 39. Requisitos para DevOps e Infraestrutura

A stack entrega os seguintes requisitos operacionais:

```text
RUNTIME API
Node.js 24 LTS

WEB BUILD
artefato estático Vite/React

DATABASE
PostgreSQL 18.x

MIGRATIONS
Prisma 8

SECRETS
OIDC + Protheus + database nunca no browser/repo

NETWORK
backend precisa alcançar Protheus por canal autorizado

OBSERVABILITY
OpenTelemetry traces/metrics no backend

RTO/RPO
materializar targets definidos na arquitetura

ARTEFATO
build reproduzível e identificável

ENVIRONMENTS
separação explícita entre staging e production

DATA
nenhum dado real de produção em ambiente de desenvolvimento/teste sem política específica
```

---

# 40. Gates da etapa

| Gate | Estado |
| --- | --- |
| TL-01 Inputs | PASS |
| TL-02 Research atual | PASS |
| TL-03 Hard constraints | PASS |
| TL-04 Alternatives | PASS |
| TL-05 POCs | PASS no cenário simulado; limitações registradas |
| TL-06 Versions | PASS com VERIFY_AT_BOOTSTRAP |
| TL-07 Security/licenças | SUFFICIENT para stack; reconfirmar patches no bootstrap |
| TL-08 Compatibility | PASS no cenário simulado |
| TL-09 Testing | PASS |
| TL-10 UX/a11y | PASS_FOR_FRAMEWORK_CAPABILITY |
| TL-11 Lock-in | PASS |
| TL-12 Traceability | PASS |
| TL-13 Infra handoff | PASS |

---

# 41. Pendências

Permanecem abertas, sem bloquear Infra:

1. identity provider concreto;
2. provider/hosting;
3. conectividade real com o ambiente Protheus;
4. endpoints e autenticação exatos do Protheus do cliente;
5. política concreta de refresh/cache de metadata ERP;
6. patches exatos da stack no momento do bootstrap;
7. decisão futura sobre TypeScript 7 quando o ecossistema de tooling estiver oficialmente compatível.

Cada uma possui etapa de resolução conhecida.

---

# 42. Readiness

```text
TECH_RESEARCH: COMPLETE
TECH_POC_SIMULATION: COMPLETE
STACK_DIRECTION: APPROVED
HARD_CONSTRAINT_FAILURE: NONE
TECH_LEAD_READINESS: SUFFICIENT_WITH_OPEN_QUESTIONS
READY_FOR_DEVOPS_INFRA: YES
READY_FOR_CODEX: NO
```

`SUFFICIENT_WITH_OPEN_QUESTIONS` é adequado porque nenhuma pendência atual impede a materialização de Infraestrutura, mas provider, rede Protheus e patches ainda precisam ser decididos nas etapas apropriadas.

---

# 43. Validação da metodologia

O caso confirmou que a etapa do Tech Lead não deve simplesmente escolher a versão mais nova.

Na pesquisa, TypeScript 7 estava estável, porém a cadeia de lint tipado ainda não possuía suporte oficial equivalente. A metodologia permitiu preferir TypeScript 6 por coerência da stack, mesmo que TypeScript 7 seja tecnologicamente mais novo e mais rápido.

As POCs simuladas também refinaram a fronteira Protheus:

```text
CAMPO COM TAMANHO 8 NO PROTHEUS
↓
metadata contract
↓
validação preventiva na UI
↓
validação autoritativa do backend CRM para o contrato conhecido
↓
Protheus permanece autoridade final de suas regras
```

E mostraram por que o banco CRM existe:

```text
BANCO CRM
não replica ERP

BANCO CRM
preserva estado cujo domínio é do CRM
```

Resultado:

```text
TECH_LEAD_METHOD_VALIDATION: PASS
STACK_BY_PREFERENCE: NO
CURRENT_RESEARCH: YES
POC_RESULT_FABRICATION_AS_REAL_WORLD: NO
SIMULATION_LABELING: YES
ARCHITECTURE_VIOLATED: NO
READY_FOR_CODEX: NO
```

---

# 44. Handoff

A próxima etapa recebe uma stack suficientemente definida para responder:

> **Onde e como construir, promover, hospedar, proteger, observar, recuperar e operar essa stack, inclusive como o backend alcançará o Protheus e como serão isolados staging e production?**

Próximo documento:

`08_DevOps_e_Infraestrutura.md`

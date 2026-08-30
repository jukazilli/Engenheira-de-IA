---
document_id: PROCESS-09-PLANO-FUNDACAO
title: Plano de Fundação
status: draft-methodology
version: 0.1.0
stage: plano-fundacao
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
  - Visao_do_Tech_Lead.md
  - 08_DevOps_e_Infraestrutura.md
produces: 09_Plano_de_Fundacao.md
next_stage: 10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
---

# 09 — Plano de Fundação

## 1. Propósito

A etapa **Plano de Fundação** transforma as decisões técnicas e operacionais aprovadas nas etapas anteriores em uma **sequência ordenada, verificável, reversível e rastreável de preparação da base do projeto**.

A pergunta central desta etapa é:

> **Qual é a menor sequência segura de ações necessárias para transformar as decisões aprovadas em uma fundação reproduzível, observável, recuperável e pronta para receber desenvolvimento funcional sem depender de conhecimento oral, contas improvisadas, segredos escondidos ou infraestrutura não provada?**

Esta etapa existe porque:

```text
ARQUITETURA APROVADA
+
STACK APROVADA
+
INFRAESTRUTURA APROVADA

NÃO SIGNIFICA

FUNDAÇÃO PRONTA PARA DESENVOLVER
```

Entre decisão e implementação existe um conjunto de ações de bootstrap que precisa ser tratado como engenharia real.

Exemplos:

- criar ownership organizacional;
- configurar contas de função;
- registrar domínio e billing quando aplicável;
- criar organização e repositório;
- aplicar branch protection;
- inicializar workspace;
- fixar versões;
- criar ambientes;
- configurar identidade entre CI e cloud;
- configurar secrets;
- criar banco e migrations iniciais;
- aplicar baseline de autorização;
- configurar observabilidade;
- configurar backups;
- provar restore;
- configurar budgets e alertas;
- provar build e deploy;
- provar rollback;
- documentar acessos, runbooks e procedimentos.

O Plano de Fundação **não implementa funcionalidades de produto**.

Ele também não deve provisionar recursos irreversíveis apenas porque o documento foi gerado.

A saída desta etapa é um **plano canônico de bootstrap** que será incorporado ao Backlog Canônico e executado somente quando a baseline documental estiver reconciliada e houver autorização correspondente.

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
Visão do Tech Lead
        ↓
08 DevOps e Infraestrutura
        ↓
09 PLANO DE FUNDAÇÃO
        ↓
10 Backlog Canônico, Rastreabilidade e Plano de Entrega
        ↓
11 Matriz Operacional de Rastreabilidade
        ↓
BASELINE RECONCILIADA
        ↓
HANDOFF PARA CODEX
        ↓
EXECUÇÃO DA FUNDAÇÃO
        ↓
IMPLEMENTAÇÃO FUNCIONAL
```

A etapa 08 responde:

> **Onde e como a stack será operada?**

A etapa 09 responde:

> **Em qual ordem a base aprovada deve ser criada e quais evidências provam que cada parte está pronta?**

O Backlog Canônico transformará os itens de fundação e de produto em uma sequência operacional completa de entrega.

---

## 3. Origem desta etapa

Esta etapa não possuía um documento equivalente independente no processo original utilizado como referência para a reconstrução da metodologia.

No processo anterior, ações de setup apareciam misturadas com Arquitetura, Infraestrutura e plano de implementação.

A metodologia refinada separa deliberadamente:

```text
07 ENGENHARIA E ARQUITETURA
“qual estrutura o sistema precisa possuir?”

VISÃO DO TECH LEAD
“com quais tecnologias?”

08 DEVOPS E INFRAESTRUTURA
“onde e como operar?”

09 PLANO DE FUNDAÇÃO
“qual sequência cria e prova a base?”

10 BACKLOG CANÔNICO
“qual é a ordem global de execução e entrega?”
```

Essa separação evita dois problemas recorrentes.

Primeiro:

```text
CRIAR CONTAS E REPOSITÓRIOS CEDO DEMAIS
        ↓
DECISÕES AINDA MUDAM
        ↓
RETRABALHO / CUSTO / CREDENCIAIS ÓRFÃS
```

Segundo:

```text
COMEÇAR FEATURE
        ↓
DESCOBRIR QUE
CI NÃO EXISTE
BACKUP NÃO EXISTE
RESTORE NÃO FOI TESTADO
SEGREDOS ESTÃO LOCAIS
PRODUÇÃO NÃO TEM OWNER
```

O Plano de Fundação existe para impedir que o projeto aprenda tarde demais que sua base operacional era apenas presumida.

---

## 4. Princípio central

> **Fundação não é o que existe antes do código. Fundação é o conjunto mínimo de capacidades que permite alterar, testar, entregar, observar e recuperar o sistema com segurança.**

Portanto:

```text
REPOSITÓRIO CRIADO
≠
FUNDAÇÃO PRONTA
```

Da mesma forma:

```text
DEPLOY FUNCIONOU UMA VEZ
≠
PIPELINE PROVADO
```

E:

```text
BACKUP ESTÁ HABILITADO
≠
RECUPERAÇÃO PROVADA
```

A fundação precisa produzir **evidência executável**, não apenas configuração declarada.

---

## 5. O que esta etapa decide

Esta etapa decide:

- quais itens de fundação precisam existir;
- dependências entre esses itens;
- ordem recomendada de execução;
- quais itens podem executar em paralelo;
- quais itens bloqueiam outros;
- quais recursos precisam existir antes de cada ambiente;
- quais controles devem nascer antes de dados reais;
- quais provas cada item deve produzir;
- quais ações são reversíveis;
- quais ações exigem aprovação humana explícita;
- quais contas ou permissões são necessárias;
- quais dados podem existir durante a fundação;
- quais custos podem ser ativados em cada passo;
- quais gates autorizam progressão;
- quais itens pertencem obrigatoriamente ao Backlog Canônico;
- quando a fundação pode ser considerada pronta.

---

## 6. O que esta etapa não decide

Ela não decide novamente:

- problema do produto;
- escopo P0/P1/P2;
- regra de negócio;
- jornada;
- sistema visual;
- arquitetura;
- boundaries;
- linguagem;
- framework;
- engine de banco;
- provider;
- região;
- topologia;
- política de CI/CD;
- SLO;
- RTO/RPO;
- tecnologia de observabilidade;
- política de backup.

Esses elementos chegam das etapas anteriores.

O Plano de Fundação **materializa a sequência**, não reabre decisões silenciosamente.

Se uma execução revelar incompatibilidade real:

```text
FND ITEM
        ↓
INCOMPATIBILIDADE REAL
        ↓
QUAL DECISÃO FOI AFETADA?
        ↓
08 INFRA?
TECH LEAD?
07 ARQUITETURA?
        ↓
RECONCILIAR NA CAMADA CORRETA
```

---

## 7. Pré-requisitos obrigatórios

Antes de iniciar o Plano de Fundação, o ChatGPT deve consumir integralmente os documentos anteriores e confirmar que existem decisões suficientes para planejar o bootstrap sem adivinhação.

No mínimo, precisa conhecer:

### 7.1. De Engenharia e Arquitetura

- drivers arquiteturais;
- atributos de qualidade;
- boundaries;
- invariantes;
- trust boundaries;
- requirements de dados;
- requisitos de consistência;
- RTO/RPO quando aplicáveis;
- observabilidade requerida;
- ambientes requeridos;
- requisitos de backup/restore;
- gatilhos de escala;
- ADRs;
- `TECH-REQs`.

### 7.2. Da Visão do Tech Lead

- linguagem;
- runtime;
- frameworks;
- engine de banco;
- persistência local quando aplicável;
- package manager;
- workspace/monorepo tooling;
- test runners;
- build tooling;
- bibliotecas estruturantes;
- política de versões;
- TDRs;
- requisitos entregues para Infra.

### 7.3. De DevOps e Infraestrutura

- providers;
- regiões;
- ambientes;
- contas;
- ownership;
- identidade de workload;
- estratégia de CI/CD;
- estratégia de artifacts;
- secrets;
- observabilidade;
- logging;
- backup;
- restore;
- custos;
- budgets;
- alertas;
- IaC quando aplicável;
- IDRs;
- decisões conjuntas pendentes.

Se uma dessas áreas estiver materialmente indefinida, o Plano de Fundação deve registrar:

```text
FOUNDATION_READINESS: INSUFFICIENT
```

em vez de inventar configuração.

---

## 8. Ativação da etapa

Exemplo:

```text
Consuma integralmente os documentos canônicos do projeto até
08_DevOps_e_Infraestrutura.md e execute a etapa 09 — Plano de Fundação.

Transforme as decisões aprovadas em uma sequência FND rastreável,
com dependências, evidências, riscos, gates e condições de parada.

Primeiro apresente a síntese no chat.
Não execute provisionamento nem crie contas ainda.
```

O ChatGPT deve responder com handshake equivalente a:

```text
PROCESS_STATUS: ACTIVE
CURRENT_STAGE: PLANO_DE_FUNDACAO
INPUT_DOCUMENT: 08_DevOps_e_Infraestrutura.md
FOUNDATION_STATUS: PLANNING
CANONICAL_OUTPUT: 09_Plano_de_Fundacao.md
NEXT_STAGE: 10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
```

---

## 9. Plano não é execução

A separação é obrigatória:

```text
PLANEJADO
≠
AUTORIZADO
≠
EXECUTADO
≠
VERIFICADO
```

Estados recomendados para cada item:

```text
PLANNED
BLOCKED
READY
AUTHORIZED
IN_PROGRESS
IMPLEMENTED
VERIFIED
FAILED
ROLLED_BACK
SUPERSEDED
CANCELLED
```

A canonização do documento coloca os itens em `PLANNED`.

Não significa autorização automática para:

- criar conta paga;
- registrar domínio;
- inserir cartão;
- contratar plano;
- gerar segredo;
- criar projeto de produção;
- alterar DNS;
- criar credencial de loja;
- fazer deploy público;
- executar migration em ambiente real;
- carregar dados reais.

Essas ações precisam aparecer explicitamente no Backlog e obedecer aos controles aplicáveis.

---

## 10. Unidade operacional: FND

Cada item de fundação recebe um ID estável:

```text
FND-001
FND-002
FND-003
...
```

IDs removidos não devem ser reutilizados.

Um `FND` representa uma capacidade fundacional verificável.

Não deve representar uma intenção vaga como:

```text
FND-003 — Configurar cloud
```

Deve ser específico o suficiente para possuir condição de saída.

Exemplo:

```text
FND-003 — Criar identidade OIDC entre CI e ambiente de staging
```

---

## 11. Contrato mínimo de um FND

Todo item material deve possuir:

| Campo | Conteúdo |
| --- | --- |
| ID | `FND-xxx` |
| Nome | Resultado fundacional objetivo |
| Objetivo | Por que o item existe |
| Origem | Documento/ADR/TDR/IDR/requisito que o exige |
| Ambiente | local / preview / staging / production / global |
| Owner | papel responsável |
| Executor | humano / agente / automação / provider |
| Dependências | FNDs que precisam estar verificados antes |
| Pré-condições | permissões, contas, decisões, dados permitidos |
| Ações | passos necessários em nível adequado |
| Evidência | prova objetiva de conclusão |
| Segurança | controles específicos |
| Dados | classificação e dados permitidos |
| Custo | custo ativado ou esperado |
| Reversibilidade | como desfazer ou desativar |
| Risco | efeito de erro |
| Condição de parada | quando não continuar |
| Status inicial | normalmente `PLANNED` |

---

## 12. Resultado, não clique

O Plano de Fundação deve preferir itens orientados a resultado.

Evitar:

```text
1. Clique em Settings.
2. Clique em New Project.
3. Digite X.
```

como contrato principal.

Isso envelhece rapidamente.

Preferir:

```text
FND-010
Resultado:
ambiente staging criado na região aprovada,
sem dados reais,
com billing e ownership corretos,
com ID registrado e acesso mínimo configurado.

Evidência:
- projeto acessível pelos owners aprovados;
- região conferida;
- budget ativo;
- nenhum segredo em repositório;
- identificadores documentados.
```

Passos específicos de UI podem aparecer em runbooks temporários quando necessários.

---

## 13. Taxonomia de fundação

Os itens podem ser classificados para facilitar leitura e dependências.

Sugestão:

```text
ORG   ownership e contas
GIT   repositório e governança
WRK   workspace e toolchain
ENV   ambientes
IAM   identidade e acesso
SEC   secrets e segurança
DAT   dados e migrations
CICD  build, CI e promoção
OBS   observabilidade
BKP   backup e restore
OPS   operação e runbooks
CST   custo e billing
EXT   integrações/sandboxes
REL   release foundation
DOC   documentação e handoff
```

O ID permanece `FND-xxx`.

A categoria é metadado, não substitui o ID.

---

## 14. Dependências explícitas

O Plano de Fundação deve produzir um grafo de dependências.

Exemplo:

```text
FND-001 Ownership
        ↓
FND-002 Contas de função
        ↓
FND-003 Organização Git
        ↓
FND-004 Repositório
        ↓
FND-005 Proteção de branch
        ↓
FND-006 Workspace base
        ↓
FND-007 CI mínimo
        ↓
FND-008 Identidade CI→Cloud
        ↓
FND-009 Staging
        ↓
FND-010 Deploy de prova
```

Mas outros itens podem executar em paralelo:

```text
FND-009 STAGING
        ├── FND-011 Observabilidade
        ├── FND-012 Budget alerts
        └── FND-013 Backup
```

O plano deve identificar:

- dependência dura;
- dependência recomendada;
- paralelismo possível;
- gate compartilhado.

---

## 15. Caminho crítico

O ChatGPT deve identificar o **caminho crítico da fundação**.

Caminho crítico é a sequência de itens cuja ausência impede todo o progresso posterior.

Exemplo:

```text
OWNERSHIP
→ REPOSITÓRIO
→ WORKSPACE
→ CI
→ IDENTIDADE
→ STAGING
→ BUILD
→ DEPLOY
→ OBSERVAR
→ RECUPERAR
```

Não confundir caminho crítico com ordem de todas as tarefas.

Um projeto pode executar documentação, budgets e setup de dashboards em paralelo quando seguro.

---

## 16. Fases recomendadas

A fundação pode ser organizada em fases.

### Fase A — Governança e ownership

Objetivo:

> garantir que recursos críticos tenham proprietário, recuperação e cobrança definidas antes da criação.

Pode incluir:

- entidade proprietária;
- owners;
- e-mails de função;
- MFA;
- recovery codes;
- password manager;
- billing owner;
- security contact;
- domínio;
- matriz inicial de acesso.

### Fase B — Fonte e workspace

Pode incluir:

- organização Git;
- repositório;
- branch padrão;
- proteção;
- CODEOWNERS;
- signing/provenance quando aplicável;
- package manager;
- workspace;
- runtime pin;
- formatter;
- lint;
- typecheck;
- test harness;
- build mínimo;
- instruções para agentes.

### Fase C — Ambientes e identidade

Pode incluir:

- projetos por ambiente;
- regiões;
- identidades;
- service accounts;
- OIDC/workload identity;
- secrets;
- DNS temporário;
- políticas de acesso.

### Fase D — Dados

Pode incluir:

- engine gerenciada aprovada;
- schema inicial;
- migrations;
- seeds sintéticos;
- grants;
- RLS/authz quando aplicável;
- data classification;
- migration test;
- upgrade test.

### Fase E — CI/CD e artifacts

Pode incluir:

- PR checks;
- build;
- artifact registry;
- preview;
- staging promotion;
- release permissions;
- migration workflow;
- rollback workflow.

### Fase F — Observabilidade e operação

Pode incluir:

- logs;
- métricas;
- traces;
- crash reporting;
- dashboards;
- alertas;
- correlation IDs;
- redaction;
- access policy;
- runbooks.

### Fase G — Continuidade

Pode incluir:

- backups;
- off-site quando exigido;
- restore test;
- RPO/RTO evidence;
- secret rotation test;
- disaster recovery básico;
- incident procedure.

### Fase H — Gate de fundação

Prova integrada de que uma pessoa autorizada consegue:

```text
CLONAR
→ CONFIGURAR
→ BUILDAR
→ TESTAR
→ PROVISIONAR/ACESSAR STAGING
→ DEPLOYAR ARTEFATO DE PROVA
→ OBSERVAR
→ REVERTER
→ RESTAURAR
```

sem credencial escondida nem conhecimento oral obrigatório.

---

## 17. Fundação mínima por horizonte

Nem todo projeto precisa da mesma fundação.

### 17.1. Protótipo descartável

Pode aceitar:

- infraestrutura mínima;
- sem produção real;
- dados sintéticos;
- sem SLA;
- sem operação 24x7.

Mas precisa registrar claramente que **não é fundação de produção**.

### 17.2. Alpha interna

Normalmente exige:

- ownership;
- repositório;
- CI básico;
- ambiente isolado;
- dados sintéticos;
- observabilidade básica;
- budget;
- rollback;
- nenhum segredo informal.

### 17.3. Beta com dados reais

Normalmente exige também:

- ambiente de produção separado;
- backup gerenciado;
- restore testado;
- retenção definida;
- autorização negativa testada;
- MFA;
- alertas;
- runbooks;
- incident handling;
- termos comerciais validados;
- política de dados reais;
- observabilidade sanitizada;
- budget/owner.

### 17.4. Produção material

Pode exigir:

- SLO formal;
- on-call;
- PITR;
- DR ampliado;
- threat model atualizado;
- exercícios de restore;
- gestão formal de vulnerabilidades;
- rotação de segredos;
- capacity planning;
- compliance adicional.

O horizonte vem do projeto, não desta metodologia.

---

## 18. Ownership antes de recursos

Nenhum recurso crítico deve nascer sem responder:

```text
QUEM É OWNER?
QUEM É OWNER DE RECUPERAÇÃO?
QUEM PAGA?
QUEM PODE ALTERAR?
QUEM PODE PROMOVER?
QUEM REVOGA ACESSO?
O QUE ACONTECE SE O OWNER SAIR?
```

Itens fundacionais típicos:

```text
FND-001 — Confirmar entidade proprietária
FND-002 — Criar contas de função
FND-003 — Configurar MFA e recuperação
FND-004 — Registrar matriz inicial de acesso
FND-005 — Configurar billing owner e budgets
```

Contas pessoais podem ser usadas apenas quando forem deliberadamente aceitas e houver caminho documentado de transferência.

---

## 19. Repositório como fundação

O repositório não é apenas local onde o código fica.

Ele deve nascer com propriedades compatíveis com `06_Tecnicas_de_Desenvolvimento.md`.

O Plano pode incluir:

- branch padrão;
- proteção;
- PR obrigatório;
- review;
- CODEOWNERS;
- status checks;
- secret scanning;
- dependency review;
- regras de merge;
- templates;
- issue conventions;
- instruções de IA;
- SECURITY;
- CONTRIBUTING;
- ADR location;
- runbook location.

Exemplo:

```text
FND-010 — Criar repositório canônico
FND-011 — Aplicar proteção da branch principal
FND-012 — Configurar ownership de código
FND-013 — Criar baseline documental do repositório
```

---

## 20. Workspace reproduzível

O workspace inicial precisa provar que uma máquina limpa consegue reproduzir o ambiente de desenvolvimento.

Deve registrar:

- versões pinadas;
- package manager;
- runtime;
- lockfile;
- comandos canônicos;
- env example sem segredos;
- build;
- lint;
- typecheck;
- testes;
- geração de contratos quando aplicável.

Evidência recomendada:

```text
CLONE LIMPO
        ↓
BOOTSTRAP DOCUMENTADO
        ↓
INSTALL REPRODUZÍVEL
        ↓
LINT VERDE
        ↓
TYPECHECK VERDE
        ↓
TEST VERDE
        ↓
BUILD VERDE
```

---

## 21. Skeleton não é feature

A fundação pode criar estruturas mínimas necessárias para provar build e deploy.

Exemplos válidos:

- app shell vazio;
- endpoint `/health` técnico;
- página de status interna;
- migration inicial;
- schema vazio;
- integração de telemetry;
- feature flag infrastructure;
- configuração de dependency injection;
- contratos mínimos de bootstrap.

Mas não deve começar:

- onboarding;
- treino;
- checkout;
- feed;
- dashboards de produto;
- regra de negócio.

Regra:

> **Código de prova da fundação existe para provar a plataforma, não para antecipar escopo funcional.**

---

## 22. Ambientes

Cada ambiente aprovado em `08_DevOps_e_Infraestrutura.md` deve possuir itens específicos de fundação.

Exemplo:

```text
FND-020 — Criar ambiente preview
FND-021 — Criar ambiente staging
FND-022 — Criar ambiente production
```

Mas `production` pode permanecer sem dados e sem tráfego até o gate apropriado.

Para cada ambiente registrar:

- provider;
- região;
- owner;
- billing;
- domínio;
- identidade;
- secrets;
- dados permitidos;
- observabilidade;
- backup;
- retenção;
- política de acesso;
- política de deploy;
- condição de destruição.

---

## 23. Produção vazia é válida

Criar um recurso chamado `production` não significa que ele está autorizado para dados reais.

Usar estados:

```text
PRODUCTION_RESOURCE_CREATED
PRODUCTION_CONTROLLED
PRODUCTION_DATA_READY
PRODUCTION_TRAFFIC_READY
```

Exemplo:

```text
Projeto de banco de produção existe
        ↓
backup ainda não foi provado
        ↓
PRODUCTION_DATA_READY = false
```

Isso impede a interpretação perigosa:

```text
“já existe produção, então pode usar.”
```

---

## 24. Identidade entre sistemas

Credenciais long-lived devem ser evitadas quando houver mecanismo aprovado de identidade federada.

O Plano pode incluir itens como:

```text
FND-025 — Criar identidade de CI para staging
FND-026 — Configurar trust OIDC
FND-027 — Limitar permissões do deploy
FND-028 — Provar deploy sem secret estático
```

Quando chave estática for inevitável:

- justificar;
- escopar;
- registrar owner;
- definir rotação;
- registrar expiração quando possível;
- garantir que não apareça em logs.

---

## 25. Secrets

A fundação precisa provar que segredo não depende de:

- `.env` pessoal;
- chat;
- e-mail;
- bloco de notas;
- variável copiada manualmente entre máquinas;
- commit revertido;
- screenshot.

Cada segredo material deve ter:

```text
NOME LÓGICO
OWNER
AMBIENTE
ORIGEM
CONSUMIDOR
STORE
ESCOPO
ROTAÇÃO
REVOGAÇÃO
AUDITORIA
```

Não registrar o valor do segredo no documento.

---

## 26. Dados fundacionais

A fundação deve conter somente o necessário para provar o sistema de dados.

Pode incluir:

- migrations iniciais;
- schemas;
- extensions aprovadas;
- roles;
- grants;
- políticas de autorização;
- tabelas de infraestrutura;
- seeds sintéticos;
- testes de migration;
- testes de rollback/forward fix quando aplicável.

Dados reais não devem ser necessários para provar a base.

---

## 27. Seeds sintéticos

Seeds precisam ser:

- determinísticos quando útil;
- pequenos;
- representativos;
- livres de dados reais;
- reproduzíveis;
- seguros para screenshots e logs.

Um seed pode representar:

- usuários fictícios;
- tenants fictícios;
- permissões;
- estados vazios;
- estados de erro;
- limites.

Não copiar produção para acelerar setup.

---

## 28. Baseline de autorização

Quando autorização é material, a fundação deve provar o comportamento negativo antes de desenvolver features.

Exemplo:

```text
SEM POLÍTICA EXPLÍCITA
        ↓
ACESSO NEGADO
```

Provas possíveis:

- tenant A não lê tenant B;
- usuário sem role não executa comando;
- segredo privilegiado não está no cliente;
- rota administrativa exige autorização;
- identidade de CI não possui permissão administrativa desnecessária.

O objetivo não é implementar todas as regras futuras.

É provar a **postura de segurança da fundação**.

---

## 29. CI mínimo antes de feature

Antes da primeira feature, o projeto deve conseguir executar automaticamente os gates estruturais aprovados.

Dependendo da stack:

```text
format
lint
typecheck
unit tests
contract validation
secret scan
dependency check
build
```

A fundação pode começar com um subconjunto coerente e expandir posteriormente, desde que nenhum gate obrigatório da etapa 06 seja esquecido.

Cada gate precisa responder:

- quando executa;
- o que bloqueia;
- em qual SHA;
- quais permissões possui;
- qual evidência deixa.

---

## 30. Build de prova

A fundação deve produzir pelo menos um artefato real usando a stack aprovada.

O objetivo é provar:

```text
STACK
+
WORKSPACE
+
DEPENDÊNCIAS
+
CONFIGURAÇÃO
+
CI

FUNCIONAM JUNTOS
```

Não basta que cada decisão pareça compatível isoladamente.

Exemplos de evidência:

- bundle web;
- imagem OCI;
- build mobile de desenvolvimento;
- pacote serverless;
- binário;
- migration package.

---

## 31. Artifact identity

Quando aplicável, registrar:

```text
SOURCE_SHA
BUILD_ID
ARTIFACT_DIGEST
VERSION
AMBIENTE
```

Isso permite provar:

```text
O QUE FOI TESTADO
=
O QUE FOI PROMOVIDO
```

Quando a tecnologia recompila por ambiente, registrar o mecanismo de equivalência aprovado em `08`.

---

## 32. Deploy de prova

O primeiro deploy deve validar plataforma e pipeline, não feature.

Provar:

- identidade;
- permissões;
- artifact;
- configuração;
- rede;
- secrets;
- health check;
- logs;
- rollback;
- acesso controlado.

A prova pode ser privada.

Não existe necessidade metodológica de publicar um produto vazio na internet.

---

## 33. Rollback antes de precisar dele

A fundação precisa provar pelo menos um caminho de reversão compatível com a tecnologia.

Exemplos:

- promover artefato anterior;
- desativar flag;
- reverter configuração;
- restaurar deployment revision;
- forward-fix de migration;
- restaurar snapshot quando apropriado.

Não esperar o primeiro incidente para descobrir o mecanismo.

---

## 34. Migrations

Quando existe banco versionado, a fundação deve provar:

```text
BANCO LIMPO
→ MIGRATION 001
→ ESTADO ESPERADO
```

E, quando material:

```text
ESTADO ANTERIOR
→ UPGRADE
→ ESTADO NOVO
```

Também precisa confirmar:

- migration não depende de clique manual;
- ordem é determinística;
- estado aplicado é rastreável;
- migration já aplicada não é reescrita;
- credencial de migration é separada da aplicação quando necessário.

---

## 35. Observabilidade antes da feature

A base deve conseguir responder pelo menos:

```text
QUAL RELEASE ESTÁ RODANDO?
ESTÁ SAUDÁVEL?
ESTÁ GERANDO ERROS?
QUANTO TEMPO LEVA?
CONSEGUIMOS CORRELACIONAR UMA OPERAÇÃO?
```

Mesmo um shell vazio precisa provar que a telemetria funciona.

Não é necessário criar dashboards finais de produto nesta etapa.

---

## 36. Sanitização da telemetria

A prova de observabilidade deve inspecionar o que realmente foi enviado.

Não basta configurar uma biblioteca e presumir segurança.

Verificar:

- headers;
- query strings;
- bodies;
- user attributes;
- stack traces;
- breadcrumbs;
- session replay;
- crash reports;
- trace attributes.

A fundação deve provar a política de minimização aprovada.

---

## 37. Backup

Itens de backup podem ser separados por ativo:

```text
FND-040 — Backup do banco
FND-041 — Backup de storage crítico
FND-042 — Backup de configuração/IaC
FND-043 — Export off-site quando exigido
```

Cada item registra:

- frequência;
- retenção;
- criptografia;
- localização;
- owner;
- custo;
- RPO atendido.

---

## 38. Restore é um item independente

Não marcar backup como verificado enquanto restore não for provado quando o risco exigir.

Exemplo:

```text
FND-040 BACKUP
        ↓
IMPLEMENTED

FND-044 RESTORE TEST
        ↓
VERIFIED

FND-GATE-DATA-READY
        ↓
PASS
```

A prova de restore pode usar ambiente isolado.

---

## 39. Prova de recuperação

O restore deve validar algo além de “o serviço iniciou”.

Quando aplicável:

- schema;
- constraints;
- contagens;
- grants;
- autorização;
- integridade de ledger;
- checksums;
- objetos;
- versão;
- migrations;
- capacidade de aplicação iniciar.

Registrar tempo observado para comparar com RTO.

---

## 40. Budgets antes de consumo

Itens que podem gerar cobrança precisam possuir controle antes de receber carga relevante.

Exemplo:

```text
FND-050 — Criar budget do ambiente staging
FND-051 — Criar alerta 50%
FND-052 — Criar alerta 80%
FND-053 — Registrar owner da fatura
```

Percentuais e valores são específicos do projeto.

O princípio é:

> **capacidade sem visibilidade de custo não está completamente fundada.**

---

## 41. Free tier não é gate

Usar free tier pode ser correto.

Mas:

```text
ESTÁ GRÁTIS
≠
ESTÁ APTO PARA PRODUÇÃO
```

A prontidão depende de:

- backup;
- suporte necessário;
- retenção;
- SLA quando material;
- quotas;
- suspensão;
- termos;
- limites de auth;
- limites de build;
- capacidade de recuperação.

---

## 42. Integrações externas

Não criar todas as contas de integração no início por ansiedade de completude.

Cadastrar provider quando:

- existe decisão aprovada;
- a fundação ou onda correspondente precisa dele;
- owner está definido;
- sandbox existe ou a exposição é aceitável;
- custo está entendido;
- segredo pode ser armazenado corretamente.

Exemplo:

```text
INTEGRAÇÃO DA ONDA 5

NÃO PRECISA

SER CADASTRADA NA FASE 0
```

---

## 43. Sandbox-first

Quando provider oferece sandbox apropriado, a fundação deve preferi-lo para provar:

- auth;
- limites;
- erros;
- timeout;
- callback;
- webhook;
- schema;
- observabilidade;
- secret handling.

Sem usar conta ou dados de produção desnecessariamente.

---

## 44. Feature flags fundacionais

Se a arquitetura depende de liberação progressiva, a capacidade de feature flag pode fazer parte da fundação.

Mas não confundir:

```text
INFRAESTRUTURA DE FLAG
```

com:

```text
FLAGS DE FEATURES QUE AINDA NÃO EXISTEM
```

A fundação prova:

- fonte autoritativa;
- default seguro;
- leitura;
- atualização autorizada;
- auditoria;
- kill switch quando necessário.

---

## 45. Domínio e DNS

Mudanças de domínio e DNS podem ser relevantes e difíceis de reverter rapidamente.

Planejar:

- owner do domínio;
- registrador;
- MFA;
- recovery;
- DNS provider;
- registros necessários;
- TTL;
- validação;
- certificados;
- rollback.

Não transferir domínio crítico para conta pessoal sem registro explícito de risco.

---

## 46. Mobile

Projetos mobile podem precisar de fundação adicional:

- bundle/application IDs;
- contas Apple/Google;
- owners;
- certificados;
- signing;
- development builds;
- preview builds;
- production profiles;
- push credentials;
- deep link domains;
- crash symbols/source maps;
- store metadata mínima quando necessária.

Credenciais de loja e signing são ativos críticos.

Devem possuir owner e recuperação.

---

## 47. Web

Projetos web podem precisar provar:

- build;
- hosting;
- headers de segurança;
- HTTPS;
- DNS;
- cache;
- SPA/static/SSR behavior conforme stack;
- fallback de rota;
- source maps;
- robots/indexing por ambiente;
- preview access control.

Staging não deve ser indexado por busca pública por acidente quando isso não for desejado.

---

## 48. Backend/API

Pode exigir:

- runtime;
- health/readiness;
- container/function package;
- config validation;
- auth baseline;
- rate limit foundation;
- contract generation;
- API version prefix;
- correlation IDs;
- error envelope;
- graceful shutdown;
- migration connectivity.

Não precisa implementar endpoints de negócio.

---

## 49. Jobs e filas

Se processamento assíncrono é fundacional:

provar:

- producer;
- consumer;
- retry;
- visibility/lease;
- dead-letter strategy;
- idempotência básica;
- observabilidade;
- kill switch;
- limites de concorrência.

Pode usar mensagem sintética de prova.

---

## 50. Segurança da cadeia de entrega

O plano deve incluir os controles aprovados em `06` e `08` que precisam existir desde o início.

Possíveis itens:

- secret scanning;
- dependency review;
- SAST;
- artifact provenance;
- SBOM;
- action pinning;
- permissions mínimas;
- protected environments;
- approval para produção;
- signed artifacts quando exigido.

Não adicionar controle apenas por lista de compliance.

Cada controle precisa de relação com risco ou política aprovada.

---

## 51. Documentação fundacional

Antes de declarar a base pronta, precisam existir instruções suficientes para outra pessoa autorizada operar a fundação.

Dependendo do projeto:

- README;
- CONTRIBUTING;
- SECURITY;
- ADRs;
- TDRs;
- IDRs;
- environment inventory;
- access matrix;
- secret inventory sem valores;
- runbooks;
- cost ledger;
- recovery procedure;
- comandos de bootstrap;
- instruções para agentes de IA.

---

## 52. Nenhuma credencial escondida

Gate obrigatório:

> **um clone limpo e uma pessoa autorizada, com os acessos documentados, devem conseguir reproduzir o ambiente sem pedir uma chave que só existe na máquina de outra pessoa.**

Se isso não for verdade:

```text
FOUNDATION_READINESS != SUFFICIENT
```

---

## 53. Human-in-the-loop

Alguns FNDs podem ser executados por agente.

Outros exigem ação humana.

Classificar:

```text
AUTOMATABLE
HUMAN_REQUIRED
JOINT
EXTERNAL_WAIT
```

Exemplos `HUMAN_REQUIRED`:

- aceitar termos;
- inserir dados de cobrança;
- validar documento de empresa;
- criar conta de loja;
- aprovar produção;
- alterar DNS crítico;
- guardar recovery codes;
- conceder autorização sensível.

Um agente não deve simular que essas ações ocorreram.

---

## 54. Ações irreversíveis ou sensíveis

Marcar explicitamente:

```text
REVERSIBILITY: EASY
REVERSIBILITY: MODERATE
REVERSIBILITY: HARD
REVERSIBILITY: IRREVERSIBLE
```

Itens de alto impacto podem exigir:

```text
HUMAN_APPROVAL_REQUIRED: true
```

Exemplos:

- contratar plano anual;
- transferir domínio;
- apagar ambiente;
- executar migration destrutiva;
- publicar app;
- mover dados reais;
- rotacionar chave crítica.

---

## 55. Condições de parada

A execução futura de um FND deve parar quando:

- decisão superior está ausente;
- provider divergiu do documento aprovado;
- preço mudou materialmente;
- região não está disponível;
- precisa de permissão não autorizada;
- precisa de dado real não aprovado;
- precisa aceitar termo não revisado quando material;
- exige mudança arquitetural;
- exige nova tecnologia;
- risco de perda de dados não possui recuperação;
- secret precisaria ser exposto de forma insegura;
- ação sairia do ambiente previsto;
- custo excederia budget;
- resultado não pode ser verificado.

A resposta correta é:

```text
STOP
→ registrar bloqueio
→ identificar decisão necessária
→ retornar à camada correta
```

Não improvisar.

---

## 56. Evidência

Cada FND precisa produzir evidência proporcional ao risco.

Tipos de evidência:

```text
COMMAND_OUTPUT
CI_RUN
SCREENSHOT_SANITIZED
CONFIG_EXPORT
RESOURCE_ID
TEST_REPORT
RESTORE_REPORT
LOG_SANITIZED
DASHBOARD
POLICY_CHECK
COST_RECORD
RUNBOOK
MANUAL_VERIFICATION
```

Evitar evidência que exponha:

- segredo;
- token;
- dados pessoais;
- e-mail sensível;
- IDs desnecessários;
- conteúdo real.

---

## 57. Evidência não é narrativa

```text
“configurei e parece certo”
```

não é evidência suficiente para item crítico.

Preferir:

```text
TESTE EXECUTADO
        ↓
RESULTADO
        ↓
ARTEFATO
        ↓
CRITÉRIO ATENDIDO
```

---

## 58. Gate vs item

Um item cria ou configura uma capacidade.

Um gate determina se um conjunto de capacidades permite avançar.

Exemplo:

```text
FND-040 backup
FND-041 restore test
FND-042 retention
        ↓
FND-GAT-005 DATA_RECOVERY_READY
```

O gate não substitui os itens.

---

## 59. Identificação dos gates

Usar:

```text
FND-GAT-001
FND-GAT-002
FND-GAT-003
...
```

IDs não devem ser reutilizados.

---

## 60. Gates recomendados

### FND-GAT-001 — Ownership Ready

Prova:

- owners definidos;
- MFA;
- recovery;
- billing owner;
- contas críticas inventariadas.

### FND-GAT-002 — Repository Ready

Prova:

- repositório canônico;
- branch protegida;
- review/checks;
- documentação mínima;
- secret scanning quando requerido.

### FND-GAT-003 — Workspace Ready

Prova:

- clone limpo;
- install reproduzível;
- versões pinadas;
- lint/type/test/build mínimos verdes.

### FND-GAT-004 — Staging Ready

Prova:

- ambiente isolado;
- identidade;
- secrets;
- deploy de prova;
- dados sintéticos;
- observabilidade mínima.

### FND-GAT-005 — Data Safety Ready

Prova:

- migrations;
- autorização baseline;
- backup;
- restore;
- dados sintéticos;
- retenção aplicável.

### FND-GAT-006 — Delivery Ready

Prova:

- CI;
- artifact;
- deploy;
- promotion;
- rollback;
- permissions.

### FND-GAT-007 — Operability Ready

Prova:

- logs;
- métricas;
- traces quando requeridos;
- alertas;
- dashboards;
- runbooks;
- correlation.

### FND-GAT-008 — Cost Ready

Prova:

- budget;
- alertas;
- owner;
- custos iniciais registrados;
- limites conhecidos.

### FND-GAT-009 — Production Data Ready

Somente quando aplicável.

Prova:

- produção separada;
- backup/restore;
- segurança;
- autorização negativa;
- retenção;
- termos;
- observabilidade;
- incident response;
- aprovação humana.

### FND-GAT-010 — Foundation Complete

Prova integrada de que a base está pronta para receber entregas funcionais.

---

## 61. Fundação concluída não significa produto pronto

```text
FOUNDATION_COMPLETE
≠
FEATURE_COMPLETE
≠
BETA_READY
≠
PRODUCTION_READY
```

Fundação significa apenas:

> **o sistema possui uma base segura e reproduzível para começar a implementar as fatias funcionais aprovadas.**

---

## 62. Plano de fundação e Backlog Canônico

Os itens `FND` não devem ficar isolados neste documento.

O próximo estágio deve incorporá-los ao backlog global.

Exemplo:

```text
FND-001 Ownership
FND-002 Repositório
FND-003 Workspace
FND-004 CI
FND-005 Staging
...

ANTES DE

US-001 primeira fatia funcional
```

Mas nem todo FND precisa obrigatoriamente terminar antes de qualquer feature.

A relação depende do risco.

Por exemplo:

```text
OBSERVABILIDADE BÁSICA
→ antes da primeira feature

PRODUÇÃO DATA READY
→ pode ocorrer antes do beta,
não necessariamente antes da primeira feature em staging
```

O Backlog Canônico resolverá essa ordem de forma explícita.

---

## 63. Fundação progressiva

Evitar uma “fase de infraestrutura” infinita.

A fundação deve ser mínima e proporcional.

Princípio:

```text
CAPACIDADE FUNDACIONAL
        ↓
PROVAR O NECESSÁRIO
        ↓
LIBERAR PRÓXIMA FATIA
        ↓
EXPANDIR QUANDO DRIVER EXIGIR
```

Não construir antecipadamente:

- cluster complexo;
- multi-region;
- data lake;
- service mesh;
- warehouse;
- observabilidade enterprise;
- DR de segundos;
- dezenas de ambientes;

sem necessidade aprovada.

---

## 64. Foundation runway

O plano deve definir quanta fundação é necessária antes da primeira fatia funcional.

Pode usar categorias:

```text
FOUNDATION_ZERO
obrigatório antes de qualquer desenvolvimento funcional

FOUNDATION_BEFORE_P0
obrigatório antes de liberar o módulo P0 correspondente

FOUNDATION_BEFORE_REAL_DATA
obrigatório antes de dados reais

FOUNDATION_BEFORE_PRODUCTION
obrigatório antes de tráfego de produção

FOUNDATION_LATER
ativado por gatilho
```

Isso evita bloquear aprendizado por controles que só serão necessários meses depois.

---

## 65. Exemplo de runway

```text
FOUNDATION_ZERO
- ownership
- repo
- workspace
- CI básico
- staging sintético
- secrets
- observabilidade básica

BEFORE_REAL_DATA
- backup
- restore
- retenção
- privacy controls
- incident runbook

BEFORE_PRODUCTION
- production environment
- budgets
- alertas
- release approval
- recovery proof
```

O projeto define seu próprio recorte.

---

## 66. Foundation spike

Quando uma decisão só pode ser validada executando parte da fundação, pode existir um spike.

Exemplo:

```text
FND-SPIKE-001
Provar que a combinação de runtime + build + provider
produz artifact dentro do limite arquitetural.
```

O spike:

- tem hipótese;
- tem timebox;
- tem critério de sucesso;
- não vira produção automaticamente;
- pode resultar em reconciliação do TDR/IDR/ADR.

---

## 67. Brownfield

Em projeto existente, o Plano de Fundação não deve presumir que estamos começando do zero.

Primeiro mapear:

- contas existentes;
- owners;
- repositórios;
- branches;
- CI;
- ambientes;
- domínios;
- secrets;
- banco;
- migrations;
- backups;
- observabilidade;
- runbooks;
- billing;
- acessos;
- dívida operacional.

Depois classificar cada capacidade:

```text
KEEP
HARDEN
MIGRATE
REPLACE
REMOVE
CREATE
```

---

## 68. Brownfield: não quebrar operação para “organizar”

Migrações fundacionais devem ser incrementais quando possível.

Exemplo:

```text
SECRET LOCAL ATUAL
        ↓
CRIAR SECRET STORE
        ↓
PUBLICAR SUPORTE NOVO
        ↓
MIGRAR CONSUMIDORES
        ↓
REVOGAR SEGREDO ANTIGO
```

Em vez de:

```text
APAGAR TUDO
        ↓
“AGORA VAMOS CONFIGURAR CERTO”
```

---

## 69. Projetos pequenos

A metodologia não exige uma equipe DevOps.

Uma pessoa pode assumir vários papéis.

O que não deve desaparecer são as responsabilidades.

Em um projeto solo:

```text
MESMA PESSOA
        ↓
PODE SER
Tech Lead
Infra Owner
Release Owner
Security Owner
```

mas deve executar conscientemente os gates correspondentes.

---

## 70. Projetos grandes

Projetos maiores podem dividir o Plano de Fundação por streams:

```text
STREAM GIT
STREAM PLATFORM
STREAM DATA
STREAM SECURITY
STREAM MOBILE
STREAM OBSERVABILITY
STREAM RELEASE
```

Mas precisam compartilhar:

- IDs FND;
- dependências;
- gates;
- owners;
- evidências;
- baseline.

---

## 71. ChatGPT durante a criação do plano

O ChatGPT deve:

1. consumir todas as decisões anteriores;
2. montar inventário de capacidades fundacionais;
3. identificar o que já existe;
4. separar greenfield/brownfield;
5. criar FNDs;
6. ordenar dependências;
7. identificar caminho crítico;
8. classificar runway;
9. registrar owners esperados;
10. definir evidências;
11. definir reversibilidade;
12. definir condições de parada;
13. definir gates;
14. expor pendências;
15. apresentar síntese ao humano antes de canonizar.

---

## 72. ChatGPT durante a execução futura

Quando um FND for executado posteriormente, o agente deve:

```text
LER FND
        ↓
VALIDAR PRÉ-CONDIÇÕES
        ↓
CONFIRMAR AUTORIZAÇÃO
        ↓
EXECUTAR MENOR PASSO
        ↓
COLETAR EVIDÊNCIA
        ↓
VERIFICAR RESULTADO
        ↓
ATUALIZAR STATUS
```

Não avançar automaticamente para o próximo item sensível.

---

## 73. Execução por Codex

Alguns FNDs poderão ser executados pelo Codex depois do handoff.

Exemplos possíveis:

- inicializar workspace;
- criar config;
- adicionar scripts;
- criar workflows;
- adicionar testes;
- criar IaC;
- criar migrations;
- criar documentação;
- executar verificações.

Mas o Codex não deve receber autorização implícita para:

- criar conta externa;
- aceitar termo;
- inserir billing;
- acessar produção;
- apagar recurso;
- criar segredo humano;
- fazer deploy público;
- alterar DNS;

sem permissão explícita e ferramenta autorizada.

---

## 74. Ready for Codex por FND

Um item fundacional pode possuir:

```text
FND_EXECUTION_READINESS: INSUFFICIENT
FND_EXECUTION_READINESS: READY_WITH_HUMAN_STEP
FND_EXECUTION_READINESS: READY_FOR_CODEX
FND_EXECUTION_READINESS: HUMAN_ONLY
```

Isso será útil no Backlog Canônico.

---

## 75. Segurança de prompts e contexto

O plano deve impedir que agentes recebam valores sensíveis em prompts.

Em vez de:

```text
“Use a chave sk_live_...”
```

usar:

```text
“Consuma o secret lógico PAYMENT_PROVIDER_KEY
pelo mecanismo aprovado do ambiente.”
```

A documentação descreve **identidade do segredo**, não seu conteúdo.

---

## 76. Drift

A fundação precisa considerar drift entre estado declarado e estado real.

Se IaC estiver aprovado:

- importar recursos existentes quando necessário;
- planejar antes de aplicar;
- detectar mudanças manuais;
- definir quem pode alterar fora do IaC.

Se IaC não estiver sendo usado:

- manter inventário;
- registrar mudanças materiais;
- reduzir configuração manual irreproduzível.

---

## 77. Foundation lock

Quando a fundação é aprovada, criamos uma baseline do plano.

Isso não significa que recursos nunca mudam.

Significa:

```text
MUDANÇA FUNDACIONAL MATERIAL
        ↓
IDENTIFICAR ORIGEM
        ↓
IDR / TDR / ADR?
        ↓
RECONCILIAR
        ↓
ATUALIZAR FND
        ↓
PROPAGAR PARA BACKLOG/MATRIZ
```

Mudanças silenciosas em infraestrutura devem ser evitadas.

---

## 78. Rastreabilidade

Exemplo completo:

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
INFRA-REQ-007
        ↓
IDR-003
        ↓
FND-031
        ↓
FND-GAT-006
        ↓
BACKLOG ITEM
        ↓
IMPLEMENTAÇÃO
        ↓
EVIDÊNCIA
```

O objetivo não é burocracia.

É conseguir explicar **por que uma configuração existe**.

---

## 79. Taxonomia sugerida

```text
FND-xxx       item fundacional
FND-GAT-xxx   gate de fundação
FND-SPIKE-xxx prova técnica de fundação
FND-RISK-xxx  risco fundacional, quando útil
FND-EV-xxx    evidência, quando houver catálogo próprio
```

Não multiplicar tipos se o projeto não precisar.

---

## 80. Riscos de fundação

Riscos comuns:

| Risco | Efeito |
| --- | --- |
| owner único | perda de acesso |
| billing sem alerta | custo inesperado |
| secrets locais | vazamento / indisponibilidade |
| CI permissivo | supply chain comprometida |
| staging com dados reais | exposição |
| backup não testado | falsa sensação de segurança |
| branch sem proteção | mudança não revisada |
| drift | ambiente não reproduzível |
| produção sem runbook | recuperação lenta |
| provider configurado diferente da decisão | baseline falsa |

Cada risco material precisa de controle ou aceitação explícita.

---

## 81. Dívida fundacional

Pode existir quando:

- não viola segurança crítica;
- não impede recuperação necessária;
- é conhecida;
- possui owner;
- possui prazo/gatilho;
- é reversível.

Exemplo aceitável:

```text
alpha interna usa restore manual
até volume X
```

Exemplo não aceitável:

```text
“depois vemos backup”
antes de dados reais
```

quando RPO exige recuperação.

---

## 82. Itens adiados por gate

Um FND pode ser planejado mas não executado imediatamente.

Registrar:

```text
TRIGGER
```

Exemplos:

```text
FND-090 — habilitar PITR
TRIGGER: RPO necessário < 24h

FND-091 — separar worker
TRIGGER: fila rompe SLO por 3 janelas

FND-092 — criar preview DB por PR
TRIGGER: migrations paralelas tornam staging compartilhado inseguro
```

Assim evitamos infraestrutura prematura sem perder o plano de evolução.

---

## 83. Critério de qualidade do plano

Um bom Plano de Fundação permite que uma pessoa competente responda:

1. o que precisa ser criado;
2. por que precisa existir;
3. em qual ordem;
4. quem é responsável;
5. o que depende de quê;
6. qual ação exige humano;
7. qual ação gera custo;
8. qual ação é difícil de reverter;
9. quais dados são permitidos;
10. qual evidência prova conclusão;
11. qual gate libera avanço;
12. o que ainda está pendente;
13. quando a fundação está pronta para cada horizonte.

Se isso não for possível, o plano ainda está incompleto.

---

## 84. Anti-padrões

### 84.1. Setup por memória

```text
“eu lembro como configurei o outro projeto.”
```

Não é processo reproduzível.

### 84.2. Conta pessoal como arquitetura

```text
“criei tudo na minha conta porque era mais rápido.”
```

Sem ownership e transferência, cria risco operacional.

### 84.3. Produção precoce

Criar recursos de produção e imediatamente carregar dados reais sem gates.

### 84.4. Secret copy-paste

Copiar segredo manualmente entre chats, máquinas e CI.

### 84.5. Backup ornamental

Backup habilitado sem restore.

### 84.6. CI de fachada

Pipeline verde porque não executa os controles importantes.

### 84.7. IaC teatral

Escrever Terraform/Pulumi apenas para dizer que existe IaC, sem state, plan, drift e ownership.

### 84.8. Infra infinita

Passar meses “preparando escala” antes da primeira fatia vertical.

### 84.9. Setup com feature escondida

Implementar regra de produto dentro da fundação para “aproveitar”.

### 84.10. Checklist sem evidência

Marcar `[x]` porque alguém disse que fez.

---

## 85. Readiness do Plano de Fundação

Usar:

```text
FOUNDATION_PLAN_READINESS: INSUFFICIENT
FOUNDATION_PLAN_READINESS: SUFFICIENT_WITH_OPEN_QUESTIONS
FOUNDATION_PLAN_READINESS: SUFFICIENT
```

`SUFFICIENT_WITH_OPEN_QUESTIONS` é válido quando as pendências:

- possuem owner;
- possuem momento de decisão;
- não impedem ordenar a fundação;
- não exigem invenção durante execução.

---

## 86. Condições para `SUFFICIENT`

O plano está suficientemente pronto quando:

1. decisões técnicas anteriores foram consumidas;
2. capacidades fundacionais foram inventariadas;
3. FNDs possuem IDs estáveis;
4. dependências estão claras;
5. caminho crítico está identificado;
6. runway está classificado;
7. ambientes possuem sequência;
8. ownership vem antes dos recursos críticos;
9. segredos possuem plano seguro;
10. CI/build/deploy têm prova definida;
11. dados/migrations têm prova definida;
12. observabilidade tem prova definida;
13. backup/restore têm prova definida quando aplicável;
14. custos e budgets possuem plano;
15. ações humanas estão identificadas;
16. ações irreversíveis possuem aprovação explícita;
17. evidências estão definidas;
18. gates estão definidos;
19. itens futuros possuem triggers quando adiados;
20. o Backlog pode consumir os FNDs sem reconstruir a intenção.

---

## 87. Síntese antes da canonização

Antes de gerar o artefato final do projeto, o ChatGPT deve apresentar ao humano uma síntese com:

```text
HORIZONTE DA FUNDAÇÃO
CAPACIDADES FUNDACIONAIS
INVENTÁRIO DO QUE JÁ EXISTE
FNDs PROPOSTOS
DEPENDÊNCIAS
CAMINHO CRÍTICO
FOUNDATION RUNWAY
AÇÕES HUMANAS
AÇÕES AUTOMATIZÁVEIS
CUSTOS ATIVADOS
AÇÕES IRREVERSÍVEIS
DADOS PERMITIDOS
EVIDÊNCIAS
GATES
RISCOS
PENDÊNCIAS
FOUNDATION_PLAN_READINESS
```

O humano pode:

- corrigir ordem;
- remover complexidade;
- pedir divisão de FND;
- adiar recurso;
- mudar owner;
- solicitar prova maior;
- voltar a Infra/Tech Lead/Arquitetura quando necessário.

---

## 88. Aprovação e canonização

Fluxo:

```text
ANÁLISE
        ↓
SÍNTESE
        ↓
REVISÃO HUMANA
        ↓
CORREÇÕES
        ↓
APROVAÇÃO
        ↓
AUTORIZAÇÃO DE CANONIZAÇÃO
        ↓
09_Plano_de_Fundacao.md
```

Canonização não significa execução automática.

---

## 89. Estrutura mínima do artefato de projeto

O projeto deve produzir `09_Plano_de_Fundacao.md` com estrutura equivalente a:

```markdown
---
document_id: DOC-09
title: Plano de Fundação
status: canonical
version: 1.0.0
depends_on:
  - DOC-08
next_document: 10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
---

# Plano de Fundação

## 1. Decisão executiva
## 2. Horizonte da fundação
## 3. Estado atual / greenfield ou brownfield
## 4. Premissas e restrições
## 5. Foundation runway
## 6. Inventário de capacidades
## 7. Grafo de dependências
## 8. Caminho crítico
## 9. Fase A — Ownership e governança
## 10. Fase B — Repositório e workspace
## 11. Fase C — Ambientes e identidade
## 12. Fase D — Dados e migrations
## 13. Fase E — CI/CD e artifacts
## 14. Fase F — Observabilidade e operação
## 15. Fase G — Backup, restore e continuidade
## 16. Integrações e sandboxes necessários
## 17. Custos, budgets e billing
## 18. Ações humanas obrigatórias
## 19. Riscos e reversibilidade
## 20. Catálogo FND
## 21. Gates FND-GAT
## 22. Evidências esperadas
## 23. Itens adiados e triggers
## 24. Pendências
## 25. Foundation Plan Readiness
## 26. Handoff para Backlog Canônico
```

Não criar seções artificiais quando não se aplicarem.

---

## 90. Template de FND

```markdown
### FND-0XX — <nome>

**Categoria:** <ORG/GIT/WRK/ENV/...>

**Objetivo**
<resultado esperado>

**Origem**
- ADR-...
- TDR-...
- IDR-...
- INFRA-REQ-...

**Ambiente**
<global/local/staging/etc.>

**Owner**
<papel>

**Executor**
<AUTOMATABLE | HUMAN_REQUIRED | JOINT | EXTERNAL_WAIT>

**Dependências**
- FND-...

**Pré-condições**
- ...

**Ações**
1. ...

**Dados permitidos**
- ...

**Custo ativado**
- ...

**Risco**
- ...

**Reversibilidade**
<EASY | MODERATE | HARD | IRREVERSIBLE>

**Evidência**
- ...

**Condição de parada**
- ...

**Runway**
<FOUNDATION_ZERO | BEFORE_P0 | BEFORE_REAL_DATA | BEFORE_PRODUCTION | LATER>

**Status inicial**
PLANNED
```

---

## 91. Template de gate

```markdown
### FND-GAT-0XX — <nome>

**Objetivo**
<o que este gate autoriza>

**Requer**
- FND-...
- FND-...

**Evidências obrigatórias**
- ...

**Bloqueadores**
- ...

**Resultado**
PASS | FAIL | WAIVED

**Waiver**
Somente com owner, risco, compensação e prazo quando permitido.
```

---

## 92. Waiver

Nem todo gate pode receber waiver.

Normalmente não aceitar waiver informal para:

- perda de dados sem recuperação;
- segredo exposto;
- autorização crítica ausente;
- obrigação legal;
- dados reais em ambiente proibido;
- falta de owner de produção;
- artifact não rastreável quando exigido.

Quando permitido, registrar:

```text
RISCO
OWNER
MOTIVO
CONTROLE COMPENSATÓRIO
EXPIRAÇÃO
PLANO DE CORREÇÃO
```

---

## 93. Quality Gate do documento

Antes da canonização, verificar:

- todas as decisões relevantes de Infra foram consumidas;
- nenhum provider novo foi inventado;
- nenhuma tecnologia nova foi escolhida silenciosamente;
- nenhum FND contém feature de produto escondida;
- ownership precede recurso crítico;
- custo ativado está visível;
- dados permitidos estão explícitos;
- ações humanas estão explícitas;
- dependências estão explícitas;
- caminho crítico existe;
- runway existe;
- build de prova existe;
- deploy de prova existe quando aplicável;
- rollback é testável;
- migrations são testáveis quando aplicável;
- observabilidade é testável;
- backup/restore são testáveis quando aplicável;
- gates existem;
- evidências são objetivas;
- foundation readiness é explícito;
- próximo estágio consegue consumir o documento sem reconstruir o setup.

---

## 94. Handoff para o Backlog Canônico

O próximo documento deve consumir integralmente o Plano de Fundação.

O Backlog recebe:

```text
FNDs
FND-GATs
DEPENDÊNCIAS
RUNWAY
CAMINHO CRÍTICO
OWNERS
AÇÕES HUMANAS
EVIDÊNCIAS
CUSTOS
RISCOS
TRIGGERS
PENDÊNCIAS
```

E deve reconciliar isso com:

```text
OUTCOMES
ÉPICOS
HISTÓRIAS
UX
UI
ARQUITETURA
TECH-REQs
STACK
INFRA
```

para produzir uma ordem global de execução.

---

## 95. O Backlog não pode achatar a fundação

O próximo estágio não deve transformar:

```text
20 FNDs com dependências e gates
```

em:

```text
TASK: “configurar infraestrutura”
```

A granularidade necessária para segurança e rastreabilidade precisa ser preservada.

---

## 96. Relação com implementação funcional

A primeira história funcional só pode começar quando todos os FNDs classificados como `FOUNDATION_ZERO` relevantes àquela superfície tiverem passado seus gates.

Exemplo:

```text
US-001
        ↓
REQUIRES
FND-GAT-003 Workspace Ready
FND-GAT-004 Staging Ready
FND-GAT-006 Delivery Ready
```

Um módulo que manipula dado real pode exigir gates adicionais.

---

## 97. Foundation Complete

O projeto pode declarar:

```text
FOUNDATION_STATUS: COMPLETE
```

somente após execução futura e verificação dos gates definidos como necessários para aquele horizonte.

Durante esta etapa documental, o estado será normalmente:

```text
FOUNDATION_STATUS: PLANNED
```

Isso evita declarar como pronto algo que ainda existe apenas no papel.

---

## 98. Princípio final

> **Uma boa fundação não é a maior infraestrutura que conseguimos construir antes do produto. É a menor base reproduzível, segura, observável e recuperável que permite começar a entregar valor sem depender de improviso.**

E:

> **Planejar a fundação não é executá-la. Executar não é verificar. Verificar é produzir evidência de que a base cumpre os contratos aprovados.**

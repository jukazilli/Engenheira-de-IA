---
document_id: PROCESS-08-DEVOPS-INFRAESTRUTURA
title: DevOps e Infraestrutura
status: draft-methodology
version: 0.1.0
stage: devops-infraestrutura
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
produces: 08_DevOps_e_Infraestrutura.md
next_stage: 09_Plano_de_Fundacao.md
---

# 08 — DevOps e Infraestrutura

## 1. Propósito

A etapa **DevOps e Infraestrutura** transforma a arquitetura aprovada, a stack tecnológica escolhida e os requisitos operacionais do produto em uma **plataforma concreta de execução, entrega, proteção, observabilidade, recuperação e custo controlado**.

A pergunta central desta etapa é:

> **Onde e como esta stack será construída, armazenada, promovida, executada, protegida, observada, recuperada e escalada para cumprir os requisitos arquiteturais e operacionais aprovados com o menor custo total e risco compatível com o horizonte do produto?**

Esta etapa decide a materialização operacional do sistema.

Ela não redefine produto, UX, arquitetura ou stack por conveniência.

Ela também não deve executar ainda a fundação do projeto de forma irreversível quando a metodologia estiver em fase de definição. Sua saída prepara o próximo documento, **Plano de Fundação**, que transformará as decisões aprovadas em uma sequência de bootstrap, provisionamento e validação.

A saída desta etapa ainda **não autoriza implementação funcional pelo Codex**.

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
08 DEVOPS E INFRAESTRUTURA
        ↓
09 Plano de Fundação
        ↓
Backlog canônico
        ↓
Matriz de rastreabilidade
        ↓
Baseline reconciliada
        ↓
Handoff para Codex
```

A Arquitetura define **o que operacionalmente precisa ser verdade**.

A Visão do Tech Lead define **quais tecnologias concretas serão executadas**.

DevOps e Infraestrutura definem **como essas tecnologias serão operadas em ambientes reais**.

O Plano de Fundação definirá **em qual ordem criar, configurar e provar a base aprovada antes da implementação funcional**.

---

## 3. Origem desta etapa

Esta etapa não possuía um documento equivalente separado no processo original utilizado como referência para a reconstrução da metodologia.

No processo anterior, decisões de provider, ambientes, CI/CD, backup, observabilidade, contas, custos e setup apareciam misturadas principalmente com Arquitetura e Engenharia.

A metodologia refinada separa deliberadamente:

```text
ENGENHARIA E ARQUITETURA
“quais propriedades e limites o sistema precisa ter?”

TECH LEAD
“com quais tecnologias concretas vamos construir?”

DEVOPS E INFRAESTRUTURA
“onde e como essa stack será operada?”

PLANO DE FUNDAÇÃO
“qual sequência cria e valida essa base?”
```

Essa separação evita dois erros frequentes:

```text
PROVIDER ESCOLHIDO PRIMEIRO
        ↓
ARQUITETURA É FORÇADA A CABER NELE
```

ou:

```text
STACK APROVADA
        ↓
INFRASTRUTURA É IMPROVISADA DURANTE O DEPLOY
```

---

## 4. O que esta etapa decide

Esta etapa pode canonizar, quando aplicável:

- provedores de cloud e serviços gerenciados;
- regiões e requisitos de residência;
- topologia concreta por ambiente;
- estratégia de contas, organizações, projetos e ownership;
- modelo de identidade de máquina e acesso administrativo;
- redes, DNS, TLS e exposição pública;
- registry de artefatos e política de promoção;
- CI/CD concreto;
- estratégia de secrets e chaves;
- infraestrutura como código;
- políticas de configuração;
- hosting da aplicação;
- hosting de banco, filas, storage, cache e serviços escolhidos pelo Tech Lead;
- observabilidade operacional e seus backends;
- alertas e escalonamento;
- backups, restore e disaster recovery;
- rollout, rollback e kill switches operacionais;
- budgets, quotas e alertas de custo;
- capacidade inicial e gatilhos de escala;
- política de dados por ambiente;
- disponibilidade e operação de integrações;
- runbooks mínimos;
- requisitos de readiness operacional;
- plano de saída de providers quando material.

---

## 5. O que esta etapa não decide

Não pertence a esta etapa escolher ou redefinir silenciosamente:

- público;
- proposta de valor;
- escopo P0/P1/P2;
- regra de negócio;
- jornadas;
- design system;
- comportamento de UX;
- domínio;
- boundary arquitetural;
- modelo de consistência já aprovado;
- linguagem;
- runtime;
- framework;
- engine de banco;
- biblioteca de aplicação;
- ORM/query builder;
- test runner;
- regra de versionamento tecnológico;
- arquitetura por conveniência do provider.

Exemplo:

```text
TECH LEAD
“PostgreSQL é a engine canônica.”

DEVOPS / INFRA
“qual serviço, região, plano,
backup e topologia executarão PostgreSQL?”
```

Outro:

```text
TECH LEAD
“artefatos de backend serão containers OCI.”

DEVOPS / INFRA
“qual registry, política de digest,
assinatura e promoção serão usados?”
```

---

## 6. Pré-requisitos obrigatórios

Antes de iniciar esta etapa, o ChatGPT deve consumir integralmente os documentos canônicos anteriores, com atenção especial a:

- `06_Tecnicas_de_Desenvolvimento.md`;
- `07_Engenharia_e_Arquitetura.md`;
- `Visao_do_Tech_Lead.md`.

Deve extrair no mínimo:

- horizonte do produto;
- ambientes requeridos;
- requisitos de disponibilidade;
- RTO e RPO;
- atributos de segurança;
- residência/regulação;
- sensibilidade dos dados;
- requisitos de observabilidade;
- artefatos executáveis;
- engines e runtimes escolhidos;
- contratos de build;
- requisitos de CI;
- necessidade de jobs/filas/cache/storage;
- tráfego estimado;
- concorrência estimada;
- crescimento esperado;
- budget ou restrições de custo;
- portabilidade necessária;
- dependências externas;
- `TECH-REQs` relacionados à operação;
- decisões conjuntas ainda abertas.

Se a stack ainda não estiver aprovada ou houver conflito material entre Tech Lead e Arquitetura, esta etapa deve bloquear a canonização.

---

## 7. Handshake operacional

Ao iniciar uma execução real, registrar algo equivalente a:

```text
PROCESS_STATUS: ACTIVE
CURRENT_STAGE: DEVOPS_E_INFRAESTRUTURA
INPUT_ARCHITECTURE: 07_Engenharia_e_Arquitetura.md
INPUT_TECH_STACK: Visao_do_Tech_Lead.md
INFRA_STATUS: IN_PROGRESS
CANONICAL_OUTPUT: 08_DevOps_e_Infraestrutura.md
NEXT_STAGE: 09_Plano_de_Fundacao.md
```

Quando houver decisões dependentes de mercado atual:

```text
INFRA_RESEARCH_DATE: YYYY-MM-DD
```

---

## 8. DevOps e Infraestrutura são responsabilidades relacionadas, não idênticas

A metodologia mantém uma etapa única porque as decisões possuem forte acoplamento operacional, mas distingue os dois focos.

### 8.1. Infraestrutura

Responde principalmente:

- onde o sistema executa;
- quais recursos existem;
- como são isolados;
- como são protegidos;
- como armazenam dados;
- qual capacidade inicial possuem;
- como são recuperados;
- quanto custam;
- quem é owner.

### 8.2. DevOps

Responde principalmente:

- como uma mudança sai do repositório e chega ao ambiente;
- como checks bloqueiam falhas;
- como artefatos são produzidos;
- como são promovidos;
- como migrations são coordenadas;
- como rollout e rollback funcionam;
- como configuração é aplicada;
- como operação é observada;
- como release é auditável e reproduzível.

### 8.3. Quando separar em dois artefatos

Projetos com complexidade suficiente podem materializar:

```text
08A_DevOps.md
08B_Infraestrutura.md
```

sem alterar a responsabilidade lógica desta etapa.

A separação só deve ocorrer quando reduzir ambiguidade, por exemplo:

- múltiplas plataformas operacionais;
- infraestrutura regulada;
- múltiplas equipes responsáveis;
- multi-cloud real;
- grande volume de IaC;
- release engineering complexo;
- operação 24x7 com SRE dedicado.

Não dividir documentos apenas por estética organizacional.

---

## 9. Princípios operacionais

| Princípio | Regra |
| --- | --- |
| Infra segue arquitetura | Provider não redefine domínio ou requisito silenciosamente. |
| Build once, promote | O mesmo artefato testado é promovido entre ambientes quando aplicável. |
| Imutável por padrão | Produção recebe artefatos/versionamento identificáveis e reproduzíveis. |
| Menor privilégio | Pessoas, CI e workloads recebem somente o acesso necessário. |
| Segredo não é configuração | Segredos vivem em sistema apropriado, nunca no repositório ou bundle. |
| Ambientes explícitos | Não esconder staging/production em flags frágeis ou contas compartilhadas. |
| Recuperação provada | Backup sem restore testado é apenas esperança. |
| Observabilidade por decisão | Telemetria existe para responder perguntas e operar, não para acumular dados. |
| Custo observável | Recurso sem owner, budget e finalidade é dívida operacional. |
| Escala por sinal | Capacidade aumenta por métrica/gatilho, não por previsão imaginária. |
| Portabilidade proporcional | Evitar lock-in destrutivo sem abstrair tudo preventivamente. |
| Automação auditável | Mudança automática deve ser rastreável, reproduzível e reversível. |

---

## 10. Evidência, recomendação e decisão

Toda análise desta etapa deve separar:

```text
EVIDÊNCIA OPERACIONAL
→ limite, preço, SLA, região, feature ou comportamento verificado

REQUISITO HERDADO
→ obrigação vinda da Arquitetura/Tech Lead/Técnicas

INFERÊNCIA
→ consequência provável

RECOMENDAÇÃO
→ escolha proposta

DECISÃO DE INFRA
→ escolha aprovada pelo humano

PENDÊNCIA
→ informação ou aprovação ainda ausente
```

Nunca transformar automaticamente uma recomendação do provider em decisão canônica.

---

## 11. Pesquisa atual é obrigatória

Infraestrutura depende de informação altamente volátil.

Deve haver pesquisa atual, preferencialmente em fonte oficial, para afirmar:

- preços;
- franquias;
- regiões;
- disponibilidade por país;
- SLAs;
- limites de execução;
- limites de build;
- quotas;
- políticas de egress;
- storage;
- backup;
- PITR;
- retenção;
- suporte;
- limites de banco;
- conexões;
- runtime suportado;
- networking;
- DNS;
- certificados;
- secrets;
- OIDC/workload identity;
- planos gratuitos;
- termos comerciais;
- limites de observabilidade;
- recursos de segurança;
- políticas de lojas/distribuição quando aplicável.

Regra:

> **Preço, limite e disponibilidade são fatos datados.**

O documento de projeto deve registrar a data de pesquisa e marcar o que precisa ser reconfirmado antes da contratação ou produção.

---

## 12. Hierarquia de fontes

Preferência:

1. documentação oficial do provider;
2. página oficial de pricing/billing;
3. documentação oficial de status/SLA;
4. documentação oficial da tecnologia;
5. contratos ou propostas comerciais válidas;
6. evidência de POC/conta sandbox;
7. fontes técnicas secundárias confiáveis;
8. relatos de comunidade apenas como sinal qualitativo;
9. inferência do modelo.

Para preço, limite, SLA, compliance e disponibilidade, fontes primárias devem prevalecer.

---

## 13. Contrato recebido da Arquitetura e do Tech Lead

Antes de comparar providers, criar uma matriz de necessidades.

Exemplo:

| ID | Necessidade | Origem | Obrigatória? | Como verificar |
| --- | --- | --- | --- | --- |
| INFRA-REQ-001 | região compatível com residência de dados | ARCH-SEC-003 | Sim | regiões oficiais |
| INFRA-REQ-002 | executar runtime aprovado | TL-DEC-004 | Sim | runtime suportado |
| INFRA-REQ-003 | backup automático | QA-REC-002 | Sim | recurso/plano |
| INFRA-REQ-004 | RPO ≤ 24h | QA-REC-003 | Sim | política de backup |
| INFRA-REQ-005 | deploy por artefato imutável | DEV-06 | Sim | pipeline + registry |
| INFRA-REQ-006 | custo inicial ≤ orçamento | Briefing | Sim/condicional | projeção |

Sugestão de IDs:

```text
INFRA-REQ-xxx  requisito operacional
INFRA-DEC-xxx  decisão aprovada
INFRA-ENV-xxx  ambiente
INFRA-SEC-xxx  controle operacional
INFRA-NET-xxx  decisão de rede
INFRA-OBS-xxx  observabilidade
INFRA-DR-xxx   recuperação/continuidade
INFRA-COST-xxx custo/budget
DEVOPS-PIPE-xxx pipeline
DEVOPS-GATE-xxx gate
IDR-xxx        Infrastructure Decision Record
INFRA-GATE-xxx gate da etapa
```

IDs removidos não devem ser reutilizados.

---

## 14. Hard constraints antes de comparar providers

Uma opção deve ser eliminada antes de pontuação ponderada quando falhar requisito obrigatório.

Exemplos:

```text
REGIÃO OBRIGATÓRIA INDISPONÍVEL
→ REJECTED_HARD_CONSTRAINT

RUNTIME NÃO SUPORTADO
→ REJECTED_HARD_CONSTRAINT

BACKUP/RESTORE INCOMPATÍVEL COM RPO/RTO
→ REJECTED_HARD_CONSTRAINT

TERMOS NÃO PERMITEM O USO
→ REJECTED_HARD_CONSTRAINT

SEGURANÇA/COMPLIANCE OBRIGATÓRIA AUSENTE
→ REJECTED_HARD_CONSTRAINT
```

Popularidade, créditos gratuitos ou facilidade de deploy não compensam hard constraint.

---

## 15. Critérios de comparação de providers

Após qualificação obrigatória, comparar apenas critérios relevantes.

Possíveis critérios:

- segurança;
- regiões;
- confiabilidade;
- suporte a backup/restore;
- compatibilidade com a stack;
- operabilidade;
- observabilidade;
- identidade e menor privilégio;
- automação/IaC;
- custo inicial;
- previsibilidade de custo;
- custo em escala;
- egress;
- facilidade de rollback;
- maturidade;
- suporte;
- portabilidade;
- lock-in;
- experiência do time;
- SLA;
- compliance;
- integração com CI;
- velocidade de provisionamento;
- limites de free tier.

Pesos devem derivar dos drivers do projeto, não ser universais.

---

## 16. Contas, organizações e ownership

Infraestrutura começa por ownership, não por CLI.

Definir:

- entidade proprietária;
- owners humanos;
- e-mails de função;
- MFA;
- recuperação;
- contas de faturamento;
- equipes/grupos;
- menor privilégio;
- inventário de contas;
- ownership de domínios;
- ownership de lojas mobile;
- ownership de certificados;
- quem pode produzir release;
- quem pode promover produção;
- quem pode acessar secrets;
- break-glass quando necessário.

Regra:

> **Nenhuma infraestrutura crítica deve depender de conhecimento oral ou de uma única conta pessoal sem plano de recuperação.**

---

## 17. Separação de ambientes

Definir apenas ambientes necessários ao projeto.

Modelo comum:

```text
LOCAL
↓
PR / PREVIEW
↓
STAGING
↓
PRODUCTION
```

Mas o processo não obriga quatro ambientes.

Para cada ambiente, registrar:

| Campo | Pergunta |
| --- | --- |
| Finalidade | Que prova este ambiente permite? |
| Dados | Sintéticos, anonimizados ou reais? |
| Provider/projeto | Qual isolamento concreto? |
| Segredos | São próprios? |
| Domínio | Qual URL/identidade? |
| Capacidade | Qual tamanho inicial? |
| Deploy | Quem promove? |
| Retenção | Qual política? |
| Observabilidade | Qual nível? |
| Custo | Qual budget? |
| Destruição | Pode ser efêmero? |

### 17.1. Regra de produção

Produção não pode compartilhar inadvertidamente com desenvolvimento:

- banco;
- secrets;
- OAuth credentials;
- signing keys;
- bucket sensível;
- filas;
- analytics quando separação for necessária;
- billing ownership crítico;
- webhook secrets.

---

## 18. Dados de teste e isolamento

Política padrão:

```text
DESENVOLVIMENTO / PR / STAGING
→ dados sintéticos por padrão

PRODUÇÃO
→ dados reais
```

Não clonar produção para staging apenas por conveniência.

Quando um caso excepcional exigir amostra de dado real:

- autorização explícita;
- minimização;
- anonimização quando possível;
- acesso restrito;
- finalidade definida;
- expiração;
- destruição comprovada;
- auditoria.

---

## 19. Identidade de máquina e acesso administrativo

Preferir credenciais de curta duração e identidade federada quando o ecossistema suportar.

Avaliar:

- OIDC/workload identity;
- service accounts;
- roles;
- escopos;
- token lifetime;
- rotação;
- MFA humano;
- sessão privilegiada;
- approval para produção;
- break-glass;
- auditoria.

Evitar:

```text
CI_SECRET_KEY=
credencial administrativa permanente
compartilhada por vários workflows
```

quando houver alternativa de identidade temporária.

---

## 20. Secrets e chaves

Definir:

- onde cada segredo vive;
- quem pode ler;
- quem pode rotacionar;
- em quais ambientes existe;
- como chega ao workload;
- tempo de vida;
- auditoria;
- procedimento de vazamento;
- dependências que usam o segredo;
- como revogar.

Classificar:

```text
BUILD-TIME PÚBLICO
RUNTIME NÃO SENSÍVEL
SEGREDO
CHAVE PRIVILEGIADA
CHAVE DE ASSINATURA
CREDENCIAL DE TERCEIRO
```

Nunca colocar segredo em:

- repositório;
- prompt;
- screenshot;
- log;
- analytics;
- bundle cliente;
- artifact público;
- README;
- variável de frontend apenas porque possui nome `env`.

---

## 21. Networking, DNS e TLS

Quando aplicável, registrar:

- superfícies públicas;
- superfícies privadas;
- ingress;
- egress;
- allowlists;
- firewall/security groups;
- private networking;
- DNS zones;
- ownership de domínio;
- subdomínios por ambiente;
- certificado TLS;
- renovação;
- redirects;
- origin protection;
- WAF;
- DDoS controls;
- rate limiting operacional;
- dependências com IP fixo;
- webhooks;
- callbacks OAuth.

Cloud privada não deve ser adotada automaticamente. Isolamento de rede deve responder a uma ameaça ou requisito real.

---

## 22. CI/CD concreto

`06_Tecnicas_de_Desenvolvimento.md` define quais gates precisam existir.

Esta etapa escolhe como implementá-los.

Fluxo conceitual:

```text
COMMIT / PR
        ↓
VALIDAÇÕES RÁPIDAS
        ↓
TESTES / SEGURANÇA / BUILD
        ↓
ARTEFATO IMUTÁVEL
        ↓
PREVIEW / STAGING
        ↓
SMOKE / GATES
        ↓
APROVAÇÃO
        ↓
PROMOÇÃO
        ↓
PRODUÇÃO
        ↓
VERIFICAÇÃO
```

Para cada pipeline, definir:

- gatilho;
- permissões;
- checkout/ref;
- cache;
- secrets;
- jobs;
- dependências;
- artifact output;
- evidence output;
- timeout;
- concurrency;
- retry;
- environment approval;
- rollback;
- logs;
- retenção;
- owner.

---

## 23. Build once, promote many

Quando a tecnologia permitir, preferir:

```text
SOURCE SHA
        ↓
BUILD
        ↓
ARTIFACT DIGEST
        ↓
STAGING
        ↓
PRODUCTION
```

em vez de:

```text
STAGING BUILD
≠
PRODUCTION BUILD
```

Se a plataforma exigir build específico por ambiente, documentar:

- por que;
- quais entradas variam;
- como provar equivalência;
- o que continua imutável;
- como reproduzir.

---

## 24. Registry, assinatura e proveniência

Quando houver artefatos empacotados, definir:

- registry;
- naming;
- digest;
- retenção;
- política de limpeza;
- assinatura quando material;
- SBOM;
- proveniência;
- acesso;
- imutabilidade;
- promoção;
- rollback.

Tags mutáveis não devem ser a única identidade de produção.

Exemplo:

```text
release: v1.4.0
artifact_digest: sha256:...
source_commit: abc123
build_workflow: run-456
```

---

## 25. Infraestrutura como código

A etapa deve decidir se e onde IaC é necessária.

Preferir IaC quando recursos são:

- críticos;
- repetíveis;
- numerosos;
- multiambiente;
- sujeitos a drift;
- relevantes para restore;
- auditáveis;
- reconstruíveis.

IaC deve responder:

- qual ferramenta;
- estado;
- locking;
- secrets;
- módulos;
- ambiente;
- review;
- plan;
- apply;
- destroy;
- drift detection;
- import de recurso existente;
- recuperação do state.

A ferramenta concreta é decisão desta etapa, pois materializa infraestrutura, não regra de aplicação.

---

## 26. Configuração

Distinguir:

```text
CONFIGURAÇÃO VERSIONADA
→ valores não secretos que devem acompanhar release

CONFIGURAÇÃO DE AMBIENTE
→ endpoints, limites, identificadores

SEGREDO
→ credencial/chave

FEATURE FLAG
→ habilitação de comportamento

SAFETY / KILL SWITCH
→ desativação operacional de risco
```

Feature flag não substitui autorização.

Configuração dinâmica crítica precisa de:

- owner;
- validação;
- auditoria;
- default seguro;
- rollback;
- cache/TTL quando aplicável.

---

## 27. Persistência hospedada

O Tech Lead escolhe a tecnologia de persistência.

DevOps/Infra escolhe a execução concreta.

Avaliar:

- serviço gerenciado versus self-host;
- região;
- HA;
- plano;
- storage;
- IOPS;
- conexões;
- pooler/proxy;
- backup;
- PITR;
- encryption;
- maintenance window;
- upgrades;
- monitoring;
- logs;
- acesso administrativo;
- rede;
- restore;
- export;
- egress;
- custo.

Não escolher self-host apenas para economizar mensalidade sem contabilizar operação.

---

## 28. Filas, cache e outros serviços de estado

Para cada tecnologia escolhida pelo Tech Lead, Infra precisa definir execução e limites.

Exemplo:

| Serviço | Perguntas operacionais |
| --- | --- |
| Fila | retenção, DLQ, visibility timeout, escala, alertas |
| Cache | memória, eviction, persistence, failover, custo |
| Storage | região, versionamento, lifecycle, malware, CDN |
| Search | índice, backup, rebuild, custo, privacidade |
| Scheduler | retries, idempotência, timezone, ownership |

Não criar serviço operacional sem owner, métrica e condição de falha conhecida.

---

## 29. Observabilidade operacional

A Arquitetura define quais sinais são necessários.

O Tech Lead define instrumentação quando isso pertence ao código.

Infra decide backends, retenção, ingestão, acesso e operação.

Definir:

- logs;
- métricas;
- traces;
- crashes;
- audit logs;
- dashboards;
- alertas;
- status pages quando aplicável;
- retenção;
- sampling;
- cardinalidade;
- redaction;
- custos;
- acesso;
- exportabilidade.

Regra:

> **Observabilidade não pode se tornar um segundo banco de dados de conteúdo sensível.**

---

## 30. Dashboards e alertas

Todo alerta deve possuir:

- condição;
- impacto;
- severidade;
- owner;
- destino;
- runbook;
- janela;
- mute/silence controlado;
- condição de resolução.

Evitar alerta que:

- nunca exige ação;
- dispara por ruído conhecido;
- não tem owner;
- não possui contexto;
- mede infraestrutura sem relação com impacto;
- vaza dado sensível.

Priorizar sinais de usuário e SLO quando disponíveis.

---

## 31. SLOs, SLIs e error budget

Arquitetura define metas quando materiais.

Infra precisa demonstrar como medir e operar essas metas.

Para cada SLO relevante:

```text
JORNADA / SERVIÇO
SLI
OBJETIVO
JANELA
FONTE DA MÉTRICA
EXCLUSÕES
ALERTA
AÇÃO
```

Exemplo:

```text
Jornada: salvar ação crítica
SLI: taxa de comandos confirmados sem erro
Objetivo: 99,9%
Janela: 30 dias
Alerta: burn rate
Ação: on-call/runbook
```

Não inventar SLO empresarial para produto sem maturidade ou necessidade correspondente.

---

## 32. Backup, restore e continuidade

A política deve partir dos RPO/RTO aprovados.

Definir por ativo:

| Ativo | Backup | Retenção | RPO | RTO | Restore test | Owner |
| --- | --- | --- | --- | --- | --- | --- |
| banco | ... | ... | ... | ... | ... | ... |
| storage | ... | ... | ... | ... | ... | ... |
| configuração | ... | ... | ... | ... | ... | ... |
| secrets | rotação/escrow quando aplicável | ... | ... | ... | ... | ... |
| IaC | Git + state | ... | ... | ... | ... | ... |

Regra:

```text
BACKUP
sem
RESTORE TESTADO
=
CONTROLE NÃO PROVADO
```

Restore deve ocorrer em ambiente isolado antes de qualquer substituição de produção.

---

## 33. Disaster recovery

Só definir DR proporcional ao risco.

Possíveis níveis:

```text
NÍVEL 0
recriação manual aceitável

NÍVEL 1
backup + restore documentado

NÍVEL 2
infra reconstruível + dados restauráveis

NÍVEL 3
warm standby / réplica

NÍVEL 4
multi-região ativa
```

Não adotar multi-região ativa apenas por aparência de maturidade.

A decisão deve derivar de:

- RTO;
- RPO;
- impacto de indisponibilidade;
- exigência legal;
- receita;
- risco reputacional;
- custo.

---

## 34. Rollout, rollback e kill switch

Para mudança de risco, definir:

- flag;
- população;
- canary;
- percentual;
- métrica;
- guardrail;
- condição de parada;
- rollback;
- rollback de migration;
- forward-fix;
- kill switch;
- owner;
- tempo máximo de decisão.

Rollback de aplicação não garante rollback de dados.

Toda migration incompatível precisa ter estratégia própria.

---

## 35. Migrations e deploy de dados

Infra e aplicação precisam coordenar:

```text
EXPAND
        ↓
DEPLOY COMPATÍVEL
        ↓
MIGRATE / BACKFILL
        ↓
VALIDATE
        ↓
SWITCH
        ↓
CONTRACT POSTERIOR
```

Pipeline deve considerar:

- locking;
- timeout;
- tamanho;
- batches;
- retry;
- observabilidade;
- compatibilidade com cliente antigo;
- rollback;
- owner presente;
- janela quando necessária.

Não executar migration destrutiva e aplicação incompatível em um único passo irreversível.

---

## 36. Segurança operacional

A etapa materializa controles como:

- IAM;
- MFA;
- WAF;
- DDoS protection;
- rate limiting;
- private networking;
- secret store;
- KMS quando aplicável;
- encryption at rest;
- TLS;
- audit logs;
- vulnerability scanning de imagens;
- patching;
- bastion/VPN quando necessário;
- hardening;
- backup protegido;
- acesso break-glass;
- segregação de funções;
- políticas de produção.

Controles devem apontar para ameaça/requisito correspondente.

---

## 37. Supply chain operacional

Materializar os requisitos de `06_Tecnicas_de_Desenvolvimento.md`:

- pin de actions/plugins;
- dependabot/renovação equivalente;
- dependency review;
- secret scan;
- code scan;
- image scan;
- SBOM;
- provenance;
- artifact signing quando material;
- registry permissions;
- workflow permissions;
- branch/environment protection;
- release auditável.

Automação de segurança não elimina review humano de finding material.

---

## 38. Custos e FinOps mínimo

Infraestrutura deve possuir um modelo de custo antes de ser criada.

Registrar por ambiente:

- provider;
- recurso;
- plano;
- custo fixo;
- custo variável;
- unidade de cobrança;
- franquia;
- egress;
- armazenamento;
- observabilidade;
- backup;
- add-ons;
- owner;
- budget;
- alerta;
- gatilho de upgrade;
- gatilho de downgrade/desligamento.

### 38.1. Estados de custo

```text
ESTIMADO
VALIDADO EM PRICING
MEDIDO EM ALPHA
MEDIDO EM BETA
RECONFIRMAR
```

### 38.2. Não assumir custo zero

Free tier é capacidade promocional ou limitada, não arquitetura de produção por definição.

Perguntar:

- o plano gratuito permite backup suficiente?
- hiberna?
- possui SLA?
- limita região?
- limita projetos?
- limita build?
- suporta dados reais conforme termos?
- qual comportamento ocorre ao exceder quota?

---

## 39. Quotas, budgets e proteção contra surpresa

Definir:

- quotas técnicas;
- budgets financeiros;
- alertas progressivos;
- limite por ambiente;
- limite de logs;
- retenção;
- autoscaling máximo;
- proteção contra loop de job;
- proteção contra egress acidental;
- rate limit de terceiros;
- kill switch de integração.

Autoscaling sem teto pode converter bug em fatura.

---

## 40. Capacidade inicial

Capacidade deve ser derivada da mensuração do `07`.

Registrar:

- usuários estimados;
- concorrência;
- RPS;
- jobs;
- armazenamento;
- crescimento;
- conexões;
- tamanho de payload;
- picos;
- latência;
- reserva;
- limitações do plano.

Usar estados:

```text
MEDIDO
ESTIMADO
HIPÓTESE
```

Não dimensionar para “milhões de usuários” sem horizonte ou evidência.

---

## 41. Gatilhos de escala

Para cada recurso crítico:

| Sinal | Limite | Primeira ação | Segunda ação | Quando reabrir arquitetura |
| --- | --- | --- | --- | --- |
| CPU | ... | otimizar | aumentar capacidade | se boundary virou gargalo |
| DB connections | ... | pooling/limite | compute | se modelo não sustenta |
| queue age | ... | aumentar consumer | separar worker | se isolamento necessário |
| storage | ... | lifecycle | expandir tier | se custo domina |
| logs | ... | sampling/retenção | tier | se observabilidade insuficiente |

A ordem padrão é:

```text
MEDIR
↓
OTIMIZAR
↓
AUMENTAR CAPACIDADE
↓
ISOLAR GARGALO
↓
REABRIR ARQUITETURA
```

não:

```text
MICROSSERVIÇOS PRIMEIRO
```

---

## 42. Providers externos e integrações

Para cada provider externo material à operação, registrar:

- conta/owner;
- ambiente/sandbox;
- credencial;
- quota;
- rate limit;
- custo;
- SLA;
- região;
- webhook;
- retry;
- circuit breaker quando aplicável;
- fallback;
- kill switch;
- observabilidade;
- retenção;
- política de dados;
- termos;
- procedimento de incidente;
- plano de troca.

Provider externo não pode ser tratado como sempre disponível.

---

## 43. Mobile e distribuição, quando aplicável

Infra/DevOps deve materializar:

- contas de desenvolvedor;
- bundle/application IDs;
- signing;
- keystores/certificados;
- owners;
- perfis de build;
- canais dev/preview/prod;
- store credentials;
- release tracks;
- phased rollout;
- OTA quando permitido;
- compatibilidade runtime/build;
- crash symbols/source maps;
- rollback compatível com regras da plataforma.

Credenciais de loja e assinatura são ativos críticos e precisam de plano de recuperação.

---

## 44. Web e domínio, quando aplicável

Definir:

- domínio principal;
- DNS provider;
- ownership;
- subdomínios;
- TLS;
- redirect canonical;
- CDN;
- cache;
- headers;
- CSP quando aplicável;
- HSTS quando aplicável;
- WAF;
- preview URLs;
- proteção de previews;
- robots/indexação por ambiente;
- origem;
- invalidation;
- logs.

Staging não deve ser indexado publicamente por acidente quando isso expõe superfície interna.

---

## 45. Brownfield

Em projeto existente, primeiro produzir inventário operacional real:

- providers;
- contas;
- regiões;
- ambientes;
- pipelines;
- secrets;
- domínios;
- certificados;
- bancos;
- buckets;
- filas;
- DNS;
- observabilidade;
- backups;
- custos;
- owners;
- runbooks;
- incidentes;
- IaC;
- recursos órfãos;
- drift;
- riscos.

Classificar cada item:

```text
KEEP
UPGRADE
HARDEN
MIGRATE
CONSOLIDATE
REPLACE
REMOVE
UNKNOWN
```

Não recriar infraestrutura do zero apenas para torná-la “mais limpa”.

---

## 46. Infrastructure Decision Record — IDR

Decisões operacionais duráveis devem receber `IDR` quando forem materialmente caras de mudar ou possuírem trade-off relevante.

Estrutura mínima:

```text
IDR-xxx

TÍTULO
STATUS
DATA
OWNER

CONTEXTO
REQUISITOS
ALTERNATIVAS
DECISÃO
CONSEQUÊNCIAS
CUSTO
LOCK-IN
SEGURANÇA
RECUPERAÇÃO
VALIDAÇÃO
GATILHO DE REVISÃO
```

Exemplos de decisões que podem justificar IDR:

- provider principal;
- região de produção;
- estratégia de contas;
- registry;
- IaC tool;
- hosting de banco;
- estratégia de secrets;
- topologia de rede;
- observability backend;
- backup/DR;
- CI platform quando fortemente acoplada;
- multi-cloud.

Decisões triviais e facilmente reversíveis não precisam de IDR formal.

---

## 47. Relação com ADR e TDR

A rastreabilidade recomendada é:

```text
ADR
“o sistema precisa de persistência relacional transacional”

        ↓

TDR
“PostgreSQL foi selecionado”

        ↓

IDR
“PostgreSQL será operado no serviço/provider X,
região Y, plano Z, com backup W”
```

Cada camada decide algo diferente.

Se o provider escolhido exigir alterar engine, isso não é decisão unilateral de Infra.

Fluxo:

```text
INFRA
        ↓
INCOMPATIBILIDADE REAL
        ↓
IMPACTA STACK?
        ↓
SIM
        ↓
REABRIR TDR / TECH LEAD
        ↓
IMPACTA ARQUITETURA?
        ↓
SIM
        ↓
REABRIR ADR / 07
```

---

## 48. Decisões conjuntas com Tech Lead

Alguns serviços misturam código e operação.

Exemplos:

- Auth SaaS;
- serverless database;
- queue proprietária;
- feature flag SaaS;
- search SaaS;
- edge runtime proprietário;
- workflow engine;
- sync-as-a-service;
- BaaS;
- observabilidade fortemente acoplada ao SDK.

Nesses casos registrar:

```text
DECISION_OWNER: JOINT_TECH_LEAD_INFRA
```

Tech Lead avalia:

- SDK;
- contratos;
- impacto no domínio;
- testes;
- portabilidade do código;
- ergonomia de desenvolvimento.

Infra avalia:

- SLA;
- região;
- custo;
- billing;
- backup;
- segurança;
- networking;
- ownership;
- operação;
- saída.

A decisão só é canonizada após reconciliar ambos.

---

## 49. Lock-in e estratégia de saída

Lock-in não é automaticamente ruim.

Perguntar:

- qual velocidade/capacidade ele compra?
- qual parte fica proprietária?
- quais dados precisam sair?
- qual custo de migração?
- qual probabilidade de migração?
- qual impacto se o provider mudar preço?
- existe export oficial?
- backups são portáveis?
- contratos internos escondem o provider onde necessário?
- o domínio depende diretamente dele?

Classificar:

```text
LOCK-IN ACEITÁVEL
LOCK-IN ACEITÁVEL COM MITIGAÇÃO
LOCK-IN NÃO ACEITÁVEL
PENDENTE
```

Não criar abstração genérica sem cenário plausível de troca.

---

## 50. Runbooks mínimos

Antes de produção, todo sistema deve possuir runbooks proporcionais ao risco.

Possíveis runbooks:

- deploy falhou;
- rollback;
- migration presa;
- banco indisponível;
- restore;
- segredo vazado;
- certificado expirando;
- fila atrasada;
- provider externo fora;
- quota excedida;
- custo anômalo;
- auth indisponível;
- DNS incorreto;
- storage indisponível;
- observabilidade fora;
- mobile release ruim;
- kill switch.

Estrutura mínima:

```text
SINTOMA
IMPACTO
VERIFICAÇÃO
MITIGAÇÃO
ROLLBACK / CONTENÇÃO
VALIDAÇÃO
ESCALONAMENTO
OWNER
```

---

## 51. Incidentes

Definir processo compatível com o estágio do produto:

```text
DETECTAR
↓
CLASSIFICAR
↓
DECLARAR OWNER
↓
CONTER
↓
RECUPERAR
↓
VALIDAR JORNADA DO USUÁRIO
↓
COMUNICAR
↓
POSTMORTEM
↓
AÇÃO PREVENTIVA
```

Não medir recuperação apenas por “servidor respondeu 200”.

A jornada crítica precisa estar funcional novamente.

---

## 52. Operação humana e on-call

Nem todo projeto precisa de plantão 24x7.

A etapa deve decidir:

- horário de suporte;
- severidades;
- quem recebe alertas;
- expectativa de resposta;
- escalonamento;
- cobertura fora do horário;
- quando on-call passa a ser necessário;
- dependência de fornecedor;
- comunicação de incidente.

Não criar SLO 24x7 sem capacidade humana correspondente.

---

## 53. Política de acesso a produção

Definir:

- quem pode ler logs;
- quem pode acessar banco;
- quem pode alterar configuração;
- quem pode promover release;
- quem pode executar migration;
- quem pode rotacionar segredo;
- quem pode acessar billing;
- quem pode alterar DNS;
- quem pode usar break-glass.

Princípios:

```text
LEAST PRIVILEGE
SEPARATION OF DUTIES QUANDO MATERIAL
MFA
AUDITORIA
ACESSO TEMPORÁRIO QUANDO POSSÍVEL
```

Acesso direto a dados de produção não deve ser rotina de debugging.

---

## 54. Política de mudanças manuais

Mudança manual inevitável deve registrar:

- quem;
- quando;
- por quê;
- recurso;
- valor anterior;
- valor novo;
- ticket/incidente;
- risco;
- como reconciliar com IaC/configuração versionada.

Regra:

> **Mudança emergencial manual não pode criar uma segunda realidade permanente fora do repositório.**

---

## 55. Readiness operacional

Usar estados explícitos:

```text
INFRA_READINESS: INSUFFICIENT
INFRA_READINESS: SUFFICIENT_WITH_OPEN_QUESTIONS
INFRA_READINESS: SUFFICIENT
```

`SUFFICIENT_WITH_OPEN_QUESTIONS` é válido quando pendências possuem:

- owner;
- risco;
- data/momento de resolução;
- fallback;
- não bloqueiam o Plano de Fundação.

A etapa está suficientemente pronta quando conseguimos responder:

1. quais providers serão usados e por quê;
2. quais hard constraints eles atendem;
3. quais regiões serão usadas;
4. quais ambientes existem;
5. como contas e ownership funcionam;
6. como identidade de máquina e humana funciona;
7. onde secrets vivem;
8. como rede, DNS e TLS funcionam;
9. como CI/CD será materializado;
10. qual artefato é promovido;
11. como IaC/configuração serão geridas;
12. onde cada tecnologia da stack será hospedada;
13. como observabilidade será operada;
14. quais SLOs são medidos;
15. como backup e restore funcionam;
16. quais metas de RPO/RTO são atendidas;
17. como rollout e rollback funcionam;
18. quais budgets e quotas existem;
19. quais gatilhos de escala existem;
20. como integrações degradam;
21. quais runbooks são necessários;
22. quais decisões estão em IDR;
23. quais pendências permanecem abertas;
24. quais ações pertencem ao próximo Plano de Fundação.

---

## 56. Gates da etapa

Antes do handoff para Fundação:

| Gate | Evidência |
| --- | --- |
| INFRA-01 Requisitos | `INFRA-REQs` rastreáveis à Arquitetura/Tech Lead. |
| INFRA-02 Providers | Providers comparados, hard constraints e trade-offs registrados. |
| INFRA-03 Ownership | Contas, owners, MFA e recuperação definidos. |
| INFRA-04 Ambientes | Isolamento, dados e finalidade de cada ambiente definidos. |
| INFRA-05 IAM/Secrets | Menor privilégio, identidade e secrets materializados em design. |
| INFRA-06 Network | DNS, TLS, exposição e controles de rede definidos quando aplicáveis. |
| INFRA-07 CI/CD | Pipeline concreto, artefato e promoção definidos. |
| INFRA-08 IaC/Config | Estratégia de infraestrutura e configuração definida. |
| INFRA-09 Data services | Hosting, backup, capacidade e operação dos serviços de estado definidos. |
| INFRA-10 Observabilidade | Backends, retenção, dashboards e alertas definidos. |
| INFRA-11 DR | Backup, restore, RPO/RTO e continuidade definidos. |
| INFRA-12 Segurança | Controles operacionais e acesso à produção definidos. |
| INFRA-13 Custo | Budget, quotas, alertas e modelo inicial definidos. |
| INFRA-14 Escala | Gatilhos de capacidade e evolução definidos. |
| INFRA-15 Runbooks | Operações críticas possuem runbooks planejados. |
| INFRA-16 Handoff | Plano de Fundação pode ser criado sem inventar provider ou topologia. |

---

## 57. Síntese antes da canonização

Antes de criar o artefato final do projeto, apresentar ao humano uma síntese com:

```text
REQUISITOS OPERACIONAIS
PROVIDERS CANDIDATOS
HARD CONSTRAINTS
DECISÕES DE PROVIDER
REGIÕES
AMBIENTES
OWNERSHIP / CONTAS
IAM
SECRETS
NETWORK / DNS / TLS
CI/CD
ARTEFATOS / REGISTRY
IaC
CONFIGURAÇÃO
DATABASE / STORAGE / QUEUE / CACHE HOSTING
OBSERVABILIDADE
SLO / ALERTAS
BACKUP / RESTORE
RTO / RPO / DR
ROLLOUT / ROLLBACK
SEGURANÇA OPERACIONAL
CUSTOS / BUDGETS
QUOTAS
GATILHOS DE ESCALA
INTEGRAÇÕES
LOCK-IN
IDRs
RUNBOOKS
PENDÊNCIAS
INFRA_READINESS
```

O humano pode:

- pedir nova comparação;
- rejeitar provider;
- alterar budget;
- pedir alternativa mais simples;
- pedir maior isolamento;
- aceitar lock-in conscientemente;
- alterar meta operacional;
- reabrir decisão do Tech Lead quando incompatível;
- reabrir Arquitetura quando necessário.

---

## 58. Aprovação e canonização

Fluxo:

```text
ANÁLISE
        ↓
PESQUISA ATUAL
        ↓
COMPARAÇÃO
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
08_DevOps_e_Infraestrutura.md
```

A conversa não substitui o documento canônico.

---

## 59. Estrutura mínima do artefato de projeto

O projeto deve produzir `08_DevOps_e_Infraestrutura.md` com estrutura equivalente a:

```markdown
---
document_id: DOC-08
title: DevOps e Infraestrutura
status: canonical
version: 1.0.0
depends_on:
  - DOC-07
  - TECH-LEAD
infra_research_date: YYYY-MM-DD
next_document: 09_Plano_de_Fundacao.md
---

# DevOps e Infraestrutura

## 1. Decisão executiva
## 2. Contexto operacional e horizonte
## 3. INFRA-REQs
## 4. Hard constraints
## 5. Pesquisa e comparação de providers
## 6. Providers aprovados
## 7. Regiões e residência
## 8. Contas, ownership e billing
## 9. Ambientes
## 10. IAM e acesso
## 11. Secrets e chaves
## 12. Networking, DNS e TLS
## 13. CI/CD
## 14. Build, artifacts e registry
## 15. Infraestrutura como código
## 16. Configuração e feature/safety flags
## 17. Hosting da stack
## 18. Persistência, storage, filas e cache
## 19. Observabilidade
## 20. SLOs, dashboards e alertas
## 21. Backup e restore
## 22. Disaster recovery
## 23. Rollout, rollback e migrations
## 24. Segurança operacional
## 25. Supply chain
## 26. Dados por ambiente
## 27. Custos, quotas e budgets
## 28. Capacidade e gatilhos de escala
## 29. Integrações e dependências externas
## 30. Runbooks e incidentes
## 31. Lock-in e estratégia de saída
## 32. IDRs
## 33. Pendências
## 34. Gates e Infra Readiness
## 35. Handoff para Plano de Fundação
```

Se uma seção não se aplica, registrar `não aplicável` com justificativa em vez de inventar complexidade.

---

## 60. Relação com o Plano de Fundação

Esta etapa responde:

```text
O QUE FOI ESCOLHIDO OPERACIONALMENTE?
```

O Plano de Fundação responderá:

```text
EM QUAL ORDEM CRIAMOS E PROVAMOS ISSO?
```

Exemplo:

```text
INFRA DECIDE
Git provider X
Cloud Y
DB managed Z
região R
CI pipeline P
secret store S

        ↓

FUNDAÇÃO ORGANIZA
FND-001 criar ownership
FND-002 criar organização
FND-003 proteger repositório
FND-004 criar billing/budget
FND-005 provisionar staging
FND-006 configurar OIDC
FND-007 provisionar banco
FND-008 provar backup/restore
...
```

O Plano de Fundação não deve rediscutir provider, salvo descoberta factual que torne a decisão inviável.

---

## 61. O Plano de Fundação ainda não é implementação funcional

A Fundação pode autorizar ou coordenar:

- criação de contas;
- configuração de organização;
- repositório;
- branches;
- ambientes;
- providers;
- secrets;
- projetos vazios;
- CI mínimo;
- observabilidade mínima;
- banco/schema inicial estrutural quando explicitamente parte da fundação;
- bootstrap da stack;
- smoke tests;
- backup/restore de fundação;
- documentação operacional.

Mas não deve começar features de produto antes da baseline e do handoff correspondente.

---

## 62. Relação com Backlog Canônico

DevOps/Infra produz necessidades que posteriormente podem virar itens de entrega.

Exemplo:

```text
INFRA-DR-004
“restore precisa ser testado mensalmente”

        ↓

BACKLOG
OPS-012 automatizar restore smoke
```

Mas esta etapa não deve ordenar todo o roadmap funcional.

---

## 63. Relação com Matriz de Rastreabilidade

Exemplo de cadeia:

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
FND-011
        ↓
ITEM DE BACKLOG
        ↓
TESTE
        ↓
EVIDÊNCIA
```

Essa cadeia permite explicar por que um recurso de infraestrutura existe.

---

## 64. Anti-padrões

### 64.1. Provider-first architecture

```text
“temos créditos no provider X,
logo toda arquitetura usará X.”
```

Crédito pode ser critério de custo, não autoridade arquitetural.

### 64.2. Free tier como requisito principal

```text
“precisa ser grátis”
```

sem analisar backup, SLA, limites, dados reais e custo de migração.

### 64.3. Kubernetes por aparência de maturidade

Não adotar orquestração complexa sem problema que a justifique.

### 64.4. Multi-cloud preventivo

Duplicar providers aumenta operação, identidade, observabilidade e incidentes.

Só adotar por driver concreto.

### 64.5. Segredo como variável comum

`.env` não é estratégia de secret management por si só.

### 64.6. Backup sem restore

Backup não testado não comprova recuperação.

### 64.7. CI verde por skip

Job pulado não é prova quando a mudança afetou o risco correspondente.

### 64.8. Rebuild em produção

Produção não deveria receber artefato diferente apenas porque foi reconstruído novamente.

### 64.9. Observabilidade ilimitada

Mais logs não significam melhor operação e podem aumentar custo e risco de privacidade.

### 64.10. Autoscaling infinito

Sem teto, bug operacional pode virar custo ilimitado.

### 64.11. Manual forever

Procedimento manual recorrente e crítico deve possuir plano de automação ou justificativa explícita.

### 64.12. Infraestrutura sem owner

Todo recurso pago, crítico ou privilegiado precisa de responsável identificável.

### 64.13. Drift aceito silenciosamente

Infra real diferente da documentação/IaC precisa ser reconciliada.

---

## 65. Quality Gate do documento

Antes de considerar a etapa pronta, verificar:

- consumiu Arquitetura e Tech Lead integralmente;
- não redefiniu stack sem reconciliação;
- fez pesquisa atual para fatos voláteis;
- comparou providers contra requisitos;
- eliminou opções que falham hard constraints;
- registrou regiões e residência;
- definiu ownership e billing;
- definiu ambientes e dados permitidos;
- definiu IAM e secrets;
- definiu networking quando material;
- definiu pipeline e artifact strategy;
- definiu IaC/configuração;
- materializou hosting da stack;
- definiu observabilidade e alertas;
- definiu backup/restore e provabilidade;
- definiu RPO/RTO operacional;
- definiu custos e budgets;
- definiu quotas e proteção de custo;
- definiu gatilhos de escala;
- registrou integrações e fallback;
- registrou lock-in conscientemente;
- registrou IDRs materiais;
- possui runbooks planejados;
- pendências estão explícitas;
- Plano de Fundação consegue consumir sem inventar topologia.

---

## 66. Handoff para o Plano de Fundação

O próximo documento deve consumir integralmente `08_DevOps_e_Infraestrutura.md`.

Ele recebe:

```text
STACK APROVADA
PROVIDERS
REGIÕES
AMBIENTES
CONTAS / OWNERS
IAM
SECRETS
NETWORK
DNS / TLS
CI/CD
ARTIFACTS
IaC
CONFIGURAÇÃO
HOSTING
DATA SERVICES
OBSERVABILIDADE
BACKUP / RESTORE
RTO / RPO
ROLLOUT / ROLLBACK
CUSTOS / BUDGETS
QUOTAS
INTEGRAÇÕES
IDRs
RUNBOOKS
GATES
PENDÊNCIAS
```

E deve responder:

> **Qual é a sequência mínima, segura, verificável e reversível para criar a fundação técnica aprovada e demonstrar que ela está pronta para receber implementação funcional?**

---

## 67. Princípio final

> **DevOps e Infraestrutura não existem para escolher a nuvem mais sofisticada. Existem para tornar a arquitetura e a stack executáveis, reproduzíveis, observáveis, recuperáveis, seguras e economicamente sustentáveis no horizonte real do produto.**

E a regra de autoridade permanece:

```text
PRODUTO
não é redefinido pela Infra

ARQUITETURA
não é redefinida pelo provider

STACK
não é trocada por conveniência operacional

INFRAESTRUTURA
não é improvisada durante o deploy

FUNDAÇÃO
não começa sem decisões operacionais aprovadas
```

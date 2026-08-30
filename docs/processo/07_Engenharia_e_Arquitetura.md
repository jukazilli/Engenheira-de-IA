---
document_id: PROCESS-07-ENGENHARIA-ARQUITETURA
title: Engenharia e Arquitetura
status: draft-methodology
version: 0.1.0
stage: engenharia-arquitetura
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
  - Principios_de_UX_UI.md
  - 04_Direcao_de_UI_e_Design_System.md
  - 05_Especificacao_de_UX.md
  - 06_Tecnicas_de_Desenvolvimento.md
produces: 07_Engenharia_e_Arquitetura.md
next_stage: Visao_do_Tech_Lead.md
---

# 07 — Engenharia e Arquitetura

## 1. Propósito

A etapa **Engenharia e Arquitetura** transforma o produto, os contratos de experiência e as políticas de desenvolvimento já aprovados em uma **mensuração técnica estruturada do sistema** e em uma **arquitetura capaz de responder a essas forças sem escolher prematuramente as tecnologias concretas de implementação**.

A pergunta central desta etapa é:

> **O que tecnicamente precisa ser verdade para que este produto cumpra seus contratos, quais forças e restrições governam o sistema, como seus domínios, dados, integrações e responsabilidades devem ser organizados e quais propriedades a stack futura obrigatoriamente deverá sustentar?**

Esta etapa existe para impedir dois extremos:

```text
PRODUTO / UX
        ↓
“vamos usar a tecnologia que já conhecemos”
```

ou:

```text
PRODUTO / UX
        ↓
“vamos desenhar uma arquitetura máxima
para todos os futuros imagináveis”
```

O caminho esperado é:

```text
CONTRATOS ANTERIORES
        ↓
MENSURAÇÃO TÉCNICA
        ↓
DRIVERS E ATRIBUTOS DE QUALIDADE
        ↓
DOMÍNIOS E BOUNDARIES
        ↓
ARQUITETURA E CONTRATOS ESTRUTURAIS
        ↓
REQUISITOS PARA A STACK
        ↓
VISÃO DO TECH LEAD
```

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
07 ENGENHARIA E ARQUITETURA
        ↓
VISÃO DO TECH LEAD
        ↓
DEVOPS / INFRAESTRUTURA
        ↓
BACKLOG CANÔNICO + RASTREABILIDADE
        ↓
HANDOFF PARA CODEX
```

As etapas anteriores já definiram **o produto**, **o comportamento esperado**, **a experiência**, **a linguagem visual** e **o padrão de qualidade da engenharia**.

Engenharia e Arquitetura convertem esse conjunto em **necessidades técnicas, invariantes estruturais, fronteiras, contratos, trade-offs e propriedades arquiteturais**.

A Visão do Tech Lead deverá receber essa mensuração e decidir **com quais linguagens, runtimes, frameworks, bibliotecas, engines, SDKs e ferramentas concretas a arquitetura será materializada**.

DevOps e Infraestrutura deverão, depois, decidir **como essa stack será construída, entregue, executada, protegida, observada, recuperada e custeada nos ambientes reais**.

---

## 3. Origem e refinamento desta etapa

Esta etapa foi formalizada a partir da arquitetura real utilizada no DayGym.

No processo original, o documento de Arquitetura e Engenharia reunia em uma única peça:

- decisão de forma arquitetural;
- stack mobile, web e backend;
- banco de dados;
- offline e sincronização;
- monorepo;
- modelo de domínio;
- APIs e eventos;
- integrações;
- segurança;
- ambientes;
- CI/CD;
- observabilidade;
- SLOs;
- backup e restauração;
- custos;
- caminho de escala;
- plano de implementação;
- setup de contas e infraestrutura.

Esse material foi extremamente útil para o projeto concreto, mas mostrou que a metodologia reutilizável precisava separar responsabilidades.

Na versão refinada:

```text
ENGENHARIA E ARQUITETURA
mensura e estrutura o sistema

TECH LEAD
seleciona a tecnologia concreta

DEVOPS / INFRAESTRUTURA
materializa execução e operação
```

Por isso, escolhas como nomes de frameworks, bancos, bibliotecas, clouds, ferramentas de observabilidade e provedores de CI/CD **não devem ser canonizadas aqui apenas porque apareceram em um projeto anterior**.

O documento 07 deve produzir contexto técnico suficiente para que essas escolhas futuras sejam justificáveis por necessidade, não por preferência.

---

## 4. Pré-requisitos obrigatórios

Antes de iniciar esta etapa, o ChatGPT deve consumir integralmente os artefatos canônicos anteriores aplicáveis ao projeto.

No mínimo, deve conhecer:

- tese e contexto do produto;
- público e stakeholders;
- escopo atual e fora de escopo;
- core loop e hierarquia de valor;
- jornadas críticas;
- regras de negócio;
- estados, erros e recuperações de UX;
- requisitos de acessibilidade;
- requisitos de privacidade e segurança;
- comportamento em conectividade degradada, quando aplicável;
- integrações necessárias ou prováveis;
- volume e criticidade dos dados;
- hipóteses de escala;
- gates e guardrails de produto;
- política de desenvolvimento, testes e revisão;
- riscos e pendências ainda abertas.

Também deve analisar, quando o projeto já existir:

- repositórios atuais;
- módulos e dependências;
- contratos de API existentes;
- schema de dados;
- migrations;
- filas e jobs;
- autenticação e autorização;
- integrações externas;
- ambientes;
- incidentes conhecidos;
- gargalos e métricas reais;
- dívida técnica material;
- limitações de compatibilidade.

Em brownfield, o estado existente é **evidência operacional**, não autoridade automática sobre o desenho futuro.

---

## 5. Mandato de Engenharia e Arquitetura

Esta etapa deve:

- mensurar tecnicamente o produto;
- identificar drivers arquiteturais;
- transformar comportamento em atributos de qualidade verificáveis;
- registrar restrições duráveis;
- separar fato, estimativa, hipótese e decisão;
- identificar domínios e ownership;
- definir boundaries e regras de dependência;
- registrar invariantes estruturais;
- definir fontes canônicas de verdade;
- identificar fronteiras transacionais;
- definir requisitos de consistência;
- definir necessidades de versionamento e compatibilidade;
- definir padrões de interação entre partes do sistema;
- definir política arquitetural de offline/sync quando necessária;
- definir trust boundaries e requisitos de segurança;
- definir requisitos arquiteturais de observabilidade e auditoria;
- definir requisitos de recuperação, RTO e RPO quando aplicáveis;
- identificar pontos de degradação e fallback;
- comparar estilos e alternativas arquiteturais;
- registrar decisões duráveis em ADR;
- definir gatilhos de escala e extração;
- produzir uma matriz de requisitos para seleção tecnológica;
- preparar um handoff inequívoco para o Tech Lead.

Esta etapa não existe para desenhar a arquitetura “mais sofisticada”.

Ela existe para encontrar a **menor arquitetura que preserve corretamente as propriedades exigidas pelo produto e permita evolução consciente**.

---

## 6. O que esta etapa pode e não pode canonizar

### 6.1. Pode canonizar

Engenharia e Arquitetura podem canonizar, quando sustentado pelas etapas anteriores:

- drivers arquiteturais;
- atributos de qualidade e sua prioridade;
- cenários de qualidade mensuráveis;
- restrições técnicas reais;
- estilo arquitetural;
- modularidade e boundaries;
- domínios e responsabilidades;
- direção de dependências;
- invariantes estruturais;
- autoridade de dados;
- necessidade de transação;
- requisitos de consistência;
- requisitos de isolamento;
- requisitos de versionamento;
- semântica de comandos, queries e eventos;
- necessidade de idempotência;
- política de compatibilidade;
- política de offline e sincronização;
- estratégia conceitual de conflitos;
- padrões arquiteturais como ports/adapters, outbox, event dispatch ou cache quando justificados;
- política de integração externa;
- trust boundaries;
- requisitos arquiteturais de autenticação e autorização;
- threat model;
- requisitos de auditabilidade;
- requisitos de telemetria e minimização;
- RTO/RPO e objetivos de confiabilidade quando derivados do produto;
- condições de degradação;
- gatilhos de escala;
- condições para extrair componentes/serviços;
- critérios que a stack futura deve atender;
- ADRs arquiteturais.

### 6.2. Não pode canonizar por conveniência

Esta etapa não deve escolher prematuramente:

- linguagem de programação concreta;
- runtime concreto;
- framework mobile;
- framework web;
- framework backend;
- biblioteca de estado;
- biblioteca de validação;
- biblioteca de sync;
- ORM;
- engine concreta de banco;
- produto concreto de cache;
- produto concreto de fila;
- biblioteca concreta de testes;
- package manager;
- ferramenta de monorepo;
- SDK de analytics;
- SDK de crash reporting;
- cloud provider;
- região de cloud;
- produto de hosting;
- provedor de observabilidade;
- provedor de secret management;
- ferramenta concreta de CI/CD;
- estrutura física final do repositório;
- versões de pacotes;
- comandos de bootstrap;
- contas de fornecedores;
- orçamento comercial concreto.

Esses itens pertencem principalmente à Visão do Tech Lead ou a DevOps/Infraestrutura.

### 6.3. Exceções legítimas

Uma tecnologia pode aparecer nesta etapa quando ela já é uma **restrição humana ou externa confirmada**.

Exemplos:

```text
“O cliente exige implantação em ambiente Kubernetes já existente.”

“O sistema precisa integrar com banco Oracle corporativo já contratado.”

“O aplicativo legado em produção deve continuar compatível com API X por 12 meses.”
```

Nesse caso, a tecnologia não está sendo escolhida pela arquitetura.

Ela está sendo tratada como restrição de entrada.

---

## 7. Mensuração técnica antes da arquitetura

A arquitetura não deve começar desenhando caixas.

Primeiro deve existir uma **mensuração técnica do problema**.

A mensuração deve ser proporcional ao projeto, mas considerar quando relevante:

| Dimensão | Perguntas |
| --- | --- |
| Usuários | Quantos usuários esperamos agora? Qual horizonte posterior importa? |
| Concorrência | Quantas operações simultâneas plausíveis existem? Existem picos previsíveis? |
| Volume | Quanto dado nasce por usuário, sessão, dia ou operação? |
| Crescimento | Quais dimensões crescem mais rápido: usuários, mídia, eventos, histórico, integrações? |
| Latência | Quais ações precisam parecer imediatas? Quais toleram processamento posterior? |
| Disponibilidade | Que tarefas podem parar? Quais precisam continuar degradadas? |
| Conectividade | Existe uso offline, rede ruim, roaming ou interrupção frequente? |
| Consistência | Onde consistência forte é necessária? Onde eventual é aceitável? |
| Durabilidade | Que dado não pode ser perdido? Qual perda máxima é tolerável? |
| Recuperação | Quanto tempo de indisponibilidade é aceitável? |
| Sensibilidade | Existem dados pessoais, financeiros, saúde, segredo empresarial ou conteúdo privado? |
| Autorização | Há multiusuário, tenant, roles, delegação, revogação ou ownership complexo? |
| Auditoria | Quais ações precisam provar ator, momento, versão e consequência? |
| Dispositivo | Mobile, web, desktop, edge, hardware restrito ou equipamento antigo? |
| Integrações | Quais dependências externas existem? São críticas? Possuem fallback? |
| Arquivos | Há upload, mídia, planilha, documento ou processamento pesado? |
| Assíncrono | Quais tarefas não devem acontecer dentro da resposta interativa? |
| Regulação | Existe localização de dados, retenção, exclusão, evidência ou certificação? |
| Time | Quantas pessoas desenvolverão e operarão? Qual maturidade e disponibilidade? |
| Operação | Quem responde a incidente? Existe horário crítico? |
| Custo | Qual é o limite ou sensibilidade de custo do horizonte atual? |
| Evolução | Quais mudanças são plausíveis e quais são apenas especulação? |

Não inventar precisão.

Se o produto ainda não possui dados reais, registrar estimativas como estimativas.

---

## 8. Estados de conhecimento técnico

Cada afirmação relevante da mensuração deve poder ser classificada.

| Estado | Significado |
| --- | --- |
| MEDIDO | Existe dado real do sistema ou experimento reproduzível. |
| CONFIRMADO | É uma restrição ou decisão humana/externa verificada. |
| ESTIMADO | Existe cálculo plausível, mas ainda sem telemetria real. |
| HIPÓTESE | Pode afetar arquitetura, mas ainda precisa ser validada. |
| PENDENTE | Informação insuficiente para decidir. |
| DESCARTADO | Alternativa analisada e rejeitada conscientemente. |

Exemplo:

```text
DAU esperado no beta: 500
ESTADO: ESTIMADO
FONTE: projeção de produto
IMPACTO: ainda não justifica particionamento
REVALIDAR: após 2 semanas de beta
```

A arquitetura não deve transformar uma estimativa em fato apenas para parecer completa.

---

## 9. Drivers arquiteturais

Drivers são forças que realmente alteram a estrutura ou as escolhas técnicas posteriores.

Exemplos:

- tarefa crítica precisa funcionar sem rede;
- dados não podem cruzar tenants;
- revogação precisa ter efeito imediato;
- escrita duplicada não pode produzir efeito duas vezes;
- histórico precisa preservar autoria e versão;
- integração externa pode ficar indisponível sem derrubar o core;
- cliente antigo precisa conviver com servidor novo;
- arquivo não confiável precisa ser tratado como dado hostil;
- recuperação precisa ocorrer dentro de uma janela definida;
- operação precisa começar com equipe pequena;
- custo inicial possui limite forte;
- produto precisa atender região ou regra regulatória específica.

Cada driver deve registrar:

```text
ID
Origem
Descrição
Por que altera arquitetura
Prioridade
Estado de conhecimento
Evidência
Decisões relacionadas
Como será validado
```

Sugestão de IDs:

```text
ARCH-DRV-001
ARCH-DRV-002
...
```

---

## 10. Atributos de qualidade

Atributos de qualidade devem ser descritos como cenários testáveis, não como adjetivos.

Evitar:

```text
“O sistema precisa ser rápido.”
“O sistema precisa ser escalável.”
“O sistema precisa ser seguro.”
```

Preferir:

```text
CENÁRIO
Durante uma sessão crítica,
uma perda temporária de rede
não pode impedir o registro local
nem causar duplicação quando a rede voltar.
```

Um cenário pode registrar:

| Campo | Conteúdo |
| --- | --- |
| ID | `QA-xxx` |
| Atributo | performance, disponibilidade, segurança, etc. |
| Fonte | jornada/regra/risco que originou a necessidade |
| Estímulo | o que acontece |
| Contexto | em qual condição |
| Resposta | o que o sistema precisa fazer |
| Medida | como provar |
| Prioridade | crítica, alta, média, baixa ou equivalente |
| Trade-off | o que pode ser sacrificado e o que não pode |

Atributos frequentes incluem:

- segurança;
- privacidade;
- confiabilidade;
- disponibilidade;
- durabilidade;
- consistência;
- desempenho;
- responsividade percebida;
- escalabilidade;
- manutenibilidade;
- testabilidade;
- operabilidade;
- observabilidade;
- recuperabilidade;
- compatibilidade;
- portabilidade;
- auditabilidade;
- extensibilidade.

Nem todo projeto precisa otimizar todos igualmente.

Arquitetura é, em parte, tornar explícitos esses trade-offs.

---

## 11. Restrições, não objetivos e orçamento de complexidade

A etapa deve registrar restrições reais e não objetivos técnicos.

Exemplos de não objetivos:

- multi-região ativa-ativa antes de existir justificativa;
- microserviços sem necessidade de isolamento;
- suporte offline para módulos que podem degradar online;
- consistência forte em dados onde eventual é suficiente;
- abstração de fornecedor sem hipótese concreta de troca;
- sistema de eventos global apenas por tendência arquitetural.

O documento deve manter um **orçamento de complexidade**.

Toda complexidade adicional precisa responder:

```text
QUE RISCO OU DRIVER ELA RESOLVE?
        ↓
EXISTE FORMA MAIS SIMPLES?
        ↓
QUAL CUSTO OPERACIONAL E COGNITIVO INTRODUZ?
        ↓
COMO SABEREMOS SE CONTINUA NECESSÁRIA?
```

---

## 12. Decomposição de domínio

O sistema deve ser decomposto primeiro por responsabilidade e regra, não por tabela, tela ou framework.

Para cada domínio ou contexto relevante, registrar:

```text
NOME
RESPONSABILIDADE
ENTIDADES / CONCEITOS CENTRAIS
INVARIANTES
FONTE CANÔNICA
COMANDOS PRINCIPAIS
LEITURAS PRINCIPAIS
EVENTOS RELEVANTES
DADOS SENSÍVEIS
DEPENDÊNCIAS PERMITIDAS
DEPENDÊNCIAS PROIBIDAS
OWNERSHIP
```

Exemplos genéricos:

```text
IDENTITY
CATALOG
ORDER
BILLING
NOTIFICATION
MODERATION
REPORTING
```

Esses nomes não são uma taxonomia obrigatória.

A decomposição nasce do produto.

---

## 13. Boundaries e regra de dependência

A arquitetura deve mostrar quem pode depender de quem.

Exemplo conceitual:

```text
EXPERIÊNCIA
        ↓
APLICAÇÃO / CASOS DE USO
        ↓
DOMÍNIO

ADAPTADORES
        → implementam portas

INFRAESTRUTURA
        → permanece na borda
```

Essa forma não é obrigatória para todos os projetos.

O princípio obrigatório é impedir que detalhes voláteis se tornem a única forma de expressar regras duráveis.

Definir explicitamente:

- imports permitidos;
- imports proibidos;
- ownership de regra;
- ownership de transação;
- ownership de dados;
- como módulos se comunicam;
- onde validação é autoritativa;
- quais contratos podem atravessar boundaries;
- que payloads externos nunca viram entidade interna diretamente.

---

## 14. Escolha de estilo arquitetural

A etapa pode escolher **forma arquitetural**, pois essa é uma decisão de estrutura, não de ferramenta.

Alternativas podem incluir, conforme o problema:

- monólito simples;
- monólito modular;
- serviços independentes;
- arquitetura orientada a eventos;
- funções isoladas;
- arquitetura híbrida;
- cliente local-first com backend canônico;
- processamento assíncrono especializado.

A comparação deve considerar drivers reais.

Exemplo:

| Critério | Opção A | Opção B | Opção C |
| --- | --- | --- | --- |
| Complexidade operacional | | | |
| Transações | | | |
| Isolamento de falha | | | |
| Escala independente | | | |
| Velocidade de mudança | | | |
| Custo | | | |
| Portabilidade | | | |
| Adequação ao time | | | |

A resposta pode perfeitamente ser:

```text
MONÓLITO MODULAR AGORA

porque:
- time pequeno;
- transações fortes entre domínios;
- escala ainda não medida;
- menor custo operacional;

extrair serviço somente se:
- houver escala independente persistente;
- isolamento regulatório;
- runtime incompatível;
- ownership organizacional estável;
- falha precisar ser isolada.
```

---

## 15. ADR — Architecture Decision Record

Toda decisão arquitetural durável deve possuir ADR quando sua reversão tiver custo relevante ou quando existir alternativa plausível.

Formato mínimo:

```text
ADR-xxx — título

STATUS
proposto | aceito | substituído | rejeitado

CONTEXTO
forças e restrições

DECISÃO
regra objetiva

ALTERNATIVAS
opções consideradas

CONSEQUÊNCIAS
positivas e negativas

VALIDAÇÃO
como provar

GATILHO DE REVISÃO
quando reabrir
```

Uma ADR desta etapa não deve escolher pacote concreto se essa decisão pertencer ao Tech Lead.

Exemplo válido:

```text
ADR-004
Usar persistência relacional transacional
para o domínio canônico.
```

A Visão do Tech Lead poderá depois decidir qual engine concreta satisfaz esse requisito.

---

## 16. Arquitetura de dados

Esta etapa deve definir a **semântica arquitetural dos dados**, não necessariamente o produto de banco.

Para cada conjunto relevante, determinar:

- autoridade;
- ownership;
- identidade;
- mutabilidade;
- versionamento;
- sensibilidade;
- retenção;
- isolamento;
- consistência;
- auditabilidade;
- necessidade de transação;
- comportamento em exclusão;
- comportamento em sincronização;
- possibilidade de reconstrução;
- requisitos de índice/consulta em nível conceitual;
- política de migration e compatibilidade.

### 16.1. Fonte canônica

Todo dado importante deve ter uma fonte canônica reconhecível.

Evitar:

```text
mobile possui um valor
web possui outro
backend possui outro
analytics vira referência
```

Perguntar:

```text
QUEM PODE DECIDIR O VALOR CANÔNICO?
QUEM PODE APENAS REPRESENTÁ-LO?
QUEM PODE PROPOR ALTERAÇÃO?
QUEM PODE AUDITÁ-LO?
```

### 16.2. Invariantes estruturais

Invariantes simples devem, quando possível, ser expressáveis por constraints, tipos, transações ou comandos autoritativos.

Exemplos:

- versão publicada não é alterada retroativamente;
- saldo deriva de ledger e não de valor arbitrário do cliente;
- revogação invalida acesso futuro;
- repetição de comando não duplica efeito;
- deleção sincronizável não ressuscita por cliente atrasado.

### 16.3. Consistência

Não aplicar consistência forte ou eventual como religião.

Classificar por operação:

```text
PRECISA SER ATÔMICO?
PRECISA SER SERIALIZÁVEL?
PODE SER EVENTUAL?
PODE SER RECONSTRUÍDO?
PODE SER CACHE?
```

---

## 17. Contratos, comandos, queries e eventos

A arquitetura deve definir a semântica das interações relevantes.

### 17.1. Comandos

Um comando importante pode precisar registrar:

- ator;
- autorização;
- recurso;
- versão base;
- idempotency key;
- resultado;
- erro estável;
- auditoria;
- evento decorrente.

### 17.2. Queries

Queries devem declarar:

- fonte autoritativa;
- escopo de acesso;
- paginação quando aplicável;
- consistência esperada;
- cache permitido ou proibido;
- limites.

### 17.3. Eventos

Eventos arquiteturais devem declarar:

```text
NOME
VERSÃO
EMISSOR
SIGNIFICADO
CONSUMIDORES ESPERADOS
PAYLOAD MÍNIMO
SEMÂNTICA DE ENTREGA
REPLAY
IDEMPOTÊNCIA
RETENÇÃO
```

Não publicar eventos “porque talvez alguém use depois”.

---

## 18. APIs e protocolos

A arquitetura pode definir contratos de interação e, quando material ao sistema, o padrão de protocolo.

Deve registrar:

- versionamento;
- erros estáveis;
- autenticação e contexto de ator;
- autorização;
- limites;
- paginação;
- concorrência;
- idempotência;
- compatibilidade;
- depreciação;
- timeout semântico;
- política de retry;
- correlação;
- schemas.

Uma API não deve nascer diretamente de tabelas apenas porque a ferramenta facilita.

O contrato público representa capacidade e regra.

---

## 19. Offline, local-first e sincronização

Só incluir esta seção quando a experiência realmente exigir.

Primeiro classificar cada domínio:

| Domínio/tarefa | Offline | Escrita local | Autoridade | Recuperação |
| --- | --- | --- | --- | --- |
| Exemplo A | completa | sim | local temporária + canônica posterior | sync |
| Exemplo B | leitura | não | servidor | cache degradado |
| Exemplo C | não | não | servidor | mensagem/fallback |

### 19.1. Contrato local-first

Quando uma tarefa crítica for local-first, definir:

- o que precisa existir localmente;
- quando a UI pode afirmar sucesso;
- o que significa pendente;
- como a intenção de sincronização é persistida;
- como retry funciona conceitualmente;
- como duplicidade é evitada;
- como conflitos são reconhecidos;
- como deleções se propagam;
- como versão antiga convive com nova;
- como logout, troca de conta e retenção local funcionam.

### 19.2. Conflitos

Conflito não deve ser escondido por uma política global de “última escrita vence” quando existe significado de domínio.

Criar matriz por objeto:

```text
OBJETO
TIPO DE CONFLITO
AUTORIDADE
MERGE POSSÍVEL?
AÇÃO AUTOMÁTICA
AÇÃO DO USUÁRIO
AUDITORIA
```

A arquitetura define essa semântica.

O Tech Lead escolherá a tecnologia concreta que a materializa.

---

## 20. Integrações externas

Toda integração externa deve ser tratada como dependência potencialmente indisponível, mutável e não confiável.

Registrar:

| Campo | Pergunta |
| --- | --- |
| Capacidade | O que a integração fornece? |
| Criticidade | O core depende dela? |
| Autoridade | O dado externo é verdade, sugestão ou referência? |
| Autenticação | Que tipo de credencial/contexto será necessário? |
| Dados | O que pode sair e entrar? |
| Timeout | Quanto esperar antes de degradar? |
| Retry | Leitura e escrita têm o mesmo comportamento? |
| Cache | É permitido? Por quanto tempo? |
| Fallback | Existe alternativa manual ou provider secundário? |
| Kill switch | Podemos desligar a integração sem quebrar o core? |
| Auditoria | Que ações precisam de trilha? |
| Custo | Existe risco por volume? |
| Contrato | Como detectar breaking change? |

Aplicar ports/adapters ou mecanismo equivalente quando isso proteger o domínio de contratos voláteis.

---

## 21. Trabalho assíncrono

Identificar trabalhos que não precisam ou não devem permanecer dentro de uma transação/resposta interativa.

Exemplos:

- envio de e-mail;
- push;
- geração de exportação;
- processamento de mídia;
- reconciliação;
- moderação;
- ingestão externa;
- tarefas pesadas;
- notificações;
- materialização de projeções.

Para cada trabalho assíncrono definir:

```text
GATILHO
DURABILIDADE
SEMÂNTICA DE ENTREGA
IDEMPOTÊNCIA
ORDEM
RETRY
DEAD LETTER / FALHA TERMINAL
OBSERVABILIDADE
CANCELAMENTO
RETENÇÃO
```

A tecnologia de fila será escolhida posteriormente.

---

## 22. Cache

Cache não deve ser usado para esconder modelagem ou consulta ruim.

Antes de introduzir cache, responder:

- o dado pode ficar desatualizado?
- por quanto tempo?
- como invalidar?
- pode afetar autorização?
- quem é a fonte canônica?
- o cache pode ser reconstruído?
- qual gargalo real ele resolve?

Cache de autorização exige cuidado especial e não deve permitir acesso após revogação quando isso viola o contrato de produto.

---

## 23. Segurança e privacidade arquitetural

A etapa deve converter riscos de produto e UX em **trust boundaries e controles arquiteturais**.

### 23.1. Threat model

Para superfícies relevantes registrar:

```text
ATIVOS
ATORES
TRUST BOUNDARIES
ENTRADAS
DADOS SENSÍVEIS
AMEAÇAS
CONTROLES
RISCO RESIDUAL
PROVAS
```

Áreas que normalmente merecem análise dedicada:

- autenticação;
- autorização;
- multi-tenant;
- dados sensíveis;
- upload;
- webhooks;
- integrações;
- pagamento;
- moderação;
- rewards/fraude;
- admin;
- sync;
- secrets;
- export/delete.

### 23.2. Autorização

A UI nunca deve ser a única barreira de autorização.

A arquitetura precisa definir onde a decisão autoritativa acontece e quais informações entram nessa decisão:

```text
SUJEITO
RECURSO
AÇÃO
CONTEXTO
OWNERSHIP
PAPEL
CONSENTIMENTO
ESTADO DE REVOGAÇÃO
```

### 23.3. Minimização

Para cada fronteira perguntar:

```text
ESTE CAMPO PRECISA ATRAVESSAR?
ESTE LOG PRECISA EXISTIR?
ESTE EVENTO PRECISA DESTE DADO?
ESTE PROVIDER PRECISA RECEBÊ-LO?
```

---

## 24. Observabilidade como requisito arquitetural

Engenharia e Arquitetura definem **o que precisa ser observável**, não o fornecedor concreto.

Considerar:

- logs estruturados;
- métricas;
- traces;
- audit logs;
- eventos de produto;
- correlation IDs;
- release/version IDs;
- queue age;
- sync lag;
- dependências externas;
- falhas por domínio;
- indicadores de segurança;
- sinais de capacidade.

Definir também:

```text
CAMPOS PERMITIDOS
DADOS PROIBIDOS
CARDINALIDADE
RETENÇÃO NECESSÁRIA
OWNER DO SINAL
DECISÃO QUE O ALERTA DISPARA
```

A ferramenta concreta virá em Tech Lead/DevOps conforme a natureza da decisão.

---

## 25. Confiabilidade, SLO, RTO e RPO

Nem todo projeto precisa de SLO formal no primeiro dia.

Mas tarefas críticas precisam de expectativa explícita.

### 25.1. SLO

Quando aplicável, definir por jornada ou capacidade:

```text
INDICADOR
OBJETIVO
JANELA
ESCOPO
CONDIÇÃO DE REVISÃO
```

Se não houver dados reais, marcar como **target inicial**, não como fato.

### 25.2. RTO e RPO

Definir a partir do impacto de negócio:

```text
RTO
quanto tempo a capacidade pode ficar indisponível?

RPO
quanto dado podemos perder no pior caso aceitável?
```

Engenharia define a necessidade.

DevOps/Infraestrutura decidirá como atingir essas metas com backup, replicação, restore, regiões e outros mecanismos.

---

## 26. Ambientes como requisito, não provider

Esta etapa pode definir a necessidade de isolamento entre ambientes.

Exemplo:

```text
LOCAL
PR/PREVIEW
STAGING
PRODUCTION
```

Mas não deve escolher aqui, sem necessidade, qual fornecedor hospedará cada ambiente.

Definir:

- objetivo do ambiente;
- tipo de dado permitido;
- isolamento necessário;
- paridade mínima;
- gates de promoção;
- necessidade de sandbox externo;
- requisitos de rollback;
- restrições de segredo.

DevOps/Infra materializará isso posteriormente.

---

## 27. Backup, restore e continuidade como requisitos

A arquitetura deve declarar **o que precisa ser recuperável e em qual objetivo**.

Pode produzir uma matriz como:

| Ativo | Criticidade | RPO | RTO | Consistência necessária | Prova exigida |
| --- | --- | --- | --- | --- | --- |
| Dados canônicos | | | | | |
| Arquivos | | | | | |
| Configuração | | | | | |
| Segredos | | | | | |
| Estado local | | | | | |

A estratégia concreta de backup, PITR, replicação, storage e restore pertence a DevOps/Infraestrutura.

---

## 28. Escala e evolução

Arquitetura deve possuir **gatilhos**, não adivinhações.

Exemplos:

```text
SE latência de consulta degradar
→ medir plano/query
→ índice/modelagem
→ capacidade
→ só depois considerar nova camada

SE fila ultrapassar SLO
→ aumentar consumidores
→ separar workload se necessário

SE domínio exigir isolamento regulatório
→ avaliar extração

SE equipe possuir ownership independente estável
→ avaliar deploy independente
```

### 28.1. Regra para extração de serviço

Uma extração pode ser justificada por ao menos um fator material:

- escala independente persistente;
- isolamento de falha;
- isolamento regulatório;
- runtime realmente incompatível;
- deploy independente frequente;
- ownership organizacional estável;
- boundary de segurança forte;
- custo mensurável de manter junto.

Não extrair serviço apenas porque existe uma tabela ou um substantivo de negócio.

---

## 29. Portabilidade

Portabilidade não significa abstrair toda tecnologia.

Significa identificar onde lock-in é aceitável e onde seria destrutivo.

Perguntas:

- quais dados precisam ser exportáveis?
- quais contratos não podem depender do provider?
- quais integrações precisam de adapter?
- qual parte seria cara de migrar?
- existe motivo real para pagar esse custo agora?
- a estratégia de saída foi alguma vez testada?

Abstração sem cenário de troca também é custo.

---

## 30. Brownfield

Em sistema existente, esta etapa precisa produzir um mapa de realidade antes de propor arquitetura futura.

### 30.1. Mapear

- módulos reais;
- dependências reais;
- bancos e schemas;
- APIs;
- jobs;
- auth;
- integrações;
- deploys;
- incidentes;
- gargalos;
- dívida;
- contratos que clientes dependem;
- incompatibilidades conhecidas.

### 30.2. Classificar

```text
PRESERVAR
comportamento ou decisão válida

MIGRAR
estrutura válida, mas inadequada ao futuro

ENCAPSULAR
legado que precisa continuar sem contaminar domínio novo

SUBSTITUIR
decisão comprovadamente inadequada

REMOVER
código/contrato morto após prova de não uso
```

### 30.3. Strangler e migração incremental

Quando necessário, preferir caminhos incrementais que mantenham o produto operável e a reversão possível.

Não exigir big bang por estética arquitetural.

---

## 31. Relação com Técnicas de Desenvolvimento

`06_Tecnicas_de_Desenvolvimento.md` define **como desenvolver com qualidade**.

`07_Engenharia_e_Arquitetura.md` define **o que estruturalmente precisamos construir e preservar**.

Exemplo:

```text
TÉCNICAS
“operações críticas precisam de teste de repetição.”

ARQUITETURA
“o comando de finalização possui chave de idempotência
e resultado repetível.”
```

Outro exemplo:

```text
TÉCNICAS
“mudança de contrato precisa ser compatível.”

ARQUITETURA
“cliente N e servidor N+1 convivem durante a janela X;
remoção só ocorre após prova de não uso.”
```

---

## 32. Relação com a Visão do Tech Lead

Esta é uma das fronteiras mais importantes da metodologia.

A arquitetura deve entregar ao Tech Lead **um problema tecnológico mensurado**.

O Tech Lead recebe algo como:

```text
REQUERIMENTO ARQUITETURAL

- cliente mobile e web;
- domínio precisa permanecer desacoplado de UI;
- escrita crítica exige transação;
- revogação precisa ser autoritativa;
- tarefa X precisa funcionar offline;
- estado local precisa suportar migration;
- API precisa de contrato tipado/versionado;
- integração externa deve ser substituível;
- testes de unidade, contrato, integração e E2E são obrigatórios;
- build precisa ser reproduzível;
- time inicial possui N pessoas;
- custo inicial possui limite Y;
- compatibilidade precisa durar Z.
```

Só então o Tech Lead decide:

```text
LINGUAGEM
RUNTIME
FRAMEWORK
ENGINE DE BANCO
BIBLIOTECAS
SDKs
TOOLCHAIN
TEST RUNNERS
PACKAGE MANAGER
MONOREPO TOOL
VERSÕES
```

A escolha tecnológica deve apontar para quais requisitos arquiteturais ela satisfaz.

---

## 33. Matriz de requisitos para seleção tecnológica

A saída desta etapa deve conter uma matriz preparada para o Tech Lead.

Exemplo:

| ID | Necessidade | Obrigatória? | Evidência/origem | Como verificar solução candidata |
| --- | --- | --- | --- | --- |
| TECH-REQ-001 | suporte a execução mobile | Sim | UX/Jornada | build em alvo real |
| TECH-REQ-002 | persistência local transacional | Sim | offline | teste de crash/restart |
| TECH-REQ-003 | schema/contrato versionável | Sim | compatibilidade | contract test |
| TECH-REQ-004 | suporte de longo prazo | Sim | manutenção | política oficial |
| TECH-REQ-005 | custo inicial limitado | Sim | Briefing | projeção de custo |

Evitar critérios vagos como:

```text
“comunidade grande”
“moderno”
“popular”
“todo mundo usa”
```

sem explicar por que importam.

---

## 34. Relação com DevOps e Infraestrutura

Engenharia e Arquitetura devem entregar requisitos operacionais claros, mas não escolher a materialização concreta antes da hora.

Exemplo:

```text
ARQUITETURA
“produção precisa atender RPO de 24h
e RTO de 4h no horizonte beta.”

DEVOPS / INFRA
“qual mecanismo de backup,
restore, região e automação
atingirá essas metas?”
```

Outro:

```text
ARQUITETURA
“artefato promovido precisa ser imutável.”

DEVOPS
“qual pipeline, registry,
assinatura e promoção implementarão isso?”
```

---

## 35. O que não deve acontecer

### 35.1. Arquitetura por currículo

```text
“eu conheço framework X,
então a arquitetura será X.”
```

Errado.

### 35.2. Microserviços preventivos

```text
“um dia teremos milhões de usuários,
então vamos distribuir tudo agora.”
```

Errado sem driver mensurado.

### 35.3. Banco como domínio

```text
“tem tabela users,
logo existe serviço users.”
```

Errado.

### 35.4. Cloud como arquitetura

```text
“usaremos provider X”
```

não é descrição suficiente de arquitetura.

### 35.5. Diagrama sem contratos

Caixas e setas sem responsabilidade, ownership, consistência, erro e dependência não constituem arquitetura suficiente.

### 35.6. Generalidade ilimitada

Não criar interfaces abstratas para todos os futuros providers imagináveis.

### 35.7. Decisão irreversível sem ADR

Se a mudança futura for cara, a razão atual precisa ser rastreável.

---

## 36. Rastreabilidade arquitetural

Toda decisão relevante deve apontar para sua origem.

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
Visão do Tech Lead
```

Sugestão de IDs:

```text
ARCH-DRV-xxx  driver
QA-xxx        atributo/cenário de qualidade
ARCH-DOM-xxx  domínio/boundary
ARCH-INV-xxx  invariante
ARCH-INT-xxx  integração
ARCH-SEC-xxx  controle/trust boundary
ARCH-DATA-xxx decisão de dados
ADR-xxx       decisão arquitetural
TECH-REQ-xxx  requisito para seleção tecnológica
ARCH-GATE-xxx gate arquitetural
```

IDs removidos não devem ser reutilizados.

---

## 37. Readiness arquitetural

Usar estados explícitos:

```text
ARCHITECTURE_READINESS: INSUFFICIENT
ARCHITECTURE_READINESS: SUFFICIENT_WITH_OPEN_QUESTIONS
ARCHITECTURE_READINESS: SUFFICIENT
```

`SUFFICIENT_WITH_OPEN_QUESTIONS` é válido quando as pendências possuem owner, risco e momento de resolução e não impedem a seleção tecnológica.

A arquitetura está suficientemente pronta quando conseguimos responder sem inventar:

1. quais são os drivers arquiteturais;
2. quais atributos de qualidade dominam;
3. quais são as principais restrições;
4. quais são os domínios e boundaries;
5. onde vivem as invariantes;
6. qual é a direção de dependência;
7. quais dados são canônicos e sensíveis;
8. quais operações exigem transação, consistência ou idempotência;
9. como versionamento e compatibilidade funcionam;
10. quais integrações existem e como degradam;
11. qual é a política de offline/sync quando aplicável;
12. quais trust boundaries existem;
13. quais requisitos de observabilidade e recuperação existem;
14. quais gatilhos de escala existem;
15. quais decisões possuem ADR;
16. quais requisitos a stack precisa satisfazer;
17. quais pendências continuam abertas e por quê.

---

## 38. Gates de arquitetura

Antes do handoff para Tech Lead, verificar:

| Gate | Evidência |
| --- | --- |
| ARCH-01 Drivers | Drivers rastreáveis às etapas anteriores. |
| ARCH-02 Qualidade | Cenários de qualidade priorizados e testáveis. |
| ARCH-03 Domínio | Boundaries, ownership e dependências definidos. |
| ARCH-04 Dados | Autoridade, consistência, sensibilidade, retenção e migração definidos. |
| ARCH-05 Contratos | Comandos, queries, eventos e compatibilidade suficientes. |
| ARCH-06 Offline | Escopo, sync e conflitos definidos quando aplicável. |
| ARCH-07 Integrações | Criticidade, fallback e isolamento registrados. |
| ARCH-08 Segurança | Trust boundaries, authz, threat model e minimização suficientes. |
| ARCH-09 Confiabilidade | Disponibilidade, RTO/RPO e recuperação definidos quando materiais. |
| ARCH-10 Evolução | Gatilhos de escala e extração definidos. |
| ARCH-11 ADRs | Decisões duráveis registradas com alternativas e consequências. |
| ARCH-12 Tech Handoff | Matriz TECH-REQ pronta para seleção tecnológica. |

---

## 39. Síntese antes da canonização

Antes de criar o artefato final do projeto, o ChatGPT deve apresentar ao humano uma síntese contendo:

```text
MENSURAÇÃO TÉCNICA
DRIVERS ARQUITETURAIS
ATRIBUTOS DE QUALIDADE
RESTRIÇÕES
NÃO OBJETIVOS
DOMÍNIOS E BOUNDARIES
REGRAS DE DEPENDÊNCIA
DADOS CANÔNICOS
INVARIANTES
CONTRATOS
OFFLINE / SYNC
INTEGRAÇÕES
SEGURANÇA / TRUST BOUNDARIES
OBSERVABILIDADE
RTO / RPO / CONFIABILIDADE
GATILHOS DE ESCALA
ADRs PROPOSTAS
TECH-REQs
PENDÊNCIAS
ARCHITECTURE_READINESS
```

O humano pode:

- corrigir;
- pedir comparação adicional;
- rejeitar complexidade;
- alterar uma restrição;
- solicitar ADR adicional;
- reabrir etapa anterior quando uma necessidade de produto estiver contraditória.

---

## 40. Aprovação e canonização

Aprovação conceitual e escrita persistente continuam sendo atos distintos quando não houver autorização inequívoca.

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
07_Engenharia_e_Arquitetura.md
```

Uma vez canonizado, decisões arquiteturais não devem ser alteradas silenciosamente pelo Tech Lead ou por DevOps.

Se uma tecnologia candidata revelar inviabilidade real:

```text
TECH LEAD
        ↓
RESTRIÇÃO REAL DESCOBERTA
        ↓
IMPACTA ARQUITETURA?
        ↓
SIM
        ↓
REABRIR ADR / RECONCILIAR 07
```

---

## 41. Estrutura mínima do artefato de projeto

O projeto deve produzir `07_Engenharia_e_Arquitetura.md` com estrutura equivalente a:

```markdown
---
document_id: DOC-07
title: Engenharia e Arquitetura
status: canonical
version: 1.0.0
next_document: Visao_do_Tech_Lead.md
---

# Engenharia e Arquitetura

## 1. Contexto técnico e horizonte
## 2. Mensuração técnica
## 3. Drivers arquiteturais
## 4. Atributos de qualidade
## 5. Restrições e não objetivos
## 6. Domínios e boundaries
## 7. Regras de dependência
## 8. Arquitetura-alvo
## 9. Dados canônicos e invariantes
## 10. Transações e consistência
## 11. Contratos, comandos, queries e eventos
## 12. Compatibilidade e versionamento
## 13. Offline e sincronização
## 14. Integrações externas
## 15. Trabalho assíncrono e cache
## 16. Segurança, privacidade e threat model
## 17. Observabilidade arquitetural
## 18. Confiabilidade, RTO e RPO
## 19. Ambientes requeridos
## 20. Backup/restore como requisito
## 21. Escala, evolução e gatilhos
## 22. ADRs
## 23. Matriz TECH-REQ
## 24. Pendências
## 25. Gates e Architecture Readiness
## 26. Handoff para Tech Lead
```

Se um bloco não se aplica, registrar `não aplicável` com justificativa em vez de inventar complexidade.

---

## 42. Handoff para a Visão do Tech Lead

O próximo documento deve consumir integralmente `07_Engenharia_e_Arquitetura.md`.

O Tech Lead recebe:

```text
DRIVERS
ATRIBUTOS DE QUALIDADE
BOUNDARIES
INVARIANTES
CONTRATOS
DADOS
OFFLINE / SYNC
SEGURANÇA
OBSERVABILIDADE
CONFIABILIDADE
ESCALA
RESTRIÇÕES
ADRs
TECH-REQs
```

E deve responder:

> **Quais tecnologias concretas satisfazem melhor este conjunto de necessidades neste horizonte, com quais trade-offs, versões, provas e regras de uso?**

O Tech Lead não deve redefinir silenciosamente:

- público;
- escopo;
- regra de negócio;
- jornada;
- requisito de acessibilidade;
- atributo de qualidade;
- boundary arquitetural;
- política de dados;
- requisito de segurança;
- ADR aceita.

Se uma tecnologia exigir violar algum desses pontos, a incompatibilidade deve ser tratada explicitamente.

---

## 43. Princípio final

> **Arquitetura não é escolher ferramentas. É transformar o produto em um conjunto explícito de forças, limites, invariantes e estruturas que permita escolher ferramentas com justificativa.**

E:

> **O Tech Lead não deve receber uma folha em branco para escolher a stack; deve receber um sistema tecnicamente mensurado.**

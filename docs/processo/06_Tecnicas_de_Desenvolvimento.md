---
document_id: PROCESS-06-TECNICAS-DESENVOLVIMENTO
title: Técnicas de Desenvolvimento
status: draft-methodology
version: 0.1.0
stage: tecnicas-desenvolvimento
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
  - Principios_de_UX_UI.md
  - 04_Direcao_de_UI_e_Design_System.md
  - 05_Especificacao_de_UX.md
produces: 06_Tecnicas_de_Desenvolvimento.md
next_stage: 07_Engenharia_e_Arquitetura.md
---

# 06 — Técnicas de Desenvolvimento

## 1. Propósito

A etapa **Técnicas de Desenvolvimento** define **como o software deve ser desenvolvido, revisado, testado, documentado e mantido com qualidade**, independentemente das tecnologias concretas que serão escolhidas posteriormente.

A pergunta central desta etapa é:

> **Quais políticas, práticas, gates e critérios de qualidade devem governar o trabalho de engenharia — humano ou assistido por IA — para que as decisões de produto e experiência possam ser implementadas com segurança, legibilidade, verificabilidade, reversibilidade e manutenção sustentável?**

Esta etapa não escolhe stack.

Ela cria o **sistema operacional de engenharia** que a stack futura deverá ser capaz de sustentar.

A saída desta etapa ainda **não autoriza implementação pelo Codex**.

---

## 2. Posição no processo

```text
00_Discovery.md
        ↓
01_Pesquisa_e_Viabilidade.md
        ↓
02_Briefing_de_Produto_e_Escopo.md
        ↓
03_Visao_de_Product_Owner.md
        ↓
Principios_de_UX_UI.md
        ↓
04_Direcao_de_UI_e_Design_System.md
        ↓
05_Especificacao_de_UX.md
        ↓
06_TECNICAS_DE_DESENVOLVIMENTO
        ↓
07_Engenharia_e_Arquitetura.md
        ↓
Visao_do_Tech_Lead.md
        ↓
DevOps / Infraestrutura
        ↓
Backlog canônico + rastreabilidade
        ↓
Handoff para Codex
```

A Especificação de UX encerra a definição detalhada de comportamento da experiência.

As Técnicas de Desenvolvimento definem **como a engenharia deverá trabalhar para preservar esses contratos**.

A etapa seguinte, Engenharia e Arquitetura, deverá transformar produto e UX em **forças técnicas, atributos de qualidade, domínios, boundaries, contratos estruturais e arquitetura**.

A Visão do Tech Lead, em etapa posterior, deverá escolher **linguagens, runtimes, frameworks, bibliotecas, persistência concreta e toolchain** compatíveis com essa arquitetura e com os gates definidos aqui.

DevOps e Infraestrutura deverão materializar **build, ambientes, CI/CD, deploy, segredos, observabilidade operacional, backup, recuperação e execução da stack**.

---

## 3. Origem desta etapa

Esta etapa foi formalizada a partir do processo real utilizado no DayGym.

No documento original, Técnicas de Desenvolvimento era uma política vinculante para pessoas desenvolvedoras, agentes de IA, revisão, CI e QA. Seu contrato central era:

```text
IA propõe.
Automação verifica.
Uma pessoa responde pelo resultado.
```

O documento original também fazia uma separação valiosa: **esta etapa fixa como desenvolver; a etapa técnica posterior escolhe arquitetura, stack e infraestrutura**.

A metodologia preserva essa essência, mas refina a distribuição futura de responsabilidade:

```text
TÉCNICAS DE DESENVOLVIMENTO
= como trabalhar com qualidade

ENGENHARIA E ARQUITETURA
= o que tecnicamente precisa ser verdade
  e como o sistema deve ser estruturado

TECH LEAD
= com quais tecnologias concretas

DEVOPS / INFRA
= como construir, promover, executar e operar
```

Essa separação evita que uma política de qualidade se transforme, por repetição, em decisão de stack.

---

## 4. Pré-requisitos obrigatórios

Antes de iniciar esta etapa, o ChatGPT deve consumir integralmente os documentos canônicos anteriores.

O mínimo é compreender:

- problema e contexto do produto;
- escopo e fora de escopo;
- outcomes e regras de negócio;
- riscos e guardrails;
- princípios de UX/UI;
- direção visual e contratos do Design System;
- jornadas, fluxos, estados, validações e recuperação;
- requisitos de acessibilidade;
- requisitos de privacidade;
- necessidades de conectividade;
- eventos semânticos de produto;
- dependências externas conhecidas;
- riscos de segurança já identificados;
- decisões ainda pendentes.

Contradições materiais devem ser reconciliadas antes de serem transformadas em política de engenharia.

---

## 5. O que esta etapa decide

Técnicas de Desenvolvimento pode canonizar:

- responsabilidade por código assistido por IA;
- política de atuação de agentes;
- requisitos mínimos de contexto para uma tarefa técnica;
- condições de parada obrigatória;
- princípios de código legível e manutenível;
- padrões para estado, erro e efeitos;
- política para assincronismo, retry, timeout, cancelamento e idempotência;
- política Git;
- modelo de branch e pull request;
- política de revisão humana;
- estratégia de testes;
- política de qualidade de testes;
- tipos de gates obrigatórios;
- requisitos de segurança no SDLC;
- tratamento de segredos e dependências;
- requisitos de supply chain;
- política de acessibilidade na implementação;
- política de compatibilidade e migração;
- requisitos semânticos de observabilidade;
- política de documentação viva;
- Definition of Ready de engenharia;
- Definition of Done de engenharia;
- critérios de release no nível de qualidade;
- política de dívida técnica;
- métricas de saúde do sistema de entrega;
- playbook da issue até a promoção;
- critérios de passagem para Engenharia e Arquitetura.

---

## 6. O que esta etapa não decide

Esta etapa não deve canonizar prematuramente:

- linguagem de programação;
- runtime;
- framework;
- biblioteca;
- banco de dados concreto;
- mecanismo concreto de cache;
- fila concreta;
- storage concreto;
- provider de nuvem;
- vendor de observabilidade;
- ferramenta específica de CI/CD;
- organização física final do monorepo;
- quantidade definitiva de serviços;
- boundaries finais de deploy;
- topologia de infraestrutura;
- regiões de cloud;
- SLOs finais;
- capacidade e sizing de infraestrutura;
- estratégia concreta de disaster recovery;
- ferramenta concreta de gestão de segredos;
- contrato físico definitivo de API;
- mecanismo físico definitivo de sincronização;
- stack final de testes.

Exemplos técnicos podem aparecer para explicar uma prática, mas **não ganham autoridade arquitetural por estarem citados aqui**.

---

## 7. Princípio dominante

> **Velocidade de produção de código não é velocidade de produto.**

A metodologia otimiza o tempo entre:

```text
DECISÃO CORRETA
        ↓
MUDANÇA PEQUENA
        ↓
VERIFICAÇÃO CONFIÁVEL
        ↓
REVISÃO COMPREENSÍVEL
        ↓
PROMOÇÃO CONTROLADA
        ↓
RECUPERAÇÃO SIMPLES SE NECESSÁRIO
```

Código gerado rapidamente que aumenta incerteza, blast radius ou custo de recuperação não representa ganho real de velocidade.

---

## 8. Hierarquia de autoridade

Quando existir conflito durante implementação futura, a equipe deve seguir a precedência documental definida pela metodologia.

Uma forma recomendada é:

| Prioridade | Fonte | Autoridade |
| --- | --- | --- |
| 1 | Lei, segurança, privacidade e políticas obrigatórias | limites não negociáveis |
| 2 | Briefing e Visão de Product Owner | escopo, regras, prioridade e aceite do produto |
| 3 | Princípios UX/UI, Direção de UI e Especificação de UX | experiência, comportamento, estados e acessibilidade |
| 4 | Engenharia, Arquitetura e ADRs aprovadas | estrutura técnica e trade-offs |
| 5 | Visão do Tech Lead | escolhas tecnológicas concretas |
| 6 | DevOps / Infraestrutura | materialização operacional da stack |
| 7 | Técnicas de Desenvolvimento | método de implementação, revisão e qualidade |
| 8 | Issue, prompt ou sugestão local | execução de um recorte, sem poder de sobrescrever o canônico |

Essa tabela não significa que uma camada inferior deva obedecer cegamente a algo tecnicamente impossível.

Uma inviabilidade real abre **reconciliação documental**.

---

## 9. Princípios canônicos de engenharia

### DEV-P1 — Intenção antes de mecanismo

Código deve revelar a regra que implementa.

Uma pessoa competente deve conseguir localizar a responsabilidade e compreender o comportamento sem reconstruir o prompt que originou o código.

### DEV-P2 — Correto antes de otimizado

A sequência preferida é:

```text
CORRETO
↓
SIMPLES
↓
MENSURÁVEL
↓
OTIMIZADO QUANDO NECESSÁRIO
```

Otimização sem evidência não deve ocultar regra de domínio.

### DEV-P3 — Estado explícito

Estados materialmente diferentes não devem ser comprimidos em booleanos vagos.

Exemplo conceitual:

```text
PENDING
SAVED_LOCAL
SYNC_PENDING
SYNCED
CONFLICT
REVOKED
FAILED
```

quando o domínio realmente distinguir essas situações.

### DEV-P4 — Domínio não depende de mecanismo por conveniência

Regras críticas não devem existir apenas dentro de:

- componente visual;
- handler HTTP;
- callback de provider;
- job;
- script;
- banco;
- SDK externo.

A arquitetura posterior decidirá as fronteiras concretas, mas esta etapa já estabelece que **a regra precisa ser testável e compreensível sem depender de detalhes acidentais**.

### DEV-P5 — Efeitos controláveis

Tempo, rede, storage, geração de IDs, aleatoriedade e integrações precisam ser controláveis em testes quando influenciam comportamento relevante.

### DEV-P6 — Falha é caminho normal

Timeout, offline, cancelamento, duplicidade, resposta parcial, revogação, concorrência e indisponibilidade externa devem possuir comportamento previsto quando aplicáveis.

### DEV-P7 — Privacidade por construção

Coletar, transportar, retornar, logar e reter somente o necessário para a finalidade atual.

### DEV-P8 — Compatibilidade progressiva

Mudanças de contrato e dados devem permitir rollout e rollback seguros quando houver consumidores ou versões convivendo.

### DEV-P9 — Observável sem vazar

Operações importantes precisam ser diagnosticáveis sem copiar conteúdo sensível para telemetria comum.

### DEV-P10 — Reversibilidade por padrão

Mudança pequena, compatibilidade, flag e rollback reduzem o custo de corrigir uma decisão errada.

---

## 10. Atalhos proibidos

São proibidos como estratégia normal:

- comentar teste para obter pipeline verde;
- ignorar lint, typecheck ou análise de segurança para “desbloquear” merge;
- capturar exceção e continuar como sucesso;
- esconder falha em log sem recuperação;
- retornar `null`, `false` ou equivalente quando o domínio exige estado explícito;
- duplicar regra crítica em múltiplos clientes sem contrato ou prova de equivalência;
- incluir dependência sem verificar origem, manutenção, licença e risco;
- usar dados reais de produção em prompt, fixture, screenshot ou teste local;
- remover compatibilidade no mesmo passo destrutivo em que os dados são migrados;
- aceitar código que ninguém consegue explicar só porque compila;
- aumentar autonomia do agente removendo controles de segurança;
- tratar “funciona no happy path” como Definition of Done.

---

# 11. Política de desenvolvimento assistido por IA

## 11.1 Modelo de autoridade

Agentes de IA podem, quando autorizados:

- investigar;
- ler documentação;
- mapear o repositório;
- propor um plano;
- alterar arquivos;
- criar testes;
- executar verificações;
- revisar diffs;
- atualizar documentação.

Responsabilidade técnica, aceite do risco e decisão de merge pertencem a pessoas identificáveis.

```text
IA PROPÕE
AUTOMAÇÃO VERIFICA
HUMANO RESPONDE
```

### Regra

Código produzido por IA não recebe confiança adicional nem desconto de rigor.

Ele entra como contribuição **ainda não verificada**.

---

## 11.2 Classes de atuação

A classificação deve ser adaptada ao projeto, mas a metodologia recomenda pelo menos:

| Classe | Natureza | Tratamento |
| --- | --- | --- |
| Normal | boilerplate, refactor local, testes, documentação, mudança mecânica | review normal + gates |
| Sensível | autorização, criptografia, sync, migração, moderação, pagamento, antifraude, CI, infraestrutura | owner apropriado + análise de risco |
| Proibida sem autorização explícita | produção, segredos, dados reais, desativação de controle, autoaprovação | interromper e escalar |

---

## 11.3 Fluxo obrigatório para tarefa com IA

Antes de alterar código, o agente deve:

1. ler a tarefa e os critérios de aceite;
2. ler os documentos canônicos aplicáveis;
3. identificar conflito antes de editar;
4. mapear arquivos, contratos, testes e blast radius;
5. propor um plano curto;
6. identificar riscos;
7. definir verificações;
8. implementar a menor mudança coerente;
9. executar os gates aplicáveis;
10. revisar o próprio diff como adversário;
11. atualizar documentação necessária;
12. apresentar evidência e incertezas;
13. aguardar revisão humana quando exigida.

Mudança de escopo durante execução deve causar nova avaliação, não expansão silenciosa.

---

## 11.4 Pacote mínimo de contexto para um agente

Toda tarefa relevante deve informar, diretamente ou por links canônicos:

| Campo | Pergunta |
| --- | --- |
| Objetivo | Que problema e resultado observável estamos tentando resolver? |
| Escopo | Que módulos/arquivos/comportamentos podem mudar? |
| Fora de escopo | O que não pode ser alterado nesta tarefa? |
| Fontes | Quais documentos, histórias, ADRs e contratos governam a mudança? |
| Invariantes | O que nunca pode acontecer? |
| Estados | Que estados precisam continuar válidos? |
| Dados | Existe informação sensível ou restrita? |
| Risco | Auth, offline, concorrência, migração, fraude, parceiro, a11y etc.? |
| Verificação | Que testes, comandos e evidências demonstram correção? |
| Rollback | Como a mudança pode ser desativada ou revertida? |
| Parada | Em que situação o agente deve pedir decisão humana? |

Prompt sem contexto não substitui esse pacote.

---

## 11.5 Condições obrigatórias de parada do agente

O agente deve interromper e pedir decisão quando:

- requisito contradiz documento canônico;
- é necessária credencial não autorizada;
- é necessário dado real de usuário;
- mudança exige conta ou ação externa não autorizada;
- não existe estratégia segura de recuperação para risco relevante;
- API ou pacote sugerido não foi verificado;
- licença ou condição de uso é incerta;
- o agente precisa inventar regra de negócio;
- o agente precisa escolher stack ainda não aprovada;
- a mudança cria nova fronteira arquitetural não decidida;
- o teste disponível não consegue provar a regra;
- falha não é reproduzível e a correção seria especulativa;
- escopo cresce materialmente além da tarefa.

---

# 12. Código legível e manutenível

## 12.1 Nomes

Nomes devem usar o vocabulário do domínio e revelar intenção.

Evitar abreviações privadas e nomes genéricos como:

```text
data
info
manager
helper
utils2
flag
value
```

quando existir um conceito de domínio mais preciso.

---

## 12.2 Funções e unidades de código

Uma unidade deve:

- operar em nível de abstração coerente;
- limitar efeitos;
- possuir retorno compreensível;
- tornar caminho de erro explícito;
- ser extraída quando a intenção deixa de ser facilmente lida;
- evitar “função Deus” criada para concentrar passos desconexos.

A metodologia não fixa número universal de linhas por função.

O critério é **coesão e compreensibilidade**, não estética numérica.

---

## 12.3 Módulos

Módulos devem ter:

- responsabilidade reconhecível;
- API menor que sua implementação interna;
- contratos claros;
- baixo vazamento de detalhes;
- testes proporcionais ao risco;
- documentação quando a fronteira não for óbvia.

A divisão física dos módulos será definida posteriormente pela Arquitetura e pelo Tech Lead.

---

## 12.4 Tipos e estados

Quando a tecnologia escolhida suportar tipos estáticos ou modelagem equivalente, estados válidos devem ser representados explicitamente.

Quando não suportar, o Tech Lead deve garantir mecanismo equivalente de validação e teste.

Regra conceitual:

```text
MODELO REPRESENTA
APENAS ESTADOS VÁLIDOS
```

Não depender de convenção informal quando a violação puder causar perda de dados, acesso indevido ou regra inválida.

---

## 12.5 Erros

Erros relevantes devem separar:

```text
CÓDIGO ESTÁVEL
CONTEXTO SEGURO
CAUSA TÉCNICA
MENSAGEM PARA USUÁRIO
```

Mensagem de usuário não deve nascer por simples exposição de exception interna.

---

## 12.6 Comentários

Comentário serve para explicar:

- por quê;
- limite;
- trade-off;
- compatibilidade;
- razão de uma decisão não óbvia.

Não deve narrar a sintaxe nem compensar um nome ruim.

---

## 12.7 Configuração

Configuração deve ser:

- validada no início quando possível;
- separada por ambiente;
- falhar claramente quando requisito obrigatório não existe;
- nunca conter segredo hardcoded;
- compatível com a política futura de infraestrutura.

---

# 13. Assincronismo, concorrência e idempotência

Esta etapa define a política; a arquitetura posterior define a implementação concreta.

## 13.1 Operação remota

Toda operação remota relevante deve ter política explícita para:

- timeout;
- retry;
- backoff quando aplicável;
- cancelamento;
- erro parcial;
- repetição;
- observabilidade;
- comportamento da UI.

Escrita irreversível não deve ser repetida cegamente.

---

## 13.2 Idempotência

Quando uma mesma intenção pode chegar mais de uma vez, a solução deve impedir efeito duplicado.

Exemplos de gatilhos:

- double tap;
- retry automático;
- reconexão;
- webhook repetido;
- callback de parceiro;
- reprocessamento de fila;
- reenvio após timeout.

A UX descreve o comportamento esperado.

Engenharia e Arquitetura definem onde a idempotência pertence.

Tech Lead escolhe as primitivas concretas.

---

## 13.3 Concorrência

Quando duas mudanças podem disputar o mesmo recurso, o projeto deve explicitar:

- o que caracteriza conflito;
- se merge é possível;
- se uma versão deve prevalecer;
- se o usuário precisa decidir;
- como auditoria é preservada.

`last-write-wins` não deve aparecer por acidente como política de negócio.

---

## 13.4 Tempo

Relógio, timezone, calendário e ordenação temporal devem ser tratados como dependências controláveis quando influenciam regra.

Testes devem cobrir fronteiras relevantes ao domínio.

---

# 14. Git, branches, commits e pull requests

## 14.1 Branch principal

A branch principal deve ser tratada como **sempre potencialmente implantável** depois que a infraestrutura existir.

Políticas recomendadas:

- sem push direto quando a equipe e a plataforma permitirem proteção;
- sem force push;
- checks obrigatórios;
- revisão humana proporcional ao risco;
- último SHA revisado antes do merge;
- conversas bloqueantes resolvidas.

---

## 14.2 Branches de trabalho

Preferir branches curtas e específicas.

Convenções de nome podem ser definidas pelo projeto, por exemplo:

```text
feat/
fix/
refactor/
chore/
```

O nome concreto não é o princípio.

O princípio é manter **lote pequeno, intenção clara e vida curta**.

---

## 14.3 Commits

Commit deve ser:

- coerente;
- reversível quando possível;
- compreensível;
- sem misturar formatação massiva com mudança funcional não relacionada.

A equipe pode adotar Conventional Commits ou outro padrão equivalente, mas a escolha final será registrada na baseline técnica.

---

## 14.4 Orçamento de tamanho do PR

A metodologia recomenda que cada projeto defina um orçamento explícito para tamanho de PR.

O DayGym utilizou faixas numéricas próprias para incentivar lotes pequenos.

Na metodologia reutilizável, esses números **não são universais**.

A política deve responder:

```text
QUAL TAMANHO NORMAL?
QUANDO PRECISA JUSTIFICAR?
QUANDO PRECISA DIVIDIR?
O QUE É EXCLUÍDO DA CONTAGEM?
```

Código gerado, lockfile, fixtures mecânicas e migrações podem exigir tratamento específico.

PR pequeno ainda pode ser crítico.

PR grande ainda pode ser mecânico.

Tamanho é sinal de revisabilidade, não métrica de mérito.

---

## 14.5 Conteúdo mínimo do PR

Um PR relevante deve explicar:

- problema e resultado;
- fonte canônica ou issue;
- o que mudou;
- o que não mudou;
- riscos;
- como testar;
- evidências executadas;
- migração e compatibilidade, quando aplicável;
- feature flag, rollout e rollback, quando aplicável;
- assistência de IA, quando utilizada;
- documentação alterada;
- pendências e incertezas restantes.

---

# 15. Revisão de código

## 15.1 Duas passagens

A metodologia recomenda separar a revisão em duas perguntas.

### Passagem 1 — intenção

```text
O problema pertence a esta mudança?
A solução respeita os documentos canônicos?
O design técnico está no lugar certo?
O blast radius é proporcional?
```

Se a resposta for não, a revisão linha a linha pode ser interrompida.

### Passagem 2 — implementação

Avaliar:

- correção;
- legibilidade;
- tipos/estados;
- erros;
- concorrência;
- segurança;
- privacidade;
- acessibilidade;
- testes;
- performance quando relevante;
- observabilidade;
- documentação;
- rollback.

---

## 15.2 Severidade dos comentários

A equipe deve distinguir comentário bloqueante de preferência.

Taxonomia recomendada:

| Classe | Exemplo |
| --- | --- |
| BLOCKER | correção, segurança, perda de dados, contrato violado |
| MAJOR | manutenção, teste, a11y, observabilidade ou risco relevante |
| MINOR | clareza/localidade de baixo risco |
| NIT | preferência não automatizada |
| QUESTION | falta de contexto ou hipótese do revisor |

O nome dos rótulos pode mudar; a distinção semântica deve permanecer.

---

## 15.3 Revisão humana e IA

Review por IA pode complementar a revisão.

Ele não substitui aprovação humana quando a política exigir uma pessoa responsável.

Uma IA não deve:

- aprovar o próprio trabalho como prova final;
- declarar segurança sem evidência;
- inferir aprovação humana ausente;
- substituir owner de domínio em mudança sensível.

---

# 16. Estratégia de testes

## 16.1 Princípio

Cobertura é sinal, não prova.

A estratégia deve combinar verificações próximas da regra com poucos testes ponta a ponta de maior custo.

Uma taxonomia recomendada:

| Camada | Principal prova |
| --- | --- |
| Unitário/domínio | regra pura, estado, cálculo, permissão |
| Componente/UI | renderização, interação, loading, erro, foco, a11y |
| Contrato | schema, compatibilidade, erro, evento |
| Integração | banco, storage, fila ou API real controlada |
| E2E smoke | jornada crítica |
| E2E ampliado | falha, recuperação, cross-device, parceiros |
| Não funcional | segurança, performance, carga, fuzz, resiliência, acessibilidade |

A stack concreta de testes será escolhida pelo Tech Lead.

---

## 16.2 Testes por risco

Cada domínio relevante deve possuir uma matriz contendo:

```text
FALHA PRINCIPAL
        ↓
IMPACTO
        ↓
PROVA MÍNIMA
        ↓
NÍVEL DE RISCO
```

Domínio crítico exige prova mais forte, não apenas maior percentual de cobertura.

---

## 16.3 Bugs

Todo bug reproduzível deve, sempre que praticável, produzir um teste ou outra prova executável que falhe antes da correção.

Quando isso não for possível, a exceção deve ser registrada com uma forma alternativa de reprodução e evidência.

---

## 16.4 Cobertura

A metodologia não estabelece um percentual universal para todos os projetos.

Cada baseline técnica deve definir:

- cobertura mínima útil;
- regras específicas para código alterado;
- invariantes que exigem cenários completos;
- política de exclusão;
- tratamento de código gerado;
- tratamento de UI e integração.

É proibido aumentar cobertura com testes sem asserção útil apenas para atingir meta.

---

## 16.5 Flaky tests

Teste instável continua sendo falha de engenharia.

A política deve definir:

- quando abrir issue;
- quando pode existir quarentena;
- prazo máximo de quarentena;
- owner;
- como a falha continua visível;
- critério para remoção.

Reexecutar até ficar verde sem compreender a causa não constitui evidência.

---

## 16.6 Qualidade do teste

Teste deve:

- explicar condição e resultado;
- ser determinístico quando possível;
- evitar rede pública;
- evitar relógio real não controlado;
- evitar dependência de ordem;
- usar fixture mínima;
- observar comportamento e contrato;
- não duplicar implementação dentro do próprio teste;
- cobrir cenários negativos proporcionais ao risco.

---

# 17. Gates de qualidade e CI

## 17.1 Responsabilidade desta etapa

Técnicas de Desenvolvimento define **quais tipos de verificação precisam existir**.

Ela não escolhe o produto de CI nem escreve a topologia final dos workflows.

Exemplo:

```text
TÉCNICAS
“PR deve executar lint, tipos, testes, segurança e build aplicáveis.”

DEVOPS
“GitHub Actions executará esses jobs nesta DAG, com estes runners e permissões.”
```

---

## 17.2 Estágios conceituais

O processo deve prever, quando compatível com o projeto:

### Local

Feedback rápido antes do push.

### Pull Request

Gates necessários para autorizar merge.

### Main

Prova de integração e geração do artefato promovível.

### Nightly / periódicos

Provas caras ou amplas que não precisam bloquear cada PR.

### Release

Verificações que autorizam promoção.

---

## 17.3 Checks típicos

Conforme stack e risco:

- formatter;
- lint;
- typecheck ou validação equivalente;
- testes unitários;
- testes de componente;
- contratos;
- integrações;
- build;
- secret scanning;
- análise de dependências;
- SAST;
- acessibilidade automatizável;
- smoke E2E;
- migration dry-run;
- geração de artefato;
- SBOM/proveniência quando aplicável.

O Tech Lead e DevOps definirão como cada check é implementado.

---

## 17.4 Regras de gate

- check ignorado por condição não conta como prova se o risco foi afetado;
- falha intermitente continua falha até diagnóstico;
- workflow deve operar com privilégio mínimo;
- segredos não devem aparecer em log;
- artefato promovido deve ser o artefato testado quando a arquitetura de entrega permitir;
- bypass emergencial exige auditoria, owner e recomposição posterior.

---

# 18. Segurança, privacidade e supply chain

## 18.1 Secure SDLC

Segurança deve entrar no ciclo, não apenas em auditoria final.

A baseline do projeto deve escolher referências atuais e adequadas ao tipo de sistema.

Exemplos de famílias de referência que podem ser consideradas e devem ser verificadas na versão vigente quando canonizadas:

- NIST SSDF;
- OWASP ASVS;
- OWASP MASVS/MASTG para mobile;
- guias de threat modeling;
- práticas de supply chain e SBOM.

A metodologia não fixa versões eternamente.

---

## 18.2 Quando exigir threat model

Threat model deve ser considerado em mudanças que criem ou alterem, por exemplo:

- autenticação;
- autorização;
- nova fronteira de confiança;
- dado sensível;
- upload/importação;
- webhook;
- pagamento/comércio;
- comunidade/moderação;
- mecanismo de recompensa;
- sincronização;
- área administrativa;
- integração externa crítica.

---

## 18.3 Segredos

Segredo:

- não entra em código;
- não entra em prompt;
- não entra em fixture;
- não entra em screenshot;
- não entra em log;
- deve poder ser rotacionado;
- precisa de acesso mínimo.

A ferramenta concreta de secret management será decidida em DevOps/Infra.

---

## 18.4 Dependências

Toda dependência nova deve ser avaliada quanto a:

- necessidade;
- origem;
- manutenção;
- licença;
- vulnerabilidades;
- custo de atualização;
- tamanho/runtime quando relevante;
- lock-in;
- capacidade de teste.

A escolha concreta é responsabilidade posterior do Tech Lead.

---

## 18.5 Classificação de dados

Cada projeto deve adotar classificação proporcional ao risco.

Modelo inicial possível:

| Classe | Tratamento |
| --- | --- |
| Público | pode circular com controle de integridade |
| Interno | somente ferramentas aprovadas |
| Confidencial | acesso por função e compartilhamento restrito |
| Sensível/restrito | mínimo acesso, auditoria e proibição em prompts/fixtures/telemetria comum |

A classificação concreta deve respeitar produto, lei e política interna.

---

## 18.6 Supply chain

A política deve considerar:

- manifesto e lockfile;
- resolução reproduzível;
- review de dependências;
- secret scanning;
- SAST;
- proveniência de build;
- SBOM quando aplicável;
- fixação de actions/plugins ou equivalente;
- permissões mínimas para automação.

---

# 19. Acessibilidade na implementação

A Direção de UI define o sistema visual.

A Especificação de UX define estados, interação e recuperação.

Técnicas de Desenvolvimento define **como essas decisões passam a ser verificáveis durante implementação**.

Áreas típicas:

| Área | Prova esperada |
| --- | --- |
| Semântica | componente + inspeção/teste |
| Foco | keyboard/switch/E2E quando aplicável |
| Texto ampliado | teste visual/manual |
| Contraste | token + automação + revisão |
| Toque | componente + dispositivo |
| Movimento | preferência do sistema + teste |
| Erro | componente/integração |
| Gráfico | conteúdo equivalente + tecnologia assistiva |

Automação não substitui tecnologia assistiva real quando o risco exigir avaliação manual.

Correção crítica de acessibilidade é defeito funcional, não polimento.

---

# 20. Contratos, compatibilidade e migrações

## 20.1 Contratos

Contratos relevantes devem ser:

- versionados;
- validados;
- documentados;
- testados em producer e consumer quando aplicável;
- compatíveis durante janela necessária;
- acompanhados de códigos de erro estáveis;
- minimalistas em dados.

A forma concreta do contrato pertence à Engenharia/Arquitetura.

---

## 20.2 Política de compatibilidade

Regra recomendada:

```text
ADICIONAR COMPATIBILIDADE
        ↓
CONVIVER
        ↓
MIGRAR
        ↓
MEDIR CONSUMIDORES
        ↓
REMOVER SOMENTE DEPOIS
```

Não remover contrato antigo antes que seus consumidores possam deixar de depender dele.

---

## 20.3 Migrações de dados

Para mudança material de dados, considerar o padrão:

```text
EXPAND
↓
PUBLICAR CÓDIGO COMPATÍVEL
↓
MIGRAR / BACKFILL
↓
VALIDAR
↓
MUDAR LEITURA
↓
MANTER JANELA DE ROLLBACK
↓
CONTRACT
```

Migrações devem ser:

- observáveis;
- retomáveis quando necessário;
- idempotentes quando repetição for possível;
- testadas;
- acompanhadas de plano de recuperação.

Alteração destrutiva exige estratégia explícita de backup/restore quando o risco justificar.

---

# 21. Observabilidade e operação — contrato de qualidade

Esta etapa define **o que precisa ser observável**.

DevOps/Infra decidirá **com quais ferramentas e topologia**.

## 21.1 Sinais conceituais

| Sinal | Função |
| --- | --- |
| Log estruturado | explicar evento pontual |
| Métrica | medir taxa, erro, latência, fila, crash ou guardrail |
| Trace | correlacionar caminho distribuído |
| Audit log | registrar ação privilegiada |
| Evento de produto | representar resultado de jornada |

---

## 21.2 Regra de minimização

Telemetria deve usar allowlist de campos quando o risco justificar.

Não serializar indiscriminadamente:

- body;
- header;
- token;
- objeto de request;
- texto social;
- notas;
- dados de saúde;
- dados financeiros;
- credenciais;
- qualquer conteúdo sensível do domínio.

---

## 21.3 Alertas

Alerta útil precisa de:

- significado;
- owner;
- condição acionável;
- rota de diagnóstico;
- runbook quando necessário.

Alarme que nunca muda uma decisão deve ser questionado.

---

## 21.4 Incidentes

O processo de engenharia deve prever:

1. detecção;
2. severidade;
3. owner/incidente commander quando aplicável;
4. contenção;
5. preservação de evidência;
6. comunicação factual;
7. recuperação do fluxo do usuário;
8. postmortem sem culpa;
9. ações com owner e prazo;
10. teste ou controle que reduza recorrência.

A infraestrutura concreta desse processo será definida posteriormente.

---

# 22. Documentação viva

Mudança de comportamento deve atualizar documentação no mesmo ciclo de mudança quando necessário.

Artefatos típicos:

| Artefato | Deve responder |
| --- | --- |
| README do projeto | como instalar, rodar, testar e navegar |
| CONTRIBUTING | como colaborar e revisar |
| SECURITY | como reportar e tratar segurança |
| ADR | por que decisão técnica durável foi tomada |
| Contrato | como interface entre componentes funciona |
| Runbook | como diagnosticar e recuperar operação crítica |
| Documento de módulo | responsabilidade e invariantes |
| Changelog | o que mudou entre releases |

Nem todo projeto precisa de todos desde o primeiro dia.

A necessidade deve ser proporcional ao sistema.

---

## 22.1 ADR

Uma decisão durável deve registrar, quando aplicável:

- status;
- contexto;
- forças;
- decisão;
- alternativas;
- consequências;
- riscos;
- evidência;
- data de revisão;
- links para issue/PR/ADR substituída.

ADRs de arquitetura pertencem primariamente à etapa de Engenharia/Arquitetura e à evolução posterior do sistema.

---

## 22.2 Documentação para agentes

O repositório deve possuir, quando Codex ou outros agentes forem utilizados, instruções versionadas contendo:

- comandos canônicos;
- convenções;
- limites;
- áreas sensíveis;
- critérios de parada;
- hierarquia documental;
- como executar testes;
- como reportar evidência.

Instruções de módulo não podem contradizer silenciosamente a raiz.

---

# 23. Definition of Ready para engenharia

Uma entrega está **Ready para desenho técnico posterior** quando possui contexto suficiente para ser transformada em arquitetura e backlog técnico.

Dimensões mínimas:

| Dimensão | Precisa estar claro |
| --- | --- |
| Problema | usuário, contexto e resultado |
| Aceite | cenários observáveis e regras |
| UX | fluxo, estados, erros e acessibilidade |
| Dados | entrada, saída, sensibilidade e retenção |
| Risco | segurança, offline, fraude, moderação, parceiro etc. |
| Dependências | contratos e owners conhecidos |
| Operação | impacto esperado, rollback e evidência necessária |

Isso ainda não significa `READY_FOR_CODEX`.

---

# 24. Definition of Done de engenharia

Durante implementação futura, uma mudança só pode ser considerada concluída quando os critérios aplicáveis forem verdadeiros.

Modelo recomendado:

- comportamento aprovado implementado;
- estados previstos preservados;
- código legível e coerente;
- erros explícitos;
- testes proporcionais ao risco;
- testes falham quando a regra é quebrada;
- suite obrigatória verde;
- revisão humana concluída quando exigida;
- segurança e privacidade avaliadas;
- dependências verificadas;
- acessibilidade verificada;
- telemetria minimizada;
- contrato/migração compatíveis;
- flag/rollout/rollback preparados quando necessários;
- documentação atualizada;
- nenhuma incerteza material escondida.

DoD deve ser adaptado por projeto, mas não pode ser reduzido a:

```text
COMPILA
+
TELA ABRE
```

---

# 25. Definition of Done de release

Release não é apenas merge.

Quando aplicável, deve possuir:

- artefato identificado;
- origem rastreável;
- migrations verificadas;
- smoke dos fluxos críticos;
- observabilidade preparada;
- rollback praticável;
- feature flags e audiência definidas;
- condição de parada;
- owners disponíveis;
- pendências conhecidas com risco aceito.

A implementação concreta dessa política pertence à DevOps/Infraestrutura.

---

# 26. Dívida técnica

Dívida aceitável precisa ser consciente.

Modelo:

| Tipo | Tratamento |
| --- | --- |
| Trade-off reversível | issue + owner + risco + condição de remoção |
| Segurança/privacidade/integridade | não aceitar como atalho normal |
| TODO | vínculo com issue quando não puder ser resolvido agora |
| Dependência | atualização contínua e controlada |
| Feature flag | owner + data/condição de remoção |
| Depreciação | comunicar, medir consumidores, migrar e remover |

Dívida não deve existir apenas na memória de quem implementou.

---

# 27. Métricas de engenharia

Métricas servem para melhorar o sistema de entrega.

Não devem ser utilizadas para ranquear pessoas por produção aparente.

Podem ser consideradas, conforme o projeto:

- change lead time;
- deployment frequency;
- recovery time;
- change fail rate;
- rework pós-deploy;
- PR cycle time;
- defects escapados;
- flaky tests;
- dívida de segurança;
- dívida de acessibilidade;
- tempo de revisão;
- tempo de rollback.

Não usar como produtividade individual:

- linhas de código;
- número de commits;
- quantidade de PRs;
- número de prompts;
- tokens;
- percentual de código gerado por IA.

---

# 28. Playbook futuro: da tarefa à produção

Quando a baseline técnica estiver completa e a implementação estiver autorizada, o ciclo recomendado é:

```text
TRIAR
↓
TORNAR READY
↓
FATIAR
↓
MODELAR DECISÃO TÉCNICA QUANDO NECESSÁRIO
↓
CRIAR BRANCH / PREPARAR TESTE
↓
IMPLEMENTAR
↓
EXECUTAR GATES
↓
REVISAR DIFF
↓
ABRIR PR
↓
OBTER CHECKS + REVIEW
↓
MERGE
↓
PROMOVER CONTROLADAMENTE
↓
OBSERVAR
↓
ENCERRAR DÍVIDA TEMPORÁRIA / DOCUMENTAR
```

Este playbook não autoriza a criação antecipada de repositório ou infraestrutura antes das etapas responsáveis.

---

# 29. Relação com Engenharia e Arquitetura

A saída desta etapa entrega à Engenharia e Arquitetura **restrições e qualidades que o sistema precisa suportar**, mas não a solução.

Exemplos:

```text
TÉCNICAS
“operações repetíveis precisam ter comportamento idempotente”

ENGENHARIA / ARQUITETURA
“quais comandos precisam de idempotência,
onde fica a fronteira e qual contrato garante isso?”
```

```text
TÉCNICAS
“regra crítica precisa ser testável isoladamente”

ENGENHARIA / ARQUITETURA
“quais domínios, portas e boundaries permitem isso?”
```

```text
TÉCNICAS
“mudança de contrato precisa suportar compatibilidade progressiva”

ENGENHARIA / ARQUITETURA
“qual estratégia de versionamento e convivência o sistema utilizará?”
```

---

# 30. Relação com a Visão do Tech Lead

A Visão do Tech Lead receberá posteriormente:

- arquitetura aprovada;
- atributos de qualidade;
- riscos;
- requisitos de UX;
- requisitos de dados;
- política de segurança;
- política de testes;
- gates de CI;
- necessidade de compatibilidade;
- requirements de observabilidade;
- limites operacionais.

E decidirá tecnologias concretas capazes de atender esse conjunto.

Exemplo:

```text
A METODOLOGIA NÃO DIZ
“use TypeScript porque é o padrão.”

ELA DIZ
“estados críticos precisam ser explícitos,
contratos precisam ser verificáveis,
o ecossistema precisa suportar os testes
e o sistema precisa permanecer manutenível.”

O TECH LEAD AVALIA
qual linguagem/runtime/framework
satisfaz melhor o conjunto real do projeto.
```

Escolha de tecnologia deve ser consequência da mensuração anterior, não preferência isolada.

---

# 31. Relação com DevOps e Infraestrutura

Esta etapa define requisitos como:

- branch protegida;
- gates obrigatórios;
- privilégio mínimo em automações;
- secrets protegidos;
- build rastreável;
- rollout controlado;
- rollback praticável;
- observabilidade minimizada;
- backups quando necessários;
- operação auditável.

DevOps/Infra definirá:

- plataforma de CI/CD;
- workflows concretos;
- runners;
- ambientes;
- providers;
- deployment strategy;
- secrets manager;
- monitoramento;
- tracing;
- storage operacional;
- rede;
- backup;
- restore;
- disaster recovery;
- sizing;
- custos.

```text
TÉCNICAS
= O CONTROLE PRECISA EXISTIR

DEVOPS / INFRA
= COMO E ONDE O CONTROLE SERÁ IMPLEMENTADO
```

---

# 32. Gates de passagem

A etapa pode ser considerada pronta para Engenharia e Arquitetura quando houver consenso suficiente sobre:

| Gate | Evidência |
| --- | --- |
| DEV-01 Autoridade | responsabilidade humana e limites de IA claros |
| DEV-02 Código | princípios de legibilidade, estado e erro definidos |
| DEV-03 Git | política de integração e revisabilidade definida |
| DEV-04 Review | critérios e severidade de revisão definidos |
| DEV-05 Testes | estratégia por camada e risco definida |
| DEV-06 Quality Gates | tipos de checks obrigatórios definidos |
| DEV-07 Segurança | baseline de secure SDLC e segredos definida |
| DEV-08 Privacidade | classificação e minimização definidas |
| DEV-09 Acessibilidade | implementação verificável prevista |
| DEV-10 Dados | política de contrato, compatibilidade e migração definida |
| DEV-11 Observabilidade | sinais e limites de telemetria definidos |
| DEV-12 Documentação | artefatos vivos e política de ADR definidos |
| DEV-13 DoR/DoD | critérios de entrada e saída de engenharia claros |
| DEV-14 Operação | rollout, rollback e incidentes tratados conceitualmente |
| DEV-15 Métricas | métricas de sistema sem vanity metrics definidas |

Esses gates avaliam **maturidade do método de engenharia**, não existência de stack.

---

# 33. Saída esperada do documento de projeto

O `06_Tecnicas_de_Desenvolvimento.md` de um projeto real deve registrar pelo menos:

1. contrato de responsabilidade humana e IA;
2. princípios de engenharia;
3. política de atuação de agentes;
4. pacote mínimo de contexto;
5. condições de parada;
6. padrões de código e estado;
7. política de erro, concorrência e idempotência;
8. política Git/PR/review;
9. estratégia de testes;
10. política de flaky tests e cobertura;
11. gates de qualidade;
12. baseline de segurança e privacidade;
13. política de dependências e supply chain;
14. acessibilidade na implementação;
15. contratos, compatibilidade e migrações;
16. requisitos semânticos de observabilidade;
17. documentação viva;
18. Definition of Ready;
19. Definition of Done;
20. critérios de release;
21. dívida técnica;
22. métricas de engenharia;
23. playbook de entrega;
24. gates de passagem;
25. pendências que exigem Engenharia, Tech Lead ou DevOps/Infra.

---

# 34. Revisão humana e canonização

O ChatGPT deve primeiro estruturar a política e apresentar as decisões ao humano.

O documento não deve ser canonizado apenas porque uma prática é popular ou apareceu em uma referência externa.

A revisão deve distinguir:

```text
PRINCÍPIO REUTILIZÁVEL
        ↓
POLÍTICA DO PROJETO
        ↓
VALOR NUMÉRICO CALIBRÁVEL
        ↓
FERRAMENTA CONCRETA AINDA NÃO ESCOLHIDA
```

Exemplo:

```text
PRINCÍPIO
PRs precisam ser revisáveis.

POLÍTICA
Projeto define orçamento de tamanho.

VALOR CALIBRÁVEL
400 linhas pode ser ponto inicial, não lei universal.

FERRAMENTA
Bot/check concreto será decidido depois.
```

Somente após revisão humana o artefato passa de discutido para aprovado e canonizado.

---

# 35. Handoff para Engenharia e Arquitetura

A próxima etapa deve consumir integralmente este documento e utilizá-lo como **restrição de qualidade**, não como arquitetura pronta.

O handoff esperado é:

```text
PRODUTO / UX APROVADOS
        ↓
TÉCNICAS DE DESENVOLVIMENTO
        ↓
POLÍTICAS DE QUALIDADE
        ↓
ENGENHARIA E ARQUITETURA
        ↓
MENSURAÇÃO TÉCNICA
BOUNDARIES
ATRIBUTOS DE QUALIDADE
DADOS
CONTRATOS
ARQUITETURA
        ↓
VISÃO DO TECH LEAD
        ↓
ESCOLHA DE TECNOLOGIAS
        ↓
DEVOPS / INFRA
```

A etapa seguinte não deve perguntar primeiro:

```text
“Qual framework vamos usar?”
```

Ela deve perguntar:

```text
“Quais forças técnicas este produto cria,
quais propriedades o sistema precisa possuir
e qual arquitetura responde melhor a essas forças?”
```

Esse é o contrato de passagem desta etapa.

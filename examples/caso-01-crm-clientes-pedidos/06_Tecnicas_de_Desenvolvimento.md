---
document_id: CASE-01-DOC-06
title: Técnicas de Desenvolvimento — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
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

# Técnicas de Desenvolvimento — CRM para gestão de clientes e pedidos

## 1. Propósito

Este documento define **como o CRM do Caso 01 deverá ser desenvolvido, revisado, testado, documentado e mantido com qualidade**, sem escolher ainda linguagem, runtime, framework, banco, cloud, ferramenta de CI/CD ou arquitetura concreta.

A pergunta central desta etapa é:

> **Quais políticas, práticas, gates e critérios de qualidade devem governar o trabalho de engenharia — humano ou assistido por IA — para preservar corretamente os contratos de produto, UX, integração com o Protheus, privacidade, autorização, auditabilidade e reversibilidade?**

A política central do projeto é:

> **Uma mudança só é considerada boa quando preserva o comportamento aprovado, possui prova proporcional ao risco, pode ser revisada por uma pessoa e não aumenta silenciosamente o risco de integração com o Protheus ou de perda, duplicação ou exposição de dados comerciais.**

Esta etapa define **como trabalhar com qualidade**.

Ela não define ainda **como o sistema será estruturado** nem **com quais tecnologias será implementado**.

```text
TÉCNICAS DE DESENVOLVIMENTO
= como desenvolver com qualidade

ENGENHARIA E ARQUITETURA
= o que tecnicamente precisa ser verdade
  e como o sistema será estruturado

TECH LEAD
= com quais tecnologias concretas

DEVOPS / INFRA
= como construir, promover, executar e operar
```

A existência deste documento **não autoriza implementação pelo Codex**.

---

## 2. Base consumida

Esta baseline consome integralmente:

- `00_Discovery.md`;
- `01_Pesquisa_e_Viabilidade.md`;
- `02_Briefing_de_Produto_e_Escopo.md`;
- `03_Visao_de_Product_Owner.md`;
- `Principios_de_UX_UI.md`;
- `04_Direcao_de_UI_e_Design_System.md`;
- `05_Especificacao_de_UX.md`.

Contratos especialmente relevantes para engenharia:

- o Protheus permanece autoridade para dados e operações ERP definidos como canônicos;
- o CRM não pode se tornar uma segunda operação paralela ao ERP;
- vendedor não pode receber acesso irrestrito ao histórico de outra carteira;
- informação financeira é proporcional ao papel;
- histórico comercial corporativo precisa sobreviver à saída ou transferência de vendedor;
- ações materiais precisam preservar autoria e momento;
- estados do Protheus precisam distinguir atual, atualizando, potencialmente desatualizado e indisponível quando isso afeta decisão;
- double tap, retry ou reconexão não podem produzir efeitos duplicados em ações materiais;
- falhas recuperáveis não devem apagar trabalho válido;
- telemetria não deve transportar texto livre comercial, dados financeiros completos, segredos ou payload bruto do Protheus sem finalidade e autorização específicas;
- acessibilidade crítica é requisito funcional;
- build custom permanece condicionado ao business case e à reversibilidade da decisão.

---

## 3. Princípio dominante

> **Velocidade de produção de código não é velocidade de produto.**

O projeto otimiza o caminho:

```text
DECISÃO CORRETA
↓
MUDANÇA PEQUENA
↓
PROVA CONFIÁVEL
↓
REVISÃO COMPREENSÍVEL
↓
PROMOÇÃO CONTROLADA
↓
RECUPERAÇÃO PRATICÁVEL
```

Código produzido rapidamente que aumenta incerteza, blast radius ou custo de recuperação não representa ganho real de velocidade.

---

## 4. Responsabilidade humana e IA

O contrato de autoridade do projeto é:

```text
IA PROPÕE
AUTOMAÇÃO VERIFICA
HUMANO RESPONDE
```

Agentes de IA podem, quando autorizados:

- investigar;
- ler documentação;
- mapear o repositório;
- propor plano;
- alterar arquivos dentro do escopo;
- criar testes;
- executar verificações;
- revisar o próprio diff;
- atualizar documentação necessária.

Responsabilidade técnica, aceite de risco, aprovação de regra e decisão de merge pertencem a pessoas identificáveis.

Código gerado por IA entra como **contribuição ainda não verificada**.

Ele não recebe desconto de rigor por ter sido produzido por agente.

---

## 5. Classes de mudança

### 5.1. NORMAL

Exemplos:

- componente visual simples sem mudança de regra;
- ajuste de microcopy já aprovado;
- refactor local;
- documentação;
- teste adicional;
- mudança mecânica sem alteração de contrato.

Tratamento:

```text
gates normais
+
review normal
```

### 5.2. SENSÍVEL

Exemplos:

- autenticação;
- autorização;
- carteira e permissões;
- integração com Protheus;
- criação ou alteração de cliente formal;
- pedido;
- informação financeira;
- migração ou importação de dados;
- sincronização;
- histórico e auditoria;
- telemetria que toca dados comerciais;
- mudanças em CI ou controles de segurança.

Tratamento:

```text
owner apropriado
+
análise de risco
+
prova mais forte
+
rollback explícito
```

### 5.3. PROIBIDA SEM AUTORIZAÇÃO HUMANA EXPLÍCITA

- utilizar dados reais de produção em prompt, fixture ou teste local;
- obter ou expor segredo não autorizado;
- alterar produção;
- desativar autorização;
- bypassar regras canônicas do Protheus;
- executar migração destrutiva;
- remover controle de segurança;
- escolher ou substituir stack antes da etapa responsável;
- criar nova fronteira arquitetural sem decisão aprovada;
- autoaprovar mudança sensível;
- expandir escopo material durante execução.

---

## 6. Pacote mínimo de contexto para qualquer agente

Toda tarefa técnica futura relevante deverá informar, diretamente ou por links canônicos:

| Campo | Conteúdo esperado |
| --- | --- |
| Objetivo | problema e resultado observável |
| Escopo | módulos, comportamentos ou superfícies que podem mudar |
| Fora de escopo | o que não pode ser alterado |
| Fontes | documentos, IDs de produto, UX e decisões técnicas aplicáveis |
| Invariantes | o que nunca pode acontecer |
| Estados | estados que precisam continuar válidos |
| Dados | classificação e sensibilidade |
| Risco | autorização, Protheus, concorrência, migração, a11y etc. |
| Verificação | testes e evidências necessárias |
| Rollback | como desativar ou reverter |
| Parada | quando pedir decisão humana |

Prompt sem esse contexto não substitui o pacote.

Exemplo insuficiente:

```text
“Faça integração com pedidos do Protheus.”
```

---

## 7. Stop conditions específicas do Caso 01

O agente deve parar e pedir decisão quando precisar:

- inventar campo, regra, endpoint ou comportamento do Protheus;
- assumir release, API ou contrato não confirmados;
- reinterpretar sozinho uma customização ERP;
- decidir quem pode ver dado financeiro;
- decidir nova regra de carteira;
- escolher mecanismo de sincronização ainda não aprovado;
- usar credencial não autorizada;
- usar dump real de dados do cliente;
- contornar regra canônica do ERP por acesso direto a dados;
- modificar contrato sem estratégia de compatibilidade;
- corrigir bug sem reprodução ou evidência suficiente;
- criar boundary ou serviço novo sem decisão arquitetural;
- escolher framework, banco, provider ou ferramenta concreta antes do Tech Lead/DevOps;
- expandir materialmente o escopo da issue;
- executar operação destrutiva sem recuperação aprovada.

---

## 8. Princípios de código do projeto

### DEV-P1 — Intenção antes de mecanismo

Código deve revelar regra e responsabilidade.

### DEV-P2 — Correto antes de otimizado

```text
CORRETO
↓
SIMPLES
↓
MENSURÁVEL
↓
OTIMIZADO QUANDO HOUVER EVIDÊNCIA
```

### DEV-P3 — Estado explícito

Estados materialmente diferentes não devem ser comprimidos em booleanos vagos.

Exemplo derivado da UX:

```text
ERP_AVAILABLE
ERP_REFRESHING
ERP_STALE
ERP_UNAVAILABLE
```

Quando o comportamento exigir, um registro em edição também pode precisar de estados equivalentes a:

```text
DRAFT
SAVING
SAVED
FAILED_RECOVERABLE
```

A arquitetura posterior decidirá sua modelagem concreta.

### DEV-P4 — Regra crítica não mora só na UI

Autorização de carteira, acesso financeiro, transferência, vínculo com Protheus e preservação de histórico não podem depender apenas de ocultação de componente ou navegação.

### DEV-P5 — Efeitos controláveis

Tempo, rede, storage, IDs, integrações e outras dependências que alteram comportamento relevante precisam ser controláveis em testes.

### DEV-P6 — Falha é caminho normal

Timeout, indisponibilidade, retry, repetição, resposta parcial, revogação e concorrência devem possuir comportamento previsto quando aplicáveis.

### DEV-P7 — Privacidade por construção

Transportar, retornar, logar e reter apenas o necessário.

### DEV-P8 — Compatibilidade progressiva

Mudanças de contrato e dados precisam permitir convivência e recuperação quando houver consumidores ativos.

### DEV-P9 — Observável sem vazar

Diagnóstico não autoriza copiar conteúdo comercial sensível para telemetria comum.

### DEV-P10 — Reversibilidade por padrão

Mudanças pequenas, compatíveis e desligáveis reduzem custo de erro.

---

## 9. Atalhos proibidos

São proibidos como prática normal:

- comentar teste para obter pipeline verde;
- ignorar lint, validação ou segurança para liberar merge;
- capturar exceção e continuar como sucesso;
- esconder falha apenas em log;
- usar `null`, `false` ou equivalente quando o domínio exige estado explícito;
- duplicar regra crítica em vários clientes sem contrato;
- adicionar dependência sem avaliação;
- usar dados reais em prompt, fixture ou screenshot de teste;
- remover compatibilidade no mesmo passo destrutivo em que migração ocorre;
- aceitar código que ninguém consegue explicar apenas porque compila;
- tratar happy path como Definition of Done;
- aumentar autonomia do agente removendo controles.

---

## 10. Nomes, funções e módulos

Nomes devem usar o vocabulário do domínio:

```text
cliente
prospect
carteira
responsável
interação
próxima ação
pedido
contexto ERP
transferência
```

Evitar nomes genéricos quando existe conceito mais preciso.

Unidades de código devem:

- ter responsabilidade reconhecível;
- operar em nível de abstração coerente;
- limitar efeitos;
- expor caminho de erro;
- ser testáveis proporcionalmente ao risco;
- não concentrar responsabilidades desconexas.

A divisão física definitiva será definida por Arquitetura e Tech Lead.

---

## 11. Erros

Erros relevantes precisam separar conceitualmente:

```text
CÓDIGO ESTÁVEL
+
CONTEXTO SEGURO
+
CAUSA TÉCNICA
+
MENSAGEM PARA USUÁRIO
```

Uma indisponibilidade do Protheus pode existir internamente como categoria estável equivalente a:

```text
ERP_UNAVAILABLE
```

Enquanto o usuário recebe mensagem compatível com a UX, por exemplo:

> Não foi possível confirmar os dados do Protheus agora.

Exceção interna não deve vazar diretamente para a interface.

---

## 12. Tempo

Próxima ação depende de data, hora, timezone, atraso, hoje e vencimento.

Portanto:

```text
TEMPO RELEVANTE
→ dependência controlável
→ testável
→ timezone explícito quando necessário
```

Testes não devem depender do relógio real quando isso altera regra.

---

## 13. Idempotência

A UX já identificou situações em que repetição da intenção não pode duplicar efeito.

### DEV-IDEMP-01 — Registrar interação

Double tap, retry ou reconexão não podem gerar duas interações para a mesma intenção.

### DEV-IDEMP-02 — Criar prospect

Retry da mesma operação não pode criar duplicidade por acidente.

### DEV-IDEMP-03 — Transferir carteira

Retry não pode produzir transferências repetidas ou histórico inconsistente.

### DEV-IDEMP-04 — Escritas futuras no Protheus

Se o CRM futuramente criar cliente ou pedido no ERP, repetição da intenção não pode produzir duplicidade transacional.

A etapa 07 decidirá onde essas garantias pertencem estruturalmente.

---

## 14. Concorrência

Cenário material identificado:

```text
Gerente A transfere cliente para Maria
+
Gerente B transfere o mesmo cliente para João
```

`last-write-wins` não pode surgir acidentalmente como regra de negócio.

Quando concorrência material existir, o desenho técnico deverá explicitar:

- o que é conflito;
- se merge é possível;
- quando operação deve falhar;
- quando usuário precisa revisar;
- como autoria e auditoria permanecem íntegros.

---

## 15. Git e branch principal

Quando o repositório de implementação existir, a branch principal deverá ser tratada como potencialmente promovível.

Política esperada:

- sem push direto quando a plataforma permitir proteção;
- sem force push;
- checks obrigatórios;
- revisão humana proporcional ao risco;
- último SHA revisado antes do merge;
- conversas bloqueantes resolvidas.

Branches de trabalho devem ser curtas, específicas e de vida curta.

Convenção concreta de nomes será definida posteriormente.

---

## 16. Commits

Commit deve ser:

- coerente;
- compreensível;
- pequeno o suficiente para revisão;
- reversível quando possível;
- sem misturar formatação massiva com mudança funcional não relacionada.

Mudança de contrato Protheus, refactor amplo e mudança visual não devem ser agrupados por conveniência.

---

## 17. Pull Requests

Todo PR material deverá registrar:

- problema e resultado;
- origem canônica;
- o que mudou;
- o que não mudou;
- riscos;
- como testar;
- evidências;
- compatibilidade e migração quando aplicável;
- rollout e rollback quando aplicável;
- uso de IA;
- documentação alterada;
- pendências e incertezas.

O projeto deverá adotar um orçamento de tamanho/revisabilidade, mas não fixa nesta etapa um limite universal em linhas.

Tamanho é sinal de revisabilidade, não mérito.

---

## 18. Revisão em duas passagens

### 18.1. Passagem 1 — intenção

Antes da revisão linha a linha:

```text
A mudança pertence ao problema?
Respeita documentos canônicos?
Altera regra que não deveria?
Está na responsabilidade correta?
O blast radius é proporcional?
```

Se falhar nessa etapa, a revisão de implementação pode ser interrompida.

### 18.2. Passagem 2 — implementação

Avaliar:

- correção;
- legibilidade;
- estados;
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

## 19. Severidade de review

Taxonomia inicial:

| Classe | Significado |
| --- | --- |
| BLOCKER | correção, segurança, perda de dados, exposição ou contrato violado |
| MAJOR | manutenção, teste, a11y, observabilidade ou risco relevante |
| MINOR | clareza/localidade de baixo risco |
| NIT | preferência não automatizada |
| QUESTION | falta de contexto ou hipótese do revisor |

Exemplos `BLOCKER` do caso:

- vendedor acessa histórico completo de outra carteira;
- retry cria segundo cliente/pedido no Protheus;
- falha do ERP é apresentada como sucesso;
- migração perde histórico corporativo.

---

## 20. Estratégia de testes

A stack concreta será escolhida pelo Tech Lead.

A política define o que precisa ser provado.

### 20.1. Unidade / domínio

Cobrir principalmente:

- regras de carteira;
- visibilidade;
- transferência;
- próxima ação;
- vencimento;
- prospect versus cliente formal;
- autorização;
- estados explícitos;
- invariantes de domínio.

### 20.2. Componente / UI

Cobrir:

- loading;
- erro;
- dado potencialmente desatualizado;
- ERP indisponível;
- foco;
- teclado;
- permissão;
- campos;
- estados de ação.

### 20.3. Contrato

Especialmente importante para integração Protheus:

- schema;
- campos;
- códigos de erro;
- compatibilidade;
- semântica de status;
- mudanças de versão.

### 20.4. Integração

Provar interação entre componentes reais controlados e, posteriormente, sandbox/ambientes compatíveis.

### 20.5. E2E smoke

Fluxo mínimo:

```text
prioridade
→ cliente
→ registrar interação
→ próxima ação
```

### 20.6. E2E ampliado

Conforme risco:

- indisponibilidade do Protheus;
- retry;
- autorização;
- transferência concorrente;
- recuperação de rascunho;
- integração externa.

---

## 21. Bugs e regressões

Bug reproduzível deve, sempre que praticável, produzir prova que falha antes da correção.

Fluxo:

```text
REPRODUZIR
↓
PROVA FALHA
↓
CORRIGIR
↓
PROVA VERDE
```

Correção especulativa sem reprodução deve ser exceção explicitamente justificada.

---

## 22. Flaky tests

```text
FLAKY
≠
PASSOU NA SEGUNDA TENTATIVA
```

Teste instável precisa de:

- owner;
- issue;
- diagnóstico;
- prazo de resolução;
- quarentena apenas se deliberadamente aprovada;
- falha ainda visível.

Reexecutar até verde não é evidência.

---

## 23. Cobertura

Não existe percentual universal nesta etapa.

A futura baseline técnica deverá calibrar:

- cobertura mínima útil;
- política para código alterado;
- invariantes que exigem cenários completos;
- exclusões;
- código gerado;
- UI e integração.

É proibido criar teste sem asserção útil apenas para atingir percentual.

---

## 24. Quality gates conceituais

### Pull Request

Conforme stack e risco:

```text
formatter
lint
tipos/validação equivalente
testes
build
secret scan
análise de dependências
SAST
a11y automatizável
smoke
```

### Main

Além dos checks compatíveis:

- prova de integração;
- geração de artefato promovível.

### Periódicos

- E2E ampliado;
- segurança;
- dependências;
- resiliência;
- compatibilidade.

### Release

- smoke crítico;
- migração/compatibilidade;
- rollback;
- evidência do artefato.

A ferramenta concreta de CI/CD será definida posteriormente.

---

## 25. Regras de gate

- check ignorado não conta como prova se o risco foi afetado;
- flaky continua falha até diagnóstico;
- automação opera com privilégio mínimo;
- segredo não aparece em log;
- artefato promovido deve ser o testado quando a arquitetura de entrega permitir;
- bypass emergencial exige owner, auditoria e recomposição posterior.

---

## 26. Secure SDLC

Segurança integra o ciclo de desenvolvimento.

Threat model deverá ser considerado especialmente quando forem desenhados ou alterados:

- autenticação;
- autorização;
- carteira;
- integração Protheus;
- importação;
- administração;
- sincronização;
- nova fronteira de confiança;
- dado pessoal ou financeiro.

Referências concretas e versões vigentes serão selecionadas/revalidadas nas etapas adequadas.

---

## 27. Segredos

Segredo:

- não entra em código;
- não entra em prompt;
- não entra em fixture;
- não entra em screenshot;
- não entra em log;
- deve ser rotacionável;
- deve seguir menor privilégio.

Ferramenta concreta de gestão de segredos pertence a DevOps/Infra.

---

## 28. Classificação inicial de dados

Esta classificação é arquiteturalmente relevante, mas ainda deverá ser refinada com o desenho de dados e obrigações legais.

| Classe | Exemplos do Caso 01 |
| --- | --- |
| Público | nenhum dado comercial interno é presumido público |
| Interno | catálogos operacionais não sensíveis, quando aplicável |
| Confidencial | clientes, contatos, carteira, histórico comercial |
| Restrito | segredos, tokens, credenciais, certas informações financeiras, dados pessoais de maior risco |

Regra:

```text
DADO REAL
≠
PROMPT
≠
FIXTURE
≠
SCREENSHOT DE TESTE
```

sem sanitização e autorização adequadas.

---

## 29. Dependências e supply chain

Toda dependência futura deverá ser avaliada quanto a:

- necessidade;
- origem;
- manutenção;
- licença;
- vulnerabilidades;
- custo de atualização;
- lock-in;
- capacidade de teste;
- impacto de runtime/tamanho quando material.

A escolha concreta pertence ao Tech Lead.

A política de supply chain deverá considerar, conforme stack:

- manifesto e lockfile;
- resolução reproduzível;
- revisão de dependências;
- secret scanning;
- SAST;
- proveniência/SBOM quando aplicável;
- permissões mínimas de automação.

---

## 30. Acessibilidade na implementação

O que UI e UX definiram precisa virar prova executável ou revisão adequada.

| Requisito | Evidência futura |
| --- | --- |
| foco | teste de teclado/integração |
| estado não só por cor | componente + revisão |
| labels | teste semântico |
| erro associado ao campo | componente + a11y |
| retorno de foco de dialog | integração |
| texto ampliado | teste visual/manual |
| leitor de tela | avaliação proporcional ao risco |

Correção crítica de acessibilidade é defeito funcional.

---

## 31. Contratos e compatibilidade

Contratos relevantes deverão ser:

- versionados quando necessário;
- validados;
- documentados;
- testados em producer/consumer quando aplicável;
- compatíveis durante janela necessária;
- acompanhados de erros estáveis;
- minimalistas em dados.

A forma concreta do contrato será definida em Engenharia/Arquitetura.

Política de evolução:

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

---

## 32. Migrações de dados

Mudanças materiais deverão considerar:

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

Migração precisa ser observável, testável, recuperável e, quando repetição for possível, idempotente.

Para a base inicial de aproximadamente 12 mil clientes e controles legados, a política é:

```text
VALIDAR AMOSTRA
↓
EXECUTAR EM CONJUNTO CONTROLADO
↓
MEDIR RESULTADO
↓
MIGRAR POR LOTES
↓
VERIFICAR
```

Nunca importar toda a base e somente depois descobrir se a semântica estava correta.

---

## 33. Observabilidade — contrato de qualidade

A política diferencia:

| Sinal | Função |
| --- | --- |
| Log estruturado | explicar evento técnico pontual |
| Métrica | medir taxa, erro, latência, fila ou guardrail |
| Trace | correlacionar caminho distribuído quando necessário |
| Audit log | registrar ação privilegiada/material |
| Evento de produto | representar resultado de jornada |

Ações como transferência de carteira, alteração administrativa ou mudança de permissão podem exigir audit log.

Eventos de produto permanecem separados da auditoria.

---

## 34. Minimização de telemetria

É proibido serializar indiscriminadamente:

- request body;
- headers de autenticação;
- token;
- objeto completo de cliente;
- notas;
- texto livre de interação;
- dados financeiros completos;
- payload bruto do Protheus.

Telemetria deverá usar allowlist quando o risco justificar.

---

## 35. Incidentes

O processo futuro deverá prever:

1. detecção;
2. severidade;
3. owner;
4. contenção;
5. preservação de evidência;
6. comunicação factual;
7. recuperação do fluxo do usuário;
8. postmortem sem culpa;
9. ações com owner e prazo;
10. teste ou controle contra recorrência.

A infraestrutura concreta virá depois.

---

## 36. Documentação viva

O projeto deverá manter proporcionalmente:

- README;
- instruções de colaboração;
- política de segurança;
- documentação de contratos;
- ADRs;
- runbooks;
- changelog/release notes quando necessário;
- instruções versionadas para agentes.

Se Codex puder atuar no repositório, instruções de execução, comandos, limites, áreas sensíveis e stop conditions precisam estar versionadas.

---

## 37. Definition of Ready de engenharia

Uma entrega está pronta para desenho técnico posterior quando possuir contexto suficiente sobre:

| Dimensão | Precisa estar claro |
| --- | --- |
| Problema | usuário, contexto e resultado |
| Aceite | cenários observáveis e regras |
| UX | fluxo, estados, erros e acessibilidade |
| Dados | entrada, saída, sensibilidade e retenção |
| Risco | segurança, autorização, Protheus, concorrência etc. |
| Dependências | contratos e owners conhecidos |
| Operação | impacto, rollback e evidência necessária |

Isso ainda **não significa `READY_FOR_CODEX`**.

---

## 38. Definition of Done de engenharia

Uma mudança futura somente poderá ser considerada concluída quando, conforme aplicável:

- comportamento aprovado estiver implementado;
- estados previstos estiverem preservados;
- código estiver legível e coerente;
- erros estiverem explícitos;
- testes forem proporcionais ao risco;
- a suíte obrigatória estiver verde;
- revisão humana estiver concluída quando exigida;
- segurança e privacidade forem avaliadas;
- dependências forem verificadas;
- acessibilidade for verificada;
- telemetria estiver minimizada;
- contrato/migração forem compatíveis;
- rollout/rollback estiverem preparados quando necessários;
- documentação estiver atualizada;
- nenhuma incerteza material estiver escondida.

Não é aceitável:

```text
COMPILA
+
TELA ABRE
=
DONE
```

---

## 39. Definition of Done de release

Release não é sinônimo de merge.

Quando aplicável, exige:

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

A implementação concreta pertence a DevOps/Infra.

---

## 40. Dívida técnica

Dívida aceitável precisa ser consciente e rastreada.

| Tipo | Tratamento |
| --- | --- |
| Trade-off reversível | issue + owner + risco + condição de remoção |
| Segurança/privacidade/integridade | não aceitar como atalho normal |
| TODO | vínculo com issue quando não resolvido agora |
| Dependência | atualização controlada |
| Feature flag | owner + propósito + condição de retirada |
| Depreciação | comunicar, medir, migrar e remover |

Dívida não deve existir apenas na memória de quem implementou.

---

## 41. Métricas de engenharia

Podem ser utilizadas para melhorar o sistema de entrega:

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

Não utilizar como produtividade individual:

- linhas de código;
- quantidade de commits;
- quantidade de PRs;
- tokens;
- prompts;
- percentual de código gerado por IA.

---

## 42. Playbook futuro de entrega

Quando todas as etapas posteriores autorizarem execução:

```text
ISSUE CANÔNICA
↓
READY
↓
FATIAR
↓
MAPEAR RISCO
↓
MODELAR DECISÃO TÉCNICA QUANDO NECESSÁRIO
↓
BRANCH
↓
IMPLEMENTAR MENOR FATIA
↓
EXECUTAR GATES
↓
REVISAR DIFF
↓
PR
↓
CHECKS + REVIEW HUMANO
↓
MERGE
↓
PROMOÇÃO CONTROLADA
↓
OBSERVAR
↓
RECONCILIAR / ENCERRAR
```

Este playbook não autoriza a criação antecipada do produto.

---

## 43. Regras específicas derivadas da revisão do cenário

### DEV-CRM-01 — Não bypassar autoridade do Protheus

Integração não pode contornar regra canônica do ERP apenas por ser tecnicamente mais simples.

### DEV-CRM-02 — Autorização é classe sensível

Qualquer mudança capaz de expor carteira, observação ou dado financeiro recebe revisão proporcional ao risco.

### DEV-CRM-03 — Protheus não pode ser única prova manual

Testes de integração não podem depender exclusivamente de produção ou de conferência manual no ERP.

### DEV-CRM-04 — Reversibilidade preserva o business case

Mudanças precisam ser pequenas e controláveis o suficiente para que aumento de risco, custo ou baixa adoção não force continuidade por custo afundado.

---

## 44. Gates da etapa

| Gate | Evidência esperada |
| --- | --- |
| DEV-01 Autoridade | responsabilidade humana e limites de IA claros |
| DEV-02 Código | estado, erro, legibilidade e domínio possuem política |
| DEV-03 Git | lotes pequenos e branch principal protegível |
| DEV-04 Review | revisão por intenção e implementação |
| DEV-05 Testes | estratégia por camada e risco definida |
| DEV-06 Quality Gates | tipos de checks obrigatórios definidos |
| DEV-07 Segurança | mudanças sensíveis e threat model previstos |
| DEV-08 Privacidade | classificação e minimização definidas |
| DEV-09 Acessibilidade | prova incorporada ao desenvolvimento |
| DEV-10 Contratos | compatibilidade, Protheus e migrações tratados |
| DEV-11 Observabilidade | sinais necessários sem vazamento definidos |
| DEV-12 Documentação | documentação viva e instruções para agentes previstas |
| DEV-13 DoR/DoD | critérios de entrada e saída claros |
| DEV-14 Operação | rollout, rollback e incidentes tratados conceitualmente |
| DEV-15 Métricas | métricas de sistema sem vanity metrics |

---

## 45. Handoff para Engenharia e Arquitetura

A próxima etapa recebe desta baseline:

```text
PRODUTO E UX APROVADOS
+
POLÍTICA DE ESTADO E ERRO
+
POLÍTICA DE IDPOTÊNCIA E CONCORRÊNCIA
+
SEGURANÇA / PRIVACIDADE
+
TESTES E QUALITY GATES
+
CONTRATOS E COMPATIBILIDADE
+
OBSERVABILIDADE
+
REVERSIBILIDADE
+
DOR / DOD
+
STOP CONDITIONS
```

Engenharia e Arquitetura deverá responder:

> **Quais propriedades técnicas, boundaries, contratos, autoridades de dados e decisões estruturais materializam essas necessidades sem escolher prematuramente a stack?**

---

## 46. Validação da metodologia no Caso 01

A etapa preservou corretamente sua fronteira.

Exemplo:

```text
UX
“double tap não pode duplicar interação”
↓
TÉCNICAS
“ações repetíveis exigem prova contra efeito duplicado”
↓
ENGENHARIA / ARQUITETURA
posteriormente decidirá onde e como a idempotência é garantida
```

Outro exemplo:

```text
UX
“falha de rede não deve apagar trabalho válido”
↓
TÉCNICAS
“falha é caminho normal e recuperação precisa ser testada”
↓
ENGENHARIA / ARQUITETURA
definirá propriedades técnicas necessárias
```

Resultado da validação:

```text
DEV_METHOD_VALIDATION: PASS

STACK_SELECTED: NO
ARCHITECTURE_SELECTED: NO
CLOUD_SELECTED: NO
TEST_TOOL_SELECTED: NO
CI_VENDOR_SELECTED: NO

AI_POLICY: DEFINED
STOP_CONDITIONS: DEFINED
CODE_POLICY: DEFINED
IDEMPOTENCY_POLICY: DEFINED
GIT_REVIEW_POLICY: DEFINED
TEST_STRATEGY: DEFINED
SECURITY_BASELINE: DEFINED
DATA_POLICY: DEFINED
A11Y_POLICY: DEFINED
OBSERVABILITY_POLICY: DEFINED
DOR_DOD: DEFINED
DEV_GATES: DEFINED

DEV_READINESS: SUFFICIENT_FOR_ENGINEERING_AND_ARCHITECTURE
READY_FOR_CODEX: NO
```

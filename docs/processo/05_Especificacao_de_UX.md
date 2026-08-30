---
document_id: PROCESS-05-ESPECIFICACAO-UX
title: Especificação de UX
status: draft-methodology
version: 0.1.0
stage: especificacao-ux
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
  - Principios_de_UX_UI.md
  - 04_Direcao_de_UI_e_Design_System.md
produces: 05_Especificacao_de_UX.md
next_stage: 06_Tecnicas_de_Desenvolvimento.md
---

# 05 — Especificação de UX

## 1. Propósito

A **Especificação de UX** é a etapa responsável por transformar o produto aprovado, as regras de negócio, os princípios de experiência e a direção visual em **jornadas, fluxos, estados, transições, validações, recuperação, conteúdo operacional e critérios de usabilidade verificáveis**.

A pergunta central desta etapa é:

> **Como uma pessoa chega ao resultado esperado, quais decisões precisa tomar ao longo do caminho, o que acontece em cada estado e como ela se recupera quando algo não ocorre como esperado?**

A Direção de UI define como o produto se expressa visualmente.

A Especificação de UX define **como o produto se comporta ponta a ponta**.

Sua saída deve permitir que as etapas técnicas posteriores compreendam quais propriedades precisam ser preservadas sem precisar inventar comportamento de usuário durante a implementação.

Esta etapa ainda **não autoriza código**.

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
05_ESPECIFICACAO_DE_UX
        ↓
06_Tecnicas_de_Desenvolvimento.md
        ↓
CAMADAS TÉCNICAS POSTERIORES
```

A Visão de Product Owner define **o resultado, a prioridade, as regras de negócio e os critérios funcionais**.

Os Princípios de UX/UI definem **como decisões de experiência devem ser julgadas**.

A Direção de UI define **identidade, hierarquia visual, tokens, componentes e anatomia das superfícies**.

A Especificação de UX define **a experiência operacional completa**.

As etapas posteriores devem decidir como implementar essa experiência sem redefini-la silenciosamente.

---

## 3. Origem desta etapa

Esta etapa foi formalizada a partir da documentação real utilizada no DayGym.

No processo original, a Especificação de UX foi tratada como uma fonte vinculante para prototipação, conteúdo, engenharia, analytics e QA. Ela detalhava jornadas ponta a ponta, estados offline, recuperação, validações, permissões, conteúdo, instrumentação e critérios de usabilidade.

O material mostrou uma distinção especialmente útil:

```text
JORNADA
→ por que e em que contexto a pessoa entra?

FLUXO
→ quais decisões e transições levam ao resultado?

ESTADO
→ o que acontece quando algo está vazio, lento, offline,
  conflitante, revogado ou indisponível?

CONTEÚDO
→ como explicar ação, consequência, incerteza e recuperação?

EVIDÊNCIA
→ como saberemos se a experiência funcionou?
```

Essa estrutura passa a ser um princípio da metodologia.

Ao mesmo tempo, a metodologia refinada separa requisitos de experiência de decisões técnicas que no documento original apareciam misturadas.

A UX pode exigir, por exemplo:

```text
“confirmar a ação no dispositivo sem esperar a rede”
“não duplicar o efeito quando a pessoa toca novamente”
“permitir comparar versões em caso de conflito”
“retomar um fluxo interrompido sem perder dados válidos”
```

Mas não deve decidir prematuramente:

```text
qual banco local usar
qual fila usar
qual estratégia de cache
qual algoritmo de merge
qual SDK de integridade
qual framework de navegação
qual biblioteca de analytics
```

Essas escolhas pertencem às camadas técnicas posteriores.

---

## 4. Pré-requisitos obrigatórios

Antes de iniciar esta etapa, o ChatGPT deve consumir integralmente:

1. `00_Discovery.md`;
2. `01_Pesquisa_e_Viabilidade.md`;
3. `02_Briefing_de_Produto_e_Escopo.md`;
4. `03_Visao_de_Product_Owner.md`;
5. `Principios_de_UX_UI.md`;
6. `04_Direcao_de_UI_e_Design_System.md`.

Também deve analisar, quando existirem:

- fluxos já utilizados no produto;
- protótipos;
- telas implementadas;
- tickets de suporte;
- gravações de uso;
- reclamações ou feedbacks;
- restrições operacionais conhecidas;
- integrações externas relevantes;
- políticas, normas ou requisitos legais que afetem interação;
- jornadas reais executadas fora do software;
- processos manuais, planilhas, mensagens e workarounds usados pelos usuários.

A UX não deve assumir que a interface nova começa do zero quando já existe comportamento operacional validado.

---

## 5. Contrato de experiência

Todo projeto deve possuir um **Contrato de Experiência** curto e verificável.

Ele resume o que a experiência precisa garantir de forma transversal.

Estrutura recomendada:

```text
O produto deve levar <usuário/contexto>
a <resultado principal>,
permitindo <ação crítica>,
mesmo quando <condição adversa relevante>,
e sempre deixando claro <autoria / estado / consequência / próximo passo>.
```

O contrato não substitui jornadas.

Ele serve como teste de coerência para elas.

Se uma jornada contradiz o Contrato de Experiência, a divergência deve ser reconciliada.

---

## 6. O que esta etapa pode canonizar

A Especificação de UX pode canonizar:

- arquitetura da experiência no nível do usuário;
- jornadas ponta a ponta;
- entradas e saídas de jornada;
- fluxos e transições;
- estados operacionais visíveis;
- comportamento de navegação e retorno;
- retomada de tarefas interrompidas;
- critérios de confirmação;
- validações no nível da experiência;
- recuperação de erro;
- política de rascunho;
- comportamento em conectividade instável;
- comportamento esperado quando dependência externa falha;
- interação com permissões;
- consentimento no nível da experiência;
- privacidade visível;
- conflitos e comparação no nível da experiência;
- microcopy operacional;
- conteúdo de erro e recuperação;
- acessibilidade da jornada;
- instrumentação semântica necessária para avaliar a experiência;
- tarefas de pesquisa e teste;
- metas de usabilidade;
- gates de UX;
- Definition of Ready para entrada nas etapas técnicas.

---

## 7. O que esta etapa não deve canonizar

A Especificação de UX não deve escolher silenciosamente:

- linguagem de programação;
- runtime;
- framework;
- biblioteca de estado;
- biblioteca de navegação;
- banco de dados;
- banco local;
- estratégia concreta de cache;
- mecanismo concreto de fila;
- algoritmo de sincronização;
- topologia de serviços;
- contrato físico de API;
- schema físico de dados;
- provider;
- ferramenta de analytics;
- ferramenta de observabilidade;
- SDK de autenticação;
- SDK de antifraude;
- estrutura de pastas;
- CI/CD;
- infraestrutura;
- estratégia de deploy.

Também não deve redefinir:

- público;
- promessa;
- prioridade de produto;
- P0/P1/P2;
- regra de negócio aprovada;
- decisão de receita;
- identidade visual;
- tokens;
- sistema tipográfico;
- anatomia visual aprovada sem motivo registrado.

---

## 8. Princípio estrutural: comportamento antes da implementação

A UX deve especificar **o que precisa acontecer para a pessoa**, não como o sistema será internamente construído.

Exemplo:

```text
REQUISITO DE UX
“Ao confirmar uma ação crítica, a pessoa recebe confirmação imediata
quando o efeito já está seguro no dispositivo.”
```

Isso pode gerar mais tarde requisitos de engenharia como:

```text
persistência local
idempotência
fila de sincronização
reconciliação
```

Mas a UX não escolhe a implementação.

Outro exemplo:

```text
REQUISITO DE UX
“Se duas versões incompatíveis existirem, nenhuma pode sobrescrever
a outra silenciosamente; a pessoa precisa entender a diferença e escolher.”
```

A arquitetura decidirá como versões, locks, timestamps ou merge serão representados tecnicamente.

---

## 9. Estrutura mínima de uma jornada

Toda jornada material deve possuir:

```text
ID:
Nome:
Usuário / papel:
Contexto:
Gatilho:
Objetivo:
Pré-condições:
Entrada:
Fluxo principal:
Decisões:
Estados críticos:
Validações:
Saída de sucesso:
Saídas alternativas:
Recuperação obrigatória:
Privacidade / segurança visível:
Acessibilidade:
Evidência de sucesso:
Eventos semânticos necessários:
Regras de produto relacionadas:
UI relacionada:
Pendências:
```

Nem toda jornada precisa ser grande.

O importante é que seu comportamento seja testável e rastreável.

---

## 10. Taxonomia de IDs de UX

Recomenda-se utilizar IDs estáveis.

```text
UX-JRN-xxx  jornada
UX-FLW-xxx  fluxo
UX-STA-xxx  estado
UX-VAL-xxx  validação
UX-MSG-xxx  mensagem operacional
UX-ERR-xxx  erro/recuperação
UX-EVT-xxx  evento semântico
UX-TST-xxx  tarefa de teste
UX-GATE-xxx gate de passagem
```

Os prefixos podem variar conforme o projeto.

O requisito é preservar rastreabilidade.

Um ID aposentado não deve ser reutilizado para representar outro comportamento.

---

## 11. Jornada, fluxo e tela não são sinônimos

Uma jornada representa um resultado do usuário.

Um fluxo representa as decisões e transições necessárias.

Uma tela representa apenas uma superfície dentro desse fluxo.

```text
JORNADA
“obter um plano válido”

pode conter

FLUXO A
importar

FLUXO B
criar manualmente

FLUXO C
receber de terceiro
```

Cada fluxo pode atravessar várias telas.

Portanto:

```text
INVENTÁRIO DE TELAS
≠
ESPECIFICAÇÃO DE UX
```

---

## 12. Arquitetura da experiência

A UX pode definir a arquitetura de informação e navegação **do ponto de vista da pessoa**.

Ela pode estabelecer:

- destinos principais;
- destinos secundários;
- tarefas focadas;
- relações entre áreas;
- prioridade de entrada;
- comportamento de retorno;
- persistência ou não do contexto;
- possibilidade de deep link;
- diferenças entre form factors;
- quais superfícies devem permanecer independentes;
- quais módulos não podem invadir a tarefa principal.

Ela não precisa definir a biblioteca de router ou a estrutura interna de rotas.

### 12.1. Destino principal versus tarefa focada

Um padrão útil é:

```text
DESTINO PRINCIPAL
→ exploração e contexto do domínio

TAREFA FOCADA
→ criar, editar, importar, revisar, confirmar, executar
```

A tarefa focada pode suspender navegação global quando isso reduz distração ou risco.

Essa decisão deve ser orientada pela tarefa mental, não por preferência visual.

### 12.2. Form factors

Mobile, tablet e desktop podem compartilhar produto, identidade e regras sem obrigatoriamente compartilhar a mesma composição.

A UX deve documentar quando:

- o fluxo é equivalente;
- a navegação muda;
- a densidade muda;
- o contexto de uso muda;
- uma superfície precisa de comportamento próprio.

Não assumir que responsividade significa apenas ampliar ou comprimir o mesmo layout.

---

## 13. Superfície orientada por estado

Uma mesma tela pode representar experiências muito diferentes conforme o estado.

Para superfícies centrais, definir uma matriz como:

| Estado | O que a pessoa vê | Ação dominante | Próxima possibilidade | Regra |
| --- | --- | --- | --- | --- |
| estado A | conteúdo real | ação A | alternativa | regra |
| estado B | conteúdo real | ação B | alternativa | regra |

Evitar telas que mostram o mesmo CTA independentemente do estado real do domínio.

Exemplo genérico:

```text
ATIVO
→ continuar

PLANEJADO
→ iniciar

CONCLUÍDO
→ ver resultado

AUSENTE
→ escolher como começar

ERRO RECUPERÁVEL
→ recuperar
```

---

## 14. Regras de navegação e retorno

A especificação deve responder:

- o que acontece ao tocar em Voltar;
- quando preservar rascunho;
- quando confirmar saída;
- quando retornar ao último destino válido;
- quando uma tarefa deve recomeçar;
- como deep links tratam autenticação e permissão;
- o que acontece quando uma feature deixa de estar disponível;
- qual contexto é preservado após retorno de integração externa.

### 14.1. Confirmação proporcional

Não perguntar “Deseja sair?” por hábito.

Perguntar somente quando existe consequência real.

```text
NADA A PERDER
→ voltar normalmente

RASCUNHO RECUPERÁVEL
→ preservar e voltar

DADO NÃO PERSISTIDO
→ avisar consequência

AÇÃO IRREVERSÍVEL
→ confirmação explícita
```

---

## 15. Padrão de edição progressiva

Para objetos complexos, preferir decomposição que acompanhe a tarefa mental.

Padrão recorrente:

```text
LISTA
        ↓
DETALHE
        ↓
EDIÇÃO
```

Evitar colocar todas as operações possíveis na mesma superfície apenas porque tecnicamente cabem.

Uma coleção editável deve mostrar contexto suficiente para escolher o item.

O detalhe deve explicar o estado do objeto.

A edição deve concentrar a modificação.

---

## 16. Estados globais

O processo deve definir um vocabulário oficial de estados quando aplicável.

Exemplo:

| Estado | Significado de UX | Regra |
| --- | --- | --- |
| Carregando | conteúdo ainda não disponível | não apagar conteúdo já válido sem necessidade |
| Salvando | efeito ainda sendo persistido | bloquear apenas o comando afetado quando possível |
| Salvo localmente | efeito seguro no dispositivo | é sucesso local, não erro |
| Sincronização pendente | há trabalho remoto pendente | não bloquear tarefa que pode continuar |
| Sincronizado | confirmação remota concluída | não transformar operação técnica em celebração |
| Conflito | existem versões incompatíveis | não sobrescrever silenciosamente |
| Indisponível | dependência ou módulo não pode operar | explicar impacto e fallback |
| Revogado | acesso foi retirado | explicar o que parou e o que permanece |
| Bloqueado | regra impede continuidade | explicar motivo e próximo passo quando permitido |

Nem todos os produtos terão todos esses estados.

O documento deve incluir somente os que realmente existem ou são plausíveis no domínio.

---

## 17. Offline e conectividade

Quando a experiência precisa funcionar em rede instável ou sem rede, a UX deve especificar a **política comportamental por domínio**.

Estrutura recomendada:

| Domínio | Leitura offline | Escrita offline | O que fica indisponível | Recuperação esperada |
| --- | --- | --- | --- | --- |
| domínio A | sim/não | sim/não | dependência externa | comportamento |

A UX pode exigir:

- continuidade da tarefa crítica;
- confirmação local verdadeira;
- indicação de pendência;
- retry explícito;
- preservação do que já foi digitado;
- resolução visível de conflito;
- fallback quando serviço externo estiver indisponível.

A UX não deve escolher:

- engine de storage;
- outbox concreta;
- filas;
- protocolo de sync;
- estratégia de cache;
- política interna de merge.

---

## 18. Repetição e efeito duplicado

Toque repetido, retry, retorno do background e falha de rede fazem parte da experiência.

A UX deve identificar ações em que repetir a intenção **não pode duplicar o efeito percebido**.

Exemplo:

```text
USUÁRIO TOCA CONFIRMAR
        ↓
SEM RESPOSTA VISÍVEL
        ↓
TOCA NOVAMENTE
```

A especificação deve dizer qual resultado é esperado.

Isso gera um requisito posterior de engenharia, mas a necessidade nasce da experiência.

Evitar usar o termo técnico sem explicar o comportamento que ele protege.

---

## 19. Erros e recuperação

Uma mensagem de erro útil precisa responder, quando possível:

```text
O QUE ACONTECEU?
        ↓
QUAL É O IMPACTO?
        ↓
O QUE CONTINUA SEGURO?
        ↓
O QUE A PESSOA PODE FAZER AGORA?
```

Evitar:

```text
“Algo deu errado”
“Erro 500”
“Falha desconhecida”
“Operação inválida”
```

quando o produto sabe algo mais específico.

### 19.1. Erro de campo

Erro ligado a um campo deve aparecer perto do contexto do campo.

Preservar valores válidos.

Foco deve levar ao primeiro problema quando isso melhora recuperação.

### 19.2. Erro externo

Quando a falha pertence a terceiro, deixar claro:

- qual dependência falhou, quando apropriado;
- o impacto;
- se os dados locais continuam preservados;
- se há fallback;
- quando tentar novamente.

Não fazer o usuário interpretar uma falha de parceiro como corrupção do produto inteiro.

---

## 20. Validação proporcional

Nem toda inconsistência precisa bloquear.

A UX pode classificar validações em níveis como:

```text
BLOQUEIO
→ não é seguro ou válido continuar

REVISÃO
→ exige decisão humana

AVISO
→ pode continuar, mas existe consequência ou incerteza

INFORMATIVO
→ algo foi ajustado, ignorado ou interpretado
```

Isso é especialmente útil em:

- importações;
- uploads;
- cadastros complexos;
- integrações;
- dados externos;
- automações;
- recomendações;
- conteúdo gerado por IA.

A classificação deve ser explicável ao usuário.

---

## 21. Automação confirmável

Quando o produto sugere ou gera algo automaticamente, a UX deve definir:

- o que foi sugerido;
- por que apareceu;
- qual fonte ou autoria existe;
- qual efeito ocorrerá;
- se o usuário pode editar;
- se pode recusar;
- quando a ação se torna definitiva.

Regra geral:

```text
SUGESTÃO
≠
DECISÃO
```

Exemplos:

- importação precisa de prévia quando altera estrutura relevante;
- recomendação precisa de contexto quando afeta decisão importante;
- conteúdo social deve ser revisado antes de publicação;
- mudança de configuração sensível deve ser confirmada antes de efeito externo.

---

## 22. Jornadas de criação e importação

Quando o produto recebe conteúdo externo ou permite criar estruturas complexas, documentar:

```text
GATILHO
        ↓
SELEÇÃO / ENTRADA
        ↓
PRÉ-CHECAGEM
        ↓
VALIDAÇÃO
        ↓
PRÉVIA
        ↓
CORREÇÃO
        ↓
CONFIRMAÇÃO
        ↓
RESULTADO
```

Nem toda jornada precisa usar todas as fases.

Mas operações de alto impacto não devem pular diretamente de entrada para efeito definitivo sem necessidade explícita.

A recuperação deve explicar:

- o que foi preservado;
- se é possível substituir a entrada;
- se a tentativa pode ser retomada;
- como duplicidade é tratada;
- como erros parciais aparecem.

---

## 23. Jornada de tarefa crítica

Toda aplicação possui uma ou mais tarefas cujo fracasso compromete o valor central.

A UX deve identificar essas tarefas e criar uma especificação mais rigorosa.

Uma tarefa crítica deve registrar:

- gatilho;
- menor caminho útil;
- ação dominante;
- tempo esperado quando relevante;
- estados intermediários;
- interrupções plausíveis;
- comportamento offline quando aplicável;
- repetição de ação;
- perda de foco;
- fechamento ou background;
- recuperação;
- saída parcial;
- saída completa;
- correção posterior.

A experiência deve ser testada no contexto real de uso, não apenas em protótipo ideal.

---

## 24. Casos especiais e variantes de domínio

Uma especificação madura não força comportamentos diferentes dentro do mesmo molde apenas para simplificar a UI.

Quando uma entidade possui variantes legítimas, documentar diferenças.

Exemplo genérico:

```text
TIPO A
→ campo X + campo Y

TIPO B
→ duração substitui quantidade

TIPO C
→ usa distância e intensidade
```

O objetivo é evitar interfaces que tecnicamente armazenam tudo, mas semanticamente confundem o usuário.

---

## 25. Conclusão e decisão posterior

Toda jornada com resultado relevante deve especificar o fechamento.

Perguntas:

- como a pessoa sabe que concluiu?;
- o que mudou?;
- existe resumo?;
- existe recomendação?;
- existe ação posterior?;
- essa ação é obrigatória ou opcional?;
- existe compartilhamento?;
- existe correção?;
- existe reversão?;
- existe efeito em próxima versão ou apenas no histórico atual?

Evitar transformar todo sucesso em nova oportunidade de engajamento.

---

## 26. Permissões e consentimento

Permissão não deve ser apenas um toggle técnico.

A UX deve explicar:

```text
QUAL DADO?
PARA QUAL FINALIDADE?
PARA QUEM?
POR QUANTO TEMPO?
O QUE MUDA SE NEGAR?
COMO REVOGAR?
```

Permissões sensíveis devem ser solicitadas no contexto em que geram valor, quando possível.

Evitar pedir câmera, localização, notificações, contatos ou dados sensíveis no primeiro acesso apenas porque serão úteis futuramente.

### 26.1. Revogação

A revogação deve deixar claro:

- o que deixa de funcionar;
- o que permanece salvo;
- se existe histórico;
- se existe nova solicitação possível;
- se existe efeito imediato.

---

## 27. Colaboração, versões e autoria

Quando mais de uma pessoa ou sistema pode alterar o mesmo objeto, a UX deve representar autoria e versão quando isso for relevante para confiança.

Especificar:

- quem alterou;
- quando;
- o que mudou;
- qual versão está ativa;
- se existe rascunho;
- se a mudança exige aceite;
- se existe conflito;
- como comparar;
- como rejeitar;
- como reverter quando permitido.

A UX não decide como versionamento será implementado no banco.

Ela define o comportamento necessário para não apagar autoria ou mudança silenciosamente.

---

## 28. Integrações e saída para terceiros

Quando uma jornada sai do produto para um parceiro, navegador, app externo ou serviço terceiro, especificar:

- o que a pessoa está prestes a fazer;
- quais dados são compartilhados;
- quem executa a próxima etapa;
- quando o produto perde controle;
- como retornar;
- qual estado pode ser confirmado;
- o que fazer se a integração falhar;
- como tratar informação desatualizada.

Regra:

```text
O PRODUTO NÃO DEVE ALEGAR UM RESULTADO EXTERNO
QUE O TERCEIRO NÃO CONFIRMOU.
```

---

## 29. Comunidade e conteúdo gerado por usuário

Quando houver UGC, a UX deve especificar no mínimo:

- criação;
- revisão antes de publicação quando aplicável;
- audiência;
- edição;
- exclusão;
- denúncia;
- bloqueio;
- ocultação;
- moderação;
- contestação/apelação quando necessária;
- estados de conteúdo removido ou restrito.

A segurança não deve depender apenas de operação administrativa invisível.

Controles essenciais precisam ser acessíveis dentro da experiência.

---

## 30. Gamificação e reconhecimento

Quando houver gamificação, a UX deve distinguir:

```text
RECONHECIMENTO
≠
PUNIÇÃO
≠
VALOR ECONÔMICO
```

Documentar:

- o que gera reconhecimento;
- o que não gera;
- estados pendentes;
- reversões;
- limites;
- contestação;
- consequências reais;
- ausência de benefício quando aplicável.

Evitar mecânicas que transformem descanso, falha de rede ou condição de saúde em culpa artificial.

---

## 31. Comércio e monetização na experiência

Quando o produto possui comércio ou monetização adjacente, a UX deve proteger o core.

Especificar:

- onde a oferta pode aparecer;
- onde não pode aparecer;
- disclosure;
- autoria/parceiro;
- atualização de preço quando aplicável;
- saída para checkout;
- retorno;
- falha externa;
- indisponibilidade;
- política para dados sensíveis;
- guardrails contra urgência artificial.

Receita não deve controlar silenciosamente a hierarquia da tarefa principal.

---

## 32. Microcopy operacional

Microcopy deve ajudar a pessoa a:

- decidir;
- compreender estado;
- entender consequência;
- corrigir;
- recuperar;
- reconhecer incerteza;
- identificar autoria;
- saber qual é o próximo passo.

Evitar usar texto para compensar uma hierarquia ruim.

### 32.1. Estrutura de mensagens

Quando aplicável:

```text
TÍTULO
→ nomeia situação

CORPO
→ explica consequência apenas se necessário

AÇÃO
→ descreve resultado, não “OK” genérico
```

### 32.2. Linguagem de incerteza

Sistemas que lidam com estimativas, IA, dados de terceiros ou recomendações devem comunicar incerteza de forma útil.

Exemplos:

```text
Estimativa
Sugestão
Fonte externa
Aguardando confirmação
Em revisão
```

Não transformar inferência em certeza visual.

---

## 33. Acessibilidade da jornada

Acessibilidade deve ser especificada no fluxo, não apenas no componente.

Avaliar:

- ordem de foco;
- retorno de foco após sheet/dialog;
- teclado;
- leitor de tela;
- anúncio de resultado;
- alvo de toque;
- texto ampliado;
- zoom;
- reflow;
- alternativa a gesto;
- alternativa a cor;
- redução de movimento;
- CTA fixo sem encobrir foco;
- timer sem depender apenas de som;
- gráfico com equivalente textual;
- erro identificado em texto;
- conteúdo dinâmico anunciado quando necessário.

Uma tela acessível isoladamente pode formar uma jornada inacessível se foco, retorno ou transição estiverem errados.

---

## 34. Contexto real de uso

A UX deve registrar condições físicas e cognitivas relevantes.

Exemplos:

- uma mão ocupada;
- movimento;
- luva;
- ruído;
- sol forte;
- pouca atenção disponível;
- interrupções frequentes;
- rede ruim;
- uso prolongado;
- teclado aberto;
- dispositivo pequeno;
- desktop com teclado;
- ambiente profissional denso;
- baixa familiaridade técnica.

Os testes devem reproduzir as condições mais importantes sempre que possível.

---

## 35. Instrumentação semântica

A UX pode definir **quais eventos precisam ser observáveis para medir a experiência**.

Ela não escolhe a ferramenta concreta de analytics.

Uma taxonomia útil pode registrar:

```text
EVENTO
quando acontece
qual outcome mede
quais propriedades mínimas são necessárias
quais dados são proibidos
```

Exemplo:

| Evento semântico | Significado | Propriedades permitidas | Dados proibidos |
| --- | --- | --- | --- |
| tarefa_iniciada | início real | origem, contexto | conteúdo sensível |
| tarefa_concluida | resultado alcançado | duração agregada, estado | texto livre sensível |
| recuperacao_usada | usuário recuperou falha | tipo de falha | payload bruto |

A nomenclatura final pode ser reconciliada com a engenharia sem perder o significado.

---

## 36. Minimização de dados em analytics

A especificação deve declarar quando eventos **não podem transportar conteúdo operacional sensível**.

Preferir:

- IDs técnicos;
- categorias;
- enums;
- faixas;
- estados;
- duração agregada;
- contagens;
- códigos de razão.

Evitar em analytics, quando desnecessário:

- texto livre;
- conteúdo de mensagens;
- dados de saúde;
- senha;
- token;
- documento pessoal;
- conteúdo privado;
- payload de integração;
- dados completos de terceiros.

Privacidade de telemetria deve ser considerada antes da implementação.

---

## 37. Funil de valor

Quando a experiência possui uma sequência de ativação ou geração de valor, a UX pode criar um funil orientado a resultado.

Exemplo:

```text
F0 — entrada
F1 — contexto mínimo
F2 — capacidade preparada
F3 — primeira ação de valor
F4 — primeira conclusão
F5 — retorno / decisão seguinte
F6 — valor recorrente
```

O funil deve refletir comportamento real.

Visitar uma página não deve contar como ativação se o produto só gera valor depois de uma ação concreta.

---

## 38. Plano de validação

A UX deve definir como provar que as jornadas funcionam antes de tratá-las como resolvidas.

Estrutura recomendada:

| Superfície/Jornada | Perfil | Tarefa | Amostra inicial | Meta | Falha crítica |
| --- | --- | --- | --- | --- | --- |
| jornada | usuário | tarefa real | n | critério | condição |

Possíveis evidências:

- teste moderado;
- protótipo navegável;
- teste em produto real;
- arquivo real;
- uso offline;
- leitor de tela;
- teclado;
- dispositivo pequeno;
- cenário de erro;
- falha externa simulada;
- retomada após interrupção.

### 38.1. Métricas de UX

Métricas úteis incluem:

- conclusão;
- tempo;
- erro;
- necessidade de ajuda;
- recuperação;
- abandono;
- compreensão;
- confiança;
- repetição indevida;
- quantidade de passos quando relevante.

Evitar medir qualidade apenas por clique ou quantidade de telas entregues.

---

## 39. Perguntas de pesquisa

A Especificação de UX deve encerrar pendências como perguntas testáveis, por exemplo:

```text
A pessoa reconhece a próxima ação sem ajuda?

Ela entende quando algo está salvo localmente mas ainda não sincronizado?

Consegue corrigir um erro sem perder trabalho válido?

Entende a diferença entre sugestão e decisão?

Consegue revogar uma permissão sem suporte?

Reconhece quando está saindo para um terceiro?
```

Perguntas não devem ser redigidas de forma que pressuponham a resposta desejada.

---

## 40. Gates de UX

Antes da passagem para a próxima etapa, criar gates proporcionais ao produto.

Exemplo:

| Gate | Evidência | Owner |
| --- | --- | --- |
| UX-01 Core | tarefa principal especificada e testável | UX + Produto |
| UX-02 Estados | vazio, erro, loading e recuperação definidos | UX + QA |
| UX-03 Offline | comportamento de conectividade definido quando aplicável | UX + Engenharia |
| UX-04 Inclusão | foco, toque, leitor, texto e movimento cobertos | Design + QA |
| UX-05 Privacidade | consentimento, minimização e revogação cobertos | Produto + responsável |
| UX-06 Dados externos | incerteza, fallback e autoria definidos | UX + Produto |
| UX-07 Medição | eventos e tarefas de validação definidos | Analytics + Research |
| UX-08 Rastreabilidade | jornadas ligadas a PO e UI | PO + UX |

Projetos pequenos podem usar menos gates.

Projetos regulados, sensíveis ou multiatores podem precisar de mais.

---

## 41. Definition of Ready para entrada técnica

A UX está pronta para alimentar as etapas técnicas quando:

- jornadas P0 possuem gatilho e saída;
- fluxo principal está descrito;
- decisões relevantes estão explícitas;
- estados críticos estão definidos;
- validações estão classificadas;
- recuperação existe;
- comportamento de retorno está definido;
- conectividade está tratada quando relevante;
- permissões e privacidade visível estão cobertas;
- acessibilidade foi incorporada;
- dependências externas possuem fallback ou estado de falha;
- métricas de experiência estão definidas;
- eventos semânticos necessários estão identificados;
- decisões de UI não foram redefinidas silenciosamente;
- regras do PO permanecem rastreáveis;
- pendências técnicas estão marcadas como pendências técnicas, não resolvidas por suposição.

`Ready para etapa técnica` ainda não significa `Ready for Codex`.

---

## 42. Handoff para Técnicas de Desenvolvimento

A próxima etapa recebe da UX:

```text
JORNADAS
FLUXOS
ESTADOS
VALIDAÇÕES
RECUPERAÇÃO
CONTRATOS DE INTERAÇÃO
CRITÉRIOS DE ACESSIBILIDADE
REQUISITOS DE CONECTIVIDADE
REQUISITOS DE PRIVACIDADE VISÍVEL
EVENTOS SEMÂNTICOS
METAS DE USABILIDADE
GATES
PENDÊNCIAS
```

A etapa de Técnicas de Desenvolvimento deve transformar essas necessidades em **padrões de qualidade para o trabalho de engenharia**.

Ela não deve escolher arquitetura ou stack por conta própria.

Exemplos de necessidades que podem surgir da UX:

```text
UX
“toque repetido não pode duplicar efeito”

→ Técnicas de Desenvolvimento
“testes e práticas precisam cobrir repetição e retry”

UX
“estado de erro deve preservar valores válidos”

→ Técnicas de Desenvolvimento
“testes precisam verificar preservação de estado e recuperação”

UX
“fluxo precisa funcionar com leitor de tela”

→ Técnicas de Desenvolvimento
“acessibilidade precisa entrar em revisão, teste e DoD”
```

---

## 43. Fronteira com Engenharia e Arquitetura

A UX pode descobrir necessidades técnicas sem escolher a solução.

Exemplo:

```text
UX OBSERVA
“usuário precisa trabalhar sem rede”
        ↓
ENGENHARIA RECEBE
“existem requisitos fortes de disponibilidade local,
persistência, reconciliação e recuperação”
        ↓
ARQUITETURA DECIDE
como estruturar essas propriedades
```

A Engenharia e Arquitetura deverão mensurar forças como:

- consistência;
- disponibilidade;
- latência;
- confiabilidade;
- concorrência;
- segurança;
- privacidade;
- escalabilidade;
- auditabilidade;
- resiliência;
- interoperabilidade.

A UX apenas registra o comportamento que torna essas forças necessárias.

---

## 44. Fronteira com a Visão do Tech Lead

A Especificação de UX não escolhe tecnologia concreta.

Quando surgir uma necessidade como:

```text
animação
háptica
offline
scanner
câmera
notificação
reader accessibility
charts
upload
sync
```

ela deve ser descrita como capacidade e contrato de experiência.

A Visão do Tech Lead decidirá posteriormente:

- runtime;
- framework;
- bibliotecas;
- SDKs;
- compatibilidade;
- estratégia concreta de implementação.

Nenhuma preferência tecnológica deve entrar na UX apenas por familiaridade do autor ou da IA.

---

## 45. Fronteira com DevOps e Infraestrutura

A UX pode exigir comportamento perceptível relacionado à operação, como:

- disponibilidade mínima de uma função crítica;
- fallback em indisponibilidade;
- manutenção comunicada;
- retorno após falha externa;
- retomada de upload;
- recuperação após interrupção.

Mas não decide:

- provider;
- regiões;
- CDN;
- filas gerenciadas;
- cluster;
- autoscaling;
- observabilidade concreta;
- backup concreto;
- topologia de rede.

Essas decisões pertencem às etapas técnicas e operacionais posteriores.

---

## 46. Rastreabilidade

Toda jornada material deve apontar para decisões anteriores.

Exemplo:

```text
BRIEFING
        ↓
OUT-003
        ↓
US-014
        ↓
UI-SCR-006
        ↓
UX-JRN-004
        ↓
UX-FLW-011
        ↓
UX-GATE-003
```

A rastreabilidade não precisa ficar inteira em uma única tabela nesta etapa.

Mas os IDs precisam permitir que a Matriz de Rastreabilidade posterior reconstrua a origem da decisão.

---

## 47. Mudança de produto descoberta durante UX

UX frequentemente revela problemas de escopo ou regra.

Quando isso ocorrer:

```text
PROBLEMA DE UX
        ↓
É APENAS INTERAÇÃO?
        ├── SIM → resolver na UX
        └── NÃO
             ↓
MUDA REGRA / OUTCOME / ESCOPO?
        ↓
RECONCILIAR COM PO OU BRIEFING
```

A UX não deve esconder mudança material dentro de um wireflow.

Exemplos de mudança material:

- nova permissão de produto;
- novo tipo de usuário;
- novo módulo;
- mudança de P0;
- mudança de regra financeira;
- nova coleta sensível;
- novo comportamento de publicação;
- nova dependência externa obrigatória.

---

## 48. Brownfield: preservar comportamento real sem canonizar bug

Em produtos existentes, a implementação atual é evidência, não autoridade absoluta.

Antes de redesenhar uma jornada:

```text
COMPORTAMENTO ATUAL
        ↓
É REGRA APROVADA?
        ├── SIM → preservar ou reconciliar
        └── NÃO
             ↓
É NECESSÁRIO PARA COMPATIBILIDADE?
        ├── SIM → registrar restrição
        └── NÃO → pode ser corrigido
```

Não documentar um bug como requisito apenas porque ele existe no código.

Também não remover comportamento necessário sem entender por que existe.

---

## 49. Revisão humana

A especificação deve ser construída iterativamente.

Uma sequência útil:

```text
1. arquitetura da experiência
2. jornadas core
3. estados e recuperação
4. permissões / privacidade
5. jornadas secundárias
6. conteúdo
7. acessibilidade
8. instrumentação
9. validação
10. gates e handoff
```

O humano deve revisar:

- se a jornada representa a intenção real;
- se a prioridade não mudou;
- se regras não foram inventadas;
- se estados extremos fazem sentido;
- se a fricção está proporcional ao risco;
- se o produto continua simples onde deveria;
- se a UX não antecipou tecnologia.

---

## 50. Canonização

Durante elaboração, manter distinção:

```text
DISCUTIDO
≠
APROVADO
≠
CANONIZADO
```

Antes de salvar o documento final do projeto, o ChatGPT deve apresentar síntese das decisões e principais pendências.

A canonização ocorre somente após autorização humana.

Exemplo:

```text
A Especificação de UX está aprovada.
Gere o 05_Especificacao_de_UX.md no projeto.
```

---

## 51. Estrutura recomendada do artefato do projeto

O `05_Especificacao_de_UX.md` de um projeto deve conter, conforme aplicável:

```text
1. Contrato de experiência
2. Leitura executiva
3. Autoridade e fontes
4. Problemas de UX relevantes
5. Arquitetura da experiência
6. Vocabulário de estados
7. Jornadas core
8. Jornadas secundárias
9. Regras de navegação e retorno
10. Validações
11. Erros e recuperação
12. Offline/conectividade
13. Permissões e consentimento
14. Colaboração/versões
15. Integrações externas
16. Conteúdo e microcopy
17. Acessibilidade
18. Instrumentação semântica
19. Plano de validação
20. Gates de UX
21. Rastreabilidade
22. Pendências
23. Handoff
```

A estrutura pode ser reduzida em produtos simples.

Não criar seções vazias apenas para obedecer ao template.

---

## 52. Anti-padrões

Evitar:

### UX como catálogo de telas

```text
Tela A
Tela B
Tela C
```

sem jornada, estado ou recuperação.

### UX como especificação técnica disfarçada

```text
“usar banco X”
“usar library Y”
“usar fila Z”
```

### Apenas caminho feliz

```text
abrir
clicar
salvar
fim
```

sem erro, retorno, interrupção ou conflito.

### Confirmação para tudo

Dialogs em toda ação aumentam fricção e dessensibilizam a pessoa.

### Mensagens genéricas

“Algo deu errado” para erros conhecidos.

### Tutorial como remendo

Explicar em cinco parágrafos uma interface que não deixa claro o próximo passo.

### Analytics como coleta indiscriminada

Enviar conteúdo sensível apenas porque a ferramenta permite.

### Referência externa como fonte de verdade

Copiar fluxo de concorrente sem reconciliar produto, contexto e restrições próprios.

### Exceção silenciosa

Criar um comportamento diferente localmente sem registrar por que o padrão não serviu.

---

## 53. Regras para trabalho com IA

Ao usar ChatGPT ou outra IA para elaborar UX:

1. ler os documentos anteriores integralmente;
2. não inferir regra de negócio ausente;
3. separar fato, hipótese e proposta;
4. perguntar ou registrar pendência quando decisão humana for necessária;
5. não escolher tecnologia concreta;
6. não copiar concorrente como solução automática;
7. considerar estados adversos;
8. considerar acessibilidade desde o fluxo;
9. considerar privacidade antes de instrumentação;
10. verificar se cada jornada termina em resultado observável;
11. verificar recuperação;
12. manter rastreabilidade com PO e UI;
13. destacar mudanças materiais antes de incorporá-las;
14. não canonizar automaticamente.

---

## 54. Critério de conclusão

A etapa pode ser considerada concluída quando a equipe consegue responder, sem improviso:

```text
POR QUE A PESSOA ENTRA?

O QUE ELA ESTÁ TENTANDO CONCLUIR?

QUAL É O CAMINHO PRINCIPAL?

QUAIS DECISÕES EXISTEM?

O QUE ACONTECE NOS ESTADOS ADVERSOS?

COMO ELA RECUPERA?

O QUE É REVERSÍVEL?

O QUE É SENSÍVEL?

O QUE PRECISA FUNCIONAR SEM REDE?

O QUE ACONTECE QUANDO TERCEIROS FALHAM?

COMO SABEMOS QUE A EXPERIÊNCIA FUNCIONOU?
```

E, principalmente:

> **As camadas técnicas conseguem compreender o comportamento necessário sem precisar inventar a experiência durante a implementação.**

---

## 55. Saída esperada

A saída desta etapa é:

```text
05_Especificacao_de_UX.md
```

Esse artefato deve funcionar como contrato comportamental da experiência.

Ele será consumido inicialmente por `06_Tecnicas_de_Desenvolvimento.md` e, posteriormente, pelas etapas de Engenharia e Arquitetura, Visão do Tech Lead, DevOps/Infraestrutura, backlog, testes e implementação.

Código continua bloqueado até que a baseline técnica posterior esteja aprovada e reconciliada.

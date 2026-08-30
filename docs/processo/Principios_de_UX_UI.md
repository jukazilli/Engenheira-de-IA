---
document_id: PROCESS-UXUI-PRINCIPLES
title: Princípios de UX e UI
status: draft-methodology
version: 0.1.0
stage: principios-ux-ui
type: transversal-constitution
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
produces: Principios_de_UX_UI.md
next_stage: 04_Direcao_de_UI_e_Design_System.md
---

# Princípios de UX e UI

## 1. Propósito

`Principios_de_UX_UI.md` é a constituição operacional de experiência do Processo de Desenvolvimento de Software com IA Assistida.

Sua função é transformar intenção de produto, comportamento esperado, contexto de uso, riscos e guardrails já aprovados em **regras reutilizáveis para decidir como uma interface deve funcionar**.

A pergunta central desta etapa é:

> **Quais princípios devem orientar todas as decisões de interface para que o produto permaneça compreensível, consistente, acessível, seguro e fiel à intenção aprovada, independentemente da tela, dispositivo ou implementação concreta?**

Este documento existe para reduzir decisões de interface baseadas apenas em preferência pessoal, referência visual isolada ou conveniência de implementação.

Ele deve permitir responder, antes do código e antes do detalhamento de uma tela:

- qual é a tarefa mental atual da pessoa;
- qual ação precisa dominar aquele estado;
- qual é a menor interrupção suficiente para resolver a necessidade;
- quando preservar contexto e quando iniciar uma nova etapa;
- como comunicar carregamento, salvamento, erro, conflito, risco e recuperação;
- quais dados exigem maior cuidado de privacidade;
- quais princípios de acessibilidade são obrigatórios desde o desenho;
- como referências externas podem ensinar sem se tornar fonte de verdade do produto;
- quais decisões do produto não podem ser reinterpretadas silenciosamente por um redesenho.

Um bom design deve se explicar prioritariamente por **hierarquia, agrupamento, rótulos, estados, controles reconhecíveis e feedback**.

Tutorial, onboarding explicativo e texto didático são recursos legítimos quando necessários, mas não devem ser usados para compensar uma estrutura de interface ambígua.

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
PRINCIPIOS_DE_UX_UI.md
        ↓
04_Direcao_de_UI_e_Design_System.md
        ↓
05_Especificacao_de_UX.md
        ↓
CAMADAS TÉCNICAS POSTERIORES
```

O Product Owner define **resultado, comportamento, prioridade e regra de negócio**.

Os Princípios de UX/UI definem **como decisões de interface devem ser avaliadas**.

A Direção de UI e Design System definirá **como essa constituição se materializa visualmente em identidade, tokens, componentes e linguagem de interface**.

A Especificação de UX definirá **como jornadas, estados, transições, exceções e recuperação funcionam concretamente**.

As etapas técnicas posteriores transformarão essas necessidades em propriedades de engenharia, arquitetura, stack e operação.

---

## 3. Natureza transversal

Este documento é diferente das etapas sequenciais comuns.

Ele possui uma **primeira canonização após a Visão de Product Owner**, mas continua válido de forma transversal durante todo o projeto.

Isso significa:

```text
PO APROVADO
        ↓
PRINCÍPIOS UX/UI — BASELINE INICIAL
        ↓
UI / DESIGN SYSTEM
        ↓
UX DETALHADO
        ↓
ENGENHARIA / ARQUITETURA
        ↓
TECH LEAD
        ↓
DEVOPS / INFRA
        ↓
IMPLEMENTAÇÃO
        ↓
NOVAS EVIDÊNCIAS
        ↓
RECONCILIAÇÃO DOS PRINCÍPIOS, SE NECESSÁRIO
```

A existência de novas informações técnicas ou operacionais não autoriza uma camada posterior a contrariar silenciosamente os princípios.

Quando surgir uma restrição legítima que exija exceção ou alteração:

```text
RESTRIÇÃO NOVA
        ↓
CONFLITO COM PRINCÍPIO?
        ↓
SIM
        ↓
REGISTRAR CONTEXTO E IMPACTO
        ↓
RECONCILIAR DOCUMENTAÇÃO
        ↓
APROVAÇÃO HUMANA
```

---

## 4. Origem desta etapa

Esta constituição foi formalizada a partir do documento operacional utilizado no DayGym.

No processo real, os Princípios de UX/UI eram usados para novos recortes de interface e redesenhos incrementais e transformavam direção de produto, sistema visual, jornadas e regras de engenharia em critérios práticos de decisão.

Esse material mostrou que um documento de princípios pode cumprir funções diferentes de um Design System ou de uma Especificação de UX.

Ele não dizia apenas “como a interface deve parecer”.

Ele orientava decisões como:

- quando usar feedback inline;
- quando usar bottom sheet;
- quando usar dialog;
- quando iniciar uma nova tela;
- quando manter ação fixa durante rolagem;
- como representar estados offline e de sincronização;
- como preservar contratos durante redesenhos;
- como reduzir carga cognitiva;
- como tratar acessibilidade e privacidade como propriedades da interação.

A metodologia preserva essa essência, mas corrige uma circularidade do processo original: no DayGym, o documento já consumia decisões das etapas de UI, UX e Engenharia porque foi criado posteriormente para governar redesenhos.

Na metodologia refinada, ele nasce primeiro como **baseline de princípios após o PO** e depois pode ser reconciliado com restrições comprovadas pelas camadas posteriores.

---

## 5. O que este documento decide

Os Princípios de UX/UI podem canonizar:

- princípios de interação;
- regras de carga cognitiva;
- critérios para ação dominante;
- política de revelação progressiva;
- critérios para preservação ou mudança de contexto;
- matriz de escolha de superfície;
- hierarquia de ações;
- regras de feedback;
- princípios de prevenção e recuperação;
- postura de acessibilidade;
- postura de privacidade na interface;
- regras de conteúdo e microcopy;
- regras de uso de referências externas;
- contratos mínimos para especificar uma tela;
- Definition of Ready de UX/UI;
- Definition of Done de UX/UI;
- protocolo de exceção e evolução.

---

## 6. O que este documento não decide

Este documento não deve definir silenciosamente:

- novo público;
- novo módulo de produto;
- prioridade de produto;
- regra de negócio não aprovada;
- roadmap;
- arquitetura de software;
- framework;
- biblioteca;
- banco de dados;
- provider;
- estrutura de repositório;
- API concreta;
- schema físico de dados;
- estratégia de deploy;
- CI/CD;
- infraestrutura;
- detalhes visuais finais que pertencem ao Design System;
- wireflows completos que pertencem à Especificação de UX.

Os princípios orientam decisões.

Eles não substituem as camadas responsáveis por produto, design detalhado ou tecnologia.

---

## 7. Autoridade e precedência documental

No processo refinado, a precedência deve evitar tanto que referências visuais sobrescrevam produto quanto que limitações técnicas não investigadas empobreçam a experiência prematuramente.

Ordem de autoridade recomendada:

| Prioridade | Fonte | O que decide |
| --- | --- | --- |
| 1 | Lei, segurança, privacidade e políticas obrigatórias | limites que o produto não pode violar |
| 2 | Briefing e Visão de Product Owner | escopo, promessa, prioridade, regra de negócio e aceite |
| 3 | Princípios de UX/UI | constituição de interação e decisão de interface |
| 4 | Direção de UI e Design System | identidade, tokens, componentes e linguagem visual |
| 5 | Especificação de UX | jornadas, estados, transições, recuperação e conteúdo operacional |
| 6 | Engenharia, Arquitetura, Tech Lead, DevOps e Infra | materialização técnica e operacional dentro dos contratos aprovados |
| 7 | Código e implementação existente | evidência do estado real; divergência com o canônico deve ser registrada |
| 8 | Issue, prompt, mock isolado ou referência externa | recorte local sem poder de contrariar fontes superiores |

Uma camada posterior pode descobrir uma inviabilidade real.

Nesse caso, ela não “vence” silenciosamente a fonte anterior.

Ela abre uma reconciliação.

---

## 8. Princípio estrutural: tarefa mental antes da tela

A unidade primária de decisão de UX não é a página, o card ou o componente.

É a **tarefa mental atual da pessoa**.

Antes de desenhar uma superfície, deve ser possível responder:

```text
O QUE A PESSOA ESTÁ TENTANDO FAZER AGORA?
        ↓
QUAL DECISÃO ELA PRECISA TOMAR?
        ↓
QUAL INFORMAÇÃO É NECESSÁRIA PARA ESSA DECISÃO?
        ↓
QUAL AÇÃO REPRESENTA O PRÓXIMO PASSO?
```

Uma tela visualmente simples pode ser cognitivamente confusa.

Uma tela relativamente rica pode ser cognitivamente clara se sua hierarquia refletir corretamente a tarefa.

---

## 9. Princípios canônicos

### P1 — Começar pelo problema e pela próxima decisão

Toda interface nasce de uma necessidade observável.

A pessoa deve conseguir reconhecer rapidamente:

- onde está;
- o que importa agora;
- o que mudou;
- qual é o próximo passo.

Não começar desenhando componentes.

Começar entendendo o problema e a decisão.

### P2 — Uma ação dominante por estado

Pode haver várias ações em uma jornada, mas apenas uma deve dominar cada estado da interface quando existir uma ação principal clara.

Ações secundárias não devem competir por:

- cor;
- tamanho;
- posição;
- contraste;
- repetição.

“Uma ação dominante” não significa “um único botão na tela”.

Significa uma hierarquia inequívoca.

### P3 — Contexto real de uso primeiro

Projetar para o contexto em que a pessoa realmente utilizará o produto.

Avaliar, conforme o projeto:

- uso com uma mão;
- movimento;
- pouco tempo disponível;
- iluminação adversa;
- ruído;
- interrupções;
- rede instável;
- dispositivo antigo;
- teclado;
- toque;
- mouse;
- leitor de tela;
- zoom;
- baixa familiaridade técnica;
- necessidade de alternar atenção com o ambiente físico.

A pessoa não deve precisar memorizar informação entre superfícies quando o sistema já conhece esse dado.

### P4 — Complexidade fica no sistema

O domínio pode ser complexo.

A interface não precisa expor essa complexidade integralmente.

Regras, sincronização, cálculos, versões, políticas e integrações podem existir internamente enquanto a superfície mostra apenas a informação necessária para a decisão atual.

Aplicar **revelação progressiva**.

Detalhes aparecem quando aumentam compreensão ou controle, não porque existem no modelo de dados.

### P5 — Menor interrupção suficiente

A superfície escolhida deve ser proporcional ao peso mental e ao risco da ação.

```text
RESPOSTA LOCAL
→ preferir resposta local

ESCOLHA CURTA
→ não transformar em fluxo desnecessário

DECISÃO CRÍTICA
→ não esconder em feedback efêmero
```

Evitar abrir uma nova janela quando o contexto atual é suficiente.

Evitar comprimir uma tarefa complexa em componente pequeno apenas para “não sair da tela”.

### P6 — Mudou a tarefa mental, mudou a superfície

Se a pessoa continua resolvendo essencialmente a mesma tarefa, preservar o contexto quando possível.

Se inicia uma etapa com:

- objetivo próprio;
- conteúdo extenso;
- múltiplos campos;
- navegação própria;
- histórico próprio;
- retomada independente;
- risco maior;
- deep link próprio;

uma nova tela ou fluxo focado pode ser mais apropriado.

### P7 — Estado e confiança são visíveis

Estados tecnicamente diferentes devem ser comunicados como estados diferentes quando isso afeta a confiança ou a ação do usuário.

Exemplos:

```text
CARREGANDO
SALVANDO
SALVO LOCALMENTE
SINCRONIZAÇÃO PENDENTE
SINCRONIZADO
CONFLITO
ERRO RECUPERÁVEL
ERRO BLOQUEANTE
SUCESSO
```

Ausência de mensagem de erro não é confirmação suficiente de sucesso.

### P8 — Prevenir e recuperar antes de culpar

A interface deve ajudar a pessoa a evitar erros previsíveis e recuperar-se quando eles acontecem.

Práticas:

- preencher valores conhecidos quando apropriado;
- mostrar restrições perto do ponto de decisão;
- preservar valores válidos depois de falha;
- oferecer desfazer quando seguro;
- explicar impacto;
- informar a próxima ação;
- evitar linguagem que atribui culpa ao usuário.

### P9 — Acessibilidade integra a decisão

Acessibilidade não é etapa de acabamento.

Ela influencia desde o início:

- contraste;
- foco;
- ordem de leitura;
- semântica;
- leitor de tela;
- teclado;
- alvo de toque;
- safe area;
- texto ampliado;
- zoom;
- redução de movimento;
- alternativas a gesto;
- informação que não dependa apenas de cor.

### P10 — Consistência vem de comportamento compartilhado

Problemas equivalentes devem usar comportamentos equivalentes.

Consistência não significa repetir o mesmo layout em toda situação.

Significa que:

- mesma intenção usa padrão compatível;
- mesmo estado tem significado compatível;
- mesma família de ação preserva semântica;
- componentes compartilhados não ganham variantes locais sem necessidade.

### P11 — Privacidade é padrão

Dados sensíveis, privados ou potencialmente constrangedores aparecem apenas onde são necessários para a tarefa.

Uma lacuna visual nunca justifica maior exposição de dado privado.

Avaliar especialmente:

- saúde;
- localização;
- finanças;
- documentos;
- histórico privado;
- comunicação privada;
- menores;
- dados profissionais;
- credenciais;
- dados que possam inferir condição sensível.

### P12 — Identidade própria, aprendizado externo

Referências externas servem para aprender:

- hierarquia;
- ritmo;
- padrões de interação;
- processos de design;
- acessibilidade;
- ergonomia;
- convenções de plataforma.

Elas não autorizam copiar:

- marca;
- linguagem;
- navegação;
- regra de produto;
- payload;
- estado de domínio;
- componente sem análise de contexto;
- arquitetura de informação incompatível.

A solução final deve pertencer ao produto que está sendo construído.

---

## 10. Referências externas e pesquisa de design

Quando referências públicas forem utilizadas, distinguir:

```text
FONTE OFICIAL DE PLATAFORMA
→ convenções e requisitos da plataforma

PADRÃO DE ACESSIBILIDADE
→ requisito ou recomendação verificável

PUBLICAÇÃO DE DESIGN
→ aprendizado de processo ou princípio

PRODUTO CONCORRENTE
→ evidência de padrão de mercado ou oportunidade

REFERÊNCIA VISUAL
→ inspiração, nunca fonte canônica
```

O documento original do DayGym foi influenciado por publicações de design do Nubank e por diretrizes oficiais de Apple, Android e WCAG.

O aprendizado metodológico preservado é:

- envolver UX cedo;
- considerar contexto real de uso;
- cocriar entre produto, design e engenharia;
- questionar a primeira solução óbvia;
- testar compreensão, não apenas aparência;
- construir linguagem comum para crítica de design;
- evoluir por evidência;
- não copiar uma solução isolada fora do contexto.

A metodologia não considera nenhuma empresa externa como autoridade sobre o produto do usuário.

---

## 11. Protocolo obrigatório antes de desenhar uma tela

Antes de especificar ou redesenhar uma superfície, responder:

1. Quem usa e em qual contexto?
2. Qual outcome, jornada ou história origina esta interface?
3. De onde a pessoa veio?
4. Para onde ela deve retornar?
5. Qual tarefa mental está sendo executada?
6. Qual é a ação dominante neste estado?
7. O que a pessoa precisa reconhecer sem memorizar?
8. O que pode permanecer oculto até ser solicitado?
9. A ação é reversível, destrutiva, externa, financeira, sensível ou regulada?
10. Quais estados de carregamento, vazio, salvamento, erro e sucesso existem?
11. Existe possibilidade de rede instável, retry, repetição ou conflito?
12. Que dado privado aparece e por quê?
13. Como a interação funciona sem gesto?
14. Como funciona sem depender apenas de cor?
15. Como funciona com teclado, leitor de tela e texto ampliado, quando aplicável?
16. Qual princípio justifica a superfície escolhida?
17. Quais decisões canônicas não podem ser alteradas por este recorte?
18. Qual evidência demonstrará que a solução funciona?

Sem essas respostas, a interface ainda não atende à Definition of Ready de UX/UI.

---

## 12. Greenfield e brownfield

O protocolo muda ligeiramente dependendo do estado do projeto.

### 12.1. Produto novo

Em greenfield, a interface é derivada principalmente de:

```text
PO
↓
PRINCÍPIOS
↓
DESIGN SYSTEM
↓
UX
```

Não existe implementação anterior para preservar.

O foco é evitar criar contratos técnicos prematuros a partir do layout.

### 12.2. Produto existente ou redesenho

Em brownfield, antes de alterar uma tela, também é necessário compreender o estado real.

Investigar, quando aplicável:

- rota;
- deep link;
- permissões;
- contratos de API;
- mutations;
- estados de domínio;
- offline;
- sincronização;
- analytics permitido;
- testes existentes;
- integrações;
- atalhos de teclado;
- dependências entre telas.

O código existente não substitui a documentação canônica, mas ignorá-lo pode produzir um redesenho destrutivo.

---

## 13. Matriz de decisão da superfície

Evitar especificações vagas como “abrir um popup”.

Nomear o padrão correto deixa intenção, acessibilidade, comportamento e teste mais explícitos.

| Necessidade | Padrão preferido | Critério |
| --- | --- | --- |
| validar ou orientar um campo | feedback inline | informação pertence ao controle e não interrompe a tarefa |
| confirmar ação simples e reversível | snackbar/toast acionável com desfazer, quando a plataforma permitir | mensagem breve; sem decisão crítica |
| mostrar detalhe opcional curto | expansão inline | pessoa permanece na mesma leitura |
| escolher opção curta em desktop | dropdown ou popover | escolha local, sem tarefa independente |
| escolher ou ajustar algo curto em mobile | bottom sheet | mesma tarefa, retorno imediato ao contexto |
| oferecer poucas ações relacionadas | action sheet/menu de ações | ação já foi iniciada e falta escolher desfecho |
| interromper por risco, conflito ou consequência irreversível | dialog/alert | decisão é necessária antes de continuar |
| executar formulário ou decisão com começo e fim próprios | nova tela | nova tarefa mental, maior conteúdo ou retomada própria |
| executar etapa sequencial sem distrações | fluxo focado | reduz navegação global e preserva progressão/retorno |
| manter ação principal disponível durante rolagem | barra de ação fixa | mesma ação permanece válida e não encobre conteúdo |

A matriz não é uma lei universal de plataforma.

É uma heurística operacional que deve respeitar convenções atuais de cada ambiente.

---

## 14. Feedback inline

Usar quando a informação pertence diretamente ao elemento sendo manipulado.

Exemplos:

- formato inválido;
- campo obrigatório;
- regra de intervalo;
- ajuda contextual;
- disponibilidade local;
- aviso diretamente relacionado ao valor.

Evitar deslocar uma correção simples para modal ou tela separada.

---

## 15. Snackbar, toast e ação reversível

Feedback efêmero é apropriado quando:

- a ação já ocorreu;
- a consequência é de baixo risco;
- a mensagem pode desaparecer sem prejudicar compreensão;
- existe recuperação simples, como `Desfazer`, quando necessária.

Não usar como único meio para:

- erro crítico;
- decisão obrigatória;
- informação jurídica relevante;
- perda irreversível;
- conflito que exige escolha;
- confirmação que o usuário precisa consultar depois.

---

## 16. Bottom sheet

Usar quando uma escolha ou ajuste breve pertence claramente ao contexto atual.

Boas condições:

- tarefa curta;
- poucas opções;
- retorno imediato à origem;
- conteúdo que cabe sem navegação complexa;
- fechamento previsível;
- foco controlado;
- acionador restaurado ao fechar.

Não usar para:

- navegação permanente;
- conteúdo longo;
- múltiplas etapas;
- formulário extenso;
- histórico próprio;
- deep link independente;
- tarefa que precisa ser retomada muito depois.

---

## 17. Dialog ou alert

Usar com parcimônia para:

- risco alto;
- conflito;
- perda não recuperável;
- confirmação crítica;
- decisão que precisa interromper a tarefa.

O título deve nomear a situação.

O corpo explica consequência apenas quando necessário.

Os botões devem nomear resultados diferentes.

Evitar dialogs apenas para informar sucesso comum ou erro recuperável simples.

---

## 18. Nova tela ou fluxo focado

Usar quando existe mudança real de tarefa mental.

Sinais:

- vários campos;
- leitura extensa;
- etapa sequencial;
- histórico independente;
- deep link;
- retomada posterior;
- decisão complexa;
- necessidade de reduzir distração.

Voltar deve preservar rascunho quando seguro.

Sair só deve pedir confirmação quando existe algo real a perder.

---

## 19. Regra para ação fixa

Uma barra ou CTA fixo é adequado quando:

- existe uma ação dominante estável durante toda a rolagem;
- voltar a procurar a ação aumentaria esforço ou erro;
- a superfície reserva espaço para que conteúdo não fique encoberto;
- teclado, zoom, texto ampliado e safe areas continuam utilizáveis;
- foco e mensagens de erro continuam visíveis.

Não é adequado quando:

- a ação muda conforme o item visível;
- existem várias ações equivalentes;
- ocupa área excessiva;
- cobre campos ou feedback;
- causa conflito com teclado;
- cria duplicação sem ganho real.

Prioridade de ação deve permanecer equivalente entre mobile, tablet e desktop, mesmo que a posição física mude.

---

## 20. Hierarquia de ações

### Ação primária

Representa o próximo passo dominante.

Recebe maior ênfase.

### Ação secundária

Alternativa relevante, com menor ênfase.

### Ação terciária

Ação local, auxiliar ou de navegação.

### Ação destrutiva

Consequência explícita e confirmação proporcional ao risco.

### Ícone isolado

Usar apenas quando:

- o significado é reconhecível no contexto;
- existe nome acessível;
- área de interação é suficiente;
- não depende de descoberta acidental.

### Gesto

Todo gesto importante deve possuir alternativa visível ou equivalente acessível por controle convencional.

---

## 21. Feedback e estados

Toda interação deve produzir resposta verdadeira.

| Estado | Tratamento esperado |
| --- | --- |
| carregando | representar progresso sem falsear conteúdo final |
| salvando | indicar operação e impedir repetição apenas quando necessário |
| salvo localmente | deixar claro que a ação foi preservada neste dispositivo quando isso importa |
| sincronização pendente | indicar estado sem tratá-lo como falha definitiva |
| sincronizado | feedback discreto; não transformar operação técnica em celebração |
| vazio | explicar ausência e oferecer próxima ação real quando houver |
| erro recuperável | manter contexto, preservar valores e indicar próxima ação |
| erro bloqueante | explicar impacto e caminho de saída |
| conflito | comparar alternativas ou pedir decisão; nunca sobrescrever silenciosamente |
| sucesso reversível | oferecer desfazer quando apropriado |
| sucesso de jornada | atualizar estado ou avançar; evitar confirmação redundante |

Duplo clique, retry, retomada de background, repetição de envio e conexão instável devem ser considerados quando fazem parte do contexto do produto.

UX pode exigir idempotência ou preservação de estado como propriedade de experiência, mas não deve escolher a implementação técnica concreta.

---

## 22. Empty states

Estado vazio não é espaço para marketing genérico.

Ele deve responder:

```text
O QUE ESTÁ AUSENTE?
POR QUE ISSO IMPORTA?
HÁ ALGO QUE POSSO FAZER AGORA?
```

Quando não houver uma ação útil, não inventar CTA apenas para preencher espaço.

---

## 23. Erros

Uma mensagem de erro deve, quando possível, responder:

1. o que aconteceu;
2. o que foi ou não foi preservado;
3. o que a pessoa pode fazer;
4. quando tentar novamente é apropriado;
5. quando suporte ou outra rota é necessária.

Evitar códigos técnicos sem tradução.

Evitar mensagens que culpam o usuário por limitações do sistema.

---

## 24. Conteúdo e microcopy

Texto visível deve ajudar a:

- escolher;
- compreender estado;
- reduzir risco;
- recuperar-se;
- entender consequência;
- reconhecer valor.

Boas práticas:

- CTA usa verbo ligado ao resultado real;
- erro informa ação seguinte;
- empty state oferece ação real quando existir;
- unidades acompanham números;
- períodos e escopo temporal ficam claros;
- siglas são explicadas quando necessárias;
- linguagem segue o público do produto;
- jargão interno não aparece para usuário final;
- texto auxiliar repetitivo é removido;
- linguagem não manipula, culpa ou infantiliza sem intenção aprovada.

Microcopy não deve explicar arquitetura, nome de rota, payload ou detalhe interno sem necessidade do usuário.

---

## 25. Acessibilidade operacional

Antes de considerar uma solução pronta, avaliar quando aplicável:

- contraste suficiente;
- foco visível;
- ordem de foco;
- leitor de tela;
- semântica dos controles;
- teclado;
- alvo de toque;
- texto ampliado;
- zoom;
- reflow;
- orientação;
- safe areas;
- redução de movimento;
- informação não dependente apenas de cor;
- alternativa a gesto;
- ação fixa sem encobrir foco ou erro.

O padrão de conformidade deve ser definido de acordo com o projeto e suas obrigações.

Quando WCAG for aplicável, a versão e o nível alvo devem ser explicitados na documentação do projeto.

---

## 26. Responsividade não significa apenas redimensionar

Mobile, tablet e desktop podem exigir composição diferente.

O que deve permanecer equivalente é:

- prioridade;
- resultado;
- semântica;
- acesso às capacidades;
- segurança;
- compreensão do estado.

O mesmo componente visual não precisa existir em todos os breakpoints se outra composição atende melhor à tarefa mental.

---

## 27. Privacidade na interface

A interface deve aplicar minimização visual.

Perguntas obrigatórias:

- este dado precisa aparecer aqui?
- precisa aparecer completo?
- precisa permanecer visível depois da tarefa?
- pode ser ocultado por padrão?
- existe risco em screenshot, compartilhamento ou projeção?
- existe consentimento para essa finalidade?
- outro papel pode ver este dado?
- revogação altera a superfície?

Privacidade não deve ser usada apenas como texto legal.

Ela precisa existir no comportamento da interface.

---

## 28. Relação com a Direção de UI e Design System

Os Princípios dizem **como decidir**.

A Direção de UI define **como materializar visualmente essas decisões**.

Exemplo:

```text
PRINCÍPIO
Uma ação dominante por estado
        ↓
DESIGN SYSTEM
quais tokens e variantes representam primária, secundária e destrutiva
        ↓
TELA
qual ação concreta utiliza cada variante
```

O Design System não pode criar hierarquia visual que contradiga os princípios sem reconciliação.

---

## 29. Relação com a Especificação de UX

Os Princípios definem regras gerais.

A Especificação de UX aplica essas regras a jornadas concretas.

Exemplo:

```text
PRINCÍPIO
Mudou a tarefa mental, mudou a superfície
        ↓
UX
Jornada J-004 passa de lista para fluxo focado ao iniciar edição complexa
```

O documento de UX deve citar ou apontar quais princípios são particularmente relevantes em jornadas críticas quando isso melhora rastreabilidade.

---

## 30. Relação com Engenharia e Arquitetura

UX pode estabelecer propriedades observáveis como:

- tarefa crítica deve continuar sem rede;
- ação não pode duplicar efeito;
- estado precisa ser recuperável;
- conflito não pode apagar dados silenciosamente;
- resposta precisa ocorrer dentro de determinada janela de percepção;
- informação sensível não pode aparecer em logs visíveis ao usuário ou analytics indevido.

Engenharia e Arquitetura transformam essas necessidades em requisitos técnicos e estruturais.

Os Princípios não escolhem a tecnologia concreta.

---

## 31. Relação com Tech Lead

A Visão do Tech Lead consumirá necessidades de experiência já amadurecidas.

Exemplo:

```text
UX
sessão crítica precisa funcionar offline
        ↓
ENGENHARIA
consistência eventual é aceitável e operação deve ser idempotente
        ↓
ARQUITETURA
sync é boundary próprio
        ↓
TECH LEAD
seleciona tecnologias concretas compatíveis
```

O Tech Lead não deve reduzir uma exigência de experiência apenas porque uma tecnologia favorita não a atende.

Se houver inviabilidade real, deve retornar para reconciliação.

---

## 32. Contrato de preservação para redesenhos

Antes de redesenhar uma interface existente, criar um mapa com três categorias.

### Preservar

Quando já forem canônicos ou necessários:

- rota/deep link;
- autenticação;
- autorização;
- políticas de acesso;
- contratos de leitura e escrita;
- regras de negócio;
- estados de domínio;
- idempotência;
- offline;
- sincronização;
- analytics permitido;
- testes de contrato;
- rastreabilidade.

### Melhorar ou transplantar

Podem ser alvo de redesenho:

- hierarquia;
- agrupamento;
- ordem visual;
- densidade;
- espaçamento;
- superfície escolhida;
- composição de componentes;
- microcopy;
- foco;
- toque;
- teclado;
- responsividade;
- feedback.

### Adiar

Fora do recorte quando não houver decisão superior:

- mudança de backend motivada apenas por layout;
- reescrita arquitetural sem necessidade comprovada;
- nova regra de produto sem aceite;
- tela paralela que duplica implementação real;
- migração visual massiva sem fatias verificáveis.

---

## 33. Processo de redesenho incremental

Quando o produto já existe:

1. ler documentos canônicos aplicáveis;
2. inspecionar implementação real;
3. registrar tarefa mental e ação dominante;
4. mapear preservar / melhorar / adiar;
5. selecionar a menor fatia verificável;
6. prototipar;
7. validar compreensão e estados;
8. implementar na superfície real;
9. comparar antes/depois;
10. executar testes e verificações afetadas;
11. registrar evidência;
12. reconciliar documentação quando a decisão mudar.

Redesenho deve preferir tela ou jornada curta em vez de migração visual total em um único corte.

---

## 34. Contrato mínimo de uma tela

Toda especificação ou issue relevante de interface deve conseguir responder:

```text
Tela / superfície:
Origem canônica:
Usuário e contexto:
Tarefa mental:
Entrada:
Saída / retorno:
Ação dominante:
Ações secundárias:
Superfície escolhida e motivo:
Estados obrigatórios:
Dados sensíveis envolvidos:
Contratos a preservar:
Componentes reutilizados:
Acessibilidade:
Alternativa a gesto/cor:
Responsividade:
Fora do recorte:
Evidência de aceite:
```

O nível de detalhe pode variar conforme a complexidade da tela.

---

## 35. Definition of Ready de UX/UI

Uma interface está `Ready para design detalhado` quando:

- possui origem em outcome, jornada ou história aprovada;
- tarefa mental está explícita;
- ação dominante foi identificada;
- contexto de uso foi descrito;
- estados críticos são conhecidos;
- risco e sensibilidade de dados foram avaliados;
- dependências de produto estão claras;
- princípios aplicáveis foram identificados;
- superfície proposta possui justificativa;
- fora de escopo foi registrado;
- acessibilidade mínima foi considerada;
- existem critérios para avaliar o resultado.

`Ready de UX/UI` não significa `Ready for Code`.

---

## 36. Definition of Done de UX/UI

Uma tela ou fluxo pode ser considerado concluído no nível de UX/UI quando, conforme aplicável:

- a tarefa mental é compreensível;
- a ação dominante é reconhecível sem explicação adicional;
- não existe conteúdo ou ação duplicada sem justificativa;
- a superfície escolhida corresponde ao peso da tarefa e do risco;
- loading, vazio, erro, sucesso e recuperação foram definidos;
- offline/sync/conflito foram especificados quando relevantes;
- contratos de produto foram preservados;
- acessibilidade foi validada no nível esperado;
- gesto possui alternativa quando necessário;
- foco, teclado, toque e texto ampliado foram considerados;
- ação fixa não encobre conteúdo essencial;
- microcopy não expõe jargão interno;
- tokens/componentes do Design System são reutilizados quando existentes;
- exceções estão registradas;
- evidência de usabilidade ou revisão humana existe;
- owner apropriado validou o comportamento esperado.

A Definition of Done técnica pertence às camadas posteriores.

---

## 37. Evidência de UX/UI

Uma decisão de interface importante deve ser sustentada por evidência proporcional ao risco.

Pode incluir:

- walkthrough humano;
- teste moderado;
- teste não moderado;
- protótipo;
- comparação antes/depois;
- gravação de sessão autorizada;
- acessibilidade automatizada e manual;
- captura em viewport real;
- teste com teclado;
- teste com leitor de tela;
- métrica comportamental;
- feedback qualitativo;
- análise de suporte;
- experimento controlado.

Uma imagem bonita isolada não prova usabilidade.

---

## 38. Exceções

Princípios orientam decisões, mas não substituem julgamento.

Uma exceção é permitida quando registra:

- princípio afetado;
- contexto;
- alternativa considerada;
- motivo da exceção;
- risco;
- owner;
- duração, quando temporária;
- evidência esperada;
- critério para revisar a decisão.

Repetir a mesma exceção várias vezes é sinal de que o princípio ou o Design System precisa ser revisitado.

---

## 39. Anti-padrões

### Copiar concorrente

Reproduzir layout ou comportamento porque outro produto utiliza.

### Resolver ambiguidade com tutorial

Adicionar explicação longa em vez de corrigir hierarquia.

### Tudo vira modal

Usar dialog para qualquer interação porque é fácil tecnicamente.

### Tudo vira nova tela

Quebrar contexto sem necessidade.

### Tudo fica na mesma tela

Comprimir tarefas independentes em uma superfície excessivamente densa.

### Muitas ações primárias

Dar o mesmo peso visual para ações concorrentes.

### Gesto sem alternativa

Depender de swipe, long press ou gesto oculto para função essencial.

### Cor como único estado

Comunicar erro, sucesso ou seleção apenas por cor.

### Estado técnico invisível

Tratar salvamento local, sincronização e sucesso remoto como a mesma coisa quando isso importa.

### Privacidade decorativa

Ter política de privacidade, mas expor dado desnecessário em interfaces.

### Redesenho destrutivo

Trocar UX e, junto, alterar contratos, backend ou regras sem decisão canônica.

### Design System como catálogo

Criar dezenas de variantes sem comportamento compartilhado.

### Responsive por encolhimento

Apenas reduzir a largura de desktop até caber no mobile.

### Referência como autoridade

Deixar um screenshot externo contradizer produto, permissão ou regra de negócio.

---

## 40. Quality Gate dos Princípios de UX/UI

Antes de canonizar o documento do projeto, verificar:

- Briefing e Visão de PO foram consumidos;
- princípios derivam do contexto real do produto;
- princípios não antecipam tecnologia concreta;
- existe regra de ação dominante;
- existe critério de mudança de superfície;
- existe matriz ou heurística de escolha de superfície;
- estados e feedback estão contemplados;
- prevenção e recuperação estão contempladas;
- acessibilidade está integrada;
- privacidade está integrada;
- referências externas são tratadas como aprendizado, não verdade;
- há contrato para greenfield e brownfield;
- redesenhos protegem decisões canônicas;
- exceções possuem governança;
- Design System e UX conseguem consumir a constituição sem adivinhar seus limites.

---

## 41. Processo de revisão humana

A primeira versão dos princípios deve ser apresentada ao humano antes da canonização.

Revisar especialmente:

- contexto real de uso;
- tolerância a densidade;
- linguagem;
- filosofia de interação;
- ações críticas;
- comportamento mobile/desktop;
- acessibilidade alvo;
- dados sensíveis;
- referências que realmente representam o produto;
- padrões explicitamente rejeitados.

Depois da aprovação, o humano autoriza:

```text
Os Princípios de UX/UI estão aprovados.
Gere o Principios_de_UX_UI.md e salve no projeto.
```

Mudanças posteriores relevantes devem incrementar versão e registrar motivo.

---

## 42. Estrutura esperada do artefato de projeto

A saída canônica do projeto deve ser:

```text
Principios_de_UX_UI.md
```

Estrutura mínima recomendada:

```text
# Princípios de UX/UI

## Contexto de uso
## Autoridade e precedência
## Princípios canônicos
## Protocolo antes de desenhar
## Matriz de superfícies
## Hierarquia de ações
## Feedback e estados
## Conteúdo e microcopy
## Acessibilidade
## Privacidade
## Relação com Design System
## Relação com Especificação de UX
## Preservação em redesenhos
## Contrato mínimo de tela
## Definition of Ready
## Definition of Done
## Exceções
## Referências
```

Nem todo projeto precisa do mesmo volume textual.

O que não pode faltar é a capacidade de orientar decisões reais.

---

## 43. Handoff para Direção de UI e Design System

A etapa está pronta para entregar à Direção de UI quando existe clareza suficiente sobre:

```text
CONTEXTO DE USO
        ↓
PRINCÍPIOS DE INTERAÇÃO
        ↓
AÇÃO DOMINANTE
        ↓
CARGA COGNITIVA
        ↓
SUPERFÍCIES
        ↓
ESTADOS / FEEDBACK
        ↓
ACESSIBILIDADE
        ↓
PRIVACIDADE
        ↓
CONSISTÊNCIA
        ↓
EXCEÇÕES
```

A Direção de UI deve então responder:

> **Como materializar visualmente essa constituição em uma linguagem própria, coerente e reutilizável?**

---

## 44. Gate para avançar

Pode avançar para `04_Direcao_de_UI_e_Design_System.md` quando:

- o documento foi revisado pelo humano;
- conflitos com o PO foram reconciliados;
- princípios estão claros e testáveis como critérios de decisão;
- não existem escolhas prematuras de framework ou biblioteca;
- a matriz de superfícies é compreensível;
- acessibilidade e privacidade estão integradas;
- greenfield e redesenho estão contemplados quando aplicáveis;
- exceções possuem governança;
- `Principios_de_UX_UI.md` foi canonizado no projeto.

---

## 45. Referências metodológicas herdadas do caso DayGym

O documento real que originou esta etapa utilizou, entre outras, referências como:

- publicações do time de design do Nubank sobre princípios e processo;
- Apple Human Interface Guidelines para sheets, alerts e action sheets;
- Android Developers para bottom sheets;
- WCAG 2.2 para foco e tamanho de alvo.

Essas fontes demonstram uma prática de pesquisa, não uma lista fixa obrigatória para todos os projetos.

Cada projeto deve pesquisar as fontes oficiais e atuais das plataformas que realmente utilizará.

---

## 46. Regra final

> **A interface não deve obrigar a pessoa a entender a complexidade do sistema para conseguir realizar a própria tarefa. Os princípios de UX/UI existem para manter a próxima decisão clara, o estado confiável, a ação proporcional ao risco e o produto fiel ao que foi aprovado — mesmo quando telas, dispositivos e tecnologias mudarem.**

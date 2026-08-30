---
document_id: PROCESS-00-DISCOVERY
title: Discovery
status: draft-methodology
version: 0.1.0
stage: discovery
produces: 00_Discovery.md
next_stage: Pesquisa e Viabilidade
---

# 00 — Discovery

## 1. Propósito

O **Discovery** é a primeira etapa operacional do Processo de Desenvolvimento de Software com IA Assistida.

Sua função é transformar uma ideia ainda informal, incompleta ou contraditória em **contexto de produto suficientemente compreensível para que a Pesquisa e Viabilidade possa investigar o mundo real sem precisar adivinhar o que o usuário quis criar**.

O Discovery acontece principalmente por conversa entre humano e ChatGPT.

Ele não existe para produzir uma especificação completa, escolher stack, definir arquitetura ou provar que a ideia é viável. Ele existe para compreender a intenção antes de pesquisá-la e formalizá-la nas camadas seguintes.

A pergunta central desta etapa é:

> **O que estamos tentando criar, para quem, por quê, em qual contexto e quais partes ainda são apenas hipóteses?**

---

## 2. Posição no processo

```text
IDEIA / PROBLEMA / OPORTUNIDADE
        ↓
ATIVAÇÃO DO PROCESSO
        ↓
DISCOVERY
        ↓
00_Discovery.md
        ↓
PESQUISA E VIABILIDADE
```

O Discovery é anterior ao Documento 01 — Pesquisa e Viabilidade.

Na experiência original do DayGym, a Pesquisa e Viabilidade foi registrada como investigação pré-Briefing e já continha análise de mercado, riscos, UX, viabilidade técnica, concorrentes e hipóteses. Nesta metodologia, o Discovery passa a ser formalizado como a camada anterior que fornece a essa investigação uma descrição clara da intenção, do problema, do público, das hipóteses e das perguntas que precisam ser validadas.

---

## 3. Como acionar o Discovery

O usuário pode iniciar uma nova conversa ou utilizar uma conversa em que a ideia já vinha sendo discutida.

O comando recomendado é:

```text
Vamos utilizar o Processo de Desenvolvimento de Software com IA Assistida:
https://github.com/jukazilli/processo-de-desenvolvimento-de-software-com-ia-assistida

Quero começar o Discovery.
A ideia é: <descreva sua ideia inicial>.
```

Exemplo:

```text
Vamos utilizar o Processo de Desenvolvimento de Software com IA Assistida:
https://github.com/jukazilli/processo-de-desenvolvimento-de-software-com-ia-assistida

Quero começar o Discovery.
A ideia é criar uma comunidade em que pessoas possam publicar golpes que descobriram,
explicar como eles funcionam e acompanhar novos golpes relatados por outras pessoas.
```

A ideia inicial não precisa estar organizada como requisito.

Ela pode ser curta, conter dúvidas ou até misturar várias possibilidades. Organizar esse material é parte da responsabilidade do Discovery.

---

## 4. Bootstrap obrigatório do ChatGPT

Ao receber a solicitação de utilizar o processo, o ChatGPT deve primeiro carregar a metodologia indicada pelo usuário.

Antes de conduzir o Discovery, deve:

1. acessar a fonte canônica informada;
2. ler integralmente a versão disponível do processo;
3. identificar, quando possível, repositório, branch e commit consumidos;
4. localizar este documento de Discovery;
5. compreender qual é a responsabilidade desta etapa e qual será sua saída;
6. considerar a conversa anterior como matéria-prima quando ela fizer parte da mesma ideia;
7. não iniciar Pesquisa e Viabilidade, arquitetura, stack ou implementação antes da hora;
8. não gerar automaticamente o documento final apenas porque o processo foi ativado.

Quando a leitura estiver concluída, a IA pode confirmar de forma curta:

```text
PROCESS_STATUS: ACTIVE
CURRENT_STAGE: DISCOVERY
PROCESS_SOURCE: <repositório>
PROCESS_COMMIT: <sha, quando disponível>
DISCOVERY_STATUS: IN_PROGRESS
NEXT_CANONICAL_ARTIFACT: 00_Discovery.md
```

Esse handshake não substitui o Discovery; apenas confirma que a metodologia foi carregada.

---

## 5. Como o usuário deve participar

O Discovery deve parecer uma **conversa de produto guiada**, não um formulário burocrático.

O usuário pode falar naturalmente, por exemplo:

```text
"Hoje isso acontece pelo WhatsApp e fica tudo perdido."

"Eu imaginei que o gestor também pudesse acompanhar."

"Não sei ainda se vamos cobrar assinatura."

"Isso eu não quero no primeiro lançamento."

"E se adicionarmos X?"

"Pensando melhor, Y não faz sentido."
```

Durante a conversa, o usuário deve:

- explicar o problema ou oportunidade que percebeu;
- descrever situações reais que motivaram a ideia;
- contar como o problema é resolvido hoje, quando souber;
- explicar quem imagina usando a solução;
- corrigir interpretações da IA;
- explorar alternativas sem precisar tratá-las como decisões;
- informar restrições conhecidas;
- dizer quando algo é apenas uma ideia futura;
- rejeitar caminhos que não representam sua intenção;
- pedir aprofundamento quando uma pergunta revelar algo importante.

O usuário não precisa conhecer linguagem de produto, UX, engenharia ou arquitetura.

O ChatGPT deve traduzir a conversa para estrutura sem exigir que o humano pense como analista de requisitos.

---

## 6. Responsabilidade do ChatGPT durante o Discovery

O ChatGPT atua como facilitador de descoberta.

Ele deve:

- ouvir e reconstruir a intenção do usuário;
- fazer perguntas que reduzam ambiguidades relevantes;
- desafiar premissas sem tomar a decisão pelo humano;
- identificar contradições;
- diferenciar necessidade de solução imaginada;
- explorar cenários de uso;
- ajudar a separar o núcleo da ideia de extensões futuras;
- registrar mentalmente o que já foi decidido, o que é hipótese, o que está pendente e o que foi descartado;
- perceber quando uma informação exige pesquisa posterior em vez de resposta intuitiva;
- resumir periodicamente o entendimento quando isso reduzir risco de interpretação errada;
- manter a conversa proporcional à complexidade do produto.

O ChatGPT não deve transformar cada frase do usuário em requisito definitivo.

---

## 7. O que deve ser descoberto

O Discovery não precisa seguir uma entrevista rígida na ordem abaixo. Esses tópicos funcionam como **cobertura mínima de entendimento**.

### 7.1. Origem da ideia

Entender:

- o que motivou a ideia;
- se nasceu de experiência própria, observação, cliente, operação existente ou oportunidade percebida;
- qual situação fez o usuário acreditar que vale a pena criar alguma coisa.

### 7.2. Problema ou oportunidade

Compreender:

- qual problema parece existir;
- quem sente esse problema;
- quando ele ocorre;
- como ele é enfrentado hoje;
- qual consequência o usuário espera reduzir ou qual oportunidade espera capturar.

A IA deve evitar aceitar imediatamente uma solução proposta como prova de que o problema existe.

### 7.3. Usuários e stakeholders imaginados

Identificar, quando aplicável:

- usuário principal;
- usuários secundários;
- administrador;
- comprador ou decisor;
- operador interno;
- profissional ou parceiro externo;
- pessoas afetadas mesmo que não utilizem diretamente a aplicação.

Esses perfis ainda podem ser hipóteses. A Pesquisa e Viabilidade poderá confirmá-los, refiná-los ou rejeitá-los.

### 7.4. Situações de uso

Explorar exemplos concretos:

```text
Quando acontece X,
a pessoa precisa fazer Y,
porque deseja alcançar Z.
```

O objetivo é compreender comportamento e contexto antes de desenhar telas.

### 7.5. Valor esperado

Perguntar o que faria a solução valer a pena.

Exemplos:

- economizar tempo;
- reduzir erro;
- aumentar segurança;
- melhorar comunicação;
- organizar informação;
- permitir acompanhamento;
- gerar receita;
- reduzir custo;
- criar comunidade;
- dar visibilidade a um problema.

### 7.6. Escopo mental inicial

Separar:

- o que parece central para a ideia;
- o que é complementar;
- o que é uma possibilidade futura;
- o que o usuário explicitamente não deseja.

Isso não substitui o Briefing de Produto. É apenas uma primeira fronteira para impedir que a Pesquisa e Viabilidade investigue um produto diferente do que está sendo imaginado.

### 7.7. Regras ou necessidades já conhecidas

Registrar necessidades que o usuário já considera importantes, sem antecipar sua especificação detalhada.

Exemplo:

```text
"Empresas diferentes não podem ver dados umas das outras."
```

é uma necessidade válida de Discovery.

Já decidir como isso será implementado pertence a etapas posteriores.

### 7.8. Restrições conhecidas

Podem aparecer restrições como:

- orçamento;
- prazo;
- equipe;
- plataforma desejada;
- país ou idioma;
- necessidade de integração;
- restrição regulatória já conhecida;
- necessidade de operar offline;
- existência de sistema legado;
- dependência de dados ou parceiros;
- decisão empresarial que não está aberta para discussão.

No Discovery, essas restrições são registradas. Sua validade e impacto podem ser avaliados nas etapas adequadas.

### 7.9. Ativos e referências existentes

Registrar se já existem:

- planilhas;
- PDFs;
- sistemas legados;
- screenshots;
- protótipos;
- fluxos manuais;
- banco de dados;
- APIs;
- contratos;
- documentos internos;
- aplicativos ou produtos usados como referência.

A existência desses materiais deve ser entregue à Pesquisa e Viabilidade para análise quando forem relevantes.

### 7.10. Hipóteses

Toda afirmação ainda não comprovada deve permanecer claramente como hipótese.

Exemplos:

```text
"Acho que as pessoas pagariam por isso."

"Provavelmente profissionais vão querer participar."

"Talvez a comunidade seja o principal motivo de retenção."
```

O objetivo não é eliminar hipóteses no Discovery. É **torná-las visíveis para que a Pesquisa e Viabilidade saiba o que precisa validar**.

### 7.11. Pendências

Nem tudo precisa ser decidido antes de avançar.

Uma questão pode permanecer pendente quando:

- depende de pesquisa externa;
- depende de validação com usuário;
- não é necessária para compreender a tese inicial;
- a decisão pertence claramente a uma etapa posterior.

Pendência explícita é melhor do que certeza inventada.

### 7.12. Ideias descartadas

Quando o usuário rejeitar conscientemente uma alternativa relevante, registrar essa decisão.

Isso evita que a mesma ideia reapareça como se nunca tivesse sido discutida.

---

## 8. Classificação obrigatória do conhecimento

Durante o Discovery, o ChatGPT deve conseguir separar o material em quatro estados:

| Estado | Significado |
| --- | --- |
| **Decidido** | o humano confirmou que aquela interpretação representa sua intenção atual |
| **Hipótese** | parece plausível, mas precisa ser pesquisada, testada ou validada |
| **Pendente** | ainda não há informação ou decisão suficiente |
| **Descartado** | alternativa discutida e conscientemente rejeitada |

A classificação não precisa aparecer após cada mensagem.

Ela deve aparecer de forma explícita na síntese de encerramento e no documento canônico.

---

## 9. Discovery não é Pesquisa e Viabilidade

Essa fronteira é obrigatória.

O Discovery pode identificar perguntas como:

```text
"Já existe algo assim?"
"Esse mercado é grande?"
"As pessoas realmente têm essa dor?"
"Essa integração é tecnicamente possível?"
"Existe risco regulatório?"
```

Mas essas perguntas devem se transformar principalmente em **agenda de investigação** para a etapa seguinte.

O Discovery não deve realizar uma pesquisa extensa de:

- mercado;
- concorrentes;
- tendências;
- tamanho de categoria;
- benchmarks;
- legislação;
- APIs e provedores;
- preços de infraestrutura;
- frameworks;
- arquitetura;
- stack;
- segurança técnica detalhada.

Uma consulta pontual pode ser usada para esclarecer um termo ou evitar que a conversa se baseie em um fato claramente incorreto, mas ela não transforma o Discovery em estudo de viabilidade.

A etapa seguinte existe justamente para confrontar a intenção descoberta com evidências externas.

---

## 10. O que não deve ser decidido nesta etapa

Salvo quando alguma escolha já for uma restrição humana explícita, o Discovery não deve escolher:

- framework;
- linguagem de programação;
- banco de dados;
- cloud provider;
- arquitetura;
- monorepo ou polyrepo;
- bibliotecas;
- padrão de API;
- design system definitivo;
- estrutura completa de telas;
- backlog de implementação;
- modelo de dados;
- estratégia detalhada de CI/CD.

Também não deve criar código de produção.

Essas decisões precisam de contexto que ainda será formado pelas etapas seguintes.

---

## 11. Forma de condução recomendada

O ChatGPT deve evitar duas falhas opostas:

```text
INTERROGATÓRIO EXAUSTIVO
        ×
CONVERSA SOLTA SEM CONVERGÊNCIA
```

O comportamento recomendado é iterativo:

```text
usuário apresenta contexto
        ↓
IA interpreta
        ↓
IA faz poucas perguntas relevantes
        ↓
usuário responde e adiciona ideias
        ↓
IA confronta ou aprofunda pontos importantes
        ↓
entendimento evolui
        ↓
síntese parcial quando necessário
        ↓
novas lacunas são exploradas
```

Preferir perguntas que alterariam de forma material a compreensão do produto.

Perguntas de detalhe que pertencem a UX, arquitetura ou implementação devem ser adiadas quando não forem necessárias para o Discovery.

---

## 12. Exemplo resumido de Discovery

### Usuário

```text
Quero criar um site onde pessoas possam avisar umas às outras sobre golpes.
Eu descobri um golpe do Pix, publico lá, e outras pessoas ficam sabendo.
```

### ChatGPT

Em vez de partir para stack ou telas, o ChatGPT pode investigar:

```text
Você imagina isso principalmente como uma base pesquisável de golpes,
como uma comunidade que publica relatos, ou as duas coisas?

Quem você imagina contribuindo: qualquer pessoa, especialistas,
empresas ou órgãos verificados?

Quando alguém entra na plataforma, qual seria o valor principal:
descobrir se uma mensagem que recebeu é golpe, acompanhar golpes novos,
ou compartilhar algo que aconteceu com ela?
```

### Usuário

```text
As duas coisas. Quero que qualquer pessoa publique,
mas no futuro poderia ter especialistas verificando.
O principal seria ficar informado e poder pesquisar algo suspeito.
```

### ChatGPT

A conversa então pode explorar:

- confiança e verificação como hipótese;
- moderação como risco a investigar;
- busca e acompanhamento como necessidades centrais;
- especialistas como evolução, não requisito já aprovado;
- possibilidade de conteúdo malicioso como pergunta para Pesquisa e Viabilidade.

O Discovery continua até existir contexto suficiente para formular a investigação seguinte.

---

## 13. Critério de suficiência — Discovery Readiness

Discovery suficiente **não significa produto completamente definido**.

Ele está pronto para encerrar quando o ChatGPT consegue responder, sem inventar:

1. qual é a ideia ou tese inicial;
2. qual problema ou oportunidade a motivou;
3. quem são os usuários/stakeholders inicialmente imaginados;
4. quais são os principais contextos ou situações de uso;
5. qual valor o produto pretende gerar;
6. quais capacidades o usuário considera centrais neste momento;
7. quais limites preliminares já foram estabelecidos;
8. quais restrições conhecidas precisam ser consideradas;
9. quais hipóteses precisam de validação;
10. quais perguntas devem ser investigadas na Pesquisa e Viabilidade;
11. quais alternativas relevantes foram descartadas;
12. quais decisões ainda podem permanecer pendentes sem impedir a pesquisa.

Estados recomendados:

```text
DISCOVERY_READINESS: INSUFFICIENT
DISCOVERY_READINESS: SUFFICIENT_WITH_OPEN_QUESTIONS
DISCOVERY_READINESS: SUFFICIENT
```

`SUFFICIENT_WITH_OPEN_QUESTIONS` é um estado válido e provavelmente comum.

O processo não exige certeza artificial para avançar.

---

## 14. Encerramento antes da canonização

Quando considerar o Discovery suficiente, o ChatGPT **não deve criar o arquivo imediatamente**.

Primeiro deve apresentar no chat uma síntese estruturada para revisão humana.

A síntese deve conter pelo menos:

```text
IDEIA / TESE ATUAL
PROBLEMA / OPORTUNIDADE
USUÁRIOS E STAKEHOLDERS
CENÁRIOS DE USO
VALOR ESPERADO
CAPACIDADES CENTRAIS
LIMITES PRELIMINARES
RESTRIÇÕES CONHECIDAS
DECIDIDO
HIPÓTESES
PENDÊNCIAS
DESCARTADO
ATIVOS / REFERÊNCIAS
PERGUNTAS PARA PESQUISA E VIABILIDADE
DISCOVERY_READINESS
```

O humano lê e pode:

- corrigir;
- complementar;
- rejeitar interpretações;
- reabrir um ponto;
- aprovar o conteúdo.

---

## 15. Aprovação e canonização

O processo distingue:

```text
APROVAÇÃO DO CONTEÚDO
        ↓
AUTORIZAÇÃO PARA GERAR O DOCUMENTO
```

Exemplo:

```text
Usuário:
"Agora entendeu corretamente."

→ conteúdo aprovado, mas ainda pode permanecer apenas no chat.

Usuário:
"Pode gerar o Documento de Discovery e salvar no projeto."

→ canonização autorizada.
```

Se a intenção do usuário for inequívoca, aprovação e geração podem acontecer na mesma mensagem.

Em caso de dúvida, a IA deve preservar a síntese no chat e perguntar antes de escrever em um repositório ou destino persistente.

---

## 16. Saída canônica do Discovery

O artefato produzido para o **projeto que está sendo desenvolvido** deve ser:

```text
00_Discovery.md
```

Esse arquivo não é este documento metodológico.

Este arquivo (`docs/processo/00_Discovery.md`) explica **como executar a etapa**.

O `00_Discovery.md` criado dentro de cada projeto registra **o resultado do Discovery daquele produto**.

---

## 17. Estrutura mínima de `00_Discovery.md`

O documento de projeto deve permanecer legível por humano e por IA e conter, quando aplicável:

```markdown
---
document_id: DOC-00
title: Discovery
status: canonical
version: 1.0.0
next_document: 01_Pesquisa_e_Viabilidade.md
---

# Discovery

## 1. Contexto e origem da ideia

## 2. Problema ou oportunidade percebida

## 3. Tese inicial do produto

## 4. Usuários e stakeholders imaginados

## 5. Situações de uso conhecidas

## 6. Valor e outcomes esperados

## 7. Capacidades centrais imaginadas

## 8. Limites preliminares e não objetivos

## 9. Restrições conhecidas

## 10. Ativos, referências e processos existentes

## 11. Decisões confirmadas

## 12. Hipóteses a validar

## 13. Pendências

## 14. Alternativas descartadas

## 15. Ideias futuras não comprometidas

## 16. Perguntas para Pesquisa e Viabilidade

## 17. Discovery Readiness e handoff
```

A estrutura pode ser adaptada ao produto, desde que não misture hipóteses com decisões e preserve informação suficiente para a etapa seguinte.

---

## 18. Contrato de handoff para Pesquisa e Viabilidade

A Pesquisa e Viabilidade deve iniciar consumindo integralmente `00_Discovery.md`.

Ela não deve receber o Discovery como conjunto de verdades comprovadas.

Deve interpretar:

```text
DECIDIDO
→ intenção atual do produto

HIPÓTESE
→ algo a investigar ou validar

PENDENTE
→ lacuna a resolver quando a evidência permitir

DESCARTADO
→ alternativa que não deve reaparecer sem nova justificativa

ATIVOS / REFERÊNCIAS
→ materiais que podem precisar de análise

PERGUNTAS DE PESQUISA
→ agenda inicial de investigação
```

A próxima etapa deverá então confrontar essa matéria-prima com evidências externas, referências, concorrentes, riscos e viabilidade aplicável ao caso.

O resultado da Pesquisa e Viabilidade pode confirmar, refinar ou enfraquecer hipóteses do Discovery.

Se encontrar evidência que contradiga uma decisão humana de intenção, a pesquisa deve expor a tensão; não deve reescrever silenciosamente o Discovery.

---

## 19. Gate para avançar

A etapa Discovery pode ser considerada concluída quando:

- a síntese foi apresentada no chat;
- o humano teve oportunidade real de revisar;
- correções relevantes foram incorporadas;
- o conteúdo foi aprovado;
- a canonização foi autorizada;
- `00_Discovery.md` foi criado ou atualizado no destino definido;
- o documento diferencia decisões, hipóteses, pendências e descartes;
- existe uma agenda clara para Pesquisa e Viabilidade.

Somente então o próximo passo se torna elegível:

```text
01 — Pesquisa e Viabilidade
```

---

## 20. Regra final da etapa

> **Discovery não prova que a ideia é boa. Discovery garante que sabemos qual ideia estamos prestes a investigar.**

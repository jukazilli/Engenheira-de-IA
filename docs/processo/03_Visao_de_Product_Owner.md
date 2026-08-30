---
document_id: PROCESS-03-VISAO-PO
title: Visão de Product Owner
status: draft-methodology
version: 0.1.0
stage: visao-product-owner
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
produces: 03_Visao_de_Product_Owner.md
next_stage: Principios_de_UX_UI.md
---

# 03 — Visão de Product Owner

## 1. Propósito

A **Visão de Product Owner** é a quarta etapa operacional do Processo de Desenvolvimento de Software com IA Assistida.

Sua função é transformar o produto e o escopo aprovados no Briefing em uma **visão executável de produto**, capaz de orientar design, UX, engenharia e as etapas posteriores sem obrigá-las a reinterpretar prioridade, resultado esperado, regra de negócio ou critério de sucesso.

A pergunta central desta etapa é:

> **Como transformar o produto aprovado em outcomes, comportamentos, regras, hipóteses, prioridades, histórias e critérios de aceite que possam ser desenhados, mensurados e posteriormente implementados sem perder a intenção do produto?**

O Product Owner não existe para produzir a maior quantidade possível de funcionalidades.

Ele protege o problema central, ordena o aprendizado, traduz escopo em comportamento verificável e define como o produto saberá se uma entrega realmente gerou valor.

A saída desta etapa ainda **não autoriza código**.

---

## 2. Posição no processo

```text
00_Discovery.md
        ↓
01_Pesquisa_e_Viabilidade.md
        ↓
02_Briefing_de_Produto_e_Escopo.md
        ↓
03_VISÃO_DE_PRODUCT_OWNER
        ↓
PRINCÍPIOS DE UX E UI
        ↓
DIREÇÃO DE UI / DESIGN SYSTEM
        ↓
ESPECIFICAÇÃO DE UX
        ↓
CAMADAS TÉCNICAS POSTERIORES
```

O Briefing fixa **qual produto será construído neste horizonte**.

A Visão de Product Owner transforma esse contrato em **resultado, comportamento e entrega funcional priorizada**.

As etapas de UX/UI decidirão como essa intenção será percebida e operada pelo usuário.

As etapas técnicas posteriores decidirão como o sistema será estruturado, quais tecnologias materializarão essa estrutura e como ele será executado e operado.

---

## 3. Origem desta etapa

Esta metodologia foi extraída do processo real utilizado no DayGym.

Na documentação original, a Visão de Product Owner foi definida como uma **visão executável de produto**, derivada do Briefing aprovado e destinada a orientar UI, UX, engenharia e implementação por IA, embora o código ainda não estivesse autorizado.

O documento real introduziu uma separação especialmente importante:

```text
RESULTADO
→ que mudança importa para usuário e negócio?

COMPORTAMENTO
→ que ação demonstra que o valor aconteceu?

ENTREGA
→ o que habilita esse comportamento?
```

Essa separação passa a ser um princípio da metodologia.

Uma entrega funcional não deve ser confundida com sucesso apenas porque foi construída ou publicada.

---

## 4. Pré-requisitos obrigatórios

Antes de iniciar esta etapa, o ChatGPT deve consumir integralmente:

1. `00_Discovery.md`;
2. `01_Pesquisa_e_Viabilidade.md`;
3. `02_Briefing_de_Produto_e_Escopo.md`.

O Briefing é a principal fonte canônica de escopo desta etapa.

O Discovery e a Pesquisa permanecem necessários para recuperar contexto, hipóteses, evidências e motivos que explicam as decisões do Briefing.

Antes de produzir qualquer nova definição, o ChatGPT deve verificar:

- se a definição do produto está clara;
- se público e horizonte estão definidos;
- se existe promessa ou proposta de valor aprovada;
- se o core loop está reconhecível;
- se P0/P1/P2 ou classificação equivalente está consistente;
- se existe fora de escopo explícito;
- se riscos e dependências críticas estão registrados;
- se há decisões do Briefing ainda marcadas como pendentes;
- se existe alguma contradição material entre Briefing, Pesquisa e Discovery.

Contradições não devem ser resolvidas silenciosamente dentro da Visão de PO.

---

## 5. Mandato do Product Owner nesta metodologia

O Product Owner deve:

- proteger o problema central;
- proteger o Product Scope Freeze definido no Briefing;
- ordenar aprendizado antes de quantidade de entrega;
- identificar quem recebe valor;
- definir outcomes mensuráveis;
- conectar outcomes a comportamentos observáveis;
- decompor o escopo em capacidades, épicos e histórias no nível de produto;
- explicitar regras de negócio vinculantes;
- definir critérios de aceite funcionais e de negócio;
- definir hipóteses e condições de retirada;
- organizar ondas ou estágios de liberação quando necessário;
- definir métricas e guardrails de produto;
- registrar gates e owners de decisão;
- manter decisões removidas rastreáveis;
- impedir expansão silenciosa de escopo;
- preparar um handoff que permita a UX/UI trabalhar sem inventar prioridade ou regra.

O Product Owner não deve maximizar quantidade de telas, histórias ou funcionalidades como objetivo em si.

---

## 6. O que esta etapa pode e não pode canonizar

### 6.1. Pode canonizar

A Visão de PO pode canonizar:

- visão operacional do produto;
- missão do horizonte atual;
- escolhas estratégicas já compatíveis com o Briefing;
- personas comportamentais;
- Jobs to be Done;
- anti-personas quando úteis;
- outcome tree;
- North Star;
- scorecard inicial;
- guardrails;
- hipóteses de produto;
- condições de retirada;
- ordem de aprendizado;
- jornadas no nível de intenção e sucesso;
- loops de valor;
- regras de negócio;
- capacidades, épicos e histórias de produto;
- prioridade funcional;
- critérios de aceite de produto;
- ondas de liberação;
- gates de produto e operação;
- decisão GO / GO LIMITADO / HOLD / PIVOT / KILL;
- experimentos necessários;
- requisitos semânticos de instrumentação;
- Definition of Ready de produto;
- Definition of Done de produto;
- política de mudança;
- riscos e dependências sob governança de produto.

### 6.2. Não pode canonizar

A Visão de PO não deve decidir prematuramente:

- wireframes finais;
- layout visual;
- design system;
- tokens;
- microinterações detalhadas;
- conteúdo final de interface;
- estrutura de componentes;
- arquitetura de software;
- boundaries técnicos definitivos;
- banco de dados concreto;
- linguagem de programação;
- runtime;
- framework;
- biblioteca;
- provider de nuvem;
- estratégia concreta de CI/CD;
- topologia de infraestrutura;
- ferramenta de observabilidade;
- estrutura definitiva do repositório;
- plano de implementação do Codex.

Quando um comportamento exige uma propriedade técnica, o PO descreve **o que precisa ser verdade**, não qual tecnologia deve ser usada.

Exemplo:

```text
CORRETO NO PO
“O usuário precisa continuar registrando a tarefa crítica quando a rede estiver instável e receber confirmação local imediata.”

INCORRETO NO PO
“Usar biblioteca X com banco Y e mecanismo Z de sincronização.”
```

---

## 7. Resultado, comportamento e entrega

Toda capacidade relevante deve poder ser explicada em três níveis.

| Nível | Pergunta |
| --- | --- |
| Resultado | Que mudança importa para usuário ou negócio? |
| Comportamento | Que ação observável demonstra essa mudança? |
| Entrega | Que capacidade do produto habilita esse comportamento? |

A sequência correta é:

```text
OUTCOME
        ↓
COMPORTAMENTO DE VALOR
        ↓
CAPACIDADE / ENTREGA
```

O caminho inverso cria backlog orientado a feature:

```text
“vamos construir X”
        ↓
“depois vemos se foi útil”
```

Essa lógica deve ser evitada.

---

## 8. Visão operacional e missão do horizonte

A etapa deve produzir uma visão curta o suficiente para orientar decisões.

Ela deve responder:

- qual transformação o produto pretende gerar;
- para quem;
- em qual contexto;
- com qual diferenciação;
- sem quais concessões o produto perderia identidade.

Também deve definir a missão do horizonte atual.

Uma missão de beta, por exemplo, não deve ser “implementar todos os módulos P0”.

Deve ser formulada em termos de aprendizado e valor, como:

```text
provar que o usuário consegue obter valor central
+
medir o comportamento esperado
+
validar módulos adjacentes sem prejudicar o core
```

---

## 9. Escolhas estratégicas e princípios inegociáveis

Quando o Briefing possuir escolhas estruturais de produto, o PO deve transformá-las em regras operacionais.

Exemplo de estrutura:

| Escolha | Decisão | Implicação operacional |
| --- | --- | --- |
| Core | qual loop domina | módulos secundários não podem bloqueá-lo |
| Mercado | público inicial | critérios e linguagem devem servir esse recorte |
| Social | forma de interação | liberação depende de controles específicos |
| Receita | hipótese de monetização | não pode violar guardrails de produto |
| Diferenciação | atributo central | decisões posteriores devem preservá-lo |

Princípios inegociáveis devem ser escritos como comportamento verificável.

Exemplo:

```text
PRINCÍPIO
“sem automação silenciosa”

REGRA OPERACIONAL
“ações que alteram estado relevante exigem confirmação ou autoria explícita.”
```

---

## 10. Pessoas, contextos e Jobs to be Done

### 10.1. Personas comportamentais

Personas nesta metodologia são instrumentos de priorização, não perfis demográficos inventados.

Devem ser construídas a partir de contexto e comportamento.

Estrutura recomendada:

| Persona | Contexto | Progresso desejado | Maior risco |
| --- | --- | --- | --- |
| U1 | situação recorrente | mudança desejada | o que pode quebrar valor |

A IA não deve inventar renda, gênero, condição de saúde, ocupação ou outras características que não sejam necessárias e sustentadas.

O mesmo usuário real pode atravessar mais de uma persona ao longo do tempo.

### 10.2. Persona primária de decisão

Quando múltiplas personas existirem, o PO deve registrar qual grupo possui precedência quando houver trade-off.

Isso impede que a interface e o escopo tentem otimizar igualmente para todos.

### 10.3. Jobs to be Done

Formato recomendado:

```text
QUANDO <contexto>
QUERO <progresso desejado>
PARA <resultado>
```

O JTBD deve descrever progresso e contexto, não reproduzir uma feature.

### 10.4. Anti-personas e encaminhamento

Anti-personas podem ser registradas quando determinado público:

- está fora do horizonte atual;
- exigiria proteção específica;
- busca um resultado que o produto explicitamente não oferece;
- criaria risco material;
- pertence a outro produto ou fase.

“Anti-persona” não significa usuário indesejado; significa **contexto que o produto atual decidiu não atender**.

---

## 11. Outcome Tree

A Visão de PO deve estruturar outcomes em níveis adequados ao projeto.

Uma árvore típica pode conter:

```text
NEGÓCIO
        ↓
USUÁRIO
        ↓
PRODUTO
        ↓
ECOSSISTEMA / OPERAÇÃO
        ↓
RECEITA, quando aplicável
```

Para cada outcome, registrar uma forma de evidência.

| Nível | Outcome | Evidência esperada |
| --- | --- | --- |
| Usuário | mudança desejada | comportamento ou métrica |
| Produto | redução de atrito/falha | tempo, conclusão, erro |
| Negócio | aprendizado ou sustentabilidade | retenção, conversão, custo |

Outcomes devem ser mensuráveis ou avaliáveis.

---

## 12. North Star

Quando o produto justificar uma North Star, ela deve medir **valor sustentado**, não consumo superficial de interface.

Evitar automaticamente:

- DAU;
- MAU;
- abertura diária;
- quantidade de telas visitadas;
- curtidas;
- notificações abertas;
- tempo gasto no aplicativo;

quando essas métricas não representarem valor real.

A definição deve conter:

- nome;
- fórmula;
- numerador;
- denominador;
- janela temporal;
- critérios de elegibilidade;
- exclusões;
- eventos que não contam;
- limitações da interpretação.

A North Star não deve ser usada isoladamente para declarar product-market fit.

---

## 13. Scorecard de produto

O PO deve definir um scorecard inicial quando houver necessidade de validar múltiplas dimensões.

Estrutura recomendada:

| Área | Definição | Target inicial | Guardrail |
| --- | --- | --- | --- |
| Ativação | comportamento de entrada em valor | hipótese | limite que não pode ser violado |
| Core | valor sustentado | hipótese | segurança/qualidade |
| Fricção | esforço necessário | hipótese | perda/erro |
| Módulo | comportamento esperado | hipótese | não prejudicar core |
| Confiabilidade | qualidade percebida | hipótese | incidente crítico |

Targets iniciais de beta são **hipóteses operacionais**, não verdades estatísticas.

Amostra pequena deve ser acompanhada por pesquisa qualitativa.

---

## 14. Guardrails transversais

Guardrail é um limite que não pode ser sacrificado para melhorar uma métrica.

Exemplos de categorias:

- segurança;
- privacidade;
- integridade;
- confiança;
- acessibilidade;
- moderação;
- comércio;
- carga cognitiva;
- confiabilidade;
- responsabilidade profissional.

Estrutura:

```text
MÉTRICA MELHOROU
        ↓
GUARDRAIL FOI VIOLADO?
        ↓
SIM
        ↓
NÃO É SUCESSO
```

Uma funcionalidade não deve permanecer apenas porque aumenta engajamento se cria dano incompatível com o produto.

---

## 15. Hipóteses de produto e condições de retirada

Cada módulo ou capacidade relevante deve existir por uma hipótese explícita.

Estrutura recomendada:

| ID | Crença testada | Evidência | Condição de retirada |
| --- | --- | --- | --- |
| H-001 | o que acreditamos | como observar | quando reduzir/desligar |

A metodologia deve preservar uma regra importante:

> **Uma feature construída não adquire direito de permanência apenas porque consumiu tempo de desenvolvimento.**

Se a hipótese falhar ou o guardrail for violado, o PO pode:

- manter flag desligada;
- reduzir escopo;
- modificar a hipótese;
- repetir experimento;
- retirar módulo;
- retornar ao Briefing se a mudança for material.

---

## 16. Ordem de aprendizado

A prioridade deve representar principalmente **ordem de aprendizado e redução de risco**, não preferência estética.

Perguntas úteis:

1. qual hipótese, se falsa, invalida maior parte do produto?
2. qual comportamento demonstra o core?
3. qual risco pode impedir lançamento?
4. qual dependência externa possui maior incerteza?
5. qual módulo pode ser validado isoladamente sem contaminar o core?
6. qual evidência precisa existir antes de expandir?

A ordem de aprendizado deve ser registrada antes de detalhar um roadmap extenso.

---

## 17. Jornadas de valor no nível de PO

A Visão de PO pode definir jornadas, mas apenas no nível de intenção, sucesso e recuperação.

Estrutura:

| Jornada | Entrada | Sucesso | Recuperação / limite |
| --- | --- | --- | --- |
| J1 | estado inicial | comportamento concluído | erro, fallback ou limite |

Esta etapa não deve definir:

- wireflow detalhado;
- posição de componentes;
- animações;
- texto final;
- padrão visual;
- comportamento específico de cada modal;
- decisão final de navegação.

Esses detalhes pertencem às etapas de UX/UI.

---

## 18. Loops de valor

Quando o produto possuir ciclos recorrentes, o PO deve registrá-los.

Exemplo:

```text
CORE DIÁRIO
entrada → ação → confirmação → resumo

CORE SEMANAL
histórico → interpretação → decisão → próximo ciclo

LOOP DE COLABORAÇÃO
convite → permissão → ação → revisão
```

O objetivo é permitir que UX, engenharia e métricas enxerguem **ciclos completos**, e não telas isoladas.

---

## 19. Regras de negócio vinculantes

Regras que não podem ser reinterpretadas silenciosamente devem receber IDs estáveis.

Padrão recomendado:

```text
BR-001
BR-002
BR-003
...
```

Estrutura:

| ID | Tema | Regra |
| --- | --- | --- |
| BR-001 | elegibilidade | condição explícita |

Boas regras de negócio são:

- testáveis;
- independentes de layout;
- independentes de framework;
- específicas o suficiente para impedir interpretação incompatível;
- rastreáveis ao Briefing ou evidência anterior.

IDs removidos não devem ser reutilizados para outra regra.

---

## 20. Taxonomia mínima de IDs de produto

Para facilitar rastreabilidade, recomenda-se utilizar IDs estáveis.

```text
OUT-xxx   Outcome
HYP-xxx   Hipótese
BR-xxx    Regra de negócio
J-xxx     Jornada
E-xxx     Épico
US-xxx    História de usuário
G-xxx     Gate
EXP-xxx   Experimento
R-xxx     Risco de produto
```

O prefixo exato pode variar, desde que seja consistente e não reutilize identificadores aposentados.

Esses IDs devem sobreviver às etapas seguintes sempre que a decisão permanecer a mesma.

---

## 21. Baseline de backlog de produto

A Visão de PO deve decompor o P0 e horizontes posteriores em uma **baseline de backlog de produto**.

Essa baseline pode conter:

```text
DOMÍNIO
        ↓
ÉPICO
        ↓
HISTÓRIA / CAPACIDADE
        ↓
OUTCOME
        ↓
PRIORIDADE
        ↓
ONDA / GATE
```

### 21.1. Importante: não é o Backlog Canônico de Entrega

A baseline de PO **não é ainda o backlog técnico final que será executado pelo Codex**.

Ela representa o produto.

Etapas posteriores ainda adicionarão:

- estados de UX;
- acessibilidade detalhada;
- requisitos de engenharia;
- arquitetura;
- decisões tecnológicas;
- infraestrutura;
- testes técnicos;
- dependências de implantação;
- evidências de execução.

Somente depois dessas camadas o processo poderá gerar um backlog de entrega plenamente executável e rastreável.

Portanto:

```text
BACKLOG DE PRODUTO DO PO
= o que precisa entregar valor

BACKLOG CANÔNICO DE ENTREGA
= como a entrega será executada com todas as camadas incorporadas
```

A rastreabilidade entre ambos deve preservar os IDs de produto.

---

## 22. Prioridade de produto

O modelo de prioridade pode ser adaptado ao projeto.

Uma taxonomia útil é:

```text
MUST CORE
→ libera o valor individual essencial

MUST GATE
→ pertence ao horizonte, mas depende de gate antes de ativação

SHOULD
→ importante, mas não necessário ao horizonte atual

COULD
→ oportunidade futura

REMOVIDO
→ existiu, foi deliberadamente retirado e permanece rastreável
```

Prioridade não define peso visual.

Uma feature `Must Gate` pode estar no P0 contratual e ainda permanecer desligada durante parte do beta.

---

## 23. Histórias de usuário e critérios de aceite

Histórias devem representar uma intenção compreensível.

Formato recomendado:

```text
Como <persona/contexto>,
quero <progresso ou capacidade>,
para <resultado>.
```

Cada história relevante deve possuir:

- ID estável;
- épico;
- outcome;
- prioridade;
- hipótese associada, quando aplicável;
- regras de negócio relacionadas;
- critério de aceite funcional;
- estados críticos conhecidos;
- gate ou feature flag quando aplicável.

### 23.1. Critério de aceite de produto

Critério de aceite deve ser verificável.

Evitar:

```text
“a tela deve ser bonita”
“a experiência deve ser boa”
“o sistema deve ser rápido”
```

Preferir:

```text
“o usuário consegue desfazer a ação antes de confirmação definitiva”
“o módulo desligado não bloqueia o fluxo principal”
“a mesma entrada confirmada novamente não duplica o efeito”
```

O PO descreve o resultado observável.

UX e Engenharia ainda adicionarão critérios próprios.

---

## 24. Estados críticos no nível de produto

Uma história não deve considerar apenas o caminho feliz.

O PO deve identificar, quando relevantes:

- vazio;
- erro;
- cancelamento;
- permissão ausente;
- permissão revogada;
- dependência externa indisponível;
- operação parcial;
- conflito;
- repetição;
- reversão;
- bloqueio por segurança;
- feature flag desligada;
- usuário fora de elegibilidade;
- conteúdo removido;
- estado em revisão.

A representação visual desses estados pertence à UX/UI.

---

## 25. Ondas de liberação

Quando um beta ou rollout progressivo for necessário, o PO deve organizar ondas.

Estrutura recomendada:

| Onda | Público | Escopo | Evidência de saída |
| --- | --- | --- | --- |
| 0 | interno | core e riscos fundamentais | fluxo controlado |
| 1 | coorte pequena | core | comportamento e confiabilidade |
| 2 | expansão | colaboração ou módulos adjacentes | gates específicos |

Onda não é sprint.

Uma onda descreve **quem recebe qual risco e qual aprendizado precisa existir antes de ampliar**.

---

## 26. Gates vinculantes

Gates de produto devem conter:

| Campo | Conteúdo |
| --- | --- |
| ID | identificador estável |
| Condição | o que precisa ser verdade |
| Owner | quem responde pela decisão |
| Momento | quando o gate é avaliado |
| Evidência | prova necessária |
| Ação se falhar | HOLD, PIVOT, KILL ou correção |

A decisão por gate pode usar:

```text
GO
GO LIMITADO
HOLD
PIVOT
KILL
```

### GO

Valor e guardrails suficientes para ampliar.

### GO LIMITADO

Sinal de valor existe, mas a amostra ou o risco ainda pede coorte controlada.

### HOLD

Dependência, qualidade ou operação ainda impedem liberação.

### PIVOT

O problema permanece válido, mas hipótese, fluxo ou solução precisa mudar.

### KILL

Risco, custo ou ausência de valor justificam desligar ou retirar a capacidade.

---

## 27. Descoberta contínua e experimentação

Discovery não termina para sempre quando `00_Discovery.md` é criado.

Depois do Product Scope Freeze, novas dúvidas devem ser tratadas como **experimentos de produto**, sem reabrir silenciosamente decisões estruturais.

O PO pode manter um plano de experimentação:

| ID | Método | Amostra / contexto | Decisão alimentada |
| --- | --- | --- | --- |
| EXP-001 | entrevista | grupo relevante | hipótese X |
| EXP-002 | teste moderado | usuários | jornada Y |
| EXP-003 | POC | dados reais | dependência Z |

Experimentos podem incluir:

- entrevistas;
- testes moderados;
- protótipos;
- POCs;
- coortes;
- holdouts;
- revisão especializada;
- análise de suporte;
- pesquisa de satisfação;
- testes de compreensão.

Se um experimento invalidar uma decisão estrutural do Briefing, o processo deve retornar à camada responsável.

---

## 28. Instrumentação no nível de produto

O PO pode definir **o significado do que precisa ser medido**.

Exemplo:

```text
activated_user
qualified_cycle
first_value_time
completion_rate
recovery_rate
```

Para cada métrica, definir:

- nome semântico;
- evento ou comportamento representado;
- unidade;
- população elegível;
- exclusões;
- janela temporal;
- hipótese associada;
- guardrail relacionado.

O PO não escolhe nesta etapa a ferramenta concreta de analytics ou observabilidade.

A decisão deve sobreviver a troca de fornecedor.

---

## 29. Definition of Ready de produto

Uma história está pronta para avançar para detalhamento posterior quando:

- persona/contexto está claro;
- problema está claro;
- outcome está explícito;
- hipótese está identificada quando necessária;
- regra de negócio aplicável está vinculada;
- critérios de aceite de produto existem;
- principais estados críticos são conhecidos;
- risco relevante está mapeado;
- dependência externa está registrada;
- gate ou flag está indicado quando necessário;
- a história cabe em uma fatia de valor compreensível;
- UX e Engenharia conseguem identificar quais decisões pertencem a elas.

`Ready de produto` não significa `Ready for Codex`.

---

## 30. Definition of Done de produto

A Visão de PO pode definir critérios para que uma entrega seja aceita **como produto**, depois de implementada.

Exemplos:

- critérios funcionais cumpridos;
- comportamento observado conforme esperado;
- guardrails não violados;
- instrumentação necessária produz evidência;
- suporte/operação aplicável está preparado;
- rollback ou retirada é possível quando exigido;
- PO valida a entrega no ambiente apropriado;
- deploy não é tratado como sinônimo de aceite;
- aceite não é tratado como sinônimo de sucesso de mercado.

A Definition of Done técnica será detalhada nas camadas de engenharia e entrega.

---

## 31. Política de mudança

Toda mudança deve ser classificada.

| Tipo | Definição | Governança |
| --- | --- | --- |
| Correção | remove ambiguidade sem mudar outcome/escopo | atualizar PO e rastreabilidade |
| Mudança menor | altera regra ou fluxo dentro do escopo | revisar impacto em métrica, UX e risco |
| Mudança material | novo módulo, público, receita, dado ou risco | retornar ao Briefing |
| Exceção urgente | incidente, obrigação legal ou segurança | owner pode conter; documentação é reconciliada depois |

A Visão de PO não pode usar “ajuste de história” para esconder mudança material de produto.

---

## 32. Responsabilidades e fronteiras

A Visão de PO deve tornar claro quem decide o quê.

### Product Owner

Responsável por:

- outcomes;
- prioridade;
- regras de negócio;
- critérios de aceite de produto;
- hipóteses;
- gates;
- flags no sentido de liberação de produto;
- roadmap de aprendizado;
- decisão de continuidade.

### UX/UI

Responsável posteriormente por:

- comportamento de interface;
- hierarquia;
- fluxos detalhados;
- conteúdo;
- estados;
- acessibilidade de interação;
- sistema visual;
- evidência de usabilidade.

### Engenharia e Arquitetura

Responsável posteriormente por:

- transformar requisitos de produto e qualidade em forças de engenharia;
- definir propriedades técnicas necessárias;
- modelar domínios e boundaries;
- resolver consistência, confiabilidade, segurança e desempenho em nível estrutural;
- definir arquitetura sem antecipar tecnologia concreta quando a escolha ainda pertence ao Tech Lead.

### Visão do Tech Lead

Etapa posterior responsável por escolher **com quais tecnologias concretas** a arquitetura aprovada será materializada, com base na mensuração produzida pelas camadas anteriores.

Ela deverá tratar linguagens, runtimes, frameworks, bibliotecas, persistência concreta, ferramentas e compatibilidade de versões.

A Visão de PO não deve antecipar essas escolhas.

### DevOps e Infraestrutura

Camada posterior responsável pela forma de construir, entregar, executar e operar a stack aprovada, incluindo ambientes, automação, CI/CD, secrets, deploy, observabilidade operacional, infraestrutura, custos e recuperação.

A divisão final entre DevOps e Infraestrutura será definida na etapa técnica correspondente da metodologia; esta etapa apenas protege a fronteira de responsabilidade.

---

## 33. Riscos e dependências sob governança de PO

O PO deve manter riscos que impactem produto, liberação ou aprendizado.

Estrutura:

| ID | Risco | Nível | Resposta |
| --- | --- | --- | --- |
| R-001 | descrição | baixo/médio/alto/crítico | mitigação |

Dependências externas devem indicar:

- o que depende de terceiro;
- qual evidência libera a dependência;
- qual gate é afetado;
- fallback quando existir;
- impacto se a dependência não for obtida.

Uma dependência externa planejada não deve ser tratada como garantida.

---

## 34. Roadmap orientado a resultados

Quando um roadmap for necessário, ele deve organizar resultados, não uma sequência rígida de features.

Estrutura recomendada:

| Marco | Outcome | Entregas habilitadoras | Evidência |
| --- | --- | --- | --- |
| R0 | resultado | capacidades | prova |

O roadmap pode mudar se a evidência mudar.

O outcome possui mais estabilidade que a solução específica.

---

## 35. Revisão humana

A etapa deve ser conduzida de forma iterativa.

### Fase A — elaboração

O ChatGPT pode construir o documento por blocos:

1. visão e mandato;
2. personas e JTBD;
3. outcomes e métricas;
4. hipóteses e guardrails;
5. regras de negócio;
6. épicos e histórias;
7. gates e experimentos;
8. governança e handoff.

O usuário revisa decisões e corrige interpretações.

### Fase B — reconciliação

Antes da canonização, o ChatGPT deve comparar o conteúdo proposto com o Briefing.

Mudanças materiais devem ser destacadas.

### Fase C — autorização

Somente após aprovação humana o arquivo do projeto é criado ou atualizado.

Exemplo:

```text
A Visão de PO está aprovada.
Gere o 03_Visao_de_Product_Owner.md e salve no projeto.
```

---

## 36. Estrutura esperada do artefato de projeto

A saída canônica deve ser:

```text
03_Visao_de_Product_Owner.md
```

Estrutura recomendada:

```text
---
document_id: DOC-03
status: canonical
version: 1.0.0
depends_on:
  - DOC-00
  - DOC-01
  - DOC-02
next_document: Principios_de_UX_UI.md
---

# Visão de Product Owner

## 1. Visão e mandato
## 2. Pessoas, contextos e JTBD
## 3. Outcomes e North Star
## 4. Scorecard e guardrails
## 5. Hipóteses e condições de retirada
## 6. Jornadas e loops de valor
## 7. Regras de negócio
## 8. Épicos e baseline de backlog de produto
## 9. Histórias e critérios de aceite
## 10. Ondas e gates
## 11. Experimentos e instrumentação
## 12. Definition of Ready de produto
## 13. Definition of Done de produto
## 14. Política de mudança
## 15. Riscos e dependências
## 16. Handoff
```

A estrutura pode ser adaptada ao projeto sem perder as responsabilidades essenciais.

---

## 37. Quality Gate da Visão de PO

Antes de propor canonização, verificar:

- Discovery, Pesquisa e Briefing foram consumidos;
- nenhuma mudança material foi escondida;
- visão e missão do horizonte estão claras;
- persona primária ou critério de precedência existe quando necessário;
- JTBD descreve progresso, não features;
- outcomes estão separados de entregas;
- North Star mede valor relevante quando aplicável;
- targets são tratados como hipóteses, não certezas;
- guardrails estão explícitos;
- módulos relevantes possuem hipótese e condição de retirada;
- regras de negócio possuem IDs estáveis;
- backlog de produto possui rastreabilidade;
- itens removidos preservam histórico;
- critérios de aceite são verificáveis;
- estados críticos foram considerados;
- prioridade representa valor/aprendizado e não peso visual;
- ondas não foram confundidas com sprints;
- gates possuem condição e owner;
- dependências externas não foram tratadas como garantias;
- instrumentação foi descrita semanticamente sem escolher fornecedor prematuramente;
- escolhas de UX/UI não foram antecipadas indevidamente;
- arquitetura e stack não foram escolhidas nesta etapa;
- a diferença entre backlog de produto e backlog canônico de entrega está explícita;
- a próxima etapa consegue trabalhar sem inventar regra de negócio ou prioridade.

---

## 38. Anti-padrões

### Feature factory

Mede produtividade por quantidade de telas ou histórias concluídas.

### Backlog sem outcome

Possui centenas de itens, mas não explica qual comportamento cada grupo pretende mudar.

### Persona inventada

Cria biografias, renda e demografia sem evidência ou necessidade.

### North Star de vaidade

Escolhe abertura, tempo de tela ou curtidas porque são fáceis de medir.

### Target tratado como verdade

Transforma hipótese de beta em obrigação estatística sem amostra adequada.

### História como especificação técnica

Inclui framework, banco, provider ou biblioteca sem necessidade de produto.

### Critério subjetivo

Usa “intuitivo”, “bonito”, “rápido” ou “moderno” sem comportamento verificável.

### P0 igual a ordem de implementação

Entrega todos os módulos do escopo antes de provar o core.

### Feature construída é feature permanente

Mantém uma capacidade apenas porque já foi desenvolvida.

### Gate sem owner

Registra condição sem alguém responsável por decidir.

### Onda igual a sprint

Transforma rollout de aprendizagem em cronograma arbitrário.

### PO escolhe stack

Usa a visão de produto para definir tecnologia concreta antes de Engenharia, Tech Lead e Infraestrutura.

### PO redesenha o Briefing silenciosamente

Altera público, monetização, core ou escopo material dentro de uma história.

### PO gera backlog pronto para Codex cedo demais

Ignora UX, engenharia, arquitetura, tecnologia e infraestrutura e entrega histórias diretamente para implementação.

---

## 39. Handoff para UX/UI

A Visão de PO está pronta para avançar quando as próximas etapas conseguem responder:

```text
QUEM RECEBE VALOR?
QUAL OUTCOME IMPORTA?
QUAL COMPORTAMENTO DEMONSTRA VALOR?
QUAL LOOP É CENTRAL?
QUAL REGRA NÃO PODE SER REINTERPRETADA?
QUAL PRIORIDADE É MAIOR?
QUAL HIPÓTESE ESTÁ SENDO TESTADA?
QUAL GUARDRAIL NÃO PODE SER VIOLADO?
QUAL ESTADO DE ERRO OU RECUPERAÇÃO IMPORTA?
QUAL GATE CONTROLA LIBERAÇÃO?
COMO SABEREMOS SE FUNCIONOU?
```

O próximo passo da metodologia refinada é consolidar os **Princípios de UX e UI** antes de detalhar direção visual e fluxos.

O handoff deve preservar:

- personas;
- JTBD;
- outcomes;
- North Star;
- guardrails;
- journeys;
- business rules;
- épicos e histórias;
- prioridades;
- critérios de aceite;
- estados críticos;
- gates;
- condições de retirada.

UX/UI pode propor solução diferente, mas não pode mudar silenciosamente a intenção.

---

## 40. Relação com o backlog final de entrega

A cadeia pretendida é:

```text
BRIEFING
        ↓
VISÃO DE PO
        ↓
BACKLOG DE PRODUTO
        ↓
UX/UI
        ↓
ENGENHARIA E ARQUITETURA
        ↓
VISÃO DO TECH LEAD
        ↓
DEVOPS / INFRAESTRUTURA
        ↓
BACKLOG CANÔNICO DE ENTREGA
        ↓
CODEX
```

O backlog final não deve substituir o backlog de produto.

Ele deve **enriquecê-lo tecnicamente**, mantendo rastreabilidade até outcomes, regras e histórias originais.

---

## 41. Gate para avançar

A etapa pode ser considerada concluída quando:

- os documentos anteriores foram consumidos;
- visão, outcomes e público estão claros;
- regras de negócio vinculantes estão identificadas;
- hipóteses e guardrails estão visíveis;
- backlog de produto foi ordenado;
- critérios de aceite de produto foram definidos;
- riscos e dependências foram registrados;
- gates possuem owners e evidências;
- mudanças materiais foram reconciliadas com o Briefing;
- o humano revisou o conteúdo;
- o humano aprovou a Visão de PO;
- o humano autorizou a canonização;
- `03_Visao_de_Product_Owner.md` foi criado ou atualizado;
- UX/UI consegue avançar sem inventar produto.

Somente então a próxima etapa é elegível.

---

## 42. Regra final da etapa

> **Product Owner não transforma escopo em uma lista de features. Ele transforma a intenção do produto em outcomes, comportamentos, regras, hipóteses e entregas priorizadas que possam ser testadas sem permitir que a implementação redefina silenciosamente o produto.**

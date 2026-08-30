# Engenharia de IA — Processo Canônico de Desenvolvimento

> **Status:** canônico  
> **Formato:** Markdown (`.md`)  
> **Objetivo:** definir um processo reproduzível para transformar Discovery assistido por IA em software rastreável, testável, validado e com identidade própria.

## 1. Propósito

Este repositório documenta o processo de desenvolvimento de aplicações assistido por ChatGPT e Codex adotado a partir da experiência do projeto DayGym.

O objetivo não é pedir para uma IA "criar um sistema" a partir de um prompt único. O processo separa descoberta, definição de produto, experiência, engenharia, arquitetura, infraestrutura, execução, validação e evolução documental.

A regra central é:

```text
Discovery humano assistido por IA
        ↓
Documentação canônica aprovada
        ↓
Engenharia
        ↓
Arquitetura
        ↓
Infraestrutura
        ↓
Backlog rastreável
        ↓
Fundação / Setup
        ↓
Implementação por fatias
        ↓
Testes e gates
        ↓
Staging e evidências
        ↓
Promoção
        ↓
Rastreabilidade atualizada
```

A documentação não existe apenas para explicar o projeto. Ela deve orientar decisões, limitar interpretações, permitir rastreabilidade e, quando possível, gerar contratos que possam ser validados automaticamente.

---

## 2. Princípios gerais do processo

### 2.1. A conversa de Discovery não é fonte canônica

O Discovery normalmente acontece em uma longa conversa com o ChatGPT. Durante essa etapa podem existir hipóteses, ideias descartadas, comparações, pesquisas, mudanças de direção e decisões ainda incompletas.

Por isso:

```text
CONVERSA ≠ FONTE DA VERDADE
```

A conversa é matéria-prima para raciocínio.

A documentação canônica nasce quando o responsável pelo produto encerra uma etapa do Discovery e solicita explicitamente a geração do artefato correspondente, por exemplo:

> "Certo, agora crie o briefing."

Esse momento funciona como um **Discovery Freeze** daquela camada de decisão.

Antes de canonizar qualquer conteúdo, a IA deve distinguir:

- **decidido**;
- **hipótese**;
- **pendente**;
- **descartado**.

Uma hipótese discutida no Discovery não pode ser promovida automaticamente a requisito.

### 2.2. Markdown é o formato canônico

Todos os documentos de produto, UX, UI, engenharia, arquitetura, infraestrutura, backlog e rastreabilidade devem ser mantidos prioritariamente em `.md`.

```text
.md    → formato canônico
.docx  → não usar como fonte canônica
.xlsx  → não usar como fonte canônica de requisitos
.pdf   → não usar como fonte canônica de requisitos
```

Arquivos auxiliares podem existir quando houver necessidade real, mas a fonte da verdade deve permanecer legível por humanos, agentes de IA, Git, revisão de código e automações.

### 2.3. Cada documento possui uma responsabilidade semântica

Um documento não deve tentar substituir todos os outros. A separação reduz ambiguidade e permite que a IA saiba onde procurar cada tipo de decisão.

### 2.4. A IA não deve completar lacunas silenciosamente

Quando a documentação não define uma decisão relevante, o agente deve:

1. identificar a lacuna;
2. verificar se ela pode ser resolvida pelos princípios existentes;
3. verificar se uma skill, check ou regra canônica existente resolve a lacuna;
4. pedir decisão humana quando a lacuna alterar produto, negócio, risco, custo ou identidade.

A ausência de especificação não autoriza invenção silenciosa.

### 2.5. Os documentos devem ser gerados e aprovados um por vez

A baseline não deve ser produzida integralmente em uma única resposta.

O fluxo recomendado é:

```text
Discovery / documento anterior
        ↓
IA gera UM documento .md
        ↓
Humano lê
        ↓
Humano aprova ou corrige
        ↓
IA ajusta o MESMO documento
        ↓
Humano confirma a decisão
        ↓
Arquivo é salvo/versionado
        ↓
Somente então gerar o próximo documento
```

Essa regra existe para impedir propagação de erro.

```text
Briefing mal interpretado
        ↓
Visão de PO incorreta
        ↓
UX/UI incorreta
        ↓
Engenharia inadequada
        ↓
Arquitetura inadequada
        ↓
Infraestrutura inadequada
        ↓
Backlog inadequado
        ↓
Código tecnicamente correto para o produto errado
```

Ao revisar um documento, o humano pode orientar ajustes naturais, por exemplo:

> "Acho que X deve funcionar assim e Y daquela forma. Ajuste este documento e depois seguimos para o próximo."

A IA deve alterar o artefato já existente, e não criar versões concorrentes como `final`, `novo`, `(1)` ou similares.

### 2.6. Onde salvar os documentos do projeto

Após aprovação, cada documento deve ser entregue como `.md`.

Quando não houver integração com Git, o ChatGPT pode gerar o arquivo para download e o usuário o mantém na pasta canônica do projeto.

Quando houver acesso autorizado ao GitHub, o ChatGPT pode criar ou atualizar diretamente o documento no repositório.

Nos dois casos, a regra permanece:

```text
UM documento
        ↓
revisão humana
        ↓
ajuste
        ↓
aprovação
        ↓
versionamento
        ↓
próximo documento
```

### 2.7. Compatibilidade atualmente homologada

Este processo foi criado e testado no fluxo **ChatGPT + Codex**.

O escopo atualmente homologado é:

- **ChatGPT em plano pago**, usando um modelo recente de alta capacidade para Discovery, entrevistas, pesquisa, documentação e revisão;
- **Codex em plano pago**, usando um modelo de alta capacidade para engenharia, setup, implementação, testes, automação e evidências;
- **GitHub** como fonte versionada recomendada;
- **Playwright ou automação equivalente de navegador** quando o setup exige interação humano-assistida com painéis web.

Outros agentes, IDEs autônomas ou modelos menores podem funcionar, mas não foram validados de ponta a ponta por esta metodologia.

A metodologia não fixa nomes específicos de modelos porque as opções disponíveis mudam. Deve-se utilizar o modelo de maior capacidade adequado à etapa quando o projeto exigir raciocínio documental, arquitetural ou execução de engenharia extensa.

Como regra operacional:

```text
ChatGPT
→ Discovery
→ entrevista
→ pesquisa
→ documentação
→ revisão com o humano

Codex
→ consome documentação aprovada
→ executa engenharia
→ Fundação
→ implementação
→ testes
→ automação
→ evidências
```

Essa divisão também evita consumir o ambiente de coding para tarefas documentais que podem ser realizadas de forma mais econômica no ChatGPT.

---

# 3. Arquitetura documental inicial

A baseline de um novo produto é composta pelos seguintes artefatos:

```text
01_Pesquisa_e_Viabilidade.md
02_Briefing_de_Produto_e_Escopo.md
03_Visao_de_Product_Owner.md
Principios_de_UX_UI.md
04_Direcao_de_UI_e_Design_System.md
05_Especificacao_de_UX.md
06_Tecnicas_de_Desenvolvimento.md
07_Engenharia_e_Arquitetura.md
Infraestrutura_e_Plano_de_Fundacao.md
08_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
09_Matriz_Operacional_de_Rastreabilidade.md
```

`Principios_de_UX_UI.md` não é numerado porque não representa apenas uma etapa linear. Ele é uma camada normativa transversal, específica para a aplicação, consultada continuamente por UI, UX, Design System e implementação.

`Infraestrutura_e_Plano_de_Fundacao.md` também não altera a numeração histórica 01–09. Ele é uma ponte operacional entre o dimensionamento técnico do Documento 07 e os itens FND do backlog.

---

# 4. Documento 01 — Pesquisa e Viabilidade

## Pergunta central

> **Faz sentido construir este produto?**

## Objetivo

Transformar o Discovery inicial em uma análise estruturada do problema e da viabilidade da solução.

## Deve conter

- problema observado;
- público afetado;
- necessidades e Jobs To Be Done quando aplicável;
- alternativas e soluções existentes;
- concorrentes e referências;
- evidências de mercado ou comportamento;
- diferenciação possível;
- limitações técnicas conhecidas;
- riscos;
- premissas;
- hipóteses ainda não validadas;
- critérios de viabilidade.

## Regra de qualidade

O documento deve separar explicitamente:

```text
EVIDÊNCIA ≠ HIPÓTESE ≠ DECISÃO
```

## Saída

Uma conclusão clara sobre o que foi aprendido e quais pontos podem seguir para definição de produto.

---

# 5. Documento 02 — Briefing de Produto e Escopo

## Pergunta central

> **O que estamos construindo e o que não estamos construindo?**

## Objetivo

Preservar a intenção do produto e limitar interpretações futuras.

## Deve conter

- visão resumida do produto;
- problema;
- proposta de valor;
- público;
- objetivos;
- escopo;
- não escopo;
- funcionalidades macro;
- plataformas previstas;
- restrições;
- premissas;
- modelo operacional;
- definição de MVP, Beta ou corte inicial;
- critérios macro de sucesso.

## Regra de qualidade

O documento descreve requisitos de produto, não implementação.

Exemplo correto:

```text
O usuário deve conseguir registrar cada série individualmente.
```

Exemplo incorreto nesta camada:

```text
Criar o componente React WorkoutSetCard.
```

---

# 6. Documento 03 — Visão de Product Owner

## Pergunta central

> **Como o produto deve tomar decisões quando existirem várias soluções possíveis?**

## Objetivo

Transformar o briefing em uma política de decisão de produto.

## Deve conter

- visão do PO;
- princípios do produto;
- prioridades;
- objetivos da versão atual;
- jornadas prioritárias;
- regras de negócio centrais;
- trade-offs preferidos;
- critérios de valor;
- ordem macro de evolução;
- decisões que não devem ser revertidas sem revisão explícita.

## Exemplo

```text
O produto prioriza velocidade durante a execução do treino
sobre densidade de informação na tela.
```

O Briefing define **o que o produto é**. A Visão do PO define **como decidir sobre ele**.

---

# 7. Princípios de UX/UI

## Pergunta central

> **Quando houver mais de uma solução de interface possível, qual decisão combina melhor com a experiência que esta aplicação quer oferecer?**

## Natureza do documento

`Principios_de_UX_UI.md` é uma **constituição de experiência específica da aplicação**.

Ele não especifica telas individualmente. Ele orienta as decisões que serão depois materializadas pela Direção de UI, pelo Design System e pela Especificação de UX.

Os princípios devem ser definidos de acordo com o contexto, a identidade e o comportamento desejado para aquela aplicação.

## Eixos obrigatórios

### 7.1. Baixa carga cognitiva

A experiência deve minimizar:

- memorização;
- procura visual;
- interpretação desnecessária;
- comparação simultânea;
- excesso de escolhas;
- mudança de contexto;
- necessidade de reaprender padrões entre telas.

Exemplo de princípio:

```text
A ação principal necessária para concluir uma tarefa deve permanecer
perceptível durante a execução daquela tarefa.
```

Aplicação possível:

```text
Formulário longo
+ ação principal = salvar
+ risco de o botão sair da área visível
→ preferência por ação persistente no rodapé.
```

O princípio orienta a decisão. Ele não obriga que todos os botões de todas as telas tenham a mesma posição sem considerar o contexto.

### 7.2. Baixa densidade

Baixa densidade não significa apenas aumentar espaços vazios. Significa reduzir a quantidade de elementos que disputam atenção simultaneamente.

O documento deve orientar:

- quantidade de informações primárias;
- hierarquia visual;
- progressão de complexidade;
- exposição de ações raras;
- uso de detalhes sob demanda;
- redução de controles redundantes.

### 7.3. Linguagem do usuário

A aplicação deve falar sobre a tarefa que o usuário quer realizar, e não sobre a estrutura interna do software.

Preferir:

```text
Salvar treino
Adicionar exercício
Concluir série
```

Evitar:

```text
Persistir alterações
Adicionar entidade
Finalizar registro
```

Esse princípio vale para títulos, CTAs, erros, confirmações, empty states, onboarding, ajuda contextual e feedbacks.

### 7.4. Comunicação e personalidade da marca

A personalidade da marca deve influenciar a experiência completa, não somente textos promocionais.

Devem ser documentados atributos como, por exemplo:

- séria;
- alegre;
- energética;
- próxima;
- técnica;
- calma;
- premium;
- objetiva.

Esses atributos podem orientar:

- tom de voz;
- tipografia;
- hierarquia;
- densidade;
- movimentos e microinterações;
- ícones;
- feedbacks;
- ritmo da navegação;
- grau de celebração;
- cores;
- ilustrações;
- intensidade visual.

A intenção é remover o aspecto de interface genérica e dar identidade reconhecível ao produto.

## Os princípios devem ser avaliáveis

Evitar princípios vagos como:

```text
A interface deve ser simples.
```

Preferir estruturas como:

```markdown
## P-UX-004 — Uma tarefa mental dominante

### Objetivo
Permitir que o usuário identifique rapidamente o que deve fazer.

### Regra
Cada estado principal de uma tela deve possuir uma tarefa mental dominante.

### Critérios
- deve existir apenas uma CTA de maior hierarquia;
- ações secundárias não devem competir visualmente com a principal;
- informação sem utilidade imediata deve perder hierarquia;
- ações destrutivas não devem dominar visualmente a tela, salvo quando a própria tarefa for confirmar uma exclusão.

### Perguntas de avaliação
1. O objetivo da tela é reconhecível rapidamente?
2. Mais de uma ação compete pela atenção?
3. Existe informação visível sem utilidade para a tarefa atual?
4. O usuário precisa lembrar algo de outra tela para continuar?
```

## Papel no processo

```text
IDENTIDADE DA MARCA
        +
COMPORTAMENTO HUMANO
        +
PRINCÍPIOS DE EXPERIÊNCIA
        ↓
DECISÕES DE UI/UX
```

---

# 8. Documento 04 — Direção de UI e Design System

## Pergunta central

> **O que deve existir na interface para suportar cada contexto e tarefa mental, e qual deve ser sua hierarquia?**

## Objetivo

Especificar contextos, telas, tarefas mentais, elementos necessários e representação visual.

Este documento é específico. Diferentemente dos Princípios, ele toma decisões concretas para superfícies e contextos.

## Deve conter

- contextos de uso;
- telas e superfícies;
- tarefa mental principal de cada tela;
- informações obrigatórias;
- ações principais;
- ações secundárias;
- ações raras ou destrutivas;
- hierarquia visual;
- estrutura de navegação local;
- componentes previstos;
- tokens e fundamentos visuais;
- tipografia;
- espaçamento;
- cores semânticas;
- densidade;
- estados visuais;
- responsividade;
- regras do Design System.

## Exemplo

```markdown
## Tela: Editar treino

### Contexto
Usuário está montando ou ajustando um treino.

### Tarefa mental principal
Montar o treino.

### Elementos obrigatórios
- nome;
- exercícios;
- adicionar exercício;
- salvar;
- excluir treino.

### Hierarquia
- Salvar: ação principal;
- Adicionar exercício: ação contextual;
- Excluir: ação destrutiva de baixa frequência.

### Decisão de interface
Salvar permanece persistente no rodapé durante formulários longos.
Excluir fica em ação secundária e não compete visualmente com Salvar.
```

## Relação com o Design System

O Design System materializa decisões. Ele não deve decidir sozinho o contexto de uso.

```text
Princípio
   +
Contexto / tarefa mental
   ↓
Decisão de UI
   ↓
Componente do Design System
```

---

# 9. Documento 05 — Especificação de UX

## Pergunta central

> **Como o usuário percorre, executa e conclui a experiência?**

## Objetivo

Especificar jornadas, user stories, estados, transições, erros e exceções.

## Deve conter

- jornadas;
- user stories;
- fluxos;
- estados;
- transições;
- loading;
- empty state;
- erros;
- sucesso;
- confirmações;
- validações;
- interrupções;
- retomadas;
- acessibilidade comportamental;
- gestos quando aplicáveis;
- comportamento por plataforma;
- microcopy crítica.

## Exemplo de jornada

```text
Selecionar exercício
        ↓
Iniciar
        ↓
Exibir série atual
        ↓
Ajustar carga/repetições se necessário
        ↓
Concluir série
        ↓
Descanso
        ↓
Próxima série
        ↓
Última série?
  não ─────────┘
  sim
        ↓
Próximo exercício
```

## Exemplo de User Story

```text
Como praticante,
quero registrar cada série individualmente,
para acompanhar o que realizei sem interromper meu treino.
```

## Distinção entre os três documentos de experiência

| Documento | Função | Pergunta |
| --- | --- | --- |
| `Principios_de_UX_UI.md` | orientar decisões | Qual solução combina com a experiência desejada? |
| `04_Direcao_de_UI_e_Design_System.md` | especificar contexto, telas e hierarquia | O que deve existir e como deve ser representado? |
| `05_Especificacao_de_UX.md` | especificar jornadas e comportamento | Como o usuário percorre e conclui a experiência? |

Resumo:

```text
Princípios → orientam
Documento 04 → especifica a interface
Documento 05 → especifica a jornada
```

---

# 10. Documento 06 — Técnicas de Desenvolvimento

## Pergunta central

> **Como humanos e agentes de IA podem programar neste projeto?**

## Objetivo

Definir regras operacionais de implementação e estabelecer um padrão de código compreensível, consistente, reutilizável, testável e sustentável, independentemente de quem o escreveu ou de quem fará sua manutenção no futuro.

O Documento 06 não deve apenas listar ferramentas de lint, build ou testes. Ele deve funcionar como o **contrato de escrita do código**.

A regra central é:

> **Código é comunicação entre pessoas e máquinas. A IA está sujeita ao mesmo padrão de engenharia exigido de um desenvolvedor humano experiente.**

O resultado esperado é uma base que possa ser entendida por um engenheiro competente de qualquer país, equipe ou época sem depender da memória de quem implementou a funcionalidade e sem apresentar sinais de código produzido sem critério por geração automática.

## Deve conter, quando aplicável

- linguagem e runtime;
- versões fixadas;
- package manager;
- TypeScript strict ou equivalente;
- organização de módulos;
- convenções de naming;
- idioma técnico do código;
- regras de Clean Code;
- critérios de legibilidade;
- limites de dependência;
- regras de reaproveitamento e abstração;
- tratamento de erros;
- logging e observabilidade;
- política de dependências;
- critérios de desempenho;
- migrations;
- política de segredos;
- segurança de cliente e servidor;
- padrão de testes;
- testes de regressão;
- mocks;
- lint;
- formatting;
- typecheck;
- build;
- política de branches;
- commits;
- pull requests;
- revisão de código;
- Definition of Done;
- instruções específicas para agentes.

## 10.1. Princípio de legibilidade universal

O código deve ser escrito para ser lido antes de ser escrito para impressionar.

Preferir:

```text
readable > clever
explicit > implicit
cohesive > fragmented
existing convention > invented convention
small coherent change > broad speculative rewrite
measured optimization > premature optimization
```

Uma implementação não é considerada boa apenas porque compila, passa nos testes ou resolve o caso feliz.

Ela também deve permitir que outro desenvolvedor compreenda rapidamente:

- o que o código faz;
- por que ele existe;
- onde uma regra de negócio está localizada;
- quais dependências utiliza;
- quais invariantes preserva;
- quais efeitos colaterais produz;
- como deve ser testado;
- como pode ser alterado sem quebrar comportamento não relacionado.

A complexidade inevitável deve ficar explícita. Complexidade acidental deve ser removida.

## 10.2. Inglês como idioma técnico do código

O idioma técnico padrão do código-fonte deve ser **inglês**.

Devem ser escritos em inglês, salvo exceção justificada:

- nomes de variáveis;
- funções e métodos;
- classes;
- interfaces e types;
- enums;
- eventos;
- comandos;
- nomes de módulos e packages;
- arquivos técnicos de código;
- nomes de testes;
- comentários;
- docstrings;
- mensagens internas para desenvolvedores;
- identificadores de logs estruturados quando não forem texto destinado ao usuário.

Exemplo preferido:

```ts
const remainingSets = workout.totalSets - completedSets;

function calculateRestDuration(exercise: Exercise): number {
  return exercise.restSeconds ?? DEFAULT_REST_SECONDS;
}
```

Evitar misturar idiomas:

```ts
const seriesRestantes = treino.totalSets - completedSets;

function calcularRestTime(exercicio: Exercise): number {
  // Calcula o descanso padrão
  return exercicio.restSeconds ?? DEFAULT_REST_SECONDS;
}
```

### Exceções

Essa regra não obriga traduzir conteúdo que **precisa permanecer no idioma ou formato do domínio externo**, por exemplo:

- texto visível ao usuário, que segue a linguagem definida pela UX;
- códigos fiscais, legais ou regulatórios;
- nomes oficiais de campos de uma integração externa;
- payloads de terceiros;
- nomes legados que façam parte de um contrato que não pode ser alterado;
- termos de domínio cuja tradução alteraria o significado canônico.

Mesmo nesses casos, o código ao redor deve continuar legível e a exceção deve permanecer localizada.

## 10.3. Naming deve revelar intenção

Nomes devem explicar a responsabilidade do elemento sem exigir que o leitor abra sua implementação para descobrir o que ele significa.

### Funções e métodos

Preferir verbos que expressem ação ou resultado:

```ts
createWorkoutPlan()
validateSessionToken()
calculateTrainingVolume()
archiveExercise()
```

Evitar:

```ts
doStuff()
processData()
handleThing()
execute()
runLogic()
```

quando o contexto não torna a intenção inequívoca.

### Booleanos

Devem ser lidos como afirmações:

```ts
isAuthenticated
hasPendingChanges
canEditWorkout
shouldStartRestTimer
```

### Coleções

Devem deixar claro o que contêm:

```ts
activeExercises
pendingMigrations
authorizedApplications
```

em vez de nomes vagos como:

```ts
items
data
list
values
```

quando o escopo não torna o significado evidente.

### Abreviações

Não criar abreviações particulares para economizar caracteres.

Preferir nomes conhecidos pelo domínio e pela comunidade técnica. Abreviações universalmente reconhecidas, como `id`, `url`, `api` ou termos canônicos do domínio, podem ser usadas conforme a convenção da linguagem e do projeto.

## 10.4. Clean Code é requisito, não preferência estética

O projeto deve favorecer:

- responsabilidade clara;
- alta coesão;
- baixo acoplamento;
- dependências explícitas;
- fluxo de controle compreensível;
- funções com propósito identificável;
- módulos com fronteiras coerentes;
- ausência de código morto;
- ausência de duplicação sem justificativa;
- estruturas de dados adequadas ao problema;
- tratamento explícito de estados inválidos;
- separação entre regra de negócio e detalhe de infraestrutura quando a arquitetura assim exigir.

Evitar:

- funções gigantes com responsabilidades diferentes;
- arquivos que acumulam regras não relacionadas;
- condicionais profundamente aninhadas quando o fluxo pode ser simplificado;
- números e strings mágicas;
- parâmetros booleanos ambíguos;
- efeitos colaterais escondidos;
- dependências globais desnecessárias;
- abstrações genéricas que não possuem semântica real;
- `utils`, `helpers`, `common` ou equivalentes como depósitos sem responsabilidade definida;
- camadas criadas apenas para parecer que existe arquitetura;
- generalização antecipada para funcionalidades que ainda não existem.

Não há um número universal de linhas que transforme automaticamente uma função em ruim. O critério é **coesão e facilidade de compreensão**. Se uma unidade exige múltiplos contextos mentais para ser entendida, deve ser avaliada para decomposição.

## 10.5. Comentários devem explicar o porquê

Comentários e docstrings técnicas devem ser escritos em inglês.

Comentário não deve narrar código óbvio.

Evitar:

```ts
// Increment counter
counter++;
```

Preferir comentário apenas quando existe contexto que o código sozinho não consegue carregar de forma segura:

```ts
// Keep the operation id stable across retries to preserve idempotency.
const operationId = existingOperationId ?? createOperationId();
```

Comentários são apropriados para explicar, por exemplo:

- restrição externa;
- decisão não óbvia;
- workaround temporário;
- invariantes importantes;
- motivo de uma otimização;
- comportamento estranho de biblioteca ou provider;
- regra regulatória difícil de inferir.

Regras:

- não deixar código comentado; Git já preserva histórico;
- comentário desatualizado é defeito e deve ser corrigido ou removido;
- `TODO`, `FIXME` ou equivalente não deve funcionar como esquecimento silencioso; quando representar dívida real, deve possuir contexto suficiente e, quando apropriado, referência rastreável a Issue/backlog;
- não gerar blocos de comentários artificiais apenas para explicar cada passo produzido pela IA.

## 10.6. Antes de criar código, procurar o que já existe

A IA não deve presumir que precisa criar uma nova função, componente, type, serviço ou abstração.

Antes de implementar, deve procurar no repositório por:

- comportamento equivalente;
- componentes existentes;
- funções de domínio;
- validators;
- adapters;
- hooks;
- contracts/types;
- schemas;
- helpers especializados;
- testes relacionados;
- padrões usados em módulos vizinhos.

O fluxo esperado é:

```text
necessidade nova
      ↓
existe implementação semanticamente equivalente?
      ├── sim → reutilizar ou estender com segurança
      │
      └── não
           ↓
existe duplicação real que justifica abstração?
      ├── sim → extrair responsabilidade coerente
      │
      └── não → implementar localmente de forma simples
```

### Reutilizar não significa forçar abstração

Duas estruturas visualmente parecidas não são necessariamente o mesmo conceito.

A reutilização é adequada quando comportamento, invariantes e motivo de mudança são compatíveis.

Não criar uma abstração compartilhada apenas porque dois blocos possuem algumas linhas iguais se eles representam regras diferentes e provavelmente evoluirão por motivos diferentes.

Preferir composição a hierarquias artificiais quando a composição mantiver responsabilidades mais claras.

## 10.7. Duplicação deve ser analisada, não normalizada

Copy/paste não pode ser o mecanismo padrão de velocidade da IA.

Ao identificar lógica repetida, o agente deve perguntar:

1. é realmente a mesma regra?
2. as duas ocorrências devem mudar juntas quando o comportamento mudar?
3. já existe um lugar canônico para essa responsabilidade?
4. a extração melhora legibilidade ou apenas reduz linhas?
5. a nova abstração terá nome e contrato claros?

Se a resposta indicar uma regra única, reutilizar ou extrair.

Se forem conceitos diferentes que apenas coincidem hoje, manter separados pode ser mais correto.

O objetivo é evitar simultaneamente:

```text
copy/paste indiscriminado
        e
abstração prematura indiscriminada
```

## 10.8. Dependências devem possuir justificativa

A IA não deve instalar uma biblioteca para resolver uma capacidade trivial que já pode ser atendida pela plataforma, pelo runtime ou por dependência existente de forma adequada.

Antes de adicionar dependência, verificar:

- a capacidade já existe no projeto?
- a plataforma já resolve?
- a biblioteca é compatível com a versão instalada?
- é mantida?
- aumenta bundle, superfície de ataque ou complexidade operacional?
- será utilizada de forma suficiente para justificar o custo?
- introduz lock-in ou contrato desnecessário?

Quando a tecnologia instalada possuir documentação local ou versão diferente do conhecimento de treinamento do modelo, a IA deve consultar a documentação correspondente à versão efetivamente instalada antes de escrever código.

## 10.9. Desempenho deve ser tratado com evidência e responsabilidade

Código limpo não significa ignorar desempenho.

A IA deve evitar desde o início anti-padrões evidentes, como:

- complexidade desnecessariamente alta em caminhos frequentes;
- N+1 queries;
- requisições de rede redundantes;
- leitura ou escrita repetitiva sem necessidade;
- serialização excessiva;
- loops que recalculam invariantes;
- renders evitáveis em superfícies críticas quando demonstravelmente relevantes;
- carregamento de dados muito maior que o necessário;
- dependências pesadas para tarefas pequenas;
- consultas sem índices quando o padrão de acesso e o volume justificarem indexação.

Ao mesmo tempo, a IA não deve sacrificar clareza por micro-otimizações especulativas.

O fluxo esperado é:

```text
correção e legibilidade
        ↓
eliminar ineficiências óbvias
        ↓
medir quando existir caminho crítico
        ↓
identificar gargalo real
        ↓
otimizar
        ↓
medir novamente
```

Uma otimização não óbvia que reduza legibilidade deve possuir justificativa técnica e evidência suficiente para que outro mantenedor entenda por que ela existe.

## 10.10. Tratamento de erros deve ser explícito

Evitar código que engole falhas apenas para manter o fluxo aparentemente funcionando.

Não fazer:

```ts
try {
  await syncWorkout();
} catch {
  // Ignore
}
```

O projeto deve definir quando:

- retornar erro de domínio;
- lançar exceção;
- converter erro externo;
- realizar retry;
- registrar log;
- mostrar feedback ao usuário;
- interromper operação;
- degradar funcionalidade de maneira segura.

Logs técnicos não devem expor segredos, tokens, dados pessoais desnecessários ou payloads sensíveis.

Mensagens internas e estruturas de erro devem ser previsíveis e rastreáveis.

## 10.11. Testes fazem parte da escrita do código

Testes não são uma etapa decorativa adicionada depois da implementação.

O Documento 06 deve definir, conforme a natureza do projeto:

- quais regras exigem teste unitário;
- quais boundaries exigem integração;
- quais jornadas críticas exigem E2E;
- quais contratos exigem testes positivos e negativos;
- quais riscos de segurança exigem testes específicos;
- quais bugs corrigidos exigem regressão.

Regra importante:

> **Bug corrigido que pode reaparecer deve, sempre que tecnicamente viável, deixar um teste de regressão ou check capaz de detectar a mesma classe de falha.**

Nomes de testes e descrições técnicas devem ser escritos em inglês e descrever comportamento, não detalhes acidentais da implementação.

Exemplo:

```ts
it('rejects a workout completion when no exercise was recorded', async () => {
  // ...
});
```

Evitar testes frágeis que apenas espelham a implementação interna e quebram sem mudança de comportamento.

## 10.12. A IA deve respeitar o estilo existente antes de introduzir um novo

Antes de editar uma área madura do projeto, a IA deve inspecionar código vizinho e identificar:

- naming;
- estrutura de arquivos;
- padrões de importação;
- estratégia de erro;
- estilo de testes;
- composição de componentes;
- convenções de domínio;
- tooling já instalado.

Se o padrão existente for coerente e não violar uma decisão canônica, a IA deve segui-lo.

Se encontrar um padrão ruim ou conflitante, não deve criar silenciosamente um terceiro padrão. Deve corrigir de forma controlada ou registrar a necessidade de refatoração conforme o impacto.

```text
consistência local saudável
        >
invenção de um novo estilo a cada implementação
```

## 10.13. Anti-padrões típicos de código gerado por IA

A revisão deve procurar e remover sinais de geração automática sem curadoria, como:

- duplicação de lógica que já existia no repositório;
- criação de tipos equivalentes com nomes diferentes;
- arquivos gigantes gerados de uma vez;
- abstrações para cenários hipotéticos nunca solicitados;
- wrappers que apenas repassam argumentos sem responsabilidade real;
- `try/catch` genérico ao redor de grandes blocos;
- uso indiscriminado de `any`, casts ou supressões para silenciar o type system;
- comentários excessivos narrando sintaxe;
- funções chamadas `processData`, `handleData`, `helper`, `utils` sem semântica clara;
- código morto ou imports não utilizados;
- placeholders que parecem implementação concluída;
- TODOs sem rastreabilidade;
- criação de dependências desnecessárias;
- reescrita de arquivos inteiros quando uma alteração localizada resolveria;
- padrões diferentes para resolver o mesmo problema em arquivos próximos;
- tratamento feliz sem considerar estados de erro já previstos nos documentos;
- otimizações inventadas sem medir necessidade;
- código excessivamente genérico que aumenta custo cognitivo para uma necessidade simples.

A IA não recebe liberdade para "cuspir código" e deixar a organização para uma revisão futura.

Qualidade estrutural faz parte da própria entrega.

## 10.14. Contrato operacional da IA antes de escrever código

Antes de começar uma implementação, o agente deve executar mentalmente ou por tooling o seguinte ciclo:

```text
1. ler requisito e documentos de origem
        ↓
2. inspecionar módulo e código vizinho
        ↓
3. procurar componentes, tipos e funções reutilizáveis
        ↓
4. identificar convenções locais
        ↓
5. escolher a menor alteração coerente
        ↓
6. implementar seguindo naming, arquitetura e Clean Code
        ↓
7. criar/atualizar testes
        ↓
8. revisar o próprio diff como um reviewer humano experiente
        ↓
9. executar lint, typecheck, testes e gates aplicáveis
        ↓
10. remover redundância, código morto, debug e artefatos temporários
```

A velocidade de geração nunca possui precedência sobre a compreensibilidade da base.

## 10.15. Auto-revisão obrigatória do diff

Antes de considerar uma alteração pronta, a IA deve revisar o próprio diff perguntando:

- existe uma forma mais simples de expressar a mesma regra?
- criei algo que já existia?
- introduzi duplicação?
- algum nome está vago ou genérico?
- a função ou módulo possui mais de uma responsabilidade?
- existe comportamento implícito que deveria estar explícito?
- comentários explicam motivos ou apenas narram código?
- existe código morto, debug, placeholder ou TODO esquecido?
- introduzi uma dependência sem necessidade?
- alterei arquivos fora do escopo sem justificativa?
- os erros estão tratados de acordo com o projeto?
- a solução respeita boundaries arquiteturais?
- testes cobrem a regra e os casos de falha relevantes?
- existe impacto de desempenho óbvio?
- outro engenheiro entenderia este diff sem precisar conversar comigo?

Esse passo deve ser tratado como parte da implementação, não como atividade opcional.

## 10.16. Critério de qualidade humana

O objetivo não é tentar enganar detectores de IA ou imitar imperfeições humanas.

O objetivo é que uma revisão técnica não encontre os problemas normalmente associados a código automático sem curadoria.

Um reviewer humano não deveria concluir "isso foi feito por IA" por encontrar:

- naming genérico;
- comentários artificiais;
- abstrações sem necessidade;
- inconsistência com o projeto;
- duplicação evitável;
- código excessivo para um problema simples;
- dependências escolhidas sem contexto;
- ausência de tratamento de falhas;
- testes superficiais;
- performance negligenciada;
- arquivos reescritos sem motivo.

O código deve parecer pertencente ao projeto porque **segue as decisões, linguagem, convenções e qualidade do projeto**, independentemente de ter sido escrito por humano ou IA.

## 10.17. Definition of Done mínima para qualidade de código

Além dos critérios específicos da funcionalidade, uma alteração de código só deve ser considerada pronta quando, conforme aplicável:

- naming técnico está em inglês e revela intenção;
- comentários/docstrings técnicos estão em inglês e são realmente necessários;
- não existe duplicação evitável;
- abstrações possuem responsabilidade clara;
- código existente foi reaproveitado quando semanticamente adequado;
- nenhuma dependência nova foi adicionada sem justificativa;
- não existe código morto, debug ou import não utilizado;
- não existem erros silenciosamente ignorados;
- regras críticas possuem testes;
- correções de bugs possuem regressão quando viável;
- lint/format/typecheck/build/testes aplicáveis passam;
- boundaries arquiteturais são respeitadas;
- riscos óbvios de performance foram avaliados;
- o diff foi auto-revisado;
- a alteração pode ser compreendida sem depender da conversa que a originou.

## Regra para agentes

Quando uma tecnologia instalada possuir documentação local ou versão diferente do conhecimento de treinamento do modelo, a IA deve consultar a documentação correspondente à versão efetivamente instalada antes de escrever código.

A IA deve considerar o Documento 06 uma **restrição de execução**, não uma recomendação opcional. Se uma solicitação induzir código que viole os padrões definidos, o agente deve procurar uma implementação compatível ou explicitar o conflito antes de criar dívida silenciosa.

## Separação entre Técnicas e Engenharia

`06_Tecnicas_de_Desenvolvimento.md` define **como trabalhar no código**.

O Documento 07 define **quais propriedades técnicas o sistema precisa suportar e qual arquitetura responde a essas propriedades**.

Exemplo:

```text
Técnica:
TypeScript strict é obrigatório.

Engenharia:
O aplicativo precisa suportar uso offline e reconciliação posterior sem duplicar operações.

Arquitetura:
Persistência local + IDs de operação + comandos idempotentes + sincronização explícita.
```

---

# 11. Documento 07 — Engenharia e Arquitetura

## Pergunta central

> **Quais forças técnicas o produto precisa suportar e qual estrutura arquitetural consegue atendê-las com o menor conjunto de compromissos aceitáveis?**

## Objetivo

Converter requisitos de produto, UI e UX em requisitos de engenharia e, somente depois, em uma arquitetura implementável.

## Ordem obrigatória de raciocínio

```text
Produto
   ↓
Experiência
   ↓
Requisitos de engenharia
   ↓
Forças / restrições / atributos de qualidade
   ↓
Alternativas arquiteturais
   ↓
Decisão arquitetural
   ↓
Estrutura do repositório
   ↓
Fronteiras e contratos
   ↓
Inventário de necessidades de infraestrutura
```

A arquitetura é uma resposta às forças de engenharia. Não deve começar com uma tecnologia ou padrão favorito e tentar adaptar o produto a ele.

## 11.1. O que deve ser avaliado primeiro — Engenharia

A parte de engenharia deve responder:

> **Quais propriedades técnicas este produto precisa possuir para funcionar, evoluir e ser operado adequadamente?**

Deve avaliar, conforme aplicável:

### Produto e escala

- quantidade esperada de usuários;
- crescimento projetado;
- picos de utilização;
- volume de dados;
- volume de mídia;
- perfil de leitura e escrita;
- necessidade de realtime;
- necessidade de offline;
- processamento assíncrono;
- integrações.

### Qualidade

- disponibilidade;
- latência;
- consistência;
- tolerância a falhas;
- resiliência;
- testabilidade;
- manutenibilidade;
- observabilidade;
- reprodutibilidade;
- auditabilidade.

### Segurança e privacidade

- tipos de dados;
- dados sensíveis;
- autenticação;
- autorização;
- segregação;
- least privilege;
- retenção;
- backup;
- restore;
- superfícies de ataque;
- requisitos regulatórios quando aplicáveis.

### Operação

- tamanho e experiência da equipe;
- tolerância a complexidade operacional;
- frequência de deploy;
- necessidade de staging;
- rollback;
- suporte;
- custo de manutenção;
- necessidade de execução local.

### Evolução

- funcionalidades futuras previsíveis;
- extensibilidade;
- integrações futuras;
- possibilidade de separação de módulos;
- migrações previsíveis;
- portabilidade desejada.

A saída deve produzir forças de engenharia explicitamente identificadas, por exemplo:

```text
ENG-001 — Uma ação concluída offline não pode ser duplicada ao sincronizar.
ENG-002 — O frontend nunca pode possuir credenciais administrativas.
ENG-003 — A API precisa ser implantável sem obrigar novo build do frontend.
ENG-004 — O Beta será mantido por equipe pequena; baixa complexidade operacional é prioridade alta.
```

## 11.2. O que não deve ser escolhido antes dessa análise

Não escolher antecipadamente apenas por preferência:

```text
MVC
MVVM
Clean Architecture
Hexagonal
microservices
monorepo
Supabase
Cloud Run
Redis
Kafka
```

Esses nomes representam soluções possíveis. Primeiro deve existir o problema técnico que justifica a solução.

## 11.3. O que pertence à Arquitetura

Depois das forças de engenharia, a arquitetura responde:

> **Qual estrutura técnica satisfaz melhor essas forças?**

Deve definir, conforme aplicável:

- contexto do sistema;
- aplicações e superfícies;
- módulos;
- domínio;
- contratos;
- APIs;
- dados;
- autenticação e autorização;
- cache;
- offline;
- sincronização;
- eventos;
- filas;
- integrações;
- trust boundaries;
- fronteiras de dependência;
- requisitos não funcionais materializados em decisões;
- decisões arquiteturais importantes;
- alternativas rejeitadas.

## 11.4. Estratégia do repositório é decisão arquitetural

O Documento 07 deve decidir explicitamente:

- repositório único simples, monorepo ou polyrepo;
- justificativa da escolha;
- estrutura de diretórios;
- aplicações existentes;
- packages/libs compartilhados;
- localização do domínio;
- contratos compartilhados;
- design tokens compartilhados quando houver;
- migrations;
- infraestrutura como código quando existir;
- tooling;
- testes;
- documentação;
- fronteiras de importação;
- ownership lógico.

Perguntas úteis:

- Web e mobile compartilham domínio ou contratos?
- API e worker compartilham runtime?
- Existe necessidade de versionamento independente?
- Times diferentes precisam publicar componentes separadamente?
- Um único CI consegue validar todo o projeto adequadamente?
- O acoplamento de releases é benéfico ou prejudicial?
- Existem bibliotecas internas realmente compartilhadas?

Exemplo de monorepo possível:

```text
/apps
  /web
  /mobile
  /api
  /worker
/packages
  /domain
  /contracts
  /design-tokens
  /config
/supabase
/infra
/tooling
/docs
```

Esse exemplo não é template obrigatório. Uma única aplicação simples pode ficar melhor em:

```text
/src
/tests
/docs
```

A arquitetura deve evitar complexidade cerimonial.

## 11.5. Escolha do modelo arquitetural

A IA deve identificar candidatos coerentes e comparar alternativas quando houver decisão material.

Exemplos possíveis:

- MVC;
- MVVM;
- arquitetura em camadas;
- Clean Architecture;
- Hexagonal / Ports and Adapters;
- Modular Monolith;
- microservices;
- event-driven architecture;
- CQRS;
- arquitetura orientada a serverless;
- combinação controlada de padrões.

Não existe arquitetura universal desta metodologia.

Exemplo insuficiente:

```text
Usaremos Clean Architecture porque separa responsabilidades.
```

Exemplo adequado:

```text
O domínio precisa ser compartilhável entre web, mobile e testes sem depender de React,
Expo, banco ou HTTP. Por isso, regras de domínio serão isoladas em um package puro e
integrações entrarão por adapters. Não será adotada uma Clean Architecture cerimonial
completa; apenas as fronteiras que resolvem esse requisito serão utilizadas.
```

A decisão deve explicar quais forças resolve e quais custos introduz.

## 11.6. Comparação antes da decisão

Quando houver alternativas relevantes, a IA pode usar uma matriz de decisão:

| Critério | Peso | Opção A | Opção B | Opção C |
| --- | ---: | ---: | ---: | ---: |
| simplicidade inicial | | | | |
| testabilidade | | | | |
| isolamento de domínio | | | | |
| velocidade de desenvolvimento | | | | |
| operação | | | | |
| escala | | | | |
| custo de mudança | | | | |
| adequação à equipe | | | | |

A matriz existe para explicitar trade-offs, não para criar precisão matemática artificial.

## 11.7. Fronteiras devem ser verificáveis

Uma boa decisão arquitetural deve, quando possível, virar regra verificável.

```text
Decisão:
/packages/domain não depende de framework.

Verificação:
boundary check impede imports de React, Next, Expo ou SDKs de infraestrutura.
```

Outro exemplo:

```text
Decisão:
clientes nunca usam credenciais administrativas.

Verificação:
secret scanning + check de variáveis públicas + teste negativo.
```

Preferir:

```text
DECISÃO
   ↓
REGRA
   ↓
TESTE / CHECK
```

## 11.8. Decisões rejeitadas também devem ser registradas

Decisões arquiteturais relevantes podem usar ADR curto:

```markdown
### ADR-003 — Não adotar microservices no Beta

Status: aceita

Contexto:
Equipe pequena, domínio ainda em formação e baixo volume inicial.

Decisão:
Modular Monolith.

Motivos:
- menor custo operacional;
- transações simples;
- deploy único do backend;
- fronteiras modulares preservam opção de extração futura.

Revisitar quando:
- módulos precisarem escala independente;
- ownership por times mudar;
- frequência de deploy independente se tornar requisito.
```

Isso impede que um agente futuro reabra decisões sem contexto.

## 11.9. Saída obrigatória para a etapa de infraestrutura

O Documento 07 deve terminar com um inventário de necessidades sem escolher silenciosamente provedores.

Exemplo:

```text
INF-NEED-001 — PostgreSQL gerenciado com backup.
INF-NEED-002 — Auth com e-mail e recuperação de conta.
INF-NEED-003 — Hosting web com CDN.
INF-NEED-004 — Runtime stateless para API.
INF-NEED-005 — Runtime privado para worker.
INF-NEED-006 — Armazenamento privado.
INF-NEED-007 — CI/CD.
INF-NEED-008 — Secrets manager.
INF-NEED-009 — Observabilidade.
```

Arquitetura define **o que tecnicamente precisamos**. A etapa seguinte define **onde e com quais serviços essas necessidades serão executadas**.

## Critério de qualidade do Documento 07

O Documento 07 está maduro quando outra IA consegue lê-lo e montar a estrutura inicial do projeto sem inventar o modelo arquitetural, o tipo de repositório, as fronteiras ou a intenção dos módulos.

---

# 12. Infraestrutura e Plano de Fundação

## Pergunta central

> **Onde e com quais serviços a arquitetura aprovada será executada, considerando crescimento, custo, segurança e operação desejada pelo humano?**

## Objetivo

Transformar o inventário de necessidades produzido pelo Documento 07 em uma infraestrutura pesquisada, aprovada e executável pelos itens FND do backlog.

A separação é:

```text
ENGENHARIA
"Quais propriedades técnicas precisamos suportar?"
        ↓
ARQUITETURA
"Como o software será estruturado para suportá-las?"
        ↓
INFRAESTRUTURA
"Onde e com quais serviços essa arquitetura será executada?"
        ↓
FUNDAÇÃO
"Crie e valide o ambiente necessário."
```

## 12.1. A IA deve entrevistar o humano

Infraestrutura não deve ser escolhida somente por preferência técnica do agente.

A entrevista deve ser curta e adaptada ao projeto.

### Natureza do produto

Perguntar, conforme aplicável:

- É protótipo, ferramenta interna, projeto pessoal ou produto comercial?
- Existe expectativa de muitos usuários no futuro?
- Há previsão de crescimento rápido?
- Haverá usuários externos desde o início?
- Existem dados pessoais, financeiros, médicos, profissionais ou outros dados sensíveis?
- Qual disponibilidade é esperada?

### Estratégia de custo

- Quer começar com custo zero quando possível?
- Aceita pagar desde a Fundação?
- Existe orçamento mensal aproximado?
- Prefere custo mínimo agora ou menos migração futura?
- Free tiers com limites são aceitáveis?
- Recursos pagos exigem aprovação individual?

**Regra:** contratação, upgrade de plano ou criação de recurso que possa gerar cobrança exige aprovação humana explícita.

### Local versus cloud

- Prefere começar somente em `localhost`?
- Quer staging em nuvem desde o início?
- Precisa compartilhar o ambiente com outras pessoas?
- A máquina local pode fazer parte da operação?

A IA deve explicar consequências.

```text
localhost
+ custo potencialmente menor
+ simplicidade inicial
- difícil compartilhar
- depende da máquina do usuário
- não comprova comportamento real de cloud

cloud / staging
+ ambiente reproduzível
+ acesso remoto
+ valida integrações reais
+ permite CI/CD e evidência operacional
- pode exigir contas, setup e eventualmente custo
```

### Operação

- Prefere serviços gerenciados?
- Existe equipe de DevOps?
- Quer reduzir o número de provedores?
- Deseja evitar lock-in mesmo com maior complexidade?
- Já possui provedores aprovados?

### Capacidades

Perguntar quando relevante sobre:

- realtime;
- offline;
- arquivos/mídia;
- e-mail/push/SMS/WhatsApp;
- workers;
- filas/eventos;
- scheduler;
- processamento pesado;
- IA;
- busca;
- região;
- backup/restore;
- logs/métricas/alertas.

## 12.2. Pesquisa web atual é obrigatória

Preços, free tiers, quotas, regiões, planos e produtos mudam.

Antes de recomendar infraestrutura para um novo projeto, a IA deve pesquisar informações atuais, preferencialmente em fontes oficiais:

1. documentação oficial;
2. pricing oficial;
3. quotas e limits;
4. regiões;
5. segurança/compliance quando relevante;
6. SLA/status quando necessário.

A pesquisa deve responder:

- o serviço continua disponível?
- existe free tier ou crédito inicial?
- quais limites afetam o projeto?
- quando começa a cobrança?
- a região necessária existe?
- existe alternativa mais simples?
- possui API/CLI/IaC?
- existem restrições relevantes para produção?

Nunca canonizar simplesmente:

```text
"Esse serviço é grátis."
```

Preferir:

```text
"Na pesquisa realizada em AAAA-MM-DD, o provedor oferecia camada gratuita
com os seguintes limites relevantes [...]. Revalidar antes da contratação."
```

## 12.3. A IA deve comparar alternativas

Quando houver mais de uma opção razoável, apresentar de duas a quatro alternativas.

| Critério | Opção A | Opção B | Opção C |
| --- | --- | --- | --- |
| custo inicial | | | |
| camada gratuita | | | |
| facilidade de setup | | | |
| operação | | | |
| escala | | | |
| automação | | | |
| lock-in | | | |
| regiões | | | |
| adequação ao projeto | | | |

A recomendação deve explicar por que a alternativa escolhida combina com as respostas do humano e com as necessidades arquiteturais.

## 12.4. Perfil de infraestrutura de referência

A metodologia pode sugerir como ponto de partida, quando compatível e após revalidação atual:

- **GitHub** — repositório, pull requests e CI;
- **Supabase** — PostgreSQL gerenciado, autenticação e recursos de backend quando adequados;
- **Cloudflare Pages ou hosting web gerenciado equivalente** — frontend quando compatível;
- **Google Cloud Run ou runtime serverless/containerizado equivalente** — APIs e workers quando necessários;
- **GitHub Actions** — quality gates e automação de entrega;
- **Terraform ou IaC equivalente** — quando a complexidade justificar;
- **Playwright** — E2E, validação visual e setup humano-assistido quando apropriado.

Esse perfil é referência, não obrigação.

Nunca escolher a stack apenas porque ela foi usada em outro projeto.

## 12.5. O plano deve mapear a infraestrutura completa

Conforme aplicável, documentar:

### Repositório e entrega

- provedor Git;
- branches;
- proteções;
- CI;
- estratégia de promoção.

A **estrutura lógica do repositório** já foi decidida no Documento 07. Aqui são definidos os serviços operacionais ligados a ele.

### Ambientes

- local;
- development remoto, se existir;
- staging;
- production;
- segregação entre ambientes.

### Frontend

- provedor;
- região quando aplicável;
- build;
- domínio;
- variáveis públicas;
- CDN/cache.

### Backend/API

- runtime;
- provedor;
- escalabilidade;
- exposição pública/privada;
- health checks;
- secrets;
- logs.

### Banco de dados

- tecnologia;
- provedor;
- instância/projeto;
- ambientes;
- migrations;
- backup;
- restore;
- região;
- modelo de acesso;
- política de credenciais.

### Autenticação

- provedor;
- métodos habilitados;
- SMTP/e-mail quando necessário;
- redirect URLs;
- MFA quando aplicável;
- separação de chaves públicas e privadas.

### Storage e mídia

- provedor;
- buckets;
- acesso público/privado;
- limites;
- retenção.

### Workers, jobs, filas e eventos

- necessidade;
- runtime;
- scheduler;
- fila;
- retry;
- DLQ quando aplicável;
- idempotência.

### Observabilidade

- logs;
- métricas;
- erros;
- alertas;
- tracing quando necessário.

### Segurança

- secrets manager;
- IAM;
- least privilege;
- scanning;
- backups;
- exposição de serviços;
- segregação de ambiente.

### Custos

- recursos gratuitos;
- recursos potencialmente cobrados;
- gatilhos de upgrade;
- alertas/budget quando disponíveis;
- aprovações necessárias para escalar.

## 12.6. O plano gera a Fundação — FND

Depois da aprovação da infraestrutura, o Documento 08 deve transformar o plano em habilitadores FND.

Exemplo:

```text
FND-001 — Criar repositório e proteção básica
FND-002 — Fixar toolchain e lockfile
FND-003 — Configurar CI inicial
FND-004 — Criar projeto de banco de staging
FND-005 — Configurar migrations
FND-006 — Criar aplicação web de staging
FND-007 — Criar API de staging
FND-008 — Configurar secrets
FND-009 — Configurar autenticação mínima
FND-010 — Criar observabilidade mínima
FND-011 — Validar backup/restore aplicável
FND-012 — Smoke test da fundação
```

Os IDs reais devem ser derivados das necessidades do projeto.

FND não termina quando as contas foram criadas. Termina quando existe evidência de que o ambiente está utilizável.

```text
repositório criado
+
CI executando
+
banco acessível pelo mecanismo aprovado
+
migrations funcionando
+
serviços implantados
+
segredos fora do código
+
staging acessível
+
smoke tests aprovados
+
rastreabilidade reconciliada
=
FUNDAÇÃO OPERACIONAL
```

## 12.7. Automação do setup

A prioridade deve ser:

```text
API / CLI / IaC oficial
        ↓ se insuficiente
conector autorizado / OAuth
        ↓ se insuficiente
Playwright em sessão autenticada pelo humano
        ↓ se bloqueado
passo a passo manual seguro
```

Playwright é útil para:

- abrir o painel correto;
- navegar depois de autenticação humana;
- configurar opções não expostas por API;
- validar visualmente o ambiente;
- executar smoke/E2E;
- reduzir trabalho manual repetitivo.

Não deve ser usado para contornar controles de segurança.

## 12.8. Login e credenciais — humano no circuito

Se uma etapa exigir login, MFA, CAPTCHA, aceite legal, compra, cartão ou visualização única de segredo, a automação deve devolver essa ação ao humano.

Fluxo:

```text
Agente abre/prepara a página
        ↓
Humano faz login diretamente no provedor
        ↓
Humano conclui MFA/CAPTCHA/aceite quando necessário
        ↓
Agente continua na sessão já autorizada
```

O usuário não deve enviar pelo chat:

- senhas;
- service role keys;
- private keys;
- API secrets;
- refresh tokens;
- recovery codes;
- tokens permanentes;
- dados de cartão.

Quando um segredo precisar ser criado, preferir armazená-lo diretamente no secret manager, GitHub Secrets ou mecanismo equivalente, sem fazê-lo transitar pelo chat.

Se a IA não conseguir concluir uma etapa, deve fornecer um mini-runbook seguro dizendo:

- qual painel abrir;
- qual menu acessar;
- onde clicar;
- o que criar ou selecionar;
- qual valor não sensível preencher;
- o que **não** copiar para o chat;
- como confirmar que a etapa terminou;
- qual evidência segura permite continuar.

## 12.9. Custos exigem aprovação explícita

Classificar ações de infraestrutura como:

```text
GRATUITA / FREE TIER
POTENCIALMENTE COBRÁVEL
COBRÁVEL
DESCONHECIDA — REVALIDAR
```

Se houver dúvida, tratar como potencialmente cobrável.

O agente não pode contratar, fazer upgrade ou criar recurso que possa gerar cobrança sem informar finalidade, modelo de cobrança conhecido e obter aprovação humana explícita.

---

# 13. Documento 08 — Backlog Canônico, Rastreabilidade e Plano de Entrega

## Pergunta central

> **Exatamente o que deve ser construído, em qual ordem e como provar que está pronto?**

## Objetivo

Transformar toda a baseline documental em unidades executáveis pelo Codex.

## Identificadores permanentes

Cada item deve receber um ID estável, por exemplo:

```text
FND-001
AUTH-003
TRN-014
UX-008
SEC-002
```

## Cada item deve conter

- ID;
- título;
- tipo;
- origem documental;
- objetivo;
- descrição;
- critérios de aceite;
- dependências;
- riscos;
- testes necessários;
- evidência necessária;
- status.

## Exemplo

```text
TRN-014

Origem:
D02 §8.3
D03 §5.2
D05 §12.4

Objetivo:
Permitir conclusão individual de cada série.

Critérios:
AC-01 ...
AC-02 ...
AC-03 ...

Testes:
TEST-TRN-014-01
TEST-TRN-014-02
```

Não criar itens vagos como "implementar tela de treino" quando o comportamento esperado puder ser dividido em requisitos verificáveis.

## Fundação deve aparecer explicitamente no backlog

Os itens `FND-*` representam setup e habilitadores técnicos, não funcionalidades de produto.

Eles devem ser derivados conjuntamente de:

```text
06 Técnicas de Desenvolvimento
        +
07 Engenharia e Arquitetura
        +
Infraestrutura e Plano de Fundação
        ↓
FND do Backlog
```

A implementação funcional deve iniciar sobre uma Fundação considerada pronta ou sobre uma exceção explicitamente documentada.

---

# 14. Documento 09 — Matriz Operacional de Rastreabilidade

## Pergunta central

> **Onde cada requisito foi implementado, testado e comprovado?**

## Objetivo

Conectar requisito, código, testes, evidência e estado de entrega.

## Exemplo

| ID | Origem | Requisito | Implementação | Testes | Evidência | Status |
| --- | --- | --- | --- | --- | --- | --- |
| AUTH-001 | D02 §7 | Criar conta | `auth/...` | `AUTH-T01` | CI + staging | Done |
| TRN-014 | D05 §12 | Concluir série | — | `TRN-T04` | — | Planned |
| SEC-003 | D07 §9 | Sessão segura | `security/...` | `SEC-T03` | CI | Done |

A matriz deve ser legível por IA e mantida em Markdown sempre que possível.

---

# 15. Governança portátil por Skills e Agents

A metodologia não deve depender de frameworks privados ou nomes exclusivos de uma máquina.

Ela deve documentar **as capacidades necessárias** para que outro ambiente compatível possa recriá-las como skills, agents, comandos, checks ou automações equivalentes.

```text
PROCESSO CANÔNICO
        ↓
define capacidades
        ↓
SKILLS
habilidades reutilizáveis e pequenas
        ↓
AGENTS
orquestram responsabilidades maiores
```

## 15.1. Skill x Agent

### Skill

Uma skill é uma habilidade reutilizável com gatilho, entradas, regras, saída e limites claros.

Exemplos:

- verificar consistência documental;
- comparar screenshot com referência;
- detectar padrão de bug recorrente;
- validar fronteiras arquiteturais.

### Agent

Um agent é um papel operacional que coordena documentos, ferramentas e várias skills para alcançar um objetivo maior.

Exemplos:

- conduzir a Fundação;
- executar uma fatia do backlog;
- revisar uma release;
- auditar arquitetura;
- revisar qualidade visual.

## 15.2. Skill recomendada — `document-consistency`

### Objetivo

Manter documentação, backlog, matriz, código, testes e evidências coerentes entre si.

Deve verificar, conforme aplicável:

- documentos canônicos;
- backlog;
- matriz de rastreabilidade;
- Issues relevantes;
- código alterado;
- testes;
- CI/staging;
- documentação derivada.

Não permitir inconsistências como:

```text
Backlog = Done
Matriz = Planned
Teste = inexistente
Staging = sem evidência
```

Também deve detectar:

- implementação que contradiz arquitetura;
- UI que contradiz Princípios;
- backlog sem origem documental;
- requisito removido ainda tratado como ativo;
- documento descrevendo comportamento inexistente;
- código entregue sem atualização de rastreabilidade.

A skill não pode mascarar um bug atualizando o documento automaticamente para combinar com o runtime incorreto. Antes deve determinar qual camada possui precedência.

## 15.3. Skill recomendada — `backlog-evidence-audit`

### Objetivo

Determinar se um item foi realmente entregue.

```text
requisito
   ↓
critérios de aceite
   ↓
implementação existe?
   ↓
testes cobrem critérios?
   ↓
gates aprovados?
   ↓
staging é necessário e foi validado?
   ↓
evidência é suficiente?
```

Estados úteis:

```text
NOT_STARTED
IN_PROGRESS
IMPLEMENTED_NOT_VALIDATED
VALIDATED
BLOCKED
```

Não inferir `VALIDATED` apenas porque existe commit.

## 15.4. Skill recomendada — `architecture-conformance`

### Objetivo

Transformar decisões do Documento 07 em verificações recorrentes.

Exemplo:

```text
Decisão:
packages/domain não depende de frameworks.

Skill:
verifica imports proibidos.
```

Outro exemplo:

```text
Decisão:
cliente não possui segredo administrativo.

Skill:
verifica variáveis públicas, bundles e padrões de secrets.
```

Quando uma decisão ainda não possuir check automatizável, a skill deve registrar a lacuna como oportunidade de tooling.

## 15.5. Skill recomendada — `foundation-readiness`

### Objetivo

Determinar se a Fundação está realmente pronta para receber funcionalidades.

Pode verificar:

- estrutura do repo conforme arquitetura;
- toolchain;
- lockfile;
- CI;
- branches/proteções quando acessíveis;
- banco;
- migrations;
- auth mínima;
- serviços;
- secrets;
- staging;
- observabilidade mínima;
- smoke tests;
- rastreabilidade operacional.

Resultado:

```text
FND_READY
FND_PARTIAL
FND_BLOCKED
```

## 15.6. Skill de aprendizado — `discover-to-skill`

### Objetivo

Detectar quando um conhecimento descoberto durante uma ocorrência no projeto possui valor suficiente para virar habilidade reutilizável.

A finalidade é reduzir retrabalho, contexto repetido e gasto de tokens em problemas já compreendidos.

Um evento é candidato quando, por exemplo:

- o mesmo bug ocorreu novamente;
- o mesmo diagnóstico exige raciocínio extenso repetidamente;
- um setup é realizado de forma semelhante em vários projetos;
- existe erro previsível que pode ser detectado antes de build/deploy;
- uma regra de revisão se repete;
- a correção pode virar check determinístico;
- um incidente revelou uma classe de problema, e não apenas um caso isolado.

Fluxo:

```text
ocorrência real
        ↓
IA resolve
        ↓
há valor de reutilização?
        ↓
procurar skill/check existente
        ↓
registrar Issue com causa e prevenção
        ↓
acionar mecanismo de criação de skill disponível
        ↓
criar teste/check quando possível
        ↓
executar consistência documental
```

Exemplo:

```text
Bug reaparece em migrations
        ↓
IA reconhece a mesma causa raiz
        ↓
correção novamente consome contexto e tokens
        ↓
discover-to-skill classifica como reutilizável
        ↓
registra Issue
        ↓
registra causa, detecção e prevenção
        ↓
cria skill/check/teste
        ↓
próxima ocorrência pode ser detectada antes
```

Antes de criar uma nova skill, verificar se já existe capacidade equivalente.

Nem todo bug deve virar skill. Problema isolado, improvável de repetir e sem valor geral permanece como correção normal.

Pergunta de decisão:

> **Se esse evento ocorrer novamente, queremos que a IA gaste praticamente o mesmo raciocínio para resolvê-lo?**

Se a resposta for não, existe candidato para skill, check, runbook ou automação.

### Issue como memória operacional

Uma ocorrência reutilizável pode ser registrada em Issue com estrutura semelhante a:

```markdown
## Problema recorrente

## Sintoma

## Causa raiz

## Como detectar

## Como corrigir

## Como prevenir

## Onde ocorreu

## Potencial de automação
```

A Issue funciona como memória auditável do incidente, não como substituto da documentação canônica.

## 15.7. Skill visual — `visual-reference-to-spec`

### Objetivo

Transformar uma referência visual em informação estruturada e comparar essa referência com a UI real do projeto.

Pode receber:

- screenshot;
- wireframe;
- aplicativo de referência;
- tela aprovada;
- protótipo visual.

Primeiro deve decompor a referência, conforme observável:

- arquitetura da informação;
- hierarquia;
- tarefa mental aparente;
- densidade;
- espaçamento;
- alinhamento;
- grid;
- tipografia relativa;
- superfícies;
- navegação;
- posição de CTAs;
- ações secundárias;
- estados;
- padrões de componentes;
- sinais de marca.

Depois deve cruzar a referência com:

- `Principios_de_UX_UI.md`;
- Documento 04;
- Design System;
- tarefa mental da tela.

A referência visual não possui precedência automática sobre os princípios do produto.

Por fim, deve comparar a referência com screenshot da implementação e gerar delta objetivo:

| Aspecto | Referência | Implementação | Delta | Severidade |
| --- | --- | --- | --- | --- |
| CTA | persistente inferior | topo | viola direção | alta |
| densidade | baixa | cards aninhados | excessiva | alta |
| tipografia | hierarquia clara | pesos semelhantes | fraca | média |

A saída deve explicar **o que mudar e por quê**, relacionando a correção às decisões canônicas. Não apenas dizer "deixe igual à imagem".

Referências externas servem para inspiração e análise de padrões. A skill deve evitar copiar cegamente identidade proprietária, assets ou textos distintivos quando o objetivo é construir identidade própria.

## 15.8. Skills complementares

### `issue-to-knowledge`

Converte Issues relevantes encerradas em conhecimento persistente quando houver valor além do ticket, podendo gerar:

- runbook;
- ADR;
- check;
- teste de regressão;
- atualização de arquitetura;
- atualização de técnicas;
- nova skill.

Nem toda Issue exige nova documentação.

### `ui-principles-audit`

Revisa uma tela contra os princípios específicos da aplicação, avaliando:

- tarefa mental dominante;
- competição entre CTAs;
- densidade;
- linguagem;
- visibilidade da ação principal;
- exposição de ações destrutivas;
- consistência com a personalidade da marca;
- comportamento responsivo;
- sinais de UI genérica.

Os achados devem ser relacionados a princípios identificáveis, não ao gosto subjetivo do agente.

## 15.9. Agents recomendados

### `document-steward-agent`

Coordena consistência documental, reconciliação de status, precedência e ausência de fontes concorrentes.

Pode usar `document-consistency`, `backlog-evidence-audit` e `issue-to-knowledge`.

### `architecture-review-agent`

Revisa forças de engenharia, alternativas arquiteturais, estrutura de repo, boundaries, ADRs e conformidade arquitetural.

### `foundation-orchestrator-agent`

Consome Técnicas + Engenharia/Arquitetura + Infraestrutura + itens FND e conduz o setup, respeitando gates humanos para autenticação, custo e ações destrutivas.

### `backlog-implementation-agent`

Executa uma fatia canônica do backlog, lê origens documentais, implementa, testa, produz evidência e atualiza rastreabilidade.

### `visual-quality-agent`

Coordena análise de referência, princípios, Documento 04, screenshots e correções de fidelidade/identidade.

### `release-audit-agent`

Valida se uma release possui critérios, testes, gates, staging, evidência e rastreabilidade suficientes antes da promoção.

## 15.10. Regra de portabilidade

A metodologia define o comportamento esperado das capacidades, não a implementação privada de uma máquina.

Cada ambiente pode implementá-las por skills, agents, comandos ou checks equivalentes, desde que preserve o contrato de comportamento e os gates humanos definidos aqui.

---

# 16. Documentação de segunda geração

Os documentos 01 a 09 formam a baseline inicial, mas não representam toda a documentação que um projeto terá durante sua vida.

Durante a implementação podem surgir artefatos derivados, por exemplo:

```text
docs/api/
docs/data/
docs/security/
docs/governance/
docs/runbooks/
docs/adr/
```

Exemplos de documentos derivados:

- contratos de API;
- dicionário de dados;
- matriz RLS;
- threat models;
- contratos de ambiente;
- runbooks;
- políticas de dependência;
- decisões arquiteturais;
- filas e eventos;
- inventários operacionais;
- observabilidade;
- restore e contingência.

Esses documentos devem nascer quando o conhecimento se torna necessário, e não apenas para preencher uma lista antecipadamente.

Skills de consistência e descoberta podem sugerir ou produzir esses artefatos quando houver justificativa, mas não devem criar documentação por burocracia.

---

# 17. Documentação deve se transformar em contrato executável quando possível

O padrão desejado é:

```text
DECISÃO
   ↓
DOCUMENTO
   ↓
CONTRATO
   ↓
TESTE
   ↓
GATE
   ↓
EVIDÊNCIA
```

Exemplo:

```text
Arquitetura:
"o cliente não acessa schemas privados"
        ↓
regra de boundary / segurança
        ↓
check automatizado
        ↓
CI falha se a regra for violada
```

Outro exemplo:

```text
Contrato de dados:
"toda superfície exposta deve possuir política de autorização"
        ↓
migration
        ↓
teste negativo
        ↓
gate de contrato de dados
```

A documentação deixa de ser somente descritiva e passa a participar da qualidade do software.

---

# 18. Três níveis de verdade

O processo trabalha com três níveis complementares:

| Camada | Fontes principais | Pergunta |
| --- | --- | --- |
| Verdade de Produto | Docs 01–05 | O que o produto deve fazer e por quê? |
| Verdade de Engenharia | Docs 06–07 + Infraestrutura + derivados | Como isso deve funcionar tecnicamente? |
| Verdade de Execução | Docs 08–09 + código + testes + CI | O que foi realmente entregue e comprovado? |

Exemplo:

```text
Produto: requisito esperado
Código: ainda inexistente
→ trabalho pendente
```

Diferente de:

```text
Arquitetura: RLS obrigatória
Runtime: tabela exposta sem RLS
→ gap de conformidade
```

---

# 19. Execução pelo Codex

Depois da canonização da baseline, o Codex não deve receber apenas um prompt genérico para "construir o sistema".

Ele deve trabalhar dentro de um universo de decisões previamente definido.

```text
O que construir       → Produto
Como decidir          → PO + Princípios
Como deve parecer     → UI + Design System
Como deve funcionar   → UX
Como programar        → Técnicas
O que precisa suportar→ Engenharia
Como estruturar       → Arquitetura
Onde executar         → Infraestrutura
Em que ordem          → Backlog
Como provar           → Rastreabilidade + testes
Quando reconciliar    → skills/agents de governança
Quando terminou       → Gates + staging
```

## Fundação antes das funcionalidades

O Codex deve consumir os itens `FND-*` do backlog como uma fase explícita de Fundação/Setup.

FND pode incluir:

- estrutura do repositório;
- runtimes e package manager;
- CI/CD;
- banco;
- migrations;
- autenticação;
- storage;
- API/worker;
- secrets;
- staging;
- observabilidade;
- backup/restore;
- quality gates;
- smoke tests.

A Fundação deriva de:

```text
06 Técnicas
+
07 Engenharia e Arquitetura
+
Infraestrutura e Plano de Fundação
        ↓
Itens FND do Backlog
```

O Codex não deve escolher silenciosamente provedores nem contratar recursos durante a execução da Fundação.

## Fluxo esperado de cada fatia

```text
Selecionar item canônico do backlog
        ↓
Ler origens documentais
        ↓
Verificar dependências e princípios
        ↓
Implementar a menor fatia coerente
        ↓
Criar/atualizar testes
        ↓
Executar gates locais
        ↓
Executar checks/skills aplicáveis
        ↓
Atualizar rastreabilidade
        ↓
Publicar em staging
        ↓
Validar evidências
        ↓
Promover
```

---

# 20. Quality Gates

Cada projeto define seus gates concretos no Documento 06, mas a metodologia espera, quando aplicável:

- format check;
- lint;
- typecheck;
- testes unitários;
- testes de integração;
- testes de contrato;
- testes negativos de segurança;
- build;
- verificação de secrets;
- auditoria de dependências;
- verificação de boundaries;
- smoke tests;
- migrações verificadas;
- validação de infraestrutura;
- conformidade arquitetural;
- consistência documental;
- auditoria de evidência do backlog.

Um item não deve ser considerado entregue apenas porque existe código.

---

# 21. Staging como parte da definição de pronto

A implementação deve ser comprovada em ambiente representativo antes da promoção final quando a natureza do projeto permitir.

```text
CODE EXISTS
≠
DELIVERED
```

E também:

```text
CODE + TESTS PASS
≠
DELIVERED
```

O estado desejado é:

```text
IMPLEMENTADO
+
TESTADO
+
CI APROVADO
+
STAGING VALIDADO
+
RASTREABILIDADE ATUALIZADA
=
ENTREGUE
```

Quando o projeto adotar promoção staging-first, o mesmo artefato ou SHA validado deve ser promovido sempre que possível, evitando reconstruir um candidato diferente do que foi efetivamente testado.

---

# 22. Identidade de produto e prevenção do "visual de IA"

Uma aplicação construída por IA não deve parecer uma composição genérica de componentes populares.

Evitar o padrão automático:

```text
Dashboard
Cards
Sidebar
Modal
Toast
Botão padrão
Tabela padrão
```

sem justificativa de produto.

O processo exige que as decisões de interface sejam derivadas de:

```text
IDENTIDADE DA MARCA
        +
PRINCÍPIOS DE UX/UI
        +
TAREFA MENTAL
        +
CONTEXTO
        +
JORNADA
        ↓
DECISÃO DE INTERFACE
        ↓
DESIGN SYSTEM
        ↓
IMPLEMENTAÇÃO
```

O mesmo agente pode desenvolver produtos diferentes, mas cada produto precisa preservar sua identidade própria.

A capacidade `visual-reference-to-spec` complementa esse processo quando existir referência visual, mas a referência não substitui os princípios nem a identidade canônica do produto.

---

# 23. Estrutura recomendada para documentos canônicos

Quando fizer sentido, documentos podem usar metadados simples no início:

```yaml
---
document_id: DOC-07
title: Engenharia e Arquitetura
status: canonical
version: 1.0.0
depends_on:
  - DOC-02
  - DOC-03
  - DOC-05
  - DOC-06
governs:
  - engineering
  - architecture
  - infrastructure-needs
  - security
---
```

A finalidade é facilitar leitura e governança por humanos e agentes.

O versionamento principal continua sendo o Git. Não criar burocracia documental que não gere valor.

---

# 24. Critério de canonização

Um documento pode ser considerado canônico quando:

1. possui responsabilidade clara;
2. não mistura hipóteses com decisões sem identificá-las;
3. não contradiz documentos de precedência superior;
4. possui escopo e não escopo compreensíveis;
5. pode ser interpretado sem depender da conversa original de Discovery;
6. utiliza linguagem suficientemente objetiva para humanos e agentes;
7. identifica pendências relevantes;
8. está versionado em Git;
9. pode originar requisitos rastreáveis quando aplicável;
10. foi revisado e aprovado pelo humano responsável antes de alimentar a próxima camada.

---

# 25. Regra de precedência

Em caso de aparente conflito, a resolução deve considerar a natureza da decisão.

Exemplo de precedência conceitual:

```text
Pesquisa / evidência
        ↓
Briefing / escopo
        ↓
Visão do PO
        ↓
Princípios de UX/UI
        ↓
Direção UI + UX
        ↓
Técnicas
        ↓
Engenharia
        ↓
Arquitetura
        ↓
Infraestrutura
        ↓
Backlog
        ↓
Implementação
```

Uma implementação não altera silenciosamente uma decisão de produto.

Se o runtime demonstrar que a decisão anterior é inviável ou inadequada, deve haver reconciliação documental antes de tratar a divergência como novo padrão.

Uma skill de consistência pode apontar a divergência, mas não deve resolver conflito de precedência simplesmente fazendo o documento combinar com o runtime.

---

# 26. Processo completo resumido

```text
┌─────────────────────────────────────────────┐
│                DISCOVERY                    │
│ conversa, pesquisa, hipóteses e decisões    │
└──────────────────────┬──────────────────────┘
                       │ Discovery Freeze
                       ▼
              01 Pesquisa e Viabilidade
                       │ aprovação humana
                       ▼
              02 Briefing e Escopo
                       │ aprovação humana
                       ▼
              03 Visão de Product Owner
                       │ aprovação humana
                       ▼
             Princípios de UX/UI
                       │ aprovação humana
             ┌─────────┴─────────┐
             ▼                   ▼
      04 Direção de UI      05 Especificação UX
      + Design System       + jornadas/user stories
             └─────────┬─────────┘
                       │ aprovação humana
                       ▼
              06 Técnicas de Desenvolvimento
                       │ aprovação humana
                       ▼
              07 Engenharia e Arquitetura
                       │
                       ▼
          inventário de necessidades técnicas
                       │
                       ▼
       entrevista + pesquisa de infraestrutura
                       │ aprovação humana
                       ▼
       Infraestrutura e Plano de Fundação
                       │
                       ▼
              08 Backlog Canônico
                       ▼
              09 Matriz Operacional
                       ▼
                     CODEX
                       ▼
               FND — Fundação / Setup
                       ▼
              implementação por fatia
                       ▼
               testes + quality gates
                       ▼
          skills/checks de consistência
                       ▼
              documentação derivada
                       ▼
                   STAGING
                       ▼
                 evidências
                       ▼
                  promoção
                       ▼
             rastreabilidade atualizada
                       │
                       ▼
         conhecimento reutilizável detectado?
                 │              │
                não            sim
                 │              ▼
                 │       Issue / check / skill
                 └──────────────┘
```

---

# 27. Resultado esperado

Este processo existe para produzir software em que:

- a intenção do produto não dependa da memória da conversa com a IA;
- documentos sejam gerados e aprovados progressivamente, sem propagação silenciosa de erro;
- decisões de experiência possuam princípios claros;
- UI e UX tenham identidade própria;
- tarefas mentais e jornadas sejam especificadas separadamente;
- técnicas de desenvolvimento sejam distinguidas de forças de engenharia;
- engenharia preceda escolhas arquiteturais;
- arquitetura defina modelo, fronteiras e estrutura do repositório por justificativa, não por hábito;
- infraestrutura seja pesquisada e aprovada depois do dimensionamento arquitetural;
- custo, contratação e credenciais permaneçam sob controle humano;
- o backlog possua origem documental;
- a Fundação prepare e prove o ambiente antes das funcionalidades;
- testes comprovem critérios de aceite;
- documentação evolua junto com o código;
- skills e agents portáveis mantenham consistência, conformidade e aprendizado sem depender de frameworks privados;
- conhecimento recorrente possa virar Issue, check, teste, runbook ou skill reutilizável;
- referências visuais sejam traduzidas em critérios objetivos sem apagar a identidade do produto;
- staging produza evidência operacional;
- a IA consiga trabalhar com autonomia sem inventar silenciosamente o produto.

A metodologia pode ser resumida em uma frase:

> **A IA não recebe apenas uma tarefa para programar; ela recebe um sistema de decisões canônicas que transforma intenção humana em software verificável, operável e progressivamente mais inteligente.**

---

# 28. Ativação da Engine no ChatGPT e handoff para o Codex

## Pergunta central

> **Como carregar este processo integralmente em uma conversa do ChatGPT, conduzir a geração documental com aprovação humana e depois transferir a execução para o Codex sem perder as decisões canônicas?**

## Objetivo

Transformar este `README.md` em um protocolo reutilizável que possa ser carregado em uma conversa já iniciada com o ChatGPT e usado como **engine operacional do processo**.

A ativação não instala software dentro do ChatGPT e não altera permanentemente o comportamento global da conta. Ela significa que, **na conversa atual**, o ChatGPT deve ler integralmente a versão canônica desta metodologia, construir um mapa operacional de seus tópicos e passar a utilizá-los como regras de condução do projeto.

Em uma nova conversa, a chave de ativação deve ser executada novamente.

## 28.1. Requisito mínimo para ativação

A engine não exige que o usuário já possua requisitos completos, arquitetura ou documentação.

O requisito mínimo é que tenha existido **Discovery conversacional suficiente para existir uma ideia de produto minimamente compreensível**.

Exemplo de estágio aceitável:

```text
Usuário:
"Quero criar uma comunidade onde pessoas possam registrar golpes que descobriram,
discutir como eles funcionam e se manter informadas sobre novos golpes. O que acha?"

ChatGPT:
analisa problema, utilidade, riscos, referências e perguntas.

Usuário:
"E se adicionarmos X?"

ChatGPT:
explora impacto.

Usuário:
"E se mudarmos Y?"

ChatGPT:
compara alternativas.
```

Isso já pode fornecer matéria-prima suficiente para acionar o processo.

Não é necessário que a conversa tenha produzido documentos.

Se a engine concluir que ainda não existe contexto mínimo para produzir uma Pesquisa e Viabilidade responsável, ela deve permanecer em Discovery e fazer perguntas direcionadas. Ela **não deve inventar as respostas para conseguir avançar**.

## 28.2. Fonte canônica da Engine

A fonte pública oficial desta metodologia é:

```text
https://github.com/jukazilli/processo-de-desenvolvimento-de-software-com-ia-assistida
```

O arquivo operacional principal é:

```text
README.md
```

Ao ativar a engine, a IA deve acessar a fonte usando o melhor mecanismo disponível no ambiente, por exemplo:

```text
GitHub conectado
        ou
acesso ao repositório público
        ou
browser/web
        ou
clone read-only, quando o ambiente suportar
```

A IA não deve depender de uma lembrança parcial deste processo ou de um resumo antigo quando a fonte canônica estiver acessível.

## 28.3. Leitura integral antes de qualquer execução

O primeiro comportamento da engine é **ler o README inteiro**.

Não é suficiente ler apenas o início, o índice ou os tópicos que pareçam relevantes naquele momento.

Se o ambiente precisar paginar, buscar por faixas, abrir múltiplas partes do arquivo ou continuar a leitura em várias chamadas, a IA deve fazê-lo até chegar ao final.

Depois da leitura, deve formar um índice operacional contendo, pelo menos:

- qual pergunta cada tópico responde;
- quando cada tópico deve ser consultado;
- quais documentos dependem de quais decisões;
- quais regras funcionam como gates humanos;
- quais etapas podem produzir artefatos;
- quais etapas apenas analisam e orientam;
- quais regras possuem precedência em caso de conflito;
- quando pesquisa web atual é obrigatória;
- quando o Codex passa a ser o ambiente de execução.

A IA não precisa reproduzir o README inteiro para o usuário após carregá-lo. Ela precisa **compreendê-lo integralmente e utilizá-lo sem reduzir suas regras a um resumo simplificado**.

## 28.4. Fixação da versão durante a sessão

Sempre que o mecanismo de acesso permitir, a IA deve identificar a versão da metodologia carregada por:

- repositório;
- branch;
- commit SHA.

Exemplo:

```text
ENGINE_SOURCE:
jukazilli/processo-de-desenvolvimento-de-software-com-ia-assistida

BRANCH:
main

LOADED_COMMIT:
<sha>
```

Durante a mesma sessão, não deve trocar silenciosamente para outra versão do processo caso `main` seja atualizado.

Se o usuário solicitar atualização da engine, a IA deve reler a versão mais recente, identificar o novo commit e reconciliar as diferenças antes de continuar.

## 28.5. A ativação não cria documentos

Girar a chave **não significa iniciar automaticamente a Pesquisa e Viabilidade**.

A ativação apenas:

```text
acessa a metodologia
        ↓
lê integralmente
        ↓
forma mapa operacional
        ↓
recupera o contexto de Discovery da conversa
        ↓
identifica a fase atual
        ↓
fica pronta para receber o próximo comando do humano
```

Nenhum `.md` do projeto deve ser criado apenas porque a engine foi ativada.

## 28.6. Handshake de ativação

Depois de carregar integralmente a metodologia, a IA deve responder de forma curta e verificável, semelhante a:

```text
ENGINE_STATUS: ACTIVE
SOURCE: jukazilli/processo-de-desenvolvimento-de-software-com-ia-assistida
BRANCH: main
COMMIT: <sha, quando disponível>
PROCESS_LOADED: complete
CURRENT_STAGE: Discovery
CANONICAL_DOCUMENTS_CREATED: none
NEXT_ELIGIBLE_ACTION: Pesquisa e Viabilidade, quando solicitada
```

Se o Discovery ainda estiver insuficiente:

```text
ENGINE_STATUS: ACTIVE
PROCESS_LOADED: complete
CURRENT_STAGE: Discovery
DISCOVERY_READINESS: insufficient
NEXT_ACTION: targeted discovery questions
```

A confirmação não deve fingir que uma leitura incompleta foi integral.

## 28.7. Chave de ativação para o ChatGPT

O usuário pode copiar e colar o prompt abaixo **na mesma conversa em que realizou o Discovery**.

```text
ATIVAR ENGINE — PROCESSO DE DESENVOLVIMENTO DE SOFTWARE COM IA ASSISTIDA

Quero que, a partir deste ponto, você utilize como protocolo operacional desta conversa
o processo canônico disponível em:

https://github.com/jukazilli/processo-de-desenvolvimento-de-software-com-ia-assistida

Antes de gerar qualquer documento ou executar qualquer etapa:

1. acesse o repositório público usando o mecanismo disponível neste ambiente;
2. leia integralmente o README.md atual, do início ao fim;
3. não use apenas um resumo, memória prévia ou trechos isolados;
4. se a leitura exigir paginação ou múltiplas chamadas, continue até consumir o arquivo inteiro;
5. identifique, quando possível, repository, branch e commit SHA da versão carregada;
6. construa um mapa operacional de cada tópico, entendendo:
   - o que ele governa;
   - quando deve ser consultado;
   - quais decisões possuem precedência;
   - quais gates exigem aprovação humana;
   - quais artefatos podem ser gerados;
   - quando pesquisa web atual é obrigatória;
   - quando a execução deve passar para o Codex;
7. considere toda a conversa anterior a esta mensagem como matéria-prima do Discovery do meu projeto;
8. classifique internamente o que já conversamos em decidido, hipótese, pendente e descartado;
9. não transforme hipótese em requisito sem minha aprovação;
10. não gere nenhum arquivo .md apenas por ativar a engine;
11. não gere todos os documentos de uma vez;
12. cada documento deverá passar por análise, minha leitura, correção e aprovação antes da canonização;
13. quando uma versão de documento for aprovada, altere o mesmo artefato em vez de criar cópias concorrentes;
14. se houver GitHub autorizado para o projeto, você poderá salvar o .md aprovado nele;
15. se não houver, gere o arquivo para eu salvar localmente no destino que definirmos;
16. nunca presuma que possui acesso de escrita a um repositório: verifique antes;
17. mantenha esta versão da engine como referência durante a conversa e não troque silenciosamente para outra versão caso o repositório seja atualizado.

Depois de concluir a leitura integral, não inicie nenhuma etapa por conta própria.
Responda apenas com um handshake curto contendo:

ENGINE_STATUS
SOURCE
BRANCH
COMMIT, se disponível
PROCESS_LOADED
CURRENT_STAGE
DISCOVERY_READINESS
CANONICAL_DOCUMENTS_CREATED
NEXT_ELIGIBLE_ACTION

Se você concluir que ainda não existe Discovery suficiente, indique isso e aguarde minha autorização para continuar as perguntas.
```

## 28.8. Primeiro acionamento — Pesquisa e Viabilidade

Depois da engine estar ativa, um comando como:

```text
Ok, faça a Pesquisa e Viabilidade com base no que já conversamos.
```

**não deve gerar imediatamente `01_Pesquisa_e_Viabilidade.md`.**

O fluxo correto é:

```text
comando humano
        ↓
reler contexto de Discovery
        ↓
consultar regras do Documento 01
        ↓
identificar lacunas
        ↓
realizar pesquisa web atual quando necessária
        ↓
separar evidência / hipótese / decisão
        ↓
apresentar análise para leitura humana
        ↓
humano corrige, questiona ou aprova
        ↓
IA ajusta a análise
        ↓
aprovação explícita para canonização
        ↓
somente então gerar 01_Pesquisa_e_Viabilidade.md
        ↓
salvar/versionar no destino aprovado
```

A Pesquisa e Viabilidade apresentada inicialmente no chat é um **artefato de revisão**, ainda não canônico.

Ela pode conter fontes, evidências, riscos, concorrentes, hipóteses, alternativas, limitações e recomendação. O humano precisa conseguir lê-la antes que ela vire fonte da verdade.

## 28.9. Aprovação possui duas fases distintas

Para evitar que uma resposta ainda em discussão vire arquivo canônico por acidente, o processo deve distinguir:

```text
APROVAÇÃO DO CONTEÚDO
        ↓
AUTORIZAÇÃO PARA CANONIZAR
```

Exemplo:

```text
Usuário:
"A análise ficou correta. Só ajuste X."

→ ainda não gerar arquivo final.

Usuário:
"Agora está aprovado. Gere o documento 01 e salve no repositório."

→ canonização autorizada.
```

Quando o contexto tornar inequívoco que o humano aprovou **e pediu a geração do documento**, a IA pode executar ambas as ações na mesma interação.

Em caso de dúvida, preservar a análise em chat e perguntar antes de escrever a fonte canônica.

## 28.10. Ciclo obrigatório para os documentos seguintes

A mesma regra se repete nas próximas camadas.

```text
conteúdo anterior aprovado
        ↓
IA consulta a seção correta da Engine
        ↓
produz proposta do próximo documento
        ↓
humano lê
        ↓
humano corrige
        ↓
IA reconcilia
        ↓
humano aprova
        ↓
humano autoriza canonização
        ↓
.md é criado/atualizado
        ↓
próxima camada se torna elegível
```

A engine deve impedir comandos vagos como:

```text
"Gere toda a documentação necessária."
```

quando isso violar o processo de aprovação progressiva.

Ela deve explicar que a metodologia exige geração **um documento por vez**.

## 28.11. Destino dos documentos do projeto

A metodologia e os documentos do produto são coisas diferentes.

```text
REPOSITÓRIO DA ENGINE
→ contém este processo

REPOSITÓRIO DO PROJETO
→ contém o software e seus documentos canônicos
```

Antes da primeira canonização, o destino deve estar claro.

Fluxos possíveis:

```text
A. GitHub conectado e autorizado
   → criar/atualizar .md diretamente no repositório do projeto

B. GitHub não conectado
   → gerar .md para download
   → usuário salva na pasta local do projeto

C. projeto ainda sem repositório
   → gerar .md localmente
   → versionar quando o repositório for criado
```

A IA nunca deve salvar documentos do projeto dentro do repositório público da Engine.

## 28.12. Continuidade de sessão

A engine deve manter um pequeno estado operacional durante a conversa, por exemplo:

```text
ENGINE_VERSION: <commit>
PROJECT_STAGE: 02_BRIEFING_REVIEW
LAST_CANONICAL_DOCUMENT: 01_Pesquisa_e_Viabilidade.md
NEXT_DOCUMENT: 02_Briefing_de_Produto_e_Escopo.md
PROJECT_DOC_DESTINATION: <repo ou pasta>
BLOCKERS: none
```

Esse estado é operacional à conversa atual. Ele não substitui os arquivos canônicos nem deve ser tratado como memória permanente garantida.

Ao retomar uma conversa muito longa ou quando houver dúvida de contexto, a IA deve reler os documentos já canonizados antes de continuar.

## 28.13. Atualização ou rotação da chave

A "chave" é um bootstrap textual, não uma credencial secreta.

Ela pode ser atualizada sempre que o protocolo de ativação mudar.

Uma chave nova deve preservar quatro propriedades:

```text
1. aponta para a fonte canônica;
2. exige leitura integral;
3. exige confirmação de versão;
4. não autoriza geração documental sem gate humano.
```

Se este README mudar de forma material, a chave deste tópico deve ser revisada no mesmo commit ou em um commit subsequente explicitamente rastreável.

O usuário nunca precisa inserir tokens, senhas, API keys ou outras credenciais dentro da chave de ativação.

## 28.14. Transição do ChatGPT para o Codex

ChatGPT e Codex possuem papéis diferentes nesta metodologia.

A transição acontece quando a baseline aprovada já está disponível no repositório ou na máquina local que o Codex utilizará.

Antes do handoff, espera-se, conforme o estágio do projeto:

- documentos canônicos aprovados;
- Documento 06 disponível;
- Documento 07 aprovado;
- Infraestrutura e Plano de Fundação aprovado;
- Documento 08 com backlog canônico;
- Documento 09 quando já aplicável;
- working tree sincronizada com a versão documental aprovada.

O Codex não deve reconstruir o Discovery do zero quando a documentação já responde às decisões necessárias.

## 28.15. Pré-condição local do Codex

Quando os documentos estiverem no Git, a máquina onde o Codex executará deve possuir o repositório do **projeto** clonado e atualizado.

Antes de começar:

```text
remote atualizado
        ↓
branch correta
        ↓
últimos commits baixados
        ↓
documentos canônicos disponíveis localmente
        ↓
Codex pode consumi-los
```

Se houver mudanças documentais ainda não commitadas ou não sincronizadas, o Codex deve tratá-las como estado local explícito e não presumir que o remoto representa a versão mais recente.

## 28.16. Prompt de bootstrap para o Codex

Na primeira execução do Codex sobre o projeto, pode-se usar:

```text
CONSUMIR PROCESSO E BACKLOG — INÍCIO DA EXECUÇÃO

Antes de alterar qualquer código, faça uma leitura integral da documentação canônica disponível neste repositório/projeto.

1. identifique todos os documentos .md canônicos;
2. leia-os na ordem de precedência definida pelo processo;
3. leia integralmente o Documento 06 — Técnicas de Desenvolvimento e trate suas regras como restrições obrigatórias de escrita de código;
4. leia o Documento 07 — Engenharia e Arquitetura e identifique modelo arquitetural, tipo de repositório, módulos, fronteiras, contratos e decisões rejeitadas;
5. leia Infraestrutura e Plano de Fundação;
6. consuma integralmente o Documento 08 — Backlog Canônico;
7. leia a Matriz Operacional de Rastreabilidade quando existir;
8. verifique se existem documentos derivados, ADRs, contratos, runbooks ou instruções locais para agents;
9. não comece implementando uma funcionalidade aleatória;
10. determine primeiro o estado real da Fundação e dos itens FND-*;
11. procure inconsistências entre documentação, backlog, código e testes antes de executar;
12. não altere produto, arquitetura, infraestrutura ou decisões canônicas silenciosamente;
13. não instale dependências, crie serviços pagos, exponha segredos ou faça ações destrutivas sem respeitar os gates definidos;
14. antes de escrever código, inspecione o código existente, padrões locais e possibilidades reais de reutilização;
15. código, naming, comentários e docstrings técnicos devem seguir as regras do Documento 06;
16. cada item executado deve deixar testes, gates e evidências exigidos pelo backlog;
17. atualize rastreabilidade conforme a execução;
18. quando encontrar uma lacuna que altere intenção de produto, custo, risco ou arquitetura, pare e apresente o bloqueio ao humano em vez de inventar uma decisão.

Nesta primeira resposta, ainda não implemente.

Apresente apenas:

DOCUMENTS_CONSUMED
DOCUMENT_CONSISTENCY
CURRENT_FOUNDATION_STATUS
BACKLOG_STATUS
NEXT_EXECUTABLE_ITEM
BLOCKERS
PROPOSED_FIRST_SLICE

Depois aguarde minha autorização para iniciar a execução.
```

## 28.17. Comando curto para uso recorrente no Codex

Depois que o Codex já consumiu a documentação e confirmou o estado do projeto, o usuário pode usar comandos muito mais simples.

Exemplo:

```text
Consuma o backlog e inicie a próxima fatia executável respeitando toda a documentação canônica, os quality gates e a rastreabilidade do projeto.
```

Ou, no início da Fundação:

```text
Consuma o backlog para iniciarmos o desenvolvimento da aplicação. Comece pelos itens FND elegíveis, respeitando a documentação canônica e os gates humanos.
```

A simplicidade do comando é possível porque as decisões complexas já foram externalizadas nos documentos.

## 28.18. O Codex deve provar que consumiu antes de executar

O Codex não deve responder apenas:

```text
"Entendido, vou começar."
```

Antes da primeira alteração, deve conseguir apontar pelo menos:

- quais documentos encontrou;
- qual Documento 06 governa o código;
- qual arquitetura está aprovada;
- qual infraestrutura está prevista;
- quais itens FND estão pendentes/concluídos;
- qual é o próximo item elegível;
- quais gates deverão provar a entrega.

Isso não exige uma reprodução integral da documentação. Exige evidência de que a execução está ancorada nela.

## 28.19. Quando devolver a decisão para o ChatGPT/humano

Durante execução, o Codex pode encontrar uma decisão que o backlog não resolve.

Exemplos:

- requisito ambíguo;
- conflito entre dois documentos;
- nova necessidade de produto;
- decisão significativa de UX/UI;
- mudança de arquitetura;
- infraestrutura não prevista;
- recurso que gera custo;
- risco de segurança novo;
- alteração que muda escopo.

Nesses casos:

```text
Codex identifica bloqueio
        ↓
não inventa solução canônica
        ↓
registra contexto e opções
        ↓
humano leva a decisão ao fluxo documental/ChatGPT
        ↓
documentação é reconciliada e aprovada
        ↓
Codex atualiza contexto
        ↓
execução continua
```

O Codex pode propor alternativas técnicas, mas não possui autoridade para mudar silenciosamente a intenção canônica do produto.

## 28.20. Integridade entre ChatGPT e Codex

O handoff deve preservar a seguinte cadeia:

```text
DISCOVERY NO CHATGPT
        ↓
ANÁLISE
        ↓
REVISÃO HUMANA
        ↓
DOCUMENTO CANÔNICO .MD
        ↓
REPOSITÓRIO / PASTA LOCAL
        ↓
CODEX CONSOME
        ↓
BACKLOG
        ↓
IMPLEMENTAÇÃO
        ↓
TESTES / GATES
        ↓
EVIDÊNCIA
        ↓
RASTREABILIDADE
```

O ChatGPT não deve entregar ao Codex apenas um resumo informal quando os documentos canônicos existem.

O Codex não deve substituir documentos por sua própria interpretação da conversa original.

A ponte entre ambos é a **documentação versionada**.

## 28.21. Regra para exemplos práticos desta metodologia

Exemplos completos de aplicação deste processo não devem ser misturados a este README canônico.

Eles devem ser mantidos em diretório separado, por exemplo:

```text
/examples/
```

O README principal continua definindo **o processo**.

Os exemplos demonstram **o processo acontecendo**: conversa de Discovery, comandos do humano, respostas da IA, momentos de revisão, aprovações, geração dos `.md`, handoff para o Codex e execução.

A criação desses exemplos deve acontecer separadamente para que uma narrativa fictícia ou didática nunca seja confundida com regra normativa da Engine.

## 28.22. Resultado esperado da ativação

Quando este tópico estiver sendo seguido corretamente, o usuário pode partir de uma conversa natural sobre uma ideia e progressivamente chegar a software executável sem transformar a primeira conversa em código prematuro.

```text
IDEIA DISCUTIDA
        ↓
CHAVE DE ATIVAÇÃO
        ↓
ENGINE CARREGADA INTEGRALMENTE
        ↓
PESQUISA / ANÁLISE
        ↓
REVISÃO HUMANA
        ↓
DOCUMENTAÇÃO CANÔNICA UM A UM
        ↓
BASELINE APROVADA
        ↓
HANDOFF PARA CODEX
        ↓
FUNDAÇÃO
        ↓
IMPLEMENTAÇÃO RASTREÁVEL
```

A chave existe para reduzir o prompt necessário ao usuário sem reduzir a profundidade do processo.

> **O usuário gira a chave; a Engine carrega as regras; o humano continua aprovando as decisões; o Codex executa somente o que foi canonizado.**
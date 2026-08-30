# Conversa simulada — Discovery até handoff

> **Cenário fictício:** consultoria que treina usuários do software OMEM, um CRM fictício integrado ao TOTVS Protheus.  
> **Objetivo:** mostrar a interação realista entre humano e ChatGPT antes de cada canonização.

---

# 1. Discovery livre — antes da Engine

## Usuário

Quero criar uma plataforma web para a nossa consultoria. Nós damos treinamento de um software chamado OMEM. Ele é um CRM e possui integração com o Protheus. Hoje treinamos cliente por Teams, enviamos PDF e vídeo por WhatsApp e depois fica difícil saber quem realmente aprendeu. Pensei em criar um AVA próprio. O que você acha?

## ChatGPT

A ideia faz sentido principalmente porque o problema não parece ser apenas “hospedar vídeo”. O problema é controlar uma jornada de capacitação: quem recebeu treinamento, em qual módulo, o que concluiu, onde teve dificuldade e qual evidência existe de que a pessoa terminou.

Um AVA próprio pode fazer sentido se a consultoria quiser transformar treinamento em parte do produto/serviço, e não apenas usar uma ferramenta genérica de cursos. Antes de pensar em tecnologia eu investigaria: quantidade de clientes, como as turmas funcionam, se o conteúdo muda com frequência, se os treinamentos são por empresa, se existe certificação e se vocês querem futuramente vender cursos sem consultor ao vivo.

## Usuário

Hoje cada cliente compra implantação e treinamento. Normalmente temos usuários de vendas, gestor e administrativo. Cada perfil precisa aprender coisas diferentes. Eu queria criar trilhas por função. Também quero que o cliente consiga ver o andamento da equipe dele.

## ChatGPT

Isso muda bastante o produto. Em vez de um catálogo simples de cursos, começa a aparecer um modelo corporativo com pelo menos três perspectivas:

- consultoria administra conteúdo e clientes;
- gestor do cliente acompanha sua empresa;
- aluno executa a trilha atribuída ao seu perfil.

A trilha por função pode ser uma diferenciação relevante porque o usuário não precisa consumir o sistema inteiro. Ele aprende o que precisa para trabalhar.

## Usuário

Também quero prova no final e certificado. E em alguns treinamentos eu queria colocar uma tarefa prática tipo: “cadastre uma oportunidade no OMEM e depois marque como concluído”. No futuro talvez a plataforma valide sozinha se a pessoa fez isso no OMEM.

## ChatGPT

Eu separaria essas duas coisas. Para a primeira versão, a tarefa prática pode ser declarativa ou validada pelo instrutor. A validação automática dentro do OMEM cria uma integração operacional nova e aumenta bastante a complexidade, porque o AVA precisaria consultar eventos ou dados do CRM e entender contexto, usuário, cliente e ambiente.

Eu manteria essa automação como evolução prevista, mas não como requisito obrigatório do primeiro corte.

## Usuário

Concordo. Quero começar simples mas já sem fazer algo que depois precise jogar fora. Também quero que os treinamentos possam ter aula ao vivo, vídeo gravado, PDF e quiz.

## ChatGPT

Então já temos uma hipótese de produto mais clara: um AVA corporativo especializado no treinamento do OMEM, com trilhas por função, acompanhamento por empresa e estrutura preparada para futuramente receber validações vindas do próprio CRM.

Ainda faltaria entender, entre outras coisas: volume inicial, quem publica conteúdo, se o mesmo curso pode ser reutilizado entre clientes, se haverá personalização por cliente, política de certificado e se a plataforma será apenas interna da consultoria ou um produto que poderá ser comercializado separadamente.

## Usuário

No começo é ferramenta da consultoria, mas se der certo eu quero vender como parte do OMEM ou até como produto separado para outras empresas de software. Os cursos devem ser reaproveitados entre clientes, mas uma turma pode ter datas e instrutor próprios. Não quero customização de tela por cliente agora. A marca é da própria consultoria.

## ChatGPT

Isso já é Discovery suficiente para começar a estruturar a viabilidade, desde que a pesquisa trate como hipótese a expansão para outros softwares. O produto inicial continua sendo treinamento do OMEM; o potencial de virar uma plataforma mais genérica não deve contaminar o MVP com abstrações prematuras.

---

# 2. Ativação da Engine

## Usuário

Vou usar o processo de desenvolvimento com IA assistida. [O usuário cola a chave de ativação definida no Tópico 28 do README canônico.]

## ChatGPT — handshake esperado

```text
ENGINE_STATUS: ACTIVE
SOURCE: jukazilli/processo-de-desenvolvimento-de-software-com-ia-assistida
BRANCH: main
COMMIT: <commit carregado na sessão>
PROCESS_LOADED: complete
CURRENT_STAGE: Discovery
DISCOVERY_READINESS: sufficient
CANONICAL_DOCUMENTS_CREATED: none
NEXT_ELIGIBLE_ACTION: Pesquisa e Viabilidade
```

A Engine não cria nenhum arquivo neste momento.

---

# 3. Pesquisa e Viabilidade — análise antes do documento

## Usuário

Ok, faça a Pesquisa e Viabilidade com base no que já conversamos.

## ChatGPT

A análise inicial conclui que existe problema real e recorrente: materiais dispersos, ausência de evidência de aprendizagem, dificuldade de segmentar treinamento por função e falta de visão corporativa do progresso.

Referências de mercado confirmam que LMS/AVA já resolvem catálogo, conteúdos, avaliações e acompanhamento. Portanto, “ter um AVA” sozinho não é diferenciação. A hipótese de diferenciação está na especialização operacional para treinamento de software: trilhas por função, turmas vinculadas a clientes, tarefas práticas e possibilidade futura de integração com o próprio OMEM.

Riscos principais:

- tentar competir desde o início com LMS generalistas maduros;
- criar integração automática com o OMEM cedo demais;
- misturar gestão de treinamento com suporte técnico e base de conhecimento sem delimitação;
- produzir conteúdo sem processo editorial consistente;
- armazenar vídeo diretamente sem necessidade e elevar custo.

Conclusão preliminar: **viável para um Beta focado na operação da consultoria**, desde que o primeiro corte não tente virar um LMS universal.

## Usuário

Eu concordo, mas quero deixar mais claro que a plataforma também vai ajudar na implantação. O consultor consegue montar a trilha da empresa conforme os módulos que ela comprou. Por exemplo, se não usa módulo de atendimento, não precisa aparecer aquele treinamento.

## ChatGPT

Ajuste incorporado. Isso fortalece a proposta: não é apenas trilha por cargo, mas uma combinação de **módulos contratados + função do usuário + turma/implantação**. Essa regra deve aparecer como hipótese aprovada de produto e depois virar regra de negócio no Briefing/PO.

## Usuário

Agora está correto. Gere a Pesquisa e Viabilidade e salve no projeto do exemplo.

## Resultado

É canonizado:

`documentos/01_Pesquisa_e_Viabilidade.md`

Somente agora o Documento 02 se torna elegível.

---

# 4. Briefing de Produto e Escopo

## Usuário

Com base na Pesquisa aprovada, prepare o Briefing para eu revisar. Não gere o arquivo ainda.

## ChatGPT

Proposta de corte Beta:

**Inclui:** clientes/empresas, usuários por empresa, perfis de acesso, catálogo de cursos, módulos e aulas, trilhas atribuíveis, turmas, materiais em vídeo/link/PDF, quiz, tarefas práticas declarativas, progresso, certificado e painel do gestor do cliente.

**Não inclui no Beta:** marketplace, white-label por cliente, aplicativo nativo, gamificação complexa, SCORM completo, validação automática de ações dentro do OMEM, integração direta com Protheus e criação de conteúdo por IA.

A plataforma será web responsiva. O conteúdo pertence à consultoria e pode ser reutilizado entre clientes. A atribuição de uma trilha considera os módulos OMEM contratados e o papel do aluno.

## Usuário

Só quero mudar uma coisa. O gestor do cliente pode acompanhar, mas não pode editar curso nem trilha. Quem monta trilha é a consultoria. O cliente só pode convidar usuários se a consultoria liberar isso.

## ChatGPT

Ajustado. O gestor do cliente passa a ter escopo administrativo restrito ao tenant e permissões explicitamente concedidas. Conteúdo e desenho pedagógico continuam sob domínio da consultoria.

## Usuário

Aprovado. Gere o Documento 02.

## Resultado

`documentos/02_Briefing_de_Produto_e_Escopo.md`

---

# 5. Visão de Product Owner

## Usuário

Agora prepare a Visão de Product Owner para revisão.

## ChatGPT

Diretrizes propostas:

- reduzir tempo até o aluno começar o conteúdo correto;
- priorizar clareza sobre riqueza de funcionalidades;
- separar claramente operação da consultoria e visão do cliente;
- não transformar o Beta em LMS genérico;
- preservar possibilidade de integração futura com OMEM sem antecipar complexidade;
- evidência de conclusão vale mais que quantidade de recursos sociais;
- o conteúdo deve ser reutilizável; a atribuição é contextual.

## Usuário

Inclua que a plataforma deve ajudar o consultor a conduzir implantação. Se ele enxergar que uma empresa está parada em um treinamento importante, isso é um sinal operacional.

## ChatGPT

Incluído como princípio de produto: progresso de aprendizagem também é sinal de risco da implantação, mas o Beta não deve automaticamente tomar decisões pelo consultor.

## Usuário

Aprovado. Gere o Documento 03.

## Resultado

`documentos/03_Visao_de_Product_Owner.md`

---

# 6. Princípios de UX/UI

## Usuário

Prepare os princípios de UX/UI. Quero algo profissional, simples e muito fácil para pessoas que nem sempre têm intimidade com tecnologia.

## ChatGPT

Proposta de princípios:

- uma tarefa mental dominante por tela;
- baixa densidade e progressão de complexidade;
- linguagem de treinamento, não linguagem de sistema;
- progresso sempre compreensível;
- contexto da empresa/aluno explícito para evitar ações no tenant errado;
- ações administrativas destrutivas com baixa exposição;
- marca profissional, próxima e didática, sem estética escolar infantil;
- aluno vê primeiro “o que preciso fazer agora”, não dashboards extensos.

## Usuário

Perfeito. A marca também tem que transmitir que a consultoria conhece o OMEM profundamente. Não pode parecer uma plataforma genérica que só recebeu nosso logo.

## ChatGPT

Incluído: identidade deve se apoiar no vocabulário, estrutura de trilhas, ícones e microcopy ligados à rotina real de implantação e uso do OMEM, sem copiar a interface do CRM.

## Usuário

Aprovado. Gere o documento.

## Resultado

`documentos/Principios_de_UX_UI.md`

---

# 7. UI/Design System e UX

## Usuário

Agora faça a proposta da Direção de UI e Design System.

## ChatGPT

A proposta define superfícies separadas por tarefa mental: Hoje/Minha trilha para aluno; Empresas, Turmas, Conteúdo e Acompanhamento para consultoria; Equipe e Progresso para gestor do cliente. Evita concentrar tudo em um dashboard genérico.

O sistema visual usa hierarquia clara, cards apenas quando representam unidades reais como curso/aula/turma, ações primárias persistentes em formulários longos e disclosure progressivo para configurações avançadas.

## Usuário

Aprovado. Gere o Documento 04.

## Resultado

`documentos/04_Direcao_de_UI_e_Design_System.md`

## Usuário

Agora proponha o Documento 05 com as jornadas.

## ChatGPT

Jornadas prioritárias propostas:

1. consultoria cria cliente e configura módulos contratados;
2. consultoria cria turma e atribui trilha;
3. aluno aceita convite e inicia a trilha;
4. aluno consome aula, faz quiz e conclui tarefa prática;
5. gestor acompanha equipe;
6. consultor identifica bloqueio de aprendizagem;
7. aluno conclui trilha e recebe certificado.

Estados de vazio, erro, reentrada e retomada são especificados por jornada.

## Usuário

Aprovado. Gere o Documento 05.

## Resultado

`documentos/05_Especificacao_de_UX.md`

---

# 8. Técnicas, Engenharia e Arquitetura

## Usuário

Prepare as Técnicas de Desenvolvimento seguindo todas as regras da Engine.

## ChatGPT

A proposta fixa TypeScript em modo estrito, código técnico em inglês, lint/format/typecheck/testes obrigatórios, regras de naming, Clean Code, reaproveitamento antes de criação, testes de regressão para bugs, migrations versionadas e revisão obrigatória do próprio diff. Também define que bibliotecas precisam de justificativa e que comentários explicam contexto, não sintaxe.

## Usuário

Aprovado. Gere o Documento 06.

## Resultado

`documentos/06_Tecnicas_de_Desenvolvimento.md`

## Usuário

Agora faça Engenharia e Arquitetura. Quero que você avalie primeiro o que o sistema precisa suportar e só depois escolha a arquitetura.

## ChatGPT

Forças identificadas: multi-tenant corporativo, segregação forte entre clientes, crescimento de catálogo/conteúdo, trilhas reutilizáveis, auditoria de progresso, upload/material externo, notificações e futuras integrações com OMEM. O Beta será mantido por equipe pequena, então baixa complexidade operacional é prioridade.

Arquitetura recomendada: modular monolith com frontend web e API TypeScript, monorepo para compartilhar contratos e domínio, PostgreSQL relacional e separação explícita de tenant. Microservices são rejeitados no Beta.

## Usuário

Faz sentido. Quero API separada do frontend para termos liberdade futura, mas continuar no mesmo monorepo.

## ChatGPT

Ajustado. O repo passa a prever `apps/web`, `apps/api` e packages compartilhados. Deploy pode ser independente sem fragmentar repositórios.

## Usuário

Aprovado. Gere o Documento 07.

## Resultado

`documentos/07_Engenharia_e_Arquitetura.md`

---

# 9. Infraestrutura — entrevista humana

## ChatGPT

Antes de escolher provedores preciso da entrevista de infraestrutura.

1. O produto pode virar comercial?  
2. Você quer começar sem custo quando possível?  
3. Precisa de staging em nuvem desde o início?  
4. Quantas pessoas devem usar o Beta?  
5. O projeto terá dados sensíveis?  
6. Prefere serviços gerenciados?  
7. Recursos pagos precisam de aprovação individual?

## Usuário

1. Sim, pode virar produto.  
2. Quero começar gratuito quando for seguro.  
3. Sim, quero staging porque outras pessoas vão testar.  
4. Inicialmente menos de 500 usuários.  
5. Teremos nome, e-mail, empresa, progresso e resultados de avaliação; nada financeiro.  
6. Prefiro gerenciado. Não quero administrar servidor.  
7. Sim, qualquer coisa paga precisa ser aprovada.

## ChatGPT

Com essas respostas, pesquiso opções atuais e comparo custo, limites e aderência. A recomendação de exemplo usa serviços gerenciados e separa claramente o que pode iniciar em free tier do que precisa ser reavaliado antes da produção.

## Usuário

Aprovado. Gere o Plano de Infraestrutura e Fundação.

## Resultado

`documentos/Infraestrutura_e_Plano_de_Fundacao.md`

---

# 10. Backlog e Matriz

## Usuário

Agora transforme tudo em backlog. Não quero item genérico tipo “criar AVA”. Quero itens pequenos e testáveis, incluindo a Fundação.

## ChatGPT

O backlog é dividido em FND, AUTH, TEN, CNT, TRL, CLS, LRN, ASM, CERT e OBS. Cada item possui origem, dependências, critérios de aceite, testes e evidência.

A primeira sequência elegível é Fundação: repo/toolchain → CI → banco/migrations → auth/tenant baseline → staging → smoke tests.

## Usuário

Aprovado. Gere o Documento 08.

## Resultado

`documentos/08_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md`

## Usuário

Agora gere a Matriz Operacional com o estado inicial real. Nada deve aparecer como Done porque ainda não codificamos.

## ChatGPT

Correto. A matriz começa com itens `Planned`, sem inventar implementação, teste ou evidência.

## Usuário

Aprovado. Gere o Documento 09.

## Resultado

`documentos/09_Matriz_Operacional_de_Rastreabilidade.md`

---

# 11. Encerramento da fase documental

## ChatGPT

```text
BASELINE_STATUS: CANONICAL
DOCUMENTS_01_09: approved
INFRASTRUCTURE_PLAN: approved
BACKLOG: ready for execution
MATRIX: initialized
NEXT_ENVIRONMENT: Codex
NEXT_STAGE: Foundation / FND
```

## Usuário

Perfeito. Vou clonar o repositório do projeto na minha máquina e abrir no Codex.

A partir daqui, o ChatGPT não inicia implementação. O exemplo continua em [`10_Handoff_para_Codex.md`](./10_Handoff_para_Codex.md).
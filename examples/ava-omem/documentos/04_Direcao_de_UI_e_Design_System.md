---
document_id: DOC-04
title: Direção de UI e Design System
status: canonical-example
version: 1.0.0
depends_on:
  - DOC-03
  - Principios_de_UX_UI
---

# 04 — Direção de UI e Design System

## Direção geral

A interface deve parecer uma aplicação de treinamento profissional ligada à rotina de implantação do OMEM, e não um painel administrativo genérico.

O Design System materializa decisões de contexto e hierarquia. Ele não define sozinho a experiência.

## Navegação por perfil

### Aluno

Superfícies prioritárias:

- Hoje / Minha trilha;
- Aula;
- Avaliação;
- Tarefa prática;
- Histórico;
- Certificados.

A home do aluno deve abrir na retomada do que precisa fazer agora.

### Consultoria

Superfícies prioritárias:

- Empresas;
- Turmas;
- Conteúdo;
- Trilhas;
- Acompanhamento;
- Pessoas.

Evitar um dashboard inicial carregado. O ponto de entrada deve permitir localizar rapidamente o cliente, turma ou tarefa operacional relevante.

### Gestor do cliente

Superfícies prioritárias:

- Equipe;
- Progresso;
- Trilhas atribuídas;
- Convites, somente quando permitido.

Não exibir recursos de autoria de conteúdo.

## Tela: Minha trilha

### Contexto

Aluno retorna para continuar capacitação.

### Tarefa mental principal

Identificar a próxima atividade e continuar.

### Elementos obrigatórios

- nome da trilha;
- progresso compreensível;
- próxima atividade;
- módulos/aulas concluídos;
- bloqueios quando existirem.

### Ação principal

`Continuar treinamento`.

### Ações secundárias

- ver todas as etapas;
- consultar materiais concluídos.

## Tela: Aula

### Tarefa mental principal

Consumir o conteúdo e avançar.

### Elementos

- título;
- contexto curto;
- conteúdo principal;
- material complementar quando existir;
- estado de conclusão;
- navegação anterior/próxima.

### Direção

Evitar menus laterais extensos quando comprimirem o conteúdo. Em telas menores, a estrutura da trilha deve aparecer sob demanda.

## Tela: Empresa

### Tarefa mental principal

Entender situação de treinamento daquele cliente.

### Elementos

- identificação inequívoca da empresa;
- módulos OMEM contratados;
- turmas ativas;
- progresso agregado;
- usuários;
- alertas operacionais relevantes.

### Ação principal

Depende do estado. Exemplos: `Criar turma`, `Acompanhar turma` ou `Convidar usuários`.

Não usar várias ações primárias simultaneamente.

## Tela: Editor de curso

### Tarefa mental principal

Organizar conteúdo do curso.

### Direção

- ação `Salvar` persistente em formulários longos;
- estrutura de módulos/aulas facilmente reordenável;
- configurações avançadas com disclosure progressivo;
- excluir curso em área secundária, não ao lado de Salvar.

## Tela: Acompanhamento de turma

### Tarefa mental principal

Identificar quem precisa de atenção.

### Hierarquia

1. alunos bloqueados/em atraso;
2. tarefas aguardando validação;
3. progresso geral;
4. concluídos;
5. dados históricos.

## Componentes do Design System

Componentes devem existir quando representarem padrões reais, por exemplo:

- `PrimaryAction`;
- `ProgressStep`;
- `LearningItem`;
- `CourseOutline`;
- `TenantContextHeader`;
- `StatusBadge`;
- `EmptyState`;
- `ConfirmationDialog`;
- `FormSection`;
- `StickyFormActions`.

Nomes técnicos são ilustrativos; o projeto real deve seguir as regras do Documento 06.

## Densidade

- uma superfície principal por bloco;
- evitar cards dentro de cards;
- usar divisores, espaçamento e tipografia antes de criar contêineres extras;
- tabelas apenas quando comparação tabular for a tarefa;
- métricas sem decisão associada devem perder prioridade.

## Responsividade

### Desktop/tablet

Administração e acompanhamento podem usar painéis laterais/contextuais quando isso reduzir navegação.

### Mobile

Priorizar consumo de aula, retomada, quiz e tarefas. Configurações complexas de autoria podem ser simplificadas ou sinalizadas como experiência prioritária de desktop.

## Estados obrigatórios

Cada superfície relevante deve prever:

- loading;
- vazio;
- erro recuperável;
- erro sem permissão;
- sucesso;
- conteúdo indisponível;
- conexão degradada quando aplicável.

## Critério de qualidade

Uma tela está alinhada quando a tarefa mental, a ação principal e a hierarquia podem ser explicadas sem citar o framework ou o componente usado para implementá-la.
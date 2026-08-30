---
document_id: DOC-02
title: Briefing de Produto e Escopo
status: canonical-example
version: 1.1.0
depends_on:
  - DOC-01
---

# 02 — Briefing de Produto e Escopo

## Visão resumida

Criar uma plataforma web de aprendizagem para a consultoria organizar e acompanhar treinamentos do software OMEM, um CRM fictício integrado ao TOTVS Protheus.

A plataforma deve transformar treinamentos hoje dispersos em uma jornada estruturada por cliente, módulos contratados, função do usuário e turma de implantação.

## Proposta de valor

Para a consultoria:

- reutilizar conteúdo entre clientes;
- montar trilhas adequadas à implantação;
- acompanhar progresso sem planilhas paralelas;
- identificar bloqueios de aprendizagem;
- registrar evidência de conclusão.

Para o cliente:

- saber o que cada usuário precisa aprender;
- acompanhar avanço da equipe;
- reduzir dependência de materiais dispersos;
- ter histórico de capacitação.

Para o aluno:

- entrar e entender rapidamente o que precisa fazer;
- consumir conteúdo na ordem correta;
- retomar de onde parou;
- concluir avaliações e tarefas;
- receber certificado quando elegível.

## Perfis principais

### Administrador da consultoria

Gerencia clientes, usuários internos, catálogo, trilhas, turmas e regras de acesso.

### Consultor / instrutor

Conduz turmas, acompanha alunos, valida tarefas práticas quando necessário e identifica bloqueios.

### Gestor do cliente

Acompanha somente sua empresa e sua equipe. Não cria ou edita conteúdo. Convite de usuários depende de permissão concedida pela consultoria.

### Aluno

Consome trilhas atribuídas, realiza avaliações, tarefas e acompanha seu progresso.

## Regras centrais

A atribuição de conteúdo considera, conforme configurado:

```text
empresa
+
módulos OMEM contratados
+
função do usuário
+
turma / implantação
        ↓
trilha aplicável
```

Cursos e conteúdos pertencem ao catálogo da consultoria e podem ser reutilizados entre clientes.

Turmas podem possuir datas, instrutor, participantes e contexto próprios sem duplicar o curso-base.

## Escopo do Beta

- autenticação;
- empresas/clientes;
- usuários e papéis;
- catálogo de cursos;
- módulos, aulas e materiais;
- trilhas;
- vínculo de módulos OMEM contratados;
- turmas;
- convites;
- vídeos por link ou provider aprovado;
- PDFs e links externos;
- quizzes;
- tarefas práticas declarativas ou validadas por instrutor;
- progresso por aula/trilha;
- painel de acompanhamento da consultoria;
- painel restrito do gestor do cliente;
- certificados;
- e-mails transacionais essenciais;
- auditoria mínima das ações críticas.

## Não escopo do Beta

- marketplace de cursos;
- white-label por cliente;
- aplicativo móvel nativo;
- gamificação complexa;
- rede social/comunidade completa;
- SCORM completo;
- criação automática de curso por IA;
- integração automática com o OMEM para validar tarefas;
- integração direta com Protheus;
- cobrança/checkout dentro do AVA;
- personalização visual por tenant.

## Plataforma

Aplicação web responsiva, com prioridade para desktop e tablet na administração e experiência funcional em mobile para o aluno.

## Premissas

- a consultoria é dona do conteúdo;
- o mesmo curso pode atender vários clientes;
- o Beta terá volume inicial controlado;
- integrações futuras não justificam abstrações prematuras no Beta;
- decisões de stack, provider, custo e modelo operacional de infraestrutura serão tomadas nas camadas técnicas correspondentes, depois do dimensionamento de engenharia.

## Critérios macro de sucesso

O Beta será considerado útil se permitir que a consultoria substitua o processo disperso de materiais e acompanhamento por um fluxo único, conseguindo responder com confiança:

- quem precisa aprender o quê;
- quem iniciou;
- quem concluiu;
- quem está bloqueado;
- qual empresa está atrasada em uma etapa de treinamento;
- quais evidências de conclusão existem.
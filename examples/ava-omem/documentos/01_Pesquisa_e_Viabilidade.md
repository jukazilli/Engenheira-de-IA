---
document_id: DOC-01
title: Pesquisa e Viabilidade
status: canonical-example
version: 1.0.0
---

# 01 — Pesquisa e Viabilidade

## Problema observado

A consultoria treina usuários do OMEM por reuniões ao vivo e distribui materiais por canais diferentes. Depois do treinamento, falta uma fonte única para saber quem recebeu qual conteúdo, quem concluiu, onde houve dificuldade e se o cliente está pronto para operar os módulos contratados.

## Público afetado

- consultores e instrutores da consultoria;
- gestores dos clientes;
- usuários finais do OMEM;
- responsáveis por implantação e adoção.

## Necessidades principais

1. organizar treinamento por empresa, perfil e módulo contratado;
2. reutilizar conteúdo sem recriar curso para cada cliente;
3. acompanhar progresso individual e da empresa;
4. avaliar conhecimento com quiz e tarefa prática;
5. registrar evidência de conclusão e certificado;
6. permitir que o consultor use progresso como sinal da implantação.

## Soluções existentes e referência de mercado

LMS/AVA generalistas já resolvem catálogo, conteúdo, avaliação, matrícula, progresso e certificados. Portanto, construir apenas “mais um LMS” não representa diferenciação suficiente.

A oportunidade está em especializar o fluxo para treinamento de software corporativo, especialmente:

```text
módulos contratados
+
função do usuário
+
turma / implantação
        ↓
trilha atribuída
```

## Diferenciação potencial

- trilhas derivadas do contexto da implantação;
- visão da consultoria sobre clientes e turmas;
- visão restrita do gestor do cliente;
- tarefas práticas vinculadas ao uso do OMEM;
- possibilidade futura de validar automaticamente ações realizadas no OMEM;
- linguagem e experiência voltadas para implantação de software, não para ensino escolar genérico.

## Hipóteses ainda não validadas

- clientes valorizarão certificado como evidência formal;
- a visão de progresso reduzirá retrabalho de consultoria;
- trilhas por função reduzirão tempo de capacitação;
- no futuro o produto poderá ser vendido para outras empresas de software;
- integração automática com o OMEM terá retorno suficiente para justificar complexidade.

## Riscos

- tentar reproduzir recursos de LMS maduros sem necessidade;
- ampliar o escopo para marketplace, comunidade, gamificação ou white-label cedo demais;
- integrar com o OMEM antes de estabilizar o modelo pedagógico;
- custos de vídeo e armazenamento crescerem sem estratégia;
- baixa adesão se o aluno enxergar o AVA como obrigação paralela ao trabalho;
- dados de clientes diferentes serem expostos entre tenants.

## Limitações do primeiro corte

O Beta não deve depender de integração automática com OMEM ou Protheus. Tarefas práticas podem ser declarativas ou validadas pelo instrutor.

## Critérios de viabilidade

O projeto segue como viável se o Beta conseguir:

- atender múltiplas empresas com segregação clara;
- permitir reutilização de conteúdo;
- atribuir trilhas por contexto;
- registrar progresso e avaliação;
- oferecer operação simples para a consultoria;
- iniciar com custo compatível com o estágio do produto;
- preservar caminho de evolução sem antecipar arquitetura excessiva.

## Conclusão

**Viável para um Beta focado na operação real da consultoria.**

A recomendação é construir uma plataforma especializada em capacitação do OMEM, sem tentar competir funcionalmente com LMS generalistas no primeiro ciclo. A expansão para outros softwares permanece como hipótese de evolução, não como requisito do Beta.
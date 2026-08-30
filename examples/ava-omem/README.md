# Exemplo prático — AVA OMEM

> **Natureza:** estudo de caso fictício  
> **Objetivo:** demonstrar, de ponta a ponta, como a Engine é usada em uma conversa do ChatGPT, como os documentos são aprovados um a um e como ocorre o handoff final para o Codex.

## Cenário

Uma consultoria oferece treinamentos para um software fictício chamado **OMEM**, um CRM integrado ao TOTVS Protheus. A consultoria quer criar uma plataforma web de aprendizagem — um AVA — para organizar cursos, turmas, materiais, avaliações, progresso e certificados dos clientes que treinam o OMEM.

O exemplo foi separado da documentação normativa de propósito:

```text
README.md da raiz
→ metodologia canônica

/examples/ava-omem/
→ aplicação prática fictícia da metodologia
```

Nada desta pasta altera as regras da Engine. Se houver conflito, o `README.md` da raiz possui precedência.

## Como ler este exemplo

1. Comece por [`00_Conversa_Simulada_Discovery_ate_Handoff.md`](./00_Conversa_Simulada_Discovery_ate_Handoff.md). Ele mostra o Discovery, a ativação da Engine, a revisão humana e os comandos de canonização.
2. Consulte a pasta [`documentos/`](./documentos/) para ver como ficaram os artefatos aprovados do projeto fictício. Observe especialmente a passagem `06 Técnicas → 07 Engenharia e Arquitetura → Visão do Tech Lead → Infraestrutura`.
3. Termine em [`10_Handoff_para_Codex.md`](./10_Handoff_para_Codex.md) para ver como a documentação passa do ChatGPT para o ambiente de execução.

## Estrutura

```text
examples/ava-omem/
├── README.md
├── 00_Conversa_Simulada_Discovery_ate_Handoff.md
├── 10_Handoff_para_Codex.md
└── documentos/
    ├── 01_Pesquisa_e_Viabilidade.md
    ├── 02_Briefing_de_Produto_e_Escopo.md
    ├── 03_Visao_de_Product_Owner.md
    ├── Principios_de_UX_UI.md
    ├── 04_Direcao_de_UI_e_Design_System.md
    ├── 05_Especificacao_de_UX.md
    ├── 06_Tecnicas_de_Desenvolvimento.md
    ├── 07_Engenharia_e_Arquitetura.md
    ├── Visao_do_Tech_Lead.md
    ├── Infraestrutura_e_Plano_de_Fundacao.md
    ├── 08_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
    └── 09_Matriz_Operacional_de_Rastreabilidade.md
```

## O que este exemplo demonstra

O objetivo não é sugerir que todo AVA deva possuir esta arquitetura, esta stack ou esta infraestrutura. O objetivo é mostrar o **mecanismo de raciocínio e aprovação**:

```text
Discovery
   ↓
Engine ativada
   ↓
proposta de conteúdo
   ↓
humano revisa
   ↓
IA ajusta
   ↓
humano aprova e manda gerar
   ↓
.md canônico
   ↓
próxima camada
```

Na parte técnica, o exemplo também demonstra a separação de responsabilidades:

```text
06 Técnicas
→ como o código deve ser escrito

07 Engenharia e Arquitetura
→ o que o sistema precisa suportar e como será estruturado

Visão do Tech Lead
→ com quais linguagens, runtimes, frameworks, bibliotecas e ferramentas será implementado

Infraestrutura
→ onde a stack aprovada será executada
```

No exemplo, nenhuma etapa posterior é tratada como pronta antes da aprovação da camada anterior. Isso é intencional.
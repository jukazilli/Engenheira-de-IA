---
title: Infraestrutura e Plano de Fundação
status: canonical-example
version: 1.0.0
depends_on:
  - DOC-06
  - DOC-07
---

# Infraestrutura e Plano de Fundação — AVA OMEM

> **Pesquisa de referência:** 2026-08-30.  
> **Regra:** preços, free tiers e limites devem ser revalidados antes de qualquer contratação real.

## 1. Respostas da entrevista

- produto pode evoluir para oferta comercial;
- começar com custo zero quando for seguro e coerente;
- staging em nuvem desde o início;
- menos de 500 usuários no Beta;
- dados pessoais básicos e dados de aprendizagem;
- preferência por serviços gerenciados;
- sem equipe DevOps dedicada;
- qualquer recurso pago exige aprovação humana explícita.

## 2. Estratégia geral

A infraestrutura inicial deve minimizar operação manual sem bloquear crescimento futuro.

```text
GitHub
   ↓
CI
   ↓
web + API em serviços gerenciados
   ↓
PostgreSQL/Auth/Storage gerenciados
   ↓
e-mail transacional
   ↓
staging validado
```

## 3. Pesquisa atual de referência

### Supabase

Fonte oficial: https://supabase.com/pricing

Na pesquisa realizada em 2026-08-30, o plano Free informava, entre outros limites, 50.000 MAU, 500 MB de banco, 1 GB de file storage e até dois projetos gratuitos, com regras de pausa por inatividade. O plano Pro iniciava em US$ 25/mês.

**Uso considerado:** PostgreSQL, Auth e Storage gerenciados no Beta.

**Atenção:** produção comercial, backup, retenção e disponibilidade devem ser reavaliados antes do go-live.

### Cloudflare Pages / Workers

Fontes oficiais:

- https://developers.cloudflare.com/pages/functions/pricing/
- https://developers.cloudflare.com/workers/platform/pricing/

Na pesquisa de 2026-08-30, assets estáticos em Pages eram gratuitos e sem cobrança por requisição de asset estático; Functions compartilhavam limites do Workers. Workers Free indicava 100.000 requests/dia, sujeito a limites de CPU.

**Uso considerado:** hosting web e, se compatível com o runtime definido, API leve/serverless.

**Atenção:** se a API exigir runtime ou bibliotecas incompatíveis, utilizar outro runtime gerenciado sem alterar a arquitetura lógica.

### Resend

Fonte oficial: https://resend.com/pricing

Na pesquisa de 2026-08-30, o plano Free indicava 3.000 e-mails/mês e limite de 100 por dia.

**Uso considerado:** convites, recuperação e notificações transacionais do Beta.

### GitHub Actions

Fonte oficial: https://docs.github.com/en/actions/concepts/billing-and-usage

A documentação informa que runners padrão são gratuitos para repositórios públicos e que repositórios privados possuem cotas conforme o plano da conta, com cobrança acima da franquia.

**Uso considerado:** CI e gates.

**Atenção:** este projeto de cliente pode ser privado; portanto, não presumir custo zero sem verificar a conta real.

## 4. Composição recomendada para o exemplo

### Repositório

- GitHub;
- monorepo conforme Documento 07;
- branch `main` protegida quando o plano/ambiente permitir;
- PR obrigatório para promoção após a Fundação.

### Web

- Cloudflare Pages como primeira opção de exemplo;
- HTTPS e domínio técnico de staging;
- variáveis públicas separadas de secrets.

### API

Primeira opção: runtime serverless/containerizado gerenciado compatível com Node/TypeScript.

A escolha final entre Workers, Cloud Run ou equivalente deve ser validada durante FND contra dependências reais da API.

### Banco/Auth/Storage

- Supabase;
- projetos separados por ambiente quando o orçamento permitir;
- RLS ou autorização equivalente como defesa adicional;
- migrations versionadas no repo;
- storage privado para materiais não públicos.

### E-mail

- Resend;
- domínio de envio validado;
- secrets somente em ambiente seguro.

### Observabilidade

- logs estruturados da API;
- captura de erros do frontend/backend por solução aprovada;
- alertas mínimos para falha de deploy e erro crítico;
- sem armazenar payload sensível em logs.

## 5. Ambientes

### Local

Desenvolvimento e testes rápidos com serviços locais/emulados quando possível.

### Staging

Obrigatório desde a Fundação, porque será usado por consultoria e usuários piloto.

### Production

Não será criado automaticamente no primeiro setup sem aprovação específica. O Beta pode validar staging antes de decidir produção.

## 6. Segurança de credenciais

Nenhuma senha, service role key, private key, refresh token ou API secret deve ser enviada pelo chat.

Fluxo para setup humano-assistido:

```text
agente abre/prepara painel
        ↓
humano autentica diretamente
        ↓
MFA/CAPTCHA ficam com o humano
        ↓
agente continua na sessão autorizada
```

Preferência de automação:

```text
API/CLI/IaC
   ↓
OAuth/conector
   ↓
Playwright em sessão autorizada
   ↓
runbook manual seguro
```

## 7. Itens de Fundação derivados

```text
FND-001 — inicializar monorepo conforme DOC-07
FND-002 — fixar Node/pnpm e toolchain
FND-003 — configurar lint/format/typecheck/test/build
FND-004 — configurar CI
FND-005 — criar ambiente de banco/auth de staging
FND-006 — criar migrations baseline e autorização de tenant
FND-007 — configurar hosting web de staging
FND-008 — configurar runtime da API de staging
FND-009 — configurar secrets por ambiente
FND-010 — configurar e-mail transacional de teste
FND-011 — adicionar observabilidade mínima
FND-012 — executar smoke tests da Fundação
```

## 8. Gate de custo

Antes de criar qualquer recurso:

```text
FREE / INCLUÍDO
POTENCIALMENTE COBRÁVEL
COBRÁVEL
DESCONHECIDO
```

Qualquer estado diferente de `FREE / INCLUÍDO` exige explicação e aprovação humana antes da ação.

## 9. Fundação pronta

A Fundação não está pronta apenas porque contas existem.

```text
repo conforme arquitetura
+
CI executando
+
banco e migrations funcionando
+
auth/tenant baseline validado
+
web e API em staging
+
secrets fora do código
+
logs mínimos
+
smoke tests aprovados
=
FND_READY
```
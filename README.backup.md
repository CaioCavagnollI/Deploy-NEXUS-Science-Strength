# NEXUS Science & Strength — Plano de Reestruturação

Este documento revisa e organiza a proposta de evolução do repositório com foco em **deploy na Vercel e Replit**, mantendo simplicidade operacional e espaço para crescimento.

## Objetivo

Estruturar um repositório completo com:
- documentação clara em Markdown,
- base pronta para empacotamento (ZIP),
- arquitetura monorepo simples,
- integração com Supabase e Stripe,
- suporte a PWA e caminho de empacotamento mobile com Capacitor.

## Estrutura proposta (monorepo)

```txt
.
├── apps/
│   ├── web/        # Next.js (aplicação principal)
│   └── api/        # NestJS (opcional, para domínio mais complexo)
├── packages/       # bibliotecas compartilhadas (opcional)
├── docs/           # arquitetura, produto, monetização, segurança, operação
├── supabase/       # migrações, seeds, políticas RLS
└── scripts/        # automações de build, setup e validação
```

## Diagnóstico do estado atual

A base atual já possui pontos importantes implementados:
- aplicação em Next.js,
- integração com Stripe,
- integração com Supabase,
- rotas de API e componentes de produto.

A proposta é **evoluir a organização e governança** sem ruptura desnecessária.

## Melhorias prioritárias

1. **README principal orientado a produto e operação**
   - visão de arquitetura,
   - setup local,
   - variáveis de ambiente,
   - fluxo de deploy.

2. **Documentação técnica em `docs/`**
   - `ARCHITECTURE.md`
   - `MONETIZATION.md`
   - `SECURITY.md`
   - `DEPLOYMENT.md`

3. **Padronização de ambiente**
   - `.env.example` com chaves de Supabase/Stripe,
   - convenção de nomes e escopos por ambiente (dev/staging/prod).

4. **PWA (fase incremental)**
   - manifesto (`manifest.webmanifest`),
   - service worker via `next-pwa` somente em produção,
   - estratégia de cache inicial conservadora.

5. **Capacitor (fase posterior)**
   - encapsular o `apps/web` para builds mobile,
   - manter paridade funcional com a versão web,
   - validar plugins nativos somente quando houver necessidade real.

6. **API NestJS opcional**
   - manter no `apps/api` como trilha de evolução,
   - usar apenas para domínios que ultrapassem o escopo ideal de rotas/ações do Next.

## Estratégia de implementação

- **Fase 1 — Organização e docs**: limpar README, estruturar `docs/`, preparar `.env.example`.
- **Fase 2 — Plataforma base**: reforçar Supabase/Stripe, adicionar migrações e webhook.
- **Fase 3 — Experiência**: ativar PWA em produção e medir impacto.
- **Fase 4 — Expansão**: API NestJS e Capacitor conforme necessidade de produto.

## Resultado esperado

Um repositório mais profissional, auditável e pronto para escalar, com curva de manutenção menor e onboarding mais rápido para novos colaboradores.

# Deploy — Vercel / Netlify

A plataforma faz o deploy automaticamente a cada push, conectada
diretamente ao repositório GitHub via o app oficial dela — não há
workflow de deploy próprio a manter.

## Configuração (manual, uma vez)

1. Conecte o repositório em vercel.com (ou netlify.com) → "Import Project".
2. Configure a branch de produção como `main`.
3. Configure `develop` e `test` como branches de preview, se aplicável.
4. Variáveis de ambiente/segredos são configuradas no painel da
   plataforma — nunca commitadas no repositório.

## Fluxo de branch (igual aos outros modelos)

`feature/* → PR → develop → promoção → test → PR revisado → main`. A
plataforma gera uma preview URL automática pra cada PR.

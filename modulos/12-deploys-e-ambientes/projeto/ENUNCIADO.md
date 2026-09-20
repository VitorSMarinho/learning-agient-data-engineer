# Projeto — CI com lint, teste e separação de ambiente

## Contexto

Sem CI, todo PR depende de alguém lembrar de rodar teste manualmente antes de aprovar — e mais
cedo ou mais tarde alguém esquece. Automatizar isso é a diferença entre "acho que funciona" e
"o robô confirmou que funciona".

## Tarefa

1. Escolha um projeto seu de módulo anterior (ex.: o pipeline do Módulo 03, ou o sprint do
   Módulo 11) que tenha testes (`pytest` ou equivalente).
2. Crie um workflow de GitHub Actions (`.github/workflows/ci.yml`) que roda em todo push/PR:
   lint (ex.: `ruff` ou `flake8`) + testes, e falha o check se qualquer um dos dois falhar.
3. Configure separação de ambiente: pelo menos uma config (ex.: endpoint, nível de log, flag de
   feature) que muda entre `dev` e `prod` **via variável de ambiente**, nunca hardcoded — e
   documente exatamente quais variáveis existem e o que cada uma controla.
4. Se o projeto usa algum segredo (mesmo que fictício pra esse exercício, ex. uma API key
   simulada), configure via **GitHub Secrets**, nunca em texto plano no repo — demonstre isso
   referenciando `${{ secrets.NOME }}` no workflow.
5. Documente em `PROMOCAO.md` o passo a passo de como uma mudança vai de dev pra staging/prod
   nesse fluxo (mesmo que seja um projeto pessoal sem staging real, descreva como SERIA feito).

## Restrições técnicas

- GitHub Actions (gratuito pra repo público).
- O workflow precisa rodar de verdade — não adianta só existir o YAML, tem que ter uma execução
  real visível no histórico de Actions do repo (print ou link do run).

## Entrega

PR com `.github/workflows/ci.yml` no projeto escolhido, mais
`modulos/12-deploys-e-ambientes/projeto/entrega/PROMOCAO.md` e evidência (link ou print) de uma
execução real do workflow passando.

# Módulo 12 — Deploys e Ambientes

## Objetivo

Pipeline que só roda na máquina de quem escreveu não é engenharia, é script pessoal. Este
módulo ensina CI/CD e separação de ambiente (dev/staging/prod) aplicados a projeto de dado.

## Pré-requisitos

Módulos 01, 10.

## Fundamentos

**Separação de ambiente.** Testar em dev usando o banco de prod (ou vice-versa) é como fazer
cirurgia de treino no paciente de verdade. Cada ambiente (dev/staging/prod) precisa da própria
config e do próprio dado — a única coisa que deveria ser idêntica entre eles é o CÓDIGO que
roda. Config diferente (URL de banco, feature flag, credencial) entra por variável de ambiente,
nunca por branch de código diferente.

**CI (Integração Contínua).** Rodar teste e lint manualmente antes de cada PR depende de
disciplina humana, que falha sob pressão de prazo. CI automatiza isso: todo PR dispara teste e
lint sozinho, e o merge fica bloqueado se algo falhar. Isso muda a pergunta de "será que alguém
lembrou de testar?" pra "o CI já me disse se quebrou".

**CD (Entrega/Deploy Contínuo).** Deploy manual é lento e propenso a erro humano (esqueceu um
passo, rodou na ordem errada). CD automatiza o caminho do merge até produção — e a parte que
mais importa não é a velocidade, é ter rollback fácil: se o deploy automatizado quebrar algo,
voltar pra versão anterior precisa ser tão automatizado quanto o deploy foi.

**Secrets management.** Uma credencial commitada no repo — mesmo que apagada num commit
seguinte — fica no histórico do git pra sempre, acessível por qualquer um com clone do repo.
Secret nunca entra no código: vive num cofre (GitHub Secrets, Vault, etc.), é injetado como
variável de ambiente só em runtime, e nunca aparece em log.

## Documentação de referência

- [GitHub Actions — documentação oficial](https://docs.github.com/en/actions) — como definir CI
  (fundamento 2), gratuito pra repo público.
- [GitHub Actions — secrets, documentação oficial](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions) —
  a implementação prática do fundamento 4 usada no projeto deste módulo.
- [The Twelve-Factor App — Dev/prod parity](https://12factor.net/dev-prod-parity) — o porquê por
  trás do fundamento 1, além do "boa prática" genérico.

## O que você vai construir

Um workflow de GitHub Actions que roda lint + teste automaticamente em todo PR de um projeto
seu de dado (pode reaproveitar o do Módulo 05 ou 11), com secrets geridos via GitHub Secrets
(nunca hardcoded), e documentação clara de como promover uma mudança de dev pra staging.

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`engineering-devops-automator`.

# Módulo 12 — Deploys e Ambientes

## Objetivo

Pipeline que só roda na máquina de quem escreveu não é engenharia, é script pessoal. Este
módulo ensina CI/CD e separação de ambiente (dev/staging/prod) aplicados a projeto de dado.

## Pré-requisitos

Módulos 01, 10.

## Conceitos-chave

- Separação de ambiente: config e dado nunca compartilhados entre dev/staging/prod
- CI: rodar teste e lint automaticamente a cada PR, antes de qualquer merge
- CD: deploy automatizado com rollback possível
- Secrets management: nunca em texto plano, nunca no repo

## Recursos gratuitos

- [GitHub Actions — documentação oficial](https://docs.github.com/en/actions) (gratuito pra repo público)
- [GitHub Actions — secrets documentação oficial](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions)
- [The Twelve-Factor App — Dev/prod parity](https://12factor.net/dev-prod-parity)

## O que você vai construir

Um workflow de GitHub Actions que roda lint + teste automaticamente em todo PR de um projeto
seu de dado (pode reaproveitar o do Módulo 05 ou 11), com secrets geridos via GitHub Secrets
(nunca hardcoded), e documentação clara de como promover uma mudança de dev pra staging.

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`engineering-devops-automator`.

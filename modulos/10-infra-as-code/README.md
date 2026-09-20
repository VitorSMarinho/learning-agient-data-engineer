# Módulo 10 — Infra as Code (IaC)

## Objetivo

Infra clicada manualmente no console não é reproduzível nem auditável. IaC trata infra como
código: versionada, revisada em PR, aplicada de forma determinística.

## Pré-requisitos

Módulo 01.

## Conceitos-chave

- Declarativo vs imperativo (Terraform declara o estado final, não os passos)
- State management e por que ele é a parte mais perigosa de IaC (nunca editar à mão)
- Módulos reutilizáveis vs copiar-colar configuração
- Plan antes de apply — revisar a mudança antes de aplicar, sempre

## Recursos gratuitos

- [Terraform — documentação oficial](https://developer.hashicorp.com/terraform/docs)
- [Terraform — tutoriais oficiais gratuitos](https://developer.hashicorp.com/terraform/tutorials)
- [Pulumi — documentação oficial](https://www.pulumi.com/docs/) (alternativa com linguagem de programação real, também tem tier gratuito)

## O que você vai construir

Definição Terraform de uma infra simples reproduzível (ex.: um bucket de storage + uma função
serverless, usando LocalStack do Módulo 07 pra não gastar crédito real), com `terraform plan`
documentado antes do `apply`, e a infra inteira destruível com um comando (`terraform destroy`).

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`engineering-devops-automator`.

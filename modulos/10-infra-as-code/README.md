# Módulo 10 — Infra as Code (IaC)

## Objetivo

Infra clicada manualmente no console não é reproduzível nem auditável. IaC trata infra como
código: versionada, revisada em PR, aplicada de forma determinística.

## Pré-requisitos

Módulo 01.

## Fundamentos

**Declarativo vs imperativo.** Um script imperativo (`aws s3 mb meu-bucket`) descreve os PASSOS
pra chegar num estado. Terraform é declarativo: você descreve o ESTADO FINAL desejado ("esse
bucket deve existir com essa config") e a ferramenta calcula sozinha o que precisa criar,
mudar ou destruir pra chegar lá. Isso importa porque declarativo é idempotente por natureza —
rodar duas vezes não duplica recurso, só confirma que o estado já bate.

**State management.** O Terraform mantém um arquivo de estado que mapeia "o que eu criei" pra
"o que existe de verdade" na infra real. Editar esse arquivo à mão, ou perder ele, dessincroniza
o que o Terraform PENSA que existe do que EXISTE — próximo apply pode tentar recriar algo que já
tá lá, ou destruir algo que não devia. É a parte mais perigosa da ferramenta justamente porque o
erro não aparece na hora, aparece no próximo apply.

**Módulos reutilizáveis.** Copiar e colar a mesma definição de infra pra cada ambiente
(dev/staging/prod) significa que uma correção precisa ser replicada manualmente em cada cópia —
e cedo ou tarde alguém esquece uma. Um módulo parametrizado (mesma definição, variáveis
diferentes por ambiente) garante que dev e prod só divergem onde você DECIDIU que deveriam.

**Plan antes de apply.** `terraform plan` mostra exatamente o que vai mudar antes de qualquer
coisa acontecer de verdade — o que vai ser criado, alterado, destruído. Aplicar sem revisar o
plan é como fazer merge sem ler o diff: às vezes é ok, às vezes destrói produção sem querer.

## Documentação de referência

- [Terraform — documentação oficial](https://developer.hashicorp.com/terraform/docs) — conceitos
  de state, plan, módulo (fundamentos 1, 2, 3, 4) direto da fonte.
- [Terraform — tutoriais oficiais gratuitos](https://developer.hashicorp.com/terraform/tutorials) —
  guiados, bons pro primeiro contato com `plan`/`apply`/`destroy`.
- [Terraform sobre Azure — guia oficial](https://learn.microsoft.com/en-us/azure/developer/terraform/) —
  vale ler se quiser ver como os mesmos conceitos se aplicam a um provider de nuvem real (Azure),
  não só ao provider Docker local que o projeto deste módulo usa.
- [Pulumi — documentação oficial](https://www.pulumi.com/docs/) — alternativa que usa linguagem
  de programação de verdade em vez de HCL, também com tier gratuito.

## O que você vai construir

Definição Terraform de uma infra simples reproduzível (ex.: um bucket de storage + uma função
serverless, usando LocalStack do Módulo 07 pra não gastar crédito real), com `terraform plan`
documentado antes do `apply`, e a infra inteira destruível com um comando (`terraform destroy`).

## Como é avaliado

Ao abrir o PR com a solução neste repo, rode a skill `revisar-modulo-agient`. Ela
aciona o subagente `engineering-devops-automator` sobre o diff, usando `projeto/CRITERIOS_ACEITE.md`
como rubrica, posta o resultado como comentário no PR e grava
`reviews/10-infra-as-code.json`.

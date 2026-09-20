# Módulo 07 — Event-Driven Architecture (Lambda, SQS)

## Objetivo

Nem todo pipeline roda em batch agendado. Parte do trabalho de dado hoje reage a evento em
tempo real (novo pedido, novo upload) via função serverless e fila — este módulo tira a
mágica de "Lambda" e "SQS" e mostra o padrão por trás.

## Pré-requisitos

Módulos 01, 03.

## Conceitos-chave

- Função serverless: gatilho, execução stateless, cold start
- Fila (SQS) como buffer de desacoplamento entre produtor e consumidor
- Idempotência em processamento de evento (mensagem pode chegar duplicada)
- Dead-letter queue: o que fazer quando o processamento falha repetidamente

## Recursos gratuitos

- [AWS Lambda — documentação oficial](https://docs.aws.amazon.com/lambda/) (free tier generoso)
- [Amazon SQS — documentação oficial](https://docs.aws.amazon.com/sqs/)
- [LocalStack — documentação oficial](https://docs.localstack.cloud/) (simula AWS localmente, sem gastar free tier testando)
- [Serverless Framework — documentação oficial](https://www.serverless.com/framework/docs) (facilita deploy, tem tier gratuito)

## O que você vai construir

Uma função (rodando via LocalStack local, sem custo de AWS real) disparada por mensagem numa
fila SQS simulada, que processa o evento de forma idempotente (mensagem duplicada não duplica
efeito) e envia pra dead-letter queue após N falhas.

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`engineering-devops-automator`.

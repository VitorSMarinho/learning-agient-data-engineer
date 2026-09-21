# Módulo 07 — Event-Driven Architecture (Lambda, SQS)

## Objetivo

Nem todo pipeline roda em batch agendado. Parte do trabalho de dado hoje reage a evento em
tempo real (novo pedido, novo upload) via função serverless e fila — este módulo tira a
mágica de "Lambda" e "SQS" e mostra o padrão por trás.

## Pré-requisitos

Módulos 01, 03.

## Fundamentos

**Função serverless: gatilho, execução stateless, cold start.** Uma função Lambda não fica
"rodando" esperando — ela é invocada por um gatilho (mensagem numa fila, upload num storage,
chamada HTTP) e some depois de terminar. Isso significa que ela não pode guardar estado entre
execuções na memória (stateless) — tudo que precisa persistir vai pra um banco ou storage
externo. "Cold start" é a latência extra da primeira invocação depois de um período ocioso,
quando o provedor precisa inicializar o ambiente de execução do zero — relevante pra entender
por que a mesma função às vezes responde rápido e às vezes não.

**Fila como buffer de desacoplamento.** Sem fila, um produtor que gera evento mais rápido do que
o consumidor processa derruba o consumidor (ou perde evento). A fila absorve esse descompasso —
o produtor só precisa conseguir publicar na fila (rápido), e o consumidor processa no próprio
ritmo, lendo da fila. Isso desacopla os dois: um pode cair e se recuperar sem o outro nem notar,
porque a fila segura a mensagem no meio tempo.

**Idempotência em processamento de evento.** Fila com garantia "at-least-once" (a maioria) pode
entregar a mesma mensagem mais de uma vez — é o preço de garantir que nenhuma mensagem se perca.
Isso significa que o consumidor precisa ser capaz de processar a MESMA mensagem duas vezes sem
duplicar o efeito (ex.: checar se já processou aquele ID antes de aplicar a mudança). Assumir
"cada mensagem chega exatamente uma vez" é um bug esperando pra acontecer.

**Dead-letter queue.** Quando uma mensagem falha o processamento repetidamente (código com bug,
dado malformado), reprocessá-la pra sempre trava a fila pras mensagens boas que vêm atrás. Uma
dead-letter queue é o destino dessas mensagens problemáticas depois de N tentativas — elas saem
do fluxo principal e ficam isoladas pra investigação manual, sem bloquear o resto.

## Documentação de referência

- [AWS Lambda — documentação oficial](https://docs.aws.amazon.com/lambda/) — a seção de
  "Lambda execution environment" explica cold start e ciclo de vida em detalhe.
- [Amazon SQS — documentação oficial](https://docs.aws.amazon.com/sqs/) — foque em "at-least-once
  delivery" e "dead-letter queues", são os dois conceitos que o projeto deste módulo cobra.
- [LocalStack — documentação oficial](https://docs.localstack.cloud/) — simula Lambda e SQS
  localmente, sem custo e sem precisar de conta AWS real — é como você resolve o projeto deste
  módulo sem gastar nada.

## O que você vai construir

Uma função (rodando via LocalStack local, sem custo de AWS real) disparada por mensagem numa
fila SQS simulada, que processa o evento de forma idempotente (mensagem duplicada não duplica
efeito) e envia pra dead-letter queue após N falhas.

## Como é avaliado

Ao abrir o PR com a solução neste repo, rode a skill `revisar-modulo-agient`. Ela
aciona o subagente `engineering-devops-automator` sobre o diff, usando `projeto/CRITERIOS_ACEITE.md`
como rubrica, posta o resultado como comentário no PR e grava
`reviews/07-event-driven-architecture.json`.

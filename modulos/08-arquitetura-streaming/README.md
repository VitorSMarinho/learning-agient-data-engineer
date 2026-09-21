# Módulo 08 — Arquitetura Streaming

## Objetivo

Batch processa o passado; streaming processa o presente. Este módulo ensina os conceitos de
processamento contínuo (Kafka como espinha dorsal) sem exigir cluster de produção pra aprender.

## Pré-requisitos

Módulo 07.

## Fundamentos

**Tópico, partição, consumer group.** Um tópico Kafka é dividido em partições — cada partição é
um log ordenado e imutável. A ordem só é garantida DENTRO de uma partição, não entre partições
do mesmo tópico, o que muda como você particiona dado (por chave, quando ordem importa). Um
consumer group permite que várias instâncias dividam o trabalho de ler um tópico sem duplicar
processamento — cada partição vai pra um consumer do grupo, nunca dois ao mesmo tempo.

**At-least-once vs exactly-once.** "Exactly-once" parece óbvio de querer, mas custa throughput e
complexidade (idempotência, transações). "At-least-once" é mais barato e mais comum na prática —
significa que uma mensagem pode ser processada mais de uma vez em caso de falha/retry, então seu
processamento downstream precisa ser idempotente (processar a mesma mensagem 2x não pode
duplicar o efeito). Escolher a garantia errada pro seu caso de uso é um bug de arquitetura, não
de código.

**Windowing.** Streaming não tem "fim" pra agregar como um `GROUP BY` de batch — você agrega
dentro de uma janela de tempo. Tumbling window são janelas fixas e não sobrepostas (0-1min,
1-2min...); sliding window se sobrepõem (últimos 5min, atualizando a cada 1min). A escolha
afeta latência de resultado e custo de computação — sliding window recalcula mais.

**Backpressure.** Quando o consumidor processa mais devagar que o producer emite, a fila cresce
sem limite até estourar memória ou disco. Um sistema de streaming de verdade precisa de uma
estratégia explícita pra isso: throttle no producer, buffer com limite e descarte, ou escalar o
consumer — "não fazer nada" não é uma opção válida em produção.

## Documentação de referência

- [Apache Kafka — documentação oficial](https://kafka.apache.org/documentation/) — a referência
  canônica de tópico/partição/consumer group (fundamento 1).
- [Confluent Developer — cursos gratuitos oficiais de Kafka](https://developer.confluent.io/) —
  cobre delivery semantics (fundamento 2) com exemplo prático.
- [Redpanda — documentação oficial](https://docs.redpanda.com/) — compatível com a API do Kafka,
  mais leve pra rodar local no projeto deste módulo.
- [Databricks — Structured Streaming](https://docs.databricks.com/en/structured-streaming/index.html) —
  vale ler se quiser ver como windowing e garantias de entrega (fundamentos 2 e 3) aparecem numa
  plataforma gerenciada de streaming, não só Kafka cru.

## O que você vai construir

Um tópico Kafka (ou Redpanda, local via Docker) com um producer que emite eventos e um consumer
que agrega em janela de tempo (ex.: contagem por minuto), documentando qual garantia de entrega
foi escolhida e por quê.

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`engineering-database-optimizer`.

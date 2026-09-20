# Módulo 08 — Arquitetura Streaming

## Objetivo

Batch processa o passado; streaming processa o presente. Este módulo ensina os conceitos de
processamento contínuo (Kafka como espinha dorsal) sem exigir cluster de produção pra aprender.

## Pré-requisitos

Módulo 07.

## Conceitos-chave

- Tópico, partição, consumer group (Kafka)
- At-least-once vs exactly-once semantics — o que cada garantia realmente custa
- Windowing (tumbling, sliding) pra agregação em tempo real
- Backpressure: o que acontece quando o consumidor é mais lento que o produtor

## Recursos gratuitos

- [Apache Kafka — documentação oficial](https://kafka.apache.org/documentation/)
- [Confluent Developer — cursos gratuitos oficiais de Kafka](https://developer.confluent.io/)
- [Redpanda — documentação oficial](https://docs.redpanda.com/) (compatível com Kafka, mais leve pra rodar local)

## O que você vai construir

Um tópico Kafka (ou Redpanda, local via Docker) com um producer que emite eventos e um consumer
que agrega em janela de tempo (ex.: contagem por minuto), documentando qual garantia de entrega
foi escolhida e por quê.

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`engineering-database-optimizer`.

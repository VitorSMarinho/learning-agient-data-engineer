# Módulo 09 — Observabilidade

## Objetivo

Pipeline que falha silenciosamente é pior que pipeline que não existe. Este módulo ensina a
instrumentar dado (não só aplicação): métrica de qualidade, log estruturado, alerta que
realmente aciona alguém.

## Pré-requisitos

Módulos 02, 03.

## Conceitos-chave

- Os três pilares: métricas, logs, traces — aplicados a pipeline de dado
- Data quality monitoring: volume esperado, schema esperado, freshness (dado está atualizado?)
- Log estruturado (JSON) vs log de texto solto — por que estruturado é pesquisável
- Alerta acionável: diferença entre "métrica que existe" e "alerta que alguém vai realmente agir"

## Recursos gratuitos

- [Prometheus — documentação oficial](https://prometheus.io/docs/introduction/overview/)
- [Grafana — documentação oficial](https://grafana.com/docs/grafana/latest/) (tier free/self-hosted)
- [OpenTelemetry — documentação oficial](https://opentelemetry.io/docs/)
- [Google SRE Book — capítulo de Monitoring (gratuito)](https://sre.google/sre-book/monitoring-distributed-systems/)

## O que você vai construir

Instrumentação do pipeline do Módulo 03 com métricas de volume/freshness expostas via
Prometheus, dashboard Grafana local mostrando essas métricas, e um alerta configurado que
dispara quando o volume de dado processado cai abaixo de um limite esperado.

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`engineering-sre`.

# Módulo 02 — Airflow Workflow Orchestration

## Objetivo

Pipeline de dado real não roda "na mão" nem só com cron. Precisa de orquestração com
dependência explícita entre tarefas, retry, alerta de falha e histórico de execução. Airflow é
o padrão de fato do mercado pra isso.

## Pré-requisitos

Módulo 01.

## Conceitos-chave

- DAG: tarefa, dependência, agendamento
- Operators (Python, Bash, Sensor) e quando usar cada um
- Retry, backoff, SLA e alerta de falha
- Idempotência: rodar a mesma tarefa duas vezes não pode duplicar dado

## Recursos gratuitos

- [Apache Airflow — documentação oficial](https://airflow.apache.org/docs/)
- [Astronomer Academy — cursos gratuitos oficiais de Airflow](https://academy.astronomer.io/)
- [Airflow — Best Practices (documentação oficial)](https://airflow.apache.org/docs/apache-airflow/stable/best-practices.html)

## O que você vai construir

Uma DAG Airflow (rodando local via Docker do Módulo 01) com no mínimo 3 tarefas dependentes,
retry configurado, e uma tarefa que só roda se a anterior confirmar sucesso via sensor —
processando algum dado real e idempotente (rodar duas vezes não duplica linha).

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`python-reviewer`.

# Projeto — Instrumentação de pipeline com métricas e alerta

## Contexto

Um pipeline que roda todo dia sem ninguém olhar pode estar quebrado há semanas antes de alguém
perceber (dado desatualizado, volume caindo, schema mudando). Instrumentação transforma "espero
que esteja funcionando" em "eu sei que está funcionando, e sou avisado quando não está".

## Tarefa

1. Pegue um pipeline já existente (reaproveite o do Módulo 03, ou construa uma versão mínima se
   ainda não tiver: um script que lê um CSV/API e grava um resultado processado).
2. Instrumente o pipeline com um cliente Prometheus (`prometheus_client` em Python) expondo pelo
   menos 3 métricas: `pipeline_linhas_processadas_total` (counter), `pipeline_execucao_segundos`
   (histogram/summary), e `pipeline_ultima_execucao_timestamp` (gauge, pra calcular freshness).
3. Suba Prometheus local via Docker fazendo scrape do endpoint `/metrics` do pipeline.
4. Suba Grafana local via Docker, conecte na fonte Prometheus, e monte um dashboard
   (`dashboard.json` exportado) com pelo menos: gráfico de volume processado ao longo do tempo,
   e indicador de freshness (há quanto tempo desde a última execução).
5. Configure uma regra de alerta (Prometheus Alertmanager, ou regra de alerta do próprio
   Grafana) que dispara quando o volume processado cai abaixo de um limite configurável, ou
   quando a freshness ultrapassa um limite (ex.: sem execução há mais de X minutos).
6. Demonstre o alerta dispararando de verdade: rode o pipeline com volume baixo propositalmente
   (ou pare de rodar por tempo suficiente) e capture a evidência (print, log, ou export do
   Alertmanager) de que o alerta ficou em estado `firing`.

## Restrições técnicas

- 100% local via Docker (Prometheus + Grafana) — sem SaaS de monitoramento pago.
- Métricas expostas via `prometheus_client` (Python) ou biblioteca equivalente na linguagem do
  seu pipeline.

## Entrega

PR com a pasta completa em `modulos/09-observabilidade/projeto/entrega/`: pipeline instrumentado,
`docker-compose.yml` (Prometheus+Grafana), `dashboard.json`, definição da regra de alerta, e
evidência do alerta disparando.

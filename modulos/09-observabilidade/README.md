# Módulo 09 — Observabilidade

## Objetivo

Pipeline que falha silenciosamente é pior que pipeline que não existe. Este módulo ensina a
instrumentar dado (não só aplicação): métrica de qualidade, log estruturado, alerta que
realmente aciona alguém.

## Pré-requisitos

Módulos 02, 03.

## Fundamentos

**Os três pilares (métricas, logs, traces) aplicados a dado.** Em aplicação, esses três pilares
respondem "o sistema tá de pé?". Em pipeline de dado, a pergunta muda pra "o dado tá certo?" —
métrica vira volume processado e freshness, log estruturado vira rastro de cada transformação
aplicada a um lote, e trace vira a linhagem de um registro através das etapas do pipeline. O
conceito é o mesmo, o que você mede é diferente.

**Data quality monitoring.** Um pipeline pode rodar sem erro e ainda entregar dado errado:
volume caiu 90% (fonte quebrou silenciosamente), schema mudou (coluna nova ou sumida), ou o dado
tá desatualizado (freshness — a última atualização foi há 3 dias, não há 3 horas como esperado).
Nenhum desses três é uma exceção que o código captura sozinho — precisa de instrumentação
deliberada checando essas três coisas depois de cada execução.

**Log estruturado vs texto solto.** `print(f"processei {n} registros")` é legível por humano mas
impossível de consultar em escala — você não consegue perguntar "quantas execuções processaram
menos de 100 registros na última semana?" num monte de string. Log estruturado (JSON, com campos
fixos como `timestamp`, `pipeline`, `registros_processados`) é uma linha de banco de dado
disfarçada de log — dá pra agregar, filtrar, alertar em cima.

**Alerta acionável.** Ter um dashboard bonito com métrica não é observabilidade — é decoração se
ninguém olha ou se, quando dispara, ninguém sabe o que fazer. Um alerta acionável tem um dono, um
runbook (o que fazer quando disparar) e um limiar calibrado pra não gerar ruído (alerta que
dispara toda hora vira alerta que todo mundo ignora).

## Documentação de referência

- [Prometheus — documentação oficial](https://prometheus.io/docs/introduction/overview/) — como
  métrica é coletada e consultada (fundamentos 1 e 2).
- [Grafana — documentação oficial](https://grafana.com/docs/grafana/latest/) — dashboard e regra
  de alerta (fundamento 4), tier free/self-hosted é suficiente pro projeto.
- [OpenTelemetry — documentação oficial](https://opentelemetry.io/docs/) — o padrão pra unificar
  métrica/log/trace (fundamento 1) se quiser ir além do Prometheus sozinho.
- [Google SRE Book — capítulo de Monitoring](https://sre.google/sre-book/monitoring-distributed-systems/) —
  gratuito, é a referência original do conceito de alerta acionável (fundamento 4).

## O que você vai construir

Instrumentação do pipeline do Módulo 03 com métricas de volume/freshness expostas via
Prometheus, dashboard Grafana local mostrando essas métricas, e um alerta configurado que
dispara quando o volume de dado processado cai abaixo de um limite esperado.

## Como é avaliado

Ao abrir o PR com a solução neste repo, rode a skill `revisar-modulo-agient`. Ela
aciona o subagente `engineering-sre` sobre o diff, usando `projeto/CRITERIOS_ACEITE.md`
como rubrica, posta o resultado como comentário no PR e grava
`reviews/09-observabilidade.json`.

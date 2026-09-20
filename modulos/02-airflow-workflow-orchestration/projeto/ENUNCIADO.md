# Projeto — DAG de Airflow com Dependência Real e Idempotência

## Contexto

Rodar script na mão ou via cron simples não dá visibilidade de falha, não tem retry automático
e não expressa dependência entre etapas. Uma DAG do Airflow torna o fluxo declarativo,
observável e recuperável.

## Tarefa

1. Escreva uma DAG (`dag_pipeline.py`) com **no mínimo 3 tasks** com dependência explícita entre
   elas (ex.: `extrair >> transformar >> carregar`).
2. Pelo menos uma task usa `PythonOperator` (ou `@task` do TaskFlow API) com lógica real, não
   um `print` vazio — ex.: ler um CSV de exemplo, aplicar uma transformação simples, escrever
   resultado.
3. Configure `retries` e `retry_delay` em pelo menos uma task, simulando uma falha
   intermitente controlada (ex.: falha nas 2 primeiras tentativas, sucede na 3ª — via uma
   variável de ambiente ou arquivo de estado que o teste controla).
4. A task de carga é **idempotente**: rodar a DAG duas vezes não duplica linha no destino
   (ex.: usa upsert por chave, ou limpa+recarrega a partição do dia).
5. Escreva um teste (`pytest`) que importa a DAG e valida a **estrutura** (número de tasks,
   ordem de dependência) sem precisar do scheduler do Airflow rodando.

## Restrições técnicas

- Airflow rodando local via Docker (pode reaproveitar a infra do Módulo 01, ou usar a imagem
  oficial `apache/airflow` com `docker compose`).
- Fonte de dado: um CSV de exemplo incluído na entrega (não precisa de API externa).
- Testes de estrutura da DAG não precisam do Airflow rodando — usam
  `airflow.models.DagBag` ou import direto do módulo da DAG.

## Entrega

PR com `modulos/02-airflow-workflow-orchestration/projeto/entrega/`: `dag_pipeline.py`,
`docker-compose.yml` (ou reaproveita infra existente, documentado), dado de exemplo,
`tests/test_dag_pipeline.py`, e `README.md` explicando como rodar a DAG e os testes.

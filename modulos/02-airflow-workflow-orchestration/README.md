# Módulo 02 — Airflow Workflow Orchestration

## Objetivo

Pipeline de dado real não roda "na mão" nem só com cron. Precisa de orquestração com
dependência explícita entre tarefas, retry, alerta de falha e histórico de execução. Airflow é
o padrão de fato do mercado pra isso.

## Pré-requisitos

Módulo 01.

## Fundamentos

**DAG: tarefa, dependência, agendamento.** DAG (grafo acíclico dirigido) é só um jeito formal de
dizer "essas tarefas têm ordem, e essa ordem não pode voltar em círculo". Cada nó é uma tarefa,
cada aresta é uma dependência ("B só roda depois que A terminar com sucesso"). Agendamento
(`schedule_interval`/cron) diz quando o Airflow deve criar uma nova execução do DAG — mas
agendar não é o ponto principal; o ponto é ter dependência explícita e visível, em vez de um
script gigante que faz tudo em sequência e falha sem avisar onde.

**Operators e quando usar cada um.** Operator é o "tipo" de tarefa — `PythonOperator` roda uma
função Python, `BashOperator` roda um comando shell, `Sensor` fica esperando uma condição
externa ficar verdadeira (arquivo aparecer, API responder) antes de deixar o DAG continuar.
Escolher o operator certo é escolher o nível de abstração certo: usar `BashOperator` pra chamar
um script Python externo é mais simples de debugar do que embutir lógica complexa dentro de um
`PythonOperator` gigante.

**Retry, backoff, SLA e alerta de falha.** Tarefa de pipeline de dado falha por motivo que não é
bug — API externa fora do ar, banco temporariamente sobrecarregado. Configurar retry (quantas
vezes) e backoff (quanto esperar entre tentativas) direto na tarefa é a diferença entre "o
pipeline se recupera sozinho" e "alguém precisa acordar de madrugada pra rodar de novo na mão".
SLA e alerta são o degrau seguinte: se mesmo com retry a tarefa não terminar no prazo esperado,
alguém precisa ser avisado — silêncio é o pior estado de um pipeline.

**Idempotência.** Rodar a mesma tarefa duas vezes (por retry, por reprocessamento manual, por
bug) não pode duplicar dado. Isso não é automático — precisa ser desenhado: usar `INSERT ... ON
CONFLICT` em vez de `INSERT` puro, ou limpar a partição do dia antes de reescrever, ou usar uma
chave de deduplicação. Pipeline não-idempotente parece funcionar até o dia em que alguém reroda
manualmente e duplica metade da tabela.

## Documentação de referência

- [Apache Airflow — documentação oficial](https://airflow.apache.org/docs/) — comece pelo
  tutorial de DAGs e a seção de conceitos core (Operators, Task Dependencies).
- [Airflow — Best Practices (documentação oficial)](https://airflow.apache.org/docs/apache-airflow/stable/best-practices.html) —
  a seção de idempotência e "avoid top-level code" é leitura obrigatória antes do projeto.
- [Astronomer Academy — cursos gratuitos oficiais de Airflow](https://academy.astronomer.io/) —
  trilha gratuita mantida pela empresa por trás de boa parte do desenvolvimento do Airflow.

## O que você vai construir

Uma DAG Airflow (rodando local via Docker do Módulo 01) com no mínimo 3 tarefas dependentes,
retry configurado, e uma tarefa que só roda se a anterior confirmar sucesso via sensor —
processando algum dado real e idempotente (rodar duas vezes não duplica linha).

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`python-reviewer`.

# Projeto — Contador de eventos em janela via Redpanda/Kafka

## Contexto

Dashboard de negócio que mostra "pedidos na última hora" não pode esperar um job batch rodar à
meia-noite. Esse número precisa vir de um pipeline que processa eventos conforme chegam, com uma
garantia de entrega explícita (você escolhe qual, mas documenta o motivo e o custo).

## Tarefa

1. Suba Redpanda (ou Kafka) localmente via Docker Compose (`docker-compose.yml` na entrega).
2. Crie um tópico `eventos-pedidos` com pelo menos 3 partições.
3. Escreva um **producer** (`producer.py`) que gera eventos sintéticos de pedido
   (`{"pedido_id": ..., "valor": ..., "timestamp": ...}`) e publica no tópico, em ritmo
   configurável (ex.: N eventos/segundo via argumento de linha de comando).
4. Escreva um **consumer** (`consumer.py`) que lê do tópico e agrega em **janela tumbling de 1
   minuto**: contagem de eventos e soma de valor por janela, imprimindo (ou gravando em
   `resultados.jsonl`) o resultado ao fechar cada janela.
5. Documente em `GARANTIA_DE_ENTREGA.md`: qual semântica você escolheu (at-least-once ou
   exactly-once), como ela foi implementada no consumer (ex.: commit de offset manual após
   processar, idempotência na agregação), e o que aconteceria de diferente com a outra opção.
6. Demonstre backpressure: um teste ou demonstração (script/README com passo a passo) mostrando
   o que acontece quando o producer publica mais rápido do que o consumer processa (ex.: lag de
   consumer group crescendo, visível via `rpk group describe` ou equivalente).

## Restrições técnicas

- 100% local via Docker (Redpanda ou Kafka + Zookeeper/KRaft) — sem serviço cloud pago.
- Python 3.11+, cliente `kafka-python` ou `confluent-kafka` (documentar a escolha).
- `docker-compose.yml` sobe o broker com um único comando.

## Entrega

PR com a pasta completa em `modulos/08-arquitetura-streaming/projeto/entrega/`: `producer.py`,
`consumer.py`, `docker-compose.yml`, `GARANTIA_DE_ENTREGA.md`, `README.md` de uso, e evidência
de execução real (`resultados.jsonl` de uma rodada, ou prints/log do teste de backpressure).

# Projeto — Produtor/Consumidor Assíncrono com Fila e Dead-Letter

## Contexto

Pipeline em batch agendado não serve pra tudo — parte do trabalho reage a evento em tempo real.
Este projeto tira a "mágica" de Lambda/SQS mostrando o padrão de fila + processamento
assíncrono idempotente, sem precisar de conta AWS.

## Tarefa

1. Suba uma fila local via **LocalStack** (simula SQS sem custo de AWS real) ou, alternativa
   mais simples, **Redis** local via Docker (lista/stream como fila).
2. Escreva um **produtor** que publica mensagens de evento (ex.: "novo pedido") na fila.
3. Escreva um **consumidor** que processa a mensagem de forma **idempotente** — processar a
   mesma mensagem (mesmo `id`) duas vezes não duplica o efeito (ex.: usa um registro de
   `ids processados` pra deduplicar).
4. Simule falha de processamento controlada (ex.: uma flag/variável que faz o consumidor falhar
   nas 2 primeiras tentativas de uma mensagem específica) e implemente **dead-letter**: após N
   falhas na mesma mensagem, ela vai pra uma fila/lista separada de "falhas", não fica em loop
   infinito nem se perde silenciosamente.

## Restrições técnicas

- LocalStack (SQS simulado) ou Redis, ambos via Docker local — zero custo de cloud real.
- Testes automatizados do produtor/consumidor não precisam da fila real rodando (podem mockar a
  interface da fila).

## Entrega

PR com `modulos/07-event-driven-architecture/projeto/entrega/`: `produtor.py`, `consumidor.py`,
`docker-compose.yml` (LocalStack ou Redis), `tests/`, `README.md` explicando como rodar e como
verificar a dead-letter funcionando.

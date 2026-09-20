# Projeto — Dashboard em tempo real via SSE/WebSocket

## Contexto

Fecha a trilha ligando o streaming (Módulo 08) direto na tela: em vez de um dashboard que o
usuário atualiza apertando F5, a tela se atualiza sozinha conforme o dado chega — e o sistema
precisa aguentar uma rajada de eventos sem travar a interface.

## Tarefa

1. Estenda o dashboard do Módulo 13 (ou construa um mínimo equivalente) com um componente que
   recebe dado em tempo real do consumer do Módulo 08.
2. Escolha SSE ou WebSocket (documente o motivo da escolha em `DECISAO_TRANSPORTE.md`: latência,
   complexidade, suporte a mensagem bidirecional — o que pesou na decisão).
3. Implemente o backend que expõe o stream (ex.: Route Handler do Next.js com streaming, ou um
   servidor WebSocket simples) conectado à saída do consumer Kafka/Redpanda do Módulo 08.
4. No front-end, pelo menos 1 componente reflete o dado mais recente sem reload manual — evidencie
   com um gif/vídeo curto mostrando o número mudando sozinho enquanto o producer roda.
5. Implemente e documente uma estratégia de backpressure no front-end: o que acontece se os
   eventos chegarem mais rápido do que a UI consegue renderizar (ex.: throttle/debounce de
   atualização de estado, buffer com descarte do mais antigo) — não pode ser "renderiza tudo sem
   controle e deixa travar".

## Restrições técnicas

- SSE nativo ou biblioteca WebSocket madura (`ws`, `socket.io`) — sem serviço de terceiros pago.
- Reaproveita o producer/consumer do Módulo 08 como fonte real de eventos (não é obrigatório
  usar o broker inteiro — pode simplificar a fonte de eventos, desde que documentado).

## Entrega

PR com a pasta completa em `modulos/14-realtime-dashboard/projeto/entrega/`: código do
backend+frontend, `DECISAO_TRANSPORTE.md`, descrição da estratégia de backpressure, e
gif/vídeo/print-sequence evidenciando a atualização em tempo real.

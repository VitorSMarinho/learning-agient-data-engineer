# Critérios de Aceite — Módulo 14

## Obrigatórios (bloqueiam aprovação)

- [ ] Componente do front-end atualiza sozinho com dado novo, sem reload manual — evidenciado
  por gif/vídeo, não só afirmado em texto.
- [ ] Transporte (SSE ou WebSocket) implementado de verdade, conectado a uma fonte real de
  eventos (consumer do Módulo 08 ou equivalente simplificado documentado).
- [ ] `DECISAO_TRANSPORTE.md` justifica a escolha SSE vs WebSocket com trade-offs reais
  (latência, complexidade, necessidade de bidirecional), não genérico.
- [ ] Estratégia de backpressure no front-end implementada no código (throttle, debounce, ou
  buffer com descarte) — não é "não implementei, mas documentei que seria importante".
- [ ] Nenhuma credencial/endpoint hardcoded que devesse ser configurável via env var.

## Opcionais (nota, não bloqueiam)

- [ ] Reconexão automática se a conexão SSE/WebSocket cair.
- [ ] Indicador visual de "conectado/desconectado" na UI.
- [ ] Teste automatizado da lógica de backpressure (ex.: simula rajada e confere que o estado
  não cresce sem controle).

**Veredito final**: `aprovado` se os 5 itens obrigatórios atendem; `precisa_ajuste` caso contrário.

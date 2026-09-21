# Módulo 14 — Realtime Dashboard

## Objetivo

Módulo de fechamento da trilha: liga o streaming (Módulo 08) direto numa interface que atualiza
sozinha, sem o usuário apertar F5. É onde engenharia de dado encontra front-end de verdade.

## Pré-requisitos

Módulos 08, 13.

## Fundamentos

**WebSocket vs SSE.** WebSocket é bidirecional (cliente e servidor mandam mensagem a qualquer
momento) e mais complexo de configurar. Server-Sent Events é unidirecional (só o servidor manda
pro cliente), roda sobre HTTP comum, e é mais simples de implementar e depurar. Pra um dashboard
que só RECEBE atualização (não precisa mandar nada de volta em tempo real), SSE geralmente é a
escolha mais simples que resolve o problema — WebSocket vale quando você precisa de via dupla de
verdade.

**Estado atualizado por stream, não polling.** Polling ingênuo (`fetch` a cada 5 segundos) gasta
requisição mesmo quando nada mudou, e o delay até o usuário ver a mudança é, na média, metade do
intervalo de polling. Uma conexão de stream (SSE/WebSocket) empurra a atualização assim que ela
acontece do lado do servidor — sem requisição desperdiçada, sem delay artificial.

**Backpressure no front-end.** Se o servidor manda eventos mais rápido do que o navegador
consegue re-renderizar (ex.: 100 eventos por segundo, mas o componente é pesado), a UI trava ou
o navegador acumula um backlog de renders pendentes. A estratégia comum é agrupar eventos que
chegam numa janela curta (debounce/throttle) e renderizar o estado consolidado, não cada evento
individualmente.

## Documentação de referência

- [MDN — Server-Sent Events](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events) —
  referência técnica gratuita, cobre a API usada pelo fundamento 1 e 2.
- [MDN — WebSockets API](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API) — pra
  comparar contra SSE e decidir qual usar (fundamento 1).
- [Next.js — Route Handlers com streaming, documentação oficial](https://nextjs.org/docs/app/building-your-application/routing/route-handlers) —
  como implementar o lado servidor de SSE na mesma stack usada no `learning-agient`.

## O que você vai construir

Uma extensão do dashboard do Módulo 13 que recebe atualização em tempo real via SSE ou
WebSocket a partir do consumer do Módulo 08, com pelo menos um componente que reflete o dado
mais recente sem reload manual, e uma estratégia documentada pra não sobrecarregar a UI se os
eventos chegarem em rajada.

## Como é avaliado

Ao abrir o PR com a solução neste repo, rode a skill `revisar-modulo-agient`. Ela
aciona o subagente `react-reviewer` sobre o diff, usando `projeto/CRITERIOS_ACEITE.md`
como rubrica, posta o resultado como comentário no PR e grava
`reviews/14-realtime-dashboard.json`.

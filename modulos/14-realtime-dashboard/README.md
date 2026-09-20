# Módulo 14 — Realtime Dashboard

## Objetivo

Módulo de fechamento da trilha: liga o streaming (Módulo 08) direto numa interface que atualiza
sozinha, sem o usuário apertar F5. É onde engenharia de dado encontra front-end de verdade.

## Pré-requisitos

Módulos 08, 13.

## Conceitos-chave

- WebSocket vs Server-Sent Events (SSE) pra atualização em tempo real — trade-off de cada um
- Estado no front-end atualizado por stream (não polling ingênuo de API a cada N segundos)
- Backpressure no front-end: o que fazer quando o evento chega mais rápido do que a UI renderiza

## Recursos gratuitos

- [MDN — Server-Sent Events (referência técnica gratuita)](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events)
- [MDN — WebSockets API (referência técnica gratuita)](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API)
- [Next.js — documentação oficial](https://nextjs.org/docs) (Route Handlers com streaming)

## O que você vai construir

Uma extensão do dashboard do Módulo 13 que recebe atualização em tempo real via SSE ou
WebSocket a partir do consumer do Módulo 08, com pelo menos um componente que reflete o dado
mais recente sem reload manual, e uma estratégia documentada pra não sobrecarregar a UI se os
eventos chegarem em rajada.

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`react-reviewer`.

# Módulo 13 — Prática: Data Dashboard

## Objetivo

Dado processado que ninguém vê não gera decisão. Este módulo fecha o pipeline com uma camada
de visualização real — um dashboard que uma pessoa não técnica consegue usar.

## Pré-requisitos

Módulo 03 (dado já processado e disponível).

## Conceitos-chave

- Modelagem de dado pra consumo analítico (tabela larga vs normalizada, o que serve melhor pra
  dashboard)
- Escolha de gráfico certo pra cada tipo de pergunta (comparação, tendência, distribuição)
- Performance de query sob dashboard (agregação pré-calculada vs on-the-fly)

## Recursos gratuitos

- [Next.js — documentação oficial](https://nextjs.org/docs)
- [Recharts — documentação oficial](https://recharts.org/) (biblioteca de gráfico React)
- [Streamlit — documentação oficial](https://docs.streamlit.io/) (alternativa mais rápida, só Python)

## O que você vai construir

Um dashboard (Next.js+Recharts, ou Streamlit se preferir manter tudo em Python) consumindo o
dado processado do Módulo 03, com pelo menos 3 visualizações respondendo perguntas de negócio
diferentes (comparação, tendência no tempo, distribuição), e documentação de por que cada
gráfico foi escolhido pra cada pergunta.

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`react-reviewer`.

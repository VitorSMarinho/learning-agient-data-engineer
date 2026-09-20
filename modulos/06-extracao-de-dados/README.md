# Módulo 06 — Extração de dados

## Objetivo

Aprofundamento em extração de fontes estruturadas de verdade: API paginada, autenticação,
banco de terceiro via CDC (change data capture) — não só "GET numa URL".

## Pré-requisitos

Módulos 01-04.

## Conceitos-chave

- Paginação (offset, cursor) e extração completa sem perder nem duplicar registro
- Autenticação de API (API key, OAuth2 básico) tratada como segredo, nunca hardcoded
- CDC (Change Data Capture): capturar só o que mudou num banco fonte, não tabela inteira toda vez
- Extração incremental com marca d'água (watermark) de última execução

## Recursos gratuitos

- [Airbyte — documentação oficial](https://docs.airbyte.com/) (conector open-source, referência de padrão de extração)
- [Debezium — documentação oficial](https://debezium.io/documentation/) (CDC open-source de referência)
- [REST API pagination patterns (documentação oficial GitHub API como exemplo real)](https://docs.github.com/en/rest/using-the-rest-api/using-pagination-in-the-rest-api)

## O que você vai construir

Um extrator que consome uma API pública paginada até o fim (sem perder página, sem duplicar),
autentica via variável de ambiente, e mantém uma marca d'água (última extração bem-sucedida)
pra próxima execução ser incremental.

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`python-reviewer`.

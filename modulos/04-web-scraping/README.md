# Módulo 04 — Web Scraping

## Objetivo

Quando não existe API, scraping é fonte de dado legítima — se feito com respeito (rate limit,
robots.txt) e resiliência (site muda de estrutura, scraper não pode quebrar silenciosamente).

## Pré-requisitos

Módulo 01.

## Conceitos-chave

- HTML estático (requests + BeautifulSoup) vs página renderizada por JS (Playwright)
- Rate limiting e respeito a `robots.txt` — scraping ético, não abusivo
- Resiliência a mudança de estrutura: seletor frágil vs seletor defensivo, teste que detecta
  quebra
- Armazenamento incremental (não re-scrapear o que já tem)

## Recursos gratuitos

- [Playwright — documentação oficial](https://playwright.dev/python/)
- [Beautiful Soup — documentação oficial](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
- [Scrapy — documentação oficial](https://docs.scrapy.org/)
- [MDN — HTTP e robots.txt (referência técnica gratuita)](https://developer.mozilla.org/en-US/docs/Web/HTTP)

## O que você vai construir

Um scraper que respeita `robots.txt` e rate limit, extrai dado estruturado de um site público
(estático ou dinâmico, sua escolha), grava incrementalmente (não duplica o que já coletou), e
tem teste automatizado que detecta quando o seletor não encontra mais o elemento esperado
(sinal de que o site mudou).

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`python-reviewer`.

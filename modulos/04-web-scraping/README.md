# Módulo 04 — Web Scraping

## Objetivo

Quando não existe API, scraping é fonte de dado legítima — se feito com respeito (rate limit,
robots.txt) e resiliência (site muda de estrutura, scraper não pode quebrar silenciosamente).

## Pré-requisitos

Módulo 01.

## Fundamentos

**HTML estático vs página renderizada por JS.** Se o dado que você quer já vem no HTML retornado
pelo servidor (`view-source` mostra ele), `requests` + `BeautifulSoup` resolve — é leve e rápido.
Se o dado só aparece depois que JavaScript roda no navegador (o `view-source` mostra um `<div
id="app">` vazio), você precisa de algo que executa um navegador de verdade, como Playwright.
Escolher a ferramenta errada pro caso (Playwright pra site estático) é desperdiçar
recurso; escolher `requests` pro caso errado (site dinâmico) é receber HTML vazio e não entender
por quê.

**Rate limiting e respeito a `robots.txt`.** `robots.txt` é o site te dizendo, formalmente, o
que ele permite ou não que scraper automatizado acesse — ignorar isso não é "esperto", é
antiético e pode te bloquear. Rate limiting (esperar entre requisições, nunca disparar tudo de
uma vez) existe porque um scraper mal comportado se parece com um ataque de negação de serviço
do ponto de vista do servidor alvo. Scraping responsável é o que garante que a técnica continue
disponível pra todo mundo — sites bloqueiam agressivamente quem abusa.

**Resiliência a mudança de estrutura.** Um seletor CSS/XPath que aponta pra uma classe genérica
(`div.content > p:nth-child(3)`) quebra no primeiro redesign do site, e quebra silenciosamente —
retorna vazio ou o elemento errado, sem lançar erro. Seletor defensivo usa atributo mais estável
(um `data-*` ou `id` específico, quando existe) e, mais importante, o código TESTA se encontrou
o que esperava e falha alto (erro visível) quando não encontra, em vez de seguir em frente com
dado vazio ou errado.

**Armazenamento incremental.** Re-scrapear tudo toda vez que o job roda desperdiça banda, tempo,
e aumenta a chance de ser bloqueado por excesso de requisição. A prática correta é guardar uma
chave única por item já coletado (URL, ID) e pular o que já existe — só processar o que é
genuinamente novo desde a última execução.

## Documentação de referência

- [Beautiful Soup — documentação oficial](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) —
  referência de parsing pra scraping de HTML estático.
- [Playwright — documentação oficial](https://playwright.dev/python/) — necessário só se o site
  escolhido renderizar conteúdo via JS; a seção de "Locators" é o que substitui seletor CSS
  frágil por uma abordagem mais robusta.
- [Scrapy — documentação oficial](https://docs.scrapy.org/) — referência de um framework de
  scraping completo (fila, rate limit, retry embutidos), útil como modelo mesmo que você não use
  o framework inteiro.
- [MDN — HTTP (referência técnica gratuita)](https://developer.mozilla.org/en-US/docs/Web/HTTP) —
  pra entender status code, header (`User-Agent`) e o protocolo por trás de qualquer requisição.

## O que você vai construir

Um scraper que respeita `robots.txt` e rate limit, extrai dado estruturado de um site público
(estático ou dinâmico, sua escolha), grava incrementalmente (não duplica o que já coletou), e
tem teste automatizado que detecta quando o seletor não encontra mais o elemento esperado
(sinal de que o site mudou).

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`python-reviewer`.

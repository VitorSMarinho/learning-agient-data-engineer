# Módulo 05 — Workshop (projetos práticos)

## Objetivo

Módulo de consolidação: nenhum conceito novo, só integrar tudo que os módulos 01-04 ensinaram
(infra, orquestração, pipeline, extração) num projeto único fim a fim, do jeito que aparece no
trabalho de verdade — misturado, não em caixinhas separadas.

## Pré-requisitos

Módulos 01-04.

## Conceitos-chave

- Integração de componentes já dominados em um sistema coeso
- Decisão de arquitetura sob restrição real (tempo, dado disponível, escopo)
- Documentação de decisão (por que essa abordagem e não outra)

## Recursos gratuitos

- Revisitar os recursos já listados nos módulos 01-04 — este módulo é aplicação, não conteúdo novo
- [Awesome Data Engineering (lista curada de recursos gratuitos no GitHub)](https://github.com/igorbarinov/awesome-data-engineering)

## O que você vai construir

Um projeto que combina scraping ou extração de API (Módulo 04), pipeline com transformação e
validação (Módulo 03), orquestrado por Airflow (Módulo 02), tudo rodando em Docker Compose
(Módulo 01) — um sistema pequeno mas completo, com um `ARQUITETURA.md` documentando as decisões.

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`python-reviewer`.

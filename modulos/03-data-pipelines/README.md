# Módulo 03 — Data Pipelines

## Objetivo

ETL/ELT na prática: extrair de uma fonte real, transformar com regra de negócio testável, e
carregar num destino consultável — com qualidade de dado verificada em cada etapa, não só no
fim.

## Pré-requisitos

Módulos 01-02.

## Conceitos-chave

- ETL vs ELT e quando cada abordagem faz mais sentido
- Validação de qualidade de dado (schema, nulo inesperado, duplicata) em cada etapa
- Particionamento e incremental load (não reprocessar tudo toda vez)
- Testes de pipeline: dado de entrada conhecido → saída esperada conhecida

## Recursos gratuitos

- [dbt — documentação oficial](https://docs.getdbt.com/) (transformação testável, tem tier gratuito)
- [Great Expectations — documentação oficial](https://docs.greatexpectations.io/) (validação de qualidade de dado)
- [pandas — documentação oficial](https://pandas.pydata.org/docs/)
- [Fundamentals of Data Engineering (capítulo de amostra gratuito, O'Reilly)](https://www.oreilly.com/library/view/fundamentals-of-data/9781098108298/)

## O que você vai construir

Um pipeline (orquestrado pela DAG do Módulo 02) que extrai de uma fonte pública gratuita (API
ou CSV), aplica pelo menos 2 transformações com regra de negócio testada via pytest, valida
qualidade (schema + nulo) antes de carregar, e faz carga incremental (só processa o que é novo).

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`python-reviewer`.

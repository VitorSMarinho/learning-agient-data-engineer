# Módulo 03 — Data Pipelines

## Objetivo

ETL/ELT na prática: extrair de uma fonte real, transformar com regra de negócio testável, e
carregar num destino consultável — com qualidade de dado verificada em cada etapa, não só no
fim.

## Pré-requisitos

Módulos 01-02.

## Fundamentos

**ETL vs ELT.** A diferença é ONDE a transformação acontece. ETL transforma antes de carregar
(fora do destino final, em memória ou num sistema intermediário) — bom quando o destino é caro
ou limitado. ELT carrega o dado bruto primeiro e transforma dentro do próprio destino (um banco
analítico moderno, por exemplo) — bom quando o destino é barato de escalar e você quer manter o
dado bruto disponível pra reprocessar com regra nova sem re-extrair da fonte. Não existe certo
universal, existe a pergunta: "onde é mais barato e mais seguro transformar, aqui?"

**Validação de qualidade de dado em cada etapa.** Validar só no fim é tarde demais — se a
extração já trouxe um schema errado, toda transformação em cima dele desperdiça trabalho e pode
mascarar o problema. A prática correta é validar logo após CADA etapa: schema esperado bate?
Campo que nunca deveria ser nulo veio nulo? Tem linha duplicada que não deveria existir? Pipeline
que só descobre problema no relatório final já rodou errado por semanas sem ninguém perceber.

**Particionamento e carga incremental.** Reprocessar a tabela inteira toda vez que o pipeline
roda funciona com 1000 linhas e quebra com 100 milhões — fica lento, caro, e aumenta a janela de
erro. Particionar (por data, geralmente) e processar só o incremento (o que mudou desde a última
execução) é o que permite um pipeline continuar rápido conforme o volume de dado cresce.

**Testes de pipeline.** Teste de pipeline não é "rodou sem erro" — é "dado um input conhecido,
o output bate com o que eu esperava, exatamente". Isso significa ter um pequeno conjunto de
dado de entrada fixo (fixture) com resultado esperado calculado à mão, e comparar a saída real
da transformação contra esse gabarito. Sem isso, uma mudança de regra de negócio pode quebrar
um cálculo silenciosamente e só alguém vai notar quando o número errado já tiver virado
decisão de negócio.

## Documentação de referência

- [dbt — documentação oficial](https://docs.getdbt.com/) — leia sobre "tests" (o mecanismo
  nativo de validação de qualidade do dbt) mesmo se não for usar dbt no projeto, o modelo mental
  é o que importa.
- [Great Expectations — documentação oficial](https://docs.greatexpectations.io/) — referência
  de como formalizar "expectativas" de qualidade de dado como código, não como checagem manual.
- [pandas — documentação oficial](https://pandas.pydata.org/docs/) — a seção de
  "merge, join, concatenate" e de tratamento de dado ausente é o que mais aparece na prática.

## O que você vai construir

Um pipeline (orquestrado pela DAG do Módulo 02) que extrai de uma fonte pública gratuita (API
ou CSV), aplica pelo menos 2 transformações com regra de negócio testada via pytest, valida
qualidade (schema + nulo) antes de carregar, e faz carga incremental (só processa o que é novo).

## Como é avaliado

Ao abrir o PR com a solução neste repo, rode a skill `revisar-modulo-agient`. Ela
aciona o subagente `python-reviewer` sobre o diff, usando `projeto/CRITERIOS_ACEITE.md`
como rubrica, posta o resultado como comentário no PR e grava
`reviews/03-data-pipelines.json`.

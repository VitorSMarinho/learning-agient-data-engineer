# Módulo 11 — Data Sprint

## Objetivo

Segundo módulo de consolidação da trilha: integra infra (01), orquestração (02), pipeline (03),
extração (06), streaming (08) e observabilidade (09) num sprint com escopo definido por você
mesmo, simulando prazo real. Aqui o "mentor" é o subagente `engineering-software-architect`
revisando a decisão de arquitetura, não só o código.

## Pré-requisitos

Módulos 01-09.

## Fundamentos

**Definição de escopo sob restrição de tempo.** Escopo infinito com prazo finito é a receita
clássica pra entregar nada. A habilidade que este módulo força é decidir, ANTES de codar, o que
é o núcleo inegociável (o que prova que o sistema funciona) e o que é "seria legal mas corta se
faltar tempo" — e documentar essa decisão, não só descobrir na prática quando o prazo aperta.

**Trade-off de arquitetura documentado.** Toda decisão de arquitetura troca uma coisa por outra
(latência por consistência, simplicidade por flexibilidade, custo por robustez). Implementar sem
documentar o porquê significa que daqui a 3 meses ninguém — nem você — lembra se aquela escolha
foi deliberada ou só o caminho mais rápido de sexta-feira à noite. Documentar o trade-off é o que
transforma uma decisão em algo revisável e questionável depois.

**Revisão de arquitetura como prática.** Revisão de código linha a linha pega bug. Revisão de
arquitetura pega uma pergunta diferente: essa decisão de design ainda faz sentido pro problema
real, ou resolve um problema que você imaginou que teria? É uma camada de revisão que a maioria
dos times pula porque não tem um formato pra ela — um ADR (próximo tópico) é esse formato.

## Documentação de referência

- Revisite a documentação já linkada nos módulos 01, 02, 03, 06, 08, 09 — este módulo é síntese
  do que já foi aprendido, não conteúdo novo.
- [ADR (Architecture Decision Records) — guia oficial do padrão](https://adr.github.io/) — o
  formato usado pra documentar o trade-off do fundamento 2, com exemplos reais.

## O que você vai construir

Um sistema de dado de escopo médio (ex.: pipeline de streaming com observabilidade e infra
como código, combinando pelo menos 3 módulos anteriores), com pelo menos um ADR (`docs/adr/`)
documentando uma decisão de arquitetura relevante e por que a alternativa foi descartada.

## Como é avaliado

Ao abrir o PR com a solução neste repo, rode a skill `revisar-modulo-agient`. Ela
aciona o subagente `engineering-software-architect` sobre o diff, usando `projeto/CRITERIOS_ACEITE.md`
como rubrica, posta o resultado como comentário no PR e grava
`reviews/11-data-sprint.json`.

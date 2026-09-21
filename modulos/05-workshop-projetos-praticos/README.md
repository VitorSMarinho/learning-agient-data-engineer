# Módulo 05 — Workshop (projetos práticos)

## Objetivo

Módulo de consolidação: nenhum conceito novo, só integrar tudo que os módulos 01-04 ensinaram
(infra, orquestração, pipeline, extração) num projeto único fim a fim, do jeito que aparece no
trabalho de verdade — misturado, não em caixinhas separadas.

## Pré-requisitos

Módulos 01-04.

## Fundamentos

**Integração de componentes já dominados em um sistema coeso.** Saber usar Docker, saber usar
Airflow, saber escrever um scraper — cada um isolado — não é o mesmo que saber montar os três
funcionando juntos. Integração revela problema que nenhum módulo isolado mostra: a DAG do
Airflow precisa saber onde o scraper grava o dado, o container do scraper precisa estar na
mesma rede Docker que o Postgres, a ordem de subida dos serviços importa. É nessa fricção que
o aprendizado dos módulos anteriores vira competência de verdade.

**Decisão de arquitetura sob restrição real.** No mundo real você quase nunca tem tempo/recurso
infinito pra fazer a versão "perfeita". Este módulo força a mesma pressão em miniatura: com o
tempo e escopo que você tem, o que fica simples de propósito e o que precisa ser robusto? Essa
decisão consciente (e documentada) é mais valiosa como sinal de maturidade técnica do que
qualquer código sofisticado.

**Documentação de decisão.** Escrever POR QUE você escolheu uma abordagem (e não outra) é uma
habilidade separada de escrever código que funciona. Um `ARQUITETURA.md` curto que explica o
trade-off (ex.: "optei por polling em vez de webhook porque X") é o que permite que outra
pessoa — ou você mesmo, 6 meses depois — entenda a decisão sem precisar reconstruir o raciocínio
do zero lendo código.

## Documentação de referência

Este módulo é aplicação, não conceito novo — revisite a documentação já linkada nos módulos
01-04 conforme for precisando dela durante a integração. Um recurso adicional útil pra esse
momento específico:

- [Awesome Data Engineering (lista curada de recursos gratuitos no GitHub)](https://github.com/igorbarinov/awesome-data-engineering) —
  útil se, ao integrar, você perceber que precisa de uma ferramenta que os módulos anteriores
  não cobriram.

## O que você vai construir

Um projeto que combina scraping ou extração de API (Módulo 04), pipeline com transformação e
validação (Módulo 03), orquestrado por Airflow (Módulo 02), tudo rodando em Docker Compose
(Módulo 01) — um sistema pequeno mas completo, com um `ARQUITETURA.md` documentando as decisões.

## Como é avaliado

Ao abrir o PR com a solução neste repo, rode a skill `revisar-modulo-agient`. Ela
aciona o subagente `python-reviewer` sobre o diff, usando `projeto/CRITERIOS_ACEITE.md`
como rubrica, posta o resultado como comentário no PR e grava
`reviews/05-workshop-projetos-praticos.json`.

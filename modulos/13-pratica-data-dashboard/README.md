# Módulo 13 — Prática: Data Dashboard

## Objetivo

Dado processado que ninguém vê não gera decisão. Este módulo fecha o pipeline com uma camada
de visualização real — um dashboard que uma pessoa não técnica consegue usar.

## Pré-requisitos

Módulo 03 (dado já processado e disponível).

## Fundamentos

**Modelagem de dado pra consumo analítico.** Um dado normalizado (várias tabelas relacionadas,
sem repetição) é ótimo pra sistema transacional, mas força o dashboard a fazer JOIN toda vez que
alguém abre a tela. Uma tabela larga (desnormalizada, já com os campos que o dashboard precisa
juntos) é mais lenta de escrever mas muito mais rápida de ler — e dashboard é lido muito mais
vezes do que é escrito. A escolha certa depende de quem consome, não de "o correto
academicamente".

**Escolha de gráfico certo pra cada pergunta.** Gráfico de barra compara categorias. Linha mostra
tendência no tempo. Histograma mostra distribuição. Usar o gráfico errado (linha pra comparar 2
categorias, barra pra tendência de 12 meses) não é só estética — dificulta a pessoa não técnica
de tirar a conclusão certa rápido, que é o objetivo inteiro de um dashboard existir.

**Performance de query sob dashboard.** Se cada abertura do dashboard recalcula tudo do zero
(agregação on-the-fly num dataset grande), a experiência fica lenta e o custo de computação
escala com número de usuários. Pré-calcular agregações (num job separado, rodando antes) troca
"sempre atualizado na hora" por "rápido e barato de servir" — decisão consciente, não acidente.

## Documentação de referência

- [Next.js — documentação oficial](https://nextjs.org/docs) — se for pela stack usada no resto
  da trilha de aprendizado (mesma base do `learning-agient`).
- [Recharts — documentação oficial](https://recharts.org/) — biblioteca de gráfico React, cobre
  os tipos de gráfico do fundamento 2.
- [Streamlit — documentação oficial](https://docs.streamlit.io/) — alternativa só-Python, mais
  rápida pra prototipar se você não quer lidar com front-end separado.
- [Databricks SQL — dashboards, documentação oficial](https://docs.databricks.com/en/dashboards/index.html) —
  vale conhecer como um dashboard analítico é construído numa plataforma de dado gerenciada, não
  só com biblioteca de gráfico solta.

## O que você vai construir

Um dashboard (Next.js+Recharts, ou Streamlit se preferir manter tudo em Python) consumindo o
dado processado do Módulo 03, com pelo menos 3 visualizações respondendo perguntas de negócio
diferentes (comparação, tendência no tempo, distribuição), e documentação de por que cada
gráfico foi escolhido pra cada pergunta.

## Como é avaliado

Ao abrir o PR com a solução neste repo, rode a skill `revisar-modulo-agient`. Ela
aciona o subagente `react-reviewer` sobre o diff, usando `projeto/CRITERIOS_ACEITE.md`
como rubrica, posta o resultado como comentário no PR e grava
`reviews/13-pratica-data-dashboard.json`.

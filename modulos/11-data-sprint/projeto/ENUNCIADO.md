# Projeto — Sprint integrador com ADR

## Contexto

Este módulo não introduz conceito novo — testa se você consegue **combinar** o que já foi
construído nos módulos anteriores num sistema coerente, sob um escopo que você mesmo define e
tem que respeitar (simulando prazo real de sprint).

## Tarefa

1. Defina o escopo do seu sprint ANTES de codar: escreva `ESCOPO.md` listando explicitamente o
   que entra e o que fica de fora, combinando **pelo menos 3** dos módulos anteriores (ex.:
   pipeline do Módulo 03 + streaming do Módulo 08 + observabilidade do Módulo 09).
2. Implemente o sistema combinado, reaproveitando código dos módulos anteriores sempre que fizer
   sentido (não precisa reescrever do zero o que já existe).
3. Escreva pelo menos **um ADR** (Architecture Decision Record, formato do
   [adr.github.io](https://adr.github.io/)) em `docs/adr/0001-*.md` documentando uma decisão de
   arquitetura real que você tomou nesse sprint — contexto, decisão, alternativas consideradas e
   por que foram descartadas, consequências.
4. Ao final, escreva `RETROSPECTIVA.md`: o que ficou de fora do escopo original e por quê (todo
   sprint real corta alguma coisa — documentar o corte é parte do exercício).

## Restrições técnicas

- Reaproveite infraestrutura/código já validado nos módulos anteriores (Docker Compose, etc.) —
  não precisa reinventar.
- Escopo tem que ser realista pra completar sozinho: prefira integrar bem 3 módulos a tentar
  integrar 6 pela metade.

## Entrega

PR com a pasta completa em `modulos/11-data-sprint/projeto/entrega/`: código do sistema
integrado, `ESCOPO.md`, `docs/adr/0001-*.md`, `RETROSPECTIVA.md`.

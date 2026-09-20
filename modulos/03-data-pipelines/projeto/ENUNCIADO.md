# Projeto — Pipeline ETL Testável com Carga Incremental

## Contexto

Um pipeline que "parece funcionar" mas não tem teste é uma bomba-relógio: ninguém percebe
quando uma regra de transformação quebra até o dado errado já estar no relatório do cliente.

## Tarefa

1. Escreva um pipeline (`pipeline.py`) com 3 etapas claras: **extract** (lê de uma fonte
   pública gratuita — API ou CSV), **transform** (aplica pelo menos 2 transformações com regra
   de negócio, ex.: normalizar categoria + calcular campo derivado), **load** (grava resultado
   em arquivo Parquet/CSV ou SQLite local).
2. Cada transformação tem teste `pytest` próprio: dado de entrada conhecido → saída esperada
   conhecida (não é teste de "roda sem erro", é teste de valor correto).
3. Valide qualidade do dado **antes** da carga: schema esperado (colunas/tipos) e ausência de
   nulo em campo obrigatório — se a validação falhar, o pipeline para com mensagem clara, não
   carrega dado ruim silenciosamente.
4. Implemente **carga incremental**: uma segunda execução do pipeline, com o mesmo dado de
   entrada, não duplica registro no destino (idempotência) — e se rodar com dado novo, só
   processa o que é novo, não o histórico inteiro de novo.

## Restrições técnicas

- Fonte pública gratuita sem autenticação complexa (ex.: uma API pública tipo JSONPlaceholder,
  Open-Meteo, ou um CSV de dataset aberto).
- Python puro + `pandas` (ou equivalente), sem precisar de infra externa pra rodar os testes.

## Entrega

PR com `modulos/03-data-pipelines/projeto/entrega/`: `pipeline.py`, `tests/test_pipeline.py`,
`requirements.txt`, `README.md` documentando a fonte de dado escolhida e como rodar
pipeline + testes.

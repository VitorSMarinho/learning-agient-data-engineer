# Projeto — Extrator de API Paginada com Marca d'Água Incremental

## Contexto

"GET numa URL" não escala pra fonte real: API pagina, exige autenticação, e você precisa saber
exatamente onde parou pra não perder nem duplicar registro na próxima execução.

## Tarefa

1. Escolha uma API pública paginada (ex.: GitHub REST API — listagem de repositórios/issues de
   um usuário público, ou outra API gratuita com paginação por cursor/offset).
2. Escreva um extrator (`extrator.py`) que percorre **todas as páginas** até o fim, sem perder
   nem duplicar registro, mesmo se a API tiver centenas de itens.
3. Autenticação (se a API exigir) via variável de ambiente, nunca hardcoded — se a API escolhida
   não precisar de auth, documente essa escolha.
4. Implemente **marca d'água** (watermark): grave em arquivo/banco local o timestamp/cursor da
   última extração bem-sucedida, e na próxima execução, extraia só o que é novo desde essa marca.
5. Trate rate limit da API (ex.: header `X-RateLimit-Remaining` do GitHub) com espera adequada
   em vez de falhar.

## Restrições técnicas

- Python + `requests` (ou `httpx`). Sem framework de extração pesado — o objetivo é entender o
  padrão, não usar Airbyte pronto.
- Teste local do parsing/paginação pode mockar a resposta da API (não precisa bater na API real
  em todo teste).

## Entrega

PR com `modulos/06-extracao-de-dados/projeto/entrega/`: `extrator.py`,
`tests/test_extrator.py` (paginação e watermark mockados), `.env.example`, `README.md`
documentando a API escolhida e como validar a extração incremental.

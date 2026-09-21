# Módulo 06 — Extração de dados

## Objetivo

Aprofundamento em extração de fontes estruturadas de verdade: API paginada, autenticação,
banco de terceiro via CDC (change data capture) — não só "GET numa URL".

## Pré-requisitos

Módulos 01-04.

## Fundamentos

**Paginação sem perder nem duplicar registro.** API que devolve muito dado quase sempre pagina
a resposta — por offset (`?page=2`, simples mas pode pular/duplicar registro se o dado mudar
entre páginas) ou por cursor (um token que aponta exatamente "de onde continuar", mais robusto
contra mudança concorrente). Extrair "até o fim" exige saber quando parar: normalmente a API
sinaliza isso (página vazia, campo `has_more: false`, ausência de `next` cursor) — ignorar essa
condição de parada é a causa mais comum de extração incompleta.

**Autenticação de API como segredo.** Uma API key ou token OAuth é, funcionalmente, uma senha —
o mesmo princípio do Módulo 01 da Trilha de IA se aplica aqui: nunca hardcoded, sempre variável
de ambiente. OAuth2 adiciona uma camada: o token de acesso costuma expirar, então o código
precisa saber renovar (via refresh token) em vez de simplesmente falhar quando o token vence.

**CDC (Change Data Capture).** Reextrair uma tabela inteira toda vez que ela muda é caro e lento
conforme ela cresce. CDC captura especificamente O QUE MUDOU no banco fonte (inserção, update,
delete) — normalmente lendo o log de transação do banco, não fazendo `SELECT *` repetido. É a
diferença entre "escanear tudo de novo" e "escutar as mudanças conforme acontecem".

**Extração incremental com watermark.** Watermark é um marcador (timestamp, ID, ou posição)
gravado depois de cada extração bem-sucedida, indicando até onde você já processou. A próxima
execução começa a partir dali, não do zero. Sem watermark confiável, um extrator ou reprocessa
dado desnecessariamente (perde eficiência) ou perde dado entre execuções (perde corretude) — os
dois erros mais comuns de quem implementa isso pela primeira vez.

## Documentação de referência

- [GitHub REST API — Using pagination](https://docs.github.com/en/rest/using-the-rest-api/using-pagination-in-the-rest-api) —
  exemplo real e bem documentado de paginação por cursor/link header, ótimo pra praticar contra
  uma API que realmente existe e tem free tier generoso.
- [Airbyte — documentação oficial](https://docs.airbyte.com/) — mesmo sem usar a ferramenta,
  a documentação de "connectors" mostra o padrão de como um extrator de produção lida com
  paginação, autenticação e estado incremental.
- [Debezium — documentação oficial](https://debezium.io/documentation/) — referência de CDC
  open-source; a seção de conceitos gerais explica o modelo sem exigir que você suba a
  infraestrutura completa.

## O que você vai construir

Um extrator que consome uma API pública paginada até o fim (sem perder página, sem duplicar),
autentica via variável de ambiente, e mantém uma marca d'água (última extração bem-sucedida)
pra próxima execução ser incremental.

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`python-reviewer`.

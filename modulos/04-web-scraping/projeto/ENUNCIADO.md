# Projeto — Scraper Ético e Resiliente

## Contexto

Scraping malfeito derruba o site alvo, ignora as regras dele, e quebra silenciosamente na
primeira mudança de layout — sem ninguém perceber até o dado parar de chegar.

## Tarefa

1. Escolha um site público simples e estático (ex.: uma página de listagem tipo
   `quotes.toscrape.com` ou `books.toscrape.com` — sites feitos justamente pra praticar
   scraping) e escreva um scraper (`scraper.py`) que extrai dado estruturado (ex.: título,
   preço, categoria) de múltiplos itens.
2. **Verifique e respeite `robots.txt`** do domínio antes de scrapear — o código deve checar
   programaticamente, não só "eu li e tá ok".
3. Implemente **rate limiting** (delay entre requisições) e um `User-Agent` identificável (não
   finja ser um navegador pra enganar o servidor).
4. Grave o resultado de forma **incremental**: rodar o scraper duas vezes não duplica item já
   coletado (chave única por item).
5. Escreva um teste que **simula quebra de seletor** (HTML mockado sem o elemento esperado) e
   confirma que o scraper detecta e reporta isso claramente, em vez de retornar dado vazio/errado
   silenciosamente.

## Restrições técnicas

- `requests` + `BeautifulSoup` (site estático) é suficiente; `Playwright` só se o site escolhido
  precisar de JS renderizado.
- Sem serviço de proxy pago, sem burlar paywall ou autenticação.

## Entrega

PR com `modulos/04-web-scraping/projeto/entrega/`: `scraper.py`, `tests/test_scraper.py`,
`requirements.txt`, `README.md` (site escolhido, como rodar, como verificar que não duplica
item).

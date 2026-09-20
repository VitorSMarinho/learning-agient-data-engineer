# Critérios de Aceite — Módulo 04

## Obrigatórios (bloqueiam aprovação)

- [ ] Scraper extrai dado estruturado real de múltiplos itens de um site público.
- [ ] Checagem programática de `robots.txt` antes de scrapear (não só menção em comentário).
- [ ] Rate limiting (delay configurável entre requisições) e `User-Agent` identificável presentes
  no código.
- [ ] Gravação incremental: rodar 2x não duplica item já coletado (chave única testada).
- [ ] Teste que simula quebra de seletor (HTML sem o elemento esperado) e confirma detecção
  clara do problema, não falha silenciosa.
- [ ] Nenhuma tentativa de burlar autenticação/paywall/proteção anti-bot.

## Opcionais

- [ ] Backoff progressivo em caso de erro HTTP (429/5xx).
- [ ] README documenta explicitamente por que o site escolhido é adequado pra prática (termos
  de uso / natureza pública do dado).

**Veredito final**: `aprovado` se todos os obrigatórios atendem; `precisa_ajuste` caso contrário.

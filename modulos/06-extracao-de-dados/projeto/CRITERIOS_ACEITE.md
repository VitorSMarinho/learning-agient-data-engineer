# Critérios de Aceite — Módulo 06

## Obrigatórios (bloqueiam aprovação)

- [ ] Extrator percorre todas as páginas de uma API paginada real sem perder nem duplicar
  registro (testado com resposta mockada de múltiplas páginas).
- [ ] Autenticação (quando aplicável) via variável de ambiente, nunca hardcoded; `.env.example`
  presente.
- [ ] Marca d'água (watermark) implementada: execução seguinte usa o cursor/timestamp salvo
  pra extrair só o que é novo.
- [ ] Tratamento de rate limit (espera/retry), não apenas falha direta quando a API limita.
- [ ] Testes rodam sem depender da API real (resposta mockada).

## Opcionais

- [ ] Log claro de quantos registros novos foram extraídos por execução.
- [ ] Tratamento de erro de autenticação (401/403) com mensagem clara, não stack trace cru.

**Veredito final**: `aprovado` se todos os obrigatórios atendem; `precisa_ajuste` caso contrário.

# Critérios de Aceite — Módulo 12

## Obrigatórios (bloqueiam aprovação)

- [ ] `.github/workflows/ci.yml` existe e roda lint + testes automaticamente em push/PR.
- [ ] Existe uma execução real do workflow (evidência: link do Actions run ou print), não só o
  YAML nunca disparado.
- [ ] O workflow falha (check vermelho) quando lint ou teste falham — demonstrado ou explicado
  com evidência de configuração correta (`continue-on-error` não pode estar mascarando falha).
- [ ] Pelo menos uma config muda entre dev/prod via variável de ambiente, documentada — sem
  valor hardcoded no código pra essa config.
- [ ] Se há algum segredo no projeto, está em GitHub Secrets (`${{ secrets.* }}` no workflow),
  nunca em texto plano no repo.
- [ ] `PROMOCAO.md` explica o fluxo de dev pra staging/prod de forma concreta (não genérica tipo
  "faz o deploy").

## Opcionais (nota, não bloqueiam)

- [ ] Cache de dependências no workflow (mais rápido).
- [ ] Badge de status do CI no README do projeto.
- [ ] Deploy automatizado de verdade (não só CI, CD completo) com rollback documentado.

**Veredito final**: `aprovado` se os 6 itens obrigatórios atendem; `precisa_ajuste` caso contrário.

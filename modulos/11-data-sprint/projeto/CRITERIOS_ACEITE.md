# Critérios de Aceite — Módulo 11

## Obrigatórios (bloqueiam aprovação)

- [ ] `ESCOPO.md` existe e foi escrito ANTES da implementação (ou pelo menos reflete o escopo
  real entregue — não pode ser uma lista vaga tipo "melhorar o sistema").
- [ ] O sistema entregue combina de fato **pelo menos 3 módulos anteriores** funcionando juntos
  (não é 3 pastas separadas que não se conversam — tem integração real).
- [ ] Sistema roda de ponta a ponta com um comando ou sequência documentada e reproduzível.
- [ ] `docs/adr/0001-*.md` segue o formato ADR de verdade: contexto, decisão, alternativas
  consideradas (pelo menos 1 descartada e o motivo), consequências.
- [ ] `RETROSPECTIVA.md` nomeia explicitamente o que ficou de fora do escopo original e por quê.

## Opcionais (nota, não bloqueiam)

- [ ] Mais de 1 ADR.
- [ ] Testes automatizados cobrindo a integração entre os módulos combinados.
- [ ] Diagrama de arquitetura (mesmo que simples, ASCII ou imagem) do sistema resultante.

**Veredito final**: `aprovado` se os 5 itens obrigatórios atendem; `precisa_ajuste` caso contrário.

# Critérios de Aceite — Módulo 07

## Obrigatórios (bloqueiam aprovação)

- [ ] Produtor publica mensagem numa fila local real (LocalStack/SQS ou Redis), não um mock
  in-memory sem infra nenhuma.
- [ ] Consumidor processa mensagem de forma idempotente — reprocessar o mesmo `id` não duplica
  efeito (testado).
- [ ] Simulação de falha controlada implementada, com retry até N tentativas.
- [ ] Após esgotar as tentativas, mensagem vai pra dead-letter (fila/lista separada), não é
  perdida nem fica em loop infinito.
- [ ] Testes automatizados do produtor/consumidor rodam sem exigir a fila real ativa (interface
  mockada) — pelo menos um teste de integração pode exigir a fila local, mas os unitários não.

## Opcionais

- [ ] Log estruturado mostrando o ciclo de vida de uma mensagem (recebida → falha → retry →
  dead-letter ou sucesso).
- [ ] README compara brevemente a escolha LocalStack vs Redis e por quê.

**Veredito final**: `aprovado` se todos os obrigatórios atendem; `precisa_ajuste` caso contrário.

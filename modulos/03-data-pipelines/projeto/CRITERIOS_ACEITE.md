# Critérios de Aceite — Módulo 03

## Obrigatórios (bloqueiam aprovação)

- [ ] Pipeline com extract/transform/load claramente separados (funções ou módulos distintos,
  não um script monolítico misturado).
- [ ] Pelo menos 2 transformações com regra de negócio, cada uma com teste de valor
  (entrada conhecida → saída esperada verificada, não só "não lançou exceção").
- [ ] Validação de schema/nulo obrigatório **antes** da carga, com falha clara e não-silenciosa
  quando o dado não passa.
- [ ] Carga incremental/idempotente: segunda execução com mesmo dado não duplica registro no
  destino — demonstrado por teste ou passo documentado e reproduzível.
- [ ] Testes rodam sem precisar de infra externa (banco, API real) — usam fixture/dado local.

## Opcionais

- [ ] Particionamento do destino (ex.: por data).
- [ ] Log estruturado indicando quantas linhas foram processadas/rejeitadas por execução.

**Veredito final**: `aprovado` se todos os obrigatórios atendem; `precisa_ajuste` caso contrário.

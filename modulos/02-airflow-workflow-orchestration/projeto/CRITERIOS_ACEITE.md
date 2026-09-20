# Critérios de Aceite — Módulo 02

## Obrigatórios (bloqueiam aprovação)

- [ ] DAG com no mínimo 3 tasks e dependência explícita entre elas (não paralelas soltas sem
  relação).
- [ ] Pelo menos uma task executa lógica real (lê/transforma/escreve dado), não é um stub vazio.
- [ ] `retries`/`retry_delay` configurado em pelo menos uma task.
- [ ] Task de carga é idempotente — rodar a DAG 2x não duplica registro no destino (demonstrado
  no teste ou documentado com prova, ex.: upsert por chave).
- [ ] Teste `pytest` que valida a estrutura da DAG (tasks presentes, ordem de dependência) sem
  precisar do scheduler rodando.
- [ ] Nenhum segredo/credencial hardcoded.

## Opcionais

- [ ] Uso do TaskFlow API (`@task`) em vez de `PythonOperator` clássico.
- [ ] Simulação de falha intermitente com recuperação via retry, documentada.
- [ ] README explica a decisão de particionamento/idempotência escolhida.

**Veredito final**: `aprovado` se todos os obrigatórios atendem; `precisa_ajuste` caso contrário.

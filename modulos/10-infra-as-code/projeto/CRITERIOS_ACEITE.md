# Critérios de Aceite — Módulo 10

## Obrigatórios (bloqueiam aprovação)

- [ ] `terraform plan` roda sem erro e `plan-output.txt` mostra um plano real (recursos a
  criar), não um output vazio ou de erro.
- [ ] Infra organizada em pelo menos 1 módulo reutilizável (`modules/<nome>/`), parametrizado
  por variáveis — não é tudo hardcoded num `main.tf` só.
- [ ] `terraform apply` sobe a infra de verdade (evidência: `docker ps` mostrando os containers,
  ou equivalente) e `terraform destroy` limpa tudo sem deixar recurso órfão.
- [ ] Decisão sobre remote vs local state está documentada explicitamente no README (não
  ausente, não "não pensei sobre isso").
- [ ] Nenhuma credencial hardcoded nos arquivos `.tf` (se precisar de alguma, via variável de
  ambiente ou `.tfvars` não commitado, com `.tfvars.example`).

## Opcionais (nota, não bloqueiam)

- [ ] Uso de `for_each`/`count` pra evitar repetição quando aplicável.
- [ ] Validação de variáveis (`validation` block) nos módulos.
- [ ] CI simples que roda `terraform validate`/`plan` automaticamente (antecipa o Módulo 12).

**Veredito final**: `aprovado` se os 5 itens obrigatórios atendem; `precisa_ajuste` caso contrário.

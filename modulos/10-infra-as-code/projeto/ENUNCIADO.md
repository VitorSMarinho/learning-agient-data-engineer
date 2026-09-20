# Projeto — Infra reproduzível via Terraform (provider Docker)

## Contexto

"Funciona na minha máquina porque eu cliquei os botões certos" é o oposto de infra confiável.
Este projeto força infra 100% declarada em código, versionada, com plano revisável antes de
qualquer mudança real acontecer.

## Tarefa

1. Escolha um dos projetos anteriores que precisa de infra (ex.: o broker do Módulo 08, ou o
   Prometheus+Grafana do Módulo 09).
2. Escreva a definição Terraform (`main.tf` + variáveis) usando o **provider Docker do
   Terraform** (`kreuzwerker/docker`) pra provisionar os containers necessários — isso permite
   praticar IaC de verdade sem precisar de conta cloud paga.
3. Organize em pelo menos um **módulo reutilizável** (pasta `modules/`) em vez de tudo num
   arquivo só — ex.: um módulo `modules/broker/` parametrizado por variáveis (porta, nome).
4. Documente e execute o fluxo completo: `terraform init` → `terraform plan` (capture o output
   do plan num arquivo, `plan-output.txt`) → `terraform apply` → confirme que a infra subiu
   (`docker ps`) → `terraform destroy` limpo, sem sobra.
5. Configure remote state OU documente explicitamente por que usou state local pra este escopo
   (não pode ser "esqueci", tem que ser uma decisão justificada).

## Restrições técnicas

- Provider `kreuzwerker/docker` (ou equivalente local/free) — nada que exija conta AWS/GCP/Azure
  paga.
- Terraform ou Pulumi (se escolher Pulumi, justifique a troca no README).

## Entrega

PR com a pasta completa em `modulos/10-infra-as-code/projeto/entrega/`: arquivos `.tf`, pasta
`modules/`, `plan-output.txt` de uma execução real, `README.md` documentando o fluxo
init/plan/apply/destroy e a decisão de state.

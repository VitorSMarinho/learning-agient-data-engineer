# Critérios de Aceite — Módulo 09

## Obrigatórios (bloqueiam aprovação)

- [ ] Pipeline expõe endpoint `/metrics` com pelo menos as 3 métricas pedidas (counter de
  linhas processadas, histogram/summary de duração, gauge de timestamp da última execução).
- [ ] `docker-compose.yml` sobe Prometheus fazendo scrape do pipeline com um único comando.
- [ ] `docker-compose.yml` sobe Grafana conectado ao Prometheus, dashboard importável
  (`dashboard.json`) com volume ao longo do tempo + indicador de freshness.
- [ ] Regra de alerta definida como código (não só clicada na UI e esquecida) — arquivo de regra
  do Prometheus/Alertmanager ou provisioning do Grafana versionado no repo.
- [ ] Evidência real do alerta disparando (`firing`), não só a regra existindo sem nunca ter
  sido testada.
- [ ] Nenhuma credencial hardcoded (senha do Grafana, se mudada do default, via env var).

## Opcionais (nota, não bloqueiam)

- [ ] Log estruturado (JSON) do pipeline, não só métricas.
- [ ] Mais de um canal de alerta (ex.: webhook além do estado firing).
- [ ] Métrica adicional de qualidade de dado (ex.: % de linhas rejeitadas por schema inválido).

**Veredito final**: `aprovado` se os 6 itens obrigatórios atendem; `precisa_ajuste` caso contrário.

# Critérios de Aceite — Módulo 01

## Obrigatórios (bloqueiam aprovação)

- [ ] `docker compose up` sobe pelo menos 2 serviços sem erro, com um único comando.
- [ ] Os serviços estão numa rede Docker nomeada (não a rede default do Compose).
- [ ] Postgres usa volume nomeado; `docker compose down` (sem `-v`) seguido de `up` mantém o
  dado inserido anteriormente.
- [ ] Nenhuma credencial em texto plano no `docker-compose.yml`, `Dockerfile` ou código — tudo
  via `.env`, com `.env.example` sem valor real versionado.
- [ ] `Dockerfile` da aplicação é multi-stage (pelo menos 2 estágios `FROM`).
- [ ] Serviço Postgres tem `healthcheck` definido; serviço da aplicação usa
  `depends_on` com `condition: service_healthy`.

## Opcionais (não bloqueiam, mas somam)

- [ ] Script de setup (`setup.sh`/`.ps1`) documentado e funcional.
- [ ] README da entrega explica como verificar a persistência do volume passo a passo.
- [ ] Imagem final da aplicação é enxuta (base slim/alpine quando aplicável).

**Veredito final**: `aprovado` se todos os 6 itens obrigatórios atendem; `precisa_ajuste` caso
contrário, listando exatamente o que falta.

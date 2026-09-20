# Projeto — Ambiente Reprodutível com Docker Compose

## Contexto

"Funciona na minha máquina" é a frase mais cara em engenharia de dados: um pipeline que só
roda no notebook de quem escreveu não serve pra produção. Docker Compose resolve isso
declarando o ambiente inteiro (serviços, rede, volume, variável) como código versionável.

## Tarefa

1. Escreva um `docker-compose.yml` com no mínimo **2 serviços**: um banco Postgres e uma
   aplicação Python própria (pode ser um script simples que lê/escreve no banco — não precisa
   ser complexo, o foco é a infra, não a lógica de negócio).
2. Os dois serviços devem estar na mesma rede Docker nomeada (não a rede default).
3. O Postgres precisa de **volume nomeado** persistente (dado sobrevive a `docker compose down`
   sem `-v`).
4. Nenhuma credencial hardcoded no `docker-compose.yml` ou no código — tudo via `.env`
   (com `.env.example` versionado, sem valor real).
5. O serviço da aplicação Python tem um `Dockerfile` **multi-stage** (estágio de build separado
   do estágio final de runtime, imagem final sem ferramentas de build).
6. O serviço Postgres tem um `healthcheck` configurado, e o serviço da aplicação usa
   `depends_on` com `condition: service_healthy` (não sobe antes do banco estar pronto).
7. Um script `setup.sh` (ou `.ps1` se preferir Windows) que sobe tudo com um comando só,
   documentado no README da entrega.

## Restrições técnicas

- Docker + Docker Compose (Compose v2, sintaxe `docker compose`, não `docker-compose` legado).
- Tudo local, nenhuma dependência de conta cloud paga.
- A aplicação Python pode ser tão simples quanto: conecta no Postgres, cria uma tabela se não
  existir, insere uma linha, lê e imprime.

## Entrega

PR neste repo com o conteúdo em `modulos/01-infra-linux-docker/projeto/entrega/`: `docker-compose.yml`,
`Dockerfile`, `.env.example`, código da aplicação, `setup.sh`/`.ps1`, e `README.md` explicando
como rodar e como verificar que o volume persiste (`docker compose down` sem `-v`, sobe de novo,
dado continua lá).

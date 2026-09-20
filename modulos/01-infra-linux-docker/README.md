# Módulo 01 — Infra: Linux, Docker

## Objetivo

Engenharia de dados vive em Linux e em container. Este módulo é a base de infra que sustenta
todos os módulos seguintes: shell de verdade, não GUI, e ambiente reprodutível via Docker.

## Pré-requisitos

Nenhum — é o módulo de entrada da trilha.

## Conceitos-chave

- Shell scripting essencial (pipes, redirecionamento, permissões, processos)
- Docker: imagem vs container, camadas, volume, rede
- Docker Compose pra orquestrar múltiplos serviços locais (banco, mensageria, app)
- Reprodutibilidade: "funciona na minha máquina" vira "funciona em qualquer máquina com Docker"

## Recursos gratuitos

- [Docker — documentação oficial](https://docs.docker.com/)
- [Docker Compose — documentação oficial](https://docs.docker.com/compose/)
- [The Linux Command Line (livro gratuito, William Shotts)](https://linuxcommand.org/tlcl.php)
- [Explainshell](https://explainshell.com/) (decompõe qualquer comando shell, ótimo pra aprender fazendo)

## O que você vai construir

Um `docker-compose.yml` com no mínimo 2 serviços conectados em rede própria (ex.: Postgres +
um app Python que lê/escreve nele), com volume persistente, variáveis de ambiente via `.env`, e
um script shell de setup que sobe tudo com um único comando documentado.

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`engineering-devops-automator`.

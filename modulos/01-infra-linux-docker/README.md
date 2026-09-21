# Módulo 01 — Infra: Linux, Docker

## Objetivo

Engenharia de dados vive em Linux e em container. Este módulo é a base de infra que sustenta
todos os módulos seguintes: shell de verdade, não GUI, e ambiente reprodutível via Docker.

## Pré-requisitos

Nenhum — é o módulo de entrada da trilha.

## Fundamentos

**Shell scripting essencial.** Engenheiro de dados que só clica em GUI não escala: pipeline
roda em servidor sem tela, e automação de verdade é script. O núcleo é pequeno — pipe (`|`)
encadeia comandos, redirecionamento (`>`, `>>`, `2>`) controla onde saída e erro vão parar,
permissão (`chmod`, dono/grupo) decide quem pode rodar o quê, e processo (`ps`, `kill`, `&`)
é como você sabe o que tá rodando e como para. Não precisa decorar flag nenhuma — precisa
saber que essas peças existem e se combinam.

**Docker: imagem vs container, camadas, volume, rede.** Imagem é a receita (arquivos +
dependências congeladas); container é a receita executando. Cada instrução do Dockerfile vira
uma camada cacheável — por isso ordem importa (o que muda menos fica em cima, o que muda mais
fica embaixo, senão você invalida cache à toa). Container por padrão é descartável: quando ele
morre, o que tá dentro dele morre junto — por isso existe volume (dado que precisa sobreviver
ao container) e rede própria (containers se enxergam pelo nome do serviço, não por IP fixo).

**Docker Compose pra orquestrar múltiplos serviços locais.** Rodar `docker run` várias vezes
com flag manual não escala além de 1 serviço. Compose descreve TODOS os serviços (app, banco,
fila) e como eles se conectam num arquivo YAML só, e sobe/derruba tudo junto com um comando.
É o equivalente local de "infra como código" — antes de aprender Terraform/Kubernetes, você
aprende a mesma ideia num escopo menor e mais rápido de iterar.

**Reprodutibilidade.** "Funciona na minha máquina" é a frase mais cara da engenharia — significa
que o ambiente tem estado invisível que ninguém documentou. Docker resolve isso forçando o
ambiente inteiro (SO base, dependência, versão) a estar descrito em arquivo versionado. Se o
`docker-compose.yml` sobe limpo em qualquer máquina com Docker instalado, você não depende mais
da configuração manual de ninguém.

## Documentação de referência

- [Docker — documentação oficial](https://docs.docker.com/) — comece por "Get Started" e a
  seção de Dockerfile best practices (camadas e cache).
- [Docker Compose — documentação oficial](https://docs.docker.com/compose/) — foque em
  `depends_on`, `healthcheck` e `volumes` — são o que o projeto deste módulo vai cobrar.
- [The Linux Command Line (livro gratuito, William Shotts)](https://linuxcommand.org/tlcl.php) —
  os capítulos de redirecionamento e permissões cobrem o fundamento 1 na prática.
- [Explainshell](https://explainshell.com/) — cola qualquer comando shell complexo e ele
  decompõe flag por flag; útil quando você copiar um comando de algum lugar e não souber o
  que ele faz de verdade.

## O que você vai construir

Um `docker-compose.yml` com no mínimo 2 serviços conectados em rede própria (ex.: Postgres +
um app Python que lê/escreve nele), com volume persistente, variáveis de ambiente via `.env`, e
um script shell de setup que sobe tudo com um único comando documentado.

## Como é avaliado

Este módulo ainda não tem projeto prático detalhado. Quando tiver, será resolvido e submetido
via PR neste repo, revisado pela skill `revisar-modulo-agient` usando o subagente
`engineering-devops-automator`.

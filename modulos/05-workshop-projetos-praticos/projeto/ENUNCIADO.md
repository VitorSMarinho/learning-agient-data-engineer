# Projeto — Sistema Fim a Fim (Scraping → Pipeline → Orquestração)

## Contexto

No trabalho real, os componentes não aparecem separados em módulos de curso — aparecem
misturados, sob restrição de tempo e dado incompleto. Este projeto integra o que os módulos
01-04 ensinaram separadamente.

## Tarefa

1. Combine pelo menos **2 dos componentes anteriores** num fluxo único: por exemplo, o scraper
   do Módulo 04 alimenta o pipeline do Módulo 03, orquestrado pela DAG do Módulo 02, tudo
   rodando via Docker Compose do Módulo 01. (Pode reaproveitar código das entregas anteriores
   como ponto de partida — o objetivo aqui é integração, não reescrever do zero.)
2. O sistema roda **ponta a ponta com um comando** (ou uma DAG disparada uma vez), do dado bruto
   até o resultado final persistido.
3. Escreva um `ARQUITETURA.md` explicando: por que essa combinação de componentes, quais
   decisões técnicas foram tomadas sob quais restrições, e o que ficaria diferente com mais
   tempo/recurso.
4. Pelo menos um teste de integração que valida o fluxo completo (não só as partes isoladas).

## Restrições técnicas

- Reaproveitar as entregas dos módulos 01-04 é esperado e incentivado — não precisa reescrever
  scraper/pipeline do zero, precisa fazer eles conversarem.
- Tudo local/gratuito, sem dependência de serviço pago.

## Entrega

PR com `modulos/05-workshop-projetos-praticos/projeto/entrega/`: código integrado (pode
referenciar/copiar dos módulos anteriores), `ARQUITETURA.md`, teste de integração, `README.md`
com o comando único pra rodar tudo.

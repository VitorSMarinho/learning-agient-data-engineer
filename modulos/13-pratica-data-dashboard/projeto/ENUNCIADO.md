# Projeto — Dashboard de 3 perguntas de negócio

## Contexto

Dado processado guardado num arquivo não ajuda ninguém a decidir nada. Este projeto fecha o
ciclo: pega o resultado de um pipeline seu e transforma em algo que uma pessoa não técnica
conseguiria olhar e entender em segundos.

## Tarefa

1. Reaproveite o dado processado do Módulo 03 (ou de outro módulo, se fizer mais sentido).
2. Defina **3 perguntas de negócio diferentes** que esse dado consegue responder, cada uma de um
   tipo diferente: uma de **comparação** (ex.: categoria A vs B), uma de **tendência no tempo**
   (ex.: evolução por dia/semana), uma de **distribuição** (ex.: como os valores se espalham).
3. Construa o dashboard (Next.js + Recharts, ou Streamlit) com uma visualização por pergunta,
   escolhida especificamente pro tipo de pergunta (não "coloquei um gráfico de barra em tudo").
4. Adicione pelo menos **1 filtro interativo** (ex.: intervalo de data, categoria) que realmente
   recalcula o que é mostrado, não só decorativo.
5. Escreva `POR_QUE_ESSE_GRAFICO.md` justificando a escolha de cada um dos 3 gráficos pra sua
   pergunta correspondente.

## Restrições técnicas

- Next.js + Recharts, ou Streamlit — escolha uma stack e justifique no README se preferir manter
  tudo em Python (Streamlit) em vez de reaproveitar o Next.js da trilha de IA.
- Dado vem de um arquivo local ou do resultado de um pipeline já construído — não precisa de
  banco de produção.

## Entrega

PR com a pasta completa em `modulos/13-pratica-data-dashboard/projeto/entrega/`: código do
dashboard, `POR_QUE_ESSE_GRAFICO.md`, `README.md` de como rodar local, e print/gif das 3
visualizações com o filtro em ação.

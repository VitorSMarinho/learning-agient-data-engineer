# Critérios de Aceite — Módulo 08

## Obrigatórios (bloqueiam aprovação)

- [ ] `docker-compose.yml` sobe o broker (Redpanda ou Kafka) com um único comando, sem passo
  manual extra.
- [ ] `producer.py` publica eventos no tópico com schema consistente (`pedido_id`, `valor`,
  `timestamp`), taxa configurável por argumento de linha de comando.
- [ ] `consumer.py` implementa janela **tumbling de 1 minuto** de verdade (não é só ler e
  imprimir cada evento — tem agregação por janela de tempo, contagem + soma de valor).
- [ ] `GARANTIA_DE_ENTREGA.md` nomeia explicitamente at-least-once ou exactly-once, explica como
  foi implementada no código (aponta a linha/trecho relevante), e explica o custo da alternativa
  não escolhida.
- [ ] Demonstração de backpressure real (não só descrita em texto — script, log ou print
  mostrando o lag do consumer group crescendo quando o producer acelera).
- [ ] Nenhuma credencial/segredo hardcoded (broker local não deveria precisar, mas se usar algo
  como registry externo, vem de env var).

## Opcionais (nota, não bloqueiam)

- [ ] Testes automatizados da lógica de agregação de janela (sem depender do broker real rodando).
- [ ] Suporte a windowing sliding além de tumbling.
- [ ] Dashboard simples (mesmo que só terminal) mostrando a contagem por janela em tempo real.

**Veredito final**: `aprovado` se os 6 itens obrigatórios atendem; `precisa_ajuste` caso contrário.

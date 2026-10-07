# Requisitos com critérios de aceite mensuráveis por UC

# Requisitos por UC

## 1. Objetivo
API para:
- Abrir bilhete
- Encerrar bilhete
- Cancelar bilhete
- Consultar bilhetes
- Gerar relatório

## 2. Regras principais
- Dinheiro → exclusivamente centavos inteiros.
- Cobrança → frações de `FRACAO_MINUTOS`, arredondando para cima.
- Máximo → `TETO_DIARIO_CENTAVOS`.
- Dentro da tolerância → grátis.
- Passou da tolerância → cobra desde o início.
- Uma placa → apenas **1 bilhete aberto**.
- Histórico → mantém todos os bilhetes.

## 3. UC1 — Abrir

**POST `/bilhetes`**

Entrada:
- `placa`
- `entrada` (opcional)

Regras:
- Placa com **7 caracteres maiúsculos**.
- Sem `entrada` → utiliza o horário atual.
- É exclusivamente proibido haver outro bilhete aberto.

Resultado:
- `201` → criado.
- `422` → dados inválidos.
- `409` → bilhete já aberto.

## 4. UC2 — Encerrar

**POST `/bilhetes/{id}/encerramento`**

Processo:
1. Calcula duração.
2. Verifica tolerância.
3. Calcula frações.
4. Arredonda para cima.
5. Calcula valor.
6. Aplica teto.

Resultado:
- `200` → retorna `saida`, `minutos` e `valor_centavos`.

## 5. Estados

```text
aberto → encerrado
aberto → cancelado
```

- Encerrado → não reabre.
- Cancelado → sem cobrança.
- Encerrado → possui saída e valor.
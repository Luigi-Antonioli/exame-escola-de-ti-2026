# Casos de Borda

## 1. Abertura
- Placa válida → `201`.
- Placa inválida → `422`.
- `entrada` inválida → `422`.

## 2. Frações
Considerando `F = FRACAO_MINUTOS`:

- `F` minutos → 1 fração.
- `F + 1` minutos → 2 frações.

## 3. Teto
- Abaixo do teto → valor normal.
- No teto → valor igual ao teto.
- Acima do teto → limitar ao `TETO_DIARIO_CENTAVOS`.
**Nunca ultrapassar o teto.

## 4. Tolerância
Considerando `T = TOLERANCIA_MINUTOS`:

- `T - 1` → grátis.
- `T` → grátis.
- `T + 1` → cobra desde o primeiro minuto.

## 5. Encerramento
- Aberto → `200`, registra saída e valor.
- Já encerrado → `409`.
- Inexistente → `404`.

## 6. Cancelamento
- Aberto → `200`, fica `cancelado`, sem cobrança.
- Encerrado → `409`.
- Inexistente → `404`.

## 7. Placa
- Sem bilhete aberto → pode abrir.
- Com bilhete aberto → `409`.
- Após encerrar/cancelar → pode abrir novamente.

## 8. Relatório
- Encerrados → entram no faturamento e média.
- Abertos/cancelados → não entram.
- Média:
  - `46,4` → `46`
  - `46,5` → `47`
  - `46,6` → `47`

## 9. Histórico
- Retorna todos os bilhetes da placa.
- Mais recentes primeiro.
- Sem histórico → `[]`.

## 10. Ativos
- Retorna somente bilhetes `aberto`.
- Mais recentes primeiro.
- Nenhum → `[]`.

## 11. Data
- `2026-10-05` → válida.
- Formato/data inválida → `422`.
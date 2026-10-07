# Tarefas de Implementação

## 1. Preparação para implementar
- Criar API.
- Configurar `PORTA_SERVICO`.
- Configurar servidor.

## 2. Bilhetes
- Criar modelo.
- Implementar estados.
- Gerar IDs únicos.

## 3. Abertura
- `POST /bilhetes`
- Validar placa e entrada.
- Impedir dois bilhetes abertos na mesma placa.

## 4. Encerramento
- `POST /bilhetes/{id}/encerramento`
- Calcular duração e cobrança.
- Aplicar tolerância, frações e teto.

## 5. Consultas
- `GET /bilhetes/ativos`
- `GET /bilhetes?placa=...`
- `GET /relatorios/diario?data=...`

## 6. Cancelamento dos bilhetes
- `POST /bilhetes/{id}/cancelamento`
- Cancelar somente bilhetes abertos.

## 7. Erros
- Validar IDs, placas, datas e estados.
- Implementar códigos e mensagens do contrato.

## 8. Testes
- Testar cobrança, tolerância, frações e teto.
- Testar conflitos, cancelamento e IDs inexistentes.

## 9. Finalização
- Conferir endpoints e respostas.
- Conferir parâmetros da variante.
- Confirmar execução na `PORTA_SERVICO`.
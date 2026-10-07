# Decisões técnicas com justificativa (stack, persistência, relógio)

# Decisões Técnicas

## 1. Objetivo
- Criar uma API REST seguindo o contrato do enunciado.
- Separar rotas, regras de negócio, dados e cálculos.

## 2. Tecnologia
- **Python + FastAPI**
- Facilita criação de endpoints, validações e respostas HTTP.

## 3. Organização
- **Rotas** → recebem requisições e retornam respostas.
- **Serviço** → regras dos bilhetes.
- **Modelo** → dados do bilhete.
- **Persistência** → guarda os bilhetes.
- **Cálculo** → duração e cobrança.

## 4. Bilhete
Possui:
- `id`
- `placa`
- `entrada`
- `saida`
- `status`
- `minutos`
- `valor_centavos`

Cancelado → sem cobrança.

## 5. Persistência
- Usar **memória**.
- Dados permanecem enquanto a API estiver rodando.

## 6. ID
- Inteiro, único e sequencial.
- Começa em `1`.
- Nunca reutilizar.

## 7. Datas
- Usar ISO-8601 com fuso `-03:00`.
- `entrada` informada → usar o valor recebido.
- Sem `entrada` → usar horário atual.
- `saida` → horário do encerramento.

## 8. Cobrança
1. Calcular duração.
2. Verificar tolerância.
3. Dividir por `FRACAO_MINUTOS`.
4. Arredondar para cima.
5. Calcular valor.
6. Aplicar `TETO_DIARIO_CENTAVOS`.

## 9. Valores
- Sempre **inteiros em centavos**.
- Nunca usar ponto flutuante.

## 10. Erros
- Validar dados antes da operação.
- Retornar exatamente os códigos e formatos definidos no `spec.md`.

## 11. Testes
- Permitir informar `entrada` manualmente.
- Facilita testar tolerância, frações e teto.

## 12. Execução
- API em `localhost:{PORTA_SERVICO}`.
- Usar a porta definida pela variante.
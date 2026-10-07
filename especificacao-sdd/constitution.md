## Constituição do projeto - Convenções persistentes (ex.: "valores monetários sempre em centavos inteiros"; "todo endpoint documenta status de erro")

# Convenções Persistentes

- Seguir o contrato do enunciado.
- Bilhete: `aberto`, `encerrado` ou `cancelado`.
- Uma placa → apenas **1 bilhete aberto**.
- Dinheiro → **centavos inteiros**.
- Cobrança → não ultrapassa `TETO_DIARIO_CENTAVOS`.
- Datas → ISO-8601 com `-03:00`.
- `entrada` → informada ou horário atual.
- ID → único e não reutilizado.
- Histórico → nunca apagar bilhetes.
- Placa → **7 caracteres alfanuméricos maiúsculos**.

### HTTP
- `200/201` → sucesso
- `422` → dado inválido
- `409` → conflito
- `404` → não encontrado

### Regras
- Encerrado → não pode reabrir.
- Cancelado → sem cobrança.
- Encerrado → possui saída e valor.
- Histórico → mantém todos os bilhetes.
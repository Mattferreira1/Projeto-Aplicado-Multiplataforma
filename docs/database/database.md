## Modelagem do Banco de Dados (Diagrama ER simplificado)
# Entidades:
- USER(id, email, senhaHash, nome, cnpj, setor, createdAt)
- CATEGORY(id, userId, name, type)
- EXPENSE(id, userId, categoryId, amount, date, description, vendor, recurrence, receiptUrl)
- REVENUE(id, userId, categoryId, amount, date, client, description)
- REPORT(id, userId, periodo, totalRevenue, totalExpense, netProfit, profitMargin)
- AUDIT_LOG(id, userId, actionType, entityId, entityType, timestamp)

# Relacionamentos:

- USER (1) — (N) EXPENSE
- USER (1) — (N) REVENUE
- USER (1) — (N) REPORT
- USER (1) — (N) CATEGORY
- EXPENSE (N) — (1) CATEGORY
- REVENUE (N) — (1) CATEGORY
 

![alt text](image.png)
# Requisitos Funcionais e Não-Funcionais
## REQUISITOS FUNCIONAIS (RF):
- RF-01 — Cadastro de usuário (conta com e-mail/senha, login Google, perfil com CNPJ e ramo de atividade)
- RF-02 — Gestão de despesas (inserir, editar, excluir, categorias, recorrência, comprovante opcional)
- RF-03 — Gestão de receitas (inserir, editar, excluir, categorias, observações)
- RF-04 — Relatórios e cálculos (lucro líquido, margem de lucro, relatórios mensais/trimestrais/anuais, exportar CSV/PDF, alertas automáticos)
- RF-05 — Painel administrativo (CRUD usuários, métricas, logs)
- RF-06 — Integrações (Google OAuth, CSV bancário, ERPs futuros)
- RF-07 — Auditoria (logs e histórico de versões)

## REQUISITOS NÃO-FUNCIONAIS (RNF):
- Segurança: autenticação JWT ou Firebase Auth, criptografia, TLS, proteção contra ataques comuns
- Performance: resposta <300ms, paginação e filtros
- Usabilidade: design responsivo, dashboards intuitivos
- Escalabilidade: banco na nuvem, escalonamento horizontal, backups
- Manutenibilidade: arquitetura em camadas, testes automatizados
- Conformidade: LGPD (consentimento e exclusão de dados)

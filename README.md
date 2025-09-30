# Projeto-Aplicado-Multiplataforma
A proposta do projeto é o desenvolvimento de uma plataforma digital
multiplataforma (web e mobile/PWA) voltada para microempreendedores, com o
objetivo de facilitar o controle financeiro do negócio.O sistema permitirá que o
usuário registre receitas e despesas, classifique por categorias, e acompanhe
relatórios automáticos de lucro líquido e margem de lucro para ajudar o
microempreendedor a tomar decisões mais assertivas na gestão de seus
recursos.A finalidade principal é fornecer uma ferramenta simples, acessível e
segura que apoie o microempreendedor no dia a dia, ajudando a organizar as
finanças, visualizar resultados de forma clara e planejar o crescimento de forma
sustentável.

Proposta: criar um sistema de gestão financeira prático, intuitivo e
multiplataforma.
Finalidade: auxiliar microempreendedores no controle de gastos, geração de
relatórios e melhoria da saúde financeira do negócio.

## 1. Requisitos Funcionais e Não-Funcionais
### REQUISITOS FUNCIONAIS (RF):
- RF-01 — Cadastro de usuário (conta com e-mail/senha, login Google, perfil com CNPJ e ramo de atividade)
- RF-02 — Gestão de despesas (inserir, editar, excluir, categorias, recorrência, comprovante opcional)
- RF-03 — Gestão de receitas (inserir, editar, excluir, categorias, observações)
- RF-04 — Relatórios e cálculos (lucro líquido, margem de lucro, relatórios mensais/trimestrais/anuais, exportar CSV/PDF, alertas automáticos)
- RF-05 — Painel administrativo (CRUD usuários, métricas, logs)
- RF-06 — Integrações (Google OAuth, CSV bancário, ERPs futuros)
- RF-07 — Auditoria (logs e histórico de versões)

### REQUISITOS NÃO-FUNCIONAIS (RNF):
- Segurança: autenticação JWT ou Firebase Auth, criptografia, TLS, proteção contra ataques comuns
- Performance: resposta <300ms, paginação e filtros
- Usabilidade: design responsivo, dashboards intuitivos
- Escalabilidade: banco na nuvem, escalonamento horizontal, backups
- Manutenibilidade: arquitetura em camadas, testes automatizados
- Conformidade: LGPD (consentimento e exclusão de dados)

## 2. Arquitetura Completa do Sistema
Frontend:
- React.js com Next.js (SSR/SSG) ou Vite (SPA)
- Mobile-first PWA; possível app React Native
- TailwindCSS, Chart.js/Recharts, React Query

### Backend:
- Opção A: Firebase (Auth, Firestore, Functions, Storage)
- Opção B: Node.js + NestJS, Express, MongoDB Atlas, JWT, Redis jobs

### Infraestrutura:
- Frontend em Vercel/Netlify
- Backend em Render/Railway/Cloud Run
- CI/CD com GitHub Actions
- Monitoramento: Sentry, Prometheus/Grafana

## 3. Modelagem do Banco de Dados (Diagrama ER simplificado)
Entidades:
- users: id (PK, UUID), email (único, not null), senha_hash (not null), nome (not null), cnpj (único, opcional), setor, created_at

- categories: id (PK, SERIAL), user_id (FK → users.id), name, type (ENUM: 'revenue', 'expense')

- expenses: id (PK, UUID), user_id (FK → users.id), category_id (FK → categories.id), amount, date, description, vendor, recurrence, - receipt_url

- revenues: id (PK, UUID), user_id (FK → users.id), category_id (FK → categories.id), amount, date, client, description

- reports: id (PK, UUID), user_id (FK → users.id), periodo, total_revenue, total_expense, net_profit, profit_margin

- audit_logs: id (PK, BIGSERIAL), user_id (FK → users.id), action_type, entity_id, entity_type, timestamp

# Relacionamentos:
- users 1:N categories

- users 1:N expenses

- users 1:N revenues

- users 1:N reports

- users 1:N audit_logs

- categories 1:N expenses

- categories 1:N revenues


## 4. Protótipos de Interface (descrição)
### Principais telas web/mobile:
1. Login/Registro
2. Dashboard: saldo mensal, gráfico receitas x despesas, alertas
3. Despesas: lista, filtros, CRUD
4. Receitas: lista, filtros, CRUD
5. Relatórios: seleção período, gráficos, exportar PDF/CSV
6. Configurações/Perfi
7. Admin: usuários, métricas, logs
UI: mobile-first, botões grandes, Tailwind, paleta limpa

## 5. Documentação das APIs 
### Endpoints principais: 
- POST /auth/register – Criar conta.
- POST /auth/login – Login e retorno de token JWT.
- GET /expenses – Listar despesas do usuário.
- POST /expenses – Cadastrar despesa.
- PUT /expenses/:id – Atualizar despesa.
- DELETE /expenses/:id – Excluir despesa.
- GET /reports/monthly – Retornar cálculo de lucros e gráficos.

## 6. Tecnologias e Ferramentas
Frontend: React, Next.js, Tailwind, Recharts
Backend: Firebase (MVP) ou Node.js + NestJS + MongoDB
Infra: Vercel, Render, MongoDB Atlas/Firestore, CI/CD com GitHub Actions
Dev: Postman, Swagger, Figma, Jest, Cypress

## 7. Estrutura de Testes e Validação
- Unitários: Jest/Vitest (cálculos, validações)
- Integração: Supertest (endpoints)
- E2E: Cypress/Playwright (fluxo completo)
- Performance: testes de carga em endpoints críticos
- Segurança: scans automáticos e pentest
- Validação: testes com usuários finais

## 8. Cronograma de Desenvolvimento (Etapa 2, 10 semanas)
- Semana 1: Infra (repos, CI/CD, DB, deploy inicial)
- Semana 2: Autenticação & Perfil
- Semana 3: CRUD Despesas/Receitas (backend)
- Semana 4: Frontend básico (dashboard, listas)
- Semana 5: Uploads/Storage
- Semana 6: Relatórios e cálculos
- Semana 7: Notificações & Alertas
- Semana 8: Testes & Feedback usuários
- Semana 9: Hardening & Documentação (Swagger)
- Semana 10: Release MVP e monitoramento
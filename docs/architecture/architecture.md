# Arquitetura Completa do Sistema
## Frontend:
- React.js com Next.js (SSR/SSG) ou Vite (SPA)
- Mobile-first PWA; possível app React Native
- TailwindCSS, Chart.js/Recharts, React Query

## Backend:
- Opção A: Firebase (Auth, Firestore, Functions, Storage)
- Opção B: Node.js + NestJS, Express, MongoDB Atlas, JWT, Redis jobs

## Infraestrutura:
- Frontend em Vercel/Netlify
- Backend em Render/Railway/Cloud Run
- CI/CD com GitHub Actions
- Monitoramento: Sentry, Prometheus/Grafana

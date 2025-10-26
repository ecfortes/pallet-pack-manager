# Pallet & Pack Manager

Aplicacao full stack que controla pallets e packs para a operacao da DERSA/ZIA. O projeto combina React + Vite no frontend, Express + PostgreSQL no backend e fluxos Node-RED para integracao de automacao.

## Visao Geral
- Interface web para listar, criar e revisar pallets, packs vinculados e packs orfaos.
- API REST em Node.js sem ORM em runtime (usa pg direto; Sequelize apenas para migracoes DDL).
- Banco PostgreSQL com extensao pg_trgm, triggers de updated_at e view de overview operacional.
- Fluxos Node-RED (arquivo JSON) para integrar PLCs e esteiras industriais.

## Estrutura de Diretorios
- `client/` React + Vite, componentes customizados e CSS puro.
- `server/` Express, rotas, controllers e utilitarios de banco; inclui migracoes Sequelize.
- `docker compose/` stack PostgreSQL local pronta para desenvolvimento.
- `node-red/` fluxo exportado (.json) e README do pacote.
- `TODO.md` backlog operacional (limpeza, automacoes, integracao IOT).

## Documentacao Completa
- `docs/README.md` indice geral.
- `docs/arquitetura.md` mapa de componentes e fluxos.
- `docs/backend.md` detalhes da API, variaveis de ambiente e logging.
- `docs/api.md` referencia de endpoints.
- `docs/database.md` tabelas, constraints, indexes e view.
- `docs/frontend.md` paginas, estado e estilo da SPA.
- `docs/operacional.md` setup, migracoes, deploy, rotinas.
- `docs/integracao-node-red.md` instrucao de importacao e manutencao do fluxo.

## Requisitos Basicos
- Node.js 20+
- npm 10+
- Docker + Docker Compose (para usar o banco local)
- PostgreSQL 16 (quando executar sem Docker)

## Comece Rapido
### Subir PostgreSQL
```bash
cd "docker compose"
docker compose up -d
```
Porta 35432, usuario `zegla`, senha `zg1982`, banco `zegla`.

### Backend
```bash
cd server
cp .env.example .env   # ajuste se necessario
npm install
npx sequelize-cli db:migrate
npm run dev            # http://localhost:4000
```

### Frontend
```bash
cd client
npm install
npm run dev            # http://localhost:5173
```

## Scripts Uteis
- `server npm run dev` inicia API em modo desenvolvimento.
- `server npm start` sobe API em modo producao.
- `server npx sequelize-cli db:migrate` aplica migracoes.
- `client npm run dev` inicia Vite com HMR.
- `client npm run build` gera artefatos estaticos.

## Variaveis Importantes
- `PGHOST`, `PGPORT`, `PGUSER`, `PGPASSWORD`, `PGDATABASE`, `PGSSLMODE`.
- `PORT` porta HTTP da API.
- `CLIENT_ORIGIN` lista separada por virgula de origens liberadas.
- `SQL_LOG`, `SQL_SLOW_MS`, `SQL_PARAMS` controlam logging SQL colorido.

## Proximos Passos
- Consulte `docs/` para guias completos de arquitetura, banco, API e operacao.
- Revise `TODO.md` para atividades pendentes de produto e infraestrutura.
- Registre qualquer alteracao relevante na documentacao antes de publicar.

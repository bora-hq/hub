# bora-hq/hub

Hub central do ecossistema **bora-hq** — ponto de entrada e descoberta dos projetos, bots, agentes e infraestrutura do time.

---

## 🎯 O que é o bora-hq?

O **bora-hq** é a organização que abriga o ecossistema de produtos, agentes e ferramentas do Antunes.  
Foco: **produtos reais**, **agentes autônomos** e **infra própria** — nada de teatro de assistente.

---

## 🗂️ Projetos do Ecossistema

> Só os repos públicos do `bora-hq` entram aqui. Repos internos/privados e projetos
> pessoais (`antunes-hq/`) não ficam listados numa página pública.

| Projeto | Repo | Descrição | Status |
|---------|------|-----------|--------|
| **hub** | `bora-hq/hub` | Este repo — porta de entrada e índice vivo do ecossistema | 🟢 Ativo |
| **aptdata** | `bora-hq/aptdata` | Framework Python extensível para pipelines de dados (SaaS principal) | 🔴 Pausado |
| **eval-fabrica** | `bora-hq/eval-fabrica` | Fábrica de avaliação de qualidade — grafo por org (DeepEval + LLM-as-judge) | 🟢 Ativo |
| **hermes-desktop** | `bora-hq/hermes-desktop` | Cliente desktop (web + Tauri) pro Hermes Agent | 🟡 Em desenvolvimento |

---

## 🤖 Bots em Produção — bora-hq

> **Esta seção é a FONTE CANÔNICA dos bots do ecossistema bora-hq. Edite aqui.**
> Bots pessoais/de terceiros (chat casual, favores pra família e amigos) não entram aqui — ficam documentados em `antunes-hq`.

| Bot | Plataforma | Modelo | Onde roda | Função |
|-----|------------|--------|-----------|--------|
| **Dona** | Web (FastAPI) | OpenRouter | VPS (Docker) | Agente introspectivo / Takeout Insights — **homologação pendente** |

---

## 🏗️ Infraestrutura

| Componente | Onde | Detalhes |
|------------|------|----------|
| **VPS (sandbox)** | Hostinger `srv1723096.hstgr.cloud` | acesso via chave SSH — Docker, systemd, Nginx, PostgreSQL |
| **Dona** | Container `dona-dona-1` | FastAPI + systemd, exposto via Nginx + SSL — **homologação pendente** |
| **OpenClaw Bots** | Containers individuais | Pairing via QR code, sessões persistidas |
| **Hermes Agent** | Local (Lucas) | Agente principal — `~/.hermes`, modelo DeepSeek via OpenRouter |
| **Claude Code** | Container (a montar) | Executor pesado — remote control, volume `.claude/` no host — **Dockerfile ainda não existe** |
| **OpenCode Zen** | API externa | Fallback de LLM (free tier) — configurado no Hermes |
| **GitHub** | Orgs `bora-hq` + `antunes-hq` | Source of truth, CI/CD, Issues, Projects |

> **TODO — container do Claude Code:** falta o Dockerfile (nenhum arquivo de build existe no repo ainda), definir imagem base, estratégia de auth (token/API key), mapeamento do volume `.claude/` do host e o mecanismo de remote control. Nada disso está documentado hoje porque ainda não foi construído.

---

## 📁 Estrutura do Workspace Local

```
~/lab/
├── bora-hq/            ← Projetos do ecossistema SaaS/bots
│   ├── hub/            ← ESTE REPO
│   ├── aptdata/        ← Framework de pipelines (pausado)
│   ├── flow/           ← Framework 5W2H (repo bora-hq/eco)
│   ├── dona/           ← Agente introspectivo (repo bora-hq/dona)
│   ├── eval-fabrica/   ← Fábrica de avaliação de qualidade
│   ├── fessora/        ← Plataforma multi-professor
│   ├── hermes-desktop/ ← Cliente desktop Hermes
│   ├── lab/            ← AI Labs (pausado)
│   ├── visu/           ← Lab de UI/UX
│   └── fabrica-lockin/ ← Orquestração distribuída (plano + tasks)
├── antunes-hq/         ← Projetos pessoais
│   ├── financas/       ← Dashboard financeiro (local-only)
│   ├── mavi/           ← Bot casamento (repo antunes-hq/mavi)
│   ├── painel/         ← Painel do Lucas (repo antunes-hq/dash)
│   ├── canais/         ← Conteúdo redes (repo antunes-hq/feed)
│   ├── bio/            ← Landing pessoal (repo antunes-hq/bio)
│   └── journal/        ← Diário e goals
├── archive/            ← Cemitério oficial (consulta only)
└── .hermes/            ← Plans, analysis, state
```

---

## 💡 Banco de Ideias

> **Decisão (26/07):** o hub **não é** o sistema de captura. É o **índice** que aponta pra onde as ideias vivem e como navegar nelas.

| O quê | Onde | Como acessar |
|-------|------|-------------|
| **Captura** (`!btw`) | Flow (`~/Documentos/bora-hq/flow/`) | Telegram: `!btw <texto>` |
| **Organização** (tags, links, grafo) | Flow + flow-viz | `flow nota tag\|link\|ideias` |
| **Visualização** | flow-viz (`:8000`) | `http://localhost:8000/ideias` (fase 2) |
| **Surfacing temporal** | Cron 9h | Telegram (automático) |

**Status:** MVP pessoal em construção (schema + CLI + cron).  
**Revisão virar produto:** 16/08/2026 — critérios: uso 5+ dias/semana, 1 insight via surfacing, alguém externo pediu.

> Spec completa: task `t_8a0011d5` (plano em `.hermes/plans/2026-07-26-app-banco-ideias.md`)

---

## 🚀 Começando

```bash
# Clonar este hub
gh repo clone bora-hq/hub

# Clonar todo o ecossistema (projetos ativos)
gh repo clone bora-hq/aptdata
gh repo clone bora-hq/eco
gh repo clone bora-hq/visu
gh repo clone bora-hq/fessora
# ...etc
```

---

## 📋 Governança

- **Source of truth**: GitHub (`bora-hq/` + `antunes-hq/`)
- **Issues/Projects**: GitHub Projects (kanban multi-board via `hermes kanban`)
- **Agente principal**: Hermes Agent (`~/.hermes`) — modelo DeepSeek via OpenRouter
- **Fallback LLM**: OpenCode Zen (free tier) — configurado no Hermes
- **Executor pesado**: Claude Code em container (remote control) — a montar
- **Cron jobs**: `~/.hermes/cron/jobs.json` (morning digest, cost alert, garden cleanup, bot fleet monitor)
- **Estado do dia**: `~/.hermes/scripts/hermes_state.py` → `~/lab/antunes-hq/journal/goals.md`
- **Orquestração**: Fábrica Lockin Multiplataforma — plano em `.hermes/plans/2026-07-30_200000-fabrica-lockin-multiplataforma.md`

---

## 📜 Licença

MIT — uso livre, contribuição bem-vinda.  
Projetos individuais podem ter licenças próprias (ver cada repo).

---

## 🤝 Contribuindo

1. Abra uma **Issue** no repo do projeto relevante
2. Abra **PR** com commits pequenos e descritivos
3. CI passa → merge (branch protection na `main`)
4. Deploy via CI/CD do respectivo projeto

---

## 📍 Onde encontrar o Lucas

- **Telegram**: @my_hermez_dev_bot (Hermes)
- **GitHub**: @antunes-hq (pessoal) / @bora-hq (org)
- **VPS**: acesso via chave SSH (contato: Lucas)
- **Timezone**: America/Sao_Paulo (BRT)
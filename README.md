# bora-hq/hub

Hub central do ecossistema **bora-hq** — ponto de entrada e descoberta dos projetos, bots, agentes e infraestrutura do time.

---

## 🎯 O que é o bora-hq?

O **bora-hq** é a organização que abriga o ecossistema de produtos, agentes e ferramentas do Lucas Antunes.  
Foco: **produtos reais**, **agentes autônomos** e **infra própria** — nada de teatro de assistente.

---

## 🗂️ Projetos do Ecossistema

| Projeto | Repo | Descrição | Status |
|---------|------|-----------|--------|
| **hub** | `bora-hq/hub` | Este repo — porta de entrada e índice vivo do ecossistema | 🟢 Ativo |
| **aptdata** | `bora-hq/aptdata` | Plataforma de dados para contabilidade (SaaS principal) | 🟡 Em estruturação |
| **eco** | `bora-hq/eco` | Dona — agente introspectivo (Takeout Insights) | 🟢 Produção (VPS) |
| **lab** | `bora-hq/lab` | Monorepo de kits e experimentos de IA (AI Labs) | 🟡 Pausado |
| **visu** | `bora-hq/visu` | Lab de UI/UX, componentes e design system | 🟡 Exploração |
| **fessora** | `bora-hq/fessora` | Sistema de aulas de inglês (Mariana) | 🟡 Em desenvolvimento |
| **mavi** | `antunes-hq/mavi` | Bot do casamento Mari & Vini (OpenClaw) | 🟢 Produção (Local) |
| **dash** | `antunes-hq/dash` | Painel pessoal do Lucas | 🟡 Em desenvolvimento |
| **feed** | `antunes-hq/feed` | Pipeline de conteúdo redes sociais | 🟡 Em desenvolvimento |
| **bio** | `antunes-hq/bio` | Landing pessoal pública | 🟡 Em desenvolvimento |

> Projetos pessoais (finanças, painel, conteúdo) ficam em `antunes-hq/`.  
> Projetos do ecossistema SaaS/bots ficam em `bora-hq/`.

---

## 🤖 Bots em Produção

> **Esta seção é a FONTE CANÔNICA dos bots vivos do ecossistema. Edite aqui.**

| Bot | Plataforma | Modelo | Onde roda | Função |
|-----|------------|--------|-----------|--------|
| **Dona** | Web (FastAPI) | OpenRouter | VPS (Docker) | Agente introspectivo / Takeout Insights |
| **Serginho** | Telegram | deepseek-chat | VPS (OpenClaw) | Chat casual / Audi |
| **Formiga** | Telegram | deepseek-chat | VPS (OpenClaw) | Irmã / Facilitadora |
| **Casamento M&V** | Telegram | trinity-large-thinking | Local (Docker) | Organização do casamento |

---

## 🏗️ Infraestrutura

| Componente | Onde | Detalhes |
|------------|------|----------|
| **VPS** | Hostinger | `root@2.25.158.212` — Docker, systemd, Nginx, PostgreSQL |
| **Dona** | Container `dona-dona-1` | FastAPI + systemd, exposto via Nginx + SSL |
| **OpenClaw Bots** | Containers individuais | Pairing via QR code, sessões persistidas |
| **Hermes Agent** | Local (Lucas) | Agente principal — `~/.hermes`, modelo DeepSeek via OpenRouter |
| **GitHub** | Orgs `bora-hq` + `antunes-hq` | Source of truth, CI/CD, Issues, Projects |

---

## 📁 Estrutura do Workspace Local

```
~/Documentos/
├── ecossistema/
│   ├── hub/              ← ESTE REPO
│   ├── mindflow/         ← App criativo principal
│   ├── smart-data/       ← aptdata (bora-hq/aptdata)
│   ├── ai-labs/          ← lab (bora-hq/lab) — PAUSADO
│   ├── visu/             ← visu (bora-hq/visu)
│   ├── takeout-insights/ ← eco (bora-hq/eco)
│   └── estrategia-saas/  ← Fonte da verdade estratégia APT Data
├── pessoal/
│   ├── financas/         ← Dashboard financeiro (local-only)
│   ├── mariana-ingles/   ← fessora (bora-hq/fessora)
│   ├── casamento-mari-vini/ ← mavi (antunes-hq/mavi)
│   ├── painel/           ← dash (antunes-hq/dash)
│   ├── canais/           ← feed (antunes-hq/feed)
│   └── bio/              ← bio (antunes-hq/bio)
├── archive/              ← Cemitério oficial (consulta only)
└── scripts/              ← Scripts de infra do workspace
```

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
- **Cron jobs**: `~/.hermes/cron/jobs.json` (morning digest, cost alert, garden cleanup, bot fleet monitor)
- **Estado do dia**: `~/.hermes/scripts/hermes_state.py` → `~/Documentos/pessoal/journal/goals.md`

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
- **VPS**: `ssh root@2.25.158.212`
- **Timezone**: America/Sao_Paulo (BRT)
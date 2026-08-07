# bora-hq/hub

Índice do **bora-hq** — ponto de entrada e descoberta dos projetos open source da organização. Sem teatro de assistente.

> O hub só lista repositórios **públicos** do bora-hq.

---

## 🎯 O que é o bora-hq?

O **bora-hq** é a organização que guarda o repositório aberto de **vibe code** do Antunes.
Foco: **projetos reais**, **open source**, **sem overclaim** — nada de teatro de assistente.

> **Invariante pública**: só repositórios **PÚBLICOS** do `bora-hq` aparecem aqui.
> Repos privados e projetos pessoais (`antunes-hq/`) nunca são listados numa página pública.

---

## 🗂️ Projetos do Bora (públicos)

| Projeto | Repo | Descrição | Status |
|---------|------|-----------|--------|
| **hub** | `bora-hq/hub` | Este repo — índice vivo do ecossistema | 🟢 Ativo |
| **aptdata** | `bora-hq/aptdata` | Framework Python extensível para pipelines de dados | 🔴 Pausado |
| **eval-fabrica** | `bora-hq/eval-fabrica` | Fábrica de avaliação de qualidade (DeepEval + LLM-as-judge) | 🟢 Ativo |
| **hermes-desktop** | `bora-hq/hermes-desktop` | Cliente desktop (web + Tauri) pro Hermes Agent | 🟡 Em desenvolvimento |

---

## 🏗️ Infraestrutura

| Componente | Onde | Detalhes |
|------------|------|----------|
| **GitHub Pages** | `bora-hq/hub` | Deploy direto da `master` — sem CI/CD próprio |
| **GitHub** | Orgs `bora-hq` + `antunes-hq` | Source of truth, Issues, Projects |

> Detalhes de hosting/containers ficam fora desta página pública.

---

## 🚀 Começando

```bash
# Clonar este hub
gh repo clone bora-hq/hub

# Demais repos públicos
gh repo clone bora-hq/aptdata
gh repo clone bora-hq/eval-fabrica
gh repo clone bora-hq/hermes-desktop
```

---

## 📋 Governança

- **Source of truth**: GitHub (`bora-hq/`)
- **Issues/Projects**: GitHub Projects
- **Licença**: MIT — uso livre, contribuição bem-vinda

---

## 🤝 Contribuindo

1. Abra uma **Issue** no repo do projeto relevante
2. Abra **PR** com commits pequenos e descritivos
3. CI passa → merge
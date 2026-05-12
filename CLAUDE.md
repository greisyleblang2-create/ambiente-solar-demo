# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Context

This is a **freelance automation project** for **Jhonatan Solartechnik / Ambiente Solar** (Frankfurt-area solar installer). Built by Greisy Leblang as a learning project. The goal is a fully automated business pipeline: leads from 5 sources → auto-generated quotes/invoices → Jhonatan reviews and approves → sent to customer as PDF.

**Planned automation stack:** n8n Cloud (`gleblang.app.n8n.cloud`) + Supabase (PostgreSQL) + Brevo (email) + Telegram Bot API. Two scenarios exist: Szenario A (~25€/month, cloud services) and Szenario B (~50€/month, self-hosted VPS). Currently blocked on Jhonatan answering open questions (budget choice, pricing list, SolarCan access method).

## Architecture

No build system. All deliverables are standalone static HTML files — open directly in a browser. No npm, no framework, no compilation step.

| File | Purpose |
|------|---------|
| `index.html` | Production demo website v2 (1,837 lines; this is the canonical version) |
| `demo-website-v2.html` | Identical copy of `index.html` kept as backup |
| `dashboard.html` | CRM dashboard prototype — Tailwind CSS via CDN, pure JS |
| `Budget_Szenarien_Jhonatan.html` | Printable budget comparison document |
| `Angebotsvorlage_Jhonatan_Solartechnik.md` | Quote template (Markdown) |
| `Rechnungsvorlage_Jhonatan_Solartechnik.md` | Invoice template (Markdown) |
| `FAQ_Jhonatan_Solartechnik.md` | Customer FAQ document |
| `PROJEKT_STATUS.md` | Full project status, open questions, and phase plan |
| `Automatisierung_Erklaerung_Uebersicht.md` | Plain-language explanation of the automation system |

`Backup Webseite Hauptverzeichnis/` and `Hauptverzeichnis/` contain the old WordPress site backup — excluded from git, do not modify.

## Viewing Files

```bash
open index.html          # Demo website
open dashboard.html      # CRM dashboard
open Budget_Szenarien_Jhonatan.html   # Budget doc (use browser Print → PDF)
```

## Design System

**Website** (`index.html`):
- `--amarillo: #F5A623` (orange/yellow accent)
- `--turquesa: #1B8CA6` (primary brand color)
- `--azul-dark: #0D3B4F` (navbar/dark backgrounds)
- Font: Segoe UI / Arial

**Dashboard** (`dashboard.html`):
- `--slate: #2d3f50` (header/primary)
- `--sage: #5a8a6e` (green accent)
- Tailwind CSS via CDN
- Status badges: `badge-neu`, `badge-angebot`, `badge-auftrag`, `badge-rechnung`, `badge-bezahlt`

## Automation Workflow (not yet implemented)

```
Anfrage (Website/WhatsApp/Telegram/SolarCan)
  → Supabase DB → n8n generates PDF → Jhonatan reviews in Dashboard → Email via Brevo
```

Website contact forms already have `fetch()` calls stubbed to point to n8n webhooks. The two old demo workflows in n8n will be replaced when implementation begins.

## Language

All user-facing content, comments, and documentation are in **German**. CSS variable names may use Spanish (legacy from initial design). Commit messages and code can be in German or English.

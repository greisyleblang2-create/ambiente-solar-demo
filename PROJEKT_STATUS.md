# 📋 PROJEKT STATUS — Jhonatan Solartechnik / Ambiente Solar

> **Letzte Aktualisierung:** 03.05.2026  
> **Letzte Arbeitssitzung:** 29.04.2026  
> **Projektordner:** `/Users/greisyleblang/Antigravity/Jhonatan Projekt/`

---

## 🎯 Projektziel

Aufbau einer **vollautomatisierten Geschäftsinfrastruktur** für Jhonatan Solartechnik (Ambiente Solar):

- **Leads** aus 5 Quellen automatisch in eine zentrale Datenbank sammeln
- **Angebote, Auftragsbestätigungen (AB) und Rechnungen** automatisch generieren
- Jhonatan prüft, bearbeitet und gibt alles über ein **Dashboard/CRM** frei
- Dokumente werden per **E-Mail als PDF** an Kunden versendet

---

## ✅ Erledigte Aufgaben

### Webseite (Demo)
- [x] Analyse der bestehenden Webseite `https://www.ambiente-solar.de` (war offline – 503 Error)
- [x] Demo-Webseite v1 erstellt → `demo-website.html`
- [x] Demo-Webseite v2 erstellt → `demo-website-v2.html` / `index.html` (1.837 Zeilen)
  - Navbar mit Logo, Hero-Section, CTA-Buttons
  - Statistiken-Leiste, Über uns, Leistungen (3-Spalten Grid)
  - Projekte-Galerie, Preistabelle (4 Pakete)
  - Testimonials, Kontaktformular, WhatsApp-Float-Button
  - Solar-Konzept Tabs

### Dokument-Vorlagen
- [x] Angebotsvorlage erstellt → `Angebotsvorlage_Jhonatan_Solartechnik.md`
- [x] Rechnungsvorlage erstellt → `Rechnungsvorlage_Jhonatan_Solartechnik.md`
- [x] FAQ-Dokument erstellt → `FAQ_Jhonatan_Solartechnik.md`

### Dashboard (Prototyp)
- [x] Dashboard-Prototyp erstellt → `dashboard.html`
  - Enthält bereits n8n Cloud Referenz (`gleblang.app.n8n.cloud`)
  - 2 Demo-Workflows waren eingebaut (nur zum Testen, **werden ersetzt**)

### Automatisierungs-Planung
- [x] **Architektur-Plan** erstellt (vollständiger Workflow: Anfrage → Angebot → AB → Rechnung)
- [x] **Budget-Szenarien** HTML-Dokument erstellt → `Budget_Szenarien_Jhonatan.html`
  - Mit Ambiente Solar Logo, professionell gestaltet, druckfertig als PDF
  - **Szenario A — Smart** (~25 €/Monat): n8n Cloud + Supabase Free + Brevo Free
  - **Szenario B — Professionell** (~50 €/Monat): Eigener VPS + offizielle APIs
- [x] SolarCan Installateure als Plattform identifiziert
- [x] 3 Automatisierungsmöglichkeiten für SolarCan analysiert (E-Mail-Parsing, Web-Scraping, Browser-Automation)

---

## 📁 Vorhandene Dateien

```
Jhonatan Projekt/
├── index.html                                    # Demo-Webseite v2 (aktuelle Version)
├── demo-website.html                             # Demo-Webseite v1
├── demo-website-v2.html                          # Demo-Webseite v2 (Kopie)
├── dashboard.html                                # Dashboard-Prototyp
├── Budget_Szenarien_Jhonatan.html                # Budget-Dokument (zum Drucken/PDF)
├── Angebotsvorlage_Jhonatan_Solartechnik.md      # Angebotsvorlage
├── Rechnungsvorlage_Jhonatan_Solartechnik.md     # Rechnungsvorlage
├── FAQ_Jhonatan_Solartechnik.md                  # FAQ-Dokument
├── README.md                                     # Projekt-README
├── drone-video.mp4                               # Drohnen-Video (5 MB)
├── fotos/                                        # Fotos für die Webseite
│   ├── fassade-cropped.jpeg
│   ├── PHOTO-2026-04-26-15-16-32.jpeg
│   └── Instagram.html + Instagram_files/
├── Hauptverzeichnis/                             # WordPress Backup-Dateien
│   ├── wp-content/
│   └── wp-includes/
└── Backup Webseite Hauptverzeichnis/             # Weiteres Backup
```

---

## 🔄 Kompletter Automatisierungs-Workflow

```
📥 Anfrage rein (Webseite / WhatsApp / Telegram / SolarCan)
    ↓
🗄️ Zentrale Datenbank (alle Kundendaten gesammelt)
    ↓
📄 Angebot wird AUTOMATISCH erstellt
    ↓
👀 J. prüft & bearbeitet (Dashboard / E-Mail)
    ↓
📧 Angebot → an Kunden per Mail (als PDF)
    ↓
✅ Kunde nimmt an
    ↓
📋 Auftragsbestätigung wird AUTOMATISCH erstellt
    ↓
👀 J. prüft & gibt frei
    ↓
📧 AB → an Kunden per Mail
    ↓
🔧 J. erledigt den Auftrag
    ↓
🧾 Rechnung wird AUTOMATISCH erstellt
    ↓
👀 J. kontrolliert & gibt frei
    ↓
📧 Rechnung → an Kunden per Mail
```

> **Wichtig:** Jhonatan hat IMMER die volle Kontrolle. Nichts wird versendet ohne seine Freigabe.

---

## 📥 5 Datenquellen

| # | Quelle | Status | Anbindung |
|---|--------|--------|-----------|
| 1 | **Webseite — Angebotsformular** | ✅ Formular existiert | `fetch()` → n8n Webhook |
| 2 | **Webseite — Solar-Konzept Formular** | ✅ Formular existiert | `fetch()` → n8n Webhook |
| 3 | **WhatsApp** | ⏳ Noch nicht angebunden | WWebJS (kostenlos) oder WhatsApp Business API |
| 4 | **Telegram** | ⏳ Noch nicht angebunden | Telegram Bot API (kostenlos!) |
| 5 | **SolarCan Installateure** | ❓ Klärung nötig | E-Mail-Parsing / Web-Scraping / API |

---

## ⚠️ Offene Fragen an Jhonatan

**Diese Fragen müssen beantwortet werden, bevor wir mit der Umsetzung starten:**

1. **💰 Budget-Entscheidung** — Szenario A (~25€/Monat) oder Szenario B (~50€/Monat)?  
   *(Budget-Dokument liegt als `Budget_Szenarien_Jhonatan.html` bereit → im Browser öffnen → "Als PDF drucken")*

2. **📋 Preisliste** — Ohne Standardpreise kann das Angebot nicht automatisch berechnet werden.  
   Wir müssen gemeinsam eine Preisliste erstellen (Module, Installation, Wartung, etc.)

3. **🔧 SolarCan Portal** — Wie bekommt J. die Aufträge?  
   - Per E-Mail-Benachrichtigung? → Einfachste Lösung (E-Mail-Parsing)
   - Nur im Web-Portal? → Dann Web-Scraping nötig
   - Per App? → Andere Strategie

4. **📧 E-Mail-Adresse** — Hat J. bereits `info@ambiente-solar.de` oder ähnlich?

5. **🏦 Bankdaten** — Für die automatische Rechnung: IBAN/BIC (wird sicher gespeichert)

---

## 📅 Phasenplan — Nächste Schritte

### 🔴 Blockiert (wartet auf J.'s Antworten)
- [ ] Szenario-Entscheidung von Jhonatan einholen
- [ ] Preisliste mit Jhonatan erstellen
- [ ] SolarCan-Portal Zugangsart klären

### Phase 1: Grundgerüst (Woche 1–2)
- [ ] Supabase-Datenbank einrichten (Tabellen: Kunden, Aufträge, Dokumente)
- [ ] n8n Workflows neu aufsetzen (alte Demo-Workflows ersetzen)
- [ ] Webseite-Formulare an n8n-Webhook anbinden
- [ ] Telegram Bot erstellen und anbinden

### Phase 2: Dokument-Automatisierung (Woche 3–4)
- [ ] Preisliste finalisieren
- [ ] Angebots-Template (HTML → PDF) bauen
- [ ] AB-Template (HTML → PDF) bauen
- [ ] Rechnungs-Template (HTML → PDF) bauen
- [ ] Auto-Generierung in n8n einrichten

### Phase 3: Dashboard/CRM (Woche 4–5)
- [ ] Dashboard mit Freigabe-Funktionen erweitern
- [ ] E-Mail-Benachrichtigungen an J. einrichten
- [ ] PDF-Vorschau im Dashboard
- [ ] "Freigeben" & "Bearbeiten" Buttons

### Phase 4: Messaging-Kanäle (Woche 5–6)
- [ ] WhatsApp-Anbindung (WWebJS oder Business API)
- [ ] Telegram-Bot Kundeninteraktion erweitern
- [ ] Auto-Antworten konfigurieren

### Phase 5: SolarCan + Go-Live (Woche 6–8)
- [ ] SolarCan-Portal Automation
- [ ] Zahlungsverfolgung einrichten
- [ ] Reporting / Statistiken
- [ ] Kompletter End-to-End Test
- [ ] Go-Live 🚀

---

## 🛠️ Empfohlener Technologie-Stack (Szenario A — Smart)

| Komponente | Lösung | Kosten |
|------------|--------|--------|
| **Webseite** | GitHub Pages (vorhanden) | 0 € |
| **Automatisierung** | n8n Cloud (Starter Plan) | ~20 €/Monat |
| **Datenbank** | Supabase Free Tier (PostgreSQL) | 0 € |
| **E-Mail** | Brevo (Sendinblue) Free Tier | 0 € |
| **PDF** | n8n + HTML Template | 0 € |
| **WhatsApp** | WWebJS (kostenlos) | 0 € |
| **Telegram** | Telegram Bot API | 0 € |
| **Dashboard** | Vercel/Netlify (Free) | 0 € |
| **GESAMT** | | **~20–25 €/Monat** |

---

## 💡 Kontext / Hintergrund

- **Greisy** macht das Projekt **kostenlos** als Lernprojekt im Rahmen ihrer Weiterbildung als **KI-Implementation Architect**
- Jhonatan arbeitet als **Subunternehmer** für Solarinstallationen
- Die alte Webseite `ambiente-solar.de` war zum Zeitpunkt der Analyse **offline** (503 Error)
- Es existieren **2 alte n8n Demo-Workflows** auf `gleblang.app.n8n.cloud` — diese werden im neuen Konzept komplett ersetzt
- Es gibt ein **WordPress-Backup** im Ordner `Hauptverzeichnis/` (wp-content, wp-includes)

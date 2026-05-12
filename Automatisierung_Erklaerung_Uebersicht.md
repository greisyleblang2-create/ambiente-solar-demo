# 🧠 Automatisierung für Ambiente Solar — Wie funktioniert das alles?

> **Ein Erklärdokument für Greisy & Jhonatan**  
> Stand: Mai 2026

---

## 📌 Worum geht es hier?

Du bietest Jhonatan an, sein Geschäft zu **automatisieren** — das heißt:
- Kundenanfragen werden **automatisch gesammelt** (aus Webseite, WhatsApp, Telegram, SolarCan)
- **Angebote, Auftragsbestätigungen und Rechnungen** werden automatisch erstellt
- Jhonatan muss nur noch **prüfen und freigeben** — der Rest passiert automatisch

**Aber:** Woher kommt diese "Magie"? Was läuft im Hintergrund? Was kostet es? Wer wartet es?

Hier ist die komplette Erklärung. 👇

---

## 🏗️ Teil 1: Die Bausteine — Was braucht man überhaupt?

Stell dir das System vor wie ein **digitales Büro mit 6 Abteilungen**:

```
┌─────────────────────────────────────────────────────────────┐
│                    JHONATANS DIGITALES BÜRO                  │
│                                                             │
│  🌐 WEBSEITE        → Der Showroom (Kunden sehen Angebote) │
│  🗄️ DATENBANK       → Der Aktenschrank (alle Kundendaten)  │
│  ⚙️ AUTOMATISIERUNG  → Die Sekretärin (verbindet alles)    │
│  📧 E-MAIL-DIENST   → Die Post (sendet Dokumente raus)     │
│  📄 PDF-GENERATOR    → Der Drucker (macht hübsche PDFs)    │
│  📊 DASHBOARD        → Der Schreibtisch (J. sieht alles)   │
└─────────────────────────────────────────────────────────────┘
```

Jeder dieser Bausteine ist ein **Online-Dienst** (eine Webseite/App im Internet), der 24/7 läuft. Jhonatan muss **nichts installieren** — alles läuft in der Cloud.

---

## ⚙️ Teil 2: Wie funktioniert die Automatisierung?

### Was ist n8n? (Das Herzstück)

**n8n** ist eine **Automatisierungs-Plattform** — wie ein intelligenter Assistent, der verschiedene Dienste miteinander verbindet.

> **Beispiel aus dem echten Leben:**  
> Stell dir vor, du hast eine Sekretärin, die folgendes tut:
> 1. Sie nimmt den Anruf entgegen (= Kundenanfrage kommt rein)
> 2. Sie schreibt die Daten in eine Akte (= speichert in Datenbank)
> 3. Sie erstellt ein Angebot basierend auf der Preisliste (= PDF generieren)
> 4. Sie legt es Jhonatan auf den Schreibtisch (= E-Mail / Dashboard)
> 5. Jhonatan sagt "OK, rausschicken" (= Freigabe)
> 6. Sie schickt es per Post an den Kunden (= E-Mail mit PDF)
>
> **n8n ist diese digitale Sekretärin.** Sie arbeitet 24/7, macht keine Fehler, und kostet ~20€/Monat.

### Wie sieht das technisch aus?

```
Ein "Workflow" in n8n sieht so aus:

 ┌─────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐
 │ TRIGGER  │───→│ DATEN    │───→│ ANGEBOT  │───→│ E-MAIL   │───→│ WARTEN   │
 │ Anfrage  │    │ in DB    │    │ als PDF  │    │ an J.    │    │ auf      │
 │ kommt    │    │ speichern│    │ erstellen│    │ senden   │    │ Freigabe │
 └─────────┘    └──────────┘    └──────────┘    └──────────┘    └──────────┘
                                                                      │
                                                                      ▼
                                                               ┌──────────┐
                                                               │ AN KUNDE │
                                                               │ senden   │
                                                               └──────────┘
```

Das Ganze wird in n8n **visuell gebaut** — man zieht Kästen (Nodes) zusammen, wie Legosteine. **Kein Programmieren nötig** für die Grundfunktionen.

---

## 💰 Teil 3: Die 2 Szenarien im Detail erklärt

### Szenario A — "Smart Start" (~20–30 €/Monat)

**Philosophie:** Nutze so viele **kostenlose Dienste** wie möglich, bezahle nur für das Nötigste.

| Was? | Dienst | Erklärt | Kosten |
|------|--------|---------|--------|
| **Webseite** | GitHub Pages | Kostenloses Hosting von GitHub. Die Webseite liegt dort und ist 24/7 erreichbar. | 0 € |
| **Automatisierung** | n8n Cloud (Starter) | n8n betreibt den Server für dich. Du loggst dich ein, baust Workflows, fertig. | ~20 €/M. |
| **Datenbank** | Supabase Free | Kostenlose PostgreSQL-Datenbank mit 500MB Speicher. Reicht für ~10.000+ Kunden. | 0 € |
| **E-Mail** | Brevo Free | Bis zu 300 E-Mails pro Tag kostenlos. Mehr als genug für den Start. | 0 € |
| **PDF** | In n8n integriert | n8n nimmt ein HTML-Template und macht daraus ein PDF. Kein extra Dienst nötig. | 0 € |
| **WhatsApp** | WWebJS | Open-Source Bibliothek, die WhatsApp Web automatisiert. Kostenlos, aber inoffiziell. | 0 € |
| **Telegram** | Bot API | Telegram bietet eine kostenlose Bot-Schnittstelle. Unbegrenzt, für immer kostenlos. | 0 € |
| **Dashboard** | Vercel/Netlify | Kostenlose Hosting-Plattformen für die Dashboard-Webseite. | 0 € |
| **Domain-E-Mail** | Optional | z.B. info@ambiente-solar.de statt Gmail | ~5 €/M. |

**Was Jhonatan sieht:**
- Er loggt sich im Dashboard ein → sieht alle Anfragen
- Klickt "Angebot ansehen" → sieht die PDF-Vorschau
- Klickt "Freigeben" → Angebot wird an den Kunden gesendet
- **Das war's.** Der Rest läuft automatisch.

**Wer wartet das?**
- n8n Cloud wird von n8n selbst gewartet (Updates, Server, Sicherheit)
- Supabase wird von Supabase gewartet
- Du (Greisy) müsstest nur bei Problemen eingreifen oder neue Workflows hinzufügen
- **Wartungsaufwand: ~1-2 Stunden pro Monat** (wenn alles läuft)

---

### Szenario B — "Professionell & Unabhängig" (~40–55 €/Monat)

**Philosophie:** Alles auf einem **eigenen Server** — volle Kontrolle, keine Abhängigkeit von kostenlosen Tiers.

| Was? | Dienst | Erklärt | Kosten |
|------|--------|---------|--------|
| **Eigener Server** | Hetzner VPS (CX22) | Ein virtueller Server in Deutschland. Darauf läuft ALLES — Webseite, n8n, Datenbank. | ~5 €/M. |
| **Automatisierung** | n8n Self-Hosted | Gleiche Software wie oben, aber du installierst sie selbst auf dem Server. Unbegrenzte Workflows. | 0 € (auf VPS) |
| **Datenbank** | PostgreSQL | Direkt auf dem Server installiert. Kein Speicherlimit. | 0 € (auf VPS) |
| **E-Mail** | Brevo Starter | 20.000 E-Mails pro Monat. Professioneller Absender. | ~19 €/M. |
| **WhatsApp** | 360dialog API | Offizielle WhatsApp Business API. Stabil, professionell. | ~15 €/M. |
| **Telegram** | Bot API | Gleich wie Szenario A — kostenlos. | 0 € |
| **Dashboard** | Auf VPS | Läuft auf dem eigenen Server, kein Extra-Dienst. | 0 € (auf VPS) |
| **Backups** | Automatisch | Tägliche Sicherung der Datenbank. | 0 € (auf VPS) |
| **Domain-E-Mail** | info@ambiente-solar.de | Professionelle E-Mail-Adresse. | ~5 €/M. |

**Was ist der Unterschied für Jhonatan?**
- Er merkt **keinen Unterschied** in der Bedienung
- Hinter den Kulissen ist alles stabiler und professioneller
- WhatsApp funktioniert garantiert (offizielle API statt Hack)

**Wer wartet das?**
- **Du (Greisy)** oder jemand mit technischem Wissen müsste:
  - Server-Updates einspielen (~1x pro Monat, 15 Min.)
  - Backups überprüfen
  - Bei Problemen den Server neustarten
- **Wartungsaufwand: ~3-4 Stunden pro Monat**

---

## 🔧 Teil 4: Verwaltung & Wartung — Wer macht was?

### Täglicher Betrieb (Jhonatans Aufgaben)

| Aufgabe | Häufigkeit | Aufwand |
|---------|------------|---------|
| Neue Anfragen im Dashboard ansehen | Täglich | 5 Min. |
| Angebote prüfen & freigeben | Pro Anfrage | 2-3 Min. |
| AB prüfen & freigeben | Pro Auftrag | 1-2 Min. |
| Rechnung prüfen & freigeben | Pro Auftrag | 1-2 Min. |

> **Jhonatan braucht KEIN technisches Wissen.** Er klickt nur Buttons: "Ansehen", "Bearbeiten", "Freigeben", "Senden".

### Technische Wartung (Greisys Aufgaben)

| Aufgabe | Häufigkeit | Szenario A | Szenario B |
|---------|------------|------------|------------|
| **Workflows anpassen** (z.B. neue Preise) | Bei Bedarf | In n8n Cloud | In n8n auf VPS |
| **Fehler beheben** (falls ein Workflow stoppt) | Selten | n8n zeigt Fehlermeldungen | Gleich + Server-Logs |
| **Server-Updates** | Monatlich | ❌ Nicht nötig (Cloud) | ✅ Manuell (~15 Min.) |
| **Backups prüfen** | Wöchentlich | ❌ Automatisch (Supabase) | ✅ Prüfen (~5 Min.) |
| **Neue Features hinzufügen** | Bei Bedarf | Neue Workflows bauen | Gleich |
| **WhatsApp-Verbindung prüfen** | Wöchentlich | ✅ WWebJS kann brechen | ❌ Nicht nötig (API stabil) |

### Was passiert wenn etwas kaputt geht?

```
Problem: Workflow stoppt
    → n8n sendet automatisch eine Fehler-E-Mail an Greisy
    → Greisy loggt sich ein und behebt den Fehler
    → Meistens: Node neustarten oder Verbindung erneuern

Problem: Datenbank ist voll (nur Szenario A)
    → Supabase Free hat 500MB Limit
    → Lösung: Alte Daten archivieren oder auf Supabase Pro upgraden (~25€/M.)
    → Bei ~50 Kunden/Monat: reicht für ~5+ Jahre

Problem: Server ist down (nur Szenario B)
    → Hetzner hat 99.9% Uptime
    → Falls doch: Server neustarten (1 Klick im Hetzner Panel)
    → Typisch: <1 Stunde Ausfall pro Jahr

Problem: WhatsApp-Verbindung bricht ab (nur Szenario A)
    → WWebJS muss neu verbunden werden (QR-Code scannen)
    → Passiert alle paar Wochen
    → Bei Szenario B: nicht relevant (offizielle API)
```

---

## 📊 Teil 5: Kosten-Zusammenfassung — Was Jhonatan wissen muss

### Einmalige Kosten (Setup)

| Posten | Kosten |
|--------|--------|
| Entwicklung & Setup | **0 €** (Greisy macht es kostenlos) |
| Domain (falls noch nicht vorhanden) | ~10-15 € / Jahr |
| SSL-Zertifikat | 0 € (automatisch bei allen Plattformen) |

### Laufende monatliche Kosten

| | Szenario A (Smart) | Szenario B (Profi) |
|---|---|---|
| **Automatisierung** | ~20 € (n8n Cloud) | 0 € (auf eigenem Server) |
| **Server** | 0 € (Cloud-Dienste) | ~5 € (Hetzner VPS) |
| **E-Mail** | 0 € (Brevo Free) | ~19 € (Brevo Starter) |
| **WhatsApp** | 0 € (WWebJS, inoffiziell) | ~15 € (offizielle API) |
| **Datenbank** | 0 € (Supabase Free) | 0 € (auf Server) |
| **Domain-E-Mail** | ~5 € (optional) | ~5 € |
| **Telegram** | 0 € | 0 € |
| **Dashboard** | 0 € | 0 € |
| | | |
| **GESAMT** | **~20–30 €/Monat** | **~40–55 €/Monat** |
| **Pro Jahr** | **~240–360 €/Jahr** | **~480–660 €/Jahr** |

### Was bekommt Jhonatan dafür?

> Ohne Automatisierung würde Jhonatan oder eine Bürokraft folgendes manuell machen:
>
> - Kundenanfragen aus 5 verschiedenen Quellen abtippen → **~30 Min./Tag**
> - Angebote in Word erstellen, als PDF speichern, per Mail senden → **~20 Min./Angebot**
> - AB erstellen und versenden → **~15 Min./Auftrag**
> - Rechnung erstellen und versenden → **~15 Min./Auftrag**
>
> **Bei 20 Anfragen/Monat = ~15-20 Stunden manuelle Arbeit gespart**
>
> 💡 Eine Bürokraft (Minijob) würde **~600-800 €/Monat** kosten.  
> Die Automatisierung kostet **~25-50 €/Monat** — und arbeitet 24/7.

---

## 🔄 Teil 6: Upgrade-Pfad — Von A nach B

Das Schöne an unserem Setup: **Der Umstieg von Szenario A auf B ist einfach:**

```
Szenario A (Start)                    Szenario B (Upgrade)
─────────────────                    ────────────────────
n8n Cloud          ─── Export ───→   n8n auf eigenem VPS
Supabase Free      ─── Export ───→   PostgreSQL auf VPS
Brevo Free         ─── Upgrade ──→   Brevo Starter
WWebJS (kostenlos) ─── Wechsel ──→   WhatsApp Business API
GitHub Pages       ─── Umzug ────→   VPS oder beibehalten
```

**Wann upgraden?**
- Wenn Jhonatan mehr als ~50 Kunden/Monat hat
- Wenn WhatsApp-Stabilität kritisch wird
- Wenn er mehr als 300 E-Mails/Tag versenden muss
- Wenn die Datenbank über 500MB wächst

**Empfehlung:** Mit **Szenario A starten**. In 6-12 Monaten bewerten, ob ein Upgrade nötig ist.

---

## 🛡️ Teil 7: Sicherheit & Datenschutz (DSGVO)

| Aspekt | Wie wir es lösen |
|--------|-----------------|
| **Kundendaten** | Verschlüsselt in der Datenbank gespeichert |
| **DSGVO** | Alle Dienste haben Server in der EU (Supabase EU, Hetzner DE, Brevo FR) |
| **Zugang** | Nur Jhonatan und Greisy haben Zugang zum Dashboard |
| **Backups** | Automatische tägliche Sicherung |
| **Datenlöschung** | Kunden können Löschung beantragen → 1 Klick im Dashboard |
| **Impressum/Datenschutz** | Auf der Webseite eingebaut |

---

## ❓ Teil 8: Häufige Fragen (die Jhonatan stellen könnte)

**"Muss ich etwas installieren?"**
> Nein. Alles läuft im Browser. Jhonatan braucht nur Internet und ein Gerät (Handy, Tablet, PC).

**"Was passiert, wenn du (Greisy) mal nicht erreichbar bist?"**
> Das System läuft automatisch weiter. Nur bei Problemen oder Änderungen muss jemand eingreifen. Im Notfall kann n8n-Support helfen (Szenario A) oder ein anderer Entwickler die Wartung übernehmen.

**"Kann ich das selbst bedienen?"**
> Ja! Das Dashboard ist so einfach wie eine E-Mail-App: Anfragen ansehen, Dokumente prüfen, auf "Senden" klicken.

**"Was wenn ich den Preis für ein Modul ändere?"**
> Greisy aktualisiert die Preisliste in der Datenbank (~5 Minuten). Ab dann werden neue Angebote automatisch mit dem neuen Preis erstellt.

**"Kann ich das System später erweitern?"**
> Ja. Beispiele: Mahnungssystem, Kundenbewertungen nach Auftrag, Jahresabrechnung, Buchhaltungs-Export (z.B. für den Steuerberater).

**"Was ist wenn ich aufhöre — kann ich die Daten mitnehmen?"**
> Ja. Alle Kundendaten können jederzeit als CSV/Excel exportiert werden. Die Vorlagen (Angebot, Rechnung) gehören dir.

---

## 🎯 Zusammenfassung für Jhonatan (Elevator Pitch)

> **"Dein Geschäft bekommt eine digitale Sekretärin:**
> - Sie sammelt automatisch alle Anfragen — egal ob von der Webseite, WhatsApp, Telegram oder SolarCan
> - Sie erstellt automatisch Angebote, Auftragsbestätigungen und Rechnungen
> - Du prüfst alles mit einem Klick und gibst es frei
> - **Kosten: ~25€/Monat** (weniger als ein einziges Mittagessen pro Woche)
> - **Ersparnis: ~15-20 Stunden Büroarbeit pro Monat**
> - **Setup: Kostenlos** (Greisy macht es als Lernprojekt)"

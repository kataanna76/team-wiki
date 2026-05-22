@~/projects/quinn/TEAM-RULES.md

# CLAUDE.md - team-wiki

## Identity

- **Repo:** team-wiki (shared Reference-Wissen team-weit)
- **Owner:** kein einzelner Agent, Co-Maintainer-Modell.
- **Co-Maintainer (Merge-Rechte master):** Silas (Infra/Build/Reader-Service) + Quinn (Process/Content-Review).
- **PR-Authors (kein Direct-Commit):** Max, Milo, Leo, Lina, Robin, Sara.
- **Reader-Service-Backend:** P979 Wiki-Tool (FastAPI-Routes-Erweiterung auf `~/memory-server/server.py`, Sub-Option-(a) gemaess Spec V1.2).

## Was hier gilt

Vollstaendige Team-Rules unter `@~/projects/quinn/TEAM-RULES.md` (oben eingebunden). Repo-spezifische Punkte zusaetzlich:

### Workflow

Jeder Substanz-Edit braucht PR. Direct-Commit auf master nur fuer trivial typo-Fixes durch Co-Maintainer (Silas/Quinn). Definition trivial:

- Tippfehler-Korrektur ohne Inhalts-Aenderung
- Whitespace/Formatting ohne Wortlaut-Edit
- Broken-Link-Update zu identischem Ziel mit korrigierter URL

**Self-Review-Verbot HART.** PR-Author ist nie Reviewer der eigenen PR. Auch fuer Co-Maintainer:
- Silas-PR braucht Quinn-Review (bei Quinn-Down: Backup-Reviewer-Pattern siehe Reviewer-SLA-Sektion).
- Quinn-PR braucht Silas-Review als Default (bei Silas-Down: Modal-Mailbox an Kata + Lina/Max-Backup).

### Bridge-Notify-Pflicht (Trigger fuer 2h-SLA)

- Nach `gh pr create` (oder Web-UI-PR-Open) MUSS PR-Author Bridge-Send an Quinn (oder Backup-Reviewer bei Quinn-Down) mit Subject `PR open team-wiki#<n>` + 1-Liner-Description + PR-URL.
- Ohne Bridge-Notify gilt nur 24h-voller-Review-SLA (2h-Erst-Antwort entfaellt).
- Begruendung: Quinn ist Bridge-Trigger-aktiviert (kein GitHub-Webhook-Notify), ohne Bridge-Send wird PR-Open nicht in 2h gesehen.

### PR-Pflicht-Pre-Submission-Block

Vor PR-Merge-Request:

1. **Sprach-Regeln-Self-Check** (TEAM-RULES Sprach-Regeln-Sektion):
   - Echte Umlaute ä/ö/ü/ß (kein ae/oe/ue/ss)
   - Keine Em-Dash / En-Dash
   - Gender-Form (`:innen`/`:in`-Verbot in User-facing-Wortlaut)
   - Wort "ehrlich" verboten
2. **Source-Discipline** (TEAM-RULES P293):
   - `[source: <pfad>, YYYY-MM-DD HH:MM CEST] <exakter Wortlaut>` bei jeder Authoritaets-Behauptung
   - Paraphrase verboten bei Authoritaets-Behauptungen
3. **Skill-Stack-Output** bei Wortlaut-Pages (`/schreib-quality-stack` Pflicht-Format).

### Reviewer-SLA

- **24h voller Review** ab PR-Open: HARD-SLA (gilt unabhaengig von Bridge-Notify).
- **2h Erst-Antwort** (Pre-ACK auf PR-Open): BEDINGT — nur bei expliziter PR-Author-Bridge-Notify-Pflicht (siehe PR-Workflow-Section "Bridge-Notify-Pflicht"). Ohne Bridge-Notify gilt nur 24h-voller-Review-SLA, 2h-Erst-Antwort entfaellt. Realitaets-Hinweis: Quinn ist Bridge-Trigger-aktiviert (kein GitHub-Webhook-Notify), `gh pr create` ohne Bridge-Send wird nicht in 2h gesehen.
- Quinn-Down 24h+ silent: Mailbox-Modal an Kata + Backup-Reviewer-Pattern domain-spezifisch:
  - Silas fuer Infra-Pages
  - Lina fuer Wortlaut-Pages
  - Max fuer Coordinator-/Workflow-Pages
- **Quinn-eigene-PR-Reviewer-Hierarchie:** Silas = Default-Reviewer (nicht Quinn selbst, Self-Review-Verbot). Bei Silas-Down 24h+ silent: Mailbox-Modal an Kata + Lina (Wortlaut-Pages) / Max (Workflow-Pages) als Backup-Reviewer. Quinn ist nie Reviewer der eigenen PR.
- Backup-Reviewer-Verdict ersetzt Quinn-Verdict nur fuer den jeweiligen PR.

### Domain-Trennung Wiki vs agentmemory (HART)

Siehe README.md Domain-Trennung-Tabelle. NIE Cross-Mirror. Bei Verstoss: Reviewer-REJECT.

## Cross-Refs

- Spec-Outline: `~/projects/silas/pre-reviews/p979-wiki-tool-spec-outline.md` (V1.2, alle 6 Open-Spec-Questions Q1-Q6 sealed)
- Reader-Service-Code-Owner: Silas (`~/memory-server/server.py` Erweiterung)
- agentmemory-Sub-Apply: `~/projects/silas/pre-reviews/p979-2-agentmemory-install.md` (P979.2)
- Process-Owner Quinn (TEAM-RULES-Owner)
- Coordinator Max

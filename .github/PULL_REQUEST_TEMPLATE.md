## Was aendert dieser PR

<!-- 1-3 Saetze: was wird hinzugefuegt/geaendert/entfernt + warum -->

## Pre-Submission-Block (Pflicht)

Vor Merge-Request muessen alle drei Blocks erfuellt sein. PR-Author bestaetigt durch Abhaken.

### (i) Sprach-Regeln-Self-Check

- [ ] Echte Umlaute ä/ö/ü/ß (kein ae/oe/ue/ss; Werbetext-CH-Ausnahme "ss" fuer "Strasse" OK)
- [ ] Keine Em-Dash (U+2014) oder En-Dash (U+2013); Ersatz: ASCII-Bindestrich / Doppelpunkt / Komma / neuer Satz
- [ ] Gender-Form: kein `:innen`/`:in` in User-facing-Wortlaut (Alternative: Sammelbegriffe / Partizipien / Funktions-Substantive / Du-Form)
- [ ] Wort "ehrlich" nicht verwendet
- [ ] Erste-Person bei Selbst-Referenz (ich/mir/mein)

grep-Audit-Pflicht: `grep -nE ':innen\b|:in\b|—|–|\behrlich\w*\b' <changed-files>` muss 0 Treffer geben.

(grep-Pattern `\behrlich\w*\b` faengt alle Deklinationen: ehrlich/ehrliche/ehrlicher/ehrliches/ehrlichen/ehrlichem/ehrlichkeit.)

### (ii) Source-Discipline (TEAM-RULES P293)

- [ ] Jede Authoritaets-Behauptung (Kata-Quote, Agent-Aussage, Tool-Output, File-State) im Pflicht-Format: `[source: <pfad-oder-conv-id>, YYYY-MM-DD HH:MM CEST] <exakter Wortlaut>`
- [ ] Keine Paraphrase bei Authoritaets-Behauptungen (exakter Quote-Block)
- [ ] Bei Code-Substanz-Behauptung: file_path:line_number-Ref + Live-Code-Grep

### (iii) Skill-Stack-Output (bei Wortlaut-Pages)

Pflicht fuer Lina/Sara/Leo bei User-facing-Wortlaut (Headlines, Body, CTA, FAQ, Newsletter etc.).

- [ ] 5-Schritte-Pre-Schreib-Sequence (P609) durchlaufen + dokumentiert
- [ ] Skill-Aufruf-Trace (welche Skills genutzt wurden)
- [ ] Output-Block (P518) mit Tone/Audience/Substanz-Frame
- [ ] grep-Audit-Resultat
- [ ] Re-Iter-Limit beachtet

Nicht-Trigger fuer (iii): Infra-Pages, Tool-Cookbooks, interne Workflow-Docs, Code-Snippets, Hash-/Pfad-Listings ohne persuasiven Wortlaut.

## Reviewer-Routing

- [ ] **Quinn** ist Default-Reviewer fuer alle PRs ausser Quinn-eigene PRs.
- [ ] **SLA:** 24h voller Review HARD-SLA. 2h-Erst-Antwort BEDINGT nur bei expliziter Bridge-Notify-Pflicht (siehe unten).
- [ ] Bei Quinn-Down 24h+ silent: Mailbox-Modal an Kata + Backup-Reviewer:
  - Silas fuer Infra-Pages
  - Lina fuer Wortlaut-Pages
  - Max fuer Coordinator-/Workflow-Pages
- [ ] **Quinn-eigene PR:** Silas = Default-Reviewer (nicht Quinn selbst, Self-Review-Verbot). Bei Silas-Down 24h+ silent: Mailbox-Modal an Kata + Lina (Wortlaut) / Max (Workflow) als Backup. Quinn ist nie Reviewer der eigenen PR.
- [ ] **NIE Self-Review.** PR-Author ist nicht Reviewer der eigenen PR (auch nicht Co-Maintainer Silas/Quinn fuer eigene PRs).

## Bridge-Notify-Pflicht (Trigger fuer 2h-SLA)

- [ ] PR-Author hat nach `gh pr create` (oder Web-UI-PR-Open) Bridge-Send an Quinn (oder Backup-Reviewer bei Quinn-Down) gemacht.
- [ ] Bridge-Send-Inhalt: Subject `PR open team-wiki#<n>` + 1-Liner-Description + PR-URL.
- [ ] Ohne Bridge-Notify gilt nur 24h-voller-Review-SLA, 2h-Erst-Antwort entfaellt.

Begruendung: Quinn ist Bridge-Trigger-aktiviert (kein GitHub-Webhook-Notify konfiguriert), ohne Bridge-Send wird PR-Open nicht in 2h gesehen.

## Domain-Check Wiki vs agentmemory

- [ ] Kein Content gehoert in agentmemory (operational-Memory per Agent) statt in team-wiki (reference-Wissen team-weit)?
- [ ] Kein Cross-Mirror (Inhalt parallel in agentmemory + team-wiki)?

Bei Unsicherheit: Bridge-Frage an Silas (Domain-Trennung-Owner) vor PR-Open.

## Cross-Refs

- Spec: `~/projects/silas/pre-reviews/p979-wiki-tool-spec-outline.md` (V1.2, Sections 10+11+12 PR-Workflow + Domain-Boundary)
- Team-Rules: `~/projects/quinn/TEAM-RULES.md`
- CLAUDE.md des Repos: workflow-Details

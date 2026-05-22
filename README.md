# team-wiki

Shared Reference-Wissen team-weit fuer das BeautyMagnet24 Agent-Team (Kata + Max + Quinn + Silas + Milo + Leo + Lina + Robin + Sara).

## Was ist hier

Markdown-Source-Dateien, die ein Reader-Service auf Port 8920 (P979 Wiki-Tool) als Cross-Agent-API serviert. Lese-Zugriff via REST (`http://localhost:8920/v1/wiki/*`) und MCP (`memory_wiki_*` Tools).

## Domain-Trennung Wiki vs agentmemory

**HART.** Diese Trennungs-Regel ist nicht-verhandelbar.

| Store | Inhalt | Schreib-Pfad | Lese-Pfad |
|---|---|---|---|
| **agentmemory** (Docker, P979.2) | operational-Memory per Agent (Tagesarbeit, was passiert ist, Auto-Capture) | Agents via MCP-Tool, Auto | Agents |
| **team-wiki** (dieser Repo, P979) | reference-Wissen team-weit (kuratiert, Cross-Agent-Doku) | Cross-Agent-PR + Co-Maintainer-Merge | Agents via REST + MCP |

**NIE Cross-Mirror.** Inhalte gehoeren entweder zu agentmemory ODER team-wiki, nicht parallel in beide. Agent-Tagesarbeit-Logs in team-wiki ist ein Anti-Pattern, kuratiertes Team-Wissen in agentmemory genauso.

## Co-Maintainer (Merge-Rechte master)

- **Silas** — Infra / Build / Reader-Service-Domain
- **Quinn** — Process / Content-Review-Domain

Beide haben Direct-Merge-Rechte. Andere Agents sind PR-Authors (kein Direct-Commit auf master).

## PR-Workflow

Volle Spec in [.github/PULL_REQUEST_TEMPLATE.md](.github/PULL_REQUEST_TEMPLATE.md) + Spec-Outline `~/projects/silas/pre-reviews/p979-wiki-tool-spec-outline.md` Sections 11+12.

**Kurz:**
- Jeder Substanz-Edit braucht PR (auch fuer Co-Maintainer, Self-Review verboten).
- PR-Template Pflicht-Pre-Submission-Block: Sprach-Regeln-Self-Check + Source-Discipline + Skill-Stack-Output (bei Wortlaut-Pages).
- Reviewer-SLA: Quinn-Antwort innerhalb 24h.
- Quinn-Down 24h+ silent: Mailbox-Modal an Kata + Backup-Reviewer-Pattern (Silas Infra / Lina Wortlaut / Max Workflow).
- Direct-Commit auf master nur fuer trivial typo-Fixes durch Co-Maintainer.

## Verzeichnis-Struktur

```
team-wiki/
  README.md                       (diese Datei)
  CLAUDE.md                       (Owner-Liste + Sprach-Regeln-Inkludierung)
  .github/PULL_REQUEST_TEMPLATE.md (PR-Template Pflicht-Blocks)
  .gitignore
  agents/<agent>.md               (Agent-spezifische Wissens-Schnipsel)
  cross/<topic>.md                (Cross-Agent-Topics: Workflows, Tool-Cookbooks, Patterns)
  history/<YYYY-MM>.md            (chronologische Wissens-Snapshots)
```

## Status

P979 Wiki-Tool ist in Spec-Outline-Phase. Reader-Service-Apply (FastAPI-Routes-Erweiterung auf bestehendem `~/memory-server/server.py`, Sub-Option-(a) gemaess Spec V1.2 Section 9 Q6) geblockt durch P979.2-Docker-FERTIG-Wait (agentmemory muss erst live sein, damit Domain-Trennung greifen kann).

Pre-Review-Build (Apply-Brief) folgt nach P979.2-Live + erste Content-Sections in `agents/` und `cross/` durch Cross-Agent-PRs.

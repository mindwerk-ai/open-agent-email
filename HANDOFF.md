# HANDOFF mindwerk-ai/open-agent-email

Datum: 2026-11-14. Verfasser: Claude Opus 5.5.

## Stand
Fork von Anil-matcha/open-agent-email (Basis 0f307a6). Branch `mindwerk/cc-bcc-reply-all` ergänzt To/Cc/Bcc, Reply-All, Zustellstatus je Empfänger (`message_recipients`, Migration 0013, Status `partially_failed`), Next.js 16.4.5 und (Commit 4428484) die Erfassung der SES-Message-ID je Empfänger aus `250 Ok <id>` nach DATA (`message_recipients.relay_message_id`, Migration 0014) samt Eingangs-Threading über `<id@*.amazonses.com>` (nur eigenes Postfach/Tenant). Produktiv auf EX44 (Hermes Mail, https://agentmail.mindwerk.dev) ist Commit 44284842244a8a6408b4d891d0283f19e80d7910. Betrieb, Rollback und Abnahme stehen in /root/workspace/systems/hermes (HANDOFF.md, checks/oae-extern-abnahme.md). Tests: server `pytest` 914 (davon `tests/test_ses_threading.py` 15), sdks/python 145, sdks/typescript 83; client unverändert seit d418a03 (`next build` dort grün).

## Offene Punkte
1. Upstream-Änderungen regelmäßig mergen, Tests laufen lassen, neuen Commit in /root/workspace/systems/hermes/deployment/compose.yml pinnen.
2. Optional: Folgemails auf eigene Ausgänge mit SES-ID je Empfänger in References versehen (siehe Abnahme, Grenzen).
3. Optional Upstream-PR anbieten; nur nach ausdrücklichem Auftrag.

## Nicht tun
- Nicht nach `origin` (Upstream) pushen; Remote `mindwerk` ist das eigene Ziel.
- Keine Secrets, `.venv`, `node_modules` oder Daten committen.
- Rollback nie ohne Alembic-Restamp (0013 für d418a03, 0012 für 0f307a6).
- `_send_smtp_sync` nicht auf eigene SMTP-Befehlsfolge umbauen; die DATA-Antwort kommt über das umhüllte `server.data`, die Annahme darf nie vom Parsen abhängen.

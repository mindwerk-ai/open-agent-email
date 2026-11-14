# HANDOFF mindwerk-ai/open-agent-email

Datum: 2026-11-14. Verfasser: Claude Opus 5.5.

## Stand
Fork von Anil-matcha/open-agent-email (Basis 0f307a6). Branch `mindwerk/cc-bcc-reply-all` ergänzt To/Cc/Bcc, Reply-All, Zustellstatus je Empfänger (`message_recipients`, Migration 0013, Status `partially_failed`) und Next.js 16.4.5. Produktiv auf EX44 (Hermes Mail, https://agentmail.mindwerk.dev) ist Commit d418a03f1c799a3033bfb5d48531a498d51534f4. Betrieb, Rollback und Abnahme stehen in /root/workspace/systems/hermes (HANDOFF.md, checks/oae-ccbcc-abnahme.md). Tests: server `pytest` 899, sdks/python 145, sdks/typescript 83, client `next build`.

## Offene Punkte
1. Upstream-Änderungen regelmäßig mergen, Tests laufen lassen, neuen Commit in /root/workspace/systems/hermes/deployment/compose.yml pinnen.
2. Optional Upstream-PR anbieten; nur nach ausdrücklichem Auftrag.

## Nicht tun
- Nicht nach `origin` (Upstream) pushen; Remote `mindwerk` ist das eigene Ziel.
- Keine Secrets, `.venv`, `node_modules` oder Daten committen.
- Rollback auf 0f307a6 nie ohne Alembic-Restamp auf 0012.

# DECISIONS

| Nr. | Datum | Entscheidung | Warum | Verworfene Alternativen |
|---|---|---|---|---|
| 1 | 2026-11-14 | Eigener öffentlicher Fork unter mindwerk-ai mit Branch mindwerk/cc-bcc-reply-all; CC/BCC/Reply-All mit einer SMTP-Transaktion je Empfänger und persistiertem Status je Empfänger. | Upstream unterstützt nur einen Empfänger; Teilfehler dürfen keine Doppelmails erzeugen; Bcc darf nie in Headern oder Fremdkopien landen. | Upstream direkt nutzen; eine Transaktion für alle Empfänger; Bcc-Liste in Kopien speichern. |

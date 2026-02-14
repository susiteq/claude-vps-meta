# mailbox.org SMTP konfigurieren

**Status:** Offen
**Priorität:** Niedrig

## Problem

mailbox.org-Konto existiert, eigene Domain ist eingerichtet. Empfangen funktioniert, Senden über eigene Domain noch nicht.

## Kontext

- Wird für Supabase Auth (GoTrue) SMTP gebraucht
- Supabase läuft aktuell mit Auto-Confirm (kein SMTP nötig)
- Sobald SMTP funktioniert: in Supabase `.env` die SMTP-Variablen anpassen und `ENABLE_EMAIL_AUTOCONFIRM=false` setzen

## TODO

1. mailbox.org SMTP-Konfiguration für eigene Domain prüfen (SPF, DKIM, DMARC)
2. Senden testen
3. Supabase SMTP-Variablen konfigurieren

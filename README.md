# JustDNS DACH-Blockliste

Eine **Ergänzung** zu den großen internationalen DNS-Blocklisten (Hagezi, OISD)
für den **DACH-Raum** (Deutschland, Österreich, Schweiz): deutschsprachige
Werbe-, Tracking- und Reichweitenmess-Domains, die internationale Listen
erfahrungsgemäß schwächer abdecken.

> **Keine Hagezi-Kopie.** Diese Liste enthält bewusst nur das *Delta* — Domains,
> die gängige Listen durchlassen. Betreibe sie **zusätzlich** zu Hagezi Normal,
> nicht als Ersatz.

## Was drin ist (und was nicht)

- **Drin:** DACH-spezifische Reichweitenmessung, Tracking und Ad-Dienste, die
  nachweislich keine Website-Funktion tragen (reine Mess-/Werbe-Beacons).
- **Nicht drin:** alles, was eine Seite zum Funktionieren braucht; First-Party-
  Werbung (YouTube/Facebook etc. — per DNS ohnehin nicht blockbar); Domains, die
  schon in Hagezi stehen.

## Fehlblock-Politik

Ziel sind **nahezu null Fehlblocks**. Darum:

- Jede Domain wird **einzeln geprüft**, bevor sie aufgenommen wird.
- Im Zweifel bleibt eine Domain **draußen**.
- Fehlblock gemeldet? → Issue öffnen, Domain fliegt raus oder wird präzisiert.
- Jeder Eintrag trägt (per Kommentar) seine **Quelle/Begründung**.

## Format

Eine Domain pro Zeile. `#` leitet einen Kommentar ein. Eine Domain deckt
automatisch alle Subdomains mit ab (`ioam.de` ⇒ auch `score.ioam.de`). Das ist
das schlichte „onlydomains"-Format und wird von **JustDNS**, Pi-hole und
AdGuard Home direkt gelesen.

## Nutzung in JustDNS

1. **Block/Allow → Katalog → eigenen Feed per URL hinzufügen** und die Roh-URL
   dieser Liste eintragen:
   `https://raw.githubusercontent.com/<owner>/<repo>/main/dach-ads-trackers.txt`
2. Oder — geplant — als fester **Katalog-Eintrag** mit „Empfohlen"-Badge.

## Pflege

Die Liste wächst aus **echtem Traffic** (JustDNS-Protokoll) plus Review, nicht
aus Raten. Änderungen werden im Verlauf festgehalten.

## Lizenz

CC0 / Public Domain (vorläufig — vor Veröffentlichung festlegen).

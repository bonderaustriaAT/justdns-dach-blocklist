# JustDNS Blockliste

Eine **Ergänzung** zu den großen internationalen DNS-Blocklisten (Hagezi, OISD).
Die Liste deckt zwei Dinge ab, die internationale Listen erfahrungsgemäß
schwächer oder gar nicht erfassen:

1. **DACH-Delta:** deutschsprachige Werbe-, Tracking- und Reichweitenmess-Domains
   (Deutschland, Österreich, Schweiz), die gängige Listen durchlassen.
2. **Malware / C2 / Dropper:** Domains, von denen im JustDNS-Honeypot-Netz
   nachweislich Schadsoftware nachgeladen oder Command-and-Control-Verkehr
   versucht wurde (beobachtet in echten Angreifer-Sessions).

> **Keine Hagezi-Kopie.** Die Liste enthält bewusst nur das *Delta*. Betreibe
> sie **zusätzlich** zu Hagezi Normal, nicht als Ersatz.

## Was drin ist (und was nicht)

- **Drin:** DACH-spezifische Reichweitenmessung, Tracking und Ad-Dienste ohne
  Seitenfunktion (reine Mess-/Werbe-Beacons); Malware-/C2-/Dropper-Domains aus
  echten Honeypot-Beobachtungen.
- **Nicht drin:** alles, was eine Seite zum Funktionieren braucht; First-Party-
  Werbung (YouTube/Facebook etc., per DNS ohnehin nicht blockbar); Domains, die
  schon in Hagezi stehen; legitime Hoster, von denen Angreifer bloß Dateien
  ziehen (github, pastebin, Objekt-Storage, CDN usw. bleiben per Allowlist raus).

## Fehlblock-Politik

Ziel sind **nahezu null Fehlblocks**. Darum:

- Jede Domain wird **geprüft**, bevor sie aufgenommen wird. Honeypot-Kandidaten
  durchlaufen erst Guardrails (Hoster-/CDN-Allowlist, Auflösungs-Check, Dedupe)
  und dann eine **manuelle Freigabe**; nichts landet automatisch roh in der Liste.
- Im Zweifel bleibt eine Domain **draußen**.
- Fehlblock gemeldet? Issue öffnen, Domain fliegt raus oder wird präzisiert.
- Jeder Eintrag trägt (per Kommentar) seine **Quelle/Begründung**.

## Format

Eine Domain pro Zeile. `#` leitet einen Kommentar ein. Eine Domain deckt
automatisch alle Subdomains mit ab (`ioam.de` auch `score.ioam.de`). Das ist das
schlichte onlydomains-Format und wird von **JustDNS**, Pi-hole und AdGuard Home
direkt gelesen.

## Nutzung in JustDNS

1. **Block/Allow, Katalog, eigenen Feed per URL hinzufügen** und die Roh-URL
   dieser Liste eintragen:
   `https://raw.githubusercontent.com/bonderaustriaAT/justdns-blocklist/main/dach-ads-trackers.txt`
2. Oder, geplant, als fester **Katalog-Eintrag** mit Empfohlen-Badge.

## Pflege

Die Liste wächst aus **echten Quellen** plus Review, nicht aus Raten:

- **DACH-Delta** aus JustDNS-Protokoll plus Einzelprüfung.
- **Malware/C2** aus dem Honeypot-Netz: Sensoren melden beobachtete Nachlade-URLs
  nur an die zentrale Intake-Node. Dort laufen die Guardrails, und **ausschließlich
  die Intake-Node** committet nach einer Freigabe in diese Liste. Einzelne
  Honeypots haben keinen Schreibzugriff.

Änderungen werden im Verlauf festgehalten.

## Lizenz

CC0 / Public Domain (vorläufig, vor Veröffentlichung festlegen).

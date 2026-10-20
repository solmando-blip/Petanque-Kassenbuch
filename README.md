# Pétanque Kassenbuch — Master Pro

Ein eigenständiges, browserbasiertes Kassenbuch für Pétanque-Abteilungen gemeinnütziger Vereine. Keine Installation, kein Server — eine einzelne HTML-Datei, läuft lokal im Browser.

**Datei:** [`kassenbuch_master_pro.html`](./kassenbuch_master_pro.html)

## Inhaltsverzeichnis

- [Funktionsübersicht](#funktionsübersicht)
- [Nutzung](#nutzung)
- [Steuerliche Sphären](#steuerliche-sphären)
- [Datenmodell](#datenmodell)
- [Datenhaltung & Backup](#datenhaltung--backup)
- [Bankauszug-Import (CSV)](#bankauszug-import-csv)
- [Festschreibung (GoBD)](#festschreibung-gobd)
- [Spendenquittung](#spendenquittung)
- [Bekannte Grenzen](#bekannte-grenzen)
- [Sicherheitshinweise](#sicherheitshinweise)
- [Changelog](#changelog)

## Funktionsübersicht

- Erfassung von Einnahmen/Ausgaben für **Barkasse** und **Bankkonto**, getrennt geführt
- Automatische Zuordnung jeder Buchung zu einer **steuerlichen Sphäre** (Ideell / Zweckbetrieb / Wirtschaftlicher Geschäftsbetrieb)
- **Zweckgebundene Mittel**: Nachverfolgung von zweckgebundenen Einnahmen und zugehörigen Ausgaben
- **Kassensturz-Rechner** (Stückelung von Bargeld, inkl. Wechselgeld-Abzug)
- Schnellwahltasten für häufige Buchungen
- Beleg-/Fotoanhang pro Buchung (lokal im Browser gespeichert)
- **Kassenbericht & Jahresabschluss** druckbar (inkl. Sphären-Übersicht und Unterschriftenfeldern für Kassenprüfer)
- Tabellen-Filter (Text + Monat)
- Sphären-Verteilung als Diagramm (Chart.js)
- **CSV-Export** der Buchungen (Excel-kompatibel, deutsches Format)
- **JSON-Backup** manuell und automatisch (alle 5 Buchungen + monatlich)
- **Bankauszug-Import** aus CSV mit Prüfmaske vor Übernahme
- **Festschreibung** abgeschlossener Buchungen (GoBD-Prinzip der Unveränderbarkeit)
- **Spendenquittungen** (Zuwendungsbestätigungen) druckbar für Spenden ohne Werbung

## Nutzung

1. `kassenbuch_master_pro.html` im Browser öffnen (Doppelklick genügt, kein Server nötig).
2. Beim ersten Start: unter **„⚙️ Vereinsdaten"** Vereinsname, Anschrift, Finanzamt und Freistellungsbescheid-Datum eintragen (wird für Spendenquittungen benötigt).
3. Buchungen über das Formular links erfassen oder per Schnellwahltaste vorbefüllen.
4. Regelmäßig **„💾 Als CSV sichern"** oder **„📂 Backup einspielen"** nutzen, um Daten extern zu sichern — die Daten liegen sonst nur im Browser-`localStorage` dieses einen Geräts/Browsers.

Alle Daten bleiben **lokal im Browser** (`localStorage`). Es gibt keine Server-Anbindung, keine Cloud-Synchronisation. Wird der Browser-Speicher gelöscht (z. B. "Browserdaten löschen"), gehen unges­icherte Buchungen verloren — daher sind regelmäßige Backups essenziell.

## Steuerliche Sphären

Jede Buchungskategorie ist fest einer Sphäre nach deutschem Gemeinnützigkeitsrecht zugeordnet:

| Sphäre | Beispiele | Relevanz |
|---|---|---|
| **Ideell** | Spenden ohne Werbung, Zuschüsse, Verwaltung, Versicherung | Steuerbefreit, kein wirtschaftlicher Bezug |
| **Zweckbetrieb** | Startgelder Turniere/Liga, Trainer-Honorare, Platzmiete, Pokale | Steuerbegünstigt, da unmittelbare Zweckverwirklichung (§ 65 AO) |
| **Wirtschaftlicher Geschäftsbetrieb** | Getränke-/Speisenverkauf, Tombola, Sponsoring mit Werbung | Grundsätzlich steuerpflichtig (§§ 64, 65 AO), Freigrenze beachten |

Die Zuordnung ist in `categoryMapping` im Script hinterlegt und kann bei Bedarf erweitert werden.

**Hinweis:** Dies ist eine funktionale Hilfestellung, keine Steuerberatung. Die korrekte Sphären-Zuordnung und Freigrenzen sollten im Zweifel mit einem Steuerberater abgestimmt werden.

## Datenmodell

Jede Buchung ist ein Objekt mit folgenden Feldern:

```js
{
  id: number,              // fortlaufend, stabil (nicht neu vergeben)
  date: "YYYY-MM-DD",
  account: "bar" | "bank",
  cat: string,              // Kategorie-Schlüssel, siehe categoryMapping
  desc: string,
  type: "ein" | "aus",
  amount: number,            // > 0
  balance: number,           // wird bei jedem Dashboard-Update neu berechnet
  sphere: "Ideell" | "Zweckbetrieb" | "Wirtschaft",
  restricted: boolean,       // zweckgebunden (Einnahme) bzw. verwendet zweckgebundene Mittel (Ausgabe)
  receipt: string | null,    // Beleg als Data-URL (Base64)
  locked: boolean,           // festgeschrieben, nicht mehr editierbar/löschbar
  donorName: string          // nur bei Kategorie ein_sponsoring_spende relevant
}
```

Der Saldo pro Konto wird **nicht gespeichert, sondern bei jedem Rendering aus der chronologisch sortierten Buchungsliste neu berechnet** (`sortBookingsForLedger` + `updateDashboard`), um Inkonsistenzen durch nachträgliche Bearbeitung zu vermeiden.

## Datenhaltung & Backup

| Was | localStorage-Key |
|---|---|
| Alle Buchungen | `petanque_bookings_master` |
| Checkliste | `petanque_checklist` |
| Zähler für Auto-Backup | `petanque_total_entries_counter` |
| Liste der letzten 5 Auto-Backups | `petanque_auto_backups_list_master` |
| Monatssicherungen | `petanque_monthly_master_<Jahr>_<Monat>` |
| Zeitpunkt letzte Festschreibung | `petanque_lock_date` |
| Vereinsdaten | `petanque_vereinsdaten` |

Automatische Backups:
- Alle 5 neuen Buchungen wird ein JSON-Backup automatisch heruntergeladen (die letzten 5 werden zusätzlich im Browser vorgehalten).
- Pro Kalendermonat wird einmalig eine Monatssicherung heruntergeladen.

**Backup wiederherstellen:** über „📂 Backup einspielen" eine zuvor exportierte JSON-Datei einlesen. Die Datei wird vor der Übernahme strukturell validiert; bei ungültigen Einträgen wird der Import komplett abgebrochen.

## Bankauszug-Import (CSV)

Über „🏦 Bankauszug importieren (CSV)" lässt sich eine CSV-Datei der Bank einlesen.

**Erwartetes Format pro Zeile:** `Datum;Betrag;Verwendungszweck`
- Datum: `TT.MM.JJJJ` oder `JJJJ-MM-TT`
- Betrag: deutsches (`150,00`) oder internationales (`150.00`) Format; positiv = Einnahme, negativ = Ausgabe
- Eine optionale Kopfzeile wird automatisch erkannt und übersprungen

Vor der Übernahme erscheint eine **Prüfmaske**: jede Zeile muss manuell einer Kategorie zugeordnet werden, Zeilen können abgewählt und der Verwendungszweck editiert werden. Es wird **nichts automatisch** gebucht — der Import dient nur der Dateneingabe-Beschleunigung, nicht einem automatisierten Kontoabgleich.

## Festschreibung (GoBD)

„🔒 Buchungen festschreiben" markiert alle aktuell offenen Buchungen als unveränderlich — analog zum bereits von Anfang an gesperrten Vortrag. Das bildet den GoBD-Grundsatz der Unveränderbarkeit nach Abschluss eines Prüfungszeitraums ab (z. B. nach der jährlichen Kassenprüfung).

- **Nicht rückgängig machbar** innerhalb der Anwendung — vorher Backup erstellen.
- Festgeschriebene Buchungen können weder bearbeitet noch gelöscht werden.
- Neue Buchungen nach der Festschreibung bleiben bis zur nächsten Festschreibung normal editierbar.
- Der Zeitpunkt der letzten Festschreibung wird angezeigt.

## Spendenquittung

Unter „⚙️ Vereinsdaten" müssen Vereinsname, Anschrift, zuständiges Finanzamt und Datum des Freistellungsbescheids hinterlegt werden. Bei Buchungen der Kategorie **„Spenden ohne Werbung (Ideell)"** kann optional der Spendername erfasst werden; in der Buchungstabelle erscheint dann ein Button **„Quittung"**, der eine druckfertige Zuwendungsbestätigung (§ 10b EStG) in einem neuen Fenster öffnet.

> ⚠️ **Dies ist eine Muster-Vorlage, keine Rechts- oder Steuerberatung.** Format und Pflichtangaben sollten vor Verwendung mit Steuerberater bzw. Finanzamt abgestimmt werden (amtliches Muster beachten, siehe BMF-Schreiben zu Zuwendungsbestätigungen).

## Bekannte Grenzen

- **Keine echte Mehrbenutzerfähigkeit** — Daten liegen pro Browser/Gerät; kein zentraler Server, kein Datenabgleich zwischen Geräten.
- **Kein Bankabgleich (HBCI/FinTS)** — CSV-Import ist eine manuelle Dateneingabehilfe, kein automatischer Kontoabruf.
- **Keine doppelte Buchführung** — einfache Einnahmen-Überschuss-Logik, kein Kontenrahmen (SKR etc.).
- **Belege als Base64 in `localStorage`** — Browser-Speicherlimits (meist 5–10 MB) können bei vielen/großen Belegfotos erreicht werden; bei Fehlschlag erscheint ein Warnhinweis.
- Ein Vergleich mit der kommerziellen Lösung *VereinOnline* (doppelte Buchführung, SEPA, DATEV, Mitgliederverwaltung) zeigt: Dieses Tool deckt bewusst nur den Kassenbuch-/Sphären-Ausschnitt ab, nicht die vollständige Vereinsbuchhaltung.

## Sicherheitshinweise

- Alle dynamisch eingefügten Textwerte (Beschreibung, Spendername, Belegpfad) werden vor der Anzeige escaped (`escapeHtml`), um XSS beim Import fremder Backup-Dateien zu verhindern.
- Backup-Importe werden strukturell validiert (Pflichtfelder, Typen) bevor sie übernommen werden.
- Es findet keine Übertragung an Dritte statt — die Anwendung lädt lediglich Chart.js von einem CDN (`cdn.jsdelivr.net`) nach, alle übrigen Daten bleiben lokal.

## Changelog

Siehe [`CHANGELOG.md`](./CHANGELOG.md) für die Historie der Review-Fixes und Erweiterungen.

## Lizenz

Keine Lizenz hinterlegt — intern für den Verein. Bei Bedarf (z. B. Weitergabe an andere Abteilungen/Vereine) eine Lizenz ergänzen.

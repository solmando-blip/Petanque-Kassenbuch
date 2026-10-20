# Benutzerhandbuch — Pétanque Kassenbuch Master Pro

Dieses Handbuch richtet sich an den Kassenwart bzw. die Kassenwartin der Pétanque-Abteilung. Es erklärt die Bedienung Schritt für Schritt, ohne technisches Vorwissen vorauszusetzen.

## Inhaltsverzeichnis

1. [Erste Schritte](#1-erste-schritte)
2. [Die Startseite im Überblick](#2-die-startseite-im-überblick)
3. [Eine Buchung erfassen](#3-eine-buchung-erfassen)
4. [Schnellwahltasten](#4-schnellwahltasten)
5. [Kassensturz (Bargeld zählen)](#5-kassensturz-bargeld-zählen)
6. [Zweckgebundene Mittel](#6-zweckgebundene-mittel)
7. [Beleg anhängen](#7-beleg-anhängen)
8. [Buchung bearbeiten oder löschen](#8-buchung-bearbeiten-oder-löschen)
9. [Buchungen suchen und filtern](#9-buchungen-suchen-und-filtern)
10. [Sichern und Backup](#10-sichern-und-backup)
11. [Bankauszug importieren](#11-bankauszug-importieren)
12. [Buchungen festschreiben](#12-buchungen-festschreiben)
13. [Vereinsdaten hinterlegen](#13-vereinsdaten-hinterlegen)
14. [Spendenquittung ausstellen](#14-spendenquittung-ausstellen)
15. [Kassenbericht drucken](#15-kassenbericht-drucken)
16. [Checkliste](#16-checkliste)
17. [Häufige Fragen](#17-häufige-fragen)
18. [Problembehandlung](#18-problembehandlung)

---

## 1. Erste Schritte

Das Kassenbuch ist eine einzelne Datei: `kassenbuch_master_pro.html`. Sie benötigen **keine Installation** und **keinen Internetzugang** (bis auf eine kleine Diagramm-Komponente, die beim ersten Laden nachgeladen wird).

**Öffnen:** Doppelklick auf die Datei — sie öffnet sich in Ihrem Standardbrowser (Chrome, Firefox, Edge, Safari).

> ⚠️ **Wichtig:** Öffnen Sie die Datei immer über **denselben Browser auf demselben Gerät**. Ihre Buchungen werden nur dort gespeichert, wo Sie sie eingegeben haben — nicht in einer Cloud. Siehe [Kapitel 10](#10-sichern-und-backup) für regelmäßige Sicherungen.

Beim allerersten Öffnen eines neuen Kassenbuchs sollten Sie direkt:
1. Unter **„⚙️ Vereinsdaten"** Ihre Vereinsangaben eintragen ([Kapitel 13](#13-vereinsdaten-hinterlegen)).
2. Den **Vortrag** (Anfangsbestand) prüfen — dieser ist bereits als erste, gesperrte Buchung vorhanden.

## 2. Die Startseite im Überblick

Oben sehen Sie vier Kacheln:

| Kachel | Bedeutung |
|---|---|
| **Kassenbestand (Bar)** | Aktueller Bargeldbestand |
| **Bankkonto (Giro)** | Aktueller Kontostand laut erfassten Buchungen |
| **Wirtschaftlicher Betrieb** | Saldo aus steuerpflichtigen Einnahmen/Ausgaben (z. B. Getränkeverkauf) |
| **Zweckgebunden (Offen)** | Noch nicht verbrauchte zweckgebundene Spenden |

Links befindet sich das **Erfassungsformular**, rechts die **Buchungsliste** mit Filter- und Suchfunktion sowie ein Kreisdiagramm zur Sphären-Verteilung.

## 3. Eine Buchung erfassen

1. **Zahlungsweg** wählen: Barkasse oder Bankkonto.
2. **Datum** eintragen (Vorbelegung: heute).
3. **Kategorie** auswählen — die Liste ist nach Einnahmen und Ausgaben gegliedert, jede Kategorie zeigt in Klammern die steuerliche Sphäre an.
4. **Verwendungszweck** eintragen (Pflichtfeld).
5. **Betrag** eintragen (muss größer als 0 sein).
6. Optional: **Beleg/Foto** anhängen ([Kapitel 7](#7-beleg-anhängen)).
7. Auf **„Speichern"** klicken.

Die Übersicht oben und die Buchungsliste aktualisieren sich automatisch.

> 🔴 Versucht man, mehr Bargeld auszugeben als in der Kasse ist, erscheint die Meldung „Kassenbestand darf nicht negativ werden!" — die Buchung wird dann **nicht** gespeichert.

## 4. Schnellwahltasten

Oberhalb des Formulars finden Sie vier blaue Buttons für wiederkehrende Standardbuchungen (z. B. „+ 10 € Startgeld"). Ein Klick befüllt Kategorie, Verwendungszweck und Betrag automatisch — Sie müssen nur noch Datum und Zahlungsweg prüfen und auf „Speichern" klicken.

## 5. Kassensturz (Bargeld zählen)

Bei den Kategorien **„Getränkeverkauf"** und **„Speisen-/Essensverkauf"** erscheint automatisch ein Stückelungsrechner:

1. Für jede Münz-/Scheinsorte die gezählte Anzahl eintragen.
2. Unter „Minus Wechselgeld" den Betrag eintragen, mit dem die Kasse gestartet wurde (Standard: 50 €).
3. Der Betrag für „Tageseinnahme" wird automatisch berechnet und in das Betragsfeld übernommen.

## 6. Zweckgebundene Mittel

Manche Spenden sind an einen bestimmten Zweck gebunden (z. B. „für neue Trikots"). So verwalten Sie das korrekt:

- **Bei der Einnahme:** Haken bei „Diese Einnahme ist zweckgebunden" setzen.
- **Bei der zugehörigen Ausgabe:** Haken bei „Diese Ausgabe verwendet zweckgebundene Mittel" setzen.

Die Kachel „Zweckgebunden (Offen)" zeigt dann immer den noch nicht verbrauchten Restbetrag.

## 7. Beleg anhängen

Im Formular unter „📎 Beleg/Foto anhängen" eine Bild- oder PDF-Datei auswählen (z. B. ein abfotografierter Kassenbon). Der Beleg wird mit der Buchung gespeichert und ist in der Tabelle über ein Büroklammer-Symbol (📎) abrufbar.

## 8. Buchung bearbeiten oder löschen

In der Buchungsliste finden Sie pro Zeile die Buttons **„Bearbeiten"** und **„Löschen"**.

- **Bearbeiten** lädt die Buchung zurück ins Formular — ändern Sie die gewünschten Felder und klicken Sie auf „Änderungen speichern". Mit „Abbrechen" verwerfen Sie die Bearbeitung.
- **Löschen** fragt zur Sicherheit nach Bestätigung.

Buchungen, die als **„Vortrag"** oder **„🔒 Festgeschrieben"** gekennzeichnet sind, können nicht mehr bearbeitet oder gelöscht werden (siehe [Kapitel 12](#12-buchungen-festschreiben)).

## 9. Buchungen suchen und filtern

Oberhalb der Tabelle:

- **Textsuche:** durchsucht Datum, Kategorie und Verwendungszweck.
- **Monatsfilter:** zeigt nur Buchungen eines bestimmten Monats.

Beide Filter lassen sich kombinieren und wirken sofort, ohne Bestätigung.

## 10. Sichern und Backup

Da alle Daten nur lokal im Browser liegen, sind regelmäßige Sicherungen wichtig.

**Manuell sichern:**
- **„💾 Als CSV sichern"** — exportiert alle Buchungen als Excel-kompatible Tabelle.
- **„📂 Backup einspielen"** — lädt zuvor gesicherte JSON-Dateien zurück ins Kassenbuch (ersetzt den aktuellen Stand komplett).

**Automatisch:** Alle 5 neuen Buchungen sowie einmal pro Kalendermonat wird automatisch eine JSON-Sicherung als Download ausgelöst (Hinweis erscheint kurz auf dem Bildschirm). Diese Dateien sollten Sie an einem sicheren Ort (z. B. Cloud-Speicher, USB-Stick) ablegen.

> 💡 **Empfehlung:** Laden Sie die automatischen Backup-Dateien regelmäßig aus Ihrem Download-Ordner in einen externen Sicherungsort, idealerweise außerhalb des Geräts.

## 11. Bankauszug importieren

Statt jede Bank-Buchung einzeln einzutippen, können Sie einen Kontoauszug als CSV-Datei importieren:

1. Button **„🏦 Bankauszug importieren (CSV)"** klicken und Datei auswählen.
2. Format der Datei: pro Zeile `Datum;Betrag;Verwendungszweck` (z. B. `12.04.2026;150,00;Spende Mustermann`).
3. Es öffnet sich eine Prüfmaske mit allen erkannten Zeilen. Für **jede Zeile, die Sie übernehmen möchten**, wählen Sie eine passende Kategorie aus. Nicht benötigte Zeilen können Sie über das Kästchen abwählen.
4. Mit **„✅ Ausgewählte Buchungen importieren"** werden die gewählten Zeilen als Bankbuchungen übernommen.

> Es wird **nichts automatisch** gebucht — Sie behalten die volle Kontrolle über jede einzelne Zeile.

## 12. Buchungen festschreiben

Nach einer Kassenprüfung oder zum Jahresabschluss können Sie alle bisherigen Buchungen unveränderlich machen:

1. Button **„🔒 Buchungen festschreiben (GoBD)"** klicken.
2. Bestätigen Sie den Hinweis — **dieser Schritt kann nicht rückgängig gemacht werden.**

Danach sind alle bis dahin erfassten Buchungen gesperrt (erkennbar am Hinweis „🔒 Festgeschrieben" statt der Bearbeiten/Löschen-Buttons). Neue Buchungen können Sie wie gewohnt weiter erfassen — sie bleiben bis zur nächsten Festschreibung änderbar.

Unterhalb des Buttons sehen Sie immer, wann zuletzt festgeschrieben wurde.

> 💡 Erstellen Sie vor dem Festschreiben unbedingt ein Backup (siehe [Kapitel 10](#10-sichern-und-backup)).

## 13. Vereinsdaten hinterlegen

Im Bereich **„⚙️ Vereinsdaten"** tragen Sie einmalig ein:

- Vereinsname
- Anschrift
- Zuständiges Finanzamt
- Datum des Freistellungsbescheids

Mit **„Vereinsdaten speichern"** werden die Angaben im Browser hinterlegt. Diese Daten werden für Spendenquittungen benötigt (siehe nächstes Kapitel).

## 14. Spendenquittung ausstellen

Bei Buchungen der Kategorie **„Spenden ohne Werbung (Ideell)"** erscheint im Formular zusätzlich ein Feld für den **Namen des Spenders**. Tragen Sie diesen ein, falls Sie eine Spendenquittung ausstellen möchten.

So drucken Sie eine Quittung:

1. Stellen Sie sicher, dass die [Vereinsdaten](#13-vereinsdaten-hinterlegen) hinterlegt sind.
2. Suchen Sie die Spenden-Buchung in der Tabelle.
3. Klicken Sie auf den Button **„Quittung"**.
4. Es öffnet sich ein neues Fenster mit der fertigen Zuwendungsbestätigung, die sich direkt ausdrucken lässt (Druckdialog öffnet automatisch).

> ⚠️ **Wichtiger Hinweis:** Die erzeugte Quittung ist eine **Muster-Vorlage ohne Gewähr** und stellt keine Rechts- oder Steuerberatung dar. Prüfen Sie vor der Verwendung Format und Pflichtangaben mit Ihrem Steuerberater bzw. Finanzamt (amtliches Muster beachten).

## 15. Kassenbericht drucken

Mit **„🖨️ Kassenbericht & Jahresabschluss drucken"** öffnet sich der normale Druckdialog des Browsers. Es wird automatisch eine saubere, aufbereitete Druckansicht erzeugt mit:

- Bestandsübersicht (Barkasse, Bankkonto, Gesamtvermögen)
- Sphären-Übersicht (Ideell, Zweckbetrieb, Wirtschaft)
- Unterschriftenfeldern für Kassierer und zwei Kassenprüfer

Die normalen Bedienelemente (Formular, Buttons) werden beim Drucken automatisch ausgeblendet.

## 16. Checkliste

Im Bereich **„📋 Kassenwart Checkliste"** können Sie wiederkehrende Aufgaben (z. B. „Kassenprüfung vorbereiten") abhaken. Der Status wird automatisch gespeichert und bleibt beim nächsten Öffnen erhalten.

## 17. Häufige Fragen

**Kann ich das Kassenbuch auf mehreren Geräten gleichzeitig nutzen?**
Nein. Die Daten liegen nur im Browser des Geräts, auf dem Sie gebucht haben. Für die Nutzung auf einem anderen Gerät müssen Sie ein Backup exportieren und dort importieren.

**Was passiert, wenn ich den Browser-Cache lösche?**
Alle ungesicherten Buchungen gehen verloren. Importieren Sie danach Ihr letztes Backup.

**Kann ich eine festgeschriebene Buchung doch noch korrigieren?**
Nicht direkt. Erfassen Sie stattdessen eine neue, korrigierende Gegenbuchung mit erläuterndem Verwendungszweck (so bleibt die Nachvollziehbarkeit gewahrt, wie es auch die GoBD verlangen).

**Ist die Spendenquittung rechtlich bindend?**
Es handelt sich um eine Muster-Vorlage. Die endgültige Verantwortung für Form und Inhalt liegt beim Verein — bitte vorab mit Steuerberater/Finanzamt abstimmen.

## 18. Problembehandlung

| Problem | Lösung |
|---|---|
| Meldung „Kassenbestand darf nicht negativ werden" | Prüfen Sie, ob genug Bargeld in der Kasse erfasst ist, oder korrigieren Sie den Betrag. |
| Spendenquittung öffnet sich nicht | Pop-ups für diese Seite im Browser erlauben und erneut klicken. |
| „Quittung"-Button fehlt | Nur bei Kategorie „Spenden ohne Werbung (Ideell)" verfügbar — Kategorie der Buchung prüfen. |
| Warnung „Buchungen konnten nicht gespeichert werden" | Browser-Speicher ist voll (oft durch viele Belegfotos). Zeitnah CSV-/Backup-Export durchführen und ggf. alte Belege reduzieren. |
| Bankimport findet keine Zeilen | Dateiformat prüfen: `Datum;Betrag;Verwendungszweck`, Semikolon-getrennt, deutsches oder ISO-Datum. |
| „Bearbeiten"/„Löschen" fehlt bei einer Buchung | Die Buchung ist festgeschrieben oder der Vortrag — beides ist absichtlich gesperrt. |

---

*Bei technischen Fragen zum Quellcode siehe [README.md](./README.md).*

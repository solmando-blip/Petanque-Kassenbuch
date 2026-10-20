# Changelog

Alle wesentlichen Änderungen an diesem Projekt werden hier dokumentiert.

## [Unreleased]

### Hinzugefügt
- **Bankauszug-Import (CSV)**: Einlesen von Bankkonto-Buchungen aus CSV mit Prüfmaske (Kategoriewahl, Zeilen-Abwahl) vor der Übernahme — kein automatisches Buchen ohne Kontrolle.
- **Festschreibung (GoBD)**: Button zum unveränderlichen Markieren aller offenen Buchungen, analog zum bisherigen Schutz des Vortrags. Zeigt Zeitpunkt der letzten Festschreibung an.
- **Spendenquittung**: Hinterlegbare Vereinsdaten (Name, Anschrift, Finanzamt, Freistellungsbescheid-Datum) und druckfertige Zuwendungsbestätigung (§ 10b EStG) pro Spenden-Buchung, inkl. optionalem Spendername-Feld.
- Hilfe-Center um drei neue Abschnitte (Bankimport, Festschreibung, Spendenquittung) erweitert.

### Behoben (Review kassenbuch_master_pro.html)

**Kritisch:**
1. Zweckgebunden-Logik: Ausgaben konnten zweckgebundene Mittel bisher nur über eine Textsuche nach „jugend" im Verwendungszweck reduzieren. Jetzt: explizite Checkbox „verwendet zweckgebundene Mittel" bei Ausgaben, analog zur Einnahmen-Checkbox.
2. Negativsaldo-Prüfung griff nur bei neuen Buchungen, nicht beim Bearbeiten bestehender Buchungen. Jetzt: Simulation der gesamten Buchungsliste vor jedem Speichern (neu und Edit).
3. Betrag-Validierung: `min="0.01"` im Formular sowie serverseitige (clientseitige) Prüfung auf Betrag > 0 und nicht-leeren Verwendungszweck.
4. Instabile ID-Vergabe: IDs wurden bei jedem Rendering per Array-Index neu vergeben, die Bearbeiten/Löschen-Sperre galt pauschal für Index 0. Jetzt: fortlaufender, stabiler `nextId`-Zähler sowie explizites `locked`-Flag statt Index-Prüfung.
5. XSS-Lücke: Beschreibung, Kategoriename und Beleg-Link wurden ungefiltert per `innerHTML` eingefügt. Jetzt: `escapeHtml()` für alle dynamischen Werte.

**Wichtig:**
6. CSV-Export nutzte Punkt als Dezimaltrennzeichen bei Semikolon-Trennung (Excel-DE-Inkompatibilität). Jetzt: deutsches Komma, Anführungszeichen-Escaping, UTF-8-BOM.
7. `localStorage.setItem` ohne Fehlerbehandlung — bei vollem Speicher brach `updateDashboard()` komplett ab. Jetzt: try/catch mit Warnhinweis statt Totalausfall.
8. Auto-Backup-Zähler (`bookings.length - 1`) verschob sich nach Löschungen und löste Backups zur falschen Zeit aus. Jetzt: persistenter, nur bei Neuanlage hochgezählter Zähler.
9. Begriffsverwechslung „Zweckbetrieb" (steuerliche Sphäre, § 65 AO) vs. „zweckgebunden" (Spendenrecht, § 62 AO): Formularlabel passt sich jetzt an Einnahme/Ausgabe an, Hilfe-Abschnitt erklärt den Unterschied.

**Kleinere Punkte:**
10. Tabellenspalte „Bestand (Bar)" zeigte bei Bank-Buchungen fälschlich den Barkassenstand. Jetzt: „Saldo (Konto)" mit korrektem Kontostand je Buchung.
11. Tabelle wurde nicht nach Datum sortiert. Jetzt: chronologische Sortierung vor der Anzeige (Vortrag bleibt fix oben).
12. Zwei gleichzeitige Auto-Downloads (Backup + Monatssicherung) konnten vom Browser blockiert werden. Jetzt: zeitlich entzerrt (400 ms Verzögerung).
13. Import prüfte die Struktur der Backup-Datei nicht. Jetzt: Validierung jedes Datensatzes (Pflichtfelder, Typen) vor Übernahme, Abbruch bei ungültigen Einträgen.

## [0.1.0] — Ausgangsversion

- Erste Version „Pétanque Kassenbuch — Master Pro": Barkasse/Bankkonto, Sphären-Trennung, Kassensturz-Rechner, Schnellwahltasten, Jahresabschluss-Druck, JSON-Backup, CSV-Export, Hilfe-Center.

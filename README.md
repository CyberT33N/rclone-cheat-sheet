# rclone-cheat-sheet


# Install
- https://rclone.org/install/

## Ubuntu
```shell
sudo -v ; curl https://rclone.org/install.sh | sudo bash
```










<br><br>
<br><br>
___
<br><br>
<br><br>



# docs
- https://rclone.org/docs/

















<br><br>
<br><br>
___
<br><br>
<br><br>



# Cloud Storage

<details><summary>Click to expand..</summary>


# Proton Drive
- https://rclone.org/protondrive/


## Create Remore Config
- The remote config file is located here `sudo gedit ~/.config/rclone/rclone.conf`

<br><br>

### Non-Interactive
```bash
#!/bin/bash

# Variablen definieren
USERNAME="xxxxxxxxxxx@protonmail.com"
PASSWORD="xxxxxxxxxxxxxxx"
MAILBOX_PASSWORD="xxxxxxxxxxxxxxxxxx"
TWO_FA="914892"
DESCRIPTION="Meine ProtonDrive Remote"

# Rclone Konfiguration erstellen
rclone config create --obscure proton protondrive \
    username="$USERNAME" \
    password="$PASSWORD" \
    mailbox_password="$MAILBOX_PASSWORD" \
    2fa="$TWO_FA" \
    replace_existing_draft=true \
    description="$DESCRIPTION"
```
- **Make sure that you execute the script with an valid 2FA code and then run `rclone lsd proton:` to auth**


<br><br>

### Interactive
```shell
rclone config

# Choose n) New remote

# set as name `remote`

# Choose number for Proton Drive - 43 / Proton Drive

# Enter username

# Choose y) Yes type in my own password

# Enter 2fa of your authenticator app

# Select y at Edit advanced config?

# Select y if you choosed a second layer password

# At encoding rpess enter for default

# Press again enter as default for file size

# Press again enter as default for app version

# Choose true for replace_existing_draft

# Choose true for enable_caching

# Set description for your remote

# Then choose no if it ask again for Edit advanced config?
```






<br><br>
<br><br>

# FAQ

## WARN RESTY 422 POST https://mail.proton.me/api/auth/v4: For security reasons, please complete CAPTCHA. If you can't pass it, please try updating your app or contact us here: https://proton.me/support/appeal-abuse (Code=9001, Status=422), Attempt 1
2025/02/17 13:07:41.224555 ERROR RESTY 422 POST https://mail.proton.me/api/auth/v4: For security reasons, please complete CAPTCHA. I
- Open `https://mail.proton.me` in new incognito browser window, sign-in and solve captcha. Then your host IP will be marked as captcha solved and you can continue

<br><br>

## WARN RESTY 422 POST https://mail.proton.me/api/auth/v4/2fa: Incorrect login credentials. Please try again. (Code=8002, Status=422), Attempt 1
- When youc reate your config and you enter your 2FA then it will will change in meantime so you must set the 2fa via you cli command e.g. in this list file command:
```shell
rclone ls remoteNameHere: --protondrive-2fa=123456
```

  
</details>

























<br><br>
<br><br>
___
<br><br>
<br><br>

# CLI


<details><summary>Click to expand..</summary>



## Rclone CLI Befehle und Optionen

Diese Tabelle listet die wichtigsten Rclone CLI Befehle und Optionen auf, basierend auf der von dir bereitgestellten Dokumentation.


<details><summary>Click to expand..</summary>

### Befehle (Subcommands)

| Befehl         | Beschreibung                                                                                                                               |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------|
| `rclone config`  | Startet eine interaktive Konfigurations-Session.                                                                                          |
| `rclone copy`    | Kopiert Dateien von der Quelle zum Ziel und überspringt bereits kopierte Dateien.                                                                |
| `rclone sync`    | Synchronisiert Quelle und Ziel, sodass das Ziel identisch mit der Quelle ist.                                                              |
| `rclone bisync`  | Bidirektionale Synchronisation zwischen zwei Pfaden.                                                                                                 |
| `rclone move`    | Verschiebt Dateien von der Quelle zum Ziel.                                                                                                     |
| `rclone delete`  | Entfernt den Inhalt eines Pfads.                                                                                                             |
| `rclone purge`   | Entfernt den Pfad und alle seine Inhalte.                                                                                                 |
| `rclone mkdir`   | Erstellt den Pfad, falls er noch nicht existiert.                                                                                                |
| `rclone rmdir`   | Entfernt den Pfad.                                                                                                                          |
| `rclone rmdirs`  | Entfernt leere Verzeichnisse unter dem Pfad.                                                                                                |
| `rclone check`   | Überprüft, ob die Dateien in der Quelle und im Ziel übereinstimmen.                                                                             |
| `rclone ls`      | Listet Objekte im Pfad mit Größe und Pfad auf.                                                                                                   |
| `rclone lsd`     | Listet Verzeichnisse/Container/Buckets im Pfad auf.                                                                                            |
| `rclone lsl`     | Listet Objekte im Pfad mit Größe, Änderungszeit und Pfad auf.                                                                                  |
| `rclone md5sum`  | Erstellt eine md5sum-Datei für Objekte im Pfad.                                                                                               |
| `rclone sha1sum` | Erstellt eine sha1sum-Datei für Objekte im Pfad.                                                                                              |
| `rclone size`    | Gibt die Gesamtgröße und Anzahl der Objekte in remote:path zurück.                                                                             |
| `rclone version` | Zeigt die Rclone-Versionsnummer an.                                                                                                         |
| `rclone cleanup` | Bereinigt das Remote, falls möglich.                                                                                                          |
| `rclone dedupe`  | Findet doppelte Dateien und löscht/benennt sie um.                                                                                              |
| `rclone authorize`| Remote-Authorisierung.                                                                                                                                |
| `rclone cat`     | Gibt den Inhalt einer Datei aus.                                                                                                               |
| `rclone copyto`  | Kopiert eine Datei von der Quelle zum Ziel (analog copy, aber für einzelne Dateien).                                                        |
| `rclone completion`| Gibt Shell-Completion-Skripte für Rclone aus.                                                                                              |
| `rclone gendocs` | Erzeugt Markdown-Dokumente für Rclone.                                                                                                        |
| `rclone listremotes`| Listet alle Remotes in der Konfigurationsdatei auf.                                                                                          |
| `rclone mount`   | Mountet das Remote als Mountpoint.                                                                                                           |
| `rclone moveto`  | Verschiebt eine Datei oder ein Verzeichnis von der Quelle zum Ziel (analog move, aber für einzelne Dateien).                                  |
| `rclone obscure` | Verschleiert Passwörter in der rclone.conf.                                                                                                   |
| `rclone cryptcheck`| Überprüft die Integrität eines verschlüsselten Remotes.                                                                                       |
| `rclone about`   | Ruft Quoteninformationen vom Remote ab.                                                                                                        |

### Optionen

Diese Tabelle listet eine Auswahl der wichtigsten Rclone-Optionen auf.  Beachte, dass es noch viele weitere Optionen gibt, die hier nicht aufgeführt sind. Für eine vollständige Liste konsultiere die Rclone-Dokumentation.

| Option                      | Beschreibung                                                                                                                                                                                             |
|-----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `--backup-dir=DIR`          | Verschiebt Dateien, die überschrieben oder gelöscht würden, in dieses Verzeichnis.                                                                                                                         |
| `--bind string`             | Lokale Adresse für ausgehende Verbindungen.                                                                                                                                                               |
| `--bwlimit=BANDWIDTH_SPEC`    | Beschränkt die Bandbreite. Kann als einfache Bandbreite oder als Zeitplan angegeben werden.                                                                                                                |
| `--bwlimit-file=BANDWIDTH_SPEC` | Beschränkt die Bandbreite pro Datei.                                                                                                                                                                    |
| `--buffer-size=SIZE`          | Größe des Puffers für schnellere Dateiübertragungen.                                                                                                                                                     |
| `--cache-dir=DIR`           | Verzeichnis für Rclone-Caching.                                                                                                                                                                           |
| `--check-first`             | Führt alle Prüfungen durch, bevor Übertragungen gestartet werden.                                                                                                                                           |
| `--checkers=N`              | Anzahl paralleler Dateichecker.                                                                                                                                                                          |
| `-c, --checksum`            | Verwendet die Prüfsumme zur Bestimmung der Gleichheit von Dateien.                                                                                                                                       |
| `--color WHEN`              | Legt fest, wann Farben in der Ausgabe verwendet werden. `AUTO`, `NEVER`, oder `ALWAYS`.                                                                                                                    |
| `--compare-dest=DIR`        | Vergleicht Dateien in DIR zusätzlich zum Ziel.                                                                                                                                                           |
| `--config=CONFIG_FILE`      | Pfad zur Rclone-Konfigurationsdatei.                                                                                                                                                                     |
| `--contimeout=TIME`         | Verbindungstimeout.                                                                                                                                                                                     |
| `--copy-dest=DIR`           | Verwendet Server-Side-Copy von DIR zum Ziel.                                                                                                                                                            |
| `--dedupe-mode MODE`        | Modus für den `dedupe`-Befehl.                                                                                                                                                                            |
| `--default-time TIME`       | Standardzeit, wenn eine Datei oder ein Verzeichnis keine Änderungszeit hat.                                                                                                                                |
| `--disable FEATURE,FEATURE,...` | Deaktiviert eine Liste von optionalen Features.                                                                                                                                                            |
| `--dscp VALUE`           | Specify a DSCP value or name to use in connections.                                                                                                                            |
| `-n, --dry-run`             | Testlauf ohne Änderungen.                                                                                                                                                                               |
| `--error-on-no-transfer`    | Rclone gibt einen Fehler zurück, wenn keine Dateien übertragen wurden.                                                                                                                                       |
| `--fix-case`                | Korrigiert die Groß-/Kleinschreibung von Dateinamen bei der Synchronisierung.                                                                                                                             |
| `--fs-cache-expire-duration=TIME` | Dauer, für die Remotes im "fs cache" zwischengespeichert werden.                                                                                                                                          |
| `--fs-cache-expire-interval=TIME` | Wie oft Rclone auf zwischengespeicherte Remotes überprüft, die ablaufen.                                                                                                                                      |
| `--header`                  | Fügt einen HTTP-Header für alle Transaktionen hinzu.                                                                                                                                                        |
| `--human-readable`          | Gibt Größen und Zählungen in einem für Menschen lesbaren Format aus.                                                                                                                                         |
| `--ignore-case-sync`       | Ignoriert die Groß-/Kleinschreibung bei Dateinamen bei der Synchronisierung.                                                                                                                                   |
| `--ignore-checksum`         | Ignoriert Prüfsummenfehler.                                                                                                                                                                                |
| `--ignore-existing`         | Überspringt alle Dateien, die bereits im Ziel vorhanden sind.                                                                                                                                               |
| `--ignore-size`             | Ignoriert die Dateigröße beim Vergleich von Dateien.                                                                                                                                                       |
| `-I, --ignore-times`        | Lädt alle Dateien hoch, unabhängig vom Status der Dateien im Ziel.                                                                                                                                         |
| `--immutable`               | Behandelt Dateien als unveränderlich und verhindert Änderungen.                                                                                                                                              |
| `--inplace`               | Upload directly to the final name without creating a temporary partial file (increases performance)                                                                                                                    |
| `-i, --interactive`         | Bestätigung vor destruktiven Operationen.                                                                                                                                                                    |
| `--links / -l`              | Kopiert symbolische Links als Textdateien.                                                                                                                                                                  |
| `--log-file=FILE`           | Schreibt alle Rclone-Ausgaben in eine Datei.                                                                                                                                                               |
| `--log-level LEVEL`         | Log-Level für Rclone.                                                                                                                                                                                       |
| `--low-level-retries NUMBER`| Anzahl der Low-Level-Retries.                                                                                                                                                                            |
| `--max-backlog=N`          | Maximale Anzahl von Dateien, die auf Überprüfung oder Übertragung warten.                                                                                                                                      |
| `--max-delete=N`            | Maximale Anzahl von Dateien, die gelöscht werden dürfen.                                                                                                                                                     |
| `--max-depth=N`             | Maximale Rekursionstiefe.                                                                                                                                                                                   |
| `-M, --metadata`            | Kopiert Metadaten von der Quelle zum Ziel.                                                                                                                                                                   |
| `--modify-window=TIME`      | Maximal zulässige Zeitdifferenz für Dateimodifikationszeiten.                                                                                                                                                |
| `--no-check-dest`           | Vermeidet die Überprüfung des Ziels beim Kopieren von Dateien.                                                                                                                                          |
| `--no-traverse`             | Vermeidet das Traversieren des Ziel-Dateisystems beim Kopieren.                                                                                                                                          |
| `-P, --progress`            | Zeigt den Fortschritt in einem statischen Block im Terminal an.                                                                                                                                             |
| `-q, --quiet`               | Beschränkt die Ausgabe auf Fehlermeldungen.                                                                                                                                                                 |
| `--retries int`             | Anzahl der Wiederholungen bei Fehlern.                                                                                                                                                                     |
| `--size-only`               | Überprüft nur die Größe der Dateien beim Vergleich.                                                                                                                                                       |
| `--stats=TIME`              | Zeigt Datenübertragungsstatistiken in regelmäßigen Abständen an.                                                                                                                                             |
| `--stats-one-line`          | Kondensiert die Statistiken in eine einzige Zeile.                                                                                                                                                          |
| `--suffix=SUFFIX`           | Fügt ein Suffix zu Dateien hinzu, die überschrieben oder gelöscht würden.                                                                                                                                    |
| `--syslog`                  | Sendet alle Log-Ausgaben an Syslog.                                                                                                                                                                        |
| `--temp-dir=DIR`            | Verzeichnis für temporäre Dateien.                                                                                                                                                                          |
| `--timeout=TIME`            | IO-Idle-Timeout.                                                                                                                                                                                            |
| `--transfers=N`             | Anzahl paralleler Dateiübertragungen.                                                                                                                                                                       |
| `-u, --update`              | Überspringt Dateien, die im Ziel neuer sind.                                                                                                                                                                 |
| `-v, -vv, --verbose`        | Verbose Ausgabe (-v) oder sehr verbose Ausgabe (-vv).                                                                                                                                                         |
| `-V, --version`             | Zeigt die Versionsnummer an.                                                                                                                                                                                |
| `--multi-thread-cutoff`  | Verwende multithreaded Übertragungen für Dateien über dieser Größe (z.B. 256M). |
| `--multi-thread-streams` | Anzahl der Streams für multithreaded Übertragungen (Standard 4). |
| `--fast-list`    | Benutze die schnellere ListR Funktion wenn möglich. Verwende dies wenn du für API Aufrufe bezahlst. |
| `--track-renames`|  Verfolge umbenannte Dateien (experimental). Dies kann die Effizienz von `sync` erhöhen, wenn viele Dateien umbenannt wurden.|
|`--delete-before`, `--delete-during`, `--delete-after`|  Wann Dateien auf dem Ziel gelöscht werden sollen. (`before`, `during`, `after`). Die sicherste Option ist `after`.|
| `--rc`     | Aktiviere das Remote Control Interface |

**Wichtige Hinweise:**

*   **Dokumentation:** Diese Tabelle basiert auf dem bereitgestellten Text. Für detailliertere Informationen zu jeder Option und für alle verfügbaren Optionen konsultiere bitte die offizielle Rclone-Dokumentation.
*   **Optionen können sich ändern:** Die verfügbaren Optionen und ihre Funktionsweise können sich zwischen Rclone-Versionen ändern.  Achte darauf, die Dokumentation für deine verwendete Version zu konsultieren.

</details>














<br><br>
<br><br>

# config
- https://rclone.org/commands/rclone_config/


<details><summary>Click to expand..</summary>



# Rclone Config Befehle Übersicht

| Befehl                           | Beschreibung |
|----------------------------------|-------------|
| `rclone`                        | Zeigt Hilfe für Rclone-Befehle, Flags und Backends. |
| `rclone config create`          | Erstellt einen neuen Remote mit Name, Typ und Optionen. |
| `rclone config delete`          | Löscht einen bestehenden Remote. |
| `rclone config disconnect`      | Trennt den Benutzer vom Remote. |
| `rclone config dump`            | Gibt die Konfigurationsdatei als JSON aus. |
| `rclone config edit`            | Startet eine interaktive Konfigurationssitzung. |
| `rclone config encryption`      | Setzt, entfernt und überprüft die Verschlüsselung der Konfigurationsdatei. |
| `rclone config file`            | Zeigt den Pfad der verwendeten Konfigurationsdatei an. |
| `rclone config password`        | Aktualisiert das Passwort in einem bestehenden Remote. |
| `rclone config paths`           | Zeigt die verwendeten Pfade für Konfiguration, Cache, Temp etc. an. |
| `rclone config providers`       | Listet alle Anbieter und Optionen im JSON-Format auf. |
| `rclone config reconnect`       | Authentifiziert den Benutzer mit dem Remote erneut. |
| `rclone config redacted`        | Gibt die redigierte (entschlüsselte) Konfigurationsdatei aus oder die redigierte Konfiguration eines einzelnen Remotes. |
| `rclone config show`            | Gibt die (entschlüsselte) Konfigurationsdatei aus oder die Konfiguration eines einzelnen Remotes. |
| `rclone config touch`           | Stellt sicher, dass die Konfigurationsdatei existiert. |
| `rclone config update`          | Aktualisiert Optionen in einem bestehenden Remote. |
| `rclone config userinfo`        | Zeigt Informationen über den angemeldeten Benutzer des Remotes an. |


    
</details>












  
</details>



# Life OS

Privates Alltags-Tracking. Die App läuft getrennt von Home Assistant in einem eigenen Container und ist **nur über dein Tailscale-Netz** erreichbar, unter einer eigenen HTTPS-Adresse wie `https://lifeos.<dein-tailnet>.ts.net`.

## Einrichtung

1. In der Tailscale-Verwaltung unter **DNS** sowohl **MagicDNS** als auch **HTTPS Certificates** aktivieren.
2. Unter **Settings → Keys** einen **Auth key** erzeugen. Die Standardeinstellungen passen.
3. Den Schlüssel hier unter **Konfiguration** bei `tailscale_auth_key` eintragen und die App starten.
4. Im **Protokoll** erscheint die Adresse: `Life OS is available at https://…`.
5. In der Tailscale-Verwaltung unter **Machines** beim neuen Gerät `lifeos` über das Menü **Disable key expiry** wählen. Sonst meldet sich die App nach einigen Monaten ab.

Der Auth-Key wird nur für die allererste Anmeldung gebraucht. Danach kannst du ihn aus der Konfiguration löschen.

## Optionen

| Option               | Bedeutung                                                            |
| -------------------- | -------------------------------------------------------------------- |
| `tailscale_auth_key` | Einmaliger Schlüssel für die erste Anmeldung im Tailnet              |
| `tailscale_hostname` | Gerätename im Tailnet und damit Teil der Adresse (Standard `lifeos`) |
| `log_level`          | Ausführlichkeit des Protokolls                                       |

## Daten und Backups

- Alle Daten liegen im App-Ordner `/data` und sind Teil der Home-Assistant-Backups. Während eines Backups wird die App kurz gestoppt.
- Zusätzlich gibt es in Life OS unter **Einstellungen → Datensicherung** einen Backup-Download. Bewahre die Datei außerhalb des Raspberry Pi auf.

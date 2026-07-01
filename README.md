# Social-Engineering-Project
## Beschreibung
Dieses Projekt dokumentiert die Simulation eines Phishing-Angriffs unter Verwendung des Social Engineering Toolkits. Das primäre Ziel besteht darin, die Vorgehensweise eines Angreifers praxisnah zu simulieren und die damit verbundenen Risiken zu veranschaulichen. Basierend darauf sollen geeignete Gegenmaßnahmen zur Erkennung, Prävention und Sensibilisierung gegenüber Social-Engineering-Angriffen entwickelt werden.

**Der Fokus liegt hierbei auf:**
- Erstellung einer Phishing‑E-Mail
- Aufbau einer Fake‑Login‑Seite unter Zuhilfenahme des Social Engineering Toolkits
- Abgreifen von Zugangsdaten
- Analyse der Auswirkungen, sowie der Ableitung von Sicherheitsmaßnahmen

## Vorbereitung
### Testumgebung
Für die Simulation wurde eine kontrollierte Umgebung eingerichtet mit:

    Hardware: Raspberry Pi 4
    Betriebssystem: Kali Linux
    Tools: Social Engineering Toolkit (SET) -> ist bereits auf Kali Linux vorinstalliert

### E-Mail-Adressen
**Angreifer‑Setup:**
- Erstellung eines Gmail‑Kontos mit einer temporären Telefonnummer
- Generierung eines App‑Passworts für den SMTP‑Zugriff
- Wahl eines vertrauenswürdigen Absendernamens (z. B. „Support Google“)

**Opfer-Setup:**
- ProtonMail‑Konto
      
### Python Skript für den E-Mail-Versand
Für den Versand der E-Mail wurde ein Python-Skript erstellt, welches über den Gmail-SMTP-Server E-Mails versendet und einen HTML‑basierten Nachrichtentext enthält. 
Das Skript übernimmt folgende Aufgaben:
- Aufbau einer TLS‑gesicherten Verbindung zu smtp.gmail.com
- Authentifizierung über das zuvor erstellte App‑Passwort
- Erstellung einer MIME‑Nachricht mit HTML‑Inhalt
- Setzen eines vertrauenserweckenden Absendernamens („Support Google“)
- Versand der Phishing-Nachricht

## Durchführung
Für das Einrichten der Phishing-Seite wird das Social Engineering Toolkit verwendet. Nach dem Öffnen im Terminal erscheint diese Begrüßungsseite, bei der zuerst die zweite Option mit "Website Attack Vectors" ausgewählt wird: 

![SET Bild1](Bilder/1.png)

Anschließend bietet die dritte Option mit "Credential Harvester Attack Method" die Möglichkeit zur Erstellung der Phishing-Seite:

![SET Bild2](Bilder/2.png)

Nun existiert die Wahl zwischen Web Templates, Site Cloner und Custom Import. Weil Google schon als Template vordefiniert ist, fällt die Wahl auf 1:

![SET Bild3](Bilder/3.png)

Jetzt kann Google ausgewählt werden:

![SET Bild4](Bilder/4.png)

Kali Linux startet daraufhin den Webserver auf Port 80, wodurch die gefälschte Seite nun unter unserer IP-Adresse zu finden ist. In der Realität nutzen Angreifer dafür Domains, die der originalen Website ähnlich sind. Mit dem Tool dnstwist lassen sich solche Domänennamen einfach finden. Zudem zeigt es an, welche davon bereits in Verwendung sind und welche noch verfügbar wären.

![SET Bild5](Bilder/5.png)

Diese Domäne wird im bereits erstellten HTML-Skript als Link hinter dem Button „Jetzt anmelden“ hinterlegt und das Python-Skript ausgeführt. 




# 🛠️ Personal Tool Hub & Web-Dashboard

Ein zentrales, webbasiertes Dashboard und Multi-Tool-Launcher auf Basis von **GitHub Pages**. 
Das Projekt dient als zentrale Anlaufstelle für verschiedene eigenständige Mini-Anwendungen, 
Rechner und Alltagshelfer, die über eine moderne, einheitliche Kachel-Oberfläche (Single-Page-Shell) 
gestartet und verwaltet werden.

---

## 🎯 Projektziel & Idee

Statt viele einzelne Webseiten, Lesezeichen oder lokale Skripte getrennt zu verwalten, 
bündelt dieses Dashboard alle Werkzeuge unter einer einzigen Webadresse. 
Die Oberfläche verhält sich dabei wie ein App-Launcher: Jede Anwendung öffnet sich direkt im Hauptfenster, 
während eine feste Navigationsleiste jederzeit den sofortigen Rücksprung auf die Kachel-Übersicht ermöglicht.

---

## ⚙️ Funktionsweise & Architektur

Das System ist vollständig statisch aufgebaut und benötigt keinen eigenen Server oder Datenbank-Backend:

* **Zentrale Steuerung (`index.html`):** Bildet das Grundgerüst der Anwendung mit einer dauerhaft sichtbaren Kopfzeile (`Header`) und einem responsiven Kachel-Raster (`CSS Grid`).
* **Vollautomatische Tool-Erkennung (GitHub-API):** Beim Laden der Startseite fragt ein integriertes JavaScript-Modul über die öffentliche GitHub-API automatisch den Inhalt des Verzeichnisses `tools/` ab. Jede dort abgelegte `.html`-Datei wird ohne manuelles Eingreifen als eigene Kachel inkl. formatiertem Titel auf dem Dashboard dargestellt.
* **Nahtlose Einbettung (`<iframe>`-Container):** Wird eine Kachel angeklickt, blendet sich die Übersicht aus und die jeweilige Anwendung wird direkt im selben Browserfenster geladen. Über den Button **„☰ Kacheln“** lässt sich jedes aktive Werkzeug sofort schließen, um zur Startansicht zurückzukehren.
* **Modulares Design:** Da jedes Tool als völlig eigenständige HTML/CSS/JS-Datei im Unterordner `tools/` existiert, bleiben alle Anwendungen sauber voneinander getrennt und beeinflussen sich gegenseitig nicht.

---

## 📂 Projektstruktur

```text
/Dashboard
├── index.html          # Hauptseite (Launcher, Navigation & automatische API-Abfrage)
├── README.md           # Projektdokumentation
└── tools/              # Verzeichnis für alle eigenständigen Mini-Anwendungen (*.html)

# Chatbot Web Addon

Ein einfach zu integrierender Chatbot für Websites, der maschinelles Lernen verwendet und Fragen und Antworten aus einer CSV-Datei lädt. Der Chatbot speichert unbekannte Fragen und ermöglicht eine kontinuierliche Verbesserung durch das Nachtrainieren des Modells.

## Funktionen

- **Integration auf jeder Website**: Einfacher HTML/CSS/JS-Code zur Einbindung des Chatbots auf jeder Webseite.
- **CSV-Upload**: Admin-Oberfläche zum Hochladen von Fragen und Antworten als CSV-Datei.
- **Maschinelles Lernen**: Der Chatbot nutzt ein Machine-Learning-Modell, um Antworten vorherzusagen.
- **Selbstlernend**: Unbekannte Fragen werden gespeichert und können später zum Training verwendet werden.
- **Datenbank-Speicherung**: Alle Daten werden in einer SQLite-Datenbank gespeichert.

## Installation

### Voraussetzungen

- Python 3.x
- Virtualenv (optional, aber empfohlen)

### Schritte

1. **Repository klonen:**

```sh
git clone https://github.com/dein-username/chatbot.git
cd chatbot
```

2. **Virtuelle Umgebung erstellen und aktivieren:**

  ```sh
  python -m venv venv
  source venv/bin/activate  # Auf Windows: venv\Scripts\activate
  ```

3. **Abhängigkeiten installieren:**

  ```sh
  pip install -r requirements.txt
  ```

4. **Datenbank initialisieren:**

  ```sh
  flask db init
  flask db migrate -m "Initial migration."
  flask db upgrade
  ```

5. **Flask-Anwendung starten:**

  ```sh
  python run.py
  ```

## Nutzung

### Admin-Bereich

1. Öffnen Sie den Admin-Bereich unter http://localhost:5000/admin.
2. Laden Sie eine CSV-Datei hoch, die Fragen und Antworten enthält. Beispielstruktur der CSV-Datei:

  ```sh
  Frage,Antwort
  Wie sind Ihre Öffnungszeiten?,Unsere Öffnungszeiten sind Montag bis Freitag von 9 bis 18 Uhr.
  Wo befinden Sie sich?,Wir befinden uns in der Musterstraße 1, 12345 Musterstadt.
  Wie kann ich Sie kontaktieren?,Sie können uns per E-Mail unter kontakt@musterfirma.de oder telefonisch unter 01234 567890 erreichen.
  ```
3. Nach dem Hochladen wird das Modell automatisch mit den neuen Daten trainiert.

### Einbindung auf Webseiten

Fügen Sie den folgenden HTML-Code zu der Webseite hinzu, um den Chatbot-Button anzuzeigen:

```html
<div id="chatbot-button" onclick="toggleChatbox()">Chatbot</div>
<div id="chatbox">
    <header>Chatbot</header>
    <div class="messages"></div>
    <input type="text" id="user-input" placeholder="Ihre Frage..."/>
    <button onclick="sendMessage()">Senden</button>
</div>
<script src="URL_TO_YOUR_SERVER/static/js/main.js"></script>
<link rel="stylesheet" type="text/css" href="URL_TO_YOUR_SERVER/static/css/styles.css">
```

Ersetzen Sie `URL_TO_YOUR_SERVER` durch die URL, auf der Ihr Flask-Server läuft.
   
### Training des Modells

Um das Modell manuell neu zu trainieren, nutzen Sie den Admin-Bereich oder senden Sie eine POST-Anfrage an `/retrain`:

```sh
curl -X POST http://localhost:5000/retrain
```

## Projektstruktur

```arduino
chatbot/
├── app/
│   ├── __init__.py
│   ├── routes.py
│   ├── model.py
│   ├── static/
│   │   ├── css/
│   │   │   └── styles.css
│   │   └── js/
│   │       └── main.js
│   ├── templates/
│   │   ├── index.html
│   │   └── admin.html
├── instance/
│   └── chatbot.sqlite
├── requirements.txt
├── run.py
├── config.py
├── README.md
```

### Beitragende

- Elia Albanese - Softwareengineer - EliaAlb


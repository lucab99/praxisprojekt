# Repository Dokumentation

Autoren: \
Tom Hinzmann \
Jasmin Čapka

Stand: 04.03.2021

## Repo Struktur

Dieses Repository umfasst Frontend und Backend Komponenten und wird gemeinsam im Rahmen des Google Cloud Build deployed.
Zugriff auf die Dienste erfolgt durch eine Flask REST API, die sowohl statische Inhalte als auch Berechnungen,
Datenstrukturen und Metadaten in Form von JSON Objekten liefert. Die Architektur orientiert sich damit an dem Aufbau einer
Python Django App, bleibt dabei aber uneingeschränkt flexibel im Aufbau.

```
- .github/
  - CODEOWNERS
  - pull_request_template.md
- api/
  - endpoints.py
```
    
In dem `api/` Verzeichnis liegen die Files, die der Flask App angehören, die wiederum durch die `main.py` gestartet wird.
In der `endpoints.py` Datei werden die Endpoints der Flask REST API definiert, die die Schnittstelle zum Frontend bilden.
Dort sollen die Anfragen angenommen und selektiv an die "Task Engine" `core.py`, die jegliche Logik enthält und Datenflüsse
managed.

```
- processing/
  - placeholder.txt
```

Der `processing/` folder soll alle Funktionalitäten zur Berechnung von Metriken und Aggregation von Werten einzelner
Prozesskomponenten bereitstellen. Hier erfolgt die Ergebnisermittlung.

```
- database/
  - export/
    - placeholder.txt
  - handler/
    - placeholder.txt
  - queries.json
```

Der `database/` Ordner soll alle Datenbank-bezogenen Inhalte und Funktionen enthalten, darunter die Queries (abhängig
davon, ob wir mit einem Object Mapper arbeiten können) und das Database Handler Modul, das auf den Neo4j Driver aufbaut
und die Backend-seitige Schnittstelle zur Datenbank darstellt.

```
- docu/
  - Coding Richtlinie.md
  - IntelliJ.md
  - Repository.md
```

Das `docu/` Verzeichnis soll alle wichtigen Projektdokumentationen, Leitfäden und Guidelines enthalten, die im Repository liegen.

```
- frontend/
  - static/
    - content/
      - placeholder.txt
    - css/
      - placeholder.txt
    - images/
      - placeholder.txt
    - js/
      - placeholder.txt
  - templates
    - placeholder.txt
```

Der `frontend/` folder soll alle Inhalte für das Frontend enthalten. Im `static/` Ordner werden daher grundsätzlich alle
statischen Inhalte hinterlegt. Der Unterordner `content/` soll daher ein JSON file enthalten, worin alle Texte spezifiziert
werden, um die Templates zu entlasten und Redundanzen vermeiden zu können. Der Unterordner `css/` enthält seinem Namen
entsprechend die CSS files, in denen alle Styles definiert werden - dies dient ebenfalls der Entlastung der Templates,
in denen kein Inline-CSS verwendet werden soll. Im `images/` Unterordner sollen Bilder und Icons abgelegt werden, die
im Frontend eingesetzt werden. Hierbei ist auf die Dateigröße der Bilder zu achten, die eine bestimmte Größe nicht
überschreiten sollen. Der Unterordner `js/` enthält JavaScript Funktionen, die individuell in die Templates importiert
werden können.\
Der Ordner `templates/` soll alle Views enthalten, also eine Sammlung an HTML Templates, die an bestimmte Endpoints
angeknüpft werden.

```
- .gcloudignore
- .gitignore
- app.yaml
- cloudbuild.yaml
- core.py
```

Die `core.py` ist die "Task Engine", die jegliche Logik enthält und Datenflüsse managed. Von hier werden alle Datenbank
Funktionalitäten, alle Berechnungsfunktionen, alle Helper angesprochen und bedient.

```
- main.py
```

Die `main.py` enthält die Flask App und startet damit die Software. Front- und Backend sind nun über die API erreichbar.

```
- README.md
```

Die `README.md` enthält wichtige Informationen zum Aufsetzen des Projektes und zum lokalen Testing.

```
- requirements.txt
```

Die `requirements.txt` enthält alle essentiellen Module, die im (virtuellen) Environment installiert werden müssen, um
das Projekt lokal zu testen.

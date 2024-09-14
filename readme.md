# Code zur Erstellung von synthetischen Überleitungsanträgen des Medizinischen Dienstes

## Einführung

Diese Notebooks helfen bei der Erstellung synthetischer Daten für den Überleitungsantrag des Medizinischen Dienstes zur Schnelleinstufung zwecks Pflegegrad. Die Software erzeugt aus vorhandenen Datensätzen in einer CSV-Tabelle neue synthetische Datensätze, die auf dem Muster der vorhandenen Daten basieren. Nach der Generierung dieser neuen Daten lassen sich diese mit einem zweiten Code automatisch aus der neuen CSV-Datei in eine PDF einfügen. Dies ermöglicht eine schnelle Erzeugung einer gewünschten Anzahl an PDF-Dateien mit fiktiven Daten. Der Zweck dieser Software ist es, datenschutzrechtlich problematische Daten zu vermeiden, wenn man Machine-Learning-Modelle oder Sprachmodelle mit diesen Daten trainieren möchte.

**Hinweis:** Alle hier verwendeten Daten sind frei erfunden. Jede Ähnlichkeit mit lebenden oder verstorbenen Personen ist rein zufällig.

## Data Augmentation

Data Augmentation ist ein legitimer Ansatz, um Machine Learning zu ermöglichen. Durch die Generierung synthetischer Daten können Datensätze erweitert werden, ohne auf reale und möglicherweise datenschutzrechtlich problematische Informationen zurückzugreifen. Dies ist besonders wichtig im medizinischen Bereich, wo der Schutz persönlicher Daten oberste Priorität hat. Mit synthetischen Daten können Machine-Learning-Modelle trainiert und validiert werden, ohne dass echte Patientendaten verwendet werden müssen.

## Voraussetzungen

- Python 3.10 oder höher
- `pandas` Bibliothek
- `pdfrw` Bibliothek
- `faker` Bibliothek
- `sdv` Bibliothek
- `numpy` und `scikit-learn` Bibliotheken (werden als Abhängigkeiten benötigt)

## Installation

1. **Klone dieses Repository:**

    ```bash
    git clone https://github.com/goldikolb/synthetische_ueberleitungsantraege.git
    cd uberleitbogen-synthese
    ```

2. **Installiere die benötigten Python-Pakete:**

    ```bash
    pip install pandas pdfrw faker sdv
    ```

    **Hinweis:** Falls bei der Installation von `sdv` Probleme auftreten oder zusätzliche Pakete benötigt werden, installiere diese wie folgt:

```bash
pip install numpy scikit-learn
```

3. **Stelle sicher, dass alle Pakete erfolgreich installiert wurden.**

## Verwendung

### Generieren synthetischer Daten

1. **Lade die CSV-Datei mit den vorhandenen Daten in den Ordner `csv_data`.** Achte darauf, dass die Datei korrekt formatiert ist und die benötigten Spalten enthält.

2. **Passe den `file_path` im Jupyter-Notebook `synthetic_data_creator.ipynb` an**, um auf deine CSV-Datei zu verweisen.

3. **Führe das Notebook aus**, um neue synthetische Daten zu generieren. Das Notebook verwendet die Bibliotheken `faker` und `sdv`, um realistische synthetische Datensätze zu erstellen, die auf den Mustern der vorhandenen Daten basieren.

4. **Die neuen Datensätze werden in der Datei `erweiterte_daten.csv` gespeichert.**

### Erstellen der neuen Gutachten

Die generierten synthetischen Daten können direkt verwendet oder bei Bedarf angepasst werden. Überprüfe die Daten, um sicherzustellen, dass sie den Anforderungen entsprechen. Insbesondere können die Diagnosen angepasst oder erweitert werden, um mehr Vielfalt zu bieten.

Falls du zusätzliche Diagnosen generieren möchtest, kannst du die `faker` Bibliothek erweitern oder eigene Listen von Diagnosen erstellen und in den Code integrieren.

**Beispiel für die Erweiterung der Diagnosen:**

Du kannst im Code die Liste der möglichen Diagnosen erweitern:

```python
pflege_diagnosen = [
    'Demenz', 'Schlaganfall', 'Fraktur', 'Herzinsuffizienz',
    'COPD', 'Parkinson', 'Multiple Sklerose', 'Arthrose',
    'Depression', 'Diabetes mellitus', 'Hypertonie', 'Chronische Schmerzen'
]
```

### Erstellen von PDF-Dateien

1. **Stelle sicher, dass die Vorlage `Antrag_ueberleitung.pdf` im Ordner `pdf` vorhanden ist.**

2. **Führe das Jupyter-Notebook `uberleitung_pdf_creator.ipynb` aus**, um die PDF-Dateien zu erstellen. Das Notebook liest die synthetischen Daten aus der CSV-Datei und füllt die PDF-Vorlage entsprechend aus.

3. **Die erstellten PDF-Dateien werden im Ordner `output` gespeichert.**

4. **Zusätzlich wird eine Tabelle (CSV-Datei) erstellt**, die den Formularen (Dateinamen) das Ergebnis zuordnet.

## Erklärvideo

[![Watch the video](http://img.youtube.com/vi/L3S8_Gj5t0M/mqdefault.jpg)](http://www.youtube.com/watch?feature=player_embedded&v=L3S8_Gj5t0M)

## Autor

Christian Kolb

## Kontakt

Wenn Sie Fragen haben oder einen Beitrag leisten möchten, zögern Sie nicht, uns über unsere Webseite zu kontaktieren: [pflege-ai.de](https://pflege-ai.de/).

[![Website](https://img.shields.io/badge/Pflege--AI-Webseite-%230f0122?style=flat&logo=Web&logoColor=ff8154)](https://pflege-ai.de/)

## Folgen Sie mir auf Social Media

[![Threads](https://img.shields.io/badge/Threads-Follow%20me-blue?style=flat&logo=Thread&logoColor=white)](https://www.threads.net/@pflege_ki)

[![Twitter Follow](https://img.shields.io/twitter/follow/ai_fuerth?style=social)](https://twitter.com/ai_fuerth)

[![Instagram](https://img.shields.io/badge/Instagram-Follow%20@pflege__ki-blue?style=flat&logo=instagram&logoColor=white)](https://www.instagram.com/pflege_ki/)

---

### **Zusätzliche Hinweise**

- **Anpassung des Codes:** Stelle sicher, dass alle Pfade und Dateinamen im Code korrekt auf deine lokale Umgebung angepasst sind.

- **Überprüfung der Daten:** Nach der Generierung der synthetischen Daten ist es empfehlenswert, die Daten zu überprüfen und gegebenenfalls anzupassen, um sicherzustellen, dass sie den realistischen Szenarien entsprechen.

- **Erweiterung der Funktionen:** Du kannst den Code weiter anpassen und erweitern, um zusätzliche Features hinzuzufügen, wie z.B. die Generierung spezifischer Diagnosen oder die Anpassung der Hilfebedarfsstufen.

### **Hinweis zur Verwendung von SDV**

- **PII-Erkennung:** Beachte, dass SDV standardmäßig personenbezogene Daten (PII) erkennen und anonymisieren kann. In unserem Code haben wir die PII-Erkennung für bestimmte Spalten deaktiviert, um realistische Namen und Diagnosen zu generieren. Stelle sicher, dass du keine echten personenbezogenen Daten in deinem Originaldatensatz verwendest.

- **Dokumentation:** Weitere Informationen zur Verwendung von SDV und zur Anpassung der Metadaten findest du in der offiziellen [SDV-Dokumentation](https://sdv.dev/SDV/index.html).

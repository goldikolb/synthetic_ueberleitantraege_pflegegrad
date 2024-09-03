# Überleitbogen-Synthese-Software

## Einführung

Diese Software erstellt synthetische Daten für den Überleitungsantrag des Medizinischen Dienstes zur Schnelleinstufung zwecks Pflegegrad. Die Software erzeugt aus 10 oder mehr Datensätzen in einer CSV-Tabelle mit Hilfe von ChatGPT neue Datensätze, die sich aus dem Muster der vorhandenen generieren. Mit einem zweiten Code können diese Datensätze dann aus der neuen CSV-Datei automatisch in eine PDF eingefügt werden. Dies ermöglicht die Erzeugung einer gewünschten Anzahl an PDF-Dateien mit fiktiven Daten. Der Zweck dieser Software ist es, datenschutzrechtlich problematische Daten zu vermeiden, wenn man Machine Learning-Modelle mit diesen Daten trainieren möchte.

**Hinweis** Alle hier verwendeten Daten sind frei erfunden. Jede Ähnlichkeit mit lebenden oder verstorbenen Personen sind rein zufällig.

## Data Augmentation

Data Augmentation ist ein legitimer Ansatz, um Machine Learning zu ermöglichen. Durch die Generierung synthetischer Daten können Datensätze erweitert werden, ohne auf reale und möglicherweise datenschutzrechtlich problematische Informationen zurückzugreifen. Dies ist besonders wichtig im medizinischen Bereich, wo der Schutz persönlicher Daten oberste Priorität hat. Mit synthetischen Daten können Machine Learning-Modelle trainiert und validiert werden, ohne dass echte Patientendaten verwendet werden müssen.

## Voraussetzungen

- Python 3.10 oder höher
- `pandas` Bibliothek
- `pdfrw` Bibliothek
- OpenAI API Schlüssel

## Installation

1. Klone dieses Repository:
    ```bash
    git clone https://github.com/goldikolb/synthetische_ueberleitungsantraege.git
    cd uberleitbogen-synthese
    ```

2. Installiere die benötigten Python-Pakete:
    ```bash
    pip install pandas pdfrw python-dotenv openai
    ```

3. Setze deinen OpenAI API Schlüssel in der `.env` Datei:
    ```env
    OPENAI_API_KEY=dein_openai_api_schluessel
    ```

## Verwendung

### Generieren synthetischer Daten

1. Lade die CSV-Datei mit den vorhandenen Daten in den Ordner `csv_data`.
2. Ändere den `file_path` im Jupyter-Notebook `synthetic_data_creator.ipynb` entsprechend.
3. Führe das Notebook aus, um neue synthetische Daten zu generieren.
4. Die neuen Datensätze werden in der Datei `erweiterte_daten_10.csv` gespeichert.

### Erstellen der neuen Gutachten

Bisher erzeugt die Datei synthetic_data_creator relativ zuverlässig neue Datenreihen. Diese müssen aber erst noch in eine Tablle übertragen und überprüft werden. Vor allem die Diagnosen sind noch sehr redundant und er immer nur mit einer neuen Diagnose gefüllt. Für die händische Bearbeitung in einer Tabelle. Empfehle ich über die Methode des few-shot-prompting einfach eine neue Reihe von Kombination neuer Diagnosen zu erzeugen. In gpt-4o funktioniert das einwandfrei. Füge folgenden Prompt und die Spalte mit den Pflegediagnosen ein und man bekommt adäquate pflegerelevante Diagnosen.

**Du bist Experte für Data Engineering in der Medizin, ich gebe dir eine Reihe von Diagnosen, jede Reihe ist ein Patient, bitte erzeuge weitere 10 Reihen an Diagnosen, die Auswirkungen haben auf AEDLs:**

### Erstellen von PDF-Dateien

1. Stelle sicher, dass die Vorlage `Antrag_ueberleitung.pdf` im Ordner `pdf` vorhanden ist.
2. Führe das Jupyter-Notebook `uberleitung_pdf_creator.ipynb` aus, um die PDF-Dateien zu erstellen.
3. Die erstellten PDF-Dateien werden im Ordner `output` gespeichert.
4. Zusätzlich wird eine Tabelle (csv-Datei) erstellt, die den Formularen (Dateinamen) das Ergebnis zuordnet.

## Erklärvideo

<a href="http://www.youtube.com/watch?feature=player_embedded&v=L3S8_Gj5t0M" target="_blank">
 <img src="http://img.youtube.com/vi/L3S8_Gj5t0M/mqdefault.jpg" alt="Watch the video" width="240" height="180" border="10" />
</a>

## Autor
Christian Kolb

## Kontakt

Wenn Sie Fragen haben oder einen Beitrag leisten möchten, zögern Sie nicht, uns über unsere Webseite zu kontaktieren: [pflege-ai.de](https://pflege-ai.de/).

[![Website](https://img.shields.io/badge/Pflege--AI-Webseite-%230f0122?style=flat&logo=Web&logoColor=ff8154)](https://pflege-ai.de/)

## Follow me on Social Media

[![Threads](https://img.shields.io/badge/Threads-Follow%20me-blue?style=flat&logo=Thread&logoColor=white)](https://www.threads.net/@pflege_ki)

[![Twitter Follow](https://img.shields.io/twitter/follow/ai_fuerth?style=social)](https://twitter.com/ai_fuerth)

[![Instagram](https://img.shields.io/badge/Instagram-Follow%20@pflege__ki-blue?style=flat&logo=instagram&logoColor=white)](https://www.instagram.com/pflege_ki/)

---
lab:
  title: Übung 11 – Verwenden von Repositorys in Microsoft Sentinel
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Lernpfad 7 – Lab 1 – Übung 11 – Verwenden von Repositorys in Microsoft Sentinel

## Labszenario

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Sie haben bereits geplante und Microsoft Security Analytics-Regeln erstellt.  Sie müssen die Analyseregeln in einem Azure DevOps-Repository zentralisieren.  Verbinden Sie anschließend Sentinel mit dem Azure DevOps-Repository und importieren Sie die Inhalte. 

>**Hinweis:** Eine **[interaktive Labsimulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Use%20repositories%20in%20Microsoft%20Sentinel)** ist verfügbar, mit der Sie dieses Lab in Ihrem eigenen Tempo durcharbeiten können. Möglicherweise liegen geringfügige Unterschiede zwischen der interaktiven Simulation und dem gehosteten Lab vor, aber die dargestellten Kernkonzepte und Ideen sind identisch. 


### Aufgabe 1: Erstellen und Exportieren einer Analyseregel

In dieser Aufgabe aktivieren Sie die Entitätsverhaltensanalysen in Microsoft Sentinel.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren Microsoft Sentinel-Arbeitsbereich aus.

1. Wählen Sie auf dem linken Blatt im Bereich *Konfiguration* den Eintrag **Analyse** aus.

1. Wählen Sie die zuvor erstellte Regel **Startup RegKey** aus.

1. Wählen Sie in der Symbolleiste **Exportieren** aus. **Hinweis:** Möglicherweise müssen Sie das Auslassungszeichen **(...)** auswählen, um sie anzuzeigen.

1. Die Regel wird in eine Textdatei namens *Azure_Sentinel_analytic_rule.json* exportiert.

1. Klicken Sie auf **Datei öffnen** unter dem Namen der heruntergeladenen Datei und wählen Sie dann **Weitere Anwendungen** aus.

1. Wählen Sie **Notepad** aus und klicken Sie dann auf **OK**.

1. Überprüfen Sie die Vorlage Azure Resource Manager und schließen Sie diese, wenn Sie fertig sind.


### Aufgabe 2: Erstellen unserer Azure DevOps-Umgebung

In dieser Aufgabe erstellen Sie ein Azure DevOps-Repository.

1. Öffnen Sie eine weitere Registerkarte im Browser und navigieren Sie zu (https://aexprodcus1.vsaex.visualstudio.com/me?mkt=en-US)).

1. Klicken Sie auf der Seite *Wir benötigen noch einige Details* auf **Weiter**.

1. Wählen Sie auf der Seite *Erste Schritte mit Azure DevOps* die Option **Neue Organisation erstellen** und klicken Sie dann auf **Weiter**.

1. Geben Sie auf der Seite * Fast fertig …* einen Namen für Ihre DevOps-Organisation ein, den Sie in Zukunft nicht mehr verwenden möchten, z. B. das Präfix Ihres Mandanten. **Hinweis:** Sie finden dies auf der Registerkarte „Ressourcen“ Ihres Labs (WWLx...).

1. *Geben Sie die angezeigten Zeichen ein*, danach **Weiter**.

1. Geben Sie auf der Seite *Erstellen Sie ein Projekt, um zu beginnen* **Meine Sentinel-Inhalte** ein und wählen Sie **Projekt erstellen**.aus.

1. Navigieren Sie im linken Fensterbereich zu **Repositorys**.

1. Wählen Sie am Ende der Seite im Bereich *Hauptverzweigung mit einem README oder einem Gitignore initialisieren* **Initialisieren** aus.

1. Die Seite sollte die Dateien für das Repository anzeigen.  Die einzige Datei ist README.me.

1. Im Blatt „Dateien“ (rechts auf der Seite) enthält die Symbolleiste die Optionen *Build einrichten*, *Klonen*, … Klicken Sie auf das Doppelpunkt-Symbol **(:)**, um weitere Optionen anzuzeigen.

1. Klicken Sie auf **Dateien hochladen**.

1. Wählen Sie **Durchsuchen** und wählen Sie die Datei **Azure_Sentinel_analytic_rule.json** aus Ihrem *Downloadsverzeichnis* aus.

1. Klicken Sie auf **Commit**.

1. Wählen Sie oben links auf der Seite **Azure DevOps** aus.  Ihre Organisation und Ihre Projekte werden angezeigt.

1. Wählen Sie in der linken unteren Ecke der Seite **Organisationseinstellungen** aus.

1. Wählen Sie auf der linken Seite unter *Sicherheit* die Option **Richtlinien** aus.

1. Schalten Sie *Zugriff von Drittanwendungen über OAuth* unter dem Bereich *Richtlinien für Anwendungsverbindungen* auf  **Ein**.


### Aufgabe 3: Verbinden von Sentinel mit Azure DevOps

1. Wählen Sie die Registerkarte *Azure Portal*/*Microsoft Sentinel* in Ihrem Browser aus.

1. Wählen Sie in Microsoft Sentinel im Abschnitt *Content Management* die Option **Repositorys (Vorschau)** aus.

1. Wählen Sie in der Symbolleiste die Schaltfläche **+ Neues hinzufügen** aus.

1. Geben Sie als Namen**Meine Inhalte** ein.

1. Wählen Sie für Versionskontrolle **Azure DevOps** aus.

1. Wählen Sie **Autorisieren**. Scrollen Sie in der Berechtigungsabfrage nach unten und wählen Sie **Akzeptieren** aus.

1. Wählen Sie die Organisation aus, die Sie zuvor erstellt haben (z. B. WWLx...).

1. Wählen Sie das Projekt *Mein Sentinel-Inhalt* aus, das Sie zuvor erstellt haben.

1. Wählen Sie das Repository aus *Mein Sentinel-Inhalt*, das Sie zuvor erstellt haben. **Hinweis:** Möglicherweise müssen Sie in der Dropdownliste nach unten scrollen, um das Repository zu sehen.

1. Wählen Sie als Verzweigung **main** aus. **Hinweis:** Möglicherweise müssen Sie in der Auswahlliste nach unten scrollen, um die Branch zu sehen.

1. Wählen Sie alle Inhaltstypen aus.

1. Wählen Sie dann **Erstellen** aus.

1. Kehren Sie gegebenenfalls zum Microsoft Sentinel-Arbeitsbereich zurück.

1. Gehen Sie zur Seite *Repositorys (Vorschau)* und klicken Sie auf **Aktualisieren**. Warten Sie bis bei *Letzter Bereitstellungsstatus* *Fehlgeschlagen* angezeigt wird.  

    >**Hinweis:** Der Status *Fehlgeschlagen* ist auf Einschränkungen in der gehosteten Lab-Umgebung zurückzuführen. Normalerweise würde *Erfolgreich* angezeigt werden. Dann sehen Sie in den *Analysen* die importierte Regel *Regel aus Azure DevOps*.


## Damit haben Sie das Lab beendet.

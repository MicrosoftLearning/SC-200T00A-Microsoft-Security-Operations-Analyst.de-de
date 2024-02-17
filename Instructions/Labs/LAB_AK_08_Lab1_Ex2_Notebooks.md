---
lab:
  title: Übung 2 – Bedrohungssuche mithilfe von Notebooks mit Microsoft Sentinel
  module: Learning Path 8 - Perform threat hunting in Microsoft Sentinel
---

# Lernpfad 8 – Lab 1 – Übung 2 – Bedrohungssuche mithilfe von Notebooks mit Microsoft Sentinel

## Labszenario

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Sie sollten die Vorteile der Bedrohungssuche mit Microsoft Sentinel Notebooks erkunden. Sie können Notebooks verwenden, um:

- Analysen durchzuführen, die nicht standardmäßig in Microsoft Sentinel enthalten sind, wie z. B. einige Python-Funktionen für maschinelles Lernen.
- Datenvisualisierungen zu erstellen, die nicht standardmäßig in Microsoft Sentinel enthalten sind, wie z. B. benutzerdefinierte Zeitleisten und Prozessbäume.
- Integrieren von Datenquellen, die sich außerhalb von Microsoft Sentinel befinden, z. B. eines lokalen Datasets

>**Hinweis:** Eine **[interaktive Labsimulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Hunt%20for%20threats%20using%20notebooks%20in%20Microsoft%20Sentinel)** ist verfügbar, mit der Sie dieses Lab in Ihrem eigenen Tempo durcharbeiten können. Möglicherweise liegen geringfügige Unterschiede zwischen der interaktiven Simulation und dem gehosteten Lab vor, aber die dargestellten Kernkonzepte und Ideen sind identisch. 

### Aufgabe 1: Erkunden von Notebooks

In dieser Aufgabe werden Sie die Verwendung von Notebooks in Microsoft Sentinel erkunden.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Edge-Browser zum Azure-Portal unter https://portal.azure.com.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren Microsoft Sentinel-Arbeitsbereich aus.

1. Wählen Sie im Microsoft Sentinel-Arbeitsbereich **Notebooks** unter dem Bereich *Bedrohungsmanagement* aus.

1. Als Nächstes müssen Sie einen AzureML-Arbeitsbereich erstellen. Wählen Sie **Azure Machine Learning konfigurieren** und dann die Schaltfläche **Neuen Azure ML-Arbeitsbereich erstellen** in der Befehlsleiste aus.

1. Wählen Sie im Feld „Abonnement“ Ihr Abonnement aus.

1. Wählen Sie für die Ressourcengruppe **Neue erstellen** aus, geben Sie als Namen *RG-MachineLearning* ein und klicken Sie auf **OK**. 

1. Gehen Sie im Abschnitt „Details zum Arbeitsbereich“ wie folgt vor:

     - Geben Sie einen eindeutigen Namen für den Arbeitsbereich ein.
     - Belassen Sie **East US** als Standardwert für *Region*.
     - Behalten Sie die Standardinformationen für Speicherkonto, Schlüsseltresor und Application Insights-Informationen bei.
     - Die Option „Containerregistrierung“ kann auf **Keine** bleiben.

1. Klicken Sie im unteren Seitenbereich auf **Überprüfen und erstellen**. Wenn die Nachricht *„Überprüfung erfolgreich“* angezeigt wird, klicken Sie auf **Erstellen**. 

     >**Hinweis:** Die Bereitstellung des Arbeitsbereichs für maschinelles Lernen kann einige Minuten dauern.

1. Wenn die Nachricht *Ihre Bereitstellung ist abgeschlossen* erscheint, kehren Sie zum Microsoft Sentinel-Portal zurück.

1. Wählen Sie erneut **Notebooks** und dann die Registerkarte **Vorlagen** in der mittleren Befehlsleiste aus. 

1. Wählen Sie **Ein Leitfaden „Erste Schritte“ für Microsoft Sentinel ML-Notebooks** aus. 

1. Scrollen Sie im rechten Bereich nach unten und wählen Sie die Schaltfläche **Aus Vorlage erstellen** aus. Überprüfen Sie die Standardoptionen und klicken Sie dann auf **Speichern**.

1. Sobald der Speichervorgang abgeschlossen ist, wählen Sie die Schaltfläche **Notebook starten** aus. Dadurch wird das Microsoft Azure Machine Learning Studio geöffnet.

1. Klicken Sie auf **Schließen**, wenn ein Informationsfenster im Microsoft Azure Machine Learning Studio angezeigt wird.

1. Klicken Sie in der Befehlsleiste rechts neben dem Selektor **Compute-Instanz:** auf das Symbol **+**, um eine neue Compute-Instanz zu erstellen. **Hinweis:** Es kann sich innerhalb des Auslassungspunkt-Symbols **(...)** verbergen.

     >**Hinweis:** Sie können mehr Platz auf dem Bildschirm erhalten, indem Sie das linke Azure ML Studio-Blatt ausblenden, indem Sie auf die 3 Zeilen oben links klicken, sowie die Notebook-Dateien, indem Sie auf das Symbol **<<** klicken.

1. Geben Sie einen eindeutigen Namen in das Feld *Computername* ein. Dieser identifiziert Ihre Compute-Instanz.

1. Scrollen Sie nach unten und wählen Sie die erste verfügbare Option aus. **Hinweis:** Workloadtyp: Entwicklung auf Notebooks und leichtes Testen.

1. Klicken Sie auf die Schaltfläche **Erstellen** am unteren Rand des Bereichs. Schließen Sie ein eventuell erscheinendes Feedbackfenster. Dieser Vorgang dauert einige Minuten. Sie erhalten eine Benachrichtigung (Glockensymbol), wenn der Vorgang abgeschlossen ist und das linke Symbol *Compute-Instanz* wechselt von blau nach grün.

1. Sobald der Compute erstellt wurde und läuft, überprüfen Sie, ob der zu verwendende Kernel *Python 3.8 – AzureML* ist. **Hinweis:** Dies wird rechts in der Befehlsleiste angezeigt.

1. Klicken Sie auf die Schaltfläche **Authentifizieren** und warten Sie, bis die Authentifizierung abgeschlossen ist.

1. Löschen Sie alle Ergebnisse aus dem Notebook, indem Sie die Schaltfläche **Alle Ausgaben löschen** in der Befehlsleiste auswählen und dem Tutorial *Erste Schritte* folgen. **Hinweis:** Sie finden das Tutorial, indem Sie die Auslassungspunkte (...) in der Befehlsleiste auswählen.

>**Hinweis:** Wenn Sie die obigen Schritte für den Zugriff auf das Notebook nicht ausführen können, können Sie es stattdessen auf seiner GitHub-Ansichtsseite verfolgen. [Erste Schritte mit Azure ML Notebooks und Microsoft Sentinel](https://nbviewer.org/github/Azure/Azure-Sentinel-Notebooks/blob/master/A%20Getting%20Started%20Guide%20For%20Azure%20Sentinel%20ML%20Notebooks.ipynb) 

## Damit haben Sie das Lab beendet.

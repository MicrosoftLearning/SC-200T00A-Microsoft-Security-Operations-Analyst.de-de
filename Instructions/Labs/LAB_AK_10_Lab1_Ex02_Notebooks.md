---
lab:
  title: Übung 2 – Bedrohungssuche mithilfe von Notebooks mit Microsoft Sentinel
  module: Learning Path 10 - Perform threat hunting in Microsoft Sentinel
---

# Lernpfad 10 – Lab 1 – Übung 2: Bedrohungsjagd mit Notebooks mit Microsoft Sentinel

## Labszenario

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Sie sollten die Vorteile der Bedrohungssuche mit Microsoft Sentinel Notebooks erkunden. Sie können Notebooks verwenden, um:

- Führen Sie Analysen durch, die nicht standardmäßig in Microsoft Sentinel bereitgestellt werden, z. B. einige Python-Features für maschinelles Lernen.
- Erstellen Sie Datenvisualisierungen, die nicht standardmäßig in Microsoft Sentinel bereitgestellt werden, z. B. benutzerdefinierte Zeitachsen und Prozessstrukturen.
- Integrieren von Datenquellen, die sich außerhalb von Microsoft Sentinel befinden, z. B. eines lokalen Datasets

>**Wichtig:** Die Lab-Übungen für Lernpfad Nr. 10 befinden sich in einer *eigenständigen* Umgebung. Wenn Sie das Lab vor dem Abschluss verlassen, müssen Sie die Konfigurationen erneut ausführen.

### Geschätzte Zeit bis zum Abschluss dieses Labs: 30 Minuten

### Aufgabe 1: Erkunden von Notebooks

In dieser Aufgabe erkunden Sie die Verwendung von Notebooks in Microsoft Sentinel.

>**Hinweis:** Microsoft Sentinel wurde in Ihrem Azure-Abonnement mit dem Namen **defenderWorkspace** vorab bereitgestellt, und die erforderlichen *Content Hub*-Lösungen wurden installiert.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Microsoft Edge-Browser zu der Azure-Portal unter <https://portal.azure.com>.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie den Microsoft Sentinel **defenderWorkspace** aus.

1. Wählen Sie im Microsoft Sentinel-Arbeitsbereich **Notebooks** unter dem Bereich *Bedrohungsmanagement* aus.

1. Als nächstes müssen Sie einen Azure Machine Learning-Arbeitsbereich erstellen. Wählen Sie **Azure Machine Learning konfigurieren** und dann die Schaltfläche **Neuen Azure ML-Arbeitsbereich erstellen** in der Befehlsleiste aus.

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

1. Sobald der Speichervorgang abgeschlossen ist, wählen Sie die Schaltfläche **Notebook starten** aus. Sie gelangen so zum Microsoft Azure Machine Learning Studio.

1. Wählen Sie **Schließen** aus, wenn im Microsoft Azure Machine Learning Studio ein Informationsfenster angezeigt wird.

1. Klicken Sie in der Befehlsleiste rechts neben dem **Compute:**-Selektor auf das Symbol **+**, um eine *Azure ML Compute*-Instanz zu erstellen. **Hinweis:** Es kann sich innerhalb des Auslassungspunkt-Symbols **(...)** verbergen.

     >**Hinweis:** Sie können für mehr Platz auf dem Bildschirm sorgen, indem Sie das linke Blatt von Azure ML Studio ausblenden. Dafür wählen Sie das *Hamburger-Menü* (3 horizontale Linien oben links) aus und reduzieren die Notebooks-Dateien, indem Sie das Symbol **<<** auswählen.

1. Geben Sie einen eindeutigen Namen in das Feld *Computername* ein. Dadurch wird Ihre Computeinstanz identifiziert.

1. Scrollen Sie nach unten und wählen Sie die erste verfügbare Option aus. **Hinweis:** Workloadtyp: Entwicklung in Notebooks (oder in einer anderen IDE) und einfache Tests.

1. Wählen Sie die Schaltfläche **Überprüfen + erstellen** unten auf dem Bildschirm aus. Scrollen Sie dann nach unten, und wählen Sie **Erstellen** aus. Schließen Sie ein eventuell erscheinendes Feedbackfenster. Dies dauert einige Minuten. Nach Abschluss wird eine Benachrichtigung (Glockensymbol) angezeigt, und das *Computeinstanz*-Symbol links wechselt von Blau zu Grün.

1. Vergewissern Sie sich nach der Compute-Erstellung und -Ausführung, dass der zu verwendende Kernel *Python 3.8 – Pytorch und Tensorflow* ist. **Hinweis:** Dies wird rechts in der Befehlsleiste angezeigt.

1. Klicken Sie auf die Schaltfläche **Authentifizieren** und warten Sie, bis die Authentifizierung abgeschlossen ist.

1. Löschen Sie alle Ergebnisse aus dem Notebook, indem Sie **Alle Ausgaben löschen** (Radierersymbol) aus der Befehlsleiste auswählen und dem Tutorial *Erste Schritte* folgen. **Hinweis:** Sie finden das Tutorial, indem Sie die Auslassungspunkte (...) in der Befehlsleiste auswählen.

1. Lesen Sie den Abschnitt *1 Einführung* im Notebook, und fahren Sie dann mit dem Abschnitt *2 Initialisieren des Notebooks und von MSTICPy* fort.

1. Lesen Sie im Abschnitt *2 Initialisieren des Notebooks und von MSTICPy* die Inhalte über das Initialisieren des Notebooks und das Installieren des MSTICPy-Pakets.

1. Führen Sie den *Python-Code* aus, um die Zelle zu initialisieren, indem Sie die Schaltfläche **Zelle ausführen** (Wiedergabesymbol) links neben dem Code auswählen.

1. Die Ausführung sollte ungefähr 15 Sekunden dauern. Überprüfen Sie danach die Ausgabemeldungen. Ignorieren Sie hierbei alle Warnungen zur Python-Kernelversion. Der Code wurde erfolgreich ausgeführt, wenn *msticpyconfig.yaml* im Ordner *utils* im *Datei-Explorer*-Bereich auf der linken Seite erstellt wurde. Es kann bis zu 30 Sekunden dauern, bis die Datei angezeigt wird.

    >**Hinweis:** Sie können die Ausgabemeldungen löschen, indem Sie die Auslassungspunkte (...) auf der linken Seite des Codefensters für das *Ausgabemenü* auswählen und das Symbol *Ausgabe löschen* (Quadrat mit einem x*) auswählen.

1. Wählen Sie die **msticpyconfig.yaml**-Datei im *Datei-Explorer*-Bereich auf der linken Seite aus, um den Inhalt der Datei zu überprüfen und dann zu schließen.

1. Fahren Sie mit dem Abschnitt *3 Abfragen von Daten mit MSTICPy* fort, und lesen Sie die entsprechenden Inhalte. Führen Sie nicht die Codezelle *Mehrere Microsoft Sentinel-Arbeitsbereiche* aus, da sie fehlschlagen wird. Die anderen Codezellen können jedoch erfolgreich ausgeführt werden.

>**Hinweis:** Wenn Sie die obigen Schritte für den Zugriff auf das Notebook nicht ausführen können, können Sie es stattdessen auf seiner GitHub-Ansichtsseite verfolgen. [Erste Schritte mit Azure ML Notebooks und Microsoft Sentinel](https://nbviewer.org/github/Azure/Azure-Sentinel-Notebooks/blob/master/A%20Getting%20Started%20Guide%20For%20Azure%20Sentinel%20ML%20Notebooks.ipynb) 

## Damit haben Sie das Lab beendet

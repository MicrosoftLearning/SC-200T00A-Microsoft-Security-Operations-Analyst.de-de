---
lab:
  title: Übung 1 – Ausführen der Bedrohungssuche in Microsoft Sentinel
  module: Learning Path 10 - Perform threat hunting in Microsoft Sentinel
---

# Lernpfad 10 – Lab 1 – Übung 1: Ausführen der Bedrohungssuche in Microsoft Sentinel

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod8_L1_Ex1.png)

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Sie haben Informationen zu Bedrohunhen über eine Command and Control (C2 oder C&C)-Methode erhalten. Sie müssen eine Bedrohungssuche durchführen und die Bedrohung überwachen.

>**Wichtig:** Die Lab-Übungen für Lernpfad Nr. 10 befinden sich in einer *eigenständigen* Umgebung. Wenn Sie das Lab vor dem Abschluss verlassen, müssen Sie die Konfigurationen erneut ausführen.

>**Hinweis:** Die in den Lab-Übungen von Lernpfad 9 erstellten Protokolldaten sind in diesem Lab nicht verfügbar, ohne die Aufgaben 1 und 2 von Übung 5 erneut auszuführen und *Angriff 3* auf dem WIN1-Server in Übung 6 erneut auszuführen. Sie können diese Anweisungen in einem neuen Browser-Tab öffnen, indem Sie auf diese Links klicken:

**[Lab 09 Übung 5](https://microsoftlearning.github.io/SC-200T00A-Microsoft-Security-Operations-Analyst/Instructions/Labs/LAB_AK_09_Lab1_Ex05_Attacks.html)**

**[Lab 09 Übung 6](https://microsoftlearning.github.io/SC-200T00A-Microsoft-Security-Operations-Analyst/Instructions/Labs/LAB_AK_09_Lab1_Ex06_Perform_Attacks.html)**

### Geschätzte Zeit für die Durchführung dieses Labs: 40 Minuten

### Aufgabe 1: Erstellen einer Bedrohungssuchabfrage

In dieser Aufgabe erstellen Sie eine Bedrohungssuchabfrage, setzen ein Lesezeichen für ein Ergebnis und erstellen einen Livestream.

>**Hinweis:** Microsoft Sentinel wurde in Ihrem Azure-Abonnement mit dem Namen **defenderWorkspace** vorab bereitgestellt, und die erforderlichen *Content Hub-Lösungen* wurden installiert.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Edge-Browser zum Azure-Portal unter <https://portal.azure.com>.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie den Microsoft Sentinel **defenderWorkspace** aus.

1. Wählen Sie **Protokolle** aus.

1. Geben Sie die folgende KQL-Anweisung in das Feld *Neue Abfrage 1* ein:

   >**Wichtig:** Um Fehler zu vermeiden, fügen Sie bitte alle KQL-Abfragen zunächst in den Editor ein und kopieren Sie sie von dort in das Protokollfenster *Neue Abfrage 1*.

    ```KQL
    let lookback = 2d; 
    SecurityEvent 
    | where TimeGenerated >= ago(lookback) 
    | where EventID == 4688 and Process =~ "powershell.exe"
    | extend PwshParam = trim(@"[^/\\]*powershell(.exe)+" , CommandLine) 
    | project TimeGenerated, Computer, SubjectUserName, PwshParam 
    | summarize min(TimeGenerated), count() by Computer, SubjectUserName, PwshParam 
    | order by count_ desc nulls last 
    ```

1. Sehen Sie sich die verschiedenen Ergebnisse an. Sie haben jetzt PowerShell-Anforderungen identifiziert, die in Ihrer Umgebung ausgeführt werden.

1. Markieren Sie das Kontrollkästchen der Ergebnisse, welches die *"-file c2.ps1"* anzeigt..

1. Klicken Sie in der *Ergebnisse*-Befehlsleiste auf die Schaltfläche **Lesezeichen hinzufügen**.

1. Wählen Sie **+ Neue Entität hinzufügen** unter *Entitätszuordnung* aus.

1. Bei *Entität* wählen Sie für die Werte **Host**, dann **Hostname** und **Computer** aus.

1. Bei *Taktiken und Techniken* wählen Sie **Command and Control** aus.

1. Klicken Sie im Bereich *Lesezeichen hinzufügen* auf **Erstellen**. Wir werden dieses Lesezeichen später einem Incident zuordnen.

1. Schließen Sie das Fenster *Protokolle*, indem Sie oben rechts im Fenster auf **X** klicken und dann auf **OK**, um die Änderungen zu verwerfen. 

1. Wählen Sie erneut Ihren Microsoft Sentinel-Arbeitsbereich und wählen Sie unter *Threat Management* die Seite **Bedrohungssuche** aus.

1. Wählen Sie die Registerkarte **Abfragen** und dann in der Befehlsleiste **+ Neue Abfrage** aus.

1. Geben Sie im Fenster *Benutzerdefinierte Abfrage erstellen* beim *Namen* **PowerShell Hunt** ein.

1. Geben Sie für die *Benutzerdefinierte Abfrage* die folgende KQL-Anweisung ein:

    ```KQL
    let lookback = 2d; 
    SecurityEvent 
    | where TimeGenerated >= ago(lookback) 
    | where EventID == 4688 and Process =~ "powershell.exe"
    | extend PwshParam = trim(@"[^/\\]*powershell(.exe)+" , CommandLine) 
    | project TimeGenerated, Computer, SubjectUserName, PwshParam 
    | summarize min(TimeGenerated), count() by Computer, SubjectUserName, PwshParam 
    | order by count_ desc nulls last 
    ```

1. Scrollen Sie nach unten und wählen Sie unter *Entitätszuordnung* Folgendes aus:

    - In der Dropdownliste *Entitätstyp* wählen Sie **Host** aus.
    - In der Dropdownliste *Bezeichner* wählen Sie **HostName** aus.
    - In der Dropdownliste *Wert* wählen Sie **Computer** aus.

1. Scrollen Sie nach unten und wählen Sie unter *Taktiken und Techniken* **Command and Control** und klicken Sie dann auf **Erstellen**, um die Bedrohungssuchabfrage zu erstellen.

1. Suchen Sie auf dem Blatt *Microsoft Sentinel – Hunting* nach der soeben in der Liste erstellten Abfrage *PowerShell-Hunt*.

1. Wählen Sie **PowerShell-Hunt** aus der Liste aus.

1. Überprüfen Sie die Anzahl der Ergebnisse im mittleren Fensterbereich unter der Spalte *Ergebnisse*.

1. Klicken Sie im rechten Fensterbereich auf die Schaltfläche **Ergebnisse anzeigen**. Die KQL-Abfrage wird automatisch gestartet.

1. Schließen Sie das Fenster *Protokolle*, indem Sie oben rechts im Fenster auf **X** klicken und dann auf **OK**, um die Änderungen zu verwerfen. 

1. Klicken Sie mit der rechten Maustaste auf die Abfrage **PowerShell-Hunt** und wählen Sie **Zum Livestream hinzufügen** aus. **Hinweis:** Sie können dies auch tun, indem Sie die Maus nach rechts bewegen und auf die Auslassungspunkte **(...)** am Ende der Zeile klicken, um ein Kontextmenü zu öffnen.

1. Stellen Sie sicher, dass der *Status* jetzt *wird ausgeführt* lautet. Dies wird alle 30 Sekunden im Hintergrund ausgeführt, und Sie erhalten eine Benachrichtigung im Azure-Portal (Glockensymbol), wenn ein neues Ergebnis gefunden wird. 

1. Wählen Sie die Registerkarte **Lesezeichen** im mittleren Fensterbereich aus.

1. Wählen Sie in der Ergebnisliste das soeben erstellte Lesezeichen aus.

1. Scrollen Sie im rechten Fensterbereich nach unten und klicken Sie auf die Schaltfläche **Untersuchen**. **Hinweis:** Es kann einige Minuten dauern, bis das Untersuchungsdiagramm angezeigt wird.

1. Erkunden Sie das Untersuchungsdiagramm genau wie im vorherigen Modul. Beachten Sie die hohe Anzahl von *Zugehörige Warnungen* für *WINServer*.

1. Schließen Sie das *Untersuchungsdiagramm*, indem Sie auf das **X** in der oberen rechten Ecke des Fensters klicken. 

1. Blenden Sie das rechte Blatt aus, indem Sie auf das **>>**-Symbol klicken und dann nach rechts scrollen, bis das Symbol „Auslassungspunkte“ **(...)** angezeigt wird.

1. Wählen Sie **Zu vorhandenem Incident hinzufügen** aus. Im rechten Fensterbereich werden alle Incidents angezeigt.

1. Wählen Sie einen der Incidents aus und klicken Sie anschließend auf **Hinzufügen**.

1. Scrollen Sie nach links, um zu sehen, dass die Spalte *Schweregrad* nun mit den Daten des Incidents gefüllt ist.

### Aufgabe 2: Erstellen einer NRT-Abfrageregel

In dieser Aufgabe erstellen Sie anstelle eines LiveStreams eine NRT-Analyseabfrageregel. NRT-Regeln werden jede Minute ausgeführt und schauen eine Minute zurück. Der Vorteil von NRT-Regeln ist, dass sie die Logik zum Erstellen von Warnungen und Incidents verwenden können.

1. Wählen Sie die Seite **Analyse** unter *Konfiguration* in Microsoft Sentinel aus. 

1. Wählen Sie die Registerkarte **Erstellen** und dann **NRT-Abfrageregel** aus.

1. Dadurch wird der Assistent für Analyseregeln geöffnet. Für die Registerkarte *Allgemein* geben Sie ein:

    |Einstellung|Wert|
    |---|---|
    |Name|**NRT PowerShell Hunt**|
    |Beschreibung|**NRT PowerShell Hunt**|
    |Taktik|**Command-and-Control**|
    |Severity|**Hoch**|

1. Klicken Sie auf die Schaltfläche **Weiter: Regellogik festlegen >**. 

1. Geben Sie die folgende KQL-Anweisung für die *Regelabfrage* ein:

    ```KQL
    let lookback = 2d; 
    SecurityEvent 
    | where TimeGenerated >= ago(lookback) 
    | where EventID == 4688 and Process =~ "powershell.exe"
    | extend PwshParam = trim(@"[^/\\]*powershell(.exe)+" , CommandLine) 
    | project TimeGenerated, Computer, SubjectUserName, PwshParam 
    | summarize min(TimeGenerated), count() by Computer, SubjectUserName, PwshParam
    ```

1. Wählen Sie **Abfrageergebnisse anzeigen >** aus, um sicherzustellen, dass Ihre Abfrage keine Fehler enthält.

1. Schließen Sie das Fenster *Protokolle*, indem Sie oben rechts im Fenster auf **X** klicken und dann auf **OK**, um die Änderungen zu verwerfen. 

1. Wählen Sie **Test mit aktuellen Daten** unter *Ergebnissimulation* aus. Beachten Sie die erwartete Anzahl von *Warnungen pro Tag*.

1. Wählen Sie unter *Entitätszuordnung* Folgendes aus:

    - In der Dropdownliste *Entitätstyp* wählen Sie **Host** aus.
    - In der Dropdownliste *Bezeichner* wählen Sie **HostName** aus.
    - In der Dropdownliste *Wert* wählen Sie **Computer** aus.

1. Scrollen Sie nach unten, und wählen Sie die Schaltfläche **Weiter: Incidenteinstellungen >** aus.

1. Für die Registerkarte *Incidenteinstellungen* übernehmen Sie die Standardwerte, und wählen Sie die Schaltfläche **Weiter: Automatisierte Antwort >** aus.

1. Wählen Sie die Schaltfläche *Automatische Antwort* und dann die Schaltfläche **Weiter: Prüfen und erstellen** aus.

1. Wählen Sie auf der Registerkarte *Überprüfen und Erstellen* die Schaltfläche **Speichern** aus, um die neue Geplante Analyseregel zu erstellen und zu speichern.

### Aufgabe 3: Erstellen eines Suchauftrags

In dieser Aufgabe verwenden Sie einen Suchauftrag, um nach einem C2 zu suchen.

<!--- >**Note:** The *Restore* operation incurs costs that can deplete your Azure Pass subscription credits. For that reason, you will not be performing the restore operation in this lab. However, you can follow the steps below to perform the restore operation in your own environment. --->

1. Wählen Sie in Microsoft Sentinel unter *Allgemein* die Seite **Suchen** aus.

1. Geben Sie **reg.exe** in das Suchfeld ein und klicken Sie auf **Start**.

1. Ein neues Fenster wird geöffnet, in dem die Abfrage ausgeführt wird. Klicken Sie auf das Symbol „Auslassungspunkte“ **(...)** oben rechts und wechseln Sie dann in den Suchauftragsmodus ****.

1. Wählen Sie in der Befehlsleiste die Schaltfläche **Suchauftrag** aus. 

1. Der Suchauftrag erstellt eine neue Tabelle mit Ihren Ergebnissen, sobald diese eintreffen. Die Ergebnisse können auf der Registerkarte *Gespeicherte Suchen* eingesehen werden.

1. Schließen Sie das Fenster *Protokolle*, indem Sie oben rechts im Fenster auf **X** klicken und dann auf **OK**, um die Änderungen zu verwerfen.

1. Wählen Sie in der Befehlsleiste die Registerkarte **Wiederherstellung** und klicken Sie dann auf die Schaltfläche **Wiederherstellen**.

1. Suchen Sie unter *Eine Tabelle für die Wiederherstellung auswählen* nach **SecurityEvent** und wählen Sie dieses aus.

1. Überprüfen Sie die verfügbaren Optionen und wählen Sie dann die Schaltfläche **Abbrechen** aus.

    >**Hinweis:** Wenn Sie den Auftrag ausführen, wird die Wiederherstellung einige Minuten dauern und Ihre Daten werden in einer neuen Tabelle zur Verfügung stehen.

### Aufgabe 4: Erstellen Sie eine Suche, die mehrere Abfragen in einer MITRE-Taktik kombiniert

1. Die MITRE ATT&CK-Karte hilft Ihnen dabei, bestimmte Lücken in Ihrer Erkennungsabdeckung zu identifizieren. Sie können vordefinierte Huntingabfragen für bestimmte MITRE ATT&CK-Techniken als Ausgangspunkt verwenden, um eine neue Erkennungslogik zu entwickeln.

1. Erweitern Sie in Microsoft Sentinel den Eintrag **Bedrohungsmanagement** in den linken Navigationsmenüs.

1. Wählen Sie **MITRE ATT&CK (Vorschau)**.

1. Heben Sie die Auswahl der Elemente im Dropdown-Menü *Active rules* auf.

1. Wählen Sie im Filter *Simulierte Regeln* die Option **Suchabfragen** aus, um zu sehen, mit welchen Techniken Suchabfragen verknüpft sind.

1. Wählen Sie die Karte für **Kontomanipulation** aus.

1. Suchen Sie im Detailbereich nach *Simulierte Abdeckung* und klicken Sie auf den Link **Anzeigen** neben *Suchabfragen* aus.

1. Dieser Link führt Sie zu einer gefilterten Ansicht der Registerkarte Abfragen auf der Seite Hunting, basierend auf der von Ihnen ausgewählten Technik.

1. Wählen Sie alle Abfragen für diese Technik aus, indem Sie das Kästchen oben in der Liste links markieren.

1. Wählen Sie das Dropdown-Menü **Suchaktionen** in der Mitte des Bildschirms über den Filtern aus.

1. Wählen Sie **Neue Suche erstellen** aus. Alle von Ihnen ausgewählten Abfragen werden für diese neue Suche geklont.

1. Füllen Sie den Namen und die optionalen Felder für die Suche aus. In der Beschreibung können Sie Ihre Hypothese als Text formulieren. Im Pulldownmenü Hypothese legen Sie den Status Ihrer Arbeitshypothese fest.

1. Wählen Sie **Erstellen** aus, um zu beginnen.

1. Wählen Sie die Registerkarte **Suchen (Vorschau)** aus, um die neue Suche anzuzeigen.

1. Wählen Sie den Suchlink anhand des Namens aus, um die Details anzuzeigen und Maßnahmen zu ergreifen.

1. Zeigen Sie den Detailbereich mit Name der Suche, Beschreibung, Inhalt, Zeitpunkt der letzten Aktualisierung und Erstellungszeitpunkt an.

1. Wählen Sie alle Abfragen aus, indem Sie das Kästchen neben der Spalte *Abfrage* verwenden.

1. Wählen Sie entweder **Ausgewählte Abfragen ausführen** oder deaktivieren Sie die ausgewählten Zeilen und *klicken Sie mit der rechten Maustaste* und **führen Sie** eine einzelne Abfrage aus.

1. Sie können auch eine einzelne Abfrage auswählen und im Bereich „Details“ die Option **Ergebnisse anzeigen** auswählen.

1. Überprüfen Sie, welche Abfragen Ergebnisse geliefert haben.

1. Bestimmen Sie anhand der Ergebnisse, ob es genügend starke Beweise gibt, um die Hypothese zu bestätigen. Wenn dies nicht der Fall ist, schließen Sie die Suche und markieren Sie sie als ungültig.

1. Alternative Schritte:
    - Gehen Sie zu Microsoft Sentinel.
    - Erweitern Sie das Bedrohungsmanagement.
    - Wählen Sie „Suche“ aus.
    - Klicken Sie auf „Filter hinzufügen“.
    - Legen Sie den Filter auf „tactics:persistence“ fest.
    - Fügen Sie einen weiteren Filter hinzu.
    - Legen Sie den zweiten Filter auf folgende Techniken fest: T1098.

## Fahren Sie mit Übung 2 fort

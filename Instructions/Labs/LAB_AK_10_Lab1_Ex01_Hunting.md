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

Die in den Lab-Übungen von Lernpfad 9 erstellten Protokolldaten sind in diesem Lab nicht verfügbar, ohne die folgenden vorausgesetzten Aufgaben erneut auszuführen.

<!--- **[Lab 09 Exercise 5](https://microsoftlearning.github.io/SC-200T00A-Microsoft-Security-Operations-Analyst/Instructions/Labs/LAB_AK_09_Lab1_Ex05_Attacks.html)**

**[Lab 09 Exercise 6](https://microsoftlearning.github.io/SC-200T00A-Microsoft-Security-Operations-Analyst/Instructions/Labs/LAB_AK_09_Lab1_Ex06_Perform_Attacks.html)** --->

### Geschätzte Zeit bis zum Abschluss dieses Labs: 45–60 Minuten

### Vorausgesetzte Aufgabe 1: Verbinden eines lokalen Servers

In dieser Aufgabe verbinden Sie einen lokalen Server mit Ihrem Azure-Abonnement. Azure Arc wurde auf diesem Server vorinstalliert. Der Server wird in den nächsten Übungen verwendet, um simulierte Angriffe auszuführen, die Sie später für die Erkennung und Untersuchung in Microsoft Sentinel verwenden werden.

>**Wichtig:** Die nächsten Schritte werden auf einem anderen Computer ausgeführt als dem, auf dem Sie zuvor gearbeitet haben. Suchen Sie auf der Registerkarte „Referenzen“ nach dem Namen der virtuellen Maschine.

1. Melden Sie sich bei dem virtuellen Computer **WINServer** als Administrator*in mit dem Kennwort: **Passw0rd!** an, falls erforderlich.  

Wie oben beschrieben, wurde Azure Arc auf dem **WINServer-Computer** vorinstalliert. Sie verbinden diesen Computer jetzt mit Ihrem Azure-Abonnement.

1. Wählen Sie auf dem *WINServer-Computer* das Symbol *Suchen* aus, und geben Sie **cmd** ein.

1. Klicken Sie in den Suchergebnissen mit der rechten Maustaste auf *Eingabeaufforderung*, und wählen Sie **Als Administrator ausführen** aus.

1. Geben Sie im Eingabeaufforderungsfenster den folgenden Befehl ein: *Drücken Sie nicht auf die EINGABETASTE*:

    ```cmd
    azcmagent connect -g "defender-RG" -l "EastUS" -s "Subscription ID string"
    ```

1. Ersetzen Sie die **Abonnement-ID-Zeichenfolge** durch die *Abonnement-ID*, die von Ihrem Lab-Hoster (*Registerkarte „Ressourcen“) bereitgestellt wird. Achten Sie darauf, die Anführungszeichen beizubehalten.

1. Geben Sie **Eingeben** ein, um den Befehl auszuführen (dies kann einige Minuten dauern).

    >**Hinweis**: Wenn das Browser-Auswahlfenster *Wie möchten Sie das öffnen?* angezeigt wird, wählen Sie **Microsoft Edge** aus.

1. Geben Sie im Dialogfeld *Anmelden* Ihre **Mandanten-E-Mail** und Ihr **Mandantenkennwort** ein, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Anmelden** aus. Warten Sie auf die Meldung *Authentifizierung abgeschlossen*, schließen Sie die Browserregisterkarte, und kehren Sie zum Fenster *Eingabeaufforderung* zurück.

1. Lassen Sie nach Abschluss der Ausführung der Befehle das Fenster *Eingabeaufforderung* geöffnet, und geben Sie den folgenden Befehl ein, um zu bestätigen, dass die Verbindung erfolgreich hergestellt wurde:

    ```cmd
    azcmagent show
    ```

1. Überprüfen Sie in der Befehlsausgabe, ob der *Agentstatus* verbunden** ist**.

## Vorausgesetzte Aufgabe 2: Verbinden eines Windows-Computers, der nicht von Azure stammt

In dieser Aufgabe fügen Sie einen mit Azure Arc verbundenen lokalen Computer zu Microsoft Sentinel hinzu.  

>**Hinweis:** Microsoft Sentinel wurde in Ihrem Azure-Abonnement mit dem Namen **defenderWorkspace** vorab bereitgestellt, und die erforderlichen *Content Hub*-Lösungen wurden installiert.

1. Melden Sie sich beim virtuellen **WIN1-Computer** als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Microsoft Edge-Browser zu der Azure-Portal unter <https://portal.azure.com>.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie den Microsoft Sentinel **defenderWorkspace** aus.

1. Scrollen Sie im linken Navigationsmenü von Microsoft Sentinel nach unten zum Abschnitt *Konfiguration* und wählen Sie **Datenconnectors** aus.

1. Suchen Sie in den *Datenconnectors* nach der Lösung **Windows-Sicherheitsereignisse über AMA** und wählen Sie diese aus der Liste aus.

1. Wählen Sie im Detailbereich *Windows-Sicherheitsereignisse über AMA* die Option **Connectorseite öffnen** aus.

    >**Hinweis:** Die Lösung *Windows-Sicherheitsereignisse* installiert sowohl den *Windows-Sicherheitsereignisse über AMA* als auch den Datenconnector *Sicherheitsereignisse über Legacy-Agent*. Plus 2 Arbeitsmappen, 20 Analyseregeln und 43 Hunting-abfragen.

1. Wählen Sie im Abschnitt *Konfiguration* unter der Registerkarte *Anweisungen* die Option **Regel zur Datensammlung erstellen** aus.

1. Geben Sie **AZWINDCR** als Regelnamen ein und wählen Sie **Weiter: Ressourcen** aus.

1. Erweitern Sie Ihr *Abonnement* unter *Bereich* auf der Registerkarte *Ressourcen*.

    >**Hinweis:** Sie können die gesamte Hierarchie *Bereich* erweitern, indem Sie die Option „>“ vor der Spalte *Bereich* auswählen.

1. Erweitern Sie die Ressourcengruppe **defender-RG** und wählen Sie dann **WINServer** aus.

1. Wählen Sie **Weiter: Sammeln** aus und lassen Sie die Option *Alle Sicherheitsereignisse* ausgewählt.

1. Klicken Sie auf **Weiter: Überprüfen + erstellen**.

1. Wählen Sie **Erstellen** aus, nachdem *Validierung erfolgreich* angezeigt wurde.

### Vorausgesetzte Aufgabe 3: Befehls- und Kontrollangriff mit DNS

>**Wichtig:** Die nächsten Schritte werden auf einem anderen Computer ausgeführt als dem, auf dem Sie zuvor gearbeitet haben. Suchen Sie auf der Registerkarte „Referenzen“ nach dem Namen der virtuellen Maschine.

1. Melden Sie sich bei dem virtuellen Computer **WINServer** als Administrator*in mit dem Kennwort: **Passw0rd!** an, falls erforderlich.

1. Wählen Sie auf dem *WINServer-Computer* das Symbol *Suchen* aus, und geben Sie **cmd** ein.

1. Klicken Sie in den Suchergebnissen mit der rechten Maustaste auf *Eingabeaufforderung*, und wählen Sie **Als Administrator ausführen** aus.

1. Kopieren Sie diesen Befehl und führen Sie ihn aus, um ein Skript zu erstellen, das eine DNS-Anfrage an einen C2-Server simuliert:

    ```CommandPrompt
    notepad c2.ps1
    ```

1. Wählen Sie **Ja**, um eine neue Datei zu erstellen, und kopieren Sie das folgende PowerShell-Skript in *c2.ps1*.

    >**Hinweis:** Beim Einfügen in die Datei der virtuellen Maschine wird möglicherweise nicht die gesamte Länge des Skripts angezeigt. Stellen Sie sicher, dass das Skript den Anweisungen in der Datei *c2.ps1* entspricht.

    ```PowerShell
    param(
        [string]$Domain = "microsoft.com",
        [string]$Subdomain = "subdomain",
        [string]$Sub2domain = "sub2domain",
        [string]$Sub3domain = "sub3domain",
        [string]$QueryType = "TXT",
        [int]$C2Interval = 8,
        [int]$C2Jitter = 20,
        [int]$RunTime = 240
    )
    $RunStart = Get-Date
    $RunEnd = $RunStart.addminutes($RunTime)
    $x2 = 1
    $x3 = 1 
    Do {
        $TimeNow = Get-Date
        Resolve-DnsName -type $QueryType $Subdomain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
        if ($x2 -eq 3 )
        {
            Resolve-DnsName -type $QueryType $Sub2domain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
            $x2 = 1
        }
        else
        {
            $x2 = $x2 + 1
        }    
        if ($x3 -eq 7 )
        {
            Resolve-DnsName -type $QueryType $Sub3domain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
            $x3 = 1
        }
        else
        {
            $x3 = $x3 + 1
        }
        $Jitter = ((Get-Random -Minimum -$C2Jitter -Maximum $C2Jitter) / 100 + 1) +$C2Interval
        Start-Sleep -Seconds $Jitter
    }
    Until ($TimeNow -ge $RunEnd)
    ```

1. Wählen Sie im Menü Notepad **Datei** und dann **Speichern**. 

1. Kehren Sie zum Eingabeaufforderungsfenster zurück, geben Sie den folgenden Befehl ein und drücken Sie die Eingabetaste. 

    >**Hinweis:** Es werden DNS-Auflösungsfehler angezeigt. Dies entspricht dem erwarteten Verhalten.

    ```CommandPrompt
    Start PowerShell.exe -file c2.ps1
    ```

>**Wichtig:** Schließen Sie diese Fenster nicht. Lassen Sie dieses PowerShell-Skript im Hintergrund laufen. Der Befehl muss einige Stunden lang Protokolleinträge generieren. Sie können mit der nächsten Aufgabe und den nächsten Übungen fortfahren, während dieses Skript läuft. Die durch diese Aufgabe erzeugten Daten werden später im Lab zur Bedrohungssuche verwendet. Bei diesem Vorgang werden keine großen Datenmengen erzeugt oder verarbeitet.

### Aufgabe 1: Erstellen einer Bedrohungssuchabfrage

In dieser Aufgabe erstellen Sie eine Bedrohungssuchabfrage, setzen ein Lesezeichen für ein Ergebnis und erstellen einen Livestream.

>**Hinweis:** Microsoft Sentinel wurde in Ihrem Azure-Abonnement mit dem Namen **defenderWorkspace** vorab bereitgestellt, und die erforderlichen *Content Hub-Lösungen* wurden installiert.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Microsoft Edge-Browser zu der Azure-Portal unter <https://portal.azure.com>.

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

1. Wählen Sie in der Ergebnisliste das erstellte Lesezeichen aus.

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

1. Wählen Sie im Abschnitt *Warnungserweiterung* die Option *Entitätszuordnung >* **+ Neue Entität hinzufügen** aus.

1. Wählen Sie in der *Entität* Folgendes aus:

    - In der Dropdownliste *Entitätstyp* wählen Sie **Host** aus.
    - In der Dropdownliste *Bezeichner* wählen Sie **HostName** aus.
    - In der Dropdownliste *Wert* wählen Sie **Computer** aus.

1. Scrollen Sie nach unten, und wählen Sie die Schaltfläche **Weiter: Incidenteinstellungen >** aus.

1. Für die Registerkarte *Incidenteinstellungen* übernehmen Sie die Standardwerte, und wählen Sie die Schaltfläche **Weiter: Automatisierte Antwort >** aus.

1. Wählen Sie die Schaltfläche *Automatische Antwort* und dann die Schaltfläche **Weiter: Prüfen und erstellen** aus.

1. Wählen Sie auf der Registerkarte *Überprüfen und Erstellen* die Schaltfläche **Speichern** aus, um die neue Geplante Analyseregel zu erstellen und zu speichern.

### Aufgabe 3: Erstellen eines Suchauftrags

In dieser Aufgabe verwenden Sie einen Suchauftrag, um nach einem C2 zu suchen.

**Hinweis:** Der Vorgang *Wiederherstellen* verursacht Kosten, die Ihr Azure-Abonnementguthaben aufbrauchen können. Aus diesem Grund werden Sie den Wiederherstellungsvorgang in diesem Lab nicht durchführen. Sie können jedoch die folgenden Schritte ausführen, um den Wiederherstellungsvorgang in Ihrer eigenen Umgebung auszuführen.

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

1. Wählen Sie **Suche erstellen** aus. Alle von Ihnen ausgewählten Abfragen werden für diese neue Suche geklont.

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
    - Legen Sie den Filter auf „tactics: persistence“ fest.
    - Fügen Sie einen weiteren Filter hinzu.
    - Legen Sie den zweiten Filter auf folgende Techniken fest: T1098.

## Fahren Sie mit Übung 2 fort

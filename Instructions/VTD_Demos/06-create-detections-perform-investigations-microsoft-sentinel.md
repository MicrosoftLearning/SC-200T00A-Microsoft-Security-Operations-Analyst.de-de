# Modul 6: Erstellen von Erkennungen und Durchführen von Untersuchungen mithilfe von Microsoft Sentinel

**Hinweis:** Der erfolgreiche Abschluss dieser Demo hängt davon ab, dass Sie alle Schritte im [Dokument „Voraussetzungen“](00-prerequisites.md) abschließen.

**Wichtig:** Diese Demo ist für VTD-5002-FY25 nicht erforderlich.

## Erstellen einer NRT-Abfrageregel

In dieser Aufgabe erstellen Sie eine NRT-Analyseabfrageregel (Near Real Time).

1. Wählen Sie die Seite **Analyse** unter *Konfiguration* in Microsoft Sentinel aus.

1. Wählen Sie die Registerkarte **Erstellen** und dann **NRT-Abfrageregel** aus.

1. Dadurch wird der Assistent für Analyseregeln geöffnet. Für die Registerkarte *Allgemein* geben Sie ein:

    |Einstellung|Wert|
    |---|---|
    |Name|**NRT PowerShell Hunt**|
    |Beschreibung|**NRT PowerShell Hunt**|
    |Taktiken und Techniken|**Command-and-Control**|
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

1. Wählen Sie **Weiter: Überprüfen + erstellen >** aus.

1. Wählen Sie auf der Registerkarte *Überprüfen und erstellen* die Schaltfläche **Speichern** aus, um die neue geplante Analyseregel zu erstellen und zu speichern.

## Mit dem Azure Monitor-Agent (AMA) konfigurierte Angriffserkennungsfenster

In dieser Aufgabe untersuchen Sie den Incident, der anhand der von Ihnen erstellten `NRT`-Regel erstellt wurde.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Edge-Browser zum Azure-Portal unter https://portal.azure.com.

1. Kopieren Sie im Dialogfeld **Anmelden** das **Mandanten-E-Mail**-Konto für den Administrator, das von Ihrem Labhostinganbieter bereitgestellt wird, und fügen Sie es ein, und wählen Sie dann **Weiter**aus.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren zuvor erstellten Microsoft Sentinel-Arbeitsbereich aus.

1. Wechseln si in `Microsoft Sentinel` zum `Threat management` Menüabschnitt, und wählen Sie **Incidents** aus.

**Hinweis** Es kann einige Minuten dauern, bis `Incident` angezeigt wird.

1. Es sollte ein Incident angezeigt werden, der mit `Severity` und `Title` übereinstimmt, die Sie in der von Ihnen erstellten Regel `NRT` konfiguriert haben.

1. Wählen Sie `Incident` aus, und der Bereich `detail` wird geöffnet.

1. Wählen Sie **Alle Informationen anzeigen** und dann die Schaltfläche **Untersuchen** aus.

1. Erkunden Sie die Zuordnung `Entities` mit dem Incident `NRT PowerShell Hunt`.

1. Schließen Sie das Fenster `Investigation` durch Auswahl von **X** oben rechts im Fenster.

1. Wählen Sie die Registerkarte `Logs` aus, und geben Sie die folgende KQL-Anweisung ein:

    ```KQL
    let lookback = 2d; 
    SecurityEvent 
    | where TimeGenerated >= ago(lookback) 
    | where EventID == 4688 and Process =~ "powershell.exe"
    | extend PwshParam = trim(@"[^/\\]*powershell(.exe)+" , CommandLine) 
    | project TimeGenerated, Computer, SubjectUserName, PwshParam 
    | summarize min(TimeGenerated), count() by Computer, SubjectUserName, PwshParam
    ```

**Hinweis**: Sie finden diese Abfrage möglicherweise in `Queries History` und können sie von dort aus **ausführen**.

1. Wählen Sie die Schaltfläche **Fertig** aus, um das Fenster `Logs` zu schließen.

1. Schließen Sie das Fenster `Incident` durch Auswahl des **X** oben rechts im Fenster.

## Damit haben Sie die Demo beendet

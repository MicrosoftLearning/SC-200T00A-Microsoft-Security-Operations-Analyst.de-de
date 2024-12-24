---
lab:
  title: Übung 1 – Erstellen von Abfragen für Microsoft Sentinel mithilfe von Kusto Query Language (KQL)
  module: Learning Path 6 - Create queries for Microsoft Sentinel using Kusto Query Language (KQL)
---

# Lernpfad 6 – Lab 1 – Übung 1: Erstellen von Abfragen für Microsoft Sentinel mit der Kusto-Abfragesprache (KQL)

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod4_L1_Ex1.png)

Sie sind Security Operations Analyst in einem Unternehmen, das Microsoft Sentinel implementiert. Sie sind für die Analyse von Protokolldaten verantwortlich, um nach schädlichen Aktivitäten zu suchen, Visualisierungen anzuzeigen und Bedrohungen aufzuspüren. Zum Abfragen von Protokolldaten verwenden Sie die Kusto-Abfragesprache (KQL).

>**Wichtig:** Dieses Lab umfasst das Eingeben vieler KQL-Skripts in Microsoft Sentinel. Die Skripte wurden zu Beginn des Labs in einer Datei zur Verfügung gestellt. Sie können auch hier: <https://github.com/MicrosoftLearning/SC-200T00A-Microsoft-Security-Operations-Analyst/tree/master/Allfiles> heruntergeladen werden

### Geschätzte Zeit bis zum Abschluss dieses Labs: 60 Minuten

### Aufgabe 1: Zugriff auf den KQL-Testbereich

In dieser Aufgabe erhalten Sie Zugriff auf eine Log Analytics-Umgebung, in der Sie das Schreiben von KQL-Anweisungen üben können.

1. Melden Sie sich beim virtuellen **WIN1-Computer** als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Gehen Sie im Microsoft Edge-Browser zu <https://aka.ms/lademo> und melden Sie sich mit den Administrator-Anmeldeinformationen an.

1. Schließen Sie das Popupfenster „Log Analytics-Video“, das erscheint.

1. Sehen Sie sich die verfügbaren Tabellen und andere Tools an, die im *Schema und im Filterbereich* auf der linken Seite des Bildschirms aufgeführt sind.

1. Geben Sie im Abfrage-Editor die folgende Abfrage ein und wählen Sie die Schaltfläche **„Ausführen“**. Die Abfrageergebnisse sollten im unteren Fenster angezeigt werden.

    ```KQL
    SecurityEvent
    ```

1. Beachten Sie, dass Sie die maximale Anzahl von Ergebnissen erreicht haben (30.000).

1. Ändern Sie im Abfragefenster den *Zeitbereich* in **Letzte 30 Minuten**.

1. Wählen Sie **>** neben dem ersten Datensatz, um die Informationen für die Zeile zu erweitern.


### Aufgabe 2: Ausführen grundlegender KQL-Anweisungen

In dieser Aufgabe werden Sie grundlegende KQL-Anweisungen erstellen.

>**Wichtig:** Löschen Sie bei jeder Abfrage die vorherige Anweisung aus dem Abfragefenster oder öffnen Sie ein neues Abfragefenster, indem Sie **+** nach der zuletzt geöffneten Registerkarte (bis zu 25) auswählen.

1. Die folgende Anweisung demonstriert den Operator **Suchen**, der alle Spalten der Tabelle nach dem Wert durchsucht.

1. Ändern Sie im Abfragefenster den *Zeitbereich* in **Letzte 30 Minuten**.

1. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus:

    ```KQL
    search "location"
    ```

    >**Hinweis:** Die Verwendung des *Suchoperators* ohne bestimmte Tabellen oder qualifizierende Klauseln ist weniger effizient als tabellenspezifische und spaltenspezifische Textfilterung.

1. Die folgende Anweisung demonstriert die **Suche** über die in der **in**-Klausel angegebenen Tabellen. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    search in (SecurityEvent,App*) "new"
    ```

1. Ändern Sie im Abfragefenster den *Zeitbereich* auf **Letzte 24 Stunden**.

1. Die folgenden Anweisungen demonstrieren den **where** Operator, der nach einem bestimmten Prädikat filtert. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    >**Wichtig:** Sie sollten **Ausführen** wählen, nachdem Sie jede Abfrage aus den folgenden Codeblöcken eingegeben haben.

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    ```

    >**Hinweis:** Der *Zeitbereich* zeigt jetzt *In der Abfrage gesetzt* an, da wir mit der Spalte „TimeGenerated“ filtern.

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) and EventID == 4624
    ```

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    | where EventID == 4624  
    | where AccountType =~ "user"
    ```

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) and EventID in (4624, 4625)
 
    ```

1. Die folgende Anweisung demonstriert die Verwendung der **let**-Anweisung zur Deklaration von *Variablen*. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    let timeOffset = 1h;
    let discardEventId = 4688;
    SecurityEvent
    | where TimeGenerated > ago(timeOffset*2) and TimeGenerated < ago(timeOffset)
    | where EventID != discardEventId
    ```

1. Die folgende Anweisung demonstriert die Verwendung der **let**-Anweisung zur Deklaration von einer *dynamischen Liste*. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    let suspiciousAccounts = datatable(account: string) [
      @"NA\timadmin", 
      @"NT AUTHORITY\SYSTEM"
    ];
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    | where Account in (suspiciousAccounts)
    ```

    >**Tipp:** Sie können die Abfrage ganz einfach neu formatieren, indem Sie die Ellipse (…) im Abfragefenster markieren und **Abfrage formatieren** wählen.

1. Die folgende Anweisung demonstriert die Verwendung der **let**-Anweisung zur Deklaration von einer *dynamischen Liste*. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    let LowActivityAccounts =
        SecurityEvent 
        | summarize cnt = count() by Account 
        | where cnt < 1000;
    LowActivityAccounts | where Account contains "sql"
    ```

1. Ändern Sie im Abfragefenster den **Zeitbereich** auf **Letzte Stunde**. Dies wird unsere Ergebnisse für die folgenden Anweisungen einschränken.

1. Die folgende Anweisung demonstriert den Operator **Extend**-Operator, der eine berechnete Spalte erstellt und der Ergebnismenge hinzufügt. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) 
    | where ProcessName != "" and Process != "" 
    | extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process))
    ```

1. Die folgende Anweisung demonstriert den Operator **Order by**, der die Zeilen der Eingabetabelle nach einer oder mehreren Spalten in aufsteigender oder absteigender Reihenfolge sortiert. Der Operator **Order by** ist ein Alias für den Operator **Sortieren nach**. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) 
    | where ProcessName != "" and Process != "" 
    | extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process)) 
    | order by StartDir desc, Process asc
    ```

1. Die folgenden Anweisungen demonstrieren den **Project**-Operator, der die einzufügenden Spalten in der angegebenen Reihenfolge auswählt. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) 
    | where ProcessName != "" and Process != "" 
    | extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process)) 
    | order by StartDir desc, Process asc 
    | project Process, StartDir
    ```

1. Die folgenden Anweisungen demonstrieren den **project-away**-Operator, der die Spalten auswählt, die von der Ausgabe ausgeschlossen werden sollen. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) 
    | where ProcessName != "" and Process != "" 
    | extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process)) 
    | order by StartDir desc, Process asc 
    | project-away ProcessName
    ```

### Aufgabe 3: Analysieren von Ergebnissen in KQL mit dem summarize-Operator

In dieser Aufgabe erstellen Sie KQL-Anweisungen zum Aggregieren von Daten. **Summarize** gruppiert die Zeilen gemäß den **by** Group-Spalten und berechnet Aggregationen über jede Gruppe.

1. Die folgende Anweisung demonstriert die **count()**-Funktion, die eine Zählung der Gruppe zurückgibt. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) and EventID == 4688  
    | summarize count() by Process, Computer
    ```

1. Die folgende Anweisung demonstriert die **count()**-Funktion, aber in diesem Beispiel benennen wir die Spalte mit *cnt*. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) and EventID == 4624  
    | summarize cnt=count() by AccountType, Computer
    ```

1. Die folgende Anweisung demonstriert die **dcount()**-Funktion, die eine ungefähre Anzahl der Gruppenelemente zurückgibt. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    | summarize dcount(IpAddress)
    ```

1. Die folgende Anweisung ist eine Regel zur Erkennung von Fehlern aufgrund eines ungültigen Kennworts bei mehreren Anwendungen für dasselbe Konto. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    let timeframe = 30d;
    let threshold = 1;
    SigninLogs
    | where TimeGenerated >= ago(timeframe)
    | where ResultDescription has "Invalid password"
    | summarize applicationCount = dcount(AppDisplayName) by UserPrincipalName, IPAddress
    | where applicationCount >= threshold
    ```

1. Die folgende Anweisung demonstriert die **arg_max()** Funktion, die einen oder mehrere Ausdrücke zurückgibt, wenn das Argument maximiert ist. Die folgende Anweisung gibt die neueste Zeile aus der SecurityEvent-Tabelle für den Computer „SQL10.NA.contosohotels.com“ zurück. Mit dem Sternchen (*) in der arg_max-Funktion werden alle Spalten für die Zeile angefordert. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where Computer == "SQL10.na.contosohotels.com"
    | summarize arg_max(TimeGenerated,*) by Computer
    ```

1. Die folgende Anweisung demonstriert die **arg_min()**-Funktion, die einen oder mehrere Ausdrücke zurückgibt, wenn das Argument minimiert ist. In dieser Anweisung wird das älteste SecurityEvent für den Computer „SQL10.NA.contosohotels.com“ als Resultset zurückgegeben. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where Computer == "SQL10.na.contosohotels.com"
    | summarize arg_min(TimeGenerated,*) by Computer
    ```

1. Die folgenden Aussagen zeigen, wie wichtig es ist, die Ergebnisse auf der Grundlage der Reihenfolge der *Pipe* zu verstehen. Geben Sie im Abfragefenster die folgende Abfrage ein, und führen Sie jede Abfrage einzeln aus: 

    1. **Abfrage 1** enthält Konten, deren letzte Aktivität eine Anmeldung war. Zuerst wird die SecurityEvent-Tabelle zusammengefasst, dann wird die neueste Zeile für jedes Konto zurückgegeben. Danach werden nur Zeilen zurückgegeben, deren EventID 4624 (Anmeldung) lautet.

        ```KQL
        SecurityEvent  
        | summarize arg_max(TimeGenerated, *) by Account 
        | where EventID == 4624  
        ```

    1. **Abfrage 2** enthält die neueste Anmeldung für Konten, die angemeldet sind. Die SecurityEvent-Tabelle wird nach EventID 4624 gefiltert. Dann werden diese Ergebnisse nach Konto für die Zeile mit der neuesten Anmeldung zusammengefasst.

        ```KQL
        SecurityEvent  
        | where EventID == 4624  
        | summarize arg_max(TimeGenerated, *) by Account
        ```

    >**Hinweis:** Sie können auch die „Gesamt-CPU“ und die „Für die verarbeitete Abfrage verwendeten Daten“ überprüfen, indem Sie den Link „Abfragedetails“ unten rechts auswählen und die Daten zwischen den beiden Aussagen vergleichen.

1. Die folgende Anweisung demonstriert die **make_list()**-Funktion, die eine *Liste* mit allen Werten innerhalb der Gruppe zurückgibt. Diese KQL-Abfrage filtert zuerst die EventID mit dem where-Operator. Danach sind die Ergebnisse für jeden Computer ein JSON-Array aus Konten. Das resultierende JSON-Array enthält doppelte Konten. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    | where EventID == 4624  
    | summarize make_list(Account) by Computer
    ```

1. Die folgende Anweisung demonstriert die **make_set()**-Funktion, die eine Menge von *Distinct*-Werten innerhalb der Gruppe zurückgibt. Diese KQL-Abfrage filtert zuerst die EventID mit dem where-Operator. Danach sind die Ergebnisse für jeden Computer ein JSON-Array aus eindeutigen Konten. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    | where EventID == 4624  
    | summarize make_set(Account) by Computer
    ```


### Aufgabe 4: Erstellen von Visualisierungen in KQL mit dem render-Operator

In dieser Aufgabe werden Sie die Erzeugung von Visualisierungen mit KQL-Anweisungen verwenden.

1. Die folgende Anweisung demonstriert den **render**-Operator (der die Ergebnisse als grafische Ausgabe rendert) anhand einer **Balkendiagramm**-Visualisierung. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    | summarize count() by Account
    | render barchart
    ```

1. Die folgende Anweisung demonstriert den **render**-Operator zur Visualisierung von Ergebnissen mit einer Zeitreihe. Die **bin()**-Funktion rundet alle Werte in einem Zeitrahmen und gruppiert sie. Sie wird häufig in Kombination mit **summarize** verwendet. Wenn Sie einen unregelmäßig verteilten Satz von Werten haben, werden die Werte in einen kleineren Satz mit spezifischen Werten gruppiert. Durch das Kombinieren der generierten Ergebnisse und der Pipe zu einem **render**-Operator mit einem **Zeitdiagrammtyp** erhalten Sie eine Visualisierung der Zeitreihe. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    | summarize count() by bin(TimeGenerated, 1m)
    | render timechart
    ```


### Aufgabe 5: Erstellen von Anweisungen mit mehreren Tabellen in KQL

In dieser Aufgabe erstellen Sie KQL-Anweisungen mit mehreren Tabellen.

1. Ändern Sie im Abfragefenster den **Zeitbereich** auf **Letzte Stunde**. Dies wird unsere Ergebnisse für die folgenden Anweisungen einschränken.

1. Die folgende Anweisung demonstriert den **Union**-Operator, der zwei oder mehr Tabellen verwendet und alle ihre Zeilen zurückgibt. Es ist wichtig, dass Sie grundlegendes Verständnis darüber haben, wie Ergebnisse mit dem Pipezeichen übergeben und beeinflusst werden. Geben Sie die folgenden Anweisungen in das Abfragefenster ein und wählen Sie für jede einzelne Abfrage **Ausführen**, um die Ergebnisse anzuzeigen: 

    1. **Abfrage 1** gibt alle Zeilen von SecurityEvent und alle Zeilen von SigninLogs zurück.

        ```KQL
        SecurityEvent  
        | union SigninLogs  
        ```

    1. **Abfrage 2** gibt eine Zeile und eine Spalte zurück, nämlich die Anzahl aller Zeilen von SecurityEvent und aller Zeilen von SigninLogs.

        ```KQL
        SecurityEvent  
        | union SigninLogs  
        | summarize count() 
        ```

    1. **Abfrage 3** gibt alle Zeilen von SecurityEvent und eine Zeile für SigninLogs zurück. Die letzte Zeile für „SigninLogs“ enthält die zusammengefasste Anzahl der Zeilen.

        ```KQL
        SecurityEvent  
        | union (SigninLogs | summarize count() | project count_)
        ```

    >**Hinweis:** Die „leere Zeile“ in den Ergebnissen zeigt die zusammengefasste Anzahl von SigninLogs an.

1. Die folgende Anweisung demonstriert die Unterstützung des **Union**-Operators zur Vereinigung mehrerer Tabellen mit Platzhaltern. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    union App*  
    | summarize count() by Type
    ```

1. Die folgende Anweisung demonstriert den **Join**-Operator, der die Zeilen von zwei Tabellen zu einer neuen Tabelle zusammenführt, indem er die Werte der angegebenen Spalte(n) aus jeder Tabelle abgleicht. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where EventID == 4624 
    | summarize LogOnCount=count() by  EventID, Account
    | project LogOnCount, Account
    | join kind = inner( 
     SecurityEvent  
    | where EventID == 4634 
    | summarize LogOffCount=count() by  EventID, Account
    | project LogOffCount, Account
    ) on Account
    ```

    >**Wichtig:** Die erste in der Verknüpfung (Join) angegebene Tabelle wird als linke Tabelle betrachtet. Die Tabelle nach dem **join**-Operator ist die rechte Tabelle. Wenn Sie mit Spalten aus den Tabellen arbeiten, werden die Namen $left.Column und $right.Column verwendet, um zu unterscheiden, auf welche Tabellen die Spalten verweisen. Der **join**-Operator unterstützt eine umfangreiche Zahl von Join-Typen (Verknüpfungen): fullouter, inner, innerunique, leftanti, leftantisemi, leftouter, leftsemi, rightanti, rightantisemi, rightouter, rightsemi.

1. Ändern Sie im Abfragefenster den **Zeitbereich** auf **Letzte 24 Stunden**.

### Aufgabe 6: Arbeiten mit Zeichenfolgendaten in KQL

In dieser Aufgabe arbeiten Sie mit strukturierten und unstrukturierten Zeichenfolgenfeldern mit KQL-Anweisungen.

1. Die folgende Anweisung demonstriert die **extract** -Funktion, die eine Übereinstimmung mit einem regulären Ausdruck aus einer Quellzeichenfolge ermittelt. Sie haben die Möglichkeit, die extrahierte Teilzeichenfolge in den angegebenen Typ zu konvertieren. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    print extract("x=([0-9.]+)", 1, "hello x=45.6|wo") == "45.6"
    ```

1. Die folgenden Anweisungen verwenden die **extract**-Funktion, um den Kontonamen aus dem Feld „Account“ der Tabelle „SecurityEvent“ auszulesen. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SecurityEvent  
    | where EventID == 4672 and AccountType == 'User' 
    | extend Account_Name = extract(@"^(.*\\)?([^@]*)(@.*)?$", 2, tolower(Account))
    | summarize LoginCount = count() by Account_Name
    | where Account_Name != "" 
    | where LoginCount < 10
    ```

1. Die folgende Anweisung demonstriert den **Parse**-Operator, der einen Zeichenfolgenausdruck auswertet und seinen Wert in eine oder mehrere berechnete Spalten umwandelt. Ermöglicht die Strukturierung unstrukturierter Daten. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    let Traces = datatable(EventText:string)
    [
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=23, lockTime=02/17/2016 08:40:01, releaseTime=02/17/2016 08:40:01, previousLockTime=02/17/2016 08:39:01)",
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=15, lockTime=02/17/2016 08:40:00, releaseTime=02/17/2016 08:40:00, previousLockTime=02/17/2016 08:39:00)",
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=20, lockTime=02/17/2016 08:40:01, releaseTime=02/17/2016 08:40:01, previousLockTime=02/17/2016 08:39:01)",
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=22, lockTime=02/17/2016 08:41:01, releaseTime=02/17/2016 08:41:00, previousLockTime=02/17/2016 08:40:01)",
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=16, lockTime=02/17/2016 08:41:00, releaseTime=02/17/2016 08:41:00, previousLockTime=02/17/2016 08:40:00)"
    ];
    Traces   
    | parse EventText with * "resourceName=" resourceName ", totalSlices=" totalSlices:long * "sliceNumber=" sliceNumber:long * "lockTime=" lockTime ", releaseTime=" releaseTime:date "," * "previousLockTime=" previousLockTime:date ")" *  
    | project resourceName, totalSlices, sliceNumber, lockTime, releaseTime, previousLockTime
    ```

>**Wichtig:** Die folgenden Abfragen liefern derzeit keine Ergebnisse in der für diese Übung verwendeten Lademo-Umgebung. Es wurden Einträge in der Tabelle *SigninLogs* entfernt. Die KQL-Abfragen veranschaulichen jedoch wichtige Konzepte und Anwendungsfälle, daher nehmen Sie sich Zeit, diese zu überprüfen.

1. Die folgende Anweisung demonstriert die Arbeit mit **dynamischen** Feldern, die etwas Besonderes sind, da sie jeden Wert anderer Datentypen annehmen können. In diesem Beispiel ist das Feld „DeviceDetail“ aus der Tabelle SigninLogs vom Typ **dynamisch**. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SigninLogs 
    | extend OS = DeviceDetail.operatingSystem
    ```

1. Das folgende Beispiel zeigt, wie gepackte Felder für SigninLogs aufgeteilt werden können. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus:

    ```KQL
    SigninLogs 
    | extend OS = DeviceDetail.operatingSystem, Browser = DeviceDetail.browser 
    | extend StatusCode = tostring(Status.errorCode), StatusDetails = tostring(Status.additionalDetails) 
    | extend Date = startofday(TimeGenerated) 
    | summarize count() by Date, Identity, UserDisplayName, UserPrincipalName, IPAddress, ResultType, ResultDescription, StatusCode, StatusDetails 
    | sort by Date
    ```

    >**Wichtig:** Obwohl der dynamische Typ ähnlich wie JSON aussieht, kann er Werte enthalten, die das JSON-Modell nicht darstellt, weil sie in JSON nicht existieren. Daher werden bei der Serialisierung dynamischer Werte in eine JSON-Darstellung Werte, die JSON nicht darstellen kann, in Zeichenfolgenwerten serialisiert. 

1. Die folgenden Anweisungen demonstrieren Operatoren zur Manipulation von JSON, die in Zeichenfolgenfeldern gespeichert sind. Viele Protokolle übertragen Daten im JSON-Format, weshalb Sie wissen müssen, wie Sie JSON-Daten in abfragbare Felder umwandeln können. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

    ```KQL
    SigninLogs 
    | extend AuthDetails =  parse_json(AuthenticationDetails) 
    | extend AuthMethod =  AuthDetails[0].authenticationMethod 
    | extend AuthResult = AuthDetails[0].["authenticationStepResultDetail"] 
    | project AuthMethod, AuthResult, AuthDetails 
    ```

1. Die folgende Anweisung demonstriert den **mv-expand**-Operator, der dynamische Arrays in Zeilen umwandelt (mehrwertige Erweiterung).

    ```KQL
    SigninLogs 
    | mv-expand AuthDetails = parse_json(AuthenticationDetails) 
    | project AuthDetails
    ```

1. Erweitern Sie die erste Zeile, indem Sie „>“ und dann erneut neben *AuthDetails* wählen, um die erweiterten Ergebnisse zu überprüfen.

1. Die folgende Anweisung demonstriert den **mv-apply**-Operator, der eine Unterabfrage auf jeden Datensatz anwendet und die Vereinigung der Ergebnisse aller Unterabfragen zurückgibt.

    ```KQL
    SigninLogs 
    | mv-apply AuthDetails = parse_json(AuthenticationDetails) on
    (where AuthDetails.authenticationMethod == "Password")
    ```

1. Eine **Funktion** ist eine Protokollabfrage, die in anderen Protokollabfragen mit dem gespeicherten Namen als Befehl verwendet werden kann. Um eine **Funktion** zu erstellen, klicken Sie nach der Ausführung Ihrer Abfrage auf die Schaltfläche **Speichern** und wählen dann **Speichern als Funktion** aus der Dropdown-Liste. Geben Sie den gewünschten Namen (zum Beispiel: *PrivLogins*) in das Feld **Funktionsname** ein und geben Sie eine **Legacy-Kategorie** ein (zum Beispiel: *Allgemein*) und wählen Sie **Speichern**. Die Funktion wird in KQL unter dem Alias der Funktion verfügbar sein:

    >**Hinweis:** In der Lademo-Umgebung, die für diese Übung verwendet wurde, ist dies nicht möglich, da Ihr Konto nur über Leserechte verfügt, aber es ist ein wichtiges Konzept, um Ihre Abfragen effizienter und effektiver zu gestalten. 

    ```KQL
    PrivLogins  
    ```

## Damit haben Sie das Lab beendet.

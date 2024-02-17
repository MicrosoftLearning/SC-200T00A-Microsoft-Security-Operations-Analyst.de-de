# Modul 4: Erstellen von Abfragen für Microsoft Sentinel mithilfe von Kusto Query Language (KQL)

**Hinweis:** Der erfolgreiche Abschluss dieser Demo hängt davon ab, alle Schritte im  [Dokument](00-prerequisites.md) „Voraussetzungen“ abzuschließen. 

## Zugriff auf KQL-Testbereich

In dieser Aufgabe erhalten Sie Zugriff auf eine Log Analytics-Umgebung, in der Sie das Schreiben von KQL-Anweisungen üben können.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Browser zu https://aka.ms/lademo. Melden Sie sich mit den Anmeldeinformationen des MOD-Administrators an 

1. Erkunden Sie die verfügbaren Tabellen auf der Registerkarte auf der linken Seite des Bildschirms.

1. Geben Sie im Abfrage-Editor die folgende Abfrage ein und wählen Sie die Schaltfläche „Ausführen“.  Die Abfrageergebnisse sollten im unteren Fenster angezeigt werden.

    ```KQL
    SecurityEvent
    ```

1. Wählen Sie **>** neben dem ersten Datensatz, um die Informationen für die Zeile zu erweitern.

### Aufgabe 2: Ausführen grundlegender KQL-Anweisungen

In dieser Aufgabe werden Sie grundlegende KQL-Anweisungen erstellen.

1. Der `search`-Operator ermöglicht die Suche mit mehreren Tabellen und Spalten. In der folgenden Abfrage wird die Verwendung des `search`-Operators demonstriert.

```KQL
search "err" 

search in (SecurityEvent,SecurityAlert,A*) "err"
```

1. Der `where`-Operator filtert eine Tabelle auf die Teilmenge der Zeilen, die einem Prädikat entsprechen. In der folgenden Abfrage wird die Verwendung des `where`-Operators demonstriert.

```KQL
SecurityEvent | where EventID in (4624, 4625)

SecurityEvent 
| where TimeGenerated > ago(1d) 

SecurityEvent 
| where TimeGenerated > ago(1h) and EventID == "4624" 

SecurityEvent 
| where TimeGenerated > ago(1h) 
| where EventID == 4624 
| where AccountType =~ "user" 
```

1. Die folgende Anweisung demonstriert die Verwendung des `let`-Operators zur Deklaration von Variablen. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

```KQL
let timeOffset = 7d;
let discardEventId = 4688;
SecurityEvent
| where TimeGenerated > ago(timeOffset*2) and TimeGenerated < ago(timeOffset)
| where EventID != discardEventId
```

1. Die folgende Anweisung demonstriert die Verwendung der `let`-Anweisung zur Deklaration einer dynamischen Liste. Geben Sie im Abfragefenster die folgende Anweisung ein, und wählen Sie dann **Ausführen** aus: 

```KQL
let suspiciousAccounts = datatable(account: string) [
    @"\administrator", 
    @"NT AUTHORITY\SYSTEM"
];
SecurityEvent | where Account in (suspiciousAccounts)
```

1. Die folgende Anweisung demonstriert die Suche nach Datensätzen in allen Tabellen und Spalten innerhalb des im Abfragefenster angezeigten Zeitbereichs. Bevor Sie dieses Skript ausführen, ändern Sie den Zeitbereich im Abfragefenster auf „Letzte Stunde“. Geben Sie die folgende Abfrage ein, und wählen Sie **Ausführen** aus:

```KQL
search "err"
```

**Warnung:** Stellen Sie sicher, dass Sie den Zeitbereich für die nächsten Skripte wieder auf „Letzte 24 Stunden“ zurücksetzen.

### Visualisierungen in KQL mit dem render-Operator erstellen

In dieser Aufgabe werden Sie die Erzeugung von Visualisierungen mit KQL-Anweisungen verwenden.

1. Die folgende Anweisung demonstriert den render-Operator, der die Ergebnisse mit einem Balkendiagramm visualisiert. Im Abfragefenster. Geben Sie die folgende Abfrage ein, und wählen Sie **Ausführen** aus: 

```KQL
SecurityEvent 
| summarize count() by Account
| render barchart
```

1. Die folgende Anweisung demonstriert die Renderfunktion, die die Ergebnisse mit einer Zeitreihe visualisiert.

Die bin()-Funktion rundet Werte auf eine ganzzahliges Mehrfaches der angegebenen Intervallgröße ab.  Sie wird häufig in Kombination mit „summarize by“ verwendet. Wenn Sie einen unregelmäßig verteilten Satz von Werten haben, werden die Werte in einen kleineren Satz mit spezifischen Werten gruppiert.  Durch Kombinieren der generierten Zeitreihe und der Pipe zu einem render-Operator mit einem Zeitdiagrammtyp erhalten Sie eine Visualisierung der Zeitreihe. Im Abfragefenster. Geben Sie die folgende Abfrage ein, und wählen Sie **Ausführen** aus: 

```KQL
SecurityEvent 
| summarize count() by bin(TimeGenerated, 1d) 
| render timechart
```

## Damit haben Sie die Demo beendet

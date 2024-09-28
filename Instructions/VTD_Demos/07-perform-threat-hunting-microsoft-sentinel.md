# Modul 7: Bedrohungssuche in Microsoft Sentinel

**Hinweis:** Der erfolgreiche Abschluss dieser Demo hängt davon ab, alle Schritte im  [Dokument](00-prerequisites.md) „Voraussetzungen“ abzuschließen.

**Wichtig:** Diese Demo ist für VTD-5002-FY25 nicht erforderlich.

## Erstellen einer Bedrohungssuchabfrage

In dieser Aufgabe erstellen Sie eine Bedrohungssuchabfrage, setzen ein Lesezeichen für ein Ergebnis und erstellen einen Livestream.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Edge-Browser zum Azure-Portal unter https://portal.azure.com.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren Microsoft Sentinel-Arbeitsbereich aus.

1. Wählen Sie **Protokolle** aus. 

1. Geben Sie die folgende KQL-Anweisung in das Feld Neue Abfrage 1 ein:

```KQL
let lookback = 2d;
DeviceEvents | where TimeGenerated >= ago(lookback) 
| where ActionType == "DnsQueryResponse"
| extend c2 = substring(tostring(AdditionalFields.DnsQueryString),0,indexof(tostring(AdditionalFields.DnsQueryString),"."))
| where c2 startswith "sub"
| summarize count() by bin(TimeGenerated, 3m), c2
| where count_ > 5
| render timechart 
```

1. Ziel dieser Aussage ist es, eine Visualisierung bereitzustellen, die konsistent überprüft, ob ein C2-Beaconing versendet wird.  Nehmen Sie sich die Zeit, um beispielsweise die Einstellung „3m“ auf „30s“ anzupassen.  Ändern Sie die Einstellung „count_ > 5“ auf andere Schwellenwerte, um die Auswirkungen zu beobachten.

1. Sie haben nun DNS-Anforderungen identifiziert, die an einen C2-Server gesendet werden.  Ermitteln Sie als Nächstes, für welche Geräte Beaconing vorgenommen wird.  Geben Sie die folgende KQL-Anweisung ein:

```KQL
let lookback = 2d;
DeviceEvents | where TimeGenerated >= ago(lookback) 
| where ActionType == "DnsQueryResponse"
| extend c2 = substring(tostring(AdditionalFields.DnsQueryString),0,indexof(tostring(AdditionalFields.DnsQueryString),".")) 
| where c2 startswith "sub"
| summarize cnt=count() by bin(TimeGenerated, 5m), c2, DeviceName
| where cnt > 15
```

**Hinweis** Die generierten Protokolldaten stammen nur vom integrierten Gerät.

1. Schließen Sie das Fenster *Protokolle*, indem Sie oben rechts im Fenster auf **X** klicken und dann auf **OK**, um die Änderungen zu verwerfen. 

1. Wählen Sie die Seite **Hunting** im Bereich „Bedrohungsmanagement“ des Microsoft Sentinel-Portals aus.

1. Wählen Sie aus der Befehlsleiste **Neue Abfrage** aus.

1. Geben Sie im Fenster *Benutzerdefinierte Abfrage erstellen* für den *Namen* **C2 Hunt** ein.

1. Geben Sie für die *Benutzerdefinierte Abfrage* die folgende KQL-Anweisung ein:

```KQL
let lookback = 2d;
DeviceEvents | where TimeGenerated >= ago(lookback) 
| where ActionType == "DnsQueryResponse"
| extend c2 = substring(tostring(AdditionalFields.DnsQueryString),0,indexof(tostring(AdditionalFields.DnsQueryString),"."))
| where c2 startswith "sub"
| summarize cnt=count() by bin(TimeGenerated, 5m), c2, DeviceName
| where cnt > 15
```

1. Scrollen Sie nach unten, und wählen Sie unter *Entitätszuordnung (Vorschau)* Folgendes aus:

    - In der Dropdownliste *Entitätstyp* wählen Sie **Host** aus.
    - In der Dropdownliste *Bezeichner* wählen Sie **HostName** aus.
    - Wählen Sie für die Dropdownliste *Wert* die Option **DeviceName** aus.

1. Scrollen Sie nach unten und wählen Sie unter *Taktiken und Techniken* **Command and Control** und klicken Sie dann auf **Erstellen**, um die Bedrohungssuchabfrage zu erstellen.

1. Suchen Sie im Blatt *Microsoft Sentinel – Hunting* nach der Abfrage, die Sie soeben in der Liste erstellt haben, *C2 Hunt*.

1. Wählen Sie **C2 Hunt** aus der Liste aus.

1. Scrollen Sie im rechten Bereich nach unten, und wählen Sie die Schaltfläche **Abfrage ausführen** aus.

1. Die Anzahl der Ergebnisse wird im mittleren Bereich unter der Spalte *Ergebnisse* angezeigt. Alternativ können Sie nach oben scrollen, um die Anzahl über dem Feld *Ergebnisse* anzuzeigen.

1. Wählen Sie **Ergebnisse anzeigen** aus.

1. Wählen Sie die erste Zeile in den Ergebnissen aus. 

1. Wählen Sie **Lesezeichen hinzufügen** aus.

1. Wählen Sie im angezeigten Bereich **Erstellen** aus.

1. Kehren Sie zur Seite „Hunting“ im Microsoft Sentinel-Portal zurück.

1. Wählen Sie die Registerkarte **Textmarke** aus.

1. Wählen Sie die Textmarke in der Ergebnisliste aus.

1. Wählen Sie im Flyoutbereich **Untersuchen** aus.

1. Sehen Sie sich das Untersuchungsdiagramm an.

1. Kehren Sie zur Seite „Hunting“ im Microsoft Sentinel-Portal zurück.

1. Wählen Sie die Registerkarte **Abfragen** aus.

1. Wählen Sie die Abfrage **C2 Hunt** aus.

1. Wählen Sie die Ellipse **...** am Ende der Zeile aus, um das Kontextmenü zu öffnen.

1. Wählen Sie **Zu Livestream hinzufügen** aus.

## Sie haben die Demo abgeschlossen.
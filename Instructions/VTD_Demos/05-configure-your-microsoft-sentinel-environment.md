# Modul 5: Konfigurieren Ihrer Microsoft Sentinel-Umgebung

**Hinweis:** Der erfolgreiche Abschluss dieser Demo hängt davon ab, alle Schritte im  [Dokument](00-prerequisites.md) „Voraussetzungen“ abzuschließen.

**Wichtig:** Diese Demo ist für VTD-5002-FY25 nicht erforderlich.

## Erkunden der Microsoft Sentinel-Oberfläche

1. Kehren Sie zu der Microsoft Sentinel-Instanz zurück, die Sie beim Ausfüllen des [Abschnitts „Voraussetzungen“](00-prerequisites.md#deploy-azure-sentinel-workspace-for-demo-in-module-4) erstellt haben.

1. Navigieren Sie durch den neu erstellten Microsoft Sentinel-Arbeitsbereich, um sich mit den Optionen der Benutzeroberfläche vertraut zu machen.

## Erstellen einer Watchlist

In dieser Aufgabe erstellen Sie eine Watchlist.

1. Geben Sie `Notepad` in das Suchfeld unten auf dem Bildschirm ein.  Wählen Sie aus den Ergebnissen **Notepad** aus.

1. Tippen Sie `Hostname` und dann drücken Sie die Eingabetaste, um eine neue Zeile zu beginnen.

1. Fügen Sie die folgenden Hostnamen in die Zeilen 2 bis 6 ein:
    ```
    Host1
    Host2
    Host3
    Host4
    Host5
    ```

1. Wählen Sie aus dem Menü **Datei – Speichern unter** aus, benennen Sie die Datei `HighValue.csv`.  Ändern Sie dann den Dateityp in **Alle Dateien(*.*)**.  Klicken Sie dann auf **Speichern**.

1. Schließen Sie den Editor.

1. Wählen Sie in Microsoft Sentinel im Bereich **Meine Watchlists** die Option **Watchlist** aus.

1. Wählen Sie in der Befehlsleiste **Neue hinzufügen** aus.

1. Geben Sie im Assistenten der Watchlist folgende Daten ein:  Name: HighValueHosts  Beschreibung: High Value Hosts  Watchlist Alias: HighValueHosts

1. Wählen Sie die Option **Weiter: Quelle >** aus.

1. Suchen Sie die soeben erstellte Datei `HighValue.csv`. 

1. Sobald die CSV-Datei geladen ist, wählen Sie aus der Dropdownliste **SearchKey** den Eintrag **Hostname** aus.

1. Wählen Sie **Weiter: Überprüfen und erstellen** aus.

1. Klicken Sie auf **Erstellen**.

1. Der Bildschirm kehrt zur Liste der Watchlists zurück.

1. Wählen Sie Ihre neue Watchlist aus.  Wählen Sie auf der rechten Registerkarte **In Log Analytics anzeigen** aus.

1. Die folgende KQL-Anweisung wird automatisch mit den angezeigten Ergebnissen ausgeführt.

```KQL
_GetWatchlist('HighValueHosts')
```
**Hinweis:** Es kann eine Minute dauern, bis der Import abgeschlossen ist.

Sie können nun _GetWatchlist(‚HighValueHosts‘) in Ihren eigenen KQL-Anweisungen verwenden, um auf die Liste zuzugreifen. Die zu referenzierende Spalte wäre *Hostname*.

## Erstellen eines Bedrohungsindikators.

In dieser Aufgabe erstellen Sie einen Indikator.

1. Wählen Sie in Microsoft Sentinel im Bereich **Threat Management** die Option **Threat Intelligence** aus.

1. Wählen Sie in der Befehlsleiste **Neue hinzufügen** aus.

1. Überprüfen Sie die verfügbaren Indikatortypen in der Dropdownliste „Typen“.  Wählen Sie dann **Domänenname**. Geben Sie Ihre Initialen in das Feld „Domäne“ ein. Ein Beispiel wäre „fmg.com“.

1. Wählen Sie beim Bedrohungstyp  **+ Hinzufügen** aus und kopieren Sie **Schädliche Aktivität** in das Feld hinein.

1. Geben Sie als Namen denselben Wert ein, den Sie für die Domäne verwendet haben. Ein Beispiel wäre „fmg.com“.

1. Setzen Sie das Feld **Gültig ab** auf das aktuelle Datum.

1. Wählen Sie **Übernehmen**.

**Hinweis:** Es kann eine Minute dauern, bis der Indikator angezeigt wird.

1. Wählen Sie im Bereich „Allgemein“ die Option **Protokolle** aus.  Möglicherweise müssen Sie die Option „Abfragen immer anzeigen“ deaktivieren, um zum Abfragefenster zu gelangen.

1. Führen Sie die folgende KQL-Anweisung aus.

```KQL
ThreatIntelligenceIndicator 
```
Scrollen Sie nach rechts, um die Spalte DomainName zu sehen. Sie können auch die folgende KQL-Anweisung ausführen, um nur die Spalte DomainName anzuzeigen.  

```KQL
ThreatIntelligenceIndicator 
| project DomainName
```
## Sie haben die Demo beendet.
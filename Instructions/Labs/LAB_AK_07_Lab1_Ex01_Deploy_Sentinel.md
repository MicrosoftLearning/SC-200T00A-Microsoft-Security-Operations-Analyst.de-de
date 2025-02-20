---
lab:
  title: Übung – Konfigurieren Ihrer Microsoft Sentinel-Umgebung
  module: Learning Path 7 - Configure your Microsoft Sentinel environment
---

# Lernpfad 7 – Lab 1 – Übung 1: Konfigurieren Ihre Microsoft Sentinel-Umgebung

## Labszenario

Sie sind Security Operations Analyst in einem Unternehmen, das Microsoft Sentinel implementiert. Sie sind dafür verantwortlich, die Microsoft Sentinel-Umgebung so einzurichten, dass die Anforderungen des Unternehmens im Hinblick auf die Minimierung der Kosten sowie der Einhaltung der Compliancebestimmungen erfüllt werden, und die am besten verwaltbare Umgebung für Ihr Sicherheitsteam bereitzustellen, damit es seine täglichen Aufgaben erfüllen kann.

>**Wichtig:** Die Lab-Übungen für Lernpfad Nr. 7 befinden sich in einer *eigenständigen* Umgebung. Wenn Sie das Lab vor dem Abschluss verlassen, müssen Sie die Konfigurationen erneut ausführen.

### Geschätzte Zeit bis zum Abschluss dieses Labs: 30 Minuten

### Aufgabe 1: Erstellen eines Log Analytics-Arbeitsbereichs

Erstellen Sie einen Log Analytics-Arbeitsbereich, einschließlich der Regionsoption. Weitere Informationen zu [Onboarding in Microsoft Sentinel](https://learn.microsoft.com/azure/sentinel/quickstart-onboard).

1. Melden Sie sich beim virtuellen Computer **WIN1** als Administrator mit dem Kennwort **Pa55w.rd**an.

1. Navigieren Sie im Microsoft Edge-Browser zu der Azure-Portal unter <https://portal.azure.com>.
  
1. Kopieren Sie im Dialogfeld **Anmelden**das von Ihrem Labhostinganbieter bereitgestellte Mandanten-E-Mail-Konto für den Administrator, und fügen Sie es ein, und wählen Sie dann **Weiter** aus.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das von Ihrem Labhostinganbieter bereitgestellte Mandantenkennwort für den Administrator, und fügen Sie es ein, und wählen Sie dann **Anmelden** aus.

1. Geben Sie in der Suchleiste des Azure-Portals „Microsoft Sentinel“ ein, und wählen Sie dann

1. Wählen Sie **+ Erstellen** aus.

1. Klicken Sie auf **Create a new workspace** (Neuen Arbeitsbereich erstellen).

1. Wählen Sie **Neu erstellen** für die Ressourcengruppe aus.

1. Geben Sie *Defender-RG* ein und klicken Sie auf **OK**.

1. Geben Sie als Namen *defenderWorkspace* ein.

1. Sie können die Standardregion für den Arbeitsbereich beibehalten.

1. Wählen Sie **Überprüfen + Erstellen**, um den neuen Arbeitsbereich zu bestätigen.

1. Wählen Sie **Erstellen**, um den Arbeitsbereich bereitzustellen.

### Aufgabe 2: Bereitstellen von Microsoft Sentinel in einem Arbeitsbereich

Bereitstellen von Microsoft Sentinel in einem Arbeitsbereich.

1. Wenn die Bereitstellung des Arbeitsbereichs abgeschlossen ist, wählen Sie im „Brotkrumen“-Menü von Microsoft Azure die Option **Home** aus.

1. **Microsoft Sentinel** sollte im Abschnitt *Azure-Dienste* des Portals zusehen sein. Wählen Sie ihn aus.

1. Wählen Sie im oberen Menü **+ Erstellen** aus.

1. Wählen Sie den Arbeitsbereich aus, dem Sie Sentinel hinzufügen möchten (erstellt in Aufgabe 1).

1. Wählen Sie **Hinzufügen**.

### Aufgabe 3: Konfigurieren der Datenaufbewahrung

1. Wählen Sie im „Breadcrumb“-Menü von Microsoft Azure **Home**.

1. Geben Sie in der Suchleiste des Azure-Portals „Protokollanalyse“ ein und wählen Sie den in Aufgabe 1 erstellten Arbeitsbereich aus.

1. Erweitern Sie den Abschnitt *Einstellungen* im Navigationsmenü und wählen Sie **Nutzung und geschätzte Kosten**.

1. Wählen Sie **Datenaufbewahrung** aus den Menüelementen aus.

1. Ändern Sie den Daten-Aufbewahrungszeitraum auf **180 Tage**.

1. Wählen Sie **OK** aus.

### Aufgabe 4: Erstellen einer Watchlist

In dieser Aufgabe erstellen Sie eine Watchlist in Microsoft Sentinel.

1. Geben Sie *Notepad* in das Suchfeld am unteren Rand des Windows 10-Bildschirms ein. Wählen Sie aus den Ergebnissen **Notepad** aus.

1. Geben Sie *Hostname* ein und drücken Sie die Eingabetaste, um eine neue Zeile zu beginnen.

1. Kopieren Sie aus Zeile 2 des Notepads die folgenden Hostnamen, jeweils in eine andere Zeile:

    ```Notepad
    Host1
    Host2
    Host3
    Host4
    Host5
    ```

1. Wählen Sie im Menü **Datei – Speichern unter**, benennen Sie die Datei *HighValue.csv*, ändern Sie den Dateityp auf **Alle Dateien(*.*)** und wählen Sie **Speichern** aus. **Hinweis:** Die Datei kann im Ordner *Dokumente* gespeichert werden.

1. Schließen Sie den Editor.

1. Wählen Sie im „Breadcrumb“-Menü von Microsoft Azure **Home** aus.

1. **Microsoft Sentinel** sollte im Abschnitt *Azure-Dienste* des Portals zusehen sein. Wählen Sie ihn aus.

1. Wählen Sie in Microsoft Sentinel unter Konfiguration die Option **Watchlist** aus.

1. Wählen Sie in der Befehlsleiste **+ Neu** aus.

1. Geben Sie im Watchlist-Assistenten Folgendes ein:

    |Allgemeine Einstellung|Wert|
    |---|---|
    |Name|**HighValueHosts**|
    |Beschreibung|**High Value Hosts**|
    |Alias „Watchlist“|**HighValueHosts**|

1. Wählen Sie die Option **Weiter: Quelle >** aus.

1. Wählen Sie **Dateien suchen** unter *Datei hochladen* und suchen Sie die soeben erstellte Datei *HighValue.csv* aus.

1. Wählen Sie im Feld *SearchKey* **Hostname** aus.

1. Wählen Sie **Weiter: Überprüfen und erstellen** aus.

1. Überprüfen Sie die eingegebenen Einstellungen und wählen Sie **Erstellen** aus.

1. Der Bildschirm kehrt zur Seite Watchlist zurück.

1. Wählen Sie im Menü **Aktualisieren** aus, um die neue Watchlist anzuzeigen.

1. Wählen Sie die Watchlist *HighValueHosts* aus und wählen Sie auf der rechten Seite **In Logs anzeigen**.

    >**Wichtig:** Es kann bis zu zehn Minuten dauern, bis die Watchlist angezeigt wird. **Bitte fahren Sie mit der nächsten Aufgabe fort und führen Sie diesen Befehl im nächsten Lab aus**.

    >**Hinweis:** Sie können nun die _GetWatchlist(‚HighValueHosts’) in Ihren eigenen KQL-Anweisungen verwenden, um auf die Liste zuzugreifen. Die zu referenzierende Spalte wäre *Hostname*.

1. Schließen Sie das Fenster *Protokolle*, indem Sie das ‚x‘ oben rechts auswählen und wählen Sie **OK** aus, um die nicht gespeicherten Änderungen zu verwerfen.

### Aufgabe 5: Erstellen eines Bedrohungsindikator

In dieser Aufgabe erstellen Sie einen Indikator in Microsoft Sentinel.

1. Wählen Sie in Microsoft Sentinel im Bereich Bedrohungsmanagement die Option **Threat Intelligence** aus.

1. Wählen Sie in der Befehlsleiste **+ Neu hinzufügen** aus.

1. Wählen Sie das **TI-Objekt**aus.

1. Wählen Sie im Dropdownmenü *Objekttyp* die Option **Indikator** aus.

1. Wählen Sie die Dropdown-Liste **+ Neu beobachtbar** aus und wählen Sie **Domainname** aus.

1. Geben Sie für Domain einen Domainnamen ein, zum Beispiel *contoso.com*.

1. Geben Sie für den **Namen** den gleichen Wert wie für die Domain ein.

1. Wählen Sie unter *Indikatorentypen* die Option **böswillige Aktivitäten** aus.

1. Setzen Sie das Feld **Gültig ab** auf das aktuelle Datum.

1. Scrollen Sie nach unten zur **Beschreibung** und geben Sie *Diese Domain ist als bösartig bekannt* ein.

1. Wählen Sie **Hinzufügen**.

1. Wählen Sie die Option **Logs** im Bereich *Allgemein* des Navigationsmenüs *Sentinel* aus. Eventuell können Sie die Option „Abfragen immer anzeigen“ deaktivieren und das Fenster *Abfragen* schließen, um die KQL-Anweisungen auszuführen.

    >**Hinweis:** Auf der Standardregisterkarte *Neue Abfrage 1* sollte die Abfrage **_GetWatchList('HighValueHosts')** weiterhin vorhanden sein und bei Ausführung nun Ergebnisse liefern.

1. Wählen Sie das Zeichen *+* aus, um eine neue Registerkarte für Abfragen zu erstellen.

1. Führen Sie die folgende KQL-Anweisung aus.

    ```KQL
    ThreatIntelligenceIndicator
    ```

    >**Hinweis:** Es kann bis zu fünf Minuten dauern, bis der Indikator angezeigt wird.

1. Scrollen Sie nach rechts, um die Spalte DomainName zu sehen. Sie können auch die folgende KQL-Anweisung ausführen, um nur die Spalte DomainName anzuzeigen.

    ```KQL
    ThreatIntelligenceIndicator 
    | project DomainName
    ```

### Aufgabe 6: Konfigurieren der Protokollaufbewahrung

In dieser Aufgabe ändern Sie die Aufbewahrungszeit für die Tabelle SecurityEvent.

1. Wählen Sie in Microsoft Sentinel unter *Konfiguration* die Option **Einstellungen** aus.

1. Wählen Sie **Arbeitsbereichseinstellungen** aus.

1. Wählen Sie im Arbeitsbereich Log Analytics unter dem Bereich *Einstellungen* die Option **Tabellen** aus.

1. Suchen Sie die Tabelle **SecurityEvent** und wählen Sie sie aus. Klicken Sie dann auf den Link mit den Auslassungspunkten (…).

    >**Hinweis:** Möglicherweise müssen Sie nach rechts scrollen, um den Link mit den Auslassungspunkten zu sehen.

1. Wählen Sie **Tabelle verwalten** aus.

1. Ändern Sie den *interaktiven Aufbewahrungszeitraum* auf **90 Tage**.

1. Setzen Sie den *gesamten Aufbewahrungszeitraum* auf **180 Tage** zurück (falls erforderlich). Beachten Sie, dass der *Archivierungszeitraum* jetzt auf *90 Tage* festgelegt ist, da *Azure Monitor* die verbleibenden 90 Tage der Gesamtspeicherdauer automatisch als kostengünstige Langzeitspeicherung behandelt.

1. Klicken Sie auf **Speichern**, um die Änderungen zu übernehmen.

## Damit haben Sie das Lab beendet

---
lab:
  title: Übung 2 – Verbinden von Windows-Geräten mit Microsoft Sentinel über Datenconnectors
  module: Learning Path 8 - Connect logs to Microsoft Sentinel
---

# Lernpfad 8 – Lab 1 – Übung 2: Verbinden der Windows-Geräte über Datenconnectors mit Microsoft Sentinel

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex2.png)

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Nun müssen Sie herausfinden, wie Protokolldaten aus den verschiedenen Datenquellen in Ihrer Organisation verbunden werden. Die nächste Datenquelle sind virtuelle Windows-Computer innerhalb und außerhalb von Azure, beispielsweise in lokalen Umgebungen und anderen öffentlichen Clouds.

>**Wichtig:** Die Lab-Übungen für Lernpfad Nr. 8 befinden sich in einer *eigenständigen* Umgebung. Wenn Sie das Lab vor dem Abschluss verlassen, müssen Sie die Konfigurationen erneut ausführen.

### Geschätzte Zeit bis zum Abschluss dieses Labs: 30 Minuten

### Aufgabe 1: Erstellen eines virtuellen Windows-Computers in Azure

In dieser Aufgabe erstellen Sie einen virtuellen Windows-Computer in Azure.

1. Melden Sie sich beim virtuellen **WIN1-Computer** als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Microsoft Edge-Browser zu der Azure-Portal unter <https://portal.azure.com>.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Klicken Sie auf **+ Ressource erstellen**. **Hinweis:** Wenn Sie bereits im Azure-Portal waren, müssen Sie möglicherweise *Microsoft Azure* in der oberen Leiste auswählen, um zum Startmenü zu wechseln.

1. Geben Sie im Feld **Services und Marketplace durchsuchen** *Windows 10* ein und wählen Sie **Microsoft Windows 10** aus der Dropdownliste.

1. Wählen Sie das Feld für **Microsoft Window 10** aus.

1. Öffnen Sie die Dropdownliste *Plan* und wählen Sie **Windows 10 Enterprise, Version 22H2**.

1. Wählen Sie **Mit vordefinierter Konfiguration starten** aus, um fortzufahren.

1. Wählen Sie **Dev/Test** und dann **Fortfahren, um eine VM zu erstellen**aus.

1. Wählen Sie **Neu anlegen** für *Ressourcengruppe*, geben Sie „RG-AZWIN01“ als Namen ein und wählen Sie **OK**.

    >**Hinweis:** Dies ist eine neue Ressourcengruppe für Nachverfolgungszwecke. 

1. Geben Sie unter *Name der virtuellen Maschine* AZWIN01 ein.

1. Belassen Sie **(US) East US** als Standardwert für *Region*.

1. Scrollen Sie nach unten und überprüfen Sie *Image* für den virtuellen Computer. Wenn es leer ist, wählen Sie **Windows 10 Enterprise, Version 22H2** aus.

1. Überprüfen Sie die *Größe* des virtuellen Computers. Wenn sie leer ist, wählen Sie **Alle Größen anzeigen** aus, wählen Sie die erste VM-Größe unter *Von Azure-Benutzern am häufigsten verwendet* und danach wählen Sie **Auswählen** aus.

    >**Hinweis:** Wenn die folgende Meldung angezeigt wird: *Dieses Bild wird für Azure Automanage nicht unterstützt. Um diese Funktion zu deaktivieren, navigieren Sie zur Registerkarte Verwaltung. Andernfalls wählen Sie ein unterstütztes Bild aus.* Navigieren Sie zur Registerkarte Verwaltung und deaktivieren Sie „Automanage“. Der Erstellungsprozess wird dann erfolgreich sein.

1. Scrollen Sie nach unten und geben Sie einen *Benutzernamen* Ihrer Wahl ein. **Hinweis:** Vermeiden Sie reservierte Wörter wie Admin oder Root.

1. Geben Sie ein *Kennwort* Ihrer Wahl ein. **Hinweis:** Es kann einfacher sein, Ihr Mandantenkennwort wiederzuverwenden. Sie finden es auf der Registerkarte Ressourcen.

1. Scrollen Sie bis zum Ende der Seite und aktivieren Sie das Kontrollkästchen unter *Lizenzierung*, um zu bestätigen, dass Sie die entsprechende Lizenz besitzen.

1. Wählen Sie **Überprüfen + Erstellen** und warten Sie, bis die Überprüfung abgeschlossen ist.

    >**Hinweis:** Wenn die Validierung *Netzwerke* fehlschlägt, wählen Sie diese Registerkarte aus, überprüfen Sie den Inhalt und wählen Sie erneut **Prüfen + Erstellen**.

1. Klicken Sie auf **Erstellen**. Warten Sie, bis die Ressource erstellt ist. Dies kann einige Minuten in Anspruch nehmen.

### Aufgabe 2: Verbinden eines lokalen Servers mit Azure

In dieser Aufgabe verbinden Sie einen lokalen Server mit Ihrem Azure-Abonnement. Azure Arc wurde auf diesem Server vorinstalliert. Der Server wird in den nächsten Übungen verwendet, um simulierte Angriffe auszuführen, die Sie später für die Erkennung und Untersuchung in Microsoft Sentinel verwenden werden.

>**Wichtig:** Die nächsten Schritte werden auf einem anderen Computer ausgeführt als dem, auf dem Sie zuvor gearbeitet haben.

1. Melden Sie sich bei dem virtuellen Computer **WINServer** als Administrator*in mit dem Kennwort: **Passw0rd!** an, falls erforderlich.  

    >**Hinweis:** Wie oben beschrieben, wurde Azure Arc auf dem **WINServer**-Rechner vorinstalliert. Sie verbinden diesen Computer jetzt mit Ihrem Azure-Abonnement.

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

### Aufgabe 3: Verbinden Sie eine virtuelle Azure-Windows-Maschine

In dieser Aufgabe verbinden Sie einen virtuellen Azure-Windows-Computer mit Microsoft Sentinel.

>**Hinweis:** Microsoft Sentinel wurde in Ihrem Azure-Abonnement mit dem Namen **defenderWorkspace** vorab bereitgestellt, und die erforderlichen *Content Hub*-Lösungen wurden installiert.

1. Melden Sie sich beim virtuellen **WIN1-Computer** als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Öffnen Sie bei Bedarf den Microsoft Edge-Browser, navigieren Sie zum Azure-Portal unter <https://portal.azure.com> und melden Sie sich mit den bereitgestellten Anmeldedaten an.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie den Microsoft Sentinel **defenderWorkspace** aus.

1. Scrollen Sie im linken Navigationsmenü von Microsoft Sentinel nach unten zum Abschnitt *Inhaltsverwaltung* und wählen Sie **Inhalt-Hub**.

1. Suchen Sie im *Content Hub* nach der Lösung **Windows-Sicherheitsereignisse** und wählen Sie diese aus der Liste aus.

1. Wählen Sie auf der Lösungsseite *Windows-Sicherheitsereignisse* die Option **Verwalten** aus.

    >**Hinweis:** Die Lösung *Windows-Sicherheitsereignisse* installiert sowohl den *Windows-Sicherheitsereignisse über AMA* als auch den Datenconnector *Sicherheitsereignisse über Legacy-Agent*. Plus 2 Arbeitsmappen, 20 Analyseregeln und 43 Hunting-abfragen.

1. Wählen Sie den Datenconnector *Windows Sicherheitsereignisse über AMA* und wählen Sie auf dem Connector-Informationsblatt**Connectorseite öffnen**aus.

1. Wählen Sie im Abschnitt *Konfiguration* die Schaltfläche **+Regel für die Datensammlung erstellen**.

1. Geben Sie **AZWINDCR** als Regelnamen ein und wählen Sie **Weiter: Ressourcen** aus.

1. Erweitern Sie Ihr *MOC-Abonnement* unter *Scope* auf der Registerkarte *Resources*.

    >**Hinweis:** Sie können die gesamte Hierarchie *Bereich* erweitern, indem Sie die Option „>“ vor der Spalte *Bereich* auswählen.

1. Erweitern Sie **RG-AZWIN01**, und wählen Sie **dann AZWIN01** aus.

1. Wählen Sie **Weiter: Sammeln**.

1. Überprüfen Sie die verschiedenen Optionen zum Sammeln von Sicherheitsereignissen. Behalten Sie *Alle Sicherheitsereignisse* und wählen Sie dann **Weiter: Prüfen + Erstellen** aus.

1. Wählen Sie **Erstellen** aus, um die Datensammlungsregel zu speichern.

1. Warten Sie eine Minute und wählen Sie dann **Aktualisieren** aus, damit die neue Datensammlungsregel angezeigt wird.

### Aufgabe 4: Verbinden Sie einen Windows-Computer, der nicht von Azure stammt

In dieser Aufgabe fügen Sie einen mit Azure Arc verbundenen virtuellen Nicht-Azure-Windows-Computer zu Microsoft Sentinel hinzu.  

   >**Hinweis:** Der Datenconnector *Windows-Sicherheitsereignisse über AMA* erfordert Azure Arc für Nicht-Azure-Maschinen.

1. Stellen Sie sicher, dass Sie sich in der Konfiguration des Datenconnectors *Windows-Sicherheitsereignisse über AMA* in Ihrem Microsoft Sentinel-Arbeitsbereich befinden.

1. Bearbeiten Sie im Abschnitt *Konfiguration* die **AZWINDCR***Regel zur Datensammlung*, indem Sie das Symbol *Bleistift* auswählen.

1. Wählen Sie **Weiter: Ressourcen** und erweitern Sie Ihr *MOC-Abonnement* unter *Geltungsbereich* auf der Registerkarte *Ressourcen*.

    >**Hinweis:** Sie können die gesamte Hierarchie *Bereich* erweitern, indem Sie die Option „>“ vor der Spalte *Bereich* auswählen.

1. Erweitern Sie **defender-RG** (oder die von Ihnen erstellte Ressourcengruppe) und wählen Sie dann **WINServer** aus.

    >**Wichtig:** Wenn WINServer nicht angezeigt wird, lesen Sie bitte den Lernpfad 3, Übung 1, Aufgabe 4, wo Sie Azure Arc auf diesem Server installiert haben.

1. Wählen Sie **Weiter: Sammeln**, dann **Weiter: Prüfen + Erstellen** aus.

1. Wählen Sie **Erstellen** aus, nachdem *Validierung erfolgreich* angezeigt wurde.

## Fahren Sie mit Übung 3 fort

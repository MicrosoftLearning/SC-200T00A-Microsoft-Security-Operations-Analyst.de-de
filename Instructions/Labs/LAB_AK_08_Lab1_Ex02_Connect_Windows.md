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

1. Klicken Sie auf **+ Ressource erstellen**. **Hinweis:** Wenn Sie bereits im Azure-Portal waren, müssen Sie möglicherweise *Microsoft Azure* in der oberen Leiste auswählen, um zu „Start“ zu wechseln..

1. Geben Sie im Feld **Services und Marketplace durchsuchen** *Windows 10* ein und wählen Sie **Microsoft Windows 10** aus der Dropdownliste.

1. Wählen Sie das Feld für **Microsoft Window 10** aus.

1. Öffnen Sie die Dropdownliste *Plan* und wählen Sie **Windows 10 Enterprise, Version 22H2**.

1. Wählen Sie **Mit vordefinierter Konfiguration starten** aus, um fortzufahren.

1. Wählen Sie **Dev/Test** und dann **Fortfahren, um eine VM zu erstellen**aus.

1. Wählen Sie **Neu anlegen** für *Ressourcengruppe*, geben Sie RG-AZWIN01 als Namen ein und wählen Sie **OK**.

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

### Aufgabe 2: Installieren Sie Azure Arc auf einem lokalen Server

In dieser Aufgabe installieren Sie Azure Arc auf einem lokalen Server, um das Onboarding zu vereinfachen.

>**Wichtig:** Die nächsten Schritte werden in einer anderen VM ausgeführt als der, in der Sie zuvor gearbeitet haben. Suchen Sie nach den Namensverweisen der virtuellen Maschine.

1. Melden Sie sich bei dem virtuellen Computer **WINServer** als Administrator*in mit dem Kennwort: **Passw0rd!** an, falls erforderlich.  

1. Öffnen Sie den Microsoft Edge-Browser und navigieren Sie zum Azure-Portal unter <https://portal.azure.com>.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Arc* ein und wählen Sie **Azure Arc** aus.

1. Wählen Sie im Navigationsbereich unter **Azure Arc-Ressourcen** die Option **Computer** aus.

1. Klicken Sie auf **+ Hinzufügen/Erstellen** und dann auf **Computer hinzufügen**.

1. Wählen Sie **Skript generieren** aus dem Abschnitt „Einen einzelnen Server hinzufügen“ aus.

1. Wählen Sie auf der Seite *Hinzufügen eines Servers mit Azure Arc* die Ressourcengruppe aus, die Sie zuvor unter *Projektdetails* erstellt haben. **Hinweis:***RG-Defender*

    >**Hinweis:** Wenn Sie noch keine Ressourcengruppe erstellt haben, öffnen Sie eine andere Registerkarte und erstellen Sie die Ressourcengruppe.

1. Für *Region* wählen Sie **(US) East Us** aus der Dropdownliste aus.

1. Lesen Sie die Optionen *Serverdetails* und *Verbindungsmethode*. Behalten Sie die Standardwerte bei und wählen Sie **Weiter** aus, um zur Registerkarte Tags zu gelangen.

1. Überprüfen Sie, welche Tags standardmäßig verfügbar sind. Wählen Sie **Weiter** aus, um zur Registerkarte Skript herunterladen und ausführen zu gelangen.

1. Scrollen Sie nach unten und klicken Sie auf die Schaltfläche **Herunterladen**. **Hinweis:** Wenn Ihr Browser den Download blockiert, ergreifen Sie Maßnahmen im Browser, um ihn zuzulassen. Wählen Sie ggf. im Microsoft Edge-Browser die Schaltfläche mit den Auslassungspunkten (…) und klicken Sie dann auf **Beibehalten**.

1. Klicken Sie mit der rechten Maustaste auf die Windows-Schaltfläche Start und wählen Sie **Windows PowerShell (Admin)** aus.

1. Geben Sie *Administrator* für „Benutzername“ und *Passw0rd!* ein. für "Kennwort" ein, wenn Sie eine UAC-Eingabeaufforderung erhalten.

1. Geben Sie folgendes ein: cd C:\Users\Administrator\Downloads

    >**Wichtig:** Wenn Sie dieses Verzeichnis nicht sehen, befinden Sie sich höchstwahrscheinlich auf dem falschen Computer. Gehen Sie zurück zum Anfang von Aufgabe 4 und wechseln Sie zu WINServer.

1. Geben Sie *Set-ExecutionPolicy -ExecutionPolicy Unrestricted* ein und drücken Sie die Eingabetaste.

1. Geben Sie **A** für Ja zu Alle ein und drücken Sie die Eingabetaste.

1. Geben Sie *.\OnboardingScript.ps1* ein und drücken Sie die Eingabetaste.  

    >**Wichtig:** Wenn Sie die Fehlermeldung *„Der Begriff .\OnboardingScript.ps1 wird nicht erkannt …“* erhalten, stellen Sie sicher, dass Sie die Schritte für Aufgabe 4 im virtuellen Computer WINServer ausführen. Ein weiteres Problem könnte sein, dass sich der Name der Datei aufgrund mehrerer Downloads geändert hat. Suchen Sie nach *„.\OnboardingScript (1).ps1“* oder anderen Dateinummern im aktuellen Verzeichnis.

1. Geben Sie **R** für Ausführen ein und drücken Sie die Eingabetaste (dies kann ein paar Minuten dauern).

1. Während des Einrichtungsvorgangs wird eine neue Registerkarte im Microsoft Edge-Browser geöffnet, um den Azure Arc-Agenten zu authentifizieren. Wählen Sie Ihr Administratorkonto aus, warten Sie, bis die Meldung „Authentifizierung abgeschlossen" angezeigt wird, und kehren Sie dann zum Windows PowerShell-Fenster zurück.

1. Wenn die Installation abgeschlossen ist, kehren Sie zur Azure-Portalseite zurück, von der Sie das Skript heruntergeladen haben, und wählen Sie **Schließen**. Schließen Sie die Seite **Server mit Azure Arc hinzufügen**, um zur Seite Azure Arc **-Computer** zurückzukehren.

1. Klicken Sie auf **Aktualisieren**, bis der Name des WINServer-Servers erscheint und der Status *Verbunden* ist.

    >**Hinweis:** Dieser Vorgang kann einige Minuten dauern.

### Aufgabe 3: Verbinden Sie eine virtuelle Azure-Windows-Maschine

In dieser Aufgabe verbinden Sie einen virtuellen Azure-Windows-Computer mit Microsoft Sentinel.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren zuvor erstellten Microsoft Sentinel-Arbeitsbereich aus.

1. 1. Scrollen Sie im Bereich Microsoft Sentinel im linken Menü nach unten zu *Inhaltsverwaltung*, und wählen Sie **Content Hub** aus.

1. Suchen Sie im *Content Hub* nach der Lösung **Windows-Sicherheitsereignisse** und wählen Sie diese aus der Liste aus.

1. Wählen Sie auf der Lösungsseite *Windows-Sicherheitsereignisse* die Option **Installieren** aus.

1. Wenn die Installation abgeschlossen ist, wählen Sie **Verwalten** aus

    >**Hinweis:** Die Lösung *Windows-Sicherheitsereignisse* installiert sowohl den *Windows-Sicherheitsereignisse über AMA* als auch den Datenconnector *Sicherheitsereignisse über Legacy-Agent*. Plus 2 Arbeitsmappen, 20 Analyseregeln und 43 Hunting-abfragen.

1. Wählen Sie den Datenconnector *Windows Sicherheitsereignisse über AMA* und wählen Sie auf dem Connector-Informationsblatt**Connectorseite öffnen**aus.

1. Wählen Sie im Abschnitt *Konfiguration* unter der Registerkarte *Anweisungen* die Option **Regel zur Datensammlung erstellen** aus.

1. Geben Sie **AZWINDCR** als Regelnamen ein und wählen Sie **Weiter: Ressourcen** aus.

1. Wählen Sie **+Ressource hinzufügen**, um den von uns erstellten virtuellen Computer auszuwählen.

1. Erweitern Sie **RG-AZWIN01**, und wählen Sie **dann AZWIN01** aus.

1. Wählen Sie **Anwenden** und dann **Weiter: Sammeln** aus.

1. Überprüfen Sie die verschiedenen Optionen zum Sammeln von Sicherheitsereignissen. Behalten Sie *Alle Sicherheitsereignisse* und wählen Sie dann **Weiter: Prüfen + Erstellen** aus.

1. Wählen Sie **Erstellen** aus, um die Datensammlungsregel zu speichern.

1. Warten Sie eine Minute und wählen Sie dann **Aktualisieren** aus, damit die neue Datensammlungsregel angezeigt wird.

### Aufgabe 4: Verbinden Sie einen Windows-Computer, der nicht von Azure stammt

In dieser Aufgabe fügen Sie einen mit Azure Arc verbundenen virtuellen Nicht-Azure-Windows-Computer zu Microsoft Sentinel hinzu.  

   >**Hinweis:** Der Datenconnector *Windows-Sicherheitsereignisse über AMA* erfordert Azure Arc für Nicht-Azure-Maschinen.

1. Stellen Sie sicher, dass Sie sich in der Konfiguration des Datenconnectors *Windows-Sicherheitsereignisse über AMA* in Ihrem Microsoft Sentinel-Arbeitsbereich befinden.

1. Bearbeiten Sie auf der Registerkarte **Anweisungen** im Abschnitt *Konfiguration* die **AZWINDCR***Datenerfassungsregel*, indem Sie das Symbol *Bleistift* auswählen.

1. Klicken Sie auf **Weiter: Ressourcen**, und erweitern Sie Ihr *Abonnement* auf der Registerkarte *Ressourcen* unter *Bereich*.

    >**Hinweis:** Sie können die gesamte Hierarchie *Bereich* erweitern, indem Sie die Option „>“ vor der Spalte *Bereich* auswählen.

1. Erweitern Sie **RG-Defender** (oder die von Ihnen erstellte Ressourcengruppe), und wählen Sie **dann WINServer** aus.

    >**Wichtig:** Wenn WINServer nicht angezeigt wird, lesen Sie bitte den Lernpfad 3, Übung 1, Aufgabe 4, wo Sie Azure Arc auf diesem Server installiert haben.

1. Wählen Sie **Übernehmen**.

1. Wählen Sie **Weiter: Sammeln**, dann **Weiter: Prüfen + Erstellen** aus.

1. Wählen Sie **Erstellen** aus, nachdem *Validierung erfolgreich* angezeigt wurde.

## Fahren Sie mit Übung 3 fort

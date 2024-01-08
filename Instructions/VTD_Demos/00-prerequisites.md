
# Microsoft Security Operations Analyst
Leitfaden zur Vorbereitung des Kursleiters

## Purpose

Dieses Dokument richtet sich an Referenten, die sich auf die Teilnahme am Microsoft Security Virtual Training Day für `Defend Against Threats with Extended Detection and Response` und `Configure Security Operations Using Microsoft Sentinel` vorbereiten. Dieses Material ist eine Teilmenge des SC-200: Microsoft Security Operations Analyst Zertifizierungskurs.

## Demovoraussetzungen

Die Labs für diesen Kurs erfordern sowohl einen lizenzierten Microsoft 365 E5-Mandanten als auch ein Azure-Abonnement.

* Sie können Microsoft Learning Azure Passes für sich anfordern.
* Stellen Sie sicher, dass Sie diese Pässe mindestens zwei Wochen vor der Durchführung der Demos anfordern. Nachdem Sie den Pass erhalten haben, müssen Sie ihn aktivieren. 
* Der Azure Pass funktioniert genauso wie das öffentlich verfügbare Microsoft Azure-Testabonnement. Das bedeutet, dass für die Nutzung des Passes Einschränkungen gelten.
* Die Labanweisungen finden Sie im [SC-200 Microsoft Learning-GitHub Repository](https://github.com/MicrosoftLearning/SC-200T00A-Microsoft-Security-Operations-Analyst/tree/master/Instructions/VTD_Demos/).
* Stellen Sie sicher, dass der neue Microsoft Edge-Browser auf dem Computer installiert ist, den Sie für die Demos verwenden werden.

## Aktivieren von Azure Pass

## Bereitstellen von Defender für Endpoint

### Abrufen Ihrer Microsoft 365-Anmeldeinformationen

Sobald Sie das Lab gestartet haben, wird Ihnen ein kostenloser Testmandant zur Verfügung gestellt, um in der Microsoft virtuellen Labumgebung darauf zuzugreifen. Diesem Mandanten wird automatisch ein eindeutiger Benutzername und ein Kennwort zugewiesen. Sie müssen diesen Benutzernamen und das Kennwort abrufen, damit Sie sich in der Microsoft virtuellen Labumgebung bei Azure und Microsoft 365 anmelden können.

Da dieser Kurs von Lernpartnern angeboten werden kann, die einen von mehreren autorisierten Labhostinganbietern nutzen, können die tatsächlichen Schritte zum Abrufen der Ihrem Mandanten zugewiesenen Mandanten-ID je nach Labhostinganbieter variieren. Ihr Kursleiter wird Ihnen daher die notwendigen Anweisungen geben, wie Sie diese Informationen für Ihren Kurs erhalten. Notieren Sie sich die folgenden Informationen für die spätere Verwendung:

    - **Mandantensuffix-ID.** Diese ID ist für die onmicrosoft.com-Konten, mit denen Sie sich während der Labs bei Microsoft 365 anmelden. Es hat das Format **{Benutzername}@M365xZZZZZZ.onmicrosoft.com**, wobei ZZZZZZ Ihre eindeutige Mandanten-Suffix-ID ist, die Sie von Ihrem Lab-Hostinganbieter erhalten haben. Notieren Sie sich diesen Wert ZZZZZZ für die spätere Verwendung. Wenn Sie in einem der Lab-Schritte aufgefordert werden, sich an den Microsoft 365-Portalen anzumelden, müssen Sie den hier erhaltenen Wert ZZZZZZ eingeben.
    - **Mandantenkennwort.** Geben Sie das Administratorkennwort ein, das von Ihrem Labhostinganbieter erhalten haben.
    

### Initialisieren von Microsoft Defender für Endpunkt

In dieser Aufgabe führen Sie die Initialisierung von Microsoft Defender for Endpoint durch.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Öffnen Sie im Edge-Browser das Microsoft 365 Defender-Portal (https://security.microsoft.com)).

1. Kopieren und fügen Sie im Dialogfeld **Anmelden** das E-Mail-Konto des Mandanten für den Administratorbenutzernamen ein, das Sie von Ihrem Lab-Hostinganbieter erhalten haben, und klicken Sie auf **Weiter**.

1. Kopieren und fügen Sie im Dialogfeld **Kennwort eingeben** das vom Lab-Hostanbieter bereitgestellte Mandantenkennwort des/der Administratorin, und klicken Sie auf **Anmelden** aus.

Wählen Sie im **Microsoft 365 Defender**-Portal im Navigationsmenü auf der linken Seite **Start** aus.

    >**Note:** You may need to scroll all the way to the menu top.

1. Auf der Portalseite **Start** wird **Willkommen bei Microsoft 365 Defender** angezeigt.

1. Scrollen Sie durch die Kacheln nach unten, bis Sie die Kachel mit der Bezeichnung **Microsoft 365 Defender** und der Meldung **Microsoft 365 Defender aktivieren.** finden.

    >**Hinweis:** Sie sollte sich unten rechts in den Kacheln befinden.

1. Klicken Sie auf die Schaltfläche mit der Aufschrift **Neue Funktionen aktivieren**.

1. Oben auf der Seite erscheint kurz die Meldung *Laden und Initialisieren*, dann sehen Sie das Bild einer Kaffeetasse und die Meldung: **Bleiben Sie dran! Wir bereiten neue Speicherplätze für Ihre Daten vor und verbinden sie.** Der Vorgang dauert etwa 5 Minuten. *Lassen Sie die Seite geöffnet und vergewissern Sie sich, dass sie abgeschlossen wird, da sie für das nächste Lab benötigt wird.*.

    >**Hinweis:** Wenn die Meldung „Bleiben Sie dran! Wenn „Wir bereiten neue Speicherorte für Ihre Daten vor und verbinden sie“ nicht angezeigt wird oder die Seite „Einstellungen > Microsoft 365 Defender > Konto“ geöffnet wird, aber die Meldung „Fehler beim Laden des Datenspeicherorts. Bitte versuchen Sie es später erneut“ angezeigt wird, wählen Sie im Menü „Allgemein“ die Option „Warnungsdiensteinstellungen“ oder gehen Sie zum Navigationsmenü, scrollen Sie nach unten zum Abschnitt „Ressourcen“ und wählen Sie „Geräte“.

1. Wenn der neue Bereich erfolgreich abgeschlossen wurde, sehen Sie die allgemeinen Einstellungen von Microsoft 365 Defender für Konto, E-Mail-Benachrichtigungen, Einstellungen für den Benachrichtigungsdienst, Berechtigungen und Rollen und Streaming-API. Außerdem sehen Sie, dass die **Vorschaufunktionen** aktiviert sind.

**Hinweis**: In der gehosteten Lab-Umgebung sollte Ihr Datenspeicherort für Sie ausgewählt sein. Und es muss in der geografischen Region liegen, die für den Ort geeignet ist, an dem dieser Schulungsmandanten verwaltet wird. Die Dauer der Datenaufbewahrung kann noch gewählt werden, ist aber nicht erforderlich.

1. Wählen Sie in **Einstellungen** **Endpunkte**aus.

1. Wählen Sie **Onboarding** im Abschnitt Geräteverwaltung aus.

    >**Hinweis:** Sie können das Onboarding von Geräten auch über den Abschnitt **Objekte** in der linken Menüleiste durchführen. Erweitern Sie Objekte, und wählen Sie Geräte aus. Scrollen Sie auf der Seite Geräteinventarisierung mit der Auswahl Computer und Mobilgeräte nach unten zu **Onboarding von Geräten.** Daraufhin erscheint die Seite **Einstellungen > Endpunkte**.

1. Im Bereich „1. Gerät einbinden“ stellen Sie sicher, dass „Lokales Skript (für bis zu 10 Geräte)“ in der Dropdownliste „Bereitstellungsmethode“ angezeigt wird und klicken Sie auf die Schaltfläche **Onboarding-Paket herunterladen**.

1. Extrahieren Sie die heruntergeladene Zip-Datei in einen lokalen Ordner, zum Beispiel in den Ordner Dokumente.

1. Klicken Sie mit der rechten Maustaste auf die extrahierte Datei WindowsDefenderATPLocalOnboardingScript.cmd und wählen Sie **Als Administrator ausführen** aus.  Wenn Sie den Windows SmartScreen sehen, wählen Sie trotzdem Ausführen.

**Hinweis** Die Datei sollte sich standardmäßig im Verzeichnis c:\users\admin\downloads befinden.
    
1. Beantworten Sie die Fragen des Skripts mit **Y**. Wenn Sie fertig sind, sollten Sie eine Meldung auf dem Befehlsbildschirm sehen, die ungefähr so aussieht: „Onboarding des Computers erfolgreich durchgeführt …“ 

1. Kopieren Sie auf der Seite Onboarding im Portal das Skript für den Erkennungstest und führen Sie es in einem geöffneten Befehlsfenster aus.  Möglicherweise müssen Sie ein neues Fenster **Administrator: Eingabeaufforderung** öffnen, indem Sie *CMD* in die Suchleiste des Fensters eingeben und **Als Administrator ausführen** auswählen.

1. Wählen Sie im Menü des Microsoft 365 Defender-Portals **Geräteinventar** aus. Ihr Gerät sollte nun in der Liste angezeigt werden.

**Hinweis:** Es kann bis zu 5 Minuten dauern, bis das Gerät im Portal angezeigt wird.


### Rolle konfigurieren

In dieser Aufgabe konfigurieren Sie Rollen für die Verwendung mit Gerätegruppen.

1. Wählen Sie im Microsoft 365 Defender-Portal in der linken Menüleiste **Einstellungen** aus. 

1. Wählen Sie **Endpunkte** aus und dann **Rollen** im Bereich „Berechtigungen“.

1. Wählen Sie die Schaltfläche **Rollen aktivieren** aus.

1. Wählen Sie **Element hinzufügen** aus.

1. Geben Sie im Dialogfeld Rolle hinzufügen die folgenden Daten ein:

    |Allgemeine Einstellung|Wert|
    |---|---|
    |Rollenname|**Support der Ebene 1**|
    |Berechtigungen|Livereaktionsfunktionen – Erweitert|

1. Wählen Sie **Weiter** aus.

1. Auf der Registerkarte „Zugewiesene Benutzergruppen“. Wählen Sie **sg-IT** und dann **Ausgewählte Gruppen hinzufügen** aus.

1. Klicken Sie auf **Speichern**.

### Konfigurieren von Gerätegruppen

In dieser Aufgabe konfigurieren Sie Gerätegruppen, die die Zugriffssteuerung und die Automatisierungskonfiguration ermöglichen.

1. Wählen Sie in der linken Menüleiste **Einstellungen** aus. 

1. Wählen Sie **Endpunkte** und im Bereich „Berechtigungen“ **Gerätegruppen** aus.

1. Klicken Sie auf **Hinzufügen**, um eine Gerätegruppe hinzuzufügen.

1. Geben Sie auf der Registerkarte Allgemein die folgenden Informationen ein:

    |Allgemeine Einstellung|Wert|
    |---|---|
    |Name der Gerätegruppe|**Regulär**|
    |Automatisierungsebene|Vollständig – Automatisches Beheben von Bedrohungen|

1. Wählen Sie **Weiter** aus.

1. . Wählen Sie auf der Registerkarte „Geräte“ für die Betriebssystemvoraussetzung **Windows 10** und klicken Sie auf **Weiter**.

1. Wählen Sie auf der Registerkarte „Gerätevorschau“ **Vorschau anzeigen**aus, um den virtuellen Computer WIN1 anzuzeigen. Wählen Sie **Weiter** aus. 
**Hinweis:** Wenn Sie den virtuellen Computer nicht in der Vorschauliste sehen, gehen Sie zurück und wählen Sie auch *Keine* für die Betriebssystembedingung aus. Die Daten für den virtuellen Computer sind noch nicht aufgefüllt.

1. Wählen Sie auf der Registerkarte „Benutzerzugriff“ **sg-IT** und dann **Ausgewählte Gruppen hinzufügen** aus.

1. Wählen Sie **Fertig** aus.

1. Die Gerätegruppenkonfiguration wurde geändert. Klicken Sie auf **Änderungen übernehmen**, um die Übereinstimmungen zu überprüfen und die Gruppierungen neu zu berechnen.

1. Sie haben nun zwei Gerätegruppen: die soeben erstellte Gerätegruppe „Regulär“ und die Gerätegruppe „Ungruppierte Geräte (Standard)“ mit der gleichen Wartungsebene.

<!--- 
## Deploy sample alerts for Demo in Module 3

In this task, you will load sample security alerts and review the alert details.

1. In the Edge browser, open the Azure portal at https://portal.azure.com.

1. In the **Sign in** dialog box, copy and paste in the **Tenant Email** account provided by your lab hosting provider and then select **Next**.

1. In the **Enter password** dialog box, copy and paste in the **Tenant Password** provided by your lab hosting provider and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Defender*, then select **Microsoft Defender for Cloud**.

1. In the **Getting Started** menu the default selection is **Upgrade**, select or **Skip** for now.

1. Select **Security alerts** in the portal menu.

1. Select **Sample Alerts** from the command bar.

1. In the Create sample alerts (Preview) pane make sure your subscription is selected.  Make sure all sample alerts are selected and select **Create sample alerts**.  

**Note** This may take a few minutes to complete. --->

## Bereitstellen von Microsoft Sentinel-Arbeitsbereich für Demo in Modul 4

In dieser Aufgabe erstellen Sie einen Microsoft Sentinel-Arbeitsbereich.

 >**Hinweis:** Für die folgende Demo müssen Sie einen Azure Pass oder ein anderes Azure Abonnement aktiviert haben.

1. Navigieren Sie im Edge-Browser zum Azure-Portal unter https://portal.azure.com.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie **+ Erstellen** aus.

1. Wählen Sie anschließend **+ Neuen Arbeitsbereich erstellen**aus.

**Hinweis**Erstellen Sie zunächst einen neuen Arbeitsbereich für die Protokollanalyse.

1. Wählen Sie das entsprechende Abonnement aus.

1. Wählen Sie den Link **Neu erstellen** für die Ressourcengruppe und geben Sie einen neuen Ressourcengruppennamen Ihrer Wahl ein.

1. Geben Sie unter Instanzdetails im Feld Name einen beliebigen Namen für den Log Analytics-Arbeitsbereich ein.

**Hinweis:** Dieser Name sollte eindeutig sein und wird auch der Name des Microsoft Sentinel-Arbeitsbereichs sein.

1. Wählen Sie die passende Region aus.  Die entsprechende Region ist möglicherweise voreingestellt, oder Ihr Kursleiter hat spezielle Hinweise, welche Region Sie auswählen sollten.  

1. Klicken Sie auf **Überprüfen + erstellen**.

1. Klicken Sie auf **Erstellen**. Warten Sie, bis der neue Log Analytics-Arbeitsbereich auf der Seite Microsoft Sentinel zu einem Arbeitsbereich hinzufügen in der Liste angezeigt wird.  Dies kann einige Minuten dauern.

1. Wählen Sie den neu erstellten Arbeitsbereich aus, wenn er erscheint, und klicken Sie dann auf **Hinzufügen**.

## Bereitstellen von Microsoft Sentinel-Inhaltshublösungen und -Datenconnectoren

### Aufgabe 1: Zugriff auf den Microsoft Sentinel-Arbeitsbereich

In dieser Aufgabe greifen Sie auf Ihren Microsoft Sentinel-Arbeitsbereich zu.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Öffnen Sie den Browser, suchen, laden und installieren Sie den neuen Microsoft Edge-Browser. Starten Sie den neuen Edge-Browser.

1. Navigieren Sie im Edge-Browser zum Azure-Portal unter https://portal.azure.com.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren Microsoft Sentinel-Arbeitsbereich aus, den Sie in dem vorherigen Lab erstellt haben.

### Aufgabe 2: Verbinden des Azure-Aktivitätsdatenconnectors.

In dieser Aufgabe verbinden Sie den *Azure-Aktivitätsdatenconnectors*.

1. Scrollen Sie im Bereich Microsoft Sentinel im linken Menü nach unten zu *Inhaltsverwaltung*, und wählen Sie **Content Hub** aus.

1. Suchen Sie in *Content Hub* nach der Lösung **Azure-Aktivität** und wählen Sie diese aus der Liste aus.

1. Auf der Seite *Microsoft Defender für Cloud* wählen Sie **Installieren**.

1. Wenn die Installation abgeschlossen ist, wählen Sie **Verwalten** aus

    >**Hinweis:** Die Lösung *Azure-Aktivität* installiert den *Azure-Aktivitätsdatenconnector*, 12 Analyseregeln, 14 Hunting-Abfragen und 1 Arbeitsmappe.

1.  Wählen Sie den *Azure-Aktivitätsdatenconnector* aus und wählen Sie **Connectorseite öffnen**.

1. Scrollen Sie im Bereich *Konfiguration* unter der Registerkarte *Anweisungen* nach unten zu „2. Verbinden Sie Ihre Abonnements …“ und wählen Sie **Azure Policy-Zuweisungs-Assistenten starten** aus.

1. Wählen Sie auf der Registerkarte **Grundlagen** unter **Geltungsbereich** die Schaltfläche mit dem Auslassungszeichen (...) und wählen Sie Ihr Abonnement „Azure Pass – Sponsorship“ aus der Dropdownliste aus und klicken Sie auf **Auswählen**.

1. Wählen Sie die Registerkarte **Parameter** aus, wählen Sie Ihren Arbeitsbereich aus der Dropdownliste **Arbeitsbereich für primäre Protokollanalyse** aus. Diese Aktion wendet die Abonnementkonfiguration an, um die Informationen an den Log Analytics-Arbeitsbereich zu senden.

1. Wählen Sie die Registerkarte **Wartung** aus, und aktivieren Sie dann das Kontrollkästchen **Korrekturtask erstellen**. Mit dieser Aktion wird die Richtlinie auf bestehende Azure-Ressourcen angewendet.

1. Wählen Sie die Schaltfläche **Überprüfen + erstellen** aus, um die Konfiguration zu überprüfen.

1. Wählen Sie **Erstellen** aus, um den Vorgang abzuschließen.

### Aufgabe 3: Erstellen eines virtuellen Windows-Computers in Azure

In dieser Aufgabe erstellen Sie einen virtuellen Windows-Computer in Azure.

1. Melden Sie sich beim virtuellen **WIN1-Computer** als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Microsoft Edge-Browser zu der Azure-Portal unter https://portal.azure.com.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Klicken Sie auf **+ Ressource erstellen**. **Hinweis:** Wenn Sie bereits im Azure-Portal waren, müssen Sie möglicherweise *Microsoft Azure* in der oberen Leiste auswählen, um zu „Start“ zu wechseln..

1. Geben Sie im Feld **Services und Marketplace durchsuchen** *Windows 10* ein und wählen Sie **Microsoft Windows 10** aus der Dropdownliste.

1. Wählen Sie das Feld für **Microsoft Window 10** aus.

1. Öffnen Sie die Dropdownliste *Plan* und wählen Sie **Windows 10 Enterprise, Version 22H2**.

1. Wählen Sie **Mit vordefinierter Konfiguration starten** aus, um fortzufahren.

1. Wählen Sie **Dev/Test** und dann **Fortfahren, um eine VM zu erstellen**aus.

1. Klicken sie auf **Neu erstellen** für *Ressourcengruppe*, geben Sie `RG-AZWIN01` als Namen ein und klicken Sie auf **OK**.

    >**Hinweis:** Dies ist eine neue Ressourcengruppe für Nachverfolgungszwecke. 

1. Bei *Name des Virtuellen Computers* geben Sie `AZWIN01` ein.

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

### Aufgabe 4: Verbinden eines virtuellen Azure Windows-Computers

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

### Aufgabe 5: Installieren von Azure Arc und Verbinden eines lokalen Servers

In dieser Aufgabe installieren Sie Azure Arc auf einem lokalen Server, um das Onboarding zu vereinfachen.

>**Wichtig:** Die nächsten Schritte werden in einer anderen VM ausgeführt als der, in der Sie zuvor gearbeitet haben. Suchen Sie nach den Namensverweisen der virtuellen Maschine.

1. Melden Sie sich bei dem virtuellen Computer **WINServer** als Administrator*in mit dem Kennwort: **Passw0rd!** an, sofern erforderlich.  

1. Öffnen Sie den Microsoft Edge-Browser und navigieren Sie zum Azure-Portal unter https://portal.azure.com.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Arc* ein und wählen Sie **Azure Arc** aus.

1. Wählen Sie im Navigationsbereich unter **Infrastruktur** **Computer** aus.

1. Klicken Sie auf **+ Hinzufügen/Erstellen** und dann auf **Computer hinzufügen**.

1. Wählen Sie **Skript generieren** aus dem Abschnitt „Einen einzelnen Server hinzufügen“ aus.

1. Lesen Sie sich die Registerkarte *Voraussetzungen* durch und wählen Sie dann **Weiter** aus, um fortzufahren.

1. Wählen Sie auf der Seite *Hinzufügen eines Servers mit Azure Arc* die Ressourcengruppe aus, die Sie zuvor unter *Projektdetails* erstellt haben. **Hinweis:***RG-Defender*

    >**Hinweis:** Wenn Sie noch keine Ressourcengruppe erstellt haben, öffnen Sie eine andere Registerkarte und erstellen Sie die Ressourcengruppe.

1. Lesen Sie die Optionen *Serverdetails* und *Verbindungsmethode*. Behalten Sie die Standardwerte bei und wählen Sie **Weiter** aus, um zur Registerkarte Tags zu gelangen.

1. Überprüfen Sie, welche Tags standardmäßig verfügbar sind. Wählen Sie **Weiter** aus, um zur Registerkarte Skript herunterladen und ausführen zu gelangen.

1. Scrollen Sie nach unten und klicken Sie auf die Schaltfläche **Herunterladen**. **Hinweis:** Wenn Ihr Browser den Download blockiert, ergreifen Sie Maßnahmen im Browser, um ihn zuzulassen. Wählen Sie ggf. im Edge-Browser die Schaltfläche mit den Auslassungspunkten (…) und klicken Sie dann auf **Beibehalten**.

1. Klicken Sie mit der rechten Maustaste auf die Windows-Schaltfläche Start und wählen Sie **Windows PowerShell (Admin)** aus.

1. Geben Sie *Administrator* für „Benutzername“ und *Passw0rd!* ein. für "Kennwort" ein, wenn Sie eine UAC-Eingabeaufforderung erhalten.

1. Geben Sie folgendes ein: cd C:\Users\Administrator\Downloads

    >**Wichtig:** Wenn Sie dieses Verzeichnis nicht sehen, befinden Sie sich höchstwahrscheinlich auf dem falschen Computer. Gehen Sie zurück zum Anfang von Aufgabe 4 und wechseln Sie zu WINServer.

1. Geben Sie *Set-ExecutionPolicy -ExecutionPolicy Unrestricted* ein und drücken Sie die Eingabetaste.

1. Geben Sie **A** für Ja zu Alle ein und drücken Sie die Eingabetaste.

1. Geben Sie *.\OnboardingScript.ps1* ein und drücken Sie die Eingabetaste.  

    >**Wichtig:** Wenn Sie die Fehlermeldung *„Der Begriff .\OnboardingScript.ps1 wird nicht erkannt …“* erhalten, stellen Sie sicher, dass Sie die Schritte für Aufgabe 4 im virtuellen Computer WINServer ausführen. Ein weiteres Problem könnte sein, dass sich der Name der Datei aufgrund mehrerer Downloads geändert hat. Suchen Sie nach *„.\OnboardingScript (1).ps1“* oder anderen Dateinummern im aktuellen Verzeichnis.

1. Geben Sie **R** für Ausführen ein und drücken Sie die Eingabetaste (dies kann ein paar Minuten dauern).

1. Während des Einrichtungsvorgangs wird eine neue Registerkarte im Edge-Browser geöffnet, um den Azure Arc-Agenten zu authentifizieren. Wählen Sie Ihr Administratorkonto aus, warten Sie, bis die Meldung „Authentifizierung abgeschlossen" angezeigt wird, und kehren Sie dann zum Windows PowerShell-Fenster zurück.

1. Wenn die Installation abgeschlossen ist, kehren Sie zur Azure-Portalseite zurück, von der Sie das Skript heruntergeladen haben, und wählen Sie **Schließen**. Schließen Sie die Seite **Server mit Azure Arc hinzufügen**, um zur Seite Azure Arc **-Computer** zurückzukehren.

1. Klicken Sie auf **Aktualisieren**, bis der Name des WINServer-Servers erscheint und der Status *Verbunden* ist.

    >**Hinweis:** Dieser Vorgang kann einige Minuten dauern.


### Aufgabe 6: Schützen eines lokalen Servers

In dieser Aufgabe fügen Sie einen mit Azure Arc verbundenen virtuellen Nicht-Azure-Windows-Computer zu Microsoft Sentinel hinzu.  

   >**Hinweis:** Der Datenconnector *Windows-Sicherheitsereignisse über AMA* erfordert Azure Arc für Nicht-Azure-Maschinen.

1. Stellen Sie sicher, dass Sie sich in der Konfiguration des Datenconnectors *Windows-Sicherheitsereignisse über AMA* in Ihrem Microsoft Sentinel-Arbeitsbereich befinden.

1. Bearbeiten Sie auf der Registerkarte **Anweisungen** im Abschnitt *Konfiguration* die **AZWINDCR***Datenerfassungsregel*, indem Sie das Symbol *Bleistift* auswählen.

1. Wählen Sie **Weiter: Ressourcen** und **+Ressource(n)** aus.

1. Erweitern Sie die von Ihnen erstellte Ressourcengruppe und wählen Sie **WINServer**.

    >**Wichtig:** Wenn WINServer nicht angezeigt wird, lesen Sie bitte den Lernpfad 3, Übung 1, Aufgabe 4, wo Sie Azure Arc auf diesem Server installiert haben.

1. Wählen Sie **Übernehmen**.

1. Wählen Sie **Weiter: Sammeln**, dann **Weiter: Prüfen + Erstellen** aus.

1. Wählen Sie **Erstellen** aus, nachdem *Validierung erfolgreich* angezeigt wurde.


<!--- ### Task 4: Connect the Microsoft Defender for Cloud connector.

In this task, you will connect the Microsoft Defender for Cloud connector.

1. From the Data Connectors tab, select the **Microsoft Defender for Cloud** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. Review the Connecting Options. Don't connect. This is for informational purposes only.

### Task 5: Connect the Microsoft Defender for Cloud Apps connector.

In this task, you will connect theMicrosoft Defender for Cloud Apps connector.

1. From the Data Connectors Tab, select the **Microsoft Defender for Cloud Apps** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. In the **Instructions** tab in the **Configuration** section, select **Alerts** and then select **Apply Changes**.

### Task 6: Connect the Microsoft Defender for Office 365 connector.

In this task, you will connect the Microsoft Defender for Office 365 connector.

1. From the Data Connectors tab, select the **Microsoft Defender for Office 365** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. Select **Connect**.

### Task 7: Connect the Microsoft Defender for Identity connector.

In this task, you will connect the Microsoft Defender for Identity connector.

1. From the Data Connectors Tab, select the **Microsoft Defender for Identity** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. Review the Connecting Options. Don't connect. This is for informational purposes only.

### Task 8: Connect the Microsoft Defender for Endpoint connector.

In this task, you will connect the Microsoft Defender for Endpoint connector.

1. From the Data Connectors Tab, select the **Microsoft Defender for Endpoint** connector from the list.

1. Select Open connector page on the connector information blade.

1. Select **Connect**.

### Task 9: Connect the Microsoft 365 Defender connector.

In this task, you will connect the Microsoft 365 Defender connector.

1. From the Data Connectors Tab, select the **Microsoft 365 Defender** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. Select all the checkboxes for Microsoft Defender for Endpoint.

1. Select **Apply Changes**. 

### Task 3: Connect a non-Azure Windows Machine.

In this task, you will connect a non-Azure Windows virtual machine to Microsoft Sentinel.

1. Login to WIN2 virtual machine as Admin with the password: **Pa55w.rd**.  

1. Open the browser, search for, download, and install the new Microsoft Edge browser. Start the new Edge browser.

1. Open a browser and log into the Azure Portal at https://portal.azure.com with your credentials.

1. In the Search bar of the Azure Portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace.

1. From the Data Connectors tab, select the **Security Events via Legacy Agent** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. In the Select which events to stream area, select **All Events**, then select **Apply Changes**.

1. Select the **Install agent on a non-Azure Windows  Machine**.

**Note:** The instructions for Install agent on a Windows Virtual Machine and Install agent on a non-Azure Windows Machine may be reversed. The links take you to the proper location even with the reversed text.

1. Select **Download & install agent for non-Azure Windows machines**. 

1. Select the link for **Download Windows Agent (64 bit)**.

1. Run the .exe file that is downloaded and confirm and User Account Control prompt that may appear.

1. Select **Next** on the Welcome dialog.

1. Select **I Agree** on the Microsoft Software License Terms page.  On the Destination prompt select **Next**.

1. On the Agent Setup Options prompt, select **Connect the agent to Azure Log Analytics (OMS)** option, then select **Next**.

1. In the browser, copy the **Workspace ID** from the Agents Management page and paste into the Workspace ID in the dialog. 

1. In the browser, copy the **Primary key** from the Agents Management page and paste into the Primary key in the dialog. 

1. Select **Next**.

1. Select **Next** on the Microsoft Update page.

2. Then select **Install**.

### Task 4: Install and collect Sysmon logs.

In this task, you will install and collect Sysmon logs.

You should still be connected to the WIN2 virtual machine.  The following instructions will install Sysmon with the default configuration.  You should research community based configurations for Sysmon to be used on production machines.

1. In the browser, go to https://docs.microsoft.com/sysinternals/downloads/sysmon

1. Download Sysmon from the page by select **Download Sysmon**.

1. Open the downloaded file and extract the files to a new directory c:\sysmon

1. In the Windows Taskbar for WIN2 search box, enter *command*.  The search results will show command prompt app.  Right-click on the command prompt app and select **Run as Administrator**.  Confirm any User Account Control prompts that appear.

1. Enter *cd \sysmon*

1. type *notepad sysmon.xml* to create a new file.

1. Open a tab in the browser and navigate to: https://github.com/SwiftOnSecurity/sysmon-config/blob/master/sysmonconfig-export.xml

1. Copy the contents of that file from Github to the sysmon.xml notepad file you just created and save the file.

1. In the command prompt type the following and press enter:
    sysmon.exe -accepteula -i sysmon.xml

1. In the browser, navigate to the Azure portal at https://portal.azure.com 

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. In Microsoft Sentinel, select **Settings** from the Configuration area and then select **Workspace settings** tab.

1. Make sure your Microsoft Sentinel Workspace is selected.

1. Select **Agents configuration** in Settings.

1. Select the **Windows Event logs** tab.

1. Select **Add windows event log** button.

1. Enter **Microsoft-Windows-Sysmon/Operational** in the Log name field.

1. Select **Apply**. --->

## Durchführen von Angriffen

### Aufgabe 1: Angreifen von Windows, das mit Defender for Endpoint konfiguriert ist

In dieser Aufgabe führen Sie Angriffe auf einen Host aus, auf dem Microsoft Defender for Endpoint konfiguriert ist.

1. Melden Sie sich beim `WIN1`virtuellen Computer als Administrator*in mit dem Kennwort **Pa55w.rd** an.  

1. Geben Sie bei der Suche in der Taskleiste *Befehl* ein.  Die Eingabeaufforderung wird in den Suchergebnissen angezeigt.  Klicken Sie mit der rechten Maustaste auf „Eingabeaufforderung“, und wählen Sie **Als Administrator ausführen** aus. Bestätigen Sie alle Aufforderungen zur Benutzerkontensteuerung, die erscheinen.

1. Geben Sie in der Eingabeaufforderung den Befehl in jeder Zeile ein und drücken Sie nach jeder Zeile die Eingabetaste:
```
cd \
mkdir temp
cd temp
```

1. Kopieren Sie diesen Befehl und führen Sie ihn aus:

```
REG ADD "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /V "SOC Test" /t REG_SZ /F /D "C:\temp\startup.bat"
```

### Aufgabe 2: Erstellen eines C2-Angriffs (Command and Control)

1. Melden Sie sich beim `WIN1`virtuellen Computer als Administrator*in mit dem Kennwort **Pa55w.rd** an.  

1. Geben Sie bei der Suche in der Taskleiste *Befehl* ein.  Die Eingabeaufforderung wird in den Suchergebnissen angezeigt.  Klicken Sie mit der rechten Maustaste auf „Eingabeaufforderung“, und wählen Sie **Als Administrator ausführen** aus. Bestätigen Sie alle Aufforderungen zur Benutzerkontensteuerung, die erscheinen.
1. 
1. 
1. Angriff 2 – Kopieren Sie diesen Befehl und führen Sie ihn aus:

```
notepad c2.ps1
```
Klicken Sie auf **Ja**, um eine neue Datei zu erstellen und kopieren Sie das folgende PowerShell-Skript in c2.ps1 und klicken Sie auf **Speichern**.

**Hinweis:** Das Einfügen in den virtuellen Computer kann eine begrenzte Länge haben.  Fügen Sie es in drei Abschnitten ein, um sicherzustellen, dass das gesamte Skript in den virtuellen Computer eingefügt wird.  Stellen Sie sicher, dass das Skript in der Notepad-Datei c2.ps1 so aussieht, wie in dieser Anleitung dargestellt.

```


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

Geben Sie an der Eingabeaufforderung Folgendes ein, und geben Sie den Befehl in jeder Zeile ein, und drücken Sie nach jeder Zeile die Eingabetaste:
```
powershell
.\c2.ps1
```
**Hinweis:** Es wird Fehler auflösen angezeigt. Dies ist zu erwarten.
Lassen Sie diesen Befehl/dieses Powershell-Skript im Hintergrund laufen. Schließen Sie das Fenster nicht.  Der Befehl muss einige Stunden lang Protokolleinträge generieren.  Sie können mit der nächsten Aufgabe und den nächsten Übungen fortfahren, während dieses Skript läuft.  Die durch diese Aufgabe erzeugten Daten werden später im Lab zur Bedrohungssuche verwendet.  Bei diesem Vorgang werden keine großen Datenmengen erzeugt oder verarbeitet.

### Aufgabe 2: Angriff auf Windows, das mit dem Azure Monitor Agent (AMA) konfiguriert ist

In dieser Aufgabe führen Sie Angriffe auf einen Host durch, für den der Sicherheitsereignisconnector und Sysmon konfiguriert sind.

1. Wählen Sie den virtuellen Computer `AZWIN01` aus, den Sie zuvor erstellt haben.  

1. Scrollen Sie im linken Menü nach unten zu **Vorgänge** und wählen Sie **Befehl ausführen** aus.

1. Im Bereich **Befehl ausführen** wählen Sie **RunPowerShellScript** aus.

1. Kopieren Sie die folgenden Befehle, um die Erstellung eines Adminstratorkontos zu simulieren, in das Formular `PowerShell Script` und klicken Sie auf **Ausführen**.

    ```CommandPrompt
    net user theusernametoadd /add
    net user theusernametoadd ThePassword1!
    net localgroup administrators theusernametoadd /add
    ```

>**Hinweis**: Achten Sie darauf, dass Sie nur einen Befehl pro Zeile eingeben und dass Sie die Befehle durch Ändern des Benutzernamens erneut ausführen können.

1. Im Fenster `Output` sollte `The command completed successfully` dreimal angezeigt werden.

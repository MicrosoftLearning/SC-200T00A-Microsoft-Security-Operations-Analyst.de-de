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

<!--- ### Task 2: Install Azure Arc on an On-Premises Server

In this task, you install Azure Arc on an on-premises server to make onboarding easier.

>**Important:** The next steps are done in a different machine than the one you were previously working. Look for the Virtual Machine name references.

1. Log in to **WINServer** virtual machine as Administrator with the password: **Passw0rd!** if necessary.  

1. Open the Microsoft Edge browser and navigate to the Azure portal at <https://portal.azure.com>.

1. In the **Sign in** dialog box, copy, and paste in the **Tenant Email** account provided by your lab hosting provider and then select **Next**.

1. In the **Enter password** dialog box, copy, and paste in the **Tenant Password** provided by your lab hosting provider and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Arc*, then select **Azure Arc**.

1. In the navigation pane under **Azure Arc resources** select **Machines**

1. Select **+ Add/Create**, then select **Add a machine**.

1. Select **Generate script** from the "Add a single server" section.

1. In the *Add a server with Azure Arc* page, select the Resource group you created earlier under *Project details*. **Hint:** *RG-Defender*

    >**Note:** If you haven't already created a resource group, open another tab and create the resource group and start over.

1. For *Region*, select **(US) East Us** from the drop-down list.

1. Review the *Server details* and *Connectivity method* options. Keep the default values and select **Next** to get to the Tags tab.

1. Review the default available tags. Select **Next** to get to the Download and run script tab.

1. Scroll down and select the **Download** button. **Hint:** if your browser blocks the download, take action in the browser to allow it. In Microsoft Edge Browser, select the ellipsis button (...) if needed and then select **Keep**.

1. Right-click the Windows Start button and select **Windows PowerShell (Admin)**.

1. Enter *Administrator* for "Username" and *Passw0rd!* for "Password" if you get a UAC prompt.

1. Enter: cd C:\Users\Administrator\Downloads

    >**Important:** If you do not have this directory, most likely means that you are in the wrong machine. Go back to the beginning of Task 4 and change to WINServer and start over.

1. Type *Set-ExecutionPolicy -ExecutionPolicy Unrestricted* and press enter.

1. Enter **A** for Yes to All and press enter.

1. Type *.\OnboardingScript.ps1* and press enter.  

    >**Important:** If you get the error *"The term .\OnboardingScript.ps1 is not recognized..."*, make sure you are doing the steps for Task 4 in the WINServer virtual machine. Other issue might be that the name of the file changed due to multiple downloads, search for *".\OnboardingScript (1).ps1"* or other file numbers in the running directory.

1. Enter **R** to Run once and press enter (this may take a couple minutes).

1. The setup process opens a new Microsoft Edge browser tab to authenticate the Azure Arc agent. Select your admin account, wait for the message "Authentication complete" and then go back to the Windows PowerShell window.

1. When the installation finishes, go back to the Azure portal page where you downloaded the script and select **Close**. Close the **Add servers with Azure Arc** to go back to the Azure Arc **Machines** page.

1. Select **Refresh** until WINServer server name appears and the Status is *Connected*.

    >**Note:** This could take a couple of minutes. --->

### Aufgabe 2: Verbinden eines virtuellen Azure Windows-Computers

In dieser Aufgabe verbinden Sie einen virtuellen Azure-Windows-Computer mit Microsoft Sentinel.

>**Hinweis:** Microsoft Sentinel wurde in Ihrem Azure-Abonnement mit dem Namen **defenderWorkspace** vorab bereitgestellt, und die erforderlichen *Content Hub*-Lösungen wurden installiert.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie den Microsoft Sentinel **defenderWorkspace** aus.

1. Scrollen Sie im linken Navigationsmenü von Microsoft Sentinel nach unten zum Abschnitt *Inhaltsverwaltung* und wählen Sie **Inhalt-Hub**.

1. Suchen Sie im *Content Hub* nach der Lösung **Windows-Sicherheitsereignisse** und wählen Sie diese aus der Liste aus.

1. Wählen Sie auf der Lösungsseite *Windows-Sicherheitsereignisse* die Option **Verwalten** aus.

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

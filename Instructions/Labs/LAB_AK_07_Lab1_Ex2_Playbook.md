---
lab:
  title: Übung 2 – Erstellen eines Playbooks
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Lernpfad 7 - Lab 1 - Übung 2 – Erstellen eines Playbooks

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex2.png)

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Sie müssen lernen, Bedrohungen mithilfe von Microsoft Sentinel zu erkennen und abzuwehren. Nun möchten Sie reagieren und Maßnahmen einleiten, die von Microsoft Sentinel routinemäßig ausgeführt werden können.

Mit einem Playbook können Sie Ihre Reaktion auf Bedrohungen automatisieren und orchestrieren, es kann in andere interne und externe Systemen integriert oder so konfiguriert werden, dass es automatisch als Reaktion auf bestimmte Alarme oder Vorfälle ausgeführt wird, wenn es durch eine Analyse- oder Automatisierungsregel ausgelöst wird. 

>**Hinweis:** Eine **[interaktive Labsimulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Create%20a%20playbook)** ist verfügbar, mit der Sie dieses Lab in Ihrem eigenen Tempo durcharbeiten können. Möglicherweise liegen geringfügige Unterschiede zwischen der interaktiven Simulation und dem gehosteten Lab vor, aber die dargestellten Kernkonzepte und Ideen sind identisch.

### Aufgabe 1: Erstellen eines Security Operations Center-Teams in Microsoft Teams

In dieser Aufgabe erstellen Sie ein Microsoft Teams-Team für die Verwendung im Lab.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Öffnen Sie im Browser Microsoft Edge eine neue Registerkarte und navigieren Sie zum Microsoft Teams-Portal unter (https://teams.microsoft.com).

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Schließen Sie alle Teams-Popups, die möglicherweise angezeigt werden.

    >**Hinweis:** Wenn Sie aufgefordert werden, **Neue Teams** zu verwenden, akzeptieren Sie und fahren Sie mit der Übung fort.

1. Falls noch nicht ausgewählt, wählen Sie im linken Menü **Teams** und dann oben das ![Plus-Zeichen](../Media/plus-sign-icon-lab.png) aus.

1. Wählen Sie die Option **Team erstellen** aus.

1. Klicken Sie auf die Schaltfläche **Von Grund auf neu**.

1. Wählen Sie die Schaltfläche **Privat** aus.

1. Geben Sie dem Team einen Namen: Geben Sie **SOC** ein und wählen Sie die Schaltfläche **Erstellen** aus.

1. Klicken Sie auf dem Bildschirm „Mitglieder zum SOC hinzufügen“ auf die Schaltfläche **Überspringen**. 

1. Scrollen Sie auf dem Blatt „Teams“ nach unten, um das neu erstellte SOC-Team zu finden, klicken Sie auf die Auslassungspunkte **(...)** rechts neben dem Namen und wählen Sie **Kanal hinzufügen** aus.

1. Geben Sie den Kanalnamen *Neue Warnungen* ein und wählen Sie die Schaltfläche **Hinzufügen** aus.


### Aufgabe 2: Erstellen eines Microsoft Sentinel-Playbooks

In dieser Aufgabe erstellen Sie eine Logik-App, die als Playbook in Microsoft Sentinel verwendet wird.

1. Navigieren Sie im Browser Microsoft Edge zu [Microsoft Sentinel auf GitHub](https://github.com/Azure/Azure-Sentinel).

<!--- the Azure portal at https://portal.azure.com.

1. In the **Sign in** dialog box, copy and paste in the **Tenant Email** account provided by your lab hosting provider and then select **Next**.

1. In the **Enter password** dialog box, copy and paste in the **Tenant Password** provided by your lab hosting provider and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace you created earlier.

1. Select the **Community** page under the *Content management* area on the left side of the page.

1. On the right pane, select the **Onboard community content** link. This opens a new tab in the Microsoft Edge Browser for Microsoft Sentinel GitHub content. **Hint:** You might need to scroll right to see the link. Alternatively, follow this link instead: [Microsoft Sentinel on GitHub](https://github.com/Azure/Azure-Sentinel). --->

1. Scrollen Sie nach unten und wählen Sie den Ordner **Lösungen** aus.

1. Wählen Sie dann den Ordner **SentinelSOARessentials** und anschließend den Ordner **Playbooks** aus.

1. Wählen Sie den Ordner **Post-Message-Teams** aus.

1. Scrollen Sie im Feld readme.md zum Abschnitt *Schnelle Bereitstellung*, **Bereitstellung mit Ereignisauslösung (empfohlen)** und klicken Sie auf die Schaltfläche **Bereitstellen in Azure**.  

1. Stellen Sie sicher, dass Ihr Azure-Abonnement ausgewählt ist.

1. Wählen Sie für die Ressourcengruppe **Neu erstellen**, geben Sie *RG-Playbooks* ein und klicken Sie auf **OK**.

1. Belassen Sie **(US) East US** als Standardwert für *Region*.

1. Benennen Sie den *Namen des Playbooks* in „PostMessageTeams-OnIncident“ um und klicken Sie auf **Prüfen + Erstellen**.

1. Wählen Sie jetzt **Erstellen**aus. 

    >**Hinweis**: Warten Sie, bis die Bereitstellung abgeschlossen ist, bevor Sie mit der nächsten Aufgabe fortfahren.

### Aufgabe 3: Aktualisieren eines Playbook in Microsoft Sentinel

In dieser Aufgabe aktualisieren Sie das neu erstellte Playbook mit den korrekten Verbindungsinformationen.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren Microsoft Sentinel-Arbeitsbereich aus.

1. Wählen Sie im Bereich *Konfiguration* **Automatisierung** und dann die Registerkarte **Aktive Playbooks** aus.

1. Wählen Sie in der Befehlsleiste **Aktualisieren** aus, wenn keine Playbooks angezeigt werden. Das im vorherigen Schritt erstellte Playbook sollte angezeigt werden.

1. Wählen Sie den Playbooknamen **PostMessageTeams** aus.

1. Wählen Sie auf der Seite „Logik-App“ für *PostMessageTeams* im Befehlsmenü **Bearbeiten** aus.

    >**Hinweis:** Möglicherweise müssen Sie die Seite aktualisieren.

1. Wählen Sie den *ersten* Block aus, **Microsoft Sentinel-Vorfall**.

1. Wählen Sie den Link **Verbindung ändern** aus.

1. Klicken Sie auf **Neu hinzufügen** und dann **Anmelden**. Wählen Sie im neuen Fenster Ihre Azure-Administrator-Anmeldeinformationen aus, wenn Sie dazu aufgefordert werden. In der letzten Zeile des Blocks sollte nun „Verbunden mit Ihrem Administrator-Benutzernamen“ stehen.

1. Wählen Sie nun den *zweiten* Block aus, **Eine Nachricht posten (V3)**.

1. Scrollen Sie auf der Registerkarte „Prameter“ nach unten, und wählen Sie den Link **Verbindung ändern** aus, und wählen Sie dann **Neu hinzufügen** und **Anmelden** aus. Wählen Sie Ihre Azure-Anmeldeinformationen des Administrators für das Gerät auf Aufforderung aus. Auf der Registerkarte „Prameter“ sollte jetzt „Verbunden mit Ihr-Administratorbenutzername“ zu lesen sein.

1. Wählen Sie am Ende des Felds *Team* das **X** aus, um den Inhalt zu löschen.  Das Feld ändert sich in ein Dropdownfeld mit einer Liste der verfügbaren Microsoft Teams. Wählen Sie **SOC** aus.

1. Machen Sie dasselbe mit dem Feld *Kanal*, klicken Sie am Ende des Feldes auf **X**, um den Inhalt zu löschen. Das Feld ändert sich in ein Dropdownfeld mit einer Liste der Kanäle des SOC-Teams. Wählen Sie **Neue Warnungen** aus.

1. Wählen Sie in der Befehlsleiste **Speichern** aus. Die Logik-App wird in einem zukünftigen Lab verwendet.

## Fahren Sie mit Übung 3 fort

---
lab:
  title: Übung 2 – Erstellen eines Playbooks
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Lernpfad 9 – Lab 1 – Übung 2: Erstellen eines Playbooks in Microsoft Sentinel

## Labszenario

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Sie müssen lernen, Bedrohungen mithilfe von Microsoft Sentinel zu erkennen und abzuwehren. Jetzt möchten Sie reagieren und Aktionen zur Behebung von Problemen durchführen, die von Microsoft Sentinel als Routine ausgeführt werden können.

Mit einem Playbook können Sie Ihre Reaktion auf Bedrohungen automatisieren und orchestrieren, es kann in andere interne und externe Systemen integriert oder so konfiguriert werden, dass es automatisch als Reaktion auf bestimmte Warnungen oder Vorfälle ausgeführt wird, wenn es durch eine Analyse- oder Automatisierungsregel ausgelöst wird.

>**Wichtig:** Die Lab-Übungen für Lernpfad Nr. 9 befinden sich in einer *eigenständigen* Umgebung. Wenn Sie das Lab vor dem Abschluss verlassen, müssen Sie die Konfigurationen erneut ausführen.

### Aufgabe 1: Erstellen eines Playbooks in Microsoft Sentinel

In dieser Aufgabe erstellen Sie eine Logik-App, die als Playbook in Microsoft Sentinel verwendet wird.

>**Hinweis:** Microsoft Sentinel wurde in Ihrem Azure-Abonnement mit dem Namen **defenderWorkspace** vorab bereitgestellt, und die erforderlichen *Content Hub-Lösungen* wurden installiert.

1. Melden Sie sich als Admin bei der virtuellen Maschine „WIN1“ mit dem Passwort: **Pa55w.rd** an.  

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie den Microsoft Sentinel **defenderWorkspace** aus.

1. Navigieren Sie in *Microsoft Sentinel* zu **Inhalt-Hub**.

1. Suchen Sie in der Suchleiste nach **Sentinel SOAR Essentials**.

1. Wählen Sie die Lösung aus, die in den Ergebnissen erscheint.

1. Wählen Sie in den Lösungsdetails **Verwalten** aus.

1. Suchen Sie das **Defender_XDR_Ransomware_Playbook_for_SecOps-Tasks**-Playbook und wählen Sie den Namen aus.

1. Wählen Sie die Vorlage **Vorfallaufgaben - Microsoft Defender XDR Ransomware Playbook für SecOps**.

1. Wählen Sie im Detailbereich **Spielbuch erstellen**.

1. Wählen Sie für Ressourcengruppe **Neu erstellen**, geben Sie **RG-Playbooks** ein und wählen Sie OK.

1. Entfernen Sie **für** und die zusätzlichen *Unterstriche* aus dem Playbook-Namen (würde die Grenze von 64 Zeichen überschreiten). Es sollte wie folgt lauten: **Defender_XDR_Ransomware_Playbook_SecOps_Tasks**.

1. Wählen Sie **Verbindungen** aus.

1. Wählen Sie **Weiter: Überprüfen und erstellen** aus.

1. Wählen Sie nun **Playbook erstellen**.

    >**Hinweis**: Warten Sie, bis die Bereitstellung abgeschlossen ist, bevor Sie mit der nächsten Aufgabe fortfahren.

### Aufgabe 2: Aktualisieren eines Playbooks in Microsoft Sentinel

In dieser Aufgabe aktualisieren Sie das neu erstellte Playbook mit den korrekten Verbindungsinformationen.

1. Wenn die vorherige Aufgabe abgeschlossen ist, sollten Sie sich auf der Seite *Defender_XDR_Ransomware_Playbook_SecOps-Tasks | Logik-App-Designer* befinden. Falls nicht, führen Sie bitte die folgenden Schritte 1 bis 5 aus.

1. Geben Sie in der Suchleiste des Azure-Portals Sentinel ein, und wählen Sie dann  Microsoft Sentinel aus.

1. Wählen Sie Ihren Microsoft Sentinel-Arbeitsbereich aus.

1. Wählen Sie im Bereich „Konfiguration“ die Option „Automatisierung“ und dann die Registerkarte *Aktive Playbooks* aus.

1. Wählen Sie in der Befehlsleiste die Option Aktualisieren, falls Sie keine Playbooks sehen. Das im vorherigen Schritt erstellte Playbook sollte angezeigt werden.

1. Wählen Sie den Namenslink **Defender_XDR_Ransomware_Playbook_SecOps_Tasks** des Playbooks.

1. Wählen Sie auf der Logic App Designer-Seite für **Defender_XDR_Ransomware_Playbook_SecOps_Tasks** im Befehlsmenü die Option „Bearbeiten“.

    >**Hinweis:** Möglicherweise müssen Sie die Seite aktualisieren.

1. Wählen Sie den ersten Block aus, Microsoft Sentinel-Vorfall.

1. Wählen Sie den Link **Verbindung ändern*** aus.

1. Klicken Sie auf **Neu hinzufügen** und dann **Anmelden**. Wählen Sie im neuen Fenster Ihre Azure-Administrator-Anmeldeinformationen aus, wenn Sie dazu aufgefordert werden. Die letzte Zeile des Blocks sollte nun lauten: „Connected to your-admin-username“.

<!--- 1. Below within the logic split (+ sign), select Add an action to incident.--->

1. Wählen Sie in der Befehlsleiste **Speichern** aus.

1. Wählen Sie im Fenster die Schaltfläche **X**, um es zu schließen. Die Logik-App wird in einem zukünftigen Lab verwendet.

### Aufgabe 3: Erstellen einer Automatisierungsregel

1. Erweitern Sie in Microsoft Sentinel im Navigationsmenü *Konfiguration* und wählen Sie *Automatisierung*.

1. Wählen Sie **+ Erstellen** und wählen Sie **Automatisierungsregel**.

1. Geben Sie der Regel einen Namen

1. Lassen Sie den *Trigger* auf **Wenn ein Vorfall erstellt wird** eingestellt.

1. Lassen Sie unter *Bedingungen* den Vorfallanbieter auf *Alle* eingestellt.

1. Lassen Sie den Eintrag *Analyseregelname* auf *Alle* stehen.

1. Wählen Sie **+ Hinzufügen** und wählen Sie *Bedingung (Und)*.

1. Wählen Sie aus der Dropdown-Liste die Option **Taktik** aus.

1. Wählen Sie den Operator **Enthält** aus dem Dropdown-Menü aus.

1. Wählen Sie die folgenden Taktiken aus *Werte*:
    - Reconnaissance
    - Ausführung
    - Persistenz
    - Befehl und Steuerung
    - Exfiltration
    - PreAttack

1. Wählen Sie unter Aktionen die Option **Playbook ausführen**.

1. Klicken Sie auf den Link **Playbook-Berechtigungen verwalten**.

1. Wählen Sie auf der Seite *Berechtigungen verwalten* die Ressourcengruppe **RG-Playbooks** aus, die Sie in der vorherigen Übung erstellt haben, und klicken Sie auf **Anwenden**.

1. Wählen Sie aus der Dropdown-Liste das **Defender_XDR_Ransomware_Playbook_SecOps_Tasks**-Playbook aus.

1. Wählen Sie unten **Anwenden** aus.

1. Wählen Sie im Fenster *Neue Automatisierungsregel erstellen* das **X**, um es zu schließen.

Sie haben nun ein Playbook und eine Automatisierungsregel in Microsoft Sentinel erstellt.

## Fahren Sie mit Übung 3 fort

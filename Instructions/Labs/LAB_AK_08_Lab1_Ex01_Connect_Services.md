---
lab:
  title: Übung 1 – Verbinden von Daten mit Microsoft Sentinel mithilfe von Datenconnectors
  module: Learning Path 8 - Connect logs to Microsoft Sentinel
---

# Lernpfad 8 – Lab 1 – Übung 1: Verbinden der Daten mit Microsoft Sentinel mithilfe von Datenconnectors

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex1.png)

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Nun müssen Sie herausfinden, wie Protokolldaten aus den verschiedenen Datenquellen in Ihrer Organisation verbunden werden. Die Organisation verfügt über Daten von Microsoft 365, Microsoft Defender XDR, Azure-Ressourcen, virtuellen Computern ohne Azure usw. Sie beginnen damit, zuerst die Microsoft-Quellen zu verbinden.

>**Wichtig:** Die Lab-Übungen für Lernpfad Nr. 8 befinden sich in einer *eigenständigen* Umgebung. Wenn Sie das Lab vor dem Abschluss verlassen, müssen Sie die Konfigurationen erneut ausführen.

### Geschätzte Zeit bis zum Abschluss dieses Labs: 20 Minuten

### Aufgabe 1: Zugriff auf den Microsoft Sentinel-Arbeitsbereich

In dieser Aufgabe greifen Sie auf Ihren Microsoft Sentinel-Arbeitsbereich zu.

>**Hinweis:** Microsoft Sentinel wurde in Ihrem Azure-Abonnement mit dem Namen **defenderWorkspace** vorab bereitgestellt, und die erforderlichen *Content Hub-Lösungen* wurden installiert.

1. Melden Sie sich beim virtuellen Computer **WIN1** als Administrator mit dem Kennwort **Pa55w.rd**an.  

1. Schließen Sie den Microsoft Edge-Browser.

1. Navigieren Sie im Edge-Browser zum Azure-Portal unter <https://portal.azure.com>.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie den Microsoft Sentinel **defenderWorkspace** aus.

1. Fahren Sie mit der nächsten Aufgabe fort.

### Aufgabe 2: Herstellen einer Verbindung mit dem Microsoft Defender für Cloud-Datenconnector

In dieser Aufgabe stellen Sie eine Verbindung mit dem Microsoft Defender for Cloud-Datenconnector her.

1. Scrollen Sie im Navigationsmenü von Microsoft Sentinel nach unten zum Abschnitt **Inhaltsverwaltung** und wählen Sie **Content Hub** aus.

1. Suchen Sie im *Content Hub* nach der Lösung **Microsoft Defender für Cloud**, und wählen Sie sie aus der Liste aus.

1. Wählen Sie auf der Seite mit den Lösungsdetails von Microsoft Defender for Cloud die Option **Verwalten** aus.

    >**Hinweis:** Die Lösung *Microsoft Defender for Cloud* installiert den *abonnementbasierten Microsoft Defender for Cloud (Legacy)*-Datenconnector, den *mandantenbasierten Microsoft Defender for Cloud (Vorschau)*.Datenconnector und eine Analyseregel. Der *mandantenbasierte Microsoft Defender for Cloud (Preview)* -Datenconnector wird verwendet, wenn ein Mandant über mehrere Abonnements verfügt.

1. Aktivieren Sie das Kontrollkästchen *Abonnementbasierter Microsoft Defender for Cloud (Legacy)*-Datenconnector, und wählen Sie dann die Seite **Connector öffnen** aus.

1. **Aktivieren** Sie im Abschnitt *Konfiguration* das Kontrollkästchen für *MOC Subscription-XXXXXXXXXXX*, und wählen Sie den Link **Verbinden** aus.

1. Der **Status** sollte jetzt **Verbunden** lauten.

1. Um die bidirektionale Synchronisierung zu aktivieren, wählen Sie den Link **Microsoft Defender für alle Abonnements aktivieren**.

    >**Hinweis:** Möglicherweise müssen Sie nach rechts scrollen, um den Link zu sehen.

1. Auf der Seite *Microsoft Defender for Cloud – Erste Schritte* sollte das Kontrollkästchen für das *MOC-Abonnement-XXXXXXXXXXX* aktiviert sein und der *Microsoft Defender-Plan* sollte *Ein – Teilweise (30 Testtage übrig)* angezeigt werden.

1. Wählen Sie die Taste **X (Schließen)** oben rechts, um die Seite *Erste Schritte* zu schließen. Sie sollten wieder auf der Konfigurationsseite *Microsoft Defender for Cloud* sein.

1. Der *Status* für das *MOC-Abonnement-XXXXXXXXXXX* sollte *Verbunden* lauten, und die *bidirektionale Synchronisierung* sollte **Aktiviert** sein.

    >**Hinweis:** Möglicherweise müssen Sie dieses Verfahren wiederholen, damit *Bidirektionale Synchronisierung aktiviert* angezeigt wird. Versuchen Sie nach dem erneuten Ausführen der Schritte, das Dropdownmenü für *Bidirektionale Synchronisierung* auf **Aktiviert** festzulegen.

### Aufgabe 3: Verbinden des Azure-Aktivitätsdatenconnectors

In dieser Aufgabe verbinden Sie den *Azure-Aktivitätsdatenconnector*.

1. Scrollen Sie im Navigationsmenü von Microsoft Sentinel nach unten zum Abschnitt *Inhaltsverwaltung* und wählen Sie **Content Hub** aus.

1. Suchen Sie in *Content Hub* nach der Lösung **Azure-Aktivität** und wählen Sie diese aus der Liste aus.

1. Wählen Sie auf der Lösungsseite *Azure-Aktivität* die Option **Verwalten**aus.

    >**Hinweis:** Die Lösung *Azure-Aktivität* installiert den *Azure-Aktivitäts-* Datenconnector, 13 Analyseregeln, 14 Hunting-Abfragen und 1 Arbeitsmappe.

1.  Wählen Sie den *Azure-Aktivitätsdatenconnector* aus und wählen Sie **Connectorseite öffnen**.

1. Scrollen Sie im Bereich *Konfiguration* unter der Registerkarte *Anweisungen* nach unten zu „2. Verbinden Sie Ihre Abonnements …“ und wählen Sie **Azure Policy-Zuweisungs-Assistenten starten** aus.

1. Wählen Sie auf der Registerkarte **Grundlagen** unter **Umfang** die Schaltfläche mit de Auslassungspunkten (…) und wählen Sie Ihr *MOC-Abonnement-XXXXXXXXXXX* aus der Dropdown-Liste aus und klicken Sie auf **Auswählen**.

    >**Hinweis:** Wählen Sie *keine* optionale Ressourcengruppe aus.

1. Wählen Sie auf der Registerkarte **Parameter** Ihren Workspace *uniquenameDefender* aus der Dropdownliste **Primärer Log Analytics-Arbeitsbereich** aus. Mit dieser Aktion wird die Abonnementkonfiguration angewendet, um die Informationen an den Log Analytics-Arbeitsbereich zu senden.

1. Wählen Sie die Registerkarte **Wartung** aus, und aktivieren Sie dann das Kontrollkästchen **Korrekturtask erstellen**. Mit dieser Aktion wird die Richtlinie auf bestehende Azure-Ressourcen angewendet.

1. Wählen Sie die Schaltfläche **Überprüfen + erstellen** aus, um die Konfiguration zu überprüfen.

1. Wählen Sie **Erstellen** aus, um den Vorgang abzuschließen.

## Fahren Sie mit Übung 2 fort

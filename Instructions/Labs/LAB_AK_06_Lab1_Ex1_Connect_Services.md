---
lab:
  title: Übung 1 – Verbinden von Daten mit Microsoft Sentinel mithilfe von Datenconnectors
  module: Learning Path 6 - Connect logs to Microsoft Sentinel
---

# Lernpfad 6 – Lab 1 – Übung 1 – Verbinden von Daten mit Microsoft Sentinel mithilfe von Datenconnectors

## Labszenario

![Lab-Überblick.](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex1.png)

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Nun müssen Sie herausfinden, wie Protokolldaten aus den vielen verschiedenen Datenquellen in Ihrer Organisation verbunden werden. Die Organisation verfügt über Daten von Microsoft 365, Microsoft 365 Defender, Azure-Ressourcen, Nicht-Azure-Virtual Machines usw. Sie beginnen zuerst mit der Verbindung der Microsoft-Datenquellen

>**Hinweis:** Eine **[interaktive Labsimulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Connect%20data%20to%20Microsoft%20Sentinel%20using%20data%20connectors)** ist verfügbar, mit der Sie dieses Lab in Ihrem eigenen Tempo durcharbeiten können. Möglicherweise liegen geringfügige Unterschiede zwischen der interaktiven Simulation und dem gehosteten Lab vor, aber die dargestellten Kernkonzepte und Ideen sind identisch. 


### Aufgabe 1: Zugreifen auf den Microsoft Sentinel-Arbeitsbereich

In dieser Aufgabe greifen Sie auf Ihren Microsoft Sentinel-Arbeitsbereich zu.

1. Melden Sie sich bei der virtuellen Maschine **WIN1** als Administrator mit dem Kennwort: **Pa55w.rd** an.  

1. Schließen Sie den Microsoft Edge-Browser.

1. Navigieren Sie im Edge-Browser zum Azure-Portal unter https://portal.azure.com.

1. Kopieren Sie im Dialogfeld **Anmelden** das von Ihrem Lab-Hosting-Anbieter bereitgestellte **Mandanten-E-Mail**-Konto, und wählen Sie dann **Weiter** aus.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das von Ihrem Lab-Hosting-Anbieter bereitgestellte **Mandantenkennwort**, und fügen Sie es ein, und wählen Sie dann **Anmelden** aus.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie **Microsoft Sentinel** aus.

1. Wählen Sie Ihren Microsoft Sentinel-Arbeitsbereich aus, den Sie im vorherigen Lab erstellt haben.

1. Wählen Sie im Navigationsmenü „Analysen“ aus.

1. Wählen Sie *Vorfälle basierend auf Microsoft Defender for Cloud erstellen* aus den Regelvorlagen aus.

1. Wählen Sie im Connectorinformationen-Blatt **Regel erstellen** aus.

1. Wählen Sie im Analyseregel-Assistenten **Weiter: Automatisierte Antwort** und dann  **Weiter: Überprüfen und erstellen** aus.

1. Wählen Sie **save** (Speichern) aus.

### Aufgabe 2: Herstellen einer Verbindung mit dem Microsoft Defender for Cloud-Datenconnector

In dieser Aufgabe stellen Sie eine Verbindung mit dem Microsoft Defender for Cloud-Datenconnector.

1. Scrollen Sie im linken Menü von Microsoft Sentinel nach unten zu *Content Management*, und wählen Sie **Content Hub** aus.

1. Suchen Sie im *Content Hub* nach der Lösung **Microsoft Defender for Cloud**, und wählen Sie sie aus der Liste aus.

1. Wählen Sie auf der Seite mit der Lösung *Microsoft Defender for Cloud* die Option **Installieren** aus.

1. Wenn die Installation abgeschlossen ist, wählen Sie **Verwalten** aus

    >**Hinweis:** Die Lösung *Microsoft Defender for Cloud* installiert den *abonnementbasierten Microsoft Defender for Cloud (Legacy)*-Datenconnector, den *mandantenbasierten Microsoft Defender for Cloud (Vorschau)*.Datenconnector und eine Analyseregel.

1. Aktivieren Sie das Kontrollkästchen *Abonnementbasierter Microsoft Defender for Cloud (Legacy)*-Datenconnector, und wählen Sie dann die Seite **Connector öffnen** aus.

1. Aktivieren Sie im Abschnitt *Konfiguration* auf der Registerkarte *Anweisungen* **** das Kontrollkästchen für das Abonnement „Azure Pass – Sponsorship“, und schieben Sie die Option **Status** nach rechts.

    >**Hinweis:** Wenn die Verbindung wieder getrennt wird, überprüfen Sie bitte den Lernpfad 3, Übung 1, Aufgabe 1, um Ihrem Konto die richtigen Berechtigungen zuzuweisen.

1. Der *Status* sollte jetzt **Verbunden** lauten, und „Bidirektionale Synchronisierung“ sollte *Aktiviert* sein.

1. Scrollen Sie nach unten, und stellen Sie unter *Erstellen von Vorfällen – Empfohlen!* sicher dass *Automatisch Vorfälle anhand aller Warnungen erstellen, die in diesem verbundenen Dienst generiert werden* den Status **Aktiviert** aufweist.

### Aufgabe 3: Verbinden des Azure Activity-Datenconnectors

In dieser Aufgabe verbinden Sie den *Azure Activity*-Datenconnector.

1. Scrollen Sie im linken Menü von Microsoft Sentinel nach unten zu *Content Management*, und wählen Sie **Content Hub** aus.

1. Suchen Sie im *Content Hub* nach der **Azure Activity**-Lösung, und wählen Sie sie aus der Liste aus.

1. Wählen Sie auf der Seite mit der *Azure Activity*-Lösung die Option **Installieren** aus.

1. Wenn die Installation abgeschlossen ist, wählen Sie **Verwalten** aus

    >**Hinweis:** Die *Azure Activity*-Lösung installiert den *Azure Activity*-Datenconnector, 12 Analyseregeln, 14 Hunting-Abfragen und 1 Arbeitsmappe.

1. Wählen Sie den *Azure Activity*-Datenconnector aus, und wählen Sie **Connectorseite öffnen** aus.

1. Scrollen Sie im Bereich *Konfiguration* unter der Registerkarte *Anweisungen* nach unten zu „2. Verbinden Ihrer Abonnements …“, und wählen Sie **Azure Policy-Zuweisungs-Assistenten starten** aus.

1. Wählen Sie auf der Registerkarte **Grundlagen** unter **Geltungsbereich** die Schaltfläche mit den Auslassungspunkten (...) aus, wählen Sie Ihr Abonnement „Azure Pass – Sponsorship“ aus der Dropdownliste aus, und klicken Sie auf **Auswählen**.

1. Wählen Sie auf der Registerkarte **Parameter** Ihren Workspace *uniquenameDefender* aus der Dropdownliste **Primärer Log Analytics-Arbeitsbereich** aus. Diese Aktion wendet die Abonnementkonfiguration an, um die Informationen an den Log Analytics-Arbeitsbereich zu senden.

1. Wählen Sie die Registerkarte **Wartung** aus, und aktivieren Sie dann das Kontrollkästchen **Korrekturtask erstellen**. Mit dieser Aktion wird die Richtlinie auf bestehende Azure-Ressourcen angewendet.

1. Wählen Sie die Schaltfläche **Überprüfen + erstellen** aus, um die Konfiguration zu überprüfen.

1. Wählen Sie **Erstellen** aus, um den Vorgang abzuschließen.

## Fahren Sie mit Übung 2 fort

---
lab:
  title: Übung 1 – Verbinden von Daten mit Microsoft Sentinel mithilfe von Datenconnectors
  module: Learning Path 6 - Connect logs to Microsoft Sentinel
---

# Lernpfad 6 – Lab 1 – Übung 1 – Verbinden von Daten mit Microsoft Sentinel mithilfe von Datenconnectors

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex1.png)

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Nun müssen Sie herausfinden, wie Protokolldaten aus den verschiedenen Datenquellen in Ihrer Organisation verbunden werden. Die Organisation verfügt über Daten aus Microsoft 365, Microsoft 365 Defender, Azure-Ressourcen, virtuellen Maschinen ohne Azure usw. Sie beginnen zuerst mit der Verbindung der Microsoft-Quellen.

>**Hinweis:** Eine **[interaktive Labsimulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Connect%20data%20to%20Microsoft%20Sentinel%20using%20data%20connectors)** ist verfügbar, mit der Sie dieses Lab in Ihrem eigenen Tempo durcharbeiten können. Möglicherweise liegen geringfügige Unterschiede zwischen der interaktiven Simulation und dem gehosteten Lab vor, aber die dargestellten Kernkonzepte und Ideen sind identisch. 


### Aufgabe 1: Zugriff auf den Microsoft Sentinel-Arbeitsbereich

In dieser Aufgabe greifen Sie auf Ihren Microsoft Sentinel-Arbeitsbereich zu.

1. Melden Sie sich beim virtuellen Computer **WIN1** als Administrator mit dem Kennwort **Pa55w.rd**an.  

1. Schließen Sie den Microsoft Edge-Browser.

1. Navigieren Sie im Edge-Browser zum Azure-Portal unter https://portal.azure.com.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren Microsoft Sentinel-Arbeitsbereich aus, den Sie in dem vorherigen Lab erstellt haben.

1. Wählen Sie im Navigationsmenü Analytics aus.

1. Wählen Sie *Vorfälle basierend auf Microsoft Defender for Cloud erstellen* in den Regelvorlagen aus.

1. Wählen Sie im Regelinformationsbereich **Regel erstellen** aus, oder wählen Sie die Auslassungspunkte (...) und dann **+ Regel erstellen** aus.

1. Wählen Sie im Assistenten für Analyseregeln **Weiter: Automatisierte Antwort** und dann **Weiter: Prüfen und erstellen** aus.

1. Wählen Sie **save** (Speichern) aus.

### Aufgabe 2: Herstellen einer Verbindung mit dem Microsoft Defender für Cloud-Datenconnector

In dieser Aufgabe verbinden Sie Microsoft Defender für Cloud-Datenconnector.

1. Scrollen Sie im Bereich Microsoft Sentinel im linken Menü nach unten zu *Inhaltsverwaltung*, und wählen Sie **Content Hub** aus.

1. Suchen Sie im *Content Hub* nach der Lösung **Microsoft Defender für Cloud**, und wählen Sie sie aus der Liste aus.

1. Wählen Sie auf der Seite mit den Lösungsdetails von *Microsoft Defender for Cloud* die Option **Installieren** aus.

1. Wenn die Installation abgeschlossen ist, suchen Sie nach der Lösung von **Microsoft Defender for Cloud**, und wählen Sie sie aus.

1. Wählen Sie auf der Seite mit den Lösungsdetails von *Microsoft Defender for Cloud* die Option **Verwalten** aus.

    >**Hinweis:** Die Lösung *Microsoft Defender for Cloud* installiert den *abonnementbasierten Microsoft Defender for Cloud (Legacy)*-Datenconnector, den *mandantenbasierten Microsoft Defender for Cloud (Vorschau)*.Datenconnector und eine Analyseregel.

1. Aktivieren Sie das Kontrollkästchen *Abonnementbasierter Microsoft Defender for Cloud (Legacy)*-Datenconnector, und wählen Sie dann die Seite **Connector öffnen** aus.

1. Aktivieren Sie im Abschnitt *Konfiguration* auf der Registerkarte *Anweisungen* **** das Kontrollkästchen für das Abonnement „Azure Pass – Sponsorship“, und schieben Sie die Option **Status** nach rechts.

    >**Hinweis:** Wenn der Status wieder auf „Getrennt“ wechselt, lesen Sie bitte Lernpfad 3, Übung 1, Aufgabe 1, um Ihrem Konto die richtigen Berechtigungen zuzuweisen.

1. Der *Status* sollte jetzt **Verbunden** sein und „Bidirektionale Synchronisierung“ sollte *Aktiviert* sein.

    <!--- 1. Scroll down and under the *Create incidents - Recommended!* area, verify that *Create incidents automatically from all alerts generated in this connected service* is **Enabled**. --->

### Aufgabe 3: Verbinden des Azure-Aktivitätsdatenconnectors

In dieser Aufgabe verbinden Sie den *Azure-Aktivitätsdatenconnectors*.

1. Scrollen Sie im Bereich Microsoft Sentinel im linken Menü nach unten zu *Inhaltsverwaltung*, und wählen Sie **Content Hub** aus.

1. Suchen Sie in *Content Hub* nach der Lösung **Azure-Aktivität** und wählen Sie diese aus der Liste aus.

1. Wählen Sie auf der Lösungsseite *Azure-Aktivität* die Option **Installieren**aus.

1. Wenn die Installation abgeschlossen ist, wählen Sie **Verwalten** aus

    >**Hinweis:** Die Lösung *Azure-Aktivität* installiert den *Azure-Aktivitätsdatenconnector*, 12 Analyseregeln, 14 Hunting-Abfragen und 1 Arbeitsmappe.

1.  Wählen Sie den *Azure-Aktivitätsdatenconnector* aus und wählen Sie **Connectorseite öffnen**.

1. Scrollen Sie im Bereich *Konfiguration* unter der Registerkarte *Anweisungen* nach unten zu „2. Verbinden Sie Ihre Abonnements …“ und wählen Sie **Azure Policy-Zuweisungs-Assistenten starten** aus.

1. Wählen Sie auf der Registerkarte **Grundlagen** unter **Geltungsbereich** die Schaltfläche mit dem Auslassungszeichen (...) und wählen Sie Ihr Abonnement „Azure Pass – Sponsorship“ aus der Dropdownliste aus und klicken Sie auf **Auswählen**.

1. Wählen Sie auf der Registerkarte **Parameter** Ihren Workspace *uniquenameDefender* aus der Dropdownliste **Primärer Log Analytics-Arbeitsbereich** aus. Diese Aktion wendet die Abonnementkonfiguration an, um die Informationen an den Log Analytics-Arbeitsbereich zu senden.

1. Wählen Sie die Registerkarte **Wartung** aus, und aktivieren Sie dann das Kontrollkästchen **Korrekturtask erstellen**. Mit dieser Aktion wird die Richtlinie auf bestehende Azure-Ressourcen angewendet.

1. Wählen Sie die Schaltfläche **Überprüfen + erstellen** aus, um die Konfiguration zu überprüfen.

1. Wählen Sie **Erstellen** aus, um den Vorgang abzuschließen.

## Fahren Sie mit Übung 2 fort

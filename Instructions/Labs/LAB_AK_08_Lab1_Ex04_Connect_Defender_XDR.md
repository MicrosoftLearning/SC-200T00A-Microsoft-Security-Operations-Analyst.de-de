---
lab:
  title: "Übung\_4: Verbinden von Defender\_XDR mit Microsoft Sentinel mithilfe von Datenconnectors"
  module: Learning Path 8 - Connect logs to Microsoft Sentinel
---

# Lernpfad 8 – Lab 1 – Übung 4: Verbinden von Defender XDR mit Microsoft Sentinel mithilfe von Datenconnectors

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod8_L1_Ex4.png)

Sie sind Security Operations Analyst und arbeiten in einem Unternehmen, das Microsoft Defender XDR und Microsoft Sentinel bereitgestellt hat. Sie müssen sich auf die einheitliche Security Operations-Platform vorbereiten, die Microsoft Sentinel mit Defender XDR verbindet. Im nächsten Schritt installieren Sie die Defender XDR Content Hub-Lösung und stellen den Defender XDR-Datenconnector in Microsoft Sentinel bereit.

>**Hinweis:** Die Umgebung für diese Übung ist eine Simulation, die aus dem Produkt generiert wurde. Da es sich um eine eingeschränkte Simulation handelt, werden Links auf einer Seite möglicherweise nicht aktiviert, und textbasierte Eingaben, die außerhalb des angegebenen Skripts liegen, werden möglicherweise nicht unterstützt. Es wird eine Popup-Meldung mit dem Hinweis „Diese Funktion ist in der Simulation nicht verfügbar“ angezeigt. Wenn dies der Fall ist, wählen Sie OK und fahren Sie mit den Übungsschritten fort.

![Popupfenster mit Fehlermeldung](../Media/simulation-pop-up-error.png)

### Aufgabe 1: Verbinden von Defender XDR

In dieser Aufgabe stellen Sie den Microsoft Defender XDR-Connector bereit.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Öffnen Sie im Microsoft Edge-Browser die simulierte Umgebung, indem Sie diesen Link auswählen: **[Azure-Portal]( https://app.highlights.guide/start/1c894b46-4b0a-40cb-b0f0-1e1c86c615f3?token=16d48b6c-eace-4a1f-8050-098d29d23a89)**.

1. Wählen Sie auf der *Startseite* des Azure-Portals das **Microsoft Sentinel-Symbol** aus.

1. Wählen Sie auf der *Microsoft Sentinel*-Seite den Arbeitsbereich **Woodgrove-LogAnalyiticWorkspace** aus.

1. Scrollen Sie im Bereich Microsoft Sentinel im linken Menü nach unten zu **Inhaltsverwaltung**, und wählen Sie **Content Hub** aus.

1. Suchen Sie im *Inhaltshub* nach der **Microsoft Defender XDR**-Lösung, und wählen Sie sie aus der Liste aus.

1. Wählen Sie auf der Seite mit den Lösungsdetails von *Microsoft Defender XDR* die Option **Installieren** aus.

1. Wenn die Installation abgeschlossen ist, suchen Sie nach der **Microsoft Defender XDR**-Lösung, und wählen Sie sie aus.

1. Wählen Sie auf der Seite mit den Lösungsdetails von *Microsoft Defender XDR* die Option **Verwalten** aus

1. Aktivieren Sie das Kontrollkästchen „*Microsoft Defender XDR*-Datenconnector“, und wählen Sie die Option **Connectorseite öffnen** aus.

1. Es sollte eine Meldung angezeigt werden, dass die Verbindung erfolgreich hergestellt wurde.

### Aufgabe 2: Verbinden von Microsoft Sentinel mit Microsoft Defender XDR

In dieser Aufgabe setzen Sie die Simulation fort und verbinden einen Microsoft Sentinel-Arbeitsbereich mit Microsoft Defender XDR.

1. Navigieren Sie zurück zum *Inhaltshub* von Microsoft Sentinel (mithilfe des Links für das Breadcrumb-Menü oben auf der Seite), und wählen Sie im Navigationsmenü im Abschnitt „Allgemein“ die Option **Übersicht (Vorschau)** aus.

1. Wählen Sie die Schaltfläche **Weitere Informationen** in der Nachricht *SIEM und XDR an einer zentralen Stelle erhalten* aus.

1. Durch Auswählen der Schaltfläche **Weitere Informationen** wird eine neue Registerkarte im Browser für das *Microsoft Defender XDR-Portal* geöffnet.

1. Auf dem **Startbildschirm** des **Defender**-Portals sollten Sie oben ein Banner mit der Nachricht *SIEM und XDR an einer zentralen Stelle erhalten* sehen. Wählen Sie die Schaltfläche **Arbeitsbereiche verbinden** aus.

1. Wählen Sie auf der Seite *Arbeitsbereich auswählen* den Microsoft Sentinel-Arbeitsbereich **woodgrove-loganalyiticsworkspace** aus.

1. Wählen Sie die Schaltfläche **Weiter** aus.

1. Auf der Seite **Primären Arbeitsbereich festlegen** sollte der Microsoft Sentinel-Arbeitsbereich **woodgrove-loganalyiticsworkspace** im Dropdownmenü angezeigt werden. Wählen Sie die Schaltfläche **Weiter** aus.

1. Überprüfen Sie auf der Seite *Überprüfen und fertig stellen*, ob der ausgewählte *Arbeitsbereich* der richtige ist, und überprüfen Sie die Aufzählungselemente unter dem Abschnitt *Was ist zu erwarten, wenn der Arbeitsbereich verbunden ist*. Wählen Sie die Schaltfläche **Verbinden** aus.

1. Es sollte die Nachricht *Sie sind dabei, einen Arbeitsbereich zu verbinden* angezeigt werden. Wählen Sie die Schaltfläche **Verbinden** aus.

1. Sie sollten sich jetzt auf der Seite *Arbeitsbereich erfolgreich verbunden* befinden.

1. Klicken Sie auf die Schaltfläche **Schließen**.

1. Auf dem **Startbildschirm** des **Defender XDR**-Portals sollten Sie oben ein Banner mit der Nachricht *Ihr vereinheitlichtes SIEM und XDR ist bereit* sehen. Wählen Sie die Schaltfläche **Suche starten** aus.

1. Unter *Erweiterte Bedrohungssuche* sollte die folgende Meldung angezeigt werden: „Erkunden Sie Ihre Inhalte von Microsoft Sentinel“. Im Navigationsmenü *Erweiterte Bedrohungssuche* finden Sie die *Microsoft Sentinel*-Tabellen, -Funktionen und -Abfragen unter den entsprechenden Registerkarten.

1. Scrollen Sie unter der Registerkarte **Schema** zur Überschrift **Microsoft Sentinel**, und doppelklicken Sie dann auf die Tabelle **ThreatIntelligenceIndicator**.

1. Im Bereich *Abfrage* sollte eine (KQL-)Abfrage angezeigt werden, die Threat Intelligence-Indikatoren zurückgibt. Wählen Sie die Schaltfläche **Abfrage ausführen** aus.

1. Im *Ergebnisbereich* sollten Ergebnisse angezeigt werden.

1. Erweitern Sie den linken Hauptmenübereich, wenn er reduziert ist, und erweitern Sie die neuen **Microsoft Sentinel**-Menüelemente. Die Auswahl von *Suchen*, *Bedrohungsmanagement*, *Content Management* und *Konfiguration* sollte angezeigt werden.

    >**Hinweis:** Beachten Sie, dass es Funktionsunterschiede zwischen dem Microsoft Sentinel-Portal und Sentinel im Microsoft Defender XDR-Portal **[Portal-Funktionsunterschiede](https://learn.microsoft.com/azure/sentinel/microsoft-sentinel-defender-portal#capability-differences-between-portals)** gibt.

1. Wählen Sie in den Menüelementen von Microsoft Defender XDR **Microsoft Sentinel** die Option **Konfiguration** und dann **Datenconnectors** aus.

1. Auf der Seite *Datenconnectors* sollten die **Azure-Aktivität** und andere Datenconnectors mit dem Status **Verbunden** aufgeführt sein.

>**Hinweis:** Sie können die anderen Microsoft Sentinel-Funktionen erkunden und vergleichen. Aber da es sich um eine Simulation handelt, ist Ihre Fähigkeit, Microsoft Sentinel im Microsoft Defender-Portal zu erkunden, eingeschränkt. In einer echten Umgebung können Sie die vollständigen Microsoft Sentinel-Funktionen im Microsoft Defender-Portal erkunden.

## Sie haben das Lab abgeschlossen: Fahren Sie mit „Lernpfad 9 – Lab 1 – Übung 1 – Ändern einer Microsoft-Sicherheitsregel“ fort.

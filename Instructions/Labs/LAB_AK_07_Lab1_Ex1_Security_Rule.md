---
lab:
  title: Übung 1 – Ändern einer Microsoft-Sicherheitsregel
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Lernpfad 7 – Lab 1 – Übung 1 – Ändern einer Microsoft-Sicherheitsregel

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex1.png)

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Sie müssen lernen, Bedrohungen mithilfe von Microsoft Sentinel zu erkennen und abzuwehren. Zunächst müssen Sie die von Defender for Cloud in Microsoft Sentinel eingehenden Warnmeldungen nach Schweregrad filtern.

>**Hinweis:** Eine **[interaktive Labsimulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Modify%20a%20Microsoft%20Security%20rule)** ist verfügbar, mit der Sie dieses Lab in Ihrem eigenen Tempo durcharbeiten können. Möglicherweise liegen geringfügige Unterschiede zwischen der interaktiven Simulation und dem gehosteten Lab vor, aber die dargestellten Kernkonzepte und Ideen sind identisch. 

>**Wichtig:** Wenn Sie das vorherige Lab *Lernpfad 6 – Lab 1 – Übung 4 – Verbinden von Defender XDR mit Microsoft Sentinel mithilfe von Datenconnectors abgeschlossen haben*, können Sie dieses Lab überspringen und mit der nächsten Übung fortfahren.


### Aufgabe 1: Aktivieren einer Microsoft-Sicherheitsregel

In dieser Aufgabe aktivieren Sie eine Microsoft-Sicherheitsregel.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Microsoft Edge-Browser zum Azure-Portal unter (https://portal.azure.com).

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie den Microsoft Sentinel-Arbeitsbereich aus, den Sie in dem vorherigen Lab erstellt haben.

1. Wählen Sie im Bereich Konfiguration **Analytics** aus.

1. Klicken Sie in der Befehlsleiste auf die Schaltfläche **+ Erstellen** und wählen Sie **Microsoft Incident-Regelerstellung** aus.

1. Geben Sie unter *Name* ein: **Erstelle Incidents basierend auf Defender for Endpoint**.

1. Scrollen Sie nach unten und wählen Sie unter *Microsoft-Sicherheitsdienst* **Microsoft Defender for Endpoint** aus.

1. Wählen Sie unter *Nach Schweregrad filtern* die Option *Benutzerdefiniert* aus und wählen Sie **Niedrig**, **Mittel** und **Hoch** für den Schweregrad aus. Danach kehren Sie zur Regel zurück.

1. Wählen Sie die Schaltfläche **Weiter: Automatische Antwort** und dann die Schaltfläche **Weiter: Prüfen und erstellen** aus.

1. Überprüfen Sie die vorgenommenen Änderungen und wählen Sie die Schaltfläche **Speichern** aus. Die Analyseregel wird gespeichert und Incidents werden erstellt, wenn eine Warnung in Defender for Endpoint vorhanden ist.

1. Sie verfügen nun über je einen Warnungstyp *Fusion* und *Microsoft Security*.

## Fahren Sie mit Übung 2 fort

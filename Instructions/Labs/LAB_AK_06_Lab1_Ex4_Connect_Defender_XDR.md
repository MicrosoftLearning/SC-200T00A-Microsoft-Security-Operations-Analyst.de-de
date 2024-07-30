---
lab:
  title: "Übung\_4: Verbinden von Defender\_XDR mit Microsoft Sentinel mithilfe von Datenconnectors"
  module: Learning Path 6 - Connect logs to Microsoft Sentinel
---

# Lernpfad 6 – Lan 1 – Übung 4: Verbinden von Defender XDR mit Microsoft Sentinel mithilfe von Datenconnectors

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex4.png)

Sie sind Security Operations Analyst und arbeiten in einem Unternehmen, das Microsoft Defender XDR und Microsoft Sentinel bereitgestellt hat. Sie müssen sich auf die einheitliche Security Operations-Platform vorbereiten, die Microsoft Sentinel mit Defender XDR verbindet. Im nächsten Schritt installieren Sie die Defender XDR Content Hub-Lösung und stellen den Defender XDR-Datenconnector in Microsoft Sentinel bereit.

>**Wichtig:** Beachten Sie, dass es Funktionsunterschiede zwischen dem Microsoft Sentinel-Portal und Sentinel im Microsoft Defender XDR-Portal **[Portal-Funktionsunterschiede](https://learn.microsoft.com/azure/sentinel/microsoft-sentinel-defender-portal#capability-differences-between-portals)** gibt.

### Aufgabe 1: Verbinden von Defender XDR

In dieser Aufgabe stellen Sie den Microsoft Defender XDR-Connector bereit.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Microsoft Edge-Browser zum Azure-Portal unter (<https://portal.azure.com>).

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren zuvor erstellten Microsoft Sentinel-Arbeitsbereich aus.

1. Scrollen Sie im Bereich Microsoft Sentinel im linken Menü nach unten zu **Inhaltsverwaltung**, und wählen Sie **Content Hub** aus.

1. Suchen Sie im *Inhaltshub* nach der **Microsoft Defender XDR**-Lösung, und wählen Sie sie aus der Liste aus.

1. Wählen Sie auf der Seite mit den Lösungsdetails von *Microsoft Defender XDR* die Option **Installieren** aus.

1. Wenn die Installation abgeschlossen ist, suchen Sie nach der **Microsoft Defender XDR**-Lösung, und wählen Sie sie aus.

1. Wählen Sie auf der Seite mit den Lösungsdetails von *Microsoft Defender XDR* die Option **Verwalten** aus

1. Aktivieren Sie das Kontrollkästchen „*Microsoft Defender XDR*-Datenconnector“, und wählen Sie die Option **Connectorseite öffnen** aus.

1. **Deaktivieren** Sie im Abschnitt *Konfiguration* auf der Registerkarte *Anweisungen* das Kontrollkästchen für *Deaktivieren aller Microsoft-Vorfallerstellungsregeln für diese Produkte. Empfohlen*, und wählen Sie die Schaltfläche **Vorfälle und Warnungen verbinden** aus.

1. Es sollte eine Meldung angezeigt werden, dass die Verbindung erfolgreich hergestellt wurde.

### Aufgabe 2: Verbinden von Microsoft Sentinel mit Microsoft Defender XDR

In dieser Aufgabe verbinden Sie einen Microsoft Sentinel-Arbeitsbereich mit Microsoft Defender XDR.

>**Hinweis:** Microsoft Sentinel im Microsoft Defender XDR-Portal befindet sich in der öffentlichen Vorschau und die benutzende Person kann von den Labanweisungen abweichen.

1. Melden Sie sich mit dem Kennwort beim virtuellen **WIN1**-Computer als *Administrierende Fachkraft* an: **Pa55w.rd**.  

1. Starten Sie den Microsoft Edge-Browser.

1. Wechseln Sie im Edge-Browser zum Microsoft Defender XDR-Portal unter <https://security.microsoft.com>.

1. Kopieren Sie im Dialogfeld **Anmelden**das von Ihrem Labhostinganbieter bereitgestellte Mandanten-E-Mail-Konto für den Administrator, und fügen Sie es ein, und wählen Sie dann **Weiter** aus.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das von Ihrem Labhostinganbieter bereitgestellte Mandantenkennwort für den Administrator, und fügen Sie es ein, und wählen Sie dann **Anmelden** aus.

    >**Tipp:** Das Administrator-E-Mail-Konto und Kennwort des Mandanten finden Sie auf der Registerkarte „Ressourcen“.

1. Auf dem **Startbildschirm** des **Defender XDR**-Portals sollten Sie oben ein Banner mit der Nachricht *Bringen Sie Ihr SIEM und XDR an einem Ort zusammen* sehen. Wählen Sie die Schaltfläche **Arbeitsbereiche verbinden** aus.

1. Wählen Sie auf der Seite *Arbeitsbereich auswählen* den von Ihnen zuvor erstellten **Microsoft Sentinel**-Arbeitsbereich aus.

    >**Hinweis:** Er sollte einen Namen wie *uniquenameDefender* haben.

1. Wählen Sie die Schaltfläche **Weiter** aus.

    >**Hinweis:** Wenn die Schaltfläche *Weiter* deaktiviert oder abgeblendet ist und eine Fehlermeldung angezeigt wird, dass der Microsoft Sentinel-Arbeitsbereich *nicht in Defender XDR integriert ist*, versuchen Sie, die Defender XDR-Portalseite zu aktualisieren, da die Synchronisierung 5 bis 10 Minuten dauern kann.

1. Überprüfen Sie auf der Seite *Änderungen überprüfen*, ob der ausgewählte *Arbeitsbereich* der richtige ist, und überprüfen Sie die Aufzählungselemente unter dem Abschnitt *Was ist zu erwarten, wenn der Arbeitsbereich verbunden ist*. Wählen Sie die Schaltfläche **Verbinden** aus.

1. Sie sollten die Meldung *Es wir eine Verbindung mit dem Arbeitsbereich erstellt* und anschließend die Meldung *Arbeitsbereich erfolgreich verbunden* sehen.

1. Klicken Sie auf die Schaltfläche **Schließen**.

1. Auf dem **Startbildschirm** des **Defender XDR**-Portals sollten Sie oben ein Banner mit der Nachricht *Ihr vereinheitlichtes SIEM und XDR ist bereit* sehen. Wählen Sie die Schaltfläche **Suche starten** aus.

1. In der *erweiterten Suche* sollte die folgende Meldung angezeigt werden: „Erkunden Sie Ihre Inhalte von Sentinel“. Notieren Sie sich im linken Menübereich die *Microsoft Sentinel*-Tabellen, -Funktionen und -Abfragen unter den entsprechenden Registerkarten.

1. Erweitern Sie den linken Hauptmenübereich, wenn er reduziert ist, und erweitern Sie die neuen **Microsoft Sentinel**-Menüelemente. Die Auswahl von *Bedrohungsverwaltung*, *Inhaltsverwaltung* und *Konfiguration* sollte angezeigt werden.

 >**Hinweis:**  Die Synchronisierung zwischen Microsoft Sentinel und Microsoft Defender XDR kann einige Minuten dauern, sodass möglicherweise nicht alle installierten *Datenconnectors* angezeigt werden.

## Sie haben das Lab abgeschlossen

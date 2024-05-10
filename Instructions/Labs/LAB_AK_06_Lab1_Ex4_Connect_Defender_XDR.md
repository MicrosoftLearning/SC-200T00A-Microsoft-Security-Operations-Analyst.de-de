---
lab:
  title: "Übung\_4: Verbinden von Defender\_XDR mit Microsoft Sentinel mithilfe von Datenconnectors"
  module: Learning Path 6 - Connect logs to Microsoft Sentinel
---

# Lernpfad 6 – Lan 1 – Übung 4: Verbinden von Defender XDR mit Microsoft Sentinel mithilfe von Datenconnectors

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex4.png)

Sie sind Security Operations Analyst und arbeiten in einem Unternehmen, das Microsoft Defender XDR und Microsoft Sentinel bereitgestellt hat. Sie müssen sich auf die einheitliche Security Operations-Platform vorbereiten, die Microsoft Sentinel mit Defender XDR verbindet. Im nächsten Schritt installieren Sie die Defender XDR Content Hub-Lösung und stellen den Defender XDR-Datenconnector in Microsoft Sentinel bereit.

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

1. Wählen Sie auf der Seite mit den Lösungsdetails von *Microsoft Defender XDR* die Option **Verwalten** aus.

>**Hinweis:** Die *Microsoft Defender XDR*-Lösung installiert den *Microsoft Defender XDR-* Datenconnector, Suchabfragen, Arbeitsmappen und Analyseregeln.

1. Aktivieren Sie das Kontrollkästchen „*Microsoft Defender XDR*-Datenconnector“, und wählen Sie die Option **Connectorseite öffnen** aus.

1. **Deaktivieren** Sie im Abschnitt *Konfiguration* auf der Registerkarte *Anweisungen* das Kontrollkästchen für *Deaktivieren aller Microsoft-Vorfallerstellungsregeln für diese Produkte. Empfohlen*, und wählen Sie die Schaltfläche **Vorfälle und Warnungen verbinden** aus.

1. Es sollte eine Meldung angezeigt werden, dass die Verbindung erfolgreich hergestellt wurde.

## Damit haben Sie das Lab beendet

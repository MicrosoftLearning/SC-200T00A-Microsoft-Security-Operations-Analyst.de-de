---
lab:
  title: Übung 4 – Erkunden von Entitätsverhaltensanalysen
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Lernpfad 7 – Lab 1 – Übung 4 – Erkunden von Entitätsverhaltensanalysen

## Labszenario

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Sie haben bereits geplante und Microsoft Security Analytics-Regeln erstellt. 


Sie müssen Microsoft Sentinel so konfigurieren, dass Entitätsverhaltensanalysen ausgeführt werden, um Anomalien zu ermitteln und Entitätsanalyseseiten bereitzustellen.

>**Hinweis:** Eine **[interaktive Labsimulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Explore%20entity%20behavior%20analytics)** ist verfügbar, mit der Sie dieses Lab in Ihrem eigenen Tempo durcharbeiten können. Möglicherweise liegen geringfügige Unterschiede zwischen der interaktiven Simulation und dem gehosteten Lab vor, aber die dargestellten Kernkonzepte und Ideen sind identisch. 

### Aufgabe 1: Erkunden von Entitätsverhalten 

In dieser Aufgabe untersuchen Sie die Entitätsverhaltensanalysen in Microsoft Sentinel.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Edge-Browser zum Azure-Portal unter https://portal.azure.com.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren zuvor erstellten Microsoft Sentinel-Arbeitsbereich aus.

1. Wählen Sie die Seite **Entitätsverhalten** aus.

1. Wählen Sie im Popupmenü *Entitätsverhaltenseinstellungen* die Option **UEBA festlegen**.

1. Auf der nächsten Seite wählen Sie **UEBA festlegen**.

1. Überprüfen Sie die drei Schritte, die erforderlich sind, um die Entitätsverhaltensanalyse zu aktivieren.

1. Schließen Sie die Seite *Entitätsverhalten konfigurieren*, indem Sie das ‚x‘ oben rechts auf der Seite auswählen.

1. Scrollen Sie auf der Seite *Einstellungen* nach unten und lesen Sie den Abschnitt *Anomalien*.

1. Wählen Sie **Zur Analyse gehen, um die Anomalien zu konfigurieren**.


### Aufgabe 2: Bestätigen und Überprüfen der Anomalienregeln

In dieser Aufgabe bestätigen Sie, dass Anomalieanalyseregeln aktiviert sind.

1. Sie sollten sich nun auf der Seite *Analysen*, Registerkarte *Anomalien* befinden.

1. Vergewissern Sie sich, dass in der Statusspalte der Regeln *Aktiviert* steht.

1. Wählen Sie eine Regel und danach **Bearbeiten** auf dem Regelblatt aus.

1. Überprüfen Sie die Informationen auf der Registerkarte *Allgemein*. Beachten Sie, dass der *Modus* **Produktion** ist und wählen Sie dann **Weiter: Konfiguration**.

1. Überprüfen Sie die Informationen auf der Registerkarte *Konfiguration*. Beachten Sie, dass Sie den **Schwellenwert für Anomalien** nicht ändern können.

1. Wählen Sie dann **X** in der oberen rechten Ecke, um den Assistenten für Analyseregeln zu verlassen.

1. Scrollen Sie nach rechts zu der Analyseregel, die Sie ausgewählt haben, bis Sie das Ellipsensymbol **(...)** sehen und wählen Sie es aus.

1. Wählen Sie **Duplizieren** und scrollen Sie nach links, um die neue Regel mit der Registerkarte **FLGT** am Anfang des Namens zu überprüfen.

1. Wählen Sie die Regel **FLGT** und dann **Bearbeiten** auf dem Regelblatt.

1. Überprüfen Sie die Informationen auf der Registerkarte *Allgemein*. Beachten Sie, dass der *Modus* **Flighting** ist und wählen Sie dann **Weiter: Konfiguration**.

1. Überprüfen Sie die Informationen auf der Registerkarte *Konfiguration*. Beachten Sie, dass Sie nun den **Schwellenwert für Anomalien** ändern können.

1. Setzen Sie den Wert auf **1** und wählen Sie **Weiter: Feedback senden**.

1. Wählen Sie **Weiter: Überprüfen** und dann **Speichern**, um die Regel zu aktualisieren.

    >**Hinweis:** Sie können die Regel **Flighting** auf **Produktion** aktualisieren, indem Sie die Einstellung dieser Regel ändern und die Änderungen speichern. Die Regel **Produktion** wird dann zur Regel **Flighting**.
    

## Fahren Sie mit Übung 5 fort

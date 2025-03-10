---
lab:
  title: Übung 4 – Erkunden von Entitätsverhaltensanalysen
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Lernpfad 9 – Lab 1 – Übung 4: Erkunden der Verhaltensanalyse von Entitäten

## Labszenario

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Sie haben bereits geplante und Microsoft Security Analytics-Regeln erstellt.

Sie müssen Microsoft Sentinel so konfigurieren, dass Entitätsverhaltensanalysen ausgeführt werden, um Anomalien zu ermitteln und Entitätsanalyseseiten bereitzustellen.

>**Wichtig:** Die Lab-Übungen für Lernpfad Nr. 9 befinden sich in einer *eigenständigen* Umgebung. Wenn Sie das Lab vor dem Abschluss verlassen, müssen Sie die Konfigurationen erneut ausführen.

### Geschätzte Zeit bis zum Abschluss dieses Labs: 15 Minuten

### Aufgabe 1: Erkunden von Entitätsverhalten

In dieser Aufgabe untersuchen Sie die Entitätsverhaltensanalysen in Microsoft Sentinel.

>**Hinweis:** Microsoft Sentinel wurde in Ihrem Azure-Abonnement mit dem Namen **defenderWorkspace** vorab bereitgestellt, und die erforderlichen *Content Hub-Lösungen* wurden installiert.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Edge-Browser zum Azure-Portal unter <https://portal.azure.com>.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie den Microsoft Sentinel **defenderWorkspace** aus.

1. Wählen Sie die Seite **Entitätsverhalten** aus.

1. Wählen Sie im Popupmenü *Entitätsverhaltenseinstellungen* die Option **UEBA festlegen**.

1. Scrollen Sie auf der Registerkarte *Einstellungen* unter *Entitätsverhaltensanalyse* den Abschnitt *Anomalien* herunter, lesen Sie den Absatz und überprüfen Sie, ob der *Schalter* auf *Ein* steht.

1. Wählen Sie den Link **Zur Analyse gehen, um die Anomalien zu konfigurieren**.

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

1. Wählen Sie **Weiter: Überprüfen und Erstellen** und dann **Speichern**, um die Regel zu aktualisieren.

    >**Hinweis:** Sie können die Regel **Flighting** auf **Produktion** aktualisieren, indem Sie die Einstellung dieser Regel ändern und die Änderungen speichern. Die Regel **Produktion** wird dann zur Regel **Flighting**.

## Fahren Sie mit Übung 5 fort

---
lab:
  title: Übung 3 – Erstellen einer geplanten Abfrage aus einer Vorlage
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Lernpfad 9 – Lab 1 – Übung 3: Erstellen einer zeitgesteuerten Abfrage anhand einer Vorlage

## Labszenario

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Sie müssen lernen, Bedrohungen mithilfe von Microsoft Sentinel zu erkennen und abzuwehren. Nachdem Sie Ihre Datenquellen mit Microsoft Sentinel verbunden haben, können Sie benutzerdefinierte Analyseregeln erstellen, um Bedrohungen und anomales Verhalten in Ihrer Umgebung zu erkennen.

Mit diesen Analyseregeln werden bestimmte Ereignisse oder Ereignisgruppen in Ihrer Umgebung gesucht, beim Erreichen bestimmter Ereignisschwellenwerte oder -bedingungen Warnungen ausgegeben, und Incidents generiert, die Ihr SOC selektieren und untersuchen kann. Außerdem wird mit automatisierten Nachverfolgungs- und Korrekturprozessen auf Bedrohungen reagiert.

>**Wichtig:** Die Lab-Übungen für Lernpfad Nr. 9 befinden sich in einer *eigenständigen* Umgebung. Wenn Sie das Lab vor dem Abschluss verlassen, müssen Sie die Konfigurationen erneut ausführen.

### Geschätzte Zeit bis zum Abschluss dieses Labs: 30 Minuten

### Aufgabe 1: Erstellen einer geplanten Abfrage

In dieser Aufgabe erstellen Sie eine geplante Abfrage und verbinden diese mit dem Teams-Kanal, den Sie in der vorherigen Übung erstellt haben.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren Microsoft Sentinel-Arbeitsbereich aus.

1. Wählen Sie im Bereich Konfiguration **Analytics** aus.

1. Stellen Sie sicher, dass Sie sich auf der Registerkarte *Regelvorlagen* in der Befehlsleiste befinden und suchen Sie nach der Regel **Neuer CloudShell-Benutzer**.

1. Vergewissern Sie sich auf dem Blatt „Regelzusammenfassung“, dass Sie Daten erhalten, indem Sie das grüne Symbol unter *Datenquellen: Azure Activity* überprüfen.

    >**Hinweis:** Wenn sie nicht in einem verbundenen Zustand angezeigt wird, stellen Sie sicher, dass Sie die Aufgabe 3 des Lernpfads 6 Lab, Übung 1, abgeschlossen haben.

1. Wählen Sie **Regel erstellen** aus, um fortzufahren.

1. Ändern Sie den *Schweregrad* im Assistenten für Analyseregeln auf der Registerkarte *Allgemein* auf **Mittel**.

1. Klicken Sie auf die Schaltfläche **Weiter: Regellogik festlegen >**:

1. Wählen Sie für die Regelabfrage **Abfrageergebnisse anzeigen** aus. Es sollten keine Ergebnisse oder Fehler angezeigt werden.

1. Schließen Sie das Fenster *Protokolle*, indem Sie oben rechts auf **X** klicken und klicken Sie **OK**, um die Änderungen zu speichern und zum Assistenten zurückzukehren.

1. Scrollen Sie nach unten und stellen Sie unter *Abfrageplanung* folgendes ein:

    |Einstellung|Wert|
    |---|---|
    |Ausführen der Abfrage alle:|5 Minuten|
    |Datensuche für letzte:|1 Days|

    >**Hinweis:** Wir erzeugen absichtlich viele Incidents für die gleichen Daten. Dies ermöglicht es dem Lab, diese Warnungen zu verwenden.

1. Lassen Sie im Bereich *Warnungsschwellenwert* den Wert unverändert, da die Warnung jedes Ereignis registrieren soll.

1. Lassen Sie im Bereich *Ereignisgruppierung* die Option **Alle Ereignisse zu einer einzigen Warnung gruppieren** ausgewählt, da wir bei jeder Ausführung nur eine Warnung erzeugen wollen, solange die Abfrage mehr Ergebnisse als den oben angegebenen Warnungsschwellenwert liefert.

1. Klicken Sie auf die Schaltfläche **Weiter: Incidenteinstellungen >**.

1. Überprüfen Sie die Standardoptionen auf der Registerkarte *Incidenteinstellungen *.

1. Wählen Sie die Schaltfläche **Weiter: Automatisierte Reaktion >** aus.

1. Wählen Sie die Schaltfläche **Weiter: Überprüfen und erstellen >** aus.
  
1. Wählen Sie **Speichern**.

### Aufgabe 2: Bearbeiten Ihrer neuen Regel

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren Microsoft Sentinel-Arbeitsbereich aus.

1. Wählen Sie im Bereich Konfiguration **Analytics** aus.

1. Stellen Sie sicher, dass Sie sich in der Befehlsleiste auf der Registerkarte *Aktive Regeln* befinden, und wählen Sie die Regel **Neuer CloudShell-Benutzer** aus.

1. Klicken Sie mit der rechten Maustaste auf die Regel und wählen Sie **Bearbeiten** aus dem *Popup-Menü* aus.

1. Klicken Sie auf die Schaltfläche **Weiter: Regel-Logik festlegen >**.

1. Klicken Sie auf die Schaltfläche **Weiter: Incidenteinstellungen >**.

1. Wählen Sie die Schaltfläche **Weiter: Automatisierte Reaktion >** aus.

1. Wählen Sie auf der Registerkarte *Automatisierte Antwort* unter *Automatisierungsregeln* die Option **+ Neu hinzufügen**.

1. Beim *Namen der Automatisierungsregel* geben Sie **Ebene 2** ein.

1. Bei *Aktionen* wählen Sie **Besitzer zuweisen**aus.

1. Wählen Sie dann **Mir zuweisen** aus.

1. Wählen Sie **Übernehmen** aus.

1. Wählen Sie die Schaltfläche **Weiter: Überprüfen und erstellen >** aus.
  
1. Wählen Sie **Speichern**.

### Aufgabe 3: Testen Ihrer neuen Regel

In dieser Aufgabe testen Sie ihre neue Regel für geplante Abfragen.

1. Klicken Sie in der oberen Leiste des Azure-Portals auf das Symbol **>_**, das der Cloud Shell entspricht. Möglicherweise müssen Sie zuerst das Symbol mit den Auslassungspunkten **(...)** auswählen, wenn Ihre Bildschirmauflösung zu niedrig ist.

1. Wählen Sie im Fenster *Willkommen bei Azure Cloud Shell* die Option **PowerShell** aus.

1. Wählen Sie auf der Seite *Erste Schritte* die Option **Speicherkonto bereitstellen** aus, und wählen Sie dann Ihren **Azure Pass – Sponsoring** aus dem Dropdownmenüelement *Speicherkontoabonnement* aus, und klicken Sie auf die Schaltfläche **Anwenden**.

    >**Wichtig:** Wählen Sie nicht die Option *Kein Speicherkonto erforderlich* aus. Dies führt dazu, dass die Vorfallerstellung fehlschlägt.

1. Wählen Sie auf der Seite *Speicherkonto bereitstellen* die Option **Wir erstellen ein Speicherkonto für Sie** und dann **Weiter** aus.

1. Warten Sie, bis die Cloud Shell bereitgestellt wird, und schließen Sie dann das Azure Cloud Shell-Fenster.

1. Geben Sie in der Suchleiste des Azure-Portals *Aktivität* ein und wählen Sie dann **Aktivitätsprotokoll** aus.

1. Stellen Sie sicher, dass die folgenden *Vorgangsnamen* angezeigt werden: **Liste der Speicherkontoschlüssel** und **Erstellung einer Aktualisierung des Speicherkontos**. Dies sind die Vorgänge, die der KQL-Abfrage entsprechen, die Sie zuvor überprüft haben, um die Warnung zu erzeugen. **Hinweis:** Möglicherweise müssen Sie **Aktualisieren** wählen, um die Liste zu aktualisieren.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren Microsoft Sentinel-Arbeitsbereich aus.

1. Wählen Sie unter *Bedrohungsmanagement* den Menüpunkt **Incidents** aus.

1. Betätigen Sie den Umschalter **Incident automatisch aktualisieren**.

1. Sie sollten den neu angelegten Incident sehen.

    >**Hinweis:** Die Verarbeitung des Ereignisses, das den Incident ausgelöst hat, kann länger als 5 Minuten dauern. Fahren Sie mit der nächsten Übung fort, Sie werden später zu dieser Ansicht zurückkehren.

1. Wählen Sie den Incident aus und überprüfen Sie die Informationen auf dem rechten Blatt.

## Fahren Sie mit Übung 4 fort

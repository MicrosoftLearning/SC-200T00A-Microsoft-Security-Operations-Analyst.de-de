---
lab:
  title: Übung 1 – Implementieren von Microsoft Defender for Cloud
  module: Learning Path 5 - Mitigate threats using Microsoft Defender for Cloud
---

# Lernpfad 5 – Lab 1 – Übung 1: Aktivieren von Microsoft Defender für die Cloud

## Labszenario

Sie sind eine Sicherheitsanalystin bzw. ein Sicherheitsanalyst und arbeiten in einem Unternehmen, das Cloud-Workload-Schutz mit Microsoft Defender for Cloud implementiert. In diesem Lab aktivieren Sie Microsoft Defender for Cloud.

>**Wichtig:** Die Lab-Übungen für Lernpfad 5 befinden sich in einer *eigenständigen* Umgebung. Wenn Sie das Lab vor dem Abschluss verlassen, müssen Sie die Konfigurationen erneut ausführen.

### Geschätzte Zeit bis zum Abschluss dieses Labs: 15 Minuten

### Aufgabe 1: Aktivieren von Microsoft Defender für Cloud

In dieser Aufgabe aktivieren und konfigurieren Sie Microsoft Defender for Cloud.

1. Melden Sie sich beim virtuellen Computer **WIN1** als Administrator mit dem Kennwort **Pa55w.rd**an.

1. Navigieren Sie im Microsoft Edge-Browser zu der Azure-Portal unter <https://portal.azure.com>.
  
    >**Hinweis:** Wählen Sie die Registerkarte **Ressourcen** aus, um den *Benutzernamen* und das *Kennwort* für das Lab einzugeben. Verwenden Sie das Konto **<LabUser-XXXXXXXX@LODSPRODXXX.onmicrosoft.com>** für dieses Lab.

1. Kopieren Sie im Dialogfeld **Anmelden**das von Ihrem Labhostinganbieter bereitgestellte Mandanten-E-Mail-Konto für den Administrator, und fügen Sie es ein, und wählen Sie dann **Weiter** aus.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das von Ihrem Labhostinganbieter bereitgestellte Mandantenkennwort für den Administrator, und fügen Sie es ein, und wählen Sie dann **Anmelden** aus.

1. Geben Sie in der Suchleiste des Microsoft Azure-Portals *Defender* ein und wählen Sie dann **Microsoft Defender für Cloud**.

1. Erweitern Sie im linken Navigationsmenü für Microsoft Defender for Cloud den Abschnitt *Verwaltung* und wählen Sie **Umgebungseinstellungen** aus.

1. Wählen Sie die Schaltfläche **Alles erweitern**, um alle Abonnements und Ressourcen anzuzeigen.

1. Wählen Sie das **MOC-Abonnement-lodxxxxxxxx** Abonnement (oder einen entsprechenden Namen in Ihrer Sprache).

1. Überprüfen Sie die Azure-Ressourcen, die nun durch die Defender for Cloud-Pläne geschützt sind.

    >**Wichtig:** Wenn alle Defender-Pläne *deaktiviert* sind, wählen Sie **Alle Pläne aktivieren** aus. Wählen Sie den *Microsoft Defender für APIs-Plan 1 für 200 USD/Monat* aus, und wählen Sie dann **Speichern**. Wählen Sie oben auf der Seite **Speichern** aus, und warten Sie auf die Benachrichtigung *„Defender-Pläne (für Ihr) Abonnement wurden erfolgreich gespeichert!“* erscheint.

1. Wählen Sie im Bereich Einstellungen (neben Speichern) die Registerkarte **Einstellungen und Überwachung** aus.

1. Überprüfen Sie die Überwachungserweiterungen. Sie enthält Konfigurationen für virtuelle Computer, Container und Speicherkonten.

1. Wählen Sie die Schaltfläche **Weiter** oder schließen Sie die Seite „Einstellungen und Überwachung“, indem Sie oben rechts auf der Seite auf das „X“ klicken.

1. Schließen Sie die Einstellungsseite, indem Sie auf das „X“ oben rechts auf der Seite klicken, um zu den **Umgebungseinstellungen** zurückzukehren.

<!---1. Select the Log analytics workspace you created earlier *uniquenameDefender* to review the available options and pricing.

1. Select **Enable all plans** (to the right of Select Defender plan) and then select **Save**. Wait for the *"Microsoft Defender plan for workspace uniquenameDefender were saved successfully!"* notification to appear.

    >**Note:** If the page is not being displayed, refresh your Edge browser and try again.

1. Close the Defender plans page by selecting the 'X' on the upper right of the page to go back to the **Environment settings**. --->

### Aufgabe 3: Grundlegendes zum Microsoft Defender for Cloud-Dashboard

1. Geben Sie in der Suchleiste des Microsoft Azure-Portals *Defender* ein und wählen Sie dann **Microsoft Defender für Cloud**.

1. Wählen Sie im linken Navigationsmenü für Microsoft Defender für Cloud unter dem Abschnitt *Allgemein* die Option **Übersicht**.

1. Das Blatt „Übersicht“ stellt eine einheitliche Ansicht der Sicherheitslage bereit und umfasst mehrere unabhängige Cloud-Sicherheitssäulen wie Sicherheitslage, gesetzliche Konformität, Workload-Schutz, Firewall Manager, Inventar und Informationsschutz (Vorschau). Für jede dieser Säulen gibt es auch ein eigenes Dashboard, das tiefere Einblicke und Aktionen in diesem Bereich ermöglicht und den Sicherheitsexperten eine einfache Barrierefreiheit und bessere Sichtbarkeit bereitstellt.

    >**Hinweis:** In der oberen Menüleiste können Sie durch Auswahl der Schaltfläche „Abonnements“ die Abonnements anzeigen und filtern. In dieser Übung werden wir nur ein Abonnement verwenden, aber durch die Auswahl unterschiedlicher/zusätzlicher Abonnements wird die Schnittstelle so angepasst, dass sie die Sicherheitslage der ausgewählten Abonnements widerspiegelt

1. Klicken Sie auf den Link des Symbols **Was ist neu** - es öffnet sich eine neue Registerkarte mit den neuesten Release-Hinweisen, in der Sie sich über neue Funktionen, behobene Fehler und mehr informieren können.

    >**Hinweis:** Die hochstufigen Zahlen im oberen Menü; Mit dieser Ansicht können Sie eine Zusammenfassung Ihrer Abonnements, aktiven Empfehlungen und Sicherheitswarnungen neben verbundenen Cloud-Konten sehen.

1. Wählen Sie in der oberen Menüleiste **Azure-Abonnements** aus. Dadurch gelangen Sie zu den Umgebungseinstellungen, wo Sie aus den verfügbaren Abonnements auswählen können.

1. Kehren Sie zur Seite **Übersicht** zurück und überprüfen Sie die Kachel **Sicherheitsstatus**. Sie können Ihre aktuelle *Sicherheitsbewertung* zusammen mit der Anzahl der abgeschlossenen Steuerelemente und Empfehlungen sehen. Wenn Sie diese Kachel auswählen, werden Sie zu einer Drilldownansicht für Abonnements weitergeleitet.

1. Auf der Kachel **Regulierungskonformität** erhalten Sie Einblicke in Ihre Konformität auf der Grundlage einer kontinuierlichen Bewertung von Azure- und Hybrid-Cloudumgebungen. Diese Kachel zeigt die folgenden Standards: den Microsoft Cloud Security-Benchmark und den niedrigsten regulatorischen Compliance-Standard. Zur Ansicht der Daten müssen wir zunächst die Sicherheitsrichtlinien hinzufügen.

1. Wenn Sie diese Kachel auswählen, werden Sie zum Dashboard **Regulatorische Konformität** weitergeleitet, wo Sie weitere Standards hinzufügen und die aktuellen erkunden können.

1. In der nächsten Übung werden wir uns weiter mit *Microsoft Defender für Cloud***Sicherheitslage** und **Einhaltung gesetzlicher Vorschriften** befassen.

## Fahren Sie mit Übung 2 fort

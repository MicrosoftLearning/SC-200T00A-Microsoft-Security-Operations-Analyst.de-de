---
lab:
  title: Übung 2 – Entschärfen von Angriffen mit Microsoft Defender for Endpoint
  module: Learning Path 2 - Mitigate threats using Microsoft Defender for Endpoint
---

# Lernpfad 2 – Übung 1 – Übung 2 – Minimieren von Angriffen mit Microsoft Defender for Endpoint

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod2_L1_Ex2_10_19.png)

Sie sind Security Operations Analyst in einem Unternehmen, das Microsoft Defender für Endpunkt implementiert. Ihr Vorgesetzter plant, einige Geräte zu integrieren, um einen Einblick in die erforderlichen Änderungen der Reaktionsverfahren des SecOps-Teams zu erhalten.

Um die Fähigkeiten von Defender for Endpoint zur Abwehr von Angriffen zu testen, führen Sie zwei simulierte Angriffe aus.


>**Hinweis:** Eine **[interaktive Labsimulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Mitigate%20attacks%20with%20Microsoft%20Defender%20for%20Endpoint)** ist verfügbar, mit der Sie dieses Lab in Ihrem eigenen Tempo durcharbeiten können. Möglicherweise liegen geringfügige Unterschiede zwischen der interaktiven Simulation und dem gehosteten Lab vor, aber die dargestellten Kernkonzepte und Ideen sind identisch. 


### Aufgabe 1: Überprüfung des Onboarding der Geräte

In dieser Aufgabe bestätigen Sie, dass das Gerät erfolgreich integriert ist und erstellen eine Testwarnung.

1. Wenn Sie sich nicht bereits im Microsoft 365 Defender-Portal in Ihrem Microsoft Edge-Browser befinden, gehen Sie zu (https://security.microsoft.com) und melden Sie sich als Administrator für Ihren Mandanten an.

1. Wählen Sie im linken Menü unter **Ressourcen** die Option **Geräte** aus. Bitte warten Sie, bis WIN1 auf der Seite „Geräte“ angezeigt wird, bevor Sie fortfahren. Andernfalls müssen Sie diese Aufgabe möglicherweise wiederholen, um die später generierten Warnmeldungen zu sehen.

    >**Hinweis:** Wenn Sie den Onboarding-Prozess abgeschlossen haben und nach einer Stunde keine Geräte in der Liste „Geräte“ angezeigt werden, kann dies auf ein Onboarding- oder Verbindungsproblem hindeuten.

1. Wählen Sie in der linken Menüleiste **Einstellungen** und dann auf der Seite Einstellungen **Endpunkte** aus.

1. Wählen Sie im Abschnitt Geräteverwaltung **Onboarding** und stellen Sie sicher, dass *„Windows 10 und 11“* als Betriebssystem ausgewählt ist. Die Meldung *„Erstes Gerät integriert“* zeigt nun *Abgeschlossen* an.

1. Scrollen Sie nach unten und kopieren Sie im Abschnitt *„2. Erkennungstest durchführen“* das Erkennungstest-Skript, indem Sie die Schaltfläche **Kopieren**auswählen.  

1. Geben Sie in der Windows-Suchleiste den virtuellen Computer WIN1 **CMD** ein und wählen Sie im rechten Fensterbereich **Als Administrator ausführen** für die Eingabeaufforderung aus. 

1. Wenn das Fenster „Benutzerkontensteuerung“ angezeigt wird, wählen Sie **Ja**, um die App auszuführen. 

1. Fügen Sie das Skript ein, indem Sie mit der rechten Maustaste auf die **Administrator: Eingabeaufforderung** klicken und die **Eingabetaste** drücken, um es auszuführen. **Hinweis:** Nach der Ausführung des Skripts schließt sich das Fenster automatisch.


### Aufgabe 2: Simulierte Angriffe

In dieser Aufgabe führen Sie zwei simulierte Angriffe aus, um die Funktionen von Microsoft Defender for Endpoint zu erkunden.

1. Wählen Sie im linken Menü unter **Endpunkte** die Option **Auswertung und Tutorials** und dann auf der linken Seite **Tutorials und Simulationen** aus.

1. Wählen Sie die Registerkarte **Tutorials** aus.

1. Unter *Automatisierte Untersuchung (Hintertür)* sehen Sie eine Meldung, die das Szenario beschreibt.  Klicken Sie unterhalb dieses Absatzes auf **Exemplarische Vorgehensweise lesen**. Eine neue Browser-Registerkarte mit Anweisungen zur Durchführung der Simulation wird geöffnet.

1. Suchen Sie in der neuen Browser-Registerkarte den Abschnitt **Simulation durchführen** (Seite 5, ab Schritt 2) und führen Sie die Schritte zur Durchführung des Angriffs aus. **Hinweis:** Die Simulationsdatei *RS4_WinATP-Intro-Invoice.docm* finden Sie im Portal direkt unter der **exemplarischen Vorgehensweise**, die Sie im vorherigen Schritt über die Schaltfläche **Simulationsdatei erhalten** ausgewählt haben. 

<!--- 1. Repeat the last 3 steps to run another tutorial, *Automated investigation (fileless attack)*. This is no longer working due to win1 AV --->


### Aufgabe 3: Untersuchung der Angriffe

1. Wählen Sie im Microsoft 365 Defender-Portal in der linken Menüleiste **Vorfälle und Warnungen** und dann **Vorfälle** aus.

1. Ein neuer Vorfall mit dem Namen „Mehrstufiger Vorfall …“ wird im rechten Fensterbereich angezeigt. Wählen Sie den Namen des Vorfalls, um seine Details zu laden.

    >**Hinweis:** Es kann sein, dass zunächst ein Vorfall mit dem Namen „Verdächtiger Vorfall …“ erscheint. Dieser wird später durch den oben genannten Vorfall ersetzt, wenn Microsoft 365 Defender ihn einem einzelnen Sicherheitsproblem zuordnet, einschließlich der ursprünglichen Testwarnung, die in Aufgabe 1 erstellt wurde.

1. Wählen Sie die Schaltfläche **Vorfall verwalten** aus und ein neues Fenster wird geöffnet. 

1. Geben Sie unter **Vorfall-Tags** „Tutorial“ ein und wählen Sie **Tutorial (Neu erstellen)**, um einen neuen Tag zu erstellen. 

1. Wählen Sie die Schaltfläche **Zuweisen an**  und fügen Sie Ihr Benutzerkonto (Ich) als Besitzer des Vorfalls hinzu. 

1. Erweitern Sie unter **Klassifizierung**das Dropdownmenü. 

1. Wählen Sie unter **Information, erwartete Aktivität** **Sicherheitstests** aus. 

1. Fügen Sie bei Bedarf Kommentare hinzu und wählen Sie **Speichern**, um das Ereignis zu aktualisieren und zu schließen.

1. Überprüfen Sie den Inhalt der Registerkarten *Angriffshistorie, Alarme, Ressourcen, Untersuchungen, Beweise und Reaktion* und *Zusammenfassung*. Geräte und Benutzer befinden sich unter der Registerkarte *Ressourcen*. Die Registerkarte *Angriffshistorie* zeigt das *Vorfallsdiagramm*. Der **Hinweis:** Einige Registerkarten können aufgrund der Größe Ihres Bildschirms ausgeblendet sein. Wählen Sie die Registerkarte Auslassungspunkte (…), um sie anzuzeigen.

>**Warnung:** Die Simulationen und Tutorials auf dieser Seite sind eine ausgezeichnete Quelle für praktisches Lernen.  Das Portal wird regelmäßig um Simulationen und Tutorials erweitert.  Einige dieser Simulationen und Tutorials können jedoch die Leistung der für diesen Kurs entwickelten Labs beeinträchtigen.  Führen Sie die in den Anweisungen für dieses Lernprogramm empfohlenen Simulationen und Tutorials nur durch, wenn Sie den für diesen Kurs entwickelten Azure-Mandanten verwenden.  Die anderen Simulationen und Tutorials können Sie *nach* Abschluss dieses Kurses mit diesem Mandanten durchführen.

## Damit haben Sie das Lab beendet.

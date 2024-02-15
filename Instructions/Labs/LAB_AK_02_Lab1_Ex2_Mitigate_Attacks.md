---
lab:
  title: Übung 2 – Entschärfen von Angriffen mit Microsoft Defender for Endpoint
  module: Learning Path 2 - Mitigate threats using Microsoft Defender for Endpoint
---

# Lernpfad 2 – Übung 1 – Übung 2 – Minimieren von Angriffen mit Microsoft Defender for Endpoint

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod2_L1_Ex2_10_19.png)

Sie sind Security Operations Analyst in einem Unternehmen, das Microsoft Defender für Endpunkt implementiert. Ihr Vorgesetzter plant, einige Geräte zu integrieren, um einen Einblick in die erforderlichen Änderungen der Reaktionsverfahren des SecOps-Teams zu erhalten.

Zum Erkunden der Angriffsentschärfungsfunktionen von Defender for Endpoint werden Sie das erfolgreiche Geräte-Onboarding überprüfen sowie Warnungen und Vorfälle untersuchen, die während dieses Prozesses erstellt wurden.

>**Hinweis:** Eine **[interaktive Labsimulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Mitigate%20attacks%20with%20Microsoft%20Defender%20for%20Endpoint)** ist verfügbar, mit der Sie dieses Lab in Ihrem eigenen Tempo durcharbeiten können. Möglicherweise liegen geringfügige Unterschiede zwischen der interaktiven Simulation und dem gehosteten Lab vor, aber die dargestellten Kernkonzepte und Ideen sind identisch.

### Aufgabe 1: Überprüfung des Onboarding der Geräte

In dieser Aufgabe bestätigen Sie, dass das Gerät erfolgreich integriert ist und erstellen eine Testwarnung.

1. Wenn Sie noch nicht im Microsoft Defender XDR-Portal in Ihrem Microsoft Edge-Browser sind, navigieren Sie zu https://security.microsoft.com) und melden sich als Administrator*in für Ihren Mandanten an.

1. Wählen Sie im linken Menü unter **Ressourcen** die Option **Geräte** aus. Bitte warten Sie, bis WIN1 auf der Seite „Geräte“ angezeigt wird, bevor Sie fortfahren. Andernfalls müssen Sie diese Aufgabe möglicherweise wiederholen, um die später generierten Warnmeldungen zu sehen.

    >**Hinweis:** Wenn Sie den Onboarding-Prozess abgeschlossen haben und nach einer Stunde keine Geräte in der Liste „Geräte“ angezeigt werden, kann dies auf ein Onboarding- oder Verbindungsproblem hindeuten.

1. Wählen Sie in der linken Menüleiste **Einstellungen** und dann auf der Seite Einstellungen **Endpunkte** aus.

1. Wählen Sie im Abschnitt Geräteverwaltung **Onboarding** und stellen Sie sicher, dass *„Windows 10 und 11“* als Betriebssystem ausgewählt ist. Die Meldung *„Erstes Gerät integriert“* zeigt nun *Abgeschlossen* an.

1. Scrollen Sie nach unten und kopieren Sie im Abschnitt *„2. Erkennungstest durchführen“* das Erkennungstest-Skript, indem Sie die Schaltfläche **Kopieren**auswählen.  

1. Geben Sie in der Windows-Suchleiste den virtuellen Computer WIN1 **CMD** ein und wählen Sie im rechten Fensterbereich **Als Administrator ausführen** für die Eingabeaufforderung aus.

1. Wenn das Fenster „Benutzerkontensteuerung“ angezeigt wird, wählen Sie **Ja**, um die App auszuführen. 

1. Fügen Sie das Skript ein, indem Sie mit der rechten Maustaste auf die **Administrator: Eingabeaufforderung** klicken und die **Eingabetaste** drücken, um es auszuführen.

    >**Hinweis:** Nach erfolgreicher Ausführung des Skripts wird das Fenster automatisch geschlossen, und nach ein paar Minuten werden Warnungen im Microsoft Defender XDR-Portal generiert.

<!--- ### Task 2: Simulated Attacks

>**Note:** The Evaluation lab and the Tutorials & simulations section of the portal is no longer available. Please refer to the **[interactive lab simulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Mitigate%20attacks%20with%20Microsoft%20Defender%20for%20Endpoint)** for a demonstration of the simulated attacks.

1. From the left menu, under **Endpoints**, select **Evaluation & tutorials** and then select **Tutorials & simulations** from the left side.

1. Select the **Tutorials** tab.

1. Under *Automated investigation (backdoor)* you will see a message describing the scenario. Below this paragraph, click **Read the walkthrough**. A new browser tab opens which includes instructions to perform the simulation.

1. In the new browser tab, locate the section named **Run the simulation** (page 5, starting at step 2) and follow the steps to run the attack. **Hint:** The simulation file *RS4_WinATP-Intro-Invoice.docm* can be found back in portal, just below the **Read the walkthrough** you selected in the previous step by selecting the **Get simulation file** button.

    <!--- 1. Repeat the last 3 steps to run another tutorial, *Automated investigation (fileless attack)*. This is no longer working due to win1 AV --->

### Aufgabe 2: Untersuchen von Warnungen und Vorfällen

In dieser Aufgabe untersuchen Sie die Warnungen und Vorfälle, die vom Onboarding-Erkennungstestskript in der vorherigen Aufgabe generiert wurden.

1. Wählen Sie im Microsoft Defender XDR-Portal in der linken Menüleiste **Incidents und Warnungen** und dann **Warnungen** aus.

1. Wählen Sie im Bereich **Warnungen** die Warnung namens *Verdächtige PowerShell-Befehlszeile* aus, um ihre Details zu laden.

1. Überprüfen Sie die Zeitachse *Warnungsverlauf* und dann die Registerkarten *Details* und *Empfehlungen*.

    >**Hinweis:** Unter der Registerkarte *Details* der Warnung können Sie nach unten zum Bereich *Details zum Incident* blättern und dann den Link *Ausführungsvorfall auf einem Endpunkt* auswählen, um den Vorfall zu öffnen.

1. Wählen Sie im Microsoft Defender XDR-Portal in der linken Menüleiste **Incidents und Warnungen** und dann **Incidents** aus.

1. Ein neuer Vorfall namens *Ausführungsvorfall auf einem Endpunkt* befindet sich im rechten Bereich. Wählen Sie den Namen des Vorfalls, um seine Details zu laden.

1. Wählen Sie den Link **Vorfall verwalten** (mit einem Bleistiftsymbol) aus. Daraufhin wird ein neues Fensterblatt angezeigt.

1. Geben Sie unter **Incidenttags** die Zeichenfolge „Simulation“ ein, und wählen Sie **Simulation (Neu erstellen)** aus, um ein neues Tag zu erstellen.

1. Wählen Sie die Schaltfläche **Zuweisen an**  und fügen Sie Ihr Benutzerkonto (Ich) als Besitzer des Vorfalls hinzu.

1. Erweitern Sie unter **Klassifizierung**das Dropdownmenü.

1. Wählen Sie unter **Information, erwartete Aktivität** **Sicherheitstests** aus.

1. Fügen Sie bei Bedarf Kommentare hinzu und wählen Sie **Speichern**, um das Ereignis zu aktualisieren und zu schließen.

1. Überprüfen Sie den Inhalt der Registerkarten *Angriffshistorie, Alarme, Ressourcen, Untersuchungen, Beweise und Reaktion* und *Zusammenfassung*. Geräte und Benutzer:innen befinden sich unter der Registerkarte *Ressourcen*. In einem echten Vorfall wird auf der Registerkarte *Angriffsverlauf* das *Vorfalldiagramm* angezeigt. **Hinweis:** Einige Registerkarten sind möglicherweise wegen der Größe Ihres Displays nicht sichtbar. Wählen Sie die Registerkarte Auslassungspunkte (…), um sie anzuzeigen.

<!---    >**Warning:** The simulated attacks here are an excellent source of learning through practice. Only perform the attacks in the instructions provided for this lab when using the course provided Azure tenant.  You may perform other simulated attacks *after* this training course is complete with this tenant. --->

## Damit haben Sie das Lab beendet

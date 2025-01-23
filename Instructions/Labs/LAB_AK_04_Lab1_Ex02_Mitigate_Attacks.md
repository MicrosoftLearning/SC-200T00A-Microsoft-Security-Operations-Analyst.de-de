---
lab:
  title: 'Übung 4: Abwehren von Angriffen mit Microsoft Defender for Endpoint'
  module: Learning Path 4 - Mitigate threats using Microsoft Defender for Endpoint
---

# Lernpfad 4 – Lab 1 – Übung 2: Abwehr von Angriffen mit Microsoft Defender for Endpoint

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod2_L1_Ex2_10_19.png)

Sie sind Security Operations Analyst in einem Unternehmen, das Microsoft Defender für Endpunkt implementiert. Ihr Vorgesetzter plant, einige Geräte zu integrieren, um einen Einblick in die erforderlichen Änderungen der Reaktionsverfahren des SecOps-Teams zu erhalten.

Zum Erkunden der Angriffsentschärfungsfunktionen von Defender for Endpoint werden Sie das erfolgreiche Geräte-Onboarding überprüfen sowie Warnungen und Vorfälle untersuchen, die während dieses Prozesses erstellt wurden.

### Geschätzte Zeit bis zum Abschluss dieses Labs: 30 Minuten

### Aufgabe 1: Überprüfung des Onboarding der Geräte

In dieser Aufgabe bestätigen Sie, dass das Gerät erfolgreich integriert ist und erstellen eine Testwarnung.

1. Wenn Sie sich nicht bereits im Microsoft Defender XDR-Portal in Ihrem Microsoft Edge-Browser befinden, gehen Sie zu (<https://security.microsoft.com>) und melden Sie sich als Admin für Ihren Mandanten an.

1. Wählen Sie im linken Menü unter **Ressourcen** die Option **Geräte** aus. Bitte warten Sie, bis WIN1 auf der Seite „Geräte“ angezeigt wird, bevor Sie fortfahren. Andernfalls müssen Sie diese Aufgabe möglicherweise wiederholen, um die später generierten Warnmeldungen zu sehen.

    >**Hinweis:** Wenn Sie den Onboarding-Prozess abgeschlossen haben und nach einer Stunde keine Geräte in der Liste „Geräte“ angezeigt werden, kann dies auf ein Onboarding- oder Verbindungsproblem hindeuten.

1. Erweitern Sie im Microsoft Defender XDR-Portal auf der linken Menüleiste den Abschnitt **System**, wählen Sie **Einstellungen** und anschließend auf der Seite *Einstellungen* **Endpunkte** aus.

1. Wählen Sie im Abschnitt Geräteverwaltung **Onboarding** und stellen Sie sicher, dass *„Windows 10 und 11“* als Betriebssystem ausgewählt ist. Die Meldung *„Erstes Gerät integriert“* zeigt nun *Abgeschlossen* an.

1. Scrollen Sie nach unten und kopieren Sie im Abschnitt *„2. Erkennungstest durchführen“* das Erkennungstest-Skript, indem Sie die Schaltfläche **Kopieren**auswählen.  

1. Geben Sie in der Windows-Suchleiste den virtuellen Computer WIN1 **CMD** ein und wählen Sie im rechten Fensterbereich **Als Administrator ausführen** für die Eingabeaufforderung aus.

1. Wenn das Fenster „Benutzerkontensteuerung“ angezeigt wird, wählen Sie **Ja**, um die App auszuführen. 

1. Fügen Sie das Skript ein, indem Sie mit der rechten Maustaste auf die **Administrator: Eingabeaufforderung** klicken und die **Eingabetaste** drücken, um es auszuführen.

    >**Hinweis:** Nach erfolgreicher Ausführung des Skripts wird das Fenster automatisch geschlossen, und nach ein paar Minuten werden Warnungen im Microsoft Defender XDR-Portal generiert.

### Aufgabe 2: Untersuchen von Warnungen und Vorfällen

In dieser Aufgabe untersuchen Sie die Warnungen und Vorfälle, die vom Onboarding-Erkennungstestskript in der vorherigen Aufgabe generiert wurden.

1. Erweitern Sie im Microsoft Defender XDR-Portal auf der linken Menüleiste **Untersuchung und Antwort** und anschließend **Incidents und Warnungen**, und wählen Sie **Warnungen** aus.

    >**Hinweis:** Auf aktualisierten Versionen der Seite des Microsoft Defender XDR-Portals befindet sich *Incidents und Warnungen* unter der Menüüberschrift *Untersuchungen und Antwort*.

1. Wählen Sie im Bereich **Warnungen** die Warnung mit dem Namen *[TestAlert] Verdächtige PowerShell-Befehlszeile* aus, um die Details der Warnung zu laden.

1. Überprüfen Sie die Zeitachse *Warnungsverlauf* und dann die Registerkarten *Details* und *Empfehlungen*.

    >**Hinweis:** Unter der Registerkarte *Details* der Warnung können Sie nach unten zum Bereich *Details zum Incident* blättern und dann den Link *Ausführungsvorfall auf einem Endpunkt* auswählen, um den Vorfall zu öffnen.

1. Wählen Sie im Microsoft Defender XDR-Portal in der linken Menüleiste **Incidents und Warnungen** und dann **Incidents** aus.

1. Deaktivieren Sie den Filter *Warnungsschweregrad*, indem Sie auf der rechten Seite des Filters das Symbol **X** auswählen.

1. Im rechten Bereich wird ein neuer Incident namens *[TestAlert] Verdächtige PowerShell-Befehlszeile* angezeigt. Wählen Sie den Namen des Vorfalls, um seine Details zu laden.

1. Wählen Sie den Link **Vorfall verwalten** (mit einem Bleistiftsymbol) aus. Daraufhin wird ein neues Fensterblatt angezeigt.

1. Geben Sie unter **Incidenttags** die Zeichenfolge „Simulation“ ein, und wählen Sie **Simulation (Neu erstellen)** aus, um ein neues Tag zu erstellen.

1. Wählen Sie die Schaltfläche **Zuweisen an**  und fügen Sie Ihr Benutzerkonto (Ich) als Besitzer des Vorfalls hinzu.

1. Erweitern Sie unter **Klassifizierung**das Dropdownmenü.

1. Wählen Sie unter **Information, erwartete Aktivität** **Sicherheitstests** aus.

1. Wählen Sie **Speichern** aus, um den Vorfall zu aktualisieren und den Vorgang abzuschließen.

1. Überprüfen Sie den Inhalt der Registerkarten *Angriffshistorie, Alarme, Ressourcen, Untersuchungen, Beweise und Reaktion* und *Zusammenfassung*. Geräte und Benutzer:innen befinden sich unter der Registerkarte *Ressourcen*. In einem echten Vorfall wird auf der Registerkarte *Angriffsverlauf* das *Vorfalldiagramm* angezeigt. **Hinweis:** Einige Registerkarten sind möglicherweise wegen der Größe Ihres Displays nicht sichtbar. Wählen Sie die Registerkarte Auslassungspunkte (…), um sie anzuzeigen.

### Aufgabe 3: Simulieren eines Angriffs

>**Warnung:** Dieser simulierte Angriff ist eine hervorragende praktische Lernquelle. Führen Sie den Angriff aus den Anweisungen für diese Übung nur aus, wenn Sie den für den Kurs bereitgestellten Azure-Mandanten verwenden.  Sie können andere simulierte Angriffe für diesen Mandanten durchführen, *nachdem* dieser Schulungskurs abgeschlossen wurde.

In dieser Aufgabe simulieren Sie einen Angriff auf die WIN1-VM (durch Ausführen eines PowerShell-Skripts) und überprüfen, ob der Angriff von Microsoft Defender for Endpoint erkannt und abgewehrt wird.

1. Geben Sie auf der virtuellen Maschine WIN1 **PowerShell** in die Suchleiste ein und *klicken Sie dann mit der rechten Maustaste auf* **Windows PowerShell** und wählen Sie die Option *Als Administrator ausführen* aus.

1. Wenn das Fenster „Benutzerkontensteuerung“ angezeigt wird, wählen Sie **Ja**, um die App auszuführen.

1. Navigieren Sie zur Verwendung des Skripts in **Windows PowerShell (Administrator)** zum Ordner *\Users\Admin\Desktop\Allfiles*, geben Sie *.\AttackScript.ps1* ein, und drücken Sie die **EINGABETASTE**, um es auszuführen. Geben Sie als Nächstes **R** ein, und drücken Sie die **EINGABETASTE**, um es *einmal auszuführen*.

1. Das Skript erzeugt eine Ausgabe mit mehreren Zeilen und die Meldung, dass *Domänencontroller in der Domäne nicht aufgelöst werden konnten*. Ein paar Sekunden später wird die *Editor*-App geöffnet. Ein simulierter Angriffscode wird im Editor eingefügt. Lassen Sie die automatisch generierte Editor-Instanz geöffnet, um das vollständige Szenario zu erleben. Der simulierte Angriffscode versucht, mit einer externen IP-Adresse zu kommunizieren (simuliert einen C2-Server).

### Aufgabe 4: Untersuchen des simulierten Angriffs als einzelner Incident

1. Erweitern Sie im Microsoft Defender XDR-Portal auf der linken Menüleiste **Untersuchung und Antwort** und anschließend **Incidents und Warnungen**, und wählen Sie **Incidents** aus.

    >**Hinweis:** Auf aktualisierten Versionen der Seite des Microsoft Defender XDR-Portals befindet sich *Incidents und Warnungen* unter der Menüüberschrift *Untersuchungen und Antwort*.

1. Ein neuer Incident namens *Mehrstufiger Incident mit Verteidigungsumgehung und -ermittlung auf einem Endpunkt* befindet sich im rechten Bereich. Wählen Sie den Namen des Vorfalls, um seine Details zu laden.

    >**Hinweis:** Wenn der Incident nicht angezeigt wird, müssen Sie den Filter *Warnungsschweregrad* löschen, indem Sie auf der rechten Seite des Filters das Symbol **X** auswählen.

1. Reduzieren Sie auf der Registerkarte *Angriffsverlauf* die Bereiche **Warnungen** und **Incidentdetails**, um das vollständige **Incidentdiagramm** anzuzeigen.

1. Zeigen Sie mit der Maus auf die **Incidentdiagrammknoten** und wählen Sie sie aus, um die *Entitäten* zu überprüfen.

1. Erweitern Sie den Bereich **Warnungen** (links) erneut und klicken Sie auf das Symbol **Angriffsverlauf wiedergeben** *-Ausführen* aus. Dadurch wird die Angriffszeitleiste mit den einzelnen Warnungen angezeigt und das *Incidentdiagramm* dynamisch ausgefüllt.

1. Überprüfen Sie den Inhalt der Registerkarten *Angriffshistorie, Alarme, Ressourcen, Untersuchungen, Beweise und Reaktion* und *Zusammenfassung*. Geräte und Benutzer:innen befinden sich unter der Registerkarte *Ressourcen*. **Hinweis:** Einige Registerkarten sind möglicherweise wegen der Größe Ihres Displays nicht sichtbar. Wählen Sie die Registerkarte Auslassungspunkte (…), um sie anzuzeigen.

1. Wählen Sie auf der Registerkarte **Beweis und Antwort** die Option **IP-Adressen** und dann die angezeigte *IP-Adresse* aus. Überprüfen Sie im Popupfenster die IP-Adressdetails, scrollen Sie nach unten, und wählen Sie die Schaltfläche **IP-Adressseite öffnen** aus.

1. Überprüfen Sie auf der Seite *IP-Adresse* die Registerkarten *„Übersicht“, „Incidents und Warnungen“ und „Beobachtet in Organisationen“*. Einige Registerkarten enthalten möglicherweise keine Informationen für die IP-Adresse.

## Damit haben Sie das Lab beendet

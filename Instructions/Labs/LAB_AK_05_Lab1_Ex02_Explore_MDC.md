---
lab:
  title: Übung 2 – Minimieren von Bedrohungen mithilfe von Microsoft Defender for Cloud
  module: Learning Path 5 - Mitigate threats using Microsoft Defender for Cloud
---

# Lernpfad 5 – Lab 1 – Übung 2: Minimieren von Bedrohungen mithilfe von Microsoft Defender for Cloud

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod3_L1_Ex2.png)

Sie arbeiten als Security Operations Analyst in einem Unternehmen, das Microsoft Defender for Cloud implementiert hat. Sie müssen auf Empfehlungen und Sicherheitswarnungen reagieren, die von Microsoft Defender for Cloud generiert werden.

>**Wichtig:** Die Lab-Übungen für Lernpfad 5 befinden sich in einer *eigenständigen* Umgebung. Wenn Sie das Lab vor dem Abschluss verlassen, müssen Sie die Konfigurationen erneut ausführen.

### Geschätzte Zeit bis zum Abschluss dieses Labs: 15 Minuten

### Aufgabe 1: Erkunden der Einhaltung gesetzlicher Bestimmungen

In dieser Aufgabe überprüfen Sie die Konfiguration für die Einhaltung gesetzlicher Bestimmungen in Microsoft Defender for Cloud. 

>**Wichtig:** Die nächsten Schritte werden in einer anderen VM ausgeführt als der, in der Sie zuvor gearbeitet haben. Suchen Sie nach den Namensverweisen der virtuellen Maschine.

1. Melden Sie sich beim virtuellen Computer **WIN1** als Administrator mit dem Kennwort **Pa55w.rd**an.  

1. Öffnen Sie im Microsoft Edge-Browser das Azure-Portal unter <https://portal.azure.com>.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Defender* ein und wählen Sie dann **Microsoft Defender for Cloud** aus.

1. Wählen Sie unter *Cloudsicherheit* die Option **Einhaltung gesetzlicher Bestimmungen** aus den linken Menüelementen aus.

    >**Hinweis:** Möglicherweise müssen Sie diese Seite aktualisieren, wenn die Registerkarten der *Symbolleiste* nicht angezeigt werden.

1. Wählen Sie auf der Symbolleiste **Compliancestandards verwalten** aus.

1. Wählen Sie Ihr Abonnement aus.

    >**Hinweis:** Wenn Sie über eine Hierarchie von Verwaltungsgruppen verfügen, wählen Sie **Alle erweitern** aus, um Ihr Abonnement zu finden.

1. Wählen Sie unter *Einstellungen* im Portalmenü **Sicherheitsrichtlinien**.

1. Führen Sie einen Bildlauf nach unten aus, und überprüfen Sie die standardmäßig für Sie verfügbaren „Sicherheitsstandards“.

1. Verwenden Sie das Suchfeld, um *ISO 27001:2013* zu finden.

1. Schalten Sie den Schieberegler**Status** rechts neben *ISO 27001:2013* auf **Ein** um.

    >**Hinweis:** Einige Standards erfordern die Zuweisung einer Azure Policy-Initiative.

1. Wählen Sie im Seitenmenü **Aktualisieren** aus, um zu bestätigen, dass *ISO 27001:2013* für Ihr Abonnement auf *Ein* festgelegt wird.

1. Schließen Sie die Seite *Sicherheitsrichtlinien*, indem Sie rechts oben auf der Seite das „X“ auswählen, um zu den **Umgebungseinstellungen** zurückzukehren.

    >**Hinweis:** Möglicherweise möchten Sie zu einem späteren Zeitpunkt zu *Einhaltung gesetzlicher Bestimmungen* zurückkehren, um die neuen Standardkontrollen und Empfehlungen zu überprüfen.

### Aufgabe 2: Erkunden der Sicherheitsempfehlungen

In dieser Aufgabe werden Sie die Empfehlungen zum Cloud Security Posture Management überprüfen.

1. Wählen Sie im Abschnitt *Allgemein* im Navigationsmenü **Empfehlungen** aus.

1. Wählen Sie zunächst die Option **Filter hinzufügen** und dann **Ressourcentyp** aus.

1. Aktivieren Sie das Kontrollkästchen **Computer – Azure Arc**, und wählen Sie dann die Schaltfläche **Anwenden** aus.

    >**Hinweis:** Wenn **Maschinen – Azure Arc** nicht aufgeführt ist, aktualisieren Sie die Seite.

1. Wählen Sie eine Empfehlung aus, deren Status nicht *Abgeschlossen* ist. Möglicherweise müssen Sie nach rechts scrollen, um die Spalte *Status* zu sehen.

1. Überprüfen Sie die Empfehlung, und führen Sie auf der Registerkarte **Aktion ausführen** einen Bildlauf nach unten zu **Delegat** durch, und wählen Sie **Besitzer zuweisen und Fälligkeitsdatum festlegen** aus.

1. Lassen Sie im Fenster **Zuweisung erstellen** die Option *Typ* auf *Defender for Cloud* festgelegt, und erweitern Sie die **Zuweisungsdetails**.

1. Geben Sie in das Feld *E-Mail-Adresse* Ihre Administrator-E-Mail-Adresse ein. **Tipp:** Sie können diese aus den Anweisungen auf der Registerkarte *Ressourcen* kopieren.

1. Untersuchen Sie die Optionen *Wartungszeitrahmen festlegen* und *E-Mail-Benachrichtigungen festlegen*, und wählen Sie **Erstellen** aus.

    >**Hinweis:** Wenn Sie die Fehlermeldung *Die angeforderten Zuweisungen konnten nicht erstellt werden* erhalten, versuchen Sie es später noch einmal.

1. Schließen Sie die Empfehlungsseite, indem Sie auf das ‚X‘ in der oberen rechten Ecke des Fensters klicken.


### Aufgabe 3: Verringern von Sicherheitswarnungen

In dieser Aufgabe laden Sie Beispielsicherheitswarnungen und überprüfen die Warnungsdetails.


1. Wählen Sie im Portalmenü unter *Allgemein* die Option **Sicherheitswarnungen** aus.

1. Wählen Sie in der Befehlsleiste **Beispielwarnungen** aus. **Hinweis:** Möglicherweise müssen Sie die Schaltfläche mit den Auslassungspunkten (...) in der Befehlsleiste auswählen.

1. Vergewissern Sie sich im Bereich Beispielwarnungen erstellen (Vorschau), dass Ihr Abonnement ausgewählt ist und dass alle Beispielwarnungen im Bereich *Defender für Cloud-Pläne* ausgewählt sind.

1. Klicken Sie auf **Beispielwarnungen erstellen**.  

    >**Hinweis:** Die Erstellung der Beispielwarnungen kann einige Minuten dauern. Warten Sie auf die Meldung *„Beispielwarnungen erfolgreich erstellt“*.

1. Wählen Sie anschließend **Aktualisieren** aus (sofern erforderlich), damit die Warnungen unter dem Bereich *Sicherheitswarnungen* angezeigt werden.

1. Wählen Sie eine interessante Warnung mit dem *Schweregrad* *Hoch* aus, und führen Sie die folgenden Aktionen aus:

    - Aktivieren Sie das Kontrollkästchen der Warnung, und der Bereich mit Details zur Warnung sollte eingeblendet werden. Wählen Sie **Alle Informationen anzeigen** aus.

    - Überprüfen und lesen Sie die Registerkarte *Warnungdetails*.

    - Wählen Sie die Registerkarte **Aktion ausführen** aus, oder scrollen Sie nach unten, und wählen Sie die Schaltfläche **Weiter: Aktion ausführen** am Ende der Seite aus.

    - Lesen Sie die Informationen zu *Maßnahmen ergreifen*. Beachten Sie die Abschnitte zum Ergreifen von Maßnahmen, die je nach Art der Warnung verfügbar sind: Ressourcenkontext untersuchen, Bedrohung verringern, zukünftige Angriffe verhindern, automatische Reaktion auslösen und ähnliche Warnungen unterdrücken.

## Damit haben Sie das Lab beendet

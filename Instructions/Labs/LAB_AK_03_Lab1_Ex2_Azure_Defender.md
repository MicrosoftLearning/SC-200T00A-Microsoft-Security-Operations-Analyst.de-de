---
lab:
  title: Übung 2 – Minimieren von Bedrohungen mithilfe von Microsoft Defender for Cloud
  module: Learning Path 3 - Mitigate threats using Microsoft Defender for Cloud
---

# Lernpfad 3 – Lab 1 – Übung 2 – Minimieren von Bedrohungen mithilfe von Microsoft Defender for Cloud

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod3_L1_Ex2.png)

Sie arbeiten als Security Operations Analyst in einem Unternehmen, das Microsoft Defender for Cloud implementiert hat. Sie müssen auf Empfehlungen und Sicherheitswarnungen reagieren, die von Microsoft Defender for Cloud generiert werden.

>**Hinweis:** Eine **[interaktive Labsimulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Mitigate%20threats%20using%20Microsoft%20Defender%20for%20Cloud)** ist verfügbar, mit der Sie dieses Lab in Ihrem eigenen Tempo durcharbeiten können. Möglicherweise liegen geringfügige Unterschiede zwischen der interaktiven Simulation und dem gehosteten Lab vor, aber die dargestellten Kernkonzepte und Ideen sind identisch. 


### Aufgabe 1: Erkunden der Einhaltung gesetzlicher Bestimmungen

In dieser Aufgabe überprüfen Sie die Konfiguration der Einhaltung gesetzlicher Bestimmungen in Microsoft Defender for Cloud. 

>**Wichtig:** Die nächsten Schritte werden in einer anderen VM ausgeführt als der, in der Sie zuvor gearbeitet haben. Suchen Sie nach den Namensverweisen der virtuellen Maschine.

1. Melden Sie sich beim virtuellen Computer **WIN1** als Administrator mit dem Kennwort **Pa55w.rd**an.  

1. Öffnen Sie im Edge-Browser das Azure-Portal unter (https://portal.azure.com).

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Defender* ein und wählen Sie dann **Microsoft Defender for Cloud** aus.

1. Wählen Sie unter *Cloudsicherheit* im Menü des Portals **Einhaltung gesetzlicher Bestimmungen** aus.

1. Wählen Sie in der Symbolleiste **Verwalten von Konformitätsrichtlinien** aus.

1. Wählen Sie Ihr Abonnement aus.

    >**Hinweis:** Wenn Sie über eine Hierarchie von Verwaltungsgruppen verfügen, wählen Sie **Alle erweitern** aus, um Ihr Abonnement zu finden.

1. Wählen Sie im Portalmenü unter *Einstellungen* die Option **Sicherheitsrichtlinie** aus.

1. Scrollen Sie nach unten, und überprüfen Sie die standardmäßig für Sie verfügbaren „Sicherheitsstandards“.

1. Verwenden Sie das Suchfeld, um *ISO 27001:2013* zu finden.

1. Schalten Sie den Schieberegler**Status** rechts neben *ISO 27001:2013* auf **Ein** um.

    >**Hinweis:** Einige Standards erfordern die Zuweisung einer Azure Policy-Initiative.

1. Wählen Sie im Seitenmenü **Aktualisieren** aus, um zu bestätigen, dass *ISO 27001:2013* für Ihr Abonnement auf *Ein* festgelegt wird.

1. Schließen Sie die Seite *Sicherheitsrichtlinien*, indem Sie rechts oben auf der Seite das „X“ auswählen, um zu den **Umgebungseinstellungen** zurückzukehren.

    >**Hinweis:** Möglicherweise möchten Sie zu einem späteren Zeitpunkt zu *Einhaltung gesetzlicher Bestimmungen* zurückkehren, um die neuen Standardkontrollen und Empfehlungen zu überprüfen.

### Aufgabe 2: Erkunden von Sicherheitsstatus und Empfehlungen

In dieser Aufgabe überprüfen Sie die Verwaltung vom Cloudsicherheitsstatus.  Die Neuberechnung der Informationen zur Sicherheitsbewertung können 24 Stunden dauern. Es wird empfohlen, diese Aufgabe in 24 Stunden erneut auszuführen.

1. Wählen Sie im Portalmenü unter *Cloudsicherheit* **Sicherheitsstatus** aus.

1. Die Sicherheitsbewertung wird höchstwahrscheinlich *N/A* anzeigen, bis die Bewertung berechnet wurde.

1. Wählen Sie im Portalmenü unter *Allgemein* die Option **Empfehlungen** aus.

1. Erkunden Sie die Empfehlungen, die für Ihr Abonnement und Ihren WINServer (Arc Server) bereitgestellt werden.

1. Wählen Sie eine Empfehlung, deren Status für WINServer nicht *„Abgeschlossen“* lautet.

1. Lesen Sie die Empfehlung und scrollen Sie nach unten, um das Kontrollkästchen „WINServer“ zu **markieren**. **Hinweis:** Möglicherweise müssen Sie **Betroffene Ressourcen** auswählen, um sie anzuzeigen.

1. Wählen Sie **Besitzer zuweisen** und dann **Besitzer wählen** aus.

1. Geben Sie im Feld *E-Mail-Adresse* Ihre Administrator-E-Mail-Adresse ein. **Tipp:** Sie können diese aus den Anweisungen auf der Registerkarte *Ressourcen* kopieren.

1. Klicken Sie auf **Zurück**, ändern Sie das *Fälligkeitsdatum* nach Ihren Wünschen und klicken Sie auf **Speichern**.

    >**Hinweis:** Wenn Sie die Fehlermeldung *Die angeforderten Zuweisungen konnten nicht erstellt werden* erhalten, versuchen Sie es später noch einmal.

1. Schließen Sie die Empfehlungsseite, indem Sie auf das ‚X‘ in der oberen rechten Ecke des Fensters klicken.


### Aufgabe 3: Verringern von Sicherheitswarnungen

In dieser Aufgabe laden Sie Beispiele für Sicherheitswarnungen und lesen die Details der Warnungen.


1. Wählen Sie im Portalmenü unter *Allgemein* die Option **Sicherheitswarnungen** aus.

1. Wählen Sie in der Befehlsleiste **Beispielwarnungen** aus. **Hinweis:** Möglicherweise müssen Sie auf die Schaltfläche mit den Auslassungspunkten (...) in der Befehlsleiste klicken.

1. Vergewissern Sie sich im Bereich Beispielwarnungen erstellen (Vorschau), dass Ihr Abonnement ausgewählt ist und dass alle Beispielwarnungen im Bereich *Defender für Cloud-Pläne* ausgewählt sind.

1. Klicken Sie auf **Beispielwarnungen erstellen**.  

    >**Hinweis:** Die Erstellung der Beispielwarnungen kann einige Minuten dauern. Warten Sie auf die Meldung *„Beispielwarnungen erfolgreich erstellt“*. 

1. Sobald der Vorgang abgeschlossen ist, klicken Sie auf **Aktualisieren**, um die Warnungen im Bereich *Sicherheitswarnungen* anzuzeigen.

1. Führen Sie die folgenden Aktionen für die Warnungen durch, die Ihre Aufmerksamkeit erregt haben:

    - Wählen Sie die Warnung aus. Informationen über die Warnung sollten angezeigt werden. Wählen Sie **Alle Informationen anzeigen** aus.

    - Überprüfen und lesen Sie die Registerkarte *Warnungdetails*.

    - Wählen Sie die Registerkarte **Maßnahmen ergreifen** aus oder wählen Sie unten auf der Seite die Schaltfläche **Weiter: Maßnahmen ergreifen** aus.

    - Lesen Sie die Informationen zu *Maßnahmen ergreifen*. Beachten Sie die Abschnitte zum Ergreifen von Maßnahmen, die je nach Art der Warnung verfügbar sind: Ressourcenkontext untersuchen, Bedrohung verringern, zukünftige Angriffe verhindern, automatische Reaktion auslösen und ähnliche Warnungen unterdrücken.

## Damit haben Sie das Lab beendet.

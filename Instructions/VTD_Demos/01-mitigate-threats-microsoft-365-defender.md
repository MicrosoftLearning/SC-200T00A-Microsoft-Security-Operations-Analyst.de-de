# Modul 1 – Abwehr von Bedrohungen mithilfe von Microsoft 365 Defender

**Hinweis:** Der erfolgreiche Abschluss dieser Demo hängt davon ab, alle Schritte im  [Dokument](00-prerequisites.md) „Voraussetzungen“ abzuschließen.

## Verwenden des Microsoft Defender-Portals

In dieser Aufgabe machen Sie sich mit den Funktionen des Microsoft 365 Defender-Portals vertraut.

- Home (Dashboard)
- Incidents und Warnungen
- Suche
- Info-Center
- Bedrohungsanalyse
- Sicherheitsbewertung
- Endpunkte
- Verwaltung von Sicherheitsrisiken
- E-Mails und Zusammenarbeit
- Cloud-Apps
- Berichte
- Einstellungen
- Berechtigungen

1. Wenn Sie sich nicht bereits im Microsoft Defender Security Center in Ihrem Browser befinden, gehen Sie zum Microsoft Defender Security Center unter (https://security.microsoft.com) als Admin für Ihren Mandanten angemeldet.

1. Das **Home**-Dashboard gibt Ihnen einen Überblick über Ihren Sicherheitsstatus. Sie können die Ansicht anpassen, indem Sie **Karten hinzufügen** oder Karten entfernen. Um eine Karte zu entfernen, wählen Sie die Auslassungspunkte (...) auf einer Karte aus.
1. Wählen Sie dann **Incidents und Warnungen** aus. Dadurch werden die folgenden Menüoptionen erweitert. Hier werden Untersuchungen durchgeführt.
1. Machen Sie dasselbe mit **Hunting**, um die Abfrageseite **Erweitertes Hunting** zu öffnen. 
    1. Hier können Sie KQL-Abfragen ausführen.
1. Wählen Sie **Aktionen und Übermittlungen** aus, um das **Info-Center** und **Übermittlungen** zu öffnen.
1. Wählen Sie **Threat Intelligence** und dann **Threat Analytics** aus. Diese Seite enthält Einblicke in die allgemeinen Sicherheitsrisiken und Sicherheitsrisiken (Common Vulnerabilities and Exposures, CVE), die Sie nachverfolgen müssen. Wählen Sie **Sicherheitsbewertung** aus und erkunden Sie die Registerkarten. Werfen Sie hier einen Blick auf **Empfohlene Aktionen**.
1. Wählen Sie **Ressourcen** und **Geräte** für Ihr `Device Inventory` aus. Hier können Sie das Onboarding für Geräte durchführen oder mit einem bestehenden Inventar arbeiten.
1. Ebenfalls unter `Assets` finden Sie **Identitäten**
1. Im Abschnitt **Endpunkte** finden Sie **Sicherheitsrisikomanagement**. `Vulnerability management` hat ein `Dashboard`, in dem Sie Ihren Gefährdungsscore überprüfen können.
1. Eine weitere Funktion innerhalb von **Endpunkte** ist **Auswertungen und Simulationen**. Im **Auswertungs-Lab** können Sie isolierte Geräte einrichten, um Schadsoftware zu untersuchen.
1. Unter **E-Mail und Zusammenarbeit** finden Sie die Funktionen von `Defender for Office 365`. Unter **Untersuchungen** sehen Sie die Ergebnisse der automatischen Untersuchung und Reaktion (AIR) auf Bedrohungen.
1. Ebenfalls unter **E-Mail und Zusammenarbeit** finden Sie **Richtlinien und Regeln**. Sie konfigurieren hier **Bedrohungs- und Warnungsrichtlinien**.
1. Scrollen Sie nach unten zu **Cloud-Apps**. Dies ist der Abschnitt **Microsoft Defender for Cloud Apps**-Dienst. Unter **App-Governance** können Sie App-Richtlinien festlegen.
1. Im nächsten Abschnitt finden Sie **Berichte** für die Microsoft 365 Defender-Dienste, **Audit**, wo Sie die Aufzeichnung von Benutzerverwaltungsaktivitäten aktivieren können, sowie **Berechtigungen** und **Einstellungen**.
1. In **Berechtigungen** können Sie die Rollen **Azure AD** und **Endpunkt** konfigurieren.
1. **Einstellungen** ist der Ort, an dem allgemeine Konfigurationen wie Zeitzone und E-Mail-Benachrichtigungen sowie granulare Einstellungen für Endpunkte, Identitäten und Geräteerkennung eingegeben werden.
1. Wählen Sie **Einstellungen** und dann **Endpunkte** aus. Hier können Sie **Lizenzen** anzeigen und hinzufügen. Wählen Sie dann **Erweiterte Funktionen** aus. Blättern Sie durch die Liste der Funktionen, aber nehmen Sie noch keine Änderungen vor.
1. Verlassen Sie schließlich **Einstellungen** und wählen Sie in der linken Hauptmenüliste **Weitere Ressourcen** aus. Sie sollten Karten oder Kacheln mit Links für **Microsoft Purview Compliance**, **Azure Active Directory** und andere Funktionen sehen, die nicht direkt zu **Microsoft 365 Defender** gehören. Klicken Sie auf die Schaltfläche **Öffnen** für **Microsoft Purview Compliance**. Das Compliance-Portal wird geöffnet.

## Verbinden von Microsoft Sentinel und Microsoft Defender XDR

In dieser Aufgabe verbinden Sie einen Microsoft Sentinel-Arbeitsbereich mit Microsoft Defender XDR.

**Hinweis:** Es gibt Funktionsunterschiede zwischen dem Microsoft Defender XDR-Portal und dem Microsoft Sentinel-Portal. Die Benutzeroberfläche und die Schritte können sich von den Lab-Anweisungen unterscheiden.

1. Melden Sie sich mit dem Kennwort beim virtuellen **WIN1**-Computer als *Administrierende Fachkraft* an: **Pa55w.rd**.  

1. Starten Sie den Microsoft Edge-Browser.

1. Wechseln Sie im Edge-Browser zum Microsoft Defender XDR-Portal unter <https://security.microsoft.com>.

1. Kopieren Sie im Dialogfeld **Anmelden**das von Ihrem Labhostinganbieter bereitgestellte Mandanten-E-Mail-Konto für den Administrator, und fügen Sie es ein, und wählen Sie dann **Weiter** aus.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das von Ihrem Labhostinganbieter bereitgestellte Mandantenkennwort für den Administrator, und fügen Sie es ein, und wählen Sie dann **Anmelden** aus.

    >**Tipp:** Das Administrator-E-Mail-Konto und Kennwort des Mandanten finden Sie auf der Registerkarte „Ressourcen“.

1. Auf dem **Startbildschirm** des **Defender XDR**-Portals sollten Sie oben ein Banner mit der Nachricht *Bringen Sie Ihr SIEM und XDR an einem Ort zusammen* sehen. Wählen Sie die Schaltfläche **Arbeitsbereiche verbinden** aus.

1. Wählen Sie auf der Seite *Arbeitsbereich auswählen* den von Ihnen zuvor erstellten **Microsoft Sentinel**-Arbeitsbereich aus.

    >**Hinweis:** Er sollte einen Namen wie *uniquenameDefender* haben.

1. Wählen Sie die Schaltfläche **Weiter** aus.

    >**Hinweis:** Wenn die Schaltfläche *Weiter* deaktiviert oder abgeblendet ist und eine Fehlermeldung angezeigt wird, dass der Microsoft Sentinel-Arbeitsbereich *nicht in Defender XDR integriert ist*, versuchen Sie, die Defender XDR-Portalseite zu aktualisieren, da die Synchronisierung 5 bis 10 Minuten dauern kann.

1. Überprüfen Sie auf der Seite *Änderungen überprüfen*, ob der ausgewählte *Arbeitsbereich* der richtige ist, und überprüfen Sie die Aufzählungselemente unter dem Abschnitt *Was ist zu erwarten, wenn der Arbeitsbereich verbunden ist*. Wählen Sie die Schaltfläche **Verbinden** aus.

1. Sie sollten die Meldung *Es wir eine Verbindung mit dem Arbeitsbereich erstellt* und anschließend die Meldung *Arbeitsbereich erfolgreich verbunden* sehen.

1. Klicken Sie auf die Schaltfläche **Schließen**.

1. Auf dem **Startbildschirm** des **Defender XDR**-Portals sollten Sie oben ein Banner mit der Nachricht *Ihr vereinheitlichtes SIEM und XDR ist bereit* sehen. Wählen Sie die Schaltfläche **Suche starten** aus.

1. In der *erweiterten Suche* sollte die folgende Meldung angezeigt werden: „Erkunden Sie Ihre Inhalte von Sentinel“. Notieren Sie sich im linken Menübereich die *Microsoft Sentinel*-Tabellen, -Funktionen und -Abfragen unter den entsprechenden Registerkarten.

1. Erweitern Sie den linken Hauptmenübereich, wenn er reduziert ist, und erweitern Sie die neuen **Microsoft Sentinel**-Menüelemente. Die Auswahl von *Bedrohungsverwaltung*, *Inhaltsverwaltung* und *Konfiguration* sollte angezeigt werden.

 >**Hinweis:**  Die Synchronisierung zwischen Microsoft Sentinel und Microsoft Defender XDR kann einige Minuten dauern, sodass möglicherweise nicht alle installierten *Datenconnectors* angezeigt werden.

## Damit haben Sie das Lab beendet.
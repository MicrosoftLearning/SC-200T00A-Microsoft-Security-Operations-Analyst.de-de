---
lab:
  title: 'Übung 1: Erkunden von Anwendungsfällen in Microsoft Security Copilot'
  module: Learning Path 2 - Mitigate threats using Microsoft Security Copilot
---

# Lernpfad 2 – Lab 1 – Übung 1: Erkunden von Microsoft Security Copilot

## Labszenario

Die Organisation, für die Sie arbeiten, möchte die Effizienz und die Fähigkeiten ihrer Sicherheitsanalysten steigern und die Sicherheitsergebnisse verbessern. Zur Unterstützung dieses Ziels hat das Büro der CISO festgestellt, dass die Bereitstellung von Microsoft Security Copilot ein wichtiger Schritt zur Erreichung dieses Ziels ist. Als Sicherheitsadministratorin bzw. -administrator für Ihre Organisation sind Sie für die Einrichtung von Copilot zuständig.

In dieser Übung durchlaufen Sie die *erste Ausführungserfahrung* von Microsoft Security Copilot, um Copilot mit einer Sicherheitsrecheneinheit (SCU) auszustatten.

>**Hinweis:** Die Umgebung für diese Übung ist eine Simulation, die aus dem Produkt generiert wurde. Da es sich um eine eingeschränkte Simulation handelt, werden Links auf einer Seite möglicherweise nicht aktiviert, und textbasierte Eingaben, die außerhalb des angegebenen Skripts liegen, werden möglicherweise nicht unterstützt. Es wird eine Popup-Meldung mit dem Hinweis „Diese Funktion ist in der Simulation nicht verfügbar“ angezeigt. Wenn dies der Fall ist, wählen Sie OK und fahren Sie mit den Übungsschritten fort.  

![Popupfenster mit Fehlermeldung](../Media/simulation-pop-up-error.png)

### Geschätzte Zeit bis zum Abschluss dieses Labs: 45 Minuten

### Aufgabe 1: Bereitstellung von Microsoft Security Copilot

Für diese Übung sind Sie als Avery Howard angemeldet und verfügen über die Rolle eines globalen Administrators in Microsoft Entra. Sie werden sowohl im Azure-Portal als auch in Microsoft Security Copilot arbeiten.

Diese Übung dauert ca. **15** Minuten.

>**Hinweis:** Wenn in einer Lab-Anweisung das Öffnen eines Links zur simulierten Umgebung gefordert wird, wird im Allgemeinen empfohlen, den Link in einem neuen Browserfenster zu öffnen, damit Sie gleichzeitig die Anweisungen und die Übungsumgebung anzeigen können. Wählen Sie dazu die rechte Maustaste und dann die Option aus.

Bevor Benutzerinnen und Benutzer mit der Verwendung von Copilot beginnen können, müssen Admins Kapazität bereitstellen und zuordnen. Bereitstellen der Kapazität:

- Sie benötigen ein Azure-Abonnement.
- Sie müssen mindestens Azure-Besitzer oder Azure-Mitwirkender auf Ressourcengruppenebene sein.

In dieser Aufgabe werden Sie schrittweise durch den Prozess geführt, um sicherzustellen, dass Sie über die entsprechenden Rollenberechtigungen verfügen. Dies beginnt mit der Aktivierung der Zugriffsverwaltung für Azure-Ressourcen.

Nachdem Sie die Rolle "Benutzerzugriffsadministrator" in Azure zugewiesen haben, können Sie einem Benutzer den erforderlichen Zugriff für die Bereitstellung von SCUs für Copilot zuweisen.  Nur für diese Übung, die Ihnen die einzelnen Schritte zeigen soll, werden Sie sich selbst die erforderlichen Zugriffsrechte zuweisen.  Die folgenden Schritte führen Sie durch den Prozess.

1. Öffnen Sie die simulierte Umgebung, indem Sie den folgenden Link auswählen: **[Azure-Portal](https://app.highlights.guide/start/6d7270b9-7187-456a-ac16-97bc227d5c27?token=045faae1-1078-4eac-bf56-e12472eddaf9&link=1&azure-portal=true)**.

1. Sie beginnen, indem Sie die Access-Verwaltung für Azure-Ressourcen aktivieren. So greifen Sie auf diese Einstellung zu:
    1. Wählen Sie im Azure-Portal **Microsoft Entra ID** aus.
    1. Erweitern Sie im linken Navigationsbereich **Verwalten**.
    1. Scrollen Sie im linken Navigationsbereich nach unten und wählen Sie **Eigenschaften** aus.
    1. Aktivieren Sie den Umschalter für **Zugriffsverwaltung für Azure-Ressourcen**, und wählen Sie dann **Speichen** aus.

1. Nachdem Sie nun alle Ressourcen anzeigen und Zugriff auf beliebige Abonnement- oder Verwaltungsgruppen im Verzeichnis zuweisen können, weisen Sie sich selbst die Rolle „Besitzer“ für das Azure-Abonnement zu.
    1. Wählen Sie oben auf der Seite im blauen Banner **Microsoft Azure** aus, um zur Startseite des Azure-Portals zurückzukehren.
    1. Wählen Sie **Abonnements** und dann **Woodgrove - GTP Demos (Exernal/Sponsored)**.
    1. Wählen Sie **Zugriffssteuerung (IAM)** aus.
    1. Wählen Sie **Hinzufügen** und dann **Rollenzuweisung hinzufügen** aus.
    1. Wählen Sie auf der Registerkarte „Rolle“ **privilegierte Administratorrollen** aus.
    1. Wählen Sie **Besitzer**und dann **Weiter** aus.
    1. Wählen Sie **+ Mitglieder auswählen** aus.
    1. Avery Howard ist der erste Name in dieser Liste, wählen Sie rechts das **+** neben dem Namen aus.  Avery Howard ist jetzt unter ausgewählten Mitgliedern aufgeführt. Wählen Sie die Schaltfläche **Auswählen** und dann **Weiter** aus.
    1. Wählen Sie **Benutzer dürfen alle Rollen außer privilegierten Administratorrollen, Besitzer, UAA, RBAC (Empfohlen)** zuweisen.
    1. Wählen Sie **Überprüfen + Zuweisen** aus, und wählen Sie dann **Überprüfen + Zuweisen** ein letztes Mal aus.

Als Besitzer des Azure-Abonnements können Sie jetzt Kapazität innerhalb von Copilot bereitstellen.

#### Unteraufgabe 1: Bereitstellungskapazität

In dieser Aufgabe durchlaufen Sie die Schritte der Bereitstellung von Kapazität für Ihre Organisation. Es gibt zwei Optionen für die Bereitstellung der Kapazität:

- Bereitstellen der Kapazität innerhalb von Security Copilot (empfohlen)
- Bereitstellen der Kapazität über Azure

Für diese Übung stellen Sie die Kapazität über Security Copilot bereit. Wenn Sie Security Copilot zum ersten Mal öffnen, führt ein Assistent Sie durch die Schritte zum Einrichten der Kapazität für Ihre Organisation.

1. Öffnen Sie die simulierte Umgebung, indem Sie den folgenden Link auswählen: **[Microsoft Security Copilot](https://app.highlights.guide/start/6d7270b9-7187-456a-ac16-97bc227d5c27?token=045faae1-1078-4eac-bf56-e12472eddaf9&azure-portal=true)**.

1. Führen Sie die Schritte im Assistenten aus, und wählen Sie **Erste Schritte** aus.
1. Auf dieser Seite richten Sie Ihre Sicherheitskapazität ein. Für alle unten aufgeführten Felder können Sie das Informationssymbol auswählen, um weitere Informationen zu erhalten.
    1. Azure-Abonnement: Wählen Sie in der Dropdownliste **Woodgrove – GTP Demos (External/Sponsored)** aus.
    1. Ressourcengruppe: Wählen Sie in der Dropdownliste **RG-1** aus.
    1. Kapazitätsname: Geben Sie einen Kapazitätsnamen ein.
    1. Ort der Promptauswertung [Geo]: Wählen Sie in der Dropdownliste Ihre Region aus.
    1. „Sie können auswählen, ob Sie die Option auswählen möchten: "Wenn dieser Standort zu viel Datenverkehr hat, erlauben Sie Copilot, Aufforderungen überall in der Welt auszuwerten (empfohlen für optimale Leistung).
    1. Der Kapazitätsbereich wird basierend auf dem ausgewählten Standort festgelegt.
    1. Sicherheitscompute: Dieses Feld wird automatisch mit der Anzahl der mindestens erforderlichen SCU-Einheiten aufgefüllt, die 1 beträgt. Lassen Sie das Feld mit dem Wert **1** stehen.
    1. Wählen Sie das Kontrollkästchen **Ich bestätige, dass ich die Allgemeinen Geschäftsbedingungen gelesen und verstanden habe, und stimme ihnen zu**.
    1. Wählen Sie in der unteren rechten Ecke der Seite **Weiter** aus.

1. Der Assistent zeigt Informationen darüber an, wo Ihre Kundendaten gespeichert werden. Der angezeigte Bereich basiert auf der Region, die Sie im Feld „Promptauswertung“ausgewählt haben. Wählen Sie **Weiter**.

1. Sie können Optionen auswählen, um bei der Verbesserung von Copilot zu helfen. Sie können die Umschaltfläche basierend auf Ihren Einstellungen auswählen.  Wählen Sie **Weiter**.

1. Im Rahmen des anfänglichen Setups bietet Copilot standardmäßig Zugriff als Mitwirkender für alle Benutzer und schließt globale Administratoren und Sicherheitsadministratoren als Copilot-Besitzer ein. In Ihrer Produktionsumgebung können Sie ändern, wer Zugriff auf Copilot hat, nachdem Sie die Ersteinrichtung abgeschlossen haben. Wählen Sie **Weiter**.
1. Alles erledigt! Wählen Sie **Fertig stellen** aus.
1. Schließen Sie die Browserregisterkarte, da in der nächsten Übung ein separater Link zu einer lab-ähnlichen Umgebung verwendet wird.

### Aufgabe 2: Erkunden der eigenständigen Erfahrung von Microsoft Security Copilot

Der Sicherheitsadmin für Ihre Organisation hat Copilot bereitgestellt. Da Sie der ranghöchste Analytiker im Team sind, hat der Administrator Sie als Copilot-Besitzer hinzugefügt und Sie gebeten, sich mit der Lösung vertraut zu machen.

In dieser Übung erkunden Sie alle wichtigen Orientierungspunkte auf der Startseite der eigenständigen Anwendung von Microsoft Security Copilot.

Sie sind als Avery Howard angemeldet und haben die Copilot-Besitzerrolle. Sie werden in der eigenständigen Umgebung von Microsoft Security Copilot arbeiten.

Diese Übung dauert ca. **15** Minuten.

#### Unteraufgabe 1: Erkunden der Menüoptionen

In dieser Aufgabe beginnen Sie ihre Erkundung im Startmenü.

1. Öffnen Sie die simulierte Umgebung, indem Sie den folgenden Link auswählen: **[Microsoft Security Copilot](https://app.highlights.guide/start/7608581a-ee3a-4fe0-be03-309a58b78c60?token=045faae1-1078-4eac-bf56-e12472eddaf9&azure-portal=true)**.

1. Wählen Sie das **Menü**-Symbol ![Home-Menü-Symbol](../Media/home-menu-icon.png), das manchmal auch als Hamburger-Symbol bezeichnet wird.

1. Wählen Sie **Meine Sitzungen** aus, und notieren Sie sich die verfügbaren Optionen.
    1. Wählen Sie „Zuletzt verwendet“ aus, um die zuletzt verwendeten Sitzungen anzuzeigen.
    1. Wählen Sie „Filter“ aus, notieren Sie sich die verfügbaren Optionen, und schließen Sie dann den Filter.
    1. Wählen Sie das Startmenüsymbol aus, um das Startmenü zu öffnen.

1. Wählen Sie **Promptbook-Bibliothek** aus.
    1. Wählen Sie „Meine Promptbooks“ aus. Eine nachfolgende Aufgabe befasst sich näher mit Promptbooks.
    1. Wählen Sie Woodgrove aus.
    1. Wählen Sie Microsoft aus.
    1. Wählen Sie „Filter“ aus, um die verfügbaren Optionen anzuzeigen, und wählen Sie dann das X zum Schließen aus.
    1. Wählen Sie das Startmenüsymbol aus, um das Startmenü zu öffnen.

1. Wählen Sie **Besitzereinstellungen** aus. Diese Einstellungen stehen Ihnen als Copilot-Besitzerin oder -Besitzer zur Verfügung. Copilot-Mitwirkende haben keinen Zugriff auf diese Menüoptionen.
    1. Wählen Sie für Plugins für Security Copilot in der Dropdownliste die Option„Wer kann eigene benutzerdefinierte Plugins hinzufügen oder verwalten“ aus, um die verfügbaren Optionen anzuzeigen.
    1. Wählen Sie für alle Mitglieder der Organisation die Dropdown-Liste „Wer kann benutzerdefinierte Plugins hinzufügen und verwalten“, um die verfügbaren Optionen anzuzeigen. Beachten Sie, dass diese Option ausgegraut ist, wenn „Wer kann eigene benutzerdefinierte Plugins hinzufügen und verwalten“ auf „Nur Besitzerinnen und Besitzer“ festgelegt ist.
    1. Klicken Sie auf das Informationssymbol neben „Security Copilot Zugriff auf Daten Ihrer Microsoft 365-Dienste gewähren“.  Diese Einstellung muss aktiviert sein, wenn Sie das Microsoft Purview-Plugin verwenden möchten. Mit dieser Einstellung werden Sie in einer späteren Übung arbeiten.
    1. Wählen Sie das Dropdown-Menü für die Personen, die Dateien hochladen können, um die verfügbaren Optionen anzuzeigen.
    1. Wählen Sie das Startmenüsymbol aus, um das Startmenü zu öffnen.

1. Wählen Sie **Rollenzuweisung** aus.
    1. Wählen Sie „Mitglieder hinzufügen“ und dann „Schließen“ aus.
    1. Erweitern Sie Besitzer.
    1. Erweitern Sie Mitwirkende.
    1. Wählen Sie das Startmenüsymbol aus, um das Startmenü zu öffnen.

1. Wählen Sie **Nutzungsüberwachung**.
    1. Wählen Sie den Datumsfilter aus, um die verfügbaren Optionen anzuzeigen.
    1. Wählen Sie das Startmenüsymbol aus, um das Startmenü zu öffnen.

1. Wählen Sie **Einstellungen** aus.
    1. Wählen Sie „Einstellungen“ aus. Scrollen Sie nach unten, um verfügbare Optionen anzuzeigen.
    1. Wählen Sie „Daten und Datenschutz“ aus.
    1. Wählen Sie Hinweis.
    1. Wählen Sie das X aus, um das Einstellungsfenster zu schließen.

1. Wählen Sie unten links im Startmenü die Stelle aus, an der **Woodgrove** steht.
    1. Wenn Sie diese Option auswählen, werden Ihre Mandanten angezeigt. Dies wird als der Mandantenwechsel bezeichnet. In diesem Fall ist Woodgrove der einzige verfügbare Mandant.
    1. Wählen Sie **Start** aus, um zur Landing Page zurückzukehren.

#### Unteraufgabe 2: Erkunden des Zugangs zu aktuellen Sitzungen

In der Mitte der Landing Page befinden sich Karten, die Ihre letzten Sitzungen darstellen.

1. Die größte Karte ist Ihre letzte Sitzung. Wenn Sie den Titel einer beliebigen Sitzungskarte auswählen, gelangen Sie zu dieser Sitzung.
1. Wählen Sie **Alle Sitzungen anzeigen** aus, um zur Seite „Meine Sitzungen“ zu wechseln.
1. Wählen Sie **Microsoft Copilot für Security** neben dem Startmenüsymbol aus, um zur Landing Page zurückzukehren.

#### Unteraufgabe 3: Erkunden des Zugriffs auf Promptbooks

Der nächste Abschnitt der Copilot-Startseite dreht sich um Promptbooks. Auf der Startseite werden Kacheln für einige Microsoft Security-Promptbooks angezeigt. Hier erkunden Sie den Zugriff auf Promptbooks und die Promptbook-Bibliothek. In einer der nächsten Übung erkunden Sie das Erstellen und Ausführen eines Promptbook.

1. Rechts von der Stelle, an der „Erste Schritte mit diesen Promptbooks“ steht, befinden sich eine linke und eine rechte Pfeiltaste, mit denen Sie durch die Kacheln für die Microsoft Security-Promptbooks blättern können. Wählen Sie den **nach rechts zeigenden Pfeil** aus.

1. Jede Kachel zeigt den Titel des Promptbooks, eine kurze Beschreibung, die Anzahl der Prompts und ein Ausführungssymbol. Wählen Sie den Titel einer der Promptbook-Kacheln, um dieses Promptbook zu öffnen. Wählen Sie beispielsweise **Folgenabschätzung für Sicherheitsrisiken** aus.
    1. Das Fenster für das ausgewählte Promptbook enthält Informationen wie den Ersteller des Promptbooks, Tags, eine kurze Beschreibung, die für die Ausführung des Promptbooks erforderlichen Eingaben und eine Liste der Prompts.
    1. Notieren Sie sich die Informationen zum Promptbook und den verfügbaren Optionen. Für diese Simulation können Sie keine neue Sitzung starten, dies werden Sie in einer nachfolgenden Übung tun. 
    1. Wählen Sie **X** aus, um das Fenster zu schließen.

1. Wählen Sie **Promptbook-Bibliothek anzeigen** aus.
    1. Um Promptbooks anzuzeigen, die Sie besitzen, wählen Sie „Meine Promptbooks“ aus.
    1. Wählen Sie Woodgrove für eine Auflistung von Promptbooks im Besitz von Woodgrove, dem Namen einer fiktiven Organisation.
    1. Um in Microsoft integrierte oder von Microsoft entwickelte Promptbooks anzuzeigen, wählen Sie Microsoft aus.
    1. Wählen Sie das Filtersymbol aus. Hier können Sie basierend auf Tags filtern, die der Arbeitsmappe zugewiesen sind. Schließen Sie das Filterfenster, indem Sie auf der Registerkarte „Neuer Filter“ das X auswählen.
    1. Wählen Sie **Microsoft Copilot für Security** neben dem Startmenüsymbol aus, um zur Landing Page zurückzukehren.

#### Unteraufgabe 4: Erkunden des Symbols „Prompts und Quellen“ in der Prompt-Leiste

Die Prompt-Leiste befindet sich in der unteren Mitte der Seite. Die Prompt-Leiste enthält das Symbol „Prompts und Quellen“, das Sie in dieser Aufgabe erkunden. In nachfolgenden Übungen werden Sie Eingaben direkt in der Prompt-Leiste eingeben.

1. In der Prompt-Leiste können Sie das Symbol „Prompts“ auswählen, um einen integrierten Prompt oder ein Promptbook auszuwählen. Wählen Sie das Symbol für **Eingabeaufforderungen**![Eingabeaufforderungen](../Media/prompt-icon.png).
    1. Wählen Sie **Alle Promptbooks anzeigen** aus.
        1. Scrollen Sie, um alle verfügbaren Promptbooks anzuzeigen.
        1. Wählen Sie den **Rückwärtspfeil** neben der Suchleiste aus, um zurück zu gelangen.
    1. Wählen Sie **Alle Systemfunktionen anzeigen**. In der Liste werden alle verfügbaren Systemfunktionen angezeigt (diese Funktionen sind in der Tat Prompts, die Sie ausführen können). Viele Systemfunktionen sind bestimmten Plugins zugeordnet und werden als solche nur aufgeführt, wenn das entsprechende Plugin aktiviert ist.
        1. Scrollen Sie, um alle verfügbaren Promptbooks anzuzeigen.
        1. Wählen Sie den **Rückwärtspfeil** neben der Suchleiste aus, um zurück zu gelangen.

1. Wählen Sie das **Quellen-Symbol**![Quellen-Symbol](../Media/sources-icon.png).
    1. Das Quellen-Symbol öffnet das Fenster „Quellen verwalten“. Von hier aus können Sie auf Plugins oder Dateien zugreifen. Die Registerkarte **Plugins** ist standardmäßig ausgewählt.
        1. Wählen Sie aus, ob Sie alle Plugins anzeigen möchten, die aktiviert (an) oder deaktiviert (aus) sind.
        1. Erweitern/Klappen Sie die Liste der Microsoft-, Nicht-Microsoft- und benutzerdefinierten Plugins ein.
        1. Einige Plugins erfordern das Konfigurieren von Parametern. Wählen Sie das Symbol **Einrichten** für das Microsoft Sentinel-Plugin aus, um das Einstellungsfenster anzuzeigen. Wählen Sie **Abbrechen** aus, um das Fenster „Einstellungen“ zu schließen. In einer separaten Übung konfigurieren Sie das Plugin.
    1. Sie sollten sich weiterhin im Fenster Quellen verwalten befinden. Wählen Sie **Dateien** aus.
        1. Schauen Sie sich die Beschreibung an.
        1. Dateien können hochgeladen und von Copilot als Wissensdatenbank verwendet werden. In einer nachfolgenden Übung werden Sie mit Dateiuploads arbeiten.
        1. Wählen Sie **X** aus, um das Fenster „Quellen verwalten“ zu schließen.

#### Unteraufgabe 5: Erkunden der Hilfefunktion

In der unteren rechten Ecke des Fensters befindet sich das Hilfesymbol, in dem Sie auf einfache Weise auf die Dokumentation zugreifen und Lösungen für häufige Probleme finden können. Über das Hilfesymbol übermitteln Sie auch einen Supportfall an das Microsoft-Supportteam, wenn Sie über die entsprechenden Rollenberechtigungen verfügen.

1. Wählen Sie das **Hilfesymbol (?)** aus.
    1. Wählen Sie **Dokumentation** aus. Diese Auswahl öffnet eine neue Browser-Registerkarte mit der Microsoft Security Copilot-Dokumentation. Kehren Sie zur Microsoft Security Copilot-Browserregisterkarte zurück.
    1. Wählen Sie **Hilfe** aus.
        1. Jede Person mit Zugriff auf Security Copilot kann auf das Self-Help-Widget zugreifen, indem sie das Hilfesymbol und dann die Registerkarte „Hilfe“ auswählt. Hier finden Sie Lösungen für häufige Probleme, indem Sie etwas über das Problem eingeben.
        1. Benutzerinnen und Benutzer mit mindestens der Rolle Dienstsupportadmin oder Helpdesk-Admin können einen Supportfall an das Microsoft-Supportteam übermitteln. Wenn Sie über eine dieser Rollen verfügen, wird ein Headsetsymbol angezeigt. Schließen Sie die Seite „Support kontaktieren“.

### Aufgabe 3: Erkunden Sie die eingebettete Erfahrung von Microsoft Security Copilot

In dieser Übung untersuchen Sie einen Vorfall in Microsoft Defender XDR. Im Rahmen der Untersuchung erkunden Sie die wichtigsten Features von Microsoft Copilot in Microsoft Defender XDR, einschließlich Vorfallzusammenfassung, Gerätezusammenfassung, Skriptanalyse u. v. m. Außerdem pivotieren Sie Ihre Untersuchung auf der eigenständigen Oberfläche und verwenden die Pinwand, um Details Ihrer Untersuchung mit Ihren Kolleg:innen zu teilen.

Sie sind als Avery Howard angemeldet und haben die Copilot-Besitzerrolle. Sie arbeiten in Microsoft Defender mit der neuen einheitlichen Sicherheitsoperationsplattform, um auf die eingebetteten Copilot-Funktionen in Microsoft Defender XDR zuzugreifen. Am Ende der Übung wechseln Sie zur eigenständige Erfahrung von Microsoft Security Copilot.

Diese Übung dauert ca. **30** Minuten.

#### Unteraufgabe 1: Zusammenfassung der Vorfallzusammenfassung und geleitete Antworten

1. Öffnen Sie die simulierte Umgebung, indem Sie den folgenden Link auswählen: **[Microsoft Defender-Portal.](https://app.highlights.guide/start/be8a91c3-3979-4048-ad38-fd38deaf7117?token=045faae1-1078-4eac-bf56-e12472eddaf9&azure-portal=true)**

1. Über das Microsoft Defender-Portal:
    1. Erweitern Sie **Untersuchung und Antwort**.
    1. Erweitern Sie **Vorfälle und Warnungen**.
    1. Wählen Sie **Vorfälle** aus.

1. Wählen Sie den ersten Vorfall in der Liste aus, **Vorfall-ID: 185856** mit dem Namen „Ein von Menschen durchgeführter Ransomware-Angriff wurde von einem kompromittierten Objekt aus gestartet (Angriffsunterbrechung)“.

1. Dies ist ein komplexer Vorfall. Defender XDR bietet viele Informationen, aber bei 50 Warnungen kann es schwierig sein, die wichtigsten herauszufinden. Auf der rechten Seite der Vorfallseite generiert Copilot automatisch eine **Vorfallzusammenfassung**, die Ihnen hilft, die wichtigsten Informationen zu erfassen und Ihre Reaktion einzuleiten. Wählen Sie **Mehr anzeigen** aus.
    1. Die Zusammenfassung von Copilot beschreibt, wie sich dieser Vorfall weiterentwickelt hat, einschließlich anfänglicher Zugriff, Lateralbewegung, Sammlung, Zugriff auf Anmeldeinformationen und Exfiltration. Dies identifiziert bestimmte Geräte, zeigt an, dass das PsExec-Tool zum Starten ausführbarer Dateien verwendet wurde, und vieles mehr.
    1. All diese Informationen können Sie zur weiteren Untersuchung nutzen. Einige davon erkunden Sie in den nachfolgenden Aufgaben.

1. Scrollen Sie im Copilot-Bereich nach unten. Direkt unterhalb der Zusammenfassung finden Sie **geführte Reaktionen**. In den geführten Reaktionen werden Aktionen zur Unterstützung von Triage, Eindämmung, Untersuchung und Behebung empfohlen.
    1. Die erste Aufgabe in der Kategorie „Triage“ ist das Klassifizieren des Vorfalls. Wählen Sie **Klassifizieren** aus, um die Optionen anzuzeigen. Sehen Sie sich auch die geführten Reaktionen unter den anderen Kategorien an.
    1. Wählen Sie die Schaltfläche **Status** oberhalb von *Zusammenfassung* aus, und filtern Sie nach **Abgeschlossen**. Vier abgeschlossene Aktivitäten haben die Bezeichnung *Angriffsunterbrechung*. Mit automatischen Angriffsunterbrechungen sollen laufende Angriffe eingedämmt und die Auswirkungen auf die Ressourcen einer Organisation begrenzt werden. Außerdem sollen Sicherheitsteams damit mehr Zeit erhalten, den Angriff vollständig zu beheben.
1. Lassen Sie die Vorfallseite geöffnet, Sie verwenden sie in der nächsten Aufgabe.

#### Unteraufgabe 2: Erkunden der Geräte- und Identitätszusammenfassung

1. Scrollen Sie auf der Incidentseite auf der Registerkarte *Angriffsverlauf* durch die Warnungen nach unten, und wählen Sie die Warnung **Verdächtige RDP-Sitzung** aus.

1. Copilot erstellt automatisch eine **Warnungszusammenfassung**, die eine Fülle von Informationen für weitere Analysen enthält. In der Zusammenfassung werden beispielsweise verdächtige Aktivitäten, Datenerfassungsaktivitäten, Zugriff auf Anmeldeinformationen, Malware, Entdeckungsaktivitäten und vieles mehr identifiziert.

1. Die Seite enthält sehr viele Informationen. Um eine bessere Ansicht dieser Warnung zu erhalten, wählen Sie **Warnungsseite öffnen** aus. Es befindet sich im dritten Bereich der Warnungsseite, neben dem Vorfalldiagramm und unterhalb des Warnungstitels.

1. Oben auf der Seite befindet sich die Karte für das Gerät **parkcity-win10v**. Wählen Sie die Auslassungspunkte aus, und erkunden Sie die Optionen. Wählen Sie **Zusammenfassen** aus. Copilot generiert eine **Gerätezusammenfassung**. Beachten Sie, dass es viele Möglichkeiten gibt, auf Gerätezusammenfassungen zuzugreifen, dies ist lediglich eine einfache Methode. In der Zusammenfassung können Sie sehen, dass das Gerät eine VM ist, wem das Gerät gehört, welchen Compliancestatus es gemäß den Intune-Richtlinien hat u. v. m.

1. Neben der Gerätekarte finden Sie eine Karte mit der Besitzerin oder dem Besitzer des Geräts. Wählen Sie **PARKCITY\jonaw** aus. Die Anzeige im dritten Bereich auf der Seite wird von Details zur Warnung in Informationen zum Benutzer Jonathan Wolcott, einen Kundenbetreuer, geändert, dessen Schweregrad für Microsoft Entra ID-Risiko und Insider-Risiko als hoch eingestuft wird. Dies ist wenig überraschend nach dem, was Sie aus den Zusammenfassungen für Copilot-Vorfall und -Warnung erfahren haben. Wählen Sie die Auslassungspunkte und dann **Zusammenfassen** aus, um eine von Copilot erstellte Identitätszusammenfassung zu erhalten.

1. Lassen Sie die Warnungsseite geöffnet, da Sie sie in der nächsten Aufgabe verwenden werden.

#### Unteraufgabe 3: Erkunden der Analyse von Drehbüchern

1. Konzentrieren Sie sich nun auf den Warnungsverlauf. Klicken Sie auf das Symbol **Maximieren ![Maximieren-Symbol](../Media/maximize-icon.png)**, das sich im Hauptbereich der Warnung direkt unter der Karte mit der Bezeichnung „partycity\jonaw“ befindet, um eine bessere Ansicht der Prozess-Baumstruktur zu erhalten. Über die maximierte Ansicht erhalten Sie eine deutlichere Übersicht darüber, wie dieser Vorfall abgelaufen ist. Viele Elemente deuten darauf hin, dass mit „powershell.exe“ ein Skript ausgeführt wurde. Da der Benutzer Jonathan Wolcott ein Kundenbetreuer ist, kann davon ausgegangen werden, dass dieser Benutzer nicht sehr häufig PowerShell-Skripts ausführt.

1. Erweitern Sie die erste Instanz von **powershell.exe execute a script** (Skriptausführung mit powershell.exe) mit dem Zeitstempel „4:57:11 AM“. Copilot ist in der Lage, Skripts zu analysieren. Wählen Sie **Analysieren** aus.
    1. Copilot generiert eine Analyse des Skripts und weist darauf hin, dass es sich um einen Phishingversuch handeln könnte, oder dass es verwendet wurde, um einen webbasierten Exploit bereitzustellen.
    1. Wählen Sie **Code anzeigen** aus. Der Code enthält eine URL, die unschädlich gemacht wurde.

1. Es gibt noch einige andere Elemente, die angeben, dass ein Skript mit „powershell.exe“ ausgeführt wurde. Erweitern Sie das Element mit der Bezeichnung **powershell.exe -EncodedCommand...**. Das ursprüngliche Skript war Base64-codiert, aber Defender hat es für Sie decodiert. Wählen Sie zum Anzeigen der decodierten Version **Analysieren** aus. In der Analyse sind spezifische Aspekte des bei diesem Angriff verwendeten Skripts hervorgehoben.

1. In der Copilot-Skriptanalyse verfügen Sie über Schaltflächen für „Code anzeigen“ und „MITRE-Techniken anzeigen“.

1. Wählen Sie die Schaltfläche **MITRE-Techniken anzeigen** aus, und wählen Sie den Link mit der folgenden Bezeichnung aus: T1105: Eingehende Toolübertragung

1. Dadurch wird die *MITRE | ATT&CK*-Website geöffnet, auf der die Technik ausführlich beschrieben wird.

1. Schließen Sie die Seite mit dem Warnungsverlauf, indem Sie das **X** (links neben dem Copilot-Bereich) auswählen. Verwenden Sie nun die Brotkrümelnavigation, um zum Vorfall zurückzukehren. Wählen Sie **Human-operated ransomware attack was launched from a compromised asset (attack disruption)** (Ransomware-Angriff durch Personen von einer kompromittierten Ressource aus gestartet (Angriffsunterbrechung)) aus.

#### Unteraufgabe 4: Erkunden der Dateianalyse

1. Sie zeigen wieder die Vorfallseite an. In der Warnungszusammenfassung identifizierte Copilot die Datei „mimikatz.exe“, die der Malware „Mimikatz“ zugeordnet ist. Sie können die Dateianalysefunktion in Defender XDR verwenden, um mögliche weitere Erkenntnisse zu erhalten. Es gibt mehrere Möglichkeiten, auf Dateien zuzugreifen. Wählen Sie oben auf der Seite die Registerkarte **Beweis und Reaktion** aus.

1. Wählen Sie auf der linken Seite des Bildschirms **Dateien** aus.
1. Wählen Sie das erste Element aus der Liste mit der Entität namens **mimikatz.exe** aus.
1. Wählen Sie im daraufhin geöffneten Fenster **Dateiseite öffnen** aus.
1. Wählen Sie das Copilot-Symbol aus (wenn die Dateianalyse nicht automatisch geöffnet wird). Dann generiert Copilot eine Dateianalyse.
1. Überprüfen Sie die detaillierte Dateianalyse, die Copilot generiert.
1. Schließen Sie die Dateiseite, und verwenden Sie den Breadcrumb, um zum Incident zurückzukehren. Wählen Sie **Human-operated ransomware attack was launched from a compromised asset (attack disruption)** (Ransomware-Angriff durch Personen von einer kompromittierten Ressource aus gestartet (Angriffsunterbrechung)) aus.

#### Unteraufgabe 5: Pivotieren auf das eigenständige Erlebnis

Diese Aufgabe ist komplex und erfordert das Hinzuziehen von erfahrenen Analyst:innen. In dieser Aufgabe pivotieren Sie Ihre Untersuchung und führen das Defender-Promptbook für den Vorfall aus, damit die anderen Analyst:innen einen Ausgangspunkt für ihre Untersuchung haben. Sie heften Reaktionen an die Pinwand an und generieren einen Link zu dieser Untersuchung, den Sie mit erfahreneren Mitgliedern des Teams teilen können, damit diese Sie bei der Untersuchung unterstützen können.

1. Kehren Sie zur Vorfallseite zurück, indem Sie oben auf der Seite die Registerkarte **Angriffsverlauf** auswählen.

1. Wählen Sie die Auslassungspunkte neben der Vorfallzusammenfassung von Copilot und dann **In Security Copilot öffnen** aus.

1. Copilot wird auf der eigenständigen Oberfläche geöffnet und zeigt die Vorfallzusammenfassung an. Sie können auch noch weitere Prompts ausführen. In diesem Fall werden Sie das Promptbook für einen Vorfall ausführen. Wählen Sie das **Eingabeaufforderung-Symbol**![Eingabeaufforderung-Symbol](../Media/prompt-icon.png). 
    1. Wählen Sie **Alle Promptbooks anzeigen** aus.
    1. Wählen Sie **Microsoft 365 Defender: Vorfalluntersuchung** aus.
    1. Die Seite „Promptbook“ wird mit einer Aufforderung zur Eingabe der Defender-Vorfall-ID geöffnet. Geben Sie **185856** ein, und wählen Sie dann **Übermitteln** aus.
    1. Überprüfen Sie die bereitgestellten Informationen. Durch die Pivotierung auf die eigenständige Oberfläche und das Ausführen des Promptbook können Sie bei der Untersuchung Funktionen aus einer umfangreicheren Sicherheitslösung aufrufen, die nicht nur Defender XDR umfasst und auf den aktivierten Plug-Ins basiert.

1. Wählen Sie das **Kästchen-Symbol ![Kästchen-Symbol](../Media/box-icon.png)** neben dem Pin-Symbol, um alle Eingabeaufforderungen und die entsprechenden Antworten auszuwählen, und wählen Sie dann das **Pin-Symbol ![Pin-Symbol](../Media/pin-icon.png)**, um diese Antworten auf dem Board zu speichern.

1. Das Stecknadelboard wird automatisch geöffnet. Die Pinwand enthält Ihre gespeicherten Prompts und Reaktionen mit jeweils einer Zusammenfassung. Sie können die Pinnwand öffnen und schließen, indem Sie das **Pinnwand-Symbol ![Pinnwand-Symbol](../Media/pinboard-icon.png)** auswählen.

1. Wählen Sie oben auf der Seite **Teilen** aus, um Ihre Optionen anzuzeigen. Durch das Teilen des Vorfalls über einen Link oder eine E-Mail können Personen in Ihrer Organisation mit Copilot-Zugriff diese Sitzung anzeigen. Schließen Sie das Fenster, indem Sie das **X** auswählen.

#### Teilaufgabe 6: Erstellen und Ausführen einer KQL-Abfrage

Als Nächstes verwenden wir Copilot, um eine KQL-Abfrage (Kusto Query Language) zu erstellen, die mit der erweiterten Suche in Defender XDR verwendet werden kann.

1. Geben Sie in der eigenständigen Security Copilot-Instanz den folgenden Prompt in das Promptfeld ein: *Erstellen Sie basierend auf diesem Incident eine Abfrage, um proaktiv nach dieser Art von Schadsoftwareangriffen zu suchen. Verwenden Sie woodgrove-loganalyticsworkspace.*

1. Wählen Sie das Symbol „Prompt senden“ aus, um den Prompt auszuführen.
Copilot wählt „Natürliche Sprache in KQL“ für die erweiterte Suche aus.

1. Copilot generiert eine KQL-Abfrage und eine Antwort:

    1. Lesen Sie die Erläuterung der Kusto-Abfrage.

    1. Überprüfen Sie die Aufschlüsselung der Kusto-Abfrage. Diese ist sehr hilfreich, wenn Sie gerade erst mit KQL beginnen.

1. Kopieren Sie die von Copilot generierte KQL-Abfrage, und kehren Sie zum Defender XDR-Portal zurück.
***Es wird empfohlen, die Abfrage zuerst in Editor oder einen anderen Editor zu kopieren, um Formatierungsprobleme zu verringern.***

1. Defender XDR sollte weiterhin den Abschnitt „Untersuchungen und Antwort“ geöffnet haben. Wählen Sie **Hunting** aus, und dann im Navigationsmenü **Erweiterte Suche**.

1. Wählen Sie unter „Erweiterte Bedrohungssuche“ **Neue Abfrage +** aus, um ein neues Fenster zu öffnen, und fügen Sie die von Copilot generierte KQL-Abfrage in das Formular ein.
***Es wird empfohlen, die Abfrage zuerst in Editor oder einen anderen Editor zu kopieren, um Formatierungsprobleme zu verringern.***

1. Nachdem Sie die KQL-Abfrage ausgeführt haben, können Sie zu Copilot zurückkehren, um die Abfrage einzuschränken, oder das Copilot-Symbol auf der Seite „Abfrage für erweiterte Bedrohungssuche“ auswählen, um Suchabfragen zu optimieren.

1. Sie können nun die Browserregisterkarte schließen, um die Simulation zu beenden.

## Zusammenfassung und zusätzliche Ressourcen

In dieser Übung haben Sie die ersten Erfahrungen mit Microsoft Security Copilot erkundet, Kapazitäten bereitgestellt und die eigenständigen und eingebetteten Erfahrungen mit Copilot erkundet. Sie haben einen Vorfall in Microsoft Defender XDR untersucht, die Zusammenfassung des Vorfalls, die Gerätezusammenfassung, die Skriptanalyse und mehr erkundet. Sie haben Ihre Untersuchung auch auf das eigenständige Erlebnis gelenkt und die Pinnwand als Möglichkeit genutzt, Details Ihrer Untersuchung mit Ihren Kolleginnen und Kollegen zu teilen.

Um weitere Microsoft Security Copilot Anwendungssimulationen auszuführen, gehen Sie zu [Microsoft Security Copilot Anwendungssimulationen erkunden](/training/modules/security-copilot-exercises/).

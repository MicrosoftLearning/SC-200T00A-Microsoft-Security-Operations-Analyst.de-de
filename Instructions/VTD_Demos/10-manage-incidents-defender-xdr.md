# Modul 10: Verwalten von Incidents in Microsoft Defender XDR

## Verwalten von Incidents in Microsoft Defender XDR

Bei dieser Aufgabe untersuchen Sie die Funktionen des Incidentmanagements in Microsoft Defender XDR, einschließlich Incidentuntersuchung, Antwortaktionen und Zusammenarbeitsfeatures.

>**Wichtig:** Dieses Lab für die Ausführung in der Demoumgebung *Zava/Alpine Ski House* konzipiert. Für den Zugriff sind entsprechende Anmeldeinformationen erforderlich.

### Wichtige abgedeckte Bereiche

- Incidentdashboard
- Vorfalluntersuchung
- Beweis- und Antwortaktionen
- Incidentmanagementworkflows
- Zusammenarbeit und Dokumentation

1. Wenn Sie sich in Ihrem Browser noch nicht im Microsoft Defender-Portal befinden, wechseln Sie zum Microsoft Defender-Portal unter (<https://security.microsoft.com>), und melden Sie sich mit den Ihnen zugewiesenen Anmeldeinformationen an.

1. Erweitern Sie im linken Navigationsbereich den Abschnitt **Untersuchung und Antwort**, und wählen Sie **Incidents und Warnungen** > **Incidents** aus. Dadurch wird die Incidentwarteschlange mit allen aktiven Incidents in Ihrer gesamten Umgebung angezeigt.

1. Überprüfen Sie die Incidentwarteschlangenschnittstelle:
   - Filteroptionen (Status, Zugewiesen an, Tags usw.)
   - Incidentpriorität und Schweregradindikatoren
   - Dienstquellen (Defender for Endpunkt, Office 365 usw.)
   - Zeitstempel der letzten Aktivität

1. Wählen Sie einen Incident aus der Liste aus, um die Seite mit den Incidentdetails zu öffnen. Beachten Sie die Incidentübersicht, auf der Folgendes angezeigt wird:
   - Incidentzeitachse
   - Betroffene Ressourcen (Benutzer, Geräte, Postfächer)
   - Warnungsdetails und Korrelation
   - MITRE ATT&CK-Taktiken und -Techniken

## Incidentuntersuchungsprozess

1. Untersuchen Sie in den Incidentdetails die Registerkarte **Warnungen**, um alle Warnungen zu diesem Incident anzuzeigen.
   - Überprüfen der Warnungskorrelation und der automatischen Gruppierung
   - Untersuchen von Warnungsbeweisen und Artefakten
   - Beachten der Konfidenzstufen und Erkennungsquellen

1. Wählen Sie die Registerkarte **Geräte** aus, um alle betroffenen Endpunkte anzuzeigen:
   - Geräterisikostufen
   - Prioritätsscores der Untersuchung
   - Gerätezeitachse von Aktivitäten
   - Verfügbare Antwortaktionen

1. Navigieren Sie zur Registerkarte **Benutzer**, um betroffene Benutzerkonten zu überprüfen:
   - Benutzerrisikobewertungen
   - Anmeldeaktivitäten und Anomalien
   - Kontokompromittierungsindikatoren

1. Überprüfen Sie die Registerkarte **Postfächer** (falls zutreffend) auf E-Mail-bezogene Incidents:
   - E-Mail-Flow und Übermittlungsdetails
   - Anlagen- und URL-Analyse
   - Bewertung der Auswirkungen auf empfangende Personen

## Beweisanalyse und Antwortaktionen

1. Überprüfen Sie auf der Registerkarte **Beweise** alle erfassten Beweise:
   - Dateien und Dateihashes
   - IP-Adressen und Domänen
   - Registrierungsschlüssel und -prozesse
   - E-Mail-Nachrichten und URLs

1. Untersuchen Sie für die verfügbaren Aktionen jedes Beweiselement:
   - **Übermitteln zur Analyse**: Senden verdächtiger Dateien an Microsoft zur tiefen Analyse
   - **Hinzufügen zu Indikatoren**: Erstellen benutzerdefinierter Bedrohungsindikatoren
   - **Blockieren bzw. Zulassen**: Ergreifen sofortiger Schutzmaßnahmen

1. Veranschaulichen Sie Antwortaktionen, indem Sie ein Gerät auswählen und aus den verfügbaren Aktionen auswählen:
   - **Isolieren von Geräte**: Trennen des Geräts vom Netzwerk bei gleichzeitiger Aufrechterhaltung der Verbindung mit Defender
   - **Ausführen eines Antischadsoftwarescans**: Starten eines vollständigen oder schnellen Scans
   - **Erfassen des Untersuchungspakets**: Erfassen forensischer Daten
   - **Einschränken der App-Ausführung**: Einschränken der Anwendungsausführung auf dem Gerät

## Incidentmanagement und Workflow

1. Üben der Zuweisung und Verwaltung von Incidents:
   - **Zuweisen des Incidents**: Zuweisen zu einem bestimmten Analyse- oder Sicherheitsteam
   - **Ändern des Status**: Ändern von „Aktiv“ in „Behandelt“ oder weitere Status
   - **Hinzufügen von Tags**: Anwenden benutzerdefinierter zur Kategorisierung und Nachverfolgung
   - **Festlegen der Klassifizierung**: Kennzeichnen als „True Positive“, „False Positive“ oder „Informational“

1. Erkunden Sie den Workflow für das Incidentmanagement:
   - Überprüfen der Registerkarte **Kommentare** für die Zusammenarbeit von Fachkräften für die Analyse
   - Überprüfen der Registerkarte **Verlauf** für alle ausgeführten Aktionen
   - Verwenden der Registerkarte **Zusammenfassung** für Ausführungsberichte

1. Veranschaulichen Sie den Incidentbewertungsprozess:
   - **True Positive**: Bestätigte schädliche Aktivitäten, die eine Antwort erfordern
   - **Informational**: Erwartete Aktivität, die die Erkennung ausgelöst hat
   - **False Positive**: Harmlose Aktivität, die fälschlicherweise gekennzeichnet wurde

## Erweiterte Incidentfeatures

1. Untersuchen Sie die Ergebnisse für **Automatisierte Untersuchung** (falls verfügbar):
   - Überprüfen KI-gesteuerter Untersuchungsergebnissen
   - Überprüfen empfohlener Aktionen
   - Genehmigen oder Ablehnen der automatisierten Wartung

1. Navigieren Sie zur Integration der **Bedrohungsanalyse**:
   - Verknüpfen von Incidents mit bekannten Bedrohungskampagnen
   - Überprüfen des Threat Intelligence-Kontexts
   - Zugreifen auf Analyseberichte und IoCs

1. Veranschaulichen Sie die Auswirkung auf **benutzerdefinierte Erkennungsregeln**:
   - Veranschaulichen des Beitrags benutzerdefinierter Regeln zur Erstellung von Incidents
   - Überprüfen der Effektivität von Regeln und Optimierungsmöglichkeiten
   - Optionen zum Ändern und Testen von Zugriffsregeln

## Berichterstellung und Metriken für Incidents

1. Zugreifen auf Incidentberichterstellungsfunktionen:
   - Navigieren Sie zu **Berichten** > **Sicherheitsbericht**.
   - Überprüfen von Incidenttrends und -statistiken
   - Generieren von Ausführungszusammenfassungsberichten

1. Untersuchen Sie Incidentmetriken und KPIs:
   - Durchschnittliche Erkennungsdauer (Mean Time To Detection, MTTD)
   - Durchschnittliche Antwortdauer (Mean Time To Response, MTTR)
   - Incidentvolumentrends
   - Raten für falsch positives Ergebnisse

1. Einrichten von Incidentbenachrichtigungen:
   - Konfigurieren von E-Mail-Warnungen für Incidents mit hoher Priorität
   - Einrichten der Teams-Integration für die kollaborative Antwort
   - Erstellen benutzerdefinierter Benachrichtigungsregeln basierend auf Incidentkriterien

## Best Practices für das Incidentmanagement

1. **Priorisierungsstrategie**:
   - Konzentrieren auf Incidents mit hohem Schweregrad vorab
   - Berücksichtigen der Geschäftswirkungen und der Kritikalität von Ressourcen
   - Verwenden der Risikobewertung zur Anleitung der Untersuchungsbemühungen

1. **Dokumentationsstandards**:
   - Verwalten detaillierter Untersuchungshinweise
   - Dokumentieren aller ergriffenen Antwortaktionen
   - Erfassen gesammelter Erfahrungen und Verbesserungsmöglichkeiten

1. **Teamzusammenarbeit**:
   - Verwenden konsistenter Tagging- und Klassifizierungsschemas
   - Einrichten klarer Eskalationsverfahren
   - Implementieren regulärer Prozesse zur Überprüfung von Incidents

1. **Fortlaufende Verbesserung:**
   - Regelmäßige Überprüfung der Raten für falsch positives Ergebnisse
   - Optimieren von Erkennungsregeln basierend auf Incidentergebnissen
   - Aktualisieren von Playbooks zur Antwort auf Incidents basierend auf Ergebnissen

## Integration mit Microsoft Sentinel

1. Wenn Microsoft Sentinel verbunden ist, demonstrieren Sie das einheitliche Incidentmanagement:
   - Plattformübergreifende Incidentkorrelation
   - Einheitliche Untersuchungsoberfläche
   - Geteilte Threat Intelligence und Indikatoren

1. Zeigen Sie Sentinel-spezifische Incidentfeatures an:
   - Untersuchungsdiagrammvisualisierung
   - Benutzerdefinierte Playbookautomatisierung
   - Erweiterte Bedrohungssuche in verschiedenen Umgebungen

## Damit haben Sie die Demo beendet

---

**Zusätzliche Ressourcen:**

- [Microsoft Defender XDR Incident Management](https://docs.microsoft.com/microsoft-365/security/defender/manage-incidents)
- [Playbooks für die Reaktion auf Vorfälle](https://docs.microsoft.com/security/compass/incident-response-playbooks)
- [MITRE ATT&CK-Framework](https://attack.mitre.org/)

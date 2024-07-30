---
lab:
  title: Übung 7 – Erstellen von Erkennungen
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Lernpfad 7 – Lab 1 – Übung 7 –  Erstellen von Erkennungen

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex7.png)

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Sie arbeiten mit Log Analytics KQL-Abfragen und erstellen daraus benutzerdefinierte Analyseregeln, um Bedrohungen und anomales Verhalten in Ihrer Umgebung zu erkennen.

Mit diesen Analyseregeln werden bestimmte Ereignisse oder Ereignisgruppen in Ihrer Umgebung gesucht, beim Erreichen bestimmter Ereignisschwellenwerte oder -bedingungen Warnungen ausgegeben, und Incidents generiert, die Ihr SOC selektieren und untersuchen kann. Außerdem wird mit automatisierten Nachverfolgungs- und Korrekturprozessen auf Bedrohungen reagiert.


>**Hinweis:** Eine **[interaktive Labsimulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Create%20detections)** ist verfügbar, mit der Sie dieses Lab in Ihrem eigenen Tempo durcharbeiten können. Möglicherweise liegen geringfügige Unterschiede zwischen der interaktiven Simulation und dem gehosteten Lab vor, aber die dargestellten Kernkonzepte und Ideen sind identisch. 


### Aufgabe 1: Erkennen von Persistenzangriffen

>**Wichtig:** Die nächsten Schritte werden in einer anderen VM ausgeführt als der, in der Sie zuvor gearbeitet haben. Suchen Sie nach den Namensverweisen der virtuellen Maschine.

In dieser Aufgabe erstellen Sie eine Erkennung für den ersten Angriff der vorherigen Übung.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Edge-Browser zum Azure-Portal unter https://portal.azure.com.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren zuvor erstellten Microsoft Sentinel-Arbeitsbereich aus.

1. Wählen Sie **Protokolle** im Abschnitt *Allgemein* aus.

1. **Führen** Sie die folgende KQL-Anweisung erneut aus, um die Tabellen aufzurufen, in denen wir diese Daten haben:

    ```KQL
    search "temp\\startup.bat"
    ```

    >**Hinweis:** Es kann bis zu 5 Minuten dauern, bis ein Ergebnis bei dem Ereignis erscheint. Warten Sie, bis es erscheint. Wenn es nicht erscheint, vergewissern Sie sich, dass Sie den WINServer neu gestartet haben, wie in der vorherigen Übung beschrieben, und dass Sie die Aufgabe Nr. 3 des Lernpfads 6 Lab, Übung 2, abgeschlossen haben.

1. Es sieht so aus, als wären die Daten in der Tabelle *SecurityEvent* bereits normalisiert und wir können sie leicht abfragen. Erweitern Sie die Zeile, um alle mit dem Datensatz verknüpften Spalten zu sehen.

1. Anhand der Ergebnisse wissen wir nun, dass der Bedrohungsakteur reg.exe verwendet, um Schlüssel zum Registrierungsschlüssel hinzuzufügen, und dass sich das Programm in C:\temp befindet. **Führen** Sie die folgende Anweisung aus, um den Operator *suchen* in unserer Abfrage durch den Operator *wo* zu ersetzen:

    ```KQL
    SecurityEvent 
    | where Activity startswith "4688" 
    | where Process == "reg.exe" 
    | where CommandLine startswith "REG" 
    ```

1. Es ist wichtig, dass Sie den Security Operations Analyst unterstützen, indem Sie so viel Kontext wie möglich über die Warnung zur Verfügung stellen. Dazu gehört auch die Projektion von Entitäten zur Verwendung im Untersuchungsdiagramm. **Führen** Sie die folgende Abfrage aus:

    ```KQL
    SecurityEvent 
    | where Activity startswith "4688" 
    | where Process == "reg.exe" 
    | where CommandLine startswith "REG" 
    | extend timestamp = TimeGenerated, HostCustomEntity = Computer, AccountCustomEntity = SubjectUserName
    ```

1. Nun, da Sie eine gute Erkennungsregel haben, wählen Sie im Fenster „Protokolle“ die Option **+ Neue Warnungsregel** aus der Befehlsleiste und wählen Sie dann **Microsoft Sentinel Warnung erstellen** aus. Dadurch wird eine neue geplante Regel erstellt. **Hinweis:** Möglicherweise müssen Sie auf die Schaltfläche Auslassungspunkte (...) in der Befehlsleiste klicken.

1. Dadurch wird der „Assistent für Analyseregeln“ gestartet. Für die Registerkarte *Allgemein* geben Sie ein:

    |Einstellung|Wert|
    |---|---|
    |Name|Startup RegKey|
    |Beschreibung|Startup RegKey in c:\temp|
    |Taktik|Persistenz|
    |Severity|Hoch|

1. Klicken Sie auf die Schaltfläche **Weiter: Regellogik festlegen >**.

1. Auf der Registerkarte *Regellogik festlegen* sollte die *Regelabfrage* bereits mit Ihrer KQL-Abfrage ausgefüllt sein.

1. Konfigurieren Sie die Entitäten unter *Warnungserweiterung - Entitätszuordnung* mit Hilfe der Parameter in der folgenden Tabelle.

    |Entity|Bezeichner|Datenfeld|
    |:----|:----|:----|
    |Konto|FullName|AccountCustomEntity|
    |Host|Hostname|HostCustomEntity|

1. Legen Sie für *Abfrageplanung* Folgendes fest:

    |Einstellung|Wert|
    |---|---|
    |Ausführen der Abfrage alle:|5 Minuten|
    |Datensuche für letzte:|1 Days|

    >**Hinweis:** Wir erzeugen absichtlich viele Incidents für die gleichen Daten. Dies ermöglicht es dem Lab, diese Warnungen zu verwenden.

1. Belassen Sie die anderen Optionen bei den Standardwerten. Klicken Sie auf die Schaltfläche **Weiter: Incident-Einstellungen**.

1. Belassen Sie auf der Registerkarte *Incident-Einstellungen* die Standardwerte und klicken Sie auf die Schaltfläche **Weiter: Automatisierte Antwort >**.

1. Wählen Sie auf der Registerkarte *Automatisierte Antwort* unter *Automatisierungsregeln* die Option **Neue hinzufügen** aus.

1. Verwenden Sie die Einstellungen in der Tabelle, um die Automatisierungsregel zu konfigurieren.

    |Einstellung|Wert|
    |:----|:----|
    |Name der Automatisierungsregel|Startup RegKey|
    |Trigger|Bei Erstellung des Vorfalls|
    |Aktionen |Playbook ausführen|
    |Playbook |PostMessageTeams-OnIncident|

    >**Hinweis:** Sie haben dem Playbook bereits Berechtigungen zugewiesen, sodass es verfügbar ist.

1. Wählen Sie **Übernehmen** aus.

1. Wählen Sie unten **Weiter: Überprüfen + erstellen >**.
  
1. Wählen Sie auf der Registerkarte *Überprüfen und erstellen* die Schaltfläche **Speichern** aus, um die neue Regel „Geplante Analyse“ zu erstellen.

### Aufgabe 2: Erkennung von Angriffen zur Rechteerweiterung

In dieser Aufgabe erstellen Sie eine Erkennung für den zweiten Angriff aus der vorherigen Übung.

1. Wählen Sie im Microsoft Sentinel-Portal **Protokolle** im Bereich Allgemein, wenn Sie von dieser Seite aus navigiert haben.

1. **Führen** Sie die folgende KQL-Anweisung aus, um alle Einträge zu identifizieren, die sich auf Administrator*innen beziehen:

    ```KQL
    search "administrators" 
    | summarize count() by $table
    ```

1. Das Ergebnis könnte Ereignisse aus verschiedenen Tabellen anzeigen, aber in unserem Fall wollen wir die Tabelle „SecurityEvent“ untersuchen. Die EventID und das Ereignis, nach dem wir suchen, ist „4732 – Ein Mitglied wurde zu einer sicherheitsaktivierten lokalen Gruppe hinzugefügt". Damit können wir das Hinzufügen eines Mitglieds zu einer privilegierten Gruppe identifizieren. **Führen** Sie die folgende KQL-Abfrage aus, um dies zu bestätigen:

    ```KQL
    SecurityEvent 
    | where EventID == 4732
    | where TargetAccount == "Builtin\\Administrators"
    ```

1. Erweitern Sie die Zeile, um alle mit dem Datensatz verknüpften Spalten zu sehen. Der Benutzername des Kontos, das als Administrator hinzugefügt wurde, wird nicht angezeigt. Das Problem ist, dass wir die Sicherheits-ID (SID) anstelle des Benutzernamens gespeichert haben. **Führen** Sie den folgenden KQL aus, um die SID mit dem Benutzernamen abzugleichen, der der Gruppe „Administratoren“ hinzugefügt wurde:

    ```KQL
    SecurityEvent 
    | where EventID == 4732
    | where TargetAccount == "Builtin\\Administrators"
    | extend Acct = MemberSid, MachId = SourceComputerId  
    | join kind=leftouter (
        SecurityEvent 
        | summarize count() by TargetSid, SourceComputerId, TargetUserName 
        | project Acct1 = TargetSid, MachId1 = SourceComputerId, UserName1 = TargetUserName) on $left.MachId == $right.MachId1, $left.Acct == $right.Acct1
    ```

   ![Screenshot](../Media/SC200_sysmon_attack3.png)

1. Erweitern Sie die Zeile, um die resultierenden Spalten anzuzeigen. In der letzten sehen wir den Namen des/der hinzugefügten Benutzer*in in der Spalte *Benutzername1* oder *Projekt* in der KQL-Abfrage. Es ist wichtig, dass Sie den Security Operations Analyst unterstützen, indem Sie so viel Kontext wie möglich über die Warnung zur Verfügung stellen. Dazu gehört auch die Projektion von Entitäten zur Verwendung im Untersuchungsdiagramm. **Führen** Sie die folgende Abfrage aus:

    ```KQL
    SecurityEvent 
    | where EventID == 4732
    | where TargetAccount == "Builtin\\Administrators"
    | extend Acct = MemberSid, MachId = SourceComputerId  
    | join kind=leftouter (
        SecurityEvent 
        | summarize count() by TargetSid, SourceComputerId, TargetUserName 
        | project Acct1 = TargetSid, MachId1 = SourceComputerId, UserName1 = TargetUserName) on $left.MachId == $right.MachId1, $left.Acct == $right.Acct1
    | extend timestamp = TimeGenerated, HostCustomEntity = Computer, AccountCustomEntity = UserName1
    ```

1. Nun, da Sie eine gute Erkennungsregel haben, wählen Sie im Fenster „Protokolle“ **+ Neue Warnungsregel** in der Befehlsleiste und dann **Microsoft Sentinel-Warnung erstellen** aus. **Hinweis:** Möglicherweise müssen Sie auf die Schaltfläche Auslassungspunkte (...) in der Befehlsleiste klicken.

1. Dadurch wird der „Assistent für Analyseregeln“ gestartet. Für die Registerkarte *Allgemein* geben Sie ein:

    |Einstellung|Wert|
    |---|---|
    |Name|**SecurityEvent Benutzer*in zu „Lokale Administratoren“ hinzufügen**|
    |Beschreibung|**Benutzer*in zur Gruppe „Lokale Administratoren“ hinzugefügt**|
    |Taktik|**Rechteausweitung**|
    |Severity|**Hoch**|

1. Klicken Sie auf die Schaltfläche **Weiter: Regellogik festlegen >**.

1. Auf der Registerkarte *Regellogik festlegen* sollte die *Regelabfrage* bereits mit der KQL-Abfrage sowie den Entitäten unter *Warnungserweiterung – Entitätszuordnung* aufgefüllt werden.

    |Entity|Bezeichner|Datenfeld|
    |:----|:----|:----|
    |Konto|FullName|AccountCustomEntity|
    |Host|Hostname|HostCustomEntity|

1. Wenn **Hostname** für die *Host*-Entität nicht ausgewählt ist, wählen Sie ihn aus der Dropdownliste aus, und verwenden Sie die Parameter in der vorherigen Tabelle, um die Felder aufzufüllen.

1. Legen Sie für *Abfrageplanung* Folgendes fest:

    |Einstellung|Wert|
    |---|---|
    |Ausführen der Abfrage alle:|5 Minuten|
    |Datensuche für letzte:|1 Days|

    >**Hinweis:** Wir erzeugen absichtlich viele Incidents für die gleichen Daten. Dies ermöglicht es dem Lab, diese Warnungen zu verwenden.

1. Belassen Sie die anderen Optionen bei den Standardwerten. Klicken Sie auf die Schaltfläche **Weiter: Incident-Einstellungen**.

1. Belassen Sie auf der Registerkarte *Incident-Einstellungen* die Standardwerte und klicken Sie auf die Schaltfläche **Weiter: Automatisierte Antwort >**.

1. Wählen Sie auf der Registerkarte *Automatisierte Antwort* unter *Automatisierungsregeln* die Option **Neue hinzufügen** aus.

1. Verwenden Sie die Einstellungen in der Tabelle, um die Automatisierungsregel zu konfigurieren.

   |Einstellung|Wert|
   |:----|:----|
   |Name der Automatisierungsregel|SecurityEvent Benutzer*in zu „Lokale Administratoren“ hinzufügen|
   |Trigger|Bei Erstellung des Vorfalls|
   |Aktionen |Playbook ausführen|
   |Playbook |PostMessageTeams-OnIncident|

   >**Hinweis:** Sie haben dem Playbook bereits Berechtigungen zugewiesen, sodass es verfügbar ist.

1. Wählen Sie **Übernehmen** aus.

1. Wählen Sie die Schaltfläche **Weiter: Überprüfen und erstellen >** aus.
  
1. Klicken Sie auf der Registerkarte *Überprüfen und Erstellen* auf die Schaltfläche **Erstellen**, um die neue Regel für die geplante Analyse zu erstellen.

## Fahren Sie mit Übung 8 fort

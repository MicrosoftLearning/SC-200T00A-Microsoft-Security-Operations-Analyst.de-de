---
lab:
  title: 'Übung 5: Vorbereiten simulierter Angriffe'
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Lernpfad 9 – Lab 1 – Übung 5 – Vorbereiten der Durchführung simulierter Angriffe

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod9_L1_Ex5.png)

>**Wichtig:** Die Lab-Übungen für Lernpfad Nr. 9 befinden sich in einer *eigenständigen* Umgebung. Wenn Sie das Lab vor dem Abschluss verlassen, müssen Sie die Konfigurationen erneut ausführen.

### Geschätzte Zeit bis zum Abschluss dieses Labs: 30 Minuten

### Aufgabe 1: Herstellen einer Verbindung mit einem lokalen Server

In dieser Aufgabe verbinden Sie einen lokalen Server mit Ihrem Azure-Abonnement. Azure Arc wurde auf diesem Server vorinstalliert. Der Server wird in den nächsten Übungen verwendet, um simulierte Angriffe auszuführen, die Sie später für die Erkennung und Untersuchung in Microsoft Sentinel verwenden werden.

>**Wichtig:** Die nächsten Schritte werden auf einem anderen Computer ausgeführt als dem, auf dem Sie zuvor gearbeitet haben. Suchen Sie auf der Registerkarte „Referenzen“ nach dem Namen der virtuellen Maschine.

1. Melden Sie sich bei dem virtuellen Computer **WINServer** als Administrator*in mit dem Kennwort: **Passw0rd!** an, falls erforderlich.  

Wie oben beschrieben, wurde Azure Arc auf dem **WINServer-Computer** vorinstalliert. Sie verbinden diesen Computer jetzt mit Ihrem Azure-Abonnement.

1. Wählen Sie auf dem *WINServer-Computer* das Symbol *Suchen* aus, und geben Sie **cmd** ein.

1. Klicken Sie in den Suchergebnissen mit der rechten Maustaste auf *Eingabeaufforderung*, und wählen Sie **Als Administrator ausführen** aus.

1. Geben Sie im Eingabeaufforderungsfenster den folgenden Befehl ein: *Drücken Sie nicht auf die EINGABETASTE*:

    ```cmd
    azcmagent connect -g "defender-RG" -l "EastUS" -s "Subscription ID string"
    ```

1. Ersetzen Sie die **Abonnement-ID-Zeichenfolge** durch die *Abonnement-ID*, die von Ihrem Lab-Hoster (*Registerkarte „Ressourcen“) bereitgestellt wird. Achten Sie darauf, die Anführungszeichen beizubehalten.

1. Geben Sie **Eingeben** ein, um den Befehl auszuführen (dies kann einige Minuten dauern).

    >**Hinweis**: Wenn das Browser-Auswahlfenster *Wie möchten Sie das öffnen?* angezeigt wird, wählen Sie **Microsoft Edge** aus.

1. Geben Sie im Dialogfeld *Anmelden* Ihre **Mandanten-E-Mail** und Ihr **Mandantenkennwort** ein, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Anmelden** aus. Warten Sie auf die Meldung *Authentifizierung abgeschlossen*, schließen Sie die Browserregisterkarte, und kehren Sie zum Fenster *Eingabeaufforderung* zurück.

1. Lassen Sie nach Abschluss der Ausführung der Befehle das Fenster *Eingabeaufforderung* geöffnet, und geben Sie den folgenden Befehl ein, um zu bestätigen, dass die Verbindung erfolgreich hergestellt wurde:

    ```cmd
    azcmagent show
    ```

1. Überprüfen Sie in der Befehlsausgabe, ob der *Agentstatus* verbunden** ist**.

## Aufgabe 2: Verbinden Sie einen Windows-Computer, der nicht von Azure stammt

In dieser Aufgabe fügen Sie einen mit Azure Arc verbundenen lokalen Computer zu Microsoft Sentinel hinzu.  

>**Hinweis:** Microsoft Sentinel wurde in Ihrem Azure-Abonnement mit dem Namen **defenderWorkspace** vorab bereitgestellt, und die erforderlichen *Content Hub*-Lösungen wurden installiert.

1. Melden Sie sich beim virtuellen **WIN1-Computer** als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Microsoft Edge-Browser zu der Azure-Portal unter <https://portal.azure.com>.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie den Microsoft Sentinel **defenderWorkspace** aus.

1. Scrollen Sie im linken Navigationsmenü von Microsoft Sentinel nach unten zum Abschnitt *Konfiguration* und wählen Sie **Datenconnectors** aus.

1. Suchen Sie in den *Datenconnectors* nach der Lösung **Windows-Sicherheitsereignisse über AMA** und wählen Sie diese aus der Liste aus.

1. Wählen Sie im Detailbereich *Windows-Sicherheitsereignisse über AMA* die Option **Connectorseite öffnen** aus.

    >**Hinweis:** Die Lösung *Windows-Sicherheitsereignisse* installiert sowohl den *Windows-Sicherheitsereignisse über AMA* als auch den Datenconnector *Sicherheitsereignisse über Legacy-Agent*. Plus 2 Arbeitsmappen, 20 Analyseregeln und 43 Hunting-abfragen.

1. Wählen Sie im Abschnitt *Konfiguration* unter der Registerkarte *Anweisungen* die Option **Regel zur Datensammlung erstellen** aus.

1. Geben Sie **AZWINDCR** als Regelnamen ein und wählen Sie **Weiter: Ressourcen** aus.

1. Erweitern Sie Ihr *Abonnement* unter *Bereich* auf der Registerkarte *Ressourcen*.

    >**Hinweis:** Sie können die gesamte Hierarchie *Bereich* erweitern, indem Sie die Option „>“ vor der Spalte *Bereich* auswählen.

1. Erweitern Sie die Ressourcengruppe **defender-RG** und wählen Sie dann **WINServer** aus.

1. Wählen Sie **Weiter: Sammeln** aus und lassen Sie die Option *Alle Sicherheitsereignisse* ausgewählt.

1. Klicken Sie auf **Weiter: Überprüfen + erstellen**.

1. Wählen Sie **Erstellen** aus, nachdem *Validierung erfolgreich* angezeigt wurde.

### Aufgabe 3: Verstehen der Angriffe

>**Wichtig: In dieser Übung werden keine Aktionen ausgeführt.**  Diese Anweisungen sind nur eine Erklärung der Angriffe, die Sie in der nächsten Übung durchführen werden. Bitte lesen Sie diese Seite aufmerksam durch.

Angriffsmuster basieren auf einem Open-Source-Projekt: <https://github.com/redcanaryco/atomic-red-team>

#### Angriff 1 – Persistenz mit dem Registrierungsschlüssel hinzufügen

Angreifer fügen ein Programm im Registrierungsschlüssel ausführen hinzu. Dadurch wird Persistenz erreicht, indem das Programm bei jeder Anmeldung des Benutzers ausgeführt wird.

```
REG ADD "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /V "SOC Test" /t REG_SZ /F /D "C:\temp\startup.bat"
```

#### Angriff 2 – Benutzerberechtigungen hinzufügen und erhöhen

Der Angreifer fügt neue Benutzer hinzu und erhebt den neuen Benutzer in die Gruppe der Administratoren. Dadurch kann sich der Angreifer mit einem anderen privilegierten Konto anmelden.

```
net user theusernametoadd /add
net user theusernametoadd ThePassword1!
net localgroup administrators theusernametoadd /add
```

#### Angriff 3 – DNS/C2

Angreifer sendet eine große Anzahl von DNS-Abfragen an einen Befehls- und Steuerelementserver (C2). Die Absicht ist, eine schwellwertbasierte Erkennung der Anzahl von DNS-Anfragen entweder von einem einzelnen Quellsystem oder zu einer einzelnen Zieldomäne auszulösen.

```
param(
    [string]$Domain = "microsoft.com",
    [string]$Subdomain = "subdomain",
    [string]$Sub2domain = "sub2domain",
    [string]$Sub3domain = "sub3domain",
    [string]$QueryType = "TXT",
        [int]$C2Interval = 8,
        [int]$C2Jitter = 20,
        [int]$RunTime = 240
)
$RunStart = Get-Date
$RunEnd = $RunStart.addminutes($RunTime)
$x2 = 1
$x3 = 1 
Do {
    $TimeNow = Get-Date
    Resolve-DnsName -type $QueryType $Subdomain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
    if ($x2 -eq 3 )
    {
        Resolve-DnsName -type $QueryType $Sub2domain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
        $x2 = 1
    }
    else
    {
        $x2 = $x2 + 1
    }
    if ($x3 -eq 7 )
    {
        Resolve-DnsName -type $QueryType $Sub3domain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
        $x3 = 1
    }
    else
    {
        $x3 = $x3 + 1
    }
    $Jitter = ((Get-Random -Minimum -$C2Jitter -Maximum $C2Jitter) / 100 + 1) +$C2Interval
    Start-Sleep -Seconds $Jitter
}
Until ($TimeNow -ge $RunEnd)
```

### Aufgabe 4: Verstehen der Erkennungsmodellierung

Der in dieser Übung verwendete Angriffserkennungs-Konfigurationszyklus repräsentiert alle Datenquellen, auch wenn Sie sich nur auf zwei bestimmte Datenquellen konzentrieren.

Um eine Erkennung zu erstellen, beginnen Sie mit der Erstellung einer KQL-Anweisung. Da Sie einen Host angreifen, verfügen Sie über repräsentative Daten, um mit der Erstellung der KQL-Anweisung zu beginnen.

Nachdem Sie die KQL-Anweisung erstellt haben, erstellen Sie die Analyseregel.

Sobald die Regel ausgelöst wird und Warnungen und Incidents generiert, prüfen Sie, ob Sie Felder zur Verfügung stellen, die den Security Operations Analysts bei ihren Untersuchungen helfen.

Nehmen Sie anschließend weitere Änderungen an der Analyseregel vor.

>**Hinweis:** Einige Warnungen werden nur zu Labzwecken in einem kürzeren Zeitintervall ausgelöst.

## Fahren Sie mit Übung 6 fort

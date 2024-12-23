---
lab:
  title: Übung 6 – Durchführen von Angriffen
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Lernpfad 9 – Lab 1 – Übung 6: Durchführen von Angriffen

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex6.png)

Sie simulieren die Angriffe, die Sie später für die Erkennung und Untersuchung in Microsoft Sentinel verwenden werden.

>**Wichtig:** Die Lab-Übungen für Lernpfad Nr. 9 befinden sich in einer *eigenständigen* Umgebung. Wenn Sie das Lab vor dem Abschluss verlassen, müssen Sie die Konfigurationen erneut ausführen.

### Geschätzte Zeit bis zum Abschluss dieses Labs: 30 Minuten

### Aufgabe 1: Persistenzangriff mit dem Registrierungsschlüssel hinzufügen

>**Wichtig:** Die nächsten Schritte werden in einer anderen VM ausgeführt als der, in der Sie zuvor gearbeitet haben. Suchen Sie nach den Namensverweisen der virtuellen Maschine.

In dieser Aufgabe werden Sie Angriffe auf den Host ausführen, der mit Azure Arc verbunden ist und auf dem der Azure Monitor-Agent konfiguriert ist.

1. Melden Sie sich beim virtuellen Computer WINServer als Administrator mit dem Kennwort **Pa55w.rd**an.  

    >**Wichtig:** Die Funktion *SPEICHERN* im Lab kann dazu führen, dass die Verbindung zwischen WINServer und Azure Arc unterbrochen wird. Ein Neustart behebt das Problem.  

1. Wählen Sie in Windows **Start**. Dann **Herunterfahren**, dann **Neustart**.

1. Folgen Sie den Anweisungen, um sich erneut bei WINServer anzumelden.

1. Geben Sie bei der Suche in der Taskleiste *Befehl* ein. Die Eingabeaufforderung wird in den Suchergebnissen angezeigt. Klicken Sie mit der rechten Maustaste auf „Eingabeaufforderung“, und wählen Sie **Als Administrator ausführen** aus. Wählen Sie **Ja** in dem erscheinenden Fenster der Benutzerkontensteuerung, um die Ausführung der Anwendung zu erlauben.

1. Erstellen Sie in der Eingabeaufforderung einen Temp-Ordner im Stammverzeichnis. Vergessen Sie nicht, nach der letzten Zeile die Eingabetaste zu drücken:

    ```CommandPrompt
    cd \
    mkdir temp
    cd temp
    ```

1. Kopieren Sie diesen Befehl und führen Sie ihn aus, um die Persistenz des Programms zu simulieren:

    ```CommandPrompt
    REG ADD "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /V "SOC Test" /t REG_SZ /F /D "C:\temp\startup.bat"
    ```


### Aufgabe 2: Rechteerweiterungsangriff mit Benutzer hinzufügen

1. Kopieren Sie diesen Befehl, und führen Sie ihn aus, um die Erstellung eines Administratorkontos zu simulieren. Vergessen Sie nicht, nach der letzten Zeile die Eingabetaste zu drücken:

    ```CommandPrompt
    net user theusernametoadd /add
    net user theusernametoadd ThePassword1!
    net localgroup administrators theusernametoadd /add
    ```


### Aufgabe 3: Befehls- und Kontrollangriff mit DNS

1. Kopieren Sie diesen Befehl und führen Sie ihn aus, um ein Skript zu erstellen, das eine DNS-Anfrage an einen C2-Server simuliert:

    ```CommandPrompt
    notepad c2.ps1
    ```

1. Wählen Sie **Ja**, um eine neue Datei zu erstellen, und kopieren Sie das folgende PowerShell-Skript in *c2.ps1*.

    >**Hinweis:** Beim Einfügen in die Datei der virtuellen Maschine wird möglicherweise nicht die gesamte Länge des Skripts angezeigt. Stellen Sie sicher, dass das Skript den Anweisungen in der Datei *c2.ps1* entspricht.

    ```PowerShell
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

1. Wählen Sie im Menü Notepad **Datei** und dann **Speichern**. 

1. Kehren Sie zum Eingabeaufforderungsfenster zurück, geben Sie den folgenden Befehl ein und drücken Sie die Eingabetaste. 

    >**Hinweis:** Es werden DNS-Auflösungsfehler angezeigt. Dies entspricht dem erwarteten Verhalten.

    ```CommandPrompt
    Start PowerShell.exe -file c2.ps1
    ```

>**Wichtig:** Schließen Sie diese Fenster nicht. Lassen Sie dieses PowerShell-Skript im Hintergrund laufen. Der Befehl muss einige Stunden lang Protokolleinträge generieren. Sie können mit der nächsten Aufgabe und den nächsten Übungen fortfahren, während dieses Skript läuft. Die durch diese Aufgabe erzeugten Daten werden später im Lab zur Bedrohungssuche verwendet. Bei diesem Vorgang werden keine großen Datenmengen erzeugt oder verarbeitet.


## Fahren Sie mit Übung 7 fort

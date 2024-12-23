---
lab:
  title: 'Übung 1: Erkunden der Microsoft Purview-Audit-Protokolle'
  module: Learning Path 3 - Mitigate threats using Microsoft Purview
---

# Lernpfad 3 – Lab 1 – Übung 1: Erkunden der Microsoft Purview-Audit-Protokolle

## Labszenario

Sie sind eine Sicherheitsanalystin bzw. ein Sicherheitsanalyst und arbeiten in einem Unternehmen, das Microsoft Defender XDR und Microsoft Purview implementiert. Sie unterstützen die Kollegen im IT-Compliance-Team bei der Konfiguration von Purview Audit (Standard) und Audit (Premium). Ihr Ziel ist es sicherzustellen, dass alle Zugriffe auf Patientendaten und Änderungen an diesen Daten in unserem Netzwerk von Gesundheitseinrichtungen genau protokolliert werden, um die Vorschriften zum Schutz von Integritätsdaten zu erfüllen.

### Geschätzte Zeit bis zum Abschluss dieses Labs: 15 Minuten

### Aufgabe 1: Aktivieren von Purview Überwachungsprotokollen

In dieser Aufgabe weisen Sie im Microsoft 365 Security-Portal voreingestellte Sicherheitsrichtlinien für Exchange Online Protection (EOP) und Microsoft Defender for Office 365 zu.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Starten Sie den Microsoft Edge-Browser.

1. Wechseln Sie im Microsoft Edge-Browser zum Microsoft Defender XDR-Portal unter <https://security.microsoft.com>.

1. Kopieren Sie im Dialogfeld **Anmelden**das von Ihrem Labhostinganbieter bereitgestellte Mandanten-E-Mail-Konto für den Administrator, und fügen Sie es ein, und wählen Sie dann **Weiter** aus.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das von Ihrem Labhostinganbieter bereitgestellte Mandantenkennwort für den Administrator, und fügen Sie es ein, und wählen Sie dann **Anmelden** aus.

1. Erweitern Sie im Navigationsmenü den Eintrag *Operationelle Technologie* und wählen Sie **Weitere Ressourcen** aus.

1. Wählen Sie im Bereich **Weitere Ressourcen** die Schaltfläche **Öffnen** auf der Kachel *Microsoft Purview-Portal* aus.

1. Wenn das Microsoft Purview-Portal geöffnet wird, erscheint eine Meldung über das *neue Microsoft Purview-Portal* auf dem Bildschirm. Wählen Sie die Option, um den Bedingungen für die Veröffentlichung des Datenflusses und der Datenschutzerklärung zuzustimmen, und wählen Sie dann **Jetzt testen** aus.

    ![Screenshot des Bildschirms „Willkommen im neuen Microsoft Purview-Portal“.](../Media/welcome-purview-portal.png)

1. Wählen Sie **Lösungen** in der linken Seitenleiste und wählen Sie dann **Überwachen**.

1. Wählen Sie auf der Seite **Suchen** die blaue Leiste **Aufzeichnung der Benutzer- und Administratoraktivitäten starten** aus, um die Audit-Protokollierung zu aktivieren.

    ![Der Screenshot zeigt die Schaltfläche „Aufzeichnung von Benutzenden- und Admin-Aktivitäten starten".](../Media/enable-audit-button.png)

1. Sobald Sie diese Option wählen, sollte der blaue Balken von dieser Seite verschwinden.

    >**Hinweis:** Es kann bis zu 60 Minuten dauern, bis die Aufzeichnung der Aktivitäten beginnt.

## Damit haben Sie das Lab beendet

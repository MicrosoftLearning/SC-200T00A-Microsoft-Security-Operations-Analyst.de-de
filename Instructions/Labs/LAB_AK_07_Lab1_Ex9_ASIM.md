---
lab:
  title: Übung 9 – Erstellen von ASIM-Parsern
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Lernpfad 7 – Lab 1 – Übung 9 – Bereitstellen von ASIM-Parsern

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex9.png)

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Sie müssen ASIM-Parser für ein bestimmtes Windows-Registrierungsereignis modellieren. Diese vereinfachten Parser werden zu einem späteren Zeitpunkt auf der Grundlage der [Referenz zum Schema für die Registrierungsereignisnormalisierung des erweiterten Sicherheitsinformationsmodells (Advanced Security Information Model, ASIM)](https://docs.microsoft.com/en-us/azure/sentinel/registry-event-normalization-schema) fertiggestellt.

>**Hinweis:** Eine **[interaktive Labsimulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Create%20Advanced%20Security%20Information%20Model%20Parsers)** ist verfügbar, mit der Sie dieses Lab in Ihrem eigenen Tempo durcharbeiten können. Möglicherweise liegen geringfügige Unterschiede zwischen der interaktiven Simulation und dem gehosteten Lab vor, aber die dargestellten Kernkonzepte und Ideen sind identisch. 

### Aufgabe 1: Bereitstellen der ASIM-Parser für das Registrierungsschema

In dieser Aufgabe stellen Sie die Registrierungsschema-Parser aus dem Microsoft Sentinel GitHub-Repository bereit.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Edge-Browser zum Azure-Portal unter https://portal.azure.com.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren zuvor erstellten Microsoft Sentinel-Arbeitsbereich aus.

1. Öffnen Sie im Edge-Browser eine neue Registerkarte (STRG+T), und navigieren Sie zur Seite „Microsoft Sentinel GitHub ASIM“<https://github.com/Azure/Azure-Sentinel/tree/master/ASIM>.

    <!--- 1. On the right pane, select the **Onboard community content** link. This will open a new tab in the Edge Browser for Microsoft Sentinel GitHub content. **Hint:** You might need to scroll right to see the link. Alternatively, follow this link instead: [Microsoft Sentinel on GitHub](https://github.com/Azure/Azure-Sentinel). --->

    >**Hinweis:** Im Ordner **ASIM** können Sie Vorlagen bereitstellen, die alle ASIM-Parser enthalten, aber wir konzentrieren uns nur auf das Registrierungsschema.

1. Scrollen Sie nach unten und wählen Sie neben der **Registrierung** die Schaltfläche **Bereitstellen in Azure**.

1. Für *Ressourcengruppe* wählen Sie **RG-Defender**, wo sich Ihr Sentinel-Arbeitsbereich befindet.

1. Geben Sie für *Arbeitsbereich* den Namen Ihres Sentinel-Arbeitsbereichs ein, zum Beispiel *EuniquenameDefender*.

1. Lassen Sie die anderen Voreinstellungen unverändert und wählen Sie **Prüfen + Erstellen**.

1. Wählen Sie **Erstellen** aus, um die Vorlage bereitzustellen. Beachten Sie die Namen der verschiedenen Ressourcen.

1. Kehren Sie nach Abschluss der Bereitstellung zur Registerkarte *Microsoft Sentinel* zurück.

1. Wählen Sie im Menü auf der linken Seite unter **Allgemein** die Option *Protokolle* aus.

1. Öffnen Sie das Blatt *Schema und Filter*, indem Sie bei Bedarf **>>** auswählen.

1. Wählen Sie die Registerkarte **Funktionen** (neben den Registerkarten Tabellen und Abfragen). **Hinweis:** Möglicherweise müssen Sie auf das Ellipsensymbol **(...)** klicken, um die Registerkarte auszuwählen.

1. Erweitern Sie **Arbeitsbereichsfunktionen**. Beachten Sie, dass die Namen den soeben bereitgestellten Vorlagen entsprechen.

1. Zeigen Sie mit der Maus auf den *Arbeitsbereichsparser* **vimRegistryEventMicrosoftSecurityEvents**, und wählen Sie dann im Popupfenster die Option **Funktionscode laden** aus.

1. Überprüfen Sie den KQL, der die Ereignis-ID 4657 analysiert, um Ihre Analyse der Daten im Microsoft Sentinel-Arbeitsbereich zu vereinfachen.

1. Abfrage **ausführen**. Sie sollten keine Ergebnisse oder Fehler erhalten, da dies nur zu Validierungszwecken dient.

1. Gehen Sie zurück zum Blatt *Schema und Filter* und bewegen Sie nun den Mauszeiger auf **inRegistry***Vereinheitlichender Parser* und wählen Sie **Funktionscode laden**.

1. Beachten Sie, dass der vereinheitlichende Parser den *Union*- Operator verwendet, um alle Parser im Arbeitsbereich auf einmal auszuführen. Wenn Sie einen Parser für das Registrierungsschema entwickeln, müssen Sie ihn hier hinzufügen.

1. Abfrage **ausführen**. Sie sollten weder ein Ergebnis noch einen Fehler erhalten, da dies nur der Überprüfung dient.

1. Dieser vereinheitlichende Parser kann nun für Analyseregeln oder Huntingabfragen verwendet werden.

## Fahren Sie mit Übung 10 fort
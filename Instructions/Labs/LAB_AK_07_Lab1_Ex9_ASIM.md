---
lab:
  title: Übung 9 – Erstellen von ASIM-Parsern
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Lernpfad 7 – Lab 1 – Übung 9 – Bereitstellen von ASIM-Parsern

## Labszenario

![Übersicht über Lab.](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex9.png)

Sie sind als Security Operations Analyst für ein Unternehmen tätig, das Microsoft Sentinel implementiert hat. Sie müssen ASIM-Parser für ein bestimmtes Windows-Registrierungsereignis modellieren. Diese Parser werden zu einem späteren Zeitpunkt in Anlehnung an das [Normalisierungsschema des Advanced Security Information Model (ASIM) Registry Event](https://docs.microsoft.com/en-us/azure/sentinel/registry-event-normalization-schema) fertiggestellt.

>**Hinweis:** Eine **[interaktive Labsimulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Create%20Advanced%20Security%20Information%20Model%20Parsers)** ist verfügbar, mit der Sie dieses Lab in Ihrem eigenen Tempo durcharbeiten können. Möglicherweise liegen geringfügige Unterschiede zwischen der interaktiven Simulation und dem gehosteten Lab vor, aber die dargestellten Kernkonzepte und Ideen sind identisch. 

### Aufgabe 1: Bereitstellen der ASIM-Parser für das Registrierungsschema

In dieser Aufgabe sehen Sie sich die Registrierungsschema-Parser an, die in der Bereitstellung von Microsoft Sentinel enthalten sind.

1. Melden Sie sich beim virtuellen Computer WIN1 als Administrator mit dem Kennwort **Pa55w.rd** an.  

1. Navigieren Sie im Microsoft Edge-Browser zu der Azure-Portal unter https://portal.azure.com.

1. Kopieren Sie im Dialogfeld **Anmelden** die **E-Mail vom Mandanten**, die Sie von Ihrem Labhostinganbieter erhalten haben, und wählen Sie **Weiter**.

1. Kopieren Sie im Dialogfeld **Kennwort eingeben** das **Kennwort des Mandanten**, das Sie von Ihrem Labhostinganbieter erhalten haben, und fügen Sie es ein. Wählen Sie dann **Anmelden**.

1. Geben Sie in der Suchleiste des Azure-Portals *Sentinel* ein, und wählen Sie dann ** Microsoft Sentinel** aus.

1. Wählen Sie Ihren zuvor erstellten Microsoft Sentinel-Arbeitsbereich aus.

<!--- 1. In the Edge browser, open a new tab (Ctrl+T) and navigate to the Microsoft Sentinel GitHub ASIM page <https://github.com/Azure/Azure-Sentinel/tree/master/ASIM>.

 1. On the right pane, select the **Onboard community content** link. This will open a new tab in the Edge Browser for Microsoft Sentinel GitHub content. **Hint:** You might need to scroll right to see the link. Alternatively, follow this link instead: [Microsoft Sentinel on GitHub](https://github.com/Azure/Azure-Sentinel).

    >**Note:** In the **ASIM** folder you can deploy templates that contain all ASIM parsers, but we will only focus on the Registry Schema.

1. Scroll down and next to **Registry Event**, select the **Deploy to Azure** button.

1. For *Resource Group*, select **RG-Defender** where your Sentinel workspace resides.

1. For *Workspace*, type your Sentinel workspace name, like *uniquenameDefender*.

1. Leave the other default values and select **Review + create**.

1. Select **Create** to deploy the template. Notice the Names of the different resources. 

1. After the deployment completes return to the *Microsoft Sentinel* tab. --->

1. Wählen Sie im Menü auf der linken Seite unter **Allgemein** die Option *Protokolle* aus.

1. Öffnen Sie das Blatt *Schema und Filter*, indem Sie bei Bedarf **>>** auswählen.

1. Wählen Sie die Registerkarte **Funktionen** (neben den Registerkarten Tabellen und Abfragen). **Hinweis:** Möglicherweise müssen Sie auf das Ellipsensymbol **(...)** klicken, um die Registerkarte auszuwählen.

1. Geben Sie in der *Suchleiste* **Registrierung** ein, und scrollen Sie durch die ASIM-Parser-Funktionen, bis Sie den Eintrag *_Im_RegistryEvent_MicrosoftWindowsEventxxx* für Microsoft Windows unter der Überschrift *Microsoft Sentinel* sehen.

    >**Hinweis:** Wir verwenden das xxx im Funktionsnamen des ASIM-Parsers, um Versionsänderungen zu berücksichtigen. Zum Zeitpunkt der Aktualisierung dieses Labs war der Name der Funktion _Im_RegistryEvent_MicrosoftWindowsEvent*V02*.

1. Bewegen Sie den Mauszeiger über die ASIM-Funktion **_Im_RegistryEvent_MicrosoftWindowsEventxxx** und wählen Sie dann im Popup-Fenster die Option **Funktionscode laden** aus.

1. Überprüfen Sie den KQL, der die Ereignis-ID 4657 analysiert, um Ihre Analyse der Daten im Microsoft Sentinel-Arbeitsbereich zu vereinfachen.

    >**Hinweis:** Wenn Sie STRG+F in das Codefenster eingeben, wird die *Suchfunktion* angezeigt und die Suche nach *EventID: 4657* viel einfacher.

1. Öffnen Sie in *Protokollen* eine Registerkarte „Neue Abfrage“.

1. Gehen Sie zurück zur *Schema- und Filterleiste* und bewegen Sie nun den Mauszeiger auf **_Im_RegistryEvent_MicrosoftWindowsEventxxx** *Registrierungsereignis ASIM-Filterparser für Microsoft Windows-Ereignisse und Sicherheitsereignisse* und wählen Sie dann **Im Editor verwenden** aus.

1. **Führen Sie** die ASIM-Funktionsabfrage aus. Wenn Sie die vorherigen Labübungen abgeschlossen haben, sollten Ergebnisse und keine Fehlermeldungen angezeigt werden.

## Fahren Sie mit Übung 10 fort
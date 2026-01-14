---
title: Erstellen von Zusammenführungsrichtlinien
seo-title: Create merge policies | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Erstellen von Zusammenführungsrichtlinien
description: In dieser Lektion erstellen Sie Zusammenführungsrichtlinien, um zu bestimmen, wie Daten in Profile zusammengeführt werden.
role: Data Architect, Data Engineer
feature: Profiles
jira: KT-4348
audience: data architect
doc-type: tutorial
activity: implement
thumbnail: 4348-create-merge-policies.jpg
exl-id: ec862bb2-7aa2-4157-94eb-f5af3a94295f
source-git-commit: 10d36ee194c8da937f667c1ba438681959c5fc68
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 0%

---

# Erstellen von Zusammenführungsrichtlinien

<!--20 min-->

In dieser Lektion erstellen Sie Zusammenführungsrichtlinien, um zu priorisieren, wie mehrere Datenquellen in Profilen zusammengeführt werden.

Mit Adobe Experience Platform können Sie Daten aus verschiedenen Quellen zusammenführen und kombinieren, damit Sie sich einen kompletten Überblick über jeden einzelnen Kunden verschaffen können. Beim Zusammenführen dieser Daten bestimmen Zusammenführungsrichtlinien, wie Daten priorisiert werden und welche Daten kombiniert werden, um diese einheitliche Ansicht zu schaffen.

In dieser Lektion halten wir uns an die Benutzeroberfläche. Es gibt jedoch auch API-Optionen zum Erstellen von Zusammenführungsrichtlinien.

**Datenarchitekten** müssen Zusammenführungsrichtlinien außerhalb dieses Tutorials erstellen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über Zusammenführungsrichtlinien zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/330433?learn=on&enablevpops)

## Erforderliche Berechtigungen

In der Lektion [Berechtigungen konfigurieren](configure-permissions.md) richten Sie alle Zugriffssteuerungen ein, die zum Abschließen dieser Lektion erforderlich sind.

<!--* Permission items **[!UICONTROL Profile Management]** > **[!UICONTROL View Merge Policies]** and **[!UICONTROL Manage Merge Policies]**
* Permission item **[!UICONTROL Profile Management]** > **[!UICONTROL View Profiles]** and **[!UICONTROL Manage Profiles]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
-->

## Über Zusammenführungsrichtlinien und Vereinigungsschema

Vielleicht erinnern Sie sich daran, dass wir in der Lektion zur Batch-Aufnahme zwei Datensätze mit leicht unterschiedlichen Informationen für denselben Kunden hochgeladen haben. In den [!DNL Loyalty] Daten war der Vorname des Kunden `Daniel` und er lebte in `New York City`, aber in den CRM-Daten war der Vorname des Kunden `Danny` und er lebte in `Portland`. Kundendaten ändern sich im Laufe der Zeit. Vielleicht ist er von `Portland` nach `New York City` gezogen. Auch andere Dinge ändern sich, z. B. Telefonnummern und E-Mail-Adressen. Mithilfe von Zusammenführungsrichtlinien können Sie entscheiden, wie diese Arten von Konflikten gehandhabt werden sollen, wenn zwei Datenquellen unterschiedliche Informationen für denselben Benutzer bereitstellen.

Warum also hat `Danny` als Vorname gewonnen? Sehen wir uns das einmal an:

1. Wählen Sie in der Platform-Benutzeroberfläche **[!UICONTROL Profile]** im linken Navigationsbereich aus
1. Navigieren Sie zur Registerkarte **[!UICONTROL Zusammenführungsrichtlinien]**
1. Die standardmäßige Zusammenführungsrichtlinie ist nach Zeitstempel geordnet. Da Sie die CRM-Daten nach den Treueprogramm-Daten hochgeladen haben, hat sich `Danny` als Vorname im Profil durchgesetzt:

![Bildschirm „Zusammenführungsrichtlinie“](assets/mergepolicies-default.png)

Wenn mehrere Schemata für ein Profil aktiviert sind, wird [!UICONTROL Vereinigungsschema] automatisch für alle profilaktivierten Datensatzschemata erstellt, die eine Basisklasse gemeinsam nutzen. Sie können die [!UICONTROL Vereinigungsschemata] anzeigen, indem Sie zur Registerkarte **[!UICONTROL Vereinigungsschema]** wechseln.

![Bildschirm „Zusammenführungsrichtlinie“](assets/mergepolicies-unionSchema.png)

Beachten Sie, dass es kein Vereinigungsschema für die ExperienceEvent-Klasse gibt. ExperienceEvent-Daten landen zwar weiterhin im Profil, da sie zeitreihenbasiert sind, jedes Ereignis jedoch einen Zeitstempel und eine ID enthält und Kollisionen kein Problem darstellen.

Was nun, wenn Ihnen diese standardmäßige Zusammenführungsrichtlinie nicht gefällt? Was, wenn Luma entscheidet, dass ihr Treuesystem im Konfliktfall die Quelle der Wahrheit sein sollte? Dazu werden wir eine Zusammenführungsrichtlinie erstellen.

## Erstellen einer Zusammenführungsrichtlinie in der Benutzeroberfläche

1. Klicken Sie im Bildschirm „Zusammenführungsrichtlinien **[!UICONTROL oben rechts auf die Schaltfläche]** Zusammenführungsrichtlinie erstellen“
1. Geben Sie als **[!UICONTROL Name]** `Loyalty Prioritized`
1. Wählen Sie als **[!UICONTROL Schema]** die Option **[!UICONTROL XDM-Profil]** aus (beachten Sie, dass Ihre benutzerdefinierte Klasse, da es sich um Datensatzdaten handelt, auch für Zusammenführungsrichtlinien verfügbar ist)
1. Wählen **[!UICONTROL für „ID]** Zuordnung“ die Option **[!UICONTROL Privates Diagramm]**
1. Wählen **[!UICONTROL für]** Attributzusammenführung“ die Option **[!UICONTROL Datensatzpriorität]**
1. Ziehen Sie `Luma Loyalty Dataset` und `Luma CRM Dataset` per Drag-and-Drop in das **[!UICONTROL Datensatz]**-Bedienfeld.
1. Stellen Sie sicher, dass `Luma Loyalty Dataset` oben ist, indem Sie es per Drag-and-Drop über die `Luma CRM Dataset` ziehen.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
   <!--do i need to explain Private Graph? Is that GA?-->
   ![Zusammenführungsrichtlinie](assets/mergepolicies-newPolicy.png)

## Validieren der Zusammenführungsrichtlinie

Mal sehen, ob die Zusammenführungsrichtlinie das tut, was wir erwarten würden:

1. Navigieren Sie zur Registerkarte **[!UICONTROL Durchsuchen]**.
1. Ändern Sie die **[!UICONTROL Zusammenführungsrichtlinie]** in Ihre neue `Loyalty Prioritized`
1. Verwenden Sie als **[!UICONTROL Identity-Namespace]** Ihren `Luma CRM Id`
1. Verwenden Sie als **[!UICONTROL Identitätswert]** den `b642b4217b34b1e8d3bd915fc65c4452`
1. Klicken Sie auf **[!UICONTROL Schaltfläche Profil anzeigen]**
1. `Daniel` ist zurück!

![Anzeigen eines Profils mit einer anderen Zusammenführungsrichtlinie](assets/mergepolicies-lookupProfileWithMergePolicy.png)

## Erstellen einer Zusammenführungsrichtlinie mit eingeschränkten Datensätzen

Beim Erstellen von Zusammenführungsrichtlinien mit Datensatzpriorität werden nur die Datensätze derselben Basisklasse, die Sie im rechten Bereich einbeziehen, in das Profil aufgenommen. Richten wir eine andere Zusammenführungsrichtlinie ein

1. Klicken Sie im Bildschirm „Zusammenführungsrichtlinien **[!UICONTROL oben rechts auf die Schaltfläche]** Zusammenführungsrichtlinie erstellen“
1. Geben Sie als **[!UICONTROL Name]** `Loyalty Only`
1. Wählen Sie als **[!UICONTROL Schema]** die Option **[!UICONTROL XDM-Profil]**
1. Wählen **[!UICONTROL für „ID]** Zuordnung“ **[!UICONTROL Keine]**
1. Wählen **[!UICONTROL für]** Attributzusammenführung“ die Option **[!UICONTROL Datensatzpriorität]**
1. Ziehen Sie das `Luma Loyalty Dataset` per Drag-and-Drop in das Bedienfeld **[!UICONTROL Ausgewählter]**&quot;.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

![Zusammenführungsrichtlinie nur für Treue](assets/mergepolicies-loyaltyOnly.png)

## Validieren der Zusammenführungsrichtlinie

Sehen wir uns nun an, was diese Zusammenführungsrichtlinie bewirkt:

1. Navigieren Sie zur Registerkarte **[!UICONTROL Durchsuchen]**.
1. Ändern Sie die **[!UICONTROL Zusammenführungsrichtlinie]** in Ihre neue `Loyalty Only`
1. Verwenden Sie als **[!UICONTROL Identity-Namespace]** Ihren `Luma CRM Id`
1. Verwenden Sie als **[!UICONTROL Identitätswert]** den `b642b4217b34b1e8d3bd915fc65c4452`
1. Klicken Sie auf **[!UICONTROL Schaltfläche Profil anzeigen]**
1. Bestätigen Sie, dass keine Profile gefunden wurden:
   ![Nur Treue - keine CRM-ID-Suche.](assets/mergepolicies-loyaltyOnly-noCrmLookup.png)

Die CRM-ID ist ein Identitätsfeld in der `Luma Loyalty Dataset`, zum Nachschlagen von Profilen können jedoch nur primäre Identitäten verwendet werden. Schauen wir uns also das Profil unter Verwendung der primären Identität an, `Luma Loyalty Id`&quot;

1. Ändern Sie den **[!UICONTROL Identity-Namespace]** in `Luma Loyalty Id`
1. Verwenden Sie als **[!UICONTROL Identitätswert]** den `5625458`
1. Klicken Sie auf **[!UICONTROL Schaltfläche Profil anzeigen]**
1. Profil-ID auswählen, um das Profil zu öffnen
1. Navigieren Sie zur Registerkarte **[!UICONTROL Attribute]**
1. Beachten Sie, dass andere Profildetails aus dem CRM-Datensatz, wie z. B. die Mobiltelefonnummer und die E-Mail-Adresse, nicht verfügbar sind, da unsere `Loyalty Only`-Zusammenführungsrichtlinie den CRM-Datensatz nicht enthält.
   ![CRM-Daten können nicht in der Richtlinie „Nur Treue“ angezeigt werden](assets/mergepolicies-loyaltyOnly-attributes.png)
1. Navigieren Sie zur Registerkarte **[!UICONTROL Ereignisse]**
1. ExperienceEvent-Daten sind verfügbar, auch wenn sie nicht explizit in die Datensätze der Zusammenführungsrichtlinie aufgenommen wurden:
   ![Ereignisse können in der Richtlinie „Nur Treue“ angezeigt werden](assets/mergepolicies-loyaltyOnly-events.png)

## Weitere Informationen zu Zusammenführungsrichtlinien

Ändern Sie bei der Profilsuche die verwendete Zusammenführungsrichtlinie wieder in `Default Timebased` und klicken Sie auf die Schaltfläche **[!UICONTROL Profil anzeigen]**. Danny ist zurück!

![Anzeigen eines Profils mit einer anderen Zusammenführungsrichtlinie](assets/mergepolicies-backToDanny.png)

Was ist hier los? Nun, Profilzusammenführungen sind keine einmalige Sache. Echtzeit-Kundenprofile werden im Handumdrehen zusammengestellt. Sie basieren auf verschiedenen Faktoren, darunter auch der Frage, welche Zusammenführungsrichtlinie verwendet wird. Je nach gewünschter Ansicht des Kunden können Sie mehrere Zusammenführungsrichtlinien erstellen, die in verschiedenen Kontexten verwendet werden.

Ein wichtiger Anwendungsfall für Zusammenführungsrichtlinien ist Data Governance. Angenommen, Sie nehmen Daten von Drittanbietern in Platform auf, die nicht für Personalisierungs-Anwendungsfälle verwendet werden können _aber_ für Werbe-Anwendungsfälle verwendet werden können. Sie können eine Zusammenführungsrichtlinie erstellen, die diesen Drittanbieterdatensatz ausschließt, und diese Zusammenführungsrichtlinie zum Erstellen von Segmenten für Ihre Werbeanwendungsfälle verwenden.

## Weitere Ressourcen

* [Dokumentation zu Zusammenführungsrichtlinien](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/overview.html?lang=de)
* [Zusammenführungsrichtlinien-API (Teil der Echtzeit-Kundenprofil-API)-Referenz](https://www.adobe.io/experience-platform-apis/references/profile/#tag/Merge-policies)

Fahren wir nun mit dem [Data Governance-Framework](apply-data-governance-framework.md) fort.

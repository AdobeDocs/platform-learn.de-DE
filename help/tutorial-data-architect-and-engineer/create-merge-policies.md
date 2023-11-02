---
title: Zusammenführungsrichtlinien erstellen
seo-title: Create merge policies | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Zusammenführungsrichtlinien erstellen
description: In dieser Lektion erstellen Sie Zusammenführungsrichtlinien, um zu bestimmen, wie Daten zu Profilen zusammengeführt werden.
role: Data Architect, Data Engineer
feature: Profiles
jira: KT-4348
audience: data architect
doc-type: tutorial
activity: implement
thumbnail: 4348-create-merge-policies.jpg
exl-id: ec862bb2-7aa2-4157-94eb-f5af3a94295f
source-git-commit: 915502e54365eedb09b12a92aa3b1af71f6de1f4
workflow-type: tm+mt
source-wordcount: '996'
ht-degree: 1%

---

# Zusammenführungsrichtlinien erstellen

<!--20 min-->

In dieser Lektion erstellen Sie Zusammenführungsrichtlinien, um die Zusammenführung mehrerer Datenquellen zu Profilen zu priorisieren.

Mit Adobe Experience Platform können Sie Daten aus verschiedenen Quellen zusammenführen und kombinieren, um eine vollständige Ansicht der einzelnen Kunden zu erhalten. Beim Zusammenführen dieser Daten bestimmen Zusammenführungsrichtlinien, wie Daten priorisiert werden und welche Daten kombiniert werden, um eine einheitliche Ansicht zu schaffen.

In dieser Lektion werden wir an der Benutzeroberfläche festgehalten, aber API-Optionen sind auch zum Erstellen von Zusammenführungsrichtlinien vorhanden.

**Datenarchitekten** müssen Zusammenführungsrichtlinien außerhalb dieses Tutorials erstellen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über Zusammenführungsrichtlinien zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/330433?learn=on)

## Erforderliche Berechtigungen

Im [Berechtigungen konfigurieren](configure-permissions.md) Lektion erstellen Sie alle Zugriffssteuerungen, die zum Abschluss dieser Lektion erforderlich sind.

<!--* Permission items **[!UICONTROL Profile Management]** > **[!UICONTROL View Merge Policies]** and **[!UICONTROL Manage Merge Policies]**
* Permission item **[!UICONTROL Profile Management]** > **[!UICONTROL View Profiles]** and **[!UICONTROL Manage Profiles]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
-->

## Über Zusammenführungsrichtlinien und Vereinigungsschema

In der Lektion zur Batch-Erfassung haben wir möglicherweise zwei Datensätze mit etwas anderen Informationen für denselben Kunden hochgeladen. Im [!DNL Loyalty] -Daten, war der Vorname des Kunden `Daniel` und er lebte in `New York City`, aber in den CRM-Daten war der Vorname des Kunden `Danny` und er lebte in `Portland`. Die Kundendaten ändern sich im Laufe der Zeit. Vielleicht ist er von `Portland` nach `New York City`. Auch andere Dinge ändern sich, wie Telefonnummern und E-Mail-Adressen. Zusammenführungsrichtlinien helfen Ihnen bei der Entscheidung, wie Sie diese Arten von Konflikten handhaben, wenn zwei Datenquellen unterschiedliche Informationen für denselben Benutzer bereitstellen.

Warum also? `Danny` als Vorname gewinnen? Sehen wir uns Folgendes an:

1. Wählen Sie in der Benutzeroberfläche von Platform die Option **[!UICONTROL Profile]** in der linken Navigation
1. Navigieren Sie zu **[!UICONTROL Zusammenführungsrichtlinien]** tab
1. Die standardmäßige Zusammenführungsrichtlinie ist ein bestellter Zeitstempel. Da Sie die CRM-Daten nach den Loyalitätsdaten hochgeladen haben, `Danny` hat als Vornamen im Profil gewonnen:

![Bildschirm &quot;Zusammenführungsrichtlinie&quot;](assets/mergepolicies-default.png)

Wenn mehrere Schemas für ein Profil aktiviert sind, wird ein [!UICONTROL Vereinigungsschema] wird automatisch für alle profilaktivierten Schemas erstellt, die eine Basisklasse gemeinsam nutzen. Sie können die [!UICONTROL Unionssysteme] durch **[!UICONTROL Vereinigungsschema]** Registerkarte.

![Bildschirm &quot;Zusammenführungsrichtlinie&quot;](assets/mergepolicies-unionSchema.png)

Beachten Sie, dass es kein Vereinigungsschema für die ExperienceEvent-Klasse gibt. Während ExperienceEvent-Daten weiterhin im Profil landen, da sie zeitreihenbasiert sind, enthält jedes Ereignis einen Zeitstempel und eine ID und Kollisionen sind kein Problem.

Was passiert, wenn Ihnen diese standardmäßige Zusammenführungsrichtlinie nicht gefällt? Was, wenn Luma beschließt, dass ihr Treuesystem die Quelle der Wahrheit sein sollte, wenn es einen Konflikt gibt? Dazu erstellen wir eine Zusammenführungsrichtlinie.

## Erstellen einer Zusammenführungsrichtlinie in der Benutzeroberfläche

1. Wählen Sie auf dem Bildschirm &quot;Zusammenführungsrichtlinien&quot;die **[!UICONTROL Zusammenführungsrichtlinie erstellen]** Schaltfläche oben rechts
1. Als **[!UICONTROL Name]**, eingeben `Loyalty Prioritized`
1. Als **[!UICONTROL Schema]** auswählen **[!UICONTROL XDM-Profil]** (Beachten Sie, dass Ihre benutzerdefinierte Klasse - da es sich um Datensatzdaten handelt - auch für Zusammenführungsrichtlinien verfügbar ist.)
1. Für **[!UICONTROL ID-Zuordnung]** auswählen **[!UICONTROL Privates Diagramm]**
1. Für **[!UICONTROL Attributzusammenführung]** auswählen **[!UICONTROL Datensatzpriorität]**
1. Drag &amp; Drop `Luma Loyalty Dataset` und `Luma CRM Dataset` der **[!UICONTROL Datensatz]** Bedienfeld.
1. Stellen Sie sicher `Luma Loyalty Dataset` befindet sich oben, indem Sie sie per Drag-and-Drop über dem `Luma CRM Dataset`
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]**
   <!--do i need to explain Private Graph? Is that GA?-->
   ![Zusammenführungsrichtlinie](assets/mergepolicies-newPolicy.png)

## Validieren der Zusammenführungsrichtlinie

Lassen Sie uns sehen, ob die Zusammenführungsrichtlinie das tut, was wir erwarten würden:

1. Navigieren Sie zu **[!UICONTROL Durchsuchen]** tab
1. Ändern Sie die **[!UICONTROL Zusammenführungsrichtlinie]** in der neuen `Loyalty Prioritized` policy
1. Als **[!UICONTROL Identitäts-Namespace]**, verwenden Sie Ihre `Luma CRM Id`
1. Als **[!UICONTROL Identitätswert]** use `112ca06ed53d3db37e4cea49cc45b71e`
1. Wählen Sie die **[!UICONTROL Profil anzeigen]** button
1. `Daniel` ist wieder da!

![Anzeigen eines Profils mit einer anderen Zusammenführungsrichtlinie](assets/mergepolicies-lookupProfileWithMergePolicy.png)

## Erstellen einer Zusammenführungsrichtlinie mit eingeschränkten Datensätzen

Beim Erstellen von Zusammenführungsrichtlinien mit Datensatzpriorität werden nur die Datensätze derselben Basisklasse, die Sie rechts einbeziehen, in das Profil aufgenommen. Erstellen wir eine weitere Zusammenführungsrichtlinie

1. Wählen Sie auf dem Bildschirm &quot;Zusammenführungsrichtlinien&quot;die **[!UICONTROL Zusammenführungsrichtlinie erstellen]** Schaltfläche oben rechts
1. Als **[!UICONTROL Name]**, eingeben  `Loyalty Only`
1. Als **[!UICONTROL Schema]** auswählen **[!UICONTROL XDM-Profil]**
1. Für **[!UICONTROL ID-Zuordnung]** auswählen **[!UICONTROL Keines]**
1. Für **[!UICONTROL Attributzusammenführung]** auswählen **[!UICONTROL Datensatzpriorität]**
1. Drag-and-Drop nur die `Luma Loyalty Dataset` nach **[!UICONTROL Ausgewählter Datensatz]** Bedienfeld.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]**

![Zusammenführungsrichtlinie &quot;Nur Loyalität&quot;](assets/mergepolicies-loyaltyOnly.png)

## Validieren der Zusammenführungsrichtlinie

Schauen wir uns nun an, was diese Zusammenführungsrichtlinie bewirkt:

1. Navigieren Sie zu **[!UICONTROL Durchsuchen]** tab
1. Ändern Sie die **[!UICONTROL Zusammenführungsrichtlinie]** in der neuen `Loyalty Only` policy
1. Als **[!UICONTROL Identitäts-Namespace]**, verwenden Sie Ihre `Luma CRM Id`
1. Als **[!UICONTROL Identitätswert]** use `112ca06ed53d3db37e4cea49cc45b71e`
1. Wählen Sie die **[!UICONTROL Profil anzeigen]** button
1. Vergewissern Sie sich, dass keine Profile gefunden wurden:
   ![Treue Nur keine CRM-ID-Suche.](assets/mergepolicies-loyaltyOnly-noCrmLookup.png)

CRM-ID ist ein Identitätsfeld in `Luma Loyalty Dataset`, aber nur primäre Identitäten können zum Nachschlagen von Profilen verwendet werden. Schauen wir uns also das Profil mit der primären Identität an. `Luma Loyalty Id`&quot;

1. Ändern Sie die **[!UICONTROL Identity Namespace]** nach `Luma Loyalty Id`
1. Als **[!UICONTROL Identitätswert]** use `5625458`
1. Wählen Sie die **[!UICONTROL Profil anzeigen]** button
1. Wählen Sie die Profil-ID aus, um das Profil zu öffnen
1. Navigieren Sie zu **[!UICONTROL Attribute]** tab
1. Beachten Sie, dass andere Profildetails aus dem CRM-Datensatz wie die Mobiltelefonnummer und die E-Mail-Adresse nicht verfügbar sind, da wir nur
   ![CRM-Daten werden nicht in der Richtlinie &quot;Nur Treue&quot;angezeigt](assets/mergepolicies-loyaltyOnly-attributes.png)
1. Navigieren Sie zu **[!UICONTROL Veranstaltungen]** tab
1. ExperienceEvent-Daten sind verfügbar, obwohl sie nicht explizit in den Datensätzen der Zusammenführungsrichtlinie enthalten sind:
   ![Ereignisse werden in der Richtlinie &quot;Nur Treue&quot;angezeigt](assets/mergepolicies-loyaltyOnly-events.png)

## Weitere Informationen zu Zusammenführungsrichtlinien

Ändern Sie in der Profilsuche die verwendete Zusammenführungsrichtlinie zurück in `Default Timebased` und wählen Sie die **[!UICONTROL Profil anzeigen]** Schaltfläche. Danny ist wieder da!

![Anzeigen eines Profils mit einer anderen Zusammenführungsrichtlinie](assets/mergepolicies-backToDanny.png)

Was ist hier los? Die Profilzusammenführung ist keine einmalige Sache. Echtzeit-Kundenprofile werden spontan zusammengestellt und basieren auf verschiedenen Faktoren, einschließlich der verwendeten Zusammenführungsrichtlinie. Sie können mehrere Zusammenführungsrichtlinien erstellen, die je nach gewünschter Ansicht des Kunden in verschiedenen Kontexten verwendet werden.

Ein wichtiges Anwendungsbeispiel für Zusammenführungsrichtlinien ist die Data Governance. Angenommen, Sie erfassen Daten von Drittanbietern in Platform, die nicht für Personalisierungsfälle verwendet werden können, aber _can_ für Werbezwecke verwendet werden. Sie können eine Zusammenführungsrichtlinie erstellen, die diesen Datensatz von Drittanbietern ausschließt, und diese Zusammenführungsrichtlinie verwenden, um Segmente für Ihre Anwendungsfälle für Werbung zu erstellen.

## Weitere Ressourcen

* [Dokumentation zu Zusammenführungsrichtlinien](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/overview.html)
* [Referenz zur API für Zusammenführungsrichtlinien (Teil der Echtzeit-Kundenprofil-API)](https://www.adobe.io/experience-platform-apis/references/profile/#tag/Merge-policies)

Gehen wir nun zum [Data Governance-Framework](apply-data-governance-framework.md).

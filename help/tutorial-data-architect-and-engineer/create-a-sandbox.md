---
title: Sandbox erstellen
seo-title: Create a sandbox | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Sandbox erstellen
description: In dieser Lektion erstellen Sie eine Sandbox für Entwicklungsumgebungen, die Sie für den Rest des Tutorials verwenden können.
role: Data Architect, Data Engineer
feature: Sandboxes
jira: KT-4348
thumbnail: 4348-create-a-sandbox.jpg
exl-id: a04afada-52a1-4812-8fa2-14be72e68614
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 2%

---

# Erstellen einer Sandbox

<!--25min-->

In dieser Lektion erstellen Sie eine Sandbox für Entwicklungsumgebungen, die Sie für den Rest des Tutorials verwenden werden.

Sandboxes bieten isolierte Umgebungen, in denen Sie Funktionen ausprobieren können, ohne Ressourcen und Daten mit Ihrer Produktionsumgebung zu mischen. Weitere Informationen finden Sie in der Dokumentation zu [Sandboxes](https://experienceleague.adobe.com/docs/experience-platform/sandbox/home.html?lang=de) .

**Datenarchitekten** und **Dateningenieure** müssen außerhalb dieses Tutorials Sandboxes erstellen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über Sandboxes zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/29838/?learn=on)

## Erforderliche Berechtigungen

In der Lektion [Berechtigungen konfigurieren](configure-permissions.md) richten Sie alle Zugriffssteuerungen ein, die zum Abschluss dieser Lektion erforderlich sind.

<!--
* Permission items **[!UICONTROL Sandbox Administration]** > **[!UICONTROL View Sandboxes]** and **[!UICONTROL Manage Sandboxes]**
* Permission item **[!UICONTROL Sandboxes]** > **[!UICONTROL Prod]**
* User-role access to the `Luma Tutorial Platform` product profile
* Admin-level access to the `Luma Tutorial Platform` product profile
-->

## Erstellen einer Sandbox

Erstellen wir eine Sandbox:

1. Melden Sie sich bei der Benutzeroberfläche von [Adobe Experience Platform](https://experience.adobe.com/platform) an
1. Navigieren Sie in der linken Navigation zu **[!UICONTROL Sandboxes]** .
1. Wählen Sie oben rechts **[!UICONTROL Sandbox erstellen]** aus.
   ![Wählen Sie Sandbox erstellen](assets/sandbox-createSandbox.png)

1. Wählen Sie **[!UICONTROL Entwicklung]** als **[!UICONTROL Typ]** aus.
1. Benennen Sie Ihre Sandbox mit &quot;`luma-tutorial`&quot;(erwägen Sie, Ihren Namen am Ende hinzuzufügen).
1. Titel Ihres Tutorials `Luma Tutorial` (erwägen Sie, Ihren Namen am Ende hinzuzufügen)
1. Wählen Sie die Schaltfläche **[!UICONTROL Erstellen]** aus
   ![Erstellen Ihrer Sandbox](assets/sandbox-nameSandbox.png)
   >[!NOTE]
   >
   >Sie können zwar beliebige Werte für Ihren Sandbox-Namen und Titel verwenden, es wird jedoch empfohlen, die vorgeschlagenen Werte einzuhalten, da wir im Tutorial auf diese Beschriftungen verweisen werden. Wenn Ihre Organisation mehrere Personen hat, die dieses Tutorial abschließen, sollten Sie erwägen, Ihren Namen am Ende des Sandbox-Titels und -Namens hinzuzufügen, z. B. &quot;luma-tutorial-ignatiusjreilly&quot;.

Die Erstellung von Sandboxes dauert etwa 30 Sekunden, wobei der Status &quot;[!UICONTROL Erstellen]&quot; angezeigt wird. Wenn die Sandbox vollständig erstellt wurde, wird sie als &quot;[!UICONTROL aktiv]&quot; angezeigt:
![Aktiver Status](assets/sandbox-active.png)

Warten Sie, bis Ihre Sandbox &quot;[!UICONTROL aktiv]&quot; ist, bevor Sie mit der nächsten Übung fortfahren.

## Hinzufügen der neuen Sandbox zur Rolle

Sobald die Sandbox aktiv ist, müssen Sie sie in Ihre Rolle aufnehmen, um sie verwenden zu können. So fügen Sie sie Ihrer Rolle hinzu (Systemadministrator- oder Produktadministratorberechtigungen erforderlich):

1. Navigieren Sie zum Bildschirm [!UICONTROL Berechtigungen] .
1. Öffnen Sie die Rolle `Luma Tutorial Platform` .
1. Optional _Entfernen Sie_ die Sandbox `Prod` aus der Rolle
1. Hinzufügen der Sandbox `Luma Tutorial`
1. Wählen Sie **[!UICONTROL Speichern]** aus.
1. Wählen Sie in der Zeile [!UICONTROL Sandboxes] die Option **[!UICONTROL Bearbeiten]**

   ![Hinzufügen des Luma-Tutorials](assets/sandbox-addLumaTutorial.png)

1. Laden Sie die Seite neu (oder drücken Sie die Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt.).`Luma Tutorial`
1. Wechseln Sie zur Sandbox `Luma Tutorial` , falls Sie noch nicht darin sind.

   ![Sandbox bestätigen](assets/sandbox-confirmDropdown.png)

Gut, Sie haben Ihre Sandbox erstellt und sind bereit für die [Einrichtung von Developer Console und Postman](set-up-developer-console-and-postman.md)!

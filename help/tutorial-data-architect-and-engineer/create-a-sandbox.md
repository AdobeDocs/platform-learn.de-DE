---
title: Sandbox erstellen
seo-title: Create a sandbox | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Sandbox erstellen
description: In dieser Lektion erstellen Sie eine Sandbox für die Entwicklungsumgebung, die Sie für den Rest des Tutorials verwenden können.
role: Data Architect, Data Engineer
feature: Sandboxes
jira: KT-4348
thumbnail: 4348-create-a-sandbox.jpg
exl-id: a04afada-52a1-4812-8fa2-14be72e68614
source-git-commit: 286c85aa88d44574f00ded67f0de8e0c945a153e
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 2%

---

# Erstellen einer Sandbox

<!--25min-->

In dieser Lektion erstellen Sie eine Sandbox für die Entwicklungsumgebung, die Sie für den Rest des Tutorials verwenden werden.

Sandboxes bieten isolierte Umgebungen, in denen Sie Funktionen ausprobieren können, ohne Ressourcen und Daten mit Ihrer Produktionsumgebung zu mischen. Weitere Informationen finden Sie in der [Sandbox-Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/sandbox/home.html?lang=de).

**Datenarchitekten** und **Dateningenieure** müssen außerhalb dieses Tutorials Sandboxes erstellen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über Sandboxes zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/29838/?learn=on&enablevpops)

## Erforderliche Berechtigungen

In der Lektion [Berechtigungen konfigurieren](configure-permissions.md) richten Sie alle Zugriffssteuerungen ein, die zum Abschließen dieser Lektion erforderlich sind.

<!--
* Permission items **[!UICONTROL Sandbox Administration]** > **[!UICONTROL View Sandboxes]** and **[!UICONTROL Manage Sandboxes]**
* Permission item **[!UICONTROL Sandboxes]** > **[!UICONTROL Prod]**
* User-role access to the `Luma Tutorial Platform` product profile
* Admin-level access to the `Luma Tutorial Platform` product profile
-->

## Erstellen einer Sandbox

Erstellen wir eine Sandbox:

1. Melden Sie sich bei der [Adobe Experience Platform](https://experience.adobe.com/platform)-Benutzeroberfläche an
1. Navigieren Sie **[!UICONTROL linken Navigationsbereich zu]** Sandboxes“
1. Wählen **[!UICONTROL oben rechts]**Sandbox erstellen“ aus
   ![Wählen Sie Sandbox erstellen aus](assets/sandbox-createSandbox.png)

1. Wählen Sie **[!UICONTROL Entwicklung]** als **[!UICONTROL Typ]**
1. Benennen Sie Ihre Sandbox-`luma-tutorial` (fügen Sie ggf. Ihren Namen am Ende hinzu)
1. Titel des Tutorial-`Luma Tutorial` (Erwägen Sie, am Ende Ihren Namen hinzuzufügen)
1. Klicken Sie auf **[!UICONTROL Schaltfläche]**Erstellen“
   ![Erstellen Sie Ihre Sandbox](assets/sandbox-nameSandbox.png)
   >[!NOTE]
   >
   >Sie können zwar beliebige Werte für Ihren Sandbox-Namen und -Titel verwenden, es wird jedoch empfohlen, an den vorgeschlagenen Werten festzuhalten, da wir im gesamten Tutorial auf diese Beschriftungen verweisen werden. Wenn mehrere Personen in Ihrer Organisation dieses Tutorial abschließen, sollten Sie erwägen, Ihren Namen am Ende des Sandbox-Titels und -Namens hinzuzufügen, z. B. luma-tutorial-ignatiusjreilly.

Die Erstellung von Sandboxes dauert etwa 30 Sekunden. Während dieser Zeit wird der Status [!UICONTROL Wird erstellt] angezeigt. Wenn die Sandbox vollständig erstellt ist, wird sie als &quot;[!UICONTROL &quot; ]:
![Aktiver Status](assets/sandbox-active.png)

Warten Sie, bis Ihre Sandbox &quot;[!UICONTROL aktiv] ist, bevor Sie mit der nächsten Übung fortfahren.

## Fügen Sie die neue Sandbox zur Rolle hinzu

Sobald die Sandbox aktiv ist, müssen Sie sie in Ihre Rolle einbeziehen, um sie verwenden zu können. So fügen Sie sie Ihrer Rolle hinzu (erfordert Berechtigungen als Systemadministrator oder Produktadministrator):

1. Zum Bildschirm [!UICONTROL Berechtigungen] wechseln
1. Öffnen Sie die `Luma Tutorial Platform` Rolle
1. Optional _Entfernen_ die `Prod` Sandbox aus der Rolle
1. Hinzufügen der `Luma Tutorial` Sandbox
1. Wählen Sie **[!UICONTROL Speichern]**
1. Wählen Sie in der [!UICONTROL Sandboxes] die Option **[!UICONTROL Bearbeiten]**

   ![Hinzufügen des Luma-Tutorials](assets/sandbox-addLumaTutorial.png)

1. Laden Sie die Seite neu (oder laden Sie die Umschalttaste neu). Jetzt sollten Sie sich entweder in der `Luma Tutorial` Sandbox befinden oder sie sollte in Ihrer Sandbox-Dropdown-Liste angezeigt werden
1. Wechseln Sie zur Sandbox &quot;`Luma Tutorial`&quot;, wenn Sie sich noch nicht darin befinden

   ![Sandbox bestätigen](assets/sandbox-confirmDropdown.png)

Gut, Sie haben Ihre Sandbox erstellt und sind bereit zum [Einrichten von Developer Console und Postman](set-up-developer-console-and-postman.md)!

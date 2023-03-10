---
title: Sandbox erstellen
seo-title: Create a sandbox | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Sandbox erstellen
description: In dieser Lektion erstellen Sie eine Sandbox für Entwicklungsumgebungen, die Sie für den Rest des Tutorials verwenden können.
role: Data Architect, Data Engineer
feature: Sandboxes
kt: 4348
thumbnail: 4348-create-a-sandbox.jpg
exl-id: a04afada-52a1-4812-8fa2-14be72e68614
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 5%

---

# Sandbox erstellen

<!--25min-->

In dieser Lektion erstellen Sie eine Sandbox für die Entwicklungsumgebung, die Sie für den Rest des Tutorials verwenden werden.

Sandboxes bieten isolierte Umgebungen, in denen Sie Funktionen ausprobieren können, ohne Ressourcen und Daten mit Ihrer Produktionsumgebung zu mischen. Weitere Informationen finden Sie unter [Sandbox-Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/sandbox/home.html?lang=de).

**Datenarchitekten** und **Dateningenieure** müssen Sandboxes außerhalb dieses Tutorials erstellen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über Sandboxes zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/29838/?quality=12&learn=on)

## Erforderliche Berechtigungen

Im [Berechtigungen konfigurieren](configure-permissions.md) Lektion erstellen Sie alle Zugriffssteuerungen, die zum Abschluss dieser Lektion erforderlich sind.

<!--
* Permission items **[!UICONTROL Sandbox Administration]** > **[!UICONTROL View Sandboxes]** and **[!UICONTROL Manage Sandboxes]**
* Permission item **[!UICONTROL Sandboxes]** > **[!UICONTROL Prod]**
* User-role access to the `Luma Tutorial Platform` product profile
* Admin-level access to the `Luma Tutorial Platform` product profile
-->

## Erstellen einer Sandbox

Erstellen wir eine Sandbox:

1. Melden Sie sich bei der [Adobe Experience Platform](https://experience.adobe.com/platform) Benutzeroberfläche
1. Navigieren Sie zu **[!UICONTROL Sandboxes]** in der linken Navigation
1. Auswählen **[!UICONTROL Sandbox erstellen]** oben rechts
   ![Sandbox erstellen](assets/sandbox-createSandbox.png)

1. Auswählen **[!UICONTROL Entwicklung]** als **[!UICONTROL Typ]**
1. Benennen Sie Ihre Sandbox. `luma-tutorial` (erwägen Sie, Ihren Namen am Ende hinzuzufügen)
1. Anleitung benennen `Luma Tutorial` (erwägen Sie, Ihren Namen am Ende hinzuzufügen)
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Erstellen]**
   ![Sandbox erstellen](assets/sandbox-nameSandbox.png)
   >[!NOTE]
   >
   >Sie können zwar beliebige Werte für Ihren Sandbox-Namen und Titel verwenden, es wird jedoch empfohlen, die vorgeschlagenen Werte einzuhalten, da wir im Tutorial auf diese Beschriftungen verweisen werden. Wenn Ihre Organisation mehrere Personen hat, die dieses Tutorial abschließen, sollten Sie erwägen, Ihren Namen am Ende des Sandbox-Titels und -Namens hinzuzufügen, z. B. &quot;luma-tutorial-ignatiusjreilly&quot;.

Die Erstellung von Sandboxes dauert etwa 30 Sekunden, wobei ein[!UICONTROL Erstellen]Der Status wird angezeigt. Wenn die Sandbox vollständig erstellt wurde, wird sie als &quot;[!UICONTROL Aktiv]&quot;:
![Aktiver Status](assets/sandbox-active.png)

Warten Sie, bis Ihre Sandbox[!UICONTROL Aktiv]&quot;, bevor sie mit der nächsten Übung fortfahren.

## Hinzufügen der neuen Sandbox zum Produktprofil

Sobald die Sandbox aktiv ist, müssen Sie sie in Ihr Produktprofil aufnehmen, um sie verwenden zu können. So fügen Sie ihn Ihrem Produktprofil hinzu:

1. Melden Sie sich auf einer separaten Browser-Registerkarte bei der [Admin Console](https://adminconsole.adobe.com)
1. Navigieren Sie zu **[!UICONTROL Produkte > Adobe Experience Platform]**
1. Öffnen Sie die `Luma Tutorial Platform` profile

   ![Produktprofil auswählen](assets/sandbox-selectProfile.png)

1. Navigieren Sie zu **[!UICONTROL Berechtigungen]** tab

1. Im [!UICONTROL Sandboxes] Zeile auswählen **[!UICONTROL Bearbeiten]**

   ![Wählen Sie Bearbeiten](assets/sandbox-selectSandboxes.png) aus

1. _Entfernen_ die **[!UICONTROL Prod]** Sandbox, die Sie dem Profil ursprünglich zugewiesen haben
1. Wählen Sie die **[!UICONTROL +]** Symbol zum Hinzufügen der neuen `Luma Tutorial` Sandbox in der rechten Spalte
1. Auswählen **[!UICONTROL Speichern]** , um die aktualisierten Berechtigungen zu speichern

   ![Verschieben der Sandbox in die andere Spalte](assets/sandbox-addLumaTutorial.png)

1. Kehren Sie zur Browser-Registerkarte mit Experience Platform zurück.
1. Laden Sie die Seite neu (oder drücken Sie die Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt-Umschalt). `Luma Tutorial` Sandbox oder sie sollte in der Sandbox-Dropdown-Liste angezeigt werden
1. Wechseln Sie zu `Luma Tutorial` Sandbox, falls noch nicht vorhanden

   ![Sandbox bestätigen](assets/sandbox-confirmDropdown.png)

Gut, Sie haben Ihre Sandbox erstellt und sind bereit, [Einrichten von Developer Console und Postman](set-up-developer-console-and-postman.md)!

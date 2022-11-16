---
title: Erstellen eines Datensatzes
description: Erstellen eines Datensatzes
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
kt: 10447
hide: true
hidefromtoc: true
exl-id: 7705d292-a29c-4977-bcc6-f088a51713ea
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 8%

---

# Erstellen eines Datensatzes

Zusätzlich zur Beschreibung der Daten, die Sie an Adobe Experience Platform senden, benötigen Sie eine Stelle, an der die Daten beibehalten werden. In Adobe Experience Platform werden diese Behälter, in die Sie Daten einfügen können, als Datensätze bezeichnet.

Um einen Datensatz zu erstellen, navigieren Sie zum [!UICONTROL Datensätze] Ansicht in Adobe Experience Platform.

![Ansicht &quot;Datensätze&quot;](../../../assets/implementation-strategy/datasets-view.png)

Klicken [!UICONTROL Datensatz erstellen] in der oberen rechten Ecke.

Wählen Sie während des Erstellungsprozesses des Datensatzes die Option [!UICONTROL Datensatz aus Schema erstellen] und wählen Sie [das zuvor von Ihnen erstellte Schema](create-a-schema.md).

![Schemaauswahl](../../../assets/implementation-strategy/schema-selection.png)

Klicken [!UICONTROL Nächste] und geben Sie einen Namen und eine Beschreibung ein.

![Datensatzname und Beschreibung](../../../assets/implementation-strategy/dataset-name-description.png)

Klicken Sie auf [!UICONTROL Fertigstellen]. Ihr Datensatz wurde erstellt und kann Daten empfangen.

Wenn Sie Daten in einen Datensatz senden, überprüft Adobe Experience Platform, ob die Daten, die Sie in den Datensatz einfügen möchten, mit dem angewendeten Schema übereinstimmen. Wenn die Daten nicht mit dem Schema übereinstimmen, werden die Daten zurückgewiesen und nicht in den Datensatz eingefügt. Infolge dieses Validierungsschritts können Verbraucher des Datensatzes (Adobe-Produkte, Drittanbieter oder Ihr eigenes Unternehmen) ein gewisses Maß an Sicherheit in Bezug auf die Struktur und Sauberkeit der Daten des Datensatzes haben.

Weitere Informationen zum Erstellen von Datensätzen finden Sie unter [Handbuch zur Benutzeroberfläche von Datensätzen](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/user-guide.html?lang=de).

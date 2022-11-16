---
title: Foundation - Echtzeit-Kundenprofil - Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - Benutzeroberfläche
description: Foundation - Echtzeit-Kundenprofil - Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - Benutzeroberfläche
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: ed13e37f-48eb-4668-b828-6c58340a7cc1
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 2%

---

# 3.2 Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - Benutzeroberfläche

In dieser Übung melden Sie sich bei Adobe Experience Platform an und sehen sich Ihr eigenes Echtzeit-Kundenprofil in der Benutzeroberfläche an.

## Geschichte

Im Echtzeit-Kundenprofil werden alle Profildaten zusammen mit Ereignisdaten sowie vorhandenen Segmentmitgliedschaften angezeigt. Die angezeigten Daten können von überall kommen, von Adobe-Applikationen und externen Lösungen. Dies ist die leistungsstärkste Ansicht in Adobe Experience Platform, das wahre Erlebnissystem der Aufzeichnungen.

## 3.2.1 Verwenden der Kundenprofilansicht in Adobe Experience Platform

Navigieren Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](../module2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``--aepSandboxId--``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nach Auswahl der entsprechenden [!UICONTROL Sandbox], sehen Sie die Änderung des Bildschirms und befinden sich jetzt in Ihrem [!UICONTROL Sandbox].

![Datenaufnahme](../module2/images/sb1.png)

Gehen Sie im linken Menü zu **Profile** und **Durchsuchen**.

![Kundenprofil](./images/homemenu.png)

Im Bedienfeld &quot;Profil-Viewer&quot;auf Ihrer Website finden Sie mehrere Identitäten. Jede Identität ist mit einem Namespace verknüpft.

![Kundenprofil](./images/identities.png)

Im Bedienfeld &quot;Profil-Viewer&quot;können Sie die folgenden Kombinationen von IDs und Namespaces sehen:

| Identität | Namespace |
|:-------------:| :---------------:|
| Experience Cloud ID (ECID) | 12507560687324495704459439363261812234 |
| Email ID | woutervangeluwe+06022022-01@gmail.com |
| Mobiltelefonnummer | +32473622044+06022022-01 |

Bei Adobe Experience Platform sind alle IDs gleichermaßen wichtig. Zuvor war die ECID die wichtigste ID im Kontext der Adobe, und alle anderen IDs waren hierarchisch mit der ECID verknüpft. Bei Adobe Experience Platform ist dies nicht mehr der Fall und jede ID kann als primäre Kennung betrachtet werden.

In der Regel hängt die primäre Kennung vom Kontext ab. Wenn Sie Ihr Callcenter fragen, **Was ist die wichtigste ID?** sie werden wahrscheinlich antworten, **die Telefonnummer!** Wenn Sie jedoch Ihr CRM-Team fragen, antworten diese, **Die E-Mail-Adresse!**  Adobe Experience Platform versteht diese Komplexität und verwaltet sie für Sie. Jede Anwendung, ob Adobe App oder Nicht-Adobe App, spricht mit Adobe Experience Platform, indem sie auf die ID verweist, die sie als primär betrachten. Und es funktioniert einfach.

Für das Feld **Identitäts-Namespace** auswählen **Email** und für das Feld **Identitätswert** Geben Sie die E-Mail-Adresse ein, unter der Sie sich in der vorherigen Übung registriert haben. Klicken **Ansicht**. Ihr Profil wird dann in der Liste angezeigt. Klicken Sie auf **Profil-ID** , um Ihr Profil zu öffnen.

![Kundenprofil](./images/popupecid.png)

Sie sehen jetzt eine Übersicht über einige wichtige **Profilattribute** Ihres Kundenprofils.

![Kundenprofil](./images/profile.png)

Wenn Sie alle für Ihr Profil verfügbaren Profilattribute anzeigen möchten, gehen Sie zu **Attribute**.

![Kundenprofil](./images/profilattr.png)

Navigieren Sie zu **Veranstaltungen**, wo Sie Einträge für jedes Erlebnisereignis sehen können, das mit Ihrem Profil verknüpft ist.

![Kundenprofil](./images/profileee.png)

Navigieren Sie schließlich zur Menüoption **Segmentmitgliedschaft**. Jetzt werden alle Segmente angezeigt, die für dieses Profil qualifiziert sind.

![Kundenprofil](./images/profileseg.png)

Nachdem Sie nun gelernt haben, wie Sie das Echtzeit-Profil eines jeden Kunden anzeigen können, indem Sie die Adobe Experience Platform-Benutzeroberfläche verwenden, führen wir dasselbe über die APIs durch, indem wir Postman und Adobe I/O nutzen, um Abfragen mit Adobe Experience Platform-APIs durchzuführen.

Nächster Schritt: [3.3 Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - API](./ex3.md)

[Zurück zu Modul 3](./real-time-customer-profile.md)

[Zu allen Modulen zurückkehren](../../overview.md)

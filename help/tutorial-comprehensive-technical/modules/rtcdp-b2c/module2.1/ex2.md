---
title: Foundation - Echtzeit-Kundenprofil - Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - Benutzeroberfläche
description: Foundation - Echtzeit-Kundenprofil - Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - Benutzeroberfläche
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 1%

---

# 2.1.2 Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - Benutzeroberfläche

In dieser Übung melden Sie sich bei Adobe Experience Platform an und sehen sich Ihr eigenes Echtzeit-Kundenprofil in der Benutzeroberfläche an.

## Geschichte

Im Echtzeit-Kundenprofil werden alle Profildaten zusammen mit Ereignisdaten sowie vorhandenen Segmentmitgliedschaften angezeigt. Die angezeigten Daten können von überall kommen, von Adobe-Anwendungen und externen Lösungen. Dies ist die leistungsstärkste Ansicht in Adobe Experience Platform, das wahre Erlebnissystem der Aufzeichnungen.

## 2.1.2.1 Verwenden der Kundenprofilansicht in Adobe Experience Platform

Wechseln Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](../../datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxName--``. Klicken Sie dazu in der blauen Zeile oben auf Ihrem Bildschirm auf den Text **[!UICONTROL Produktions-Prod]** . Nachdem Sie die entsprechende [!UICONTROL Sandbox] ausgewählt haben, sehen Sie die Bildschirmänderung und befinden sich nun in Ihrer dedizierten [!UICONTROL Sandbox].

![Datenaufnahme](../../datacollection/module1.2/images/sb1.png)

Gehen Sie im linken Menü zu **Profile** und zu **Durchsuchen**.

![Kundenprofil](./images/homemenu.png)

Im Bedienfeld &quot;Profil-Viewer&quot;auf Ihrer Website finden Sie mehrere Identitäten. Jede Identität ist mit einem Namespace verknüpft.

![Kundenprofil](./images/identities.png)

Im Bedienfeld &quot;Profil-Viewer&quot;können Sie die folgenden Kombinationen von IDs und Namespaces sehen:

| Identität | Namespace |
|:-------------:| :---------------:|
| Experience Cloud ID (ECID) | 12507560687324495704459439363261812234 |
| Email ID | woutervangeluwe+06022022-01@gmail.com |
| Mobiltelefonnummer | +32473622044+06022022-01 |

Bei Adobe Experience Platform sind alle IDs gleichermaßen wichtig. Zuvor war die ECID die wichtigste ID im Adobe-Kontext, und alle anderen IDs waren hierarchisch mit der ECID verknüpft. Bei Adobe Experience Platform ist dies nicht mehr der Fall und jede ID kann als primäre Kennung betrachtet werden.

In der Regel hängt die primäre Kennung vom Kontext ab. Wenn Sie Ihr Callcenter fragen, **Was ist die wichtigste ID?** werden sie wahrscheinlich antworten, **die Telefonnummer!** Wenn Sie jedoch Ihr CRM-Team fragen, antworten diese, **Die E-Mail-Adresse!** Adobe Experience Platform versteht diese Komplexität und verwaltet sie für Sie. Jede Anwendung, ob Adobe-Anwendung oder Nicht-Adobe-Anwendung, spricht mit Adobe Experience Platform, indem sie auf die ID verweist, die sie als primär betrachten. Und es funktioniert einfach.

Wählen Sie für das Feld **Identitäts-Namespace** die Option **E-Mail** aus und geben Sie für das Feld **Identitätswert** die E-Mail-Adresse ein, die Sie zur Registrierung in der vorherigen Übung verwendet haben. Klicken Sie auf **Ansicht**. Ihr Profil wird dann in der Liste angezeigt. Klicken Sie auf die **Profil-ID** , um Ihr Profil zu öffnen.

![Kundenprofil](./images/popupecid.png)

Sie sehen jetzt eine Übersicht über einige wichtige **Profilattribute** Ihres Kundenprofils.

![Kundenprofil](./images/profile.png)

Wenn Sie alle für Ihr Profil verfügbaren Profilattribute anzeigen möchten, gehen Sie zu **Attribute**.

![Kundenprofil](./images/profilattr.png)

Navigieren Sie zu **Ereignisse** , wo Sie Einträge für jedes Erlebnisereignis sehen können, das mit Ihrem Profil verknüpft ist.

![Kundenprofil](./images/profileee.png)

Navigieren Sie schließlich zur Menüoption **Segmentmitgliedschaft**. Jetzt werden alle Segmente angezeigt, die für dieses Profil qualifiziert sind.

![Kundenprofil](./images/profileseg.png)

Nachdem Sie nun gelernt haben, wie Sie das Echtzeit-Profil eines Kunden anzeigen können, indem Sie die Adobe Experience Platform-Benutzeroberfläche verwenden, führen wir über die APIs dasselbe durch, indem wir Postman und Adobe I/O verwenden, um Abfragen mit Adobe Experience Platform-APIs durchzuführen.

Nächster Schritt: [2.1.3 Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - API](./ex3.md)

[Zurück zu Modul 2.1](./real-time-customer-profile.md)

[Zu allen Modulen zurückkehren](../../../overview.md)

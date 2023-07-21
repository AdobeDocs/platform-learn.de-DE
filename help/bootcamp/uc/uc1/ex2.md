---
title: Bootcamp - Echtzeit-Kundenprofil - Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - Benutzeroberfläche
description: Bootcamp - Echtzeit-Kundenprofil - Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - Benutzeroberfläche
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Profiles
exl-id: 4c810767-00ab-4cae-baa9-97b0cb9bf2df
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 2%

---

# 1.2 Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - Benutzeroberfläche

In dieser Übung melden Sie sich bei Adobe Experience Platform an und sehen sich Ihr eigenes Echtzeit-Kundenprofil in der Benutzeroberfläche an.

## Geschichte

Im Echtzeit-Kundenprofil werden alle Profildaten zusammen mit Ereignisdaten sowie vorhandenen Segmentmitgliedschaften angezeigt. Die angezeigten Daten können von überall kommen, von Adobe-Applikationen und externen Lösungen. Dies ist die leistungsstärkste Ansicht in Adobe Experience Platform, das wahre Erlebnissystem der Aufzeichnungen.

## 1.2.1 Verwenden der Kundenprofilansicht in Adobe Experience Platform

Navigieren Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``Bootcamp``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nach Auswahl der entsprechenden [!UICONTROL Sandbox], sehen Sie die Änderung des Bildschirms und befinden sich jetzt in Ihrem [!UICONTROL Sandbox].

![Datenaufnahme](./images/sb1.png)

Gehen Sie im linken Menü zu **Profile** und **Durchsuchen**.

![Kundenprofil](./images/homemenu.png)

Im Bedienfeld &quot;Profil-Viewer&quot;auf Ihrer Website finden Sie die Identitätsübersicht. Jede Identität ist mit einem Namespace verknüpft.

![Kundenprofil](./images/identities.png)

Im Bedienfeld &quot;Profil-Viewer&quot;kann derzeit diese Identität angezeigt werden:

| Namespace | Identität |
|:-------------:| :---------------:|
| Experience Cloud ID (ECID) | 19428085896177382402834560825640259081 |

Bei Adobe Experience Platform sind alle IDs gleichermaßen wichtig. Zuvor war die ECID die wichtigste ID im Kontext der Adobe, und alle anderen IDs waren hierarchisch mit der ECID verknüpft. Bei Adobe Experience Platform ist dies nicht mehr der Fall und jede ID kann als primäre Kennung betrachtet werden.

In der Regel hängt die primäre Kennung vom Kontext ab. Wenn Sie Ihr Callcenter fragen, **Was ist die wichtigste ID?** sie werden wahrscheinlich antworten, **die Telefonnummer!** Wenn Sie jedoch Ihr CRM-Team fragen, antworten diese, **Die E-Mail-Adresse!**  Adobe Experience Platform versteht diese Komplexität und verwaltet sie für Sie. Jede Anwendung, ob Adobe App oder Nicht-Adobe App, spricht mit Adobe Experience Platform, indem sie auf die ID verweist, die sie als primär betrachten. Und es funktioniert einfach.

Für das Feld **Identitäts-Namespace** auswählen **ECID** und für das Feld **Identitätswert** Geben Sie die ECID ein, die Sie im Bereich Profil-Viewer der Bootcamp-Website finden können. Klicken **Ansicht**. Ihr Profil wird dann in der Liste angezeigt. Klicken Sie auf **Profil-ID** , um Ihr Profil zu öffnen.

![Kundenprofil](./images/popupecid.png)

Sie sehen jetzt eine Übersicht über einige wichtige **Profilattribute** Ihres Kundenprofils.

![Kundenprofil](./images/profile.png)

Navigieren Sie zu **Veranstaltungen**, wo Sie Einträge für jedes Erlebnisereignis sehen können, das mit Ihrem Profil verknüpft ist.

![Kundenprofil](./images/profileee.png)

Navigieren Sie schließlich zur Menüoption **Segmentmitgliedschaft**. Jetzt werden alle Segmente angezeigt, die für dieses Profil qualifiziert sind.

![Kundenprofil](./images/profileseg.png)

Erstellen wir nun ein neues Segment, mit dem Sie das Kundenerlebnis für einen anonymen oder bekannten Kunden personalisieren können.

Nächster Schritt: [1.3 Segment erstellen - Benutzeroberfläche](./ex3.md)

[Zurück zum Benutzerfluss 1](./uc1.md)

[Zu allen Modulen zurückkehren](../../overview.md)

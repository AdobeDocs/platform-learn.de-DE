---
title: Bootcamp - Echtzeit-Kundenprofil - Visualisieren Ihres eigenen Echtzeit-Kundenprofils - Benutzeroberfläche
description: Bootcamp - Echtzeit-Kundenprofil - Visualisieren Ihres eigenen Echtzeit-Kundenprofils - Benutzeroberfläche
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Profiles
exl-id: 4c810767-00ab-4cae-baa9-97b0cb9bf2df
source-git-commit: 5876de5015e4c8c337c235c24cc28b0a32e274dd
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# 1.2 Visualisieren Ihres eigenen Echtzeit-Kundenprofils - Benutzeroberfläche

In dieser Übung melden Sie sich bei Adobe Experience Platform an und zeigen in der Benutzeroberfläche Ihr eigenes Echtzeit-Kundenprofil an.

## Story

Im Echtzeit-Kundenprofil werden alle Profildaten zusammen mit Ereignisdaten sowie vorhandene Zielgruppenzugehörigkeiten angezeigt. Die angezeigten Daten können von überall, aus Adobe-Anwendungen und externen Lösungen stammen. Dies ist die leistungsfähigste Ansicht in Adobe Experience Platform, dem echten Erlebnissystem der Aufzeichnung.

## 1.2.1 Verwenden der Kundenprofilansicht in Adobe Experience Platform

Zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``Bootcamp``. Klicken Sie dazu auf den Text **[!UICONTROL Produktion]** in der blauen Linie am oberen Bildschirmrand. Nach Auswahl der entsprechenden [!UICONTROL Sandbox] wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten [!UICONTROL Sandbox].



Gehen Sie im linken Menü zu **Profile** und zu **Durchsuchen**.

![Kundenprofil](./images/homemenu.png)

Im Bereich Profil-Viewer auf Ihrer Website finden Sie die Identitätsübersicht. Jede Identität ist mit einem Namespace verknüpft.

![Kundenprofil](./images/identities.png)




Bei Adobe Experience Platform sind alle IDs gleich wichtig. Zuvor war die ECID die wichtigste ID im Adobe-Kontext und alle anderen IDs waren hierarchisch mit der ECID verknüpft. Bei Adobe Experience Platform ist dies nicht mehr der Fall, und jede ID kann als primäre Kennung betrachtet werden.

Normalerweise hängt die primäre Kennung vom Kontext ab. Wenn Sie Ihr Callcenter fragen: &quot;**ist die wichtigste ID?** sie wahrscheinlich antworten, **die Telefonnummer!** Wenn Sie Ihr CRM-Team fragen, wird es antworten: **Die E-Mail-Adresse!** Adobe Experience Platform versteht diese Komplexität und verwaltet sie für Sie. Jede Anwendung, unabhängig davon, ob es sich um eine Adobe-Anwendung oder eine Nicht-Adobe-Anwendung handelt, spricht mit Adobe Experience Platform, indem sie auf die ID verweist, die sie als primär betrachtet. Und es funktioniert einfach.

Wählen Sie für das Feld **Identity** die Option **ECID** und geben Sie für das Feld **Identitätswert** die ECID ein, die Sie im Bedienfeld Profil-Viewer der Bootcamp-Website finden. Klicken Sie **Anzeigen**. Anschließend wird Ihr Profil in der Liste angezeigt. Klicken Sie auf **Profil-ID**, um Ihr Profil zu öffnen.

![Kundenprofil](./images/popupecid.png)

Jetzt sehen Sie einen Überblick über einige wichtige **Profilattribute** Ihres Kundenprofils.

![Kundenprofil](./images/profile.png)

Navigieren Sie **Ereignisse**, wo Sie Einträge für jedes Erlebnisereignis sehen können, das mit Ihrem Profil verknüpft ist.

![Kundenprofil](./images/profileee.png)

Rufen Sie abschließend die Menüoption **Zielgruppenmitgliedschaft** auf. Sie sehen nun alle Zielgruppen, die sich für dieses Profil qualifizieren.

![Kundenprofil](./images/profileseg.png)

Erstellen wir nun eine neue Zielgruppe, mit der Sie das Kundenerlebnis für einen anonymen oder bekannten Kunden personalisieren können.

Nächster Schritt: [1.3 Zielgruppe erstellen - Benutzeroberfläche](./ex3.md)

[Zurück zu Benutzerfluss 1](./uc1.md)

[Zurück zu „Alle Module“](../../overview.md)

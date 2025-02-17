---
title: Foundation - Echtzeit-Kundenprofil - Visualisieren Ihres eigenen Echtzeit-Kundenprofils - Benutzeroberfläche
description: Foundation - Echtzeit-Kundenprofil - Visualisieren Ihres eigenen Echtzeit-Kundenprofils - Benutzeroberfläche
kt: 5342
doc-type: tutorial
exl-id: 66cb9b20-46e0-4b4a-af38-aa152bba342a
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 1%

---

# 2.1.2 Visualisieren Ihres eigenen Echtzeit-Kundenprofils - Benutzeroberfläche

In dieser Übung melden Sie sich bei Adobe Experience Platform an und zeigen in der Benutzeroberfläche Ihr eigenes Echtzeit-Kundenprofil an.

## Kontext

Im Echtzeit-Kundenprofil werden alle Profildaten zusammen mit Ereignisdaten sowie vorhandenen Segmentzugehörigkeiten angezeigt. Die angezeigten Daten können von überall stammen, aus Adobe-Programmen und externen Lösungen. Dies ist die leistungsfähigste Ansicht in Adobe Experience Platform, dem echten Erlebnissystem der Aufzeichnung.

## Verwenden der Kundenprofilansicht in Adobe Experience Platform

Zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](../../datacollection/dc1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``--aepSandboxName--``. Nach Auswahl der entsprechenden [!UICONTROL Sandbox] wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten [!UICONTROL Sandbox].

![Datenaufnahme](../../datacollection/dc1.2/images/sb1.png)

Gehen Sie im linken Menü zu **Profile** und zu **Durchsuchen**.

![Kundenprofil](./images/homemenu.png)

Im Bedienfeld Profil-Viewer auf Ihrer Website können Sie mehrere Identitäten finden. Jede Identität ist mit einem Namespace verknüpft.

![Kundenprofil](./images/identities.png)

Im Bedienfeld Profil-Viewer können Sie die folgenden Kombinationen aus IDs und Namespaces sehen:

| Identität | Namespace |
|:-------------:| :---------------:|
| Experience Cloud-ID (ECID) | 79943948563923140522865572770524243489 |
| Experience Cloud-ID (ECID) | 70559351147248820114888181867542007989 |
| E-Mail-ID | woutervangeluwe+18112024-01@gmail.com |
| Mobiltelefonnummer-ID | +32473622044+18112024-01 |

Bei Adobe Experience Platform sind alle IDs gleich wichtig. Zuvor war die ECID die wichtigste ID im Adobe-Kontext, und alle anderen IDs waren hierarchisch mit der ECID verknüpft. Bei Adobe Experience Platform ist dies nicht mehr der Fall, und jede ID kann als primäre Kennung betrachtet werden.

Normalerweise hängt die primäre Kennung vom Kontext ab. Wenn Sie Ihr Callcenter fragen: &quot;**ist die wichtigste ID?** sie wahrscheinlich antworten, **die Telefonnummer!** Wenn Sie aber Ihr CRM-Team fragen, wird es antworten, **die E-Mail-Adresse!** Adobe Experience Platform versteht diese Komplexität und verwaltet sie für Sie. Jede Anwendung, unabhängig davon, ob es sich um eine Adobe-Anwendung oder eine Nicht-Adobe-Anwendung handelt, spricht mit Adobe Experience Platform, indem sie auf die ID verweist, die sie als primär betrachtet. Und es funktioniert einfach.

Wählen Sie für das Feld **Identity** die Option **E-Mail** und geben Sie für das Feld **Identitätswert** die E-Mail-Adresse ein, mit der Sie sich in der vorherigen Übung registriert haben. Klicken Sie **Anzeigen**. Anschließend wird Ihr Profil in der Liste angezeigt. Klicken Sie auf **Profil-ID**, um Ihr Profil zu öffnen.

![Kundenprofil](./images/popupecid.png)

Jetzt sehen Sie einen Überblick über einige wichtige **Profilattribute** Ihres Kundenprofils. Um alle verfügbaren Profilattribute für Ihr Profil anzuzeigen, klicken Sie auf **Attribute**.

![Kundenprofil](./images/profile.png)

Anschließend wird eine vollständige Liste aller Attribute angezeigt.

![Kundenprofil](./images/profilattr.png)

Navigieren Sie **Ereignisse**, wo Sie Einträge für jedes Erlebnisereignis sehen können, das mit Ihrem Profil verknüpft ist.

![Kundenprofil](./images/profileee.png)

Rufen Sie abschließend die Menüoption **Zielgruppenmitgliedschaft** auf. Hier finden Sie alle qualifizierten Zielgruppen für diesen Kunden. Die Liste mag derzeit leer sein, aber das wird sich in den nächsten Modulen ändern.

![Kundenprofil](./images/profileseg.png)

Nachdem Sie nun gelernt haben, wie Sie das Echtzeit-Profil eines Kunden mithilfe der Benutzeroberfläche von Adobe Experience Platform anzeigen können, verwenden wir nun auch die APIs, indem wir Postman und Adobe I/O verwenden, um Abfragen nach den APIs von Adobe Experience Platform durchzuführen.

## Nächste Schritte

Navigieren Sie zu [2.1.3 Visualisieren Ihres eigenen Echtzeit-Kundenprofils - API](./ex3.md){target="_blank"}

Zurück zum [Echtzeit-Kundenprofil](./real-time-customer-profile.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}

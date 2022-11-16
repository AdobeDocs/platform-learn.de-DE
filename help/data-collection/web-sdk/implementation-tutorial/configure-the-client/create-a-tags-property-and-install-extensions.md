---
title: Erstellen einer Adobe Experience Platform-Tag-Eigenschaft und Installieren von Erweiterungen
description: Erstellen einer Adobe Experience Platform-Tag-Eigenschaft und Installieren von Erweiterungen
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
kt: 10447
hide: true
hidefromtoc: true
exl-id: 7403059f-b34c-48e0-9efe-b2db7a9afb27
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 2%

---

# Erstellen einer Adobe Experience Platform-Tag-Eigenschaft und Installieren von Erweiterungen

Jetzt, da der On-Page-Code Daten und Ereignisse in die Datenschicht pusht, ist es für den Marketing-Experten an der Zeit, die Daten aus der Datenschicht zu lesen und an Adobe Experience Platform zu senden. Dazu sind normalerweise zwei JavaScript-Bibliotheken erforderlich:

* Adobe Client-Datenschicht: In vorherigen Schritten haben Sie ein Datenschichtarray erstellt und Objekte in dieses eingefügt. Um auf Daten zugreifen zu können, müssen Sie die Adobe Client-Datenschicht-JavaScript-Bibliothek laden, die Möglichkeiten bietet, über Datenschichtänderungen und -ereignisse informiert zu werden, und darüber hinaus einfache Möglichkeiten zum Datenzugriff bietet.
* Adobe Experience Platform Web SDK: Diese JavaScript-Bibliothek kommuniziert mit dem Adobe Experience Platform Edge Network. Das SDK verarbeitet u. a. Identität, Einverständnis, Datenerfassung, Personalisierung, Zielgruppen und mehr.

Sie können diese einzelnen Bibliotheken zwar auf Ihre Website laden und sie direkt verwenden, es wird jedoch empfohlen, [Adobe Experience Platform Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de). Mit Tags können Sie ein einzelnes Skript in Ihre HTML einbetten und die Tags-Benutzeroberfläche verwenden, um sowohl die Adobe Client-Datenschicht als auch das Adobe Experience Platform Web SDK bereitzustellen. Mit Tags können Sie unter anderem auch Regeln zum Senden von Daten erstellen. In diesem Tutorial werden Tags zu diesem Zweck verwendet. Es wird davon ausgegangen, dass Sie über grundlegende Kenntnisse der Funktionsweise von Tags verfügen.

## Erstellen einer Eigenschaft innerhalb von Tags

Wenn Sie das noch nicht getan haben, [Erstellen einer Eigenschaft in Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/companies-and-properties.html#create-or-configure-a-property).

## Installieren der Adobe Client-Datenschichterweiterung

Installieren Sie die Adobe Client-Datenschichterweiterung, indem Sie zum Erweiterungskatalog navigieren, die Erweiterung suchen und auf das entsprechende klicken [!UICONTROL Installieren] Schaltfläche. Es sollte ein Konfigurationsbildschirm angezeigt werden.

![Installation der Adobe Client-Datenschicht-Erweiterung](../../../assets/implementation-strategy/acdl-extension-installation.png)

Für dieses Tutorial müssen die Standardwerte nicht geändert werden. Klicken Sie auf [!UICONTROL Speichern].

## Adobe Experience Platform Web SDK-Erweiterung installieren

Installieren Sie als Nächstes die Adobe Experience Platform Web SDK-Erweiterung, indem Sie die Erweiterung im Erweiterungskatalog suchen und auf die entsprechende [!UICONTROL Installieren] Schaltfläche. Es sollte ein Konfigurationsbildschirm angezeigt werden.

![Installation der Adobe Experience Platform Web SDK-Erweiterung](../../../assets/implementation-strategy/web-sdk-extension-installation.png)

In [Erstellen eines Datenspeichers](../configure-the-server/create-a-datastream.md), haben Sie einen Datastream erstellt, auf den das Adobe Experience Platform Edge Network verweist, um zu bestimmen, wohin Ihre eingehenden Daten gesendet werden sollen. Bei Anfragen vom Adobe Experience Platform Web SDK an Edge Network müssen Sie angeben, auf welchen Datastream Edge Network verwiesen werden soll.

Suchen Sie dazu die [!UICONTROL Datastream] und wählen Sie den zuvor erstellten Datastream aus. Ihnen werden dieselben Datastream-Umgebungen angezeigt, in denen Sie [Erstellen eines Datenspeichers](../configure-the-server/create-a-datastream.md).

![Datenspeicherauswahl](../../../assets/implementation-strategy/web-sdk-datastream-selection.png)

Wie in [Erstellen eines Datenspeichers](../configure-the-server/create-a-dataset.md), haben diese Datensatzumgebungen eine Beziehung zu Tags-Umgebungen. Nehmen Sie an, dass Sie die Installation der Adobe Experience Platform Web SDK-Erweiterung abgeschlossen haben, erstellen Sie eine Tag-Bibliothek mit der Erweiterung und veröffentlichen Sie die Bibliothek dann in einer Tags-Entwicklungsumgebung. Wenn die Tag-Bibliothek auf Ihre Web-Seite geladen wird und die Adobe Experience Platform Web SDK-Erweiterung eine Anfrage an Edge Network sendet, enthält die Erweiterung die [!UICONTROL Entwicklungsumgebung] datastream-Umgebungs-ID. Edge Network verwendet diese ID wiederum, um die Konfiguration der [!UICONTROL Entwicklungsumgebung] Datastream-Umgebung und Weiterleiten von Daten an die entsprechenden Adobe-Produkte.

Derzeit gibt es nur eine Entwicklungs-Datastream-Umgebung, eine Staging-Datastream-Umgebung und eine Produktions-Datastream-Umgebung. Aus diesem Grund zeigt die Benutzeroberfläche der Erweiterungskonfiguration alle vorab ausgewählten und unveränderlichen Elemente an. Es ist jedoch möglich, mithilfe der Benutzeroberfläche von datastream mehrere Datastream-Entwicklungsumgebungen (eine für Sie und eine für Ihren Kollegen) zu erstellen. Wenn Sie über mehrere Entwicklungs-Datastream-Umgebungen verfügen, können Sie auswählen, welche Sie für diese Tag-Eigenschaft verwenden möchten.

Scrollen Sie abschließend nach unten und deaktivieren Sie [!UICONTROL Aktivieren der Klickdatenerfassung]. Standardmäßig verfolgt das SDK automatisch Links für Sie. In diesem Tutorial zeigen wir jedoch, wie Sie Ihre eigenen Link-Klicks mithilfe von benutzerspezifischen Linkinformationen verfolgen können.

Klicken Sie auf [!UICONTROL Speichern] Schaltfläche zum Abschließen der Installation der Adobe Experience Platform Web SDK-Erweiterung.

Die entsprechenden Erweiterungen wurden installiert. Es ist Zeit, Regeln und Datenelemente zu erstellen.

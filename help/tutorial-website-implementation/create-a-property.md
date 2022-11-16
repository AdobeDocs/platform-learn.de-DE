---
title: Erstellen Sie eine Tag-Eigenschaft
description: Erfahren Sie, wie Sie sich bei der Datenerfassungsoberfläche anmelden und eine Tag-Eigenschaft erstellen. Diese Lektion ist Teil des Tutorials zum Implementieren des Experience Cloud in Websites .
exl-id: f83d374a-a831-4598-b9d3-6f183224b589
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 61%

---

# Erstellen Sie eine Tag-Eigenschaft

In dieser Lektion erstellen Sie Ihre erste Tag-Eigenschaft.

Eine Eigenschaft ist im Wesentlichen ein Container, den Sie bei der Bereitstellung von Tags auf Ihrer Site mit Erweiterungen, Regeln, Datenelementen und Bibliotheken füllen.

## Voraussetzungen

Um die nächsten Lektionen abzuschließen, müssen Sie über die Berechtigung zum Entwickeln, Genehmigen, Veröffentlichen, Verwalten von Erweiterungen und Verwalten von Umgebungen in Tags verfügen. Wenn Sie einen dieser Schritte nicht ausführen können, weil die Optionen in der Benutzeroberfläche nicht verfügbar sind, wenden Sie sich an Ihren Experience Cloud-Administrator, um den Zugriff anzufordern. Weitere Informationen zu Tag-Benutzerberechtigungen finden Sie unter [die Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html?lang=de).

>[!NOTE]
>
>Adobe Experience Platform Launch wird als eine Suite von Datenerfassungstechnologien in Adobe Experience Platform integriert. In der Benutzeroberfläche wurden verschiedene terminologische Änderungen eingeführt, die Sie bei der Verwendung dieses Inhalts beachten sollten:
>
> * platform launch (Client-seitig) ist jetzt **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)**
> * platform launch Server Side ist jetzt **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)**
> * Edge-Konfigurationen sind jetzt verfügbar **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de)**


## Lernziele

Am Ende dieser Lektion können Sie:

* Melden Sie sich bei der Benutzeroberfläche der Datenerfassung an
* Neue Tag-Eigenschaft erstellen
* Tag-Eigenschaft konfigurieren

## Navigieren Sie zur Datenerfassungsoberfläche

**So gelangen Sie zur Datenerfassung**

1. Melden Sie sich bei [Adobe Experience Cloud](https://experiencecloud.adobe.com) an.

1. Klicken Sie auf ![Symbol für Lösungsschalter](images/launch-solutionSwitcher.png) Symbol zum Öffnen des App-Umschalters

1. Auswählen **[!UICONTROL Launch/Datenerfassung]** aus dem Menü ![Öffnen Sie den Lösungsschalter über das Symbol und klicken Sie auf &quot;Launch/Data Collection&quot;](images/launch-solutionSwitcherActivation.png)

Hierdurch sollte der Bildschirm `Tags Properties` angezeigt werden (wenn keine Eigenschaften im Konto erstellt wurden, ist dieser Bildschirm möglicherweise leer):

![Eigenschaftenbildschirm](images/launch-propertiesScreen.png)

## Erstellen einer Eigenschaft

Eine Eigenschaft ist im Wesentlichen ein Container, den Sie bei der Bereitstellung von Tags auf Ihrer Site mit Erweiterungen, Regeln, Datenelementen und Bibliotheken füllen. Es kann sich bei einer Eigenschaft um eine beliebige Gruppierung einer oder mehrerer Domains bzw. Subdomains handeln. Sie können diese Assets auf ähnliche Weise verwalten und verfolgen. Angenommen, Sie haben mehrere Websites, die auf einer Vorlage basieren, und Sie möchten auf all diesen Websites dieselben Assets verfolgen. Sie können eine Eigenschaft auf mehrere Domänen anwenden. Weitere Informationen zum Erstellen von Eigenschaften finden Sie unter [„Unternehmen und Eigenschaften“](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/companies-and-properties.html) in der Produktdokumentation.

**Erstellen einer Eigenschaft**

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Neue Eigenschaft]**:

   ![Klicken Sie auf „Neue Eigenschaft“](images/launch-addNewProperty.png)

1. Benennen Sie Ihre Eigenschaft (z. B. `Luma Tutorial` oder `Luma Tutorial - Daniel`).
1. Geben Sie `enablementadobe.com` als Domain ein, da dies die Domain ist, in der die Demosite „Luma“ gehostet wird. Obwohl das Feld &quot;Domäne&quot;erforderlich ist, funktioniert die Tag-Eigenschaft in jeder Domäne, in der sie implementiert ist. Der Hauptzweck dieses Felds ist die Vorbelegung von Menüpunkten im Regel-Builder.
1. Erweitern Sie die **[!UICONTROL Erweiterte Optionen]** und aktivieren Sie das Kontrollkästchen **[!UICONTROL Regelkomponenten nacheinander ausführen]**
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]**.

   ![Eine neue Eigenschaft erstellen](images/launch-newProperty.png)

Ihre neue Eigenschaft sollte auf der Eigenschaftsseite angezeigt werden. Beachten Sie Folgendes: Wenn Sie das Kontrollkästchen neben dem Eigenschaftennamen aktivieren, werden Optionen zum **[!UICONTROL Konfigurieren]** oder **[!UICONTROL Löschen]** der Eigenschaft oberhalb der Eigenschaftsliste angezeigt. Klicken Sie auf den Namen Ihrer Eigenschaft (z. B. `Luma Tutorial`), um den `Overview` Bildschirm zu öffnen.
![Klicken Sie auf den Namen der Eigenschaft, um sie zu öffnen](images/launch-openProperty.png)

[Weiter mit &quot;Hinzufügen des Einbettungscodes&quot;>](add-embed-code.md)

---
title: Erste Schritte mit Adobe Commerce as a Cloud Service
description: Erste Schritte mit Adobe Commerce as a Cloud Service
kt: 5342
doc-type: tutorial
source-git-commit: 28553f8042be7bfc0b553272a6c72e6677fe1cb3
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 16%

---

# 1.5.1 Erste Schritte mit Adobe Commerce as a Cloud Service

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Stellen Sie sicher, dass Sie sich in der richtigen Umgebung befinden, die `--aepImsOrgName--` benannt werden sollte. Auf **Commerce**.

![AEM Assets](./images/accs1.png)

## 1.5.1.1 ACS-Instanz erstellen

Sie sollten das dann sehen. Klicken Sie auf **+ Instanz**.

![AEM Assets](./images/accs2.png)

Füllen Sie die Felder wie folgt aus:

- **Instanzname**: `--aepUserLdap-- - ACCS`
- **Umgebung**: `Sandbox`
- **Region**: `North America`

Klicken Sie **Instanz hinzufügen**.

![AEM Assets](./images/accs3.png)

Ihre Instanz wird jetzt erstellt. Dies kann 5 bis 10 Minuten dauern.

![AEM Assets](./images/accs4.png)

Sobald die Instanz fertig ist, klicken Sie auf Ihre Instanz, um sie zu öffnen.

![AEM Assets](./images/accs5.png)

## 1.5.1.2 Einrichten des CitiSignal-Shops

Sie sollten das dann sehen. Klicken Sie **Mit Adobe ID anmelden** und melden Sie sich an.

![AEM Assets](./images/accs6.png)

Sobald Sie eingeloggt sind, sollten Sie diese Homepage sehen. Der erste Schritt besteht darin, Ihren CitiSignal-Store in Commerce einzurichten. Klicken Sie auf **Stores**.

![AEM Assets](./images/accs7.png)

Klicken Sie auf **Alle Stores**.

![AEM Assets](./images/accs8.png)

Klicken Sie **Website erstellen**.

![AEM Assets](./images/accs9.png)

Füllen Sie die Felder wie folgt aus:

- **Name**: `CitiSignal`
- **Code**: `citisignal`

Klicken Sie **Website speichern**.

![AEM Assets](./images/accs10.png)

Dann solltest du wieder hier sein. Klicken Sie **Store erstellen**.

![AEM Assets](./images/accs11.png)

Füllen Sie die Felder wie folgt aus:

- **Website**: `CitiSignal`
- **Name**: `CitiSignal`
- **Code**: `citisignal`
- **Stammkategorie**: `Default Category`

Klicken Sie **Speichern**.

![AEM Assets](./images/accs12.png)

Dann solltest du wieder hier sein. Klicken Sie **Store-Ansicht erstellen**.

![AEM Assets](./images/accs13.png)

Füllen Sie die Felder wie folgt aus:

- **Store**: `CitiSignal`
- **Name**: `CitiSignal`
- **Code**: `citisignal`
- **Status**: `Enabled`

Klicken Sie **Store-Ansicht speichern**.

![AEM Assets](./images/accs14.png)

Sie sollten dann diese Meldung sehen. Klicken Sie auf **OK**.

![AEM Assets](./images/accs15.png)

Dann solltest du wieder hier sein.

![AEM Assets](./images/accs16.png)

## Kategorien und Produkte 1.5.1.3 konfigurieren

Navigieren Sie zu **Katalog** und wählen Sie dann **Kategorien** aus.

![AEM Assets](./images/accs17.png)

Wählen Sie **Standardkategorie** und klicken Sie dann auf **Unterkategorie hinzufügen**.

![AEM Assets](./images/accs18.png)

Geben Sie den `Phones` ein und klicken Sie dann auf **Speichern**.

![AEM Assets](./images/accs19.png)

Wählen Sie **Standardkategorie** und klicken Sie erneut **Unterkategorie**.

![AEM Assets](./images/accs20.png)

Geben Sie den `Watches` ein und klicken Sie dann auf **Speichern**.

![AEM Assets](./images/accs21.png)

Anschließend sollten zwei Kategorien erstellt werden.

![AEM Assets](./images/accs22.png)

Gehen Sie dann zu **Katalog** und wählen Sie **Produkte** aus.

![AEM Assets](./images/accs23.png)

Sie sollten das dann sehen. Klicken Sie **Produkt hinzufügen**.

![AEM Assets](./images/accs24.png)

Konfigurieren Sie Ihr Produkt wie folgt:

- **Produktname**: `iPhone Air`
- **SKU**: `iPhone-Air`
- **Preis**: `999`
- **Menge**: `10000`
- **Kategorien**: `Phones` auswählen

Klicken Sie auf **Speichern**.

![AEM Assets](./images/accs25.png)

Scrollen Sie nach unten zu **Konfigurationen** und klicken Sie auf **Konfigurationen erstellen**.

![AEM Assets](./images/accs26.png)

Sie sollten das dann sehen. Klicken Sie **Neues Attribut erstellen**.

![AEM Assets](./images/accs27.png)

Legen Sie die **Standardbeschriftung** auf `Storage` fest und klicken Sie dann auf **Option hinzufügen** unter **Optionen verwalten**.

![AEM Assets](./images/accs28.png)

Konfigurieren Sie die erste Option mit dem in allen 3 Spalten `256GB` Namen und klicken Sie dann erneut **Option hinzufügen**.

![AEM Assets](./images/accs29.png)

Konfigurieren Sie die zweite Option mit dem in allen 3 Spalten `512GB` Namen und klicken Sie dann erneut **Option hinzufügen**.

![AEM Assets](./images/accs30.png)

Konfigurieren Sie die dritte Option mit dem in allen 3 Spalten `1TB` Namen und klicken Sie dann erneut **Option hinzufügen**.

![AEM Assets](./images/accs31.png)

Scrollen Sie nach unten zu **Storefront-Eigenschaften**. Legen Sie die folgenden Optionen auf &quot;**&quot;**:

- **Bei der Suche verwenden**
- **HTML-Tags in der Storefront zulassen**
- **Auf Katalogseiten in der Storefront sichtbar**
- **Verwendung in der Produktliste**

![AEM Assets](./images/accs32.png)

Scrollen Sie nach oben und klicken Sie auf **Attribut speichern**.

![AEM Assets](./images/accs33.png)

Sie sollten das dann sehen. Wählen Sie beide Attribute für **color** und **storage** aus und klicken Sie auf **Weiter**.

![AEM Assets](./images/accs34.png)

Sie sollten das dann sehen. Jetzt müssen Sie die verfügbaren Farboptionen hinzufügen. Klicken Sie dazu auf &quot;**Wert erstellen**.

![AEM Assets](./images/accs35.png)

Geben Sie den Wert `Sky-Blue` ein und klicken Sie auf **Neuen Wert erstellen**.

![AEM Assets](./images/accs36.png)

Geben Sie den Wert `Light-Gold` ein und klicken Sie auf **Neuen Wert erstellen**.

![AEM Assets](./images/accs37.png)

Geben Sie den Wert `Cloud-White` ein und klicken Sie auf **Neuen Wert erstellen**.

![AEM Assets](./images/accs38.png)

Geben Sie den Wert `Space-Black` ein. Klicken Sie **Alle auswählen**

![AEM Assets](./images/accs39.png)

Wählen Sie alle drei Optionen unter **&#x200B;**&#x200B;aus und klicken Sie auf **Weiter**.

![AEM Assets](./images/accs40.png)

Behalten Sie die Standardeinstellungen bei und klicken Sie auf **Weiter**.

![AEM Assets](./images/accs41.png)

Sie sollten das dann sehen. Klicken Sie **Produkte generieren**.

![AEM Assets](./images/accs42.png)

Klicken Sie auf **Speichern**.

![AEM Assets](./images/accs43.png)

Scrollen Sie nach unten **Produkt in Websites** und aktivieren Sie das Kontrollkästchen für **CitiSignal**.

Klicken Sie auf **Speichern**.

![AEM Assets](./images/accs44.png)

Klicken Sie auf **Bestätigen**.

![AEM Assets](./images/accs45.png)

Sie sollten das dann sehen. Klicken Sie auf **Zurück**.

![AEM Assets](./images/accs46.png)

Jetzt sehen Sie das Produkt **iPhone Air** und seine Varianten im Produktkatalog.

![AEM Assets](./images/accs47.png)


Nächster Schritt: [Verbinden von ACCS mit der AEM Sites CS/EDS-Storefront](./ex2.md){target="_blank"}

Zurück zu [Adobe Commerce as a Cloud Service](./accs.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}

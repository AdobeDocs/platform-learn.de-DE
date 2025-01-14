---
title: Erstellen eines Variablen-Datenelements
description: Fügen Sie ein Datenelement hinzu, das über mehrere Regeln aufgebaut, dann an das Edge Network gesendet und an Adobe Analytics weitergeleitet wird
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-16759
source-git-commit: 7ae56d997884cf1558e72c0ad553df1c5d43c081
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---


# Erstellen eines Variablen-Datenelements

Fügen Sie ein Datenelement hinzu, das anhand mehrerer Regeln erstellt, dann an das Edge Network gesendet und an Adobe Analytics weitergeleitet wird.

Dieses Datenelement erstellt das „Daten“-Objekt, mit dem Adobe Analytics-Variablen (Props, eVars, Ereignisse usw.) zurück an Adobe Analytics und Adobe Target übergeben werden. Genau wie beim Aufbau des „s-Objekts“ in einer AppMeasurement-Implementierung in Analytics erstellen wir also diesen Typ: Variablenobjekt, auf das über Regeln hinweg zugegriffen werden kann und das über Regeln hinweg aktualisiert werden kann, und es kann verwendet werden, um Props und eVars in Analytics zu befüllen.

1. Klicken Sie in der Datenerfassungsoberfläche im **Navigationsbereich auf** Datenelemente“.

   Sie gelangen zur Landingpage für Datenelemente, auf der alle bereits vorhandenen Datenelemente angezeigt werden. Wir müssen ein neues Datenelement erstellen, um die Migration zu erleichtern. Klicken Sie **Datenelement hinzufügen**.

   ![Datenelement hinzufügen](assets/add-new-data-alement.jpg)

1. Konfigurieren Sie Ihr Datenelement.
   1. Benennen Sie Ihr Datenelement nach Belieben, damit Sie sich daran erinnern können, dass dies die Daten auf Ihrer Seite aufbaut und dass dies der Typ „Variable“ ist. Für dieses Tutorial nennen wir es **Seitenansichts-Datenvariable**.
   1. Wählen Sie **Adobe Experience Platform Web SDK** aus der Dropdown-Liste Erweiterung aus.
   1. Wählen Sie **Variable** aus der **Datenelementtyp** Dropdown-Liste aus.
   1. Wählen Sie im rechten Bedienfeld das Optionsfeld **Daten** aus.
   1. Überprüfen Sie die **Adobe Analytics**-Lösung und eine der anderen Lösungen, die Sie ebenfalls migrieren, z. B. **Adobe Target**, die in diesem Screenshot angezeigt werden.
1. Klicken Sie auf **Speichern**.

   ![Konfigurieren eines Datenelements für Variablen](assets/configure-variable-data-element.jpg)

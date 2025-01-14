---
title: Erstellen einer Report Suite für die Validierung
description: Erstellen Sie eine Report Suite in Adobe Analytics, mit der Sie Web-SDK-Daten überprüfen können, während Sie Ihre Site(s) von der alten Implementierung migrieren.
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-16756
source-git-commit: 7ae56d997884cf1558e72c0ad553df1c5d43c081
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Erstellen einer Report Suite für die Validierung

Erstellen Sie eine Report Suite in Adobe Analytics, mit der Sie Web-SDK-Daten überprüfen können, während Sie Ihre Site(s) von der alten Implementierung migrieren.

Je nach Größe und Komplexität Ihrer Analytics-Implementierung kann die Migration zur Web-SDK einige Zeit dauern. Während dieser Zeit sollten Sie Ihre Arbeit überprüfen und sicherstellen, dass die Daten korrekt in Adobe Analytics-Berichte fließen. Anstatt diese Daten zusammen mit Produktionsdaten oder sogar mit anderen Entwicklungsdaten in eine Report Suite zu übertragen, empfiehlt es sich, eine neue Report Suite zu erstellen, die Sie für diese Migration verwenden können. In der nächsten Lektion erstellen und konfigurieren wir neue „Datenströme“ für Entwicklung, Staging und Produktion. Dabei müssen wir die Report Suite-ID für die Konfiguration kennen.

## Erstellen der neuen Report Suite

1. Öffnen Sie Adobe Analytics und navigieren Sie zu **Report Suite**-Einstellungen in der Admin Console

   ![Admin Console ](assets/aa-admin-console.jpg).

1. Wählen Sie **[!UICONTROL Report Suite hinzufügen]**

   ![Report Suite hinzufügen](assets/add-report-suite.jpg)

1. Füllen Sie das Formular aus, um eine neue Report Suite zu erstellen. Obwohl Sie die neue Report Suite aus einer Vorlage erstellen können, selbst wenn es sich um eine leere Vorlage handelt, ist es wahrscheinlich besser, die Option **Duplizieren einer vorhandenen Report Suite** zu wählen und Ihre Report Suite auszuwählen, die Sie zu Web SDK migrieren. Auf diese Weise können Sie dieselben Namen und Einstellungen verwenden, wie Sie Ihre neu migrierten Daten testen, was die Validierung während des Vorgangs erleichtert. Füllen Sie alle erforderlichen Felder aus und speichern Sie Ihre neue Migration Development Report Suite.

   ![Neue Report Suite zur Migrationsentwicklung](assets/new-websdk-validation-report-suite.jpg)

1. Notieren Sie sich die ID Ihrer neuen Report Suite, da Sie sie in der nächsten Lektion benötigen werden, wenn Sie Datenströme für die Implementierung von Web SDK einrichten. Der Website-Titel sollte auch nicht vergessen werden, da Sie ihn in Analysis Workspace verwenden können, um die Report Suite zur Migrationsentwicklung in Ihrem Analytics-Projekt auszuwählen.

>[!TIP]
>
>Eine Videoeinführung zum Erstellen von Report Suites finden Sie unter [Grundlagen und Erstellen von Report Suites](https://experienceleague.adobe.com/en/docs/analytics-learn/tutorials/intro-to-analytics/analytics-basics/understanding-and-creating-report-suites){target="_blank"}.


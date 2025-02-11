---
title: Erste Schritte mit AJO-Übersetzungs-Services
description: Erste Schritte mit AJO-Übersetzungs-Services
kt: 5342
doc-type: tutorial
exl-id: 28c925dd-8a7b-4b9a-a128-ecbfbfbeaf04
source-git-commit: 7438a1289689c5c3fb3deb398aa9898d7ac26cf8
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 5%

---

# 3.5.1 Übersetzungsdienstleister

## 3.5.1.1 Konfigurieren des Microsoft Azure-Übersetzers

Navigieren Sie zu [https://portal.azure.com/#home](https://portal.azure.com/#home).

![Übersetzungen](./images/transl1.png)

Geben Sie in der Suchleiste `translators` ein. Klicken Sie dann auf **+ Erstellen**.

![Übersetzungen](./images/transl2.png)

Wählen Sie **Übersetzer erstellen** aus.

![Übersetzungen](./images/transl3.png)

Wählen Sie Ihre **Abonnement-ID** und **Ressourcengruppe**.
Legen Sie **Region** auf **Global** fest.
Setzen Sie **Preisstufe** auf **Kostenlos F0**.

Wählen Sie **Überprüfen + Erstellen** aus.

![Übersetzungen](./images/transl4.png)

Wählen Sie **Erstellen** aus.

![Übersetzungen](./images/transl5.png)

Wählen Sie **Zu Ressource wechseln** aus.

![Übersetzungen](./images/transl6.png)

Wechseln Sie im linken Menü zu **Ressourcenverwaltung** > **Schlüssel und Endpunkt**. Klicken, um den Schlüssel zu kopieren.

![Übersetzungen](./images/transl7.png)

## 3.5.1.2-Wörterbuch

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/). Auf **Journey Optimizer**.

![Übersetzungen](./images/ajolp1.png)

Gehen Sie im linken Menü zu **Übersetzungen** und dann zu **Gebietsschema-Wörterbuch**. Wenn Sie diese Meldung sehen, klicken Sie auf **Standardgebietsschema hinzufügen**.

![Übersetzungen](./images/locale1.png)

Sie sollten das dann sehen.

![Übersetzungen](./images/locale2.png)

## Konfigurieren 3.5.1.3 Übersetzungsanbieters in AJO

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/). Auf **Journey Optimizer**.

![Übersetzungen](./images/ajolp1.png)

Gehen Sie im linken Menü zu **Übersetzungen** und dann zu **Anbieter**. Klicken Sie **Anbieter hinzufügen**.

![Übersetzungen](./images/transl8.png)

Wählen **unter &quot;**&quot; die Option **Microsoft Translator** aus. Aktivieren Sie das Kontrollkästchen, um die Verwendung des Übersetzungsanbieters zu aktivieren. Fügen Sie den Schlüssel ein, den Sie aus Microsoft Azure Translators kopiert haben. Klicken Sie dann auf **Anmeldedaten überprüfen**.

![Übersetzungen](./images/transl9.png)

Ihre Anmeldedaten sollten dann erfolgreich validiert werden. Wenn dies der Fall ist, scrollen Sie nach unten, um die zu übersetzenden Sprachen auszuwählen.

![Übersetzungen](./images/transl10.png)

Stellen Sie sicher, dass Sie `[en-US] English`, `[es] Spanish`, `[fr] French`, `[nl] Dutch` auswählen.

![Übersetzungen](./images/transl11.png)

Scrollen Sie nach oben und klicken Sie auf **Speichern**.

![Übersetzungen](./images/transl12.png)

Ihr **Übersetzungsanbieter** kann jetzt verwendet werden.

![Übersetzungen](./images/transl13.png)

## 3.5.1.4 Konfigurieren von Übersetzungsprojekten

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/). Auf **Journey Optimizer**.

![Übersetzungen](./images/ajolp1.png)

Gehen Sie im linken Menü zu **Übersetzungen** und dann zu **Gebietsschema-Wörterbuch**. Wenn Sie diese Meldung sehen, klicken Sie auf **Projekt erstellen**.

![Übersetzungen](./images/ajoprovider1.png)

Geben Sie den Namen `--aepUserLdap-- - Translations` ein, legen Sie das **Source-Gebietsschema** auf `[en-US] English - United States` fest und aktivieren Sie die Kontrollkästchen, um sowohl **genehmigte Übersetzungen automatisch veröffentlichen** als auch **Überprüfungs-Workflow aktivieren**. Klicken Sie anschließend auf **+ Gebietsschema hinzufügen**.

![Übersetzungen](./images/ajoprovider1a.png)

Suchen Sie nach `fr`, aktivieren Sie das Kontrollkästchen für `[fr] French` und aktivieren Sie dann das Kontrollkästchen für **Microsoft Translator**. Klicken Sie auf **+ Gebietsschema hinzufügen**.

![Übersetzungen](./images/ajoprovider2.png)

Suchen Sie nach `es`, aktivieren Sie das Kontrollkästchen für `[es] Spanish` und aktivieren Sie dann das Kontrollkästchen für **Microsoft Translator**. Klicken Sie auf **+ Gebietsschema hinzufügen**.

![Übersetzungen](./images/ajoprovider3.png)

Suchen Sie nach `nl`, aktivieren Sie das Kontrollkästchen für `[nl] Spanish` und aktivieren Sie dann das Kontrollkästchen für **Microsoft Translator**. Klicken Sie auf **+ Gebietsschema hinzufügen**.

![Übersetzungen](./images/ajoprovider6.png)

Klicken Sie auf **Speichern**.

![Übersetzungen](./images/ajoprovider8.png)

Ihr **Übersetzungen**-Projekt kann jetzt verwendet werden.

![Übersetzungen](./images/ajoprovider9.png)

## 3.5.1.5 Spracheinstellungen konfigurieren

Navigieren Sie **Kanäle** > **Allgemeine Einstellungen** > **Spracheinstellungen**. Klicken Sie **Spracheinstellungen erstellen**.

![Journey Optimizer](./images/camploc6.png)

Verwenden Sie den Namen `--aepUserLdap--_translations`. Wählen Sie **Übersetzungsprojekt** aus. Klicken Sie dann auf das Symbol **Bearbeiten**.

![Journey Optimizer](./images/camploc7.png)

Wählen Sie das Übersetzungsprojekt aus, das Sie im vorherigen Schritt erstellt haben. Klicken Sie auf **Auswählen**.

![Journey Optimizer](./images/camploc8.png)

Sie sollten das dann sehen. Legen Sie die **Fallback-Voreinstellung** auf **Englisch - Vereinigte Staaten** fest. Klicken Sie auf **Bevorzugtes Attribut Profilsprache auswählen**, um zu entscheiden, welches Feld aus dem Kundenprofil zum Laden der Übersetzungen verwendet werden soll. Klicken Sie dann auf **Bearbeiten**, um das zu verwendende Feld auszuwählen.

![Journey Optimizer](./images/camploc9.png)

Geben Sie **Suchleiste „Bevorzugte**&quot; ein und wählen Sie dann das Feld **Bevorzugte Sprache** aus.

![Journey Optimizer](./images/camploc10.png)

Klicken Sie auf das **Bearbeiten**-Symbol für **Englisch - Vereinigte Staaten** und **Niederländisch**, um die Konfiguration zu überprüfen.

![Journey Optimizer](./images/camploc11.png)

Hier finden Sie die Konfiguration für **Englisch - Vereinigte Staaten**. Klicken Sie **Abbrechen**.

![Journey Optimizer](./images/camploc12.png)

Klicken Sie, um die Konfiguration für **Niederländisch“**. Klicken Sie **Abbrechen**.

![Journey Optimizer](./images/camploc13.png)

Scrollen Sie nach oben und klicken Sie auf **Absenden**.

![Journey Optimizer](./images/camploc14.png)

Ihre Spracheinstellungen sind jetzt konfiguriert.

![Journey Optimizer](./images/camploc15.png)

Du hast diese Übung beendet.

## Nächste Schritte

Wechseln Sie zu [3.5.2 Kampagne erstellen](./ex2.md)

Zurück zu [Modul 3.5](./ajotranslationsvcs.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}

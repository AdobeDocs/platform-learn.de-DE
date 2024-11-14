---
title: Erste Schritte - Installieren der Chrome-Erweiterung für die Experience League-Dokumentation
description: Erste Schritte - Installieren der Chrome-Erweiterung für die Experience League-Dokumentation
kt: 5342
doc-type: tutorial
exl-id: da7aa686-7f25-49fd-af3e-d243ffda025f
source-git-commit: 7f436f77ab6d7c625181304fd41be75c627c5b46
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 0%

---

# Installieren der Chrome-Erweiterung für die Experience League-Dokumentation

## Über die Chrome-Erweiterung

Die Dokumentation wurde allgemein gehalten, damit sie von jedem mithilfe einer beliebigen Adobe Experience Platform-Instanz problemlos wiederverwendet werden kann.
Damit die Dokumentation wiederverwendet werden kann, wurden **Umgebungsvariablen** in die Dokumentation eingeführt. Das bedeutet, dass Sie die folgenden **Platzhalter** in der Dokumentation finden. Jeder Platzhalter ist eine spezifische Variable für eine bestimmte Umgebung. Die Chrome-Erweiterung ändert diese Variable, damit Sie Code und Text aus den Anleitungsseiten einfach kopieren und in die verschiedenen Benutzeroberflächen einfügen können, die Sie im Rahmen des Tutorials verwenden werden.

Ein Beispiel für solche Werte finden Sie unten. Derzeit können diese Werte noch nicht verwendet werden. Sobald Sie die Chrome-Erweiterung installieren und aktivieren, sehen Sie, dass sich diese Variablen in normalen Text ändern, den Sie kopieren und wiederverwenden können.

| Name | Schlüssel |
|:-------------:| :---------------:|
| Kennung der IMS-Organisation von AEP | `--aepImsOrgId--` |
| AEP-Mandanten-ID | `--aepTenantId--` |
| AEP-Sandbox-Name | `--aepSandboxName--` |
| LDAP des Lernprofils | `--aepUserLdap--` |

Im folgenden Screenshot sehen Sie beispielsweise einen Verweis auf `aepTenantId`.

![DSN](./images/mod7before.png)

Sobald die Erweiterung installiert ist, wird derselbe Text automatisch geändert, um Ihre instanzspezifischen Werte widerzuspiegeln.

![DSN](./images/mod7.png)

## Installieren der Chrome-Erweiterung

Um diese Chrome-Erweiterung zu installieren, öffnen Sie den Chrome-Browser und navigieren Sie zu: [https://chromewebstore.google.com/detail/tech-insiders-learning-fo/hhnbkfgioecmhimdhooigajdajplinfi](https://chromewebstore.google.com/detail/tech-insiders-learning-fo/hhnbkfgioecmhimdhooigajdajplinfi). Dann wirst du das sehen.

Klicken Sie auf **Zu Chrome hinzufügen**.

![DSN](./images/c2.png)

Dann wirst du das sehen. Klicken Sie auf **Erweiterung hinzufügen**.

![DSN](./images/c3.png)

Die Erweiterung wird dann installiert und Sie erhalten eine ähnliche Benachrichtigung.

![DSN](./images/c4.png)

Klicken Sie im Menü **Erweiterungen** auf das Symbol **Puzzleteil** und veröffentlichen Sie die Erweiterung **Plattform-Lernen - Konfiguration** im Erweiterungsmenü.

![DSN](./images/c6.png)

## Konfigurieren der Chrome-Erweiterung

Wechseln Sie zu [https://experienceleague.adobe.com/en/docs/platform-learn/tutorial-comprehensive-technical/overview](https://experienceleague.adobe.com/en/docs/platform-learn/tutorial-comprehensive-technical/overview) und klicken Sie auf das Symbol für die Erweiterung, um es zu öffnen.

![DSN](./images/tuthome.png)

Dann sehen Sie dieses Popup. Klicken Sie auf das Symbol **+**.

![DSN](./images/c7.png)

Geben Sie die unten angegebenen Werte ein, die sich alle auf Ihre Adobe Experience Platform-Instanz beziehen.

![DSN](./images/c8.png)

Wenn Sie nicht sicher sind, welche Werte für diese Felder eingegeben werden sollen, folgen Sie der nachstehenden Anleitung.

**AEP IMS-Organisationsname**

Wenn Sie sich auf [https://platform.adobe.com/](https://platform.adobe.com/) bei Ihrer Adobe Experience Platform-Instanz anmelden, finden Sie den Namen Ihrer Instanz in der oberen rechten Ecke Ihres Bildschirms.

![DSN](./images/aepname.png)

**AEP IMS-Organisations-ID**

Die IMS-Organisations-ID ist die eindeutige Kennung für Ihre Adobe Experience Cloud-Instanz und wird in diesem Tutorial an mehreren Stellen referenziert.

Die Suche nach Ihrer IMS-Organisations-ID kann auf verschiedene Arten durchgeführt werden. Wenn Sie sich nicht sicher sind, wenden Sie sich an einen der Systemadministratoren Ihrer Instanz, um die ID zu ermitteln.

Sie können ihn finden, indem Sie zu [Admin Console](https://https://adminconsole.adobe.com/) gehen, wo Sie ihn als Teil der URL finden.

![DSN](./images/aepid1.png)

Sie können sie auch finden, indem Sie im AEP-Menü unter **Benutzername** zu **Data Management > Abfragen** navigieren.

![DSN](./images/aepid2.png)

Stellen Sie sicher, dass Sie den Teil **@AdobeOrg** zusammen mit der ID kopieren und einfügen.

**AEP-Mandanten-ID**

Ihre Mandantenkennung ist die eindeutige Kennung für die AEP-Instanz Ihres Unternehmens. Wenn Sie sich auf [https://platform.adobe.com/](https://platform.adobe.com/) bei Ihrer Adobe Experience Platform-Instanz anmelden, finden Sie die Mandanten-ID in der URL.

![DSN](./images/aeptenantid.png)

Wenn Sie sie in die Chrome-Erweiterung eingeben, sollten Sie sicherstellen, dass ein Unterstrich als Präfix hinzugefügt wird, sodass in diesem Beispiel **experienceplatform** zu **_experienceplatform** wird.

**AEP-Sandbox-Name**

Ihr Sandbox-Name ist der Name der Umgebung, die Sie in Ihrer AEP-Instanz verwenden werden. Wenn Sie sich auf [https://platform.adobe.com/](https://platform.adobe.com/) bei Ihrer Adobe Experience Platform-Instanz anmelden, finden Sie die Mandanten-ID in der URL.

Bevor Sie den Sandbox-Namen aus der URL übernehmen, sollten Sie sicherstellen, dass Sie sich in der Sandbox befinden, die Sie für dieses Tutorial verwenden sollten. Sie können zur rechten Sandbox wechseln, indem Sie in der oberen rechten Ecke des Bildschirms auf das Menü Sandbox-Umschalter klicken.

![DSN](./images/aepsandboxsw.png)

In diesem Beispiel lautet der AEP-Sandbox-Name **techeinsider**.

![DSN](./images/aepsname.png)

**Ihr LDAP**

Dies ist der Benutzername, der im Rahmen des Tutorials verwendet wird. In diesem Beispiel basiert das LDAP auf der E-Mail-Adresse dieses Benutzers. Die E-Mail-Adresse ist **vangeluw@adobe.com**, sodass der LDAP-Dienst zu **vangeluw** wird.

Das LDAP wird verwendet, um sicherzustellen, dass die Konfiguration, die Sie durchführen werden, mit Ihnen verknüpft wird, und keine Konflikte mit anderen Benutzern verursacht, die möglicherweise dieselbe Instanz und Sandbox verwenden, die Sie verwenden.

Ihre Werte sollten diesen ähneln.
Klicken Sie abschließend auf **Neu erstellen**.

![DSN](./images/c8a.png)


Im linken Menü der Erweiterung sehen Sie jetzt ein neues Symbol mit den Initialen Ihrer Umgebung. Klicken Sie darauf. Anschließend sehen Sie die Zuordnung zwischen den **Umgebungsvariablen** und Ihren spezifischen Adobe Experience Platform-Instanzwerten. Klicken Sie auf **Konfiguration aktivieren**.

![DSN](./images/c9.png)

Nach der Aktivierung Ihrer Konfiguration wird neben den Initialen Ihrer Umgebung ein grüner Punkt angezeigt. Das bedeutet, dass Ihre Umgebung jetzt aktiv ist.

![DSN](./images/c10.png)

## Überprüfen des Tutorial-Inhalts

Gehen Sie als Test zu [dieser Seite](https://experienceleague.adobe.com/en/docs/platform-learn/tutorial-comprehensive-technical/datadistiller/module51/ex3).

Sie sollten nun sehen, dass alle **Umgebungsvariablen** anhand der aktivierten Umgebung in der Chrome-Erweiterung durch ihre tatsächlichen Werte ersetzt wurden.

Sie sollten nun eine ähnliche Ansicht wie die unten stehende haben, in der die Umgebungsvariable `aepTenantId` durch Ihre echte AEP-Mandanten-ID ersetzt wurde, die in diesem Fall **_experienceplatform** lautet.

![DSN](./images/mod7.png)

Nächster Schritt: [Verwenden Sie das Demosystem Weiter , um Ihre Adobe Experience Platform-Datenerfassungs-Client-Eigenschaft einzurichten](./ex2.md)

[Zurück zu den ersten Schritten](./getting-started.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)

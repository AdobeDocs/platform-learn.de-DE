---
title: Authentifizieren und Zugreifen auf Experience Platform-APIs
description: Erfahren Sie, wie Sie auf Adobe Experience Platform-APIs zugreifen können.
feature: API
role: Developer
level: Beginner,Intermediate
doc-type: Technical Video
duration: 226
last-substantial-update: 2023-06-21T00:00:00Z
jira: KT-3688
exl-id: c1774670-436e-46dd-9c9b-177bfee5f749
source-git-commit: 311b296d67cf39867e7c9f3fd9f0458dfefcfdfd
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 7%

---

# Authentifizieren und Zugreifen auf [!DNL Experience Platform] APIs

Erfahren Sie mehr über die ersten Schritte mit Adobe Experience Platform-APIs. Der erste Schritt besteht darin, ein Projekt in Adobe Developer Console zu erstellen und Anmeldeinformationen abzurufen. Dieses Tutorial führt Sie durch den Prozess zum Erstellen eines Projekts in Adobe Developer Console und zum Exportieren einer Postman-Umgebungsdatei, damit Sie mit Experience Platform-API-Anfragen beginnen können.

[[!DNL Postman]](https://www.postman.com/) ist ein Drittanbieterprogramm, mit dem Entwickler schnell und einfach mit Adobe Experience Platform-APIs interagieren können.

Die Funktion [&#128279;](https://developer.adobe.com/console/home)**Details für Postman exportieren** von Adobe Developer Console bietet eine einfache Möglichkeit, die Kontodetails zu exportieren, die für den Zugriff auf und die Interaktion mit Experience Platform-APIs in einer einzigen Postman-Umgebungsdatei erforderlich sind, sodass Werte von Adobe Developer Console nicht mehr kopiert und in Postman eingefügt werden müssen.

>[!IMPORTANT]
>
>Um auf die [Adobe Developer Console](https://developer.adobe.com/console/home) zugreifen zu können, müssen Sie entweder [Systemadministrator](https://helpx.adobe.com/de/enterprise/using/admin-roles.html) oder [Entwickler](https://helpx.adobe.com/de/enterprise/using/manage-developers.html#:~:text=Add%20developers%20to%20a%20single%20product%20profile&text=In%20the%20Admin%20Console%2C%20navigate,in%20the%20upper%2Dright%20corner.) in der [Adobe Admin Console ](https://adminconsole.adobe.com).
>
> Nachdem Sie Ihre API-Anmeldedaten erstellt haben, muss ein Systemadministrator die Anmeldedaten mit einer Rolle in der Experience Platform verknüpfen.
>
>Detaillierte Anweisungen finden Sie [ Tutorial zum Hinzufügen von Entwicklern und Erteilen von Berechtigungen für ](../admin/add-developers.md) .


>[!VIDEO](https://video.tv.adobe.com/v/31575/?learn=on&enablevpops&captions=ger)

<!-- CARDS
* generate-an-access-token.md
* use-apis-with-postman.md
-->
<!-- START CARDS HTML - DO NOT MODIFY BY HAND -->
<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Generate an Experience Platform API access token with Postman">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="generate-an-access-token.md" title="Erstellen eines Experience Platform-API-Zugriffstokens mit Postman" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/32919/?format=jpeg&nocache=1752259602830&captions=ger" alt="Erstellen eines Experience Platform-API-Zugriffstokens mit Postman"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="generate-an-access-token.md" target="_blank" rel="referrer" title="Erstellen eines Experience Platform-API-Zugriffstokens mit Postman">Generieren eines Experience Platform API-Zugriffstoken mit Postman</a>
                    </p>
                    <p class="is-size-6">Erfahren Sie, wie Sie mit Postman ein Experience Platform-API-Zugriffstoken generieren</p>
                </div>
                <a href="generate-an-access-token.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">Weitere Informationen</span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Use Experience Platform APIs with Postman">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="use-apis-with-postman.md" title="Verwenden von Experience Platform-APIs mit Postman" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/32918/?format=jpeg&nocache=1752259602844&captions=ger" alt="Verwenden von Experience Platform-APIs mit Postman"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="use-apis-with-postman.md" target="_blank" rel="referrer" title="Verwenden von Experience Platform-APIs mit Postman">Verwenden von Experience Platform-APIs mit Postman</a>
                    </p>
                    <p class="is-size-6">Erkunden von Adobe Experience Platform-APIs mit den von Adobe bereitgestellten Postman-Sammlungen</p>
                </div>
                <a href="use-apis-with-postman.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">Weitere Informationen</span>
                </a>
            </div>
        </div>
    </div>
</div>
<!-- END CARDS HTML - DO NOT MODIFY BY HAND -->

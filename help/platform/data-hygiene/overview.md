---
title: Datenhygiene in Adobe Experience Platform
description: Erfahren Sie mehr über die Optionen der Datenhygiene-Tools in Adobe Experience Platform
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
feature: Data Hygiene
role: Developer
level: Intermediate
source-git-commit: 9c15708f7300672caa963c0635179dd2855e5fed
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 24%

---

# Tutorials zur Datenhygiene

Erfahren Sie mehr über die Datenhygiene-Funktionen in Adobe Experience Platform, darunter:

* Aktivierung von Prinzipien zur Datenminimierung während der Datenaufnahme
* Anpassung von Daten, die sich bereits im System befinden
* Entfernen von Daten aus dem System

<!--
Data hygiene:

* Enables citizen data stewards working in Privacy or IT teams to manage customer data lifecycle.
* Provides foundational workflows for setting expiration of datasets based on corporate policies, partner
arrangements, customer commitments or regulatory needs.
* Provides foundational workflows for managing targeted treatment of identities and data belonging to consumers in a
holistic fashion.
* Provides monitoring, work order management and notifications of tasks.
* Provides the ability to log the lifecyle management tasks for auditing purposes.
-->

## Datenminimierung während der Aufnahme

Die Datenvorbereitungsfunktion hilft Ihnen dabei, nur die Felder aufzunehmen, die Sie aus einer Datenquelle benötigen.

<!-- CARDS
{cta=Watch}
* data-prep-for-data-hygiene.md
-->
<!-- START CARDS HTML - DO NOT MODIFY BY HAND -->
<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Data prep for data hygiene">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="data-prep-for-data-hygiene.md" title="Datenvorbereitung für die Datenhygiene" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/3449284/?format=jpeg&nocache=1740251397387&captions=ger" alt="Datenvorbereitung für die Datenhygiene"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="data-prep-for-data-hygiene.md" target="_blank" rel="referrer" title="Datenvorbereitung für die Datenhygiene">Datenvorbereitung für die Datenhygiene</a>
                    </p>
                    <p class="is-size-6">Erfahren Sie, wie Sie mit der Datenvorbereitung von Experience Platform Datenminimierungsprinzipien unterstützen. Erfahren Sie, wie Sie beim Import nur die benötigten Felder erfassen und Daten hashen können.</p>
                </div>
                <a href="data-prep-for-data-hygiene.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">beobachten</span>
                </a>
            </div>
        </div>
    </div>
</div>
<!-- END CARDS HTML - DO NOT MODIFY BY HAND -->

## Entfernen von Daten im System

Es gibt viele Funktionen, mit denen Sie die Daten aus dem System entfernen können. Sie können ganze Datensätze bei Bedarf oder nach einem Zeitplan löschen, Datensätze und Profile mit Time-to-Live-Einstellungen ablaufen lassen, einzelne Profile löschen und Datenschutzanfragen erfüllen.
<!-- CARDS
{cta=Watch}
* delete-datasets-and-batches.md
* ../data-lifecycle/expire-datasets.md
* pseudonymous-profile-and-event-expiration.md
* ../profiles/delete-profiles.md{description=Learn how to delete data from the Profile Store using the Real-Time Customer Profile API. By using the Profile API, you can remove data from the profile store without affecting the data lake or identity graph.}
* ../privacy/introduction-to-privacy-services.md
-->
<!-- START CARDS HTML - DO NOT MODIFY BY HAND -->
<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Delete datasets and batches">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="delete-datasets-and-batches.md" title="Löschen von Datensätzen und Batches" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/3429790/?format=jpeg&nocache=1740251397681" alt="Löschen von Datensätzen und Batches"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="delete-datasets-and-batches.md" target="_blank" rel="referrer" title="Löschen von Datensätzen und Batches">Löschen von Datensätzen und Batches</a>
                    </p>
                    <p class="is-size-6">Hier erfahren Sie, wie Sie Datensätze und Batches in Adobe Experience Platform löschen können.</p>
                </div>
                <a href="delete-datasets-and-batches.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">beobachten</span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Schedule dataset deletes">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="../data-lifecycle/expire-datasets.md" title="Löschen von Datensätzen planen" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/3430310?format=jpeg&nocache=1740251397716&captions=ger" alt="Löschen von Datensätzen planen"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="../data-lifecycle/expire-datasets.md" target="_blank" rel="referrer" title="Löschen von Datensätzen planen">Planen von Datensatzlöschungen</a>
                    </p>
                    <p class="is-size-6">Erfahren Sie, wie Sie Datensätze mithilfe der Datenhygiene-Funktion von Adobe Experience Platform löschen können.</p>
                </div>
                <a href="../data-lifecycle/expire-datasets.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">beobachten</span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Pseudonymous profile and Experience Event expirations">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="pseudonymous-profile-and-event-expiration.md" title="Ablauf von pseudonymen Profilen und Erlebnisereignissen" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/3449865?format=jpeg&nocache=1740251397705&captions=ger" alt="Ablauf von pseudonymen Profilen und Erlebnisereignissen"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="pseudonymous-profile-and-event-expiration.md" target="_blank" rel="referrer" title="Ablauf von pseudonymen Profilen und Erlebnisereignissen">Ablauf von pseudonymen Profilen und Erlebnisereignissen</a>
                    </p>
                    <p class="is-size-6">Erfahren Sie, wie Sie die Ablaufeinstellungen für pseudonyme Profile und Ereignisse in Experience Platform konfigurieren und welche Vorteile sich daraus ergeben.</p>
                </div>
                <a href="pseudonymous-profile-and-event-expiration.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">beobachten</span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Delete profiles">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="../profiles/delete-profiles.md" title="Profile löschen" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/3429807/?format=jpeg&nocache=1740251397692" alt="Profile löschen"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="../profiles/delete-profiles.md" target="_blank" rel="referrer" title="Profile löschen">Löschen von Profilen</a>
                    </p>
                    <p class="is-size-6">Erfahren Sie, wie Sie mit der Echtzeit-Kundenprofil-API Daten aus dem Profilspeicher löschen können. Mithilfe der Profil-API können Sie Daten aus dem Profilspeicher entfernen, ohne den Data Lake oder das Identitätsdiagramm zu beeinflussen.</p>
                </div>
                <a href="../profiles/delete-profiles.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">beobachten</span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Introduction to Privacy Service">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="../privacy/introduction-to-privacy-services.md" title="Einführung in Privacy Service" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/336074?format=jpeg&nocache=1740251397727" alt="Einführung in Privacy Service"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="../privacy/introduction-to-privacy-services.md" target="_blank" rel="referrer" title="Einführung in Privacy Service">Einführung in Privacy Service</a>
                    </p>
                    <p class="is-size-6">Erfahren Sie mehr über Datenschutzbestimmungen und deren Auswirkungen auf Datenvorgänge. Erfahren Sie außerdem, wie Privacy Service mit diesen Herausforderungen umgeht.</p>
                </div>
                <a href="../privacy/introduction-to-privacy-services.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">beobachten</span>
                </a>
            </div>
        </div>
    </div>
</div>
<!-- END CARDS HTML - DO NOT MODIFY BY HAND -->





## Datenanpassung im System

<!-- CARDS
{cta=Watch}
* ../profiles/update-a-specific-attribute-with-upsert.md
-->
<!-- START CARDS HTML - DO NOT MODIFY BY HAND -->
<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Update specific profile attributes using `upsert`">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="../profiles/update-a-specific-attribute-with-upsert.md" title="Aktualisieren spezifischer Profilattribute mit „upsert“" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/3443450/?format=jpeg&nocache=1740251398874&captions=ger" alt="Aktualisieren spezifischer Profilattribute mit „upsert“"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="../profiles/update-a-specific-attribute-with-upsert.md" target="_blank" rel="referrer" title="Aktualisieren spezifischer Profilattribute mit „upsert“">Aktualisieren spezifischer Profilattribute mithilfe von „upsert“</a>
                    </p>
                    <p class="is-size-6">Erfahren Sie, wie Sie ein bestimmtes Profilattribut mit der Funktion „upsert“ von Adobe Experience Platform aktualisieren können.</p>
                </div>
                <a href="../profiles/update-a-specific-attribute-with-upsert.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">beobachten</span>
                </a>
            </div>
        </div>
    </div>
</div>
<!-- END CARDS HTML - DO NOT MODIFY BY HAND -->

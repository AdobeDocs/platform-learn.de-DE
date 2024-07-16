---
title: Bootcamp - Customer Journey Analytics - Von Einblicken zu Aktionen - Brasilien
description: Bootcamp - Customer Journey Analytics - Von Einblicken zu Aktionen - Brasilien
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
solution: Customer Journey Analytics
feature-set: Customer Journey Analytics
feature: Audiences
exl-id: 28b87e21-3168-447e-9a93-a6ae7e969657
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# 4.6 Dos Insights à ação

## Objetivos

- Entenda como crium público com base em uma visão coletada no Customer Journey Analytics
- Verwenden Sie esse público no CDP em tempo real e no Adobe Journey Optimizer

## 4.6.1 Crie uma audiência e publique-a

Em seu projeto, você criou um filo chamado **Call Feelings** e conseguiu visualizar a quantidade usuários que tiveram suas ligações ao call center classificadas como **positivas**. Agora, você poderá criar um segmento com esses usuários e ativação-los em jornadas ou em canais de comunicação.

O primeiro passo é: Kein schmerel criado no último übício, selecione a linha **1. Rufen Sie Feeling - Positiv**, klicken Sie auf com o botão direito de seu mouse e selecione a opção **Erstellen Sie eine Zielgruppe aus Auswahl**:

![demo](./images/aud1.png)

Em seguida, dê um nome para a sua audiência seguindo modelo **yourLastName - cia audience call having**:

![demo](./images/aud2.png)

Beachten Sie, dass es möglich ist, eine Vorschau der audiência que está sendo criada anzuzeigen:

![demo](./images/aud3.png)

Para finalizar, klicken Sie auf em **Publicar**:

![demo](./images/aud4.png)

## 4.6.2 Verwenden Sie sua audiência como parte de um segmento

Voltando para a Adobe Experience Platform, vá em **Segmente > Browse** e você conseguirá visualizar o seu segmento criado no CJA pronto e disponível para ser usado nas suas ativações e jornadas!

![demo](./images/aud5.png)

Vamos agora usar esse segmento em uma ativação no Facebook e em uma jornada do cliente!

## 4.6.3 Verwenden Sie &quot;seu segmento an Real-Time CDP em tempo real&quot;

Na Adobe Experience Platform, vá em **Segmente > Durchsuchen** e encontre a audiência que você criou no CJA:

![demo](./images/aud6.png)

Klicken Sie auf kein seu segmento e, em seguida, klicken Sie auf em **Activate to Destination**:

![demo](./images/aud7.png)

Wählen Sie ein Ziel chamada bootcamp-facebook e, em seguida, klicken Sie auf em Next:

![demo](./images/aud8.png)

Em seguida, clique em Next novamente:

![demo](./images/aud9.png)

Wählen Sie einen opção **Ursprung Ihrer Audience** e defina como **Direkt aus Kunden** und klicken Sie auf em Weiter:

![demo](./images/aud10.png)

Por fim, na página **Review** clique em Finish!

![demo](./images/aud11.png)

Pronto! Agora o seu segmento está vinculado aos públicos personalizados do Facebook.
Agora, vamos utilizar esse segmento no AJO!

## 4.6.4 Verwenden Sie &quot;Segment segmentieren&quot;zu Adobe Journey Optimizer

Na interface da Adobe Experience Platform clique em Journey Optimizer e, em seguida, no menu lateral esquerdo, clique em **Journey** e comece a criar uma jornada clicando em **Journey erstellen**:

![demo](./images/aud20.png)

![demo](./images/aud21.png)

![demo](./images/aud22.png)

Em seguida, no menu lateral esquerdo, em Eventos, selecione **Segmentqualifikation** e arraste-o até a jornada:

![demo](./images/aud23.png)

Em seguida, em **Segment** clique em **Edit** para selecionar um segmento:

![demo](./images/aud24.png)

Selecione a audiência que você criou no CJA e clique em **Save**:

![demo](./images/aud25.png)

Pronto! Ein partir daí você pode criar uma jornada para clientes que se qualificam para esse segmento!

[Zurück zum Benutzerfluss 4](./uc4.md)

[Voltar para todos os módulos](./../../overview.md)

---
title: Bootcamp - Customer Journey Analytics - Vom Einblick zum Handeln - Brasilien
description: Bootcamp - Customer Journey Analytics - Vom Einblick zum Handeln - Brasilien
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

## objektivisch

- Entenda como criar um público com base em uma visão coletada no Customer Journey Analytics
- Use esse público no CDP em tempo real e no Adobe Journey Optimizer

## 4.6.1 Crie uma audiência e publique-a

Em seu projeto, você criou um filtro chamado **Call Feelings** e conseguiu visualizar a quantidade de usuários que tiram suas ligações ao call center classificadas como **positivas**. Agora, você poderá criar um segmento comses usuários e ativação-los em jornadas ou em canais de comunicação.

O primeiro passo é: No painel criado no último ercício, selecione a linha **1. Call Feeling - Positive**, clique com o botão direito de seu mouse e selecione a opção **Zielgruppe aus Auswahl erstellen**:

![demo](./images/aud1.png)

Em seguida, dê um nome para a sua audiência seguindo o modelo **yourLastName - cia Zielgruppen-Aufruf Gefühl positiv**:

![demo](./images/aud2.png)

Note que é posível ter um preview da audiência que está sendo criada:

![demo](./images/aud3.png)

Para finalizar, clique em **Publicar**:

![demo](./images/aud4.png)

## 4.6.2 Verwenden Sie sua audiência como parte de um segmento

Voltando para a Adobe Experience Platform, vá em **Segmente > Browse** e você conseguirá visualizar o seu segmento criado no CJA pronto e disponível para ser usado nas suas ativações e jornadas!

![demo](./images/aud5.png)

Vamos agora usar esse segmento em uma ativação no Facebook e em uma jornada do cliente!

## 4.6.3 Verwenden Sie seu segmento na Real-Time CDP em tempo real

Na Adobe Experience Platform, vá em **Segmente > Durchsuchen** e encontre a audiência que você criou no CJA:

![demo](./images/aud6.png)

Klicken Sie auf Kein seu segmento e, em seguida, clique em **Für Ziel aktivieren**:

![demo](./images/aud7.png)

Wählen Sie ein Ziel chamada bootcamp-facebook e, em seguida, clique em Weiter:

![demo](./images/aud8.png)

Em seguida, clique em next novamente:

![demo](./images/aud9.png)

Select ecione a opção **Herkunft Ihrer Audience** e defina como **Direkt von Kunden** e clique em Weiter:

![demo](./images/aud10.png)

Por fim, na página **Review** clique em Finish!

![demo](./images/aud11.png)

Pronto! Agora o seu segmento está vinculado aos públicos personalizados do Facebook.
Agora, vamos utilizar esse segmento no AJO!

## 4.6.4 Verwenden des Segments „seu“ ohne Adobe Journey Optimizer

Na interface da Adobe Experience Platform clique em Journey Optimizer e, em seguida, no menu lateral esquerdo, clique em **Journey** e comece a criar uma jornada clicando em **Create Journey**:

![demo](./images/aud20.png)

![demo](./images/aud21.png)

![demo](./images/aud22.png)

Em seguida, no menu lateral esquerdo, em Eventos, selecione **Segmentqualifikation** e arraste-o até a jornada:

![demo](./images/aud23.png)

em seguida, em **segment** clique em **edit** para selecionar um segmento:

![demo](./images/aud24.png)

Selecione a audiência que você criou no CJA e clique em **Speichern**:

![demo](./images/aud25.png)

Pronto! A partir daí você pode criar uma jornada para clientes que se qualificam para esse segmento!

[Zurück zu Benutzerfluss 4](./uc4.md)

[Voltar para todos os módulos](./../../overview.md)

---
title: Bootcamp - Customer Journey Analytics - Von Einblicken zu Aktionen - Brasilien
description: Bootcamp - Customer Journey Analytics - Von Einblicken zu Aktionen - Brasilien
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 28b87e21-3168-447e-9a93-a6ae7e969657
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# 4.6 Dos Insights à ação

## Objetivos

- Entenda como criar um público com base em uma visão coletada nein Customer Journey Analytics
- Verwenden Sie esse público no CDP em tempo real e no Adobe Journey Optimizer

## 4.6.1 Crie uma audiência e publique-a

Em seu projeto, você criou um filtrado **Aufruffunktionen** e conseguiu visualizar a quantidade de usuários que tiver am suas ligações ao call center classificadas como **positivas**. Agora, você poderá criar um segmento com esses usuários e ativação-los em jornadas ou em canais de comunicação.

O primeiro passo é: Kein males Criado no último übício, selecione a linha **1. Rufempfindlichkeit - positiv**, clique com o botão direito de seu mouse e selecione a opção **Erstellen einer Zielgruppe aus Auswahl**:

![Demo](./images/aud1.png)

Em seguida, dê um nome para a sua audiência seguindo o modelo **yourLastName - cia-Zielgruppenaufruf mit positivem**:

![Demo](./images/aud2.png)

Beachten Sie, dass es möglich ist, eine Vorschau der audiência que está sendo criada anzuzeigen:

![Demo](./images/aud3.png)

Para finalizar, clique em **Publikum**:

![Demo](./images/aud4.png)

## 4.6.2 Verwenden Sie sua audiência como parte de um segmento

Voltando para a Adobe Experience Platform, vá em **Segmente > Durchsuchen** e você conseguirá visualizar o seu segmento criado no CJA pronto e disponível para ser usado nas suas ativações e jornadas!

![Demo](./images/aud5.png)

Vamos agora usar esse segmento em uma ativação no Facebook e em uma jornada do cliente!

## 4.6.3 Verwenden Sie &quot;seu segmento an Real-Time CDP em tempo real&quot;

Na Adobe Experience Platform, vá em **Segmente > Durchsuchen** e stellen ein audiência que você criou no CJA:

![Demo](./images/aud6.png)

Klicken Sie auf kein seu segmento e, em seguida, clique em **Für Ziel aktivieren**:

![Demo](./images/aud7.png)

Wählen Sie ein Ziel chamada bootcamp-facebook e, em seguida, klicken Sie auf em Next:

![Demo](./images/aud8.png)

Em seguida, clique em Next novamente:

![Demo](./images/aud9.png)

Selecione a opção **Herkunft der Audience** e defina como **Direkt von Kunden** Klicken Sie auf Weiter :

![Demo](./images/aud10.png)

Por fim, na página **Überprüfen** clique em Finish!

![Demo](./images/aud11.png)

Pronto! Agora o seu segmento está vinculado aos públicos personalizados do Facebook.
Agora, vamos utilizar esse segmento no AJO!

## 4.6.4 Verwenden Sie &quot;Segment segmentieren&quot;zu Adobe Journey Optimizer

Na interface da Adobe Experience Platform clique em Journey Optimizer e, em seguida, no menu lateral esquerdo, clique em **Journey** e come a criar uma jornada clicando em **Journey erstellen**:

![Demo](./images/aud20.png)

![Demo](./images/aud21.png)

![Demo](./images/aud22.png)

Em seguida, no menu lateral esquerdo, em Eventos, selecione **Segmentqualifikation** e arraste-o até a jornada:

![Demo](./images/aud23.png)

Em seguida, em **Segment** clique em **Bearbeiten** para selecionar um segmento:

![Demo](./images/aud24.png)

Selecione a audiência que você criou no CJA e clique em **Speichern**:

![Demo](./images/aud25.png)

Pronto! Ein partir daí você pode criar uma jornada para clientes que se qualificam para esse segmento!

[Zurück zum Benutzerfluss 4](./uc4.md)

[Voltar para todos os módulos](./../../overview.md)

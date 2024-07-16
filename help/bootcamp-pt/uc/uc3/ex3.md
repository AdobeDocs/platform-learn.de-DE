---
title: Bootcamp - Vermischen von physisch und digital - Journey Optimizer Journey und Push erstellen - Brazilnotification
description: Bootcamp - Vermischen von physisch und digital - Journey Optimizer Journey und Push erstellen - Brazilnotification
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Events
exl-id: a4ef6eaf-6b39-4450-82bf-7db99595a323
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 1%

---

# 3.3 Crie sua jornada e notificação push

Neste übício, você irá configuration a jornada e a mensagem que preisa ser acionada quando alguém inserir uma sinalização (Beacon) usando o aplicativo móvel.

Faça meldet sich bei Adobe Journey Optimizer-Zugriff an und erhält einen [Adobe Experience Cloud](https://experience.adobe.com). Klicken Sie auf em **Journey Optimizer**.

![ACOP](./images/acophome.png)

Você será redirecionado para a visualização da **Home** no Journey Optimizer. Primeiro, verifique se você está usando o sandbox correto. O nome do sandbox que deve ser usado é `Bootcamp`. Para alternative de um sandbox para outro, clique em **Prod** e selecione o sandbox na lista. Neste exemplo, o nome do sandbox é **Bootcamp**. Você estará na visualização da **Home** do seu sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

## 3.3.1 Crie a sua jornada

Kein Menü à esquerda, klicken Sie auf em **Journey**. Em seguida, clique em **Erstellen Sie Journey** para criar uma nova jornada.

![ACOP](./images/createjourney.png)

Você verá uma tela de jornada vazia.

![ACOP](./images/journeyempty.png)

No übício anteriore, você criou um novo **Event**. Você nomeou o evento `yourLastNameBeaconEntryEvent` e replace `yourLastName` pelo seu sobrenome. Este foi o result tado da criação do Evento:

![ACOP](./images/eventdone.png)

Agora você deve rücksichtsar este evento como início desta Jornada. Você pode fazer isso indo para o lado esquerdo da tela e procurando pelo seu evento na lista de eventos.

![ACOP](./images/eventlist.png)

Selecione seu evento, arraste e solte o evento na tela de jornada. Sua jornada agora deve ser semelhante ao seguinte. Clique em **OK** para salvar suas alterações.

![ACOP](./images/journeyevent.png)

Como segunda etapa da jornada, você deve adicionar uma ação **Push**. Vá para o lado esquerdo da tela para **Aktionen**, selecione a ação **Push** e arraste e solte a ação no segundo nó da sua jornada.

![ACOP](./images/journeyactions.png)

No lado direito da tela, agora você deve criar sua notificação push.

Definiert ein **Kategorie** -Komo **Marketing** e selecione um Push-Oberfläche que permite enviar notificações push. Nesse caso, ein Superfície pushen eine ser selecionada é **mmeeewis-app-mobile-bootcamp**.

![ACOP](./images/journeyactions1.png)

## 3.3.2 Krim a sua mensagem

Klicken Sie auf em **Inhalt bearbeiten**.

![ACOP](./images/emptymsg.png)

Em seguida, a tela abaixo será exibida:

![ACOP](./images/emailmsglist.png)

Vamos definir o conteúdo da notificação push.

Klicken Sie auf kein Campo de texto **Titel**.

![Journey Optimizer](./images/msg5.png)

Na área de texto, comece **Olá**. Clique no ícone de personalização.

![Journey Optimizer](./images/msg6.png)

Agora você recisa trazer o token de personalização para o campo **Vorname** que está rüzenado em `profile.person.name.firstName`. Kein Menü à esquerda, selecione **Profilattribute**, role para baixo/navegue para encounter o elemento **Person** e clique na seta para avançar um nível até chegar ao campo `profile.person.name.firstName`. Clique no ícone **+** para adicionar o campo à tela. Klicken Sie auf em **Save**.

![Journey Optimizer](./images/msg7.png)

Então, você irá retornar para esta tela. Clique no ícone de personalização ao lado do campo **Body**.

![Journey Optimizer](./images/msg11.png)

Na área de texto, escreva `Bem-vindo(a)`.

![Journey Optimizer](./images/msg12.png)

Unter &quot;Segment&quot;klicken Sie auf em **Kontextuelle Attribute** e **Journey Orchestration**.

![ACOP](./images/jomsg3.png)

Klicken Sie auf em **events**.

![ACOP](./images/jomsg4.png)

Klicken Sie auf nome do seu evento, que deve ser semelhante ao seguinte: **yourLastNameBeaconEntryEvent**.

![ACOP](./images/jomsg5.png)

Klicken Sie auf em **Kontext platzieren**.

![ACOP](./images/jomsg6.png)

Klicken Sie auf em **POI-Interaktion**.

![ACOP](./images/jomsg7.png)

Klicken Sie auf em **POI-Detail**.

![ACOP](./images/jomsg8.png)

Klicken Sie auf das Symbol **+** auf dem Symbol **POI-Name**.
Em seguida, o seguinte será exibido. Klicken Sie auf em **Save**.

![ACOP](./images/jomsg9.png)

Sua mensagem agora está pronta. Clique na seta no canto Superior esquerdo para retornar à sua jornada.

![ACOP](./images/jomsg11.png)

Klicken Sie auf em **OK**.

![ACOP](./images/jomsg14.png)

## 3.3.2 Envie uma mensagem para uma tela

Como terceira etapa da jornada, você deve adicionar uma ação **sendMessageToScreen**. Vá para o lado esquerdo da tela para **Aktionen**, selecione a ação **sendMessageToScreen** e arraste e solte a ação no terceiro nó da sua jornada. Em seguida, você verá a tela abaixo.

![ACOP](./images/jomsg15.png)

**sendMessageToScreen** é uma ação personalizada que irá publicar uma mensagem no **Endpoint** usado pela exibição na loja. Ein ação **sendMessageToScreen** espera que múltiplas variáveis sejam defindas. Você pode visualizar essas variáveis rolando para baixo até ver **Aktionsparameter**.

![ACOP](./images/jomsg16.png)

Agora você preisa definir os valores para cada parâmetro de ação. Siga esta tabela para entender quais valores são notwendiários e onde.

| Parameter | Wert |
|:-------------:| :---------------:|
| VERSAND | `'image'` |
| ECID | `@{yourLastNameBeaconEntryEvent._experienceplatform.identification.core.ecid}` |
| VORNAME | `#{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName}` |
| EREIGNIS | `#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first().name}` |
| EVENTSUBJECTURL | `#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first()._experienceplatform.core.imageURL}` |
| SANDBOX | `'bootcamp'` |
| CONTAINERID | `''` |
| ACTIVITYID | `''` |
| PLACEMENTID | `''` |

{style="table-layout:auto"}

Para definir weist Werte auf, clique no ícone **Bearbeiten**.

![ACOP](./images/jomsg17.png)

Em seguida, select **Advanced Mode**.

![ACOP](./images/jomsg18.png)

Em seguida, cole o valor com base na tabela acima. Klicken Sie auf em **OK**.

![ACOP](./images/jomsg19.png)

Repita esse processo para adicionar valores para cada campo.

>[!IMPORTANT]
>
>Para o campo ECID, há uma referência ao evento`yourLastNameBeaconEntryEvent`. Lembre-se de substitution `yourLastName` pelo seu sobrenome.

O result tado final deve ser semelhante ao seguinte:

![ACOP](./images/jomsg20.png)

Rolle para cima e clique em **OK**.

![ACOP](./images/jomsg21.png)

Sie müssen Ihrer Journey noch einen Namen geben. Klicken Sie dazu oben rechts auf dem Bildschirm auf das Symbol **Eigenschaften** .

![ACOP](./images/journeyname.png)

Você pode inserir o nome da jornada aqui. Verwenden Sie `yourLastName - Beacon Entry Journey`. Clique em **OK** para salvar suas alterações.

![ACOP](./images/journeyname1.png)

Agora você pode publicar sua jornada clicando em **Publish**.

![ACOP](./images/publishjourney.png)

Clique em **Publish** novamente.

![ACOP](./images/publish1.png)

Você verá uma barra de bestätigmação verde informando que sua jornada agora está Publicada.

![ACOP](./images/published.png)

Sua jornada agora está ativa e pode ser acionada.

Você terminou este übício.

Próxima etapa: [3,4 Teste sua jornada](./ex4.md)

[Retornar para Fluxo de Usuário 3](./uc3.md)

[Retornar para Todos os Módulos](../../overview.md)

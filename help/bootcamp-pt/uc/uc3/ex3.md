---
title: Bootcamp - Mischung aus physischem und digitalem - Journey Optimizer Erstellen Sie Ihren Journey und Push - BrasilienNotification
description: Bootcamp - Mischung aus physischem und digitalem - Journey Optimizer Erstellen Sie Ihren Journey und Push - BrasilienNotification
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

Neste ercício, você irá configurar a jornada e a menagem que precisa ser acionada quando alguém inserir uma sinalização (Beacon) usando o aplicativo móvel.

Faça Anmeldung auf Adobe Journey Optimizer acessando a [Adobe Experience Cloud](https://experience.adobe.com). Klicken Sie auf AEM **Journey Optimizer**.

![ACOP](./images/acophome.png)

Você será redirecionado para a visualização da **Home** no Journey Optimizer. Primeiro, verifique se você está usando oder sandbox correto. O nome do sandbox que deve ser usado é `Bootcamp`. Para alternative de um sandbox para outro, clique em **prod** e selecione o sandbox na lista. Neste exemplo, o nome do sandbox é **Bootcamp**. Você estará na visualização da **Home** do seu sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

## 3.3.1 Crie a sua jornada

Kein Menü à esquerda, clique em **Journey**. Em seguida, clique em **Create Journey** para criar uma nova jornada.

![ACOP](./images/createjourney.png)

Você verá uma tela de jornada vazia.

![ACOP](./images/journeyempty.png)

No ercício anterior, você criou um novo **Event**. Você nomeou o evento `yourLastNameBeaconEntryEvent` e substituiu `yourLastName` pelo seu sobrenome. Este foi o resultado da criação do Evento:

![ACOP](./images/eventdone.png)

Agora você deve Considerar este evento como o início desta Jornada. Você pode fazer isso indo para o lado esquerdo da tela e procurando pelo seu event to na lista de eventos.

![ACOP](./images/eventlist.png)

Selecione seu evento, arraste e solte o evento na tela de jornada. Sua jornada agora deve ser semelhante ao seguinte. Clique em **OK** para salvar suas alterações.

![ACOP](./images/journeyevent.png)

Como segunda etapa da jornada, você deve adicionar uma ação **Push**. Vá para o lado esquerdo da tela **Actions**, selecione a ação **Push** e arraste e solte a ação no segundo nó da sua jornada.

![ACOP](./images/journeyactions.png)

No lado direito da tela, agora você deve criar sua notificação push.

Definieren Sie eine **Kategorie** como **Marketing** e selecione um push surface que permite enviar notificações push. Nesse caso, a superfície push a ser selecionada é **mmeeewis-app-mobile-bootcamp**.

![ACOP](./images/journeyactions1.png)

## 3.3.2 Crie a sua menagem

Klicken Sie auf **Inhalt bearbeiten**.

![ACOP](./images/emptymsg.png)

Em seguida, a tela abaixo será exibida:

![ACOP](./images/emailmsglist.png)

Vamos definir o conteúdo da notificação push.

Clique no campo de texto **Titel**.

![Journey Optimizer](./images/msg5.png)

Na área de texto, comece **Olá**. In: Clique no ícone de personalização.

![Journey Optimizer](./images/msg6.png)

Agora você precisa trazer o token de personalização para o campo **Vorname** que está armazenado em `profile.person.name.firstName`. Kein Menü à esquerda, selecione **Profilattribute**, role para baixo/navegue para encontra o elemento **Person** e clique na seta para avançar um nível até chegar ao campo `profile.person.name.firstName`. Clique no ícone **+** para adicionar o campo à tela. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/msg7.png)

Então, você irá retornar para esta tela. Clique no ícone de personalização ao lado do campo **Body**.

![Journey Optimizer](./images/msg11.png)

Na área de texto, escreva `Bem-vindo(a)`.

![Journey Optimizer](./images/msg12.png)

em seguida, clique em **Kontextattribute** e **Journey Orchestration**.

![ACOP](./images/jomsg3.png)

Klicken Sie auf **Ereignisse**.

![ACOP](./images/jomsg4.png)

Clique no nome do seu event, que deve ser semelhante ao seguinte: **yourLastNameBeaconEntryEvent**.

![ACOP](./images/jomsg5.png)

Clique EM **Ortskontext**.

![ACOP](./images/jomsg6.png)

Clique EM **POI Interaction**.

![ACOP](./images/jomsg7.png)

Clique EM **POI-Detail**.

![ACOP](./images/jomsg8.png)

Klicken Sie auf Kein **+** Symbol **POI-Name**.
Em seguida, o seguinte será exibido. Klicken Sie auf **Speichern**.

![ACOP](./images/jomsg9.png)

In: Sua menagem agora está pronta. Clique na seta no canto superior esquerdo para retornar à sua jornada.

![ACOP](./images/jomsg11.png)

Clique EM **OK**.

![ACOP](./images/jomsg14.png)

## 3.3.2 Envie uma menagem para uma tela

Como terceira etapa da jornada, você deve adicionar uma ação **sendMessageToScreen**. Vá para o lado esquerdo da tela **Actions**, selecione a ação **sendMessageToScreen** e arraste e solte a ação no terceiro nó da sua jornada. Em seguida, você verá a tela abaixo

![ACOP](./images/jomsg15.png)

**sendMessageToScreen** é uma ação personalizada que irá publicar uma menagem no **Endpoint** usado pela exibição na loja. A ação **sendMessageToScreen** espera que múltiplas variáveis sejam definidas. Você pode visualizar essas variáveis rolando para baixo até ver **Aktionsparameter**.

![ACOP](./images/jomsg16.png)

Agora você precisa definir os valores para cada parâmetro de ação. Siga esta tabela para entender quais valores são necários e onde.

| Parameter | Wert |
|:-------------:| :---------------:|
| VERSAND | `'image'` |
| ECID | `@{yourLastNameBeaconEntryEvent._experienceplatform.identification.core.ecid}` |
| VORNAME | `#{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName}` |
| EREIGNISBETREFF | `#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first().name}` |
| EVENTSUBJECTURL | `#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first()._experienceplatform.core.imageURL}` |
| SANDBOX | `'bootcamp'` |
| CONTAINER-ID | `''` |
| ACTIVITYID | `''` |
| PLACEMENTID | `''` |

{style="table-layout:auto"}

Para definir esses valores, clique no ícone **Bearbeiten**.

![ACOP](./images/jomsg17.png)

em seguida, selecione **Erweiterter Modus**.

![ACOP](./images/jomsg18.png)

Em seguida, cole o valor com base na tabela acima. Clique EM **OK**.

![ACOP](./images/jomsg19.png)

In: Repita esse proceso para adicionar valores para cada.

>[!IMPORTANT]
>
>Para o campo ECID, há uma referência ao evento`yourLastNameBeaconEntryEvent`. In: Lembre-se de substituir `yourLastName` pelo seu sobrenome.

O resultado final deve ser semelhante ao seguinte:

![ACOP](./images/jomsg20.png)

Role para cima e clique em **OK**.

![ACOP](./images/jomsg21.png)

Sie müssen Ihrem Journey dennoch einen Namen geben. Klicken Sie dazu auf das Symbol **Eigenschaften** oben rechts auf Ihrem Bildschirm.

![ACOP](./images/journeyname.png)

Você pode inserir o nome da jornada aqui. `yourLastName - Beacon Entry Journey` verwenden. Clique em **OK** para salvar suas alterações.

![ACOP](./images/journeyname1.png)

Agora você pode publicar sua jornada clicando em **Publish**.

![ACOP](./images/publishjourney.png)

Clique em **Publish** novamente.

![ACOP](./images/publish1.png)

Você verá uma barra de confirmação verde informando que sua jornada agora está Publicada.

![ACOP](./images/published.png)

In: Sua jornada agora está ativa e pode ser acionada.

In: Você terminou este exercício.

Próxima etapa: [3.4 Teste sua jornada](./ex4.md)

[Retornar para Fluxo de Usuário 3](./uc3.md)

[In: Retornar para Todos os Módulos](../../overview.md)

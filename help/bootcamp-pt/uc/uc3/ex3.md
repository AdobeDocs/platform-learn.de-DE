---
title: Bootcamp - Vermischen von physisch und digital - Journey Optimizer Journey und Push erstellen - Brazilnotification
description: Bootcamp - Vermischen von physisch und digital - Journey Optimizer Journey und Push erstellen - Brazilnotification
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
source-git-commit: 5d824244766135cd4998feab48be7f6a69c42a70
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 2%

---

# 3.3 Crie sua jornada e notificação push

Neste übício, você irá configuration a jornada e a mensagem que preisa ser acionada quando alguém inserir uma sinalização (Beacon) usando o aplicativo móvel.

Faça login bei Adobe Journey Optimizer acessando a [Adobe Experience Cloud](https://experience.adobe.com). Clique em **Journey Optimizer**.

![ACOP](./images/acophome.png)

Você será redirecionado para visualização da **Startseite** Keine Journey Optimizer. Primeiro, verifique se você está usando o sandbox correto. O nome do sandbox que deve ser usado `Bootcamp`. Para alternar de um sandbox para outro, clique em **Prod** Auswahl von Sandbox- und Lista-Werten. Neste Exemplo, o nome do sandbox é **Bootcamp**. Você estará na visualização da **Startseite**  Ausführen einer Sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

## 3.3.1 Crie a sua jornada

No menu à esquerda, clique em **Journey**. Em seguida, clique em **Journey erstellen** para criar uma nova jornada.

![ACOP](./images/createjourney.png)

Você verá uma tela de jornada vazia.

![ACOP](./images/journeyempty.png)

No übício anteriore, você criou um novo **Ereignis**. Você nomeou o evento `yourLastNameBeaconEntryEvent` e substitution `yourLastName` pelo seu sobrenome. Este foi o result tado da criação do Evento:

![ACOP](./images/eventdone.png)

Agora você deve rücksichtsar este evento como início desta Jornada. Você pode fazer isso indo para o lado esquerdo da tela e procurando pelo seu evento na lista de eventos.

![ACOP](./images/eventlist.png)

Selecione seu evento, arraste e solte o evento na tela de jornada. Sua jornada agora deve ser semelhante ao seguinte. Clique em **Ok** para salvar suas alterações.

![ACOP](./images/journeyevent.png)

Como segunda etapa da jornada, você deve adicionar uma ação **Push**. Vá para o lado esquerdo da tela para **Aktionen**, selecione a ação **Push** e arraste e solte a ação no segundo nó da sua jornada.

![ACOP](./images/journeyactions.png)

No lado direito da tela, agora você deve criar sua notificação push.

Definieren Sie eine **Kategorie** como **Marketing** e selecione um push interface que permite enviar notificações push. Nesse caso, ein Superfície push a ser selecionada é **mmeeewis-app-mobile-bootcamp**.

![ACOP](./images/journeyactions1.png)

## 3.3.2 Krim a sua mensagem

Clique em **Inhalt bearbeiten**.

![ACOP](./images/emptymsg.png)

Em seguida, a tela abaixo será exibida:

![ACOP](./images/emailmsglist.png)

Vamos definir o conteúdo da notificação push.

Clique no campo de texto **Titel**.

![Journey Optimizer](./images/msg5.png)

Na área de texto, comece **Olá**. Clique no ícone de personalização.

![Journey Optimizer](./images/msg6.png)

Agora você recisa trazer o token de personalização para o campo **Vorname** que está armazenado em `profile.person.name.firstName`. No menu à esquerda, selecione **Profilattribute**, role para baixo/navegue para encounter o elemento **Person** e clique na seta para avançar um nível até chegar ao campo `profile.person.name.firstName`. Clique no ícone **+** para adicionar o campo à tela. Clique em **Speichern**.

![Journey Optimizer](./images/msg7.png)

Então, você irá retornar para esta tela. Clique no ícone de personalização ao lado do campo **body**.

![Journey Optimizer](./images/msg11.png)

Na área de texto, escreva `Bem-vindo(a)`.

![Journey Optimizer](./images/msg12.png)

Em seguida, clique em  **Kontextuelle Attribute** e **Journey Orchestration**.

![ACOP](./images/jomsg3.png)

Clique em **Veranstaltungen**.

![ACOP](./images/jomsg4.png)

Clique no nome do seu evento, que deve ser semelhante ao seguinte: **yourLastNameBeaconEntryEvent**.

![ACOP](./images/jomsg5.png)

Clique em **Ortskontext**.

![ACOP](./images/jomsg6.png)

Clique em **POI-Interaktion**.

![ACOP](./images/jomsg7.png)

Clique em **POI-Detail**.

![ACOP](./images/jomsg8.png)

Klicks nein **+** icon no **POI-Name**.
Em seguida, o seguinte será exibido. Clique em **Speichern**.

![ACOP](./images/jomsg9.png)

Sua mensagem agora está pronta. Clique na seta no canto Superior esquerdo para retornar à sua jornada.

![ACOP](./images/jomsg11.png)

Clique em **Ok**.

![ACOP](./images/jomsg14.png)

## 3.3.2 Envie uma mensagem para uma tela

Como terceira etapa da jornada, você deve adicionar uma ação  **sendMessageToScreen**. Vá para o lado esquerdo da tela para **Aktionen**, selecione a ação **sendMessageToScreen** e arraste e solte a ação no terceiro nó da sua jornada. Em seguida, você verá a tela abaixo.

![ACOP](./images/jomsg15.png)

**sendMessageToScreen** é uma ação personalizada que irá publicar uma mensagem ni **Endpunkt** usado pela exibição na loja. A ação **sendMessageToScreen** espera que múltiplas variáveis sejam definidas. Você pode visualizar essas variáveis rolando para baixo até ver **Aktionsparameter**.

![ACOP](./images/jomsg16.png)

Agora você preisa definir os valores para cada parâmetro de ação. Siga esta tabela para entender quais valores são notwendiários e onde.

| Parameter | value |
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

{style=&quot;table-layout:auto&quot;}

Para definir esses valores, clique no ícone **Bearbeiten**.

![ACOP](./images/jomsg17.png)

Em seguida, selecione **Erweiterter Modus**.

![ACOP](./images/jomsg18.png)

Em seguida, cole o valor com base na tabela acima. Clique em **Ok**.

![ACOP](./images/jomsg19.png)

Repita esse processo para adicionar valores para cada campo.

>[!IMPORTANT]
>
>Para o campo ECID, há uma referência ao evento`yourLastNameBeaconEntryEvent`. Lembre-se de substitution  `yourLastName` pelo seu sobrenome.

O result tado final deve ser semelhante ao seguinte:

![ACOP](./images/jomsg20.png)

Rolle para cima e clique em **Ok**.

![ACOP](./images/jomsg21.png)

Sie müssen Ihrer Journey noch einen Namen geben. Klicken Sie hierzu auf die Schaltfläche **Eigenschaften** rechts oben auf dem Bildschirm angezeigt.

![ACOP](./images/journeyname.png)

Você pode inserir o nome da jornada aqui. Verwenden von `yourLastName - Beacon Entry Journey`. Clique em **OK** para salvar suas alterações.

![ACOP](./images/journeyname1.png)

Agora você pode publicar sua jornada clicando em **Veröffentlichen**.

![ACOP](./images/publishjourney.png)

Clique em **Veröffentlichen** novamente.

![ACOP](./images/publish1.png)

Você verá uma barra de bestätigmação verde informando que sua jornada agora está Publicada.

![ACOP](./images/published.png)

Sua jornada agora está ativa e pode ser acionada.

Você terminou este übício.

Próxima etapa: [3.4 Teste sua jornada](./ex4.md)

[Retornar para Fluxo de Usuário 3](./uc3.md)

[Retornar para Todos os Módulos](../../overview.md)

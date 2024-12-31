---
title: Bootcamp - Journey Optimizer Event erstellen - Brasilien
description: Bootcamp - Journey Optimizer Event erstellen - Brasilien
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Events
exl-id: 1b9d7a35-cddf-4f4a-ad0a-95723b00c278
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# 2.2 Crie seu evento

Faça Anmeldung auf Adobe Journey Optimizer acessando a [Adobe Experience Cloud](https://experience.adobe.com). Klicken Sie auf AEM **Journey Optimizer**.

![ACOP](./images/acophome.png)

Você será redirecionado para a visualização da **Home** no Journey Optimizer. Primeiro, verifique se você está usando oder sandbox correto. O nome do sandbox que deve ser usado é `Bootcamp`. Para alternative de um sandbox para outro, clique em prod e selecione o sandbox na lista. Neste exemplo, o nome do sandbox é **Bootcamp**. Você estará na visualização da **Home** do seu sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

Kein Menü à esquerda, role para baixo e clique **Konfigurationen**. Em seguida, clique no botão **Manage** abaixo de **Events**.

![ACOP](./images/acopmenu.png)

Você verá uma visão geral de todos os eventos disponíveis. Clique em **Create Event** para começar a criar seu próprio event.

![ACOP](./images/emptyevent.png)

Uma nova janela de evento vazia irá aparecer.

![ACOP](./images/emptyevent1.png)

Em primeiro lugar, dê um nome ao seu evento como, por exemplo: `seuSobrenomeAccountCreationEvent` e adicione uma descrição como, por exemplo: `Account Creation Event`.

![ACOP](./images/eventdescription.png)

EM seguida, certificique-se de que **Type** está definido como **Unitary** e, para a a selecão de **Event ID Type**, selecione **System Generated**.

![ACOP](./images/eventidtype.png)

Ein Schema für die Sétuinte-a-selecão. Um schema foi preparation ado para este exercício. Verwenden Sie keine `Demo System - Event Schema for Website (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Depois de selecionar o Schema, você verá vários campos sendo selecionados na seção **Fields**. Agora você deve passar o mouse sobre a seção **Fields** e três ícones pop-up serão exibidos. Clique no ícone **Bearbeiten**.

![ACOP](./images/eventpayload.png)

Você verá uma janela pop-up de **Fields**, onde você deve selecionar alguns dos campos que precisamos para personalizar o e-mail. Escolheremos outros atributos de perfil posteriormente, utilizando os dados já existentes na Adobe Experience Platform.

![ACOP](./images/eventfields.png)

Kein Objekt `_experienceplatform.demoEnvironment`, pcertificfique-se de selecionar os campos **brandLogo** e **brandName**.

![ACOP](./images/eventpayloadbr.png)

Kein Objekt `_experienceplatform.identification.core`, Certifique-se de selecionar o campo **email**.

![ACOP](./images/eventpayloadbrid.png)

Clique em **Ok** to para salvar suas alterações.

![ACOP](./images/saveok.png)

Em seguida, a tela abaixo deve ser exibida. Clique em **Save** mais uma vez para salvar suas alterações..

![ACOP](./images/eventsave.png)

In: Seu evento agora está configurado e salvo.

![ACOP](./images/eventdone.png)

Clique no seu event to novamente para abrir mais uma vez a tela **Edit Event**. Passe o mouse sobre **Fields** para ver os 3 ícones outra vez. Clique no ícone **Nutzlast anzeigen**.

![ACOP](./images/viewevent.png)

Agora você verá um exemplo da carga útil esperada.
Seu event to tem um eventID de orquestração único, que você pode entracr rolando para baixo nessa carga útil (Payload) até visualizar `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

O eventID é o que deve ser enviado à Adobe Experience Platform para acionar a jornada que você construirá em um dos próximos excícios. Lembre-se deste eventID, você pode precisar del posteriormente.
`"eventID": "19cab7852cdef99d25b6d5f1b6503da39d1f486b1d585743f97ed2d1e6b6c74f"`

Klicken Sie auf em **OK** e, em seguida, klicken Sie auf em **Abbrechen**.

Agora você terminou este exercício.

Próxima etapa: [ 2.3 Crie sua menagem de E-mail](./ex3.md)

[Retornar para Fluxo de Usuário 2](./uc2.md)

[In: Retornar para Todos os Módulos](../../overview.md)

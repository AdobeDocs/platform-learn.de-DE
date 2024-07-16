---
title: Bootcamp - Journey Optimizer Erstellen Sie Ihr Ereignis - Brasilien
description: Bootcamp - Journey Optimizer Erstellen Sie Ihr Ereignis - Brasilien
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

# 2.2 Kritisches Ereignis

Faça meldet sich bei Adobe Journey Optimizer-Zugriff an und erhält einen [Adobe Experience Cloud](https://experience.adobe.com). Klicken Sie auf em **Journey Optimizer**.

![ACOP](./images/acophome.png)

Você será redirecionado para a visualização da **Home** no Journey Optimizer. Primeiro, verifique se você está usando o sandbox correto. O nome do sandbox que deve ser usado é `Bootcamp`. Para alternative de um sandbox para outro, clique em Prod e selecione o sandbox na lista. Neste exemplo, o nome do sandbox é **Bootcamp**. Você estará na visualização da **Home** do seu sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

Kein Menü à esquerda, role para baixo e clique em **Konfigurationen**. Em seguida, klicken Sie auf botão **Manage** abaixo de **Events**.

![ACOP](./images/acopmenu.png)

Você verá uma visão geral de todos os eventos disponíveis. Clique em **Create Event** para começar a criar seu próprio evento.

![ACOP](./images/emptyevent.png)

Uma nova janela de evento vazia irá aparecer.

![ACOP](./images/emptyevent1.png)

Em primeiro lugar, dê um nome ao seu evento como, por exemplo: `seuSobrenomeAccountCreationEvent` e adicione uma descrição como, por exemplo: `Account Creation Event`.

![ACOP](./images/eventdescription.png)

Em seguida, certificate-se de que **Type** está definido como **Unitary** e, para a select ção de **Event ID Type**, selecione **System generated**.

![ACOP](./images/eventidtype.png)

Ein etapa seguinte é a selção do schema. Um schema foi vorbereitado para este übício. Verwenden Sie Schema `Demo System - Event Schema for Website (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Depois de selecionar o Schema, você verá vários campos sendo selecionados na seção **Fields**. Agora você deve passar o mouse sobre a seção **Fields** e três ícones pop-up serão exibidos. Klicken Sie auf no ícone **Bearbeiten**.

![ACOP](./images/eventpayload.png)

Você verá uma janela pop-up de **Fields**, onde você deve selecionar alguns dos campos que preisamos para personalizar o e-mail. Escolheremos outros atributos de perfil posteriormente, utilizando os dados já existentes na Adobe Experience Platform.

![ACOP](./images/eventfields.png)

Kein Objekt `_experienceplatform.demoEnvironment`, pcertificate-se de selecionar os campos **brandLogo** e **brandName**.

![ACOP](./images/eventpayloadbr.png)

No object `_experienceplatform.identification.core`, certificate-se de selecionar o campo **email**.

![ACOP](./images/eventpayloadbrid.png)

Klicken Sie em **OK** auf para salvar suas alterações.

![ACOP](./images/saveok.png)

Em seguida, eine tela abaixo deve ser exibida. Clique em **Save** mais uma vez para salvar suas alterações..

![ACOP](./images/eventsave.png)

Seu evento agora está konfigurado e salvo.

![ACOP](./images/eventdone.png)

Klicken Sie auf kein seu evento novamente para abrir mais uma vez a tela **Ereignis bearbeiten**. Passe o mouse sobre **Fields** para ver os 3 ícones outra vez. Klicken Sie auf no ícone **View Payload**.

![ACOP](./images/viewevent.png)

Agora você verá um exemplo da carga útil esperada.
Seu evento tem um eventID de orquestração único, que você pode encounter rolando para baixo diena carga útil (payload) até visualizar `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

O eventID é o que deve ser enviado à Adobe Experience Platform para acionar a jornada que você construirá em um dos próximos übícios. Lembre-se deste eventID, você pode recisar dele posteriormente.
`"eventID": "19cab7852cdef99d25b6d5f1b6503da39d1f486b1d585743f97ed2d1e6b6c74f"`

Klicken Sie auf em **OK** e, em seguida, klicken Sie auf em **Abbrechen**.

Agora você terminou este übício.

Próxima etapa: [ 2.3 Crie sua mensagem de e-mail](./ex3.md)

[Retornar para Fluxo de Usuário 2](./uc2.md)

[Retornar para Todos os Módulos](../../overview.md)

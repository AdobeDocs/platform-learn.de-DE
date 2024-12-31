---
title: Bootcamp - Mischung aus physischem und digitalem - Journey Optimizer Create your event - Brasilien
description: Bootcamp - Mischung aus physischem und digitalem - Journey Optimizer Create your event - Brasilien
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Events
exl-id: 2133b560-09d8-419d-bb99-05d0f3df52cc
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# 3.2 Crie seu evento

Faça Anmeldung auf Adobe Journey Optimizer acessando a [Adobe Experience Cloud]. Klicken Sie auf AEM **Journey Optimizer**.

![ACOP](./images/acophome.png)

Você será redirecionado para a a **Home** no Journey Optimizer. Primeiro, verifique se você está usando oder sandbox correto. O nome do sandbox que deve ser usado é `Bootcamp`. Para alternative de um sandbox para outro, clique em **prod** e selecione o sandbox na lista. Neste exemplo, o nome do sandbox é **Bootcamp**. Você estará na visualização da **Home** do seu sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

Kein Menü à esquerda, role para baixo e clique **Konfigurationen**. Em seguida, clique no botão **Manage** em Eventos.

![ACOP](./images/acopmenu.png)

Você verá uma visão geral de todos os eventos disponíveis. Clique em **Create Event** para começar a criar seu próprio event.

![ACOP](./images/emptyevent.png)

Uma nova janela de evento vazia irá aparecer.

Em primeiro lugar, dê um nome ao seu evento como, por exemplo: `yourLastNameBeaconEntryEvent` e adicione uma descrição como, por exemplo: `Beacon Entry Event`.

![ACOP](./images/eventdescription.png)

EM seguida, certificique-se de que **Type** está definido como **Unitary** e, para a a selecão de **Event ID Type**, selecione **System Generated**.

![ACOP](./images/eventidtype.png)

Ein Schema für die Sétuinte-a-selecão. Um schema foi preparation ado para este exercício. Verwenden Sie keine `Demo System - Event Schema for Mobile App (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Depois de selecionar o Schema, você verá vários campos sendo selecionados na seção **Fields**. Agora você deve passar o mouse sobre a seção **Fields** e três ícones pop-up serão exibidos. Clique no ícone de **Edit**.

![ACOP](./images/eventpayload.png)

Você verá uma janela pop-up de **Fields**, onde você deve selecionar alguns dos campos que precisamos para personalizar a jornada. Escolheremos outros atributos de perfil posteriormente, utilizando os dados já existentes na Adobe Experience Platform

![ACOP](./images/eventfields.png)

Role para baixo até ver o objeto `Place context` e marque a caixa de selecão. Com isso, todo o contexto da localização do cliente será disponibilizado para a jornada. Clique em **OK** para salvar suas alterações.

![ACOP](./images/eventpayloadbr.png)

Em seguida, você deverá ver a tela abaixo. Clique em **Save** mais uma vez para salvar suas alterações.

![ACOP](./images/eventsave.png)

In: Seu evento agora está configurado e salvo.

![ACOP](./images/eventdone.png)

Clique no seu event to novamente para abrir a tela **Edit Event** mais uma vez. Passe o mouse sobre **Fields** para ver os 3 ícones. Clique no ícone **View**.

![ACOP](./images/viewevent.png)

Agora você verá um exemplo do payload esperado.
Seu event to tem um eventID de orquestração único, que você pode entracr rolando para baixo nessa carga útil até visualiza `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

O eventID é o que deve ser enviado à Adobe Experience Platform para acionar a jornada que você construirá em um dos próximos excícios. Lembre-se deste eventID, você pode precisar del posteriormente.
`"eventID": "e76c0bf0c77c3517e5b6f4c457a0754ebaf5f1f6b9357d74e0d8e13ae517c3d5"`

Clique em **OK** e, em seguida, clique em **cancelar**.

In: Você terminou este exercício.

Próxima etapa: [3.3 Crie sua jornada e notificação push](./ex3.md)

[Retornar para Fluxo de Usuário 3](./uc3.md)

[In: Retornar para Todos os Módulos](../../overview.md)

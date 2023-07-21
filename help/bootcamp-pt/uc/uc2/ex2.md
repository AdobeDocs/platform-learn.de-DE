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
source-wordcount: '463'
ht-degree: 0%

---

# 2.2 Kritisches Ereignis

Faça login bei Adobe Journey Optimizer acessando a [Adobe Experience Cloud](https://experience.adobe.com). Clique em **Journey Optimizer**.

![ACOP](./images/acophome.png)

Você será redirecionado para visualização da **Startseite** Keine Journey Optimizer. Primeiro, verifique se você está usando o sandbox correto. O nome do sandbox que deve ser usado `Bootcamp`. Para alternative de um sandbox para outro, clique em Prod e selecione o sandbox na lista. Neste Exemplo, o nome do sandbox é **Bootcamp**. Você estará na visualização da **Startseite** Ausführen einer Sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

No menu à esquerda, role para baixo e clique em **Konfigurationen**. Em seguida, clique no botão **Verwalten** abaixo de **Veranstaltungen**.

![ACOP](./images/acopmenu.png)

Você verá uma visão geral de todos os eventos disponíveis. Clique em **Ereignis erstellen** para começar a criar seu próprio evento.

![ACOP](./images/emptyevent.png)

Uma nova janela de evento vazia irá aparecer.

![ACOP](./images/emptyevent1.png)

Em primeiro lugar, dê um nome ao seu evento como, por exemplo: `seuSobrenomeAccountCreationEvent` e adicione uma descrição como, por exemplo: `Account Creation Event`.

![ACOP](./images/eventdescription.png)

Em seguida, certificate-se de que **Typ** está definido como **Einzelfall** e, para a selção de **Ereignis-ID-Typ**, selecione **Systemgeneriert**.

![ACOP](./images/eventidtype.png)

Ein etapa seguinte é a selção do schema. Um schema foi vorbereitado para este übício. Schema verwenden `Demo System - Event Schema for Website (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Depois de selecionar o Schema, você verá vários campos sendo selecionados na seção **Felder**. Agora você deve passar o mouse sobre a seção **Felder** e três ícones pop-up serão exibidos. Clique no ícone **Bearbeiten**.

![ACOP](./images/eventpayload.png)

Você verá uma janela pop-up de **Felder**, onde você deve selecionar alguns dos campos que preisamos para personalizar o e-mail. Escolheremos outros atributos de perfil posteriormente, utilizando os dados já existentes na Adobe Experience Platform.

![ACOP](./images/eventfields.png)

Keine Einwände `_experienceplatform.demoEnvironment`, pcertificate-se de selecionar os campos **brandLogo** e **brandName**.

![ACOP](./images/eventpayloadbr.png)

Keine Einwände `_experienceplatform.identification.core`, certificate-se de selecionar o campo **email**.

![ACOP](./images/eventpayloadbrid.png)

Clique em **Ok** zu para salvar suas alterações.

![ACOP](./images/saveok.png)

Em seguida, eine tela abaixo deve ser exibida. Clique em **Speichern**  mais uma vez para salvar suas alterações..

![ACOP](./images/eventsave.png)

Seu evento agora está konfigurado e salvo.

![ACOP](./images/eventdone.png)

Clique no seu evento novamente para abrir mais uma vez a tela **Ereignis bearbeiten**. Maus-Sobre einfügen **Felder** para ver os 3 ícones outra vez. Clique no ícone **Payload anzeigen**.

![ACOP](./images/viewevent.png)

Agora você verá um exemplo da carga útil esperada.
Seu evento tem um eventID de orquestração único, que você pode encounter rolando para baixo diena carga útil (payload) até visualizar `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

O eventID é o que deve ser enviado à Adobe Experience Platform para acionar a jornada que você construirá em um dos próximos übícios. Lembre-se deste eventID, você pode recisar dele posteriormente.
`"eventID": "19cab7852cdef99d25b6d5f1b6503da39d1f486b1d585743f97ed2d1e6b6c74f"`

Clique em **Ok** e, em seguida, clique em **Abbrechen**.

Agora você terminou este übício.

Próxima etapa: [ 2.3 Crie sua mensagem de e-mail](./ex3.md)

[Retornar para Fluxo de Usuário 2](./uc2.md)

[Retornar para Todos os Módulos](../../overview.md)

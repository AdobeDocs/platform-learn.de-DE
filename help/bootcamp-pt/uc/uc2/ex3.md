---
title: Bootcamp - Journey Optimizer Journey und E-Mail erstellen - Brasilien
description: Bootcamp - Journey Optimizer Journey und E-Mail erstellen - Brasilien
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Journeys
exl-id: d486d1aa-7b8e-4301-91e6-4c84fba0c72a
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 3%

---

# 2.3 Crie sua jornada e menagem de e-mail

Neste ercício, você irá configurar a jornada que precisa ser acionada quando alguém criar uma conta no site de demonstração.

Faça Anmeldung auf Adobe Journey Optimizer acessando a [Adobe Experience Cloud](https://experience.adobe.com). Klicken Sie auf AEM **Journey Optimizer**.

![ACOP](./images/acophome.png)

Você será redirecionado para a visualização da **Home** no Journey Optimizer. Primeiro, verifique se você está usando oder sandbox correto. O nome do sandbox que deve ser usado é `Bootcamp`. Para alternative de um sandbox para outro, clique em **prod** e selecione o sandbox na lista. Neste exemplo, o nome do sandbox é **Bootcamp**. Você estará na visualização da **Home** do seu sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

## 2.3.1 Crie a sua jornada

Kein Menü à esquerda, clique em **Journey**. Em seguida, clique em **Create Journey** para criar uma nova jornada.

![ACOP](./images/createjourney.png)

Você verá uma tela de jornada vazia.

![ACOP](./images/journeyempty.png)

No ercício anterior, você criou um novo **Event**. Você nomeou o evento `seuSobrenomeAccountCreationEvent` e substituiu `seuSobrenome` pelo seu sobrenome. Este foi o resultado da criação do Evento:

![ACOP](./images/eventdone.png)

Agora você deve Considerar este evento como o início desta Jornada. Você pode fazer isso indo para o lado esquerdo da tela e procurando pelo seu event to na lista de eventos.

![ACOP](./images/eventlist.png)

Selecione seu evento, arraste e solte o evento na tela de Jornada. Sua Jornada agora deve ser semelhante ao seguinte:

![ACOP](./images/journeyevent.png)

Como segunda etapa da jornada, você deve adicionar uma etapa curta de **Wait**. Vá para o lado esquerdo da tela até a seção **Orchestration** para entractor isso. Você usará atributos de perfil e precisará garantir que eles sejam preenchidos no Perfil do Cliente em tempo real.

![ACOP](./images/journeywait.png)

Sua jornada agora deve ser semelhante ao seguinte. No lado direito da tela você precisa configurar o tempo de espera. Defina como 1 minuto. Isso dará bastante tempo para que os atributos do perfil estejam disponíveis após o disparo do evento.

![ACOP](./images/journeywait1.png)

Clique em **OK** para salvar suas alterações.

Como terceira etapa da jornada, você deve adicionar uma ação **E-Mail**. Vá para o lado esquerdo da tela para **Actions**, selecione a ação **Email** e arraste e solte a ação no segundo nó da sua jornada. In: Agora o seguinte será exibido.

![ACOP](./images/journeyactions.png)

Definieren Sie eine **Kategorie** como **Marketing** e selecione uma **E-Mail-Oberfläche** que permita o envio de E-Mail. Nesse caso, eine **E-Mail Oberfläche** eine ser selecionada é E-mail. Certifique-se de que as caixas de selecão **Klicks auf E-Mail** e **E-Mail-Öffnungen** estejam marcadas.

![ACOP](./images/journeyactions1.png)

Ein próximo etapa é criar sua menagem. Para isso, clique em **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2.png)

## 2.3.2 Crie a sua menagem

Para criar sua menagem, clique em **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2.png)

O seguinte será exibido.

![ACOP](./images/journeyactions3.png)

Clique no campo de texto **Betreffzeile**.

![Journey Optimizer](./images/msg5.png)

Na área de texto, comece **Olá**

![Journey Optimizer](./images/msg6.png)

Ein Linha de assunto ainda não está pronta. Em seguida, você precisa trazer o token de personalização para o **Vorname** que está armazenado em `profile.person.name.firstName`. Kein Menü à esquerda, role para baixo para encontra o elemento **Person** e clique na seta para visualizar mais campos

![Journey Optimizer](./images/msg7.png)

Agora encontre o elemento **Vollständiger Name** e clique na seta para visualizar mais campos.

![Journey Optimizer](./images/msg8.png)

Por fim, lokalisieren o campo **Vorname** e clique no símbolo **+** ao lado dele. Você verá o token de personalização aparecer no campo de texto.

![Journey Optimizer](./images/msg9.png)

Em seguida, adicione o texto, (**a sua inscrição!**. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/msg10.png)

Então, você irá retornar para esta tela. Clique em **Email Designer** para criar o conteúdo e-mail.

![Journey Optimizer](./images/msg11.png)

Na próxima tela, será solicitado que você forneça o conteúdo do e-mail através de 3 métodos diferentes:

- **Von Grund auf gestalten**: Comece com uma tela em branco e use o editor WYSIWYG para arrastar e soltar a estrutura e os componentes de conteúdo para criar visualmente o conteúdo e-mail.
- **Eigenen Code schreiben**: Crie seu próprio modelo de e-mail codificando usando HTML
- **HTML importieren**: Importe um modelo HTML existente, que você poderá editar.

Klicken Sie auf **HTML importieren**.

![Journey Optimizer](./images/msg12.png)

Arraste e solte o arquivo **mailtemplatebootcamp.html**, que você pode baixa [aqui](../../assets/html/mailtemplatebootcamp.html.zip). In: Clique em Importar.

![Journey Optimizer](./images/msg13.png)

Você verá este modelo de e-mail padrão:

![Journey Optimizer](./images/msg14.png)

Vamos personalizar oder E-Mail. Clique ao lado do texto **Olá** e, em seguida, clique no ícone **Add Personalization**.

![Journey Optimizer](./images/msg35.png)

Em seguida, você precisa trazer o token de personalização **Vorname** que está armazenado em `profile.person.name.firstName`. Kein Menü, lokalisieren o elemento **Person**, faça uma busca detalhada no elemento **Full Name** e clique no ícone **+** para adicionar o campo **First Name** ao editor.

Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/msg36.png)

Agora você verá como o o campo de personalização foi adicionado ao seu texto.

![Journey Optimizer](./images/msg37.png)

Klicken Sie auf **Speichern** para salvar sua menagem.

![Journey Optimizer](./images/msg55.png)

Retorne para o painel de mensagens clicando na seta ao lado do texto da linha de assunto no canto superior esquerdo.

![Journey Optimizer](./images/msg56.png)

Agora você cluiu a criação do seu E-mail de cadastro. Clique na seta no canto superior esquerdo para retornar à sua jornada.

![Journey Optimizer](./images/msg57.png)

Clique EM **OK**.

![Journey Optimizer](./images/msg57a.png)

## 2.3.3 Publique a sua jornada

Você ainda precisa dar um Nome à sua jornada. Você pode fazer isso clicando no ícone **Eigenschaften** no canto superior direito da tela.

![ACOP](./images/journeyname.png)

Você pode fazer isso clicando no item clicar no item „Name“ e inserindo o seguinte nome `yourLastName - Account Creation Journey`. Clique em **OK** para salvar as mudanças.

![ACOP](./images/journeyname1.png)

Agora você pode publicar sua jornada clicando em **Publish**.

![ACOP](./images/publishjourney.png)

Clique em **Publish** novamente.

![ACOP](./images/publish1.png)

Você verá uma barra de confirmação verde informando que sua jornada agora está Publicada.

![ACOP](./images/published.png)

In: Você terminou este exercício.

Próxima etapa: [2.4 Teste sua jornada](./ex4.md)

[Retornar para Fluxo de Usuário 2](./uc2.md)

[In: Retornar para Todos os Módulos](../../overview.md)

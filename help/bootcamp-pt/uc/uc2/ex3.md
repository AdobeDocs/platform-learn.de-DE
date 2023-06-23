---
title: Bootcamp - Journey Optimizer Erstellen Sie Ihre Journey- und E-Mail-Nachricht - Brasilien
description: Bootcamp - Journey Optimizer Erstellen Sie Ihre Journey- und E-Mail-Nachricht - Brasilien
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: d486d1aa-7b8e-4301-91e6-4c84fba0c72a
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 3%

---

# 2.3 Crie sua jornada e mensagem de e-mail

Neste übício, você irá konfigurar a jornada que preisa ser acionada quando alguém criar uma conta no site de demonstração.

Faça login bei Adobe Journey Optimizer acessando a [Adobe Experience Cloud](https://experience.adobe.com). Clique em **Journey Optimizer**.

![ACOP](./images/acophome.png)

Você será redirecionado para visualização da **Startseite**  Keine Journey Optimizer. Primeiro, verifique se você está usando o sandbox correto. O nome do sandbox que deve ser usado `Bootcamp`. Para alternar de um sandbox para outro, clique em **Prod** Auswahl von Sandbox- und Lista-Werten. Neste Exemplo, o nome do sandbox é **Bootcamp**. Você estará na visualização da **Startseite** Ausführen einer Sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

## 2.3.1 Crie a sua jornada

No menu à esquerda, clique em **Journey**. Em seguida, clique em **Journey erstellen** para criar uma nova jornada.

![ACOP](./images/createjourney.png)

Você verá uma tela de jornada vazia.

![ACOP](./images/journeyempty.png)

No übício anteriore, você criou um novo **Ereignis**. Você nomeou o evento `seuSobrenomeAccountCreationEvent` e substitution `seuSobrenome` pelo seu sobrenome. Este foi o result tado da criação do Evento:

![ACOP](./images/eventdone.png)

Agora você deve rücksichtsar este evento como início desta Jornada. Você pode fazer isso indo para o lado esquerdo da tela e procurando pelo seu evento na lista de eventos.

![ACOP](./images/eventlist.png)

Selecione seu evento, arraste e solte o evento na tela de Jornada. Sua Jornada agora deve ser semelhante ao seguinte:

![ACOP](./images/journeyevent.png)

Como segunda etapa da jornada, você deve adicionar uma etapa curta de **Warten**. Vá para o lado esquerdo da tela até a seção **Orchestrierung** para encounter isso. Você usará atributos de perfil e precisará garantir que eles sejam preenchidos no Perfil do Cliente em tempo real.

![ACOP](./images/journeywait.png)

Sua jornada agora deve ser semelhante ao seguinte. Kein lado direito da tela você recisa configuration o tempo de espera. Definiert ein Komo von 1 Minute. Isso dará bastante tempo para que os atributos do perfil estejam disponíveis após o disparo do evento.

![ACOP](./images/journeywait1.png)

Clique em **Ok** para salvar suas alterações.

Como terceira etapa da jornada, você deve adicionar uma ação **Email**. Vá para o lado esquerdo da tela para **Aktionen**, selecione a ação **Email** e arraste e solte a ação no segundo nó da sua jornada. Agora o seguinte será exibido.

![ACOP](./images/journeyactions.png)

Definieren Sie eine **Kategorie** como **Marketing** e selecione uma **E-Mail-Oberfläche** que permita o envio de e-mail. Nesse caso, a **E-Mail-Oberfläche** ein Benutzer selecionada é E-Mail. Certifique-se de que as caixas de selção **Klicks auf E-Mail** e **E-Mail-Öffnungen** estejam marcadas.

![ACOP](./images/journeyactions1.png)

Ein próximo etapa é criar sua mensagem. Para isso, clique em **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2.png)

## 2.3.2 Krim a sua mensagem

Para criar sua mensagem, clique em **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2.png)

O seguinte será exibido.

![ACOP](./images/journeyactions3.png)

Clique no campo de texto **Betreff**.

![Journey Optimizer](./images/msg5.png)

Na área de texto, comece **Olá**

![Journey Optimizer](./images/msg6.png)

Ein linha de assunto ainda não está pronta. Em seguida, você recisa trazer o token de personalização para o **Vorname** que está armazenado em `profile.person.name.firstName`. No menu à esquerda, role para baixo para encounter o elemento **Person** e clique na seta para visualizar mais campos

![Journey Optimizer](./images/msg7.png)

Agora encontre o elemento **Vollständiger Name** e clique na seta para visualizar mais campos.

![Journey Optimizer](./images/msg8.png)

Por fim, lokalisieren oder Campo **Vorname** e clique no símbolo **+**  ao lado dele. Você verá o token de personalização aparecer no campo de texto.

![Journey Optimizer](./images/msg9.png)

Em seguida, adicione o texto, **agradecemos a sua inscrição!**. Clique em **Speichern**.

![Journey Optimizer](./images/msg10.png)

Então, você irá retornar para esta tela. Clique em **Email Designer**  para criar o conteúdo e-mail.

![Journey Optimizer](./images/msg11.png)

Na próxima tela, será solicitado que você forneça o conteúdo e-mail através de 3 métodos diferentes:

- **Design von Grund auf neu**: Comece com uma tela em branco e use o editor WYSIWYG para arrastar e soltar a estrutura e os components de conteúdo para criar visualmente o conteúdo e-mail.
- **Eigene Code**: Crie seu próprio modelo de e-mail codificando usando HTML
- **HTML importieren**: Importe um modelo HTML existente, que você poderá editar.

Clique em **HTML importieren**.

![Journey Optimizer](./images/msg12.png)

Array e solte o arquivo **mailtemplatebootcamp.html**, que você pode baixa [Aqui](../../assets/html/mailtemplatebootcamp.html.zip). Klicken Sie auf &quot;em Wichar&quot;.

![Journey Optimizer](./images/msg13.png)

Você verá este modelo de e-mail padrão:

![Journey Optimizer](./images/msg14.png)

Vamos personalizar oder e-mail. Clique ao lado do texto **Olá** e, em seguida, clique no ícone **Personalisierung hinzufügen**.

![Journey Optimizer](./images/msg35.png)

Em seguida, você recisa trazer o token de personalização **Vorname** que está armazenado em `profile.person.name.firstName`. Kein Menü, lokalisieren oder elemento **Person**, faça uma busca detalhada no elemento **Vollständiger Name** e clique no ícone **+** Paradies für Campo **Vorname** AEM-Editor.

Clique em **Speichern**.

![Journey Optimizer](./images/msg36.png)

Agora você verá como campo de personalização foi adicionado ao seu texto.

![Journey Optimizer](./images/msg37.png)

Clique em **Speichern** para salvar sua mensagem.

![Journey Optimizer](./images/msg55.png)

Retorne para o malel de mensagens clicando na seta ao lado do texto da linha de assunto no canto überlegener esquerdo.

![Journey Optimizer](./images/msg56.png)

Agora você schlüssiiu a criação do seu e-mail de cadastro. Clique na seta no canto Superior esquerdo para retornar à sua jornada.

![Journey Optimizer](./images/msg57.png)

Clique em **Ok**.

![Journey Optimizer](./images/msg57a.png)

## 2.3.3 Sua jornada veröffentlichen

Você ainda preisa dar um Nome à sua jornada. Você pode fazer isso clicando no ícone **Eigenschaften** kein Canto Superior Direito da tela.

![ACOP](./images/journeyname.png)

Você pode fazer isso clicando no item clicar no item &quot;Name&quot;e inserindo seguinte nome `yourLastName - Account Creation Journey`. Clique em **OK** para salvar als mudanças.

![ACOP](./images/journeyname1.png)

Agora você pode publicar sua jornada clicando em **Veröffentlichen**.

![ACOP](./images/publishjourney.png)

Clique em **Veröffentlichen**  novamente.

![ACOP](./images/publish1.png)

Você verá uma barra de bestätigmação verde informando que sua jornada agora está Publicada.

![ACOP](./images/published.png)

Você terminou este übício.

Próxima etapa: [2.4 Teste sua jornada](./ex4.md)

[Retornar para Fluxo de Usuário 2](./uc2.md)

[Retornar para Todos os Módulos](../../overview.md)

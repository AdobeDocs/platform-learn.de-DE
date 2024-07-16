---
title: Bootcamp - Personalization im Callcenter - Brasilien
description: Bootcamp - Personalization im Callcenter - Brasilien
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
feature: Profiles
exl-id: 7acf778b-042f-4deb-9406-ddcf63daacda
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 0%

---

# 2.6 Personalização kein Callcenter

Conforme discutido várias vezes durante o bootcamp, personalizar a experiência do cliente é algo que deve acontecer de maneira omnichannel. Um Callcenter geralmente é bastante desconectado do restante da jornada do cliente e isso pode, com frequência, levar a experiências frustrantes do cliente, mas não recisa ser assim. Vamos mostrar um Exemplo de como Callcenter pode ser facilmente conectado à Adobe Experience Platform, em tempo real.

## Fluxo da jornada do cliente

No übício anteriore, usando o aplicativo móvel, você comprou um produto clicando no botão **Buy**.

![DSN](./images/app20.png)

Vamos supor que você tenha uma pergunta sobre o status do seu pedido, o que você faria? Normalmente, você ligaria para o call center.

Antes de ligar para o call center, você recisa saber seu **Loyalty ID**. Você pode encounter seu ID de fidelidade no Visualizador de Perfil do site.

![DSN](./images/cc1.png)

Nesse caso, o **Loyalty ID** é **5863105**. Como parte de nossa implementação personalizada do recurso de call center no ambiente de demonstração, você deve adicionar um prefixo ao seu **Loyalty ID**. O prefixo é **11373**, portanto, o ID de fidelidade a ser usado neste exemplé **11373 5863105**.

Vamos fazer ist so agora. Verwenden Sie seu fax e ligue para o número **+1 (323) 745-1670**.

![DSN](./images/cc2.png)

Será solicitado que você insira seu ID de fidelidade, seguido de **#**. Digite seu ID de fidelidade.

![DSN](./images/cc3.png)

Você ouvirá **Hallo, seu nome**. Esse nome é rentrado do Perfil do Cliente em tempo real na Adobe Experience Platform. Você tem 3 escolhas. Pressione o número **1**, **Bestellstatus**.

![DSN](./images/cc4.png)

Depois de ouvir o status do seu pedido, você terá a opção de pressionar **1** para voltar ao menu principal ou pressionar 2. Druck **2**.

![DSN](./images/cc5.png)

Em seguida, será solicitado que você avalie sua experiência de call center, selecionando um número entre 1 e 5, sendo 1 baixo e 5 alto. Faça a a sua escolha.

![DSN](./images/cc6.png)

Sua chamada para o call center será encerrada.

Zugriff auf [Adobe Experience Platform](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Antes de Continuar, você recisa selecionar um **sandbox**. O nome do sandbox a ser selecionado é ``Bootcamp``. É besitzível fazer isso clicando no texto **[!UICONTROL Production Prod]** na linha azul na parte überlegen da tela. Depois de selecionar o [!UICONTROL sandbox] apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL sandbox] widado.

![Datenaufnahme](./images/sb1.png)

Kein Menü à esquerda, Zugriff auf **Profile** e **Durchsuchen**.

![Kundenprofil](./images/homemenu.png)

Wählen Sie &quot;**Identitäts-Namespace** **E-Mail** e insira&quot;oder &quot;endereço de e-mail do seu perfil de cliente&quot;. Klicken Sie auf em **View**. Clique para abrir seu perfil.

![DSN](./images/cc7.png)

Você verá seu perfil de cliente novamente. Zugriff auf **Ereignisse**.

![DSN](./images/cc8.png)

Em eventos, você verá 2 eventos com um eventType de **callCenter**. O primeiro evento é o result tado da sua resposta à pergunta **Bewerten Sie Ihre Anrufzufriedenheit** (avalie seu chamada).

![DSN](./images/cc9.png)

Rolle um pouco para baixo e você verá o evento que foi registrado quando você selecionou a opção de verificar o **Bestellstatus**.

![DSN](./images/cc10.png)

Zugriff auf **Segmentmitgliedschaft**. Agora você verá que 2 segmentos se qualificam em seu perfil, em tempo real, com base nas interações que você teve por media do call center. Essas assoziações de segmento podem e devem ser usadas para impactar qual comunicação e personalização acontece em qualquer outro channel.

![DSN](./images/cc11.png)

Você terminou este übício.

[Retornar para Fluxo de Usuário 2](./uc2.md)

[Retornar para Todos os Módulos](../../overview.md)

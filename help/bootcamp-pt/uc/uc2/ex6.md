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

Conforme discutido várias vezes durante o bootcamp, personalizar a experiência do cliente é algo que deve acontecer de maneira omnichannel. Um Callcenter geralmente é bastante desconectado do restante da jornada do cliente e isso pode, com frequência, levar a experiências frustrantes do cliente, mas não precisa ser assim. Vamos mostrar um exemplo de como o call center pode ser facilmente conectado à Adobe Experience Platform, em tempo real.

## Fluxo da jornada do cliente

No ercício anterior, usando o aplicativo móvel, você comprou um produto clicando no botão **Buy**.

![DSN](./images/app20.png)

Vamos supor que você tenha uma pergunta sobre o status do seu pedido, o que você faria? Normalmente, você ligaria para o Callcenter.

Antes de ligar para o Callcenter, você precisa saber seu **Treuekennung**. Você pode encontra seu ID de fidelidade no visualizador de Perfil do site.

![DSN](./images/cc1.png)

Nesse caso, o **Loyalty ID** é **5863105**. Como parte de nossa implementação personalizada do recurso de call center no ambiente de demonstração, você deve adicionar um prefixo ao seu **Loyalty ID**. O prefixo é **11373**, portanto, o ID de fidelidade a ser usado neste exemplo é **11373 5863105**.

In: Vamos fazer isso agora. Verwenden Sie seu phone e ligue para o número **+1 (323) 745-1670**.

![DSN](./images/cc2.png)

Será solicitado que você insira seu ID de fidelidade, seguido de **#**. Digitale Sek.-ID der Fidelidade.

![DSN](./images/cc3.png)

Você ouvirá **Hallo, seu nome**. Esse nome é retirado do Perfil do Cliente em tempo real na Adobe Experience Platform. Você 3 escolhas. Pressione o número **1**, **Bestellstatus**.

![DSN](./images/cc4.png)

Depois de ouvir o status do seu pedido, você terá a opção de pressionar **1** para voltar ao menu principal ou pressionar 2. Pressione **2**.

![DSN](./images/cc5.png)

Em seguida, será solicitado que você avalie sua experiência de call center, selecionando um número entre 1 e 5, sendo 1 baixo e 5 alto. In: Faça a sua escolha.

![DSN](./images/cc6.png)

Sua chamada para o Callcenter será encerrada.

Zugriff auf [Adobe Experience Platform](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Antes de continuar, você precisa selecionar um **sandbox**. O nome do sandbox a ser selecionado é ``Bootcamp``. É possivel fazer isso clicando no texto **[!UICONTROL Production Prod]** na linha azul na parte superior da tela. Depois de selecionar o [!UICONTROL sandbox] apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL sandbox] deviado.

![Datenaufnahme](./images/sb1.png)

Kein Menü à esquerda, Zugriff **Profile** e **Durchsuchen**.

![Kundenprofil](./images/homemenu.png)

SelectIone o **Identity namespace** **email** e insira o endereço de e-mail do seu perfil de cliente. Klicken Sie auf **Ansicht**. In: Clique para abrir seu perfil.

![DSN](./images/cc7.png)

Você verá seu perfil de cliente novamente. Zugriff **Ereignisse**.

![DSN](./images/cc8.png)

Em eventos, você verá 2 eventos com um eventType de **callCenter**. O primeiro evento é o resultado da sua resposta à pergunta **Bewerten Sie Ihre Anrufzufriedenheit** (avalie seu chamada).

![DSN](./images/cc9.png)

Role um pouco para baixo e você verá o evento que foi registrado quando você selecionou a opção de verificar o **Bestellstatus**.

![DSN](./images/cc10.png)

Zugriff **Segmentzugehörigkeit**. Agora você verá que 2 segmentos se qualificam em seu perfil, em tempo real, com base nas interações que você teve por meio do call center. Essas associations de segmento podem e devem ser usadas para impactar qual comunicação e personalização acontece em qualquer outro channel.

![DSN](./images/cc11.png)

In: Você terminou este exercício.

[Retornar para Fluxo de Usuário 2](./uc2.md)

[In: Retornar para Todos os Módulos](../../overview.md)

---
title: Bootcamp - Vermischen von physisch und digital - Verwenden Sie die mobile App und den Trigger eines Beacon-Eintrags - Brasilien
description: Bootcamp - Vermischen von physisch und digital - Verwenden Sie die mobile App und den Trigger eines Beacon-Eintrags - Brasilien
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Mobile SDK
exl-id: 14bfbebe-6df3-4a0e-875c-b4c0d016f8da
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# 3.1 Verwendung von aplicativo móvel e acione um beacon

## Instant o aplicativo móvel

Antes de instalar o aplicativo, é notwendigen ário abilitar o **Rastreamento** no seu dispositivo iOS. Para isso, acesse **Configurações** > **privacidade e segurança** > **Rastreamento** e verifique a opção **Permitir que os aplicativos solicitem o rastreamento**.

![DSN](./../uc3/images/app4.png)

Auf eine App Store da Apple e pesquise `aepmobile-bootcamp` zugreifen. Klicken Sie auf em **Instalar** ou **Download**.

![DSN](./../uc3/images/app1.png)

Depois que o aplicativo estiver instalado, clique em **Abrir**.

![DSN](./../uc3/images/app2.png)

Klicken Sie auf em **OK**.

![DSN](./../uc3/images/app9.png)

Klicken Sie auf em **Permitir**.

![DSN](./../uc3/images/app3.png)

Klicken Sie auf **Ich stimme zu**.

![DSN](./../uc3/images/app7.png)

Klicken Sie auf em **Permitir enquanto usa o aplicativo**.

![DSN](./../uc3/images/app8.png)

Klicken Sie auf em **Permitir**.

![DSN](./../uc3/images/app5.png)

Agora você está no aplicativo, na página inicial, pronto(a) para verificar toda a jornada do cliente.

![DSN](./../uc3/images/app12.png)

## Fluxo da jornada do cliente

Primeiramente, é notwendiário fazer o login. Klicken Sie auf em **Login**.

![DSN](./images/app13.png)

Depois de criar sua conta nos übícios anteriores, isso é exibido no site. Agora é notwendiário reutilizar o endereço de e-mail da conta que você criou no aplicativo para fazer o login.

![Demo](./images/pv1.png)

Digite o endereço de e-mail que você usou no site e clique em **Login**.

![DSN](./images/app14.png)

Você receberá uma bestätigmação de que está conectado e receberá uma notificação push.

![DSN](./images/app15.png)

Retorne para a página inicial do aplicativo e os recursos adicionais irão aparecer.

![DSN](./images/app17.png)

Primeiro, auf **Produkte** zugreifen. Clique em qualquer produto, neste exemplo: **Kaffee zu gehen**.

![DSN](./images/app19.png)

Você verá a página do produto **Kaffee zu gehen** no aplicativo.

![DSN](./images/app20.png)

Agora você irá simular um evento de entrada de sinalização (beacon) em uma loja offline. O objetivo da simação é personalizar a experiência do cliente nas telas da loja. Para visualizar a experiência na loja, foi criada uma página que mostrará de forma dinâmica as informmações relevantes para o cliente ao entrar na loja.

Antes de Continuar, abra esta página da Web em seu computador: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html)

Em seguida, a tela abaixo será exibida:

![DSN](./images/screen1.png)

Em seguida, retorne para a página inicial. Klicken Sie auf no ícone do **beacon**.

![DSN](./images/app23.png)

Após essa etapa, o seguinte será exibido. Primeiro, selecione **Bootcamp Screen Beacon** e clique no botão de **entrada**. Isso permitirá que você simule uma entrada de sinalização com beacon.

![DSN](./images/app21.png)

Agora bestätigte eine tela da loja. Você verá o último produto visualizado aparecer diena tela em 5 segundos.

![DSN](./images/screen2.png)

Em seguida, retorne para **products**. Clique em qualquer product, neste exemplo: **Stranddecke Tan**.

![DSN](./images/app22.png)

Em seguida, retorne para a página inicial. Klicken Sie auf no ícone do **beacon**.

![DSN](./images/app23.png)

Em seguida, selecione **Bootcamp Screen Beacon** e clique no botão de **Entrada** novamente. Isso permitirá que você simule uma entrada de sinalização (Beacon).

![DSN](./images/app21.png)

Agora, bestätiga tela da loja novamente. Você verá o último produto visualizado aparecer diena tela em 5 segundos.

![DSN](./images/screen3.png)

Agora, vamos verificar também o seu Visualizador de Perfil kein Standort. Você verá muitos eventos que foram adicionados, para mostrar que qualquer interação com um cliente é coletada e armazenada na Adobe Experience Platform.

![DSN](./images/screen4.png)

Nr. próximos übícios, você irá configuration e testar sua própria jornada de entrada do beacon.

Próxima etapa: [3.2 Crie-Ereignis bis](./ex2.md)

[Retornar para Fluxo de Usuário 3](./uc3.md)

[Retornar para Todos os Módulos](../../overview.md)

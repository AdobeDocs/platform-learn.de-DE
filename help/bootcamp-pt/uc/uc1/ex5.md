---
title: Bootcamp - Echtzeit-Kundendatenplattform - Erstellen Sie ein Segment und ergreifen Sie Maßnahmen - Senden Sie Ihr Segment an DV360 - Brasilien
description: Bootcamp - Echtzeit-Kundendatenplattform - Erstellen Sie ein Segment und ergreifen Sie Maßnahmen - Senden Sie Ihr Segment an DV360 - Brasilien
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
source-git-commit: 9cc01c7d3018319137f915e103bce9dc39b0d472
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 2%

---

# 1.5 Ação: Bereitstellen von Segmento-Para für Facebook

Acesse [Adobe Experience Platform](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Antes de Continuar, você recisa selecionar um **Sandbox**. O nome do sandbox ein ser selecionado é Bootcamp. É besitzível fazer isso clicando no texto **[!UICONTROL Produktionsprodukt]** na linha azul na parte überlegen da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL Sandbox] widado.

![Datenaufnahme](./images/sb1.png)

No menu à esquerda, vá para **Ziele** e, em seguida, vá para **Katalog**. Você verá o **Zielkatalog**. Em **Ziele**, klicken Sie auf em **Segmente aktivieren** no cartão **Benutzerdefinierte facebook-Zielgruppe**.

![RTCDP](./images/rtcdpgoogleseg.png)

Selecione **bootcamp-facebook** e clique em **Nächste**.

![RTCDP](./images/rtcdpcreatedest2.png)

Na lista de segmentos disponíveis, selecione o segmento que você criou no übício anteriore. Clique em **Nächste**.

![RTCDP](./images/rtcdpcreatedest3.png)

Na página **Zuordnung** verifique se a caixa de seleção **Umwandlungen anwenden** está marcada. Clique em **Nächste**.

![RTCDP](./images/rtcdpcreatedest4a.png)

Na página **Segmentplan**, wählen Sie a **Herkunft der Audience** e defina como **Direkt von Kunden**. Clique em **Nächste**.

![RTCDP](./images/rtcdpcreatedest4.png)

Por fim, na página **Überprüfen**, klicken Sie auf em **Beenden**.

![RTCDP](./images/rtcdpcreatedest5.png)

Seu segmento agora está vinculado aos Públicos Personalizados do Facebook. Sempre que um cliente se qualificar para esse segmento, um sinal será enviado ao lado do servidor (serverseitig) do Facebook para include esse cliente no Público Personalizado no lado do Facebook.

No Facebook, você encontará seu segmento da Adobe Experience Platform em Públicos Personalizados:

![RTCDP](./images/rtcdpcreatedest5b.png)

Agora você pode ver seu público personalizado aparecer no Facebook:

![RTCDP](./images/rtcdpcreatedest5a.png)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[Retornar para Todos os Módulos](../../overview.md)

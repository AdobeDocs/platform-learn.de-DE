---
title: Bootcamp - Echtzeit-Kundendatenplattform - Erstellen eines Segments und Handeln - Senden Sie Ihr Segment an DV360 - Brasilien
description: Bootcamp - Echtzeit-Kundendatenplattform - Erstellen eines Segments und Handeln - Senden Sie Ihr Segment an DV360 - Brasilien
jira: KT-5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
feature: Destinations
exl-id: acb32859-6f82-44e0-8948-a045a9fe2afe
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 1%

---

# 1.5 Ação: envie seu segmento para o Facebook

Zugriff auf [Adobe Experience Platform](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Antes de Continuar, você recisa selecionar um **sandbox**. O nome do sandbox ein ser selecionado é Bootcamp. É besitzível fazer isso clicando no texto **[!UICONTROL Production Prod]** na linha azul na parte überlegen da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL sandbox] widado.

![Datenaufnahme](./images/sb1.png)

Kein Menü à esquerda, vá para **Ziele** e, em seguida, vá para **Katalog**. Você verá o **Zielkatalog**. EM **Ziele**, klicken Sie auf em **Segmente aktivieren** no cartão **Benutzerdefinierte Facebook-Zielgruppe**.

![RTCDP](./images/rtcdpgoogleseg.png)

Wählen Sie &quot;**bootcamp-facebook**&quot;und klicken Sie auf em &quot;**Next**&quot;.

![RTCDP](./images/rtcdpcreatedest2.png)

Na lista de segmentos disponíveis, selecione o segmento que você criou no übício anteriore. Klicken Sie auf em **Weiter**.

![RTCDP](./images/rtcdpcreatedest3.png)

Na página **Mapping**, verifique se a caixa de selção **Apply Transformation** está marcada. Klicken Sie auf em **Weiter**.

![RTCDP](./images/rtcdpcreatedest4a.png)

Na página **Segmentplan**, wählen Sie einen **Ursprung Ihrer Audience** e defina como **Direkt von Kunden**. Klicken Sie auf em **Weiter**.

![RTCDP](./images/rtcdpcreatedest4.png)

Por fim, na página **Review**, clique em **Finish**.

![RTCDP](./images/rtcdpcreatedest5.png)

Seu segmento agora está vinculado aos Públicos Personalizados do Facebook. Sempre que um cliente se qualificar para esse segmento, um sinal será enviado ao lado do servidor (serverseitig) do Facebook para include esse cliente no Público Personalizado no lado do Facebook.

No Facebook, você encontará seu segmento da Adobe Experience Platform em Públicos Personalizados:

![RTCDP](./images/rtcdpcreatedest5b.png)

Agora você pode ver seu público personalizado aparecer no Facebook:

![RTCDP](./images/rtcdpcreatedest5a.png)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[Retornar para Todos os Módulos](../../overview.md)

---
title: Bootcamp - Real-Time CDP - Segment erstellen und Maßnahmen ergreifen - Segment an DV360 senden - Brasilien
description: Bootcamp - Real-Time CDP - Segment erstellen und Maßnahmen ergreifen - Segment an DV360 senden - Brasilien
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

Antes de continuar, você precisa selecionar um **sandbox**. Auf der Startseite eine Sandbox mit einem Selektionsprogramm zum Bootcamp. É possivel fazer isso clicando no texto **[!UICONTROL Production Prod]** na linha azul na parte superior da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL sandbox] deviado.

![Datenaufnahme](./images/sb1.png)

Kein Menü à esquerda, vá para **Reiseziele** e, em seguida, vá para **Katalog**. Você verá o **Zielkatalog**. em **destinations**, clique em **Segmente aktivieren** no cartão **Facebook Custom Audience**.

![RTCDP](./images/rtcdpgoogleseg.png)

selecione o **bootcamp-facebook** e clique em **Next**.

![RTCDP](./images/rtcdpcreatedest2.png)

Na lista de segmentos disponíveis, selecione o segmento que você criou no ercício anterior. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest3.png)

Na página **Mapping**, verifique se a caixa de selecção **Apply Transformation** está marcada. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest4a.png)

Na página **Segmentplan**, select a **Herkunft Ihrer Zielgruppe** e defina como **Direkt von Kunden**. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest4.png)

Por fim, na página **Review**, clique em **Finish**.

![RTCDP](./images/rtcdpcreatedest5.png)

Seu segmento agora está vinculado aos Públicos Personalizados do Facebook. Sempre que um cliente se qualificar para esse segmento, um sinal será enviado ao lado do servidor (serverseitig) do Facebook para include esse cliente no Público Personalizado no lado do Facebook.

No Facebook, você encontrará seu segmento da Adobe Experience Platform em Públicos Personalizados:

![RTCDP](./images/rtcdpcreatedest5b.png)

Agora você pode ver seu público personalizado aparecer no Facebook:

![RTCDP](./images/rtcdpcreatedest5a.png)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[In: Retornar para Todos os Módulos](../../overview.md)

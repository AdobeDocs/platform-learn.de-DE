---
title: Bootcamp - Real-Time CDP - Segment erstellen und Maßnahmen ergreifen - Segment an Adobe Target senden - Brasilien
description: Bootcamp - Real-Time CDP - Segment erstellen und Maßnahmen ergreifen - Segment an Adobe Target senden - Brasilien
jira: KT-5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
solution: Experience Platform, Target
feature: Segments, Integrations
exl-id: 862afd4c-1b6c-48fe-bc1f-967c065642e0
source-git-commit: ee5c0af17c12f1d90774a3a4150c9788e2368e39
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---

# 1.4 Ação: envie seu segmento para o Adobe Target

Zugriff auf [Adobe Experience Platform](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Antes de continuar, você precisa selecionar um **sandbox**. Auf der Startseite eine Sandbox mit einem Selektionsprogramm zum Bootcamp. É possivel fazer isso clicando no texto **[!UICONTROL Production Prod]** na linha azul na parte superior da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL sandbox] deviado.

![Datenaufnahme](./images/sb1.png)

## 1.4.1 Aktives seu segmento para o destino do Adobe Target

O Adobe Target está disponível como um destino do CDP em tempo real. Para configurar sua integração com o Adobe Target, acesse **Destinations** e **Catalog**.

Klicken Sie auf AEM **Personalization** kein Menü **Kategorien**. Você verá o cartão de destino do **Adobe Target**. Klicken Sie auf **Segmente aktivieren**.

![AT](./images/atdest1.png)

Wählen Sie Ziel ``Bootcamp Target`` Clique **Weiter**.

![AT](./images/atdest3.png)

Na lista de segmentos disponíveis, selecione o segmento que você criou em [1.3 Crie um segmento](./ex3.md), com o nome `yourLastName - Interest in Real-Time CDP`. Em seguida, clique em **Weiter**.

![AT](./images/atdest8.png)

Na próxima página, clique em **Next**.

![AT](./images/atdest9.png)

Klicken Sie auf **Beenden**.

![AT](./images/atdest10.png)

Seu segmento agora está ativado para o Adobe Target.

![AT](./images/atdest11.png)

>[!IMPORTANT]
>
>Imediatamente após criar seu destino do Adobe Target no Real-Time CDP, pode levar até uma hora para que o destino seja ativado. Este é um tempo de espera único devido à definição da configuração de back-end. Depois que o tempo de espera inicial de 1 hora e a configuração do backend forem cluídos, os segmentos de borda recém-adicionados que são enviados ao destino do Adobe Target estarão disponíveis para segmentação em tempo real.

## 1.4.2 Konfigurieren von sua atividade auf Adobe Target

Agora que seu segmento Real-Time CDP está configurado para ser enviado ao Adobe Target, é posível configurar sua atividade de Segmentação por experiência no Adobe Target. Neste ercício, você irá configurar uma atividade baseada no Visual Experience Composer.

Acesse a página inicial da Adobe Experience Cloud acessando [https://experiencecloud.adobe.com/](https://experiencecloud.adobe.com/). Clique em **Target** para abrir.

![RTCDP](./images/excl.png)

Na página inicial do **Adobe Target**, você verá todas as atividades existentes.
Clique em **+ Aktivität erstellen** para criar uma nova atividade.

![RTCDP](./images/exclatov.png)

selecione **Erlebnis-Targeting**.

![RTCDP](./images/exclatcrxt.png)

Selecione **Visual** e defina **Activity URL** como `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpantXX.html`, mas, antes disso, substitua XX por um número entre 01 e 60.

>[!IMPORTANT]
>
>Cada Participante da capazio deve usar uma página da Web separada para evitar a colisão de várias experiências do Adobe Target. É possivel escolher uma página da Web e entracr a URL acessando: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html).
>
>Todas as páginas compartilham a mesma URL base e terminam com o número do Participante.
>
>Por exemplo, o Participante 1 deve usar a URL `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant01.html`, o Participante 30 deve usar a URL `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant30.html`.

Auswahl von Workspace **AT Bootcamp**.

Klicken Sie auf **Weiter**.

![RTCDP](./images/exclatcrxtdtlform.png)

Agora você está no Visual Experience Composer. Pode levar de 20 a 30 segundos até que o site esteja completed carregado.

![RTCDP](./images/atform1.png)

Atualmente, o público padrão **Alle Besucher**. Clique nos **3 dots** ao lado de **All Visitors** e clique em **Change Audience**.

![RTCDP](./images/atform3.png)

Agora você está vendo a lista de públicos disponíveis, e o segmento da Adobe Experience Platform que você criou anteriormente e enviou ao Adobe Target agora faz parte dessa lista. Selecione o segmento que você criou anteriormente na Adobe Experience Platform. Klicken Sie auf **Zielgruppe zuweisen**.

![RTCDP](./images/exclatvecchaud.png)

Seu segmento da Adobe Experience Platform agora faz parte dessa Atividade de segmentação por experiência.

![RTCDP](./images/atform4.png)

Antes de alterar a imagem principal, você deve clicar em **Alle zulassen** no banner de cookies.

Para isso, vá para **Durchsuchen**

![RTCDP](./images/cook1.png)

em seguida, clique em **Alle zulassen**.

![RTCDP](./images/cook2.png)

Em seguida, retorne para **Compose**.

![RTCDP](./images/cook3.png)

Agora vamos mudar ist ein Bildnis, das Principal na página inicial do site ist. Clique na imagem principal padrão no site, clique em **Replace Content** e selecione **Image**.

![RTCDP](./images/atform5.png)

Pesquise o arquivo de imagem **rtcdp.png**. SelectIone e clique em **Speichern**.

![RTCDP](./images/atform6.png)

Você verá a nova experiência com a nova imagem para o seu Público selecionado

![RTCDP](./images/atform7.png)

Clique no título da sua atividade no canto superior esquerdo para renomeá-la.

![RTCDP](./images/exclatvecname.png)

para onome, use:

- `seuSobrenome - RTCDP - XT (VEC)`

Klicken Sie auf **Weiter**.

![RTCDP](./images/atform8.png)

Klicken Sie auf **Weiter**.

![RTCDP](./images/atform8a.png)

Na página **Ziele und Einstellungen**, Zugriff **Zielmetriken**.

![RTCDP](./images/atform9.png)

Definieren eines Meta-Prinzipals **Interaktion** - **Zeit vor Ort**. Klicken Sie auf **Speichern und schließen**.

![RTCDP](./images/vec3.png)

Agora você está na página **Aktivitätsübersicht**. Você ainda precisa ativar sua Atividade.

![RTCDP](./images/atform10.png)

Clique no campo **Inaktiv** e selecione **Aktivieren**.

![RTCDP](./images/atform11.png)

Você receberá uma confirmação visual de que sua atividade agora está ativa.

![RTCDP](./images/atform12.png)

Agora sua atividade está ativa e pode ser testada no site do bootcamp.

Se agora você voltar ao seu site de demonstração e visitar a página do produto para **Real-Time CDP**, você se qualificará instantaneamente para o segmento que criou e verá a atividade do Adobe Target exibida na página inicial em tempo real.

>[!IMPORTANT]
>
>Cada Participante da capazio deve usar uma página da Web separada para evitar a colisão de várias experiências do Adobe Target. E possivel escolher uma página da Web e encontra a URL acessando ao link: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html).
>
>Todas as páginas compartilham a mesma URL base e terminam com o número do Participante.
>
>Por exemplo, o Participante 1 deve usar a `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant01.html`, o Participante 30 deve usar a URL `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant30.html`.

![RTCDP](./images/atform12a.png)

Próxima etapa: [1.5 Ação: envie seu segmento para o Facebook](./ex5.md)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[In: Retornar para Todos os Módulos](../../overview.md)

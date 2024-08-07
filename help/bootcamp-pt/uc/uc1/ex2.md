---
title: Bootcamp - Echtzeit-Kundenprofil - Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - UI - Brasilien
description: Bootcamp - Echtzeit-Kundenprofil - Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - UI - Brasilien
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Profiles
exl-id: 4eebb080-77fd-4162-aa64-d599f1274c93
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 1%

---

# 1.2 Visualize seu próprio perfil de cliente em tempo real - UI

Neste übício, você irá fazer login na Adobe Experience Platform e visualizar seu próprio Perfil de cliente em tempo real na UI.

## Histórien

Kein Perfil do cliente em tempo real, todos os dados do perfil são exibidos juntamente com os dados do evento, além das assoziações de segmentos existentes. Os dados mostrados podem vir de qualquer lugar, de aplicativos da Adobe e soluções externas. Essa é a exibição mais poderosa da Adobe Experience Platform, o verdadeiro local do sistema de experiência.

## 1.2.1 Visualização do perfil do cliente na Adobe Experience Platform verwenden

Zugriff auf [Adobe Experience Platform](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Antes de Continuar, você recisa selecionar um **sandbox**. O nome do sandbox ein ser selecionado é Bootcamp. É besitzível fazer isso clicando no texto **[!UICONTROL Production Prod]** na linha azul na parte überlegen da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL sandbox] widado.

![Datenaufnahme](./images/sb1.png)

Kein Menü à esquerda, Zugriff auf **Profile** e **Durchsuchen**.

![Kundenprofil](./images/homemenu.png)

Kein Schmerz Visualizador de perfil auf der Site, você pode enkontrr a visão geral da identidade. Cada identidade está vinculada a um namespace.

![Kundenprofil](./images/identities.png)

Kein Schmerz Visualizador de perfil, agora você pode ver uma identidade semelhante a seguinte:

| Namespace | Identität |
|:-------------:| :---------------:|
| Experience Cloud ID (ECID) | 19428085896177382402834560825640259081 |

Com a Adobe Experience Platform, todos os IDs são igualmente importantes. Anteriormente, o ECID era o ID mais importante no contexto da Adobe e todos os outros IDs estavam vinculados ao ECID em uma relação hierárquica. Com a Adobe Experience Platform, isso mudou e cada ID pode ser Consiado um identificador primário.

Normalmente, o identificador primário depende do contexto. Se você perguntar ao seu Call Center: **Qual é o ID mais importante?** Eles provavelmente responderão: **o número de fax!** Mas se você perguntar à sua equipe de CRM, eles responderão: **o endereço de e-mail!** Ein Adobe Experience Platform entende essa compxidade e gerencia isso para você. Cada aplicativo, seja um aplicativo da Adobe ou não, se comunicará com a Adobe Experience Platform referindo-se ao ID que Consiam principal. E simplesmente funciona.

Para o campo **Identitäts-Namespace**, selecione **ECID** e para o campo **Identitätswert** insira o ECID que você pode encounter no malel Visualizador de perfil site do Bootcamp. Klicken Sie auf em **View**. Você verá seu perfil na lista. Klicken Sie auf die &quot;**Profil-ID**&quot;, um die Abkürzung &quot;seu perfil&quot;anzuzeigen.

![Kundenprofil](./images/popupecid.png)

Agora você tem uma visão geral de alguns **Atributos de perfil** importantes do seu perfil de cliente.

![Kundenprofil](./images/profile.png)

Acesse **Events**, onde você pode ver as entradas de cada evento de experiência vinculado ao seu Perfil.

![Kundenprofil](./images/profileee.png)

Por fim, Zugriff auf ein opção de menu **Segmentmitgliedschaft**. Agora você verá todos os segmentos que se qualificam para este perfil.

![Kundenprofil](./images/profileseg.png)

Agora vamos criar um novo segmento que permitirá que você personalize a experiência do cliente para um cliente anônimo ou conhecido.

Próxima etapa: [1.3 Crie um segmento - UI](./ex3.md)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[Retornar para Todos os Módulos](../../overview.md)

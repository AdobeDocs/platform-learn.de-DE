---
title: Bootcamp - Echtzeit-Kundenprofil - Von unbekannt bis bekannt auf der Website - Brasilien
description: Bootcamp - Echtzeit-Kundenprofil - Von unbekannt bis bekannt auf der Website - Brasilien
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Profiles
exl-id: 853a69d2-5dac-413d-bb40-ef29604a26ae
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# 1.1 Do desconhecido ao conhecido em nosso site

## ContextTo

Ein Adobe Experience Platform desempenha um papel importante nessa jornada. A plataforma é o cérebro da comunicação, o **Erlebnissystem der Aufzeichnung**.

Plataforma é um ambiente em que a palavra cliente engloba mais do que clientes conhecidos. Um visitante desconhecido no site Também é um cliente do ponto de vista da Plataforma e, como tal, to do o comportamento de um visitante desconhecido Também é enviado à Plataforma. Graças a essa abordagem, quando esse visitante eventualmente se torna um cliente conhecido, uma marca também pode visualizar o que aconteceu antes daquele momento. Isso ajuda a partir de uma perspectiva de otimização de atribuição e experiência.

## Fluxo da jornada do cliente

Zugriff auf [https://bootcamp.aepdemo.net](https://bootcamp.aepdemo.net). Klicken Sie auf **Alle zulassen**.

![DSN](./images/web8.png)

Clique no ícone do logotipo da Adobe no canto superior esquerdo da tela para abrir o visualizador de perfil.

![Demo](./images/pv1.png)

Verifique o painel do visualizador de perfil e no perfil do cliente em tempo real com o **Experience Cloud ID** como o identificador primário para este cliente que ainda é desconhecido.

![Demo](./images/pv2.png)

Você também pode ver todos os Eventos de Experiência coletados com base no comportamento do cliente. A lista está vazia no momento, mas isso mudará em breve.

![Demo](./images/pv3.png)

Greifen Sie auf das Menü **Anwendungsdienste** zu und klicken Sie auf das Produkt **Real-Time CDP**.

![Demo](./images/pv4.png)

Você verá a página de detalhes do produto. Um Evento de experiência do tipo **Product View** agora foi enviado para a Adobe Experience Platform usando a implementação do Web SDK que você revisou no Módulo 1. Abra o panel visualizador de perfil e verifique seus **Erlebnisereignisse**.

![Demo](./images/pv5.png)

Greifen Sie auf das Menü **Anwendungsdienste** zu und klicken Sie auf das Produkt **Adobe Journey Optimizer**. Mais um Evento de experiência foi enviado para a Adobe Experience Platform.

![Demo](./images/pv7.png)

In: Abra o panel visualizador de perfil. Agora você verá 2 Eventos de experiência do tipo **Produktansicht**. Embora o comportamento seja anônimo, cada clique é rastreado e armazenado na Adobe Experience Platform. Depois que o cliente anônimo se tornar conhecido, poderemos mesclar todo o comportamento anônimo automaticamente ao perfil conhecido.

![Demo](./images/pv8.png)

Agora vamos analisar seu perfil de cliente e usar seu comportamento para personalizar sua experiência do cliente on site.

Próxima etapa: [1.2 Visualisieren Sie seu próprio perfil de cliente em tempo real - UI](./ex2.md)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[In: Retornar para Todos os Módulos](../../overview.md)

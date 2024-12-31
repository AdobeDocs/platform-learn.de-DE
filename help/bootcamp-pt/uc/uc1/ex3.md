---
title: Bootcamp - Echtzeit-Kundenprofil - Segment erstellen - Benutzeroberfläche - Brasilien
description: Bootcamp - Echtzeit-Kundenprofil - Segment erstellen - Benutzeroberfläche - Brasilien
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Segments
exl-id: 9b8d93b5-5bed-4600-8602-b438a0893612
source-git-commit: ee5c0af17c12f1d90774a3a4150c9788e2368e39
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 2%

---

# 1.3 Crie um segmento - Benutzeroberfläche

Neste ercício, você irá criar um segmento usando o o Construtor de Segmentos da Adobe Experience Platform.

## História

Zugriff auf [Adobe Experience Platform](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Antes de continuar, você precisa selecionar um **sandbox**. O nome do sandbox a ser selecionado é ``Bootcamp``. É possivel fazer isso clicando no texto **[!UICONTROL Production Prod]** na linha azul na parte superior da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL sandbox] deviado.

![Datenaufnahme](./images/sb1.png)

Kein Menü à esquerda, Zugriff **Segmente**. Nesta página, você tem uma visão geral de todos os segmentos existentes. Clique no botão + Criar segmento para começar a criar um novo segmento.

![Segmentierung](./images/menuseg.png)

Quando estiver no novo construtor de segmentos, você irá perceber imediatamente a opção de menu **Attribute** e a referência do **XDM Individual Profile**.

![Segmentierung](./images/segmentationui.png)

Como o XDM é a linguagem que alimenta o setor de experiência, o XDM também é a base para o construtor de segmentos. Todos os dados ingeridos na plataforma devem ser mapeados em relação ao XDM e, portanto, todos os dados se tornam parte do mesmo modelo de dados, unabhängigemente da origem desses dados. Isso oferece uma grande vabilitao criar segmentos, pois a partir dessa interface do usuário do construtor de segmento, é posível combined dados de qualquer origem no mesmo fluxo de trabalho. Os segmentos criados no Construtor de segmentos podem ser enviados para soluções como Adobe Target, Adobe Campaign e Adobe Audience Manager para ativação.

Agora você precisa criar um segmento de todos os clientes que visualizaram o produto **Real-Time CDP**.

Para construir este segmento, você precisa adicionar um Evento de experiência. Você pode entractor todos os Eventos de experiência clicando no ícone **Events** na barra de menu **Fields**.

![Segmentierung](./images/findee.png)

Em seguida, você verá o nó **XDM ExperienceEvents** do nível superior. Klicken Sie auf **XDM ExperienceEvent**.

![Segmentierung](./images/see.png)

Zugriff **Produktlistenelemente**.

![Segmentierung](./images/plitems.png)

Selecione **Name** e arraste e solte o objeto **Name** do menu à esquerda na tela do construtor de segmentos na seção **Events**. Em seguida, o seguinte será exibido:

![Segmentierung](./images/eewebpdtlname.png)

O parâmetro de comparação deve ser **equals** e, no campo de entrada, insira **Real-time CDP**.

![Segmentierung](./images/pv.png)

Sempre que adicionar um elemento ao construtor de segmentos, você pode clicar no **(Schätzung aktualisieren** para obter uma nova estimativa da população em seu segmento.

![Segmentierung](./images/refreshest.png)

**Auswertungsmethode**, selecione **Edge**.

![Segmentierung](./images/evedge.png)

Por fim, vamos dar um nome ao seu segmento e salvá-lo.

Como modelo de nomenclatura, verwenden:

- `seuSobrenome - Interest in Real-Time CDP`

Em seguida, clique no botão **Speichern und schließen** para salvar seu segmento.

![Segmentierung](./images/segmentname.png)

Agora você irá retornar à página de visão geral do segmento, onde verá uma visualização de amostra dos perfis de clientes que se qualificam para o seu segmento.

![Segmentierung](./images/savedsegment.png)

Agora você pode continuar no próximo ercício e usar seu segmento com o Adobe Target.

Próxima etapa: [1.4 Ação: envie seu segmento para o Adobe Target](./ex4.md)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[In: Retornar para Todos os Módulos](../../overview.md)

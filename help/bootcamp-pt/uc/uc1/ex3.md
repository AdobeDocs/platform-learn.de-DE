---
title: Bootcamp - Echtzeit-Kundenprofil - Segment erstellen - Benutzeroberfläche - Brasilien
description: Bootcamp - Echtzeit-Kundenprofil - Segment erstellen - Benutzeroberfläche - Brasilien
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
source-git-commit: 5d824244766135cd4998feab48be7f6a69c42a70
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 3%

---

# 1.3 Crit um segmento - UI

Neste übício, você irá criar um segmento usando o Construtor de Segmentos da Adobe Experience Platform.

## Histórien

Acesse [Adobe Experience Platform](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Antes de Continuar, você recisa selecionar um **Sandbox**. O nome do sandbox a ser selecionado é ``Bootcamp``. É besitzível fazer isso clicando no texto **[!UICONTROL Produktionsprodukt]** na linha azul na parte überlegen da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL Sandbox] widado.

![Datenaufnahme](./images/sb1.png)

No menu à esquerda, acesse **Segmente**. Nesta página, você tem uma visão geral de todos os segmentos existentes. Clique no botão + Criar segmento para começar a criar um novo segmento.

![Segmentierung](./images/menuseg.png)

Quando estiver no novo construtor de segmentos, você irá perceber imediatamente a opção de menu **Attribute** e a referência do **XDM Individual Profile**.

![Segmentierung](./images/segmentationui.png)

Como XDM é a linguagem que alimenta o setor de experiência, o XDM também é a base para o construtor de segmentos. Todos os dados ingeridos na plataforma devem ser mapeados em relação ao XDM e, portanto, todos os dados se tornam parte do mesmo modelo de dados, indepenentemente da origem desses dados. Isso oferece uma grande vous m ao criar segmentos, pois a partir dessa interface do usuário do construtor de segmento, é besitzível ombinar dados de qualquer origem no mesmo fluxo de trabalho. OS segmentos criados no Construtor de segmentos podem ser enviados para soluções como Adobe Target, Adobe Campaign e Adobe Audience Manager para ativação.

Agora você recisa criar um segmento de todos os clientes que visualizaram o produto **Real-Time CDP**.

Para construir este segmento, você recisa adicionar um Evento de experiência. Você pode encounter todos os Eventos de experiência clicando no ícone **Veranstaltungen** Barra de menu **Felder**.

![Segmentierung](./images/findee.png)

Em seguida, você verá o nó **XDM ExperienceEvents** do nível überlegen. Clique em **XDM ExperienceEvent**.

![Segmentierung](./images/see.png)

Acesse **Produktlistenelemente**.

![Segmentierung](./images/plitems.png)

Selecione **Name** e arraste e solte o objeto **Name** do menu à esquerda na tela do construtor de segmentos na seção **Veranstaltungen**. Em seguida, o seguinte será exibido:

![Segmentierung](./images/eewebpdtlname.png)

O parâmetro de vergleichação deve ser **gleich** e, kein Campo de entrada, insira **Echtzeit-Kundendatenplattform**.

![Segmentierung](./images/pv.png)

Sempre que adicionar um elemento ao construtor de segmentos, você pode clicar no botão **Schätzung aktualisieren** para obter uma nova estimated ativa da popação em seu segmento.

![Segmentierung](./images/refreshest.png)

Para **Auswertungsmethode**, selecione **Edge**.

![Segmentierung](./images/evedge.png)

Por fim, vamos dar um nome ao seu segmento e salvá-lo.

Como modelo de nomenclatura, Verwendung:

- `seuSobrenome - Interest in Real-Time CDP`

Em seguida, clique no botão **Speichern und schließen** para salvar seu segmento.

![Segmentierung](./images/segmentname.png)

Agora você irá retornar à página de visão geral do segmento, onde verá uma visualização de amostra dos perfis de clientes que se qualificam para o seu segmento.

![Segmentierung](./images/savedsegment.png)

Agora você pode Continuar no próximo übício e usar seu segmento com o Adobe Target.

Próxima etapa: [1.4 Ação: Bereitstellen von Segmento-Para für Adobe Target](./ex4.md)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[Retornar para Todos os Módulos](../../overview.md)

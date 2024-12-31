---
title: Bootcamp - Customer Journey Analytics - Datenvorbereitung in Analysis Workspace - Brasilien
description: Bootcamp - Customer Journey Analytics - Datenvorbereitung in Analysis Workspace - Brasilien
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
solution: Customer Journey Analytics
feature-set: Customer Journey Analytics
feature: Workspace Basics, Calculated Metrics
exl-id: d56128af-dd1e-47ea-922f-85418e9da687
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 1%

---

# 4.4 Vorbereitung des Customer Journey Analytics

## objektivisch

- Entenda a UO do Analysis Workspace no CJA
- Entenda os conceitos de preparation ação de dados no Analysis Workspace
- Aprenda a fazer cálculos de dados

## 4.4.1 Benutzeroberfläche von Analysis Workspace ohne CJA

O Analysis Workspace Entfernen Sie todas als limitações típicas de um único relatório do Analytics. Ele fornece uma tela robusta e flexível para criar projetos de analytics personalizados. Arraste e solte qualquer número de tabelas de dados, visualizações e componentes (dimensões, métricas, segmentos e granularidades de tempo) para um project. Criação instantânea de avarias e segmentos, criação de cortes para análise, criação de alertas, comparação de segmentos, análise de fluxo e de falhas e relatórios de curadoria e agendamento para compartilhar com qualquer pessoa em seu negócio.

O Customer Journey Analytics traz essa solução além dos dados da plataforma. É altamente recomendável assistir a este video de visão geral de quatro minutos:

>[!VIDEO](https://video.tv.adobe.com/v/35109?quality=12&learn=on)

Se você nunca usou o Analysis Workspace antes, recomendamos este video:

>[!VIDEO](https://video.tv.adobe.com/v/26266?quality=12&learn=on)

### Projekt Crie Seu

Agora é hora de criar seu primeiro project do CJA. Vá para a aba de projetos dentro do CJA. Klicken Sie auf **Neu erstellen**.

![demo](./images/prmenu.png)

Em seguida, você verá a tela abaixo selecione **Leeres Projekt** então clique em **Create**.

![demo](./images/prmenu1.png)

Você verá um projeto vazio.

![demo](./images/premptyprojects.png)

Primeiro, certificique-se de selecionar a visualização de dados correta no canto superior direito da tela. Neste exemplo, a visualização de dados a ser selecionada é `vangeluwe - Omnichannel Data View`.

![demo](./images/prdv.png)

Em seguida, você irá salvar seu projeto e dar um nome a ele. Você pode usar o seguinte comando para salvar:

| Betriebssystem | Abkürzung |
| ----------------- |-------------| 
| Windows | Strg+S |
| Mac | Befehl + S |

Popup-Fenster „Você verá este“:

![demo](./images/prsave.png)

Este modelo de nomenclatura verwenden:

| Name | Beschreibung |
| ----------------- |-------------| 
| `yourLastName - Omnichannel Analysis` | `yourLastName - Omnichannel Analysis` |

EM seguida, klicken Sie auf em **Speichern**.

![demo](./images/prsave2.png)

## 4.4.2. Métricas-Berechnungen

Embora tenhamos organizado todos os componentes na visualização de dados, você ainda deve adaptar alguns deles para que os usuários de negócios estejam prontos para iniciar suas análises. Além disso, durante qualquer processo de analytics, você pode criar métricas calculate para aprofundar a descoberta de insights.

Como exemplo, criaremos uma Taxa de conversão calculate usando a métrica/event compras que definimos na Visualização de dados.

## Taxa de Conversão

Vamos começar ist ein Barrio des Construtor de métricas calculate. Clique em **+** para criar sua primeira Métrica calculate no Analysis Workspace

![demo](./images/pradd.png)

O **Generator für berechnete Metriken** irá aparecer:

![demo](./images/prbuilder.png)

Encontre **Einkäufe** na lista de métricas no menu do lado esquerdo. em **Metriken** clique em **Alle anzeigen**

![demo](./images/calcbuildercr1.png)

Agora arraste e solte a métrica **Einkäufe** na definição da métrica calculate (Berechnungen mit Metriken).

![demo](./images/calcbuildercr2.png)

Normalmente, taxa de conversão signifika **Konversionen / Sitzungen**. Então, vamos fazer o mesmo cálculo na tela de definição de métrica calculate. Encontre a metrica **Sessions** e arraste e solte-a no criador de definição, no event to **Purchases**.

![demo](./images/calcbuildercr3.png)

Observe que o operador de divisão é selecionado automaticamente.

![demo](./images/calcbuildercr4.png)

A taxa de conversão é comumente presentada em procentagem. Então, vamos mudar o formato para procentagem e selecionar 2 casas decimais.

![demo](./images/calcbuildercr5.png)

Ändern Sie abschließend den Namen und die Beschreibung der berechneten Metrik:

| Titel | Beschreibung |
| ----------------- |-------------| 
| Konversionsrate | Konversionsrate |

Por fim, altere on nome e a descrição da métrica calculate:

![demo](./images/calcbuildercr6.png)

In: Não se esqueça **Salvar** a Métrica Calculada.

![demo](./images/pr9.png)

## 4.4.3 Dimensões calculate as: Filtros (segmentação) e intervalos de datas

### Filter: Dimensões calculate

Os cálculos não devem ser apenas para métricas. Antes de iniciar qualquer análise, também é interessante criar algumas **Berechnete Dimensionen**. Isso signifikant, essencialmente, **segmente** kein Adobe Analytics. Keine Customer Journey Analytics, esses segmentos são chamados de **filters**.

![demo](./images/prfilters.png)

A criação de filtros ajudará os usuários de negócios a iniciar o analytics com algumas dimensões calculate as valiosas . Issoirá automatizar algumas tarefas, além de ajudar na parte de adoção. Abaixo estão alguns beispielhaft:

1. Mídia Própria, Mídia Paga,
2. Visitas novas x recorrentes
3. Kunden von Carrinho Abandonado

Esses filtros podem ser criados antes ou durante a parte de análise (o que você fará no próximo ercício).

### Intervall de datas: Taschenrechnungen

Wie dimensões de tempo são outro tipo de dimensões calculate. Alguns já forma criados, mas você também pode criar suas próprias Dimensões de tempo personalizadas na fase de preparation ação de dados.

Essas Dimensões de tempo calculate ajudarão analistas e usuários de negócios a lembrar datas importantes e usá-las para filtrar e alterar o tempo de relatório. Perguntas e dúvidas típicas quando fazemos análises:

- Quando foi a Black Friday do ano passado? Entre os dias 21 e 29?
- Quando veiculamos aquela campanha de TV em dezembro?
- De quando a quando fizemos as vendas de verão de 2018? Quero comparar com 2019. A propósito, você sabe os dias exatos em 2019?

![demo](./images/timedimensions.png)

Agora você cluiu o excício de preparation ação de dados usando o Analysis Workspace do CJA.

Próxima etapa: [4.5 Visualização usando Customer Journey Analytics](./ex5.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[In: Retornar para Todos os Módulos](./../../overview.md)

---
title: Bootcamp - Customer Journey Analytics - Datenvorbereitung in Analysis Workspace - Brasilien
description: Bootcamp - Customer Journey Analytics - Datenvorbereitung in Analysis Workspace - Brasilien
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
source-git-commit: 9cc01c7d3018319137f915e103bce9dc39b0d472
workflow-type: tm+mt
source-wordcount: '793'
ht-degree: 1%

---

# 4.4 Customer Journey Analytics des Präparação de dados

## Objetivos

- Entenda a UO do Analysis Workspace on CJA
- Entenda os conceitos de vorbereitação de dados in Analysis Workspace
- Aprenda a fazer cálculos de dados

## 4.4.1 Benutzeroberfläche führt Analysis Workspace auf CJA aus

O Analysis Workspace entfernen todas als limitações típicas de um único relatório do Analytics. Ele fornece uma tela robusta e flexível para criar projetos de analytics personalizados. Array e solte qualquer número de tabelas de dados, visualizações e components (dimensões, métricas, segmentos e granularidades de tempo) para um projeto. Criação instantânea de avarias e segmentos, criação de cortes para análise, criação de alertas, Comparação de segmentos, análise de fluxo e de falhas e relatórios de curadoria e agendamento para compartilhar com qualpessoa em seu negócio.

O Customer Journey Analytics traz essa solução além dos dados da plataforma. É altamente recomendável assistir a este vídeo de visão geral de Quatro minutos:

>[!VIDEO](https://video.tv.adobe.com/v/35109?quality=12&learn=on)

Se você nunca usou o Analysis Workspace antes, recomendamos este vídeo:

>[!VIDEO](https://video.tv.adobe.com/v/26266?quality=12&learn=on)

### Crie Seu Project

Agora é hora de criar seu primeiro projeto do CJA. Vá para a aba de projetos dentro do CJA. Clique em **Neu erstellen**.

![Demo](./images/prmenu.png)

Em seguida, você verá a tela abaixo. Selecione **Leeres Projekt** então clique em **Erstellen**.

![Demo](./images/prmenu1.png)

Você verá um projeto vazio.

![Demo](./images/premptyprojects.png)

Primeiro, certificate-se de selecionar a Visualização de dados correta no canto überlegen direito da tela. Neste Exemplo, Visualização de dados a ser selecionada é `vangeluwe - Omnichannel Data View`.

![Demo](./images/prdv.png)

Em seguida, você irá salvar seu projeto e dar um nome a ele. Você pode usar o seguinte comando para salvar:

| BS | Kurzschnitt |
| ----------------- |-------------| 
| Windows | Kontrolle + S |
| Mac | Befehl + S |

Pop-up Você verá este:

![Demo](./images/prsave.png)

Verwenden Sie das este Modell de nomenclatura:

| Name | Beschreibung |
| ----------------- |-------------| 
| `yourLastName - Omnichannel Analysis` | `yourLastName - Omnichannel Analysis` |

Em seguida, clique em **Speichern**.

![Demo](./images/prsave2.png)

## 4.4.2 Métricas kalkadas

Embora tenhamos organizado todos os componentes na Visualização de dados, você ainda deve adaptar alguns deles para que os usuários de negócios estejam prontos para iniciar suas análises. Além disso, durante qualquer processo de analytics, você pode criar métricas calculadas para aprofundar a descoberta de insights.

Como exemplo, criaremos uma Taxa de versão calculada usando a métrica/evento Compras que definimos na Visualização de dados.

## Taxa de dialogão

Vamos começar a abrir o construtor de métricas calculadas. Clique em **+** para criar sua primeira Métrica calculada auf Analysis Workspace.

![Demo](./images/pradd.png)

O **Generator für berechnete Metriken** irá aparecer:

![Demo](./images/prbuilder.png)

Sichern **Käufe** na lista de métricas kein Menü do lado esquerdo. Em **Metriken** clique em **Alle anzeigen**

![Demo](./images/calcbuildercr1.png)

Agora arraste e solte a métrica **Käufe** na definição da métrica calculada.

![Demo](./images/calcbuildercr2.png)

Normalmente, taxa de dialogão signia **Konversionen/Sitzungen**. Então, vamos fazer o mesmo cálculo na tela de definição de métrica calculada. Encontre a métrica **Sitzungen** e arraste e solte-a no criador de definição, no evento **Käufe**.

![Demo](./images/calcbuildercr3.png)

Observe que o operador de divisão é selecionado automaticamente.

![Demo](./images/calcbuildercr4.png)

Ein Taxa de dialogão é comumente darada em porcentagem. Então, vamos mudar o formato para porcentagem e selecionar 2 casas decimais.

![Demo](./images/calcbuildercr5.png)

Ändern Sie abschließend den Namen und die Beschreibung der berechneten Metrik:

| Titel | Beschreibung |
| ----------------- |-------------| 
| Konversionsrate | Konversionsrate |

Por fim, altere o nome e a descrição da métrica calculada:

![Demo](./images/calcbuildercr6.png)

Não se esqueça de **Salvar** eine Métrica Calculada.

![Demo](./images/pr9.png)

## 4.4.3 Dimensões calculate: Filtros (segmentação) e intervalos de datas

### Filter: Dimensões calculate

Os cálculos não devem ser apenas para métricas. Antes de iniciar qualquer análise, também é interessante algumas **Berechnete Dimensionen**. Isso signia, essencialmente **Segmente** Keine Adobe Analytics. Kein Customer Journey Analytics, weist segmentos são chamados de **Filter**.

![Demo](./images/prfilters.png)

Ein criação de filtros ajudará os usuários de negócios a iniciar o analytics com algumas dimensões calculadas valiosas. Isso irá automatizar algumas tarefas, além de ajudar na parte de adoção. Abaixo estão alguns example:

1. Mídia Própria, Mídia Paga,
2. Visitas novas x recorrentes
3. Clientcom carrinho abandonado

Esses filtros podem ser criados antes ou durante a parte de análise (o que você fará no próximo übício).

### Intervalos de datas: Dimensões de tempo calculadas

Als dimensões de tempo são outro tipo de dimensões calculadas. Alguns já foram criados, mas você também pode criar suas próprias Dimensões de tempo personalizadas na fase de prepare ação de dados.

Essas Dimensões de tempo calculado ajudarão analistas e usuários de negócios a lembrar datas importantes e usá-las para filtrar e alterar o tempo de relatório. Perguntas e dúvidas típicas quando fazemos análises:

- Quando foi ein Black Friday do ano passado? Geben Sie os dias 21 e 29 ein?
- Quando veiculamos aquela campanha de TV em dezembro?
- De quando a quando fiemos as vendas de verão de 2018? Quero Comparar com 2019. a propósito, você sabe os dias exatos em 2019?

![Demo](./images/timedimensions.png)

Agora você schlüssiiu o übício de vorbereitação de dados usando o Analysis Workspace do CJA.

Próxima etapa: [4.5 Visualização usando Customer Journey Analytics](./ex5.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[Retornar para Todos os Módulos](./../../overview.md)

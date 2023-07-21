---
title: Bootcamp - Customer Journey Analytics - Visualisierung mit Customer Journey Analytics - Brasilien
description: Bootcamp - Customer Journey Analytics - Visualisierung mit Customer Journey Analytics - Brasilien
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
solution: Customer Journey Analytics
feature-set: Customer Journey Analytics
feature: Visualizations
exl-id: eb5eac54-22d8-428b-acac-16570f75085e
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '1586'
ht-degree: 1%

---

# 4.5 Visualização usando o Customer Journey Analytics

## Objetivos

- Erweitern einer Benutzeroberfläche für Analysis Workspace
- Conheça alguns recursos que tornam o Analysis Workspace tão diferente.
- Aprenda a analisar no CJA usando Analysis Workspace

## ContextTo

Neste übício, você usará o Analysis Workspace no CJA para analisar visualizações de produtos, funis de produtos, rotatividade usw.

Vamos usar o projeto que você criou em  [4.4 Vorbereitende Maßnahmen für dados in der Analysis Workspace](./ex4.md)então acesse [https://analytics.adobe.com](https://analytics.adobe.com).

![Demo](./images/prohome.png)

Abra seu Project `yourLastName - Omnichannel Analysis`.

Com seu projeto aberto e Visualização de dados `yourLastName - Omnichannel Analysis` selecionado, você está pronto para começar a construir suas primeiras visualizações.

![Demo](./images/prodataView1.png)

## Quantas visualizações de produtos temos diariamente?

Em primeiro lugar, preisamos selecionar als datas certas para analisar os dados. Acesse o menu suspenso do calendário no lado direito da tela. Clique nele e selecione o intervalo de datas aplicável.

>[!IMPORTANT]
>
>Selecione um intervalo de datas como **Diese Woche** ou **Diesen Monat**. Os dados disponíveis mais recentes foram absorvidos em 19 de setembro de 2022.

![Demo](./images/pro1.png)
Kein Menü do lado esquerdo (área de componentes), stellen Sie wie métricas kalkadas **Produktansichten**. Selecione-as e arraste e solte na tela, no canto überlegen direito da tabela de forma livre.

![Demo](./images/pro2.png)

Automaticamente a dimensão **Tag** será adicionada para criar sua primeira tabela. Agora você pode ver sua pergunta respondida imediatamente.

![Demo](./images/pro3.png)

Em seguida, clique com o botão direito do mouse no resumo da métrica.

![Demo](./images/pro4.png)

Clique em **Visualisieren** e selecione **Linie** como visualização.

![Demo](./images/pro5.png)

Você verá as suas visualizações de produto por dia.

![Demo](./images/pro6.png)

Você pode alterar o escopo de tempo para o dia clicando em **Einstellungen** Visualização.

![Demo](./images/pro7.png)

Clique no ponto ao lado de **Linie** e **Datenquelle verwalten**.

![Demo](./images/pro7a.png)

Em seguida, clique em **Auswahl sperren** e selecione **Ausgewählte Elemente** para bloquear esta visualização para que ela sempre exiba uma linha do tempo de Visualizações de produtos.

![Demo](./images/pro7b.png)

## 5 produtos mais vistos

Quais são os 5 produtos mais vistos?

Lembre-se de salvar o projeto de tempos em tempos.

| BS | Kurzschnitt |
| ----------------- |-------------| 
| Windows | Kontrolle + S |
| Mac | Befehl + S |

Vamos começar a encounter os 5 produtos mais vistos. Kein Menü do lado esquerdo, Encontre zu Nome do produto - Dimensão.

![Demo](./images/pro8.png)

Agora arraste e solte **Produktname** para replace a dimensão **Tag**:

Este será o result tado.

![Demo](./images/pro10a.png)

Em seguida, tente dividir um dos produtos por Nome da marca. Pesquise **brandName** e arraste para baixo do primeiro nome do produto.

![Demo](./images/pro13.png)

Em seguida, faça um detalhamento usando Agente de usuário. Pesquise **Benutzeragent** e arraste-o para baixo do nome da marca.

![Demo](./images/pro15.png)

Em seguida, será exibida a tela abaixo:

![Demo](./images/pro15a.png)

Por fim, você pode adicionar mais visualizações. No lado esquerdo, em visualizações, pesquise `Donut`. Pegue `Donut`, arraste e solte na tela sob a visualização **Linie** 

![Demo](./images/pro18.png)

Wählen Sie als Nächstes in der Tabelle die ersten 5 **Benutzeragent**  Zeilen aus der Aufschlüsselung, die wir unter **Google Pixel XL 32 GB Black Smartphone** > **Citi Signal**. Halten Sie bei Auswahl der fünf Zeilen die **STRG** (unter Windows) oder **Befehl** Schaltfläche (in Mac).

Em seguida, na Tabela, selecione as primeiras 5 linhas de **Benutzeragent** do detalhamento que fiemos em **Google Pixel XL 32 GB Black Smartphone** > **Citi Signal**. Ao selecionar as 5 linhas, sego botão **STRG** (kein Windows) ou o botão **Befehl** (kein Mac).

![Demo](./images/pro20.png)

Você verá o gráfico de donut alterado:

![Demo](./images/pro21.png)

Você pode até adaptar o design para ser mais legível, tornando o gráfico de **Linie** e o gráfico de **Ringdiagramm** um pouco menor para que sejam exibidos lado a lado:

![Demo](./images/pro22.png)

Clique no ponto ao lado de *Ringdiagramm** para **Datenquelle verwalten**. Em seguida, clique em **Auswahl sperren** para bloquear essa visualização para que ela sempre exiba uma linha do tempo de Visualizações de produto.

![Demo](./images/pro22b.png)

Saiba mais sobre visualizações usando o Analysis Workspace em:

- [https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/freeform-analysis-visualizations.html?lang=de](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/freeform-analysis-visualizations.html?lang=de)
- [https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/t-sync-visualization.html](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/t-sync-visualization.html)

## Funil de interação do produto, da visualização à compra

Existem muitas formas de resolver esta questão. Uma delas é usar o Tipo de Interação de Produto e usá-lo em uma tabela de formato livre. Outra forma é usar uma **Fallout-Visualisierung**. Vamos usar o último, pois queremos visualizar e analisar ao mesmo tempo.

Fieber oder Painel atual clicando aqui:

![Demo](./images/pro23.png)

Agora adicione um novo schmerel em branco clicando em **+ Leeres Bedienfeld hinzufügen**.

![Demo](./images/pro24.png)

Clique na visualização de **Fallout**.

![Demo](./images/pro25.png)

Selecione o mesmo intervalo de datas do übício anteriore.

![Demo](./images/prodatef.png)

Em seguida, você verá:

![Demo](./images/prodatefa.png)

Eingeben einer Dimension **Ereignistyp** nos components no lado esquerdo:

![Demo](./images/pro26.png)

Clique na seta para abrir a dimensão:

![Demo](./images/pro27.png)

Você verá todos os Tipos de eventos disponíveis.

![Demo](./images/pro28.png)

Auswahl eines Elements **commerce.productViews** e arraste e solte-o no campo **Touchpoint hinzufügen** dentro da **Fallout-Visualisierung**.

![Demo](./images/pro29.png)

Faça o mesmo com **commerce.productListAdds** und **commerce.purchases** e solte-os no campo **Touchpoint hinzufügen** dentro da  **Fallout-Visualisierung**. Sua visualização agora deve ser semelhante ao seguinte:

![Demo](./images/props1.png)

Você pode fazer muitas coisas aqui. Algen sind Beispiele: Comparar ao longo do tempo, vergleichen cada passo por dispositivo ou Comparar por fidelidade. Keine entanto, se quisermos analisar coisas interessantes como porque os clientes não compram depois de adicionar um item ao carrinho, podemos usar a melhor ferramenta do CJA: clicar com o botão direito.

Clique com o botão direito do mouse no touchpoint **commerce.productListAdds**. Em seguida, clique em **Aufschlüsselungs-Fallout an diesem Touchpoint**.

![Demo](./images/pro32.png)

Uma nova tabela de formato livre será criada para analisar o que as pessoas fizeram se não compraram.

![Demo](./images/pro33.png)

Altere o **Ereignistyp** von **Seitenname**, na nova tabela de formato livre, para ver em quais páginas eles estão indo, em vez da Página de bestätigmação de compra.

![Demo](./images/pro34.png)

## O que as pessoas fazem no site antes de acessar a página Cancelar serviço?

Novamente, há muitas formas de realizar essa análise. Vamos usar a análise de fluxo para iniciar parte da descoberta.

Fieber oder Painel atual clicando aqui:

![Demo](./images/pro0.png)

Agora adicione um novo schmerel em branco clicando em **+ Leeres Bedienfeld hinzufügen**.

![Demo](./images/pro0a.png)

Clique na visualização **Fluss**.

![Demo](./images/pro35.png)

Em seguida, será exibido:

![Demo](./images/pro351.png)

Selecione o mesmo intervalo de datas do übício anteriore.

![Demo](./images/pro0b.png)

Eingeben einer Dimension **Seitenname** nos components no lado esquerdo:

![Demo](./images/pro36.png)

Clique na seta para abrir a dimensão:

![Demo](./images/pro37.png)

Você encontará todas as páginas vistas. Encontre o nome da página: **Dienst abbrechen**.
Array e solte **Dienst abbrechen** na Visualização de fluxo no campo do meio:

![Demo](./images/pro38.png)

Em seguida, será exibido:

![Demo](./images/pro40.png)

Vamos agora analisar se os clientes que visitaram a página C **Dienst abbrechen** keine Website também ligaram para o call center e qual foi o result tado.

Nas dimensões, retorne e encontre Tipo de interação de chamada. Array e solte **Interaktionstyp aufrufen** para replace a primeira interação à direita em **Flussvisualisierung**.

![Demo](./images/pro43.png)

Agora você visualiza o ticket de suporte dos clientes que ligaram para a central de atendimension depois de visitar a página **Dienst abbrechen**.

![Demo](./images/pro44.png)

Em seguida, nas dimensões, procure **Rufempfindlichkeit**. Array e solte para replace a primeira interação à direita na visualização de fluxo.

![Demo](./images/pro46.png)

Em seguida, será exibido:

![Demo](./images/flow.png)

Como pode ver, executamos uma análise omnichannel usando a visualização de fluxo. Graças a isso, descobrimos que alguns clientes que estavam pensando em cancelar o serviço tiveram uma avaliação positiva depois de ligar para o call center. Talvez tenhamos mudado de ideia com uma promoção?

## Qual é o desempenho dos clientes com um contato de Call center Positivo em relação aos principais KPIs?

Primeiramente, vamos segmentar os dados para obter apenas usuários com chamadas **positive**. No CJA, os Segmentos são chamados de Filtros. Acesse para filtros na área de components (no lado esquerdo) e clique em **+**.

![Demo](./images/pro58.png)

Dentro do Construtor de filo, dê um nome ao filtro

| Name | Beschreibung |
| ----------------- |-------------| 
| Rufempfindlichkeit - positiv | Rufempfindlichkeit - positiv |

![Demo](./images/pro47.png)

No componentes (dentro do Construtor de filtro), encontre **Rufempfindlichkeit** e arraste e solte na Definição do construtor de filtro.

![Demo](./images/pro48.png)

Agora selecione **positive** como valor para o filtro.

![Demo](./images/pro49.png)

Altere o escopo para o nível **Person**.

![Demo](./images/pro50.png)

Para finalizar, Basta clicar em **Speichern**.

![Demo](./images/pro51.png)

Então, você irá retornar para esta tela. Se ainda não retornou, feche o schmerel anteriore.

![Demo](./images/pro0c.png)

Agora adicione um novo schmerel em branco clicando em **+ Leeres Bedienfeld hinzufügen**.

![Demo](./images/pro24c.png)

Selecione o mesmo intervalo de datas do übício anteriore.

![Demo](./images/pro24d.png)

Clique em **Freiformtabelle**.

![Demo](./images/pro52.png)

Agora arraste e solte o filo que você acabou de criar.

![Demo](./images/pro53.png)

Hora de adicionar algumas métricas. Comece com **Produktansichten**. Array e solte na tabela de forma livre. Você também pode excluir a métrica **Veranstaltungen**.

![Demo](./images/pro54.png)

Faça o mesmo com **Personen**, **Zum Warenkorb hinzufügen** e **Käufe**. Você vai acabar com uma tabela como a seguinte.

![Demo](./images/pro55.png)

Graças à primeira análise de fluxo, uma nova pergunta surgiu. Então decidimos criar esta tabela e verificar alguns KPIs em um segmento para responder a essa pergunta. Como você pode ver, o tempo de insight é muito mais rápido do que usar SQL ou usar outras soluções de BI.

## Recapitulação do Analysis Workspace e do Customer Journey Analytics

O Analysis Workspace entfernen todas als limitações típicas de um relatório do Analytics. Ele fornece uma tela robusta e flexível para criar projetos de analytics personalizados. Array e solte qualquer número de tabelas de dados, visualizações e components (dimensões, métricas, segmentos e granularidades de tempo) para um projeto. Você pode criar de forma instantânea filtros e analises, gráficos de coorte, alertas, segmentos, análises de fluxo e relatórios de curadoria e agendamento para compartilhar com qualquer pessoa em seu negócio.

Próxima etapa: [4.6 De Insights a ação](./ex6.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[Retornar para Todos os Módulos](./../../overview.md)

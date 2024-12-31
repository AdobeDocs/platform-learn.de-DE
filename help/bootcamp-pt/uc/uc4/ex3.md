---
title: Bootcamp - Customer Journey Analytics - Datenansicht erstellen - Brasilien
description: Customer Journey Analytics - Datenansicht erstellen - Brasilien
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
solution: Customer Journey Analytics
feature-set: Customer Journey Analytics
feature: Data Views
exl-id: 8cfd4467-167d-4235-a305-4596e3a7d4fb
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '1667'
ht-degree: 2%

---

# 4.3 Crie uma visualização de Dados

## objektivisch

- Entenda a UI de Visualização de Dados
- Compreenda as configurações básicas de definição de visita
- Compreenda a atribuição e a Persistência em uma Visualização de

## 4.3.1 Visualização de Dados

Agora, com sua conexão cluída, é possivel progredir para influenciar a visualização. Uma diferença entre o Adobe Analytics e o CJA é que o CJA precisa de uma visualização de dados para limpar e Preparar os dados antes da visualização.

Uma visualização de Dados é semelhante ao concito de Virtual Report Suites no Adobe Analytics, onde você estabelece as definições de visita com Reconhecimento de Contexto, filtragem e também como os componentes são chamados.

Será necário, no mínimo, uma visualização de Dados por conexão. No entanto, para alguns casos de uso, é ótimo ter múltiplas visualizações de Dados para a mesma conexão, com o objetivo de fornecer insights diferentes para equipes distintas. Se você deseja que sua empresa seja orientada por dados, deve adaptar a forma como os dados são vistos em cada equipe. Beispiele für Alguns:

- Métricas de UX apenas para a equipe de UX Design
- Verwenden Sie os mesmos nomes para KPIs e métricas para o Google Analytics e para o Customer Journey Analytics, para que a equipe de análise digital fale apenas 1 idioma.
- Visualização de Dados filtrada para mostrar, por exemplo, dados para apenas um mercado, ou uma marca, ou apenas para Dispositivos móveis.

Na tela de **Connections** marque a caixa de selecão da conexão que você acabou de criar. Klicken Sie auf **Datenansicht erstellen**.

![demo](./images/exta.png)

Você será redirecionado para o fluxo de trabalho **Datenansicht erstellen** Workflow.

![demo](./images/0-v2.png)

## 4.3.2 Definição de Visualização de Dados

Agora você pode configurar as definições básicas para sua visualização de dados.

![demo](./images/0-v2.png)

A **Connection** que você criou no excício anterior já está selecionada. Sua conexão se chama `yourLastName – Omnichannel Data Connection`.

![demo](./images/ext5.png)

Dê um nome à sua visualização de Dados seguindo este modelo de nomenclatura: `yourLastName – Omnichannel Data View`.

Insira o mesmo valor para a descrição: `yourLastName – Omnichannel Data View`.

| Name | Beschreibung |
| ----------------- |-------------| 
| `yourLastName – Omnichannel Data View` | `yourLastName – Omnichannel Data View` |

![demo](./images/1-v2.png)

Para **Zeitzone**, selecione o fuso horário **Berlim, Estocolmo, Roma, Berna, Bruxelas, Wien, Amsterdam GMT+01:00**. Este é um cenário realmente interessante, pois algumas empresas operam em diferentes países e geografias. Alocar o fuso horário certo para cada país evitará erros típicos de dados, como, por exemplo, acreditar que a maioria das pessoas compra camisetas às 4h no Peru.

![demo](./images/ext7.png)

Você também pode modificar a nomenclatura das métricas principais (Pessoa, Sessão e Evento). Isso não é obrigatório, mas alguns clientes gostam de usar Pessoas, visitas e Acessos em vez de Pessoa, Sessão e Eventos (Convenção de nomenclatura padrão do Customer Journey Analytics.)

Agora você deve ter as seguintes configurações definidas:

![demo](./images/1-v2.png)

Klicken Sie auf **Speichern und fortfahren**.

![demo](./images/12-v2.png)

## 4.3.3 Components da Visualização de Dados

Neste ercício, você irá configurar os componentes neccários para analisar os dados e visualizá-los usando o Analysis Workspace. Nesta IU, há três áreas principais:

- Lado esquerdo: componentes disponíveis dos datasets selecionados
- Meio: componentes adicionados à visualização de Dados
- Lado direito: Configurações do components

![demo](./images/2-v2.png)

>[!IMPORTANT]
>
>Se você não entracr uma métrica ou dimensão específica, verifique se o campo `Contains data` foi removido de sua visualização de dados. Caso contrário, exklusia esse campo.
>
>![demo](./images/2-v2a.png)

Agora você precisa arrastar e soltar os componentes necários para a análise nos **Components Added**. Para isso, você deve selecionar os componentes no menu à esquerda e arrastá-los e soltá-los na tela no meio.

Vamos começar com o primeiro componente: **Name (web.webPageDetails.name)**. Pesquise esse componente e arraste-o e solte-o na tela.

![demo](./images/3-v2.png)

Esse componente é o nome da página, como você pode derivar da leitura do campo do schema `(web.webPageDetails.name)`.

No entanto, usar **Name** como nome não é a melhor Convenção de nomenclatura para um usuário corporativo compreender rapidamente essa dimensão.

Vamos mudar o nome para **Seitenname**. Klicken Sie auf no componente e o renomeie na área **Komponenteneinstellungen**.

![demo](./images/3-0-v2.png)

As Configurações de persistência são **Persistenzeinstellungen**. Os conceitos de eVars e prop não existem no CJA, mas as configurações de Persistência possibilitam um comportamento semelhante.

![demo](./images/3-0-v21.png)

Se você não alterar essas configurações, o CJA irá interpretar a dimensão como um **Prop** (nível de ocorrência). Além disso, podemos alterar a Persistência para tornar a dimensão uma **eVar** (persistir o valor ao longo da jornada).

Se você não estiver familiarizado com eVars e Props, [leia mais sobre isso na documentação](https://experienceleague.adobe.com/docs/analytics/landing/an-key-concepts.html)..

Vamos dei xar o Nome da Página como Prop. Dessa forma, você não precisa alterar nenhuma **Persistenzeinstellungen**.

| Zu suchender Komponentenname | Neuer Name | Persistenzeinstellungen |
| ----------------- |-------------| --------------------| 
| Name (web.webPageDetails.name) | Seitenname |          |

Em seguida, escolha a dimensão **phoneNumber** e solte-a na tela. O novo nome deve ser **Telefonnummer**.

![demo](./images/3-1-v2.png)

Por fim, vamos alterar as Configurações de persistência, pois o Número do Celular deve persistir no nível do usuário.

Para alterar a persistência, role para baixo no menu à direita e abra a aba **Persistenz**:

![demo](./images/5-v2.png)

Markieren Sie eine Caixa de selecão para modificar als configurações de persistência. Selecione **Zuletzt verwendet** e o escopo **Person (Reporting-Fenster)**, pois nos preocupamos apenas com o último número de celular da pessoa. Se o cliente não preencher o celular em visitas futuras, você ainda verá esse valor preenchido.

![demo](./images/6-v2.png)

| Zu suchender Komponentenname | Neuer Name | Persistenzeinstellungen |
| ----------------- |-------------| --------------------| 
| Telefonnummer | Telefonnummer | Zuletzt verwendet, Person (Reporting-Fenster) |

O próximo componente é `web.webPageDetails.pageViews.value`.

Kein Menü à esquerda, pesquise `web.webPageDetails.pageViews.value`. In: Arraste e solte essa métrica na tela.

Ändern Sie unter **Komponenteneinstellungen** den **Seitenansichten**.

| Zu suchender Komponentenname | Neuer Name | Attributionseinstellungen |
| ----------------- |-------------| --------------------| 
| web.webPageDetails.pageViews.value | Seitenansichten |         |

![demo](./images/7-v2.png)

Para as configurações de atribuição, deixaremos em branco.

Observação: As configurações de persistência nas métricas também podem ser alteradas no Analysis Workspace. Em alguns casos, você pode optar por configurá-las aqui para evitar que os usuários de negócios tenham que pensar qual é o melhor modelo de persistência.

Em seguida, você terá que configurar várias dimensões e métricas, conforme indicado na tabela abaixo.

### DIMENSÕES

| Zu suchender Komponentenname | Neuer Name | Persistenzeinstellungen |
| ----------------- |-------------| --------------------| 
| brandName | Markenname | Zuletzt verwendet, Sitzung |
| Call-Feeling | Call Feeling |          |
| Anruf-ID | Interaktionstyp des Aufrufs |          |
| callTopic | Gesprächsthema | Zuletzt verwendet, Sitzung |
| ECID | ECID | Zuletzt verwendet, Person (Reporting-Fenster) |
| E-Mail | E-Mail-ID | Zuletzt verwendet, Person (Reporting-Fenster) |
| Zahlungsart | Zahlungsart |          |
| Methode zum Hinzufügen von Produkten | Methode zum Hinzufügen von Produkten | Zuletzt verwendet, Sitzung |
| Ereignistyp | Ereignistyp |         |
| Name (productListItems.name) | Produktname |         |
| SKU | SKU (Sitzung) | Zuletzt verwendet, Sitzung |
| Transaction ID | Transaction ID |         |
| URL (web.webPageDetails.URL) | URL |         |
| Benutzeragent | Benutzeragent | Zuletzt verwendet, Sitzung |

### METRIKA

| Zu suchender Komponentenname | Neuer Name | Attributionseinstellungen |
| ----------------- |-------------| --------------------| 
| Menge | Menge |          |
| commerce.order.priceTotal | Einnahmen |         |

Sua configuração deve ser semelhante ao seguinte:

![demo](./images/11-v2.png)

In: Não se esqueça de Salvar sua visualização de Dados. In: Então clique em **Save**.

![demo](./images/12-v2s.png)

## 4.3.4. Métricas-Berechnungen

Embora tenhamos organizado todos os componentes na visualização de dados, você ainda deve adaptar alguns deles para que os usuários de negócios estejam prontos para iniciar suas análises.

Se você se lembra, não trouxemos specificamente métricas como adicionar ao Carrinho, visualização do produto ou compras para a visualização de dados. Kein Entanto, temos uma dimensão chamada: **Ereignistyp**. Então, vamos derivars esses tipos de interação criando 3 métricas calculate.

Vamos começar com a primeira Métrica: **Produktansichten**.

Kein lado esquerdo, pesquise **Ereignistyp** e selecione a dimensão. Em seguida, arraste-o e solte-o na tela **Enthaltene Komponenten**.

![demo](./images/calcmetr1.png)

Clique para selecionar a nova **(Ereignistyp**.

![demo](./images/calcmetr2.png)

Agora altere on nome e a descrição do componente para os seguintes valores:

| Name der Komponente | Komponentenbeschreibung |
| ----------------- |-------------| 
| Produktansichten | Produktansichten |

![demo](./images/calcmetr3.png)

Agora vamos contar apenas eventos de **Produktansichten**. Para fazer isso, role para baixo em **Komponenteneinstellungen** até ver Valores de **Werte einschließen/ausschließen**. Certifique-se de habilitar a opção **Werteinschluss/-ausschluss festlegen**.

![demo](./images/calcmetr4.png)

Como queremos contar apenas **Produktansichten**, specific **commerce.productViews** nos critérios.

![demo](./images/calcmetr5.png)

Agora a sua métrica calculate está pronta!

Em seguida, repita o mesmo processo para os eventos **In den Warenkorb** e **Kauf**.

### Zum Warenkorb hinzufügen

Primeiro, arraste e solte a mesma dimensão **Ereignistyp**.

![demo](./images/calcmetr1.png)

Você verá um alerta pop-up de um Campo Duplicado, pois estamos usando a mesma variável. Clique EM **Trotzdem hinzufügen**:

![demo](./images/calcmetr6.png)

Agora, siga o mesmo processo que fizemos para a métrica visualizações de produto:
- Primeiro altere on nome e a descrição.
- Por fim, adicione **commerce.productListAdds** como critério para contar apenas In den Warenkorb

| Name | Beschreibung | Kriterien |
| ----------------- |-------------| -------------|
| Zum Warenkorb hinzufügen | Zum Warenkorb hinzufügen | commerce.productListAdds |

![demo](./images/calcmetr6a.png)

### Käufe

Primeiro, arraste e solte a mesma dimensão **Ereignistyp** como fizemos para as duas métricas anteriores.

![demo](./images/calcmetr1.png)

Você verá um alerta pop-up de um Campo Duplicado, pois estamos usando a mesma variável. Clique EM **Trotzdem hinzufügen**:

![demo](./images/calcmetr7.png)

Agora, siga o mesmo processo que fizemos para as métricas Artikelansichten In den Warenkorb:
- Primeiro altere on nome e a descrição.
- Por fim, adicione **commerce.purchases** como critérios para contabilizar apenas compras

| Name | Beschreibung | Kriterien |
| ----------------- |-------------| -------------|
| Käufe | Käufe | commerce.purchases |

![demo](./images/calcmetr7a.png)

Sua configuração final deve ser semelhante ao seguinte. Klicken Sie auf **Speichern und fortfahren**.

![demo](./images/calcmetr8.png)

## 4.3.5 Components da Configuração de Dados

Você deve ser redirecionado para esta tela:

![demo](./images/8-v2.png)

Nesta aba, você pode modificar algumas configurações importantes para alterar a forma como os dados são processados. Vamos começar definindo o **Sitzungs-Timeout** como 30 min. Graças ao registro de data e hora de cada evento de experiência, você pode estender o concito de uma sessão em todos os canais. Oder exemplarisch, o que acontece se um cliente ligar para o Call center depois de visitar vor Ort? Usando Tempos Limite de Sessão personalizados, você tem muita flexibilidade para decidir o que é uma sessão e como essa sessão irá mesclar os dados.

![demo](./images/ext8.png)

Nesta aba você pode modificar outras coisas como filtrar os dados usando um segmento/filtro. Você não precisará fazer isso neste ercício.

![demo](./images/10-v2.png)

Quando Terminar, clique em **Speichern und beenden**.

![demo](./images/13-v2.png)

>[!NOTE]
>
>Você pode voltar a esta visualização de dados posteriormente e alterar as configurações e os componentes a qualquer momento. Als alterações afetarão a forma como os dados históricos são mostrados.

Agora você pode continuar com a parte de visualização e análise!

Próxima etapa: [4.4 Preparação de dados em Customer Journey Analytics](./ex4.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[In: Retornar para Todos os Módulos](./../../overview.md)

---
title: Bootcamp - Customer Journey Analytics - Eine Datenansicht erstellen - Brasilien
description: Customer Journey Analytics - Erstellen einer Datenansicht - Brasilien
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 8cfd4467-167d-4235-a305-4596e3a7d4fb
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '1655'
ht-degree: 2%

---

# 4.3 Crie uma Visualização de Dados

## Objetivos

- Entenda a UI de Visualização de Dados
- Compreenda as configuration ações básicas de definição de visita
- Compreenda a atribuição e a Persistência em uma Visualização de

## 4.3.1 Visualização de Dados

Agora, com sua conexão completída, é besitzível progredir para influenciar a visualização. Uma diferença entre o Adobe Analytics e o CJA é que o CJA preisa de uma visualização de dados para limpar e prepare os dados antes da visualização.

Uma Visualização de Dados é semelhante ao konzipto de Virtual Report Suites no Adobe Analytics, onde você estabelece as definições de visita com Reconhecimento de contexto, filtragem e também como os components são chamados.

Será notwendiário, no mínimo, uma Visualização de Dados por conexão. Keine entanto, para alguns casos de uso, é ótimo ter múltiplas Visualizações de Dados para a mesma conexão, com o objetivo de fornecer insights diferentes para equipes distintas. Se você deseja que sua empresa seja orientada por dados, deve adaptar a forma como os dados são vistos em cada equipe. Algen sind Beispiele:

- Métricas de UX apenas para a equide UX Design
- Verwenden Sie os mesmos nomes para KPIs e métricas para o Google Analytics e para o Customer Journey Analytics, para que a equipe de análise digital fale apenas 1 idioma.
- Visualização de Dados filtrada para mostrar, por exemplo, dados para apenas um mercado, ou uma marca, ou apenas para dispositivos móveis.

Na tela de **Verbindungen** marque a caixa de selção da conexão que você acabou de criar. Clique em  **Datenansicht erstellen**.

![Demo](./images/exta.png)

Você será Redrecionado para o fluxo de trabalho **Datenansicht erstellen** Arbeitsablauf.

![Demo](./images/0-v2.png)

## 4.3.2 Definição de Visualização de Dados

Agora você pode konfigurar als definições básicas para sua Visualização de dados.

![Demo](./images/0-v2.png)

A **Verbindung** que você criou no übício anteriore já está selecionada. Sua conexão se chama `yourLastName – Omnichannel Data Connection`.

![Demo](./images/ext5.png)

Em seguida, dê um nome à sua Visualização de Dados seguindo este modelo de nomenclatura: `yourLastName – Omnichannel Data View`.

Insira o mesmo valor para a descrição: `yourLastName – Omnichannel Data View`.

| Name | Beschreibung |
| ----------------- |-------------| 
| `yourLastName – Omnichannel Data View` | `yourLastName – Omnichannel Data View` |

![Demo](./images/1-v2.png)

Para **Zeitzone**, selecione o fuso horário **Berlim, Estocolmo, Roma, Berna, Bruxelas, Viena, Amsterdam GMT+01:00**. Este é um cenário realmente interessante, pois algumas empresas operam em diferentes países e geografias. Alocar o fuso horário certo para cada país evitará erros típicos de dados, como, por exemplo, acreditar que a maioria das pessoas compra camisetas às 4h no Peru.

![Demo](./images/ext7.png)

Você também pode modificar a nomenclatura das métricas principais (Pessoa, Sessão e Evento). Isso não é obrigatório, mas alguns clientes gostam de usar Pessoas, Visitas e Acessos em vez de Pessoa, Sessão e Eventos (Convenção de nomenclatura padrão do Customer Journey Analytics).

Agora você deve ter as seguintes configuration ações definiert das:

![Demo](./images/1-v2.png)

Clique em **Speichern und fortfahren**.

![Demo](./images/12-v2.png)

## 4.3.3 Componentes da Visualização de Dados

Neste übício, você irá konfigurar os components notwendiários para analisar os dados e visualizá-los usando Analysis Workspace. Nesta IU, há três áreas principais:

- Lado esquerdo: Component disponíveis dos datasets selecionados
- Medien: Componentes adicionados à Visualização de Dados
- Lado direito: Configurações do componente

![Demo](./images/2-v2.png)

>[!IMPORTANT]
>
>Se você não entrar uma métrica ou dimensão específica, verifique se o campo `Contains data` foi removido de sua visualização de dados. Caso contário, exclua esse campo.
>
>![Demo](./images/2-v2a.png)

Agora você recisa arrastar e soltar os components notwendiários para a análise nos **Komponenten hinzugefügt**. Para isso, você deve selecionar os components no menu à esquerda e arrastá-los e soltá-los na tela no meio.

Vamos começar com o primeiro component: **Name (web.webPageDetails.name)**. Pesquise esse component e arraste-o e solte-o na tela.

![Demo](./images/3-v2.png)

Esse component é o nome da página, como você pode derivar da leitura do campo do schema `(web.webPageDetails.name)`.

Keine entanto, usar **Name** como nome não é a melhor konventionção de nomenclatura para um usuário corporativo compreender rapidamente essa dimensão.

Vamos mudar o nome para **Seitenname**. Clique no component e o renomeie na área **Komponenteneinstellungen**.

![Demo](./images/3-0-v2.png)

Als Configurações de persistência são **Persistenz-Einstellungen**. Os conceitos de eVars e prop não existem no CJA, mas as configuration ações de Persistência possibility tam um comportamento semelhante.

![Demo](./images/3-0-v21.png)

Se você não alterar essas konfigurações, o CJA irá interpretar a dimensão como um **Prop** (nível de ocorrência). Além disso, podemos alterar a Persistência para tornar a dimensão uma **eVar** (persistir o valor ao longo da jornada).

Se você não estiver familiarizado com eVars e Props, [leia mais sobre isso na documentação](https://experienceleague.adobe.com/docs/analytics/landing/an-key-concepts.html).

Vamos deixar o Nome da Página como Prop. Dessa forma, você não recisa alterar nenhuma **Persistenz-Einstellungen**.

| Komponentenname zur Suche | Neuer Name | Persistenz-Einstellungen |
| ----------------- |-------------| --------------------| 
| Name (web.webPageDetails.name) | Seitenname |          |

Em seguida, escolha a dimensão **phoneNumber** e solte-a na tela. O novo nome deve ser **Telefonnummer**.

![Demo](./images/3-1-v2.png)

Por fim, vamos alterar as Configurações de persistência, pois o Número do Celular deve persistir no nível do usuário.

Para alterar a Persistência, role para baixo no menu à direita e abra a aba **Persistenz**:

![Demo](./images/5-v2.png)

Marque a caixa de selekção para modificar as configuration ações de persistência. Selecione **Zuletzt verwendet** e o escopo **Person (Berichtsfenster)**, pois nos preocupamos apenas com o último número de celular da pessoa. Siehe o cliente não preencher o celular em visitas futuras, você ainda verá esse valor preenchido.

![Demo](./images/6-v2.png)

| Komponentenname zur Suche | Neuer Name | Persistenz-Einstellungen |
| ----------------- |-------------| --------------------| 
| phoneNumber | Telefonnummer | Zuletzt verwendet, Person (Berichtsfenster) |

O próximo component é `web.webPageDetails.pageViews.value`.

No menu à esquerda, pesquise `web.webPageDetails.pageViews.value`. Array e solte essa métrica na tela.

Altere o nome para **Seitenansichten** unter **Komponenteneinstellungen**.

| Komponentenname zur Suche | Neuer Name | Attributionseinstellungen |
| ----------------- |-------------| --------------------| 
| web.webPageDetails.pageViews.value | Seitenansichten |         |

![Demo](./images/7-v2.png)

Para wie configuration ações de atribuição, deixaremos em branco.

Observação: Als konfigurações de persistência nas métricas também podem ser alteradas auf Analysis Workspace. Em alguns casos, você pode optar por configuration á-las aqui para evitar que os usuários de negócios tenham que pensar qual é o melhor modelo de persistência.

Em seguida, você terá que konfigurar várias Dimensões e Métricas, conforme indicado na tabela abaixo.

### DIMENES

| Komponentenname zur Suche | Neuer Name | Persistenz-Einstellungen |
| ----------------- |-------------| --------------------| 
| brandName | Markenname | Zuletzt verwendete Sitzung |
| Rückruf | Rufempfindlichkeit |          |
| Aufruf-ID | Interaktionstyp aufrufen |          |
| callTopic | Anrufthema | Zuletzt verwendete Sitzung |
| ecid | ECID | Zuletzt verwendet, Person (Berichtsfenster) |
| E-Mail | Email ID | Zuletzt verwendet, Person (Berichtsfenster) |
| Zahlungsart | Zahlungsart |          |
| Methode zum Hinzufügen von Produkten | Methode zum Hinzufügen von Produkten | Zuletzt verwendete Sitzung |
| Ereignistyp | Ereignistyp |         |
| Name (productListItems.name) | Produktname |         |
| SKU | SKU (Sitzung) | Zuletzt verwendete Sitzung |
| Transaction ID | Transaction ID |         |
| URL (web.webPageDetails.URL) | URL |         |
| Benutzeragent | Benutzeragent | Zuletzt verwendete Sitzung |

### MÉTRICA

| Komponentenname zur Suche | Neuer Name | Attributionseinstellungen |
| ----------------- |-------------| --------------------| 
| Menge | Menge |          |
| commerce.order.priceTotal | Umsatz |         |

Sua configuration ação deve ser semelhante ao seguinte:

![Demo](./images/11-v2.png)

Não se esqueça de Salvar sua Visualização de Dados. Então clique em **Speichern**.

![Demo](./images/12-v2s.png)

## 4.3.4 Métricas kalkadas

Embora tenhamos organizado todos os componentes na Visualização de dados, você ainda deve adaptar alguns deles para que os usuários de negócios estejam prontos para iniciar suas análises.

Se você se lembra, não trouxemos specificamente Métricas como Adicionar ao Carrinho, Visualização do produto ou Compras para a Visualização de dados. Keine entanto, temos uma dimensão chamada: **Ereignistyp**. Então, vamos derivar esses tipos de interação criando 3 métricas calculadas.

Vamos começar com a primeira Métrica: **Produktansichten**.

No lado esquerdo, pesquise **Ereignistyp** Wir wählen eine Dimension aus. Em seguida, arraste-o e solte-o na tela **Enthaltene Komponenten**.

![Demo](./images/calcmetr1.png)

Clique para selecionar a nova métrica **Ereignistyp**.

![Demo](./images/calcmetr2.png)

Agora altero nome e a descrição do componente para os seguintes valores:

| Name der Komponente | Komponentenbeschreibung |
| ----------------- |-------------| 
| Produktansichten | Produktansichten |

![Demo](./images/calcmetr3.png)

Agora vamos contar apenas eventos de **Produktansichten**. Para fazer isso, role para baixo em **Komponenteneinstellungen** até ver Valores de **Ausschlusswerte einschließen**. Certifique-se de abilitar a opção **Ein-/Ausschlusswerte festlegen**.

![Demo](./images/calcmetr4.png)

Como queremos contar apenas **Produktansichten**, specifique **commerce.productViews** nos critérios.

![Demo](./images/calcmetr5.png)

Agora a sua métrica calculada está pronta!

Em seguida, repita o mesmo processo para os eventos **Zum Warenkorb hinzufügen** e **Kauf**.

### Zum Warenkorb hinzufügen

Primeiro, arraste e solte a mesma dimensão **Ereignistyp**.

![Demo](./images/calcmetr1.png)

Você verá um alerta pop-up de um Campo Duplicado, pois estamos usando a mesma variável. Clique em **Alles hinzufügen**:

![Demo](./images/calcmetr6.png)

Agora, siga o mesmo processo que fiemos para a métrica Visualizações de produto:
- Primeiro altere o nome e a descrição.
- Por fim, adicion **commerce.productListAdds** como critério para contar apenas Zum Warenkorb hinzufügen

| Name | Beschreibung | Kriterien |
| ----------------- |-------------| -------------|
| Zum Warenkorb hinzufügen | Zum Warenkorb hinzufügen | commerce.productListAdds |

![Demo](./images/calcmetr6a.png)

### Käufe

Primeiro, arraste e solte a mesma dimensão **Ereignistyp** como fiemos para wie duas métricas anteriores.

![Demo](./images/calcmetr1.png)

Você verá um alerta pop-up de um Campo Duplicado, pois estamos usando a mesma variável. Clique em **Alles hinzufügen**:

![Demo](./images/calcmetr7.png)

Agora, siga o mesmo processo que ischemos para as métricas Produktansichten e Zum Warenkorb hinzufügen:
- Primeiro altere o nome e a descrição.
- Por fim, adicion **commerce.purchases** como critérios para contabilizar apenas as compras

| Name | Beschreibung | Kriterien |
| ----------------- |-------------| -------------|
| Käufe | Käufe | commerce.purchases |

![Demo](./images/calcmetr7a.png)

Sua konfiguração final deve ser semelhante ao seguinte. Clique em **Speichern und fortfahren**.

![Demo](./images/calcmetr8.png)

## 4.3.5 Componentes da Configuração de Dados

Você deve ser redirecionado para esta tela:

![Demo](./images/8-v2.png)

Nesta aba, você pode modificar algumas konfigurações importantes para alterar a forma como os dados são processados. Vamos começar definindo **Sitzungs-Timeout** Como 30 Min. Graças ao registro de data e hora de cada evento de experiência, você pode estender o konzept de uma sessão em todos os canais. Por exemplo, o que acontece se um cliente ligar para o call center depois de visitar o site? Usando Tempos Limite de Sessão personalizados, você tem muita flexibilidade para decidir o que é uma sessão e como essa sessão irá mesclar os dados.

![Demo](./images/ext8.png)

Nesta aba você pode modificar outras coisas como filtrar os dados usando um segmento/filtro. Você não preisará fazer isso neste übício.

![Demo](./images/10-v2.png)

Quando terminar, clique em **Speichern und beenden**.

![Demo](./images/13-v2.png)

>[!NOTE]
>
>Você pode volar a esta Visualização de dados posteriormente e alterar as configuration ações e os components a qualquer momento. Als alterações afetarão a forma como os dados históricos são mostrados.

Agora você pode Continuar com a parte de visualização e análise!

Próxima etapa: [4.4 Customer Journey Analytics des Präparação de dados](./ex4.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[Retornar para Todos os Módulos](./../../overview.md)

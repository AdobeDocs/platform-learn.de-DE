---
title: Bootcamp - Customer Journey Analytics - Verbinden von Adobe Experience Platform-Datensätzen in Customer Journey Analytics - Brasilien
description: Bootcamp - Customer Journey Analytics - Verbinden von Adobe Experience Platform-Datensätzen in Customer Journey Analytics - Brasilien
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
solution: Customer Journey Analytics
feature-set: Customer Journey Analytics
feature: Connections
exl-id: 51078fca-f234-4e50-96ba-ee7f5e286869
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---

# 4.2 Konkrete Datensätze da Adobe Experience Platform Customer Journey Analytics

## Objetivos

- Compreenda a UI da conexão de dados
- Traga os dados da Adobe Experience Platform para o CJA
- Entenda a ID da pessoa e a compilação de dados
- Aprenda o konzipiert de streaming de dados no Customer Journey

## 4.2.1 Conexão

Zugriff auf [analytics.adobe.com](https://analytics.adobe.com) para acessar o Customer Journey Analytics.

Na página inicial do Customer Journey Analytics, auf **Verbindungen** zugreifen.

![demo](./images/cja2.png)

Aqui você pode ver todas as diferentes conexões feitas entre o CJA e a Plataforma. Essas conexões têm o mesmo objetivo dos konuntos de relatórios no Adobe Analytics. Keine entanto, ein coleta dos dados é completamente diferente. Todos os dados vêm de datasets da Adobe Experience Platform.

Vamos criar sua primeira conexão. Klicken Sie auf em **Neue Verbindung erstellen**.

![demo](./images/cja4.png)

Você verá a UI **Erstellen einer Verbindung** -Benutzeroberfläche.

![demo](./images/cja5.png)

Agora você pode dar um nome à conexão.

Verwenden Sie das este Modell von nomenclatura: `yourLastName – Omnichannel Data Connection`.

Beispiel: `vangeluw - Omnichannel Data Connection`

Você também deve selecionar o sandbox correto para usar. Keine Menü-Sandbox, Selektions-Sandbox, que-deve-Benutzer `Bootcamp`. Neste Exemplo, o sandbox a ser usado é o **Bootcamp**. E você também deve definir **Durchschnittliche Anzahl der täglichen Ereignisse** bis **weniger als 1 Million**.

![demo](./images/cjasb.png)

Após selecionar seu sandbox, você pode começar a adicionar datensets a esta conexão. Klicken Sie auf em **Hinzufügen von Datensätzen**.

![demo](./images/cjasb1.png)

## 4.2.2 Selecione-Datensätze da Adobe Experience Platform

Pesquise auf Datensatz `Demo System - Event Dataset for Website (Global v1.1)`. Klicken Sie em **+** para adicionar oder Datensatz a esta conexão.

![demo](./images/cja7.png)

Agora pesquise e marque as caixas de selekção `Demo System - Event Dataset for Voice Assistants (Global v1.1)` and `Demo System - Event Dataset for Call Center (Global v1.1)`.

Em seguida, você verá a tela abaixo. Klicken Sie auf em **Weiter**.

![demo](./images/cja9.png)

## 4.2.3 ID da pessoa e compilação de dados

### ID da pessoa

O objetivo agora é juntar verwendet Datensätze. Para cada dataset selecionado, você verá um campo chamado **Personen-ID**. Cada dataset tem seu próprio campo de ID de pessoa.

![demo](./images/cja11.png)

Como você pode ver, a maioria deles tem o ID da pessoa selecionado automaticamente. Isso ocorre porque um identificador principal é selecionado em cada esquema na Adobe Experience Platform. Como exemplo, aqui está o esquema para `Demo System - Event Schema for Call Center (Global v1.1)`, onde você pode ver que o Identificador Primário está definido como `phoneNumber`.

![demo](./images/cja13.png)

Keine entanto, você ainda pode influenciar qual identificador será usado para compilar datasets para sua conexão. Você pode usar qualquer identificador konfigurado no esquema vinculado ao seu dataset. Klicken Sie auf kein Menü Suspenso para explorar os IDs disponíveis em cada dataset.

![demo](./images/cja14.png)

Conforme mencionado, você pode definir diferentes IDs de pessoa para cada dataset. Isso permite reunir diferentes datasets de múltiplas origens no CJA. Stellen Sie sich vor, der NPS ou dados de pesquisa que seriam muito interessantes e úteis para compreender o contexto e o motivo de um acontecimento.

O nome do campo ID da pessoa não é importante, desde que o valor nos campos ID da pessoa corresponda. Digamos que temos `email` em um dataset e `emailAddress` em outro dataset definido como ID da pessoa. Siehe `delaigle@adobe.com` verver o mesmo valor para o campo ID da pessoa em ambos os datasets, o CJA poderá compilar os dados.

Atualmente, existem algumas outras limitações, como compilar o comportamento anônimo para conhecido. Consulte as perguntas frequentes aqui: [FAQ](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-faq.html).


### Compilando os dados usando o o ID da pessoa

Agora que você compreende o konzepto de compilar datensets usando o ID da pessoa, vamos escolher `email` como ID da pessoa para cada dataset.

![demo](./images/cja15.png)

Acesse cada dataset para atualizar o ID da pessoa.

![demo](./images/cja12a.png)

Agora preencha o campo ID da pessoa escolhendo `email` na lista Susensa.

![demo](./images/cja17.png)

Depois de compilar os três -Datensätze, estamos prontos para Continuar.

| datensatz | Personen-ID |
| ----------------- |-------------| 
| Demosystem - Ereignis-Datensatz für Website (Global v1.1) | E-Mail |
| Demosystem - Ereignis-Datensatz für Sprachassistenten (Global v1.1) | E-Mail |
| Demosystem - Ereignis-Datensatz für das Callcenter (Global v1.1) | E-Mail |

Você também preisa garantir que, para cada dataset, essas opções estejam abilitadas:

- Wichtige Todos os novos dados
- Preencher todos os dados existentes
- Preencher tipo de fonte de dados com &quot;Others&quot;
- Preencher a descrição com o mesmo nome do Dataset

Klicken Sie auf em **Hinzufügen von Datensätzen**.

![demo](./images/cja16.png)

Klicken Sie em **Save** e vá para o próximo übício. Depois de criar sua **Connection**, pode levar algumas horas até que seus dados estejam disponíveis no CJA.

![demo](./images/cja20.png)

Próxima etapa: [4.3 Crie uma Visualização de Dados](./ex3.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[Retornar para Todos os Módulos](./../../overview.md)

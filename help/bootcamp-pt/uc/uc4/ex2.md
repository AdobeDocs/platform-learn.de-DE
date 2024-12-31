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

# 4.2 Verknüpfte Datensätze da Adobe Experience Platform ohne Customer Journey Analytics

## objektivisch

- Compreenda a UI da conexão de dados
- Traga os dados da Adobe Experience Platform para o CJA
- Entenda a ID da pessoa e a compilação de dados
- Aprenda o conceito de streaming de dados no Customer Journey

## 4.2.1 Conexão

Acesse [analytics.adobe.com](https://analytics.adobe.com) para acessar o Customer Journey Analytics.

Na página inicial do Customer Journey Analytics, acesse **Connections**.

![demo](./images/cja2.png)

Aqui você pode ver todas as diferentes conexões feitas entre o CJA e a Plataforma. Essas conexões têm o mesmo objetivo dos conjuntos de relatórios no Adobe Analytics. Kein entanto, a coleta dos dados é completamente diferente. Todos os dados vêm de datasets da Adobe Experience Platform.

In: Vamos criar sua primeira conexão. Klicken Sie auf **Neue Verbindung erstellen**.

![demo](./images/cja4.png)

Você verá a UI **Verbindung erstellen** UI.

![demo](./images/cja5.png)

Agora você pode dar um nome à sua conexão.

Verwenden Sie ESTE modelo de nomenclatura: `yourLastName – Omnichannel Data Connection`.

Beispiel: `vangeluw - Omnichannel Data Connection`

Você também deve selecionar o sandbox correto para usar. Keine Menü-Sandbox, wählen Sie Seu-Sandbox, que deve ser `Bootcamp` aus. Neste exemplo, o sandbox a ser usado é o **Bootcamp**. E você também deve definir o **Durchschnittliche Anzahl der täglichen Veranstaltungen** bis **weniger als 1 Million**.

![demo](./images/cjasb.png)

Após selecionar seu sandbox, você pode começar a adicionar datasets a esta conexão. Klicken Sie auf **Datensätze hinzufügen**.

![demo](./images/cjasb1.png)

## 4.2.2 Auswahldatensätze da Adobe Experience Platform

Drücken Sie auf `Demo System - Event Dataset for Website (Global v1.1)` Datensatz. Clique em **+** para adicionar o dataset a esta conexão.

![demo](./images/cja7.png)

Agora pesquise e marque als Caixas de Seleção `Demo System - Event Dataset for Voice Assistants (Global v1.1)` und `Demo System - Event Dataset for Call Center (Global v1.1)`.

Em seguida, você verá a tela abaixo Klicken Sie auf **Weiter**.

![demo](./images/cja9.png)

## 4.2.3 Ausweisdokument da pessoa e compilação de dados

### ID da pessoa

Datensätze von Objetivo agora é juntars. Para cada dataset selecionado, você verá um campo chamado **Personen-ID**. Cada dataset tem seu próprio campo de ID de pessoa.

![demo](./images/cja11.png)

Como você pode ver, a maioria deles tem o ID da pessoa selecionado automaticamente. Isso ocorre porque um identificador principal é selecionado em cada esquema na Adobe Experience Platform. Como exemplo, aqui está o esquema para `Demo System - Event Schema for Call Center (Global v1.1)`, onde você pode ver que o Identificador Primário está definido como `phoneNumber`.

![demo](./images/cja13.png)

No entanto, você ainda pode influenciar qual identificador será usado para compilar datasets para sua conexão. Você pode usar qualquer identificador configurado no esquema vinculado ao seu dataset. Klicken Sie auf das Menü suspenso para explorar os IDs disponíveis em cada datensatz.

![demo](./images/cja14.png)

Conforme mencionado, você pode definir diferentes IDs de pessoa para cada. Isso permite reunir diverentes datasets de múliplas origens on CJA. Stellen Sie sich Trazer NPS oder dados de pesquisa que seriam muito interessantes e úteis para compreender o contexto e o motivo de um acontecimento vor.

O nome do campo ID da pessoa não é importante, desde que o valor nos campos ID da pessoa corresponda. Digamos que temos `email` em um dataset e `emailAddress` em outro dataset definido como ID da pessoa. Se `delaigle@adobe.com` tiver o mesmo valor para o campo ID da pessoa em ambos os datasets, o CJA poderá compilar os dados.

Atualmente, existem algumas outras limitações, compilar o comportamento anônimo para conhecido. Konsultieren Sie als perguntas frequentes aqui: [FAQ](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-faq.html).


### Compilando os dados usando o ID da pessoa

Agora que você compreende o concito de compilar datasets usando o o ID da pessoa, vamos escolher `email` como ID da pessoa para cada dataset.

![demo](./images/cja15.png)

Zugriff auf den Datensatz para atualizar o ID da pessoa.

![demo](./images/cja12a.png)

Agora preencha o campo ID da pessoa escolhendo o `email` na lista suspensa.

![demo](./images/cja17.png)

Depois de compilar os três datasets, estamos prontos para continuar.

| datensatz | Personen-ID |
| ----------------- |-------------| 
| Demosystem - Ereignisdatensatz für eine Website (Global v1.1) | E-Mail |
| Demosystem - Ereignisdatensatz für Sprachassistenten (Global v1.1) | E-Mail |
| Demosystem - Ereignisdatensatz für Callcenter (Global v1.1) | E-Mail |

Você também precisa garantir que, para cada dataset, essas opções estejam habilitadas:

- Wichtige todos os novos dados
- Preencher todos os dados existentes
- Preencher tipo de fonte de dados com „Sonstige“
- Preencher a descrição com o mesmo nome do Dataset

Klicken Sie auf **Datensätze hinzufügen**.

![demo](./images/cja16.png)

Clique em **Save** e vá para o próximo exercício. Depois de criar **Connection**, pode levar algumas horas até que seus dados estejam disponíveis no CJA.

![demo](./images/cja20.png)

Próxima etapa: [4.3 Crie uma visualização de Dados](./ex3.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[In: Retornar para Todos os Módulos](./../../overview.md)

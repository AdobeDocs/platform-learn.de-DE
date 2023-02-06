---
title: Bootcamp - Customer Journey Analytics - Adobe Experience Platform-Datensätze in Customer Journey Analytics verbinden - Brasilien
description: Bootcamp - Customer Journey Analytics - Adobe Experience Platform-Datensätze in Customer Journey Analytics verbinden - Brasilien
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
source-git-commit: 9cc01c7d3018319137f915e103bce9dc39b0d472
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 2%

---

# 4.2 Konkrete Datensätze da Adobe Experience Platform kein Customer Journey Analytics

## Objetivos

- Compreenda a UI da conexão de dados
- Traga os dados da Adobe Experience Platform para o CJA
- Entenda a ID da pessoa e a compilação de dados
- Aprenda o konzipiert de streaming de dados no Customer Journey

## 4.2.1 Conexão

Acesse [analytics.adobe.com](https://analytics.adobe.com) para acessar oder Customer Journey Analytics.

Na página inicial do Customer Journey Analytics, acesse **Verbindungen**.

![Demo](./images/cja2.png)

Aqui você pode ver todas as diferentes conexões feitas entre o CJA e a Plataforma. Essas conexões têm o mesmo objetivo dos konuntos de relatórios no Adobe Analytics. Keine entanto, ein coleta dos dados é completamente diferente. Todos os dados vêm de datasets da Adobe Experience Platform.

Vamos criar sua primeira conexão. Clique em **Neue Verbindung erstellen**.

![Demo](./images/cja4.png)

Você verá a UI **Verbindung erstellen** Benutzeroberfläche.

![Demo](./images/cja5.png)

Agora você pode dar um nome à sua conexão.

Verwenden Sie das este Modell de nomenclatura: `yourLastName – Omnichannel Data Connection`.

Exemplar: `vangeluw - Omnichannel Data Connection`

Você também deve selecionar o sandbox correto para usar. No menu sandbox, selecione seu sandbox, que deve ser `Bootcamp`. Neste Exemplo, o sandbox a ser usado é o **Bootcamp**. E você também deve definir **Durchschnittliche Anzahl der täglichen Ereignisse** nach **weniger als 1 Million**.

![Demo](./images/cjasb.png)

Após selecionar seu sandbox, você pode começar a adicionar datensets a esta conexão. Clique em **Hinzufügen von Datensätzen**.

![Demo](./images/cjasb1.png)

## 4.2.2 Selecione-Datensätze da Adobe Experience Platform

Pesquise oder Datensatz `Demo System - Event Dataset for Website (Global v1.1)`. Clique em **+** para adicionar o dataset a esta conexão.

![Demo](./images/cja7.png)

Agora pesquise e marque as caixas de selekção `Demo System - Event Dataset for Voice Assistants (Global v1.1)` und `Demo System - Event Dataset for Call Center (Global v1.1)`.

Em seguida, você verá a tela abaixo. Clique em **Nächste**.

![Demo](./images/cja9.png)

## 4.2.3 ID da pessoa e compilação de dados

### ID da pessoa

O objetivo agora é juntar verwendet Datensätze. Para cada dataset selecionado, você verá um campado **Personen-ID**. Cada dataset tem seu próprio campo de ID de pessoa.

![Demo](./images/cja11.png)

Como você pode ver, a maioria deles tem o ID da pessoa selecionado automaticamente. Isso ocorre porque um identificador principal é selecionado em cada esquema na Adobe Experience Platform. Como exemplo, aqui está o esquema para `Demo System - Event Schema for Call Center (Global v1.1)`, onde você pode ver que o Identificador Primário está definido como `phoneNumber`.

![Demo](./images/cja13.png)

Keine entanto, você ainda pode influenciar qual identificador será usado para compilar datasets para sua conexão. Você pode usar qualquer identificador konfigurado no esquema vinculado ao seu dataset. Klicken Sie auf kein Menü Suspenso para explorar os IDs disponíveis em cada dataset.

![Demo](./images/cja14.png)

Conforme mencionado, você pode definir diferentes IDs de pessoa para cada dataset. Isso permite reunir diferentes datasets de múltiplas origens no CJA. Stellen Sie sich vor, der NPS ou dados de pesquisa que seriam muito interessantes e úteis para compreender o contexto e o motivo de um acontecimento.

O nome do campo ID da pessoa não é importante, desde que o valor nos campos ID da pessoa corresponda. Digamos que temos `email` em um dataset e `emailAddress` em outro dataset definido como ID da pessoa. Siehe `delaigle@adobe.com` Veretiver o mesmo valor para o campo ID da pessoa em ambos os datasets, o CJA poderá compilar os dados.

Atualmente, existem algumas outras limitações, como compilar o comportamento anônimo para conhecido. Consulte as perguntas frequentes aqui: [FAQs](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-faq.html?lang=de).


### Compilando os dados usando o o ID da pessoa

Agora que você compreende o concept de compilar datensets usando o ID da pessoa, vamos escolher `email` como ID da pessoa para cada dataset.

![Demo](./images/cja15.png)

Acesse cada dataset para atualizar o ID da pessoa.

![Demo](./images/cja12a.png)

Agora preencha o campo ID da pessoa escolhendo `email` las lista Susensa.

![Demo](./images/cja17.png)

Depois de compilar os três -Datensätze, estamos prontos para Continuar.

| Datensatz | Personen-ID |
| ----------------- |-------------| 
| Demosystem - Ereignis-Datensatz für Website (Global v1.1) | email |
| Demosystem - Ereignis-Datensatz für Sprachassistenten (Global v1.1) | email |
| Demosystem - Ereignis-Datensatz für das Callcenter (Global v1.1) | email |

Você também preisa garantir que, para cada dataset, essas opções estejam abilitadas:

- Wichtige Tools os novos dados
- Preencher todos os dados existentes

Clique em **Hinzufügen von Datensätzen**.

![Demo](./images/cja16.png)

Clique em **Speichern** e vá para o próximo übício. Depois de criar sua **Verbindung**, pode levar algumas horas até que seus dados estejam disponíveis no CJA.

![Demo](./images/cja20.png)

Próxima etapa: [4.3 Crie uma Visualização de Dados](./ex3.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[Retornar para Todos os Módulos](./../../overview.md)

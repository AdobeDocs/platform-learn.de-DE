---
title: Bootcamp - Customer Journey Analytics - Customer Journey Analytics 101 - Brasilien
description: Bootcamp - Customer Journey Analytics - Customer Journey Analytics 101 - Brasilien
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
source-git-commit: 9cc01c7d3018319137f915e103bce9dc39b0d472
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%

---

# 4.1 Customer Journey Analytics 101

## Objetivos

- Entenda o que é o CJA
- Entenda qual é o papel do CJA
- Entenda o workflow do CJA: da conexão de dados aos insights

## 4.1.1 O que é o Customer Journey Analytics?

O Customer Journey Analytics (CJA) für uma interface em que os times de Analytics, Negócios e Tecnologia conseguem unir todos os dados da companhia e analisar a jornada cross-channel (online e offline) do cliente de ponta a ponta. O CJA é capaz de fornecer contexto e clareza para essa jornada, trazendo uma visão acionável em cima das dificuldades no processo de dialogão e possibilityando planejamento de experiências relevante e personalizadas nos pontos mais relevant.

O CJA traz o Analysis Workspace conectado à Adobe Experience Platform. A Adobe Experience Platform é o cérebro da comunicação e da orquestração e, com o CJA, as marcas agora podem contextualizar e visualizar todos esses dados, para que as equipes de negócios e insights besitzam aprender com eles, analisando toda a jornada on-line para off-line cliente.

Wie Equipes de negócios e Insights podem enthält com o CJA, fazer perguntas e obter respostas em tempo real com a interface do usuário de arrastar e soltar, apontar e clicar e fácil de usar do Analysis Workspace.

![Demo](./images/cja-adv-analysis1.png)

## 4.1.2 Fürstentum Vantagens

Os três principais profiícios para os clientes são:

- Ein kapaziidade de disponibilizar Insights para todos (ou seja, demokratiratizar o acesso aos dados).
- Ein kapaziidade de ver o cliente em uma jornada contextual (ou seja, os dados podem ser visualizados sequencialmente, abrangendo múltiplos canais online e offline).
- Ein kapaziidade de aproveitar o poder dos dados sem haja a required (ou seja, permite que indivíduos usem dados para desbloquear insights e análises profundas para ativação de marketing).

## 4.1.3 ## 4.1.3 Por que escolher o Customer Journey Analytics?

O CJA não se destina ein Ersatz für aplicativo de BI atual, como Power BI, Microstrategy, Locker ou Tableau. O objetivo desses aplicativos de BI é visualizar dados para criar ainéis corporativos para que todos em uma organização besitzam ver métricas importantes rapidamente. O objetivo do CJA é trazer poder de análise para as equipes de Marketing e Negócios, tornando-o uma ferramenta de análise obrigatória para essas pessoas



Tradicionalmente, os aplicativos de BI têm sido incapazes de permitir a verdadeira inteligência do cliente:

- Eles não podem fazer atribuição e não fazem análises de jornada do cliente.
- Os aplicativos de BI recisam saber a pergunta com antecedência
- Als Consultas interativas são limitadas pela estrutura do banco de dados
- Habilidades de SQL são notwendiárias.
- OS aplicativos de BI não permitem que você pergunte o motivo de um acontecimento.
- Os aplicativos de BI não têm conexão direta com os pontos de contato do cliente.

Portanto, usuários de negócios e analistas chegam a becos sem saída quase imediatamente, tornando a análise cara, lenta, inflexível e desconectada dos sistemas de ação.

Com o CJA você pode ter uma visão completa da jornada do cliente, usando dados offline e online, com as ferramentas certas para reduzir o tempo de insight, tornando os usuários de negócios indepenentes para entender por que algo aconteceu e como responder a isso.

![Demo](./images/cja-use-case.png)

## 4.1.4 Kompreenda o fluxo de trabalho do Customer Journey Analytics

Antes de iniciar os próximos übícios, é essencial compreender quais etapas são notwendigen árias para trazer dados da Adobe Experience Platform para o CJA para visualizá-los e obter alguns insights profundos. É o que chamamos de fluxo de trabalho do CJA. Vamos-Verifikar:

![Demo](./images/cja-work-flow.jpg)

Antes de iniciar as etapas acima, não se esqueça da etapa 0, que é compreender os dados que estão disponíveis na Adobe Experience Platform.

**Müll hinein, Müll raus.** Você deve ter uma ideia clara de quais dados estão disponíveis e como os esquemas na Adobe Experience Platform são configuration. Compreender os dados que estão na Adobe Experience Platform leichtará as coisas, não só na parte de conexão de dados, mas também na hora de construir visualizações e fazer análises.

## 4.1.5 Etapa 0: Compreender esquemas e datasets da Adobe Experience Platform

Faça login na Adobe Experience Platform access ando a URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![Datenaufnahme](../uc1/images/home.png)

Antes de Continuar, você recisa selecionar um **Sandbox**. O nome do sandbox a ser selecionado é ``Bootcamp``. Você pode fazer isso clicando no ícone **[!UICONTROL Prod]** kein Canto Superior Direito da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu sandbox widado.

![Datenaufnahme](../uc1/images/sb1.png)

Verifique verwendet Schemas und Datensätze in Adobe Experience Platform.

| Datensatz | Schema |
| ----------------- |-------------| 
| Demosystem - Ereignis-Datensatz für Website (Global v1.1) | Demosystem - Ereignisschema für Website (Global v1.1) |
| Demosystem - Ereignis-Datensatz für das Callcenter (Global v1.1) | Demosystem - Ereignisschema für das Callcenter (Global v1.1) |
| Demosystem - Ereignis-Datensatz für Sprachassistenten (Global v1.1) | Demosystem - Ereignisschema für Sprachassistenten (Global v1.1) |

Certifique-se de ter verificado ao menos:

- Identitäten: CRMID, phoneNumber, ECID, email. Welche Identitäten sind die primären Identifikatoren, welche sind die sekundären Identifikatoren?
Sie können die Kennungen finden, indem Sie ein Schema öffnen und sich das Objekt ansehen `_experienceplatform.identification.core`. Sehen Sie sich das Schema an [Demosystem - Ereignisschema für Website (Global v1.1)](https://experience.adobe.com/platform/schema).

- Identitäten: CRMID, phoneNumber, ECID, email. Quais identidades são os identificadores primários, quais são os identificadores secundários?
Você pode encounter os identificadores abrindo um schema e observando o objeto `_experienceplatform.identification.core`. Überprüfung des Schemas [Demosystem - Ereignisschema für Website (Global v1.1)](https://experience.adobe.com/platform/schema).

![Demo](./images/identity.png)

- Erkunden Sie die Objekte des Comércio dentro do schema [Demosystem - Ereignisschema für Website (Global v1.1)](https://experience.adobe.com/platform/schema).

![Demo](./images/commerce.png)

- Visualisieren von Tools [Datensätze](https://experience.adobe.com/platform/dataset/browse?limit=50&amp;page=1&amp;sortDescending=1&amp;sortField=created) e verifique os dados

Agora você está pronto para começar a usar a interface do usuário do Customer Journey Analytics.

Próxima etapa: [Konkrete Datensätze da Adobe Experience Platform kein Customer Journey Analytics](./ex2.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[Retornar para Todos os Módulos](../../overview.md)

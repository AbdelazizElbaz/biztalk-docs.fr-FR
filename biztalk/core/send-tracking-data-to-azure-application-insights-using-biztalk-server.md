---
title: "Envoyer des données de suivi à Azure Application Insights à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3ff6cb9-44d0-46cd-9b4f-a346365afb7b
caps.latest.revision: "10"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: f587c3049e191505c87ba456b5ddfd41011862c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="send-tracking-data-to-azure-application-insights-using-biztalk-server"></a><span data-ttu-id="8bb13-102">Envoyer des données de suivi à Azure Application Insights à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="8bb13-102">Send tracking data to Azure Application Insights using BizTalk Server</span></span>
<span data-ttu-id="8bb13-103">Envoyer [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] les données de suivi à Inisights d’Application Azure.</span><span class="sxs-lookup"><span data-stu-id="8bb13-103">Send [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] tracking data to Azure Application Inisights.</span></span> 

<span data-ttu-id="8bb13-104">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , vous pouvez traiter et envoyer vos données de suivi à Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="8bb13-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, you can process and send your tracking data to Azure Application Insights.</span></span> <span data-ttu-id="8bb13-105">Utiliser les fonctionnalités de l’Application Insights pour effectuer le suivi de vos instances à partir des orchestrations, ports d’envoi et ports de réception.</span><span class="sxs-lookup"><span data-stu-id="8bb13-105">Use the Application Insights features to track your instances from receive ports, send ports, and orchestrations.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8bb13-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8bb13-106">Prerequisites</span></span>
* <span data-ttu-id="8bb13-107">Créer une nouvelle instance de [Application Insights](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)</span><span class="sxs-lookup"><span data-stu-id="8bb13-107">Create a new instance of [Application Insights](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)</span></span>
* <span data-ttu-id="8bb13-108">Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bb13-108">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>

## <a name="enable-analytics-for-your-environment"></a><span data-ttu-id="8bb13-109">Activer analytique pour votre environnement</span><span class="sxs-lookup"><span data-stu-id="8bb13-109">Enable analytics for your environment</span></span>

1. <span data-ttu-id="8bb13-110">Ouvrir le **Administration de BizTalk Server** de la console, développez **Administration de BizTalk**, avec le bouton droit le **groupe BizTalk**, puis sélectionnez **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="8bb13-110">Open the **BizTalk Server Administration** console, expand **BizTalk Administration**, right-click the **BizTalk Group**, and select **Settings**.</span></span> 
2. <span data-ttu-id="8bb13-111">Vérifiez **activer au niveau du groupe analytique**.</span><span class="sxs-lookup"><span data-stu-id="8bb13-111">Check **Enable group-level analytics**.</span></span>
3. <span data-ttu-id="8bb13-112">Pour le **type cible**, sélectionnez **Application Insight** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="8bb13-112">For the **Target type**, select **Application Insight** from the list.</span></span>
4. <span data-ttu-id="8bb13-113">Pour le **les paramètres de connexion**, entrez votre Application Insights  **[clé d’instrumentation](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)**  (disponible dans le portail Azure).</span><span class="sxs-lookup"><span data-stu-id="8bb13-113">For the **Connection parameters**, enter your Application Insights **[instrumentation key](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)** (available in the Azure portal).</span></span>

    <span data-ttu-id="8bb13-114">Paramètres de votre groupe se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="8bb13-114">Your Group settings look similar to the following:</span></span> 

    ![Activer analytique pour votre environnement](../core/media/environmentsettingapplicationinishgt.PNG)

5. <span data-ttu-id="8bb13-116">Sélectionnez **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="8bb13-116">Select **OK** to save your changes.</span></span> 

<span data-ttu-id="8bb13-117">Une fois activé, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] est prêt à transmettre des données à Application Insights.</span><span class="sxs-lookup"><span data-stu-id="8bb13-117">Once enabled, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] is ready to transmit data to Application Insights.</span></span> <span data-ttu-id="8bb13-118">Ensuite, activez l’analytique sur vos orchestrations et les ports.</span><span class="sxs-lookup"><span data-stu-id="8bb13-118">Next, enable analytics on your ports and orchestrations.</span></span> 

## <a name="enable-analytics-on-your-artifacts"></a><span data-ttu-id="8bb13-119">Activer l’analytique sur vos artefacts</span><span class="sxs-lookup"><span data-stu-id="8bb13-119">Enable analytics on your artifacts</span></span>

1. <span data-ttu-id="8bb13-120">Dans la console Administration de BizTalk Server, cliquez sur un **port de réception**, **port d’envoi** ou **orchestration**, puis sélectionnez **suivi**.</span><span class="sxs-lookup"><span data-stu-id="8bb13-120">In BizTalk Server Administration, right-click a **receive port**, **send port** or **orchestration**, and select **Tracking**.</span></span>
2. <span data-ttu-id="8bb13-121">Sous **Analytique**, vérifiez **activer l’Analytique**.</span><span class="sxs-lookup"><span data-stu-id="8bb13-121">Under **Analytics**, check **Enable Analytics**.</span></span> <span data-ttu-id="8bb13-122">Ce paramètre lance le suivi et la transmission de données à partir de l’artefact à Application Insights.</span><span class="sxs-lookup"><span data-stu-id="8bb13-122">This setting starts tracking and transmitting data from the artifact to Application Insights.</span></span>

    <span data-ttu-id="8bb13-123">Vos paramètres de l’artefact se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="8bb13-123">Your artifact settings look similar to the following:</span></span> 
    
    ![Données de suivi pour l’Orchestration](../core/media/orchestrationsettingsapplicationinsight.PNG)

3. <span data-ttu-id="8bb13-125">Sélectionnez **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="8bb13-125">Select **OK** to save your changes.</span></span>

<span data-ttu-id="8bb13-126">Ensuite, exécutez les requêtes dans Application Insights pour afficher vos données.</span><span class="sxs-lookup"><span data-stu-id="8bb13-126">Next, run queries within Application Insights to see your data.</span></span>  

> [!TIP]
> <span data-ttu-id="8bb13-127">Se connecter à votre Analytique du serveur BizTalk avec les autres systèmes pour avoir une idée davantage de données de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="8bb13-127">Connect your BizTalk Server Analytics with other systems to gain even more insight into your organizations data.</span></span>

## <a name="run-queries-on-your-data"></a><span data-ttu-id="8bb13-128">Exécuter des requêtes sur vos données</span><span class="sxs-lookup"><span data-stu-id="8bb13-128">Run queries on your data</span></span>
<span data-ttu-id="8bb13-129">Une fois que les données sont envoyées à Application Insights, vous pouvez utiliser les outils d’analytique dans Azure pour créer des requêtes avancées et analyser vos données.</span><span class="sxs-lookup"><span data-stu-id="8bb13-129">Once the data is sent to Application Insights, you can use the analytics tools within Azure to create advanced queries, and analyze your data.</span></span>

1. <span data-ttu-id="8bb13-130">Se connecter à la [portail Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="8bb13-130">Sign in to the [Azure Portal](https://portal.azure.com).</span></span>
2. <span data-ttu-id="8bb13-131">Ouvrez votre ressource Application Insights, puis sélectionnez **Analytique**.</span><span class="sxs-lookup"><span data-stu-id="8bb13-131">Open your Application Insights resource, and select **Analytics**.</span></span>
3. <span data-ttu-id="8bb13-132">Sélectionnez **utilisation**, et exécutez la requête fournie.</span><span class="sxs-lookup"><span data-stu-id="8bb13-132">Select **usage**, and run the query provided.</span></span>

    > [!TIP]
    > <span data-ttu-id="8bb13-133">En savoir plus sur la façon d’écrire des requêtes dans Application Insights à [Analytique dans Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics).</span><span class="sxs-lookup"><span data-stu-id="8bb13-133">Learn more about how to write queries in Application Insights at [Analytics in Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="8bb13-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8bb13-134">See also</span></span>
 [<span data-ttu-id="8bb13-135">Configurer le Pack de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="8bb13-135">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)
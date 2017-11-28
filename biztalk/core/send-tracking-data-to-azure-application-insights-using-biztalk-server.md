---
title: "Envoyer des données de suivi à Azure Application Insights | Documents Microsoft"
description: "Installer le feature pack pour permettre l’analytique des données suivies avec Azure Application Insights dans BizTalk Server"
ms.custom: fp1
ms.date: 11/06/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3ff6cb9-44d0-46cd-9b4f-a346365afb7b
caps.latest.revision: "10"
author: tordgladnordahl
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a65ffd2c5ee76d857effde6ab82dddf17b3de4b
ms.sourcegitcommit: 30189176c44873e3de42cc5f2b8951da51ffd251
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="send-tracking-data-to-azure-application-insights-using-biztalk-server"></a><span data-ttu-id="a9dd0-103">Envoyer des données de suivi à Azure Application Insights à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a9dd0-103">Send tracking data to Azure Application Insights using BizTalk Server</span></span>

<span data-ttu-id="a9dd0-104">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , vous pouvez traiter et envoyer vos données de suivi à Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, you can process and send your tracking data to Azure Application Insights.</span></span> <span data-ttu-id="a9dd0-105">Utiliser les fonctionnalités de l’Application Insights pour effectuer le suivi de vos instances à partir des orchestrations, ports d’envoi et ports de réception.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-105">Use the Application Insights features to track your instances from receive ports, send ports, and orchestrations.</span></span>
          
> [!IMPORTANT]
> <span data-ttu-id="a9dd0-106">Actuellement, cette fonctionnalité ne fonctionne pas avec des Instances nommées de SQL.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-106">This feature currently does not work with SQL Named Instances.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a9dd0-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a9dd0-107">Prerequisites</span></span>
* <span data-ttu-id="a9dd0-108">Créer une nouvelle instance de [Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-create-new-resource).</span><span class="sxs-lookup"><span data-stu-id="a9dd0-108">Create a new instance of [Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-create-new-resource).</span></span> <span data-ttu-id="a9dd0-109">Dans ses propriétés, copiez la **clé d’Instrumentation**.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-109">In its properties, copy the **Instrumentation Key**.</span></span> <span data-ttu-id="a9dd0-110">Collez-le dans un autre fichier afin que vous ayez prêt.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-110">Paste it in another file so you have it ready.</span></span> <span data-ttu-id="a9dd0-111">Nous utilisons cette clé dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-111">We use this key within BizTalk Server.</span></span> 
* <span data-ttu-id="a9dd0-112">Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9dd0-112">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>

## <a name="enable-analytics-for-your-environment"></a><span data-ttu-id="a9dd0-113">Activer analytique pour votre environnement</span><span class="sxs-lookup"><span data-stu-id="a9dd0-113">Enable analytics for your environment</span></span>

1. <span data-ttu-id="a9dd0-114">Ouvrir le **Administration de BizTalk Server** de la console, cliquez sur le **groupe BizTalk**, puis sélectionnez **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-114">Open the **BizTalk Server Administration** console, right-click the **BizTalk Group**, and select **Settings**.</span></span> 
2. <span data-ttu-id="a9dd0-115">Vérifiez **activer au niveau du groupe analytique**.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-115">Check **Enable group-level analytics**.</span></span>
3. <span data-ttu-id="a9dd0-116">Pour le **type cible**, sélectionnez **Application Insight** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-116">For the **Target type**, select **Application Insight** from the list.</span></span>
4. <span data-ttu-id="a9dd0-117">Pour le **les paramètres de connexion**, entrez votre Application Insights  **[clé d’instrumentation](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)**  (disponible dans le portail Azure).</span><span class="sxs-lookup"><span data-stu-id="a9dd0-117">For the **Connection parameters**, enter your Application Insights **[instrumentation key](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)** (available in the Azure portal).</span></span> <span data-ttu-id="a9dd0-118">Paramètres de votre groupe se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="a9dd0-118">Your Group settings look similar to the following:</span></span> 

    ![Activer analytique pour votre environnement](../core/media/environmentsettingapplicationinishgt.PNG)

5. <span data-ttu-id="a9dd0-120">Sélectionnez **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-120">Select **OK** to save your changes.</span></span> 

<span data-ttu-id="a9dd0-121">Une fois activé, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] est prêt à transmettre des données à Application Insights.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-121">Once enabled, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] is ready to transmit data to Application Insights.</span></span> <span data-ttu-id="a9dd0-122">Ensuite, activez l’analytique sur vos orchestrations et les ports.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-122">Next, enable analytics on your ports and orchestrations.</span></span> 

## <a name="enable-analytics-on-your-artifacts"></a><span data-ttu-id="a9dd0-123">Activer l’analytique sur vos artefacts</span><span class="sxs-lookup"><span data-stu-id="a9dd0-123">Enable analytics on your artifacts</span></span>

1. <span data-ttu-id="a9dd0-124">Dans la console Administration de BizTalk Server, cliquez sur un **port de réception**, **port d’envoi** ou **orchestration**, puis sélectionnez **suivi**.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-124">In BizTalk Server Administration, right-click a **receive port**, **send port** or **orchestration**, and select **Tracking**.</span></span>
2. <span data-ttu-id="a9dd0-125">Sous **Analytique**, vérifiez **activer l’Analytique**, semblable au suivant.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-125">Under **Analytics**, check **Enable Analytics**, similar to the following.</span></span> <span data-ttu-id="a9dd0-126">Ce paramètre lance le suivi et la transmission de données à partir de l’artefact à Application Insights.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-126">This setting starts tracking and transmitting data from the artifact to Application Insights.</span></span>
    
    ![Données de suivi pour l’Orchestration](../core/media/orchestrationsettingsapplicationinsight.PNG)

3. <span data-ttu-id="a9dd0-128">Sélectionnez **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-128">Select **OK** to save your changes.</span></span>
4. <span data-ttu-id="a9dd0-129">Redémarrez l’Instance d’hôte de suivi et confirmer le que démarrage de l’Application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-129">Restart the tracking host Instance, and confirm the BizTalk Application is started.</span></span>

<span data-ttu-id="a9dd0-130">Ensuite, exécutez les requêtes dans Application Insights pour afficher vos données.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-130">Next, run queries within Application Insights to see your data.</span></span>  

> [!TIP]
> <span data-ttu-id="a9dd0-131">Se connecter à votre Analytique du serveur BizTalk avec les autres systèmes pour avoir une idée davantage de données de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-131">Connect your BizTalk Server Analytics with other systems to gain even more insight into your organizations data.</span></span>

## <a name="view-your-data"></a><span data-ttu-id="a9dd0-132">Afficher vos données</span><span class="sxs-lookup"><span data-stu-id="a9dd0-132">View your data</span></span>
<span data-ttu-id="a9dd0-133">Une fois que les données sont envoyées à Application Insights, vous pouvez utiliser les outils d’analytique dans Azure pour créer des requêtes avancées et analyser vos données.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-133">Once the data is sent to Application Insights, you can use the analytics tools within Azure to create advanced queries, and analyze your data.</span></span>

1. <span data-ttu-id="a9dd0-134">Se connecter à la [portail Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="a9dd0-134">Sign in to the [Azure Portal](https://portal.azure.com).</span></span>
2. <span data-ttu-id="a9dd0-135">Ouvrez votre ressource Application Insights, puis sélectionnez **Metrics Explorer**.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-135">Open your Application Insights resource, and select **Metrics Explorer**.</span></span>
3. <span data-ttu-id="a9dd0-136">Peuvent afficher des graphiques vides.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-136">Empty charts may display.</span></span> <span data-ttu-id="a9dd0-137">Dans un graphique, sélectionnez **modifier**.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-137">In a chart, select **Edit**.</span></span> <span data-ttu-id="a9dd0-138">Sous **métriques**, sélectionnez **personnalisé** pour afficher les propriétés de suivi disponibles.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-138">Under **Metrics**, select **Custom** to see the available tracked properties.</span></span> <span data-ttu-id="a9dd0-139">Sélectionnez parmi les différentes options pour voir les modifications sur votre graphique :</span><span class="sxs-lookup"><span data-stu-id="a9dd0-139">Select some of the different options to see the changes on your chart:</span></span> 

    ![Analytique Azure](../core/media/azure-stream-metrics-custom.png)

4. <span data-ttu-id="a9dd0-141">Revenez à votre ressource Application Insights, puis sélectionnez **Analytique**.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-141">Go back to your Application Insights resource, and select **Analytics**.</span></span> <span data-ttu-id="a9dd0-142">Dans **utilisation**, sélectionnez **exécuter**.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-142">In **Usage**, select **Run**.</span></span> <span data-ttu-id="a9dd0-143">Un exemple de requête est exécutée, et les résultats sont affichés dans un graphique.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-143">A sample query is executed, and the results are displayed in a chart.</span></span>  

> [!TIP]
> <span data-ttu-id="a9dd0-144">Azure Application Insights est un outil puissant.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-144">Azure Application Insights is a powerful tool.</span></span> <span data-ttu-id="a9dd0-145">Il existe des ressources pour vous aider à écrire des requêtes dans Application Insights à [Analytique dans Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)et même de commencer à utiliser [Nouveautés d’Application Insights ?](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-overview).</span><span class="sxs-lookup"><span data-stu-id="a9dd0-145">There are resources to help you write queries in Application Insights at [Analytics in Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics), and even to get started at [What is Application Insights?](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-overview).</span></span>

## <a name="where-the-data-is-stored"></a><span data-ttu-id="a9dd0-146">Où les données sont stockées.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-146">Where the data is stored</span></span>

<span data-ttu-id="a9dd0-147">Vos données de suivi doivent s’afficher assez rapidement (dans quelques minutes) au sein de l’Application Insights.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-147">Your tracking data should display fairly quickly (within a few minutes) within Application Insights.</span></span> <span data-ttu-id="a9dd0-148">Si ce n’est pas le cas, il peut y être un problème avec l’hôte de suivi.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-148">If it doesn't, then there may be an issue with the tracking host.</span></span> <span data-ttu-id="a9dd0-149">Dans SQL Server, les données Analytique sont stockées dans la base de données BizTalkMsgBoxDb, dans le TrackingData_2_*x* tables.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-149">In SQL Server, the Analytics data is stored in the BizTalkMsgBoxDb database, in the TrackingData_2_*x* tables.</span></span> <span data-ttu-id="a9dd0-150">Dans SQL Server Management Studio, retourner les 1000 lignes du haut sur ces quatre tables.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-150">In SQL Server Management Studio, return the top 1000 rows on these four tables.</span></span> <span data-ttu-id="a9dd0-151">Si les données, l’hôte de suivi ne bouge pas les données de la base de données BizTalkDTADb.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-151">If the data is there, then the tracking host is not moving the data to the BizTalkDTADb database.</span></span> 

<span data-ttu-id="a9dd0-152">Certaines solutions possibles :</span><span class="sxs-lookup"><span data-stu-id="a9dd0-152">Some possible resolutions:</span></span>

1. <span data-ttu-id="a9dd0-153">Redémarrez l’hôte de suivi.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-153">Restart the tracking host.</span></span>
2. <span data-ttu-id="a9dd0-154">Créer un hôte de suivi dédié.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-154">Create a dedicated tracking host.</span></span> <span data-ttu-id="a9dd0-155">Lorsque BizTalk Server est installé, le suivi peut être activé sur le **1 d’Application de BizTalk Server** hôte.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-155">When BizTalk Server is installed, tracking may be enabled on the **BizTalk Server Application 1** host.</span></span> <span data-ttu-id="a9dd0-156">En règle générale, cette application est également utilisée pour traiter les messages.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-156">Typically, this application is also used to process messages.</span></span> <span data-ttu-id="a9dd0-157">Créer un hôte de suivi dédié en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="a9dd0-157">Create a dedicated tracking host using the following steps:</span></span> 

    1. <span data-ttu-id="a9dd0-158">Dans la console Administration de BizTalk Server, ouvrez les propriétés de l’hôte BizTalk Server Application 1 et désélectionnez **autoriser suivi de l’hôte**.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-158">In BizTalk Server Administration, open the properties of the BizTalk Server Application 1 host, and uncheck **Allow Host Tracking**.</span></span> <span data-ttu-id="a9dd0-159">Redémarrer cette instance d’hôte.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-159">Restart this host instance.</span></span>

    2. <span data-ttu-id="a9dd0-160">Créer un hôte nommé **suivi**et vérifiez **autoriser suivi de l’hôte**.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-160">Create a new host named **Tracking**, and check **Allow Host Tracking**.</span></span> <span data-ttu-id="a9dd0-161">Créer une instance d’hôte et le démarrer.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-161">Create a host instance, and start it.</span></span>

<span data-ttu-id="a9dd0-162">À présent, interroger les tables BizTalkMsgBoxDb TrackingData_2_x à nouveau.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-162">Now, query the BizTalkMsgBoxDb TrackingData_2_x tables again.</span></span> <span data-ttu-id="a9dd0-163">Si les tables sont vides, les données a été déplacées et il doivent commencer à afficher dans Application Insights.</span><span class="sxs-lookup"><span data-stu-id="a9dd0-163">If the tables are empty, then the data was moved, and should start displaying in Application Insights.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="a9dd0-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9dd0-164">See also</span></span>
 [<span data-ttu-id="a9dd0-165">Configurer le Pack de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="a9dd0-165">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)
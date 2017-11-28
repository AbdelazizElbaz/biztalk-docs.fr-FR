---
title: "Configurer le pack de fonctionnalités | Documents Microsoft"
description: "Installer et configurer le pack de fonctionnalités 1 du feature pack 2. Consultez la liste des fonctionnalités nouvelles, y compris la gestion des API, déploiement de services d’équipe, nouveaux adaptateurs Azure, les sauvegardes, etc. dans BizTalk Server 2016"
ms.custom: 
ms.date: 11/22/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1027bfa6-49b9-4f58-a2e2-3e0ae2fc3bf3
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5b4164cf1f1355ab9a0d2f350aa5b3b5ce411e0
ms.sourcegitcommit: f4c0d7bc4b617688c643101a34062db90014851a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2017
---
# <a name="configure-the-feature-pack"></a><span data-ttu-id="03869-104">Configurer le pack de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="03869-104">Configure the feature pack</span></span>

## <a name="overview"></a><span data-ttu-id="03869-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="03869-105">Overview</span></span>

[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="03869-106">utilise des packs de fonctionnalités pour fournir une intégration plus étroite avec Azure, fonctionnalités et améliorations.</span><span class="sxs-lookup"><span data-stu-id="03869-106"> uses feature packs to provide improvements, features, and closer integration with Azure.</span></span> <span data-ttu-id="03869-107">Ces packs de fonctionnalités étendent les fonctionnalités dans des domaines clés, telles que le déploiement, la sécurité, analytique, runtime et sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="03869-107">These feature packs extend functionality in key areas, such as deployment, security, analytics, runtime, and backup.</span></span> 

> [!NOTE]
> <span data-ttu-id="03869-108">Les packs de fonctionnalités sont disponibles dans les éditions Enterprise et Developer de [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] lorsque :</span><span class="sxs-lookup"><span data-stu-id="03869-108">The feature packs are available with the Enterprise and Developer editions of [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] when:</span></span> 
> 
> - <span data-ttu-id="03869-109">Utilisé avec Software Assurance (SA), ou</span><span class="sxs-lookup"><span data-stu-id="03869-109">Used with Software Assurance (SA), OR</span></span>
> - <span data-ttu-id="03869-110">En cours d’exécution [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] dans Azure à l’aide d’un contrat entreprise</span><span class="sxs-lookup"><span data-stu-id="03869-110">Running [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in Azure using an Enterprise Agreement</span></span>
> 
> <span data-ttu-id="03869-111">Les packs de fonctionnalités ne sont pas disponibles pour n’importe quel autre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] Édition ou tout autre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] version.</span><span class="sxs-lookup"><span data-stu-id="03869-111">The feature packs are not available for any other [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] edition, or any other [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] version.</span></span> 

## <a name="download-and-install"></a><span data-ttu-id="03869-112">Téléchargez et installez</span><span class="sxs-lookup"><span data-stu-id="03869-112">Download and install</span></span>

<span data-ttu-id="03869-113">Les packs de fonctionnalités sont cumulatifs.</span><span class="sxs-lookup"><span data-stu-id="03869-113">The feature packs are cumulative.</span></span> <span data-ttu-id="03869-114">Par conséquent, lorsque installer feature pack 2, vous obtenez également les fonctionnalités et les mises à jour dans le feature pack 1.</span><span class="sxs-lookup"><span data-stu-id="03869-114">So when you install feature pack 2, you also get the features and updates in feature pack 1.</span></span>

* <span data-ttu-id="03869-115">Téléchargez le [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 2](https://aka.ms/bts2016fp2).</span><span class="sxs-lookup"><span data-stu-id="03869-115">Download the [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 2](https://aka.ms/bts2016fp2).</span></span>

* <span data-ttu-id="03869-116">Téléchargez le [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100).</span><span class="sxs-lookup"><span data-stu-id="03869-116">Download the [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100).</span></span>

#### <a name="install"></a><span data-ttu-id="03869-117">Install</span><span class="sxs-lookup"><span data-stu-id="03869-117">Install</span></span>

1. <span data-ttu-id="03869-118">Exécutez le programme d’installation en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="03869-118">Run setup as administrator.</span></span>
2. <span data-ttu-id="03869-119">Dans **Bienvenue**, sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="03869-119">In **Welcome**, select **Next**.</span></span> 
3. <span data-ttu-id="03869-120">Acceptez le contrat de licence et sélectionnez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="03869-120">Accept the license agreement, and select **Next**.</span></span> 
4. <span data-ttu-id="03869-121">Poursuivez l’installation.</span><span class="sxs-lookup"><span data-stu-id="03869-121">Continue with the installation.</span></span> <span data-ttu-id="03869-122">Pendant l’installation, plusieurs fenêtres de commande peuvent ouvrir et fermer.</span><span class="sxs-lookup"><span data-stu-id="03869-122">During the install, several command windows may open and close.</span></span> <span data-ttu-id="03869-123">Lorsque vous avez terminé, vous êtes invité à **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="03869-123">When complete, you are prompted to **Finish**.</span></span>

<span data-ttu-id="03869-124">Un journal d’installation est créé dans `C:\ProgramData\Microsoft\E-Business Servers Updates\Updates\Uninstall4014788-FP2\setup.log`.</span><span class="sxs-lookup"><span data-stu-id="03869-124">A setup log is created in `C:\ProgramData\Microsoft\E-Business Servers Updates\Updates\Uninstall4014788-FP2\setup.log`.</span></span>

>[!TIP]
> <span data-ttu-id="03869-125">Pour obtenir des instructions complètes sur l’installation, consultez le [installation pas à pas de Feature Pack](https://blog.sandro-pereira.com/2017/04/27/microsoft-biztalk-server-2016-feature-pack-1-step-by-step-installation/) billet de blog.</span><span class="sxs-lookup"><span data-stu-id="03869-125">For comprehensive guidance on the installation, see the [Feature Pack step-by-step installation](https://blog.sandro-pereira.com/2017/04/27/microsoft-biztalk-server-2016-feature-pack-1-step-by-step-installation/) blog post.</span></span>

## <a name="feature-pack-2-updates"></a><span data-ttu-id="03869-126">Fonctionnalité des mises à jour du Pack 2</span><span class="sxs-lookup"><span data-stu-id="03869-126">Feature Pack 2 updates</span></span>

#### <a name="expose-soap-endpoints-with-api-managementcoreconnect-to-azure-api-managementmd"></a>[<span data-ttu-id="03869-127">Exposer des points de terminaison SOAP avec la gestion des API</span><span class="sxs-lookup"><span data-stu-id="03869-127">Expose SOAP endpoints with API Management</span></span>](../core/connect-to-azure-api-management.md)

<span data-ttu-id="03869-128">En développant sur l’intégration de gestion des API avec Feature Pack 1, vous pouvez exposer un WCF-BasicHTTP réception en tant que point de terminaison SOAP à l’aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="03869-128">Expanding on the API management integration made with Feature Pack 1, you can now expose a WCF-BasicHTTP receive location as a SOAP endpoint using the BizTalk Server Administration console.</span></span> 

#### <a name="use-the-event-hub-adapterevent-hubs-adaptermd"></a>[<span data-ttu-id="03869-129">Utilisation de l’adaptateur de concentrateur d’événements</span><span class="sxs-lookup"><span data-stu-id="03869-129">Use the Event Hub adapter</span></span>](event-hubs-adapter.md)

<span data-ttu-id="03869-130">Envoyer des messages à partir de BizTalk à Azure Event Hubs et recevoir des messages à partir d’Azure Event Hubs à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="03869-130">Send messages from BizTalk to Azure Event Hubs, and receive messages from Azure Event Hubs to BizTalk Server.</span></span> <span data-ttu-id="03869-131">Lorsque vous configurez les propriétés de transport, vous pouvez facilement vous connecter à votre compte Azure et sélectionnent automatiquement votre espace de noms Azure Event Hubs et le concentrateur d’événements.</span><span class="sxs-lookup"><span data-stu-id="03869-131">When you configure the transport properties, you can easily sign in to your Azure account, and automatically select your Azure Event Hubs namespace, and Event Hub.</span></span>

#### <a name="backup-to-azure-blob-accountcorehow-to-configure-the-backup-biztalk-server-jobmd"></a>[<span data-ttu-id="03869-132">Sauvegarde sur le compte d’objets blob Azure</span><span class="sxs-lookup"><span data-stu-id="03869-132">Backup to Azure blob account</span></span>](../core/how-to-configure-the-backup-biztalk-server-job.md)
<span data-ttu-id="03869-133">Le travail de sauvegarde de BizTalk Server sauvegarde les fichiers journaux et les bases de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="03869-133">The Backup BizTalk Server job backs up the BizTalk databases and log files.</span></span> <span data-ttu-id="03869-134">Lorsque vous configurez ce travail de l’Agent SQL, vous pouvez entrer un compte de stockage d’objets blob Azure dans les propriétés du travail.</span><span class="sxs-lookup"><span data-stu-id="03869-134">When you configure this SQL Agent job, you can enter an Azure blob storage account within the job properties.</span></span> <span data-ttu-id="03869-135">Cela vous donne une autre option pour sauvegarder vos données, au lieu d’utiliser un disque physique local.</span><span class="sxs-lookup"><span data-stu-id="03869-135">This gives you another option to backup your data, instead of using a local physical disk.</span></span> 

#### <a name="multi-machine-deployment-using-vstscoreconfigure-automatic-deployment-with-visual-studio-team-services-in-biztalkmd"></a>[<span data-ttu-id="03869-136">Déploiement de plusieurs ordinateur à l’aide de VSTS</span><span class="sxs-lookup"><span data-stu-id="03869-136">Multi-machine deployment using VSTS</span></span>](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)
<span data-ttu-id="03869-137">À l’aide de groupes de déploiement, vous pouvez déployer vos applications à plusieurs serveurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="03869-137">Using deployment groups, you can deploy your applications to multiple BizTalk Servers.</span></span> <span data-ttu-id="03869-138">Vous pouvez également définir le nom de l’application dans le projet d’application et installer votre application en entrant votre serveur d’administration.</span><span class="sxs-lookup"><span data-stu-id="03869-138">You can also set the application name within the application project, and install your application by entering your management server.</span></span>

<span data-ttu-id="03869-139">[Groupes de déploiement](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index) fournit plus de détails sur la façon de procéder dans VSTS.</span><span class="sxs-lookup"><span data-stu-id="03869-139">[Deployment groups](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index) provides more details on how this is done in VSTS.</span></span>  

#### <a name="use-service-bus-premiumcoresb-messaging-adaptermd"></a>[<span data-ttu-id="03869-140">Utiliser Service Bus Premium</span><span class="sxs-lookup"><span data-stu-id="03869-140">Use Service Bus Premium</span></span>](../core/sb-messaging-adapter.md)

<span data-ttu-id="03869-141">L’adaptateur de Bus de Service prend en charge le Service Bus Premium, y compris l’envoi de messages vers des rubriques et files d’attente partitionnées.</span><span class="sxs-lookup"><span data-stu-id="03869-141">The Service Bus adapter supports Service Bus Premium, including sending messages to partitioned queues and topics.</span></span> <span data-ttu-id="03869-142">[Service Bus Premium et les niveaux de messagerie Standard](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-premium-messaging) détails plus sur Service Bus Premium.</span><span class="sxs-lookup"><span data-stu-id="03869-142">[Service Bus Premium and Standard messaging tiers](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-premium-messaging) details more about Service Bus Premium.</span></span> 

#### <a name="use-named-instances-with-application-insightscoresend-tracking-data-to-azure-application-insights-using-biztalk-servermd"></a>[<span data-ttu-id="03869-143">Utiliser les instances nommées avec Application Insights</span><span class="sxs-lookup"><span data-stu-id="03869-143">Use named instances with Application Insights</span></span>](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)
<span data-ttu-id="03869-144">Lorsque vous activez l’Analytique et que vous entrez la clé d’Application Insights, vous obtiendrez l’erreur :</span><span class="sxs-lookup"><span data-stu-id="03869-144">When you enable Analytics, and enter the Application Insights key, you may get error:</span></span> 

```
Group settings were not applied. (A database failure occurred due to database connectivity problems.)
```

<span data-ttu-id="03869-145">Cela se produit lorsque vous utilisez des instances nommée de SQL.</span><span class="sxs-lookup"><span data-stu-id="03869-145">This happens when you use SQL named instances.</span></span> <span data-ttu-id="03869-146">Il est résolu dans ce feature pack ; Vous pouvez utiliser des instances par défaut SQL, et les instances nommées de SQL.</span><span class="sxs-lookup"><span data-stu-id="03869-146">This is fixed in this feature pack; you can use SQL default instances, and SQL named instances.</span></span> 

#### <a name="tls-12-support"></a><span data-ttu-id="03869-147">Prise en charge de TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="03869-147">TLS 1.2 support</span></span>

<span data-ttu-id="03869-148">TLS 1.2 est entièrement pris en charge dans BizTalk Server, y compris toutes les cartes et tous les accélérateurs.</span><span class="sxs-lookup"><span data-stu-id="03869-148">TLS 1.2 is fully supported in BizTalk Server, including all the adapters and all the accelerators.</span></span> <span data-ttu-id="03869-149">Vous pouvez désactiver SSL, TLS 1.0 et 1.1 du protocole TLS sur le serveur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="03869-149">You can disable SSL, TLS 1.0, and TLS 1.1 on the BizTalk Server.</span></span> 

<span data-ttu-id="03869-150">Informations de clé :</span><span class="sxs-lookup"><span data-stu-id="03869-150">Key information:</span></span> 

* <span data-ttu-id="03869-151">Les systèmes externes communique également avec BizTalk doivent prendre en charge de TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="03869-151">Any external systems communicating with BizTalk also need to support TLS 1.2</span></span>
* <span data-ttu-id="03869-152">N’importe quel code personnalisé, tels que des fonctoids, peut-être être mise à jour pour prendre en charge TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="03869-152">Any custom code, such as functoids, may need to be updated to support TLS 1.2</span></span>

<span data-ttu-id="03869-153">[Description du protocole TLS/SSL](https://support.microsoft.com/kb/3155464) explique comment configurer un environnement TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="03869-153">[Description of the TLS/SSL protocol](https://support.microsoft.com/kb/3155464) describes how to setup a TLS 1.2 environment.</span></span> 

#### <a name="use-latest-newtonsoft-json"></a><span data-ttu-id="03869-154">Utiliser la dernière JSON Newtonsoft</span><span class="sxs-lookup"><span data-stu-id="03869-154">Use latest Newtonsoft JSON</span></span> 
<span data-ttu-id="03869-155">Newtonsoft est une infrastructure JSON pour .NET.</span><span class="sxs-lookup"><span data-stu-id="03869-155">Newtonsoft is a JSON framework for .NET.</span></span> <span data-ttu-id="03869-156">Dans ce feature pack, la prise en charge pour la version 10.0.3 est inclus.</span><span class="sxs-lookup"><span data-stu-id="03869-156">In this feature pack, support for version 10.0.3 is included.</span></span> <span data-ttu-id="03869-157">[Téléchargement v. 10.0.3](https://www.nuget.org/packages/Newtonsoft.Json/10.0.3) directement à partir de NuGet.</span><span class="sxs-lookup"><span data-stu-id="03869-157">[Download v. 10.0.3](https://www.nuget.org/packages/Newtonsoft.Json/10.0.3) directly from NuGet.</span></span> 


## <a name="feature-pack-1-updates"></a><span data-ttu-id="03869-158">Fonctionnalité des mises à jour du Pack 1</span><span class="sxs-lookup"><span data-stu-id="03869-158">Feature Pack 1 updates</span></span>

#### <a name="send-tracking-data-to-application-insightscoresend-tracking-data-to-azure-application-insights-using-biztalk-servermd"></a>[<span data-ttu-id="03869-159">Envoyer des données de suivi à Application Insights</span><span class="sxs-lookup"><span data-stu-id="03869-159">Send tracking data to Application Insights</span></span>](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)

<span data-ttu-id="03869-160">Envoyer des données de suivi à Azure Application Insights pour utiliser ses fonctionnalités, telles qu’analytique, apprentissage, diagnostics et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="03869-160">Send tracking data to Azure Application Insights to use its features, such as analytics, machine learning, diagnostics, and more.</span></span> 

#### <a name="configure-the-operational-data-feed-using-power-bicoreconfigure-the-operational-data-feed-for-power-bi-with-biztalk-servermd"></a>[<span data-ttu-id="03869-161">Configurer les données opérationnelles de flux à l’aide de Power BI</span><span class="sxs-lookup"><span data-stu-id="03869-161">Configure the operational data feed using Power BI</span></span>](../core/configure-the-operational-data-feed-for-power-bi-with-biztalk-server.md)

<span data-ttu-id="03869-162">Envoyer des données de suivi à Power BI à l’aide d’oData.</span><span class="sxs-lookup"><span data-stu-id="03869-162">Send tracking data to Power BI using oData.</span></span> <span data-ttu-id="03869-163">Par exemple, obtenir une représentation visuelle de vos données de suivi à partir de vos orchestrations et les ports.</span><span class="sxs-lookup"><span data-stu-id="03869-163">For example, get a visual representation of your tracking data from your ports and orchestrations.</span></span> 

#### <a name="connect-to-the-management-rest-apis-in-biztalkcoreinstall-and-configure-the-management-rest-apis-in-biztalk-servermd"></a>[<span data-ttu-id="03869-164">Se connecter à l’API REST dans BizTalk management</span><span class="sxs-lookup"><span data-stu-id="03869-164">Connect to the management REST APIs in BizTalk</span></span>](../core/install-and-configure-the-management-rest-apis-in-biztalk-server.md)

<span data-ttu-id="03869-165">Utiliser l’API REST pour gérer à distance vos artefacts BizTalk, y compris les accords, les instances suspendues, orchestrations désinscrits et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="03869-165">Use REST APIs to remotely manage your BizTalk artifacts, including agreements, suspended instances, unenlisted orchestrations, and more.</span></span>

#### <a name="configure-advanced-schedulingcoreconfigure-the-time-zone-and-recurrence-scheduling-in-biztalk-servermd"></a>[<span data-ttu-id="03869-166">Configurer la planification avancée</span><span class="sxs-lookup"><span data-stu-id="03869-166">Configure advanced scheduling</span></span>](../core/configure-the-time-zone-and-recurrence-scheduling-in-biztalk-server.md)

<span data-ttu-id="03869-167">Activer avancé de planification dans vos emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="03869-167">Enable advanced scheduling in your receive locations.</span></span> <span data-ttu-id="03869-168">Par exemple, définir le fuseau horaire, ou définir une fenêtre de service de récurrence d’un jour spécifique sur un mois spécifique.</span><span class="sxs-lookup"><span data-stu-id="03869-168">For example, set the timezone, or set a recurrence service window for a specific day on a specific month.</span></span>

#### <a name="configure-automatic-deployments-with-vstscoreconfigure-automatic-deployment-with-visual-studio-team-services-in-biztalkmd"></a>[<span data-ttu-id="03869-169">Configurer des déploiements automatiques avec VSTS</span><span class="sxs-lookup"><span data-stu-id="03869-169">Configure automatic deployments with VSTS</span></span>](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)  

<span data-ttu-id="03869-170">Visual Studio Team Services (VSTS) permet de déployer automatiquement vos solutions, ou mettre à jour des applications existantes.</span><span class="sxs-lookup"><span data-stu-id="03869-170">Use Visual Studio Team Services (VSTS) to automatically deploy your solutions, or update existing applications.</span></span> <span data-ttu-id="03869-171">VSTS communique avec un agent installé sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03869-171">VSTS communicates with an agent installed on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>

#### <a name="connect-to-sql-server-always-encrypted-columns-with-biztalk-servercoreconnect-to-sql-server-always-encrypted-columns-with-biztalk-servermd"></a>[<span data-ttu-id="03869-172">Se connecter à SQL Server Always Encrypted des colonnes avec BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="03869-172">Connect to SQL Server Always Encrypted columns with BizTalk Server</span></span>](../core/connect-to-sql-server-always-encrypted-columns-with-biztalk-server.md)  

<span data-ttu-id="03869-173">Utiliser l’adaptateur WCF-SQL pour interroger des colonnes chiffrées à partir d’une base de données Always Encrypted dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="03869-173">Use the WCF-SQL adapter to query encrypted columns from an Always Encrypted database in SQL Server.</span></span>

#### <a name="integrate-with-api-managementcoreconnect-to-azure-api-managementmd"></a>[<span data-ttu-id="03869-174">Intégrer la gestion des API</span><span class="sxs-lookup"><span data-stu-id="03869-174">Integrate with API Management</span></span>](../core/connect-to-azure-api-management.md)

<span data-ttu-id="03869-175">Au sein de votre service de gestion des API Azure, vous pouvez créer et exposent une API en tant que WSDL et utiliser l’URI vers un point de terminaison SOAP BizTalk.</span><span class="sxs-lookup"><span data-stu-id="03869-175">Within your Azure API management service, you can create and expose an API as WSDL, and use the URI to a BizTalk SOAP endpoint.</span></span>  
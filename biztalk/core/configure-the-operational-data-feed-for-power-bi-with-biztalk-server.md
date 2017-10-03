---
title: "Configurer les données opérationnelles de flux pour Power BI avec BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe6d3a97-c7c0-4147-baa9-ee12f93248eb
caps.latest.revision: "11"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 09b1b1fd7f350e168b2bb13d6bee2e45c12d49cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-operational-data-feed-for-power-bi-with-biztalk-server"></a><span data-ttu-id="4e0fb-102">Configurer les données opérationnelles de flux pour Power BI avec BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4e0fb-102">Configure the operational data feed for Power BI with BizTalk Server</span></span>
<span data-ttu-id="4e0fb-103">Lire des données opérationnelles fournies via un flux oData dans [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e0fb-103">Read operational data provided through an oData feed in [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> 

<span data-ttu-id="4e0fb-104">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , suivi d’envoi à l’aide du modèle de Power BI fourni de Power BI ou créer vos propres.</span><span class="sxs-lookup"><span data-stu-id="4e0fb-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, send tracking to Power BI using the Power BI template provided, or create your own.</span></span> 

## <a name="what-is-operational-data"></a><span data-ttu-id="4e0fb-105">Nouveautés des données opérationnelles</span><span class="sxs-lookup"><span data-stu-id="4e0fb-105">What is operational data</span></span>
<span data-ttu-id="4e0fb-106">Données opérationnelles sont plus d’informations sur les instances et les messages transitant via votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnement.</span><span class="sxs-lookup"><span data-stu-id="4e0fb-106">Operational data is information on the instances and messages flowing through your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="4e0fb-107">Le flux de données opérationnelles est les mêmes données que vous obtenez examinant Hub du groupe dans le [!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)] console.</span><span class="sxs-lookup"><span data-stu-id="4e0fb-107">The operational data feed is the same data you get looking at Group Hub in the [!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)] console.</span></span> <span data-ttu-id="4e0fb-108">Les données sont accessibles et interrogés à l’aide des outils de visualisation, y compris Power BI.</span><span class="sxs-lookup"><span data-stu-id="4e0fb-108">The data can be accessed and queried using visualization tools, including Power BI.</span></span> 

<span data-ttu-id="4e0fb-109">Le flux inclut les tables de données suivantes :</span><span class="sxs-lookup"><span data-stu-id="4e0fb-109">The feed includes the following data tables:</span></span>
* <span data-ttu-id="4e0fb-110">Données d’application</span><span class="sxs-lookup"><span data-stu-id="4e0fb-110">Application data</span></span>
* <span data-ttu-id="4e0fb-111">AS2 Enregistrements d’état</span><span class="sxs-lookup"><span data-stu-id="4e0fb-111">AS2 Status Records</span></span>
* <span data-ttu-id="4e0fb-112">Informations de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="4e0fb-112">Batching information</span></span>
* <span data-ttu-id="4e0fb-113">Informations sur l’instance</span><span class="sxs-lookup"><span data-stu-id="4e0fb-113">Instance information</span></span>
* <span data-ttu-id="4e0fb-114">Échange des enregistrements d’agrégations</span><span class="sxs-lookup"><span data-stu-id="4e0fb-114">Interchange Aggregations Records</span></span>
* <span data-ttu-id="4e0fb-115">Enregistrements d’état de l’échange</span><span class="sxs-lookup"><span data-stu-id="4e0fb-115">Interchange Status Records</span></span>
* <span data-ttu-id="4e0fb-116">Messages</span><span class="sxs-lookup"><span data-stu-id="4e0fb-116">Messages</span></span>
* <span data-ttu-id="4e0fb-117">Abonnements</span><span class="sxs-lookup"><span data-stu-id="4e0fb-117">Subscriptions</span></span>
* <span data-ttu-id="4e0fb-118">Événements suivis</span><span class="sxs-lookup"><span data-stu-id="4e0fb-118">Tracked Events</span></span>
* <span data-ttu-id="4e0fb-119">Rapports de transaction</span><span class="sxs-lookup"><span data-stu-id="4e0fb-119">Transaction reports</span></span>
* <span data-ttu-id="4e0fb-120">Documents informatisés</span><span class="sxs-lookup"><span data-stu-id="4e0fb-120">Transaction sets</span></span>

> [!TIP]
> <span data-ttu-id="4e0fb-121">[PowerBI.com](http://powerbi.microsoft.com) est un bon point de départ pour comprendre et en savoir plus sur Power BI.</span><span class="sxs-lookup"><span data-stu-id="4e0fb-121">[PowerBI.com](http://powerbi.microsoft.com) is a great resource to understand and learn more about Power BI.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4e0fb-122">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4e0fb-122">Prerequisites</span></span>
* <span data-ttu-id="4e0fb-123">Téléchargez et installez [Power BI Desktop](https://powerbi.microsoft.com/desktop/) sur n’importe quel ordinateur qui dispose d’un accès réseau pour votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e0fb-123">Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) on any computer that has network access to your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* <span data-ttu-id="4e0fb-124">Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e0fb-124">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* <span data-ttu-id="4e0fb-125">Installer IIS sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e0fb-125">Install IIS on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="4e0fb-126">Dans la plupart des [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnements, IIS est déjà installé.</span><span class="sxs-lookup"><span data-stu-id="4e0fb-126">In most [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments, IIS is already installed.</span></span> <span data-ttu-id="4e0fb-127">Consultez [matérielle et logicielle requise pour BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span><span class="sxs-lookup"><span data-stu-id="4e0fb-127">See [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span></span> 

## <a name="enable-operational-data-feed"></a><span data-ttu-id="4e0fb-128">Activer le flux de données opérationnelles</span><span class="sxs-lookup"><span data-stu-id="4e0fb-128">Enable operational data feed</span></span>

1. <span data-ttu-id="4e0fb-129">Exécutez Windows PowerShell en tant qu’administrateur (**Démarrer** menu, tapez **PowerShell**avec le bouton droit et cliquez sur Sélectionner **exécuter en tant qu’administrateur**).</span><span class="sxs-lookup"><span data-stu-id="4e0fb-129">Run Windows PowerShell as Administrator (**Start** menu, type **PowerShell**, right click, and select **Run as administrator**).</span></span> 
2. <span data-ttu-id="4e0fb-130">Accédez au dossier où [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] est installé **Program Files (x86)/Microsoft BizTalk Server 2016**</span><span class="sxs-lookup"><span data-stu-id="4e0fb-130">Browse to the folder where [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] is installed **Program Files (x86)/Microsoft BizTalk Server 2016**</span></span>
3. <span data-ttu-id="4e0fb-131">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4e0fb-131">Run the following command.</span></span> <span data-ttu-id="4e0fb-132">Veillez à mettre à jour votre `website`, `domain\user`, `password`, et `domain\group` avec vos valeurs :</span><span class="sxs-lookup"><span data-stu-id="4e0fb-132">Be sure to update your `website`, `domain\user`, `password`, and `domain\group` with your values:</span></span> 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service operationaldata -WebSiteName '<Default Web Site>' -ApplicationPool <operationalDataServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group1>, <domain>\<group2>'
    ```
4. <span data-ttu-id="4e0fb-133">Après avoir exécuté le script, accédez à la nouvelle Application IIS :</span><span class="sxs-lookup"><span data-stu-id="4e0fb-133">After you run the script, browse the new IIS Application:</span></span>  
    1. <span data-ttu-id="4e0fb-134">Ouvrez votre navigateur web</span><span class="sxs-lookup"><span data-stu-id="4e0fb-134">Open your web browser</span></span>
    2. <span data-ttu-id="4e0fb-135">Accédez à **http://localhost/BizTalkOperationalDataService**</span><span class="sxs-lookup"><span data-stu-id="4e0fb-135">Go to **http://localhost/BizTalkOperationalDataService**</span></span>

## <a name="use-the-power-bi-template"></a><span data-ttu-id="4e0fb-136">Utilisez le modèle de Power BI</span><span class="sxs-lookup"><span data-stu-id="4e0fb-136">Use the Power BI template</span></span>
<span data-ttu-id="4e0fb-137">Pour accéder au fichier de modèle Power BI et utiliser la visualisation fournie par Microsoft, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4e0fb-137">To access the Power BI Template file, and use the provided visualization from Microsoft, use the following steps:</span></span>

1. <span data-ttu-id="4e0fb-138">Téléchargez et installez le [Power BI Desktop](https://powerbi.microsoft.com/desktop/).</span><span class="sxs-lookup"><span data-stu-id="4e0fb-138">Download and install the [Power BI Desktop](https://powerbi.microsoft.com/desktop/).</span></span>
2. <span data-ttu-id="4e0fb-139">Accédez à votre dossier de BizTalk Server sous **Program Files (x86) \Microsoft BizTalk Server 2016\OperationalDataService**.</span><span class="sxs-lookup"><span data-stu-id="4e0fb-139">Browse to your BizTalk Server folder under **Program Files (x86)\Microsoft BizTalk Server 2016\OperationalDataService**.</span></span>
3. <span data-ttu-id="4e0fb-140">Ouvrez le **BizTalkOperationalData.pbit** fichier.</span><span class="sxs-lookup"><span data-stu-id="4e0fb-140">Open the **BizTalkOperationalData.pbit** file.</span></span>
4. <span data-ttu-id="4e0fb-141">Lorsque vous êtes invité à partir de Power BI, collez la **http://localhost/\<votresiteweb\>**  URL que vous avez créé pour votre flux OData.</span><span class="sxs-lookup"><span data-stu-id="4e0fb-141">When prompted from Power BI, paste the **http://localhost/\<yourWebSite\>** URL that you created for your OData feed.</span></span> <span data-ttu-id="4e0fb-142">Par exemple, entrez **http://localhost/OperationalDataService**.</span><span class="sxs-lookup"><span data-stu-id="4e0fb-142">For example, enter **http://localhost/OperationalDataService**.</span></span> 

    <span data-ttu-id="4e0fb-143">Votre URL est similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4e0fb-143">Your URL looks similar to the following:</span></span> 
    
    ![Collez l’URL OData pour le fichier de modèle Power BI](../core/media/pasteurltopowerbitempaltefile.PNG)

5. <span data-ttu-id="4e0fb-145">Sélectionnez **charge** pour remplir les champs dans votre rapport Power BI.</span><span class="sxs-lookup"><span data-stu-id="4e0fb-145">Select **Load** to populate the fields in your Power BI report.</span></span> 
6. <span data-ttu-id="4e0fb-146">Le fichier de modèle génère automatiquement les informations et les tables disponibles à partir du flux OData.</span><span class="sxs-lookup"><span data-stu-id="4e0fb-146">The Template file automatically generates the information and tables available from the OData feed.</span></span>

<span data-ttu-id="4e0fb-147">Les données opérationnelles sont exposées via l’ordinateur et peuvent être accessible et exécutées par d’autres applications en fonction des autorisations.</span><span class="sxs-lookup"><span data-stu-id="4e0fb-147">The operational data is exposed through the computer, and can be accessed and executed by other applications based on permissions.</span></span> 

<span data-ttu-id="4e0fb-148">Pour en savoir plus sur Power BI et comment publier le rapport en ligne atteindre [PowerBI.com](http://powerbi.microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="4e0fb-148">To learn more about Power BI, and how to publish the report online go to [PowerBI.com](http://powerbi.microsoft.com)</span></span>

## <a name="see-also"></a><span data-ttu-id="4e0fb-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e0fb-149">See also</span></span>

[<span data-ttu-id="4e0fb-150">En savoir plus sur Power BI</span><span class="sxs-lookup"><span data-stu-id="4e0fb-150">Learn more about Power BI</span></span>](https://www.powerbi.com)  
[<span data-ttu-id="4e0fb-151">Configurer le Pack de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="4e0fb-151">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)
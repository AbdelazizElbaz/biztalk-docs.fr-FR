---
title: Installer et configurer la gestion des API REST | Documents Microsoft
description: "Interroger l’état des artefacts dans votre environnement BizTalk à l’aide des données de gestion des API REST avec Feature Pack 1 dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39442756-5886-4ddd-b700-3800a237de4a
caps.latest.revision: "8"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 009b3b0bb333b8f92f6235da57b0c3e9f5daca96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-and-configure-the-management-rest-apis-in-biztalk-server"></a><span data-ttu-id="41109-103">Installer et configurer l’API REST de gestion dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="41109-103">Install and configure the management REST APIs in BizTalk Server</span></span>
<span data-ttu-id="41109-104">Utiliser un script Windows PowerShell pour activer l’API REST gérer à distance votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41109-104">Use a Windows PowerShell script to enable REST APIs that remotely manage your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>

## <a name="what-are-management-data-apis"></a><span data-ttu-id="41109-105">Quelles sont les données de gestion des API</span><span class="sxs-lookup"><span data-stu-id="41109-105">What are Management data APIs</span></span>
<span data-ttu-id="41109-106">API de données de gestion est les points de terminaison qui vous permettent de mettre à jour à distance, ajouter et interroger l’état des différents artefacts dans votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnement.</span><span class="sxs-lookup"><span data-stu-id="41109-106">Management data APIs are the endpoints that let you remotely update, add, and query the status of different artifacts in your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="41109-107">Les points de terminaison sont ajoutés à l’aide de REST et être accompagnée d’une définition Swagger.</span><span class="sxs-lookup"><span data-stu-id="41109-107">The endpoints are added using REST, and come with a Swagger definition.</span></span> 

<span data-ttu-id="41109-108">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , il existe un script Windows PowerShell qui installe ces API REST et leurs définitions swagger.</span><span class="sxs-lookup"><span data-stu-id="41109-108">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, there's a Windows PowerShell script that installs these REST APIs, and their swagger definitions.</span></span> <span data-ttu-id="41109-109">Ces API effectuer des appels REST pour gérer à distance des ports, orchestrations, partenaires, accords, pipelines et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="41109-109">These APIs make REST calls to remotely manage ports, orchestrations, partners, agreements, pipelines, and more.</span></span> 

<span data-ttu-id="41109-110">Cette rubrique vous montre comment installer les API REST.</span><span class="sxs-lookup"><span data-stu-id="41109-110">This topic shows you how to install the REST APIs.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="41109-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="41109-111">Prerequisites</span></span>
* <span data-ttu-id="41109-112">Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41109-112">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>

* <span data-ttu-id="41109-113">Installer IIS sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41109-113">Install IIS on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="41109-114">Dans la plupart des [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnements, IIS est déjà installé.</span><span class="sxs-lookup"><span data-stu-id="41109-114">In most [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments, IIS is already installed.</span></span> <span data-ttu-id="41109-115">Consultez [matérielle et logicielle requise pour BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span><span class="sxs-lookup"><span data-stu-id="41109-115">See [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span></span>

## <a name="enable-the-rest-apis"></a><span data-ttu-id="41109-116">Activer l’API REST</span><span class="sxs-lookup"><span data-stu-id="41109-116">Enable the REST APIs</span></span>

1. <span data-ttu-id="41109-117">Exécutez Windows PowerShell en tant qu’administrateur (**Démarrer** menu, tapez **PowerShell**avec le bouton droit et cliquez sur Sélectionner **exécuter en tant qu’administrateur**).</span><span class="sxs-lookup"><span data-stu-id="41109-117">Run Windows PowerShell as Administrator (**Start** menu, type **PowerShell**, right click, and select **Run as administrator**).</span></span> 
2. <span data-ttu-id="41109-118">Accédez au dossier BizTalk sous **Program Files (x86)/Microsoft BizTalk Server 2016**</span><span class="sxs-lookup"><span data-stu-id="41109-118">Browse to the BizTalk folder under **Program Files (x86)/Microsoft BizTalk Server 2016**</span></span>
3. <span data-ttu-id="41109-119">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="41109-119">Run the following command.</span></span> <span data-ttu-id="41109-120">Veillez à mettre à jour votre `website`, `domain/user`, `password`, et `domain\group` avec vos valeurs :</span><span class="sxs-lookup"><span data-stu-id="41109-120">Be sure to update your `website`, `domain/user`, `password`, and `domain\group` with your values:</span></span> 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName '<Default Web Site>' -ApplicationPool <mgmtServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group>, <domain>\<group>'
    ```
4. <span data-ttu-id="41109-121">Après avoir exécuté le script, accédez à la nouvelle application IIS :</span><span class="sxs-lookup"><span data-stu-id="41109-121">After you run the script, browse the new IIS application:</span></span>  
    1. <span data-ttu-id="41109-122">Ouvrez votre navigateur web</span><span class="sxs-lookup"><span data-stu-id="41109-122">Open your web browser</span></span>
    2. <span data-ttu-id="41109-123">Accédez à **http://localhost/OperationalDataService/swagger**</span><span class="sxs-lookup"><span data-stu-id="41109-123">Browse to **http://localhost/OperationalDataService/swagger**</span></span>

5. <span data-ttu-id="41109-124">Les charges de définitions Swagger.</span><span class="sxs-lookup"><span data-stu-id="41109-124">The Swagger definitions loads.</span></span> <span data-ttu-id="41109-125">Vous pouvez également modifier qui a accès en mettant à jour le **web.config** fichier dans le dossier racine de l’Application de gestion.</span><span class="sxs-lookup"><span data-stu-id="41109-125">You can also change who has access by updating the **web.config** file in the root folder of the Management Application.</span></span>

<span data-ttu-id="41109-126">Les API REST sont exposées via un ordinateur et peut être accessible et exécutés par d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="41109-126">The REST APIs are exposed through the machine, and can be accessed and executed by other applications.</span></span> 


## <a name="see-also"></a><span data-ttu-id="41109-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41109-127">See also</span></span>
 [<span data-ttu-id="41109-128">Configurer le Pack de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="41109-128">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)
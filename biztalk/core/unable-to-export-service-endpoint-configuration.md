---
title: "Impossible d’exporter la configuration de point de terminaison de service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 795145fa-0ce4-498f-a82e-eb752a5f4764
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3b36fa47d9302f3f88f65575bfa8f74c6469e9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-export-service-endpoint-configuration"></a><span data-ttu-id="bf550-102">Impossible d'exporter la configuration du point de terminaison du service</span><span class="sxs-lookup"><span data-stu-id="bf550-102">Unable to export service endpoint configuration</span></span>
## <a name="details"></a><span data-ttu-id="bf550-103">Détails</span><span class="sxs-lookup"><span data-stu-id="bf550-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bf550-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="bf550-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="bf550-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="bf550-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="bf550-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="bf550-106">Event ID</span></span>|<span data-ttu-id="bf550-107">0</span><span class="sxs-lookup"><span data-stu-id="bf550-107">0</span></span>|  
|<span data-ttu-id="bf550-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="bf550-108">Event Source</span></span>|<span data-ttu-id="bf550-109">0</span><span class="sxs-lookup"><span data-stu-id="bf550-109">0</span></span>|  
|<span data-ttu-id="bf550-110">Composant</span><span class="sxs-lookup"><span data-stu-id="bf550-110">Component</span></span>|<span data-ttu-id="bf550-111">0</span><span class="sxs-lookup"><span data-stu-id="bf550-111">0</span></span>|  
|<span data-ttu-id="bf550-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="bf550-112">Symbolic Name</span></span>|<span data-ttu-id="bf550-113">0</span><span class="sxs-lookup"><span data-stu-id="bf550-113">0</span></span>|  
|<span data-ttu-id="bf550-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="bf550-114">Message Text</span></span>|<span data-ttu-id="bf550-115">Impossible d'exporter la configuration du point de terminaison du service vers « {0} »</span><span class="sxs-lookup"><span data-stu-id="bf550-115">Unable to export service endpoint configuration to "{0}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bf550-116">Explication</span><span class="sxs-lookup"><span data-stu-id="bf550-116">Explanation</span></span>  
 <span data-ttu-id="bf550-117">Cette erreur indique que l'utilisateur ne dispose pas d'autorisation en écriture vers la destination</span><span class="sxs-lookup"><span data-stu-id="bf550-117">This error indicates the user may not have permission to write to the destination.</span></span> <span data-ttu-id="bf550-118">ou que certaines propriétés requises n'ont pas été correctement spécifiées, par exemple Adresse (URI) et Type de liaison.</span><span class="sxs-lookup"><span data-stu-id="bf550-118">Or some of the required properties were not correctly specified, such as Address (URI), and Binding Type.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bf550-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="bf550-119">User Action</span></span>  
 <span data-ttu-id="bf550-120">La procédure suivante permet de configurer l'identité du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="bf550-120">Use the following procedure to configure the endpoint identity.</span></span>  
  
#### <a name="to-configure-the-endpoint-identity"></a><span data-ttu-id="bf550-121">Pour configurer l'identité du point de terminaison</span><span class="sxs-lookup"><span data-stu-id="bf550-121">To configure the endpoint identity</span></span>  
  
1.  <span data-ttu-id="bf550-122">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="bf550-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="bf550-123">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="bf550-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="bf550-124">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="bf550-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="bf550-125">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="bf550-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="bf550-126">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bf550-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="bf550-127">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="bf550-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="bf550-128">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="bf550-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="bf550-129">WCF **[***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="bf550-129">In the WCF **[***transport type***] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="bf550-130">Assurez-vous que l’écriture dans le dossier de destination est autorisé.</span><span class="sxs-lookup"><span data-stu-id="bf550-130">Ensure that writing to the destination folder is permitted.</span></span>  
  
10. <span data-ttu-id="bf550-131">Vérifiez le **comportement** onglet et la **identité du point de terminaison** paramètres dans le **général** onglet pour vous assurer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="bf550-131">Check the **Behavior** tab and the **Endpoint Identity** settings in the **General** tab to ensure they are valid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf550-132">Vous devez disposer d'autorisations en écriture dans le dossier de destination.</span><span class="sxs-lookup"><span data-stu-id="bf550-132">You must have write permissions to the destination folder.</span></span> <span data-ttu-id="bf550-133">Pour les obtenir, contactez l'administrateur de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bf550-133">Contact the administrator of the machine to get these permissions.</span></span>
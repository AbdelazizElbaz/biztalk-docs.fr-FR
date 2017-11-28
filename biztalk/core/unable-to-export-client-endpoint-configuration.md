---
title: "Impossible d’exporter la configuration de point de terminaison client | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d93fe5e-fdb2-49c5-86de-d428b1ecda7f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 941d42ff01bcf578bd7ba7c426c6fe5ca2bfbce3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-export-client-endpoint-configuration"></a><span data-ttu-id="20faa-102">Impossible d'exporter la configuration du point de terminaison client</span><span class="sxs-lookup"><span data-stu-id="20faa-102">Unable to export client endpoint configuration</span></span>
## <a name="details"></a><span data-ttu-id="20faa-103">Détails</span><span class="sxs-lookup"><span data-stu-id="20faa-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="20faa-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="20faa-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="20faa-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="20faa-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="20faa-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="20faa-106">Event ID</span></span>|<span data-ttu-id="20faa-107">0</span><span class="sxs-lookup"><span data-stu-id="20faa-107">0</span></span>|  
|<span data-ttu-id="20faa-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="20faa-108">Event Source</span></span>|<span data-ttu-id="20faa-109">0</span><span class="sxs-lookup"><span data-stu-id="20faa-109">0</span></span>|  
|<span data-ttu-id="20faa-110">Composant</span><span class="sxs-lookup"><span data-stu-id="20faa-110">Component</span></span>|<span data-ttu-id="20faa-111">0</span><span class="sxs-lookup"><span data-stu-id="20faa-111">0</span></span>|  
|<span data-ttu-id="20faa-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="20faa-112">Symbolic Name</span></span>|<span data-ttu-id="20faa-113">0</span><span class="sxs-lookup"><span data-stu-id="20faa-113">0</span></span>|  
|<span data-ttu-id="20faa-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="20faa-114">Message Text</span></span>|<span data-ttu-id="20faa-115">Impossible d'exporter la configuration du point de terminaison client vers « {0} »</span><span class="sxs-lookup"><span data-stu-id="20faa-115">Unable to export client endpoint configuration to "{0}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="20faa-116">Explication</span><span class="sxs-lookup"><span data-stu-id="20faa-116">Explanation</span></span>  
 <span data-ttu-id="20faa-117">Cette erreur indique l'un des problèmes suivants :</span><span class="sxs-lookup"><span data-stu-id="20faa-117">This error indicates one of the following:</span></span>  
  
-   <span data-ttu-id="20faa-118">L'utilisateur ne dispose pas d'autorisation en écriture dans la destination.</span><span class="sxs-lookup"><span data-stu-id="20faa-118">The user may not have permission to write to the destination.</span></span>  
  
     <span data-ttu-id="20faa-119">\- - OU -</span><span class="sxs-lookup"><span data-stu-id="20faa-119">\- OR -</span></span>  
  
-   <span data-ttu-id="20faa-120">Certaines propriétés requises ont été pas correctement spécifiés, tel que **adresse (URI)** et **Type de liaison**.</span><span class="sxs-lookup"><span data-stu-id="20faa-120">Some of the required properties were not correctly specified, such as **Address (URI)** and **Binding Type**.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="20faa-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="20faa-121">User Action</span></span>  
 <span data-ttu-id="20faa-122">Utilisez la procédure suivante pour vérifier les autorisations utilisateur et confirmer **adresse (URI)** et **Type de liaison** les paramètres sont valides.</span><span class="sxs-lookup"><span data-stu-id="20faa-122">Use the following procedure to verify user permissions and confirm **Address (URI)** and **Binding Type** settings are valid.</span></span>  
  
#### <a name="to-verify-user-permissions-and-confirm-settings"></a><span data-ttu-id="20faa-123">Pour vérifier les autorisations d'utilisateur et confirmer les paramètres</span><span class="sxs-lookup"><span data-stu-id="20faa-123">To verify user permissions and confirm settings</span></span>  
  
1.  <span data-ttu-id="20faa-124">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="20faa-124">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="20faa-125">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="20faa-125">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="20faa-126">Localisez votre application, puis votre transport.</span><span class="sxs-lookup"><span data-stu-id="20faa-126">Locate your application, and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="20faa-127">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="20faa-127">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="20faa-128">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="20faa-128">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="20faa-129">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="20faa-129">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="20faa-130">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="20faa-130">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="20faa-131">WCF **[***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="20faa-131">In the WCF **[***transport type***] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="20faa-132">Vérifiez que l'écriture dans le dossier de destination est autorisée.</span><span class="sxs-lookup"><span data-stu-id="20faa-132">Ensure writing to the destination folder is permitted.</span></span>  
  
10. <span data-ttu-id="20faa-133">Vérifier la **comportement** onglet et la **identité du point de terminaison** paramètres **général** onglet pour vous assurer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="20faa-133">Check the **Behavior** tab and the **Endpoint Identity** settings in **General** tab to ensure they are valid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20faa-134">Vous devez disposer d'autorisations en écriture dans le dossier de destination.</span><span class="sxs-lookup"><span data-stu-id="20faa-134">You must have write permissions to the destination folder.</span></span> <span data-ttu-id="20faa-135">Pour les obtenir, contactez l'administrateur de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="20faa-135">Contact the administrator of the machine to get these permissions.</span></span>
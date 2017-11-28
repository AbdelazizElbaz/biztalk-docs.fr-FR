---
title: "Impossible de créer l’identité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 531f1057-1b6d-40ae-bf2f-a36baf4e0341
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 246db2e9546fbbea3db07cbaa5267f57936dfa14
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="failed-to-create-identity"></a><span data-ttu-id="b56b5-102">Échec de création d'une identité</span><span class="sxs-lookup"><span data-stu-id="b56b5-102">Failed to create identity</span></span>
## <a name="details"></a><span data-ttu-id="b56b5-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b56b5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b56b5-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b56b5-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b56b5-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b56b5-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="b56b5-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b56b5-106">Event ID</span></span>|<span data-ttu-id="b56b5-107">0</span><span class="sxs-lookup"><span data-stu-id="b56b5-107">0</span></span>|  
|<span data-ttu-id="b56b5-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b56b5-108">Event Source</span></span>|<span data-ttu-id="b56b5-109">0</span><span class="sxs-lookup"><span data-stu-id="b56b5-109">0</span></span>|  
|<span data-ttu-id="b56b5-110">Composant</span><span class="sxs-lookup"><span data-stu-id="b56b5-110">Component</span></span>|<span data-ttu-id="b56b5-111">0</span><span class="sxs-lookup"><span data-stu-id="b56b5-111">0</span></span>|  
|<span data-ttu-id="b56b5-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b56b5-112">Symbolic Name</span></span>|<span data-ttu-id="b56b5-113">0</span><span class="sxs-lookup"><span data-stu-id="b56b5-113">0</span></span>|  
|<span data-ttu-id="b56b5-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b56b5-114">Message Text</span></span>|<span data-ttu-id="b56b5-115">Cette erreur indique que l'adaptateur n'a pas pu créer l'identité du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b56b5-115">This error indicates the adapter failed to create the endpoint identity.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b56b5-116">Explication</span><span class="sxs-lookup"><span data-stu-id="b56b5-116">Explanation</span></span>  
 <span data-ttu-id="b56b5-117">Cette erreur indique que l'adaptateur n'a pas pu créer l'identité du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b56b5-117">This error indicates the adapter failed to create the endpoint identity.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b56b5-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b56b5-118">User Action</span></span>  
 <span data-ttu-id="b56b5-119">La procédure suivante permet de configurer l'identité du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b56b5-119">Use the following procedure to configure the endpoint identity.</span></span>  
  
#### <a name="to-configure-the-endpoint-identity"></a><span data-ttu-id="b56b5-120">Pour configurer l'identité du point de terminaison</span><span class="sxs-lookup"><span data-stu-id="b56b5-120">To configure the endpoint identity</span></span>  
  
1.  <span data-ttu-id="b56b5-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="b56b5-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b56b5-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="b56b5-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="b56b5-123">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="b56b5-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="b56b5-124">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="b56b5-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="b56b5-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b56b5-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="b56b5-126">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="b56b5-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="b56b5-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="b56b5-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="b56b5-128">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="b56b5-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="b56b5-129">Dans le **identité du point de terminaison** , cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="b56b5-129">In the **Endpoint Identity** section, click **Edit**.</span></span>  
  
10. <span data-ttu-id="b56b5-130">Dans le **Éditeur d’identités** boîte de dialogue zone, vérifiez que les paramètres sont valides.</span><span class="sxs-lookup"><span data-stu-id="b56b5-130">In the **Identity Editor** dialog box, ensure that the settings are valid.</span></span>
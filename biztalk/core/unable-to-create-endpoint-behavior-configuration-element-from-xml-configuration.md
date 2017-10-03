---
title: "Impossible de créer l’élément de configuration de comportement de point de terminaison à partir de la configuration XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89d906a4-ea85-42d8-8e9e-0a3a7774bcd8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc10a737f2c0a2f344a106868c910a2ecb8144bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-create-endpoint-behavior-configuration-element-from-xml-configuration"></a><span data-ttu-id="7dd17-102">Impossible de créer l'élément de configuration du comportement du point de terminaison à partir de la configuration XML.</span><span class="sxs-lookup"><span data-stu-id="7dd17-102">Unable to create endpoint behavior configuration element from XML configuration</span></span>
## <a name="details"></a><span data-ttu-id="7dd17-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7dd17-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7dd17-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7dd17-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7dd17-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7dd17-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="7dd17-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7dd17-106">Event ID</span></span>|<span data-ttu-id="7dd17-107">0</span><span class="sxs-lookup"><span data-stu-id="7dd17-107">0</span></span>|  
|<span data-ttu-id="7dd17-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7dd17-108">Event Source</span></span>|<span data-ttu-id="7dd17-109">0</span><span class="sxs-lookup"><span data-stu-id="7dd17-109">0</span></span>|  
|<span data-ttu-id="7dd17-110">Composant</span><span class="sxs-lookup"><span data-stu-id="7dd17-110">Component</span></span>|<span data-ttu-id="7dd17-111">0</span><span class="sxs-lookup"><span data-stu-id="7dd17-111">0</span></span>|  
|<span data-ttu-id="7dd17-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7dd17-112">Symbolic Name</span></span>|<span data-ttu-id="7dd17-113">0</span><span class="sxs-lookup"><span data-stu-id="7dd17-113">0</span></span>|  
|<span data-ttu-id="7dd17-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7dd17-114">Message Text</span></span>|<span data-ttu-id="7dd17-115">Impossible de créer l'élément de configuration du comportement du point de terminaison à partir de la configuration XML.</span><span class="sxs-lookup"><span data-stu-id="7dd17-115">Unable to create endpoint behavior configuration element from XML configuration</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7dd17-116">Explication</span><span class="sxs-lookup"><span data-stu-id="7dd17-116">Explanation</span></span>  
 <span data-ttu-id="7dd17-117">Cette erreur indique que l'adaptateur n'a pas chargé la configuration du comportement du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="7dd17-117">This error indicates the adapter did not load the endpoint behavior configuration.</span></span> <span data-ttu-id="7dd17-118">Cette situation se produit essentiellement avec les adaptateurs WCF-Custom et WCF-CustomIsolated.</span><span class="sxs-lookup"><span data-stu-id="7dd17-118">This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7dd17-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7dd17-119">User Action</span></span>  
 <span data-ttu-id="7dd17-120">La procédure suivante permet de configurer le comportement du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="7dd17-120">Use the following procedure to configure the endpoint behavior.</span></span>  
  
#### <a name="to-configure-the-endpoint-behavior"></a><span data-ttu-id="7dd17-121">Pour configurer le comportement du point de terminaison</span><span class="sxs-lookup"><span data-stu-id="7dd17-121">To configure the endpoint behavior</span></span>  
  
1.  <span data-ttu-id="7dd17-122">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="7dd17-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="7dd17-123">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="7dd17-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="7dd17-124">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="7dd17-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="7dd17-125">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="7dd17-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="7dd17-126">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7dd17-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="7dd17-127">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="7dd17-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="7dd17-128">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="7dd17-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="7dd17-129">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **comportement** onglet.</span><span class="sxs-lookup"><span data-stu-id="7dd17-129">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Behavior** tab.</span></span>  
  
9. <span data-ttu-id="7dd17-130">Dans le **comportement** section, vérifiez le **EndpointBehavior** configuration.</span><span class="sxs-lookup"><span data-stu-id="7dd17-130">In the **Behavior** section, check the **EndpointBehavior** configuration.</span></span>
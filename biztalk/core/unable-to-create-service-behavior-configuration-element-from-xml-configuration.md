---
title: "Impossible de créer l’élément de configuration de comportement de service à partir de la configuration XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6732e5d2-bb4b-48ec-af59-467eede80f36
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 830391eca955c3a3381cb780df0c01e114ceda2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-create-service-behavior-configuration-element-from-xml-configuration"></a><span data-ttu-id="84e0f-102">Impossible de créer l'élément de configuration du comportement du service à partir de la configuration XML</span><span class="sxs-lookup"><span data-stu-id="84e0f-102">Unable to create service behavior configuration element from XML configuration</span></span>
## <a name="details"></a><span data-ttu-id="84e0f-103">Détails</span><span class="sxs-lookup"><span data-stu-id="84e0f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="84e0f-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="84e0f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="84e0f-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="84e0f-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="84e0f-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="84e0f-106">Event ID</span></span>|<span data-ttu-id="84e0f-107">0</span><span class="sxs-lookup"><span data-stu-id="84e0f-107">0</span></span>|  
|<span data-ttu-id="84e0f-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="84e0f-108">Event Source</span></span>|<span data-ttu-id="84e0f-109">0</span><span class="sxs-lookup"><span data-stu-id="84e0f-109">0</span></span>|  
|<span data-ttu-id="84e0f-110">Composant</span><span class="sxs-lookup"><span data-stu-id="84e0f-110">Component</span></span>|<span data-ttu-id="84e0f-111">0</span><span class="sxs-lookup"><span data-stu-id="84e0f-111">0</span></span>|  
|<span data-ttu-id="84e0f-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="84e0f-112">Symbolic Name</span></span>|<span data-ttu-id="84e0f-113">0</span><span class="sxs-lookup"><span data-stu-id="84e0f-113">0</span></span>|  
|<span data-ttu-id="84e0f-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="84e0f-114">Message Text</span></span>|<span data-ttu-id="84e0f-115">Impossible de créer l'élément de configuration du comportement du service à partir de la configuration XML.</span><span class="sxs-lookup"><span data-stu-id="84e0f-115">Unable to create service behavior configuration element from XML configuration.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="84e0f-116">Explication</span><span class="sxs-lookup"><span data-stu-id="84e0f-116">Explanation</span></span>  
 <span data-ttu-id="84e0f-117">Cette erreur indique que l'adaptateur n'a pas chargé la configuration de comportement de service.</span><span class="sxs-lookup"><span data-stu-id="84e0f-117">This error indicates the adapter did not load the service behavior configuration.</span></span> <span data-ttu-id="84e0f-118">Cette situation se produit essentiellement avec les adaptateurs WCF-Custom et WCF-CustomIsolated.</span><span class="sxs-lookup"><span data-stu-id="84e0f-118">This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="84e0f-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="84e0f-119">User Action</span></span>  
 <span data-ttu-id="84e0f-120">La procédure suivante permet de configurer le comportement du service.</span><span class="sxs-lookup"><span data-stu-id="84e0f-120">Use the following procedure to configure the service behavior.</span></span>  
  
#### <a name="to-configure-the-service-behavior"></a><span data-ttu-id="84e0f-121">Pour configurer le comportement du service</span><span class="sxs-lookup"><span data-stu-id="84e0f-121">To configure the service behavior</span></span>  
  
1.  <span data-ttu-id="84e0f-122">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="84e0f-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="84e0f-123">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="84e0f-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="84e0f-124">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="84e0f-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="84e0f-125">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="84e0f-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="84e0f-126">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="84e0f-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="84e0f-127">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="84e0f-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="84e0f-128">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="84e0f-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="84e0f-129">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **comportement** onglet.</span><span class="sxs-lookup"><span data-stu-id="84e0f-129">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Behavior** tab.</span></span>  
  
9. <span data-ttu-id="84e0f-130">Dans le **comportement** section, vérifiez le **ServiceBehavior** configuration.</span><span class="sxs-lookup"><span data-stu-id="84e0f-130">In the **Behavior** section, check the **ServiceBehavior** configuration.</span></span>
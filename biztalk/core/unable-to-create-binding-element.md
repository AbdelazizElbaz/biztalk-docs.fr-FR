---
title: "Impossible de créer l’élément de liaison | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b036833-12ba-463c-8df6-9d5e1ac26b6d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9b93bfd8ca7f87904f32fefa60837603677bc23
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-create-binding-element"></a><span data-ttu-id="b958d-102">Impossible de créer l'élément de liaison</span><span class="sxs-lookup"><span data-stu-id="b958d-102">Unable to create binding element</span></span>
## <a name="details"></a><span data-ttu-id="b958d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b958d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b958d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b958d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b958d-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b958d-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="b958d-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b958d-106">Event ID</span></span>|<span data-ttu-id="b958d-107">0</span><span class="sxs-lookup"><span data-stu-id="b958d-107">0</span></span>|  
|<span data-ttu-id="b958d-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b958d-108">Event Source</span></span>|<span data-ttu-id="b958d-109">0</span><span class="sxs-lookup"><span data-stu-id="b958d-109">0</span></span>|  
|<span data-ttu-id="b958d-110">Composant</span><span class="sxs-lookup"><span data-stu-id="b958d-110">Component</span></span>|<span data-ttu-id="b958d-111">0</span><span class="sxs-lookup"><span data-stu-id="b958d-111">0</span></span>|  
|<span data-ttu-id="b958d-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b958d-112">Symbolic Name</span></span>|<span data-ttu-id="b958d-113">0</span><span class="sxs-lookup"><span data-stu-id="b958d-113">0</span></span>|  
|<span data-ttu-id="b958d-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b958d-114">Message Text</span></span>|<span data-ttu-id="b958d-115">Impossible de créer l'élément pour la liaison « {0} »</span><span class="sxs-lookup"><span data-stu-id="b958d-115">Unable to create binding element for binding "{0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b958d-116">Explication</span><span class="sxs-lookup"><span data-stu-id="b958d-116">Explanation</span></span>  
 <span data-ttu-id="b958d-117">Cette erreur indique que l'adaptateur n'a pas pu créer la liaison spécifiée dans la configuration au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="b958d-117">This error indicates the adapter cannot create the binding specified in the configuration at runtime.</span></span> <span data-ttu-id="b958d-118">Cette situation se produit essentiellement avec les adaptateurs WCF-Custom et WCF-CustomIsolated.</span><span class="sxs-lookup"><span data-stu-id="b958d-118">This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b958d-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b958d-119">User Action</span></span>  
 <span data-ttu-id="b958d-120">La procédure suivante permet de vérifier que les éléments de liaison sont valides.</span><span class="sxs-lookup"><span data-stu-id="b958d-120">Use the following procedure to verify binding elements are valid.</span></span>  
  
#### <a name="to-verify-binding-elements"></a><span data-ttu-id="b958d-121">Pour vérifier les éléments de liaison</span><span class="sxs-lookup"><span data-stu-id="b958d-121">To verify binding elements</span></span>  
  
1.  <span data-ttu-id="b958d-122">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="b958d-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b958d-123">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="b958d-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="b958d-124">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="b958d-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="b958d-125">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="b958d-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="b958d-126">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b958d-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="b958d-127">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="b958d-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="b958d-128">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="b958d-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="b958d-129">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="b958d-129">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="b958d-130">Vérifiez que les éléments de liaison spécifiées dans la configuration sont valides.</span><span class="sxs-lookup"><span data-stu-id="b958d-130">Ensure that the binding elements specified in the configuration are valid.</span></span>
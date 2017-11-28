---
title: "Élément de liaison inconnu ou inattendu. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56021ff3-5abf-46ab-90bb-4531ccc9abd0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43c59c20968ea1329a6d689c7976aeba48650fc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unknown-or-unexpected-binding-element"></a><span data-ttu-id="49c2c-102">Élément de liaison inattendu ou inconnu</span><span class="sxs-lookup"><span data-stu-id="49c2c-102">Unknown or unexpected binding element</span></span>
## <a name="details"></a><span data-ttu-id="49c2c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="49c2c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49c2c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="49c2c-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="49c2c-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="49c2c-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="49c2c-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="49c2c-106">Event ID</span></span>|<span data-ttu-id="49c2c-107">0</span><span class="sxs-lookup"><span data-stu-id="49c2c-107">0</span></span>|  
|<span data-ttu-id="49c2c-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="49c2c-108">Event Source</span></span>|<span data-ttu-id="49c2c-109">0</span><span class="sxs-lookup"><span data-stu-id="49c2c-109">0</span></span>|  
|<span data-ttu-id="49c2c-110">Composant</span><span class="sxs-lookup"><span data-stu-id="49c2c-110">Component</span></span>|<span data-ttu-id="49c2c-111">0</span><span class="sxs-lookup"><span data-stu-id="49c2c-111">0</span></span>|  
|<span data-ttu-id="49c2c-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="49c2c-112">Symbolic Name</span></span>|<span data-ttu-id="49c2c-113">0</span><span class="sxs-lookup"><span data-stu-id="49c2c-113">0</span></span>|  
|<span data-ttu-id="49c2c-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="49c2c-114">Message Text</span></span>|<span data-ttu-id="49c2c-115">Élément de liaison inattendu ou inconnu</span><span class="sxs-lookup"><span data-stu-id="49c2c-115">Unknown or unexpected binding element</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="49c2c-116">Explication</span><span class="sxs-lookup"><span data-stu-id="49c2c-116">Explanation</span></span>  
 <span data-ttu-id="49c2c-117">Cette erreur indique que l'adaptateur n'a pas pu trouver l'élément de liaison défini par l'utilisateur spécifié dans la liaison.</span><span class="sxs-lookup"><span data-stu-id="49c2c-117">This error indicates the adapter cannot find the user defined binding element specified in the binding.</span></span> <span data-ttu-id="49c2c-118">Cette situation se produit essentiellement avec les adaptateurs WCF-Custom et WCF-CustomIsolated.</span><span class="sxs-lookup"><span data-stu-id="49c2c-118">This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="49c2c-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="49c2c-119">User Action</span></span>  
 <span data-ttu-id="49c2c-120">La procédure suivante permet de vérifier que les éléments de liaison sont valides.</span><span class="sxs-lookup"><span data-stu-id="49c2c-120">Use the following procedure to verify binding elements are valid.</span></span>  
  
#### <a name="to-verify-binding-elements-are-valid"></a><span data-ttu-id="49c2c-121">Pour vérifier la validité des éléments de liaison</span><span class="sxs-lookup"><span data-stu-id="49c2c-121">To verify binding elements are valid</span></span>  
  
1.  <span data-ttu-id="49c2c-122">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="49c2c-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="49c2c-123">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="49c2c-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="49c2c-124">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="49c2c-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="49c2c-125">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="49c2c-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="49c2c-126">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="49c2c-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="49c2c-127">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="49c2c-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="49c2c-128">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="49c2c-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="49c2c-129">WCF **[***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="49c2c-129">In the WCF **[***transport type***] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="49c2c-130">Vérifiez que les éléments de liaison spécifiées dans la configuration sont valides.</span><span class="sxs-lookup"><span data-stu-id="49c2c-130">Ensure that the binding elements specified in the configuration are valid.</span></span>
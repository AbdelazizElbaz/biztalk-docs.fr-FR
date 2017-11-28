---
title: "Erreurs d’action | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87cf0a5b-d1dd-4807-9660-e8a8b7012b40
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49f25f1f15307077943ef370a335885690bea22c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="action-errors"></a><span data-ttu-id="a6372-102">Erreurs en relation avec les actions</span><span class="sxs-lookup"><span data-stu-id="a6372-102">Action Errors</span></span>
<span data-ttu-id="a6372-103">Cette section inclut des informations détaillées sur le diagnostic et la résolution des erreurs en relation avec les actions WCF.</span><span class="sxs-lookup"><span data-stu-id="a6372-103">This section contains detailed information for diagnosing and resolving WCF Action errors.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a6372-104">Détails</span><span class="sxs-lookup"><span data-stu-id="a6372-104">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a6372-105">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a6372-105">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a6372-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a6372-106">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="a6372-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a6372-107">Event ID</span></span>|<span data-ttu-id="a6372-108">0</span><span class="sxs-lookup"><span data-stu-id="a6372-108">0</span></span>|  
|<span data-ttu-id="a6372-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a6372-109">Event Source</span></span>|<span data-ttu-id="a6372-110">0</span><span class="sxs-lookup"><span data-stu-id="a6372-110">0</span></span>|  
|<span data-ttu-id="a6372-111">Composant</span><span class="sxs-lookup"><span data-stu-id="a6372-111">Component</span></span>|<span data-ttu-id="a6372-112">0</span><span class="sxs-lookup"><span data-stu-id="a6372-112">0</span></span>|  
|<span data-ttu-id="a6372-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a6372-113">Symbolic Name</span></span>|<span data-ttu-id="a6372-114">0</span><span class="sxs-lookup"><span data-stu-id="a6372-114">0</span></span>|  
|<span data-ttu-id="a6372-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a6372-115">Message Text</span></span>|<span data-ttu-id="a6372-116">Une action unique ne peut pas contenir de caractères de nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="a6372-116">A single action cannot contain new line characters.</span></span> <span data-ttu-id="a6372-117">Supprimez tous les caractères de nouvelle ligne ou,</span><span class="sxs-lookup"><span data-stu-id="a6372-117">Remove all new line characters.</span></span> <span data-ttu-id="a6372-118">pour spécifier plusieurs actions, utilisez la syntaxe du mappage d'actions.</span><span class="sxs-lookup"><span data-stu-id="a6372-118">Or, to specify multiple actions, use the action mapping syntax.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a6372-119">Explication</span><span class="sxs-lookup"><span data-stu-id="a6372-119">Explanation</span></span>  
 <span data-ttu-id="a6372-120">Cette erreur indique que la propriété d'action d'un port d'envoi inclut un caractère de nouvelle ligne, ce qui n'est pas autorisé.</span><span class="sxs-lookup"><span data-stu-id="a6372-120">This error indicates the action property of a send port contains a new line character, which is not allowed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6372-121">Cette restriction ne s'applique pas lorsque l'action est définie en tant que mappage.</span><span class="sxs-lookup"><span data-stu-id="a6372-121">This restriction does not apply when the action is defined as a mapping.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a6372-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a6372-122">User Action</span></span>  
 <span data-ttu-id="a6372-123">La procédure suivante permet de résoudre la propriété d'action.</span><span class="sxs-lookup"><span data-stu-id="a6372-123">Use the following procedure to fix the action property.</span></span>  
  
 
1.  <span data-ttu-id="a6372-124">Ouvrez **Administration de BizTalk Server.**</span><span class="sxs-lookup"><span data-stu-id="a6372-124">Open **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a6372-125">Dans la racine de la Console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="a6372-125">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="a6372-126">Localisez votre application, puis votre transport.</span><span class="sxs-lookup"><span data-stu-id="a6372-126">Locate your application, and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="a6372-127">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="a6372-127">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="a6372-128">Sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a6372-128">Select **Properties**.</span></span>  
  
6.  <span data-ttu-id="a6372-129">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="a6372-129">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="a6372-130">Sélectionnez **Configurer**.</span><span class="sxs-lookup"><span data-stu-id="a6372-130">Select **Configure**.</span></span>  
  
8.  <span data-ttu-id="a6372-131">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, sélectionnez le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="a6372-131">In the **WCF [***transport type***] Transport Properties** dialog box, select the **General** tab.</span></span>  
  
9. <span data-ttu-id="a6372-132">Dans le **en-tête d’Action SOAP** section, supprimez le caractère de nouvelle ligne à partir de la **Action** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6372-132">In the **SOAP Action header** section, remove the new line character from the **Action** text box.</span></span>  

## <a name="more-good-info"></a><span data-ttu-id="a6372-133">Plus d’informations correct</span><span class="sxs-lookup"><span data-stu-id="a6372-133">More good info</span></span>  
 <span data-ttu-id="a6372-134">Pour plus d’informations sur les actions, consultez [spécifiant les Actions SOAP pour envoyer les adaptateurs WCF](../core/specifying-soap-actions-for-wcf-send-adapters.md)</span><span class="sxs-lookup"><span data-stu-id="a6372-134">For additional information on actions, see [Specifying SOAP Actions for WCF Send Adapters](../core/specifying-soap-actions-for-wcf-send-adapters.md)</span></span>
---
title: Erreurs de Configuration de port | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92eae0d8-a0c4-4f8c-b91a-fd98b9f6931a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f0e51c06fab9dadb60fc43a003108e50bbb0fab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="port-configuration-errors"></a><span data-ttu-id="e2b05-102">Erreurs en relation avec la configuration des ports</span><span class="sxs-lookup"><span data-stu-id="e2b05-102">Port Configuration Errors</span></span>
<span data-ttu-id="e2b05-103">Informations sur le diagnostic et résolution des erreurs de Configuration du Port WCF.</span><span class="sxs-lookup"><span data-stu-id="e2b05-103">Information for diagnosing and resolving WCF Port Configuration errors.</span></span>  

## <a name="cannot-merge-operation-due-to-communication-pattern-conflict"></a><span data-ttu-id="e2b05-104">Impossible de fusionner l'opération en raison d'un conflit de modèles de communication</span><span class="sxs-lookup"><span data-stu-id="e2b05-104">Cannot merge operation due to communication pattern conflict</span></span>
  
||<span data-ttu-id="e2b05-105">Détails</span><span class="sxs-lookup"><span data-stu-id="e2b05-105">Details</span></span>|  
|-|-|  
|<span data-ttu-id="e2b05-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e2b05-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e2b05-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e2b05-107">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="e2b05-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e2b05-108">Event ID</span></span>|<span data-ttu-id="e2b05-109">0</span><span class="sxs-lookup"><span data-stu-id="e2b05-109">0</span></span>|  
|<span data-ttu-id="e2b05-110">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e2b05-110">Event Source</span></span>|<span data-ttu-id="e2b05-111">0</span><span class="sxs-lookup"><span data-stu-id="e2b05-111">0</span></span>|  
|<span data-ttu-id="e2b05-112">Composant</span><span class="sxs-lookup"><span data-stu-id="e2b05-112">Component</span></span>|<span data-ttu-id="e2b05-113">0</span><span class="sxs-lookup"><span data-stu-id="e2b05-113">0</span></span>|  
|<span data-ttu-id="e2b05-114">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e2b05-114">Symbolic Name</span></span>|<span data-ttu-id="e2b05-115">0</span><span class="sxs-lookup"><span data-stu-id="e2b05-115">0</span></span>|  
|<span data-ttu-id="e2b05-116">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e2b05-116">Message Text</span></span>|<span data-ttu-id="e2b05-117">Impossible de fusionner l'opération « {0} » en raison d'un conflit de modèles de communication.</span><span class="sxs-lookup"><span data-stu-id="e2b05-117">Cannot merge operation "{0}" due to communication pattern conflict.</span></span>  <span data-ttu-id="e2b05-118">Toutes les opérations doivent être unidirectionnelles ou avec requête-réponse</span><span class="sxs-lookup"><span data-stu-id="e2b05-118">All operations must be one-way or request-response</span></span>|  
  
### <a name="explanation"></a><span data-ttu-id="e2b05-119">Explication</span><span class="sxs-lookup"><span data-stu-id="e2b05-119">Explanation</span></span>  
 <span data-ttu-id="e2b05-120">Cette erreur indique que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tente de fusionner des types de ports possédant différents modèles de communication.</span><span class="sxs-lookup"><span data-stu-id="e2b05-120">This error indicates [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is attempting to merge ports with port types that have different communication patterns.</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="e2b05-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e2b05-121">User Action</span></span>  
 <span data-ttu-id="e2b05-122">À l'aide de l'Assistant Configuration du port, vérifiez que tous les ports en cours de fusion possèdent la même direction de communication (unidirectionnelle ou de requête-réponse).</span><span class="sxs-lookup"><span data-stu-id="e2b05-122">Using the Port Configuration Wizard, ensure that all the ports that are being merged have the same communication direction, either one-way or request-response.</span></span>  
  
 <span data-ttu-id="e2b05-123">Pour plus d’informations sur la configuration du port, consultez [comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="e2b05-123">For additional information on port configuration, see [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md).</span></span>
 
## <a name="port-types-that-have-a-combination-of-one-way-and-request-response-operations-are-not-allowed"></a><span data-ttu-id="e2b05-124">Les types de ports associant les opérations de requête-réponse et unidirectionnelles ne sont pas autorisés</span><span class="sxs-lookup"><span data-stu-id="e2b05-124">Port types that have a combination of one-way and request-response operations are not allowed</span></span> 
  
||<span data-ttu-id="e2b05-125">Détails</span><span class="sxs-lookup"><span data-stu-id="e2b05-125">Details</span></span>|  
|-|-|  
|<span data-ttu-id="e2b05-126">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e2b05-126">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e2b05-127">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e2b05-127">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="e2b05-128">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e2b05-128">Event ID</span></span>|<span data-ttu-id="e2b05-129">0</span><span class="sxs-lookup"><span data-stu-id="e2b05-129">0</span></span>|  
|<span data-ttu-id="e2b05-130">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e2b05-130">Event Source</span></span>|<span data-ttu-id="e2b05-131">0</span><span class="sxs-lookup"><span data-stu-id="e2b05-131">0</span></span>|  
|<span data-ttu-id="e2b05-132">Composant</span><span class="sxs-lookup"><span data-stu-id="e2b05-132">Component</span></span>|<span data-ttu-id="e2b05-133">0</span><span class="sxs-lookup"><span data-stu-id="e2b05-133">0</span></span>|  
|<span data-ttu-id="e2b05-134">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e2b05-134">Symbolic Name</span></span>|<span data-ttu-id="e2b05-135">0</span><span class="sxs-lookup"><span data-stu-id="e2b05-135">0</span></span>|  
|<span data-ttu-id="e2b05-136">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e2b05-136">Message Text</span></span>|<span data-ttu-id="e2b05-137">Les types de ports associant les opérations de requête-réponse et unidirectionnelles ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="e2b05-137">Port types that have a combination of one-way and request-response operations are not allowed.</span></span> <span data-ttu-id="e2b05-138">Corrigez le type de port de description « {0} » de service « {{1} », puis réexécutez l’Assistant</span><span class="sxs-lookup"><span data-stu-id="e2b05-138">Correct service description "{0}" port type "{1}" and rerun the wizard</span></span>|  
  
### <a name="explanation"></a><span data-ttu-id="e2b05-139">Explication</span><span class="sxs-lookup"><span data-stu-id="e2b05-139">Explanation</span></span>  
 <span data-ttu-id="e2b05-140">Cette erreur indique que le service que vous tentez d'utiliser est associé à des opérations unidirectionnelles et bidirectionnelles (ou avec requête-réponse).</span><span class="sxs-lookup"><span data-stu-id="e2b05-140">This error indicates the service trying to be consumed has operations that are both one-way and two-way (or request-response).</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="e2b05-141">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e2b05-141">User Action</span></span>  
 <span data-ttu-id="e2b05-142">Corrigez le service WCF avec les opérations appropriées (soit unidirectionnelles, soit avec requête-réponse) et tentez à nouveau de l'utiliser (si vous en êtes propriétaire).</span><span class="sxs-lookup"><span data-stu-id="e2b05-142">Correct the service with the appropriate operations (either one-way or request-response but not both) and try to consume (if you own the WCF services that you are trying to consume).</span></span> <span data-ttu-id="e2b05-143">Sinon, contactez le fournisseur de services.</span><span class="sxs-lookup"><span data-stu-id="e2b05-143">Otherwise, contact the service provider.</span></span>

---
title: "Find (méthode) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Find method
ms.assetid: 676827a6-82af-4922-bf9e-aca5bd23624b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a5432c68c36dcf8e769351af6d57f3cd3ed712b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="find-method"></a><span data-ttu-id="1b74a-102">Find (méthode)</span><span class="sxs-lookup"><span data-stu-id="1b74a-102">Find Method</span></span>
<span data-ttu-id="1b74a-103">Utilisé pour renvoyer la liste des clés qui correspondent aux clés partielles fournies.</span><span class="sxs-lookup"><span data-stu-id="1b74a-103">Used to return a list of keys that satisfy the supplied partial search keys.</span></span> <span data-ttu-id="1b74a-104">Notez que pour une interface de composant qui n'inclut qu'une instance (sans clé), la fonction `Find()` n'est pas générée.</span><span class="sxs-lookup"><span data-stu-id="1b74a-104">Note that for a component interface that has only one instance, that is, there is no key, the `Find()` function is not generated.</span></span> <span data-ttu-id="1b74a-105">Voir aussi [Get (méthode)](../core/get-method.md).</span><span class="sxs-lookup"><span data-stu-id="1b74a-105">See also [Get Method](../core/get-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b74a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b74a-106">Syntax</span></span>  
  
```  
Find (partialKey, keyList)  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b74a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1b74a-107">Parameters</span></span>  
  
|<span data-ttu-id="1b74a-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="1b74a-108">Parameter</span></span>|<span data-ttu-id="1b74a-109"> Description</span><span class="sxs-lookup"><span data-stu-id="1b74a-109">Description</span></span>|  
|---------------|-----------------|  
|`partialKey`|<span data-ttu-id="1b74a-110">Structure dans laquelle les clés individuelles sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="1b74a-110">A structure where the individual keys are optional.</span></span>|  
|`keyList`|<span data-ttu-id="1b74a-111">Liste de clés qui correspond au paramètre `partialKey`.</span><span class="sxs-lookup"><span data-stu-id="1b74a-111">A list of keys that matches the `partialKey`.</span></span> <span data-ttu-id="1b74a-112">Il est un paramètre de sortie.</span><span class="sxs-lookup"><span data-stu-id="1b74a-112">It is an output parameter.</span></span><br /><br /> <span data-ttu-id="1b74a-113">Les clés correspondent au jeu de clés Find défini pour l'interface de composant spécifique.</span><span class="sxs-lookup"><span data-stu-id="1b74a-113">The keys correspond to the set of Find Keys as defined for the particular component interface.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b74a-114">Notes</span><span class="sxs-lookup"><span data-stu-id="1b74a-114">Remarks</span></span>  
 <span data-ttu-id="1b74a-115">Lorsque vous spécifiez les clés partielles, il est possible d'utiliser la recherche par caractères génériques disponible via la fonction `Find()` interne de PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="1b74a-115">When you specify the partial keys, it is possible to use the same wildcard search available from the PeopleSoft internal `Find()` function.</span></span> <span data-ttu-id="1b74a-116">Par exemple, la valeur de clé partielle ACCOUNT « 11 » renvoie toutes les clés ACCOUNT commençant par « 11 », tandis que la valeur « %40 » renvoie toutes les clés ACCOUNT contenant la valeur « 40 ».</span><span class="sxs-lookup"><span data-stu-id="1b74a-116">For example, the partial ACCOUNT key of "11" returns all ACCOUNT keys that start with "11", whereas "%40" returns all ACCOUNT keys that contain "40" anywhere within the key.</span></span> <span data-ttu-id="1b74a-117">Une clé partielle « _4_4 » renvoie toutes les clés ACCOUNT incluant le caractère « 4 » en deuxième et quatrième position.</span><span class="sxs-lookup"><span data-stu-id="1b74a-117">A partial key "_4_4" returns all ACCOUNT keys with the character "4" in the 2nd and 4th positions.</span></span>  
  
 <span data-ttu-id="1b74a-118">Remarque : Avec l’implémentation actuelle du serveur PeopleSoft, si plus de 300 éléments correspondent aux critères de recherche, l’appel échoue.</span><span class="sxs-lookup"><span data-stu-id="1b74a-118">Note: With the current implementation of the PeopleSoft Server, if more than 300 items match the search criteria, the call fails.</span></span> <span data-ttu-id="1b74a-119">Il s'agit d'une restriction du serveur PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="1b74a-119">This is a restriction of the PeopleSoft server.</span></span> <span data-ttu-id="1b74a-120">La méthode de l'adaptateur BizTalk pour PeopleSoft Enterprise `Find()` est fournie si la fonction `Find` de PeopleSoft est activée dans l'interface de composant et si les clés Get sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="1b74a-120">The Microsoft BizTalk Adapter for PeopleSoft Enterprise `Find()` method is provided if the PeopleSoft `Find` function in the component interface is enabled and Get keys are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b74a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b74a-121">See Also</span></span>  
 [<span data-ttu-id="1b74a-122">Annexe a : méthodes d’Interface de composant</span><span class="sxs-lookup"><span data-stu-id="1b74a-122">Appendix A: Component Interface Methods</span></span>](../core/appendix-a-component-interface-methods.md)
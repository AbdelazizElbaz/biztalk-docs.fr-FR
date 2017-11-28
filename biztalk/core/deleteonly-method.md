---
title: "Méthode DeleteOnly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DeleteOnly method
ms.assetid: 99e1d7af-1450-439b-882f-de677e593bee
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3982c67b4c2eb572a57a4ad602b1d302f9b53ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deleteonly-method"></a><span data-ttu-id="e60f7-102">Méthode DeleteOnly</span><span class="sxs-lookup"><span data-stu-id="e60f7-102">DeleteOnly Method</span></span>
<span data-ttu-id="e60f7-103">Permet de supprimer des éléments dans un regroupement.</span><span class="sxs-lookup"><span data-stu-id="e60f7-103">Allows you to delete items in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e60f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e60f7-104">Syntax</span></span>  
  
```  
DeleteOnly(key1, key2, ..., keyn, correctionMode, interactiveMode,  
    properties)  
```  
  
## <a name="parameters"></a><span data-ttu-id="e60f7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e60f7-105">Parameters</span></span>  
  
|<span data-ttu-id="e60f7-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="e60f7-106">Parameter</span></span>|<span data-ttu-id="e60f7-107"> Description</span><span class="sxs-lookup"><span data-stu-id="e60f7-107">Description</span></span>|  
|---------------|-----------------|  
|`key`|<span data-ttu-id="e60f7-108">Constitue un ensemble de paramètres qui doit être fourni.</span><span class="sxs-lookup"><span data-stu-id="e60f7-108">Is a set of parameters that must be supplied.</span></span> <span data-ttu-id="e60f7-109">Ce jeu de clés doit exister dans la base de données du serveur, sans quoi une erreur survient.</span><span class="sxs-lookup"><span data-stu-id="e60f7-109">This set of keys must exist in the server database, or an error occurs.</span></span> <span data-ttu-id="e60f7-110">Ces clés correspondent au jeu de clés Get défini pour l'interface de composant spécifique.</span><span class="sxs-lookup"><span data-stu-id="e60f7-110">These keys correspond to the set of Get Keys as defined for the particular component interface.</span></span>|  
|`correctionMode`|<span data-ttu-id="e60f7-111">Indicateur booléen.</span><span class="sxs-lookup"><span data-stu-id="e60f7-111">A Boolean flag.</span></span> <span data-ttu-id="e60f7-112">Lorsque ce paramètre est défini sur true, il permet la suppression d'éléments ayant une date d'effet passée dans une collection.</span><span class="sxs-lookup"><span data-stu-id="e60f7-112">When set to true, allows deletion of past effective-dated items in a collection.</span></span> <span data-ttu-id="e60f7-113">Plus précisément, il permet de supprimer des éléments dont l'EFFDT est antérieure à la date d'effet actuelle.</span><span class="sxs-lookup"><span data-stu-id="e60f7-113">Specifically, it allows the deletion of items that have EFFDT prior to the current effective date.</span></span> <span data-ttu-id="e60f7-114">Sans cet indicateur défini sur TRUE, toute modification apportée à ces éléments génère une erreur renvoyée par le serveur PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="e60f7-114">Without this flag set to TRUE, any modification to these items results in an error returned from PeopleSoft server.</span></span> <span data-ttu-id="e60f7-115">**Remarque :** le `correctionMode` argument est uniquement exposé pour ces interfaces de composant qui contiennent des éléments d’effet.</span><span class="sxs-lookup"><span data-stu-id="e60f7-115">**Note:**  The `correctionMode` argument is only exposed for those component interfaces that contain effective-dated items.</span></span> <span data-ttu-id="e60f7-116">Sinon, il n’est pas affiché dans le cadre de l’argument.</span><span class="sxs-lookup"><span data-stu-id="e60f7-116">Otherwise it is not shown as part of the argument.</span></span>|  
|`interactiveMode`|<span data-ttu-id="e60f7-117">Utilisé pour la gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="e60f7-117">Used for error handling.</span></span><br /><br /> <span data-ttu-id="e60f7-118">Lorsqu'il accède aux propriétés dans une interface de composant, l'adaptateur BizTalk pour PeopleSoft Enterprise utilise les API fournies par PeopleSoft qui lisent et écrivent des champs individuels dans l'interface de composant. Cependant, ces modifications ne sont pas propagées au serveur PeopleSoft les unes après les autres.</span><span class="sxs-lookup"><span data-stu-id="e60f7-118">When accessing properties in a component interface, the BizTalk Adapter for PeopleSoft Enterprise uses PeopleSoft-provided APIs, which read and write individual fields in the component interface; however, these changes are not propagated to the PeopleSoft server one at a time.</span></span> <span data-ttu-id="e60f7-119">Au lieu de cela, psjoa.jar (avec lequel l’adaptateur BizTalk pour PeopleSoft Enterprise interagit) regroupe toutes les modifications et envoie les modifications au serveur dans un seul package.</span><span class="sxs-lookup"><span data-stu-id="e60f7-119">Instead, the psjoa.jar (with which the BizTalk Adapter for PeopleSoft Enterprise interacts) packages all the changes and sends the changes to the server in one package.</span></span> <span data-ttu-id="e60f7-120">En cas d'échec d'une des mises à jour individuelles, une erreur générique est renvoyée, sans identifier l'erreur réelle.</span><span class="sxs-lookup"><span data-stu-id="e60f7-120">If any of the individual updates fail, a generic error is returned, which does not pinpoint the actual error.</span></span> <span data-ttu-id="e60f7-121">Si le mode interactif est défini sur TRUE, chaque mise à jour de champ est envoyée au serveur individuellement.</span><span class="sxs-lookup"><span data-stu-id="e60f7-121">With the interactive mode set to TRUE, every field update is sent to the server individually.</span></span> <span data-ttu-id="e60f7-122">Cela a un impact considérable sur les performances mais des informations spécifiques sur l'erreur sont fournies en cas d'échec de la mise à jour (par exemple, si une valeur non valide est utilisée pour la définition d'un champ).</span><span class="sxs-lookup"><span data-stu-id="e60f7-122">This has a substantial impact on performance, but it does provide specific error information if the update fails (for example, if an invalid value is used for setting a field).</span></span><br /><br /> <span data-ttu-id="e60f7-123">Le paramètre `interactiveMode` offre des performances optimales et fournit des rapports d'erreurs au niveau de la mise à jour du champ.</span><span class="sxs-lookup"><span data-stu-id="e60f7-123">The `interactiveMode` parameter provides maximum performance and provides error reporting at the field-update level.</span></span> <span data-ttu-id="e60f7-124">Pour utiliser correctement cette fonctionnalité, il est recommandé d'effectuer des appels normaux avec `interactiveMode` défini sur FALSE.</span><span class="sxs-lookup"><span data-stu-id="e60f7-124">To use this feature properly, it is recommended that you make normal calls with `interactiveMode` set to FALSE.</span></span> <span data-ttu-id="e60f7-125">Cela ne doit avoir aucun impact sur les performances.</span><span class="sxs-lookup"><span data-stu-id="e60f7-125">There should be no impact on performance.</span></span> <span data-ttu-id="e60f7-126">Si une erreur est renvoyée, le même appel peut faire l'objet d'une nouvelle tentative avec l'indicateur interactiveMode défini sur TRUE.</span><span class="sxs-lookup"><span data-stu-id="e60f7-126">If an error is returned, the same call can be retried with the interactiveMode flag set to TRUE.</span></span> <span data-ttu-id="e60f7-127">Lorsque l'appel échoue, le serveur renvoie un message d'erreur plus précis.</span><span class="sxs-lookup"><span data-stu-id="e60f7-127">When the call fails, the server returns a more precise error message.</span></span>|  
|`properties`|<span data-ttu-id="e60f7-128">Contient un sous-ensemble de la structure existant sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="e60f7-128">Contains a subset of the structure that exists on the server.</span></span> <span data-ttu-id="e60f7-129">Tous les éléments terminaux sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="e60f7-129">All items that are leaves are deleted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e60f7-130">Notes</span><span class="sxs-lookup"><span data-stu-id="e60f7-130">Remarks</span></span>  
 <span data-ttu-id="e60f7-131">Les propriétés possèdent le même type de données que celui de la méthode `CreateEx` ou `UpdateEx` de cette interface de composant. Toutefois, seules les valeurs des clés sont importantes.</span><span class="sxs-lookup"><span data-stu-id="e60f7-131">The properties have the same data type as the `CreateEx` or `UpdateEx` methods of this component interface; however, only the key values are important.</span></span> <span data-ttu-id="e60f7-132">Les autres valeurs sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="e60f7-132">The non-key values are ignored.</span></span> <span data-ttu-id="e60f7-133">Les valeurs des clés doivent correspondre à celles se trouvant sur le serveur. Dans le cas contraire, une exception est générée.</span><span class="sxs-lookup"><span data-stu-id="e60f7-133">The key values must match those on the server, otherwise an exception is raised.</span></span>  
  
 <span data-ttu-id="e60f7-134">Ce qui suit présente l'utilisation des valeurs des clés.</span><span class="sxs-lookup"><span data-stu-id="e60f7-134">The following demonstrates the use of the key values.</span></span> <span data-ttu-id="e60f7-135">Une collection contient les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e60f7-135">If a collection contains the items:</span></span>  
  
-   <span data-ttu-id="e60f7-136">item0</span><span class="sxs-lookup"><span data-stu-id="e60f7-136">item0</span></span>  
  
-   <span data-ttu-id="e60f7-137">item1</span><span class="sxs-lookup"><span data-stu-id="e60f7-137">item1</span></span>  
  
-   <span data-ttu-id="e60f7-138">item2</span><span class="sxs-lookup"><span data-stu-id="e60f7-138">item2</span></span>  
  
-   <span data-ttu-id="e60f7-139">item3</span><span class="sxs-lookup"><span data-stu-id="e60f7-139">item3</span></span>  
  
 <span data-ttu-id="e60f7-140">Vous pouvez supprimer item1 et item3 en fournissant les clés qui leur sont associées dans les propriétés :</span><span class="sxs-lookup"><span data-stu-id="e60f7-140">You can delete item1 and item3 by providing the keys of item1 and item3 in the properties:</span></span>  
  
-   <span data-ttu-id="e60f7-141">item1</span><span class="sxs-lookup"><span data-stu-id="e60f7-141">item1</span></span>  
  
-   <span data-ttu-id="e60f7-142">item3</span><span class="sxs-lookup"><span data-stu-id="e60f7-142">item3</span></span>  
  
 <span data-ttu-id="e60f7-143">Après l'appel, le serveur dispose des éléments restants suivants dans la collection :</span><span class="sxs-lookup"><span data-stu-id="e60f7-143">After the call, the server has the remaining items in the collection:</span></span>  
  
-   <span data-ttu-id="e60f7-144">item0</span><span class="sxs-lookup"><span data-stu-id="e60f7-144">item0</span></span>  
  
-   <span data-ttu-id="e60f7-145">item2</span><span class="sxs-lookup"><span data-stu-id="e60f7-145">item2</span></span>  
  
 <span data-ttu-id="e60f7-146">Le deuxième exemple affiche les éléments contenant d'autres collections :</span><span class="sxs-lookup"><span data-stu-id="e60f7-146">The second example shows the items containing other collections:</span></span>  
  
-   <span data-ttu-id="e60f7-147">item0</span><span class="sxs-lookup"><span data-stu-id="e60f7-147">item0</span></span>  
  
    -   <span data-ttu-id="e60f7-148">item0a</span><span class="sxs-lookup"><span data-stu-id="e60f7-148">item0a</span></span>  
  
-   <span data-ttu-id="e60f7-149">item1</span><span class="sxs-lookup"><span data-stu-id="e60f7-149">item1</span></span>  
  
    -   <span data-ttu-id="e60f7-150">item1a</span><span class="sxs-lookup"><span data-stu-id="e60f7-150">item1a</span></span>  
  
    -   <span data-ttu-id="e60f7-151">item1b</span><span class="sxs-lookup"><span data-stu-id="e60f7-151">item1b</span></span>  
  
    -   <span data-ttu-id="e60f7-152">item1c</span><span class="sxs-lookup"><span data-stu-id="e60f7-152">item1c</span></span>  
  
-   <span data-ttu-id="e60f7-153">item2</span><span class="sxs-lookup"><span data-stu-id="e60f7-153">item2</span></span>  
  
    -   <span data-ttu-id="e60f7-154">item2a</span><span class="sxs-lookup"><span data-stu-id="e60f7-154">item2a</span></span>  
  
    -   <span data-ttu-id="e60f7-155">item2b</span><span class="sxs-lookup"><span data-stu-id="e60f7-155">item2b</span></span>  
  
 <span data-ttu-id="e60f7-156">Vous pouvez supprimer item1b ainsi que tous les éléments item2 en fournissant les clés qui leur sont associées :</span><span class="sxs-lookup"><span data-stu-id="e60f7-156">You can delete item1b and all of item2 by giving the keys to item1b and item2:</span></span>  
  
-   <span data-ttu-id="e60f7-157">item1</span><span class="sxs-lookup"><span data-stu-id="e60f7-157">item1</span></span>  
  
    -   <span data-ttu-id="e60f7-158">item1b</span><span class="sxs-lookup"><span data-stu-id="e60f7-158">item1b</span></span>  
  
-   <span data-ttu-id="e60f7-159">item2</span><span class="sxs-lookup"><span data-stu-id="e60f7-159">item2</span></span>  
  
 <span data-ttu-id="e60f7-160">En fournissant une sous-collection vide pour item2, vous le transformez en élément terminal et toute cette sous-branche est supprimée.</span><span class="sxs-lookup"><span data-stu-id="e60f7-160">By providing an empty sub-collection for item2, you turn it into a leaf and that entire sub-branch is deleted.</span></span> <span data-ttu-id="e60f7-161">Après l'appel, le serveur dispose des éléments restants suivants :</span><span class="sxs-lookup"><span data-stu-id="e60f7-161">After the call, the server has the remaining items:</span></span>  
  
-   <span data-ttu-id="e60f7-162">item0</span><span class="sxs-lookup"><span data-stu-id="e60f7-162">item0</span></span>  
  
    -   <span data-ttu-id="e60f7-163">item0a</span><span class="sxs-lookup"><span data-stu-id="e60f7-163">item0a</span></span>  
  
-   <span data-ttu-id="e60f7-164">item1</span><span class="sxs-lookup"><span data-stu-id="e60f7-164">item1</span></span>  
  
    -   <span data-ttu-id="e60f7-165">item1a</span><span class="sxs-lookup"><span data-stu-id="e60f7-165">item1a</span></span>  
  
    -   <span data-ttu-id="e60f7-166">item1c</span><span class="sxs-lookup"><span data-stu-id="e60f7-166">item1c</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e60f7-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e60f7-167">See Also</span></span>  
 [<span data-ttu-id="e60f7-168">Annexe a : méthodes d’Interface de composant</span><span class="sxs-lookup"><span data-stu-id="e60f7-168">Appendix A: Component Interface Methods</span></span>](../core/appendix-a-component-interface-methods.md)
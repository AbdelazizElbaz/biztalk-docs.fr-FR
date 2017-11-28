---
title: "Get (méthode) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Get method
ms.assetid: 0e621077-f0ef-495c-ba6b-0c6154f48113
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d56b060cc261f707a4aa7b0d6a496a62707c4dca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-method"></a><span data-ttu-id="f8bcb-102">Méthode Get</span><span class="sxs-lookup"><span data-stu-id="f8bcb-102">Get Method</span></span>
<span data-ttu-id="f8bcb-103">Permet de récupérer les propriétés basées sur les paramètres de clé d’entrée (key1, key2...</span><span class="sxs-lookup"><span data-stu-id="f8bcb-103">Used to retrieve properties based on the input key parameters (key1, key2, …</span></span> <span data-ttu-id="f8bcb-104">keyn).</span><span class="sxs-lookup"><span data-stu-id="f8bcb-104">keyn).</span></span> <span data-ttu-id="f8bcb-105">Le paramètre sortant est une structure contenant les propriétés de l'enregistrement correspondant aux paramètres de clé.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-105">The output parameter is a structure containing the properties of the record that matches the key parameters.</span></span> <span data-ttu-id="f8bcb-106">Si l’interface de composant a une seule instance (autrement dit, aucune clé n’existe), la fonction Get ne contient pas de n’importe quel paramètre de clé.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-106">If the component interface has only one instance (that is, there is no key), the Get function does not contain any key parameter.</span></span> <span data-ttu-id="f8bcb-107">Consultez également [méthode Find](../core/find-method.md).</span><span class="sxs-lookup"><span data-stu-id="f8bcb-107">Also see [Find Method](../core/find-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8bcb-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8bcb-108">Syntax</span></span>  
  
```  
Get (key1, key2, ... keyn, properties)  
Get (key1, key2, ... keyn, getHistoryItems, properties)  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8bcb-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8bcb-109">Parameters</span></span>  
  
|<span data-ttu-id="f8bcb-110">Paramètre</span><span class="sxs-lookup"><span data-stu-id="f8bcb-110">Parameter</span></span>|<span data-ttu-id="f8bcb-111"> Description</span><span class="sxs-lookup"><span data-stu-id="f8bcb-111">Description</span></span>|  
|---------------|-----------------|  
|`key`|<span data-ttu-id="f8bcb-112">Ensemble de paramètres qui doit exister dans la base de données du serveur, sans quoi une erreur survient.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-112">A set of parameters that must exist in the server database; otherwise an error occurs.</span></span> <span data-ttu-id="f8bcb-113">Ces clés correspondent au jeu de clés Get défini pour l’Interface de composant particulier.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-113">These keys correspond to the set of Get Keys as defined for the particular Component Interface.</span></span>|  
|`properties`|<span data-ttu-id="f8bcb-114">Contient une structure complète des propriétés de l'interface de composant, qui est renvoyée une fois l'appel terminé.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-114">Contains a complete structure of the component interface properties, which is returned upon completion of the call.</span></span>|  
|`getHistoryItems`|<span data-ttu-id="f8bcb-115">Valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-115">A Boolean value.</span></span> <span data-ttu-id="f8bcb-116">Si les propriétés de l'interface de composant contiennent des éléments ayant une date d'effet en dessous de 0 (et donc, un champ de clé nommé EFFDT), le paramètre supplémentaire `getHistoryItems` est requis.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-116">If the properties of the component interface contain effective-dated items below level 0 (that is, a key field with a name of EFFDT) the `getHistoryItems` additional parameter is required.</span></span><br /><br /> <span data-ttu-id="f8bcb-117">Si la valeur est :</span><span class="sxs-lookup"><span data-stu-id="f8bcb-117">If the value is:</span></span><br /><br /> <span data-ttu-id="f8bcb-118">-Valeur est true, tous les éléments sont retournés en tant que séquence (qui peut être incorporée dans n’importe quel niveau).</span><span class="sxs-lookup"><span data-stu-id="f8bcb-118">-   True—All effective dated items are returned as a sequence (which could be embedded in any level).</span></span> <span data-ttu-id="f8bcb-119">à savoir tous les éléments passés, actuels et futurs.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-119">These include all past effective dated items, the current effective dated item, as well as all future effective dated items</span></span><br /><span data-ttu-id="f8bcb-120">-False — uniquement actuel et tous les éléments ayant une date futures effet sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-120">-   False—Only the current and all future effective dated items are returned.</span></span> <span data-ttu-id="f8bcb-121">Si les appels suivants à la mise à jour sur la même instance sont effectués, puis `getHistoryItems` doit être défini à False.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-121">If subsequent calls to update on the same instance will be made, then `getHistoryItems` should be set to False.</span></span>|  
  
### <a name="remarks"></a><span data-ttu-id="f8bcb-122">Notes</span><span class="sxs-lookup"><span data-stu-id="f8bcb-122">Remarks</span></span>  
 <span data-ttu-id="f8bcb-123">Si les propriétés de l'interface de composant contiennent des éléments ayant une date d'effet en dessous de 0 (et donc, un champ de clé nommé EFFDT), un paramètre supplémentaire `getHistoryItems` est requis.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-123">If the properties of the component interface contain effective dated items below level 0 (that is, a key field with a name of EFFDT), an additional parameter, `getHistoryItems`, is required.</span></span> <span data-ttu-id="f8bcb-124">Ce paramètre est de type booléen.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-124">This parameter is of type Boolean.</span></span> <span data-ttu-id="f8bcb-125">S'il est défini sur True, tous les éléments ayant une date d'effet sont renvoyés en tant que séquence (qui peut être incorporée à tous les niveaux),</span><span class="sxs-lookup"><span data-stu-id="f8bcb-125">If it is set to True, all effective dated items are returned as a sequence (which could be embedded in any level).</span></span> <span data-ttu-id="f8bcb-126">Ces incluent tous les éléments ayant une date d’effet, l’élément ayant une date effective actuelle, ainsi que tous les éléments ayant une date futures efficaces.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-126">These include all past effective dated items, the current effective dated item, as well as all future effective dated items.</span></span> <span data-ttu-id="f8bcb-127">Si le `getHistoryItems` paramètre est défini sur False, uniquement actuel et tous les éléments ayant une date futures effet sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-127">If the `getHistoryItems` parameter is set to False, only the current and all future effective dated items are returned.</span></span> <span data-ttu-id="f8bcb-128">Si d'autres appels relatifs à la mise à jour de la même instance sont effectués par la suite, `getHistoryItems` doit être défini sur False.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-128">If subsequent calls to update on the same instance are to be made, then `getHistoryItems` should be set to False.</span></span> <span data-ttu-id="f8bcb-129">Voir aussi [méthode UpdateEx](../core/updateex-method.md).</span><span class="sxs-lookup"><span data-stu-id="f8bcb-129">See also [UpdateEx Method](../core/updateex-method.md).</span></span>  
  
 <span data-ttu-id="f8bcb-130">Si l'interface de composant ne possède pas de clé (par exemple, s'il n'existe qu'une seule instance), la méthode `Get()` a la forme :</span><span class="sxs-lookup"><span data-stu-id="f8bcb-130">If the component interface does not have a key, as in the case where only one instance can exist, then the `Get()` method has the form:</span></span>  
  
```  
Get(properties)  
```  
  
 <span data-ttu-id="f8bcb-131">Pour plus d'informations sur les éléments ayant une date d'effet, consultez la documentation de PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-131">For more information on effective dated items, see the PeopleSoft Enterprise documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8bcb-132">La méthode de l'adaptateur BizTalk pour PeopleSoft Enterprise `Get()` est fournie si la fonction `Get` de PeopleSoft est activée dans l'interface de composant.</span><span class="sxs-lookup"><span data-stu-id="f8bcb-132">The BizTalk Adapter for PeopleSoft Enterprise `Get()` method is provided if the PeopleSoft `Get` function in the component interface is enabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8bcb-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8bcb-133">See Also</span></span>  
 [<span data-ttu-id="f8bcb-134">Annexe a : méthodes d’Interface de composant</span><span class="sxs-lookup"><span data-stu-id="f8bcb-134">Appendix A: Component Interface Methods</span></span>](../core/appendix-a-component-interface-methods.md)
---
title: "Création de liens | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps, links
- BizTalk Mapper, links
ms.assetid: e8596c50-62e9-40a7-ad61-29cbdb4f4fc9
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87570b82dc63a02c629e0fc024c2e44d57df1401
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-links"></a><span data-ttu-id="56ce0-102">Création de liens</span><span class="sxs-lookup"><span data-stu-id="56ce0-102">Creating Links</span></span>
<span data-ttu-id="56ce0-103">Le Mappeur BizTalk permet d’automatiser certains éléments participant à la création des liens.</span><span class="sxs-lookup"><span data-stu-id="56ce0-103">BizTalk Mapper helps you automate some elements involved in link creation.</span></span> <span data-ttu-id="56ce0-104">La création de liens simple s’apparente aux types de données simples.</span><span class="sxs-lookup"><span data-stu-id="56ce0-104">Simple link creation is similar to simple data types.</span></span> <span data-ttu-id="56ce0-105">Il existe des formes plus sophistiquées de création de liens qui ressemblent davantage à l’attribution de structure dans un langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="56ce0-105">There are more sophisticated forms of link creation that are more like structure assignment in a programming language.</span></span> <span data-ttu-id="56ce0-106">Une création de liens simple spécifie, par exemple, combien d’éléments de données multiples doivent être déplacés de messages d’instance d’entrée vers les messages d’instance de sortie correspondants.</span><span class="sxs-lookup"><span data-stu-id="56ce0-106">An example is a single link creation that specifies how multiple items of data are to be moved from input instance messages to corresponding output instance messages.</span></span>  
  
 <span data-ttu-id="56ce0-107">Vous pouvez créer des liens à l’aide des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="56ce0-107">You create links using the following methods:</span></span>  
  
-   <span data-ttu-id="56ce0-108">**Création de liens simple.**</span><span class="sxs-lookup"><span data-stu-id="56ce0-108">**Simple link creation.**</span></span> <span data-ttu-id="56ce0-109">dans la création de liens simple, vous produisez un lien par déplacement.</span><span class="sxs-lookup"><span data-stu-id="56ce0-109">In simple link creation, you produce a link by dragging.</span></span> <span data-ttu-id="56ce0-110">Le déplacement par glissement d’un champ du schéma source vers un champ du schéma de destination entraîne la création d’un élément ou d’un attribut dans un message d’instance de sortie et insère la valeur de l’élément ou de l’attribut dans le message.</span><span class="sxs-lookup"><span data-stu-id="56ce0-110">Dragging a field in the source schema to a field in the destination schema causes the creation of an element or attribute in an output instance message and inserts the value of the element or attribute in the message.</span></span> <span data-ttu-id="56ce0-111">Ces liens peuvent être créés directement entre **enregistrement** et **champ** nœuds dans le schéma source et de destination, ou ils peuvent inclure un ou plusieurs fonctoids dans un chemin d’accès du lien entre **enregistrement**et **champ** nœuds dans les schémas source et de destination.</span><span class="sxs-lookup"><span data-stu-id="56ce0-111">Such links can be made directly between **Record** and **Field** nodes in the source and destination schema, or they can include one or more functoids in a link path between **Record** and **Field** nodes in the source and destination schemas.</span></span>  
  
-   <span data-ttu-id="56ce0-112">**Liens de type structure.**</span><span class="sxs-lookup"><span data-stu-id="56ce0-112">**Structure links.**</span></span> <span data-ttu-id="56ce0-113">Lors de la création de liens de type structure, vous produisez plusieurs liens simples en même temps entre **enregistrement** et **champ** nœuds dans les schémas source et de destination qui ont la même structure relative.</span><span class="sxs-lookup"><span data-stu-id="56ce0-113">In creating structure links, you produce multiple simple links at the same time between **Record** and **Field** nodes in the source and destination schemas that have the same relative structure.</span></span> <span data-ttu-id="56ce0-114">Pour utiliser la création de liens de type structure, la structure des parties pertinentes des deux schémas doit être identique.</span><span class="sxs-lookup"><span data-stu-id="56ce0-114">To use structure linking, the structure of the relevant parts of the two schemas must be the same.</span></span> <span data-ttu-id="56ce0-115">Pour plus d’informations sur la configuration des liens de type structure, consultez [comment lier des enregistrements automatiquement](../core/how-to-link-records-automatically.md).</span><span class="sxs-lookup"><span data-stu-id="56ce0-115">For more information about configuring structure links, see [How to Link Records Automatically](../core/how-to-link-records-automatically.md).</span></span>  
  
-   <span data-ttu-id="56ce0-116">**Liens de mise en correspondance de nom.**</span><span class="sxs-lookup"><span data-stu-id="56ce0-116">**Name-matching links.**</span></span> <span data-ttu-id="56ce0-117">Lorsque vous utilisez cette méthode, vous créez plusieurs liens simples en même temps entre **enregistrement** et **champ** nœuds dans les schémas source et de destination selon les noms de la **enregistrements** et **champ** nœuds.</span><span class="sxs-lookup"><span data-stu-id="56ce0-117">When you use this method, you create multiple simple links at the same time between **Record** and **Field** nodes in the source and destination schemas based on the names of the **Records** and **Field** nodes.</span></span> <span data-ttu-id="56ce0-118">Pour utiliser la création de liens de type correspondance des noms, la structure des schémas source et de destination doit être très similaire mais pas rigoureusement identique.</span><span class="sxs-lookup"><span data-stu-id="56ce0-118">To use name-matching linking, the structure of the source and destination schemas must be very similar, but not exactly the same.</span></span> <span data-ttu-id="56ce0-119">Pour plus d’informations sur la configuration des liaisons de correspondance de noms, consultez [comment lier des enregistrements automatiquement](../core/how-to-link-records-automatically.md).</span><span class="sxs-lookup"><span data-stu-id="56ce0-119">For more information about configuring name-matching links, see [How to Link Records Automatically](../core/how-to-link-records-automatically.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56ce0-120">Vous pouvez également voir [comment gérer des liens existants](../core/how-to-manage-existing-links.md) pour plus d’informations sur la modification les liaisons existantes.</span><span class="sxs-lookup"><span data-stu-id="56ce0-120">You can also see [How to Manage Existing Links](../core/how-to-manage-existing-links.md) for information about how to change/modify the existing links.</span></span>  
  
## <a name="preserving-whitespace-in-a-link"></a><span data-ttu-id="56ce0-121">Conservation des espaces dans un lien</span><span class="sxs-lookup"><span data-stu-id="56ce0-121">Preserving Whitespace in a Link</span></span>  
 <span data-ttu-id="56ce0-122">Vous devez écrire un script personnalisé si vous souhaitez conserver les espaces figurant dans un élément source lorsque vous effectuez un mappage sur un fonctoid ou un élément cible.</span><span class="sxs-lookup"><span data-stu-id="56ce0-122">If you want to preserve whitespace from a source element when mapping to a target element or functoid, you will need to write a custom script.</span></span>  
  
 <span data-ttu-id="56ce0-123">Les espaces ne sont pas conservés que ce soit dans le mappeur ou dans le système runtime.</span><span class="sxs-lookup"><span data-stu-id="56ce0-123">Whitespace is not preserved either in the Mapper or in the runtime system.</span></span> <span data-ttu-id="56ce0-124">Le Mappeur et le système runtime utilisent l'objet BTSXslTransform.Transform qui gère la transformation de messages volumineux et s'appuie sur XmlReader pour naviguer à l'aide du modèle de données XPath.</span><span class="sxs-lookup"><span data-stu-id="56ce0-124">Both the Mapper and the runtime system use BTSXslTransform.Transform which handles large-message transformations and relies on XmlReader to navigate using the XPath data model.</span></span>  
  
 <span data-ttu-id="56ce0-125">Afin de conserver les espaces, vous pouvez écrire un script personnalisé qui renvoie le nombre d'espaces requis.</span><span class="sxs-lookup"><span data-stu-id="56ce0-125">To preserve whitespace, you can write a custom script that returns the required amount of whitespace.</span></span> <span data-ttu-id="56ce0-126">Par exemple, le code ci-après renvoie toujours une chaîne comprenant 5 espaces :</span><span class="sxs-lookup"><span data-stu-id="56ce0-126">For example, the code below always returns a string containing 5 whitespace characters:</span></span>  
  
```  
public string Whitespace(string param1)  
{  
  return "     ";  
}  
```  
  
 <span data-ttu-id="56ce0-127">Si vous liez un élément source à l'entrée de ce script et un élément cible en tant qu'élément sortant, l'élément sortant comprendra 5 caractères une fois le mappage exécuté.</span><span class="sxs-lookup"><span data-stu-id="56ce0-127">If you link a source element to the input of this script and a target element as the output, when the map is executed, the output element will contain 5 whitespace characters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56ce0-128">Si vous affichez la sortie à l’aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], l’élément apparaîtra vide.</span><span class="sxs-lookup"><span data-stu-id="56ce0-128">If you view the output using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], the element will appear empty.</span></span> <span data-ttu-id="56ce0-129">En effet, la visionneuse XML considère les éléments contenant des espaces comme des éléments vides.</span><span class="sxs-lookup"><span data-stu-id="56ce0-129">This is because the XML viewer treats elements containing whitespace only as empty.</span></span> <span data-ttu-id="56ce0-130">Pour afficher l’espace blanc, avec le bouton droit de la vue XML et sélectionnez **afficher la Source**.</span><span class="sxs-lookup"><span data-stu-id="56ce0-130">To see the whitespace, right-click the XML view and select **View Source**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ce0-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56ce0-131">See Also</span></span>  
 [<span data-ttu-id="56ce0-132">Procédure : modifier les propriétés de lien</span><span class="sxs-lookup"><span data-stu-id="56ce0-132">How to Edit Link Properties</span></span>](../core/how-to-edit-link-properties.md)
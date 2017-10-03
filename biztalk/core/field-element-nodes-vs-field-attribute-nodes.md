---
title: "Nœuds Élément de champ et Nœuds d’attribut de champ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1fffbca-8886-42c0-9214-cd0c5314850c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d90f622e20bbdbace6804b2418cb68fd2ad60da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="field-element-nodes-vs-field-attribute-nodes"></a><span data-ttu-id="89797-102">Nœuds Élément de champ et Nœuds Attribut de champ</span><span class="sxs-lookup"><span data-stu-id="89797-102">Field Element Nodes vs. Field Attribute Nodes</span></span>

## <a name="overview"></a><span data-ttu-id="89797-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="89797-103">Overview</span></span>
<span data-ttu-id="89797-104">Des schémas de fichier plat sont utilisés par le désassembleur de fichier plat afin de contrôler la manière dont les messages d'instance de fichier plat entrants sont convertis dans leur format XML équivalent et utilisés par l'assembleur de fichier plat pour contrôler comment les messages XML sortants sont convertis dans leurs messages d'instance de fichier plat équivalents.</span><span class="sxs-lookup"><span data-stu-id="89797-104">Flat file schemas are used by the flat file disassembler to control how inbound flat file instance messages are translated into their equivalent XML form, and are used by the flat file assembler to control how outbound XML messages are translated into their equivalent flat file instance messages.</span></span> <span data-ttu-id="89797-105">Lors de la construction de ces schémas, vous utilisez soit un **élément de champ** nœud ou un **attribut de champ** nœud à certains endroits du schéma pour contrôler si un champ particulier dans l’instance de fichier plat message correspond à un élément XML ou à un attribut XML dans le format XML équivalent du message.</span><span class="sxs-lookup"><span data-stu-id="89797-105">When constructing such schemas, you use either a **Field Element** node or a **Field Attribute** node in particular positions within the schema to control whether a particular field in the flat file instance message corresponds to an XML element or to an XML attribute in the equivalent XML form of the message.</span></span>  

## <a name="example"></a><span data-ttu-id="89797-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="89797-106">Example</span></span>  
 <span data-ttu-id="89797-107">Par exemple, la valeur de champ alignée à gauche, et remplie d’astérisques «`red*****`» dans un fichier plat, message d’instance peut être convertie dans sa représentation XML équivalente de deux manières différentes, selon si ce champ dans le schéma est un **champ Élément** nœud ou un **attribut de champ** nœud.</span><span class="sxs-lookup"><span data-stu-id="89797-107">For example, the left-aligned, asterisk-padded field value "`red*****`" in a flat file instance message can be translated into its equivalent XML representation in two different ways depending upon whether that field in the schema is a **Field Element** node or a **Field Attribute** node.</span></span> <span data-ttu-id="89797-108">Lorsque ce champ est représenté dans le schéma par un **élément de champ** nœud avec ses **nom de nœud** « couleur » et le contenant la valeur de propriété **enregistrement** nœud a son **Nom du nœud** propriété définie sur « shirt », l’équivalent XML du champ de fichier plat est (indiqué en gras).</span><span class="sxs-lookup"><span data-stu-id="89797-108">When that field is represented in the schema by a **Field Element** node with its **Node Name** property set to "color", and the containing **Record** node has its **Node Name** property set to "shirt", the XML equivalent of the flat file field is (shown in bold type).</span></span>  
  
```  
<shirt>  
    <color>red</color>  
</shirt>  
```  
  
 <span data-ttu-id="89797-109">Lorsque ce même champ de fichier plat est représenté dans le schéma par un **attribut de champ** nœud avec ses **nom de nœud** de couleur et de l’objet contenant la valeur de propriété **enregistrement** nœud possède son **Nom de nœud** propriété shirt, l’équivalent XML du champ de fichier plat est (indiqué en gras) :</span><span class="sxs-lookup"><span data-stu-id="89797-109">When that same flat file field is represented in the schema by a **Field Attribute** node with its **Node Name** property set to color, and the containing **Record** node has its **Node Name** property set to shirt, the XML equivalent of the flat file field is (shown in bold type):</span></span>  
  
```  
<color shirt="red"/>  
```  
  
> [!NOTE]
>  <span data-ttu-id="89797-110">Schémas de fichier plat ont une restriction supplémentaire qui, au sein d’une donnée **enregistrement** nœud subordonné **attribut de champ** nœuds subordonnés doivent précéder **enregistrement** nœuds ou  **Élément de champ** nœuds.</span><span class="sxs-lookup"><span data-stu-id="89797-110">Flat file schemas have a further restriction that within a given **Record** node, subordinate **Field Attribute** nodes must come before subordinate **Record** nodes or **Field Element** nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89797-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89797-111">See Also</span></span>  
-  [<span data-ttu-id="89797-112">Considérations relatives aux champs</span><span class="sxs-lookup"><span data-stu-id="89797-112">Field Considerations</span></span>](../core/field-considerations.md)
-  <span data-ttu-id="89797-113">**Nom du nœud** propriété[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="89797-113">**Node Name** property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
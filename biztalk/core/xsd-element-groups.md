---
title: "Groupes d’éléments XSD | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XSLT, XSLT variations
- BizTalk Mapper, XSLT variations
- maps, groups
- Choice Group node
- XSD element groups
- XSLT, warnings
ms.assetid: a6ea22cb-6066-480e-8a2a-75fade3e5970
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b850841819ce844a10e407827d02993ce3559bad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xsd-element-groups"></a><span data-ttu-id="f1863-102">Groupes d'éléments XSD</span><span class="sxs-lookup"><span data-stu-id="f1863-102">XSD Element Groups</span></span>
<span data-ttu-id="f1863-103">L'utilisation de certaines structures dans un schéma peut créer des variations dans les transformations XSLT (Extensible Stylesheet Language Transformations) générées par le Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f1863-103">The use of certain structures in a schema may create variations in the Extensible Stylesheet Language Transformations (XSLT) that BizTalk Mapper generates.</span></span>  
  
 <span data-ttu-id="f1863-104">Cela peut se produire lors de l'inclusion dans le mappage d'un schéma qui définit des groupes d'éléments Séquence, Choix ou Tous.</span><span class="sxs-lookup"><span data-stu-id="f1863-104">This can occur when you include a schema in your map that defines sequence, choice, or all element groups.</span></span> <span data-ttu-id="f1863-105">Par exemple, si vous utilisez un schéma qui inclut un **groupe choix** nœud, il est possible de créer un mappage qui requiert au moins deux des enfants de la **groupe choix** nœud s’affichent dans une instance de sortie Message.</span><span class="sxs-lookup"><span data-stu-id="f1863-105">For example, if you use a schema that includes a **Choice Group** node, it is possible for you to create a map that requires two or more of the children of the **Choice Group** node to appear in an output instance message.</span></span> <span data-ttu-id="f1863-106">Dans ce cas, le Mappeur BizTalk affiche un avertissement quand vous compilez le mappage.</span><span class="sxs-lookup"><span data-stu-id="f1863-106">In this case, BizTalk Mapper displays a warning when you compile the map.</span></span> <span data-ttu-id="f1863-107">Cet avertissement signale qu'un seul des champs obligatoires que vous avez mappés peut être renseigné dans la même itération de la boucle parente lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="f1863-107">The warning tells you that only one of the required fields you have mapped may be populated in the same iteration of the parent loop at run time.</span></span> <span data-ttu-id="f1863-108">Le Mappeur BizTalk ne vous signale pas que la logique du mappage est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="f1863-108">BizTalk Mapper does not give you an error message stating that your mapping logic is incorrect.</span></span>  
  
 <span data-ttu-id="f1863-109">Vous pouvez aussi générer des variations dans les transformations XSLT quand les conditions suivantes sont réunies :</span><span class="sxs-lookup"><span data-stu-id="f1863-109">Another situation in which you might generate variations in the XSLT is when the following conditions are met:</span></span>  
  
-   <span data-ttu-id="f1863-110">**Enregistrement A** a un enfant **B d’élément de champ**.</span><span class="sxs-lookup"><span data-stu-id="f1863-110">**Record A** has a child **Field Element B**.</span></span>  
  
-   <span data-ttu-id="f1863-111">**Enregistrement A** et enfant **B d’élément de champ** se produire qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="f1863-111">**Record A** and child **Field Element B** occur once.</span></span>  
  
-   <span data-ttu-id="f1863-112">**Enregistrement A** fait partie d’un **groupe choix** qui se répète.</span><span class="sxs-lookup"><span data-stu-id="f1863-112">**Record A** is part of a **Choice Group** that repeats.</span></span>  
  
 <span data-ttu-id="f1863-113">Dans ce cas, le Mappeur BizTalk génère des transformations XSLT qui contiennent une logique d'itération pour gérer la possibilité des nombreuses variations des enregistrements sources.</span><span class="sxs-lookup"><span data-stu-id="f1863-113">In this situation, BizTalk Mapper generates XSLT that contains iteration logic to handle the possibility of the many variations of the source records.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1863-114">Vous devez être explicite concernant les mappages impliquant des groupes.</span><span class="sxs-lookup"><span data-stu-id="f1863-114">You must be explicit with respect to mappings involving groups.</span></span> <span data-ttu-id="f1863-115">Par exemple, si un schéma de destination contient un **groupe choix** nœud avec des nœuds enfants A et B, il n’est pas valide A et B simultanément dans la même itération de leur groupe parent.</span><span class="sxs-lookup"><span data-stu-id="f1863-115">For example, if a destination schema contains a **Choice Group** node with child nodes A and B, it is not valid to have A and B simultaneously on the same iteration of their parent group.</span></span> <span data-ttu-id="f1863-116">Le Mappeur BizTalk ne vous empêche pas de créer des mappages non valides.</span><span class="sxs-lookup"><span data-stu-id="f1863-116">BizTalk Mapper does not prevent you from creating mappings that are not valid.</span></span> <span data-ttu-id="f1863-117">Par conséquent, vous devez utiliser des fonctoids logiques pour définir des mappages dans lesquels A et B n'apparaissent jamais ensemble.</span><span class="sxs-lookup"><span data-stu-id="f1863-117">Therefore, you must use logical functoids to set up mappings in which A and B can never occur at the same time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1863-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1863-118">See Also</span></span>  
 <span data-ttu-id="f1863-119">[Mappages](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="f1863-119">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="f1863-120">Création de mappages à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="f1863-120">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)
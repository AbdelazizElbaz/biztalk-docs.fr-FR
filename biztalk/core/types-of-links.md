---
title: Types de liens | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compiler directives, links
- elastic links [maps]
- maps, links
- BizTalk Mapper, links
- partial links [maps]
- fixed links [maps]
ms.assetid: 348fae77-2e25-4b79-93bb-d42f3d18a3f7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64d6f1039e65989a2de0243a1a9a09f30165e603
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="types-of-links"></a><span data-ttu-id="1b1bc-102">Types de liens</span><span class="sxs-lookup"><span data-stu-id="1b1bc-102">Types of Links</span></span>
<span data-ttu-id="1b1bc-103">Voici une liste des différents types de liens disponibles dans le Mappeur BizTalk :</span><span class="sxs-lookup"><span data-stu-id="1b1bc-103">The following list summarizes the various types of links available in BizTalk Mapper:</span></span>  
  
-   <span data-ttu-id="1b1bc-104">**Liaisons souples.**</span><span class="sxs-lookup"><span data-stu-id="1b1bc-104">**Elastic links.**</span></span> <span data-ttu-id="1b1bc-105">le terme « souple » s’applique à un lien en cours de création, avant que les deux terminaisons du lien ne soient connectées.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-105">The term elastic applies to a link as it is being created, before both ends of the link are connected.</span></span> <span data-ttu-id="1b1bc-106">Par exemple, si vous faites glisser un lien depuis un champ d'un schéma source, mais que vous ne l'avez pas encore connecté à son champ correspondant dans le schéma de destination, le lien est souple.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-106">For example, if you are dragging a link from a field in the source schema, but you have not yet connected it to its corresponding field in the destination schema, the link is elastic.</span></span> <span data-ttu-id="1b1bc-107">La connexion achevée, la liaison souple devient liaison fixe.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-107">As you complete the connection, the elastic link becomes a fixed link.</span></span>  
  
     <span data-ttu-id="1b1bc-108">Vous pouvez déplacer un point de terminaison de liaison vers un autre nœud ou fonctoid.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-108">You can drag one endpoint of a link to another node or a functoid.</span></span> <span data-ttu-id="1b1bc-109">Pour plus d’informations sur le remplacement de lien, consultez [comment créer des liens](../core/how-to-create-links.md).</span><span class="sxs-lookup"><span data-stu-id="1b1bc-109">For more information about link replacement, see [How to Create Links](../core/how-to-create-links.md).</span></span>  
  
-   <span data-ttu-id="1b1bc-110">**Liaisons fixes.**</span><span class="sxs-lookup"><span data-stu-id="1b1bc-110">**Fixed Links.**</span></span> <span data-ttu-id="1b1bc-111">le terme « fixe » s'applique à un lien que vous avez explicitement construit pour représenter le mouvement d'une valeur entre un message d'instance source et un message d'instance de destination, ou au moins une partie du mouvement.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-111">The term fixed applies to a link that you have explicitly constructed to represent the movement of a value from a source instance message to a destination instance message, or at least a part of that movement.</span></span> <span data-ttu-id="1b1bc-112">Liens fixes qui sont directement connectés un **enregistrement** ou **champ** nœud dans le schéma source vers un **enregistrement** ou **champ** nœud dans la destination schéma représente une copie directe des données en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-112">Fixed links that directly connect a **Record** or **Field** node in the source schema to a **Record** or **Field** node in the destination schema represent a straight copying of data at run time.</span></span> <span data-ttu-id="1b1bc-113">Les liaisons fixes qui effectuent une connexion à l'une des extrémités d'un fonctoid représentent une partie du mouvement des données entre un message d’instance d’entrée et un message d’instance de sortie au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-113">Fixed links connecting to a functoid at one end or the other represent part of the movement of data from an input instance message to an output instance message at run time.</span></span> <span data-ttu-id="1b1bc-114">Plusieurs de ces liaisons, achevant le lien entre les schémas source et de destination, représentent l'ensemble du mouvement d'un élément de donnée.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-114">Several of these together, completing the link between the source and destination schemas, represent the entire movement of an item of data.</span></span>  
  
-   <span data-ttu-id="1b1bc-115">**Liaisons partielles.**</span><span class="sxs-lookup"><span data-stu-id="1b1bc-115">**Partial links.**</span></span> <span data-ttu-id="1b1bc-116">Le terme « partiel » s’applique aux liens pour lesquelles vous ne pouvez pas actuellement voir exactement **enregistrement** ou **champ** nœud auquel elles sont connectées dans les schémas source et de destination.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-116">The term partial applies to links for which you cannot currently see the exact **Record** or **Field** node to which they are connected in the source or destination schemas.</span></span> <span data-ttu-id="1b1bc-117">Cela se produit lorsque le **enregistrement** ou **champ** nœud auquel elles sont attachées n’est pas affiché, car un de ses nœuds ancêtres est réduit dans la représentation sous forme de l’arborescence du schéma.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-117">This occurs when the **Record** or **Field** node to which they are attached is not shown because one of its ancestor nodes is collapsed in the tree representation of the schema.</span></span> <span data-ttu-id="1b1bc-118">Pour plus d’informations sur les liaisons partielles, consultez [comment optimiser l’affichage de liens](../core/how-to-optimize-the-display-of-links.md).</span><span class="sxs-lookup"><span data-stu-id="1b1bc-118">For more information about partial links, see [How to Optimize the Display of Links](../core/how-to-optimize-the-display-of-links.md).</span></span>  
  
-   <span data-ttu-id="1b1bc-119">**Liaisons du compilateur.**</span><span class="sxs-lookup"><span data-stu-id="1b1bc-119">**Compiler links.**</span></span> <span data-ttu-id="1b1bc-120">le terme « compilateur » s'applique aux liens que le Mappeur BizTalk crée automatiquement lorsque vous générez un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-120">The term compiler applies to links that BizTalk Mapper creates automatically when you build a BizTalk project.</span></span> <span data-ttu-id="1b1bc-121">Par exemple, si vous configurez un bouclage piloté par la table, les liaisons du compilateur affichent la relation et les liens existant entre les enregistrements et les champs du schéma source et les enregistrements et les champs du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-121">For example, if you configure table-driven looping, the compiler links show the relationship and the links between the records and fields in the source schema and the records and fields in the destination schema.</span></span> <span data-ttu-id="1b1bc-122">Ce type de lien peut être généré automatiquement par des directives de compilateur ; il peut également être dirigé par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-122">This type of link can be generated automatically by compiler directives, or it can be user-directed.</span></span>  
  
 <span data-ttu-id="1b1bc-123">Par défaut, le Mappeur BizTalk affiche ces différents types de liens dans différentes couleurs de ligne pour vous aider à distinguer plus facilement les détails de vos mappages.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-123">BizTalk Mapper, by default, displays these various types of links using different colored lines to help you distinguish the detail of your maps.</span></span> <span data-ttu-id="1b1bc-124">Vous pouvez modifier les couleurs utilisées pour ces différents types de liens avec la **Options** commande sur le **outils** menu.</span><span class="sxs-lookup"><span data-stu-id="1b1bc-124">You can change the colors used for these different kinds of links with the **Options** command on the **Tools** menu.</span></span> <span data-ttu-id="1b1bc-125">Pour plus d’informations sur la modification de la couleur du rendu de différentes catégories de liens, consultez [comment personnaliser les couleurs et la police dans le Mappeur BizTalk](../core/how-to-customize-colors-and-font-in-biztalk-mapper.md).</span><span class="sxs-lookup"><span data-stu-id="1b1bc-125">For more information about how change in color renders different categories of links, see [How to Customize Colors and Font in BizTalk Mapper](../core/how-to-customize-colors-and-font-in-biztalk-mapper.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1bc-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b1bc-126">See Also</span></span>  
 [<span data-ttu-id="1b1bc-127">À l’aide de liens pour spécifier l’enregistrement et les mappages de champs</span><span class="sxs-lookup"><span data-stu-id="1b1bc-127">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)
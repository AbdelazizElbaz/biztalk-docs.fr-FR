---
title: Fonctoid Bouclage de table | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Table Looping functoids
- Table Looping functoids, about Table Looping functoids
ms.assetid: 6189a789-afe7-4e72-a778-2b0374db8f69
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c5e5f2967fb48bfe896c26246db1630266812f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="table-looping-functoid"></a><span data-ttu-id="4847f-102">Fonctoid Bouclage de table</span><span class="sxs-lookup"><span data-stu-id="4847f-102">Table Looping Functoid</span></span>
<span data-ttu-id="4847f-103">Le **bouclage de Table** fonctoid vous permet de créer une table de valeurs de sortie à utiliser pour créer le message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="4847f-103">The **Table Looping** functoid enables you to create a table of output values to use in creating the output instance message.</span></span> <span data-ttu-id="4847f-104">Les données de la table peuvent être composées de liens et de constantes.</span><span class="sxs-lookup"><span data-stu-id="4847f-104">The data in the table can consist of links and constants.</span></span> <span data-ttu-id="4847f-105">Le premier paramètre d’entrée de la **bouclage de Table** fonctoid configure l’étendue, ou combien de fois les enregistrements de boucle.</span><span class="sxs-lookup"><span data-stu-id="4847f-105">The first input parameter to the **Table Looping** functoid configures the scope, or how many times the records will loop.</span></span> <span data-ttu-id="4847f-106">La deuxième entrée de paramètre pour le **bouclage de Table** fonctoid détermine le nombre de colonnes dans la table, et les autres entrées définissent les valeurs de cellule possibles pour la table, dans aucun ordre particulier.</span><span class="sxs-lookup"><span data-stu-id="4847f-106">The second input parameter for the **Table Looping** functoid determines how many columns are in the table, and the remaining inputs define possible cell values for the table, in no particular order.</span></span> <span data-ttu-id="4847f-107">Pour plus d’informations sur l’utilisation de ces propriétés, consultez [Configuration de bouclage Table-Driven](../core/table-driven-looping-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="4847f-107">For more information about working with these properties, see [Table-Driven Looping Configuration](../core/table-driven-looping-configuration.md).</span></span> <span data-ttu-id="4847f-108">Consultez également [exemple de bouclage Table-Driven](../core/table-driven-looping-example.md).</span><span class="sxs-lookup"><span data-stu-id="4847f-108">Also see [Table-Driven Looping Example](../core/table-driven-looping-example.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4847f-109">Le **bouclage de Table** fonctoid est répétée pour qu’il est connecté à l’enregistrement de bouclage.</span><span class="sxs-lookup"><span data-stu-id="4847f-109">The **Table Looping** functoid repeats with the looping record it is connected to.</span></span> <span data-ttu-id="4847f-110">À chaque itération, il effectue une boucle par ligne de la grille de bouclage de table, produisant des boucles de sortie multiples.</span><span class="sxs-lookup"><span data-stu-id="4847f-110">Within each iteration, it loops once per row in the table looping grid, producing multiple output loops.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4847f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4847f-111">See Also</span></span>  
 <span data-ttu-id="4847f-112">[Fonctoid Extracteur de table](../core/table-extractor-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="4847f-112">[Table Extractor Functoid](../core/table-extractor-functoid.md) </span></span>  
 <span data-ttu-id="4847f-113">[L’ajout de bouclage de Table et fonctoids Extracteur de Table à une carte](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="4847f-113">[How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="4847f-114">[Fonctoids avancés](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="4847f-114">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="4847f-115">[Fonctoid Index](../core/index-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="4847f-115">[Index Functoid](../core/index-functoid.md) </span></span>  
 <span data-ttu-id="4847f-116">[Fonctoid Itération](../core/iteration-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="4847f-116">[Iteration Functoid](../core/iteration-functoid.md) </span></span>  
 <span data-ttu-id="4847f-117">[Fonctoid Bouclage](../core/looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="4847f-117">[Looping Functoid](../core/looping-functoid.md) </span></span>  
 [<span data-ttu-id="4847f-118">Fonctoid Nombre d’enregistrements</span><span class="sxs-lookup"><span data-stu-id="4847f-118">Record Count Functoid</span></span>](../core/record-count-functoid.md)
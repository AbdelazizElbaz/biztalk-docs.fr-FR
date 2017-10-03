---
title: Comment afficher des info-bulles | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5621bd0a-7028-43fc-b6e8-74a528129285
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06aba645f94b87e0a7951d9c8264056262a12a13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-infotip-and-tooltip"></a><span data-ttu-id="5f4f7-102">Affichage des info-bulles</span><span class="sxs-lookup"><span data-stu-id="5f4f7-102">How to View Infotip and Tooltip</span></span>
<span data-ttu-id="5f4f7-103">Lorsque vous déplacez le curseur sur un élément de mappage sans cliquer dessus, une info-bulle comportant des informations utiles sur cet élément s'affiche.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-103">When you move the cursor over a map item without clicking it, a screen tip appears with useful information about that item.</span></span>  
  
 <span data-ttu-id="5f4f7-104">Le Mappeur BizTalk utilise deux types d'info-bulles.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-104">The BizTalk Mapper uses two types of screen tips – infotip and tooltip.</span></span>  
  
-   <span data-ttu-id="5f4f7-105">**Info-bulles** sont affichés pour les fonctoids ou des liens.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-105">**Infotips** are displayed for functoids or links.</span></span> <span data-ttu-id="5f4f7-106">Lorsque vous configurez des étiquettes ou des commentaires pour des fonctoids ou des liens, ceux-ci apparaissent dans des info-bulles dans la page de la grille.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-106">When you configure labels or comments for functoids or links, you see them as infotip on the grid page.</span></span> <span data-ttu-id="5f4f7-107">En outre, lorsque la valeur de texte pour les propriétés dépasse l’affichage de la **grille des propriétés**, l’info-bulle s’affiche.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-107">Also, when the text value for properties exceeds the display of the **Properties Grid**, the infotip is displayed.</span></span>  
  
-   <span data-ttu-id="5f4f7-108">**Info-bulles** sont affichées pour les nœuds de schéma partiellement/intégralement masqués à partir de l’alignement actuel dans la vue grille.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-108">**Tooltips** are displayed for those schema nodes that are hidden partially/completely from the current alignment in the grid view.</span></span>  
  
 <span data-ttu-id="5f4f7-109">Pour les étiquettes de lien, seuls les 256 premiers caractères sont conservés. L'info-bulle affiche l'intégralité de l'étiquette.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-109">For link labels, only the first 256 characters are retained, and the tooltip displays the complete label.</span></span> <span data-ttu-id="5f4f7-110">Pour les fonctoids, l'étiquette peut contenir jusqu'à 256 caractères et les commentaires sont limités à 1 024 caractères.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-110">For functoids, the label can contain a maximum of 256 characters and comments have a limit of 1024 characters.</span></span> <span data-ttu-id="5f4f7-111">Le texte des commentaires est tronqué de façon à n'afficher que les 256 premiers caractères du commentaire.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-111">Text of comment gets truncated accordingly to display only first 256 characters of comment.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5f4f7-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="5f4f7-112">Prerequisites</span></span>  
 <span data-ttu-id="5f4f7-113">Pour afficher les info-bulles, vérifiez que le Mappeur BizTalk est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-113">To view the tooltips, ensure BizTalk Mapper is running.</span></span>  
  
## <a name="to-view-the-infotip"></a><span data-ttu-id="5f4f7-114">Pour afficher l'info-bulle</span><span class="sxs-lookup"><span data-stu-id="5f4f7-114">To view the infotip</span></span>  
 <span data-ttu-id="5f4f7-115">Lorsque vous déplacez le curseur sur un fonctoid, l'info-bulle affiche des informations sur le nom, l'étiquette et les commentaires du fonctoid, ainsi que sur les paramètres d'entrée (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="5f4f7-115">When you move the mouse on a functoid, the infotip displays information about the functoid name, the functoid label, the functoid comment, and the input parameters (if existing).</span></span> <span data-ttu-id="5f4f7-116">Pour un **script** fonctoid, l’info-bulle affiche les premières lignes de code.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-116">For a **Scripting** functoid, the infotip displays the first few lines of code.</span></span>  
  
 <span data-ttu-id="5f4f7-117">L'info-bulle d'un lien affiche les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5f4f7-117">The infotip to a link displays the following information:</span></span>  
  
-   <span data-ttu-id="5f4f7-118">étiquette du lien, si celle-ci est définie ;</span><span class="sxs-lookup"><span data-stu-id="5f4f7-118">Link label, if set.</span></span>  
  
-   <span data-ttu-id="5f4f7-119">**À partir de : connexion à la source**.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-119">**From: source connection**.</span></span> <span data-ttu-id="5f4f7-120">Si la connexion source est un élément de schéma, l'info-bulle indique le nom de l'élément.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-120">If the source connection is a schema element, it shows the element name.</span></span> <span data-ttu-id="5f4f7-121">S'il s'agit d'un fonctoid, elle indique le nom du fonctoid ;</span><span class="sxs-lookup"><span data-stu-id="5f4f7-121">If the source connection is a functoid, it shows the functoid name.</span></span>  
  
-   <span data-ttu-id="5f4f7-122">**À : connexion de destination**.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-122">**To: destination connection**.</span></span> <span data-ttu-id="5f4f7-123">Si la connexion de destination est un élément de schéma, l'info-bulle indique le nom de l'élément.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-123">If the destination connection is a schema element, it shows the element name.</span></span> <span data-ttu-id="5f4f7-124">S'il s'agit d'un fonctoid, l'info-bulle indique le nom du fonctoid.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-124">If the destination connection is a functoid, it shows the functoid name.</span></span>  
  
 <span data-ttu-id="5f4f7-125">Si les champs dans le **grille des propriétés** contiennent du texte qui dépasse la zone d’affichage, déplacez la souris sur le champ.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-125">If the fields in the **Properties Grid** have text that exceeds the display, move the mouse on the field.</span></span> <span data-ttu-id="5f4f7-126">L'info-bulle affiche alors l'intégralité du texte.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-126">The infotip will show the full text.</span></span>  
  
 <span data-ttu-id="5f4f7-127">L’illustration suivante montre les info-bulles d’un fonctoid, lien et la **grille des propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-127">The following figure illustrates infotips to a functoid, link, and the **Properties Grid**.</span></span>  
  
 <span data-ttu-id="5f4f7-128">![Info-bulle pour le fonctoid, lien et étiquette](../core/media/viewing-infotips.gif "Viewing_infotips")</span><span class="sxs-lookup"><span data-stu-id="5f4f7-128">![Infotips for functoid, link, and label](../core/media/viewing-infotips.gif "Viewing_infotips")</span></span>  
  
## <a name="to-view-the-tooltip"></a><span data-ttu-id="5f4f7-129">Pour afficher l’info-bulle</span><span class="sxs-lookup"><span data-stu-id="5f4f7-129">To view the tooltip</span></span>  
 <span data-ttu-id="5f4f7-130">Lorsque vos schémas sources et/ou de destination sont trop grands, votre mappage peut s'étendre verticalement. Certains nœuds du schéma peuvent alors être partiellement masqués.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-130">When your source and/or destination schemas are big, your map can span vertically; hence the schema nodes may be partially visible.</span></span> <span data-ttu-id="5f4f7-131">Dans ce cas, vous pouvez afficher des info-bulles en déplaçant le curseur sur ces nœuds.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-131">In such a scenario, you can see tooltips when you move the mouse on those source nodes.</span></span>  
  
 <span data-ttu-id="5f4f7-132">La figure suivante montre l'info-bulle d'un nœud de schéma cible partiellement masqué.</span><span class="sxs-lookup"><span data-stu-id="5f4f7-132">The following figure shows a tooltip to a partially hidden target schema node.</span></span>  
  
 <span data-ttu-id="5f4f7-133">![Info-bulle à un nœud de schéma](../core/media/viewing-tooltips.gif "Viewing_tooltips")</span><span class="sxs-lookup"><span data-stu-id="5f4f7-133">![Tooltip to a schema node](../core/media/viewing-tooltips.gif "Viewing_tooltips")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f4f7-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f4f7-134">See Also</span></span>  
 [<span data-ttu-id="5f4f7-135">À l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="5f4f7-135">Using BizTalk Mapper</span></span>](../core/using-biztalk-mapper.md)
---
title: "Imbriqué enregistrements positionnels | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e205e9d-f740-4177-b45a-5e1baadae99a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c278d3ac794c560d8cd886605c1d04c097793564
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="nested-positional-records"></a><span data-ttu-id="00e0f-102">Enregistrements positionnels imbriqués</span><span class="sxs-lookup"><span data-stu-id="00e0f-102">Nested Positional Records</span></span>
<span data-ttu-id="00e0f-103">Les enregistrements positionnels imbriqués sont autorisés si le **Max Occurs** des enregistrements enfants est définie sur un nombre entier positif.</span><span class="sxs-lookup"><span data-stu-id="00e0f-103">Nested positional records are allowed if the **Max Occurs** property of child records is set to a positive integer.</span></span> <span data-ttu-id="00e0f-104">Le calcul automatique de champ doit être en mesure de gérer la nouvelle profondeur.</span><span class="sxs-lookup"><span data-stu-id="00e0f-104">Field autocalculation should be able to handle the new depth.</span></span> <span data-ttu-id="00e0f-105">Toutefois, son comportement est modifié.</span><span class="sxs-lookup"><span data-stu-id="00e0f-105">However, there is a modification to the way this behaves.</span></span> <span data-ttu-id="00e0f-106">Concrètement, en raison de la possibilité d’appliquer des délimiteurs NULL, le calcul automatique des positions de champ ne fonctionne que si l'une des conditions suivantes est remplie :</span><span class="sxs-lookup"><span data-stu-id="00e0f-106">Specifically, because of the possibility for null delimiters, autocalculation of field positions will function only if one of the following conditions is met:</span></span>  
  
-   <span data-ttu-id="00e0f-107">Le nœud sélectionné possède un parent qui est délimité par un infix.</span><span class="sxs-lookup"><span data-stu-id="00e0f-107">The selected node has a parent that is infix delimited.</span></span>  
  
-   <span data-ttu-id="00e0f-108">Le nœud sélectionné possède une position de départ spécifiée.</span><span class="sxs-lookup"><span data-stu-id="00e0f-108">The selected node has a specified starting position.</span></span>  
  
 <span data-ttu-id="00e0f-109">Notez qu'il existe une distinction entre les enregistrements positionnels imbriqués et les enregistrements positionnels dont le parent est un conteneur délimité pour lequel le délimiteur est null.</span><span class="sxs-lookup"><span data-stu-id="00e0f-109">Note that there is a distinction between nested positional records and positional records whose parent is a delimited container where the delimiter is null.</span></span> <span data-ttu-id="00e0f-110">Pour que les structures soient réellement positionnées de façon imbriquée, il ne doit subsister aucune ambiguïté en ce qui concerne leur longueur.</span><span class="sxs-lookup"><span data-stu-id="00e0f-110">For structures to be truly nested positionally, there must not be any ambiguity in determining their length.</span></span> <span data-ttu-id="00e0f-111">Par exemple, un nœud de boucle délimité peut contenir un enregistrement positionnel à répétition se produisant entre 0 et N fois.</span><span class="sxs-lookup"><span data-stu-id="00e0f-111">For example, a delimited loop node can contain a repeating positional record that occurs 0 to N times.</span></span> <span data-ttu-id="00e0f-112">Toutefois, pour que le nœud de boucle lui même soit positionnel, et contienne éventuellement aussi des champs en tant qu'homologues de l'enregistrement positionnel à répétition, l'occurrence de l'enregistrement positionnel à répétition doit être déterministe (un entier positif).</span><span class="sxs-lookup"><span data-stu-id="00e0f-112">However, for that loop node itself to be positional, and possibly also contain fields as peers to the repeating positional record, the occurrence of the repeating positional record must be deterministic (a positive integer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00e0f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00e0f-113">See Also</span></span>  
 [<span data-ttu-id="00e0f-114">Considérations concernant les enregistrements positionnels</span><span class="sxs-lookup"><span data-stu-id="00e0f-114">Positional Record Considerations</span></span>](../core/positional-record-considerations.md)
---
title: Calcul de la Position de champ | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e315f09-f2c9-49cc-8d2f-0f4f2d48fd45
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55c58f532ea64300518667d677d2248f5c1c2b6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="field-position-calculation"></a><span data-ttu-id="15192-102">Calcul de Position de champ</span><span class="sxs-lookup"><span data-stu-id="15192-102">Field Position Calculation</span></span>

## <a name="overview"></a><span data-ttu-id="15192-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="15192-103">Overview</span></span>
<span data-ttu-id="15192-104">Lorsque vous utilisez la **longueur positionnelle** et **décalage de position** propriétés de la **élément de champ** et **attribut de champ** nœuds dans votre schéma pour définir la disposition des enregistrements positionnels dans votre message de fichier plat, le **Position de début** et **longueur** les colonnes de la **fichier plat** onglet L’Éditeur BizTalk affiche les positions de départ calculées et les longueurs, respectivement, des enregistrements et champs appropriés.</span><span class="sxs-lookup"><span data-stu-id="15192-104">When you use the **Positional Length** and **Positional Offset** properties of the **Field Element** and **Field Attribute** nodes in your schema to define the layout of the positional records in your flat file message, the **Start Position** and **Length** columns of the **Flat File** tab in BizTalk Editor show the calculated starting positions and lengths, respectively, of the relevant fields and records.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15192-105">Le **fichier plat** onglet apparaît sous la forme d’une autre vue à onglets avec la vue XSD dans l’Éditeur BizTalk vous avez configuré l’extension de fichier plat à l’aide de la **Extensions de l’éditeur de schéma** propriété de la **Schéma** nœud.</span><span class="sxs-lookup"><span data-stu-id="15192-105">The **Flat File** tab appear as an alternate tabbed view with the XSD view in BizTalk Editor when you have configured the flat file extension using the **Schema Editor Extensions** property of the **Schema** node.</span></span> <span data-ttu-id="15192-106">Plus de détails sur cette propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="15192-106">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="15192-107">En général, la position de départ d’un champ particulier *N* est la position de départ du champ précédent, plus la longueur de champ précédent, plus le décalage (positionnel) que vous avez spécifié pour le champ *N*.</span><span class="sxs-lookup"><span data-stu-id="15192-107">In general, the starting position of a particular field *N* is the starting position of the previous field, plus the length of the previous field, plus the (positional) offset you have specified for field *N*.</span></span>  
  
 <span data-ttu-id="15192-108">Dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], tous les calculs de position des champs sont effectués automatiquement, immédiatement, sans qu'il faille exécuter une commande (comme c'était le cas dans les précédentes versions de BizTalk Server).</span><span class="sxs-lookup"><span data-stu-id="15192-108">All field position calculation in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is performed automatically, on-the-fly, without any need to execute a command (as was required in previous versions of BizTalk Server).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15192-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15192-109">See Also</span></span>  
-  [<span data-ttu-id="15192-110">Considérations concernant les enregistrements positionnels</span><span class="sxs-lookup"><span data-stu-id="15192-110">Positional Record Considerations</span></span>](../core/positional-record-considerations.md)   
-  <span data-ttu-id="15192-111">**Longueur positionnelle (propriété de nœud des schémas de fichier plat)** et **le décalage de position (propriété de nœud des schémas de fichier plat)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="15192-111">**Positional Length (Node Property of Flat File Schemas)** and **Positional Offset (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
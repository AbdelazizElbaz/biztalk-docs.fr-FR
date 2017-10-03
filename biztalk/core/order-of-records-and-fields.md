---
title: Ordre des enregistrements et champs | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Mapper, sorting
- XSLT, sorting
ms.assetid: 7fa9b5cd-73bc-496f-a081-4a45da3afe42
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5826d46fef73400a5d54e2d1154a1647af85294e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="order-of-records-and-fields"></a><span data-ttu-id="c4c82-102">Ordre des enregistrements et des champs</span><span class="sxs-lookup"><span data-stu-id="c4c82-102">Order of Records and Fields</span></span>
<span data-ttu-id="c4c82-103">Le langage de transformation de feuille de style extensible (XSLT) tel qu'il est utilisé par le Mappeur BizTalk ne garantit pas l'ordre de sortie des éléments et attributs de sortie.</span><span class="sxs-lookup"><span data-stu-id="c4c82-103">Extensible Stylesheet Language Transformations (XSLT), as used by BizTalk Mapper, do not guarantee the output order of output elements and attributes.</span></span> <span data-ttu-id="c4c82-104">En effet, le Mappeur BizTalk génère XSLT en examinant la structure de schéma de destination, puis procède à la propagation des éléments en revenant dans les pages de grille afin d'extraire les valeurs de la structure de schéma source.</span><span class="sxs-lookup"><span data-stu-id="c4c82-104">This is because BizTalk Mapper generates XSLT by examining the destination schema structure, and then propagating elements back through the grid pages to extract values from the source schema structure.</span></span> <span data-ttu-id="c4c82-105">Par exemple, si vous souhaitez créer un fichier de sortie dont l'enregistrement BillTo Address est répertorié avant l'enregistrement ShipTo Address, vous devez vous assurer que BillTo Address précède ShipTo Address dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="c4c82-105">For example, if you want to create an output file that has the BillTo Address record listed before the ShipTo Address record, you must ensure that the BillTo Address precedes the ShipTo Address record in the destination schema.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c4c82-106">L'ordre dans lequel les éléments et les attributs apparaissent dans un message d'instance de sortie dépend de l'ordre des enregistrements et des champs du schéma de destination correspondant.</span><span class="sxs-lookup"><span data-stu-id="c4c82-106">The order in which elements and attributes appear in an output instance message depends on the order of the records and fields of the corresponding destination schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c82-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4c82-107">See Also</span></span>  
 <span data-ttu-id="c4c82-108">[Mappages](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="c4c82-108">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="c4c82-109">Création de mappages à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="c4c82-109">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)
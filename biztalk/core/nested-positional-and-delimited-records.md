---
title: "Imbriqué enregistrements positionnels et délimités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1688f04-d3c7-492c-82f7-a734bec0e409
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccc3d994a3561f26df1bdffa7b547b1f647936a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="nested-positional-and-delimited-records"></a><span data-ttu-id="3a7e8-102">Enregistrements positionnels et délimités imbriqués</span><span class="sxs-lookup"><span data-stu-id="3a7e8-102">Nested Positional and Delimited Records</span></span>
<span data-ttu-id="3a7e8-103">Dans les formats de fichier plat pris en charge par Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], certaines combinaisons d'enregistrements positionnels et délimités sont autorisées et d'autres non.</span><span class="sxs-lookup"><span data-stu-id="3a7e8-103">In the flat file formats supported by Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], some combinations of positional and delimited records are allowed and others are disallowed.</span></span> <span data-ttu-id="3a7e8-104">Les combinaisons suivantes sont autorisées :</span><span class="sxs-lookup"><span data-stu-id="3a7e8-104">The following combinations are allowed:</span></span>  
  
-   <span data-ttu-id="3a7e8-105">Les fichiers plats dans lesquels des délimiteurs sont utilisés pour déterminer les limites entre tous les enregistrements et leurs enregistrements subordonnés entre eux, et dans lesquels des délimiteurs (éventuellement différents) sont utilisés pour séparer les champs de ces enregistrements.</span><span class="sxs-lookup"><span data-stu-id="3a7e8-105">Flat files in which delimiters are used to determine the boundaries between all records and their subordinate records from each other, and in which (possibly different) delimiters are used to separate the fields within those records.</span></span>  
  
-   <span data-ttu-id="3a7e8-106">Les fichiers plats dans lesquels les limites entre tous les enregistrements, leurs enregistrements subordonnés et leurs champs sont déterminées sur la base de leur position dans le fichier, selon des longueurs d'enregistrement et de champ prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="3a7e8-106">Flat files in which the boundaries between all records, their subordinate records, and their fields are determined based on their position within the file according to predefined record and field lengths.</span></span>  
  
-   <span data-ttu-id="3a7e8-107">Les fichiers plats dans lesquels des délimiteurs sont utilisés pour déterminer les limites entre au moins l'ensemble d'enregistrements le plus externe dans le fichier, et dans lesquels une combinaison d'enregistrements subordonnés délimités et positionnels est utilisée.</span><span class="sxs-lookup"><span data-stu-id="3a7e8-107">Flat files in which delimiters are used to determine the boundaries between at least the outermost set of records in the file, and in which a mix of delimited and positional subordinate records are used.</span></span> <span data-ttu-id="3a7e8-108">Les limites entre les champs d'un enregistrement subordonné délimité ou positionnel sont déterminées en utilisant des délimiteurs ou des longueurs de champ fixes respectivement.</span><span class="sxs-lookup"><span data-stu-id="3a7e8-108">Boundaries between the fields within a delimited or positional subordinate record are determined using either delimiters or fixed field lengths, respectively.</span></span> <span data-ttu-id="3a7e8-109">Les enregistrements subordonnés d'un enregistrement (subordonné) positionnel doivent également être positionnels. En d'autres termes, une fois qu'une partie du fichier passe d'enregistrements délimités à des enregistrements positionnels, l'ensemble de cette partie subordonnée du fichier doit être positionnelle.</span><span class="sxs-lookup"><span data-stu-id="3a7e8-109">The subordinate records of a positional (subordinate) record must also be positional; in other words, once a portion of the file switches from delimited to positional records, that entire subordinate portion of the file must be positional.</span></span>  
  
 <span data-ttu-id="3a7e8-110">En raison des ambiguïtés d'analyse qui pourraient en résulter, les enregistrements positionnels, où qu'ils aient lieu, ne doivent en aucune façon contenir des enregistrements subordonnés délimités.</span><span class="sxs-lookup"><span data-stu-id="3a7e8-110">Due to the parsing ambiguities that would result, positional records, wherever they occur, are prohibited from containing delimited subordinate records.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a7e8-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a7e8-111">See Also</span></span>  
 [<span data-ttu-id="3a7e8-112">Considérations relatives à la création de plat fichier schémas de Message</span><span class="sxs-lookup"><span data-stu-id="3a7e8-112">Considerations When Creating Flat File Message Schemas</span></span>](../core/considerations-when-creating-flat-file-message-schemas.md)
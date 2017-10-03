---
title: "Étiquette de la gestion des enregistrements délimités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 568eb804-bea5-46d4-8547-8bc30b87156c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5be9d28e3de6b1a7613db8d0c5ac7365a298a679
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tag-handling-in-delimited-records"></a><span data-ttu-id="ffa7e-102">Gestion des balises dans les enregistrements délimités</span><span class="sxs-lookup"><span data-stu-id="ffa7e-102">Tag Handling in Delimited Records</span></span>

## <a name="overview"></a><span data-ttu-id="ffa7e-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="ffa7e-103">Overview</span></span>
<span data-ttu-id="ffa7e-104">Les enregistrements délimités peuvent inclure une séquence connue de caractères, appelée balise, qui peut être utilisée pour lever l'ambiguïté entre les types d'enregistrements.</span><span class="sxs-lookup"><span data-stu-id="ffa7e-104">Delimited records can include a well-known sequence of characters, known as a tag, which can be used to disambiguate one type of record from another.</span></span> <span data-ttu-id="ffa7e-105">Ainsi, le désassembleur de fichier plat identifier correctement les **enregistrement** nœud dans le schéma qui contient les informations requises pour analyser correctement l’enregistrement de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="ffa7e-105">This will allow the flat file disassembler to properly identify the appropriate **Record** node in the schema that contains the information required to correctly parse the flat file record.</span></span>  
  
 <span data-ttu-id="ffa7e-106">Vous pouvez utiliser la **identificateur de balise** propriété pour spécifier la balise dans un enregistrement délimité.</span><span class="sxs-lookup"><span data-stu-id="ffa7e-106">You can use the **Tag Identifier** property to specify the tag within a delimited record.</span></span> <span data-ttu-id="ffa7e-107">Contrairement aux balises des enregistrements positionnels, les balises des enregistrements délimités doivent intervenir au début de l'enregistrement et, automatiquement, ne sont jamais incluses dans les données lorsque l'enregistrement est converti dans son format XML équivalent.</span><span class="sxs-lookup"><span data-stu-id="ffa7e-107">Unlike tags in positional records, tags in delimited records must occur at the beginning of the delimited record and are automatically never included in the data when the record is translated to its equivalent XML format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa7e-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffa7e-108">See Also</span></span>  
-  [<span data-ttu-id="ffa7e-109">Considérations concernant les enregistrements délimités</span><span class="sxs-lookup"><span data-stu-id="ffa7e-109">Delimited Record Considerations</span></span>](../core/delimited-record-considerations.md)   
-  <span data-ttu-id="ffa7e-110">**Identificateur (propriété de nœud des schémas de fichier plat) de balise**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="ffa7e-110">**Tag Identifier (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
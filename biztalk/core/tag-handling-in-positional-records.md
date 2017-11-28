---
title: La balise de la gestion des enregistrements positionnels | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c85d695-6dc9-4200-a453-dc576832adca
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 804647b3cf43b9b6747b2e5f50e05e38313b03d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tag-handling-in-positional-records"></a><span data-ttu-id="98f83-102">Gestion des balises dans les enregistrements positionnels</span><span class="sxs-lookup"><span data-stu-id="98f83-102">Tag Handling in Positional Records</span></span>

## <a name="overview"></a><span data-ttu-id="98f83-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="98f83-103">Overview</span></span>
<span data-ttu-id="98f83-104">Les enregistrements positionnels peuvent inclure une séquence connue de caractères, appelée balise, qui peut être utilisée pour lever l'ambiguïté entre les types d'enregistrements.</span><span class="sxs-lookup"><span data-stu-id="98f83-104">Positional records can include a well-known sequence of characters, known as a tag, which can be used to disambiguate one type of record from another.</span></span> <span data-ttu-id="98f83-105">Ainsi, le désassembleur de fichier plat identifier correctement les **enregistrement** nœud dans le schéma qui contient les informations requises pour analyser correctement l’enregistrement de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="98f83-105">This allows the flat file disassembler to properly identify the appropriate **Record** node in the schema that contains the information required to correctly parse the flat file record.</span></span>  
  
 <span data-ttu-id="98f83-106">Vous pouvez utiliser la **[identificateur de balise** et **décalage de la balise** propriétés pour spécifier la balise et sa position dans un enregistrement positionnel.</span><span class="sxs-lookup"><span data-stu-id="98f83-106">You can use the **[Tag Identifier** and **Tag Offset** properties together to specify the tag and its position within a positional record.</span></span> <span data-ttu-id="98f83-107">Notez que cela permet la balise se produise n’importe où dans l’enregistrement positionnel et qui, selon vos paramètres pour le **longueur positionnelle** et **décalage de position** propriétés des champs différents dans l’enregistrement, l’étiquette peut être interprétée comme faisant partie des données associées à un ou plusieurs de ces champs.</span><span class="sxs-lookup"><span data-stu-id="98f83-107">Note that this allows the tag to occur anywhere within the positional record and that depending on your settings for the **Positional Length** and **Positional Offset** properties of the various fields within the record, the tag can be interpreted as part of data associated with one or more of these fields.</span></span>  
  
 <span data-ttu-id="98f83-108">Le **décalage de position** propriété vous permet également de traiter la balise séparément à partir des données dans l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="98f83-108">The **Positional Offset** property also allows you to treat the tag separately from the data in the record.</span></span> <span data-ttu-id="98f83-109">Par exemple, si la balise se produit au début de l’enregistrement et quatre caractères, vous pouvez définir la valeur de la **décalage de position** propriété du premier champ dans l’enregistrement de quatre, ignorant ainsi efficacement ignorant la balise d’enregistrement positionnel lorsque la valeur du premier champ est convertie au format XML équivalent de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="98f83-109">For example, if the tag occurs at the beginning of the record and is four characters in length, you could set the value of the **Positional Offset** property of the first field in the record to four, thereby effectively skipping over the positional record tag when the value of the first field is translated in the equivalent XML format of the record.</span></span>  

<span data-ttu-id="98f83-110">Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="98f83-110">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="98f83-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98f83-111">See Also</span></span>  
 [<span data-ttu-id="98f83-112">Considérations concernant les enregistrements positionnels</span><span class="sxs-lookup"><span data-stu-id="98f83-112">Positional Record Considerations</span></span>](../core/positional-record-considerations.md)   

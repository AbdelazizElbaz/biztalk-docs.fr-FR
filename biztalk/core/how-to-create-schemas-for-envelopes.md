---
title: "Comment créer des schémas pour les enveloppes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae1c991c-447f-497e-803c-1cb8cad2846b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7308a093f9f95ce2342f268554deb67193aea053
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-schemas-for-envelopes"></a><span data-ttu-id="6cf29-102">Créer des schémas pour les enveloppes</span><span class="sxs-lookup"><span data-stu-id="6cf29-102">Create Schemas for Envelopes</span></span>

## <a name="overview"></a><span data-ttu-id="6cf29-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="6cf29-103">Overview</span></span>
<span data-ttu-id="6cf29-104">Après avoir créé un schéma de message XML, comme décrit dans [création de schémas pour les Messages XML](../core/how-to-create-schemas-for-xml-messages.md), définissez le **enveloppe** propriété de la **schéma** nœud **Oui**.</span><span class="sxs-lookup"><span data-stu-id="6cf29-104">After creating an XML message schema as described in [Creating Schemas for XML Messages](../core/how-to-create-schemas-for-xml-messages.md), set the **Envelope** property of the **Schema** node to **Yes**.</span></span> <span data-ttu-id="6cf29-105">En fonction de certaines caractéristiques de votre schéma d'enveloppe, par exemple selon qu'il y a plusieurs nœuds racine, vous devrez définir plusieurs autres propriétés propres aux enveloppes.</span><span class="sxs-lookup"><span data-stu-id="6cf29-105">Depending on certain characteristics of your envelope schema, such as whether there are multiple root nodes, you will need to set several other envelope-specific properties.</span></span> <span data-ttu-id="6cf29-106">Pour plus d’informations, consultez [schémas d’enveloppe](../core/envelope-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="6cf29-106">For more information, see [Envelope Schemas](../core/envelope-schemas.md).</span></span>  
  
 <span data-ttu-id="6cf29-107">La propriété XPath de corps de l'enveloppe pointe sur l'élément qui contient les éléments de document.</span><span class="sxs-lookup"><span data-stu-id="6cf29-107">The body XPath property of the envelope points to the element that contains the document elements.</span></span> <span data-ttu-id="6cf29-108">L'élément réel vers lequel XPath pointe n'appartient pas au document.</span><span class="sxs-lookup"><span data-stu-id="6cf29-108">The actual element where the XPath points to does not belong to the document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cf29-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cf29-109">See Also</span></span>  
-  [<span data-ttu-id="6cf29-110">Gestion des schémas dans des projets</span><span class="sxs-lookup"><span data-stu-id="6cf29-110">Managing Schemas Within Projects</span></span>](../core/managing-schemas-within-projects.md)
-  <span data-ttu-id="6cf29-111">**Enveloppe** propriété[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="6cf29-111">**Envelope** property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
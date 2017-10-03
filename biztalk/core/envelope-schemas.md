---
title: "Les schémas d’enveloppe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af296c30-95dc-4fef-9aa3-bea2f2cd8caf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03c44f1a5d9797ec09cc164789148287c98b4399
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="envelope-schemas"></a><span data-ttu-id="0775b-102">Schémas d’enveloppe</span><span class="sxs-lookup"><span data-stu-id="0775b-102">Envelope Schemas</span></span>

## <a name="overview"></a><span data-ttu-id="0775b-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="0775b-103">Overview</span></span>
<span data-ttu-id="0775b-104">Vous pouvez créer un schéma d'enveloppe de la même façon que vous pouvez créer un schéma XML pour un document commercial.</span><span class="sxs-lookup"><span data-stu-id="0775b-104">You can create an envelope schema in all of the same ways that you can create an XML schema for a business document.</span></span> <span data-ttu-id="0775b-105">Vous pouvez créer un schéma à partir d'un message d'instance d'enveloppe XML bien formé ou à partir de représentations de définition de type de document (DTD) ou XDR (XML-Data Reduced) du schéma d'enveloppe.</span><span class="sxs-lookup"><span data-stu-id="0775b-105">You can create a schema from a well-formed XML envelope instance message, or from Document Type Definition (DTD) or XML-Data reduced (XDR) representations of the envelope schema.</span></span> <span data-ttu-id="0775b-106">Vous pouvez également créer un schéma en association ou non avec d'autres schémas.</span><span class="sxs-lookup"><span data-stu-id="0775b-106">Or, you can create a new schema, either in conjunction with other schemas or not.</span></span> <span data-ttu-id="0775b-107">Les schémas d'enveloppe étant généralement beaucoup plus petits et moins compliqués que la plupart des schémas de document commercial, la création de schémas d'enveloppe est une alternative viable dans la majorité des cas.</span><span class="sxs-lookup"><span data-stu-id="0775b-107">Because envelope schemas are generally much smaller and less complicated than most business document schemas, creating new envelope schemas is usually a viable alternative.</span></span>  
  
 <span data-ttu-id="0775b-108">Pour définir un schéma en tant qu’un schéma d’enveloppe, vous devez définir le **enveloppe** propriété de la **schéma** nœud à la valeur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="0775b-108">To define a schema as an envelope schema, you need to set the **Envelope** property of the **Schema** node to the value **Yes**.</span></span> <span data-ttu-id="0775b-109">Lorsque vous définissez un schéma d’enveloppe, vous devez faire de l’enveloppe **XPath de corps** au nœud parent qui contient uniquement le \<tout > élément enfant.</span><span class="sxs-lookup"><span data-stu-id="0775b-109">When you define an envelope schema, you should point the envelope's **Body XPath** to the parent node that contains only the \<any> child element.</span></span> <span data-ttu-id="0775b-110">Pour que l'assembleur XML utilise l'enveloppe, le nœud parent ne doit pas contenir d'autres éléments.</span><span class="sxs-lookup"><span data-stu-id="0775b-110">In order for the XML assembler to use the envelope, the parent node must not contain any other elements.</span></span>  
  
 <span data-ttu-id="0775b-111">Lorsque vous définissez **enveloppe** propriété **Oui**, cela signifie que le contenu réel du message d’instance XML (appelé corps du message) est présent à l’intérieur de la racine **enregistrement**  nœud de ce schéma, tel que spécifié par le **XPath de corps** propriété de ce nœud.</span><span class="sxs-lookup"><span data-stu-id="0775b-111">When you set **Envelope** property to **Yes**, it means that the actual message content of the XML instance message (called the body of the message) is present somewhere inside the root **Record** node of this schema, as specified by the **Body XPath** property of that node.</span></span> <span data-ttu-id="0775b-112">Par conséquent, vous devez également définir des propriétés supplémentaires sur la base de diverses conditions :</span><span class="sxs-lookup"><span data-stu-id="0775b-112">Therefore, you must also set additional properties based on a variety of conditions:</span></span>  
  
-   <span data-ttu-id="0775b-113">Si un schéma d’enveloppe a une racine unique, vous devez définir le **XPath de corps** propriété pour cette racine.</span><span class="sxs-lookup"><span data-stu-id="0775b-113">If an envelope schema has a single root, you must set the **Body XPath** property for that root.</span></span>  
  
-   <span data-ttu-id="0775b-114">Si un schéma d’enveloppe a plusieurs racines et **référence de racine** propriété n’est pas définie, vous devez définir le **XPath de corps** propriété pour toutes les racines.</span><span class="sxs-lookup"><span data-stu-id="0775b-114">If an envelope schema has multiple roots and the **Root Reference** property is not set, you must set the **Body XPath** property for all roots.</span></span>  
  
-   <span data-ttu-id="0775b-115">Si un schéma d’enveloppe a plusieurs racines et **référence de racine** est définie, vous devez définir le **XPath de corps** propriété de la racine correspondante **enregistrement** nœud.</span><span class="sxs-lookup"><span data-stu-id="0775b-115">If an envelope schema has multiple roots and the **Root Reference** property is set, you must set the **Body XPath** property of the corresponding root **Record** node.</span></span> <span data-ttu-id="0775b-116">Vous pouvez éventuellement définir le **XPath de corps** propriété pour les racines restantes.</span><span class="sxs-lookup"><span data-stu-id="0775b-116">You can optionally set the **Body XPath** property for the remaining roots.</span></span>  
  
-   <span data-ttu-id="0775b-117">Qu’un schéma d’enveloppe possède une ou plusieurs racines, en définissant le **[référence de racine** propriété n’est pas requise.</span><span class="sxs-lookup"><span data-stu-id="0775b-117">Regardless of whether an envelope schema has a single root or multiple roots, setting the **[Root Reference** property is not required.</span></span>  

<span data-ttu-id="0775b-118">Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="0775b-118">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0775b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0775b-119">See Also</span></span>  
 <span data-ttu-id="0775b-120">[Différents Types de schémas BizTalk](../core/different-types-of-biztalk-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="0775b-120">[Different Types of BizTalk Schemas](../core/different-types-of-biztalk-schemas.md) </span></span>  
 [<span data-ttu-id="0775b-121">Comment créer des schémas pour les enveloppes</span><span class="sxs-lookup"><span data-stu-id="0775b-121">How to Create Schemas for Envelopes</span></span>](../core/how-to-create-schemas-for-envelopes.md)
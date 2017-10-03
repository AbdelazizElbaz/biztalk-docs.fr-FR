---
title: "Schémas source et Destination | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- destination schemas
- source schemas, maps
- XML schemas, defining
- destination schemas, about destination schemas
- schemas, destination
- destination schemas, maps
- maps, source schemas
- schemas, Root Reference property
- Root Reference property, modifying
- source schemas
- modifying, Root Reference property
- maps, Root Reference property
- source schemas, about source schemas
- schemas, maps
- maps, schema requirements
- schemas, requirements
- schemas, source schemas
- maps, destination schemas
- Root Reference property
ms.assetid: 8c805854-9fa1-4ce3-938d-a2e61ba17fa1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d82fb8445260b505fbd04b648c251b99fe896dcd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="source-and-destination-schemas"></a><span data-ttu-id="81a43-102">Schémas source et de destination</span><span class="sxs-lookup"><span data-stu-id="81a43-102">Source and Destination Schemas</span></span>
<span data-ttu-id="81a43-103">Chaque mappage BizTalk utilise deux schémas : un schéma source et un schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="81a43-103">Each BizTalk map uses two schemas: a source schema and a destination schema.</span></span> <span data-ttu-id="81a43-104">Le schéma source définit la structure des messages d'instance desquels vous prélevez des données.</span><span class="sxs-lookup"><span data-stu-id="81a43-104">A source schema defines the structure of the instance messages from which you are taking data.</span></span> <span data-ttu-id="81a43-105">Le schéma de destination définit la structure des messages d'instance que le mappage produit.</span><span class="sxs-lookup"><span data-stu-id="81a43-105">The destination schema defines the structure of the instance messages the map produces.</span></span> <span data-ttu-id="81a43-106">Par exemple, si vous souhaitez mapper les informations d'expédition et de facturation d'un bon de commande avec une facture, il vous faut un schéma pour définir des bons de commande pour le schéma source, et un schéma définissant les factures pour le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="81a43-106">For example, if you want to map the shipping and billing information from a purchase order to an invoice, you need a schema to define purchase orders for the source schema and a schema defining invoices for the destination schema.</span></span>  
  
 <span data-ttu-id="81a43-107">Les schémas utilisés dans les mappages BizTalk doivent satisfaire aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="81a43-107">Schemas used in BizTalk maps must meet the following conditions:</span></span>  
  
-   <span data-ttu-id="81a43-108">Les schémas source et de destination doivent faire partie de votre projet BizTalk en cours, ou vous devez inclure une référence aux schémas dans l'assembly de manière à ce qu'ils soient accessibles pendant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="81a43-108">The source and destination schemas need to be a part of your current BizTalk project, or you must include a reference to the schemas in the assembly so that the schemas can be accessed during run time.</span></span>  
  
-   <span data-ttu-id="81a43-109">Les schémas utilisés dans le Mappeur BizTalk doivent être basés sur le langage XSD (XML Schema Definition).</span><span class="sxs-lookup"><span data-stu-id="81a43-109">The schemas used in BizTalk Mapper must be based on the XML Schema definition (XSD) language.</span></span> <span data-ttu-id="81a43-110">L'Éditeur BizTalk constitue un moyen aisé de créer ce genre de schémas.</span><span class="sxs-lookup"><span data-stu-id="81a43-110">BizTalk Editor provides an easy way to create such schemas.</span></span> <span data-ttu-id="81a43-111">Pour plus d’informations sur la création de schémas avec l’Éditeur BizTalk, consultez [création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md).</span><span class="sxs-lookup"><span data-stu-id="81a43-111">For more information about creating schemas with BizTalk Editor, see [Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md).</span></span> <span data-ttu-id="81a43-112">Consultez également [création de schémas](../core/creating-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="81a43-112">Also see [Creating Schemas](../core/creating-schemas.md).</span></span>  
  
 <span data-ttu-id="81a43-113">Dans l'Éditeur BizTalk, vous pouvez créer des schémas avec plusieurs nœuds racine.</span><span class="sxs-lookup"><span data-stu-id="81a43-113">In BizTalk Editor, you can create schemas with multiple root nodes.</span></span> <span data-ttu-id="81a43-114">Mais si vous utilisez un schéma avec plusieurs nœuds racine dans un mappage BizTalk, vous devez choisir quel nœud racine (et la sous-structure correspondante) utiliser dans ce dernier.</span><span class="sxs-lookup"><span data-stu-id="81a43-114">However, if you use a schema with multiple root nodes in a BizTalk map, you must choose which root node (and corresponding substructure) to use in the map.</span></span> <span data-ttu-id="81a43-115">Schémas ont un **référence de racine** propriété qui identifie la racine est le principale.</span><span class="sxs-lookup"><span data-stu-id="81a43-115">Schemas have a **Root Reference** property identifying which root is primary.</span></span> <span data-ttu-id="81a43-116">Si un schéma a plusieurs racines et **référence de racine** propriété est définie lorsque le schéma de la première ouverture correspond à la source ou le schéma de destination, le Mappeur BizTalk utilise la racine spécifiée.</span><span class="sxs-lookup"><span data-stu-id="81a43-116">If a schema has multiple roots and the **Root Reference** property is set when the schema is first opened as the source or destination schema, BizTalk Mapper uses the specified root.</span></span> <span data-ttu-id="81a43-117">Si un schéma a plusieurs racines et **référence de racine** propriété n’est pas définie, le Mappeur BizTalk vous invite à choisir une racine.</span><span class="sxs-lookup"><span data-stu-id="81a43-117">If a schema has multiple roots and the **Root Reference** property is not set, BizTalk Mapper prompts you to choose a root.</span></span>  
  
 <span data-ttu-id="81a43-118">Si vous modifiez le **référence de racine** ne tient pas compte de la modification de propriété d’un schéma déjà utilisé dans un mappage, le Mappeur BizTalk et continue d’utiliser la racine initialement spécifiée.</span><span class="sxs-lookup"><span data-stu-id="81a43-118">If you change the **Root Reference** property of a schema already used in a map, BizTalk Mapper does not notice the change and continues to use the originally specified root.</span></span> <span data-ttu-id="81a43-119">Si vous souhaitez créer divers mappages à l’aide de différentes racines d’un même schéma, il est préférable de ne pas définir le **référence de racine** propriété.</span><span class="sxs-lookup"><span data-stu-id="81a43-119">If you want to build different maps using different roots of the same schema, it is best not to set the **Root Reference** property.</span></span> <span data-ttu-id="81a43-120">Ainsi, dès que le schéma est utilisé dans un nouveau mappage, vous devez explicitement choisir la racine.</span><span class="sxs-lookup"><span data-stu-id="81a43-120">That way, whenever the schema is used for a new map, you must explicitly choose the root.</span></span>  
  
 <span data-ttu-id="81a43-121">Modifier un schéma après l'avoir inclus dans un mappage peut entraîner la rupture de liens à l'intérieur de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="81a43-121">If you edit a schema after it is included in a map, the links within the map may break.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a43-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81a43-122">See Also</span></span>  
 <span data-ttu-id="81a43-123">[Mappages](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="81a43-123">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="81a43-124">Création de mappages à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="81a43-124">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)
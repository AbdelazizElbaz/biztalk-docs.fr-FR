---
title: "Nœuds racines | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2161f877-835e-434d-a8d1-2426f977d60e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2070982a6bca09e8bffb2bcc88e5997360c86851
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="root-nodes"></a><span data-ttu-id="25119-102">Nœuds racine</span><span class="sxs-lookup"><span data-stu-id="25119-102">Root Nodes</span></span>
<span data-ttu-id="25119-103">Dans l’Éditeur BizTalk, les nœuds enfants de la **schéma** nœud sont appelés **racine** nœuds.</span><span class="sxs-lookup"><span data-stu-id="25119-103">In BizTalk Editor, child nodes of the **Schema** node are known as **Root** nodes.</span></span> <span data-ttu-id="25119-104">**Racine** nœuds sont un type spécial de **enregistrement** nœud, et avoir quelques propriétés supplémentaires que regular **enregistrement** nœuds.</span><span class="sxs-lookup"><span data-stu-id="25119-104">**Root** nodes are a special type of **Record** node, and have a few more properties than regular **Record** nodes.</span></span> <span data-ttu-id="25119-105">Le **racine** nœud représente le type de document décrit par le schéma et peut être renommé selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="25119-105">The **Root** node represents the type of document described by the schema, and can be renamed as appropriate.</span></span> <span data-ttu-id="25119-106">Par exemple, vous pouvez renommer la **racine** nœud afin qu’il décrive le type de message que le schéma représente, tel que purchaseOrder, orderAcknowledgment ou shipNotice.</span><span class="sxs-lookup"><span data-stu-id="25119-106">For example, you can rename the **Root** node so that it describes the type of message that the schema represents, such as purchaseOrder, orderAcknowledgment, or shipNotice.</span></span>  
  
 <span data-ttu-id="25119-107">Lorsque vous créez un schéma XML dans l’Éditeur BizTalk, le **schéma** nœud et l’autre **racine** nœud sont créées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="25119-107">When you create a new XML schema in BizTalk Editor, the **Schema** node and one **Root** node are created automatically.</span></span> <span data-ttu-id="25119-108">Vous pouvez créer d’autres **racine** nœuds en tant qu’enfants de le **schéma** nœud ; cela vous permet de créer une bibliothèque de schémas dans une représentation de langage XML Schema definition (XSD) unique.</span><span class="sxs-lookup"><span data-stu-id="25119-108">You can create additional **Root** nodes as children of the **Schema** node; this enables you to create a library of schemas within a single XML Schema definition (XSD) language representation.</span></span> <span data-ttu-id="25119-109">Vous pouvez par exemple créer une bibliothèque de schémas pour décrire les différents schémas de messages connexes pour envoyer des bons de commande et appeler les différents nœuds racine purchaseOrder, orderAcknowledgment et shipNotice.</span><span class="sxs-lookup"><span data-stu-id="25119-109">For example, you can create a library of schemas to describe the various schemas of messages related to sending purchase orders, naming the various root nodes purchaseOrder, orderAcknowledgment, and shipNotice.</span></span>  
  
## <a name="xsd-representation"></a><span data-ttu-id="25119-110">Représentation XSD</span><span class="sxs-lookup"><span data-stu-id="25119-110">XSD representation</span></span>  
 <span data-ttu-id="25119-111">L’exemple suivant affiche les lignes dans la représentation XSD du schéma qui correspondent à la **racine** nœud dans l’arborescence du schéma.</span><span class="sxs-lookup"><span data-stu-id="25119-111">The following example shows the lines in the XSD representation of the schema that correspond to the **Root** node in the tree view of the schema.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16" ?>  
<xs:schema xmlns="http://BizTalk_Server_Project1.Schema2"  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
    targetNamespace="http://BizTalk_Server_Project1.Schema2"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name="Root">  
        <xs:complexType />   
    </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="25119-112">**Racine** nœuds dans l’Éditeur BizTalk représentent l’élément principal d’une instance XML correspondante du message en question.</span><span class="sxs-lookup"><span data-stu-id="25119-112">**Root** nodes in BizTalk Editor represent the main element in a corresponding XML instance of the message in question.</span></span> <span data-ttu-id="25119-113">Par exemple, si le **racine** nœud d’un schéma particulier est renommé en purchaseOrder, la représentation XSD correspondante présente la structure de haut niveau suivante.</span><span class="sxs-lookup"><span data-stu-id="25119-113">For example, if the **Root** node of a particular schema is renamed to purchaseOrder, the corresponding XSD representation has the following high-level structure.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16" ?>  
<xs:schema xmlns="http://BizTalk_Server_Project1.Schema2"  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
    targetNamespace="http://BizTalk_Server_Project1.Schema2"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name="">  
        <xs:complexType>   
            ...  
        </xs:complexType>   
    </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="25119-114">Un message d'instance XML correspondant doit présenter la structure de base suivante.</span><span class="sxs-lookup"><span data-stu-id="25119-114">A corresponding XML instance message must have the following basic structure.</span></span>  
  
```  
<?xml version="1.0"?>  
<purchaseOrder ...>  
    ...  
</purchaseOrder>  
```  
  
> [!NOTE]
>  <span data-ttu-id="25119-115">Nœuds racine ne peuvent pas avoir **champ** attributs.</span><span class="sxs-lookup"><span data-stu-id="25119-115">Root nodes may not have **Field** attributes.</span></span> <span data-ttu-id="25119-116">**Champ** attributs attaché à la **racine** nœud ne sont pas enregistrées avec le schéma.</span><span class="sxs-lookup"><span data-stu-id="25119-116">**Field** attributes attached to the **Root** node are not saved with the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25119-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25119-117">See Also</span></span>  
-  [<span data-ttu-id="25119-118">Représentation BizTalk de schémas</span><span class="sxs-lookup"><span data-stu-id="25119-118">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
-  [<span data-ttu-id="25119-119">Propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="25119-119">Node Properties</span></span>](../core/node-properties.md)   
-  <span data-ttu-id="25119-120">**Propriétés d’un nœud enregistrement**  [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="25119-120">**Record Node Properties**  [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
-  [<span data-ttu-id="25119-121">Comment définir les propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="25119-121">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)
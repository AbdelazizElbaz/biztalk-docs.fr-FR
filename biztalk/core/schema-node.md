---
title: "Nœud de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ea02c2a-ee00-4f44-9086-83d7ac4a8832
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dee662cb9cb6e86b85a7760daf45af832a447b5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-node"></a><span data-ttu-id="17764-102">Nœud de schéma</span><span class="sxs-lookup"><span data-stu-id="17764-102">Schema Node</span></span>

## <a name="overview"></a><span data-ttu-id="17764-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="17764-103">Overview</span></span>
<span data-ttu-id="17764-104">Dans l’Éditeur BizTalk, le haut de la hiérarchie de schéma est toujours le **schéma** nœud, qui ne peut pas être renommé.</span><span class="sxs-lookup"><span data-stu-id="17764-104">In BizTalk Editor, the top of the schema hierarchy is always the **Schema** node, which cannot be renamed.</span></span> <span data-ttu-id="17764-105">Le **schéma** nœud correspond à la **schéma** élément dans la représentation de langage de schéma XML (XSD) de la définition du schéma.</span><span class="sxs-lookup"><span data-stu-id="17764-105">The **Schema** node corresponds to the **schema** element in the XML Schema definition (XSD) language representation of the schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17764-106">Dans l’Éditeur BizTalk, le **schéma** nœud est représenté par la chaîne \<schéma > dans l’arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="17764-106">In BizTalk Editor, the **Schema** node is represented with the string \<Schema> in the schema tree view.</span></span>  
  
 <span data-ttu-id="17764-107">En général, les propriétés de la **schéma** nœud correspondent aux attributs de la **schéma** élément dans la représentation XSD du schéma.</span><span class="sxs-lookup"><span data-stu-id="17764-107">In general, the properties of the **Schema** node correspond to the attributes of the **schema** element in the XSD representation of the schema.</span></span> <span data-ttu-id="17764-108">Pour obtenir des informations générales sur les propriétés d’un nœud, consultez [propriétés d’un nœud](../core/node-properties.md).</span><span class="sxs-lookup"><span data-stu-id="17764-108">For general information about node properties, see [Node Properties](../core/node-properties.md).</span></span> <span data-ttu-id="17764-109">Pour plus d’informations de référence sur les propriétés de la **schéma** nœud, consultez la **propriétés de nœud de schéma** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="17764-109">For reference information about the properties of the **Schema** node, see the **Schema Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="17764-110">Lorsque vous créez un schéma XML dans l’Éditeur BizTalk, le **schéma** nœud et l’autre **racine** nœud sont créées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="17764-110">When you create a new XML schema in BizTalk Editor, the **Schema** node and one **Root** node are created automatically.</span></span>  
  
## <a name="xsd-representation"></a><span data-ttu-id="17764-111">Représentation XSD</span><span class="sxs-lookup"><span data-stu-id="17764-111">XSD representation</span></span>  
 <span data-ttu-id="17764-112">L’exemple suivant, en caractères gras, les lignes dans la représentation XSD du schéma qui correspondent à la  **\<schéma >** nœud dans l’arborescence du schéma.</span><span class="sxs-lookup"><span data-stu-id="17764-112">The following example shows, in bold type, the lines in the XSD representation of the schema that correspond to the **\<Schema>** node in the tree view of the schema.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17764-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17764-113">See Also</span></span>  
 <span data-ttu-id="17764-114">[Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="17764-114">[BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md) </span></span>  
 <span data-ttu-id="17764-115">[Propriétés de nœud](../core/node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="17764-115">[Node Properties](../core/node-properties.md) </span></span>  
 [<span data-ttu-id="17764-116">Définir les propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="17764-116">Set Node Properties</span></span>](../core/how-to-set-node-properties.md)
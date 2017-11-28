---
title: "Pour insérer un élément Any ou n’importe quel nœud d’attribut | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cbfdc04-6c83-4639-82de-169b6f009a2e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 913d7d0c68d61df1c457dd22500a9e4a8d90ec68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-insert-an-any-element-or-any-attribute-node"></a><span data-ttu-id="62e7f-102">Pour insérer un élément Any ou n’importe quel nœud d’attribut</span><span class="sxs-lookup"><span data-stu-id="62e7f-102">How to Insert an Any Element or Any Attribute Node</span></span>
<span data-ttu-id="62e7f-103">L’Éditeur BizTalk prend en charge deux types de nœuds : **tout élément** et **tout attribut**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-103">BizTalk Editor supports two types of any nodes: **Any Element** and **Any Attribute**.</span></span> <span data-ttu-id="62e7f-104">Ces nœuds vous permettent de créer dans votre schéma des emplacements correspondant aux emplacements des messages d'instance correspondant où vous ignorez quels éléments ou attributs apparaîtront.</span><span class="sxs-lookup"><span data-stu-id="62e7f-104">These nodes allow you to create locations within your schema that correspond to locations within the corresponding instance messages where you do not know what elements or attributes will appear.</span></span> <span data-ttu-id="62e7f-105">Pour plus d'informations sur la manière dont ces nœuds sont interprétés lors du traitement des messages d'instance, reportez-vous directement aux informations relatives au langage XSD (XML Schema definition) sur le Web.</span><span class="sxs-lookup"><span data-stu-id="62e7f-105">For detailed information about how these nodes are interpreted when processing instance messages, refer directly to information about the XML Schema definition (XSD) language on the Web.</span></span> <span data-ttu-id="62e7f-106">Pour accéder à ces informations, voir [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).</span><span class="sxs-lookup"><span data-stu-id="62e7f-106">For links to this information, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).</span></span>  
  
## <a name="insert-an-any-element-node-or-an-any-attribute-node"></a><span data-ttu-id="62e7f-107">Insérer un nœud tout élément ou un nœud tout attribut</span><span class="sxs-lookup"><span data-stu-id="62e7f-107">Insert an Any Element node or an Any Attribute node</span></span>  
  
1.  <span data-ttu-id="62e7f-108">Dans l’arborescence du schéma, sélectionnez le **enregistrement** nœud dans lequel vous souhaitez insérer le **tout élément** nœud ou la **tout attribut** nœud.</span><span class="sxs-lookup"><span data-stu-id="62e7f-108">In the schema tree view, select the **Record** node into which you want to insert the **Any Element** node or the **Any Attribute** node.</span></span>  
  
2.  <span data-ttu-id="62e7f-109">Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **tout élément** ou **tout attribut**, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="62e7f-109">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Any Element** or **Any Attribute**, as appropriate.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="62e7f-110">Définition de la **Process Contents** propriété **Lax** pour **tout élément** ou **tout attribut** nœuds peuvent ne pas fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="62e7f-110">Setting the **Process Contents** property to **Lax** for **Any Element** or **Any Attribute** nodes may not work correctly.</span></span> <span data-ttu-id="62e7f-111">Pour transmettre la validation **tout élément** ou **tout attribut** nœuds, affectez à la propriété **ignorer**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-111">To pass validation on **Any Element** or **Any Attribute** nodes, set the property to **Skip**.</span></span>  <span data-ttu-id="62e7f-112">Plus de détails sur cette propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="62e7f-112">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
>
>  <span data-ttu-id="62e7f-113">Pour créer un mappage qui contient **tout élément** ou **tout attribut** nœuds, vous devez utiliser soit le [copie de masse](mass-copy-functoid.md) fonctoid ou [script](scripting-functoid.md) fonctoid (avec Inline XSLT ou modèle d’appel XSLT Inline) pour effectuer le mappage pour ces nœuds ou ne simplement pas mapper ces nœuds.</span><span class="sxs-lookup"><span data-stu-id="62e7f-113">To create a map that contains **Any Element** or **Any Attribute** nodes, you must use either the [Mass Copy](mass-copy-functoid.md) functoid or the [Scripting](scripting-functoid.md) functoid (with Inline XSLT or Inline XSLT Call Template) to perform the mapping for such nodes, or simply not map those nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e7f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62e7f-114">See Also</span></span>  
-  [<span data-ttu-id="62e7f-115">Insertion de nœuds dans un schéma</span><span class="sxs-lookup"><span data-stu-id="62e7f-115">Inserting Nodes into a Schema</span></span>](../core/inserting-nodes-into-a-schema.md)
- <span data-ttu-id="62e7f-116">**Référence du fonctoid**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="62e7f-116">**Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
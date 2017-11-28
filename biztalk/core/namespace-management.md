---
title: Gestion de Namespace | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4638c47c-3cdd-43af-aa00-da98e7293503
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 897ab6de3e7fddb362cb59356e6a4808d35f8f47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="namespace-management"></a><span data-ttu-id="c5707-102">Gestion des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="c5707-102">Namespace Management</span></span>
<span data-ttu-id="c5707-103">L'Éditeur BizTalk prend en charge les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="c5707-103">BizTalk Editor provides support for namespaces.</span></span> <span data-ttu-id="c5707-104">Un espace de noms XML est un ensemble de noms qui peuvent être utilisés comme noms d'élément ou d’attribut dans un message XML.</span><span class="sxs-lookup"><span data-stu-id="c5707-104">An XML namespace is a collection of names that can be used as element or attribute names in an XML message.</span></span> <span data-ttu-id="c5707-105">L'espace de noms qualifie des noms d'élément et d’attribut de façon à éviter les conflits entre des noms d'élément et d’attribut identiques pouvant être définis ailleurs dans le même schéma.</span><span class="sxs-lookup"><span data-stu-id="c5707-105">The namespace qualifies element and attribute names to avoid conflicts between the same element and attribute names that might be defined elsewhere within the same schema.</span></span>  
  
 <span data-ttu-id="c5707-106">Les espaces de noms sont identifiés par un URI (Universal Resource Identifier), en tant qu'URL (Uniform Resource Locator) ou URN (Uniform Resource Name).</span><span class="sxs-lookup"><span data-stu-id="c5707-106">Namespaces are identified by a Universal Resource Identifier (URI), either as a Uniform Resource Locator (URL) or a Uniform Resource Name (URN).</span></span> <span data-ttu-id="c5707-107">On leur ajoute également un alias de préfixe généralement court, séparé par un deux-points (:) du nom de l'élément ou de l'attribut lui-même.</span><span class="sxs-lookup"><span data-stu-id="c5707-107">They are also given a typically short prefix alias that is prepended with a separating colon (:) from the element or attribute name itself.</span></span> <span data-ttu-id="c5707-108">Par exemple, il est courant de voir la déclaration d’espace de noms suivantes au sein de la **schéma** élément dans la représentation XSD du schéma.</span><span class="sxs-lookup"><span data-stu-id="c5707-108">For example, it is common to see the following namespace declaration within the **schema** element in the XSD representation of the schema.</span></span>  
  
```  
xmlns:xs="http://www.w3.org/2001/XMLSchema"  
  
```  
  
 <span data-ttu-id="c5707-109">Le préfixe est xs, que vous voyez dans la représentation XSD, qualifie des éléments tels que les **élément** élément (xs : Element) et le **attribut** élément (xs : Attribute).</span><span class="sxs-lookup"><span data-stu-id="c5707-109">The prefix is xs, which you see throughout the XSD representation, qualifying such elements as the **element** element (xs:element) and the **attribute** element (xs:attribute).</span></span>  
  
 <span data-ttu-id="c5707-110">Lorsque vous créez un nouveau schéma, qu’il s’agisse d’un schéma de message ou un schéma de propriété, il est important de définir la **cible Namespace** propriété de la **schéma** nœud correctement.</span><span class="sxs-lookup"><span data-stu-id="c5707-110">When you first create a new schema, regardless of whether it is a message schema or a property schema, it is important to set the **Target Namespace** property of the **Schema** node properly.</span></span> <span data-ttu-id="c5707-111">Vous devez établir l'espace de noms cible avant que le schéma ne soit utilisé par un autre schéma avec les mécanismes importer, inclure et redéfinir, et avant que toute promotion de propriété ne soit définie.</span><span class="sxs-lookup"><span data-stu-id="c5707-111">You need to establish the target namespace before the schema is used by another schema with the import/include/redefine mechanisms, and before any property promotions are defined.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c5707-112">Si vous utilisez deux espaces de noms qui varient uniquement par la casse, la base de données BizTalk doit être installé avec un classement qui respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="c5707-112">If you will be using two namespaces that vary only by case, the BizTalk database must be installed with a case-sensitive collation.</span></span> <span data-ttu-id="c5707-113">Des classements binaires ou non binaires pour lesquels le respect de la casse est activé sont des exemples de classements respectant la casse.</span><span class="sxs-lookup"><span data-stu-id="c5707-113">Examples of case-sensitive collations include binary and non-binary collations with case-sensitivity enabled.</span></span> <span data-ttu-id="c5707-114">Si vous ne procédez pas à une telle installation, la résolution de schéma échoue, car le format XML fait la distinction entre majuscules et minuscules.</span><span class="sxs-lookup"><span data-stu-id="c5707-114">If this is not done, schema resolution will fail because XML is case-sensitive.</span></span>  
  
 <span data-ttu-id="c5707-115">Les deux espaces de noms suivants sont automatiquement ajoutés en tant que déclaration d’espaces de noms à l'élément de schéma dans la représentation XSD (XML Schema definition) du schéma :</span><span class="sxs-lookup"><span data-stu-id="c5707-115">The following two namespaces are automatically added as namespace declarations to the schema element in the XML Schema definition (XSD) language representation of the schema:</span></span>  
  
-   <span data-ttu-id="c5707-116">xmlns:b="http://schemas.microsoft.com/BizTalk/2003"</span><span class="sxs-lookup"><span data-stu-id="c5707-116">xmlns:b="http://schemas.microsoft.com/BizTalk/2003"</span></span>  
  
-   <span data-ttu-id="c5707-117">xmlns:xs="http://www.w3.org/2001/XMLSchema"</span><span class="sxs-lookup"><span data-stu-id="c5707-117">xmlns:xs="http://www.w3.org/2001/XMLSchema"</span></span>  
  
 <span data-ttu-id="c5707-118">Tandis que vous utilisez d’autres schémas dans le schéma que vous créez, d'autres espaces de noms seront déclarés.</span><span class="sxs-lookup"><span data-stu-id="c5707-118">In the course of using other schemas within the schema you are creating, other namespaces will be declared.</span></span> <span data-ttu-id="c5707-119">Vous pouvez examiner ces espaces de noms, ainsi que les espaces de noms inclus automatiquement dans le **importations** boîte de dialogue que vous pouvez accéder à l’aide de la **importations** propriété de la **deschéma** nœud.</span><span class="sxs-lookup"><span data-stu-id="c5707-119">You can examine these namespaces, as well as the automatically included namespaces, in the **Imports** dialog box that you can access by using the **Imports** property of the **Schema** node.</span></span> <span data-ttu-id="c5707-120">Pour plus d’informations sur l’utilisation d’autres types de données déclarés dans d’autres schémas dans le schéma que vous créez, consultez [schémas utilisant d’autres schémas](../core/schemas-that-use-other-schemas.md) et [création de schémas utilisant d’autres schémas](../core/how-to-create-schemas-that-use-other-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="c5707-120">For more information about using other data types declared in other schemas within the schema you are creating, see [Schemas That Use Other Schemas](../core/schemas-that-use-other-schemas.md) and [Creating Schemas That Use Other Schemas](../core/how-to-create-schemas-that-use-other-schemas.md).</span></span>  
  
 <span data-ttu-id="c5707-121">Espace de noms associés à des schémas de propriété peut être examinés dans le **promouvoir les propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c5707-121">Namespaces associated with property schemas can be examined in the **Promote Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5707-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5707-122">See Also</span></span>  
 [<span data-ttu-id="c5707-123">Considérations relatives à la création de schémas</span><span class="sxs-lookup"><span data-stu-id="c5707-123">Considerations When Creating Schemas</span></span>](../core/considerations-when-creating-schemas.md)
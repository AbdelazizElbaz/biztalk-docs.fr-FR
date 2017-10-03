---
title: RetractByType | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RetractByType function [Business Rules Engine], TypedXMLDocument
- RetractByType function [Business Rules Engine]
- RetractByType function [Business Rules Engine], .NET objects
- RetractByType function [Business Rules Engine], TypedData table
- RetractByType function [Business Rules Engine], DataConnection
- .NET objects
ms.assetid: e8867553-ee3c-46be-84cd-d5373eaf3337
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da8cd4581007ad2bd93ed66ebce4f5de6378280c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="retractbytype"></a><span data-ttu-id="b4b52-102">RetractByType</span><span class="sxs-lookup"><span data-stu-id="b4b52-102">RetractByType</span></span>
<span data-ttu-id="b4b52-103">Le **RetractByType** fonction retire toutes les instances d’un type spécifié dans la mémoire de travail, tandis que la **Retract**fonction retire seulement les éléments spécifiques d’un certain type.</span><span class="sxs-lookup"><span data-stu-id="b4b52-103">The **RetractByType** function retracts all instances of a specified type in the working memory, whereas the **Retract**function retracts only specific items of a certain type.</span></span> <span data-ttu-id="b4b52-104">Les paragraphes suivants décrivent comment les **RetractByType** avec des entités de types différents.</span><span class="sxs-lookup"><span data-stu-id="b4b52-104">The following paragraphs describe how the **RetractByType** function works with entities of different types.</span></span>  
  
## <a name="net-objects"></a><span data-ttu-id="b4b52-105">Objets .NET</span><span class="sxs-lookup"><span data-stu-id="b4b52-105">.NET Objects</span></span>  
 <span data-ttu-id="b4b52-106">Tous les objets d'un type de classe donné sont retirés de la mémoire de travail.</span><span class="sxs-lookup"><span data-stu-id="b4b52-106">All objects for a given class type are retracted from working memory.</span></span> <span data-ttu-id="b4b52-107">La classe faites simplement glisser à partir du volet des faits Classes .NET dans le **RetractByType** (fonction).</span><span class="sxs-lookup"><span data-stu-id="b4b52-107">You simply drag the class from the .NET Classes fact pane into the **RetractByType** function.</span></span>  
  
## <a name="typedxmldocument"></a><span data-ttu-id="b4b52-108">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="b4b52-108">TypedXmlDocument</span></span>  
 <span data-ttu-id="b4b52-109">Toutes les instances sont retirées.</span><span class="sxs-lookup"><span data-stu-id="b4b52-109">All instances are retracted.</span></span> <span data-ttu-id="b4b52-110">Cela signifie que tous les **TypedXmlDocument**comportant le même **DocumentType.Selector** sont retirées.</span><span class="sxs-lookup"><span data-stu-id="b4b52-110">This means that all **TypedXmlDocument**s with the same **DocumentType.Selector** are retracted.</span></span> <span data-ttu-id="b4b52-111">Vous devez faire glisser le nœud approprié à partir du volet des faits schémas XML dans le **RetractByType** (fonction).</span><span class="sxs-lookup"><span data-stu-id="b4b52-111">You should drag the appropriate node from the XML Schemas fact pane into the **RetractByType** function.</span></span> <span data-ttu-id="b4b52-112">Cohérent avec la **retrait** de fonction, si vous effectuez un **RetractByType** sur le nœud racine du document, il sera non seulement toutes les **TypedXmlDocuments** déclarées avec ce  **DocumentType** rétracté, mais tous les enfants **TypedXmlDocuments** (**XmlNode**s dans la hiérarchie d’arborescence) associées à ces parent **TypedXmlDocuments**  également vont être retirées.</span><span class="sxs-lookup"><span data-stu-id="b4b52-112">Consistent with the **Retract** function, if you perform a **RetractByType** on the document root node, not only will all **TypedXmlDocuments** asserted with that **DocumentType** be retracted, but all child **TypedXmlDocuments** (**XmlNode**s in the tree hierarchy) associated with those parent **TypedXmlDocuments** will also be retracted.</span></span>  
  
## <a name="typeddatatable-and-dataconnection"></a><span data-ttu-id="b4b52-113">TypedDataTable et DataConnection</span><span class="sxs-lookup"><span data-stu-id="b4b52-113">TypedDataTable and DataConnection</span></span>  
 <span data-ttu-id="b4b52-114">**Retrait** et **RetractByType** sont équivalents pour **TypedDataTable** et **DataConnection**.</span><span class="sxs-lookup"><span data-stu-id="b4b52-114">**Retract** and **RetractByType** are equivalent for both **TypedDataTable** and **DataConnection**.</span></span> <span data-ttu-id="b4b52-115">Étant donné que **DataSetName.DataTableName** est un identificateur unique pour les deux types, il n'existe qu’une seule instance dans le moteur à tout moment dans le temps.</span><span class="sxs-lookup"><span data-stu-id="b4b52-115">Because **DataSetName.DataTableName** is a unique identifier for both types, there is only one instance in the engine at any point in time.</span></span> <span data-ttu-id="b4b52-116">Comme avec **retrait**, vous faites glisser la table dans le **RetractByType** (fonction).</span><span class="sxs-lookup"><span data-stu-id="b4b52-116">As with **Retract**, you drag the table into the **RetractByType** function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b52-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4b52-117">See Also</span></span>  
 [<span data-ttu-id="b4b52-118">Fonctions de contrôle du moteur</span><span class="sxs-lookup"><span data-stu-id="b4b52-118">Engine Control Functions</span></span>](../core/engine-control-functions.md)
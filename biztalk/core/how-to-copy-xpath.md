---
title: Comment copier XPath | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 404599d4-0fb3-4c7c-91e6-1295d9d0965e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb282c5c32d8da62a9da6d7a9c900c798e44eee7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-xpath"></a><span data-ttu-id="71ce0-102">Comment copier XPath</span><span class="sxs-lookup"><span data-stu-id="71ce0-102">How to Copy XPath</span></span>
<span data-ttu-id="71ce0-103">Le langage XSD (XML Schema definition) fournit la syntaxe sous-jacente des schémas de message définis dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="71ce0-103">The XML Schema definition (XSD) language provides the underlying syntax of the message schemas defined within BizTalk Server.</span></span> <span data-ttu-id="71ce0-104">Bien que les arborescences du Mappeur BizTalk utilisent une hiérarchie graphique propre à BizTalk pour les nœuds d'enregistrement et de champ (entre autres types de nœuds), chacune associée à son propre ensemble de propriétés, de telles hiérarchies sont élaborées et conservées au format XSD.</span><span class="sxs-lookup"><span data-stu-id="71ce0-104">Although the tree views in BizTalk Mapper use a BizTalk-specific graphical hierarchy of record and field nodes (among other types of nodes), each with its own set of properties, such hierarchies are constructed and persisted as XSD.</span></span>  
  
 <span data-ttu-id="71ce0-105">Dans les scénarios incluant des mappages complexes et étendus sur plusieurs pages de grille, la localisation du parent d'un nœud de schéma peut être difficile.</span><span class="sxs-lookup"><span data-stu-id="71ce0-105">In scenarios where maps are complex and span across grid pages, locating the parent of a schema node can be difficult.</span></span> <span data-ttu-id="71ce0-106">Le chemin d'accès XSD est utile dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="71ce0-106">The XSD path will be of use here.</span></span> <span data-ttu-id="71ce0-107">Vous pouvez utiliser le chemin d'accès XSD pour obtenir des informations sur la profondeur des nœuds de schéma.</span><span class="sxs-lookup"><span data-stu-id="71ce0-107">You can use the XSD path to get information about the depth of schema nodes.</span></span> <span data-ttu-id="71ce0-108">Vous pouvez également réutiliser ce chemin d'accès dans une autre page de grille pour identifier la relation.</span><span class="sxs-lookup"><span data-stu-id="71ce0-108">Also, you can reuse this path in another grid page to identify the relationship.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="71ce0-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="71ce0-109">Prerequisites</span></span>  
 <span data-ttu-id="71ce0-110">Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="71ce0-110">These instructions require that BizTalk Mapper is running.</span></span>  
  
### <a name="to-copy-the-xsd-path-xpath"></a><span data-ttu-id="71ce0-111">Pour copier le chemin XSD (XPath)</span><span class="sxs-lookup"><span data-stu-id="71ce0-111">To copy the XSD path (XPath)</span></span>  
  
1.  <span data-ttu-id="71ce0-112">Cliquez sur le nœud de schéma pour lequel vous souhaitez que le chemin d’accès XSD, puis cliquez sur **Copier XPath**.</span><span class="sxs-lookup"><span data-stu-id="71ce0-112">Right-click the schema node for which you want the XSD path, and then click **Copy XPath**.</span></span>  
  
2.  <span data-ttu-id="71ce0-113">Ouvrez un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="71ce0-113">Open a text editor.</span></span> <span data-ttu-id="71ce0-114">Dans le menu **Edition** , cliquez sur **Coller**.</span><span class="sxs-lookup"><span data-stu-id="71ce0-114">On the **Edit** menu, click **Paste**.</span></span> <span data-ttu-id="71ce0-115">Le chemin d'accès XSD est à présent affiché.</span><span class="sxs-lookup"><span data-stu-id="71ce0-115">You can now see the XSD path.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="71ce0-116">Vous pouvez également appuyer sur CTRL+V pour coller le chemin d'accès dans un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="71ce0-116">Alternatively, you can press CTRL+V to paste the path in a text editor.</span></span>  
  
     <span data-ttu-id="71ce0-117">Le code suivant affiche le chemin XSD du nœud de schéma sélectionné.</span><span class="sxs-lookup"><span data-stu-id="71ce0-117">The code below displays the XSD path for the selected schema node.</span></span>  
  
    ```  
    /*[local-name()='<Schema>']/*[local-name()='Shipment']/*[local-name()='DataCollection']  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="71ce0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71ce0-118">See Also</span></span>  
 <span data-ttu-id="71ce0-119">[À l’aide des fonctionnalités améliorées dans le Mappeur BizTalk](../core/using-enhanced-features-in-biztalk-mapper.md) </span><span class="sxs-lookup"><span data-stu-id="71ce0-119">[Using Enhanced Features in BizTalk Mapper](../core/using-enhanced-features-in-biztalk-mapper.md) </span></span>  
 <span data-ttu-id="71ce0-120">[Procédure de remplacement des schémas](../core/how-to-replace-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="71ce0-120">[How to Replace Schemas](../core/how-to-replace-schemas.md) </span></span>  
 <span data-ttu-id="71ce0-121">[Comment développer et réduire les arborescences de schéma](https://msdn.microsoft.com/library/ee253802(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="71ce0-121">[How to Expand and Collapse the Schema Trees](https://msdn.microsoft.com/library/ee253802(v=bts.10).aspx)</span></span>
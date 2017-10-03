---
title: Configuration de la Transformation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XSLT
- maps, compiling
- Source Links property
- BizTalk Mapper, compiler directives
- code samples, XSLT
- compiler directives, copy text and subcontentent value
- compiler directives, copy text value
- maps, XSLT
- compiler directives, copy name
- compiler directives
- maps, code sample [XSLT]
- XSLT, code samples
ms.assetid: 05abe091-5202-4590-99ec-e60ca53a4324
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8304d43f59f63e474a3257915521d5dc36c38d30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-transformation-configuration"></a><span data-ttu-id="d7715-102">Configuration de la transformation de données</span><span class="sxs-lookup"><span data-stu-id="d7715-102">Data Transformation Configuration</span></span>
<span data-ttu-id="d7715-103">Lors d’un mappage à partir d’un élément, un langage de transformation de feuille de style extensible (XSLT) classique ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="d7715-103">When mapping from an element, a typical Extensible Stylesheet Language Transformations (XSLT) looks as follows.</span></span>  
  
```  
<xsl:attribute name='CatalogPurposeCode'>  
     <xsl:value-of select='BCT/BCT01/text()'/>  
</xsl:attribute>  
```  
  
 <span data-ttu-id="d7715-104">Si l’élément **BCT01** contient du contenu mixte, l’utilisation de text() rend possible d’accéder au premier texte uniquement jusqu’au point du premier sous-élément, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="d7715-104">If the element **BCT01** contains mixed content, the use of text() makes it possible to access the first text only up to the point of the first subelement, if any.</span></span> <span data-ttu-id="d7715-105">Si text() n’était pas utilisé dans l’instruction XSLT, il en résulterait que tout le contenu du texte, plus tout le contenu texte des sous-éléments, serait mappé en tant que chaîne de texte unique.</span><span class="sxs-lookup"><span data-stu-id="d7715-105">If text() were not used in this XSLT statement, the result would be that all text content, plus any text content of subelements, would be mapped as one string of text.</span></span> <span data-ttu-id="d7715-106">Configuration de la **liaisons sources** propriété pour un lien vous permet de contrôler la source des données copiées dans la structure définie par le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="d7715-106">Configuring the **Source Links** property for a link allows you to control the source of the data that is copied into the structure defined by the destination schema.</span></span>  
  
 <span data-ttu-id="d7715-107">Lorsque vous sélectionnez un lien dans la page de grille affichée, une des propriétés affichées dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés est le **liaisons sources** propriété.</span><span class="sxs-lookup"><span data-stu-id="d7715-107">When you select a link in the displayed grid page, one of the properties displayed in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window is the **Source Links** property.</span></span> <span data-ttu-id="d7715-108">Vous avez le choix entre les valeurs possibles suivantes pour chaque lien de votre mappage :</span><span class="sxs-lookup"><span data-stu-id="d7715-108">You can choose between the following possible values for each link in your map:</span></span>  
  
-   <span data-ttu-id="d7715-109">**Copier la valeur texte.**</span><span class="sxs-lookup"><span data-stu-id="d7715-109">**Copy text value.**</span></span> <span data-ttu-id="d7715-110">cette valeur, constituant celle par défaut, permet de copier la valeur de l’élément ou attribut dans le message d’instance d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d7715-110">Use this value, which is the default, to copy the value of the element or attribute in the input instance message.</span></span> <span data-ttu-id="d7715-111">Par exemple, si l’élément concerné est BoldExample :</span><span class="sxs-lookup"><span data-stu-id="d7715-111">For example, if the relevant element is BoldExample, as follows:</span></span>  
  
    ```  
    <BoldExample>This is a <B>Bold Text</B> example.</BoldExample>  
    ```  
  
     <span data-ttu-id="d7715-112">La valeur copiée dans l’élément ou attribut concerné dans le message d'instance de sortie correspond à « This is a ».</span><span class="sxs-lookup"><span data-stu-id="d7715-112">The value copied into the relevant element or attribute in the output instance message is "This is a ".</span></span> <span data-ttu-id="d7715-113">Pour les éléments de contenu mixte tels que celui-ci, ce résultat risque de ne pas être celui attendu.</span><span class="sxs-lookup"><span data-stu-id="d7715-113">For mixed content elements like this, this result may not be what is desired.</span></span> <span data-ttu-id="d7715-114">Mais étant donné que les éléments de contenu mixte étant relativement rares, le **copier la valeur texte** définition pour le **liaisons sources** propriété convient probablement dans la plupart des cas.</span><span class="sxs-lookup"><span data-stu-id="d7715-114">But because mixed content elements are relatively rare, the **Copy text value** setting for the **Source Links** property is probably appropriate in most cases.</span></span>  
  
-   <span data-ttu-id="d7715-115">**Nom de la copie.**</span><span class="sxs-lookup"><span data-stu-id="d7715-115">**Copy name.**</span></span> <span data-ttu-id="d7715-116">utilisez cette valeur pour copier le nom du nœud dans le message d’instance d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d7715-116">Use this value to copy the name of the node in the input instance message.</span></span> <span data-ttu-id="d7715-117">Dans l’exemple de la **copier la valeur texte** description, le résultat est « BoldExample », qui est le nom réel de l’élément.</span><span class="sxs-lookup"><span data-stu-id="d7715-117">For the example in the **Copy text value** description, the result is "BoldExample", which is the actual name of the element.</span></span>  
  
-   <span data-ttu-id="d7715-118">**Copier le texte et sub de valeur de contenu.**</span><span class="sxs-lookup"><span data-stu-id="d7715-118">**Copy text and sub content value.**</span></span> <span data-ttu-id="d7715-119">utilisez cette valeur pour concaténer les valeurs du nœud et toutes les valeurs de ses nœuds enfants dans le message d’instance d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d7715-119">Use this value to concatenate the values of the node and all values of its child nodes in the input instance message.</span></span> <span data-ttu-id="d7715-120">Dans l’exemple de la **copier la valeur texte** description, le résultat est « Voici un exemple de texte en gras. », ce qui pourrait très bien être le résultat approprié pour les éléments définis pour contenir du contenu mixte.</span><span class="sxs-lookup"><span data-stu-id="d7715-120">For the example in the **Copy text value** description, the result is "This is a Bold Text example.", which might very well be the appropriate result for elements defined to contain mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7715-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7715-121">See Also</span></span>  
 <span data-ttu-id="d7715-122">[Fonctoid copie de masse](../core/mass-copy-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="d7715-122">[Mass Copy Functoid](../core/mass-copy-functoid.md) </span></span>  
 <span data-ttu-id="d7715-123">[Comment définir la valeur du compilateur Source de liens](../core/how-to-set-the-source-links-compiler-value.md) </span><span class="sxs-lookup"><span data-stu-id="d7715-123">[How to Set the Source Links Compiler Value](../core/how-to-set-the-source-links-compiler-value.md) </span></span>  
 [<span data-ttu-id="d7715-124">Correspondance au niveau de hiérarchie de nœuds</span><span class="sxs-lookup"><span data-stu-id="d7715-124">Node-Hierarchy Level Matching</span></span>](../core/node-hierarchy-level-matching.md)
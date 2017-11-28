---
title: "Propriétés du nœud | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 366080f0-c21a-467d-8051-fd280264c5c3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d41f0f3b0fe0b302a763629b8777669b54f6cc86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="node-properties"></a><span data-ttu-id="82498-102">Propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="82498-102">Node Properties</span></span>

## <a name="overview"></a><span data-ttu-id="82498-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="82498-103">Overview</span></span>
<span data-ttu-id="82498-104">Dans l’Éditeur BizTalk, vous examinez et définissez les propriétés de nœud dans la fenêtre Propriétés de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="82498-104">In BizTalk Editor, you examine and set node properties in the Visual Studio Properties window.</span></span> <span data-ttu-id="82498-105">À mesure que vous sélectionnez différents types de nœuds dans la vue de l'arborescence de schéma, différents ensembles de propriétés s'affichent dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="82498-105">As you select different types of nodes in the schema tree view, different sets of properties are displayed in the Properties window.</span></span> <span data-ttu-id="82498-106">Comme c'est la norme dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ces propriétés peuvent être affichées soit par catégories, soit par ordre alphabétique, sans indication de la catégorie.</span><span class="sxs-lookup"><span data-stu-id="82498-106">As is standard in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], these properties can be displayed either in categories or alphabetically with no indication of their categories.</span></span> <span data-ttu-id="82498-107">Les boutons standard situés vers le haut de la fenêtre Propriétés vous permettent de passer de l’un de ces paramètres à l’autre.</span><span class="sxs-lookup"><span data-stu-id="82498-107">Use the standard buttons near the top of the Properties window to toggle this setting.</span></span>  
  
 <span data-ttu-id="82498-108">Les propriétés de nœud, en particulier lorsqu’elles affichent des valeurs autres que leurs valeurs par défaut, sont généralement représentées en langage XSD (XML Schema definition) comme des attributs et valeurs d'attributs associés à l'élément correspondant.</span><span class="sxs-lookup"><span data-stu-id="82498-108">Node properties, especially when set to values other than their defaults, are generally represented in the XML Schema definition (XSD) language as attributes and attribute values associated with the corresponding element.</span></span> <span data-ttu-id="82498-109">Par exemple, lorsque les propriétés sont définies pour le **Min Occurs** et **Max Occurs** propriétés, qui sont disponibles pour plusieurs types de nœud différents, les valeurs qui sont définies sont utilisées comme valeurs de la **minOccurs** et **maxOccurs** attributs, respectivement, associé à l’élément qui représente le nœud pour lequel la **Min Occurs** et **Max Se produit** propriétés sont définies.</span><span class="sxs-lookup"><span data-stu-id="82498-109">For example, when properties are set for the **Min Occurs** and **Max Occurs** properties, which are available for several different node types, the values that are set are used as the values of the **minOccurs** and **maxOccurs** attributes, respectively, associated with the element that represents the node for which the **Min Occurs** and **Max Occurs** properties are being set.</span></span>  

## <a name="property-types"></a><span data-ttu-id="82498-110">Types de propriétés</span><span class="sxs-lookup"><span data-stu-id="82498-110">Property types</span></span>
 <span data-ttu-id="82498-111">Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] référence du développeur contient une section de référence pour les propriétés de différents types de nœuds, organisés par catégorie et par ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="82498-111">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] developer reference contains a reference section for the properties of the various node types, organized by category and alphabetically.</span></span> <span data-ttu-id="82498-112">Les éléments suivants récapitulent les propriétés associées à chaque type de nœud :</span><span class="sxs-lookup"><span data-stu-id="82498-112">The following summarize the properties associated with each node type:</span></span>  
  
-   <span data-ttu-id="82498-113">Propriétés de nœud de schéma</span><span class="sxs-lookup"><span data-stu-id="82498-113">Schema Node Properties</span></span>
  
-   <span data-ttu-id="82498-114">Propriétés d’un nœud Enregistrement</span><span class="sxs-lookup"><span data-stu-id="82498-114">Record Node Properties</span></span>
  
-   <span data-ttu-id="82498-115">Propriétés d’un nœud Élément de champ</span><span class="sxs-lookup"><span data-stu-id="82498-115">Field Element Node Properties</span></span>
  
-   <span data-ttu-id="82498-116">Propriétés d’un nœud Attribut de champ</span><span class="sxs-lookup"><span data-stu-id="82498-116">Field Attribute Node Properties</span></span>
  
-   <span data-ttu-id="82498-117">Propriétés d’un nœud Groupe Séquence</span><span class="sxs-lookup"><span data-stu-id="82498-117">Sequence Group Node Properties</span></span>
  
-   <span data-ttu-id="82498-118">Propriétés d’un nœud Groupe Choix</span><span class="sxs-lookup"><span data-stu-id="82498-118">Choice Group Node Properties</span></span> 
  
-   <span data-ttu-id="82498-119">Propriétés d’un nœud Groupe Tous</span><span class="sxs-lookup"><span data-stu-id="82498-119">All Group Node Properties</span></span>
  
-   <span data-ttu-id="82498-120">Propriétés d’un nœud Groupe Attribut</span><span class="sxs-lookup"><span data-stu-id="82498-120">Attribute Group Node Properties</span></span>
  
-   <span data-ttu-id="82498-121">Propriétés d’un nœud Tout élément</span><span class="sxs-lookup"><span data-stu-id="82498-121">Any Element Node Properties</span></span>
  
-   <span data-ttu-id="82498-122">Propriétés d’un nœud Tout attribut</span><span class="sxs-lookup"><span data-stu-id="82498-122">Any Attribute Node Properties</span></span>
  
-   <span data-ttu-id="82498-123">Propriétés d’un nœud Équivalent</span><span class="sxs-lookup"><span data-stu-id="82498-123">Equivalent Node Properties</span></span>
  
-   <span data-ttu-id="82498-124">Propriétés d’un nœud enfant Équivalent</span><span class="sxs-lookup"><span data-stu-id="82498-124">Equivalent Child Node Properties</span></span>

<span data-ttu-id="82498-125">Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="82498-125">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="82498-126">**Propriétés de nœud-Liste alphabétique** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] contient toutes les rubriques de référence pour chaque propriété de nœud, certains d'entre eux s’appliquent à différents types de nœuds.</span><span class="sxs-lookup"><span data-stu-id="82498-126">**Node Properties — Alphabetical Listings** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] contains all of the individual reference topics for each node property, some of which apply to various types of nodes.</span></span> <span data-ttu-id="82498-127">Les rubriques de référence individuelles sont classées selon qu’il s’agit de propriétés de base s’appliquant à tous les types de schémas, ou de propriétés spécialisées associées à une extension de l’éditeur de schéma, telle que l’extension de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="82498-127">The individual reference topics are categorized according to whether they are basic properties that apply to all types of schemas, or a specialized properties that are associated with a schema editor extension, such as the flat file extension.</span></span> <span data-ttu-id="82498-128">Au sein de ces catégories, elles sont répertoriées par ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="82498-128">Within these categories, they are listed alphabetically.</span></span>  
  
 <span data-ttu-id="82498-129">L'Éditeur BizTalk utilise la fenêtre Propriétés de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour vous permettre d'examiner et de définir les propriétés des nœuds dans l'arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="82498-129">BizTalk Editor uses the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window to enable you to examine and set the properties of the nodes in the schema tree.</span></span> <span data-ttu-id="82498-130">Cette section décrit certaines caractéristiques de l’utilisation des propriétés dans la fenêtre Propriétés, y compris des considérations spéciales pour le **nom de nœud** propriété, une explication des interdépendances entre les propriétés, et Pour plus d’informations sur les longueurs maximales autorisées pour certaines propriétés ou les types de propriétés.</span><span class="sxs-lookup"><span data-stu-id="82498-130">This section describes some characteristics of working with properties in the Properties window, including special considerations for the **Node Name** property, an explanation of the interdependencies between properties, and information about the maximum lengths allowed for certain properties or types of properties.</span></span>  
  
 <span data-ttu-id="82498-131">Le reste de cette section propose des informations supplémentaires sur des propriétés de nœuds particulières et d’autres informations s’appliquant à des propriétés de nœud de manière générale.</span><span class="sxs-lookup"><span data-stu-id="82498-131">The remainder of this section provides additional information about particular, special node properties and other information that applies generally to node properties.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="82498-132">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="82498-132">Next steps</span></span>
  
-   [<span data-ttu-id="82498-133">Propriété de nom de nœud</span><span class="sxs-lookup"><span data-stu-id="82498-133">Node Name Property</span></span>](../core/node-name-property.md)  
  
-   [<span data-ttu-id="82498-134">Interdépendances des propriétés</span><span class="sxs-lookup"><span data-stu-id="82498-134">Property Interdependencies</span></span>](../core/property-interdependencies.md)  
  
-   [<span data-ttu-id="82498-135">Propriétés de fichier plat supplémentaires</span><span class="sxs-lookup"><span data-stu-id="82498-135">Additional Flat File Properties</span></span>](../core/additional-flat-file-properties.md)
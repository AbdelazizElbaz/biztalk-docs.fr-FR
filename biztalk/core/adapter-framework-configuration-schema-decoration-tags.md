---
title: "Balises d’ornement adaptateur Framework Configuration schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d5d7f6b-2273-45a6-ba9d-43201760cf22
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b834482b70e75d12bb6786dac2a5d9eb6f9fef40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-framework-configuration-schema-decoration-tags"></a><span data-ttu-id="5f9d3-102">Balises d’ornement adaptateur Framework Configuration schéma</span><span class="sxs-lookup"><span data-stu-id="5f9d3-102">Adapter Framework Configuration Schema Decoration Tags</span></span>
<span data-ttu-id="5f9d3-103">Vous pouvez utiliser les balises décrites dans cette rubrique dans les fichiers de schéma de configuration afin d'afficher et d'organiser les données sur les pages de propriétés de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-103">You can use the tags described in this topic within the configuration schema files to display and organize data on the adapter property pages.</span></span>  
  
 <span data-ttu-id="5f9d3-104">La capture d'écran suivante montre comment la page de propriétés de l'emplacement de réception FTP implémente certaines de ces balises.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-104">The following figure shows how the FTP receive location property page implements some of these tags.</span></span>  
  
 ![](../core/media/ebiz-prog-custad-tags.gif "ebiz_prog_custad_tags")  
<span data-ttu-id="5f9d3-105">Le \<description >, \<displayname >, et \<catégorie > balises dans la page de propriétés de l’adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="5f9d3-105">The \<description>, \<displayname>, and \<category> tags in the FTP adapter property page</span></span>  
  
## <a name="designer"></a><span data-ttu-id="5f9d3-106">\<Concepteur ></span><span class="sxs-lookup"><span data-stu-id="5f9d3-106">\<designer></span></span>  
 <span data-ttu-id="5f9d3-107">Les ornements de l’infrastructure d’adaptateurs BizTalk s’affichent entre un \<baf : Designer > balise et \</baf:designer > balise de fin.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-107">The BizTalk Adapter Framework decorations appear between a \<baf:designer> tag and \</baf:designer> end tag.</span></span> <span data-ttu-id="5f9d3-108">Le \<baf : Designer > balise permet de faire la distinction entre l’infrastructure d’adaptateurs \<appinfo > et autres adaptateur fournie \<appinfo > plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-108">The \<baf:designer> tag helps distinguish between Adapter Framework \<appinfo> and other adapter-supplied \<appinfo> information.</span></span>  
  
## <a name="category"></a><span data-ttu-id="5f9d3-109">\<catégorie ></span><span class="sxs-lookup"><span data-stu-id="5f9d3-109">\<category></span></span>  
 <span data-ttu-id="5f9d3-110">Le \<catégorie > décoration contient la chaîne utilisée pour séparer les entrées dans la grille des propriétés en groupes.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-110">The \<category> decoration contains the string used to separate entries in the property grid into groups.</span></span> <span data-ttu-id="5f9d3-111">Il affiche toutes les entrées de la même chaîne de catégorie sous forme d'entrées subordonnées.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-111">The decoration displays all entries with the same category string as subordinate entries of the category.</span></span>  
  
 <span data-ttu-id="5f9d3-112">Vous pouvez localiser \<catégorie > entrées.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-112">You can localize \<category> entries.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5f9d3-113">\<Description ></span><span class="sxs-lookup"><span data-stu-id="5f9d3-113">\<description></span></span>  
 <span data-ttu-id="5f9d3-114">Le \<description > décoration contient la chaîne utilisée pour fournir le texte descriptif pour les entrées au bas de la grille des propriétés.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-114">The \<description> decoration contains the string used to provide descriptive text for entries at the bottom of the property grid.</span></span>  
  
 <span data-ttu-id="5f9d3-115">Vous pouvez localiser \<description > entrées.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-115">You can localize \<description> entries.</span></span>  
  
## <a name="displayname"></a><span data-ttu-id="5f9d3-116">\<DisplayName ></span><span class="sxs-lookup"><span data-stu-id="5f9d3-116">\<displayname></span></span>  
 <span data-ttu-id="5f9d3-117">Le \<displayname > décoration contient la chaîne utilisée pour afficher le nom d’une entrée.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-117">The \<displayname> decoration contains the string used for displaying the name of an entry.</span></span> <span data-ttu-id="5f9d3-118">Cela vous permet d’utiliser des espaces, des expressions et ainsi de suite, lorsqu’il ne sont pas autorisé pour un \<élément > ou \<attribut > nom.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-118">This enables you to use spaces, phrases, and so on, when they would not be allowed for an \<element> or \<attribute> name.</span></span>  
  
 <span data-ttu-id="5f9d3-119">Vous pouvez localiser \<displayname > entrées.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-119">You can localize \<displayname> entries.</span></span>  
  
## <a name="readonly"></a><span data-ttu-id="5f9d3-120">\<ReadOnly ></span><span class="sxs-lookup"><span data-stu-id="5f9d3-120">\<readonly></span></span>  
 <span data-ttu-id="5f9d3-121">Le \<readonly fixée = » « > décoration contrôle si un champ peut être modifié.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-121">The \<readonly fixed=""> decoration controls whether a field may be edited.</span></span> <span data-ttu-id="5f9d3-122">Une valeur d'attribut « fixed » correspondant à `true` (valeur par défaut) signifie que le champ est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-122">A "fixed" attribute value of `true` (the default) makes a field read-only.</span></span>  
  
 <span data-ttu-id="5f9d3-123">Lors de l’implémentation d’un éditeur externe, implémentez un externe **TypeConverter** classe et substituer les **GetStandardValuesExclusive** méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-123">When implementing an external editor, implement an external **TypeConverter** class and override the **GetStandardValuesExclusive(ITypeDescriptorContext)** method instead.</span></span> <span data-ttu-id="5f9d3-124">Si la valeur `true` est renvoyée, le champ est en lecture seule, mais l'accès à l'éditeur personnalisé est possible.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-124">Returning `true` makes a field read-only but preserves access to the custom editor.</span></span>  
  
## <a name="browsable"></a><span data-ttu-id="5f9d3-125">\<Browsable ></span><span class="sxs-lookup"><span data-stu-id="5f9d3-125">\<browsable></span></span>  
 <span data-ttu-id="5f9d3-126">Le \<browsable show = " » > décoration contrôle si un champ s’affiche dans la grille des propriétés.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-126">The \<browsable show=""> decoration controls whether a field appears in the property grid.</span></span> <span data-ttu-id="5f9d3-127">Une valeur d'attribut « show » correspondant à `True` (valeur par défaut) signifie que le champ apparaît dans la grille.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-127">A "show" attribute value of `True` (the default) makes a field appear in the grid.</span></span>  
  
## <a name="converter"></a><span data-ttu-id="5f9d3-128">\<convertisseur ></span><span class="sxs-lookup"><span data-stu-id="5f9d3-128">\<converter></span></span>  
 <span data-ttu-id="5f9d3-129">Le \<assembly de convertisseur = » « > décoration spécifie souhaité **TypeConverter** nom de classe pour le \<élément > ou \<attribut >.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-129">The \<converter assembly=""> decoration specifies the desired **TypeConverter** class name for the \<element> or \<attribute>.</span></span> <span data-ttu-id="5f9d3-130">La valeur d’attribut « assembly » facultative indique le chemin d’accès à l’assembly contenant le texte souhaité **TypeConverter**.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-130">The optional "assembly" attribute value specifies the path to the assembly containing the desired **TypeConverter**.</span></span> <span data-ttu-id="5f9d3-131">Si la valeur « assembly » n'est pas spécifiée, le nom de la classe doit inclure les valeurs de version, culture, clé et nom d'assembly du GAC.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-131">With no "assembly" value specified, the class name must include the global assembly cache's assembly name, key, culture, and version values.</span></span>  
  
## <a name="editor"></a><span data-ttu-id="5f9d3-132">\<Éditeur ></span><span class="sxs-lookup"><span data-stu-id="5f9d3-132">\<editor></span></span>  
 <span data-ttu-id="5f9d3-133">Le \<assembly de l’éditeur = » « > décoration spécifie souhaité **UITypeEditor** nom de classe pour le \<élément > ou \<attribut >.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-133">The \<editor assembly=""> decoration specifies the desired **UITypeEditor** class name for the \<element> or \<attribute>.</span></span> <span data-ttu-id="5f9d3-134">La valeur d’attribut « assembly » facultative indique le chemin d’accès à l’assembly contenant le texte souhaité **UITypeEditor**.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-134">The optional "assembly" attribute value specifies the path to the assembly containing the desired **UITypeEditor**.</span></span> <span data-ttu-id="5f9d3-135">Si la valeur « assembly » n'est pas spécifiée, le nom de la classe doit inclure les valeurs de version, culture, clé et nom d'assembly du GAC.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-135">With no "assembly" value specified, the class name must include the global assembly cache's assembly name, key, culture, and version values.</span></span>  
  
## <a name="null-values-for-optional-enumerations"></a><span data-ttu-id="5f9d3-136">Valeurs Null pour les énumérations facultatives</span><span class="sxs-lookup"><span data-stu-id="5f9d3-136">Null Values for Optional Enumerations</span></span>  
 <span data-ttu-id="5f9d3-137">Lorsque vous utilisez une énumération facultative, une des valeurs doit être \<none > pour indiquer une valeur null.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-137">When using an optional enumeration, one of the values should be \<none> to denote a null value.</span></span> <span data-ttu-id="5f9d3-138">Il ne s'agit pas d'une balise intégrée, mais d'une valeur obtenue en indiquant une valeur d'énumération considérée comme étant « none » si l'énumération est dérivée de xsd:string.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-138">This is not a built-in tag, but may be achieved by providing an enumeration value that is treated as none if the enumeration is derived from xsd:string.</span></span> <span data-ttu-id="5f9d3-139">Cela n'est pas possible pour les énumérations dérivées de xsd:int, car le nombre entier doit comporter une valeur.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-139">This is not possible for enumerations derived from xsd:int, because the integer must hold a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f9d3-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f9d3-140">See Also</span></span>  
 [<span data-ttu-id="5f9d3-141">Extensions de schéma de Configuration Framework adaptateur</span><span class="sxs-lookup"><span data-stu-id="5f9d3-141">Adapter Framework Configuration Schema Extensions</span></span>](../core/adapter-framework-configuration-schema-extensions.md)
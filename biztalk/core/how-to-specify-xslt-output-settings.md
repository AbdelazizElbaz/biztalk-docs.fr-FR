---
title: "Paramètres de sortie de la spécification XSLT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c541432-fd4e-41cc-8bcc-f570ce5df439
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1aa3eea4c3f2f4696d3dc1fdf8109aeddec3ff8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="set-map-compilation-and-output-settings"></a><span data-ttu-id="f0cac-102">Définissez compilation de mappage et de sortie</span><span class="sxs-lookup"><span data-stu-id="f0cac-102">Set map compilation and output settings</span></span>
<span data-ttu-id="f0cac-103">Définissez les propriétés de mappage dans le Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f0cac-103">Set the map properties in the BizTalk mapper.</span></span> 

<span data-ttu-id="f0cac-104">L’utilisation de ces propriétés de mappage, vous pouvez définir comment les mappages sont compilés, inclure ou exclure une déclaration XML et l’encodage de jeu.</span><span class="sxs-lookup"><span data-stu-id="f0cac-104">Using these map properties, you can set how maps are compiled, include or exclude an XML declaration, and set the encoding.</span></span> 

<span data-ttu-id="f0cac-105">Cette rubrique montre comment définir ces propriétés sur la carte.</span><span class="sxs-lookup"><span data-stu-id="f0cac-105">This topic shows you how to set these properties on your map.</span></span>

## <a name="set-the-map-level-compilation"></a><span data-ttu-id="f0cac-106">Définir la compilation au niveau de la carte</span><span class="sxs-lookup"><span data-stu-id="f0cac-106">Set the map-level compilation</span></span>

<span data-ttu-id="f0cac-107">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** , vous choisissez la `XslTransform` ou `XslCompiledTransform` classe à compiler vos mappages.</span><span class="sxs-lookup"><span data-stu-id="f0cac-107">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you choose the `XslTransform` or the `XslCompiledTransform` class to compile your maps.</span></span> 

1. <span data-ttu-id="f0cac-108">Ouvrez votre mappage dans l’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="f0cac-108">Open your map in the Grid view.</span></span>
2. <span data-ttu-id="f0cac-109">Avec le bouton droit n’importe où dans la grille du mappeur, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f0cac-109">Right-click anywhere in the mapper grid, and select **Properties**.</span></span>  
3. <span data-ttu-id="f0cac-110">Définir le **utiliser XSLT** propriété :</span><span class="sxs-lookup"><span data-stu-id="f0cac-110">Set the **Use XSL Transform** property:</span></span> 

    | <span data-ttu-id="f0cac-111">Option</span><span class="sxs-lookup"><span data-stu-id="f0cac-111">Option</span></span> | <span data-ttu-id="f0cac-112"> Description</span><span class="sxs-lookup"><span data-stu-id="f0cac-112">Description</span></span> |
    | --- | --- |
    | <span data-ttu-id="f0cac-113">Indéfini</span><span class="sxs-lookup"><span data-stu-id="f0cac-113">Undefined</span></span> | <span data-ttu-id="f0cac-114">L’indicateur de Registre pour le paramètre XslTransform est utilisée :</span><span class="sxs-lookup"><span data-stu-id="f0cac-114">The registry flag for the XslTransform setting is used:</span></span> <ul><li><span data-ttu-id="f0cac-115">instances d’hôte 64 bits :`HKLM\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration`</span><span class="sxs-lookup"><span data-stu-id="f0cac-115">64-bit host instances: `HKLM\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration`</span></span></li><li><span data-ttu-id="f0cac-116">instances d’hôte 32 bits et fonctionnalité de mappage de Test de Visual Studio :`HKLM\SOFTWARE\Wow6432Node\Microsoft\BizTalk Server\3.0\Configuration`</span><span class="sxs-lookup"><span data-stu-id="f0cac-116">32-bit host instances, and Visual Studio’s Test Map functionality: `HKLM\SOFTWARE\Wow6432Node\Microsoft\BizTalk Server\3.0\Configuration`</span></span></li></ul> | 
    | <span data-ttu-id="f0cac-117">True</span><span class="sxs-lookup"><span data-stu-id="f0cac-117">True</span></span> | <span data-ttu-id="f0cac-118">A la valeur de la propriété de niveau de compilation de mappage `XslTransform` (comportement hérité)</span><span class="sxs-lookup"><span data-stu-id="f0cac-118">The map level compilation property is set to `XslTransform` (legacy behavior)</span></span> | 
    | <span data-ttu-id="f0cac-119">False</span><span class="sxs-lookup"><span data-stu-id="f0cac-119">False</span></span> | <span data-ttu-id="f0cac-120">A la valeur de la propriété de niveau de compilation de mappage`XslCompiledTransform`</span><span class="sxs-lookup"><span data-stu-id="f0cac-120">The map level compilation property is set to `XslCompiledTransform`</span></span> | 

> [!NOTE] 
> <span data-ttu-id="f0cac-121">À partir de BizTalk Server 2013, le comportement de compilation du Mappeur a été modifié à partir de `XslTransform` à `XslCompiledTransform`.</span><span class="sxs-lookup"><span data-stu-id="f0cac-121">Starting with BizTalk Server 2013, the mapper compilation behavior was changed from `XslTransform` to `XslCompiledTransform`.</span></span> <span data-ttu-id="f0cac-122">Le [le mappeur de mises à jour de signification pour vous](http://www.quicklearn.com/blog/2013/05/24/what-the-biztalk-server-2013-mapper-updates-mean-for-you/) billet de blog fournit une explication excellente du comportement et son impact potentiel.</span><span class="sxs-lookup"><span data-stu-id="f0cac-122">The [What the Mapper Updates Mean for You](http://www.quicklearn.com/blog/2013/05/24/what-the-biztalk-server-2013-mapper-updates-mean-for-you/) blog post provides a great explanation of the behavior, and its potential impact.</span></span> 
> 
> <span data-ttu-id="f0cac-123">En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], vous pouvez choisir la classe à la compilation de vos mappages.</span><span class="sxs-lookup"><span data-stu-id="f0cac-123">Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], you can choose which class to compile your maps.</span></span> 
  
## <a name="include-or-exclude-an-xml-declaration"></a><span data-ttu-id="f0cac-124">Inclure ou exclure une déclaration XML</span><span class="sxs-lookup"><span data-stu-id="f0cac-124">Include or exclude an XML declaration</span></span>  
<span data-ttu-id="f0cac-125">Vous pouvez choisir si une déclaration XML est sortie ou non.</span><span class="sxs-lookup"><span data-stu-id="f0cac-125">You can choose whether an XML declaration is output or not.</span></span> 

1. <span data-ttu-id="f0cac-126">Ouvrez votre mappage dans l’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="f0cac-126">Open your map in the Grid view.</span></span>
2. <span data-ttu-id="f0cac-127">Avec le bouton droit n’importe où dans la grille du mappeur, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f0cac-127">Right-click anywhere in the mapper grid, and select **Properties**.</span></span>  
3. <span data-ttu-id="f0cac-128">Dans la liste déroulante pour le **omettre la déclaration XML** propriété, sélectionnez **Oui** pour omettre une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="f0cac-128">In the drop-down list for the **Omit XML Declaration** property, select **Yes** to omit an XML declaration.</span></span> <span data-ttu-id="f0cac-129">Sélectionnez **non** pour ne pas omettre une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="f0cac-129">Select **No** not to omit an XML declaration.</span></span>  

<span data-ttu-id="f0cac-130">Une déclaration XML apparaît (si vous avez sélectionné **non**) semblable au suivant.</span><span class="sxs-lookup"><span data-stu-id="f0cac-130">An XML declaration would appear (if you selected **No**) similar to the following.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
```  
  
## <a name="set-encoding-for-output-instance-data"></a><span data-ttu-id="f0cac-131">Définir le codage de données d’instance de sortie</span><span class="sxs-lookup"><span data-stu-id="f0cac-131">Set encoding for output instance data</span></span>  
<span data-ttu-id="f0cac-132">Le codage fournit au moteur d’exécution les informations nécessaires pour déterminer le jeu de caractères à utiliser lors de la création de la sortie d'un mappage.</span><span class="sxs-lookup"><span data-stu-id="f0cac-132">Encoding provides the run-time engine with the information it needs to determine which character set to use when creating the output result of a map.</span></span>  
   
1. <span data-ttu-id="f0cac-133">Ouvrez votre mappage dans l’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="f0cac-133">Open your map in the Grid view.</span></span>
2. <span data-ttu-id="f0cac-134">Avec le bouton droit n’importe où dans la grille du mappeur, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f0cac-134">Right-click anywhere in the mapper grid, and select **Properties**.</span></span>    
3.  <span data-ttu-id="f0cac-135">Dans la liste déroulante pour le **codage XSLT** propriété, sélectionnez le jeu de caractères vous souhaitez utiliser pour les données d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="f0cac-135">In the drop-down list for the **XSLT Encoding** property, select the character set you want used for the output instance data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0cac-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0cac-136">See Also</span></span>  
 <span data-ttu-id="f0cac-137">[La compilation et test des mappages](../core/compiling-and-testing-maps.md) </span><span class="sxs-lookup"><span data-stu-id="f0cac-137">[Compiling and Testing Maps](../core/compiling-and-testing-maps.md) </span></span>  
 <span data-ttu-id="f0cac-138">[À l’aide du Mappeur BizTalk](../core/using-biztalk-mapper.md) </span><span class="sxs-lookup"><span data-stu-id="f0cac-138">[Using BizTalk Mapper](../core/using-biztalk-mapper.md) </span></span>  
 [<span data-ttu-id="f0cac-139">Types de codages de XSLT valides du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="f0cac-139">Valid BizTalk Mapper XSLT Encoding Types</span></span>](../core/valid-biztalk-mapper-xslt-encoding-types.md)
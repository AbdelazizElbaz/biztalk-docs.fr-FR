---
title: Scripts utilisant Inline c#, JScript .NET et Visual Basic .NET | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scripting functoids, JScript
- Scripting functoids, warnings
- Scripting functoids, Visual Basic .NET
- Scripting functoids, inline C#
- Scripting functoids, .NET
ms.assetid: dda60024-58bd-483f-a750-31b21059eded
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe2002bd92342a953406a21e076b801d3e90b938
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="scripting-using-inline-c-jscript-net-and-visual-basic-net"></a><span data-ttu-id="27270-102">Scripts utilisant Inline C#, Jscript .NET et Visual Basic .NET</span><span class="sxs-lookup"><span data-stu-id="27270-102">Scripting Using Inline C#, JScript .NET, and Visual Basic .NET</span></span>
<span data-ttu-id="27270-103">Les scripts Inline peuvent s’avérer pratiques pour le code personnalisé que vous risquez de ne pas réutiliser dans votre application.</span><span class="sxs-lookup"><span data-stu-id="27270-103">Inline scripts are convenient for custom code that you are unlikely to use elsewhere in your application.</span></span>  
  
 <span data-ttu-id="27270-104">BizTalk enregistre les scripts Inline dans la feuille de style XSLT (Extensible Stylesheet Language Transformations) définissant le mappage.</span><span class="sxs-lookup"><span data-stu-id="27270-104">BizTalk saves inline scripts in the Extensible Stylesheet Language Transformations (XSLT) stylesheet defining the map.</span></span> <span data-ttu-id="27270-105">Pour cette raison, les scripts Inline peuvent utiliser les mêmes espaces de noms que n’importe quel autre script de feuille de style XSLT.</span><span class="sxs-lookup"><span data-stu-id="27270-105">Because of this, inline scripts may use the same namespaces as any other XSLT stylesheet script.</span></span> <span data-ttu-id="27270-106">Le tableau suivant indique les espaces de noms disponibles.</span><span class="sxs-lookup"><span data-stu-id="27270-106">The following table shows the available namespaces.</span></span>  
  
|<span data-ttu-id="27270-107">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="27270-107">Namespace</span></span>|<span data-ttu-id="27270-108"> Description</span><span class="sxs-lookup"><span data-stu-id="27270-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27270-109">Système</span><span class="sxs-lookup"><span data-stu-id="27270-109">System</span></span>|<span data-ttu-id="27270-110">La classe System.</span><span class="sxs-lookup"><span data-stu-id="27270-110">The System class.</span></span>|  
|<span data-ttu-id="27270-111">System.Collection</span><span class="sxs-lookup"><span data-stu-id="27270-111">System.Collection</span></span>|<span data-ttu-id="27270-112">Les classes de regroupement.</span><span class="sxs-lookup"><span data-stu-id="27270-112">The collection classes.</span></span>|  
|<span data-ttu-id="27270-113">System.Text</span><span class="sxs-lookup"><span data-stu-id="27270-113">System.Text</span></span>|<span data-ttu-id="27270-114">Les classes de texte.</span><span class="sxs-lookup"><span data-stu-id="27270-114">The text classes.</span></span>|  
|<span data-ttu-id="27270-115">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="27270-115">System.Text.RegularExpressions</span></span>|<span data-ttu-id="27270-116">Les classes d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="27270-116">The regular expression classes.</span></span>|  
|<span data-ttu-id="27270-117">System.Xml</span><span class="sxs-lookup"><span data-stu-id="27270-117">System.Xml</span></span>|<span data-ttu-id="27270-118">Les classes XML principales.</span><span class="sxs-lookup"><span data-stu-id="27270-118">The core XML classes.</span></span>|  
|<span data-ttu-id="27270-119">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="27270-119">System.Xml.Xsl</span></span>|<span data-ttu-id="27270-120">Les classes XSLT.</span><span class="sxs-lookup"><span data-stu-id="27270-120">The XSLT classes.</span></span>|  
|<span data-ttu-id="27270-121">System.Xml.Xpath</span><span class="sxs-lookup"><span data-stu-id="27270-121">System.Xml.Xpath</span></span>|<span data-ttu-id="27270-122">Les classes XPath.</span><span class="sxs-lookup"><span data-stu-id="27270-122">The XPath classes.</span></span>|  
|<span data-ttu-id="27270-123">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="27270-123">Microsoft.VisualBasic</span></span>|<span data-ttu-id="27270-124">Les classes de script Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="27270-124">The Visual Basic script classes.</span></span>|  
  
 <span data-ttu-id="27270-125">Pour plus d’informations sur les espaces de noms et types de données, effectuez une recherche sur « à l’aide de XSLT Stylesheet Scripting \<msxsl : script\>» et « System.Xml.Xsl.XslCompiledTransform » dans la collection du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27270-125">For more information about namespaces and data types, search on "XSLT Stylesheet Scripting using \<msxsl:script\>" and on "System.Xml.Xsl.XslCompiledTransform" in the .NET Framework collection.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="27270-126">Veillez à ne pas utiliser la même signature de méthode plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="27270-126">Avoid using the same method signature more than once.</span></span> <span data-ttu-id="27270-127">Lorsque plusieurs fonctoids Script ont la même signature de méthode, BizTalk sélectionne la première implémentation et ignore les autres.</span><span class="sxs-lookup"><span data-stu-id="27270-127">When several Scripting functoids have the same method signature, BizTalk selects the first implementation and disregards the others.</span></span>  
  
 <span data-ttu-id="27270-128">Outre leur facilité d’utilisation pour les scripts à usage unique, les scripts Inline sont également utiles pour déclarer des variables globales à utiliser avec un certain nombre de scripts.</span><span class="sxs-lookup"><span data-stu-id="27270-128">In addition to being convenient for one-time scripts, inline scripts are also useful for declaring global variables for use among a number of scripts.</span></span> <span data-ttu-id="27270-129">Par exemple, dans un script C# inline, vous pourriez placer la ligne de code suivante en dehors de toute classe.</span><span class="sxs-lookup"><span data-stu-id="27270-129">For example, in a C# inline script, you could place the following line of code outside of any class.</span></span>  
  
```  
ArrayList statusList = new ArrayList();  
```  
  
 <span data-ttu-id="27270-130">Cette opération crée un **ArrayList**, `statusList`, disponible à tous les scripts inline dans le mappage.</span><span class="sxs-lookup"><span data-stu-id="27270-130">This creates an **ArrayList**, `statusList`, available to all inline scripts in the map.</span></span>  
  
 <span data-ttu-id="27270-131">Pour un exemple de script inline, consultez [XML outils (dossier d’exemples BizTalk Server)](../core/xml-tools-biztalk-server-samples-folder.md).</span><span class="sxs-lookup"><span data-stu-id="27270-131">For a sample inline script, see [XML Tools (BizTalk Server Samples Folder)](../core/xml-tools-biztalk-server-samples-folder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27270-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27270-132">See Also</span></span>  
 <span data-ttu-id="27270-133">[Fonctoid script](../core/scripting-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="27270-133">[Scripting Functoid](../core/scripting-functoid.md) </span></span>  
 <span data-ttu-id="27270-134">[Écriture de scripts à l’aide des assemblys externes](../core/scripting-using-external-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="27270-134">[Scripting Using External Assemblies](../core/scripting-using-external-assemblies.md) </span></span>  
 <span data-ttu-id="27270-135">[Écriture de scripts utilisant Inline XSLT et modèles d’appel XSLT](../core/scripting-using-inline-xslt-and-xslt-call-templates.md) </span><span class="sxs-lookup"><span data-stu-id="27270-135">[Scripting Using Inline XSLT and XSLT Call Templates](../core/scripting-using-inline-xslt-and-xslt-call-templates.md) </span></span>  
 <span data-ttu-id="27270-136">[Comment ajouter des fonctoids de script à une carte](../core/how-to-add-scripting-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="27270-136">[How to Add Scripting Functoids to a Map](../core/how-to-add-scripting-functoids-to-a-map.md) </span></span>  
 [<span data-ttu-id="27270-137">Comment configurer le fonctoid script</span><span class="sxs-lookup"><span data-stu-id="27270-137">How to Configure the Scripting Functoid</span></span>](../core/how-to-configure-the-scripting-functoid.md)
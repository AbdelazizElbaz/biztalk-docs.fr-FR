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
ms.openlocfilehash: 68fe19b4616e23066603995b6403654fa3960789
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scripting-using-inline-c-jscript-net-and-visual-basic-net"></a><span data-ttu-id="d74de-102">Scripts utilisant Inline C#, Jscript .NET et Visual Basic .NET</span><span class="sxs-lookup"><span data-stu-id="d74de-102">Scripting Using Inline C#, JScript .NET, and Visual Basic .NET</span></span>
<span data-ttu-id="d74de-103">Les scripts Inline peuvent s’avérer pratiques pour le code personnalisé que vous risquez de ne pas réutiliser dans votre application.</span><span class="sxs-lookup"><span data-stu-id="d74de-103">Inline scripts are convenient for custom code that you are unlikely to use elsewhere in your application.</span></span>  
  
 <span data-ttu-id="d74de-104">BizTalk enregistre les scripts Inline dans la feuille de style XSLT (Extensible Stylesheet Language Transformations) définissant le mappage.</span><span class="sxs-lookup"><span data-stu-id="d74de-104">BizTalk saves inline scripts in the Extensible Stylesheet Language Transformations (XSLT) stylesheet defining the map.</span></span> <span data-ttu-id="d74de-105">Pour cette raison, les scripts Inline peuvent utiliser les mêmes espaces de noms que n’importe quel autre script de feuille de style XSLT.</span><span class="sxs-lookup"><span data-stu-id="d74de-105">Because of this, inline scripts may use the same namespaces as any other XSLT stylesheet script.</span></span> <span data-ttu-id="d74de-106">Le tableau suivant indique les espaces de noms disponibles.</span><span class="sxs-lookup"><span data-stu-id="d74de-106">The following table shows the available namespaces.</span></span>  
  
|<span data-ttu-id="d74de-107">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="d74de-107">Namespace</span></span>|<span data-ttu-id="d74de-108"> Description</span><span class="sxs-lookup"><span data-stu-id="d74de-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d74de-109">Système</span><span class="sxs-lookup"><span data-stu-id="d74de-109">System</span></span>|<span data-ttu-id="d74de-110">La classe System.</span><span class="sxs-lookup"><span data-stu-id="d74de-110">The System class.</span></span>|  
|<span data-ttu-id="d74de-111">System.Collection</span><span class="sxs-lookup"><span data-stu-id="d74de-111">System.Collection</span></span>|<span data-ttu-id="d74de-112">Les classes de regroupement.</span><span class="sxs-lookup"><span data-stu-id="d74de-112">The collection classes.</span></span>|  
|<span data-ttu-id="d74de-113">System.Text</span><span class="sxs-lookup"><span data-stu-id="d74de-113">System.Text</span></span>|<span data-ttu-id="d74de-114">Les classes de texte.</span><span class="sxs-lookup"><span data-stu-id="d74de-114">The text classes.</span></span>|  
|<span data-ttu-id="d74de-115">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="d74de-115">System.Text.RegularExpressions</span></span>|<span data-ttu-id="d74de-116">Les classes d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="d74de-116">The regular expression classes.</span></span>|  
|<span data-ttu-id="d74de-117">System.Xml</span><span class="sxs-lookup"><span data-stu-id="d74de-117">System.Xml</span></span>|<span data-ttu-id="d74de-118">Les classes XML principales.</span><span class="sxs-lookup"><span data-stu-id="d74de-118">The core XML classes.</span></span>|  
|<span data-ttu-id="d74de-119">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="d74de-119">System.Xml.Xsl</span></span>|<span data-ttu-id="d74de-120">Les classes XSLT.</span><span class="sxs-lookup"><span data-stu-id="d74de-120">The XSLT classes.</span></span>|  
|<span data-ttu-id="d74de-121">System.Xml.Xpath</span><span class="sxs-lookup"><span data-stu-id="d74de-121">System.Xml.Xpath</span></span>|<span data-ttu-id="d74de-122">Les classes XPath.</span><span class="sxs-lookup"><span data-stu-id="d74de-122">The XPath classes.</span></span>|  
|<span data-ttu-id="d74de-123">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="d74de-123">Microsoft.VisualBasic</span></span>|<span data-ttu-id="d74de-124">Les classes de script Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d74de-124">The Visual Basic script classes.</span></span>|  
  
 <span data-ttu-id="d74de-125">Pour plus d’informations sur les espaces de noms et types de données, effectuez une recherche sur « à l’aide de XSLT Stylesheet Scripting \<msxsl : script > » et « System.Xml.Xsl.XslCompiledTransform » dans la collection du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d74de-125">For more information about namespaces and data types, search on "XSLT Stylesheet Scripting using \<msxsl:script>" and on "System.Xml.Xsl.XslCompiledTransform" in the .NET Framework collection.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="d74de-126">Veillez à ne pas utiliser la même signature de méthode plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="d74de-126">Avoid using the same method signature more than once.</span></span> <span data-ttu-id="d74de-127">Lorsque plusieurs fonctoids Script ont la même signature de méthode, BizTalk sélectionne la première implémentation et ignore les autres.</span><span class="sxs-lookup"><span data-stu-id="d74de-127">When several Scripting functoids have the same method signature, BizTalk selects the first implementation and disregards the others.</span></span>  
  
 <span data-ttu-id="d74de-128">Outre leur facilité d’utilisation pour les scripts à usage unique, les scripts Inline sont également utiles pour déclarer des variables globales à utiliser avec un certain nombre de scripts.</span><span class="sxs-lookup"><span data-stu-id="d74de-128">In addition to being convenient for one-time scripts, inline scripts are also useful for declaring global variables for use among a number of scripts.</span></span> <span data-ttu-id="d74de-129">Par exemple, dans un script C# inline, vous pourriez placer la ligne de code suivante en dehors de toute classe.</span><span class="sxs-lookup"><span data-stu-id="d74de-129">For example, in a C# inline script, you could place the following line of code outside of any class.</span></span>  
  
```  
ArrayList statusList = new ArrayList();  
```  
  
 <span data-ttu-id="d74de-130">Cette opération crée un **ArrayList**, `statusList`, disponible à tous les scripts inline dans le mappage.</span><span class="sxs-lookup"><span data-stu-id="d74de-130">This creates an **ArrayList**, `statusList`, available to all inline scripts in the map.</span></span>  
  
 <span data-ttu-id="d74de-131">Pour un exemple de script inline, consultez [XML outils (dossier d’exemples BizTalk Server)](../core/xml-tools-biztalk-server-samples-folder.md).</span><span class="sxs-lookup"><span data-stu-id="d74de-131">For a sample inline script, see [XML Tools (BizTalk Server Samples Folder)](../core/xml-tools-biztalk-server-samples-folder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d74de-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d74de-132">See Also</span></span>  
 <span data-ttu-id="d74de-133">[Fonctoid script](../core/scripting-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="d74de-133">[Scripting Functoid](../core/scripting-functoid.md) </span></span>  
 <span data-ttu-id="d74de-134">[Écriture de scripts à l’aide des assemblys externes](../core/scripting-using-external-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="d74de-134">[Scripting Using External Assemblies](../core/scripting-using-external-assemblies.md) </span></span>  
 <span data-ttu-id="d74de-135">[Écriture de scripts utilisant Inline XSLT et modèles d’appel XSLT](../core/scripting-using-inline-xslt-and-xslt-call-templates.md) </span><span class="sxs-lookup"><span data-stu-id="d74de-135">[Scripting Using Inline XSLT and XSLT Call Templates](../core/scripting-using-inline-xslt-and-xslt-call-templates.md) </span></span>  
 <span data-ttu-id="d74de-136">[Comment ajouter des fonctoids de script à une carte](../core/how-to-add-scripting-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="d74de-136">[How to Add Scripting Functoids to a Map](../core/how-to-add-scripting-functoids-to-a-map.md) </span></span>  
 [<span data-ttu-id="d74de-137">Comment configurer le fonctoid script</span><span class="sxs-lookup"><span data-stu-id="d74de-137">How to Configure the Scripting Functoid</span></span>](../core/how-to-configure-the-scripting-functoid.md)
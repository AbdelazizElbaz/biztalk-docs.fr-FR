---
title: "Écriture de scripts à l’aide des assemblys externes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scripting functoids, warnings
- Scripting functoids, external assemblies
ms.assetid: 0bdf6adc-91b9-462e-8fd0-9cb48bfa7817
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 475a3b9781eecb0ccc79165bbe54e6dfd542ecfc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scripting-using-external-assemblies"></a><span data-ttu-id="c9d47-102">Scripts utilisant les assemblys externes</span><span class="sxs-lookup"><span data-stu-id="c9d47-102">Scripting Using External Assemblies</span></span>
<span data-ttu-id="c9d47-103">L'utilisation de scripts avec assemblys externes est recommandée dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c9d47-103">Scripting with external assemblies is the preferred way to use scripting in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="c9d47-104">Les assemblys externes présentent plusieurs avantages :</span><span class="sxs-lookup"><span data-stu-id="c9d47-104">External assemblies provide several advantages:</span></span>  
  
-   <span data-ttu-id="c9d47-105">le partage de code ;</span><span class="sxs-lookup"><span data-stu-id="c9d47-105">Easy code sharing</span></span>  
  
-   <span data-ttu-id="c9d47-106">la maintenance ;</span><span class="sxs-lookup"><span data-stu-id="c9d47-106">Simpler maintenance</span></span>  
  
-   <span data-ttu-id="c9d47-107">le débogage.</span><span class="sxs-lookup"><span data-stu-id="c9d47-107">Easier debugging</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9d47-108">Tester le mappage échoue si le **script** fonctoid utilise un assembly externe qui n’est pas enregistré dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="c9d47-108">Test Map fails if the **Scripting** functoid uses an external assembly which is not registered in the GAC.</span></span> <span data-ttu-id="c9d47-109">Il fonctionne si l'assembly externe se trouve dans le même dossier bin que l'assembly du projet en cours (placé après la génération).</span><span class="sxs-lookup"><span data-stu-id="c9d47-109">It works if the external assembly is in the same bin folder as the current project's assembly (placed after build).</span></span>  
  
 <span data-ttu-id="c9d47-110">Nouveau en utilisant le script suffit de définir la **Script** propriété de la **script** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="c9d47-110">Re-using the script only requires setting the **Script** property of the **Scripting** functoid.</span></span> <span data-ttu-id="c9d47-111">Le script étant conservé à l’extérieur du mappage, vous pouvez le modifier sans avoir besoin de changer le mappage.</span><span class="sxs-lookup"><span data-stu-id="c9d47-111">Because the script is stored outside of the map, you can modify the script without changing the map.</span></span> <span data-ttu-id="c9d47-112">Vous pouvez également utiliser toute la variété d’outils de débogage de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour garantir le bon fonctionnement de votre script.</span><span class="sxs-lookup"><span data-stu-id="c9d47-112">And you can use the full array of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] debugging tools to ensure your script runs correctly.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c9d47-113">Le code contenu dans l’assembly externe doit être exempt de tout thread.</span><span class="sxs-lookup"><span data-stu-id="c9d47-113">The code in the external assembly must be thread-safe.</span></span> <span data-ttu-id="c9d47-114">Dans les situations de forte charge, il est possible d’exécuter plusieurs instances d’un mappage en même temps.</span><span class="sxs-lookup"><span data-stu-id="c9d47-114">Under stress conditions, multiple instances of a map may be running concurrently.</span></span>  
  
 <span data-ttu-id="c9d47-115">Pour un exemple de fonction hébergée dans un assembly externe, consultez [XML outils (dossier d’exemples BizTalk Server)](../core/xml-tools-biztalk-server-samples-folder.md).</span><span class="sxs-lookup"><span data-stu-id="c9d47-115">For a sample function housed in an external assembly, see [XML Tools (BizTalk Server Samples Folder)](../core/xml-tools-biztalk-server-samples-folder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d47-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9d47-116">See Also</span></span>  
 <span data-ttu-id="c9d47-117">[Fonctoid script](../core/scripting-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="c9d47-117">[Scripting Functoid](../core/scripting-functoid.md) </span></span>  
 <span data-ttu-id="c9d47-118">[Scripts utilisant Inline c#, JScript .NET et Visual Basic .NET](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md) </span><span class="sxs-lookup"><span data-stu-id="c9d47-118">[Scripting Using Inline C#, JScript .NET, and Visual Basic .NET](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md) </span></span>  
 <span data-ttu-id="c9d47-119">[Écriture de scripts utilisant Inline XSLT et modèles d’appel XSLT](../core/scripting-using-inline-xslt-and-xslt-call-templates.md) </span><span class="sxs-lookup"><span data-stu-id="c9d47-119">[Scripting Using Inline XSLT and XSLT Call Templates](../core/scripting-using-inline-xslt-and-xslt-call-templates.md) </span></span>  
 <span data-ttu-id="c9d47-120">[Comment ajouter des fonctoids de script à une carte](../core/how-to-add-scripting-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="c9d47-120">[How to Add Scripting Functoids to a Map](../core/how-to-add-scripting-functoids-to-a-map.md) </span></span>  
 [<span data-ttu-id="c9d47-121">Comment configurer le fonctoid script</span><span class="sxs-lookup"><span data-stu-id="c9d47-121">How to Configure the Scripting Functoid</span></span>](../core/how-to-configure-the-scripting-functoid.md)
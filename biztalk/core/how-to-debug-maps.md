---
title: "Comment déboguer des mappages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ee1e26-fced-4126-b48a-71007043424d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e40964b267ad0788308a92490a106f940a6cb33e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-debug-maps"></a><span data-ttu-id="158ba-102">Comment déboguer des mappages</span><span class="sxs-lookup"><span data-stu-id="158ba-102">How to Debug Maps</span></span>
<span data-ttu-id="158ba-103">Le **déboguer le mappage** fonctionnalité est utile pour identifier et résoudre les problèmes de mappage complexes.</span><span class="sxs-lookup"><span data-stu-id="158ba-103">The **Debug Map** feature is useful in identifying and fixing complex mapping issues.</span></span> <span data-ttu-id="158ba-104">Cette rubrique fournit des instructions pas à pas pour déboguer des mappages à l'aide du débogueur inline XSLT.</span><span class="sxs-lookup"><span data-stu-id="158ba-104">This topic provides step-by-step instructions for debugging maps using the inline XSLT debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="158ba-105">Lors du débogage de la carte, le **déboguer le mappage** fonctionnalité utilise les propriétés de fichier de mappage **Instance d’entrée TestMap** et **Instance de sortie TestMap**.</span><span class="sxs-lookup"><span data-stu-id="158ba-105">When debugging the map, the **Debug Map** feature uses the map file properties **TestMap Input Instance** and **TestMap Output Instance**.</span></span> <span data-ttu-id="158ba-106">Par conséquent, avant de déboguer le mappage, nous vous recommandons de configurer les propriétés d'instance d'entrée et de sortie dans le fichier de mappage.</span><span class="sxs-lookup"><span data-stu-id="158ba-106">Therefore, before you debug the map, we recommend that you configure the input and output instance properties in the map file.</span></span>  
  
### <a name="to-debug-a-biztalk-map"></a><span data-ttu-id="158ba-107">Pour déboguer un mappage BizTalk</span><span class="sxs-lookup"><span data-stu-id="158ba-107">To debug a BizTalk map</span></span>  
  
1.  <span data-ttu-id="158ba-108">Dans l’Explorateur de solutions, cliquez sur la carte que vous souhaitez tester, puis cliquez sur **déboguer le mappage**.</span><span class="sxs-lookup"><span data-stu-id="158ba-108">In Solution Explorer, right-click the map you want to test, and then click **Debug Map**.</span></span> [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="158ba-109">Affiche la carte au format XSLT dans son éditeur.</span><span class="sxs-lookup"><span data-stu-id="158ba-109"> displays the map in XSLT format in its editor.</span></span>  
  
2.  <span data-ttu-id="158ba-110">Appuyez sur F10 ou F11 pour déboguer le code XSL.</span><span class="sxs-lookup"><span data-stu-id="158ba-110">Press F10 or F11 to debug the XSL code.</span></span> <span data-ttu-id="158ba-111">Lorsque vous appuyez sur F11 suite à un appel de fonctoid, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] passe dans le code C# pour le fonctoid.</span><span class="sxs-lookup"><span data-stu-id="158ba-111">When you press F11 on a functoid call, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] steps into the C# code for the functoid.</span></span> <span data-ttu-id="158ba-112">Vous pouvez visualiser les valeurs des variables utilisées dans le code source du fonctoid dans le Débogueur local de Windows.</span><span class="sxs-lookup"><span data-stu-id="158ba-112">You can view the values of variables used in the functoid source code in the Local Windows Debugger.</span></span>
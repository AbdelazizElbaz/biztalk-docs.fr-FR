---
title: "Comment utiliser un Assembly .NET comme Source de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Business Rule Composer, data sources
ms.assetid: 14dbec48-acc9-4c3c-bd7f-737dabf29543
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fa56370cf894d0d18a36320ca97c4d028fee487
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-a-net-assembly-as-a-data-source"></a><span data-ttu-id="febcc-102">Utilisation d'un assembly .NET comme source de données</span><span class="sxs-lookup"><span data-stu-id="febcc-102">How to Use a .NET Assembly as a Data Source</span></span>
<span data-ttu-id="febcc-103">Vous pouvez spécifier un assembly .NET en tant que source de données.</span><span class="sxs-lookup"><span data-stu-id="febcc-103">You can specify a .NET assembly as a data source.</span></span> <span data-ttu-id="febcc-104">Vous pouvez ensuite sélectionner une classe ou un membre de classe à partir de l’assembly et le déplacer dans une règle ou une définition.</span><span class="sxs-lookup"><span data-stu-id="febcc-104">You can subsequently select a class or class member from the assembly, and drag it onto a vocabulary definition or rule.</span></span>  
  
### <a name="to-specify-a-net-assembly-as-a-data-source"></a><span data-ttu-id="febcc-105">Pour spécifier un assembly .NET comme source de données </span><span class="sxs-lookup"><span data-stu-id="febcc-105">To specify a .NET assembly as a data source</span></span>  
  
1.  <span data-ttu-id="febcc-106">Dans la fenêtre Explorateur de faits, cliquez sur le **Classes .NET** onglet.</span><span class="sxs-lookup"><span data-stu-id="febcc-106">In the Facts Explorer window, click the **.NET Classes** tab.</span></span>  
  
2.  <span data-ttu-id="febcc-107">Cliquez sur le **Modules** nœud.</span><span class="sxs-lookup"><span data-stu-id="febcc-107">Right-click the **Modules** node.</span></span>  
  
3.  <span data-ttu-id="febcc-108">Parmi les assemblys disponibles, sélectionnez un assembly .NET.</span><span class="sxs-lookup"><span data-stu-id="febcc-108">From the available assemblies, select a .NET assembly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="febcc-109">Les assemblys doivent se trouver dans le Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="febcc-109">The assemblies have to be in the global assembly cache (GAC).</span></span> <span data-ttu-id="febcc-110">L’éditeur des règles d’entreprise charge un assembly .NET lorsque vous recherchez l’assembly .NET dans le **l’Explorateur de faits** fenêtre ou dans le **classe .NET ou définition de membre de classe** page de la **vocabulaire Définition** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="febcc-110">The business rule composer loads a .NET assembly when you browse for the .NET assembly in the **Facts Explorer** window or in the **.NET Class or Class Member Definition** page of the **Vocabulary Definition** window.</span></span>  <span data-ttu-id="febcc-111">Si vous mettez à jour l'assembly dans le GAC, fermez l'Éditeur des règles d'entreprise et redémarrez-le afin de charger l'assembly .NET mis à jour.</span><span class="sxs-lookup"><span data-stu-id="febcc-111">If you update the assembly in the GAC, close the business rule composer and restart it to load the updated .NET assembly.</span></span> <span data-ttu-id="febcc-112">L'actualisation n'est en effet pas automatique.</span><span class="sxs-lookup"><span data-stu-id="febcc-112">The business rule composer does not refresh the assembly automatically.</span></span>  
  
     <span data-ttu-id="febcc-113">![Capture d’écran de faits de l’Explorateur d’arborescence de la définition. ] (../core/media/ebiz-netbrowse.gif "ebiz_netbrowse")</span><span class="sxs-lookup"><span data-stu-id="febcc-113">![Screenshot of facts and definition tree browser.](../core/media/ebiz-netbrowse.gif "ebiz_netbrowse")</span></span>
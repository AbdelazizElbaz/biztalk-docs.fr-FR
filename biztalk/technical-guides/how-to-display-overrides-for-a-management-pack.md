---
title: "Comment afficher les remplacements d’un Pack d’administration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8261a514-b4c4-4e6b-ac35-40a3e3e090e0
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a28c4ab2ef8f82fdd770203816239ad78e74418e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-display-overrides-for-a-management-pack"></a><span data-ttu-id="a80d7-102">Comment afficher les remplacements d’un Pack d’administration</span><span class="sxs-lookup"><span data-stu-id="a80d7-102">How to Display Overrides for a Management Pack</span></span>
<span data-ttu-id="a80d7-103">Pour afficher les remplacements d’un Pack d’administration, utilisez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="a80d7-103">To display overrides for a management pack, use the following procedure.</span></span>  
  
### <a name="to-display-overrides-for-a-management-pack"></a><span data-ttu-id="a80d7-104">Pour afficher les remplacements d’un Pack d’administration</span><span class="sxs-lookup"><span data-stu-id="a80d7-104">To display overrides for a management pack</span></span>  
  
1.  <span data-ttu-id="a80d7-105">Dans votre serveur d’administration, cliquez sur **programmes**, puis cliquez sur **System Center**.</span><span class="sxs-lookup"><span data-stu-id="a80d7-105">In your management server, click **Programs**, and then click **System Center**.</span></span>  
  
2.  <span data-ttu-id="a80d7-106">Cliquez sur **interface de commande**.</span><span class="sxs-lookup"><span data-stu-id="a80d7-106">Click **Command Shell**.</span></span>  
  
3.  <span data-ttu-id="a80d7-107">Dans l’interface de commande, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a80d7-107">In the Command Shell, type the following command:</span></span>   
    `$mp = get-scommanagementpack -DisplayName "Operations Manager Internal Library"`   
    `$mp.GetOverrides()`  
  
4.  <span data-ttu-id="a80d7-108">Un fichier .csv est créé.</span><span class="sxs-lookup"><span data-stu-id="a80d7-108">A .csv file is created.</span></span> <span data-ttu-id="a80d7-109">Le fichier .csv peut être ouvert dans Office Excel.</span><span class="sxs-lookup"><span data-stu-id="a80d7-109">The .csv file can be opened in Office Excel.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a80d7-110">Dans Office Excel, vous pouvez être nécessaire de spécifier que le fichier .csv est un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="a80d7-110">In Office Excel, you may be required to specify that the .csv file is a text file.</span></span>  
  
 <span data-ttu-id="a80d7-111">Par exemple, la commande suivante affiche les remplacements pour un des packs d’administration principaux :</span><span class="sxs-lookup"><span data-stu-id="a80d7-111">For example, the following command displays the overrides for one of the core management packs:</span></span>   
`$mp = get-scommanagementpack -DisplayName "Contoso.BizTalk.Overrides.mp"`  
`$mp.GetOverrides()`
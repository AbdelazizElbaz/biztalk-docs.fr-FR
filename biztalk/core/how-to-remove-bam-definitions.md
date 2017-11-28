---
title: "Comment supprimer des définitions BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- definitions [BAM], deleting
- deleting, definitions [BAM]
- managing [BAM definitions], deleting definitions
- Remove-All command
ms.assetid: a905f54b-7c55-49b8-809b-030ad65f3e46
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bce5454528b3dc1cf0feb54a52eae2008e607811
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-bam-definitions"></a><span data-ttu-id="6c105-102">Suppression de définitions BAM</span><span class="sxs-lookup"><span data-stu-id="6c105-102">How to Remove BAM Definitions</span></span>
<span data-ttu-id="6c105-103">Les administrateurs utilisent la **remove-all** commande de l’utilitaire de gestion BAM pour supprimer toutes les vues et tables d’activité sous-jacentes d’un fichier de définition BAM spécifique.</span><span class="sxs-lookup"><span data-stu-id="6c105-103">Administrators use the **remove-all** command of the BAM Management utility to remove all views and underlying activity tables for a particular BAM definition file.</span></span>  
  
### <a name="to-remove-bam-definitions"></a><span data-ttu-id="6c105-104">Pour supprimer des définitions BAM</span><span class="sxs-lookup"><span data-stu-id="6c105-104">To Remove BAM definitions</span></span>  
  
1.  <span data-ttu-id="6c105-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c105-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="6c105-106">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="6c105-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="6c105-107">Type **bm remove-all DefinitionFile :\<fichier def >**.</span><span class="sxs-lookup"><span data-stu-id="6c105-107">Type **bm remove-all DefinitionFile:\<def file>**.</span></span>  
  
4.  <span data-ttu-id="6c105-108">Appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="6c105-108">Press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c105-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c105-109">See Also</span></span>  
 <span data-ttu-id="6c105-110">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="6c105-110">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="6c105-111">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="6c105-111">BAM Management Utility</span></span>](../core/bam-management-utility.md)
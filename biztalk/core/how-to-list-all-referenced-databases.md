---
title: "Comment répertorier toutes les bases de données référencées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f6166dd-6228-45c2-98ef-4de2a4345189
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69c6411378311892f85821a3e86d65a85f909d0a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-list-all-referenced-databases"></a><span data-ttu-id="31d6e-102">Génération de la liste de toutes les bases de données référencées</span><span class="sxs-lookup"><span data-stu-id="31d6e-102">How to List All Referenced Databases</span></span>
<span data-ttu-id="31d6e-103">Les administrateurs utilisent la **get-references** commande pour répertorier toutes les bases de données d’importation principale BAM sur d’autres serveurs BizTalk qui ont été attribuées des références à la base de données d’importation principale BAM locale.</span><span class="sxs-lookup"><span data-stu-id="31d6e-103">Administrators use the **get-references** command to list all of the BAM Primary Import databases on other BizTalk servers that have been given references to the local BAM Primary Import database.</span></span>  
  
### <a name="to-list-all-referenced-databases"></a><span data-ttu-id="31d6e-104">Pour répertorier toutes les bases de données référencées</span><span class="sxs-lookup"><span data-stu-id="31d6e-104">To list all referenced databases</span></span>  
  
1.  <span data-ttu-id="31d6e-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="31d6e-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="31d6e-106">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="31d6e-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="31d6e-107">Tapez la commande suivante à l’invite de ligne de commande : **bm.exe get-references**.</span><span class="sxs-lookup"><span data-stu-id="31d6e-107">Type the following at the command line prompt: **bm.exe get-references**.</span></span> <span data-ttu-id="31d6e-108">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="31d6e-108">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d6e-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31d6e-109">See Also</span></span>  
 [<span data-ttu-id="31d6e-110">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="31d6e-110">BAM Management Utility</span></span>](../core/bam-management-utility.md)
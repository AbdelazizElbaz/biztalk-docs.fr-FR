---
title: "Comment référencer des bases de données importation principale BAM supplémentaire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea80b32c-f2cb-4aca-89f4-d5b72e1ba021
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be973777fda6fad83b4ed6c672b68969cdde5919
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-reference-additional-bam-primary-import-databases"></a><span data-ttu-id="ebeed-102">Création de références à des bases de données d'importation principales BAM supplémentaires</span><span class="sxs-lookup"><span data-stu-id="ebeed-102">How to Reference Additional BAM Primary Import Databases</span></span>
<span data-ttu-id="ebeed-103">Les administrateurs utilisent la **enable-reference** commande référencer d’autres bases de données importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="ebeed-103">Administrators use the **enable-reference** command to reference additional BAM Primary Import databases.</span></span> <span data-ttu-id="ebeed-104">Vous pouvez référencer plusieurs bases de données d'importation principales BAM pour faciliter l'affichage d'activités BAM distribuées.</span><span class="sxs-lookup"><span data-stu-id="ebeed-104">You reference multiple BAM Primary Import databases to facilitate viewing distributed BAM activities.</span></span>  
  
### <a name="to-enable-a-reference-to-an-additional-bam-primary-import-database"></a><span data-ttu-id="ebeed-105">Pour activer une référence à une base de données d'importation principale BAM supplémentaire</span><span class="sxs-lookup"><span data-stu-id="ebeed-105">To enable a reference to an additional BAM Primary Import database</span></span>  
  
1.  <span data-ttu-id="ebeed-106">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ebeed-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="ebeed-107">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="ebeed-107">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="ebeed-108">Tapez la commande suivante à l’invite de ligne de commande : **bm enable-reference - TargetServer :\<serveur cible > - TargetDatabase :\<base de données cible >**, où \< *cible serveur*> est remplacé par le nom du serveur SQL sur lequel la base de données importation principale BAM cible spécifiée par \<base de données cible > réside.</span><span class="sxs-lookup"><span data-stu-id="ebeed-108">Type the following at the command line prompt: **bm enable-reference -TargetServer:\<target server> -TargetDatabase:\<target database>**, where \<*target server*> is replaced by the name of the SQL server on which the target BAM Primary Import database specified by \<target database> resides.</span></span> <span data-ttu-id="ebeed-109">Appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="ebeed-109">Press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebeed-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebeed-110">See Also</span></span>  
 [<span data-ttu-id="ebeed-111">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="ebeed-111">BAM Management Utility</span></span>](../core/bam-management-utility.md)
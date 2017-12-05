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
ms.openlocfilehash: fca916339e48f6bce053753111f4467a4c9ae7d5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-reference-additional-bam-primary-import-databases"></a><span data-ttu-id="a38f6-102">Création de références à des bases de données d'importation principales BAM supplémentaires</span><span class="sxs-lookup"><span data-stu-id="a38f6-102">How to Reference Additional BAM Primary Import Databases</span></span>
<span data-ttu-id="a38f6-103">Les administrateurs utilisent la **enable-reference** commande référencer d’autres bases de données importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="a38f6-103">Administrators use the **enable-reference** command to reference additional BAM Primary Import databases.</span></span> <span data-ttu-id="a38f6-104">Vous pouvez référencer plusieurs bases de données d'importation principales BAM pour faciliter l'affichage d'activités BAM distribuées.</span><span class="sxs-lookup"><span data-stu-id="a38f6-104">You reference multiple BAM Primary Import databases to facilitate viewing distributed BAM activities.</span></span>  
  
### <a name="to-enable-a-reference-to-an-additional-bam-primary-import-database"></a><span data-ttu-id="a38f6-105">Pour activer une référence à une base de données d'importation principale BAM supplémentaire</span><span class="sxs-lookup"><span data-stu-id="a38f6-105">To enable a reference to an additional BAM Primary Import database</span></span>  
  
1.  <span data-ttu-id="a38f6-106">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a38f6-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="a38f6-107">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="a38f6-107">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="a38f6-108">Tapez la commande suivante à l’invite de ligne de commande : **bm enable-reference - TargetServer :\<serveur cible\> - TargetDatabase :\<base de données cible\>**, où \< *serveur cible* \> est remplacé par le nom du serveur SQL sur lequel la base de données importation principale BAM cible spécifiée par \<base de données cible\> réside.</span><span class="sxs-lookup"><span data-stu-id="a38f6-108">Type the following at the command line prompt: **bm enable-reference -TargetServer:\<target server\> -TargetDatabase:\<target database\>**, where \<*target server*\> is replaced by the name of the SQL server on which the target BAM Primary Import database specified by \<target database\> resides.</span></span> <span data-ttu-id="a38f6-109">Appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="a38f6-109">Press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a38f6-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a38f6-110">See Also</span></span>  
 [<span data-ttu-id="a38f6-111">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="a38f6-111">BAM Management Utility</span></span>](../core/bam-management-utility.md)
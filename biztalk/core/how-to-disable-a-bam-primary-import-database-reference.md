---
title: "Comment désactiver une référence de base de données d’importation principale BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d2d644-6ebb-4051-ae59-af7d0fb75753
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6efa79822f6a5406db29c69b5ba0892a63bcc5f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-disable-a-bam-primary-import-database-reference"></a><span data-ttu-id="c4e18-102">Désactivation d'une référence à une base de données d'importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="c4e18-102">How to Disable a BAM Primary Import Database Reference</span></span>
<span data-ttu-id="c4e18-103">Les administrateurs utilisent la **disable-reference** commande pour désactiver une référence à une base de données d’importation principale BAM spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c4e18-103">Administrators use the **disable-reference** command to disable a reference to a specified BAM Primary Import database.</span></span>  
  
### <a name="to-disable-a-reference-to-a-bam-primary-import-database"></a><span data-ttu-id="c4e18-104">Pour désactiver une référence à une base de données d'importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="c4e18-104">To disable a reference to a BAM Primary Import database</span></span>  
  
1.  <span data-ttu-id="c4e18-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c4e18-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="c4e18-106">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="c4e18-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="c4e18-107">Tapez la commande suivante à l’invite de ligne de commande : **bm disable-reference - TargetServer :\<serveur cible > - TargetDatabase :\<base de données cible > [-Server :\<serveur >] [-base de données :\< base de données >]**, où  **\<**  *serveur cible*  **>**  est remplacé par le nom du serveur SQL sur lequel la base de données importation principale BAM cible spécifiée par \< *base de données cible*> réside.</span><span class="sxs-lookup"><span data-stu-id="c4e18-107">Type the following at the command line prompt: **bm disable-reference -TargetServer:\<target server> -TargetDatabase:\<target database>[ -Server:\<server> ][ -Database:\<database> ]**, where **\<***target server***>** is replaced by the name of the SQL server on which the target BAM Primary Import database specified by \<*target database*> resides.</span></span> <span data-ttu-id="c4e18-108">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="c4e18-108">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e18-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4e18-109">See Also</span></span>  
 [<span data-ttu-id="c4e18-110">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="c4e18-110">BAM Management Utility</span></span>](../core/bam-management-utility.md)
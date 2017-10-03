---
title: "Comment mettre à jour la Configuration BAM à l’aide de l’utilitaire de gestion BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 714a834e-1879-4019-9b54-e511705bd67a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee5958120e364cc0c2661ead6100bd2ba5502226
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-the-bam-configuration-using-the-bam-management-utility"></a><span data-ttu-id="b5235-102">Mise à jour de la configuration BAM à l'aide de l'utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="b5235-102">How to Update the BAM Configuration Using the BAM Management Utility</span></span>
<span data-ttu-id="b5235-103">Les administrateurs peuvent utiliser l'utilitaire de gestion de l'analyse BAM pour mettre à jour une installation BAM existante.</span><span class="sxs-lookup"><span data-stu-id="b5235-103">Administrators can use the BAM Management utility to update an existing BAM installation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b5235-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b5235-104">Prerequisites</span></span>  
 <span data-ttu-id="b5235-105">Vous devez disposer des autorisations d'administrateur sur la base de données BAM mise à jour.</span><span class="sxs-lookup"><span data-stu-id="b5235-105">You must have Administrator permissions on the BAM database being updated.</span></span>  
  
### <a name="to-update-the-bam-configuration-using-the-bam-management-utility"></a><span data-ttu-id="b5235-106">Pour mettre à jour la configuration BAM à l'aide de l'utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="b5235-106">To update the BAM configuration using the BAM Management utility</span></span>  
  
1.  <span data-ttu-id="b5235-107">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b5235-107">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="b5235-108">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="b5235-108">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="b5235-109">Tapez la commande suivante à l’invite de ligne de commande : **bm update-config - FileName :\<le fichier de configuration >**, où \< *fichier de configuration*> est remplacé par le nom de votre analyse BAM fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="b5235-109">Type the following at the command line prompt: **bm update-config -FileName:\<config file>**, where \<*configuration file*> is replaced by the name of your BAM configuration file.</span></span> <span data-ttu-id="b5235-110">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="b5235-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5235-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5235-111">See Also</span></span>  
 [<span data-ttu-id="b5235-112">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="b5235-112">BAM Management Utility</span></span>](../core/bam-management-utility.md)
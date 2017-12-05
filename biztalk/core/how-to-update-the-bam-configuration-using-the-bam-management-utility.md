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
ms.openlocfilehash: b08209d3b3a1555bbc674e469ea9f8a4b1f81a9d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-update-the-bam-configuration-using-the-bam-management-utility"></a><span data-ttu-id="beb9b-102">Mise à jour de la configuration BAM à l'aide de l'utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="beb9b-102">How to Update the BAM Configuration Using the BAM Management Utility</span></span>
<span data-ttu-id="beb9b-103">Les administrateurs peuvent utiliser l'utilitaire de gestion de l'analyse BAM pour mettre à jour une installation BAM existante.</span><span class="sxs-lookup"><span data-stu-id="beb9b-103">Administrators can use the BAM Management utility to update an existing BAM installation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="beb9b-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="beb9b-104">Prerequisites</span></span>  
 <span data-ttu-id="beb9b-105">Vous devez disposer des autorisations d'administrateur sur la base de données BAM mise à jour.</span><span class="sxs-lookup"><span data-stu-id="beb9b-105">You must have Administrator permissions on the BAM database being updated.</span></span>  
  
### <a name="to-update-the-bam-configuration-using-the-bam-management-utility"></a><span data-ttu-id="beb9b-106">Pour mettre à jour la configuration BAM à l'aide de l'utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="beb9b-106">To update the BAM configuration using the BAM Management utility</span></span>  
  
1.  <span data-ttu-id="beb9b-107">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="beb9b-107">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="beb9b-108">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="beb9b-108">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="beb9b-109">Tapez la commande suivante à l’invite de ligne de commande : **bm update-config - FileName :\<le fichier de configuration\>**, où \< *fichier de configuration* \> est remplacé par le nom de votre fichier de configuration BAM.</span><span class="sxs-lookup"><span data-stu-id="beb9b-109">Type the following at the command line prompt: **bm update-config -FileName:\<config file\>**, where \<*configuration file*\> is replaced by the name of your BAM configuration file.</span></span> <span data-ttu-id="beb9b-110">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="beb9b-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb9b-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="beb9b-111">See Also</span></span>  
 [<span data-ttu-id="beb9b-112">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="beb9b-112">BAM Management Utility</span></span>](../core/bam-management-utility.md)
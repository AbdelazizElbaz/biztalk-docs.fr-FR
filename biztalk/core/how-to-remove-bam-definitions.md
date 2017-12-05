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
ms.openlocfilehash: aa02b24ed7d0c7ac09162f486df629bf027d13b9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-remove-bam-definitions"></a><span data-ttu-id="32770-102">Suppression de définitions BAM</span><span class="sxs-lookup"><span data-stu-id="32770-102">How to Remove BAM Definitions</span></span>
<span data-ttu-id="32770-103">Les administrateurs utilisent la **remove-all** commande de l’utilitaire de gestion BAM pour supprimer toutes les vues et tables d’activité sous-jacentes d’un fichier de définition BAM spécifique.</span><span class="sxs-lookup"><span data-stu-id="32770-103">Administrators use the **remove-all** command of the BAM Management utility to remove all views and underlying activity tables for a particular BAM definition file.</span></span>  
  
### <a name="to-remove-bam-definitions"></a><span data-ttu-id="32770-104">Pour supprimer des définitions BAM</span><span class="sxs-lookup"><span data-stu-id="32770-104">To Remove BAM definitions</span></span>  
  
1.  <span data-ttu-id="32770-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="32770-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="32770-106">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="32770-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="32770-107">Type **bm remove-all DefinitionFile :\<fichier def\>**.</span><span class="sxs-lookup"><span data-stu-id="32770-107">Type **bm remove-all DefinitionFile:\<def file\>**.</span></span>  
  
4.  <span data-ttu-id="32770-108">Appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="32770-108">Press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32770-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32770-109">See Also</span></span>  
 <span data-ttu-id="32770-110">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="32770-110">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="32770-111">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="32770-111">BAM Management Utility</span></span>](../core/bam-management-utility.md)
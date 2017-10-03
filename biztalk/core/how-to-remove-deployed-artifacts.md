---
title: "Comment supprimer des artefacts déployés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM definitions], undeploying artifacts
- Remove-All command
- undeploying, artifacts [BAM]
- artifacts, undeploying [BAM]
ms.assetid: 90135965-d18e-4a71-9877-d2b0c3caf59f
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2a134e41c8f94c875498db03866d16a45bb9bc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-deployed-artifacts"></a><span data-ttu-id="8f9ac-102">Suppression d'artefacts déployés</span><span class="sxs-lookup"><span data-stu-id="8f9ac-102">How to Remove Deployed Artifacts</span></span>
<span data-ttu-id="8f9ac-103">Les administrateurs utilisent la **remove-all** commande pour supprimer les artefacts déployés dans la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="8f9ac-103">Administrators use the **remove-all** command to remove artifacts deployed in the BAM Primary Import database.</span></span> <span data-ttu-id="8f9ac-104">La définition d'analyse BAM fournie est soit un fichier XML soit un classeur Excel contenant des informations sur les artefacts à supprimer.</span><span class="sxs-lookup"><span data-stu-id="8f9ac-104">The supplied BAM definition is either an XML file or an Excel Workbook containing information about the artifacts to be removed.</span></span>  
  
### <a name="to-remove-deployed-artifacts"></a><span data-ttu-id="8f9ac-105">Pour supprimer des artefacts déployés</span><span class="sxs-lookup"><span data-stu-id="8f9ac-105">To remove deployed artifacts</span></span>  
  
1.  <span data-ttu-id="8f9ac-106">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8f9ac-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="8f9ac-107">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="8f9ac-107">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="8f9ac-108">Type **bm remove-all - DefinitionFile :\<fichier def >**.</span><span class="sxs-lookup"><span data-stu-id="8f9ac-108">Type **bm remove-all -DefinitionFile:\<def file>**.</span></span>  
  
4.  <span data-ttu-id="8f9ac-109">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="8f9ac-109">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f9ac-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f9ac-110">See Also</span></span>  
 <span data-ttu-id="8f9ac-111">[Comment ajouter un artefact BAM à une Application](../core/how-to-add-a-bam-artifact-to-an-application.md) </span><span class="sxs-lookup"><span data-stu-id="8f9ac-111">[How to Add a BAM Artifact to an Application](../core/how-to-add-a-bam-artifact-to-an-application.md) </span></span>  
 <span data-ttu-id="8f9ac-112">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="8f9ac-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="8f9ac-113">[Recommandations de sécurité BAM](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="8f9ac-113">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="8f9ac-114">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="8f9ac-114">BAM Management Utility</span></span>](../core/bam-management-utility.md)
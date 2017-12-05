---
title: "Comment mettre à jour des artefacts BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Update-All command [BAM]
- managing [BAM definitions], updating artifacts
- updating, artifacts
- artifacts, updating
ms.assetid: bc28159e-df51-499b-bd51-7b682b849891
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f80499881c075c805bc5949942644dcece5075fb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-update-bam-artifacts"></a><span data-ttu-id="97409-102">Mise à jour des artefacts BAM</span><span class="sxs-lookup"><span data-stu-id="97409-102">How to Update BAM Artifacts</span></span>
<span data-ttu-id="97409-103">Les administrateurs utilisent la **mise à jour-all** commande pour mettre à jour des artefacts déployés dans la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="97409-103">Administrators use the **update-all** command to update artifacts deployed in the BAM Primary Import database.</span></span> <span data-ttu-id="97409-104">La définition d'analyse BAM fournie est soit un fichier XML soit un classeur Excel contenant des informations sur les artefacts à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="97409-104">The supplied BAM definition is either an XML file or an Excel Workbook containing information about the artifacts to be updated.</span></span>  
  
### <a name="to-update-bam-artifacts"></a><span data-ttu-id="97409-105">Pour mettre à jour des artefacts BAM</span><span class="sxs-lookup"><span data-stu-id="97409-105">To update BAM Artifacts</span></span>  
  
1.  <span data-ttu-id="97409-106">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="97409-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="97409-107">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="97409-107">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="97409-108">Type **bm update-all - DefinitionFile :\<fichier def\>**.</span><span class="sxs-lookup"><span data-stu-id="97409-108">Type **bm update-all -DefinitionFile:\<def file\>**.</span></span>  
  
4.  <span data-ttu-id="97409-109">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="97409-109">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97409-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97409-110">See Also</span></span>  
 <span data-ttu-id="97409-111">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="97409-111">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="97409-112">[Recommandations de sécurité BAM](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="97409-112">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="97409-113">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="97409-113">BAM Management Utility</span></span>](../core/bam-management-utility.md)
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
ms.openlocfilehash: f1d3e395223840dd4caa534130061fac33e89b78
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-remove-deployed-artifacts"></a>Suppression d'artefacts déployés
Les administrateurs utilisent la **remove-all** commande pour supprimer les artefacts déployés dans la base de données d’importation principale BAM. La définition d'analyse BAM fournie est soit un fichier XML soit un classeur Excel contenant des informations sur les artefacts à supprimer.  
  
### <a name="to-remove-deployed-artifacts"></a>Pour supprimer des artefacts déployés  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3.  Type **bm remove-all - DefinitionFile :\<fichier def\>**.  
  
4.  Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment ajouter un artefact BAM à une Application](../core/how-to-add-a-bam-artifact-to-an-application.md)   
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Recommandations de sécurité BAM](../core/bam-security-recommendations.md)   
 [Utilitaire de gestion de l’analyse BAM](../core/bam-management-utility.md)
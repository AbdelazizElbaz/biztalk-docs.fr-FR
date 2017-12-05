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
# <a name="how-to-update-bam-artifacts"></a>Mise à jour des artefacts BAM
Les administrateurs utilisent la **mise à jour-all** commande pour mettre à jour des artefacts déployés dans la base de données d’importation principale BAM. La définition d'analyse BAM fournie est soit un fichier XML soit un classeur Excel contenant des informations sur les artefacts à mettre à jour.  
  
### <a name="to-update-bam-artifacts"></a>Pour mettre à jour des artefacts BAM  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3.  Type **bm update-all - DefinitionFile :\<fichier def\>**.  
  
4.  Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Recommandations de sécurité BAM](../core/bam-security-recommendations.md)   
 [Utilitaire de gestion de l’analyse BAM](../core/bam-management-utility.md)
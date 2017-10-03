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
ms.openlocfilehash: bce5454528b3dc1cf0feb54a52eae2008e607811
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-bam-definitions"></a>Suppression de définitions BAM
Les administrateurs utilisent la **remove-all** commande de l’utilitaire de gestion BAM pour supprimer toutes les vues et tables d’activité sous-jacentes d’un fichier de définition BAM spécifique.  
  
### <a name="to-remove-bam-definitions"></a>Pour supprimer des définitions BAM  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3.  Type **bm remove-all DefinitionFile :\<fichier def >**.  
  
4.  Appuyez sur Entrée.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)
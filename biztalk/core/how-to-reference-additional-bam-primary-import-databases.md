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
ms.openlocfilehash: be973777fda6fad83b4ed6c672b68969cdde5919
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-reference-additional-bam-primary-import-databases"></a>Création de références à des bases de données d'importation principales BAM supplémentaires
Les administrateurs utilisent la **enable-reference** commande référencer d’autres bases de données importation principale BAM. Vous pouvez référencer plusieurs bases de données d'importation principales BAM pour faciliter l'affichage d'activités BAM distribuées.  
  
### <a name="to-enable-a-reference-to-an-additional-bam-primary-import-database"></a>Pour activer une référence à une base de données d'importation principale BAM supplémentaire  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3.  Tapez la commande suivante à l’invite de ligne de commande : **bm enable-reference - TargetServer :\<serveur cible > - TargetDatabase :\<base de données cible >**, où \< *cible serveur*> est remplacé par le nom du serveur SQL sur lequel la base de données importation principale BAM cible spécifiée par \<base de données cible > réside. Appuyez sur Entrée.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)
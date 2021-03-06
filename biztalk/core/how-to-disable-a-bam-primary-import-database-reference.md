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
ms.openlocfilehash: fc9afef7bdcfad84f105abda158c5ed5c6461619
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-disable-a-bam-primary-import-database-reference"></a>Désactivation d'une référence à une base de données d'importation principale BAM
Les administrateurs utilisent la **disable-reference** commande pour désactiver une référence à une base de données d’importation principale BAM spécifiée.  
  
### <a name="to-disable-a-reference-to-a-bam-primary-import-database"></a>Pour désactiver une référence à une base de données d'importation principale BAM  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3.  Tapez la commande suivante à l’invite de ligne de commande : **bm disable-reference - TargetServer :\<serveur cible\> - TargetDatabase :\<base de données cible\>[-Server :\<server\> ] [-Base de données :\<base de données\> ]**, où  **\<**  *serveur cible*  **\>**  est remplacé par le nom du serveur SQL sur lequel la base de données importation principale BAM cible spécifiée par \< *base de données cible* \> réside. Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion de l’analyse BAM](../core/bam-management-utility.md)
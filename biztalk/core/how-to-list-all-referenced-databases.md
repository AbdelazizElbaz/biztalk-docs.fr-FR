---
title: "Comment répertorier toutes les bases de données référencées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f6166dd-6228-45c2-98ef-4de2a4345189
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69c6411378311892f85821a3e86d65a85f909d0a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-list-all-referenced-databases"></a>Génération de la liste de toutes les bases de données référencées
Les administrateurs utilisent la **get-references** commande pour répertorier toutes les bases de données d’importation principale BAM sur d’autres serveurs BizTalk qui ont été attribuées des références à la base de données d’importation principale BAM locale.  
  
### <a name="to-list-all-referenced-databases"></a>Pour répertorier toutes les bases de données référencées  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3.  Tapez la commande suivante à l’invite de ligne de commande : **bm.exe get-references**. Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)
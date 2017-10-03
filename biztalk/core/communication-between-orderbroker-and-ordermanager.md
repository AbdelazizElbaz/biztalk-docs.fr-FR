---
title: Communication entre OrderBroker et OrderManager | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, publishing [MessageBox database]
- MessageBox database, publishing
ms.assetid: 1b77dcd2-f7a5-4013-b9a2-c06ace161792
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f438b0dfe744aae5867943f4b1493bb163994f4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="communication-between-orderbroker-and-ordermanager"></a>Communication entre OrderBroker et OrderManager
Le courtier de commandes et les orchestrations du Gestionnaire de commandes (**OrderBroker**, **OrderManager**) communiquent via la MessageBox de base de données plutôt que liaison directe entre partenaires. Le courtier et le gestionnaire sont ainsi faiblement couplés de sorte qu'ils puissent, le cas échéant, se trouver dans des groupes BizTalk et des emplacements géographiques distincts. Une telle séparation des orchestrations demande uniquement une configuration administrative et ne requiert aucune modification au niveau du code.  
  
 La configuration actuelle de la solution permet au courtier de commandes de marquer les messages destinés à un gestionnaire de commandes particulier et de les envoyer vers MessageBox. Le gestionnaire de commandes effectue ensuite un filtrage des messages pour obtenir ceux qui lui sont destinés, puis il les récupère dans MessageBox. Ce détour (à savoir la communication via MessageBox plutôt que par une liaison directe) simplifie le déplacement du courtier et du gestionnaire dans des groupes distincts.  
  
 Si la gestion du courtier et du gestionnaire est effectuée par plusieurs groupes ou si ces deux éléments doivent être situés dans des emplacements géographiques distincts, une telle conception permet répondre facilement à cette exigence. Il vous suffit simplement de déplacer les orchestrations dans des groupes BizTalk distincts. Après avoir séparé les orchestrations, vous devez les reconnecter en créant des ports. Dans le groupe du courtier de commandes, vous devez créer un port d'envoi qui dispose du même filtre que celui du gestionnaire de commandes ; cette opération permet de transférer un message vers le nouveau groupe. Dans le groupe du gestionnaire de commandes, vous devez créer un port de réception pour ce message chargé de placer ce dernier dans la base de données MessageBox.  
  
 Vous pouvez déplacer les applications en les exportant dans deux fichiers MSI, un pour le courtier et un pour le gestionnaire. Pour plus d’informations sur l’exportation d’applications, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise](../core/implementation-highlights-of-the-business-process-management-solution.md)
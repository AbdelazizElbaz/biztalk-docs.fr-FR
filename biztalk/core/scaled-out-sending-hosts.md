---
title: "Montée en charge des hôtes d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosts, sending
- FTP adapters, high availability
- EDI adapters, high availability
- hosts, high availability
- hosts, availability
- Windows SharePoint Services adapters, high availability
- scaling, hosts
- hosts, clustering
- scaling, adapters
- high availability, hosts
- clustering, hosts
- MSMQ adapters, high availability
- hosts, planning
- hosts, scaling
- adapters, scaling
ms.assetid: a3d79e0b-8c1e-471c-88e2-623600dfd81a
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50659e267731caafe4bad6dabe89944cb16c0c98
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="scaled-out-sending-hosts"></a>Mise à l'échelle des hôtes d'envoi
Un hôte d'envoi mis à l'échelle garantit que la fonctionnalité d'envoi de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est hautement disponible. Si vous ajoutez plusieurs ordinateurs à un hôte afin d'envoyer des messages, vous pouvez exécuter plusieurs instances de l'hôte d'envoi et ainsi obtenir une redondance et une disponibilité élevée.  
  
 Le schéma suivant montre un déploiement de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournissant une disponibilité élevée à l'hôte d'envoi grâce à l'utilisation de deux ordinateurs pour exécuter ses instances. Remarquez que les hôtes de traitement et de réception représentés ici ne sont pas des hôtes hautement disponibles.  
  
 ![Mise à l’échelle &#45; un envoi hôte](../core/media/tdi-ha-scalesend.gif "TDI_HA_ScaleSend")  
  
## <a name="high-availability-for-sending-hosts"></a>Configuration de la haute disponibilité pour des hôtes d'envoi  
 La fonctionnalité d'envoi de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est semblable à celle du traitement dans la mesure où ni l'une ni l'autre ne requiert une association entre l'hôte et les données. De même qu'une instance de l'hôte de traitement peut extraire des messages de la base de données MessageBox pour les traiter, une instance de l'hôte d'envoi peut récupérer des messages de cette base de données pour les envoyer. Par conséquent, doter les hôtes d'envoi de la haute disponibilité revient à utiliser les mêmes techniques que celles utilisées pour rendre les hôtes de traitement hautement disponibles.  
  
## <a name="scaling-the-biztalk-server-send-adapters"></a>Mise à l'échelle des adaptateurs d'envoi de BizTalk Server  
  
### <a name="high-availability-for-the-msmq-send-adapter"></a>Configuration de la haute disponibilité pour l'adaptateur d'envoi MSMQ  
 Pour obtenir un adaptateur d'envoi MSMQ haute disponibilité, mettez les services MSMQ et un hôte BizTalk en cluster dans le même groupe, puis configurez le gestionnaire d'envoi afin qu'il s'exécute dans ce cluster. Cette opération doit être effectuée afin de garantir la cohérence des envois transactionnels lancés par l'adaptateur MSMQ. Pour plus d’informations, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).  
  
### <a name="high-availability-for-the-windows-sharepoint-services-send-adapter"></a>Configuration de la haute disponibilité pour l'adaptateur d'envoi Windows SharePoint Services  
 Pour assurer la haute disponibilité à l'adaptateur d'envoi Windows SharePoint Services, ajoutez plusieurs ordinateurs à l'hôte d'envoi et assurez-vous que le port d'envoi de chaque ordinateur fait référence à la même bibliothèque de documents. L’adaptateur Windows SharePoint Services envoie des messages à SharePoint en appelant le service web de Windows SharePoint Services installé par BizTalk Server sur l’ordinateur SharePoint. BizTalk Server offre une haute disponibilité pour l’adaptateur d’envoi SharePoint en vous permettant de procéder à l’envoi du même ports sur plusieurs instances d’hôte transmettre des messages à la même URL HTTP pointant vers une installation SharePoint NLB.  
  
## <a name="see-also"></a>Voir aussi  
 [Offrant une haute disponibilité pour les hôtes BizTalk](../core/providing-high-availability-for-biztalk-hosts.md)   
 [Éléments à prendre en compte pour l’exécution des gestionnaires d’adaptateur au sein d’un hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)
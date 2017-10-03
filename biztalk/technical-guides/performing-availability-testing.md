---
title: "Exécution de tests de disponibilité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10b543dd-ba85-40da-8c6f-485eddb59158
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6f0d9b1cb7b38ab8a1173ee227a8202812048f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="performing-availability-testing"></a>Exécution de tests de disponibilité
Vous devez tester votre système pour la récupération d’urgence vérifier sa capacité à récupérer à partir de différents niveaux d’échec, allant des échecs à petite échelle (par exemple, une défaillance de la carte réseau) à la perte d’un serveur de production. Votre test de la récupération d’urgence doit inclure les étapes suivantes :  
  
-   **Test de défaillance d’un composant matériel.**  
  
     Vous devez tester la capacité du système à restaurer à partir d’une défaillance de composant matériel, tel qu’un réseau ou un disque.  
  
-   **Test de défaillance du serveur BizTalk unique.**  
  
     Dans la plupart des [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les environnements de production, traitement de l’hôte est réparti entre plusieurs ordinateurs en cours d’exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un seul groupe BizTalk. Quelle est la possibilité de continuer le traitement de l’événement de l’hôte du groupe BizTalk, un des serveurs dans le groupe échoue ?  
  
-   **Test de basculement de nœud de cluster.**  
  
     Si le Clustering Windows est utilisé pour fournir une haute disponibilité pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données ou des hôtes BizTalk, vous devez vérifier la fonctionnalité de basculement de nœud de cluster. Pour plus d’informations sur l’utilisation de Clustering Windows pour fournir une haute disponibilité pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [liste de vérification : fournir une haute disponibilité avec une tolérance de panne ou l’équilibrage de charge](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md).  
  
-   **Tester la restauration des bases de données BizTalk Server à l’aide des journaux de transaction.**  
  
     Vous devez vérifier la récupération de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Pour plus d’informations sur l’utilisation de la copie des journaux pour sauvegarder et restaurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, consultez [ce qui est BizTalk Server l’envoi de journaux ?](../technical-guides/what-is-biztalk-server-log-shipping.md) dans ce guide ou [journaux](http://go.microsoft.com/fwlink/?LinkID=153450) (http://go.microsoft.com/fwlink/?LinkID=153450).  
  
     Pour obtenir la liste des étapes à suivre pour augmenter la disponibilité d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement à l’aide de la récupération d’urgence, consultez [liste de vérification : Increasing Availability with la récupération d’urgence](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Augmentation de la disponibilité de BizTalk Server](../technical-guides/increasing-availability-for-biztalk-server.md)
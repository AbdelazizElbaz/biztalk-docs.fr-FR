---
title: "Gestion de clusters hôtes de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93544f39-836f-4a4f-9587-230bfa3a9d4e
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 488a87539228a90ac427339e260653a141eb7121
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="clustering-receiving-hosts"></a>Gestion de clusters hôtes de réception
BizTalk Server fournit des fonctionnalités qui vous permet de configurer un hôte BizTalk en tant que ressource en cluster dans un [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] groupe de clusters. Prise en charge du cluster hôte est fourni pour prendre en charge une haute disponibilité intégrée BizTalk adaptateurs de réception qui ne doivent pas être exécutés dans plusieurs instances d’hôte simultanément, telles que le Gestionnaire de réception FTP ou, dans certaines circonstances, Gestionnaire de réception POP3. Cette prise en charge garantit également la cohérence transactionnelle des messages envoyés ou reçus via l'adaptateur MSMQ dans des scénarios exigeant une mise en cluster du service MSMQ.  
  
> [!NOTE]  
>  Cluster hôte est disponible uniquement avec BizTalk Server Enterprise Edition.  
  
> [!NOTE]  
>  Avant de mettre en cluster un hôte BizTalk vous devez configurer au moins deux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs dans un groupe BizTalk en tant que membres d’un [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster. Pour plus d’informations sur la configuration d’un [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] de cluster, consultez [les Documents de gestion de clusters Windows Server 2008, les livres blancs, les Webcasts, les groupes](http://go.microsoft.com/fwlink/?LinkId=156818) (http://go.microsoft.com/fwlink/?LinkId=156818).  
  
 Prise en charge du cluster hôte BizTalk est disponible pour fournir une haute disponibilité pour cinq des adaptateurs BizTalk intégrés : l’adaptateur FTP, l’adaptateur MSMQ, l’adaptateur POP3, l’adaptateur SQL et l’adaptateur SAP. Cette prise en charge garantit également une disponibilité élevée lors de l'exécution d'une seule instance d'un adaptateur en vue de respecter un ordre de livraison chronologique.  
  
 Tous les gestionnaires d’adaptateur BizTalk peuvent être exécuté sur un hôte en cluster, mais il est inutile de l’exécution des gestionnaires d’adaptateur dans un hôte en cluster à l’exception, comme décrit ci-dessous. Si vos exigences de traitement incluent les scénarios décrits dans la section ci-dessous, vous devez exécuter les gestionnaires d’adaptateur dans un cluster hôte. Pour les étapes détaillées de configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] clusters, consultez [Improving Fault Tolerance in BizTalk Server à l’aide d’un Cluster de basculement Windows Server 2008 ou un Cluster de serveurs Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=156819) (http://go.microsoft.com/fwlink/?LinkId=156819).  
  
## <a name="scenarios-for-running-adapter-handlers-in-clustered-hosts"></a>Scénarios pour l’exécution des gestionnaires d’adaptateur dans les ordinateurs hôtes en cluster  
 Si vos exigences de traitement incluent les scénarios répertoriés ci-dessous, vous devez exécuter les gestionnaires d’adaptateur dans un cluster hôte.  
  
-   Exécution du gestionnaire de réception de l'adaptateur FTP dans un hôte BizTalk mis en cluster  
  
-   Gestionnaires d’adaptateur MSMQ dans un hôte BizTalk en cluster en cours d’exécution  
  
-   Exécution du gestionnaire de réception de l'adaptateur POP3 dans un hôte BizTalk en cluster  
  
-   Exécution d'un adaptateur de réception prenant en compte la livraison chronologique dans un hôte BizTalk mis en cluster  
  
 Pour plus d’informations sur ces scénarios, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](http://go.microsoft.com/fwlink/?LinkId=151284) (http://go.microsoft.com/fwlink/?LinkId=151284).  
  
## <a name="see-also"></a>Voir aussi  
 [Montée en puissance parallèle de l’hôte de réception](../technical-guides/scaling-out-receiving-hosts.md)   
 [Mise à l’échelle des hôtes de traitement](../technical-guides/scaling-out-processing-hosts.md)   
 [Montée en charge des hôtes d’envoi](../technical-guides/scaling-out-sending-hosts.md)
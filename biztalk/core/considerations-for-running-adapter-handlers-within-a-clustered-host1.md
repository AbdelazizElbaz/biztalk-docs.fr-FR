---
title: "Considérations pour l’exécution des gestionnaires d’adaptateur au sein d’un cluster Host1 | Documents Microsoft"
ms.custom: 
ms.date: 2016-03-17
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- high availability
- receive adapters, clustering
- clustering, POP3 adapters
- FTP adapters, clustering
- clustering, receive adapters
- NLB system
- MSMQ send handler
- MSMQ receive handler
- clustering, FTP adapters
- handlers [adapters], best practices
- hosts, clustering
- MSMQ adapters
- clustering, MSMQ adapters
- adapters, best practices
- adapters, handlers
- POP3 adapters, clustering
- MSMQ adapters, clustering
- clustering
ms.assetid: ee66663c-4f4d-4515-9df1-aacf4fc72be4
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1fc93db61cddae43023f5c25eec62ecebd46e69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-for-running-adapter-handlers-within-a-clustered-host"></a>Éléments à prendre en compte pour l'exécution des gestionnaires d'adaptateur au sein d'un hôte mis en cluster
Prise en charge du cluster BizTalk hôte est disponible pour fournir une haute disponibilité pour les éléments suivants intégré d’adaptateurs BizTalk : l’adaptateur FTP, l’adaptateur SFTP, l’adaptateur MSMQ et l’adaptateur POP3. Cette prise en charge garantit également une disponibilité élevée lors de l'exécution d'une seule instance d'un adaptateur en vue de respecter un ordre de livraison chronologique.  
  
 Tous les gestionnaires d'adaptateur BizTalk peuvent être exécutés dans un hôte mis en cluster, mais cela ne présente d'intérêt que dans le cas ci-dessous. Si vos exigences de traitement n’incluent pas tous les scénarios ci-dessous, vous devez exécuter pas les gestionnaires d’adaptateur dans un cluster hôte.  
  
## <a name="running-the-ftp-or-sftp-adapter-receive-handler-within-a-clustered-biztalk-host"></a>Exécution du gestionnaire de réception d'adaptateur FTP ou SFTP dans un hôte BizTalk en cluster  
 Pour la plupart des adaptateurs intégrés BizTalk Server, la haute disponibilité est obtenue en créant plusieurs gestionnaires d'adaptateur exécutés dans des instances de l'hôte BizTalk sur différents serveurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d'un groupe BizTalk. Cependant, les gestionnaires de réception d'adaptateur FTP ou SFTP ne doivent pas être configuré de façon à être exécutés simultanément dans plusieurs instances de l'hôte BizTalk. Cette recommandation est faite parce que l'adaptateur de réception FTP ou SFTP  utilise le protocole FTP ou SFTP pour récupérer des fichiers à partir du système cible. Le protocole FTP ou SFTP ne verrouille pas les fichiers pour s'assurer que plusieurs copies du même fichier ne sont pas récupérées simultanément lors de l'exécution de plusieurs instances de l'adaptateur de réception FTP ou SFTP.  
  
 Pour assurer la haute disponibilité de l'adaptateur de réception FTP ou SFTP, vous devez configurer celui-ci afin qu'il s'exécute dans une instance de l'hôte BizTalk en cluster.  
  
## <a name="running-msmq-adapter-handlers-within-a-clustered-biztalk-host"></a>Gestionnaires d’adaptateur MSMQ dans un hôte BizTalk en cluster en cours d’exécution  
 Pour garantir la haute disponibilité de l'adaptateur MSMQ ainsi qu'une cohérence transactionnelle pour les messages envoyés ou reçus via cet adaptateur, procédez comme suit :  
  
1.  Configurez Message Queuing (MSMQ) en tant que ressource en cluster dans un groupe de clusters Windows sur votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs.  
  
2.  Ajoutez le service MSMQ en cluster à la liste de dépendances de ressource de l'hôte BizTalk mis en cluster. Cela garantit que l’hôte BizTalk en cluster démarre toujours le service MSMQ en cluster dans les scénarios de basculement.  
  
3.  Configurez les gestionnaires d'envoi et de réception de l'adaptateur MSMQ dans une instance d'hôte BizTalk préalablement définie en tant que ressource de cluster dans le même groupe de clusters que la ressource MSMQ en cluster.  
  
 Il est recommandé de suivre cette procédure pour les raisons suivantes :  
  
 **Gestionnaire de réception de l’adaptateur MSMQ** – versions MSMQ antérieures à MSMQ 4.0 (Windows Server 2008) ne prennent pas en charge les lectures transactionnelles à distance ; les lectures transactionnelles locales seulement sont pris en charge. Dans ce cas, l’adaptateur MSMQ réception gestionnaire doit être exécuté dans une instance d’hôte local pour le service Message Queuing en cluster pour effectuer les lectures transactionnelles locales par l’adaptateur MSMQ.  
  
> [!IMPORTANT]
>  Le gestionnaire de réception de l'adaptateur MSMQ nécessite qu'une instance locale qui ne fait pas partie d'un cluster du service Message Queuing soit exécutée sur l'ordinateur sur lequel l'instance de l'hôte de l'adaptateur de réception est exécutée.  
  
 **Gestionnaire d’envoi MSMQ adaptateur** : afin de garantir la cohérence des envois transactionnels effectués par l’adaptateur MSMQ, la file d’attente sortante utilisée par le Gestionnaire d’envoi de l’adaptateur MSMQ doit être hautement disponible afin que si le service MSMQ pour la sortie en file d’attente échoue, il peut être reprise. Configuration d’un cluster Queuingresource de Message et les gestionnaires d’adaptateur MSMQ dans un groupe de clusters garantit que la file d’attente sortante utilisée par le Gestionnaire d’envoi de l’adaptateur MSMQ soient hautement disponible. Ainsi, les risques de perdre des messages en cas de défaillance du service Message Queuing se trouvent limités.  
  
> [!NOTE]
>  Si l’emplacement de réception MSMQ est **uniquement** réception à partir de files d’attente MSMQ sur un serveur MSMQ distant, puis de la haute disponibilité peut être obtenue en exécutant MSMQ réception hôte sur plusieurs ordinateurs BizTalk dans le groupe BizTalk.  Pour fournir une haute disponibilité pour MSMQ, vous devez vérifier que le serveur MSMQ distant à l’aide de clustering de basculement dans Windows.  Si vous utilisez des files d’attente transactionnelles, le serveur MSMQ distant doit être en cours d’exécution MSMQ 4.0 (Windows Server 2008) ou version ultérieure.  
  
## <a name="running-the-pop3-adapter-receive-handler-within-a-clustered-biztalk-host"></a>Exécution du gestionnaire de réception de l'adaptateur POP3 dans un hôte BizTalk en cluster  
 Il n'est pas nécessaire de configurer le gestionnaire de réception de l'adaptateur POP3 de façon qu'il puisse fonctionner sur plusieurs hôtes dans un hôte BizTalk en cluster, sauf si le serveur POP3 à partir duquel l'adaptateur lit les données permet plusieurs connexions simultanées à une même boîte aux lettres. Pour obtenir un adaptateur POP3 hautement disponible lorsque le serveur POP3 auquel il se connecte autorise ces connexions simultanées, il est recommandé de configurer un gestionnaire de réception pour l'adaptateur POP3 de façon à ce qu'il puisse être exécuté sur une instance d'hôte BizTalk mise en cluster. Cette recommandation s'explique par le fait que plusieurs copies du même courrier électronique ne doivent pas être récupérées de manière simultanée lorsque plusieurs instances de l'adaptateur de réception POP3 sont exécutées.  
  
## <a name="running-a-receive-adapter-that-supports-ordered-delivery-with-a-clustered-biztalk-host"></a>Exécution d'un adaptateur de réception prenant en compte la livraison chronologique dans un hôte BizTalk mis en cluster  
 Les adaptateurs MSMQ et MQSeries intégrés offrent la possibilité de présenter les documents à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'ordre dans lequel ils ont été reçus. Une implémentation correcte de cette fonctionnalité exige qu'une seule instance de ces adaptateurs de réception soit exécutée à la fois. Pour assurer la haute disponibilité de l'instance unique de ces adaptateurs, vous devez les configurer afin qu'ils puissent être exécutés dans une instance de l'hôte BizTalk mis en cluster.
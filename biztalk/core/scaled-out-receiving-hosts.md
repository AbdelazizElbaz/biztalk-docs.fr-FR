---
title: "Mise à l’échelle des hôtes de réception | Documents Microsoft"
ms.custom: 
ms.date: 2016-03-17
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, receive adapters
- high availability
- HTTP adapters, scaling
- receive adapters, scaling
- POP3 adapters, scaling
- MSMQ adapters, scaling
- EDI adapters, scaling
- Web services, scaling
- hosts, multiple
- MQSeries adapters, scaling
- adapters, Windows SharePoint Services
- scaling, hosts
- scaling, adapters
- SAP adapters
- FTP adapters
- scaling, receive adapters
- hosts, receiving
- adapters, Web services
- hosts, scaling
- SOAP adapters, scaling
- adapters, scaling
- SQL adapters, scaling
- Web services, adapters
- File adapters, scaling
- clustering
ms.assetid: 94f35426-37fa-4ad2-8e35-d82fdca02262
caps.latest.revision: "54"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b9bc048de978a6dfd7c28505c54cdaaaef64064
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaled-out-receiving-hosts"></a>Mise à l'échelle des hôtes de réception
Lorsqu’un ordinateur hôte contient un élément de réception, tel qu’un emplacement de réception ou d’un pipeline, il agit comme une limite de sécurité, et le message de décodage et le déchiffrement se produit dans un pipeline au sein de l’hôte. Pour que les hôtes de réception soient dotés d'une disponibilité élevée, vous devez avoir installé deux ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou plus, exécutant une instance de chacun des hôtes de réception. La mise à l'échelle des hôtes de réception garantit la disponibilité des déploiements de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], très exigeants en matière de messagerie. Bien que son traitement des orchestrations soit minimal, ce modèle de déploiement permet d'acheminer de nombreux messages de types différents de manière rapide et fiable.  
  
 Vous pouvez encore améliorer la sécurité et l'évolutivité au sein de votre environnement en séparant l'hôte de réception des hôtes chargés du traitement des orchestrations et de l'envoi des messages, car il est alors possible de sécuriser et de déployer chaque hôte indépendamment des autres. Par exemple, vous pouvez attribuer deux ordinateurs supplémentaires (instances de l'hôte) à l'hôte de réception sans pour autant en ajouter aux hôtes de traitement ou d'envoi.  
  
## <a name="multiple-hosts-for-receiving-messages"></a>Hôtes de réception multiples  
 Le schéma suivant montre un déploiement de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournissant une disponibilité élevée à l'hôte de réception grâce à l'utilisation de deux ordinateurs pour exécuter ses instances. Remarquez que les hôtes de traitement et d'envoi représentés ici ne sont pas des hôtes hautement disponibles.  
  
 ![Plusieurs hôtes de réception de Messages](../core/media/tdi-ha-scalereceive.gif "TDI_HA_ScaleReceive")  
  
 Dans les cas de déploiement à grande échelle, dans des scénarios de partenariats commerciaux multiples ou d'utilisation de protocoles différents, vous avez la possibilité de répartir la fonction de réception entre plusieurs hôtes. Vous pouvez par exemple créer un hôte de réception des messages pour chaque adaptateur ou des hôtes distincts pour la réception des messages provenant de partenaires différents. Lorsque vous mettez en place plusieurs hôtes de réception, vous pouvez créer des limites de sécurité et faciliter la gestion et l'évolutivité de votre environnement sans que ce dernier puisse bénéficier pour autant d'une disponibilité élevée.  
  
 Pour obtenir un environnement à haute disponibilité, vous devez créer deux instances de l'hôte (ou plus) pour chaque hôte de réception créé. Vous pouvez par exemple créer trois hôtes de réception différents (A, B et C) afin de recevoir des messages de trois sociétés distinctes. Pour faire en sorte que tous ces hôtes bénéficient d'une disponibilité élevée, vous devez ensuite créer des instances d'hôte sur deux ordinateurs ou plus pour chaque hôte. Vous pouvez disposer des instances de chaque hôte sur un seul ordinateur sans perdre pour autant les fonctionnalités de limite de sécurité, de gestion ou d'évolutivité.  
  
 Le schéma suivant représente un environnement BizTalk Server hautement disponible à trois ordinateurs où des hôtes sont uniquement utilisés pour la réception de messages provenant de différentes sociétés.  
  
 ![Recevoir des Instances de](../core/media/tdi-ha-receiveinstances2.gif "TDI_HA_ReceiveInstances2")  
  
 Pour fournir une haute disponibilité dans cette configuration, chaque ordinateur exécute les trois instances d’hôte : une instance pour chacune des trois sociétés. Les instances de l'hôte de chaque société contiennent les emplacements de réception et les pipelines permettant la communication avec ces sociétés. Lors de tâches classiques, si les opérations de déploiement nécessaires ont été effectuées pour les adaptateurs de réception (ex. : configuration de l'équilibrage de charge réseau pour HTTP), la charge des messages est répartie entre les trois instances de chaque hôte. Si l'exécution d'une instance de l'hôte échoue sur un ordinateur, les instances de l'hôte exécutées sur les deux autres ordinateurs constituent une redondance permettant de conserver une disponibilité de service.  
  
## <a name="scaling-the-biztalk-server-receive-adapters"></a>Mise à l'échelle des adaptateurs de réception de BizTalk Server  
 Outre les instances de l'hôte, le processus de mise à l'échelle et d'installation de la haute disponibilité pour les hôtes de réception dépend également des adaptateurs que vous implémentez dans votre déploiement. Chaque adaptateur possède des caractéristiques de protocole particulières qui rendent la planification et le déploiement différents à chaque fois. Néanmoins, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permet de mettre en place une solution haute disponibilité identique pour tous les adaptateurs, principalement par l'intermédiaire d'ordinateurs et d'instances d'hôte supplémentaires.  
  
 Selon le protocole utilisé, certains adaptateurs de réception nécessitent un mécanisme supplémentaire pour la distribution des messages entrants sur plusieurs ordinateurs afin de fournir une disponibilité élevée. Par exemple, pour des solutions [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisant un adaptateur HTTP ou SOAP (également connu sous le nom d'adaptateur de services Web), un service d'équilibrage de la charge réseau est indispensable à la distribution de la charge de travail reçue. Le tableau ci-dessous donne les instructions permettant aux adaptateurs les plus courants dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d'être dotés d'une disponibilité élevée.  
  
|**Adaptateur**|**Instructions de haute disponibilité**|  
|-----------------|---------------------------------------|  
|HTTP|Ajoutez plusieurs ordinateurs à l’hôte de réception et configurer l’équilibrage de charge réseau pour distribuer des messages entrants sur plusieurs ordinateurs hôtes.|  
|SOAP|Ajoutez plusieurs ordinateurs à l’hôte de réception et configurer l’équilibrage de charge réseau pour distribuer des messages entrants sur plusieurs ordinateurs hôtes.|  
|Fichier|Ajoutez des ordinateurs à l'hôte de réception et faites en sorte que l'emplacement de réception de chacun des ordinateurs fasse référence au même dossier ou chemin d'accès UNC (Universal Naming Convention). Pour obtenir une solution intégralement dotée de la haute disponibilité, vous devez vous assurer que l'emplacement du fichier vers lequel le chemin d'accès UNC pointe est hautement disponible (ou suffisamment fiable).|  
|FTP|Configurez l'adaptateur de réception FTP de sorte qu'il puisse être exécuté sur un hôte BizTalk mis en cluster. Pour plus d’informations, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).|  
|POP3|Configurez l'adaptateur de réception POP3 de sorte qu'il puisse être exécuté sur un hôte BizTalk mis en cluster. Pour plus d’informations, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).|  
|MSMQ|Configurez MSMQ adaptateur de réception pour s’exécuter sur un hôte BizTalk de cluster Windows. Pour plus d’informations, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md). Si le de réception MSMQ emplacements sont à l’aide de files d’attente sur un serveur MSMQ distant, vous n’avez pas besoin de mettre en cluster l’hôte BizTalk.  Dans ce scénario, exécuter MSMQ sur plusieurs ordinateurs BizTalk dans le groupe hôte de réception.|  
|MQSeries|Pour cet adaptateur, ajoutez plusieurs ordinateurs à l'hôte de réception. De plus, dans MQSeries pour Windows, utilisez des gestionnaires de file d'attente mis en cluster et mettez en cluster MQSeries Server pour Windows.|  
|Windows Sharepoint Services|Ajoutez plusieurs ordinateurs à l’hôte de réception et configurer l’équilibrage de charge réseau pour distribuer des messages entrants sur plusieurs ordinateurs hôtes.|  
|-WCF-NetTcp<br />-WCF-Custom|Utilisez plusieurs ordinateurs pour l'hôte de réception et configurez le service d'équilibrage de la charge réseau de sorte qu'il répartisse les messages entrants entre ces ordinateurs.<br /><br /> - ou -<br /><br /> Mettez en cluster l'hôte utilisé par le gestionnaire de réception de l'adaptateur.|  
|-WCF-NetNamedPipe<br />-WCF-BasicHttp<br />-WCF-WSHttp<br />-WCF-CustomIsolated|Utilisez plusieurs ordinateurs pour l'hôte de réception et configurez le service d'équilibrage de la charge réseau de sorte qu'il répartisse les messages entrants entre ces ordinateurs.|  
|WCF-NetMsmq|Mettez en cluster l'hôte utilisé par le gestionnaire de réception de l'adaptateur.|  
  
### <a name="http-adapter"></a>Adaptateur HTTP  
 L'adaptateur de réception HTTP de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est une extension d'API de serveur Web (ISAPI, Internet Service Application Programming Interface) de type BTSHTTPReceive.dll s'exécutant sous forme d'instance d'hôte sur chaque ordinateur hôte de réception. Lorsqu'un partenaire envoie un message à BizTalk Server par le biais du protocole HTTP, ce message arrive en général à une adresse URL spécifique, sur un ordinateur BizTalk Server où sont installés les services IIS (Internet Information Services). Dans BizTalk Server, créez une instance de l'hôte et un emplacement de réception abonné à cette URL. Lorsque des messages parviennent à cette URL, BizTalk Server les extrait et les stocke dans la base de données MessageBox.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournit une disponibilité élevée à l'adaptateur de réception HTTP, car il permet la création de plusieurs instances d'hôte pour un même hôte de réception. Ces instances d'hôte doivent être abonnées à une URL, cette dernière pouvant être une adresse IP mise en cluster et partagée si vous utilisez l'équilibrage de la charge réseau afin de répartir les messages entrants entre plusieurs hôtes de réception. L'ensemble de ces hôtes gère l'adresse IP virtuelle du cluster si bien que, si l'un des membres du cluster est défaillant, les autres peuvent continuer le service.  
  
### <a name="soap-adapter-web-services-adapter"></a>Adaptateur SOAP (Adaptateur de services Web)  
 Contrairement à l'adaptateur de réception HTTP, l'adaptateur de services Web ne comprend pas d'extension ISAPI. Il reçoit les messages par l'intermédiaire d'une URL préalablement indiquée dans l'Assistant Publication de services Web BizTalk. Ce dernier exporte un service Web et crée un répertoire virtuel servant d'emplacement de réception.  
  
 Pour assurer la haute disponibilité à l'adaptateur de services Web, utilisez plusieurs ordinateurs pour l'hôte de réception et servez-vous de l'équilibrage de la charge réseau afin d'obtenir une répartition des messages entrants. Lorsqu'un client envoie un message à BizTalk Server par l'intermédiaire de l'adaptateur de services, le service d'équilibrage de la charge dirige le message vers l'un des hôtes de réception et l'instance de l'hôte concernée stocke le message dans la base de données MessageBox.  
  
### <a name="file-adapter"></a>Adaptateur FILE  
 L'adaptateur de réception File extrait les messages d'un dossier ou d'un chemin d'accès UNC. Beaucoup de sociétés utilisent cet adaptateur en lieu et place de scénarios interentreprises (B2B), car les deux parties doivent disposer d'autorisations d'accès au chemin et parce que les sociétés ne partagent généralement pas leur système de fichiers. Configurez le gestionnaire de réception File de sorte qu'il soit abonné au chemin d'accès et que BizTalk Server puisse ensuite récupérer les messages à leur arrivée dans l'emplacement de réception.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournit une disponibilité élevée à l'adaptateur de réception File, car il permet la création d'instances d'hôte sur plusieurs ordinateurs hôtes abonnés au même chemin d'accès UNC. Si l'une des instances s'exécutant sur un ordinateur hôte rencontre des problèmes ou est défaillante, la même instance s'exécutant sur un autre ordinateur hôte est capable de récupérer le message et de le stocker dans la base de données MessageBox.  
  
### <a name="ftp-adapter"></a>adaptateur FTP  
 L'adaptateur de réception FTP ne doit pas être configuré de façon à être exécuté sur plusieurs hôtes, car il utilise le protocole FTP pour extraire les fichiers du système cible. Or, ce protocole ne comportant aucune capacité de verrouillage, il ne peut garantir que plusieurs copies d'un même fichier ne soient pas récupérées en même temps lors de l'exécution de plusieurs instances de l'adaptateur de réception FTP. L'adaptateur FTP doit être configuré uniquement pour être exécuté sur un hôte BizTalk en cluster. Pour plus d’informations, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).  
  
### <a name="pop3-adapter"></a>Adaptateur POP3  
 L'adaptateur de réception POP3 peut être configuré de façon à fonctionner sur plusieurs hôtes, sauf si le serveur POP3 à partir duquel l'adaptateur lit les données permet plusieurs connexions simultanées à une même boîte aux lettres. Pour obtenir un adaptateur hautement disponible lorsque le serveur POP3 auquel il se connecte permet ces connexions simultanées, il est nécessaire de configurer le gestionnaire de réception de l'adaptateur POP3 de façon qu'il puisse être exécuté sur une instance d'hôte BizTalk mise en cluster. Pour plus d’informations, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).  
  
### <a name="msmq-adapter"></a>Adaptateur MSMQ  
 Pour obtenir une haute disponibilité, exécuter MSMQ adaptateur de réception dans un hôte BizTalk de cluster Windows qui se trouve dans le même groupe de clusters que la ressource MSMQ en cluster. Pour plus d’informations, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).  
  
 Si l’emplacement de réception MSMQ est **uniquement** réception à partir de files d’attente MSMQ sur un serveur MSMQ distant, puis de la haute disponibilité peut être obtenue en exécutant MSMQ réception hôte sur plusieurs ordinateurs BizTalk dans le groupe BizTalk.  Pour fournir une haute disponibilité pour MSMQ, vous devez vérifier que le serveur MSMQ distant à l’aide de clustering de basculement dans Windows.  Si vous utilisez des files d’attente transactionnelles, le serveur MSMQ distant doit être en cours d’exécution MSMQ 4.0 (Windows Server 2008) ou version ultérieure.  
  
### <a name="mqseries-adapter"></a>Adaptateur MQSeries  
 L'adaptateur Microsoft BizTalk pour MQSeries fait office de pont entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les serveurs IBM MQSeries. Pour obtenir une solution hautement disponible avec cet adaptateur, vous devez disposer de plusieurs instances de l'hôte exécutant l'adaptateur, utiliser des gestionnaires de file d'attente mis en cluster dans MQSeries pour Windows et mettre en cluster MQSeries Server pour Windows. Pour plus d'informations sur la mise en cluster du gestionnaire de file d'attente et celle de MQSeries Server, reportez-vous à la documentation d'IBM WebSphere MQ. Pour plus d'informations sur la haute disponibilité pour l'adaptateur MQSeries, reportez-vous à la rubrique « High Availability » (Haute disponibilité) dans l'aide de l'adaptateur Microsoft BizTalk pour MQSeries.  
  
### <a name="windows-sharepoint-services-adapter"></a>Adaptateur Windows SharePoint Services  
 L'adaptateur Windows SharePoint Services extrait les messages provenant de SharePoint en appelant le service Web de Windows SharePoint Services installé par BizTalk sur la machine exécutant SharePoint. L'adaptateur utilise un mécanisme de vérification afin de s'assurer que des instances d'hôte différentes ne traiteront pas le même message. Ainsi, l’adaptateur de réception montée en puissance parallèle en ajoutant plusieurs instances de l’hôte. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Fournit une haute disponibilité pour adaptateur de réception SharePoint en vous permettant d’exécuter les mêmes emplacements de réception sur plusieurs instances d’hôte qui sont abonnées à la même URL HTTP pointant vers une installation SharePoint NLB.  
  
### <a name="wcf-nettcp-adapter"></a>Adaptateur WCF-NetTcp  
 La charge de la liaison NetTcpBinding peut être équilibrée à l'aide des techniques d'équilibrage de la charge au niveau de la couche IP. Toutefois, la liaison NetTcpBinding regroupe les connexions TCP par défaut pour réduire la latence de connexion. Cette optimisation interfère avec le mécanisme de base d'équilibrage de la charge. La valeur de configuration principale pour l'optimisation de la liaison NetTcpBinding correspond au délai d'expiration du bail, qui fait partie des paramètres du pool de connexions. Le regroupement des connexions provoque l'association des connexions clientes à des serveurs spécifiques dans la batterie. Comme la durée de vie de ces connexions augmente (facteur contrôlé par le paramètre Délai d'expiration du bail), la distribution de la charge entre les serveurs de la batterie n'est plus équilibrée et la durée moyenne des appels augmente. Aussi, lorsque vous utilisez NetTcpBinding dans les scénarios avec équilibrage de charge, pensez à réduire le délai d'expiration du bail par défaut. Un délai d'expiration du bail de 30 secondes est un point de départ raisonnable pour les scénarios avec équilibrage de charge, bien que la valeur optimale du délai dépende de l'application. Pour plus d'informations sur le délai d'expiration de bail du canal et les autres quotas de transport, consultez la section Quotas de transport.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de la haute disponibilité pour des hôtes BizTalk](../core/providing-high-availability-for-biztalk-hosts.md)
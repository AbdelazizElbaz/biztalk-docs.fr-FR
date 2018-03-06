---
title: "Migrer à partir de l’adaptateur MSMQT vers l’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 12/07/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97126f70-0be5-4a2f-bcba-173fd932b6de
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1696e732bdbd005b01f16834a075fe69460602f9
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="migrate-from-the-msmqt-adapter-to-the-msmq-adapter"></a>Migrer à partir de l’adaptateur MSMQT vers l’adaptateur MSMQ
Cette rubrique décrit les aspects à prendre en compte en relation avec la livraison chronologique de bout en bout des messages, la cohérence transactionnelle, la haute disponibilité et l'évolutivité avant de procéder à la migration des solutions de l'adaptateur BizTalk Message Queuing (MSMQT) vers l'adaptateur Message Queuing (MSMQ). Dans le cadre de cette rubrique, la livraison chronologique des messages, la cohérence transactionnelle, la haute disponibilité et l'évolutivité sont définies comme suit :  
  
-   **Livraison chronologique des messages.** Garantie que les messages sont envoyés depuis BizTalk Server dans l'ordre dans lequel ils ont été reçus.  
  
-   **Cohérence transactionnelle.** Garantie que les messages traités ne sont pas perdus ou dupliqués en raison d'une défaillance matérielle, logicielle ou du réseau.  
  
-   **Haute disponibilité.** Garantie que les services utilisés pour traiter les messages sont toujours disponibles pour le traitement.  
  
-   **Évolutivité.** Possibilité d'augmenter la capacité existante de traitement des messages.  
  
## <a name="end-to-end-ordered-delivery"></a>Livraison chronologique de bout en bout des messages  
 L'adaptateur MSMQT assure la livraison chronologique de bout en bout des messages. Ainsi, si une application MSMQ envoie les messages 1, 2 et 3 à un emplacement de réception lié à l'adaptateur MSMQT, ces messages sont remis à une orchestration ou un port d'envoi dans BizTalk Server dans le même ordre : 1, 2, 3. Par exemple, cette fonctionnalité peut être utile pour les opérations boursières qui doivent être transmises et exécutées dans l'ordre dans lequel elles ont été reçues.  
  
 La livraison chronologique de bout en bout des messages avec MSMQT requiert le fonctionnement conjoint de divers composants. La séquence d'événements suivante illustre cet aspect avec l'adaptateur MSMQT :  
  
1.  L'API MSMQ sur un ordinateur distant reçoit les messages 1, 2 et 3 et les transmet à une file d'attente locale transactionnelle dans le même ordre : 1, 2, 3.  
  
2.  Un client MSMQ sur l'ordinateur distant extrait les messages de la file d'attente et les envoie à la file d'attente MSMQT dans l'ordre : 1, 2, 3.  
  
3.  L'adaptateur MSMQT reçoit les messages dans l'ordre 1, 2, 3 et les transmet au composant MessageAgent de BizTalk dans le même ordre : 1, 2, 3.  
  
4.  Le composant MessageAgent de BizTalk vérifie que les messages sont envoyés à la base de données MessageBox dans l'ordre : 1, 2, 3.  
  
5.  La base de données MessageBox achemine les messages et, si ceux-ci sont acheminés à la même instance d'une orchestration ou d'un port d'envoi, vérifie qu'ils sont remis à cette instance dans le même ordre : 1, 2, 3.  
  
 Dans BizTalk Server 2004, MSMQT a été le seul adaptateur capable d’assurer de bout en fin de livraison chronologique des messages. Tous les autres adaptateurs BizTalk intégrés peuvent modifier l'ordre des messages au cours des étapes 3 à 5 indiquées ci-dessus. La plupart des autres adaptateurs intégrés effectuent l'étape 3 à l'aide d'un composant appelé Gestionnaire de points de terminaison. Celui-ci étant multithread par nature, il ne conserve pas l'ordre des messages. L’adaptateur BizTalk Server 2004 MSMQ utilisé une fonctionnalité « Traitement en série » qui conserve l’ordre de l’étape 3, mais il ne demande pas puis au composant MessageAgent préserver l’ordre à l’avenir, afin que les messages peuvent être acheminés à une orchestration ou port d’envoi de manière désordonnée.  
  
 **Livraison chronologique des messages avec l’adaptateur MSMQ de bout en bout**  
  
 Pour obtenir une livraison chronologique des messages avec l’adaptateur MSMQ de bout en bout, procédez comme suit :  
  
1.  Activer la **livraison chronologique des messages** propriété sur la réception de l’orchestration d’abonnement de port ou le port d’envoi. Dans BizTalk Server, les ports dans les orchestrations et ports d’envoi doivent une **livraison chronologique des messages** option de configuration. Lorsque celle-ci est activée, le port de réception de l'orchestration ou le port d'envoi demande à la base de données MessageBox de lui remettre les messages dans l'ordre dans lequel ils ont été envoyés à la base de données MessageBox.  
  
2.  Définir le **traitement chronologique** propriété pour l’emplacement de réception qui est lié à l’adaptateur MSMQ sur `True`. Dans BizTalk Server, les emplacements que l’utilisation du transport MSMQ peut être configurée pour utiliser le traitement chronologique, qui, s’il est activé, permet de s’assurer que les messages sont envoyés vers la MessageBox dans le même ordre qu’ils ont été reçus de réception.  
  
3.  Définir le **transactionnel** propriété pour l’emplacement de réception qui est lié à l’adaptateur MSMQ sur `True`.  
  
4.  Vérifiez que les files d'attentes MSMQ surveillées par les emplacements de réception MSMQ sont marquées comme « transactionnelles ». Cette propriété doit être définie sur les files d'attente pour assurer la livraison chronologique des messages.  
  
> [!NOTE]
>  La livraison chronologique des messages n'est garantie que si la ou les files d'attente MSMQ surveillées par les emplacements de réception BizTalk sont traitées par un seul ordinateur. Une telle configuration peut présenter des problèmes d'évolutivité, comme décrit ci-dessous.  
  
## <a name="transaction-usage-when-processing-messages-with-the-msmqt-adapter-vs-the-msmq-adapter"></a>Utilisation des transactions lors du traitement des messages avec l'adaptateur MSMQT et l'adaptateur MSMQ  
 Le traitement des messages par les adaptateurs MSMQT et MSMQ diffère du point de vue de l'utilisation des transactions.  
  
 Lorsque l'adaptateur MSMQT est utilisé, les processus ayant trait à la réception d'un message du réseau et à son traitement avec BizTalk Server sont gérés sous une seule transaction. De même, les messages d'accusé de réception générés pour l'expéditeur indiquent que le message a été reçu et traité par BizTalk Server.  
  
 Lorsque l'adaptateur MSMQ est utilisé, les processus ayant trait à la réception d'un message du réseau et à son traitement avec BizTalk Server sont gérés sous deux transactions distinctes (une pour la réception du réseau et une pour le traitement avec BizTalk Server). De même, les messages d'accusé de réception générés pour l'expéditeur indiquent seulement que le message a été reçu du réseau, pas qu'il a été traité par BizTalk Server. L'expéditeur reçoit un accusé de réception du serveur Microsoft Message Queuing lorsque le message est reçu du réseau et conservé dans la file d'attente MSMQ locale, que BizTalk Server soit installé ou non. Une fois le message conservé dans la file d'attente MSMQ, l'adaptateur MSMQ le récupère, le traite et le publie dans la base de données MessageBox. En cas d'échec de ce processus, le message est envoyé à la file d'attente des messages interrompus de BizTalk ou conservé dans la file d'attente MSMQ locale (lorsque le traitement transactionnel est utilisé), et l'expéditeur n'est pas informé de l'échec du traitement du message dans BizTalk Server.  
  
 Si votre architecture inclut la réception d'accusés de réception en cas de traitement réussi des messages par BizTalk Server, vous pouvez ajouter les accusés de réception au niveau de l'application si vous effectuez une migration de l'adaptateur MSMQT vers l'adaptateur MSMQ. Vous devez mettre à jour votre orchestration et l'application d'envoi pour implémenter les accusés de réception au niveau de l'application.  
  
## <a name="high-availability-transactional-in-order"></a>Haute disponibilité (transactionnelle, chronologique)  
 Pour fournir une haute disponibilité de l’adaptateur MSMQT vous pouvez ajouter plusieurs ordinateurs à l’hôte de réception et configurer l’équilibrage de charge réseau (NLB) pour la tolérance de panne, ou vous pouvez mettre en cluster l’hôte BizTalk par défaut. Si vous exécutez l'adaptateur MSMQT avec l'équilibrage de la charge réseau, les autres serveurs gèrent la charge d'un serveur tombé en panne. Si vous exécutez les gestionnaires de l'adaptateur MSMQT sur un hôte en cluster, l'échec d'un nœud d'hôte provoque l'échec du logiciel du cluster via l'hôte en cluster sur l'autre nœud. Lorsque l'adaptateur MSMQ est utilisé, l'équilibrage de la charge réseau ne fonctionne pas si vous devez utiliser le traitement transactionnel sans perte de données car l'adaptateur MSMQ utilise les files d'attente MSMQ locales pour le stockage intermédiaire. Dans ce cas, si un message remis à une file d'attente MSMQ locale n'est pas consommé par l'adaptateur MSMQ, il est perdu lorsque l'ordinateur échoue.  
  
 Pour fournir une haute disponibilité et la cohérence transactionnelle avec l’adaptateur MSMQ, vous devez procédez comme suit :  
  
1.  Configurez Microsoft Message Queuing (MSMQ) en tant que ressource mise en cluster dans un groupe de clusters de serveurs Windows Server sur vos serveurs BizTalk Server.  
  
2.  Configurez le gestionnaire de réception de l'adaptateur MSMQ dans une instance d'hôte BizTalk préalablement définie en tant que ressource de cluster dans le même groupe de clusters que la ressource MSMQ en cluster.  
  
3.  Configurez la ressource de cluster pour l'instance d'hôte BizTalk afin qu'elle maintienne une dépendance sur la ressource MSMQ en cluster.  
  
 Pour implémenter la livraison chronologique des messages avec cette architecture, suivez les étapes présentées précédemment sous « De bout en bout livraison chronologique des messages avec l’adaptateur MSMQ. »  
  
## <a name="high-availability-nontransactional-not-in-order"></a>Haute disponibilité (non transactionnelle, non chronologique)  
 Pour implémenter la haute disponibilité sans le traitement transactionnel à l'aide de l'adaptateur MSMQ, vous devez implémenter l'équilibrage de la charge réseau et exécuter les instances d'un hôte configuré avec les gestionnaires d'envoi et de réception MSMQ sur plusieurs serveurs BizTalk derrière l'équilibrage de la charge réseau. Lors de l’implémentation d’équilibrage de charge réseau avec MSMQ vous devez suivre les meilleures pratiques décrites dans l’article de la Base de connaissances Microsoft [899611 : comment Message Queuing peut fonctionner sur l’équilibrage de charge réseau (NLB)](https://support.microsoft.com/help/899611/how-message-queuing-can-function-over-network-load-balancing-nlb). Dans ce scénario, l'échec d'un des serveurs BizTalk provoque l'indisponibilité des messages exécutés dans l'instance d'hôte sur ce serveur jusqu'à la récupération du serveur BizTalk. Dans cette configuration, la haute disponibilité est assurée comme suit : si l'un des serveurs BizTalk n'est pas disponible, l'équilibrage de la charge réseau achemine les demandes vers l'autre serveur BizTalk.  
  
## <a name="scalability-nontransactional-not-in-order"></a>Évolutivité (non transactionnelle, non chronologique)  
 Pour implémenter l'évolutivité, suivez les directives relatives à la haute disponibilité (non transactionnelle) et ajoutez des instances d'hôte supplémentaires. Cette architecture favorise la livraison rapide et l'évolutivité, mais n'assure pas la livraison chronologique des messages.  
  
## <a name="scalability-transactional-not-in-order"></a>Évolutivité (transactionnelle, non chronologique)  
 Pour implémenter la livraison transactionnelle des messages sans livraison chronologique, vous pouvez combiner l'équilibrage de la charge réseau avec MSMQ et le clustering Windows. Cette architecture requiert la configuration d'au moins deux groupes de cluster dans deux environnements en cluster Windows distincts en suivant les étapes de la section « Haute disponibilité (transactionnelle, chronologique) » pour chaque cluster Windows. Vous devez ensuite implémenter l'équilibrage de la charge réseau pour répartir la charge entre les groupes de cluster. Comme l'équilibrage de la charge réseau n'est pas pris en charge sur un cluster Windows, ce scénario requiert une solution d'équilibrage de la charge réseau matérielle. Le diagramme suivant illustre cette architecture.  
  
 ![Équilibrage de charge entre les groupes de clusters](../core/media/scaleclusteredmsmqwithnlb.gif "ScaleClusteredMSMQwithNLB")  
  
> [!NOTE]
>  Cette architecture n'assure pas la livraison chronologique des messages.  
  
## <a name="scalability-transactional-in-order"></a>Évolutivité (transactionnelle, chronologique)  
 L'évolution horizontale d'une architecture qui assure la haute disponibilité, la cohérence transactionnelle et la livraison chronologique des messages pose problème si MSMQ 3.0 ou une version antérieure est utilisée. En effet, les lectures transactionnelles à distance ne sont pas prises en charge sauf si l'ordinateur BizTalk Server et le serveur MSMQ distant exécutent MSMQ 4.0. Lorsque MSMQ 3.0 ou une version antérieure est utilisée, vous devez procéder à l'évolution horizontale à l'aide de plusieurs files d'attente MSMQ locales. Dans ce cas, si la connexion TCP/IP entre la session MSMQ et l'équilibrage de la charge réseau est interrompue, elle peut être restaurée par l'équilibrage de la charge réseau vers un autre ordinateur, ce qui peut entraîner une livraison non chronologique.  
  
 Pour contourner cette limitation, vous pouvez équilibrer manuellement la charge associée à la livraison des messages en affectant des files d'attente de destination à différents ordinateurs. Pour ce faire, vous devez lier des instances d'hôte BizTalk spécifiques à des files d'attente MSMQ spécifiques. Par exemple, si vous recevez un grand nombre de document d'un partenaire commercial particulier, créez un hôte distinct et une file d'attente de réception sur un serveur BizTalk particulier pour ce partenaire commercial uniquement.  
  
 Si possible, exécutez MSMQ 4.0 sur les ordinateurs distants lorsque les lectures transactionnelles distantes et l'équilibrage de la charge sont requis.  
  
## <a name="summary"></a>Résumé  
 Le tableau suivant récapitule les architectures que vous pouvez implémenter pour prendre en charge les fonctionnalités spécifiques.  
  
|**Fonctionnalités**|**Équilibrage de charge réseau, ni cluster**|**NLB**|**Cluster**|**Équilibrage de charge réseau et le cluster**|  
|-----------------------|---------------------------------|-------------|-----------------|-------------------------|  
|Livraison chronologique des messages de bout en bout|Oui|Non|Oui|Possible avec une configuration manuelle|  
|Cohérence transactionnelle|Non (les messages peuvent être perdus ou dupliqués en cas de défaillance du service)|non|Oui|Oui|  
|Haute disponibilité|non|Oui|Oui|Oui|  
|Évolutivité|non|Oui|Non|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)
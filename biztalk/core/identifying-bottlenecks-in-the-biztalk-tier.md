---
title: "Identification des goulots d’étranglement au niveau de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f38ade78-8af3-4485-9b2a-5e4cdba965d2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5dd356ac3b8563d207e3534fc503711f11a9c8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="identifying-bottlenecks-in-the-biztalk-tier"></a>Identification des goulots d'étranglement dans le niveau BizTalk
Le niveau BizTalk peut être divisé en plusieurs zones fonctionnelles :  
  
-   Réception  
  
-   Traitement  
  
-   Transmission  
  
-   Suivi  
  
-   Autres  
  
 Pour ces zones, si les ressources système (UC, mémoire et disque) semblent saturées, vous devez mettre votre serveur à niveau par l'intermédiaire d'une évolution verticale. Si les ressources système ne sont pas saturées, suivez les procédures décrites dans cette section.  
  
## <a name="bottlenecks-in-the-receive-location"></a>Goulots d'étranglement dans l'emplacement de réception  
 Si les messages commencent à s'accumuler dans l'emplacement de réception (par exemple, si la taille du dossier de réception de fichiers augmente ou si la file d'attente sortante n'est pas vidée assez rapidement), cela indique que le système ne parvient pas à absorber les données assez rapidement pour traiter la charge entrante. Le problème peut également être dû à des limitations internes (BizTalk réduit la vitesse de réception si les abonnés n'arrivent pas traiter les données assez vite, ce qui entraîne une accumulation de travaux en retard dans les tables de base de données). Si le problème est matériel, procédez à une évolution verticale. Vous pouvez également effectuer une évolution horizontale, à savoir ajouter une instance d'hôte (un serveur) à l'hôte mappé sur le gestionnaire de réception. Utilisez l'utilitaire Perfmon pour surveiller l'utilisation des ressources système. Il est important de confirmer que l'emplacement de réception externe n'est pas à l'origine du goulot d'étranglement. Par exemple, le partage de fichiers distant est saturé en raison de nombreuses entrées/sorties sur le disque, le serveur hébergeant la file d'attente sortante distante n'est pas saturé ou le client utilisé pour générer la charge HTTP/SOAP n'est pas en manque de threads.  
  
## <a name="processing-bottlenecks"></a>Goulots d'étranglement de traitement  
 Si la valeur associée à File d'attente hôte - Longueur (voir le tableau de décompte Perfmon ci-dessous) augmente, cela signifie que les orchestrations ne sont pas exécutées assez rapidement. Ce problème peut être dû à un conflit de mémoire ou à une saturation de l'UC.  
  
 Si les serveurs d'orchestration constituent le goulot d'étranglement, utilisez l'utilitaire Perfmon pour en identifier la source.  
  
 Si le serveur est lié à l'UC, prenez en compte les éléments suivants :  
  
-   Si le workflow est complexe, vous pouvez fractionner l'orchestration en plusieurs orchestrations plus petites.  
  
    > [!NOTE]
    >  Le fractionnement d'une orchestration en plusieurs workflows peut engendrer une latence supplémentaire et une plus grande complexité.  
  
-   Si les mappages utilisés sont complexes, vérifiez s'ils peuvent être déplacés sur les ports de réception/d'envoi (renseignez-vous sur la bande passante disponible sur ces ports).  
  
-   Envisagez une évolution verticale du matériel ou, si possible, une évolution horizontale avec la configuration d'un nouveau serveur de traitement.  
  
## <a name="transmitting-bottlenecks"></a>Goulots d'étranglement de transmission  
 Si les ressources du serveur de transmission sont saturées (par exemple, disque, mémoire, UC), envisagez une évolution verticale de ce serveur ou, si possible, une évolution horizontale avec des serveurs d'hôtes d'envoi supplémentaires. Le niveau d'envoi peut devenir le goulot d'étranglement si la destination (externe à BizTalk) ne parvient pas à recevoir les données assez rapidement. Les messages s'accumulent alors dans la base de données MessageBox (application SendHostQ).  
  
 Si tous les points de terminaison se trouvent dans les limites de la topologie, isolez la cause du problème au niveau de la destination. Par exemple, la configuration de l'emplacement HTTP/SOAP est-elle optimale pour la réception de la charge ou pouvez-vous effectuer une évolution horizontale ? L'augmentation de la destination est-elle due à un trop grand nombre de messages de sortie envoyés par BizTalk ? Dans l'affirmative, prévoyez un plan de maintenance destiné à archiver et purger les messages de destination. Par exemple, un grand nombre de fichiers dans un dossier de destination peut entraver sérieusement la capacité du service BizTalk à valider les données sur le lecteur de disque.  
  
## <a name="tracking-bottlenecks"></a>Goulots d'étranglement de suivi  
 L'instance d'hôte de suivi est chargée de déplacer les événements de message suivis et BAM et les données de l'instance de service de la base de données MessageBox (table TrackingData) vers les tables de base de données BizTalkDTADb et/ou BAMPrimaryImport. Si plusieurs bases de données MessageBox sont configurées, l'instance d'hôte de suivi utilise quatre threads par MessageBox.  
  
 Il est possible que cette instance d'hôte soit liée à l'UC. Dans ce cas, procédez à une évolution verticale du serveur ou effectuez une évolution horizontale avec la configuration d'un nouveau serveur, pour lequel l'option de suivi de l'hôte est activée. Les différentes instances d'hôte équilibreront automatiquement la charge des différentes MessageBoxes configurées.  
  
 Si la table TrackingData de la base de données MessageBox commence une sauvegarde, c'est généralement parce que les travaux de maintenance de données de la base de données BizTalkDTADb et/ou BAMPrimaryImport ne s'exécutent pas conformément à leur configuration, ce qui entraîne l'augmentation de la base de données BizTalkDTADb et/ou BAMPrimaryImport. Si ces bases de données deviennent trop volumineuses, cela peut nuire à la capacité de l'hôte de suivi à insérer des données dans ces tables, ce qui entraîne la sauvegarde des données suivies dans les tables de la base de données MessageBox. L'augmentation de la table MessageBox->TrackingData entraîne l'activation des limitations.  
  
## <a name="other"></a>Autres  
 Configurez la topologie de déploiement de telle façon que les différentes fonctionnalités s'exécutent sur des instances d'hôte dédiées isolées. Ainsi, chaque instance d'hôte dispose de ses propres ressources (sur un système 32 bits, 2 Go d'espace d'adressage de mémoire virtuelle, handles, threads). Si le serveur est assez puissant (marge d'UC et mémoire suffisantes) pour héberger plusieurs instances d'hôte, ces dernières peuvent être toutes configurées pour une exécution sur le même ordinateur physique. Dans le cas contraire, il est possible de procéder à une évolution horizontale, à savoir déplacer les fonctionnalités vers des serveurs dédiés. Le fait d'exécuter une même fonctionnalité sur plusieurs serveurs permet également de disposer d'une configuration hautement disponible.  
  
## <a name="biztalk-system-performance-counters"></a>Compteurs de performances du système BizTalk  
  
|Objet|Instance|Compteur|Objet de la surveillance|  
|------------|--------------|-------------|------------------------|  
|Processeur|_Total|% temps processeur|Conflit de ressources|  
|Traiter|BTSNTSvc|Octets virtuels|Fuite/encombrement de mémoire|  
|Traiter|BTSNTSvc|Octets privés|Fuite/encombrement de mémoire|  
|Traiter|BTSNTSvc|Nombre de handles|Conflit de ressources|  
|Traiter|BTSNTSvc|Nombre de threads|Conflit de ressources|  
|Disque physique|_Total|% inactivité|Conflit de ressources|  
|Disque physique|_Total|Longueur actuelle de la file d'attente du disque|Conflit de ressources|  
  
### <a name="cpu-contention"></a>Conflit d'UC  
 Si le processeur est saturé, fragmentez l'application afin de séparer les éléments Réception des éléments Envoi et Orchestration. Pour ce faire, vous devez créer des hôtes distincts, mapper ces hôtes à une fonctionnalité spécifique (Réception/Envoi/Orchestrations/Suivi) et ajouter des serveurs dédiés à ces hôtes distincts. La fonctionnalité d'orchestration est généralement gourmande en UC. Par conséquent, configurez le système de façon à ce que les orchestrations s'exécutent sur un serveur dédié distinct afin d'améliorer le débit global du système.  
  
 Si plusieurs orchestrations sont déployées, il est possible de les inscrire sur différents hôtes d'orchestration dédiés. Le mappage des serveurs physiques sur des hôtes d'orchestration dédiés permet d'assurer que les différentes orchestrations sont isolées et ne se disputent pas les ressources partagées au sein d'un même espace d'adressage physique ou sur un même serveur.  
  
### <a name="memory-starvation"></a>Insuffisance de mémoire  
 Des scénarios de débits élevés ont pu augmenter la demande au niveau de la mémoire du système. Étant donné que les processus 32 bits sont limités par la quantité de mémoire à leur disposition, il est recommandé de séparer les fonctionnalités Réception/Traitement/Envoi sur des instances d'hôte distinctes de façon à ce que chaque hôte bénéficie d'un espace d'adressage de 2 Go propre. De plus, si plusieurs instances d'hôte sont exécutées sur le même serveur physique, il est conseillé de passer à 4 ou 8 Go de mémoire afin de ne pas avoir à transférer des données sur disque à partir de la mémoire réelle. Peuvent contenir des orchestrations à long terme sur la mémoire allouée plus à l’origine d’encombrement de mémoire et par conséquent, la limitation. Les messages volumineux peuvent également entraîner la consommation de mémoire élevée.  
  
 Il est possible de remédier à ce problème d’encombrement de mémoire lors du traitement des messages volumineux en diminuant la **taille de file d’attente de messages interne** et **Messages In-process par UC** valeurs de l’hôte spécifique.  
  
### <a name="disk-contention"></a>Conflit au niveau des disques  
 Si les disques sont saturés (par exemple, transports File/MSMQ) vous pouvez mettre à niveau vers plusieurs piles et à la technologie RAID 1 + 0. En outre chaque fois que vous utilisez le fichier transport il est important de s’assurer que les dossiers (réception et envoi) n’augmentent pas trop volumineux (> 50 000 fichiers).  
  
 Le dossier Réception peut augmenter si BizTalk Server limite l'entrée des données dans le système pour les raisons mentionnées ci-dessous. Il est également important de transférer les données à partir du dossier d'envoi afin que l'augmentation de ce dossier n'empêche pas BizTalk Server d'écrire de nouvelles données. Pour les files d'attente MSMQ non transactionnelles, il est conseillé de créer les files de réception à distance afin que les conflits de disques soient limités sur le serveur BizTalk.  
  
 Cette configuration (files d'attentes non transactionnelles distantes) présente également l'avantage d'une disponibilité élevée étant donné que le serveur distant hébergeant la file d'attente peut être mis en cluster.  
  
### <a name="other-system-resource-contention"></a>Conflit au niveau d'autres ressources système  
 En fonction de la nature du transport configuré, il peut être nécessaire de configurer des ressources système telles que IIS pour HTTP/SOAP (par exemple, MaxIOThreads, MaxWorkerThreads).  
  
### <a name="downstream-bottlenecks"></a>Goulots d'étranglement en aval  
 Si le système en aval ne reçoit pas les données BizTalk assez rapidement, ces données de sortie sont sauvegardées dans les bases de données BizTalk, ce qui entraîne un encombrement générant une activation des limitations. Le pipeline de réception est alors réduit, ce qui affecte le débit global du système BizTalk. Un signe direct de ce problème peut être l'augmentation de la mise en file d'attente.  
  
### <a name="throttling-impact"></a>Impact des limitations  
 L'activation des limitations permet de protéger le système contre toute défaillance irrécupérable. Grâce à ces limitations, vous pouvez vérifier si le système fonctionne normalement et découvrir l'origine du problème. Une fois la source des goulots d'étranglement identifiée dans l'état de limitation, analysez les autres compteurs de performances pour accéder à la cause du problème.  
  
 Par exemple, un conflit important au niveau de la base de données MessageBox peut être dû à une utilisation intensive de l'UC, qui peut découler d'une pagination excessive sur le disque, elle-même due à une mémoire insuffisante. Un conflit important associé à MessageBox peut également être dû à un conflit de verrouillage découlant de lecteurs de disques saturés.  
  
## <a name="biztalk-application-counters"></a>Compteurs d'application BizTalk  
  
|Objet|Instance|Compteur| Description|  
|------------|--------------|-------------|-----------------|  
|Messagerie BizTalk|RxHost|Nombre de documents reçus par seconde|Vitesse d'entrée|  
|Messagerie BizTalk|TxHost|Nombre de documents traités par seconde|Vitesse de sortie|  
|Orchestrations XLANG/s|PxHost|Orchestrations réussies par seconde|Vitesse de traitement|  
|BizTalk : MessageBox : compteurs généraux|MsgBoxName|Taille mise en file d'attente|Taille cumulée de toutes les files d'attente hôte|  
|BizTalk : MessageBox : compteurs généraux|MsgBoxName|Taille données de suivi|Taille de la table TrackingData de la MessageBox|  
|Compteurs de BizTalk:MessageBox:Host|PxHost:MsgBoxName|File d'attente hôte - Longueur|Nombre de messages dans la file d'attente hôte spécifiée|  
|Compteurs de BizTalk:MessageBox:Host|TxHost:MsgBoxName|File d'attente hôte - Longueur|Nombre de messages dans la file d'attente hôte spécifiée|  
|BizTalk:agent des messages|RxHost|Taille des bases de données|Taille de la file d'attente de publication (PxHost)|  
|BizTalk:agent des messages|PxHost|Taille des bases de données|Taille de la file d'attente de publication (TxHost)|  
|BizTalk:agent des messages|HostName|État de limitation de remise de messages|Affecte les transports XLANG et sortants|  
|BizTalk:agent des messages|HostName|État de limitation de publication de messages|Affecte les transports XLANG et entrants|  
  
### <a name="where-do-i-start"></a>Par où commencer ?  
 Analyse le **état de limitation de remise de messages** et **état de limitation de publication de messages** pour chaque hôte instance est généralement un bon point de départ. Si la valeur de ces compteurs n'est pas zéro, cela signifie que des limitations sont appliquées au système BizTalk et qu'il est possible de rechercher plus avant la cause du goulot d'étranglement. Pour obtenir des descriptions sur les autres compteurs de performance, consultez [identifier les goulots d’étranglement au niveau de la base de données](http://msdn.microsoft.com/library/f1dc58b5-73b0-41b5-9a1e-c0698485c732).  
  
## <a name="backlog-buildup"></a>Accumulation de travaux en retard  
 Pour un scénario de déploiement 1-1 pour lequel un 1 message reçu génère 1 message traité et transmis, si la vitesse de sortie n'est pas égale à la vitesse d'entrée, des travaux en retard s'accumulent au sein du système. Dans ce cas, il est possible de surveiller la taille de la mise en file d'attente.  
  
 Si la file d'attente augmente de manière linéaire, il est possible d'approfondir les recherches afin de découvrir la file d'attente d'application responsable de cette augmentation.  
  
 Si aucune file d'attente d'application ne grandit et que la mise en file d'attente continue d'augmenter, cela peut signifier que les travaux de purge ne suivent pas le rythme, soit parce que l'agent n'est pas exécuté, soit en raison d'un conflit d'autres ressources système sur le serveur SQL.  
  
 Si aucune file d'attente d'application ne grandit, il est important de diagnostiquer la cause de cette augmentation. Surveillez les ressources du système qui ne parvient pas à vider la file d'attente d'application spécifiée (par exemple, la file d'attente d'hôte d'orchestration qui augmente en raison d'une UC insuffisante sur le serveur). Vérifiez également les valeurs du compteur de limitations de l'instance d'hôte spécifique.  
  
 Si l'état de remise/publication ne présente pas la valeur zéro, vérifiez cette valeur afin de confirmer la raison de la limitation (par exemple, dépassement du seuil de la mémoire, nombre de messages en vol trop élevé, etc.).  
  
## <a name="f1-profiler"></a>Générateur de profils F1  
 Grâce aux compteurs de performances, il est possible de détecter rapidement, à un niveau élevé, l'emplacement d'un goulot d'étranglement. Cependant, une fois la recherche affinée, il peut se révéler nécessaire de rechercher la solution au problème jusque dans le code. Le Générateurs de profils F1 fourni avec Visual Studio est un outil qui peut se montrer très utile au diagnostic de l'utilisation des cycles de code.  
  
 Les symboles sont importants pour faciliter la création d'une pile plus utile (en particulier pour du code non managé). Ainsi, le Générateur de profils F1 peut permettre de déterminer de façon très précise le nombre d'appels, ainsi que le temps de retour d'un appel d'API. Encore plus en avant dans la pile, il peut être possible de détecter la cause sous-jacente de la latence élevée. Il peut s'agir d'un appel bloquant vers une requête de base de données ou simplement d'un appel d'attente d'un événement.  
  
## <a name="l2l3-cache"></a>Cache L2/L3  
 Les principaux avantages (d'un point de vue matériel) dont vous pouvez bénéficier découlent de l'utilisation du cache interne de l'UC. L'augmentation de cette mémoire cache permet d'accroître le taux d'accès au cache et de réduire ainsi la nécessité pour le système de paginer les données en dehors et à l'intérieur de la mémoire sur le disque.  
  
## <a name="64-bit-performance-bottlenecks"></a>Goulots d'étranglement des performances 64 bits  
 Les performances des systèmes 64 bits peuvent paraître inférieures à celles qu'il est possible d'atteindre sur les systèmes 32 bits. Ceci est dû à plusieurs raisons, la plus importante étant la mémoire.  
  
 L'évaluation des performances sur un système 32 bits avec 2 Go de mémoire et la comparaison des résultats avec ceux obtenus sur un système 64 bits similaire avec 2 Go de mémoire ne constitue pas une véritable comparaison. Le système 64 bits semblera être lié aux entrées/sorties du disque (% d'inactivité du disque faible & longueur de file d'attente du disque importante) et lié à l'UC (UC max. & basculements de contexte élevés). Cependant, ce n'est pas parce que l'exécution d'une E/S de fichier est plus onéreuse.  
  
 Le système 64 bits est plus gourmand en mémoire (adressage 64 bits), ce qui fait que le système d'exploitation consomme la plupart des 2 Go de mémoire disponible. Dans ce cas, la plupart des autres opérations entraînent une pagination sur le disque, ce qui affecte le sous-système de fichiers. Le système utilise alors les cycles de l'UC pour effectuer une pagination à la fois de données et de code à l'intérieur et à l'extérieur de la mémoire. De plus, il subit l'importante latence du disque. Cela se traduit par un plus grand nombre de conflits sur le disque et par une plus grande utilisation de l'UC.  
  
 Pour résoudre ce problème, vous pouvez procéder à une évolution verticale du serveur, à savoir augmenter sa mémoire (idéalement 8 Go). Cependant, le fait d'ajouter de la mémoire ne permet pas d'améliorer le débit, sauf si l'origine du problème est une UC insuffisante due à une mémoire faible.  
  
## <a name="using-bam-to-identify-bottlenecks-and-high-latency-issues"></a>Utilisation de l'analyse BAM pour identifier les goulots d'étranglement et les problèmes de latence  
 Lorsque la latence est trop faible, vous pouvez utiliser l'analyse BAM pour calculer le temps mis par le système pour réaliser chaque étape du système BizTalk. Bien que les données des instances de service et des événements de message suivis puissent être utilisées pour déboguer l'état des messages et diagnostiquer l'origine des problèmes de routage des messages, l'analyse BAM permet de vérifier plusieurs éléments au sein du flux de messages. En créant un modèle de suivi BAM (définition d'une activité avec des continuations), vous pouvez calculer la latence entre les différentes parties du système afin de découvrir les étapes les plus onéreuses du processus de workflow.
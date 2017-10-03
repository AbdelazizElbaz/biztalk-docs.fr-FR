---
title: "Les goulots d’étranglement au niveau de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ad36897-4e4a-43b9-9cb7-0bf22bd954fb
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ce311461f4273b057c65913d3024f8092f87d1e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bottlenecks-in-the-biztalk-server-tier"></a>Goulots d’étranglement au niveau de BizTalk Server
Le niveau BizTalk peut être divisé en plusieurs zones fonctionnelles :  
  
-   Réception  
  
-   Traitement  
  
-   Transmission  
  
-   Suivi  
  
-   Autres  
  
 Pour ces zones, si les ressources système (processeur, mémoire et disque) semblent saturées, mettre à niveau le serveur en passant à la plateforme ou déconnecter en fonction des caractéristiques de votre application. Si les ressources système ne sont pas saturées, suivez les procédures décrites dans cette section.  
  
## <a name="bottlenecks-in-the-receive-location"></a>Goulots d’étranglement dans l’emplacement de réception  
 Si les messages s’accumuler au niveau de l’emplacement de réception (par exemple, dossier de réception de fichier devient volumineuse), cela indique que le système ne parvient à absorber les données assez rapidement pour respecter la charge entrante. Cela est dû à une limitation interne. Autrement dit, BizTalk Server permet de réduire la vitesse de réception si les abonnés ne peuvent pas traiter les données rapidement suffisamment accumulation de file d’attente à l’origine dans les tables de base de données. Si le goulot d’étranglement est provoqué par des limites matérielles, essayez l’évolution verticale. Pour plus d’informations sur l’évolution verticale, consultez les rubriques suivantes dans la documentation de BizTalk Server 2010 :  
  
-   [Mise à l’échelle verticale du niveau de BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=158073) (http://go.microsoft.com/fwlink/?LinkId=158073).  
  
-   [L’évolution verticale du niveau SQL Server](http://go.microsoft.com/fwlink/?LinkId=158077) (http://go.microsoft.com/fwlink/?LinkId=158077).  
  
 Il est également possible de faire évoluer en ajoutant une instance d’hôte (serveur) pour l’hôte mappé sur le Gestionnaire de réception. Pour plus d’informations sur la montée en puissance parallèle, consultez les rubriques suivantes dans la documentation de BizTalk Server 2010 :  
  
-   [Évolution horizontale du niveau de BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=158076) (http://go.microsoft.com/fwlink/?LinkId=158076).  
  
-   [Montée en puissance parallèle du niveau SQL Server](http://go.microsoft.com/fwlink/?LinkId=158075) (http://go.microsoft.com/fwlink/?LinkId=158075).  
  
 Utilisez Perfmon pour surveiller l’utilisation des ressources sur le système. Il est important de confirmer que l'emplacement de réception externe n'est pas à l'origine du goulot d'étranglement. Par exemple, vérifiez si le partage de fichiers distant est saturé en raison d’e/s disque élevée, le serveur qui héberge la file d’attente sortante distante n’est pas saturé ou le client utilisé pour générer une charge HTTP n’est pas privé sur des threads.  
  
## <a name="processing-bottlenecks"></a>Des goulots d’étranglement  
 Si la file d’attente hôte-compteur de performances augmente, il signifie que les orchestrations ne s’effectuent pas assez rapidement. Pour plus d’informations, consultez la table des compteurs Perfmon dans cette rubrique. Ce problème peut être dû à un conflit de mémoire ou à une saturation de l'UC.  
  
 Si les serveurs d'orchestration constituent le goulot d'étranglement, utilisez l'utilitaire Perfmon pour en identifier la source.  
  
 Si le serveur est lié à l'UC, prenez en compte les éléments suivants :  
  
-   Si le flux de travail est complexe, envisagez de fractionner l’orchestration en plusieurs orchestrations plus petites.  
  
    > [!NOTE]  
    >  Le fractionnement d'une orchestration en plusieurs workflows peut engendrer une latence supplémentaire et une plus grande complexité. Plusieurs flux de travail peut également entraîner une augmentation du nombre de messages publiés dans et utilisées à partir de la BizTalkMsgBoxDb, placer la pression supplémentaire sur la base de données.  
  
-   Si vous utilisez des mappages complexes, considérez si elles peuvent être déplacés vers les ports de réception/envoi. Veillez à vérifier les ports qui ont une bande passante supplémentaire.  
  
-   Envisagez une évolution verticale du matériel ou la montée en puissance parallèle en configurant un serveur de traitement supplémentaire.  
  
## <a name="transmitting-bottlenecks"></a>Les goulots d’étranglement de transmission  
 Si le serveur qui héberge les adaptateurs d’envoi est saturé sur les ressources (par exemple, disque, mémoire ou processeur), envisagez une évolution verticale le serveur ou une évolution horizontale avec supplémentaires envoyer des serveurs hôtes. Le niveau d'envoi peut devenir le goulot d'étranglement si la destination (externe à BizTalk) ne parvient pas à recevoir les données assez rapidement. Les messages s'accumulent alors dans la base de données MessageBox (application SendHostQ).  
  
 Si les points de terminaison sont dans l’étendue de la topologie, isoler la cause à la destination. Par exemple, déterminez si l’emplacement HTTP est configuré correctement pour recevoir la charge. Si ce n’est pas le cas, envisagez la montée en puissance parallèle. Pour déterminer si la destination est-elle en raison d’une sortie excessive les messages envoyés par BizTalk. Si Oui, vous devrez peut-être un plan de maintenance pour archiver et purger les messages de destination. Grand nombre de fichiers dans un dossier de destination peut entraver sérieusement la capacité du service BizTalk pour valider des données sur le lecteur de disque.  
  
## <a name="tracking-bottlenecks"></a>Suivi des goulots d’étranglement  
 L’instance d’hôte de suivi est chargée de déplacer les données d’analyse BAM (Business Activity) et d’intégrité et d’activité de suivi du fonctionnement (HAT) à partir de la base de données MessageBox (table TrackingData) vers les tables de base de données des suivis BizTalk et/ou d’importation principale BAM. Si plusieurs bases de données MessageBox sont configurés, le suivi des instance de l’hôte utilise quatre threads par base de données MessageBox.  
  
 Il est possible que l’instance d’hôte de suivi est lié à l’UC. S’il est, envisagez une évolution verticale du serveur ou de la montée en puissance en configurant un serveur supplémentaire avec hôte de suivi des modifications activé. Plusieurs instances d’hôte automatiquement équilibre la charge de plusieurs bases de données MessageBox configurée. Pour plus d’informations sur la mise à l’échelle, consultez la rubrique [mise à l’échelle de vos Solutions](http://go.microsoft.com/fwlink/?LinkId=158078) (http://go.microsoft.com/fwlink/?LinkId=158078).  
  
 Si la table TrackingData de la base de données MessageBox devient important, il est généralement parce que les travaux de maintenance des données sur la base de données des suivis BizTalk et/ou d’importation principale BAM ne sont exécutent pas tel que configuré, à l’origine de la croissance des suivis BizTalk et/ou de principale BAM Importer des bases de données. Une fois ces bases de données devenir trop volumineux, il peut avoir un impact négatif sur la capacité de l’hôte de suivi à insérer des données dans la table TrackingData. En effet, les données suivies à sauvegarder dans les tables de base de données MessageBox. La croissance de la table TrackingData activer la limitation de démarrer.  
  
 Vous ne devez activer le suivi minimal requis pour votre application, comme cela réduire la quantité de données consignées et réduire le risque de suivi des goulots d’étranglement. Pour plus d’informations sur la désactivation des paramètres de suivi des éléments individuels, tels que les ports d’envoi/réception et les orchestrations, consultez [comment désactiver le suivi des](http://go.microsoft.com/fwlink/?LinkId=160064) (http://go.microsoft.com/fwlink/?LinkId=160064).  
  
## <a name="other"></a>Autres  
 Configurez la topologie de déploiement de telle façon que les différentes fonctionnalités s'exécutent sur des instances d'hôte dédiées isolées. Ainsi, chaque instance de l’hôte obtient son propre ensemble de ressources (par exemple, sur un système 32 bits, espace d’adressage de 2 Go de mémoire virtuelle, handles, threads). Si le serveur est a suffisamment de marge d’UC et de mémoire pour héberger plusieurs instances d’hôte, ils peuvent être configurés pour s’exécuter sur le même ordinateur physique. Si ce n’est pas le cas, envisagez la montée en puissance parallèle en déplaçant la fonctionnalité vers des serveurs dédiés. Le fait d'exécuter une même fonctionnalité sur plusieurs serveurs permet également de disposer d'une configuration hautement disponible.  
  
## <a name="biztalk-system-performance-counters"></a>Compteurs de performance du système BizTalk  
  
|Objet|Instance|Compteur|Objet de la surveillance|  
|------------|--------------|-------------|------------------------|  
|Processeur|_Total|% temps processeur|Conflit de ressources|  
|Traiter|BTSNTSvc|Octets virtuels|Fuite/encombrement de mémoire|  
|Traiter|BTSNTSvc|Octets privés|Fuite/encombrement de mémoire|  
|Traiter|BTSNTSvc|Nombre de handles|Conflit de ressources|  
|Traiter|BTSNTSvc|Nombre de threads|Conflit de ressources|  
|Disque physique|_Instance|% inactivité|Conflit de ressources|  
|Disque physique|_Instance|Longueur moyenne de la file d'attente du disque|Conflit de ressources|  
  
### <a name="cpu-contention"></a>Contention du processeur  
 Si le processeur est saturé, vous pouvez fragmenter l’application en séparant la réception à partir de l’envoi et l’orchestration. Pour ce faire, créez des hôtes distincts, mapper les ordinateurs hôtes à des fonctionnalités spécifiques (réception/envoi/orchestrations/suivi) et ajouter des serveurs dédiés à ces hôtes distincts. Fonctionnalité d’orchestration est souvent gourmande en ressources processeur. Si vous configurez le système pour les orchestrations s’exécutent sur un serveur dédié distinct, cela peut permettre d’améliorer le débit global du système.  
  
 Si plusieurs orchestrations sont déployées, vous pouvez les inscrire à des hôtes d’orchestration dédié différent. Mappage des serveurs physiques pour les ordinateurs hôtes d’orchestration dédiés permet de s’assurer que les différentes orchestrations sont isolées et ne se disputent pas les ressources partagées dans le même espace d’adressage physique ou sur le même serveur.  
  
 Arrêtez les instances d’hôte non utilisés. Les instances d’hôte inutilisées peuvent sont en concurrence pour les ressources processeur et mémoire en vérifiant régulièrement de la MessageBox pour les messages à traiter. En outre, stop inutilisé emplacements de réception, ports d’envoi et orchestrations.  
  
### <a name="spool-table-growth"></a>Augmentation du spouleur  
 Les goulots d’étranglement en aval et/ou de conflit de ressources peut entraîner la file d’attente démarrer la croissance excessive et réduire les performances globales. Pour plus d’informations, consultez « Augmentation du spouleur » dans [comment identifier les goulots d’étranglement dans la MessageBox Database1](../technical-guides/how-to-identify-bottlenecks-in-the-messagebox-database1.md).  
  
### <a name="memory-starvation"></a>Insuffisance de mémoire  
 Des scénarios de débits élevés ont pu augmenter la demande au niveau de la mémoire du système. Dans la mesure où un processus 32 bits est limité par la quantité de mémoire peuvent consommer, il est recommandé de séparer les fonctionnalités de réception/traitement/envoi en instances d’hôte distinctes, telles que chaque hôte reçoit son propre espace d’adressage de 2 Go. En outre, si plusieurs instances d’hôte sont en cours d’exécution sur le même serveur physique, vous pouvez mettre à niveau à 4 ou 8 Go de mémoire pour éviter le remplacement des données sur le disque à partir de la mémoire réelle. Peuvent contenir des orchestrations à long terme sur plus de mémoire allouée. Cela peut entraîner d’encombrement de mémoire et de limitation pour démarrer. Les messages volumineux peuvent également entraîner la consommation de mémoire élevée.  
  
 Vous pouvez résoudre le problème d’encombrement de mémoire qui se produit lors du traitement des messages volumineux en diminuant la **taille de file d’attente de messages interne** et **Messages In-process par UC** valeurs de l’hôte spécifique.  
  
> [!NOTE]  
>  Si la latence est un critère important, devient **taille de file d’attente de messages interne** et **Messages In-process par UC** doivent être effectuées avec précaution, car cela peut augmenter la latence de bout en bout du système.  
  
### <a name="disk-contention"></a>Contention de disque  
 Si les disques sont saturés (par exemple, avec un grand nombre de transports FILE/MSMQ), vous pouvez mettre à niveau vers plusieurs piles et les disques avec RAID 10. En outre, chaque fois que vous utilisez le transport de fichier, il est important pour vous assurer que la réception et d’envoyer des dossiers n’augmentent pas plus de 50 000 fichiers.  
  
 Le dossier de réception peut augmenter si BizTalk Server limite les données entrantes dans le système. Il est important de déplacer des données à partir du dossier d’envoi afin que l’augmentation de ce dossier n’affecte pas la capacité de BizTalk Server à écrire des données supplémentaires. Pour les files d’attente non transactionnelle de MSMQ, il est recommandé de création à distance les files d’attente de réception afin que la contention de disque est réduite sur le serveur BizTalk.  
  
 La configuration de la file d’attente non transactionnelle distante fournit également une haute disponibilité du serveur distant qui héberge la file d’attente peut être mis en cluster.  
  
### <a name="other-system-resource-contention"></a>Autres contention des ressources système  
 Selon le type de transport, il peut être nécessaire de configurer les ressources système telles que IIS pour HTTP (par exemple, MaxIOThreads, MaxWorkerThreads).  
  
 Avec ASP.NET 2.0 et ASP.Net 4, le \<processModel autoConfig = « true » / > dans le fichier machine.config configure automatiquement les paramètres suivants pour optimiser les performances :  
  
-   Maximum de Threads  
  
-   Threads d’e/s maximales  
  
-   attribut minFreeThreads de l’élément httpRuntime  
  
-   attribut minLocalRequestFreeThreads de l’élément httpRuntime  
  
-   attribut maxConnection de la \<connectionManagement > élément (paramètres réseau)  
  
 Pour plus d’informations sur la configuration des paramètres qui affectent les performances de l’adaptateur, consultez [les paramètres de Configuration ASP.NET pour l’élément processModel](http://go.microsoft.com/fwlink/?LinkId=158080) (http://go.microsoft.com/fwlink/?LinkId=158080).  
  
 Pour plus d’informations sur les paramètres de configuration qui peuvent affecter les adaptateurs BizTalk Server, consultez [les paramètres de Configuration qui affectent les performances carte](http://go.microsoft.com/fwlink/?LinkID=154200) (http://go.microsoft.com/fwlink/?LinkID=154200).  
  
 En plus de l’optimisation de vos applications BizTalk Server, les autres applications ASP.NET exécutées sur le même serveur peuvent avoir une incidence sur les performances globales. Il est important d’optimiser l’ensemble de vos applications ASP.NET pour réduire la sollicitation des ressources système. Pour plus d’informations, consultez [ASP.NET Performance](http://go.microsoft.com/fwlink/?LinkId=158081) (http://go.microsoft.com/fwlink/?LinkId=158081).  
  
 Lorsque vous configurez pour optimiser les performances, envisagez d’optimiser les autres systèmes externes tels que messagerie moteurs (Message Queuing, MQSeries), les applications, les bases de données, Active Directory, etc. qui font partie de votre solution BizTalk globale. Les goulots d’étranglement de performances dans un de ces autres systèmes externes peuvent avoir un effet négatif sur votre solution BizTalk.  
  
### <a name="downstream-bottlenecks"></a>Goulots d’étranglement en aval  
 Si le système en aval est incapable de recevoir des données suffisamment rapides de BizTalk, ces données de sortie sauvegardera dans les bases de données BizTalk. Cela entraîne l’encombrement, provoque la limitation Démarrer, réduit le pipeline de réception et a un impact sur le débit global du système BizTalk. Un signe direct de ce est l’augmentation du spouleur. Pour plus d’informations sur les goulots d’étranglement et la table du spouleur, consultez [comment identifier les goulots d’étranglement dans la MessageBox Database1](../technical-guides/how-to-identify-bottlenecks-in-the-messagebox-database1.md).  
  
### <a name="throttling-impact"></a>Impact des limitations  
 La limitation sera finalement commencer à protéger le système d’atteindre un état irrécupérable. Par conséquent, vous pouvez utiliser la limitation pour vérifier si le système fonctionne normalement et découvrir l’origine du problème. Après avoir identifié la cause du goulot d’étranglement à partir de l’état de limitation, analysez les compteurs de performances pour déterminer la source du problème. Par exemple, une contention élevée sur la base de données MessageBox est peut-être en raison d’une utilisation élevée du processeur, due à la pagination excessive sur le disque qui est provoquée par une mémoire insuffisante. Une contention élevée sur la base de données MessageBox peut également provenir d’un conflit de verrouillage en raison des lecteurs de disques saturés. Occasionnel de limitation n’est pas une menace importante pour les performances, la limitation persistantes peut indiquer un problème de sous-jacent plus important. Pour plus d’informations sur ces conditions où BizTalk Server utilise la limitation, consultez [comment BizTalk Server implémente la limitation des hôtes](http://go.microsoft.com/fwlink/?LinkID=155286) (http://go.microsoft.com/fwlink/?LinkID=155286).  
  
 Pour plus d’informations sur comment BizTalk Server de limitation peut aider à gérer l’utilisation des ressources disponibles et réduire les conflits de ressources, consultez [optimisation des ressources d’utilisation via la limitation des hôtes](http://go.microsoft.com/fwlink/?LinkID=155770) (http://go.microsoft.com/fwlink/?LinkID=155770).  
  
## <a name="biztalk-application-counters"></a>Compteurs d’application BizTalk  
  
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
 Analyse le **état de limitation de remise de messages** et **état de limitation de publication de messages** pour chaque hôte instance est un bon point de départ. Si la valeur de ces compteurs n’est pas zéro, cela indique que la limitation dans le système BizTalk et vous pouvez les analyser la cause du goulot d’étranglement. Pour obtenir des descriptions sur les autres compteurs de performance, consultez [les goulots d’étranglement au niveau de la base de données](../technical-guides/bottlenecks-in-the-database-tier.md).  
  
## <a name="orchestration-engine-performance-counters"></a>Compteurs de performances du moteur d’orchestration  
 Nous vous recommandons vivement de fine régler les paramètres d’exécution d’orchestration, car les points dehydration\rehydration et de persistance d’orchestration en continu peuvent avoir un impact majeur sur les performances globales.  Vous devez utiliser les compteurs suivants lorsque vous testez des orchestrations complexes qui peuvent contenir plusieurs points de persistance et étendues transactionnelles.  
  
|Compteur|Commentaires|  
|-------------|--------------|  
|Orchestrations dehydrated/sec (Orchestrations mises en attente par seconde)|Nombre moyen d'orchestrations mises en attente par seconde.|  
|Orchestrations rehydrated/sec (Orchestrations réalimentées par seconde)|Nombre moyen d'orchestrations réalimentées par seconde.|  
|Points de persistance par seconde|Nombre moyen d'instances d'orchestration enregistrées par seconde.|  
|Orchestrations résidentes en mémoire|Nombre d'instances d'orchestration actuellement hébergées par l'instance de l'hôte.|  
|Orchestrations completed/sec (Orchestrations réussies par seconde)|Nombre moyen d'orchestrations réussies par seconde.|  
|Orchestrations suspended/sec (Orchestrations suspendues par seconde)|Nombre moyen d'orchestrations suspendues par seconde.|  
|Étendues transactionnelles validées par seconde|Nombre moyen d'étendues réussies par seconde.|  
|Étendues transactionnelles interrompues par seconde|Nombre moyen d'étendues suspendues par seconde.|  
|Étendues transactionnelles compensées par seconde|Nombre moyen d'étendues compensées par seconde.|  
  
## <a name="backlog-buildup"></a>Création de la file d’attente  
 Pour un déploiement 1-1 scénario où 1 message reçu génère 1 message traité et transmis, si la vitesse de sortie n’est pas la vitesse d’entrée, il existe un retard dans le système. Dans ce cas, vous pouvez surveiller la taille de la mise en attente. Lorsque vous déterminez la cause de goulots d’étranglement de la vitesse de sortie, exécuter un scénario de cas d’usage unique à la fois. Isoler les orchestrations, les emplacements de réception et les emplacements à différents hôtes d’envoi.  
  
 Ajoutez les compteurs de zone : hôte de BizTalk à votre journal de l’Analyseur de performances pour surveiller un hôte. La file d’attente hôte - longueur : compteur effectue le suivi du nombre total de messages dans une file d’attente hôte particulier. Si un ou plusieurs de ces compteurs continue de croître au fil du temps, une attention toute particulière à donner à ces artefacts exécuté par ces ordinateurs hôtes.  
  
 Si la file d’attente augmente linéairement, déterminer quel file d’attente de l’Application est responsable de cette augmentation.  
  
 Si aucun des files d’attente de l’Application ne grandit et que la file d’attente continue de croître, cela peut signifier que les travaux de purge ne parvenez pas à suivre. Cela se produit si l’agent n’est pas en cours d’exécution ou d’autres contention des ressources système sur le serveur SQL Server.  
  
 Si une des files d’attente de l’Application est-elle diagnostiquer la cause de cette croissance. Analyser les ressources système sur le système ne parvient pas à vider la file d’attente d’Application spécifiques (par exemple, Orchestration hôte augmente en raison d’une UC insuffisante sur le serveur). En outre, vérifiez les valeurs du compteur de limitation de l’instance d’hôte spécifique.  
  
 Si les compteurs de performances état de limitation de remise BizTalk:Messsage Agent de Message et l’état de limitation de publication de messages ne sont pas nulles, vérifiez la valeur pour confirmer la raison de la limitation (par exemple, le seuil de mémoire a dépassé, nombre de messages en vol trop haute, et ainsi de suite).  
  
## <a name="stand-alone-profiler"></a>Profileur autonome  
 Vous pouvez utiliser des compteurs de performances pour détecter l’emplacement de goulot d’étranglement à un niveau élevé. Toutefois, affinée, vous aurez peut-être besoin d’examiner le code plus étroitement pour faciliter le problème. Le profileur autonome qui est fourni avec Visual Studio 2010 peut être un outil très utile pour aider à diagnostiquer où le code est dépense des cycles. Pour plus d'informations, consultez  
  
## <a name="l2l3-cache"></a>Cache L2/L3  
 À partir d’un point de vue matériel, vous pouvez obtenir des avantages majeurs à l’aide du cache du processeur intégré. L'augmentation de cette mémoire cache permet d'accroître le taux d'accès au cache et de réduire ainsi la nécessité pour le système de paginer les données en dehors et à l'intérieur de la mémoire sur le disque.  
  
## <a name="64-bit-performance-bottlenecks"></a>Goulots d’étranglement des performances 64 bits  
 Les performances des systèmes 64 bits peuvent paraître inférieures à celles qu'il est possible d'atteindre sur les systèmes 32 bits. Cela est possible pour les raisons suivantes, celle la plus importante étant la mémoire.  
  
 Mesure des performances sur un système 32 bits avec 2 Go de mémoire et la comparaison des résultats avec un système 64 bits similaire avec 2 Go de mémoire sont comparaison pas la même chose. Le système 64 bits semble être disque e/s liée (temps d’inactivité du disque faible % & longueur de file d’attente de disque élevée) et lié à l’UC (UC max. et changement de contexte élevé). Toutefois, il s’agit pas, car les e/s de fichier sur un système 64 bits sont plus coûteuses.  
  
 Le système 64 bits est davantage de mémoire intensif (adressage 64 bits) qui entraîne le système d’exploitation consomme la plupart de la mémoire disponible de 2 Go. Dans ce cas, la plupart des autres opérations entraînent une pagination sur le disque, ce qui affecte le sous-système de fichiers. Par conséquent, le système passe à la pagination en entrée/sortie de la mémoire à la fois les cycles de processeur et de code et n’est affecté par la latence du disque élevée. Cela se traduit par un plus grand nombre de conflits sur le disque et par une plus grande utilisation de l'UC.  
  
 La façon d’atténuer ce problème consiste à montée en puissance parallèle du serveur par la mise à niveau de la mémoire. L’évolution verticale à 8 Go est l’idée, toutefois, l’ajout de mémoire ne sera pas d’améliorer le débit, sauf si la source du problème est une UC insuffisante en raison d’une insuffisance de mémoire.  
  
## <a name="using-bam-to-identify-bottlenecks-and-high-latency-issues"></a>L’analyse BAM pour identifier les goulots d’étranglement et les problèmes de latence élevée  
 Lorsque la faible latence est importante, vous pouvez utiliser BAM pour mesurer le temps du système pour réaliser chaque étape au sein du système BizTalk Server. Vous pouvez utiliser du fonctionnement pour déboguer l’état des messages et diagnostiquer l’origine des problèmes de routage des messages, vous pouvez utiliser BAM pour effectuer le suivi de plusieurs éléments au sein du flux de messages. En créant un modèle qui définit une activité à une continuation de suivi de BAM, vous pouvez mesurer la latence entre les différentes parties du système pour faciliter le suivi des étapes les plus onéreuses dans le processus de flux de travail.  
  
 Vous pouvez utiliser le débogueur de l’Orchestration dans l’outil HAT pour interroger une instance suspendue, reprise de l’instance en mode débogage et ajouter des points d’arrêt appropriés à l’aide de l’affichage des détails techniques. Ceci vous permettra de suivre vos activités et les messages de débogage pas à pas.  
  
 Vous pouvez définir des points d'arrêt pour suivre les événements suivants :  
  
-   Début/fin d'une orchestration  
  
-   Début/fin d'une forme  
  
-   Envoi ou réception d'un message  
  
-   Exceptions  
  
 À chaque point d'arrêt, vous pouvez examiner les informations sur les variables locales, les messages et leurs propriétés, les ports et les liens-rôles.  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche et suppression des goulots d’étranglement](../technical-guides/finding-and-eliminating-bottlenecks.md)
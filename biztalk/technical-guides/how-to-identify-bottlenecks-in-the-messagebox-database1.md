---
title: "Comment identifier les goulots d’étranglement dans la MessageBox Database1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a039164-5ca6-4cbc-b307-c5d4ae800689
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b25a575f8cd6a3f7d7239ce20cb4d3befdde1966
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-identify-bottlenecks-in-the-messagebox-database"></a>Identification des goulots d'étranglement dans la base de données MessageBox
Pour identifier les goulots d'étranglement dans la base de données MessageBox, commencez par vous assurer que le service SQL-Server-Agent est démarré. Modifier l’état de démarrage du Service de manuel à Auto afin que si le serveur est redémarré, le service redémarrera automatiquement.  
  
 Par défaut, le service BizTalk est limité si les tables du spouleur, TrackingData ou ApplicationQ augmentent. Ces tables sont nettoyées par les travaux de l’Agent SQL, qui, si ne pas en cours d’exécution entraîne augmenter le spouleur à l’origine de la bande passante à démarrer et protéger la base de données de toute pression supplémentaire. Vérifiez l'état des compteurs de performances suivants :  
  
-   BizTalk : agent des messages (nom de l'hôte) état de limitation de remise de messages  
  
-   BizTalk : agent des messages (nom de l'hôte) état de limitation de publication de messages  
  
 Une valeur « 0 » indique aucune limitation n’est appliquée. Une valeur de « 6 » indique que le système est la limitation en raison d’une croissance de la base de données. Pour plus d’informations sur la façon d’interpréter les valeurs de ces compteurs, consultez [quelle est la limitation des hôtes ?](http://go.microsoft.com/fwlink/?LinkID=154694) (http://go.microsoft.com/fwlink/?LinkID=154694) et [hôte la limitation des compteurs de Performance](http://go.microsoft.com/fwlink/?LinkID=155285) (http://go.microsoft.com/fwlink/?LinkID=155285) dans la documentation de BizTalk Server 2010.  
  
## <a name="spool-table-growth"></a>Augmentation du spouleur  
 Le spouleur peut augmenter pour de multiples raisons. Une augmentation fait augmentent si les files d’attente de l’Application. Celles-ci peuvent augmenter en raison d’une raisons telles que des goulots d’étranglement en aval et/ou de contention des ressources.  
  
 Si les files d’attente d’Application sont de petite taille et de la file d’attente est toujours volumineux, vérifiez que les travaux de purge sont face. Vérifiez que le service SQL-Agent est en cours d'exécution puis que les travaux suivants s'effectuent correctement :  
  
-   MessageBox_Message_Cleanup_BizTalkMessageBoxDb  
  
-   MessageBox_Parts_Cleanup_BizTalkMessageBoxDb  
  
 Si la table MessageZeroSum est importante, il indique que les messages ont été traitées. Cela signifie que DeQueue a correctement terminé et supprimer des données à partir des tables de file d’attente de l’Application et les lignes ont été marquées pour suppression. Cependant, les travaux de purge ne sont pas capables de suivre la cadence de suppression des données. Cela peut se produire si l’ordinateur exécutant SQL Server rencontre des conflits d’UC importants, qui affectent la capacité des travaux de purge à suivre en raison d’une UC insuffisante.  
  
## <a name="application-queue-table-growth"></a>Augmentation de la file d’attente application  
 Files d’attente de l’application hébergent les données en cours de transition qui, après traitement, sont nettoyées par DeQueue.  
  
 Une fois ces messages sont traités, la table du spouleur (qui détient les références à ces rangées) peut être nettoyée.  
  
 Par exemple, la file RxHostQ publie des données à l’orchestration PxHostQ. Cette file d’attente publie des données pour l’envoi TxHostQ chacune faisant référence à une ligne dans la table du spouleur. Une fois que les messages pour une file HostQ particulière traités avec succès par le système, ces lignes sont supprimées par DeQueue. Une fois ces rangées supprimées, le spouleur (qui n'est plus référencé par ces rangées) peut alors être nettoyé par les travaux de purge.  
  
 Augmentation de la file d’attente application indique que les instances d’hôte responsables de la purge de la file d’attente de l’Application ne peuvent pas suivre la vitesse d’entrée.  
  
 Par exemple, la file d'attente de l'application d'orchestration (PxHostQ) peut augmenter parce que le serveur chargé du traitement des orchestrations est lié à l'UC et incapable de les traiter plus rapidement. Toutefois, si le serveur de réception est rapide, il peut publier plus rapidement que le serveur d’orchestration peut traiter ce qui entraîne également la croissance de la file d’attente de l’Application.  
  
 Un autre motif de croissance de file d’attente d’orchestration peut être dû à la contention de mémoire. Lorsque plusieurs instances d’orchestration en cours d’exécution longue sont instanciés simultanément dans la mémoire, encombrement de mémoire provoque indirectement la limitation réduire le pool de threads jusqu'à ce que la sollicitation de la mémoire est libérée.  
  
 Une raison pour laquelle la file d’attente d’application envoi peut augmenter fait si le système en aval est incapable de recevoir des messages (sortant de BizTalk Server) assez rapidement. Par conséquent, les messages continuent de résider sur la croissance de file d’attente de l’Application à l’origine du système de BizTalk. Cela peut entraîner la limitation démarrer et de réduire la vitesse de réception affecte le débit global du système.  
  
## <a name="trackingdata-table-growth"></a>Croissance de table TrackingData  
 La table TrackingData de la base de données MessageBox est une table de transition dans laquelle les intercepteurs écrivent des données de suivi pour le suivi de l’intégrité et activité du fonctionnement (HAT) et analyse BAM (Business Activity). Si le suivi a été désactivé, cette table doit être vide. Par défaut, le suivi HAT est activé pour les pipelines et les événements d’entrée/sortie d’orchestrations.  
  
 Si le suivi des corps des messages est activé, vérifiez que le serveur de base de données MessageBox (autrement dit, l’hôte avec « autoriser le suivi de l’hôte ») est en cours d’exécution. S’assurer que l’ordinateur hôte avec « autoriser le suivi de l’hôte » est en cours d’exécution permet de réduire le risque d’un goulot d’étranglement se produit que l’hôte déplace les données à partir de la table TrackingData de la base de données MessageBox vers les tables de base de données des suivis BizTalk.  
  
 Il est possible d’effectuer le suivi des événements personnalisés en activant le suivi HAT personnalisé, par exemple, sur des propriétés promues et le suivi des corps de message. En plus des données de suivi HAT, les données BAM sont également écrites dans la table TrackingData. Le Tracking Data Decode Service (TDDS service, qui s’exécute sur l’instance d’hôte sur lequel le suivi est activé) est chargé de déplacer ces données à partir de la base de données MessageBox pour les bases de données des suivis BizTalk et d’importation principale BAM. Une fois que les données sont déplacées avec succès, le service TDDS supprime ensuite ces données. Les données de suivi des corps de message sont déplacées séparément par le travail de SQL-Agent TrackedMessages_Copy_BizTalkMsgBoxDb.  
  
 Si le service TDDS est incapable de suivre la cadence à laquelle les intercepteurs écrivent les données dans la table TrackingData, cette table augmentera, à l’origine de la limitation Démarrer. Cela affecte le débit. Pour réduire ce problème, assurez-vous d’au moins un hôte est en cours d’exécution avec le suivi activé.  
  
 Si les données continuent de s’accumuler, vérifiez que la base de données des suivis BizTalk n’augmente pas hors de contrôle. En outre, vérifiez l’archivage et le travail de purge est en cours d’exécution et est en mesure de suivre la cadence à laquelle les données arrivent.  
  
> [!NOTE]  
>  Par défaut, le travail de purge est impossible de supprimer des données à partir des tables de base de données des suivis BizTalk jusqu'à ce que ces données ont été archivées. Si vous n’avez pas besoin d’archiver les données de suivi, vous pouvez modifier le travail pour purger la base de données des suivis BizTalk sans l’archivage en suivant les étapes indiquées dans [comment vider les données à partir de la base de données de suivi BizTalk](http://go.microsoft.com/fwlink/?LinkID=153817) (http://go.microsoft.com/ fwlink / ? LinkID = 153817).  
  
## <a name="see-also"></a>Voir aussi  
 [Goulots d’étranglement au niveau de la base de données](../technical-guides/bottlenecks-in-the-database-tier.md)
---
title: "Comment identifier les goulots d’étranglement dans la MessageBox Database2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10b2eb1e-541c-457d-9735-ac6fb069b209
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e69966f0f3ecff5a27788c9a92d4e3f1ac0eae68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-identify-bottlenecks-in-the-messagebox-database"></a>Identification des goulots d'étranglement dans la base de données MessageBox
Pour identifier les goulots d'étranglement dans la base de données MessageBox, commencez par vous assurer que le service SQL-Server-Agent est démarré. Modifiez le mode de démarrage du service de Manuel à Auto : ainsi, le service redémarrera automatiquement en cas de redémarrage du serveur.  
  
 Par défaut, le service BizTalk est limité si le spouleur ou les tables TrackingData ou ApplicationQ augmentent. Ces tables sont nettoyées par les travaux de SQL-Agent qui, s'ils ne s'exécutent pas, font augmenter le spouleur et entraînent l'activation des limitations visant à protéger la base de données de toute pression supplémentaire. Vérifiez l'état des compteurs de performances suivants :  
  
-   BizTalk : agent des messages (nom de l'hôte) état de limitation de remise de messages  
  
-   BizTalk : agent des messages (nom de l'hôte) état de limitation de publication de messages  
  
 La valeur 0 indique qu'aucune limitation n'est appliquée. La valeur 6 indique que le système est limité à cause d'une augmentation de la base de données. Reportez-vous à la documentation relative à l'interprétation des valeurs de ces compteurs.  
  
## <a name="spool-table-growth"></a>Augmentation du spouleur  
 Le spouleur peut augmenter pour de multiples raisons. L'augmentation du spouleur peut être due à l'augmentation des files d'attente de l'application. Celles-ci peuvent augmenter pour diverses raisons, à cause de goulots d'étranglement en aval et/ou un conflit de ressources par exemple.  
  
 Si les files d'attente de l'application sont courtes et si le spouleur reste important, vérifiez que les travaux de purge suivent la cadence. Vérifiez que le service SQL-Agent est en cours d'exécution puis que les travaux suivants s'effectuent correctement :  
  
-   MessageBox_Message_Cleanup_BizTalkMessageBoxDb  
  
-   MessageBox_Parts_Cleanup_BizTalkMessageBoxDb  
  
 Si la table MessageZeroSum est importante, cela signifie que les messages ont été traités (DeQueue s'est terminé avec succès et a supprimé les données des tables de la file d'attente de l'application) et les rangées ont été marquées pour suppression. Cependant, les travaux de purge ne sont pas capables de suivre la cadence de suppression des données. Cela s'explique en partie par les conflits d'UC importants que rencontre SQL Server, qui ont un impact sur la capacité des travaux de purge à suivre la cadence (du fait d'une UC insuffisante).  
  
## <a name="application-queue-table-growth"></a>Augmentation de la file d'attente de l'application  
 Les files d'attente de l'application hébergent les données en cours de transition qui, une fois traitées, sont nettoyées par DeQueue.  
  
 Une fois ces messages traités, le spouleur (qui détient les références à ces rangées) peut être nettoyé.  
  
 Par exemple, la file RxHostQ publie des données dans la file PxHostQ de l'orchestration, qui à son tour publie des données dans la file d'envoi TxHostQ, chaque file référençant une rangée dans le spouleur. Une fois les messages d'une file HostQ particulière traités avec succès par le système, ces rangées sont supprimées par DeQueue. Une fois ces rangées supprimées, le spouleur (qui n'est plus référencé par ces rangées) peut alors être nettoyé par les travaux de purge.  
  
 L'augmentation de la file d'attente de l'application indique que les instances de l'hôte chargées de la drainer ne sont pas capables de suivre la vitesse d'entrée, c'est-à-dire la vitesse à laquelle les messages sont publiés dans une file d'attente donnée de l'application.  
  
 Par exemple, la file d'attente de l'application d'orchestration (PxHostQ) peut augmenter parce que le serveur chargé du traitement des orchestrations est lié à l'UC et incapable de les traiter plus rapidement. Cependant, si le serveur de réception est rapide, il peut publier les messages plus rapidement que le serveur d'orchestration ne peut les traiter, ce qui entraîne également une augmentation de la file d'attente de l'application.  
  
 L'augmentation de la file d'attente de l'orchestration peut également être due à un conflit de mémoire : lorsque de nombreuses instances d'orchestration à long terme sont toutes instanciées en même temps dans la mémoire, celle-ci est alors encombrée et active indirectement la limitation de la réserve de threads, jusqu'à-ce que la pression exercée sur la mémoire se relâche. La file d'attente de l'application d'envoi peut augmenter si le système en aval est incapable de recevoir les messages sortants de BizTalk suffisamment rapidement. Les messages restent donc dans le système BizTalk, ce qui entraîne l'augmentation de la file d'attente de l'application qui finit par activer la limitation de la vitesse de réception, celle-ci ayant un impact sur le débit global du système.  
  
## <a name="trackingdata-table-growth"></a>Augmentation de la table TrackingData  
 La table TrackingData de la base de données MessageBox est une table de transition dans laquelle les intercepteurs écrivent des données de suivi pour le suivi BAM, ainsi que le suivi des messages et des instances de service. Si le suivi a été désactivé, cette table doit être vide. Le suivi des messages et des instances de service est activé par défaut pour les pipelines et les orchestrations dans les événements d'entrée/de sortie.  
  
 Si le suivi des corps de message est activé, assurez-vous que le serveur MessageBox (c'est-à-dire l'hôte dont le suivi est autorisé) est en cours d'exécution. Il limitera le goulot d'étranglement en déplaçant les données de la table TrackingData de la base de données MessageBox vers les tables BizTalkDTADb.  
  
 Il est possible de suivre des événements personnalisés en activant le suivi des messages et des instances de services personnalisé (sur des propriétés promues, par exemple) et le suivi des corps de message. En plus des données de suivi, les données BAM sont également écrites dans cette table. Il incombe à TDDS (l'hôte pour lequel le suivi est activé) de déplacer ces données de la base de données MessageBox vers les bases de données BizTalkDTADb et BAMPrimaryImport, puis de les supprimer une fois le transfert réussi. Les données de suivi des corps de message sont déplacées séparément par le travail de SQL-Agent TrackedMessages_Copy_BizTalkMsgBoxDb.  
  
 Si TDDS est incapable de suivre la cadence à laquelle les intercepteurs écrivent les données dans la table TrackingData, cette table augmentera, ce qui activera des limitations qui auront un impact sur le débit constant. Pour résoudre ce problème, vérifiez qu'au moins 1 hôte est en cours d'exécution avec la fonction de suivi activée.  
  
 Si les données continuent de s'accumuler, vérifiez que la base de données BizTalkDTADb n'augmente pas de manière anarchique. Vérifiez que le travail d'archivage et de purge est en cours d'exécution et qu'il est capable de suivre la cadence à laquelle les données arrivent.  
  
> [!NOTE]
>  Le travail de purge est incapable de supprimer les données des tables BizTalkDTADb tant que ces données n'ont pas été archivées.  
  
 Vérifiez que la table TrackingData n'augmente pas. Vérifiez que le suivi (TDDS) est activé dans au moins 1 instance d'hôte en cours d'exécution. Si la base de données BizTalkDTADb devient trop volumineuse, cela peut nuire à la capacité de TDDS à déplacer les données de la base de données MessageBox vers la base de données BizTalkDTADb.  
  
 L'augmentation de la table TrackingData peut entraîner l'activation de limitations ayant un impact sur le débit d'exécution constant.
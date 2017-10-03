---
title: Planification pour le suivi | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ffc8573-1b4a-47c7-96ab-0471f43facf5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9853fccde9c5fa6e8c223106c8386f19298d0b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-tracking"></a>Planification pour le suivi
Suivi des messages est le processus par lequel les parties d’une instance de message, telles que le corps du message, les propriétés de message et les métadonnées sont stockées dans une base de données, généralement à des fins d’archivage. Parties d’instance de message sont suivies par la suite peuvent être affichés en exécutant des requêtes à partir de la page Hub du groupe dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Outre l’accès aux données archivées, vous pouvez également afficher des données en direct, qui peuvent être un outil très utile pour l’identification et résolution des problèmes dans le développement d’un environnement ou de transfert.  
  
 Étant donné que le processus de suivi des messages peut être consomme beaucoup de ressources, vous devez parcourir cette rubrique avant de créer votre plan.  
  
 Pour plus d’informations sur le suivi, consultez [suivi des activités et](http://go.microsoft.com/fwlink/?LinkId=154187) (http://go.microsoft.com/fwlink/?LinkId=154187).  
  
## <a name="configuring-and-enabling-the-dta-purge-and-archive-sql-agent-job"></a>Configurer et activer le DTA Purge et d’archiver le travail de l’Agent SQL  
 Ce travail Archive et purge les anciennes données à partir de la base de données des suivis BizTalk, évitant ainsi que celui-ci ne deviennent trop volumineuses. Ceci est essentiel pour une intégrité [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système. Une base de données de suivi volumineux commence à affecter les performances de l’hôte de suivi et de tous les autres processus qui interrogent la base de données de suivi.  
  
-   **Assurez-vous que le travail de Purge et archivage SQL Agent est correctement configuré, activé et exécution.** Ce travail n’est pas activé par défaut, car vous devez tout d’abord le configurer pour inclure un répertoire où les fichiers d’archive peuvent être écrite.  
  
-   **Assurez-vous que le travail est en mesure de purger les données de suivi aussi vite que les données de suivi entrantes sont générées.** Il est acceptable pour le travail se trouve derrière pendant les pics de charge, mais il doit toujours être en mesure de rattraper son retard. Si le travail de purge prend du retard et n’est jamais en mesure de rattraper son retard, la base de données des suivis BizTalk continuera de croître et performances sera finalement être affectées.  
  
-   **Passez en revue la purge normale et paramètres de purge dur afin de vous conservez les données suffisamment longtemps mais pas trop longues.** Pour plus d’informations sur ces paramètres, consultez [l’archivage et la purge de la base de données de suivi BizTalk](http://go.microsoft.com/fwlink/?LinkID=153816) (http://go.microsoft.com/fwlink/?LinkID=153816).  
  
-   **Si vous devez uniquement purger les anciennes données et ne le faites pas archiver tout d’abord, puis modifier l’instruction SQL Agent de la fonction pour appeler la procédure stockée « dtasp_PurgeTrackingDatabase ».** Ignore l’étape d’archivage et effectue simplement la purge. Pour plus d’informations sur cette procédure stockée et en modifiant le travail de l’Agent SQL pour l’utiliser, consultez [comment vider les données à partir de la base de données de suivi BizTalk](http://go.microsoft.com/fwlink/?LinkID=153817) (http://go.microsoft.com/fwlink/?LinkID=153817).  
  
-   **Si vous avez besoin de conserver la base de données des suivis BizTalk les fichiers d’archive, assurez-vous que vous disposez d’un processus en place pour restaurer et de les utiliser avec succès.**  
  
-   **Si vous rencontrez des problèmes de performances qui sont momentanément résolus en supprimant la base de données de suivi BizTalk, et que vous souhaitez configurer BizTalk pour collecter des informations de suivi n’est plus, vous souhaiterez envisager de désactiver le suivi global.** Pour plus d’informations sur la façon de désactiver le suivi global, voir la rubrique [la désactivation du suivi Global](http://go.microsoft.com/fwlink/?LinkID=154193) (http://go.microsoft.com/fwlink/?LinkID=154193).  
  
## <a name="creating-a-dedicated-tracking-host"></a>Création d’un hôte de suivi dédié  
 Lorsque l’option à **autoriser le suivi des hôtes** est activée pour un ordinateur hôte dans la console Administration de BizTalk Server, les instances de cet hôte s’exécutera le suivi des données décoder Service TDDS () pour déplacer les données suivies à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox base de données à la base de données des suivis BizTalk. Étant donné que le service TDDS peut consommer beaucoup de ressources, envisagez de créer un hôte de suivi « dédié » pour lequel le **autoriser le suivi de hôte** est activée et qui ne s’exécute pas n’importe quel autre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processus (tels que des cartes ou orchestrations). Si votre groupe BizTalk contient plusieurs serveurs BizTalk, il est également considéré comme une meilleure pratique de créer une instance de cet hôte sur chaque serveur dans le groupe pour fournir une haute disponibilité pour le service TDDS.  
  
## <a name="testing-to-measure-maximum-sustainable-tracking-throughput"></a>Test pour mesurer le débit de suivi maximal acceptable  
 Suivi de message plus long est une activité gourmandes en ressources et si pas correctement gérés peut avoir un effet très néfaste sur les performances de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement. Par conséquent, vous devez mesurer le débit de suivi maximal acceptable pour votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement pour vous assurer que le système est durable et s’exécutera indéfiniment à un débit de message donné. Pour plus d’informations sur la mesure de débit de suivi maximal acceptable, consultez [mesure de débit maximal acceptable de suivi](http://go.microsoft.com/fwlink/?LinkID=153815) (http://go.microsoft.com/fwlink/?LinkID=153815).  
  
##  <a name="BKMK_TrackingBP"></a>Meilleures pratiques pour le suivi  
  
-   **Déterminer les informations que vous devez suivre lors de la planification** : vous devez choisir lors de la planification prépare les informations que vous avez besoin pour effectuer le suivi, afin qu’une fois que vous déployez le projet vous pouvez définir les options de suivi et limiter la quantité de données suivies à vous donner uniquement les informations que vous avez besoin.  
  
-   **Ne suivez pas tous les messages**: nous vous recommandons de pas suivre tous les messages, car chaque fois qu’un message est couvertes, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] effectue une autre copie. Vous pouvez limiter à la place de la portée en effectuant le suivi d’un port spécifique uniquement. Cela permet d’optimiser les performances de votre système et de conserver les bases de données ne soit pas encombré.  
  
-   **Définition du suivi sur les ports d’envoi et ports au lieu d’un pipeline de réception**: Si vous définissez des options de suivi sur les pipelines, vous allez également définir les options de suivi global pour tous les ports qui utilise le pipeline. Cela peut à son tour entraîner beaucoup plus de données en cours de suivi que vous avez l’intention, qui ralentit les performances du système. Au lieu de cela, vous pouvez définir les options de suivi de l’envoi de ports et les ports de réception.  
  
-   **Prendre en compte différents facteurs dès que la taille de la base de données des suivis BizTalk**:  
  
    -   Lors du redimensionnement de la base de données des suivis BizTalk, compte des facteurs de SQL Server, tels que la taille de l’index, en ajoutant un multiplicateur d’urgence pour vos calculs.  
  
    -   Lors de la détermination de la taille des messages dans la base de données des suivis BizTalk, ajoutez la taille moyenne du contexte de message à la taille de message s’il est important par rapport à la taille du message.  
  
    -   Pour limiter la taille des messages dans la base de données des suivis BizTalk, limitez le nombre de propriétés que vous promouvez. Vous devez utilisez promu uniquement des propriétés si vous avez besoin pour le routage, sinon utilisez les champs distinctifs.  
  
    -   Si l’orchestration **forme début et fin** est activée, prenez en compte un événement de début et de fin pour chaque forme de chaque instance d’orchestration est enregistré dans la base de données des suivis BizTalk.
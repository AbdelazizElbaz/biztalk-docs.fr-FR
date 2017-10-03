---
title: "Meilleures pratiques pour la maintenance des bases de données BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93333f41-ee83-4b64-b381-66584a7d5551
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5f6cf1fadf5c039c53e6cca46792c4660353d0c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-maintaining-biztalk-server-databases"></a>Meilleures pratiques pour la maintenance des bases de données BizTalk Server
Cette rubrique répertorie quelques-unes des meilleures pratiques de maintenance [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.  
  
-   Assurez-vous que l’Agent SQL Server est en cours d’exécution sur le serveur SQL Server. Lorsque l’Agent SQL Server est arrêté, les travaux BizTalk SQL Server Agent intégrées qui sont chargés de maintenance de base de données ne peut pas s’exécuter. Ce comportement provoque la croissance de la base de données, et cette croissance peut entraîner des problèmes de performances. Pour plus d’informations sur la surveillance des travaux de l’Agent SQL Server, consultez [analyse les travaux de l’Agent SQL Server](../technical-guides/monitoring-sql-server-agent-jobs.md).  
  
-   Assurez-vous que les fichiers MDF et de SQL Server LDF se trouvent sur des lecteurs distincts. Les fichiers LDF et MDF pour les bases de données BizTalkMsgBoxDb et BizTalkDTADb sur le même lecteur peut entraîner de contention de disque.  
  
-   N’activez pas le corps du message de suivi, si ce n’est pas requis. Fréquemment, il pouvez que vous souhaitez activer le suivi des corps du message lors du développement et de résoudre les problèmes d’une solution. Dans ce cas, assurez-vous que vous désactivez le suivi des modifications lorsque vous avez terminé le corps du message. Si vous conservez le suivi des corps de message activée, la croissance des bases de données BizTalk Server. Si vous avez un besoin commercial qui vous oblige à activer le suivi des corps de message, vérifiez que le **TrackedMessages_Copy_BizTalkMsgBoxDb** et **DTA Purge and Archive** des travaux de l’Agent SQL Server sont en cours d’exécution. avec succès.  
  
-   En règle générale, les journaux de transactions plus petites provoquent des meilleures performances. Pour conserver les journaux des transactions plus petites, configurer le **sauvegarde de BizTalk Server** travail SQL Server Agent pour s’exécuter plus fréquemment. Pour plus d’informations, consultez la [livre blanc de l’optimisation de base de données BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=153594) (http://go.microsoft.com/fwlink/?LinkId=153594).  
  
-   Utilisez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Best Practices Analyzer (BPA) pour évaluer une existante [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déploiement. L’outil BPA effectue de nombreuses vérifications relatives à la base de données. Vous pouvez télécharger l’outil de BizTalk Server Best Practices Analyzer à partir de [outil BizTalk Server Best Practices Analyzer](http://go.microsoft.com/fwlink/?LinkId=83317) (http://go.microsoft.com/fwlink/?LinkId=83317).  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Gestion et résolution des problèmes de bases de données BizTalk Server](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)   
 [Grand croissance des Tables de base de données BizTalk Server](../technical-guides/large-growing-biztalk-server-database-tables.md)
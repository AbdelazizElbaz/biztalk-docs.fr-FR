---
title: "Recevoir des notifications de requête à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b2ed0f0-d005-4eec-b1a6-97a0c94678dc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37d333a2248c943d1d404aa086565ae4b1662226
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-query-notifications-using-the-sql-adapter"></a>Recevoir des notifications de requête à l’aide de l’adaptateur SQL
Les clients de l’adaptateur peuvent s’abonner pour recevoir des notifications de requêtes sur les modifications de données dans la base de données SQL Server. Une instruction SQL SELECT ou une procédure stockée spécifie les critères de modification de données dans une table pour déclencher des notifications de requête et le serveur SQL Server envoie des notifications de requête en tant qu’et lorsque le jeu de résultats pour l’instruction SELECT ou la procédure stockée est modifiée.  
  
> [!IMPORTANT]
>  Pour prendre en charge les notifications de requête, les clients de l’adaptateur et la base de données SQL Server doivent répondre à certaines exigences. Pour plus d’informations sur la configuration requise, consultez « Activation des Notifications de requête » à [http://go.microsoft.com/fwlink/?LinkID=122323](http://go.microsoft.com/fwlink/?LinkID=122323).  
  
 Une notification de requête classique implique les étapes suivantes :  
  
-   Les clients de l’adaptateur doivent spécifier `Notification` en tant que l’opération entrante dans le **InboundOperationType** propriété de liaison. La valeur par défaut pour cette propriété de liaison est `Polling`.  
  
-   Les clients de l’adaptateur doivent spécifier une instruction SQL à s’inscrire aux notifications de requête dans le **NotificationStatement** propriété de liaison. Le client de l’adaptateur obtient une notification à partir de SQL Server dès que le jeu de résultats pour que les modifications d’instruction SQL spécifiées.  
  
    > [!IMPORTANT]
    >  Pour recevoir des notifications, l’instruction SQL pour l’abonnement aux notifications *doit* répondent à certains critères. Pour plus d’informations sur les instructions SQL qui peut être utilisé pour les notifications de requête, consultez [http://go.microsoft.com/fwlink/?LinkId=122160](http://go.microsoft.com/fwlink/?LinkId=122160).  
  
-   Les clients de l’adaptateur doivent spécifier si l’adaptateur envoie une notification pour les clients de l’adaptateur dès que l’écouteur est démarré dans le **NotifyOnListenerStart** propriété de liaison.  
  
-   La notification est envoyée aux clients en tant que carte et lorsque le jeu de résultats de l’instruction SQL spécifiée dans le **NotificationStatement** liaison de la propriété est modifiée.  
  
 Pour plus d’informations sur ces propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
> [!NOTE]
>  L’abonnement aux notifications est toujours validé, que si la transaction dans laquelle l’exécution de l’instruction a été validée ou restaurée. Par conséquent, l’opération de notification ne peut pas garantir que le résultat de la requête d’abonnement de notification a changé. Par exemple, supposons que les données sont insérées dans une ligne de table (abonnée pour la notification) dans une transaction, et immédiatement une notification est envoyée à l’adaptateur informer de la modification (insertion). En raison d’une raison quelconque, la transaction est restaurée et efficacement aucune donnée n’est insérée dans la ligne de table. Toutefois, le serveur SQL Server n’envoie pas d’une notification à l’adaptateur sur la restauration de transaction. Pour plus d’informations sur les notifications de requête dans SQL Server, consultez [http://go.microsoft.com/fwlink/?LinkId=145367](http://go.microsoft.com/fwlink/?LinkId=145367).  
  
## <a name="differences-between-query-notification-and-polling"></a>Différences entre la Notification de requête et d’interrogation  
 Bien que l’interrogation et la notification de requête sont deux opérations entrantes et informent les clients de l’adaptateur sur les modifications de données dans la base de données SQL Server, le tableau suivant répertorie quelques différences entre les deux. Les différences suivantes vous aideront à choisir une opération selon vos besoins :  
  
|Notification de requête|Interrogation|  
|------------------------|-------------|  
|Notification de requête est lancée par SQL Server. L’instruction de notification émise par l’adaptateur simplement fait en sorte que la base de données pour lancer la notification au cas où une modification du jeu de résultats de l’instruction.|L’interrogation est lancée par l’adaptateur. L’adaptateur exécute une instruction pour vérifier si les données sont disponibles pour l’interrogation et initialise l’interrogation par l’exécution de l’instruction d’interrogation des données seront disponibles pour l’interrogation.|  
|Vous pouvez utiliser l’instruction de notification de requête à lire uniquement les données dans une table de base de données SQL Server.|Vous pouvez utiliser l’instruction d’interrogation pour lire ou mettre à jour des données dans une table de base de données SQL Server.|  
|Notification de requête informe uniquement sur le type de données, telles que Insert, Update et Delete.|L’interrogation vous informe sur les données réelles qui ont été modifiées.|  
|La notification de modification de données est instantanée.|La notification de modification de données dépend de l’intervalle d’interrogation, et les clients de la carte sont informés des changements de données à la fin de chaque intervalle d’interrogation. **Conseil :** interrogation peut vous fournir un meilleur débit dans les scénarios où les modifications de données sont produisent en permanence, et vous ne souhaitez pas être averti de chaque modification en tant qu’et lorsque cela se produit. Au lieu de cela, vous spécifiez un intervalle d’interrogation après laquelle vous souhaitez être averti de toutes les modifications qui se sont produites depuis la dernière notification de modification.|  
  
 Pour plus d’informations sur la notification de requête dans [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)], consultez [recevoir des Notifications de requête SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)
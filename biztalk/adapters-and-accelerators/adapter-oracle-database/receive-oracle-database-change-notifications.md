---
title: "Recevoir des Notifications de modification de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ffabf27-7223-4473-b33e-af6f2990cb96
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d1c33ef7bacf96a152d4b02d0c8c08991f96d64
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-oracle-database-change-notifications"></a>Recevoir des Notifications de modification de base de données Oracle
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] prend en charge la fonctionnalité de Notification de modification de base de données ODP.NET. À l’aide de cette fonctionnalité, les clients de l’adaptateur peuvent inscrire une instruction SELECT en tant que la notification de requête sur la base de données et la base de données envoie une notification au client en tant que carte et lorsque le jeu de résultats de l’instruction SELECT est modifiée. La notification de modification de base de données est implémentée dans l’adaptateur à l’aide de la classe OracleDependency. Pour plus d’informations sur la fonctionnalité de prise en charge des modifications de base de données dans ODP.NET et de la classe OracleDependency, consultez [http://go.microsoft.com/fwlink/?LinkId=124801](http://go.microsoft.com/fwlink/?LinkId=124801).  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose une opération entrante, Notification, pour prendre en charge la notification de modification de base de données. Toutefois, pour la base de données de notification de changement de travailler avec [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], vous devez vérifier les éléments suivants :  
  
-   Se connecter à la base de données Oracle avec la version de base de données Oracle sous-jacente 10.2 ou version ultérieure. Versions de base de données Oracle avant 10.2 ne gèrent pas les notifications.  
  
-   Se connecter à la base de données Oracle en tant qu’utilisateur qui détient le privilège de la NOTIFICATION de modification pour créer un enregistrement de notifications. Pour accorder le privilège de la NOTIFICATION de modification à un utilisateur, connectez-vous à la base de données Oracle en tant qu’utilisateur avec des privilèges d’administrateur et exécutez la commande suivante à l’invite de commandes SQL :  
  
    ```  
    grant change notification to <user name>  
    ```  
  
-   Choisissez un port TCP qui peut être utilisé par ODP.NET pour recevoir des notifications de modification de base de données à partir de la base de données Oracle. Ajoutez le port TCP à la liste des exceptions du pare-feu Windows. Pour obtenir des instructions sur la façon d’ajouter des ports à la liste des exceptions du pare-feu Windows, consultez [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959). Vous devez fournir le numéro de port TCP pour le **NotificationPort** propriété de liaison. Pour plus d’informations sur la propriété de liaison, consultez [fonctionne avec les propriétés de liaison](https://msdn.microsoft.com/library/dd788467.aspx).  
  
 Une base de données de type modifier à l’aide de la notification du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] implique les opérations suivantes :  
  
1.  Les clients de l’adaptateur doivent spécifier `Notification` en tant que l’opération entrante dans le **InboundOperationType** propriété de liaison. L’interrogation de la valeur par défaut pour cette propriété de liaison.  
  
2.  Les clients de l’adaptateur doivent spécifier une instruction SQL SELECT pour s’inscrire aux notifications de modification de base de données dans le **NotificationStatement** propriété de liaison. Le client de l’adaptateur obtient une notification à partir de la base de données Oracle en tant qu’et lorsque le jeu de résultats pour que les modifications d’instruction SQL spécifiées.  
  
3.  Les clients de l’adaptateur doivent spécifier si l’adaptateur envoie une notification pour les clients de l’adaptateur dès que l’écouteur est démarré dans le **NotifyOnListenerStart** propriété de liaison.  
  
4.  La notification est envoyée aux clients en tant que carte et lorsque le jeu de résultats de l’instruction SELECT spécifiée dans le **NotificationStatement** liaison de la propriété est modifiée.  
  
> [!CAUTION]
>  S’il existe une panne réseau entre la base de données Oracle et le client de carte, les notifications de n’être envoyées aux clients de la carte pour que les modifications effectuées sur la base de données Oracle pendant la période d’indisponibilité du réseau et par la suite. Par conséquent, vous devez utiliser l’opération d’interrogation au lieu de l’opération de Notification pour des scénarios critiques.  
  
## <a name="differences-between-notification-and-polling"></a>Différences entre la Notification et d’interrogation  
 Bien que l’interrogation et la notification sont les deux opérations entrantes et informent les clients de l’adaptateur sur les modifications de données dans la base de données Oracle, le tableau suivant illustre certaines différences entre les deux. Les différences suivantes vous aideront à choisir une opération selon vos besoins :  
  
|Notification|Interrogation|  
|------------------|-------------|  
|La notification est pris en charge uniquement pour les versions de base de données Oracle 10.2 et versions ultérieures.|L’interrogation est prise en charge pour toutes les versions de base de données Oracle sont pris en charge par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|La notification de modification de données est toujours instantanée.|Vous pouvez configurer l’intervalle d’interrogation pour vérifier les données disponibles pour l’interrogation à intervalles réguliers ou instantanément comme et lorsque les données sont disponibles. **Conseil :** interrogation peut vous fournir un meilleur débit dans les scénarios où les modifications de données sont produisent en permanence, et vous ne souhaitez pas être averti de chaque modification en tant qu’et lorsque cela se produit. Au lieu de cela, vous spécifiez un intervalle d’interrogation après laquelle vous souhaitez être averti de toutes les modifications qui se sont produites depuis la dernière notification de modification.|  
|Notification est initiée par la base de données Oracle. L’instruction de notification émise par l’adaptateur simplement fait en sorte que la base de données pour lancer la notification au cas où une modification du jeu de résultats de l’instruction. La notification est une fonctionnalité de la base de données Oracle.|L’interrogation est lancée par l’adaptateur. L’adaptateur exécute une instruction SQL pour confirmer que les données sont disponibles pour l’interrogation et initialise l’interrogation par l’exécution de l’instruction d’interrogation des données seront disponibles pour l’interrogation.|  
|Vous pouvez utiliser l’instruction de notification à lire uniquement les données dans une base de données Oracle.|Vous pouvez utiliser l’instruction d’interrogation pour lire ou mettre à jour des données dans la base de données Oracle.|  
|Notification informe uniquement sur le type de données, telles que Insert, Update et Delete.|L’interrogation vous informe sur les données réelles qui ont été modifiées.|  
  
 Pour plus d’informations sur :  
  
-   Les propriétés de liaison associées à l’opération de Notification, consultez [fonctionne avec les propriétés de liaison](https://msdn.microsoft.com/library/dd788467.aspx).  
  
-   L’utilisation de l’opération de Notification dans [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [réception Oracle de base de données modifiées des Notifications à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)
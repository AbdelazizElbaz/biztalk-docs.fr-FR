---
title: "Recevoir des notifications sur plusieurs emplacements de réception de la requête SQL à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9afbe98e-8901-417c-a807-8db97fd7a24b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa858483914b8325e9250e1e41f99ae03226f3ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-query-notifications-on-multiple-receive-locations-from-sql-using-biztalk-server"></a>Recevoir des notifications sur plusieurs emplacements de réception de la requête SQL à l’aide de BizTalk Server
Considérez un scénario où vous disposez de plusieurs emplacements créés dans le cadre d’applications BizTalk différentes configuré pour recevoir des notifications de requête pour la même table (par exemple, employé) de réception dans la même base de données. Si une centaine enregistrements sont insérés dans la même table, tous les emplacements de réception obtenez le message de notification. Pour recevoir des notifications à travers efficacement plusieurs emplacements de réception, vous pouvez appeler des opérations à partir de votre application BizTalk de sorte que si une notification est reçue par un emplacement de réception, l’autre emplacement de réception n’obtient pas la même notification. Par conséquent, vous pouvez efficacement les notifications d’équilibrer la charge reçues sur plusieurs emplacements.  
  
 Les tâches requises pour configurer une orchestration à recevoir des notifications d’équilibrer la charge sont les mêmes que pour [de réception requête Notifications de façon incrémentielle à partir de SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-incrementally-from-sql-using-biztalk-server.md). Cette rubrique répertorie les seules la différence entre les deux approches.  
  
## <a name="load-balancing-query-notifications-across-multiple-receive-locations"></a>Notifications de requête de l’équilibrage de charge entre plusieurs emplacements de réception  
 Comme dans la rubrique [de réception requête Notifications de façon incrémentielle à partir de SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-incrementally-from-sql-using-biztalk-server.md), vous avez configuré des notifications incrémentielles en exécutant une instruction de mise à jour sur les enregistrements qui sont déjà notifiées pour. Pour configurer l’équilibrage de charge, vous pouvez exécuter une procédure stockée qui supprime les enregistrements qui ont été notifiés pour. Par exemple, considérez une procédure stockée PROCESS_EMPLOYEE avec la définition suivante :  
  
```  
DECLARE @var int  
SELECT TOP 1 @var = Employee_ID FROM Employee  
SELECT * FROM Employee WHERE Employee_ID=@var  
DELETE FROM Employee WHERE Employee_ID=@var  
```  
  
 Lorsque vous exécutez cette procédure stockée dans le cadre de l’application BizTalk, l’enregistrement pour laquelle la notification est déjà reçue est supprimé. Par conséquent, l’autre recevoir une notification d’obtient d’emplacement pour l’enregistrement suivant.  
  
 Voici les étapes principales à effectuer pour configurer l’équilibrage de charge pour recevoir des notifications.  
  
1.  Créer le schéma pour **Notification** (opération entrante) et **PROCESS_EMPLOYEE** (opération sortante) de procédure stockée.  
  
2.  Ajouter une orchestration et ajoutez les trois messages pour la réception des notifications, l’exécution d’une procédure stockée et l’obtention de réponse pour la procédure stockée.  
  
3.  Créer une orchestration en ajoutant des formes envoi et réception, forme construire un Message et les ports. Vous pouvez utiliser le même exemple de code pour construire un message pour appeler la procédure stockée de PROCESS_EMPLOYEE. Notez que lors de l’exécution de l’opération dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous devez disposer du message de demande pour le PROCESS_EMPLOYEE de procédure stockée à l’emplacement C:\TestLocation\MessageIn. Le fait que l’extrait de code que vous appelez dans le cadre de l’orchestration créée dans [de réception requête Notifications de façon incrémentielle à partir de SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-incrementally-from-sql-using-biztalk-server.md) crée un message de demande en fonction de la demande XML présente dans C:\ TestLocation\MessageIn.  
  
4.  Générez et déployez l’application. Pour démontrer l’équilibrage de charge, vous devez déployer cette orchestration au moins sur deux ordinateurs différents qui ont [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installé.  
  
5.  Dans la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration sur les ordinateurs, spécifiez l’emplacement de réception les propriétés de liaison suivantes pour le WCF-Custom ou WCF-SQL :  
  
    |Propriété de liaison|Valeur|  
    |----------------------|-----------|  
    |**InboundOperationType**|Affectez la valeur **Notification**.|  
    |**NotificationStatement**|Affectez la valeur :<br /><br /> `SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0`<br /><br /> **Remarque :** pour les instructions de la notification, vous devez toujours spécifier le nom de table, ainsi que le nom du schéma. Par exemple, `dbo.Employee`.|  
    |**NotifyOnListenerStart**|Affectez la valeur **True**.|  
  
6.  Démarrez l’application BizTalk.  
  
7.  Pour commencer à recevoir des notifications, insérez une centaine enregistrements dans la table EMPLOYEE. Pendant cette opération, assurez-vous que la demande XML pour appeler le PROCESS_EMPLOYEE de procédure stockée est disponible dans C:\TestLocation\MessageIn.  
  
8.  Surveiller l’emplacement (sur les deux ordinateurs) où l’application BizTalk déplacer les messages de notification. Vous remarquerez que des enregistrements de centaines insérées, un seul emplacement reçoit les notifications pour certains enregistrements pendant que l’autre emplacement reçoit une notification pour les enregistrements restants. Ensemble, les emplacements recevez notification pour tous les enregistrements de centaines.  
  
## <a name="see-also"></a>Voir aussi  
 [Recevoir des Notifications de requête SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)
---
title: "Modification de la base de données Oracle de recevoir des notifications sur plusieurs emplacements de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d273517-9527-4208-99be-97c8a92f176d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9eec853c133f57320b2ecca106cc497205eda28
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-oracle-database-change-notifications-on-multiple-receive-locations"></a>Modification de la base de données Oracle de recevoir des notifications sur plusieurs emplacements de réception
Considérez un scénario où vous disposez de plusieurs emplacements créés dans le cadre d’applications BizTalk différentes configuré pour recevoir des notifications de requête pour la même table (par exemple, ACCOUNTACTIVITY) de réception dans la même base de données. Si une centaine enregistrements sont insérés dans la même table, tous les emplacements de réception obtenez le message de notification. Pour recevoir des notifications à travers efficacement plusieurs emplacements de réception, vous pouvez appeler des opérations à partir de votre application BizTalk de sorte que si une notification est reçue par un emplacement de réception, l’autre emplacement de réception n’obtient pas la même notification. Par conséquent, vous pouvez efficacement les notifications d’équilibrer la charge reçues sur plusieurs emplacements.  
  
 Les tâches requises pour configurer une orchestration à recevoir des notifications d’équilibrer la charge sont les mêmes que pour [réception Oracle de base de données modifiées Notifications incrémentielle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md). Cette rubrique répertorie les seules la différence entre les deux approches.  
  
## <a name="load-balancing-query-notifications-across-multiple-receive-locations"></a>Notifications de requête de l’équilibrage de charge entre plusieurs emplacements de réception  
 Comme dans la rubrique [réception Oracle de base de données modifiées Notifications incrémentielle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md), vous avez configuré des notifications incrémentielles en exécutant une procédure PROCESS_RECORDS. Pour configurer l’équilibrage de charge, vous pouvez exécuter une procédure stockée qui supprime les enregistrements qui ont été notifiés pour. Par exemple, considérez une procédure stockée NOTIFY_LOAD_BALANCE avec la définition suivante :  
  
```  
PROCEDURE NOTIFY_LOAD_BALANCE (TABLE_DATA OUT SYS_REFCURSOR) IS  
  var int;  
BEGIN  
  SELECT TID INTO var FROM ACCOUNTACTIVITY WHERE ROWNUM = 1 FOR UPDATE;  
  OPEN TABLE_DATA FOR SELECT * FROM ACCOUNTACTIVITY WHERE TID = var;  
  DELETE FROM ACCOUNTACTIVITY WHERE TID = var;  
END NOTIFY_LOAD_BALANCE;  
```  
  
 Lorsque vous exécutez cette procédure stockée dans le cadre de l’application BizTalk, l’enregistrement pour laquelle la notification est déjà reçue est supprimé. Par conséquent, l’autre recevoir une notification d’obtient d’emplacement pour l’enregistrement suivant.  
  
 Voici les étapes principales à effectuer pour configurer l’équilibrage de charge pour recevoir des notifications.  
  
1.  Créer le schéma pour **Notification** (opération entrante) et **NOTIFY_LOAD_BALANCE** procédure (opération sortante).  
  
2.  Ajouter une orchestration et ajoutez les trois messages pour la réception des notifications, l’exécution de la procédure et l’obtention de la réponse pour la procédure.  
  
3.  Créer une orchestration en ajoutant des formes envoi et réception, forme construire un Message et les ports. Vous pouvez utiliser le même exemple de code pour construire un message pour appeler la procédure stockée de NOTIFY_LOAD_BALANCE. Notez que lors de l’exécution de l’opération dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous devez avoir le message de demande pour la procédure NOTIFY_LOAD_BALANCE dans l’emplacement C:\TestLocation\MessageIn. Le fait que l’extrait de code que vous appelez dans le cadre de l’orchestration créée dans [réception Oracle de base de données modifiées Notifications incrémentielle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md) crée un message de demande en fonction de la demande XML présente dans C:\ TestLocation\MessageIn.  
  
4.  Générez et déployez l’application. Pour démontrer l’équilibrage de charge, vous devez déployer cette orchestration au moins sur deux ordinateurs différents qui ont [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] installé.  
  
5.  Dans la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration sur les ordinateurs, spécifiez les propriétés de liaison suivantes pour le WCF-Custom ou WCF-OracleDB emplacement de réception :  
  
    |Propriété de liaison|Valeur|  
    |----------------------|-----------|  
    |**InboundOperationType**|Affectez la valeur **Notification**.|  
    |**NotificationPort**|Spécifie le numéro de port ODP.NET doit ouvrir pour l’écoute de notification de modification de base de données à partir de la base de données Oracle. Définissez cette propriété sur le même numéro de port que vous devez avoir ajouté à la liste d’exceptions de pare-feu Windows. Pour obtenir des instructions sur la façon d’ajouter des ports à la liste des exceptions du pare-feu Windows, consultez [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959). **Important :** si vous affectez la valeur par défaut -1, vous devez désactiver le pare-feu Windows pour recevoir des messages de notification.|  
    |**NotificationStatement**|Affectez la valeur :<br /><br /> `SELECT TID,ACCOUNT,PROCESSED FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’`**Remarque :** vous devez spécifier le nom de table, ainsi que le nom du schéma. Par exemple, `SCOTT.ACCOUNTACTIVITY`.|  
    |**NotifyOnListenerStart**|Affectez la valeur **True**.|  
  
6.  Démarrez l’application BizTalk.  
  
7.  Pour commencer à recevoir des notifications, insérez une centaine enregistrements dans la table ACCOUNTACTIVITY. Pendant cette opération, assurez-vous que la demande XML pour l’appel de la procédure NOTIFY_LOAD_BALANCE est disponible dans C:\TestLocation\MessageIn.  
  
8.  Surveiller l’emplacement (sur les deux ordinateurs) où l’application BizTalk déplacer les messages de notification. Vous remarquerez que des enregistrements de centaines insérées, un seul emplacement reçoit les notifications pour certains enregistrements pendant que l’autre emplacement reçoit une notification pour les enregistrements restants. Ensemble, les emplacements recevez notification pour tous les enregistrements de centaines.  
  
## <a name="see-also"></a>Voir aussi  
 [Recevoir des Notifications de modification de base de données Oracle incrémentielle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md)
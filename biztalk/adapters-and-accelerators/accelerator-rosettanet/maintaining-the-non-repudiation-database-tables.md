---
title: "Gestion des Tables de base de données de non-répudiation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases, purging
- databases, non-repudiation database
- maintaining databases, purging
- purging databases
- databases, maintaining
- non-repudiation, database
ms.assetid: 29222510-325b-4cd7-854b-6f548a63fd08
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 182172eccddcaad684f35335708dce6027fb111f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="maintaining-the-non-repudiation-database-tables"></a>Gestion des Tables de base de données de non-répudiation
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stocke les messages à des fins de non-répudiation dans les tables MessageStorageIn et MessageStorageOut de la base de données BTARNArchive. Nombre de messages dans ces tables peut affecter les performances du système. Vous pouvez utiliser ces tables de base de données de non-répudiation par régulièrement purge et archivage des messages à partir de ces tables, comme il convient.  
  
## <a name="routine-database-maintenance"></a>Maintenance de routine de la base de données  
 Lorsque [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] reçoit un message, il enregistre toujours le message dans la table MessageStorageIn et définit d’abord le **ToBePurged** au champ « 1 », ce qui indique que le message ne requiert pas de non répudiation. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]puis déchiffre et décode le message pour déterminer l’accord. Une fois le déchiffrement et de décodage, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] examine l’accord pour voir si elle doit enregistrer le message à des fins de non-répudiation. Si, par conséquent, il définit le **ToBePurged** au champ « 0 » et renseigne les autres champs du message. Si non, il quitte la **ToBePurged** champ « 1 » et ne remplit pas les autres champs du message.  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]ne supprime pas automatiquement les messages avec la **ToBePurged** champ définie sur « 1 ». En outre, il n’archive pas les messages enregistrés pour la non répudiation à d’autres tables. Ces deux ensembles de messages peuvent s’accumuler dans la table MessageStorageIn et affecter les performances. Dans le cadre d’une maintenance de routine sur la base de données, il pouvez que vous souhaitez effectuer les opérations suivantes :  
  
-   Exécuter une procédure stockée qui contient le code SQL suivant l’instruction pour supprimer tous les messages dans la table MessageStorageIn dont **ToBePurged** champ n’est pas égal à « 0 » :  
  
    ```  
    delete MessageStorageIn where ToBePurged <> 0  
    ```  
  
-   Après une période appropriée (la stratégie d’entreprise peut nécessiter), exécuter une procédure stockée pour archiver les messages de non répudiation à une base de données hors connexion qui n’affecte pas les performances. Vous pouvez déterminer ce laps de temps à l’aide de la **TimeCreated** de la table MessageStorageIn. Une fois la période de non répudiation d’un message a expiré, vous pouvez supprimer le message à partir de la base de données d’archive à l’aide de l’instruction SQL suivante (qui supprime les messages qui datent de plus de sept jours) :  
  
    ```  
    delete <archive table name> where datediff(d, TimeCreated, GetUTCDATA())>7  
    ```  
  
> [!NOTE]
>  Le **TimeCreated** champ dans la table MessageStorageIn est au format UTC.  
  
> [!NOTE]
>  Vous ne devez pas supprimer un message entrant datant de moins d’une heure.  
  
 Lorsque [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] envoie un message sortant, il a accès à l’accord de non répudiation. Si le contrat requiert la non répudiation, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] enregistre le message dans la table MessageStorageOut. Si ce n’est pas le cas, il n’enregistre pas le message dans la table. Cela signifie qu’il n’est pas nécessaire pour un **ToBePurged** de cette table. La maintenance uniquement requise pour la table MessageStorageOut consiste à archiver les messages de non répudiation à une base de données hors connexion après un délai approprié et pour supprimer chaque message après sa période de non répudiation a expiré. Vous pouvez le faire avec l’instruction SQL suivante (qui supprime les messages qui datent de plus de sept jours) :  
  
```  
delete MessageStorageOut where datediff(d, TimeCreated, GetUTCDATA())>7  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des messages RNIF](../../adapters-and-accelerators/accelerator-rosettanet/rnif-message-processing.md)   
 [Gérer la configuration, les certificats, les bases de données et la sécurité](manage-configuration-certificates-databases-security.md)
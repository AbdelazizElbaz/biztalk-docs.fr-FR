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
# <a name="maintaining-the-non-repudiation-database-tables"></a><span data-ttu-id="e4f48-102">Gestion des Tables de base de données de non-répudiation</span><span class="sxs-lookup"><span data-stu-id="e4f48-102">Maintaining the Non-Repudiation Database Tables</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="e4f48-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stocke les messages à des fins de non-répudiation dans les tables MessageStorageIn et MessageStorageOut de la base de données BTARNArchive.</span><span class="sxs-lookup"><span data-stu-id="e4f48-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stores messages for non-repudiation purposes in the MessageStorageIn and MessageStorageOut tables of the BTARNArchive database.</span></span> <span data-ttu-id="e4f48-104">Nombre de messages dans ces tables peut affecter les performances du système.</span><span class="sxs-lookup"><span data-stu-id="e4f48-104">Many messages in these tables can affect system performance.</span></span> <span data-ttu-id="e4f48-105">Vous pouvez utiliser ces tables de base de données de non-répudiation par régulièrement purge et archivage des messages à partir de ces tables, comme il convient.</span><span class="sxs-lookup"><span data-stu-id="e4f48-105">You may want to maintain these non-repudiation database tables by periodically purging and archiving messages from these tables, as appropriate.</span></span>  
  
## <a name="routine-database-maintenance"></a><span data-ttu-id="e4f48-106">Maintenance de routine de la base de données</span><span class="sxs-lookup"><span data-stu-id="e4f48-106">Routine Database Maintenance</span></span>  
 <span data-ttu-id="e4f48-107">Lorsque [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] reçoit un message, il enregistre toujours le message dans la table MessageStorageIn et définit d’abord le **ToBePurged** au champ « 1 », ce qui indique que le message ne requiert pas de non répudiation.</span><span class="sxs-lookup"><span data-stu-id="e4f48-107">When [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receives a message, it always saves the message in the MessageStorageIn table and initially sets the **ToBePurged** field to "1", which indicates that the message does not require non-repudiation.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="e4f48-108">puis déchiffre et décode le message pour déterminer l’accord.</span><span class="sxs-lookup"><span data-stu-id="e4f48-108"> then decrypts and decodes the message to determine what the agreement is.</span></span> <span data-ttu-id="e4f48-109">Une fois le déchiffrement et de décodage, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] examine l’accord pour voir si elle doit enregistrer le message à des fins de non-répudiation.</span><span class="sxs-lookup"><span data-stu-id="e4f48-109">After decrypting and decoding, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] examines the agreement to see whether it must save the message for non-repudiation purposes.</span></span> <span data-ttu-id="e4f48-110">Si, par conséquent, il définit le **ToBePurged** au champ « 0 » et renseigne les autres champs du message.</span><span class="sxs-lookup"><span data-stu-id="e4f48-110">If so, it sets the **ToBePurged** field to "0" and fills in the other fields of the message.</span></span> <span data-ttu-id="e4f48-111">Si non, il quitte la **ToBePurged** champ « 1 » et ne remplit pas les autres champs du message.</span><span class="sxs-lookup"><span data-stu-id="e4f48-111">If not, it leaves the **ToBePurged** field as "1" and does not fill in the other fields of the message.</span></span>  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="e4f48-112">ne supprime pas automatiquement les messages avec la **ToBePurged** champ définie sur « 1 ».</span><span class="sxs-lookup"><span data-stu-id="e4f48-112"> does not automatically delete messages with the **ToBePurged** field set to "1".</span></span> <span data-ttu-id="e4f48-113">En outre, il n’archive pas les messages enregistrés pour la non répudiation à d’autres tables.</span><span class="sxs-lookup"><span data-stu-id="e4f48-113">In addition, it does not archive messages saved for non-repudiation to other tables.</span></span> <span data-ttu-id="e4f48-114">Ces deux ensembles de messages peuvent s’accumuler dans la table MessageStorageIn et affecter les performances.</span><span class="sxs-lookup"><span data-stu-id="e4f48-114">These two sets of messages can build up in the MessageStorageIn table and affect performance.</span></span> <span data-ttu-id="e4f48-115">Dans le cadre d’une maintenance de routine sur la base de données, il pouvez que vous souhaitez effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e4f48-115">As part of routine maintenance on the database, you may want to do the following:</span></span>  
  
-   <span data-ttu-id="e4f48-116">Exécuter une procédure stockée qui contient le code SQL suivant l’instruction pour supprimer tous les messages dans la table MessageStorageIn dont **ToBePurged** champ n’est pas égal à « 0 » :</span><span class="sxs-lookup"><span data-stu-id="e4f48-116">Run a stored procedure containing the following SQL statement to delete all messages in the MessageStorageIn table whose **ToBePurged** field is not equal to "0":</span></span>  
  
    ```  
    delete MessageStorageIn where ToBePurged <> 0  
    ```  
  
-   <span data-ttu-id="e4f48-117">Après une période appropriée (la stratégie d’entreprise peut nécessiter), exécuter une procédure stockée pour archiver les messages de non répudiation à une base de données hors connexion qui n’affecte pas les performances.</span><span class="sxs-lookup"><span data-stu-id="e4f48-117">After an appropriate period (which company policy may dictate), run a stored procedure to archive non-repudiation messages to an offline database that will not affect performance.</span></span> <span data-ttu-id="e4f48-118">Vous pouvez déterminer ce laps de temps à l’aide de la **TimeCreated** de la table MessageStorageIn.</span><span class="sxs-lookup"><span data-stu-id="e4f48-118">You can determine this period by using the **TimeCreated** field in the MessageStorageIn table.</span></span> <span data-ttu-id="e4f48-119">Une fois la période de non répudiation d’un message a expiré, vous pouvez supprimer le message à partir de la base de données d’archive à l’aide de l’instruction SQL suivante (qui supprime les messages qui datent de plus de sept jours) :</span><span class="sxs-lookup"><span data-stu-id="e4f48-119">After the non-repudiation period for a message has expired, you can delete the message from the archive database by using the following SQL statement (which deletes messages that are older than seven days):</span></span>  
  
    ```  
    delete <archive table name> where datediff(d, TimeCreated, GetUTCDATA())>7  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="e4f48-120">Le **TimeCreated** champ dans la table MessageStorageIn est au format UTC.</span><span class="sxs-lookup"><span data-stu-id="e4f48-120">The **TimeCreated** field in the MessageStorageIn table is in UTC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4f48-121">Vous ne devez pas supprimer un message entrant datant de moins d’une heure.</span><span class="sxs-lookup"><span data-stu-id="e4f48-121">You should not delete an incoming message that is less than one hour old.</span></span>  
  
 <span data-ttu-id="e4f48-122">Lorsque [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] envoie un message sortant, il a accès à l’accord de non répudiation.</span><span class="sxs-lookup"><span data-stu-id="e4f48-122">When [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] sends an outgoing message, it has access to the non-repudiation agreement.</span></span> <span data-ttu-id="e4f48-123">Si le contrat requiert la non répudiation, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] enregistre le message dans la table MessageStorageOut.</span><span class="sxs-lookup"><span data-stu-id="e4f48-123">If the agreement requires non-repudiation, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] saves the message in the MessageStorageOut table.</span></span> <span data-ttu-id="e4f48-124">Si ce n’est pas le cas, il n’enregistre pas le message dans la table.</span><span class="sxs-lookup"><span data-stu-id="e4f48-124">If not, it does not save the message in the table.</span></span> <span data-ttu-id="e4f48-125">Cela signifie qu’il n’est pas nécessaire pour un **ToBePurged** de cette table.</span><span class="sxs-lookup"><span data-stu-id="e4f48-125">This means that there is no need for a **ToBePurged** field in this table.</span></span> <span data-ttu-id="e4f48-126">La maintenance uniquement requise pour la table MessageStorageOut consiste à archiver les messages de non répudiation à une base de données hors connexion après un délai approprié et pour supprimer chaque message après sa période de non répudiation a expiré.</span><span class="sxs-lookup"><span data-stu-id="e4f48-126">The only maintenance required for the MessageStorageOut table is to archive non-repudiation messages to an offline database after an appropriate period, and to delete each message after its non-repudiation period has expired.</span></span> <span data-ttu-id="e4f48-127">Vous pouvez le faire avec l’instruction SQL suivante (qui supprime les messages qui datent de plus de sept jours) :</span><span class="sxs-lookup"><span data-stu-id="e4f48-127">You can do so with the following SQL statement (which deletes messages that are older than seven days):</span></span>  
  
```  
delete MessageStorageOut where datediff(d, TimeCreated, GetUTCDATA())>7  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4f48-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4f48-128">See Also</span></span>  
 <span data-ttu-id="e4f48-129">[Traitement des messages RNIF](../../adapters-and-accelerators/accelerator-rosettanet/rnif-message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="e4f48-129">[RNIF Message Processing](../../adapters-and-accelerators/accelerator-rosettanet/rnif-message-processing.md) </span></span>  
 [<span data-ttu-id="e4f48-130">Gérer la configuration, les certificats, les bases de données et la sécurité</span><span class="sxs-lookup"><span data-stu-id="e4f48-130">Manage configuration, certificates, databases, and security</span></span>](manage-configuration-certificates-databases-security.md)
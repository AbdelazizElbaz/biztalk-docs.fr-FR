---
title: "Résoudre les problèmes opérationnels avec l’adaptateur SQL dans BizTalk | Documents Microsoft"
description: "Problèmes courants et des résolutions de l’adaptateur SQL dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c75f85f4-cd03-4c6a-aac9-a6d02d3c3449
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b6850a1b8c3b0cb5d1356078fce8dc8f50c6963
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="troubleshoot-operational-issues-with-the-sql-adapter"></a><span data-ttu-id="54efa-103">Résoudre les problèmes opérationnels avec l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="54efa-103">Troubleshoot Operational Issues with the SQL adapter</span></span>
<span data-ttu-id="54efa-104">Cette section présente l’utilisation de techniques de dépannage pour résoudre les erreurs de fonctionnement que vous pouvez rencontrer lorsque vous utilisez [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54efa-104">This section discusses using troubleshooting techniques to resolve operational errors that you might encounter when using [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="54efa-105">L’activation du traçage</span><span class="sxs-lookup"><span data-stu-id="54efa-105">Enabling Tracing</span></span>  
 <span data-ttu-id="54efa-106">Vous devez activer le traçage entre l’adaptateur, [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], et SQL Server pour collecter plus d’informations sur les problèmes que vous rencontrez lors de l’utilisation du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54efa-106">You must enable tracing between the adapter, [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], and SQL Server to gather more information about any issues you encounter while using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="54efa-107">Pour plus d’informations sur la prise en charge dans les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [le suivi de Diagnostic et de journalisation des messages dans l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/diagnostic-tracing-and-message-logging-in-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="54efa-107">For more information about tracing support in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Diagnostic Tracing and Message Logging in the SQL adapter](../../adapters-and-accelerators/adapter-sql/diagnostic-tracing-and-message-logging-in-the-sql-adapter.md).</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="54efa-108">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="54efa-108">Known Issues</span></span>  
 <span data-ttu-id="54efa-109">Voici les erreurs les plus courantes que vous pouvez rencontrer en utilisant le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], ainsi que leur cause probable et de la résolution.</span><span class="sxs-lookup"><span data-stu-id="54efa-109">The following are the most common errors you might encounter when using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], along with their probable cause and resolution.</span></span>  
  
  
  
###  <a name="BKMK_SQLLoadBinding"></a><span data-ttu-id="54efa-110">Erreur lors du chargement des liaisons de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="54efa-110">Error in loading the adapter bindings</span></span>  
 <span data-ttu-id="54efa-111">**Problème**</span><span class="sxs-lookup"><span data-stu-id="54efa-111">**Problem**</span></span>  
  
 <span data-ttu-id="54efa-112">Lorsque vous essayez de démarrer le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], vous obtenez l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="54efa-112">When you try to start the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], you get the following error:</span></span>  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 <span data-ttu-id="54efa-113">**Cause**</span><span class="sxs-lookup"><span data-stu-id="54efa-113">**Cause**</span></span>  
  
 <span data-ttu-id="54efa-114">Lorsque vous essayez de démarrer le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF charge les liaisons de l’adaptateur pour tous les adaptateurs installés.</span><span class="sxs-lookup"><span data-stu-id="54efa-114">When you try to start the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF loads the adapter bindings for all the installed adapters.</span></span> <span data-ttu-id="54efa-115">À son tour, les liaisons de l’adaptateur sont dépendantes du logiciel client spécifique pour l’application d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="54efa-115">In turn, the adapter bindings are dependent on the specific client software for the enterprise application.</span></span> <span data-ttu-id="54efa-116">Vous risquez de rencontrer ce problème si vous avez effectué une installation standard ou complète de la carte, qui installe tous les adaptateurs contenus dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54efa-116">You might face this issue if you did a Typical or Complete installation of the adapter, which installs all the adapters contained in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="54efa-117">Toutefois, les bibliothèques clientes LOB peuvent être installés pour seulement une application d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="54efa-117">However, the LOB client libraries might be installed for only one enterprise application.</span></span> <span data-ttu-id="54efa-118">Par conséquent, l’interface graphique utilisateur ne peut pas charger les liaisons pour les autres adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="54efa-118">As a result, the GUI fails to load the bindings for the other adapters.</span></span>  
  
 <span data-ttu-id="54efa-119">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="54efa-119">**Resolution**</span></span>  
  
 <span data-ttu-id="54efa-120">Assurez-vous que vous effectuez une installation personnalisée des adaptateurs pour installer uniquement la carte que vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="54efa-120">Make sure you do a custom installation of the adapters to install only the adapter you need.</span></span>  
  
###  <a name="BKMK_SQLDisplay"></a><span data-ttu-id="54efa-121">L’adaptateur SQL ne s’affiche pas dans la liste des adaptateurs dans la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="54efa-121">The SQL adapter does not display in the list of adapters in BizTalk Server Administration console</span></span>  
 <span data-ttu-id="54efa-122">**Problème**</span><span class="sxs-lookup"><span data-stu-id="54efa-122">**Problem**</span></span>  
  
 <span data-ttu-id="54efa-123">Contrairement à la version antérieure des adaptateurs fournis avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] livré avec [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] n’apparaît pas dans la liste des cartes dans les [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="54efa-123">Unlike the earlier version of the adapters shipped with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] shipped with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] does not show up in the list of adapters in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="54efa-124">**Cause**</span><span class="sxs-lookup"><span data-stu-id="54efa-124">**Cause**</span></span>  
  
 <span data-ttu-id="54efa-125">La dernière version [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est une liaison WCF personnalisée.</span><span class="sxs-lookup"><span data-stu-id="54efa-125">The latest [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is a WCF custom binding.</span></span> <span data-ttu-id="54efa-126">Par conséquent, bien que le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration affiche le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], il n’affiche pas les liaisons personnalisées WCF et par conséquent, n’affiche pas la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54efa-126">So, although the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], it does not display the WCF custom bindings and hence, does not display the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
 <span data-ttu-id="54efa-127">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="54efa-127">**Resolution**</span></span>  
  
 <span data-ttu-id="54efa-128">Vous pouvez ajouter explicitement le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration en suivant les étapes mentionnées dans [Ajout de l’adaptateur SQL à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="54efa-128">You can explicitly add the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by following the steps mentioned in [Adding the SQL Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
###  <a name="BKMK_MissingAction"></a><span data-ttu-id="54efa-129">Erreur lors de l’exécution d’opérations sur une base de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="54efa-129">Error while performing operations on a SQL Server database</span></span>  
 <span data-ttu-id="54efa-130">**Problème**</span><span class="sxs-lookup"><span data-stu-id="54efa-130">**Problem**</span></span>  
  
 <span data-ttu-id="54efa-131">L’adaptateur renvoie l’erreur suivante lorsque vous effectuez une opération sur une base de données SQL Server à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54efa-131">The adapter gives the following error when performing any operation on a SQL Server database using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="54efa-132">**Pour BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="54efa-132">**For BizTalk Server**</span></span>  
  
    ```  
    System.ArgumentNullException: Value cannot be null.  
    ```  
  
 <span data-ttu-id="54efa-133">**Cause**</span><span class="sxs-lookup"><span data-stu-id="54efa-133">**Cause**</span></span>  
  
 <span data-ttu-id="54efa-134">L’action WCF pour le message n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="54efa-134">The WCF action for the message is not specified.</span></span> <span data-ttu-id="54efa-135">WCF nécessite une action SOAP pour chaque opération, qui informe l’adaptateur de l’opération à effectuer sur l’application métier.</span><span class="sxs-lookup"><span data-stu-id="54efa-135">WCF requires a SOAP action to be specified for every operation, which informs the adapter about the operation to be performed on the LOB application.</span></span>  
  
 <span data-ttu-id="54efa-136">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="54efa-136">**Resolution**</span></span>  
  
 <span data-ttu-id="54efa-137">Spécifier l’action SOAP dans le port d’envoi ou une propriété de contexte de message dans une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="54efa-137">Specify the SOAP action in the send port or as a message context property in a BizTalk orchestration.</span></span> <span data-ttu-id="54efa-138">Pour obtenir des instructions, consultez [configurer l’action SOAP pour l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="54efa-138">For instructions, see [Configure the SOAP action for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md).</span></span> <span data-ttu-id="54efa-139">Consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md) pour afficher la liste des actions pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="54efa-139">See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md) to see a list of actions for each operation.</span></span>  
  
###  <a name="BKMK_SQLInvalidOp"></a><span data-ttu-id="54efa-140">Exception InvalidOperationException avec le code d’erreur = 5 lors de l’exécution des opérations FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="54efa-140">InvalidOperationException with ErrorCode=5 while performing FILESTREAM operations</span></span>  
 <span data-ttu-id="54efa-141">**Problème**</span><span class="sxs-lookup"><span data-stu-id="54efa-141">**Problem**</span></span>  
  
 <span data-ttu-id="54efa-142">Vous obtenez l’erreur suivante lors de l’utilisation du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour effectuer des opérations FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="54efa-142">You get the following error while using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to perform FILESTREAM operations.</span></span>  
  
```  
System.InvalidOperationException: OpenSqlFileStream returned error.  
ErrorCode:5  
  
```  
  
 <span data-ttu-id="54efa-143">**Cause**</span><span class="sxs-lookup"><span data-stu-id="54efa-143">**Cause**</span></span>  
  
 <span data-ttu-id="54efa-144">Vous avez peut-être spécifié des informations d’identification de la base de données pour se connecter à la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="54efa-144">You might have specified database credentials to connect to the SQL Server database.</span></span> <span data-ttu-id="54efa-145">Pour effectuer des opérations FILESTREAM, vous devez toujours utiliser l’authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="54efa-145">To perform FILESTREAM operations, you must always use Windows Authentication.</span></span> <span data-ttu-id="54efa-146">Le code d’erreur « 5 » indique que l’accès est refusé en raison d’informations d’identification incorrectes.</span><span class="sxs-lookup"><span data-stu-id="54efa-146">The error code “5” denotes that access is denied because of incorrect credentials.</span></span> <span data-ttu-id="54efa-147">Pour plus d’informations sur les différents codes d’erreur, consultez [Codes d’erreurs système (0-499)](https://msdn.microsoft.com/library/ms681382(VS.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="54efa-147">For more information about the different error codes, see [System Error Codes (0-499)](https://msdn.microsoft.com/library/ms681382(VS.85).aspx).</span></span>
  
 <span data-ttu-id="54efa-148">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="54efa-148">**Resolution**</span></span>  
  
 <span data-ttu-id="54efa-149">Utiliser l’authentification Windows pour se connecter à la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="54efa-149">Use Windows Authentication to connect to the SQL Server database.</span></span> <span data-ttu-id="54efa-150">Dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous pouvez le faire en laissant l’utilisateur les champs nom et mot de passe vide dans la boîte de dialogue de configuration port WCF-Custom ou WCF-SQL.</span><span class="sxs-lookup"><span data-stu-id="54efa-150">In [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can do so by leaving the user name and password fields blank in the WCF-Custom or WCF-SQL port configuration dialog box.</span></span>  
  
###  <a name="BKMK_SQLPolling"></a><span data-ttu-id="54efa-151">Interrogation d’opération ne retourne pas les messages même si les instructions valides sont spécifiées pour PollingStatement et PolledDataAvailableStatement</span><span class="sxs-lookup"><span data-stu-id="54efa-151">Polling operation does not return any messages even if valid statements are specified for PollingStatement and PolledDataAvailableStatement</span></span>  
 <span data-ttu-id="54efa-152">**Problème**</span><span class="sxs-lookup"><span data-stu-id="54efa-152">**Problem**</span></span>  
  
 <span data-ttu-id="54efa-153">Même si les valeurs valides sont spécifiées pour les propriétés de liaison PollingStatement et PolledDataAvailableStatement, l’adaptateur ne reçoit pas un message d’interrogation de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="54efa-153">Even if valid values are specified for the PollingStatement and PolledDataAvailableStatement binding properties, the adapter does not receive a polling message from SQL Server.</span></span>  
  
 <span data-ttu-id="54efa-154">**Cause**</span><span class="sxs-lookup"><span data-stu-id="54efa-154">**Cause**</span></span>  
  
 <span data-ttu-id="54efa-155">Vérifiez si une autre transaction a pris un verrou sur la table de l’interrogation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="54efa-155">Verify whether any other transaction has taken a lock on the table that the adapter is polling.</span></span>  
  
 <span data-ttu-id="54efa-156">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="54efa-156">**Resolution**</span></span>  
  
 <span data-ttu-id="54efa-157">Si vous souhaitez interroger une table qui est mis à jour dans le cadre d’une autre transaction, vous pouvez envisager d’utiliser le paramètre « avec (nolock) » dans le cadre de la requête spécifiée pour la propriété de liaison PolledDataAvailableStatement pour vous assurer que les données sont retournées même si un verrou est imposé par l’autre transaction.</span><span class="sxs-lookup"><span data-stu-id="54efa-157">If you want to poll a table that is being updated as part of another transaction, you can consider using “with (nolock)” parameter as part of the query specified for PolledDataAvailableStatement binding property to ensure that data is returned even if a lock is imposed by the other transaction.</span></span> <span data-ttu-id="54efa-158">Pour plus d’informations, consultez [verrouillage SQL dans le moteur de base de données](https://msdn.microsoft.com/library/ms190615.aspx).</span><span class="sxs-lookup"><span data-stu-id="54efa-158">For more information, see [SQL Locking in the Database Engine](https://msdn.microsoft.com/library/ms190615.aspx).</span></span>
  
###  <a name="BKMK_SQLSingleOp"></a><span data-ttu-id="54efa-159">L’adaptateur ne parvient pas à insérer, mettre à jour ou supprimer des volumes importants de données en une seule opération à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="54efa-159">The adapter fails to insert, update, or delete large volumes of data in a single operation using BizTalk Server</span></span>  
 <span data-ttu-id="54efa-160">**Problème**</span><span class="sxs-lookup"><span data-stu-id="54efa-160">**Problem**</span></span>  
  
 <span data-ttu-id="54efa-161">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ne parvient pas à insérer, mettre à jour ou supprimer des volumes importants de données dans une seule opération à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54efa-161">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] fails to insert, update, or delete large volumes of data in a single operation using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="54efa-162">**Cause**</span><span class="sxs-lookup"><span data-stu-id="54efa-162">**Cause**</span></span>  
  
 <span data-ttu-id="54efa-163">Insertion, mise à jour ou suppression des volumes importants de données peut prendre un temps et le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ou la transaction dans laquelle l’opération est effectuée, peut expirer.</span><span class="sxs-lookup"><span data-stu-id="54efa-163">Inserting, updating, or deleting large volumes of data may take time and the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] or the transaction in which the operation is being performed, may time out.</span></span>  
  
 <span data-ttu-id="54efa-164">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="54efa-164">**Resolution**</span></span>  
  
-   <span data-ttu-id="54efa-165">**Pour BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="54efa-165">**For BizTalk Server**</span></span>  
  
    1.  <span data-ttu-id="54efa-166">Spécifiez le délai d’attente pour l’adaptateur WCF dans le fichier machine.config. Accédez au fichier machine.config sous \<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG et ajouter l’extrait de code qui ressemble à ceci.</span><span class="sxs-lookup"><span data-stu-id="54efa-166">Specify the timeout for the WCF adapter in the machine.config. Navigate to the machine.config file under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG and add the excerpt that resembles the following.</span></span>  
  
        ```  
        <configuration>  
         <system.transactions>  
          <machineSettings maxTimeout="02:00:00" />  
         </system.transactions>  
        </configuration>  
        ```  
  
         <span data-ttu-id="54efa-167">Avec ce paramètre, le délai d’attente de l’adaptateur WCF est définie à 2 heures.</span><span class="sxs-lookup"><span data-stu-id="54efa-167">With this setting, the WCF adapter timeout is set to 2 hours.</span></span>  
  
    2.  <span data-ttu-id="54efa-168">Spécifiez les paramètres de délai d’attente pour les transactions MSDTC dans le fichier machine.config. Accédez au fichier machine.config sous \<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG et ajouter l’extrait de code qui ressemble à ceci.</span><span class="sxs-lookup"><span data-stu-id="54efa-168">Specify the timeout settings for MSDTC transactions in the machine.config. Navigate to the machine.config file under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG and add the excerpt that resembles the following.</span></span>  
  
        ```  
        <system.transactions>   
                <defaultSettings distributedTransactionManagerName="<computer_name>" timeout="02:00:00"/>   
            </system.transactions>  
  
        ```  
  
         <span data-ttu-id="54efa-169">Avec ce paramètre, le délai d’attente MSDTC est définie à 2 heures.</span><span class="sxs-lookup"><span data-stu-id="54efa-169">With this setting, the MSDTC timeout is set to 2 hours.</span></span> <span data-ttu-id="54efa-170">La valeur par défaut pour le délai d’attente MSDTC est 10 minutes.</span><span class="sxs-lookup"><span data-stu-id="54efa-170">The default value for MSDTC timeout is 10 minutes.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="54efa-171">Vous devez effectuer cette modification sur les ordinateurs exécutant le client de l’adaptateur et le SQL Server.</span><span class="sxs-lookup"><span data-stu-id="54efa-171">You must make this change on the computers running the adapter client and SQL Server.</span></span> <span data-ttu-id="54efa-172">Dans l’extrait de code, remplacez < nom_ordinateur > par le nom de l’ordinateur exécutant le client de l’adaptateur et le SQL Server.</span><span class="sxs-lookup"><span data-stu-id="54efa-172">In the excerpt, replace <computer_name> with the name of computer running the adapter client and SQL Server.</span></span>  
  
    3.  <span data-ttu-id="54efa-173">Définir le **SendTimeout** liaison de propriété pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à une valeur relativement élevée.</span><span class="sxs-lookup"><span data-stu-id="54efa-173">Set the **SendTimeout** binding property for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to a fairly large value.</span></span> <span data-ttu-id="54efa-174">Pour obtenir des instructions sur la façon de définir les propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="54efa-174">For instructions on how to set the binding properties, see [Configure the binding properties for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).</span></span>  
  
###  <a name="BKMK_SQLFullSchemaValidate"></a><span data-ttu-id="54efa-175">Échec de la validation de schéma complet dans BizTalk Server pour les messages de réponse qui contient le jeu de données</span><span class="sxs-lookup"><span data-stu-id="54efa-175">Full schema validation in BizTalk Server fails for response messages containing DataSet</span></span>  
 <span data-ttu-id="54efa-176">**Problème**</span><span class="sxs-lookup"><span data-stu-id="54efa-176">**Problem**</span></span>  
  
 <span data-ttu-id="54efa-177">Pour les opérations qui retournent un message de réponse contenant un jeu de données, par exemple ExecuteReader, la validation de schéma complet échoue dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54efa-177">For operations that return a response message containing a DataSet, for example ExecuteReader, full schema validation fails in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="54efa-178">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="54efa-178">**Resolution**</span></span>  
  
 <span data-ttu-id="54efa-179">Nous vous recommandons de ne pas une validation de schéma complet pour les messages de réponse qui contient un jeu de données.</span><span class="sxs-lookup"><span data-stu-id="54efa-179">We recommend you to not do a full schema validation for response messages containing a dataset.</span></span> <span data-ttu-id="54efa-180">Au lieu de cela, vous pouvez procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="54efa-180">Instead, you could do the following:</span></span>  
  
1.  <span data-ttu-id="54efa-181">Exécuter l’opération une fois qui retourne le message de réponse avec le schéma.</span><span class="sxs-lookup"><span data-stu-id="54efa-181">Execute the operation once that returns the response message with the schema.</span></span>  
  
2.  <span data-ttu-id="54efa-182">Copiez le schéma à partir du message de réponse dans un fichier .xsd et de l’ajouter à votre projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="54efa-182">Copy the schema from the response message to a .xsd file and add this file to your BizTalk project.</span></span>  
  
3.  <span data-ttu-id="54efa-183">Utiliser une requête xpath dans votre orchestration pour extraire les données à partir du message de réponse.</span><span class="sxs-lookup"><span data-stu-id="54efa-183">Use an xpath query in your orchestration to extract the data from the response message.</span></span>  
  
###  <a name="BKMK_SQLRootNode"></a><span data-ttu-id="54efa-184">Erreur avec RootNode TypeName dans les projets BizTalk</span><span class="sxs-lookup"><span data-stu-id="54efa-184">Error with RootNode TypeName in BizTalk Projects</span></span>  
 <span data-ttu-id="54efa-185">**Problème**</span><span class="sxs-lookup"><span data-stu-id="54efa-185">**Problem**</span></span>  
  
 <span data-ttu-id="54efa-186">Dans un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], si les schémas générés à partir de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contient des caractères non valides ou des mots réservés pour le **RootNode TypeName** propriété, l’erreur suivante se produit lors de la compilation du projet :</span><span class="sxs-lookup"><span data-stu-id="54efa-186">In a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], if the schemas generated from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contains invalid characters or reserved words for the **RootNode TypeName** property, the following error will occur while compiling the project:</span></span>  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 <span data-ttu-id="54efa-187">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="54efa-187">**Resolution**</span></span>  
  
1.  <span data-ttu-id="54efa-188">Cliquez sur le noeud rood référencé dans l’erreur et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="54efa-188">Right-click the rood node referenced in the error and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="54efa-189">Pour le **RootNode TypeName** propriété, supprimer des caractères non valides ou réservés mots, par exemple, point (.).</span><span class="sxs-lookup"><span data-stu-id="54efa-189">For the **RootNode TypeName** property, remove any illegal characters or reserved words, for example, dot (.).</span></span>  
  
###  <a name="BKMK_SQLMetadataStronglyTyped"></a><span data-ttu-id="54efa-190">Adaptateur ne peut pas générer des métadonnées de fortement typée de procédure stockée avec des tables temporaires</span><span class="sxs-lookup"><span data-stu-id="54efa-190">Adapter fails to generate metadata of strongly-typed stored procedure with temporary tables</span></span>  
 <span data-ttu-id="54efa-191">**Problème**</span><span class="sxs-lookup"><span data-stu-id="54efa-191">**Problem**</span></span>  
  
 <span data-ttu-id="54efa-192">L’adaptateur ne parvient pas à générer des métadonnées pour les procédures stockées fortement typée qui incluent des tables temporaires dans leur définition.</span><span class="sxs-lookup"><span data-stu-id="54efa-192">The adapter fails to generate metadata for strongly-typed stored procedures that include temporary tables in their definition.</span></span> <span data-ttu-id="54efa-193">L’adaptateur permet à l’exception suivante.</span><span class="sxs-lookup"><span data-stu-id="54efa-193">The adapter gives the following exception.</span></span>  
  
```  
Microsoft.ServiceModel.Channels.Common.MetadataException:  
Retrieval of Operation Metadata has failed while building WSDL at 'TypedProcedure/<schema>/<stored_procedure_name>' --->  
System.Data.SqlClient.SqlException: Invalid object name '<temp_table_name>'.  
  
```  
  
 <span data-ttu-id="54efa-194">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="54efa-194">**Resolution**</span></span>  
  
 <span data-ttu-id="54efa-195">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ne prend pas en charge générer des métadonnées pour les procédures stockées fortement typées qui contiennent des tables temporaires dans leur définition.</span><span class="sxs-lookup"><span data-stu-id="54efa-195">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not support generating metadata for strongly-typed stored procedures that contain temporary tables in their definition.</span></span> <span data-ttu-id="54efa-196">Au lieu de cela, vous devez générer les métadonnées de la même procédure sous la **procédures** nœud lors de l’utilisation du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54efa-196">Instead, you should generate metadata for the same procedure from under the **Procedures** node while using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span>  
  
###  <a name="BKMK_SQLVS2008"></a><span data-ttu-id="54efa-197">Avertissement de liaison non valide lors de l’utilisation de l’adaptateur dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="54efa-197">Invalid binding warning when using the adapter in Visual Studio</span></span>  
 <span data-ttu-id="54efa-198">**Problème**</span><span class="sxs-lookup"><span data-stu-id="54efa-198">**Problem**</span></span>  
  
 <span data-ttu-id="54efa-199">Lorsque vous utilisez l’adaptateur pour créer une application dans Visual Studio et que vous ouvrez le fichier de configuration (app.config) généré par l’adaptateur, vous voyez un avertissement similaire au suivant :</span><span class="sxs-lookup"><span data-stu-id="54efa-199">When you use the adapter to create an application in Visual Studio and you open the configuration file (app.config) generated by the adapter, you see a warning similar to the following:</span></span>  
  
```  
The element 'bindings' has invalid child element 'sqlBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 <span data-ttu-id="54efa-200">**Cause**</span><span class="sxs-lookup"><span data-stu-id="54efa-200">**Cause**</span></span>  
  
 <span data-ttu-id="54efa-201">Cet avertissement s’affiche, car le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] de liaison, `sqlBinding`, pas une liaison standard fournie avec le [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54efa-201">This warning appears because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding, `sqlBinding`, is not a standard binding shipped with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].</span></span>  
  
 <span data-ttu-id="54efa-202">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="54efa-202">**Resolution**</span></span>  
  
 <span data-ttu-id="54efa-203">Vous pouvez ignorer cet avertissement sans problème.</span><span class="sxs-lookup"><span data-stu-id="54efa-203">You can safely ignore this warning.</span></span>  
  
###  <a name="BKMK_SQLNotification"></a><span data-ttu-id="54efa-204">BizTalk Server lève une exception si vous utilisez plusieurs schémas de Notification dans la même application ou le schéma de Notification entre plusieurs applications sur le même hôte</span><span class="sxs-lookup"><span data-stu-id="54efa-204">BizTalk Server throws an exception if you use more than one Notification schema in the same application or use the Notification schema across multiple applications on the same host</span></span>  
 <span data-ttu-id="54efa-205">**Problème**</span><span class="sxs-lookup"><span data-stu-id="54efa-205">**Problem**</span></span>  
  
 <span data-ttu-id="54efa-206">BizTalk Server lève une exception XLANG ou une exception indiquant que l’application ne peut pas localiser la spécification de document, car plusieurs schémas correspondent au type de message.</span><span class="sxs-lookup"><span data-stu-id="54efa-206">BizTalk Server throws an XLANG exception or an exception stating that the application cannot locate the document specification because multiple schemas matched the message type.</span></span>  
  
 <span data-ttu-id="54efa-207">**Cause**</span><span class="sxs-lookup"><span data-stu-id="54efa-207">**Cause**</span></span>  
  
 <span data-ttu-id="54efa-208">Cela se produit en raison de le des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="54efa-208">This happens because of either of the following:</span></span>  
  
-   <span data-ttu-id="54efa-209">Vous avez généré plus d’un schéma de Notification dans un projet BizTalk Server, déployé dans une application BizTalk Server, puis exécutez l’application pour recevoir des notifications à partir de la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="54efa-209">You have generated more than one Notification schema in a BizTalk Server project, deployed it to a BizTalk Server application, and then ran the application to receive notifications from the SQL Server database.</span></span> <span data-ttu-id="54efa-210">Étant donné que les schémas de Notification sont courantes, il existe un conflit entre les schémas qui sont déployés dans l’application BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="54efa-210">Because the Notification schemas are common, there is a conflict between the schemas that are deployed in the BizTalk Server application.</span></span>  
  
-   <span data-ttu-id="54efa-211">En cas de plusieurs projets, vous avez généré un schéma de Notification pour chacun des projets, déployés dans chaque projet à une application BizTalk Server distincte sur le même hôte BizTalk Server, puis exécutez une application ou les applications de recevoir des notifications à partir de la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="54efa-211">In case of multiple projects, you have generated a Notification schema for each of the BizTalk Server projects, deployed each project to a separate BizTalk Server application on the same host, and then ran an application or applications to receive notifications from the SQL Server database.</span></span> <span data-ttu-id="54efa-212">Étant donné que les schémas et les assemblys sont accessibles parmi les applications dans BizTalk Server, il existe un conflit entre les schémas courants déployés dans diverses applications BizTalk Server et les assemblys.</span><span class="sxs-lookup"><span data-stu-id="54efa-212">Because the schemas and assemblies are accessible across the applications in BizTalk Server, there is a conflict between the common schemas deployed under various BizTalk Server applications and assemblies.</span></span>  
  
 <span data-ttu-id="54efa-213">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="54efa-213">**Resolution**</span></span>  
  
 <span data-ttu-id="54efa-214">Utiliser un seul fichier de schéma de Notification pour une application BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="54efa-214">Use a single Notification schema file for a BizTalk Server application.</span></span> <span data-ttu-id="54efa-215">Si vous avez besoin d’utiliser le schéma de Notification dans plusieurs applications de BizTalk Server sur le même hôte, créer une application contenant un seul schéma de Notification, puis utiliser le schéma de notification à partir de toutes les autres applications dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="54efa-215">If you need to use the Notification schema in multiple BizTalk Server applications on the same host, create an application containing a single Notification schema, and then use the notification schema from all other applications in BizTalk Server.</span></span>  
  
###  <a name="BKMK_SQLRestoreConn"></a><span data-ttu-id="54efa-216">Client de l’adaptateur lève une exception sur l’exécution d’une opération après la restauration de la connectivité entre le client de carte et de la base de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="54efa-216">Adapter client throws an exception on performing an operation after the connectivity is restored between the adapter client and the SQL Server database</span></span>  
 <span data-ttu-id="54efa-217">**Problème**</span><span class="sxs-lookup"><span data-stu-id="54efa-217">**Problem**</span></span>  
  
 <span data-ttu-id="54efa-218">Client de l’adaptateur lève l’exception suivante sur l’exécution d’une opération sur la base de données SQL Server :</span><span class="sxs-lookup"><span data-stu-id="54efa-218">Adapter client throws the following exception on executing an operation on the SQL Server database:</span></span>  
  
```  
{System.Data.Common.DbException} = {"A transport-level error has occurred when sending the request to the server. (provider: TCP Provider, error: 0 - An existing connection was forcibly closed by the remote host.)"}  
```  
  
 <span data-ttu-id="54efa-219">**Cause**</span><span class="sxs-lookup"><span data-stu-id="54efa-219">**Cause**</span></span>  
  
 <span data-ttu-id="54efa-220">Pendant l’exécution d’une opération, l’adaptateur utilise la connexion à partir du pool de connexions SQL ADO.NET pour se connecter à la base de données SQL Server et d’effectuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="54efa-220">During the execution of an operation, the adapter uses the connection from the SQL ADO.NET connection pool to connect to the SQL Server database, and perform the operation.</span></span> <span data-ttu-id="54efa-221">S’il existe une brève interruption de réseau entre le client de carte et de la base de données SQL Server, ou si la base de données SQL Server est momentanément indisponible, toutes les connexions dans le pool de connexions SQL ADO.NET deviennent non valides.</span><span class="sxs-lookup"><span data-stu-id="54efa-221">If there is a brief network outage between the adapter client and the SQL Server database or if the SQL Server database is down temporarily, all the connections in the SQL ADO.NET connection pool become invalid.</span></span> <span data-ttu-id="54efa-222">Une fois la connectivité est rétablie et que vous essayez d’effectuer une opération sur la base de données SQL Server, l’adaptateur utilise les mêmes connexions non valides à partir du pool de connexions ADO.NET de SQL, et par conséquent, le client de l’adaptateur lève l’exception.</span><span class="sxs-lookup"><span data-stu-id="54efa-222">After the connectivity is restored and you try to perform an operation on the SQL Server database, the adapter uses the same invalid connections from the SQL ADO.NET connection pool, and therefore the adapter client throws the exception.</span></span>  
  
 <span data-ttu-id="54efa-223">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="54efa-223">**Resolution**</span></span>  
  
 <span data-ttu-id="54efa-224">Le client de l’adaptateur doit implémenter la logique de nouvelle tentative dans leur exécution de l’opération, où qu’ils doivent intercepter l’exception et spécifier le nombre de tentatives d’opération « n + 1 », où « n » est la valeur spécifiée pour la propriété de liaison MaxConnectionPoolSize.</span><span class="sxs-lookup"><span data-stu-id="54efa-224">The adapter client should implement retry logic in their operation execution where they should catch the exception and specify the operation retry count as “n+1”, where “n” is the value specified for the MaxConnectionPoolSize binding property.</span></span> <span data-ttu-id="54efa-225">Cela signifie que s’il existe le nombre de « n » de connexions dans le pool de connexions qui ont été rendue non valide, en théorie l’adaptateur client doit réessayer pour un maximum de « n + 1 » reprises pour obtenir une connexion valide et donc d’effectuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="54efa-225">This implies that if there are “n” number of connections in the connection pool that have been rendered invalid, theoretically the adapter client should retry for a maximum of “n+1” times to get a valid connection, and hence perform the operation.</span></span>  
  
 <span data-ttu-id="54efa-226">Par exemple, pour spécifier le nombre de tentatives [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], ouvrez le **propriétés** boîte de dialogue d’un port d’envoi dans une application, cliquez sur **Options avancées de Transport** dans le volet gauche de la boîte de dialogue, puis dans le **Options de transport** zone, spécifiez une valeur dans la **nombre de tentatives** liste.</span><span class="sxs-lookup"><span data-stu-id="54efa-226">For example, to specify the retry count in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], open the **Properties** dialog box of a send port in an application, click **Transport Advanced Options** in the left pane of the dialog box, and in the **Transport Options** area, specify a value in the **Retry count** list.</span></span>  
  
###  <a name="BKMK_MemUsage"></a><span data-ttu-id="54efa-227">Utilisation de la mémoire et de thread nombre augmente lors de l’utilisation de la carte dans une opération entrante</span><span class="sxs-lookup"><span data-stu-id="54efa-227">Memory usage and thread count increases when using the adapter in a transacted inbound operation</span></span>  
 <span data-ttu-id="54efa-228">**Problème**</span><span class="sxs-lookup"><span data-stu-id="54efa-228">**Problem**</span></span>  
  
 <span data-ttu-id="54efa-229">Dans une opération entrante, telles que l’interrogation, **si aucune donnée n’est disponible dans la table interrogée** et l’adaptateur continue à interroger, sur une période de temps, vous rencontrez une augmentation de l’utilisation de la mémoire et le nombre de threads.</span><span class="sxs-lookup"><span data-stu-id="54efa-229">In a transacted inbound operation, such as Polling, **if there is no data available in the table being polled** and the adapter continues to poll, over a period of time you experience an increase in the memory usage and the thread count.</span></span>  
  
 <span data-ttu-id="54efa-230">**Cause**</span><span class="sxs-lookup"><span data-stu-id="54efa-230">**Cause**</span></span>  
  
 <span data-ttu-id="54efa-231">**Si aucune donnée n’est disponible dans la table interrogée**, après chaque cycle de délai d’attente de réception [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] génère un nouveau thread pour poursuivre l’opération d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="54efa-231">**If there is no data available in the table being polled**, after every receive timeout cycle, [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] spawns a new thread to continue the polling operation.</span></span> <span data-ttu-id="54efa-232">Par conséquent, l’utilisation de count et de la mémoire du thread augmente sur une période de temps.</span><span class="sxs-lookup"><span data-stu-id="54efa-232">Hence, the thread count and memory usage increases over a period of time.</span></span> <span data-ttu-id="54efa-233">Toutefois, si la table interrogée possède des données, le même thread continue à effectuer toutes les interrogations suivantes.</span><span class="sxs-lookup"><span data-stu-id="54efa-233">However, if the table being polled has some data, the same thread continues to perform all subsequent polls.</span></span>  
  
 <span data-ttu-id="54efa-234">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="54efa-234">**Resolution**</span></span>  
  
 <span data-ttu-id="54efa-235">Nous vous recommandons d’affecter le **ReceiveTimeout** à la valeur maximale possible, qui est 24.20:31:23.6470000 (24 jours) afin qu’un nouveau thread est généré uniquement 24 jours.</span><span class="sxs-lookup"><span data-stu-id="54efa-235">We recommend setting the **ReceiveTimeout** to the maximum possible value, which is 24.20:31:23.6470000 (24 days) so that a new thread is spawned only every 24 days.</span></span> <span data-ttu-id="54efa-236">Cela garantit que le nombre de threads et de l’utilisation de mémoire n’augmente pas trop trop tôt.</span><span class="sxs-lookup"><span data-stu-id="54efa-236">This will ensure that the memory usage and thread count does not grow too much too soon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54efa-237">Si SqlAdapterInboundTransactionBehavior a été défini, assurez-vous que le TransactionTimeout est également configuré pour la valeur maximale possible, qui est 24.20:31:23.6470000 (24 jours).</span><span class="sxs-lookup"><span data-stu-id="54efa-237">If SqlAdapterInboundTransactionBehavior has been set, make sure the TransactionTimeout is also configured to maximum possible value, which is 24.20:31:23.6470000 (24 days).</span></span> <span data-ttu-id="54efa-238">Lorsque vous utilisez cette solution de contournement, nous pouvons ajouter la SqlAdapterInboundTransactionBehavior uniquement si le niveau d’isolation de transaction doit être configurée.</span><span class="sxs-lookup"><span data-stu-id="54efa-238">When using this workaround, we can add the SqlAdapterInboundTransactionBehavior only if the transaction isolation level has to be configured.</span></span> <span data-ttu-id="54efa-239">Sinon, il est recommandé de supprimer ce comportement.</span><span class="sxs-lookup"><span data-stu-id="54efa-239">Else, it is a best practice to remove that behavior.</span></span>  
  
 <span data-ttu-id="54efa-240">Pour plus d’informations sur la **ReceiveTimeout** liaison de propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="54efa-240">For more information about the **ReceiveTimeout** binding property, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="54efa-241">Pour obtenir des instructions sur la spécification des propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="54efa-241">For instructions on specifying binding properties, see [Configure the binding properties for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54efa-242">Lors de l’utilisation de l’adaptateur avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], définir le délai d’attente pour une valeur élevée n’affecte pas les fonctionnalités de la carte.</span><span class="sxs-lookup"><span data-stu-id="54efa-242">When using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], setting the timeout to a large value does not impact the functionality of the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54efa-243">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54efa-243">See Also</span></span>  
[<span data-ttu-id="54efa-244">Résoudre les problèmes de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="54efa-244">Troubleshoot the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)
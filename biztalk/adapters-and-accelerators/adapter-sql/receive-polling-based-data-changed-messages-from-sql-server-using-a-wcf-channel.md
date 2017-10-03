---
title: "Recevoir des Messages d’interrogation de données modifiées à partir de SQL Server à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0f4af71-fb0c-433d-ba74-48ee6487eb1a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb785631d6fe00ea68f57f943dca11ebd1a84b1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-based-data-changed-messages-from-sql-server-by-using-the-wcf-channel-model"></a><span data-ttu-id="e83d0-102">Recevoir des Messages d’interrogation de données modifiées à partir de SQL Server à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="e83d0-102">Receive Polling-based Data-changed Messages from SQL Server by Using the WCF Channel Model</span></span>
<span data-ttu-id="e83d0-103">Vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des messages de modification de données périodiques de tables SQL Server ou des vues.</span><span class="sxs-lookup"><span data-stu-id="e83d0-103">You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive periodic data-change messages for SQL Server tables or views.</span></span> <span data-ttu-id="e83d0-104">Vous pouvez spécifier une instruction d’interrogation de l’adaptateur s’exécute pour interroger la base de données.</span><span class="sxs-lookup"><span data-stu-id="e83d0-104">You can specify a polling statement that the adapter executes to poll the database.</span></span> <span data-ttu-id="e83d0-105">L’instruction d’interrogation peut être une instruction SELECT ou une procédure stockée qui retourne un jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="e83d0-105">The polling statement can be a SELECT statement or a stored procedure that returns a result set.</span></span>  
  
 <span data-ttu-id="e83d0-106">Pour plus d’informations sur la façon dont l’adaptateur prend en charge d’interrogation, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span><span class="sxs-lookup"><span data-stu-id="e83d0-106">For more information on how the adapter supports polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e83d0-107">Si vous souhaitez disposer d’interrogation plus d’une opération dans une application unique, vous devez spécifier un **InboundID** propriété de connexion dans le cadre de la connexion URI pour le rendre unique.</span><span class="sxs-lookup"><span data-stu-id="e83d0-107">If you want to have more than one polling operation in a single application, you must specify an **InboundID** connection property as part of the connection URI to make it unique.</span></span> <span data-ttu-id="e83d0-108">L’ID entrant que vous spécifiez est ajouté à l’espace de noms d’opération pour le rendre unique.</span><span class="sxs-lookup"><span data-stu-id="e83d0-108">The inbound ID you specify is added to the operation namespace to make it unique.</span></span>  
  
## <a name="how-this-topic-demonstrates-polling"></a><span data-ttu-id="e83d0-109">Comment cette rubrique illustre l’interrogation</span><span class="sxs-lookup"><span data-stu-id="e83d0-109">How This Topic Demonstrates Polling</span></span>  
 <span data-ttu-id="e83d0-110">Dans cette rubrique, pour illustrer comment le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge la réception de données, les messages de modification, créer une application .NET pour les **d’interrogation** opération.</span><span class="sxs-lookup"><span data-stu-id="e83d0-110">In this topic, to demonstrate how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports receiving data change messages, create a .NET application for the **Polling** operation.</span></span> <span data-ttu-id="e83d0-111">Pour cette rubrique, vous devez spécifier le **PolledDataAvailableStatement** en tant que :</span><span class="sxs-lookup"><span data-stu-id="e83d0-111">For this topic, specify the **PolledDataAvailableStatement** as:</span></span>  
  
```  
SELECT COUNT(*) FROM Employee  
```  
  
 <span data-ttu-id="e83d0-112">Le **PolledDataAvailableStatement** doit retourner un jeu de résultats avec la première cellule contenant une valeur positive.</span><span class="sxs-lookup"><span data-stu-id="e83d0-112">The **PolledDataAvailableStatement** must return a result set with the first cell containing a positive value.</span></span> <span data-ttu-id="e83d0-113">Si la première cellule ne contient pas une valeur positive, l’adaptateur n’exécute pas l’instruction d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="e83d0-113">If the first cell does not contain a positive value, the adapter does not execute the polling statement.</span></span>  
  
 <span data-ttu-id="e83d0-114">Dans le cadre de l’instruction d’interrogation, effectuez les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e83d0-114">As part of the polling statement, perform the following operations:</span></span>  
  
1.  <span data-ttu-id="e83d0-115">Sélectionnez toutes les lignes de la table Employee.</span><span class="sxs-lookup"><span data-stu-id="e83d0-115">Select all the rows from the Employee table.</span></span>  
  
2.  <span data-ttu-id="e83d0-116">Exécuter une procédure stockée (MOVE_EMP_DATA) pour déplacer tous les enregistrements de la table Employee pour une table HistoriqueEmployé.</span><span class="sxs-lookup"><span data-stu-id="e83d0-116">Execute a stored procedure (MOVE_EMP_DATA) to move all the records from the Employee table to an EmployeeHistory table.</span></span>  
  
3.  <span data-ttu-id="e83d0-117">Exécuter une procédure stockée (ADD_EMP_DETAILS) pour ajouter un nouvel enregistrement dans la table Employee.</span><span class="sxs-lookup"><span data-stu-id="e83d0-117">Execute a stored procedure (ADD_EMP_DETAILS) to add a new record to the Employee table.</span></span> <span data-ttu-id="e83d0-118">Cette procédure prend le nom de l’employé, désignation et salaire en tant que paramètres.</span><span class="sxs-lookup"><span data-stu-id="e83d0-118">This procedure takes the employee name, designation, and salary as parameters.</span></span>  
  
 <span data-ttu-id="e83d0-119">Pour effectuer ces opérations, vous devez spécifier les informations suivantes pour le **PollingStatement** propriété de liaison :</span><span class="sxs-lookup"><span data-stu-id="e83d0-119">To perform these operations, you must specify the following for the **PollingStatement** binding property:</span></span>  
  
```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  
  
 <span data-ttu-id="e83d0-120">Après l’exécution de l’instruction d’interrogation, tous les enregistrements de la table Employee sont sélectionnés et la réception du message à partir de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e83d0-120">After the polling statement is executed, all the records from the Employee table are selected and the message from SQL Server is received.</span></span> <span data-ttu-id="e83d0-121">Une fois la procédure stockée de MOVE_EMP_DATA est exécutée par l’adaptateur, tous les enregistrements sont déplacés vers la table HistoriqueEmployé.</span><span class="sxs-lookup"><span data-stu-id="e83d0-121">Once the MOVE_EMP_DATA stored procedure is executed by the adapter, all the records are moved to the EmployeeHistory table.</span></span> <span data-ttu-id="e83d0-122">Ensuite, la procédure stockée de ADD_EMP_DETAILS est exécutée pour ajouter un nouvel enregistrement dans la table Employee.</span><span class="sxs-lookup"><span data-stu-id="e83d0-122">Then, the ADD_EMP_DETAILS stored procedure is executed to add a new record to the Employee table.</span></span> <span data-ttu-id="e83d0-123">L’exécution de l’interrogation suivante retourne uniquement un seul enregistrement.</span><span class="sxs-lookup"><span data-stu-id="e83d0-123">The next polling execution will only return a single record.</span></span> <span data-ttu-id="e83d0-124">Ce cycle se poursuit jusqu'à la fermeture de l’écouteur de canal.</span><span class="sxs-lookup"><span data-stu-id="e83d0-124">This cycle continues until you close the channel listener.</span></span>  
  
## <a name="configuring-a-polling-query-with-the-sql-adapter-binding-properties"></a><span data-ttu-id="e83d0-125">Configuration d’une requête d’interrogation avec l’adaptateur SQL propriétés de liaison</span><span class="sxs-lookup"><span data-stu-id="e83d0-125">Configuring a Polling Query with the SQL Adapter Binding Properties</span></span>  
 <span data-ttu-id="e83d0-126">Le tableau suivant récapitule les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] propriétés que vous utilisez pour configurer l’adaptateur pour recevoir des messages de modification de données de liaison.</span><span class="sxs-lookup"><span data-stu-id="e83d0-126">The following table summarizes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding properties that you use to configure the adapter to receive data-change messages.</span></span> <span data-ttu-id="e83d0-127">Vous devez spécifier ces propriétés de liaison dans le cadre de l’application .NET pour l’interrogation.</span><span class="sxs-lookup"><span data-stu-id="e83d0-127">You must specify these binding properties as part of the .NET application for polling.</span></span>  
  
|<span data-ttu-id="e83d0-128">Propriété de liaison</span><span class="sxs-lookup"><span data-stu-id="e83d0-128">Binding Property</span></span>|<span data-ttu-id="e83d0-129"> Description</span><span class="sxs-lookup"><span data-stu-id="e83d0-129">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="e83d0-130">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="e83d0-130">**InboundOperationType**</span></span>|<span data-ttu-id="e83d0-131">Spécifie si vous souhaitez effectuer **d’interrogation**, **TypedPolling**, ou **Notification** opération entrante.</span><span class="sxs-lookup"><span data-stu-id="e83d0-131">Specifies whether you want to perform **Polling**, **TypedPolling**, or **Notification** inbound operation.</span></span> <span data-ttu-id="e83d0-132">Valeur par défaut est **d’interrogation**.</span><span class="sxs-lookup"><span data-stu-id="e83d0-132">Default is **Polling**.</span></span>|  
|<span data-ttu-id="e83d0-133">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="e83d0-133">**PolledDataAvailableStatement**</span></span>|<span data-ttu-id="e83d0-134">Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="e83d0-134">Specifies the SQL statement that the adapter executes to determine whether any data is available for polling.</span></span> <span data-ttu-id="e83d0-135">L’instruction SQL doit retourner un jeu de résultats composé de lignes et de colonnes.</span><span class="sxs-lookup"><span data-stu-id="e83d0-135">The SQL statement must return a result set consisting of rows and columns.</span></span> <span data-ttu-id="e83d0-136">Uniquement si une ligne est disponible, l’instruction SQL spécifiée pour le **PollingStatement** liaison de la propriété sera exécutée.</span><span class="sxs-lookup"><span data-stu-id="e83d0-136">Only if a row is available, the SQL statement specified for the **PollingStatement** binding property will be executed.</span></span>|  
|<span data-ttu-id="e83d0-137">**PollingIntervalInSeconds**</span><span class="sxs-lookup"><span data-stu-id="e83d0-137">**PollingIntervalInSeconds**</span></span>|<span data-ttu-id="e83d0-138">Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="e83d0-138">Specifies the interval, in seconds, at which the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="e83d0-139">La valeur par défaut est 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="e83d0-139">The default is 30 seconds.</span></span> <span data-ttu-id="e83d0-140">L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives.</span><span class="sxs-lookup"><span data-stu-id="e83d0-140">The polling interval determines the time interval between successive polls.</span></span> <span data-ttu-id="e83d0-141">Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur attend que le temps restant dans l’intervalle.</span><span class="sxs-lookup"><span data-stu-id="e83d0-141">If the statement is executed within the specified interval, the adapter waits for the remaining time in the interval.</span></span>|  
|<span data-ttu-id="e83d0-142">**PollingStatement**</span><span class="sxs-lookup"><span data-stu-id="e83d0-142">**PollingStatement**</span></span>|<span data-ttu-id="e83d0-143">Spécifie l’instruction SQL pour interroger la table de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e83d0-143">Specifies the SQL statement to poll the SQL Server database table.</span></span> <span data-ttu-id="e83d0-144">Vous pouvez spécifier une instruction SELECT simple ou une procédure stockée pour l’instruction d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="e83d0-144">You can specify a simple SELECT statement or a stored procedure for the polling statement.</span></span> <span data-ttu-id="e83d0-145">La valeur par défaut est null.</span><span class="sxs-lookup"><span data-stu-id="e83d0-145">The default is null.</span></span> <span data-ttu-id="e83d0-146">Vous devez spécifier une valeur pour **PollingStatement** pour activer l’interrogation.</span><span class="sxs-lookup"><span data-stu-id="e83d0-146">You must specify a value for **PollingStatement** to enable polling.</span></span> <span data-ttu-id="e83d0-147">L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="e83d0-147">The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="e83d0-148">Vous pouvez spécifier n’importe quel nombre d’instructions SQL séparées par un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="e83d0-148">You can specify any number of SQL statements separated by a semi-colon.</span></span>|  
|<span data-ttu-id="e83d0-149">**PollWhileDataFound**</span><span class="sxs-lookup"><span data-stu-id="e83d0-149">**PollWhileDataFound**</span></span>|<span data-ttu-id="e83d0-150">Spécifie si le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignore l’intervalle d’interrogation et exécute en permanence de l’instruction SQL spécifiée pour le **PolledDataAvailableStatement** liaison de propriété, si les données sont disponibles dans la table interrogée.</span><span class="sxs-lookup"><span data-stu-id="e83d0-150">Specifies whether the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignores the polling interval and continuously executes the SQL statement specified for the **PolledDataAvailableStatement** binding property, if data is available in the table being polled.</span></span> <span data-ttu-id="e83d0-151">Si aucune donnée n’est disponible dans la table, l’adaptateur revient à exécuter l’instruction SQL à l’intervalle d’interrogation spécifié.</span><span class="sxs-lookup"><span data-stu-id="e83d0-151">If no data is available in the table, the adapter reverts to execute the SQL statement at the specified polling interval.</span></span> <span data-ttu-id="e83d0-152">Valeur par défaut est **false**.</span><span class="sxs-lookup"><span data-stu-id="e83d0-152">Default is **false**.</span></span>|  
  
 <span data-ttu-id="e83d0-153">Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="e83d0-153">For a more complete description of these properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="e83d0-154">Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour interroger le SQL Server, lire le reste de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="e83d0-154">For a complete description of how to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to poll SQL Server, read the remainder of this topic.</span></span>  
  
## <a name="consuming-the-polling-request-message"></a><span data-ttu-id="e83d0-155">Le message de demande d’interrogation</span><span class="sxs-lookup"><span data-stu-id="e83d0-155">Consuming the Polling Request Message</span></span>  
 <span data-ttu-id="e83d0-156">L’adaptateur appelle la **d’interrogation** opération sur votre code pour interroger la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e83d0-156">The adapter invokes the **Polling** operation on your code to poll the SQL Server database.</span></span> <span data-ttu-id="e83d0-157">Autrement dit, l’adaptateur envoie un message de demande d’interrogation qui s’affiche sur une forme de canal IInputChannel.</span><span class="sxs-lookup"><span data-stu-id="e83d0-157">That is, the adapter sends a Polling request message that you receive over an IInputChannel channel shape.</span></span> <span data-ttu-id="e83d0-158">Le message de demande d’interrogation contient le jeu de résultats de la requête spécifiée par la propriété de liaison PollingStatement.</span><span class="sxs-lookup"><span data-stu-id="e83d0-158">The Polling request message contains the result set of the query specified by the PollingStatement binding property.</span></span> <span data-ttu-id="e83d0-159">Vous pouvez utiliser le message d’interrogation de deux manières :</span><span class="sxs-lookup"><span data-stu-id="e83d0-159">You can consume the Polling message in one of two ways:</span></span>  
  
-   <span data-ttu-id="e83d0-160">Pour consommer le message à l’aide de la valeur du nœud de diffusion en continu vous devez appeler la **WriteBodyContents** méthode sur la réponse de message et lui passer une **XmlDictionaryWriter** qui implémente la diffusion en continu de la valeur du nœud.</span><span class="sxs-lookup"><span data-stu-id="e83d0-160">To consume the message using node-value streaming you must call the **WriteBodyContents** method on the response message and pass it an **XmlDictionaryWriter** that implements node-value streaming.</span></span>  
  
-   <span data-ttu-id="e83d0-161">Pour consommer le message à l’aide du nœud de diffusion en continu, vous pouvez appeler **GetReaderAtBodyContents** sur le message de réponse pour obtenir un **XmlReader**.</span><span class="sxs-lookup"><span data-stu-id="e83d0-161">To consume the message using node streaming you can call **GetReaderAtBodyContents** on the response message to get an **XmlReader**.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="e83d0-162">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="e83d0-162">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="e83d0-163">Les exemples de cette rubrique interrogent la table Employee.</span><span class="sxs-lookup"><span data-stu-id="e83d0-163">The examples in this topic poll the Employee table.</span></span> <span data-ttu-id="e83d0-164">L’exemple utilise également les MOVE_EMP_DATA ADD_EMP_DETAILS procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="e83d0-164">The example also uses the MOVE_EMP_DATA and ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="e83d0-165">Un script pour générer ces artefacts est fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="e83d0-165">A script to generate these artifacts is supplied with the samples.</span></span> <span data-ttu-id="e83d0-166">Pour plus d’informations sur les exemples, consultez [exemples de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="e83d0-166">For more information about the samples, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span></span> <span data-ttu-id="e83d0-167">Un exemple, **Polling_ChannelModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="e83d0-167">A sample, **Polling_ChannelModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="receiving-inbound-messages-for-polling-operation-using-the-wcf-channel-model"></a><span data-ttu-id="e83d0-168">Réception des Messages entrants pour l’opération d’interrogation à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="e83d0-168">Receiving Inbound Messages for Polling Operation Using the WCF Channel Model</span></span>  
 <span data-ttu-id="e83d0-169">Cette section fournit des instructions sur la façon d’écrire une application .NET (modèle de canal) pour recevoir des messages entrants d’interrogation à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e83d0-169">This section provides instructions on how to write a .NET application (channel model) to receive inbound polling messages using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
#### <a name="to-receive-polling-messages-from-the-sql-adapter"></a><span data-ttu-id="e83d0-170">Pour recevoir des messages de l’interrogation de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="e83d0-170">To receive polling messages from the SQL adapter</span></span>  
  
1.  <span data-ttu-id="e83d0-171">Créez un projet Microsoft Visual c# dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e83d0-171">Create a Microsoft Visual C# project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="e83d0-172">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="e83d0-172">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="e83d0-173">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, et `System.Runtime.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="e83d0-173">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, and `System.Runtime.Serialization`.</span></span>  
  
3.  <span data-ttu-id="e83d0-174">Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="e83d0-174">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.Sql`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Description`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  <span data-ttu-id="e83d0-175">Spécifiez l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="e83d0-175">Specify a connection URI.</span></span> <span data-ttu-id="e83d0-176">Pour plus d’informations sur l’URI de connexion de l’adaptateur, consultez [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="e83d0-176">For more information about the adapter connection URI, see [Create the SQL Server connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>  
  
    ```  
    Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
    ```  
  
5.  <span data-ttu-id="e83d0-177">Créez une instance de **SqlAdapterBinding** et définissez les propriétés de liaison requises pour configurer l’interrogation.</span><span class="sxs-lookup"><span data-stu-id="e83d0-177">Create an instance of **SqlAdapterBinding** and set the binding properties required to configure polling.</span></span> <span data-ttu-id="e83d0-178">Au minimum, vous devez définir le **InboundOperationType**, **PolledDataAvailableStatement**, et **PollingStatement** propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="e83d0-178">At a minimum you must set the **InboundOperationType**, **PolledDataAvailableStatement**, and **PollingStatement** binding properties.</span></span> <span data-ttu-id="e83d0-179">Pour plus d’informations sur les propriétés utilisées pour configurer l’interrogation de liaison, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span><span class="sxs-lookup"><span data-stu-id="e83d0-179">For more information about binding properties used to configure polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  
  
    ```  
    SqlAdapterBinding binding = new SqlAdapterBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
    binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
    ```  
  
6.  <span data-ttu-id="e83d0-180">Créer une collection de paramètres de liaison et définir les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="e83d0-180">Create a binding parameter collection and set the credentials.</span></span>  
  
    ```  
    ClientCredentials credentials = new ClientCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
  
    BindingParameterCollection bindingParams = new BindingParameterCollection();  
    bindingParams.Add(credentials);  
    ```  
  
7.  <span data-ttu-id="e83d0-181">Créer un écouteur de canal et l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="e83d0-181">Create a channel listener and open it.</span></span> <span data-ttu-id="e83d0-182">Vous créez l’écouteur en appelant **BuildChannelListener < IInputChannel\>**  méthode sur le **SqlAdapterBinding**.</span><span class="sxs-lookup"><span data-stu-id="e83d0-182">You create the listener by invoking **BuildChannelListener<IInputChannel\>** method on the **SqlAdapterBinding**.</span></span>  
  
    ```  
    IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
    listener.Open();  
    ```  
  
8.  <span data-ttu-id="e83d0-183">Obtenir un **IInputChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur et ouvrez-le.</span><span class="sxs-lookup"><span data-stu-id="e83d0-183">Get an **IInputChannel** channel by invoking the **AcceptChannel** method on the listener and open it.</span></span>  
  
    ```  
    IInputChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  
  
9. <span data-ttu-id="e83d0-184">Appeler **réception** sur le canal pour obtenir le prochain message POLLINGSTMT à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="e83d0-184">Invoke **Receive** on the channel to get the next POLLINGSTMT message from the adapter.</span></span>  
  
    ```  
    Message message = channel.Receive();  
    ```  
  
10. <span data-ttu-id="e83d0-185">Utiliser le jeu de résultats retourné par l’opération POLLINGSTMT.</span><span class="sxs-lookup"><span data-stu-id="e83d0-185">Consume the result set returned by the POLLINGSTMT operation.</span></span> <span data-ttu-id="e83d0-186">Vous pouvez consommer le message en utilisant un **XmlReader** ou **XmlDictionaryWriter**.</span><span class="sxs-lookup"><span data-stu-id="e83d0-186">You can consume the message using either an **XmlReader** or an **XmlDictionaryWriter**.</span></span>  
  
    ```  
    XmlReader reader = message.GetReaderAtBodyContents();  
    ```  
  
11. <span data-ttu-id="e83d0-187">Fermer le canal lorsque vous avez terminé le traitement de la demande.</span><span class="sxs-lookup"><span data-stu-id="e83d0-187">Close the channel when you have completed processing the request.</span></span>  
  
    ```  
    channel.Close()  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e83d0-188">Vous devez fermer le canal une fois que vous avez terminé le traitement de l’opération POLLINGSTMT.</span><span class="sxs-lookup"><span data-stu-id="e83d0-188">You must close the channel after you have finished processing the POLLINGSTMT operation.</span></span> <span data-ttu-id="e83d0-189">Échec de fermer le canal peut affecter le comportement de votre code.</span><span class="sxs-lookup"><span data-stu-id="e83d0-189">Failure to close the channel may affect the behavior of your code.</span></span>  
  
12. <span data-ttu-id="e83d0-190">Fermer l’écouteur lorsque vous avez terminé la réception de messages de données modifiées.</span><span class="sxs-lookup"><span data-stu-id="e83d0-190">Close the listener when you are finished receiving data-changed messages.</span></span>  
  
    ```  
    listener.Close()  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e83d0-191">Fermeture de l’écouteur ne ferme pas les canaux créés à l’aide de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="e83d0-191">Closing the listener does not close channels created using the listener.</span></span> <span data-ttu-id="e83d0-192">Vous devez fermer explicitement chaque canal créé à l’aide de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="e83d0-192">You must explicitly close each channel created using the listener.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e83d0-193">Exemple</span><span class="sxs-lookup"><span data-stu-id="e83d0-193">Example</span></span>  
 <span data-ttu-id="e83d0-194">L’exemple suivant montre une requête d’interrogation qui s’exécute à la table Employee.</span><span class="sxs-lookup"><span data-stu-id="e83d0-194">The following example shows a polling query that executes the Employee table.</span></span> <span data-ttu-id="e83d0-195">L’instruction d’interrogation effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="e83d0-195">The polling statement performs the following tasks:</span></span>  
  
-   <span data-ttu-id="e83d0-196">Sélectionne tous les enregistrements de la table Employee.</span><span class="sxs-lookup"><span data-stu-id="e83d0-196">Selects all the records from the Employee table.</span></span>  
  
-   <span data-ttu-id="e83d0-197">Exécute la procédure MOVE_EMP_DATA stockées pour déplacer tous les enregistrements à partir de la table Employee à HistoriqueEmployé table.</span><span class="sxs-lookup"><span data-stu-id="e83d0-197">Executes the MOVE_EMP_DATA stored procedure to move all records from Employee table to EmployeeHistory table.</span></span>  
  
-   <span data-ttu-id="e83d0-198">Exécute la procédure stockée de ADD_EMP_DETAILS pour ajouter un enregistrement unique dans la table Employee.</span><span class="sxs-lookup"><span data-stu-id="e83d0-198">Executes the ADD_EMP_DETAILS stored procedure to add a single record to the Employee table.</span></span>  
  
 <span data-ttu-id="e83d0-199">Les messages d’interrogation sont enregistrés au `C:\PollingOutput.xml`.</span><span class="sxs-lookup"><span data-stu-id="e83d0-199">The polling messages are saved at `C:\PollingOutput.xml`.</span></span>  
  
```  
using System;  
using Microsoft.Adapters.Sql;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
  
using System.Xml;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("Sample started. This sample will poll 5 times and will perform the following tasks:");  
            Console.WriteLine("Press any key to start polling...");  
            Console.ReadLine();  
            IChannelListener<IInputChannel> listener = null;  
  
            IInputChannel channel = null;  
  
            try  
            {  
                TimeSpan messageTimeout = new TimeSpan(0, 0, 30);  
  
                SqlAdapterBinding binding = new SqlAdapterBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
                binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
  
                Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
  
                ClientCredentials credentials = new ClientCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                BindingParameterCollection bindingParams = new BindingParameterCollection();  
                bindingParams.Add(credentials);  
  
                listener = binding.BuildChannelListener<IInputChannel>(ConnectionUri, bindingParams);  
                listener.Open();  
  
                channel = listener.AcceptChannel();  
                channel.Open();  
  
                Console.WriteLine("Channel and Listener opened...");  
                Console.WriteLine("\nWaiting for polled data...");  
                Console.WriteLine("Receive request timeout is {0}", messageTimeout);  
  
                // Poll five times with the specified message timeout   
                // If a timeout occurs polling will be aborted  
                for (int i = 0; i < 5; i++)  
                {  
                    Console.WriteLine("Polling: " + i);  
                    Message message = null;  
                    XmlReader reader = null;  
                    try  
                    {  
                        //Message is received so process the results  
                        message = channel.Receive(messageTimeout);  
                    }  
                    catch (System.TimeoutException toEx)  
                    {  
                        Console.WriteLine("\nNo data for request number {0}: {1}", i + 1, toEx.Message);  
                        continue;  
                    }  
  
                    // Get the query results using an XML reader  
                    try  
                    {  
                        reader = message.GetReaderAtBodyContents();  
                    }  
                    catch (Exception ex)  
                    {  
                        Console.WriteLine("Exception :" + ex);  
                        throw;  
                    }  
  
                    XmlDocument doc = new XmlDocument();  
                    doc.Load(reader);  
                    using (XmlWriter writer = XmlWriter.Create("C:\\PollingOutput.xml"))  
                    {  
                        doc.WriteTo(writer);  
                        Console.WriteLine("The polling response is saved at 'C:\\PollingOutput.xml'");  
                    }  
  
                    // return the cursor  
                    Console.WriteLine();  
  
                    // close the reader  
                    reader.Close();  
  
                    message.Close();  
                }  
                Console.WriteLine("\nPolling done -- hit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
            }  
            finally  
            {  
                // IMPORTANT: close the channel and listener to stop polling  
                if (channel != null)  
                {  
                    if (channel.State == CommunicationState.Opened)  
                        channel.Close();  
                    else  
                        channel.Abort();  
                }  
  
                if (listener != null)  
                {  
                    if (listener.State == CommunicationState.Opened)  
                        listener.Close();  
                    else  
                        listener.Abort();  
                }  
            }  
        }  
    }  
}  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="e83d0-200">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e83d0-200">See Also</span></span>  
[<span data-ttu-id="e83d0-201">Développer des applications SQL à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="e83d0-201">Develop SQL applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)
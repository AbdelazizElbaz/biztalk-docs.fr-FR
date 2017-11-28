---
title: "Recevoir des Messages d’interrogation de données modifiées à partir de SQL Server en utilisant le modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8713dd38-65ff-4d89-b23b-a93c06c5ff22
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ff5ca099733a59fc5aa64c9ebbe261375f1a488
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-based-data-changed-messages-from-sql-server-using-the-wcf-service-model"></a><span data-ttu-id="ab11f-102">Recevoir des Messages d’interrogation de données modifiées à partir de SQL Server en utilisant le modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="ab11f-102">Receive Polling-based Data-changed Messages from SQL Server Using the WCF Service Model</span></span>
<span data-ttu-id="ab11f-103">Vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des messages de modification de données périodiques de tables SQL Server ou des vues.</span><span class="sxs-lookup"><span data-stu-id="ab11f-103">You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive periodic data-change messages for SQL Server tables or views.</span></span> <span data-ttu-id="ab11f-104">Vous pouvez spécifier une instruction d’interrogation de l’adaptateur s’exécute pour interroger la base de données.</span><span class="sxs-lookup"><span data-stu-id="ab11f-104">You can specify a polling statement that the adapter executes to poll the database.</span></span> <span data-ttu-id="ab11f-105">L’instruction d’interrogation peut être une instruction SELECT ou une procédure stockée qui retourne un jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="ab11f-105">The polling statement can be a SELECT statement or a stored procedure that returns a result set.</span></span>  
  
 <span data-ttu-id="ab11f-106">Pour plus d’informations sur la façon dont l’adaptateur prend en charge d’interrogation, consultez [d’interrogation dans SQL Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="ab11f-106">For more information on how the adapter supports polling, see [Polling in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab11f-107">Cette rubrique montre comment utiliser le **d’interrogation** entrant d’opération à utiliser les messages d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="ab11f-107">This topic demonstrates how to use the **Polling** inbound operation to use polling messages.</span></span> <span data-ttu-id="ab11f-108">Le message pour l’opération d’interrogation n'est pas fortement typée.</span><span class="sxs-lookup"><span data-stu-id="ab11f-108">The message for the Polling operation is not strongly-typed.</span></span> <span data-ttu-id="ab11f-109">Si vous souhaitez obtenir le message d’interrogation fortement typée, vous devez utiliser le **TypedPolling** opération.</span><span class="sxs-lookup"><span data-stu-id="ab11f-109">If you want to get strongly-typed polling message, you must use the **TypedPolling** operation.</span></span> <span data-ttu-id="ab11f-110">Vous devez également utiliser le **TypedPolling** opération plusieurs opérations d’interrogation dans une application unique.</span><span class="sxs-lookup"><span data-stu-id="ab11f-110">You must also use the **TypedPolling** operation to have multiple polling operations in a single application.</span></span> <span data-ttu-id="ab11f-111">Pour obtenir des instructions sur la façon d’effectuer **TypedPolling** opération, consultez [réception fortement typé reposant sur l’interrogation Messages de modification de données à partir du modèle de Service SQL Server à l’aide de WCF](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-sql-messages-with-wcf-service.md).</span><span class="sxs-lookup"><span data-stu-id="ab11f-111">For instructions on how to perform **TypedPolling** operation, see [Receive Strongly-typed Polling-based Data-changed Messages from SQL Server Using WCF Service Model](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-sql-messages-with-wcf-service.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ab11f-112">Si vous souhaitez disposer d’interrogation plus d’une opération dans une application unique, vous devez spécifier un **InboundID** propriété de connexion dans le cadre de la connexion URI pour le rendre unique.</span><span class="sxs-lookup"><span data-stu-id="ab11f-112">If you want to have more than one polling operation in a single application, you must specify an **InboundID** connection property as part of the connection URI to make it unique.</span></span> <span data-ttu-id="ab11f-113">L’ID entrant que vous spécifiez est ajouté à l’espace de noms d’opération pour le rendre unique.</span><span class="sxs-lookup"><span data-stu-id="ab11f-113">The inbound ID you specify is added to the operation namespace to make it unique.</span></span>  
  
## <a name="how-this-topic-demonstrates-polling"></a><span data-ttu-id="ab11f-114">Comment cette rubrique illustre l’interrogation</span><span class="sxs-lookup"><span data-stu-id="ab11f-114">How This Topic Demonstrates Polling</span></span>  
 <span data-ttu-id="ab11f-115">Dans cette rubrique, pour illustrer comment le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge la réception de données les messages de modification, créez une application .NET et générer le contrat de service WCF pour le **d’interrogation** opération.</span><span class="sxs-lookup"><span data-stu-id="ab11f-115">In this topic, to demonstrate how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports receiving data change messages, create a .NET application and generate the WCF service contract for the **Polling** operation.</span></span> <span data-ttu-id="ab11f-116">Si vous souhaitez spécifier l’interrogation associées des propriétés de liaison lors de la génération du contrat de service WCF, spécifiez la **PolledDataAvailableStatement** en tant que :</span><span class="sxs-lookup"><span data-stu-id="ab11f-116">If you want to specify the polling related binding properties while generating the WCF service contract, specify the **PolledDataAvailableStatement** as:</span></span>  
  
```  
SELECT COUNT(*) FROM Employee  
```  
  
 <span data-ttu-id="ab11f-117">Le **PolledDataAvailableStatement** doit retourner un jeu de résultats avec la première cellule contenant une valeur positive.</span><span class="sxs-lookup"><span data-stu-id="ab11f-117">The **PolledDataAvailableStatement** must return a result set with the first cell containing a positive value.</span></span> <span data-ttu-id="ab11f-118">Si la première cellule ne contient pas une valeur positive, l’adaptateur n’exécute pas l’instruction d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="ab11f-118">If the first cell does not contain a positive value, the adapter does not execute the polling statement.</span></span>  
  
 <span data-ttu-id="ab11f-119">Dans le cadre de l’instruction d’interrogation, effectuez les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ab11f-119">As part of the polling statement, perform the following operations:</span></span>  
  
1.  <span data-ttu-id="ab11f-120">Sélectionnez toutes les lignes de la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ab11f-120">Select all the rows from the Employee table.</span></span>  
  
2.  <span data-ttu-id="ab11f-121">Exécuter une procédure stockée (MOVE_EMP_DATA) pour déplacer tous les enregistrements de la table Employee pour une table HistoriqueEmployé.</span><span class="sxs-lookup"><span data-stu-id="ab11f-121">Execute a stored procedure (MOVE_EMP_DATA) to move all the records from the Employee table to an EmployeeHistory table.</span></span>  
  
3.  <span data-ttu-id="ab11f-122">Exécuter une procédure stockée (ADD_EMP_DETAILS) pour ajouter un nouvel enregistrement dans la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ab11f-122">Execute a stored procedure (ADD_EMP_DETAILS) to add a new record to the Employee table.</span></span> <span data-ttu-id="ab11f-123">Cette procédure prend le nom de l’employé, désignation et salaire en tant que paramètres.</span><span class="sxs-lookup"><span data-stu-id="ab11f-123">This procedure takes the employee name, designation, and salary as parameters.</span></span>  
  
 <span data-ttu-id="ab11f-124">Pour effectuer ces opérations, vous devez spécifier les informations suivantes pour le **PollingStatement** propriété de liaison :</span><span class="sxs-lookup"><span data-stu-id="ab11f-124">To perform these operations, you must specify the following for the **PollingStatement** binding property:</span></span>  
  
```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  
  
 <span data-ttu-id="ab11f-125">Après l’exécution de l’instruction d’interrogation, tous les enregistrements de la table Employee sont sélectionnés et la réception du message à partir de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ab11f-125">After the polling statement is executed, all the records from the Employee table are selected and the message from SQL Server is received.</span></span> <span data-ttu-id="ab11f-126">Après l’exécution de la procédure stockée de MOVE_EMP_DATA par l’adaptateur, tous les enregistrements sont déplacés vers la table HistoriqueEmployé.</span><span class="sxs-lookup"><span data-stu-id="ab11f-126">After the MOVE_EMP_DATA stored procedure is executed by the adapter, all the records are moved to the EmployeeHistory table.</span></span> <span data-ttu-id="ab11f-127">Ensuite, la procédure stockée de ADD_EMP_DETAILS est exécutée pour ajouter un nouvel enregistrement dans la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ab11f-127">Then, the ADD_EMP_DETAILS stored procedure is executed to add a new record to the Employee table.</span></span> <span data-ttu-id="ab11f-128">L’exécution de l’interrogation suivante retourne uniquement un seul enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ab11f-128">The next polling execution will only return a single record.</span></span> <span data-ttu-id="ab11f-129">Ce cycle se poursuit jusqu'à la fermeture de l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="ab11f-129">This cycle continues until you close the service host.</span></span>  
  
## <a name="configuring-a-polling-query-with-the-sql-adapter-binding-properties"></a><span data-ttu-id="ab11f-130">Configuration d’une requête d’interrogation avec l’adaptateur SQL propriétés de liaison</span><span class="sxs-lookup"><span data-stu-id="ab11f-130">Configuring a Polling Query with the SQL Adapter Binding Properties</span></span>  
 <span data-ttu-id="ab11f-131">Le tableau suivant récapitule les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] propriétés que vous utilisez pour configurer l’adaptateur pour recevoir des messages de modification de données de liaison.</span><span class="sxs-lookup"><span data-stu-id="ab11f-131">The following table summarizes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding properties that you use to configure the adapter to receive data-change messages.</span></span> <span data-ttu-id="ab11f-132">Vous devez spécifier ces propriétés de liaison dans le cadre de l’application .NET pour l’interrogation.</span><span class="sxs-lookup"><span data-stu-id="ab11f-132">You must specify these binding properties as part of the .NET application for polling.</span></span>  
  
|<span data-ttu-id="ab11f-133">Propriété de liaison</span><span class="sxs-lookup"><span data-stu-id="ab11f-133">Binding Property</span></span>|<span data-ttu-id="ab11f-134"> Description</span><span class="sxs-lookup"><span data-stu-id="ab11f-134">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="ab11f-135">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="ab11f-135">**InboundOperationType**</span></span>|<span data-ttu-id="ab11f-136">Spécifie si vous souhaitez effectuer **d’interrogation**, **TypedPolling**, ou **Notification** opération entrante.</span><span class="sxs-lookup"><span data-stu-id="ab11f-136">Specifies whether you want to perform **Polling**, **TypedPolling**, or **Notification** inbound operation.</span></span> <span data-ttu-id="ab11f-137">Valeur par défaut est **d’interrogation**.</span><span class="sxs-lookup"><span data-stu-id="ab11f-137">Default is **Polling**.</span></span>|  
|<span data-ttu-id="ab11f-138">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="ab11f-138">**PolledDataAvailableStatement**</span></span>|<span data-ttu-id="ab11f-139">Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ab11f-139">Specifies the SQL statement that the adapter executes to determine whether any data is available for polling.</span></span> <span data-ttu-id="ab11f-140">L’instruction SQL doit retourner un jeu de résultats composé de lignes et de colonnes.</span><span class="sxs-lookup"><span data-stu-id="ab11f-140">The SQL statement must return a result set consisting of rows and columns.</span></span> <span data-ttu-id="ab11f-141">Uniquement si une ligne est disponible, l’instruction SQL spécifiée pour le **PollingStatement** liaison de la propriété sera exécutée.</span><span class="sxs-lookup"><span data-stu-id="ab11f-141">Only if a row is available, the SQL statement specified for the **PollingStatement** binding property will be executed.</span></span>|  
|<span data-ttu-id="ab11f-142">**PollingIntervalInSeconds**</span><span class="sxs-lookup"><span data-stu-id="ab11f-142">**PollingIntervalInSeconds**</span></span>|<span data-ttu-id="ab11f-143">Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="ab11f-143">Specifies the interval, in seconds, at which the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="ab11f-144">La valeur par défaut est 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="ab11f-144">The default is 30 seconds.</span></span> <span data-ttu-id="ab11f-145">L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives.</span><span class="sxs-lookup"><span data-stu-id="ab11f-145">The polling interval determines the time interval between successive polls.</span></span> <span data-ttu-id="ab11f-146">Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur attend que le temps restant dans l’intervalle.</span><span class="sxs-lookup"><span data-stu-id="ab11f-146">If the statement is executed within the specified interval, the adapter waits for the remaining time in the interval.</span></span>|  
|<span data-ttu-id="ab11f-147">**PollingStatement**</span><span class="sxs-lookup"><span data-stu-id="ab11f-147">**PollingStatement**</span></span>|<span data-ttu-id="ab11f-148">Spécifie l’instruction SQL pour interroger la table de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ab11f-148">Specifies the SQL statement to poll the SQL Server database table.</span></span> <span data-ttu-id="ab11f-149">Vous pouvez spécifier une instruction SELECT simple ou une procédure stockée pour l’instruction d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="ab11f-149">You can specify a simple SELECT statement or a stored procedure for the polling statement.</span></span> <span data-ttu-id="ab11f-150">La valeur par défaut est null.</span><span class="sxs-lookup"><span data-stu-id="ab11f-150">The default is null.</span></span> <span data-ttu-id="ab11f-151">Vous devez spécifier une valeur pour **PollingStatement** pour activer l’interrogation.</span><span class="sxs-lookup"><span data-stu-id="ab11f-151">You must specify a value for **PollingStatement** to enable polling.</span></span> <span data-ttu-id="ab11f-152">L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="ab11f-152">The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="ab11f-153">Vous pouvez spécifier n’importe quel nombre d’instructions SQL séparées par un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="ab11f-153">You can specify any number of SQL statements separated by a semi-colon.</span></span>|  
|<span data-ttu-id="ab11f-154">**PollWhileDataFound**</span><span class="sxs-lookup"><span data-stu-id="ab11f-154">**PollWhileDataFound**</span></span>|<span data-ttu-id="ab11f-155">Spécifie si le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignore l’intervalle d’interrogation et exécute en permanence de l’instruction SQL spécifiée pour le **PolledDataAvailableStatement** liaison de propriété, si les données sont disponibles dans la table interrogée.</span><span class="sxs-lookup"><span data-stu-id="ab11f-155">Specifies whether the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignores the polling interval and continuously executes the SQL statement specified for the **PolledDataAvailableStatement** binding property, if data is available in the table being polled.</span></span> <span data-ttu-id="ab11f-156">Si aucune donnée n’est disponible dans la table, l’adaptateur revient à exécuter l’instruction SQL à l’intervalle d’interrogation spécifié.</span><span class="sxs-lookup"><span data-stu-id="ab11f-156">If no data is available in the table, the adapter reverts to execute the SQL statement at the specified polling interval.</span></span> <span data-ttu-id="ab11f-157">Valeur par défaut est **false**.</span><span class="sxs-lookup"><span data-stu-id="ab11f-157">Default is **false**.</span></span>|  
  
 <span data-ttu-id="ab11f-158">Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ab11f-158">For a more complete description of these properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="ab11f-159">Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour interroger le SQL Server, poursuivre la lecture.</span><span class="sxs-lookup"><span data-stu-id="ab11f-159">For a complete description of how to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to poll SQL Server, read further.</span></span>  
  
## <a name="configuring-polling-in-the-wcf-service-model"></a><span data-ttu-id="ab11f-160">Configuration d’interrogation dans le modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="ab11f-160">Configuring Polling in the WCF Service Model</span></span>  
 <span data-ttu-id="ab11f-161">Pour recevoir le **d’interrogation** opération lorsque vous utilisez le modèle de service WCF, vous devez :</span><span class="sxs-lookup"><span data-stu-id="ab11f-161">To receive the **Polling** operation when you use the WCF service model, you must:</span></span>  
  
1.  <span data-ttu-id="ab11f-162">Générer un contrat de service WCF (interface) pour le **d’interrogation** opération à partir des métadonnées exposées par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ab11f-162">Generate a WCF service contract (interface) for the **Polling** operation from the metadata exposed by the adapter.</span></span> <span data-ttu-id="ab11f-163">Pour ce faire, vous pouvez utiliser la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab11f-163">To do this, you could use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span>  
  
2.  <span data-ttu-id="ab11f-164">Implémenter un service WCF à partir de cette interface.</span><span class="sxs-lookup"><span data-stu-id="ab11f-164">Implement a WCF service from this interface.</span></span>  
  
3.  <span data-ttu-id="ab11f-165">Héberger ce service WCF à l’aide d’un hôte de service (**System.ServiceModel.ServiceHost**).</span><span class="sxs-lookup"><span data-stu-id="ab11f-165">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="ab11f-166">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="ab11f-166">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="ab11f-167">Les exemples de cette rubrique interrogent la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ab11f-167">The examples in this topic poll the Employee table.</span></span> <span data-ttu-id="ab11f-168">L’exemple utilise également les MOVE_EMP_DATA ADD_EMP_DETAILS procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="ab11f-168">The example also uses the MOVE_EMP_DATA and ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="ab11f-169">Un script pour générer ces artefacts est fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="ab11f-169">A script to generate these artifacts is supplied with the samples.</span></span> <span data-ttu-id="ab11f-170">Pour plus d’informations sur les exemples, consultez [exemples de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="ab11f-170">For more information about the samples, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span></span> <span data-ttu-id="ab11f-171">Un exemple, **Polling_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="ab11f-171">A sample, **Polling_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="ab11f-172">Le contrat de Service WCF et la classe</span><span class="sxs-lookup"><span data-stu-id="ab11f-172">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="ab11f-173">Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un contrat de service WCF (interface) et la prise en charge des classes pour la **d’interrogation** opération.</span><span class="sxs-lookup"><span data-stu-id="ab11f-173">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **Polling** operation.</span></span> <span data-ttu-id="ab11f-174">Pour plus d’informations sur la génération d’un contrat de service WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="ab11f-174">For more information about generating a WCF service contract, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="ab11f-175">Le contrat de Service WCF (Interface)</span><span class="sxs-lookup"><span data-stu-id="ab11f-175">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="ab11f-176">Le code suivant illustre le contrat de service WCF (interface) généré pour le **d’interrogation** opération.</span><span class="sxs-lookup"><span data-stu-id="ab11f-176">The following code shows the WCF service contract (interface) generated for the **Polling** operation.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/", ConfigurationName="PollingOperation")]  
public interface PollingOperation {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/Polling/) of message Polling  
    // does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="Polling")]  
    [System.ServiceModel.XmlSerializerFormatAttribute()]  
    void Polling(Polling request);  
}  
```  
  
### <a name="the-message-contracts"></a><span data-ttu-id="ab11f-177">Les contrats de Message</span><span class="sxs-lookup"><span data-stu-id="ab11f-177">The Message Contracts</span></span>  
 <span data-ttu-id="ab11f-178">L’espace de noms de contrat de message est modifié par la **InboundID** paramètre dans l’URI, s’il est spécifié de connexion.</span><span class="sxs-lookup"><span data-stu-id="ab11f-178">The message contract namespace is modified by the **InboundID** parameter in the connection URI, if specified.</span></span> <span data-ttu-id="ab11f-179">Dans cet exemple, vous n’avez pas spécifié un ID de trafic entrant dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="ab11f-179">In this example, you did not specify an inbound ID in the connection URI.</span></span> <span data-ttu-id="ab11f-180">Le message de requête retourne un jeu de données.</span><span class="sxs-lookup"><span data-stu-id="ab11f-180">The request message returns a DataSet.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Polling", WrapperNamespace="http://schemas.microsoft.com/Sql/2008/05/Polling/", IsWrapped=true)]  
public partial class Polling {  
  
[System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/Polling/", Order=0)]  
    [System.Xml.Serialization.XmlArrayAttribute(IsNullable=true)]  
    [System.Xml.Serialization.XmlArrayItemAttribute("DataSet", Namespace="http://schemas.datacontract.org/2004/07/System.Data", IsNullable=false)]  
    public System.Data.DataSet[] PolledData;  
  
    public Polling() {  
    }  
  
    public Polling(System.Data.DataSet[] PolledData) {  
        this.PolledData = PolledData;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a><span data-ttu-id="ab11f-181">Classe de Service WCF</span><span class="sxs-lookup"><span data-stu-id="ab11f-181">WCF Service Class</span></span>  
 <span data-ttu-id="ab11f-182">Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également un fichier qui a un stub pour la classe de service WCF implémenté le contrat de service (interface).</span><span class="sxs-lookup"><span data-stu-id="ab11f-182">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="ab11f-183">Le nom du fichier est SqlAdapterBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="ab11f-183">The name of the file is SqlAdapterBindingService.cs.</span></span> <span data-ttu-id="ab11f-184">Vous pouvez insérer la logique pour traiter les **d’interrogation** opération directement dans cette classe.</span><span class="sxs-lookup"><span data-stu-id="ab11f-184">You can insert the logic to process the **Polling** operation directly into this class.</span></span> <span data-ttu-id="ab11f-185">Le code suivant illustre la classe de service WCF générée par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab11f-185">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
```  
namespace SqlAdapterBindingNamespace {  
  
    public class SqlAdapterBindingService : PollingOperation {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/Polling/) of message Polling   
        // does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
        public virtual void Polling(Polling request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-inbound-messages-for-polling-operation"></a><span data-ttu-id="ab11f-186">Réception des Messages entrants pour l’opération d’interrogation</span><span class="sxs-lookup"><span data-stu-id="ab11f-186">Receiving Inbound Messages for Polling Operation</span></span>  
 <span data-ttu-id="ab11f-187">Cette section fournit des instructions sur la façon d’écrire une application .NET pour recevoir des messages entrants d’interrogation à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab11f-187">This section provides instructions on how to write a .NET application to receive inbound polling messages using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
#### <a name="to-receive-polling-messages-from-the-sql-adapter"></a><span data-ttu-id="ab11f-188">Pour recevoir des messages de l’interrogation de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="ab11f-188">To receive polling messages from the SQL adapter</span></span>  
  
1.  <span data-ttu-id="ab11f-189">Utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer un contrat de service WCF (interface) et des classes d’assistance pour le **d’interrogation** opération.</span><span class="sxs-lookup"><span data-stu-id="ab11f-189">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **Polling** operation.</span></span> <span data-ttu-id="ab11f-190">Pour plus d’informations, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="ab11f-190">For more information, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span> <span data-ttu-id="ab11f-191">Vous pouvez éventuellement spécifier les propriétés de liaison lors de la génération les classes d’assistance et de contrat de service.</span><span class="sxs-lookup"><span data-stu-id="ab11f-191">You can optionally specify the binding properties while generating the service contract and helper classes.</span></span> <span data-ttu-id="ab11f-192">Cela garantit qu’ils sont correctement définies dans le fichier de configuration généré.</span><span class="sxs-lookup"><span data-stu-id="ab11f-192">This guarantees that they are properly set in the generated configuration file.</span></span>  
  
2.  <span data-ttu-id="ab11f-193">Implémenter un service WCF à partir de l’interface et assistance des classes générées à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="ab11f-193">Implement a WCF service from the interface and helper classes generated in step 1.</span></span> <span data-ttu-id="ab11f-194">Le **d’interrogation** méthode de cette classe peut lever une exception pour annuler la transaction d’interrogation, si une erreur est rencontrée, le traitement des données reçues à partir de la **d’interrogation** opération ; dans le cas contraire, la méthode ne ne renvoie rien.</span><span class="sxs-lookup"><span data-stu-id="ab11f-194">The **Polling** method of this class can throw an exception to abort the polling transaction, if an error is encountered processing the data received from the **Polling** operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="ab11f-195">Vous devez attribuer la classe de service WCF comme suit :</span><span class="sxs-lookup"><span data-stu-id="ab11f-195">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     <span data-ttu-id="ab11f-196">Dans le **d’interrogation** (méthode), vous pouvez directement implémenter votre logique d’application.</span><span class="sxs-lookup"><span data-stu-id="ab11f-196">Within the **Polling** method, you can implement your application logic directly.</span></span> <span data-ttu-id="ab11f-197">Cette classe peut être trouvée dans SqlAdapterBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="ab11f-197">This class can be found in SqlAdapterBindingService.cs.</span></span> <span data-ttu-id="ab11f-198">Ce code dans cet exemple montre comment des classes le **SqlAdapterBindingService** classe.</span><span class="sxs-lookup"><span data-stu-id="ab11f-198">This code in this example sub-classes the **SqlAdapterBindingService** class.</span></span> <span data-ttu-id="ab11f-199">Dans ce code, le message d’interrogation reçu en tant qu’un jeu de données est écrit dans la console.</span><span class="sxs-lookup"><span data-stu-id="ab11f-199">In this code, the polling message received as a DataSet is written to the console.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
    {  
  
    public override void Polling(Polling request)  
    {  
        Console.WriteLine("\nNew Polling Records Received");  
        Console.WriteLine("*************************************************");  
        DataSet[] dataArray = request.PolledData;  
        foreach (DataTable tab in dataArray[0].Tables)  
        {  
            foreach (DataRow row in tab.Rows)  
            {  
                for (int i = 0; i < tab.Columns.Count; i++)  
                {  
                    Console.WriteLine(row[i]);  
                }  
            }  
        }  
        Console.WriteLine("*************************************************");  
        Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="ab11f-200">Étant donné que le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] n’accepte pas les informations d’identification dans le cadre de l’URI de connexion, vous devez implémenter la classe suivante pour transmettre les informations d’identification pour la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ab11f-200">Because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not accept credentials as part of the connection URI, you must implement the following class to pass credentials for the SQL Server database.</span></span> <span data-ttu-id="ab11f-201">Dans la dernière partie de l’application, vous serez instancier cette classe à transmettre les informations d’identification SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ab11f-201">In the latter part of the application, you will instantiate this class to pass on the SQL Server credentials.</span></span>  
  
    ```  
    class PollingCredentials : ClientCredentials, IServiceBehavior  
    {  
        public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
        {  
            bindingParameters.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        protected override ClientCredentials CloneCore()  
        {  
            ClientCredentials clone = new PollingCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="ab11f-202">Créer un **SqlAdapterBinding** et configurer l’opération d’interrogation en spécifiant les propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="ab11f-202">Create a **SqlAdapterBinding** and configure the polling operation by specifying the binding properties.</span></span> <span data-ttu-id="ab11f-203">Ce faire, vous pouvez soit explicitement dans le code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="ab11f-203">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="ab11f-204">Au minimum, vous devez spécifier le **InboundOperationType**, **PolledDataAvailableStatement**, et **PollingStatement**.</span><span class="sxs-lookup"><span data-stu-id="ab11f-204">At a minimum, you must specify the **InboundOperationType**, **PolledDataAvailableStatement**, and **PollingStatement**.</span></span>  
  
    ```  
    SqlAdapterBinding binding = new SqlAdapterBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
    binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
    ```  
  
5.  <span data-ttu-id="ab11f-205">Spécifiez les informations d’identification de la base de données SQL Server en instanciant le **PollingCredentials** classe que vous avez créé à l’étape 3.</span><span class="sxs-lookup"><span data-stu-id="ab11f-205">Specify SQL Server database credentials by instantiating the **PollingCredentials** class you created in Step 3.</span></span>  
  
    ```  
    PollingCredentials credentials = new PollingCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
    ```  
  
6.  <span data-ttu-id="ab11f-206">Créez une instance du service WCF créé à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="ab11f-206">Create an instance of the WCF service created in step 2.</span></span>  
  
    ```  
    // create service instance  
    PollingService service = new PollingService();  
    ```  
  
7.  <span data-ttu-id="ab11f-207">Créez une instance de **System.ServiceModel.ServiceHost** à l’aide du service WCF et l’URI de connexion de base.</span><span class="sxs-lookup"><span data-stu-id="ab11f-207">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="ab11f-208">L’URI de la connexion de base ne peut pas contenir l’ID d’entrée, s’il est spécifié.</span><span class="sxs-lookup"><span data-stu-id="ab11f-208">The base connection URI cannot contain the inbound ID, if specified.</span></span> <span data-ttu-id="ab11f-209">Vous devez également spécifier les informations d’identification ici.</span><span class="sxs-lookup"><span data-stu-id="ab11f-209">You should also specify the credentials here.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
8.  <span data-ttu-id="ab11f-210">Ajouter un point de terminaison de service à l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="ab11f-210">Add a service endpoint to the service host.</span></span> <span data-ttu-id="ab11f-211">Pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="ab11f-211">To do this:</span></span>  
  
    -   <span data-ttu-id="ab11f-212">Utilisez la liaison créée à l’étape 4.</span><span class="sxs-lookup"><span data-stu-id="ab11f-212">Use the binding created in step 4.</span></span>  
  
    -   <span data-ttu-id="ab11f-213">Spécifiez une URI qui contient les informations d’identification de connexion et, si nécessaire, un ID d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ab11f-213">Specify a connection URI that contains credentials and, if required, an inbound ID.</span></span>  
  
    -   <span data-ttu-id="ab11f-214">Spécifiez le contrat en tant que « PollingOperation ».</span><span class="sxs-lookup"><span data-stu-id="ab11f-214">Specify the contract as "PollingOperation".</span></span>  
  
    ```  
    // Add service endpoint: be sure to specify PollingOperation as the contract  
    Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
    serviceHost.AddServiceEndpoint("PollingOperation", binding, ConnectionUri);  
    ```  
  
9. <span data-ttu-id="ab11f-215">Pour recevoir les données d’interrogation, ouvrez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="ab11f-215">To receive polling data, open the service host.</span></span> <span data-ttu-id="ab11f-216">L’adaptateur retourne les données chaque fois que la requête retourne un jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="ab11f-216">The adapter will return data whenever the query returns a result set.</span></span>  
  
    ```  
    // Open the service host to begin polling  
    serviceHost.Open();  
    ```  
  
10. <span data-ttu-id="ab11f-217">Pour mettre fin à l’interrogation, fermez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="ab11f-217">To terminate polling, close the service host.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ab11f-218">La carte va continuer à interroger jusqu'à ce que l’hôte de service est fermé.</span><span class="sxs-lookup"><span data-stu-id="ab11f-218">The adapter will continue to poll until the service host is closed.</span></span>  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a><span data-ttu-id="ab11f-219">Exemple</span><span class="sxs-lookup"><span data-stu-id="ab11f-219">Example</span></span>  
 <span data-ttu-id="ab11f-220">L’exemple suivant montre une requête d’interrogation qui s’exécute à la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ab11f-220">The following example shows a polling query that executes the Employee table.</span></span> <span data-ttu-id="ab11f-221">L’instruction d’interrogation effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="ab11f-221">The polling statement performs the following tasks:</span></span>  
  
1.  <span data-ttu-id="ab11f-222">Sélectionne tous les enregistrements de la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ab11f-222">Selects all the records from the Employee table.</span></span>  
  
2.  <span data-ttu-id="ab11f-223">Exécute la procédure MOVE_EMP_DATA stockées pour déplacer tous les enregistrements à partir de la table Employee à HistoriqueEmployé table.</span><span class="sxs-lookup"><span data-stu-id="ab11f-223">Executes the MOVE_EMP_DATA stored procedure to move all records from Employee table to EmployeeHistory table.</span></span>  
  
3.  <span data-ttu-id="ab11f-224">Exécute la procédure stockée de ADD_EMP_DETAILS pour ajouter un enregistrement unique dans la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ab11f-224">Executes the ADD_EMP_DETAILS stored procedure to add a single record to the Employee table.</span></span>  
  
 <span data-ttu-id="ab11f-225">Le premier message d’interrogation contiendra tous les enregistrements de la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ab11f-225">The first polling message will contain all the records from the Employee table.</span></span> <span data-ttu-id="ab11f-226">Les messages suivants d’interrogation contiendra uniquement le dernier enregistrement inséré par la procédure stockée de ADD_EMP_DETAILS.</span><span class="sxs-lookup"><span data-stu-id="ab11f-226">The subsequent polling messages will contain only the last record inserted by the ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="ab11f-227">La carte continuera d’interroger jusqu'à ce que vous fermez l’hôte de service en appuyant sur `<RETURN>`.</span><span class="sxs-lookup"><span data-stu-id="ab11f-227">The adapter will continue to poll until you close the service host by pressing `<RETURN>`.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
using Microsoft.Adapters.Sql;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Collections.ObjectModel;  
using System.Data;  
  
namespace Polling_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
    {  
  
        public override void Polling(Polling request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            DataSet[] dataArray = request.PolledData;  
            foreach (DataTable tab in dataArray[0].Tables)  
            {  
                foreach (DataRow row in tab.Rows)  
                {  
                    for (int i = 0; i < tab.Columns.Count; i++)  
                    {  
                        Console.WriteLine(row[i]);  
                    }  
                }  
            }  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  
  
    class PollingCredentials : ClientCredentials, IServiceBehavior  
    {  
        public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
        {  
            bindingParameters.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        protected override ClientCredentials CloneCore()  
        {  
            ClientCredentials clone = new PollingCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost serviceHost = null;  
            try  
            {  
                Console.WriteLine("Sample started...");  
                Console.WriteLine("Press any key to start polling...");  
                Console.ReadLine();  
  
                SqlAdapterBinding binding = new SqlAdapterBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
                binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
                Console.WriteLine("Binding properties assigned...");  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId (if any) that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // a query_string (InboundID); otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
  
                PollingCredentials credentials = new PollingCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                Console.WriteLine("Opening service host...");  
                PollingService service = new PollingService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("PollingOperation", binding, ConnectionUri);  
                serviceHost.Open();  
                Console.WriteLine("Service host opened...");  
                Console.WriteLine("Polling started...");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("Exception :" + e.Message);  
                Console.ReadLine();  
  
                /* If there is an error it will be specified in the inner exception */  
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop polling  
                if (serviceHost.State == CommunicationState.Opened)  
                    serviceHost.Close();  
                else  
                    serviceHost.Abort();  
            }  
        }  
    }  
}  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab11f-228">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab11f-228">See Also</span></span>  
 [<span data-ttu-id="ab11f-229">Interrogation SQL Server à l’aide de l’adaptateur SQL avec le modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="ab11f-229">Poll SQL Server using the SQL Adapter with WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)
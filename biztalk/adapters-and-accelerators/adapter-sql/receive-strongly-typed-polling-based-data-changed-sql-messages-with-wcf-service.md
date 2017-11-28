---
title: "Recevoir des fortement typée d’interrogation de modification de données de Messages à partir de SQL Server à l’aide du modèle de Service WCF | Documents Microsoft"
description: "Utiliser une application .NET pour configurer l’interrogation typée ou interrogation fortement typée à l’aide du Service WCF avec l’adaptateur WCF-SQL dans BizTalk Server"
ms.custom: 
ms.date: 10/09/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b55eda71-1226-43f2-bc2f-e6b35563210b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c616d2a9f10aae5dbf822676174a0de0d4816c19
ms.sourcegitcommit: f9c6ea3c9cfb8a43f765c0d3b8b07dacaa21fc51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2017
---
# <a name="receive-strongly-typed-polling-based-data-changed-messages-from-sql-server-using-wcf-service-model"></a><span data-ttu-id="ecdf6-103">Recevoir des fortement typée d’interrogation de modification de données de Messages à partir de SQL Server à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="ecdf6-103">Receive Strongly-typed Polling-based Data-changed Messages from SQL Server Using WCF Service Model</span></span>
<span data-ttu-id="ecdf6-104">Vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des messages de l’interrogation fortement typée à partir de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-104">You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive strongly-typed polling messages from SQL Server.</span></span> <span data-ttu-id="ecdf6-105">Vous pouvez spécifier une instruction d’interrogation de l’adaptateur s’exécute pour interroger la base de données.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-105">You can specify a polling statement that the adapter executes to poll the database.</span></span> <span data-ttu-id="ecdf6-106">L’instruction d’interrogation peut être une instruction SELECT ou une procédure stockée qui retourne un jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-106">The polling statement can be a SELECT statement or a stored procedure that returns a result set.</span></span> <span data-ttu-id="ecdf6-107">Vous devez utiliser interrogation fortement typée dans un scénario où vous souhaitez recevoir un jeu de résultats de fortement typée.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-107">You must use strongly-typed polling in a scenario where you want to receive a strongly-typed result set.</span></span> <span data-ttu-id="ecdf6-108">Pour plus d’informations sur la façon dont l’adaptateur prend en charge l’interrogation fortement typée, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span><span class="sxs-lookup"><span data-stu-id="ecdf6-108">For more information on how the adapter supports strongly-typed polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ecdf6-109">Si vous souhaitez disposer d’interrogation plus d’une opération dans une application unique, vous devez spécifier un **InboundID** propriété de connexion dans le cadre de la connexion URI pour le rendre unique.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-109">If you want to have more than one polling operation in a single application, you must specify an **InboundID** connection property as part of the connection URI to make it unique.</span></span> <span data-ttu-id="ecdf6-110">L’ID entrant que vous spécifiez est ajouté à l’espace de noms d’opération pour le rendre unique.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-110">The inbound ID you specify is added to the operation namespace to make it unique.</span></span>  
  
## <a name="how-this-topic-demonstrates-polling"></a><span data-ttu-id="ecdf6-111">Comment cette rubrique illustre l’interrogation</span><span class="sxs-lookup"><span data-stu-id="ecdf6-111">How This Topic Demonstrates Polling</span></span>  
 <span data-ttu-id="ecdf6-112">Dans cette rubrique, pour illustrer comment le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge la réception des données fortement typées les messages de modification, créez une application .NET et générer le contrat de service WCF pour le **TypedPolling** opération.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-112">In this topic, to demonstrate how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports receiving strongly-typed data change messages, create a .NET application and generate the WCF service contract for the **TypedPolling** operation.</span></span> <span data-ttu-id="ecdf6-113">Assurez-vous que vous spécifiez ce qui suit lors de la génération du contrat de service WCF :</span><span class="sxs-lookup"><span data-stu-id="ecdf6-113">Make sure you specify the following while generating the WCF service contract:</span></span>  
  
-   <span data-ttu-id="ecdf6-114">Vous devez spécifier un **InboundID** dans le cadre de l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-114">You must specify an **InboundID** as part of the connection URI.</span></span>  
  
-   <span data-ttu-id="ecdf6-115">Vous devez spécifier une instruction d’interrogation pour le **PollingStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-115">You must specify a polling statement for the **PollingStatement** binding property.</span></span>  
  
 <span data-ttu-id="ecdf6-116">En outre, si vous souhaitez spécifier une autre interrogation liées des propriétés de liaison lors de la génération de la classe proxy, spécifiez la **PolledDataAvailableStatement** en tant que :</span><span class="sxs-lookup"><span data-stu-id="ecdf6-116">Additionally, if you want to specify other polling related binding properties while generating the proxy class, specify the **PolledDataAvailableStatement** as:</span></span>  
  
```  
SELECT COUNT(*) FROM Employee  
```  
  
 <span data-ttu-id="ecdf6-117">Le **PolledDataAvailableStatement** doit retourner un jeu de résultats avec la première cellule contenant une valeur positive.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-117">The **PolledDataAvailableStatement** must return a result set with the first cell containing a positive value.</span></span> <span data-ttu-id="ecdf6-118">Si la première cellule ne contient pas une valeur positive, l’adaptateur n’exécute pas l’instruction d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-118">If the first cell does not contain a positive value, the adapter does not execute the polling statement.</span></span>  
  
 <span data-ttu-id="ecdf6-119">Dans le cadre de l’instruction d’interrogation, effectuez les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ecdf6-119">As part of the polling statement, perform the following operations:</span></span>  
  
1.  <span data-ttu-id="ecdf6-120">Sélectionnez toutes les lignes de la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-120">Select all the rows from the Employee table.</span></span>  
  
2.  <span data-ttu-id="ecdf6-121">Exécuter une procédure stockée (MOVE_EMP_DATA) pour déplacer tous les enregistrements de la table Employee pour une table HistoriqueEmployé.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-121">Execute a stored procedure (MOVE_EMP_DATA) to move all the records from the Employee table to an EmployeeHistory table.</span></span>  
  
3.  <span data-ttu-id="ecdf6-122">Exécuter une procédure stockée (ADD_EMP_DETAILS) pour ajouter un nouvel enregistrement dans la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-122">Execute a stored procedure (ADD_EMP_DETAILS) to add a new record to the Employee table.</span></span> <span data-ttu-id="ecdf6-123">Cette procédure prend le nom de l’employé, désignation et salaire en tant que paramètres.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-123">This procedure takes the employee name, designation, and salary as parameters.</span></span>  
  
 <span data-ttu-id="ecdf6-124">Pour effectuer ces opérations, vous devez spécifier les informations suivantes pour le **PollingStatement** propriété de liaison lors de la génération les classes d’assistance et de contrat de service WCF :</span><span class="sxs-lookup"><span data-stu-id="ecdf6-124">To perform these operations, you must specify the following for the **PollingStatement** binding property while generating the WCF service contract and helper classes:</span></span>  
  
```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  
  
 <span data-ttu-id="ecdf6-125">Après l’exécution de l’instruction d’interrogation, tous les enregistrements de la table Employee sont sélectionnés et la réception du message à partir de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-125">After the polling statement is executed, all the records from the Employee table are selected and the message from SQL Server is received.</span></span> <span data-ttu-id="ecdf6-126">Après l’exécution de la procédure stockée de MOVE_EMP_DATA par l’adaptateur, tous les enregistrements sont déplacés vers la table HistoriqueEmployé.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-126">After the MOVE_EMP_DATA stored procedure is executed by the adapter, all the records are moved to the EmployeeHistory table.</span></span> <span data-ttu-id="ecdf6-127">Ensuite, la procédure stockée de ADD_EMP_DETAILS est exécutée pour ajouter un nouvel enregistrement dans la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-127">Then, the ADD_EMP_DETAILS stored procedure is executed to add a new record to the Employee table.</span></span> <span data-ttu-id="ecdf6-128">L’exécution de l’interrogation suivante retourne uniquement un seul enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-128">The next polling execution will only return a single record.</span></span> <span data-ttu-id="ecdf6-129">Ce cycle se poursuit jusqu'à la fermeture de l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-129">This cycle continues until you close the service host.</span></span>  
  
## <a name="configuring-typed-polling-with-the-sql-adapter-binding-properties"></a><span data-ttu-id="ecdf6-130">Configuration d’interrogation typée avec l’adaptateur SQL propriétés de liaison</span><span class="sxs-lookup"><span data-stu-id="ecdf6-130">Configuring Typed Polling with the SQL Adapter Binding Properties</span></span>  
 <span data-ttu-id="ecdf6-131">Le tableau suivant récapitule les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] propriétés que vous utilisez pour configurer l’adaptateur pour recevoir des messages de modification de données de liaison.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-131">The following table summarizes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding properties that you use to configure the adapter to receive data-change messages.</span></span> <span data-ttu-id="ecdf6-132">Autre que le **PollingStatement** propriété de liaison, toutes les autres propriétés de liaison répertoriées dans cette section sont requises lors de l’exécution de l’application .NET.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-132">Other than the **PollingStatement** binding property, all the other binding properties listed in this section are required while running the .NET application.</span></span> <span data-ttu-id="ecdf6-133">Vous devez spécifier le **PollingStatement** propriété de liaison avant de générer le contrat de service WCF **TypedPolling** opération.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-133">You must specify the **PollingStatement** binding property before generating the WCF service contract **TypedPolling** operation.</span></span>  
  
|<span data-ttu-id="ecdf6-134">Propriété de liaison</span><span class="sxs-lookup"><span data-stu-id="ecdf6-134">Binding Property</span></span>|<span data-ttu-id="ecdf6-135"> Description</span><span class="sxs-lookup"><span data-stu-id="ecdf6-135">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="ecdf6-136">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="ecdf6-136">**InboundOperationType**</span></span>|<span data-ttu-id="ecdf6-137">Spécifie si vous souhaitez effectuer **d’interrogation**, **TypedPolling**, ou **Notification** opération entrante.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-137">Specifies whether you want to perform **Polling**, **TypedPolling**, or **Notification** inbound operation.</span></span> <span data-ttu-id="ecdf6-138">Valeur par défaut est **d’interrogation**.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-138">Default is **Polling**.</span></span> <span data-ttu-id="ecdf6-139">Pour recevoir des messages d’interrogation fortement typée, affectez la valeur **TypedPolling**.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-139">To receive strongly-typed polling messages, set this to **TypedPolling**.</span></span>|  
|<span data-ttu-id="ecdf6-140">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="ecdf6-140">**PolledDataAvailableStatement**</span></span>|<span data-ttu-id="ecdf6-141">Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-141">Specifies the SQL statement that the adapter executes to determine whether any data is available for polling.</span></span> <span data-ttu-id="ecdf6-142">L’instruction SQL doit retourner un jeu de résultats composé de lignes et de colonnes.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-142">The SQL statement must return a result set consisting of rows and columns.</span></span> <span data-ttu-id="ecdf6-143">Uniquement si une ligne est disponible, l’instruction SQL spécifiée pour le **PollingStatement** liaison de la propriété sera exécutée.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-143">Only if a row is available, the SQL statement specified for the **PollingStatement** binding property will be executed.</span></span>|  
|<span data-ttu-id="ecdf6-144">**PollingIntervalInSeconds**</span><span class="sxs-lookup"><span data-stu-id="ecdf6-144">**PollingIntervalInSeconds**</span></span>|<span data-ttu-id="ecdf6-145">Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-145">Specifies the interval, in seconds, at which the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="ecdf6-146">La valeur par défaut est 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-146">The default is 30 seconds.</span></span> <span data-ttu-id="ecdf6-147">L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-147">The polling interval determines the time interval between successive polls.</span></span> <span data-ttu-id="ecdf6-148">Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur attend que le temps restant dans l’intervalle.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-148">If the statement is executed within the specified interval, the adapter waits for the remaining time in the interval.</span></span>|  
|<span data-ttu-id="ecdf6-149">**PollingStatement**</span><span class="sxs-lookup"><span data-stu-id="ecdf6-149">**PollingStatement**</span></span>|<span data-ttu-id="ecdf6-150">Spécifie l’instruction SQL pour interroger la table de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-150">Specifies the SQL statement to poll the SQL Server database table.</span></span> <span data-ttu-id="ecdf6-151">Vous pouvez spécifier une instruction SELECT simple ou une procédure stockée pour l’instruction d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-151">You can specify a simple SELECT statement or a stored procedure for the polling statement.</span></span> <span data-ttu-id="ecdf6-152">La valeur par défaut est null.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-152">The default is null.</span></span> <span data-ttu-id="ecdf6-153">Vous devez spécifier une valeur pour **PollingStatement** pour activer l’interrogation.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-153">You must specify a value for **PollingStatement** to enable polling.</span></span> <span data-ttu-id="ecdf6-154">L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-154">The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="ecdf6-155">Vous pouvez spécifier n’importe quel nombre d’instructions SQL séparées par un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-155">You can specify any number of SQL statements separated by a semi-colon.</span></span> <span data-ttu-id="ecdf6-156">**Important :** pour **TypedPolling**, vous devez spécifier cette propriété de liaison avant de générer des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-156">**Important:**  For **TypedPolling**, you must specify this binding property before generating metadata.</span></span>|  
|<span data-ttu-id="ecdf6-157">**PollWhileDataFound**</span><span class="sxs-lookup"><span data-stu-id="ecdf6-157">**PollWhileDataFound**</span></span>|<span data-ttu-id="ecdf6-158">Spécifie si le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignore l’intervalle d’interrogation et exécute en permanence de l’instruction SQL spécifiée pour le **PolledDataAvailableStatement** liaison de propriété, si les données sont disponibles dans la table interrogée.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-158">Specifies whether the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignores the polling interval and continuously executes the SQL statement specified for the **PolledDataAvailableStatement** binding property, if data is available in the table being polled.</span></span> <span data-ttu-id="ecdf6-159">Si aucune donnée n’est disponible dans la table, l’adaptateur revient à exécuter l’instruction SQL à l’intervalle d’interrogation spécifié.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-159">If no data is available in the table, the adapter reverts to execute the SQL statement at the specified polling interval.</span></span> <span data-ttu-id="ecdf6-160">Valeur par défaut est **false**.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-160">Default is **false**.</span></span>|  
  
 <span data-ttu-id="ecdf6-161">Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ecdf6-161">For a more complete description of these properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="ecdf6-162">Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour interroger le SQL Server, poursuivre la lecture.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-162">For a complete description of how to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to poll SQL Server, read further.</span></span>  
  
## <a name="configure-strongly-typed-polling-in-the-wcf-service-model"></a><span data-ttu-id="ecdf6-163">Configurer l’interrogation fortement typée dans le modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="ecdf6-163">Configure Strongly-typed Polling in the WCF Service Model</span></span>  
 <span data-ttu-id="ecdf6-164">Pour recevoir le **d’interrogation** opération lorsque vous utilisez le modèle de service WCF, vous devez :</span><span class="sxs-lookup"><span data-stu-id="ecdf6-164">To receive the **Polling** operation when you use the WCF service model, you must:</span></span>  
  
1.  <span data-ttu-id="ecdf6-165">Générer un contrat de service WCF (interface) pour le **TypedPolling** opération à partir des métadonnées exposées par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-165">Generate a WCF service contract (interface) for the **TypedPolling** operation from the metadata exposed by the adapter.</span></span> <span data-ttu-id="ecdf6-166">Pour ce faire, vous pouvez utiliser la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ecdf6-166">To do this, you could use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span> <span data-ttu-id="ecdf6-167">Lors de la génération du contrat de service WCF pour cet exemple, assurez-vous que :</span><span class="sxs-lookup"><span data-stu-id="ecdf6-167">While generating the WCF service contract for this example, make sure:</span></span>  
  
    -   <span data-ttu-id="ecdf6-168">Vous spécifiez le **InboundID** en tant que **employé**.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-168">You specify the **InboundID** as **Employee**.</span></span>  
  
    -   <span data-ttu-id="ecdf6-169">Vous spécifiez une instruction d’interrogation pour le **PollingStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-169">You specify a polling statement for the **PollingStatement** binding property.</span></span> <span data-ttu-id="ecdf6-170">Pour cet exemple, spécifiez l’instruction d’interrogation en tant que :</span><span class="sxs-lookup"><span data-stu-id="ecdf6-170">For this example, specify the polling statement as:</span></span>  
  
        ```  
        SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000  
        ```  
  
2.  <span data-ttu-id="ecdf6-171">Implémenter un service WCF à partir de cette interface.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-171">Implement a WCF service from this interface.</span></span>  
  
3.  <span data-ttu-id="ecdf6-172">Héberger ce service WCF à l’aide d’un hôte de service (**System.ServiceModel.ServiceHost**).</span><span class="sxs-lookup"><span data-stu-id="ecdf6-172">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="ecdf6-173">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="ecdf6-173">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="ecdf6-174">Les exemples de cette rubrique interrogent la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-174">The examples in this topic poll the Employee table.</span></span> <span data-ttu-id="ecdf6-175">L’exemple utilise également les MOVE_EMP_DATA ADD_EMP_DETAILS procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-175">The example also uses the MOVE_EMP_DATA and ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="ecdf6-176">Un script pour générer ces artefacts est fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-176">A script to generate these artifacts is supplied with the samples.</span></span> <span data-ttu-id="ecdf6-177">Pour plus d’informations sur les exemples, consultez [exemples de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="ecdf6-177">For more information about the samples, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span></span> <span data-ttu-id="ecdf6-178">Un exemple, **TypedPolling_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-178">A sample, **TypedPolling_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="ecdf6-179">Le contrat de Service WCF et la classe</span><span class="sxs-lookup"><span data-stu-id="ecdf6-179">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="ecdf6-180">Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un contrat de service WCF (interface) et la prise en charge des classes pour la **TypedPolling** opération.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-180">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **TypedPolling** operation.</span></span> <span data-ttu-id="ecdf6-181">Pour plus d’informations sur la génération d’un contrat de service WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="ecdf6-181">For more information about generating a WCF service contract, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="ecdf6-182">Le contrat de Service WCF (Interface)</span><span class="sxs-lookup"><span data-stu-id="ecdf6-182">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="ecdf6-183">Le code suivant illustre le contrat de service WCF (interface) généré pour le **TypedPolling** opération.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-183">The following code shows the WCF service contract (interface) generated for the **TypedPolling** operation.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/", ConfigurationName="TypedPolling_Employee")]  
public interface TypedPolling_Employee {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee) of message TypedPolling  
    // does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="TypedPolling")]  
    void TypedPolling(TypedPolling request);  
}  
```  
  
### <a name="the-message-contracts"></a><span data-ttu-id="ecdf6-184">Les contrats de Message</span><span class="sxs-lookup"><span data-stu-id="ecdf6-184">The Message Contracts</span></span>  
 <span data-ttu-id="ecdf6-185">L’espace de noms de contrat de message est modifié par la **InboundID** paramètre dans l’URI, s’il est spécifié de connexion.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-185">The message contract namespace is modified by the **InboundID** parameter in the connection URI, if specified.</span></span> <span data-ttu-id="ecdf6-186">Dans cet exemple, vous avez spécifié l’ID entrant en tant que **employé**.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-186">In this example, you specified the inbound ID as **Employee**.</span></span> <span data-ttu-id="ecdf6-187">Le message de requête retourne un jeu de résultats de fortement typée.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-187">The request message returns a strongly-typed result set.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="TypedPolling", WrapperNamespace="http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee", IsWrapped=true)]  
public partial class TypedPolling {  
  
[System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee", Order=0)]  
    public schemas.microsoft.com.Sql._2008._05.TypedPolling.Employee.TypedPollingResultSet0[] TypedPollingResultSet0;  
  
[System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee", Order=1)]  
    public schemas.microsoft.com.Sql._2008._05.TypedPolling.Employee.TypedPollingResultSet1[] TypedPollingResultSet1;  
  
    public TypedPolling() {  
    }  
  
    public TypedPolling(schemas.microsoft.com.Sql._2008._05.TypedPolling.Employee.TypedPollingResultSet0[] TypedPollingResultSet0, schemas.microsoft.com.Sql._2008._05.TypedPolling.Employee.TypedPollingResultSet1[] TypedPollingResultSet1) {  
        this.TypedPollingResultSet0 = TypedPollingResultSet0;  
        this.TypedPollingResultSet1 = TypedPollingResultSet1;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a><span data-ttu-id="ecdf6-188">Classe de Service WCF</span><span class="sxs-lookup"><span data-stu-id="ecdf6-188">WCF Service Class</span></span>  
 <span data-ttu-id="ecdf6-189">Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également un fichier qui a un stub pour la classe de service WCF implémenté le contrat de service (interface).</span><span class="sxs-lookup"><span data-stu-id="ecdf6-189">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="ecdf6-190">Le nom du fichier est SqlAdapterBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-190">The name of the file is SqlAdapterBindingService.cs.</span></span> <span data-ttu-id="ecdf6-191">Vous pouvez insérer la logique pour traiter les **TypedPolling** opération directement dans cette classe.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-191">You can insert the logic to process the **TypedPolling** operation directly into this class.</span></span> <span data-ttu-id="ecdf6-192">Le code suivant illustre la classe de service WCF générée par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ecdf6-192">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
```  
namespace SqlAdapterBindingNamespace {  
  
    public class SqlAdapterBindingService : TypedPolling_Employee {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee) of message TypedPolling  
        // does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
        public virtual void TypedPolling(TypedPolling request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receive-strongly-typed-inbound-messages-for-polling-operation"></a><span data-ttu-id="ecdf6-193">Réception fortement typée de Messages entrants pour l’opération d’interrogation</span><span class="sxs-lookup"><span data-stu-id="ecdf6-193">Receive Strongly-typed Inbound Messages for Polling Operation</span></span>  
 <span data-ttu-id="ecdf6-194">Cette section fournit des instructions sur la façon d’écrire une application .NET pour recevoir des messages d’interrogation entrant fortement typée à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ecdf6-194">This section provides instructions on how to write a .NET application to receive strongly-typed inbound polling messages using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
1.  <span data-ttu-id="ecdf6-195">Utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer un contrat de service WCF (interface) et des classes d’assistance pour le **TypedPolling** opération.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-195">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **TypedPolling** operation.</span></span> <span data-ttu-id="ecdf6-196">Assurez-vous que vous spécifiez ce qui suit lors de la génération du contrat de service WCF pour cet exemple :</span><span class="sxs-lookup"><span data-stu-id="ecdf6-196">Make sure you specify the following while generating the WCF service contract for this example:</span></span>  
  
    -   <span data-ttu-id="ecdf6-197">Vous devez spécifier le **InboundID** en tant que **employé**.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-197">You must specify the **InboundID** as **Employee**.</span></span>  
  
    -   <span data-ttu-id="ecdf6-198">Vous devez spécifier une instruction d’interrogation pour le **PollingStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-198">You must specify a polling statement for the **PollingStatement** binding property.</span></span> <span data-ttu-id="ecdf6-199">Pour cet exemple, spécifiez l’instruction d’interrogation en tant que :</span><span class="sxs-lookup"><span data-stu-id="ecdf6-199">For this example, specify the polling statement as:</span></span>  
  
        ```  
        SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000  
        ```  
  
     <span data-ttu-id="ecdf6-200">Pour plus d’informations, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="ecdf6-200">For more information, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span> <span data-ttu-id="ecdf6-201">Vous pouvez éventuellement spécifier les propriétés de liaison lors de la génération les classes d’assistance et de contrat de service.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-201">You can optionally specify the binding properties while generating the service contract and helper classes.</span></span> <span data-ttu-id="ecdf6-202">Cela garantit qu’ils sont correctement définies dans le fichier de configuration généré.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-202">This guarantees that they are properly set in the generated configuration file.</span></span>  
  
2.  <span data-ttu-id="ecdf6-203">Implémenter un service WCF à partir de l’interface et assistance des classes générées à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-203">Implement a WCF service from the interface and helper classes generated in step 1.</span></span> <span data-ttu-id="ecdf6-204">Le **TypedPolling** méthode de cette classe peut lever une exception pour annuler la transaction d’interrogation, si une erreur est rencontrée, le traitement des données reçues à partir de la **TypedPolling** opération ; sinon le méthode ne retourne rien.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-204">The **TypedPolling** method of this class can throw an exception to abort the polling transaction, if an error is encountered processing the data received from the **TypedPolling** operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="ecdf6-205">Vous devez attribuer la classe de service WCF comme suit :</span><span class="sxs-lookup"><span data-stu-id="ecdf6-205">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     <span data-ttu-id="ecdf6-206">Dans le **TypedPolling** (méthode), vous pouvez directement implémenter votre logique d’application.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-206">Within the **TypedPolling** method, you can implement your application logic directly.</span></span> <span data-ttu-id="ecdf6-207">Cette classe peut être trouvée dans SqlAdapterBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-207">This class can be found in SqlAdapterBindingService.cs.</span></span> <span data-ttu-id="ecdf6-208">Ce code dans cet exemple montre comment des classes le **SqlAdapterBindingService** classe.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-208">This code in this example sub-classes the **SqlAdapterBindingService** class.</span></span> <span data-ttu-id="ecdf6-209">Dans ce code, le message d’interrogation reçu en tant qu’un jeu de résultats de fortement typée est écrite dans la console.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-209">In this code, the polling message received as a strongly-typed result set is written to the console.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
    {  
        public override void TypedPolling(TypedPolling request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Employee ID\tName\tDesignation\tSalary");  
  
            for (int i = 0; i < request.TypedPollingResultSet0.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.TypedPollingResultSet0[i].Employee_ID,  
                request.TypedPollingResultSet0[i].Name,  
                request.TypedPollingResultSet0[i].Designation,  
                request.TypedPollingResultSet0[i].Salary);  
            }  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="ecdf6-210">Étant donné que le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] n’accepte pas les informations d’identification dans le cadre de l’URI de connexion, vous devez implémenter la classe suivante pour transmettre les informations d’identification pour la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-210">Because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not accept credentials as part of the connection URI, you must implement the following class to pass credentials for the SQL Server database.</span></span> <span data-ttu-id="ecdf6-211">Dans la dernière partie de l’application, vous serez instancier cette classe à transmettre les informations d’identification SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-211">In the latter part of the application, you will instantiate this class to pass on the SQL Server credentials.</span></span>  
  
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
  
4.  <span data-ttu-id="ecdf6-212">Créer un **SqlAdapterBinding** et configurer l’opération d’interrogation en spécifiant les propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-212">Create a **SqlAdapterBinding** and configure the polling operation by specifying the binding properties.</span></span> <span data-ttu-id="ecdf6-213">Ce faire, vous pouvez soit explicitement dans le code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-213">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="ecdf6-214">Au minimum, vous devez spécifier le **InboundOperationType**, **PolledDataAvailableStatement**, et **PollingStatement**.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-214">At a minimum, you must specify the **InboundOperationType**, **PolledDataAvailableStatement**, and **PollingStatement**.</span></span>  
  
    ```  
    SqlAdapterBinding binding = new SqlAdapterBinding();  
    binding.InboundOperationType = InboundOperation.TypedPolling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
    binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
    ```  
  
5.  <span data-ttu-id="ecdf6-215">Spécifiez les informations d’identification de la base de données SQL Server en instanciant le **PollingCredentials** classe que vous avez créé à l’étape 3.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-215">Specify SQL Server database credentials by instantiating the **PollingCredentials** class you created in Step 3.</span></span>  
  
    ```  
    PollingCredentials credentials = new PollingCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
    ```  
  
6.  <span data-ttu-id="ecdf6-216">Créez une instance du service WCF créé à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-216">Create an instance of the WCF service created in step 2.</span></span>  
  
    ```  
    // create service instance  
    PollingService service = new PollingService();  
    ```  
  
7.  <span data-ttu-id="ecdf6-217">Créez une instance de **System.ServiceModel.ServiceHost** à l’aide du service WCF et l’URI de connexion de base.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-217">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="ecdf6-218">L’URI de la connexion de base ne peut pas contenir l’ID de trafic entrant.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-218">The base connection URI cannot contain the inbound ID.</span></span> <span data-ttu-id="ecdf6-219">Vous devez également spécifier les informations d’identification ici.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-219">You must also specify the credentials here.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
8.  <span data-ttu-id="ecdf6-220">Ajouter un point de terminaison de service à l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-220">Add a service endpoint to the service host.</span></span> <span data-ttu-id="ecdf6-221">Pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="ecdf6-221">To do this:</span></span>  
  
    -   <span data-ttu-id="ecdf6-222">Utilisez la liaison créée à l’étape 4.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-222">Use the binding created in step 4.</span></span>  
  
    -   <span data-ttu-id="ecdf6-223">Spécifiez une URI qui contient les informations d’identification de connexion et, si nécessaire, un ID d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-223">Specify a connection URI that contains credentials and, if required, an inbound ID.</span></span>  
  
    -   <span data-ttu-id="ecdf6-224">Spécifiez le contrat en tant que « TypedPolling_Employee ».</span><span class="sxs-lookup"><span data-stu-id="ecdf6-224">Specify the contract as "TypedPolling_Employee".</span></span>  
  
    ```  
    // Add service endpoint: be sure to specify TypedPolling_Employee as the contract  
    Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?InboundID=Employee");  
    serviceHost.AddServiceEndpoint("TypedPolling_Employee", binding, ConnectionUri);  
    ```  
  
9. <span data-ttu-id="ecdf6-225">Pour recevoir les données d’interrogation, ouvrez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-225">To receive polling data, open the service host.</span></span> <span data-ttu-id="ecdf6-226">L’adaptateur retourne les données chaque fois que la requête retourne un jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-226">The adapter will return data whenever the query returns a result set.</span></span>  
  
    ```  
    // Open the service host to begin polling  
    serviceHost.Open();  
    ```  
  
10. <span data-ttu-id="ecdf6-227">Pour mettre fin à l’interrogation, fermez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-227">To terminate polling, close the service host.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ecdf6-228">La carte va continuer à interroger jusqu'à ce que l’hôte de service est fermé.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-228">The adapter will continue to poll until the service host is closed.</span></span>  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a><span data-ttu-id="ecdf6-229">Exemple</span><span class="sxs-lookup"><span data-stu-id="ecdf6-229">Example</span></span>  
 <span data-ttu-id="ecdf6-230">L’exemple suivant montre une requête d’interrogation qui s’exécute à la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-230">The following example shows a polling query that executes the Employee table.</span></span> <span data-ttu-id="ecdf6-231">L’instruction d’interrogation effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="ecdf6-231">The polling statement performs the following tasks:</span></span>  
  
1.  <span data-ttu-id="ecdf6-232">Sélectionne tous les enregistrements de la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-232">Selects all the records from the Employee table.</span></span>  
  
2.  <span data-ttu-id="ecdf6-233">Exécute la procédure MOVE_EMP_DATA stockées pour déplacer tous les enregistrements à partir de la table Employee à HistoriqueEmployé table.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-233">Executes the MOVE_EMP_DATA stored procedure to move all records from Employee table to EmployeeHistory table.</span></span>  
  
3.  <span data-ttu-id="ecdf6-234">Exécute la procédure stockée de ADD_EMP_DETAILS pour ajouter un enregistrement unique dans la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-234">Executes the ADD_EMP_DETAILS stored procedure to add a single record to the Employee table.</span></span>  
  
 <span data-ttu-id="ecdf6-235">Le premier message d’interrogation contiendra tous les enregistrements de la table Employee.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-235">The first polling message will contain all the records from the Employee table.</span></span> <span data-ttu-id="ecdf6-236">Les messages suivants d’interrogation contiendra uniquement le dernier enregistrement inséré par la procédure stockée de ADD_EMP_DETAILS.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-236">The subsequent polling messages will contain only the last record inserted by the ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="ecdf6-237">La carte continuera d’interroger jusqu'à ce que vous fermez l’hôte de service en appuyant sur `<RETURN>`.</span><span class="sxs-lookup"><span data-stu-id="ecdf6-237">The adapter will continue to poll until you close the service host by pressing `<RETURN>`.</span></span>  
  
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
  
namespace TypedPolling_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
    {  
        public override void TypedPolling(TypedPolling request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Employee ID\tName\tDesignation\tSalary");  
  
            for (int i = 0; i < request.TypedPollingResultSet0.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.TypedPollingResultSet0[i].Employee_ID,  
                request.TypedPollingResultSet0[i].Name,  
                request.TypedPollingResultSet0[i].Designation,  
                request.TypedPollingResultSet0[i].Salary);  
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
                binding.InboundOperationType = InboundOperation.TypedPolling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
                binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
                Console.WriteLine("Binding properties assigned...");  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?InboundId=Employee");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // the InboundID; otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
  
                PollingCredentials credentials = new PollingCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                Console.WriteLine("Opening service host...");  
                PollingService service = new PollingService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("TypedPolling_Employee", binding, ConnectionUri);  
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
  
## <a name="see-also"></a><span data-ttu-id="ecdf6-238">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecdf6-238">See Also</span></span>  
 [<span data-ttu-id="ecdf6-239">Interrogation SQL Server à l’aide de l’adaptateur SQL avec le modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="ecdf6-239">Poll SQL Server using the SQL Adapter with WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)

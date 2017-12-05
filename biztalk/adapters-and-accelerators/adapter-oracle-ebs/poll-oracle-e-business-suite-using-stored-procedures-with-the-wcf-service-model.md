---
title: "Interrogation Oracle E-Business Suite à l’aide de procédures stockées avec le modèle de service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47dcb866-9161-4b28-9481-2761794ce805
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3fb7ebcbccb1f0edb3370176192f55f0db4985a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="poll-oracle-e-business-suite-using-stored-procedures-with-the-wcf-service-model"></a><span data-ttu-id="182e3-102">Interrogation Oracle E-Business Suite à l’aide de procédures stockées avec le modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="182e3-102">Poll Oracle E-Business Suite using stored procedures with the WCF service model</span></span>
<span data-ttu-id="182e3-103">Vous pouvez configurer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des messages de modification de données périodiques interrogent régulièrement la base de données Oracle à l’aide des procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="182e3-103">You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive periodic data-change messages by using stored procedures to periodically poll the Oracle database.</span></span> <span data-ttu-id="182e3-104">Vous pouvez spécifier une procédure stockée en tant qu’une instruction d’interrogation de l’adaptateur s’exécute périodiquement pour interroger la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="182e3-104">You can specify a stored procedure as a polling statement that the adapter executes periodically to poll the Oracle database.</span></span>  
  
 <span data-ttu-id="182e3-105">Pour activer l’interrogation, vous devez spécifier certaines propriétés de liaison comme décrit dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="182e3-105">To enable polling, you must specify certain binding properties as described in this topic.</span></span>  <span data-ttu-id="182e3-106">Pour plus d’informations sur la façon dont l’adaptateur prend en charge d’interrogation, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span><span class="sxs-lookup"><span data-stu-id="182e3-106">For more information about how the adapter supports polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  
  
## <a name="configuring-a-polling-operation-with-oracle-e-business-adapter-binding-properties"></a><span data-ttu-id="182e3-107">Configuration d’une opération d’interrogation avec liaison des propriétés de l’adaptateur Oracle E-Business</span><span class="sxs-lookup"><span data-stu-id="182e3-107">Configuring a Polling Operation with Oracle E-Business Adapter Binding Properties</span></span>  
 <span data-ttu-id="182e3-108">Le tableau suivant récapitule les [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] propriétés que vous utilisez pour configurer l’adaptateur pour recevoir des messages de modification de données de liaison.</span><span class="sxs-lookup"><span data-stu-id="182e3-108">The following table summarizes the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding properties that you use to configure the adapter to receive data-change messages.</span></span> <span data-ttu-id="182e3-109">Vous devez spécifier ces propriétés de liaison lors de l’exécution de l’application d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="182e3-109">You must specify these binding properties while running the polling application.</span></span>  
  
|<span data-ttu-id="182e3-110">Propriété de liaison</span><span class="sxs-lookup"><span data-stu-id="182e3-110">Binding Property</span></span>|<span data-ttu-id="182e3-111"> Description</span><span class="sxs-lookup"><span data-stu-id="182e3-111">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="182e3-112">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="182e3-112">**InboundOperationType**</span></span>|<span data-ttu-id="182e3-113">Spécifie si vous souhaitez effectuer un **d’interrogation** ou **Notification** opération entrante.</span><span class="sxs-lookup"><span data-stu-id="182e3-113">Specifies whether you want to perform a **Polling** or **Notification** inbound operation.</span></span> <span data-ttu-id="182e3-114">Valeur par défaut est **d’interrogation**.</span><span class="sxs-lookup"><span data-stu-id="182e3-114">Default is **Polling**.</span></span>|  
|<span data-ttu-id="182e3-115">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="182e3-115">**PolledDataAvailableStatement**</span></span>|<span data-ttu-id="182e3-116">Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="182e3-116">Specifies the SQL statement that the adapter executes to determine whether any data is available for polling.</span></span> <span data-ttu-id="182e3-117">Uniquement si un enregistrement n’est disponible, la procédure stockée que vous avez spécifié pour le **PollingInput** liaison de la propriété sera exécutée.</span><span class="sxs-lookup"><span data-stu-id="182e3-117">Only if a record is available, the stored procedure you specified for the **PollingInput** binding property will be executed.</span></span>|  
|<span data-ttu-id="182e3-118">**PollingInterval**</span><span class="sxs-lookup"><span data-stu-id="182e3-118">**PollingInterval**</span></span>|<span data-ttu-id="182e3-119">Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="182e3-119">Specifies the interval, in seconds, at which the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="182e3-120">La valeur par défaut est 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="182e3-120">The default is 30 seconds.</span></span> <span data-ttu-id="182e3-121">L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives.</span><span class="sxs-lookup"><span data-stu-id="182e3-121">The polling interval determines the time interval between successive polls.</span></span> <span data-ttu-id="182e3-122">Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur est en veille pendant le temps restant dans l’intervalle.</span><span class="sxs-lookup"><span data-stu-id="182e3-122">If the statement is executed within the specified interval, the adapter sleeps for the remaining time in the interval.</span></span>|  
|<span data-ttu-id="182e3-123">**PollingInput**</span><span class="sxs-lookup"><span data-stu-id="182e3-123">**PollingInput**</span></span>|<span data-ttu-id="182e3-124">Spécifie l’instruction d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="182e3-124">Specifies the polling statement.</span></span> <span data-ttu-id="182e3-125">Pour interroger à l’aide d’une procédure stockée, vous devez spécifier le message de requête entière pour cette propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="182e3-125">To poll using a stored procedure, you must specify the entire request message for this binding property.</span></span> <span data-ttu-id="182e3-126">Le message de demande doit être le même que vous envoyez à l’adaptateur pour l’appel de la procédure stockée sous forme d’opération sortante.</span><span class="sxs-lookup"><span data-stu-id="182e3-126">The request message must be the same that you send to the adapter for invoking the stored procedure as an outbound operation.</span></span> <span data-ttu-id="182e3-127">La valeur par défaut est null.</span><span class="sxs-lookup"><span data-stu-id="182e3-127">The default is null.</span></span><br /><br /> <span data-ttu-id="182e3-128">Vous devez spécifier une valeur pour **PollingInput** propriété pour activer l’interrogation de liaison.</span><span class="sxs-lookup"><span data-stu-id="182e3-128">You must specify a value for **PollingInput** binding property to enable polling.</span></span> <span data-ttu-id="182e3-129">L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="182e3-129">The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.</span></span>|  
|<span data-ttu-id="182e3-130">**PollingAction**</span><span class="sxs-lookup"><span data-stu-id="182e3-130">**PollingAction**</span></span>|<span data-ttu-id="182e3-131">Spécifie l’action pour l’opération d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="182e3-131">Specifies the action for the polling operation.</span></span> <span data-ttu-id="182e3-132">Vous pouvez déterminer l’action d’interrogation de l’interface de service généré pour l’opération en utilisant la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="182e3-132">You can determine the polling action from the service interface generated for the operation using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span>|  
|<span data-ttu-id="182e3-133">**PostPollStatement**</span><span class="sxs-lookup"><span data-stu-id="182e3-133">**PostPollStatement**</span></span>|<span data-ttu-id="182e3-134">Spécifie un bloc d’instructions qui est exécuté après l’instruction spécifiée par le **PollingInput** propriété de liaison est exécutée.</span><span class="sxs-lookup"><span data-stu-id="182e3-134">Specifies a statement block that is executed after the statement specified by the **PollingInput** binding property is executed.</span></span>|  
|<span data-ttu-id="182e3-135">**PollWhileDataFound**</span><span class="sxs-lookup"><span data-stu-id="182e3-135">**PollWhileDataFound**</span></span>|<span data-ttu-id="182e3-136">Spécifie si le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignore l’intervalle d’interrogation et exécute en permanence l’instruction d’interrogation, si les données sont disponibles dans la table interrogée.</span><span class="sxs-lookup"><span data-stu-id="182e3-136">Specifies whether the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignores the polling interval and continuously executes the polling statement, if data is available in the table being polled.</span></span> <span data-ttu-id="182e3-137">Si aucune donnée n’est disponible dans la table, l’adaptateur revient pour exécuter l’instruction d’interrogation à l’intervalle d’interrogation spécifié.</span><span class="sxs-lookup"><span data-stu-id="182e3-137">If no data is available in the table, the adapter reverts to execute the polling statement at the specified polling interval.</span></span> <span data-ttu-id="182e3-138">La valeur par défaut est False.</span><span class="sxs-lookup"><span data-stu-id="182e3-138">Default is false.</span></span>|  
  
 <span data-ttu-id="182e3-139">Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="182e3-139">For a more complete description of these properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span> <span data-ttu-id="182e3-140">Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] d’interrogation, lisez les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="182e3-140">For a complete description of how to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll, read the following sections.</span></span>  
  
## <a name="how-this-topic-demonstrates-polling"></a><span data-ttu-id="182e3-141">Comment cette rubrique illustre l’interrogation</span><span class="sxs-lookup"><span data-stu-id="182e3-141">How This Topic Demonstrates Polling</span></span>  
 <span data-ttu-id="182e3-142">Dans cette rubrique, pour illustrer comment le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge la réception de messages à l’aide de procédures stockées, vous utilisez la GET_ACTIVITYS de modification de données procédure stockée pour interroger la table ACCOUNTACTIVITY dans la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="182e3-142">In this topic, to demonstrate how the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports receiving data change messages using stored procedures, you use the GET_ACTIVITYS stored procedure to poll the ACCOUNTACTIVITY table in the Oracle database.</span></span> <span data-ttu-id="182e3-143">Cette procédure stockée est disponible avec le package ACCOUNT_PKG.</span><span class="sxs-lookup"><span data-stu-id="182e3-143">This stored procedure is available with the ACCOUNT_PKG package.</span></span> <span data-ttu-id="182e3-144">Vous pouvez exécuter les scripts SQL fournis avec les exemples pour créer ces objets dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="182e3-144">You can run the SQL scripts provided with the samples to create these objects in the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="182e3-145">L’exemple de sondages de cette rubrique le ACCOUNTACTIVITY de table, qui est une table de base de données créée en exécutant les scripts fournis avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="182e3-145">The example in this topic polls the ACCOUNTACTIVITY table, which is a base database table created by running the scripts provided with the samples.</span></span> <span data-ttu-id="182e3-146">Vous devez effectuer les procédures similaires comme décrit dans cette rubrique pour interroger toute autre table, y compris les tables de l’interface.</span><span class="sxs-lookup"><span data-stu-id="182e3-146">You must perform similar procedures as described in this topic to poll any other table, including interface tables.</span></span>  
  
 <span data-ttu-id="182e3-147">Pour illustrer une opération d’interrogation, nous les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="182e3-147">To demonstrate a polling operation, we do the following:</span></span>  
  
-   <span data-ttu-id="182e3-148">Spécifiez une instruction SELECT pour le **PolledDataAvailableStatement** liaison de propriété pour déterminer où la table interrogés (ACCOUNTACTIVITY) comporte des données.</span><span class="sxs-lookup"><span data-stu-id="182e3-148">Specify a SELECT statement for the **PolledDataAvailableStatement** binding property to determine where the table being polled (ACCOUNTACTIVITY) has any data.</span></span> <span data-ttu-id="182e3-149">Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :</span><span class="sxs-lookup"><span data-stu-id="182e3-149">In this example, you can set this binding property as:</span></span>  
  
    ```  
    SELECT COUNT (*) FROM ACCOUNTACTIVITY  
    ```  
  
     <span data-ttu-id="182e3-150">Cela garantit que l’adaptateur s’exécute l’instruction d’interrogation uniquement lorsque la table ACCOUNTACTIVITY a des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="182e3-150">This ensures that the adapter executes the polling statement only when the ACCOUNTACTIVITY table has some records.</span></span>  
  
-   <span data-ttu-id="182e3-151">Exécuter une procédure stockée, GET_ACTIVITYS, en fournissant le message de demande dans le cadre de la **PollingInput** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="182e3-151">Execute a stored procedure, GET_ACTIVITYS, by providing the request message as part of the **PollingInput** binding property.</span></span> <span data-ttu-id="182e3-152">Cette procédure stockée récupère toutes les lignes dans la table ACCOUNTACTIVITY et vous obtiendrez un message de réponse de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="182e3-152">This stored procedure will retrieve all the rows in the ACCOUNTACTIVITY table and you will get a response message from the adapter.</span></span>  
  
-   <span data-ttu-id="182e3-153">Exécution d’un bloc de PL/SQL dans le cadre de la **PostPollStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="182e3-153">Execute a PL/SQL block as part of the **PostPollStatement** binding property.</span></span> <span data-ttu-id="182e3-154">Cette instruction déplacera toutes les données à partir de la table ACCOUNTACTIVITY à une autre table dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="182e3-154">This statement will move all data from ACCOUNTACTIVITY table to another table in the database.</span></span> <span data-ttu-id="182e3-155">Une fois que cela se produit, la prochaine fois **PollingInput** est exécutée, elle ne permet pas d’extraire des données et par conséquent, la procédure stockée de GET_ACTIVITYS retournera un message de réponse vide.</span><span class="sxs-lookup"><span data-stu-id="182e3-155">After this happens, the next time **PollingInput** is executed, it will not fetch any data and hence the GET_ACTIVITYS stored procedure will return an empty response message.</span></span>  
  
-   <span data-ttu-id="182e3-156">Jusqu'à ce que davantage de données est ajouté à la table ACCOUNTACTIVITY, vous continuez à obtenir les messages de réponse vide, donc vous devez remplir de nouveau la table ACCOUNTACTIVITY avec les nouveaux enregistrements.</span><span class="sxs-lookup"><span data-stu-id="182e3-156">Until more data is added to the ACCOUNTACTIVITY table, you will continue to get empty response messages so you must repopulate the ACCOUNTACTIVITY table with new records.</span></span> <span data-ttu-id="182e3-157">Vous pouvez le faire en exécutant le script more_activity_data.sql fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="182e3-157">You can do so by running the more_activity_data.sql script provided with the samples.</span></span> <span data-ttu-id="182e3-158">Une fois que vous exécutez ce script, l’opération d’interrogation suivante permet d’extraire les nouveaux enregistrements insérés dans la table.</span><span class="sxs-lookup"><span data-stu-id="182e3-158">After you run this script, the next polling operation will fetch the new records inserted into the table.</span></span>  
  
## <a name="configuring-polling-in-the-wcf-service-model"></a><span data-ttu-id="182e3-159">Configuration d’interrogation dans le modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="182e3-159">Configuring Polling in the WCF Service Model</span></span>  
 <span data-ttu-id="182e3-160">Pour interroger à l’aide de procédures stockées avec la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec le modèle de service WCF, vous devez :</span><span class="sxs-lookup"><span data-stu-id="182e3-160">To poll using stored procedures with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with the WCF service model, you must:</span></span>  
  
-   <span data-ttu-id="182e3-161">Générer un contrat de service WCF (interface) pour la procédure stockée à l’aide de laquelle vous vous apprêtez à interroger.</span><span class="sxs-lookup"><span data-stu-id="182e3-161">Generate a WCF service contract (interface) for the stored procedure using which you are going to poll.</span></span> <span data-ttu-id="182e3-162">Pour cet exemple, vous devez générer le contrat de service WCF pour le **GET_ACTIVITYS** procédure stockée sous forme d’opération entrant.</span><span class="sxs-lookup"><span data-stu-id="182e3-162">For this example, you must generate the WCF service contract for the **GET_ACTIVITYS** stored procedure as an inbound operation.</span></span> <span data-ttu-id="182e3-163">Pour ce faire, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="182e3-163">To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
-   <span data-ttu-id="182e3-164">Implémenter un service WCF à partir de cette interface.</span><span class="sxs-lookup"><span data-stu-id="182e3-164">Implement a WCF service from this interface.</span></span>  
  
-   <span data-ttu-id="182e3-165">Héberger ce service WCF à l’aide d’un hôte de service (**System.ServiceModel.ServiceHost**).</span><span class="sxs-lookup"><span data-stu-id="182e3-165">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="182e3-166">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="182e3-166">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="182e3-167">Les exemples dans la table de base de données ACCOUNTACTIVITY à l’aide de la GET_ACTIVITYS sondage rubrique de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="182e3-167">The examples in this topic poll the ACCOUNTACTIVITY database table using the GET_ACTIVITYS stored procedure.</span></span> <span data-ttu-id="182e3-168">Un script pour générer la table et la procédure stockée est fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="182e3-168">A script to generate the table and the stored procedure is supplied with the samples.</span></span> <span data-ttu-id="182e3-169">Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="182e3-169">For more information about the samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="182e3-170">Un exemple, **StoredProcPolling_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="182e3-170">A sample, **StoredProcPolling_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="182e3-171">Le contrat de Service WCF et la classe</span><span class="sxs-lookup"><span data-stu-id="182e3-171">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="182e3-172">Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un contrat de service WCF (interface) et la prise en charge des classes pour la **GET_ACTIVITYS** opération entrante.</span><span class="sxs-lookup"><span data-stu-id="182e3-172">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **GET_ACTIVITYS** inbound operation.</span></span> <span data-ttu-id="182e3-173">Pour plus d’informations sur la génération d’un contrat de service WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="182e3-173">For more information about generating a WCF service contract, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="182e3-174">Le contrat de Service WCF (Interface)</span><span class="sxs-lookup"><span data-stu-id="182e3-174">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="182e3-175">Le code suivant illustre le contrat de service WCF (interface) généré pour le **GET_ACTIVITYS** opération entrante.</span><span class="sxs-lookup"><span data-stu-id="182e3-175">The following code shows the WCF service contract (interface) generated for the **GET_ACTIVITYS** inbound operation.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/", ConfigurationName="PollingPackageApis_APPS_ACCOUNT_PKG")]  
public interface PollingPackageApis_APPS_ACCOUNT_PKG {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/PollingPackageApis/APPS/ACCOUNT_PKG) of message GET_ACTIVITYS   
    // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="PollingPackageApis/APPS/ACCOUNT_PKG/GET_ACTIVITYS")]  
    void GET_ACTIVITYS(GET_ACTIVITYS request);  
}  
```  
  
### <a name="the-message-contracts"></a><span data-ttu-id="182e3-176">Les contrats de Message</span><span class="sxs-lookup"><span data-stu-id="182e3-176">The Message Contracts</span></span>  
 <span data-ttu-id="182e3-177">Voici le contrat de message pour le **GET_ACTIVITYS** opération entrante.</span><span class="sxs-lookup"><span data-stu-id="182e3-177">Following is the message contract for the **GET_ACTIVITYS** inbound operation.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="GET_ACTIVITYS", WrapperNamespace="http://schemas.microsoft.com/OracleEBS/2008/05/PollingPackageApis/APPS/ACCOUNT_PK" +  
    "G", IsWrapped=true)]  
public partial class GET_ACTIVITYS {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/PollingPackageApis/APPS/ACCOUNT_PK" +  
        "G", Order=0)]  
    public schemas.microsoft.com.OracleEBS._2008._05.RecordTypes.APPS.ACCOUNT_PKG.GET_ACTIVITYS.OUTRECSRecord[] OUTRECS;  
  
    public GET_ACTIVITYS() {  
    }  
  
    public GET_ACTIVITYS(schemas.microsoft.com.OracleEBS._2008._05.RecordTypes.APPS.ACCOUNT_PKG.GET_ACTIVITYS.OUTRECSRecord[] OUTRECS) {  
        this.OUTRECS = OUTRECS;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a><span data-ttu-id="182e3-178">Classe de Service WCF</span><span class="sxs-lookup"><span data-stu-id="182e3-178">WCF Service Class</span></span>  
 <span data-ttu-id="182e3-179">Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également un fichier qui a un stub pour la classe de service WCF implémenté le contrat de service (interface).</span><span class="sxs-lookup"><span data-stu-id="182e3-179">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="182e3-180">Le nom du fichier est OracleEBSBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="182e3-180">The name of the file is OracleEBSBindingService.cs.</span></span> <span data-ttu-id="182e3-181">Vous pouvez insérer la logique pour traiter les **GET_ACTIVITYS** opération directement dans cette classe.</span><span class="sxs-lookup"><span data-stu-id="182e3-181">You can insert the logic to process the **GET_ACTIVITYS** operation directly into this class.</span></span> <span data-ttu-id="182e3-182">Le code suivant illustre la classe de service WCF générée par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="182e3-182">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
```  
namespace OracleEBSBindingNamespace {  
  
    public class OracleEBSBindingService : PollingPackageApis_APPS_ACCOUNT_PKG {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/PollingPackageApis/APPS/ACCOUNT_PKG) of message GET_ACTIVITYS   
        // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
        public virtual void GET_ACTIVITYS(GET_ACTIVITYS request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-inbound-messages-for-polling-using-a-stored-procedure"></a><span data-ttu-id="182e3-183">Réception des Messages entrants pour l’interrogation à l’aide d’une procédure stockée</span><span class="sxs-lookup"><span data-stu-id="182e3-183">Receiving Inbound Messages For Polling Using a Stored Procedure</span></span>  
 <span data-ttu-id="182e3-184">Cette section fournit des instructions sur la façon d’écrire une application .NET pour recevoir des messages entrants d’interrogation à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="182e3-184">This section provides instructions on how to write a .NET application to receive inbound polling messages using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
#### <a name="to-receive-polling-messages-using-a-stored-procedure"></a><span data-ttu-id="182e3-185">Pour recevoir des messages d’interrogation à l’aide d’une procédure stockée</span><span class="sxs-lookup"><span data-stu-id="182e3-185">To receive polling messages using a stored procedure</span></span>  
  
1.  <span data-ttu-id="182e3-186">Utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer un contrat de service WCF (interface) et des classes d’assistance pour le **GET_ACTIVITYS** opération entrante.</span><span class="sxs-lookup"><span data-stu-id="182e3-186">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **GET_ACTIVITYS** inbound operation.</span></span> <span data-ttu-id="182e3-187">Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="182e3-187">For more information, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span> <span data-ttu-id="182e3-188">Vous pouvez éventuellement spécifier les propriétés de liaison lors de la génération les classes d’assistance et de contrat de service.</span><span class="sxs-lookup"><span data-stu-id="182e3-188">You can optionally specify the binding properties while generating the service contract and helper classes.</span></span> <span data-ttu-id="182e3-189">Cela garantit qu’ils sont correctement définies dans le fichier de configuration généré.</span><span class="sxs-lookup"><span data-stu-id="182e3-189">This guarantees that they are properly set in the generated configuration file.</span></span>  
  
2.  <span data-ttu-id="182e3-190">Implémenter un service WCF à partir de l’interface et assistance des classes générées à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="182e3-190">Implement a WCF service from the interface and helper classes generated in step 1.</span></span> <span data-ttu-id="182e3-191">Le **GET_ACTIVITYS** méthode de cette classe peut lever une exception pour annuler la transaction d’interrogation, si une erreur est rencontrée, le traitement des données reçues à partir de la **GET_ACTIVITYS** opération ; sinon la méthode ne retourne rien.</span><span class="sxs-lookup"><span data-stu-id="182e3-191">The **GET_ACTIVITYS** method of this class can throw an exception to abort the polling transaction, if an error is encountered processing the data received from the **GET_ACTIVITYS** operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="182e3-192">Vous devez attribuer la classe de service WCF comme suit :</span><span class="sxs-lookup"><span data-stu-id="182e3-192">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     <span data-ttu-id="182e3-193">Dans le **GET_ACTIVITYS** (méthode), vous pouvez directement implémenter votre logique d’application.</span><span class="sxs-lookup"><span data-stu-id="182e3-193">Within the **GET_ACTIVITYS** method, you can implement your application logic directly.</span></span> <span data-ttu-id="182e3-194">Cette classe peut être trouvée dans OracleEBSBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="182e3-194">This class can be found in OracleEBSBindingService.cs.</span></span> <span data-ttu-id="182e3-195">Ce code dans cet exemple montre comment des classes le **OracleEBSBindingService** classe.</span><span class="sxs-lookup"><span data-stu-id="182e3-195">This code in this example sub-classes the **OracleEBSBindingService** class.</span></span> <span data-ttu-id="182e3-196">Dans ce code, le message de l’interrogation reçu et est écrit dans la console.</span><span class="sxs-lookup"><span data-stu-id="182e3-196">In this code, the polling message received and is written to the console.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void  GET_ACTIVITYS(GET_ACTIVITYS request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Tx Id\tAccount\tAmount\tProcessed");  
            for (int i = 0; i < request.OUTRECS.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.OUTRECS[i].TID,  
                request.OUTRECS[i].ACCOUNT,  
                request.OUTRECS[i].AMOUNT,  
                request.OUTRECS[i].PROCESSED);  
            }  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="182e3-197">Vous devez implémenter la classe suivante pour éviter de transmettre des informations d’identification en tant que partie de l’URI.</span><span class="sxs-lookup"><span data-stu-id="182e3-197">You must implement the following class to avoid passing credentials as part of the URI.</span></span> <span data-ttu-id="182e3-198">Dans la dernière partie de l’application, vous serez instancier cette classe à transmettre les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="182e3-198">In the latter part of the application, you will instantiate this class to pass on the credentials.</span></span>  
  
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
  
4.  <span data-ttu-id="182e3-199">Créer un **OracleEBSBinding** et configurer l’opération d’interrogation en spécifiant les propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="182e3-199">Create an **OracleEBSBinding** and configure the polling operation by specifying the binding properties.</span></span> <span data-ttu-id="182e3-200">Ce faire, vous pouvez soit explicitement dans le code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="182e3-200">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="182e3-201">Au minimum, vous devez spécifier le **InboundOperationType**, **PolledDataAvailableStatement**, **PollingInput**, et **PollingAction**propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="182e3-201">At a minimum, you must specify the **InboundOperationType**, **PolledDataAvailableStatement**, **PollingInput**, and **PollingAction** binding properties.</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM ACCOUNTACTIVITY";  
    binding.PollingInput = "<GET_ACTIVITYS xmlns='http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/APPS/ACCOUNT_PKG'><INRECS>OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY</INRECS></GET_ACTIVITYS>";  
    binding.PollingAction = "PollingPackageApis/APPS/ACCOUNT_PKG/GET_ACTIVITYS";  
    binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="182e3-202">Notez que la valeur de la **PollingInput** propriété de liaison contient le message de demande pour l’appel de la **GET_ACTIVITYS** procédure stockée sous forme d’opération sortante.</span><span class="sxs-lookup"><span data-stu-id="182e3-202">Note that the value for the **PollingInput** binding property contains the request message for invoking the **GET_ACTIVITYS** stored procedure as an outbound operation.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="182e3-203">Dans cet exemple, étant donné que vous demandent une table de base de données, il est inutile définir le contexte d’applications.</span><span class="sxs-lookup"><span data-stu-id="182e3-203">In this example, because you are polling a database table, you do not need to set the applications context.</span></span> <span data-ttu-id="182e3-204">Toutefois, si vous ont été l’interrogation d’une table d’interface, vous devez définir le contexte des applications en spécifiant le **OracleUserName**, **OraclePassword**, et **OracleEBSResponsibilityName** propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="182e3-204">However, if you were polling an interface table, you must set the applications context by specifying the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="182e3-205">Pour plus d’informations sur le contexte de l’application, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span><span class="sxs-lookup"><span data-stu-id="182e3-205">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
5.  <span data-ttu-id="182e3-206">Spécifiez les informations d’identification Oracle E-Business Suite en instanciant le **PollingCredentials** classe que vous avez créé à l’étape 3.</span><span class="sxs-lookup"><span data-stu-id="182e3-206">Specify Oracle E-Business Suite credentials by instantiating the **PollingCredentials** class you created in Step 3.</span></span>  
  
    ```  
    PollingCredentials credentials = new PollingCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
    ```  
  
6.  <span data-ttu-id="182e3-207">Créez une instance du service WCF créé à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="182e3-207">Create an instance of the WCF service created in step 2.</span></span>  
  
    ```  
    // create service instance  
    PollingService service = new PollingService();  
    ```  
  
7.  <span data-ttu-id="182e3-208">Créez une instance de **System.ServiceModel.ServiceHost** à l’aide du service WCF et l’URI de connexion de base.</span><span class="sxs-lookup"><span data-stu-id="182e3-208">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="182e3-209">L’URI de la connexion de base ne peut pas contenir l’ID d’entrée, s’il est spécifié.</span><span class="sxs-lookup"><span data-stu-id="182e3-209">The base connection URI cannot contain the inbound ID, if specified.</span></span> <span data-ttu-id="182e3-210">Vous devez également passer les informations d’identification ici.</span><span class="sxs-lookup"><span data-stu-id="182e3-210">You must also pass the credentials here.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
8.  <span data-ttu-id="182e3-211">Ajouter un point de terminaison de service à l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="182e3-211">Add a service endpoint to the service host.</span></span> <span data-ttu-id="182e3-212">Pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="182e3-212">To do this:</span></span>  
  
    -   <span data-ttu-id="182e3-213">Utilisez la liaison créée à l’étape 4.</span><span class="sxs-lookup"><span data-stu-id="182e3-213">Use the binding created in step 4.</span></span>  
  
    -   <span data-ttu-id="182e3-214">Spécifiez une URI qui contient les informations d’identification de connexion et, si nécessaire, un ID d’entrée.</span><span class="sxs-lookup"><span data-stu-id="182e3-214">Specify a connection URI that contains credentials and, if required, an inbound ID.</span></span>  
  
    -   <span data-ttu-id="182e3-215">Spécifiez le contrat en tant que « PollingPackageApis_APPS_ACCOUNT_PKG » pour interroger la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="182e3-215">Specify the contract as "PollingPackageApis_APPS_ACCOUNT_PKG" to poll the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
    ```  
    // Add service endpoint: be sure to specify PollingPackageApis_APPS_ACCOUNT_PKG as the contract  
    Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
    serviceHost.AddServiceEndpoint("PollingPackageApis_APPS_ACCOUNT_PKG", binding, ConnectionUri);  
    ```  
  
9. <span data-ttu-id="182e3-216">Pour recevoir les données d’interrogation, ouvrez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="182e3-216">To receive polling data, open the service host.</span></span> <span data-ttu-id="182e3-217">L’adaptateur retourne les données chaque fois que la requête retourne un jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="182e3-217">The adapter will return data whenever the query returns a result set.</span></span>  
  
    ```  
    // Open the service host to begin polling  
    serviceHost.Open();  
    ```  
  
10. <span data-ttu-id="182e3-218">Pour mettre fin à l’interrogation, fermez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="182e3-218">To terminate polling, close the service host.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="182e3-219">La carte va continuer à interroger jusqu'à ce que l’hôte de service est fermé.</span><span class="sxs-lookup"><span data-stu-id="182e3-219">The adapter will continue to poll until the service host is closed.</span></span>  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a><span data-ttu-id="182e3-220">Exemple</span><span class="sxs-lookup"><span data-stu-id="182e3-220">Example</span></span>  
 <span data-ttu-id="182e3-221">L’exemple suivant montre une application d’interrogation qui interroge la table de base de données ACCOUNTACTIVITY à l’aide de la GET_ACTIVITYS de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="182e3-221">The following example shows a polling application that polls the ACCOUNTACTIVITY database table using the GET_ACTIVITYS stored procedure.</span></span> <span data-ttu-id="182e3-222">Le **PollingInput** propriété de liaison contient le message de demande pour appeler la procédure stockée de GET_ACTIVITYS qui lit toutes les données de la table ACCOUNTACTIVITY et l’instruction de sondage post déplace toutes les données à partir de ACCOUNTACTIVITY pour la table ACTIVITYHISTORY.</span><span class="sxs-lookup"><span data-stu-id="182e3-222">The **PollingInput** binding property contains the request message to invoke the GET_ACTIVITYS stored procedure that reads all the data from the ACCOUNTACTIVITY table and the post poll statement moves all the data from ACCOUNTACTIVITY to ACTIVITYHISTORY table.</span></span>  
  
 <span data-ttu-id="182e3-223">Le premier message d’interrogation fournit tous les enregistrements de la table ACCOUNTACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="182e3-223">The first polling message gives all the records from the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="182e3-224">Les messages suivants d’interrogation ne contient pas d’enregistrements, car l’instruction de sondage post supprime les enregistrements.</span><span class="sxs-lookup"><span data-stu-id="182e3-224">Subsequent polling messages will not contain any records because the post poll statement deletes the records.</span></span> <span data-ttu-id="182e3-225">Jusqu'à ce que davantage de données est ajouté à la table ACCOUNTACTIVITY, vous n’obtiendrez pas tous les messages d’interrogation, donc vous devez remplir de nouveau la table ACCOUNTACTIVITY avec les nouveaux enregistrements.</span><span class="sxs-lookup"><span data-stu-id="182e3-225">Until more data is added to the ACCOUNTACTIVITY table, you will not get any polling messages so you must repopulate the ACCOUNTACTIVITY table with new records.</span></span> <span data-ttu-id="182e3-226">Vous pouvez le faire en exécutant le script more_activity_data.sql fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="182e3-226">You can do so by running the more_activity_data.sql script provided with the samples.</span></span>  
  
 <span data-ttu-id="182e3-227">Une fois que vous exécutez ce script, l’opération d’interrogation suivante permet d’extraire les nouveaux enregistrements insérés dans la table.</span><span class="sxs-lookup"><span data-stu-id="182e3-227">After you run this script, the next polling operation will fetch the new records inserted into the table.</span></span> <span data-ttu-id="182e3-228">La carte continuera d’interroger jusqu'à ce que vous fermez l’hôte de service en appuyant sur `<RETURN>`.</span><span class="sxs-lookup"><span data-stu-id="182e3-228">The adapter will continue to poll until you close the service host by pressing `<RETURN>`.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.Adapters.OracleEBS;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Collections.ObjectModel;  
  
namespace StoredProcPolling_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void  GET_ACTIVITYS(GET_ACTIVITYS request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Tx Id\tAccount\tAmount\tProcessed");  
            for (int i = 0; i < request.OUTRECS.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.OUTRECS[i].TID,  
                request.OUTRECS[i].ACCOUNT,  
                request.OUTRECS[i].AMOUNT,  
                request.OUTRECS[i].PROCESSED);  
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
  
                OracleEBSBinding binding = new OracleEBSBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM ACCOUNTACTIVITY";  
                binding.PollingInput = "<GET_ACTIVITYS xmlns='http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/APPS/ACCOUNT_PKG'><INRECS>OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY</INRECS></GET_ACTIVITYS>";  
                binding.PollingAction = "PollingPackageApis/APPS/ACCOUNT_PKG/GET_ACTIVITYS";  
                binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // an InboundID; otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
  
                PollingCredentials credentials = new PollingCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                Console.WriteLine("Opening service host...");  
                PollingService service = new PollingService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("PollingPackageApis_APPS_ACCOUNT_PKG", binding, ConnectionUri);  
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
  
## <a name="see-also"></a><span data-ttu-id="182e3-229">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="182e3-229">See Also</span></span>  
 [<span data-ttu-id="182e3-230">Interrogation Oracle E-Business Suite à l’aide du modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="182e3-230">Poll Oracle E-Business Suite using the WCF service model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-the-wcf-service-model.md)
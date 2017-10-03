---
title: "Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT avec le modèle de service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 521d58e4-73b1-48a8-9a0a-9e733386c1b5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2cac950ced0fb0d7133e99bc3d12699f9379bcb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-e-business-suite-using-select-statement-with-the-wcf-service-model"></a><span data-ttu-id="e5fd8-102">Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT avec le modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="e5fd8-102">Poll Oracle E-Business Suite using SELECT statement with the WCF service model</span></span>
<span data-ttu-id="e5fd8-103">Vous pouvez configurer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des messages de modification de données périodiques à l’aide d’une instruction SELECT pour l’interrogation de façon permanente les tables d’interface, interface, des vues, des tables et des vues dans Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-103">You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive periodic data-change messages by using a SELECT statement to continuously poll the interface tables, interface views, tables and views in Oracle E-Business Suite.</span></span> <span data-ttu-id="e5fd8-104">Vous pouvez spécifier une instruction SELECT comme une instruction d’interrogation de l’adaptateur s’exécute périodiquement pour Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-104">You can specify a SELECT statement as a polling statement that the adapter executes periodically to poll Oracle E-Business Suite.</span></span> <span data-ttu-id="e5fd8-105">Vous pouvez également spécifier un bloc de code après interrogation PL/SQL que l’adaptateur s’exécute après l’exécution de l’instruction d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-105">You can also specify a post-poll PL/SQL code block that the adapter executes after the polling statement is executed.</span></span>  
  
 <span data-ttu-id="e5fd8-106">Pour activer l’interrogation, vous devez spécifier certaines propriétés de liaison comme décrit dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-106">To enable polling, you must specify certain binding properties as described in this topic.</span></span>  <span data-ttu-id="e5fd8-107">Pour plus d’informations sur la façon dont l’adaptateur prend en charge d’interrogation, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span><span class="sxs-lookup"><span data-stu-id="e5fd8-107">For more information about how the adapter supports polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  
  
## <a name="configuring-a-polling-operation-with-oracle-e-business-suite-adapter-binding-properties"></a><span data-ttu-id="e5fd8-108">Configuration d’une opération d’interrogation avec liaison des propriétés de l’adaptateur Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="e5fd8-108">Configuring a Polling Operation with Oracle E-Business Suite Adapter Binding Properties</span></span>  
 <span data-ttu-id="e5fd8-109">Le tableau suivant récapitule les [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] messages de modification des propriétés de liaison que vous utilisez pour configurer l’adaptateur pour recevoir des données.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-109">The following table summarizes the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding properties that you use to configure the adapter to receive data change messages.</span></span> <span data-ttu-id="e5fd8-110">Vous devez spécifier ces propriétés de liaison lors de l’exécution de l’application d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-110">You must specify these binding properties while running the polling application.</span></span>  
  
|<span data-ttu-id="e5fd8-111">Propriété de liaison</span><span class="sxs-lookup"><span data-stu-id="e5fd8-111">Binding Property</span></span>|<span data-ttu-id="e5fd8-112"> Description</span><span class="sxs-lookup"><span data-stu-id="e5fd8-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="e5fd8-113">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="e5fd8-113">**InboundOperationType**</span></span>|<span data-ttu-id="e5fd8-114">Spécifie si vous souhaitez effectuer **d’interrogation** ou **Notification** opération entrante.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-114">Specifies whether you want to perform **Polling** or **Notification** inbound operation.</span></span> <span data-ttu-id="e5fd8-115">Valeur par défaut est **d’interrogation**.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-115">Default is **Polling**.</span></span>|  
|<span data-ttu-id="e5fd8-116">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="e5fd8-116">**PolledDataAvailableStatement**</span></span>|<span data-ttu-id="e5fd8-117">Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-117">Specifies the SQL statement that the adapter executes to determine whether any data is available for polling.</span></span> <span data-ttu-id="e5fd8-118">Uniquement si un enregistrement n’est disponible, l’instruction SELECT que vous spécifiez pour le **PollingInput** liaison de la propriété sera exécutée.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-118">Only if a record is available, the SELECT statement you specify for the **PollingInput** binding property will be executed.</span></span>|  
|<span data-ttu-id="e5fd8-119">**PollingInterval**</span><span class="sxs-lookup"><span data-stu-id="e5fd8-119">**PollingInterval**</span></span>|<span data-ttu-id="e5fd8-120">Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-120">Specifies the interval, in seconds, at which the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="e5fd8-121">La valeur par défaut est 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-121">The default is 30 seconds.</span></span> <span data-ttu-id="e5fd8-122">L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-122">The polling interval determines the time interval between successive polls.</span></span> <span data-ttu-id="e5fd8-123">Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur est en veille pendant le temps restant dans l’intervalle.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-123">If the statement is executed within the specified interval, the adapter sleeps for the remaining time in the interval.</span></span>|  
|<span data-ttu-id="e5fd8-124">**PollingInput**</span><span class="sxs-lookup"><span data-stu-id="e5fd8-124">**PollingInput**</span></span>|<span data-ttu-id="e5fd8-125">Spécifie l’instruction d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-125">Specifies the polling statement.</span></span> <span data-ttu-id="e5fd8-126">Pour interroger à l’aide d’une instruction SELECT, vous devez spécifier une instruction SELECT pour cette propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-126">To poll using a SELECT statement, you must specify a SELECT statement for this binding property.</span></span> <span data-ttu-id="e5fd8-127">La valeur par défaut est null.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-127">The default is null.</span></span><br /><br /> <span data-ttu-id="e5fd8-128">Vous devez spécifier une valeur pour **PollingInput** propriété pour activer l’interrogation de liaison.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-128">You must specify a value for **PollingInput** binding property to enable polling.</span></span> <span data-ttu-id="e5fd8-129">L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-129">The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.</span></span>|  
|<span data-ttu-id="e5fd8-130">**PollingAction**</span><span class="sxs-lookup"><span data-stu-id="e5fd8-130">**PollingAction**</span></span>|<span data-ttu-id="e5fd8-131">Spécifie l’action pour l’opération d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-131">Specifies the action for the polling operation.</span></span> <span data-ttu-id="e5fd8-132">Vous pouvez déterminer l’action d’interrogation de l’interface de service généré pour l’opération en utilisant la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5fd8-132">You can determine the polling action from the service interface generated for the operation using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span>|  
|<span data-ttu-id="e5fd8-133">**PostPollStatement**</span><span class="sxs-lookup"><span data-stu-id="e5fd8-133">**PostPollStatement**</span></span>|<span data-ttu-id="e5fd8-134">Spécifie un bloc d’instructions qui est exécuté après l’instruction spécifiée par le **PollingInput** propriété de liaison est exécutée.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-134">Specifies a statement block that is executed after the statement specified by the **PollingInput** binding property is executed.</span></span>|  
|<span data-ttu-id="e5fd8-135">**PollWhileDataFound**</span><span class="sxs-lookup"><span data-stu-id="e5fd8-135">**PollWhileDataFound**</span></span>|<span data-ttu-id="e5fd8-136">Spécifie si le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignore l’intervalle d’interrogation et exécute en permanence l’instruction d’interrogation, si les données sont disponibles dans la table interrogée.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-136">Specifies whether the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignores the polling interval and continuously executes the polling statement, if data is available in the table being polled.</span></span> <span data-ttu-id="e5fd8-137">Si aucune donnée n’est disponible dans la table, l’adaptateur revient pour exécuter l’instruction d’interrogation à l’intervalle d’interrogation spécifié.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-137">If no data is available in the table, the adapter reverts to execute the polling statement at the specified polling interval.</span></span> <span data-ttu-id="e5fd8-138">La valeur par défaut est False.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-138">Default is false.</span></span>|  
  
 <span data-ttu-id="e5fd8-139">Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="e5fd8-139">For a more complete description of these properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span> <span data-ttu-id="e5fd8-140">Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour interroger la base de données Oracle, poursuivre la lecture.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-140">For a complete description of how to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll the Oracle database, read further.</span></span>  
  
## <a name="how-this-topic-demonstrates-polling"></a><span data-ttu-id="e5fd8-141">Comment cette rubrique illustre l’interrogation</span><span class="sxs-lookup"><span data-stu-id="e5fd8-141">How This Topic Demonstrates Polling</span></span>  
 <span data-ttu-id="e5fd8-142">Dans cette rubrique, pour illustrer comment le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge la réception de données modifier des messages à l’aide des instructions SELECT, vous continuez d’interroger le **MS_SAMPLE_EMPLOYEE** table d’interface dans le **bibliothèque d’objets Application**application.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-142">In this topic, to demonstrate how the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports receiving data change messages using SELECT statements, you poll the **MS_SAMPLE_EMPLOYEE** interface table in the **Application Object Library** application.</span></span> <span data-ttu-id="e5fd8-143">Cette table est créée lorsque vous exécutez le script create_apps_artifacts.sql fourni avec les exemples pour créer ces objets dans Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-143">This table is created when you run the create_apps_artifacts.sql script provided with the samples to create these objects in Oracle E-Business Suite.</span></span>  
  
 <span data-ttu-id="e5fd8-144">Pour illustrer une opération d’interrogation, nous les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e5fd8-144">To demonstrate a polling operation, we do the following:</span></span>  
  
-   <span data-ttu-id="e5fd8-145">Spécifiez une instruction SELECT pour le **PolledDataAvailableStatement** liaison de propriété pour déterminer où l’interface table interrogés (MS_SAMPLE_EMPLOYEE) comporte des données.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-145">Specify a SELECT statement for the **PolledDataAvailableStatement** binding property to determine where the interface table being polled (MS_SAMPLE_EMPLOYEE) has any data.</span></span> <span data-ttu-id="e5fd8-146">Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :</span><span class="sxs-lookup"><span data-stu-id="e5fd8-146">In this example, you can set this binding property as:</span></span>  
  
    ```  
    SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     <span data-ttu-id="e5fd8-147">Cela garantit que l’adaptateur s’exécute l’instruction d’interrogation uniquement lorsque la table d’interface MS_SAMPLE_EMPLOYEE a des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-147">This ensures that the adapter executes the polling statement only when the MS_SAMPLE_EMPLOYEE interface table has some records.</span></span>  
  
-   <span data-ttu-id="e5fd8-148">Spécifiez une instruction SELECT pour le **PollingInput** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-148">Specify a SELECT statement for the **PollingInput** binding property.</span></span> <span data-ttu-id="e5fd8-149">Cette instruction récupère toutes les lignes dans la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-149">This statement retrieves all the rows in the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="e5fd8-150">Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :</span><span class="sxs-lookup"><span data-stu-id="e5fd8-150">In this example, you can set this binding property as:</span></span>  
  
    ```  
    SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e5fd8-151">Pour plus d’informations sur la clause FOR UPDATE utilisée dans l’instruction SELECT, consultez [recevoir des messages d’interrogation de données modifiées à partir d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="e5fd8-151">For information about the FOR UPDATE clause used in the SELECT statement, see [Receive polling-based data-changed messages from Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md).</span></span>  
  
-   <span data-ttu-id="e5fd8-152">Spécifiez une instruction DELETE en tant que partie de la **PostPollStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-152">Specify a DELETE statement as part of the **PostPollStatement** binding property.</span></span> <span data-ttu-id="e5fd8-153">Cette instruction supprime toutes les données à partir de la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-153">This statement will delete all data from MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="e5fd8-154">Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :</span><span class="sxs-lookup"><span data-stu-id="e5fd8-154">In this example, you can set this binding property as:</span></span>  
  
    ```  
    DELETE FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     <span data-ttu-id="e5fd8-155">Une fois que cela se produit, la prochaine fois que l’instruction spécifiée pour **PollingInput** sera exécutée, elle ne permet pas d’extraire des données.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-155">After this happens, the next time the statement specified for **PollingInput** will be executed, it will not fetch any data.</span></span>  
  
-   <span data-ttu-id="e5fd8-156">Jusqu'à ce que davantage de données est ajouté à la table d’interface MS_SAMPLE_EMPLOYEE, vous n’obtiendrez pas tous les messages d’interrogation, donc vous devez remplir de nouveau la table d’interface MS_SAMPLE_EMPLOYEE avec nouveaux enregistrements.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-156">Until more data is added to the MS_SAMPLE_EMPLOYEE interface table, you will not get any polling messages so you must repopulate the MS_SAMPLE_EMPLOYEE interface table with new records.</span></span> <span data-ttu-id="e5fd8-157">Vous pouvez le faire en exécutant le script insert_apps_data.sql fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-157">You can do so by running the insert_apps_data.sql script provided with the samples.</span></span> <span data-ttu-id="e5fd8-158">Une fois que vous exécutez ce script, l’opération d’interrogation suivante permet d’extraire les nouveaux enregistrements insérés dans la table.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-158">After you run this script, the next polling operation will fetch the new records inserted into the table.</span></span>  
  
## <a name="configuring-polling-in-the-wcf-service-model"></a><span data-ttu-id="e5fd8-159">Configuration d’interrogation dans le modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="e5fd8-159">Configuring Polling in the WCF Service Model</span></span>  
 <span data-ttu-id="e5fd8-160">Pour interroger une table d’interface à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec le modèle de service WCF, vous devez :</span><span class="sxs-lookup"><span data-stu-id="e5fd8-160">To poll an interface table using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with the WCF service model, you must:</span></span>  
  
-   <span data-ttu-id="e5fd8-161">Générer un contrat de service WCF (interface) pour le **interrogation** opération sur la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-161">Generate a WCF service contract (interface) for the **Poll** operation on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="e5fd8-162">Pour ce faire, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5fd8-162">To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
-   <span data-ttu-id="e5fd8-163">Implémenter un service WCF à partir de cette interface.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-163">Implement a WCF service from this interface.</span></span>  
  
-   <span data-ttu-id="e5fd8-164">Héberger ce service WCF à l’aide d’un hôte de service (**System.ServiceModel.ServiceHost**).</span><span class="sxs-lookup"><span data-stu-id="e5fd8-164">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="e5fd8-165">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="e5fd8-165">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="e5fd8-166">Les exemples de cette rubrique interrogent la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-166">The examples in this topic poll the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="e5fd8-167">Un script pour générer la table est fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-167">A script to generate the table is supplied with the samples.</span></span> <span data-ttu-id="e5fd8-168">Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="e5fd8-168">For more information about the samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="e5fd8-169">Un exemple, **SelectPolling_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-169">A sample, **SelectPolling_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="e5fd8-170">Le contrat de Service WCF et la classe</span><span class="sxs-lookup"><span data-stu-id="e5fd8-170">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="e5fd8-171">Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un contrat de service WCF (interface) et la prise en charge des classes pour la **d’interrogation** opération.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-171">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **Polling** operation.</span></span> <span data-ttu-id="e5fd8-172">Pour plus d’informations sur la génération d’un contrat de service WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="e5fd8-172">For more information about generating a WCF service contract, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="e5fd8-173">Le contrat de Service WCF (Interface)</span><span class="sxs-lookup"><span data-stu-id="e5fd8-173">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="e5fd8-174">Le code suivant illustre le contrat de service WCF (interface) généré pour le **interrogation** dans la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-174">The following code shows the WCF service contract (interface) generated for the **Poll** operation on MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/", ConfigurationName="InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE")]  
public interface InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE) of message Poll   
    // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE")]  
    void Poll(Poll request);  
}  
```  
  
### <a name="the-message-contracts"></a><span data-ttu-id="e5fd8-175">Les contrats de Message</span><span class="sxs-lookup"><span data-stu-id="e5fd8-175">The Message Contracts</span></span>  
 <span data-ttu-id="e5fd8-176">Voici le contrat de message pour le **interrogation** dans la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-176">Following is the message contract for the **Poll** operation on MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Poll", WrapperNamespace="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE" +  
    "_EMPLOYEE", IsWrapped=true)]  
public partial class Poll {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE" +  
        "_EMPLOYEE", Order=0)]  
    public schemas.microsoft.com.OracleEBS._2008._05.TableViewRecord.APPS.MS_SAMPLE_EMPLOYEE.SelectRecord[] DATA;  
  
    public Poll() {  
    }  
  
    public Poll(schemas.microsoft.com.OracleEBS._2008._05.TableViewRecord.APPS.MS_SAMPLE_EMPLOYEE.SelectRecord[] DATA) {  
        this.DATA = DATA;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a><span data-ttu-id="e5fd8-177">Classe de Service WCF</span><span class="sxs-lookup"><span data-stu-id="e5fd8-177">WCF Service Class</span></span>  
 <span data-ttu-id="e5fd8-178">Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également un fichier qui a un stub pour la classe de service WCF implémenté le contrat de service (interface).</span><span class="sxs-lookup"><span data-stu-id="e5fd8-178">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="e5fd8-179">Le nom du fichier est OracleEBSBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-179">The name of the file is OracleEBSBindingService.cs.</span></span> <span data-ttu-id="e5fd8-180">Vous pouvez insérer la logique pour traiter les **interrogation** opération directement dans cette classe.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-180">You can insert the logic to process the **Poll** operation directly into this class.</span></span> <span data-ttu-id="e5fd8-181">Le code suivant illustre la classe de service WCF générée par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5fd8-181">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
```  
namespace OracleEBSBindingNamespace {  
  
    public class OracleEBSBindingService : InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE) of message Poll   
        // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
        public virtual void Poll(Poll request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-inbound-messages-for-the-poll-operation-using-a-select-statement"></a><span data-ttu-id="e5fd8-182">Réception des Messages entrants pour l’opération d’interrogation à l’aide d’une instruction SELECT</span><span class="sxs-lookup"><span data-stu-id="e5fd8-182">Receiving Inbound Messages for the Poll Operation Using a SELECT Statement</span></span>  
 <span data-ttu-id="e5fd8-183">Cette section fournit des instructions sur la façon d’écrire une application .NET pour recevoir des messages entrants d’interrogation à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5fd8-183">This section provides instructions on how to write a .NET application to receive inbound polling messages using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
#### <a name="to-receive-polling-messages-using-a-select-statement"></a><span data-ttu-id="e5fd8-184">Pour recevoir des messages d’interrogation à l’aide d’une instruction SELECT</span><span class="sxs-lookup"><span data-stu-id="e5fd8-184">To receive polling messages using a SELECT statement</span></span>  
  
1.  <span data-ttu-id="e5fd8-185">Utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer un contrat de service WCF (interface) et des classes d’assistance pour le **interrogation** opération sur la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-185">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **Poll** operation on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="e5fd8-186">Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="e5fd8-186">For more information, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span> <span data-ttu-id="e5fd8-187">Vous pouvez éventuellement spécifier les propriétés de liaison lors de la génération les classes d’assistance et de contrat de service.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-187">You can optionally specify the binding properties while generating the service contract and helper classes.</span></span> <span data-ttu-id="e5fd8-188">Cela garantit qu’ils sont correctement définies dans le fichier de configuration généré.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-188">This guarantees that they are properly set in the generated configuration file.</span></span>  
  
2.  <span data-ttu-id="e5fd8-189">Implémenter un service WCF à partir de l’interface et assistance des classes générées à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-189">Implement a WCF service from the interface and helper classes generated in step 1.</span></span> <span data-ttu-id="e5fd8-190">Le **interrogation** méthode de cette classe peut lever une exception pour annuler la transaction d’interrogation, si une erreur est rencontrée, le traitement des données reçues à partir de la **interrogation** opération ; dans le cas contraire, la méthode ne pas retourner une valeur.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-190">The **Poll** method of this class can throw an exception to abort the polling transaction, if an error is encountered processing the data received from the **Poll** operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="e5fd8-191">Vous devez attribuer la classe de service WCF comme suit :</span><span class="sxs-lookup"><span data-stu-id="e5fd8-191">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     <span data-ttu-id="e5fd8-192">Dans le **interrogation** (méthode), vous pouvez directement implémenter votre logique d’application.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-192">Within the **Poll** method, you can implement your application logic directly.</span></span> <span data-ttu-id="e5fd8-193">Cette classe peut être trouvée dans OracleEBSBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-193">This class can be found in OracleEBSBindingService.cs.</span></span> <span data-ttu-id="e5fd8-194">Ce code dans cet exemple montre comment des classes le **OracleEBSBindingService** classe.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-194">This code in this example sub-classes the **OracleEBSBindingService** class.</span></span> <span data-ttu-id="e5fd8-195">Dans ce code, le message de l’interrogation reçu et est écrit dans la console.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-195">In this code, the polling message received and is written to the console.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void Poll(Poll request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Emp No\tName\tDesignation\tSalary");  
            for (int i = 0; i < request.DATA.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.DATA[i].EMP_NO,  
                request.DATA[i].NAME,  
                request.DATA[i].DESIGNATION,  
                request.DATA[i].SALARY);  
            }  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="e5fd8-196">Vous devez implémenter la classe suivante pour éviter de transmettre des informations d’identification en tant que partie de l’URI.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-196">You must implement the following class to avoid passing credentials as part of the URI.</span></span> <span data-ttu-id="e5fd8-197">Dans la dernière partie de l’application, vous serez instancier cette classe à transmettre les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-197">In the latter part of the application, you will instantiate this class to pass on the credentials.</span></span>  
  
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
  
4.  <span data-ttu-id="e5fd8-198">Créer un **OracleEBSBinding** et configurer l’opération d’interrogation en spécifiant les propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-198">Create an **OracleEBSBinding** and configure the polling operation by specifying the binding properties.</span></span> <span data-ttu-id="e5fd8-199">Ce faire, vous pouvez soit explicitement dans le code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-199">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="e5fd8-200">Au minimum, vous devez spécifier le **InboundOperationType**, **PolledDataAvailableStatement**, **PollingInput**, et **PollingAction**propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-200">At a minimum, you must specify the **InboundOperationType**, **PolledDataAvailableStatement**, **PollingInput**, and **PollingAction** binding properties.</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
    binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
    binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
    binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
    ```  
  
5.  <span data-ttu-id="e5fd8-201">Étant donné que vous demandent une table d’interface, vous devez également définir le contexte des applications.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-201">Because you are polling an interface table, you must also set the applications context.</span></span> <span data-ttu-id="e5fd8-202">Pour plus d’informations sur le contexte de l’application et les propriétés de liaison requises pour le contexte de l’application de paramètre, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span><span class="sxs-lookup"><span data-stu-id="e5fd8-202">For more information about application context and the binding properties required for setting application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
6.  <span data-ttu-id="e5fd8-203">Spécifiez les informations d’identification Oracle E-Business Suite en instanciant le **PollingCredentials** classe que vous avez créé à l’étape 3.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-203">Specify Oracle E-Business Suite credentials by instantiating the **PollingCredentials** class you created in Step 3.</span></span>  
  
    ```  
    PollingCredentials credentials = new PollingCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
    ```  
  
7.  <span data-ttu-id="e5fd8-204">Créez une instance du service WCF créé à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-204">Create an instance of the WCF service created in step 2.</span></span>  
  
    ```  
    // create service instance  
    PollingService service = new PollingService();  
    ```  
  
8.  <span data-ttu-id="e5fd8-205">Créez une instance de **System.ServiceModel.ServiceHost** à l’aide du service WCF et l’URI de connexion de base.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-205">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="e5fd8-206">L’URI de la connexion de base ne peut pas contenir l’ID d’entrée, s’il est spécifié.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-206">The base connection URI cannot contain the inbound ID, if specified.</span></span> <span data-ttu-id="e5fd8-207">Vous devez également passer les informations d’identification ici.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-207">You must also pass the credentials here.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
9. <span data-ttu-id="e5fd8-208">Ajouter un point de terminaison de service à l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-208">Add a service endpoint to the service host.</span></span> <span data-ttu-id="e5fd8-209">Pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="e5fd8-209">To do this:</span></span>  
  
    -   <span data-ttu-id="e5fd8-210">Utilisez la liaison créée à l’étape 4.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-210">Use the binding created in step 4.</span></span>  
  
    -   <span data-ttu-id="e5fd8-211">Spécifiez une URI qui contient les informations d’identification de connexion et, si nécessaire, un ID d’entrée.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-211">Specify a connection URI that contains credentials and, if required, an inbound ID.</span></span>  
  
    -   <span data-ttu-id="e5fd8-212">Spécifiez le contrat en tant que « InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE » pour interroger la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-212">Specify the contract as "InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE" to poll the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
    ```  
    // Add service endpoint: be sure to specify InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE as the contract  
    Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
    serviceHost.AddServiceEndpoint("InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE", binding, ConnectionUri);  
    ```  
  
10. <span data-ttu-id="e5fd8-213">Pour recevoir les données d’interrogation, ouvrez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-213">To receive polling data, open the service host.</span></span> <span data-ttu-id="e5fd8-214">L’adaptateur retourne les données chaque fois que la requête retourne un jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-214">The adapter will return data whenever the query returns a result set.</span></span>  
  
    ```  
    // Open the service host to begin polling  
    serviceHost.Open();  
    ```  
  
11. <span data-ttu-id="e5fd8-215">Pour mettre fin à l’interrogation, fermez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-215">To terminate polling, close the service host.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e5fd8-216">La carte va continuer à interroger jusqu'à ce que l’hôte de service est fermé.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-216">The adapter will continue to poll until the service host is closed.</span></span>  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a><span data-ttu-id="e5fd8-217">Exemple</span><span class="sxs-lookup"><span data-stu-id="e5fd8-217">Example</span></span>  
 <span data-ttu-id="e5fd8-218">L’exemple suivant montre une application d’interrogation qui interroge la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-218">The following example shows a polling application that polls the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="e5fd8-219">Le **PollingInput** propriété contient l’instruction select qui lit toutes les données de la table MS_SAMPLE_EMPLOYEE et l’instruction de sondage post supprime toutes les données de la même table.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-219">The **PollingInput** property contains the select statement that reads all the data from the MS_SAMPLE_EMPLOYEE table and the post poll statement deletes all the data from the same table.</span></span> <span data-ttu-id="e5fd8-220">Le premier message d’interrogation fournit tous les enregistrements dans la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-220">The first polling message gives all the records from the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="e5fd8-221">Les messages suivants d’interrogation ne contient pas d’enregistrements, car l’instruction de sondage post supprime les enregistrements.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-221">Subsequent polling messages will not contain any records because the post poll statement deletes the records.</span></span> <span data-ttu-id="e5fd8-222">Jusqu'à ce que davantage de données est ajouté à la table d’interface MS_SAMPLE_EMPLOYEE, vous n’obtiendrez pas les messages d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-222">Until more data is added to the MS_SAMPLE_EMPLOYEE interface table, you will not get any polling messages.</span></span> <span data-ttu-id="e5fd8-223">Par conséquent, vous devez remplir de nouveau la table d’interface MS_SAMPLE_EMPLOYEE avec nouveaux enregistrements.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-223">So, you must repopulate the MS_SAMPLE_EMPLOYEE interface table with new records.</span></span> <span data-ttu-id="e5fd8-224">Vous pouvez le faire en exécutant le script insert_apps_data.sql fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-224">You can do so by running the insert_apps_data.sql script provided with the samples.</span></span> <span data-ttu-id="e5fd8-225">Une fois que vous exécutez ce script, l’opération d’interrogation suivante permet d’extraire les nouveaux enregistrements insérés dans la table.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-225">After you run this script, the next polling operation will fetch the new records inserted into the table.</span></span> <span data-ttu-id="e5fd8-226">La carte continuera d’interroger jusqu'à ce que vous fermez l’hôte de service en appuyant sur `<RETURN>`.</span><span class="sxs-lookup"><span data-stu-id="e5fd8-226">The adapter will continue to poll until you close the service host by pressing `<RETURN>`.</span></span>  
  
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
  
namespace SelectPolling_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void Poll(Poll request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Emp No\tName\tDesignation\tSalary");  
            for (int i = 0; i < request.DATA.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.DATA[i].EMP_NO,  
                request.DATA[i].NAME,  
                request.DATA[i].DESIGNATION,  
                request.DATA[i].SALARY);  
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
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
                binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
                binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
                binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
                binding.OracleUserName = "myOracleEBSUserName";  
                binding.OraclePassword = "myOracleEBSPassword";  
                binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
  
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
                serviceHost.AddServiceEndpoint("InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE", binding, ConnectionUri);  
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
  
## <a name="see-also"></a><span data-ttu-id="e5fd8-227">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5fd8-227">See Also</span></span>  
 [<span data-ttu-id="e5fd8-228">Interrogation Oracle E-Business Suite à l’aide du modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="e5fd8-228">Poll Oracle E-Business Suite using the WCF service model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-the-wcf-service-model.md)
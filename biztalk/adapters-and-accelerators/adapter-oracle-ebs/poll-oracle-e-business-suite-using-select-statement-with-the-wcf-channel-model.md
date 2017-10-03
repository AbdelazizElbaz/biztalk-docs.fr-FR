---
title: "Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT avec le modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 495b9010-856f-4782-bd19-1522bc3eb950
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71f689b035f926e0fd5bbdaa159e1450fbad92b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-e-business-suite-using-select-statement-with-the-wcf-channel-model"></a><span data-ttu-id="9f2f1-102">Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT avec le modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="9f2f1-102">Poll Oracle E-Business Suite using SELECT statement with the WCF channel model</span></span>
<span data-ttu-id="9f2f1-103">Vous pouvez configurer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des messages de modification de données périodiques à l’aide d’une instruction SELECT pour l’interrogation de façon permanente les tables d’interface, interface, des vues, des tables et des vues dans Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-103">You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive periodic data-change messages by using a SELECT statement to continuously poll the interface tables, interface views, tables and views in Oracle E-Business Suite.</span></span> <span data-ttu-id="9f2f1-104">Vous pouvez spécifier une instruction SELECT comme une instruction d’interrogation de l’adaptateur s’exécute périodiquement pour Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-104">You can specify a SELECT statement as a polling statement that the adapter executes periodically to poll Oracle E-Business Suite.</span></span> <span data-ttu-id="9f2f1-105">Vous pouvez également spécifier un bloc de code après interrogation PL/SQL que l’adaptateur s’exécute après l’exécution de l’instruction d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-105">You can also specify a post-poll PL/SQL code block that the adapter executes after the polling statement is executed.</span></span>  
  
 <span data-ttu-id="9f2f1-106">Pour activer l’interrogation, vous devez spécifier certaines propriétés de liaison comme décrit dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-106">To enable polling, you must specify certain binding properties as described in this topic.</span></span> <span data-ttu-id="9f2f1-107">Pour plus d’informations sur la façon dont l’adaptateur prend en charge d’interrogation, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span><span class="sxs-lookup"><span data-stu-id="9f2f1-107">For more information about how the adapter supports polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  
  
## <a name="configuring-a-polling-operation-with-oracle-e-business-suite-adapter-binding-properties"></a><span data-ttu-id="9f2f1-108">Configuration d’une opération d’interrogation avec liaison des propriétés de l’adaptateur Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="9f2f1-108">Configuring a Polling Operation with Oracle E-Business Suite Adapter Binding Properties</span></span>  
 <span data-ttu-id="9f2f1-109">Le tableau suivant récapitule les [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] messages de modification des propriétés de liaison que vous utilisez pour configurer l’adaptateur pour recevoir des données.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-109">The following table summarizes the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding properties that you use to configure the adapter to receive data change messages.</span></span> <span data-ttu-id="9f2f1-110">Vous devez spécifier ces propriétés de liaison lors de l’exécution de l’application d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-110">You must specify these binding properties while running the polling application.</span></span>  
  
|<span data-ttu-id="9f2f1-111">Propriété de liaison</span><span class="sxs-lookup"><span data-stu-id="9f2f1-111">Binding Property</span></span>|<span data-ttu-id="9f2f1-112"> Description</span><span class="sxs-lookup"><span data-stu-id="9f2f1-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="9f2f1-113">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="9f2f1-113">**InboundOperationType**</span></span>|<span data-ttu-id="9f2f1-114">Spécifie si vous souhaitez effectuer **d’interrogation** ou **Notification** opération entrante.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-114">Specifies whether you want to perform **Polling** or **Notification** inbound operation.</span></span> <span data-ttu-id="9f2f1-115">Valeur par défaut est **d’interrogation**.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-115">Default is **Polling**.</span></span>|  
|<span data-ttu-id="9f2f1-116">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="9f2f1-116">**PolledDataAvailableStatement**</span></span>|<span data-ttu-id="9f2f1-117">Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-117">Specifies the SQL statement that the adapter executes to determine whether any data is available for polling.</span></span> <span data-ttu-id="9f2f1-118">Uniquement si un enregistrement n’est disponible, l’instruction SELECT que vous spécifiez pour le **PollingInput** liaison de la propriété sera exécutée.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-118">Only if a record is available, the SELECT statement you specify for the **PollingInput** binding property will be executed.</span></span>|  
|<span data-ttu-id="9f2f1-119">**PollingInterval**</span><span class="sxs-lookup"><span data-stu-id="9f2f1-119">**PollingInterval**</span></span>|<span data-ttu-id="9f2f1-120">Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-120">Specifies the interval, in seconds, at which the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="9f2f1-121">La valeur par défaut est 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-121">The default is 30 seconds.</span></span> <span data-ttu-id="9f2f1-122">L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-122">The polling interval determines the time interval between successive polls.</span></span> <span data-ttu-id="9f2f1-123">Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur est en veille pendant le temps restant dans l’intervalle.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-123">If the statement is executed within the specified interval, the adapter sleeps for the remaining time in the interval.</span></span>|  
|<span data-ttu-id="9f2f1-124">**PollingInput**</span><span class="sxs-lookup"><span data-stu-id="9f2f1-124">**PollingInput**</span></span>|<span data-ttu-id="9f2f1-125">Spécifie l’instruction d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-125">Specifies the polling statement.</span></span> <span data-ttu-id="9f2f1-126">Pour interroger à l’aide d’une instruction SELECT, vous devez spécifier une instruction SELECT pour cette propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-126">To poll using a SELECT statement, you must specify a SELECT statement for this binding property.</span></span> <span data-ttu-id="9f2f1-127">La valeur par défaut est null.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-127">The default is null.</span></span><br /><br /> <span data-ttu-id="9f2f1-128">Vous devez spécifier une valeur pour **PollingInput** propriété pour activer l’interrogation de liaison.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-128">You must specify a value for **PollingInput** binding property to enable polling.</span></span> <span data-ttu-id="9f2f1-129">L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-129">The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.</span></span>|  
|<span data-ttu-id="9f2f1-130">**PollingAction**</span><span class="sxs-lookup"><span data-stu-id="9f2f1-130">**PollingAction**</span></span>|<span data-ttu-id="9f2f1-131">Spécifie l’action pour l’opération d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-131">Specifies the action for the polling operation.</span></span> <span data-ttu-id="9f2f1-132">Vous pouvez déterminer l’action d’interrogation de l’interface de service généré pour l’opération en utilisant la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f2f1-132">You can determine the polling action from the service interface generated for the operation using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span>|  
|<span data-ttu-id="9f2f1-133">**PostPollStatement**</span><span class="sxs-lookup"><span data-stu-id="9f2f1-133">**PostPollStatement**</span></span>|<span data-ttu-id="9f2f1-134">Spécifie un bloc d’instructions qui est exécuté après l’instruction spécifiée par le **PollingInput** propriété de liaison est exécutée.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-134">Specifies a statement block that is executed after the statement specified by the **PollingInput** binding property is executed.</span></span>|  
|<span data-ttu-id="9f2f1-135">**PollWhileDataFound**</span><span class="sxs-lookup"><span data-stu-id="9f2f1-135">**PollWhileDataFound**</span></span>|<span data-ttu-id="9f2f1-136">Spécifie si le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignore l’intervalle d’interrogation et exécute en permanence l’instruction d’interrogation, si les données sont disponibles dans la table interrogée.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-136">Specifies whether the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignores the polling interval and continuously executes the polling statement, if data is available in the table being polled.</span></span> <span data-ttu-id="9f2f1-137">Si aucune donnée n’est disponible dans la table, l’adaptateur revient pour exécuter l’instruction d’interrogation à l’intervalle d’interrogation spécifié.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-137">If no data is available in the table, the adapter reverts to execute the polling statement at the specified polling interval.</span></span> <span data-ttu-id="9f2f1-138">La valeur par défaut est False.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-138">Default is false.</span></span>|  
  
 <span data-ttu-id="9f2f1-139">Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="9f2f1-139">For a more complete description of these properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span> <span data-ttu-id="9f2f1-140">Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour interroger la base de données Oracle, lire le reste de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-140">For a complete description of how to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll the Oracle database, read the remainder of this topic.</span></span>  
  
## <a name="how-this-topic-demonstrates-polling"></a><span data-ttu-id="9f2f1-141">Comment cette rubrique illustre l’interrogation</span><span class="sxs-lookup"><span data-stu-id="9f2f1-141">How This Topic Demonstrates Polling</span></span>  
 <span data-ttu-id="9f2f1-142">Dans cette rubrique, pour illustrer comment le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge la réception de données modifier des messages à l’aide des instructions SELECT, vous continuez d’interroger le **MS_SAMPLE_EMPLOYEE** table d’interface dans le **bibliothèque d’objets Application**application.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-142">In this topic, to demonstrate how the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports receiving data change messages using SELECT statements, you poll the **MS_SAMPLE_EMPLOYEE** interface table in the **Application Object Library** application.</span></span> <span data-ttu-id="9f2f1-143">Cette table est créée lorsque vous exécutez le script create_apps_artifacts.sql fourni avec les exemples pour créer ces objets dans Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-143">This table is created when you run the create_apps_artifacts.sql script provided with the samples to create these objects in Oracle E-Business Suite.</span></span>  
  
 <span data-ttu-id="9f2f1-144">Pour illustrer une opération d’interrogation, nous les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9f2f1-144">To demonstrate a polling operation, we do the following:</span></span>  
  
-   <span data-ttu-id="9f2f1-145">Spécifiez une instruction SELECT pour le **PolledDataAvailableStatement** liaison de propriété pour déterminer où l’interface table interrogés (MS_SAMPLE_EMPLOYEE) comporte des données.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-145">Specify a SELECT statement for the **PolledDataAvailableStatement** binding property to determine where the interface table being polled (MS_SAMPLE_EMPLOYEE) has any data.</span></span> <span data-ttu-id="9f2f1-146">Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :</span><span class="sxs-lookup"><span data-stu-id="9f2f1-146">In this example, you can set this binding property as:</span></span>  
  
    ```  
    SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     <span data-ttu-id="9f2f1-147">Cela garantit que l’adaptateur s’exécute l’instruction d’interrogation uniquement lorsque la table d’interface MS_SAMPLE_EMPLOYEE a des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-147">This ensures that the adapter executes the polling statement only when the MS_SAMPLE_EMPLOYEE interface table has some records.</span></span>  
  
-   <span data-ttu-id="9f2f1-148">Spécifiez une instruction SELECT pour le **PollingInput** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-148">Specify a SELECT statement for the **PollingInput** binding property.</span></span> <span data-ttu-id="9f2f1-149">Cette instruction récupère toutes les lignes dans la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-149">This statement retrieves all the rows in the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="9f2f1-150">Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :</span><span class="sxs-lookup"><span data-stu-id="9f2f1-150">In this example, you can set this binding property as:</span></span>  
  
    ```  
    SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9f2f1-151">Pour plus d’informations sur la clause FOR UPDATE utilisée dans l’instruction SELECT, consultez [recevoir des messages d’interrogation de données modifiées à partir d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="9f2f1-151">For information about the FOR UPDATE clause used in the SELECT statement, see [Receive polling-based data-changed messages from Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md).</span></span>  
  
-   <span data-ttu-id="9f2f1-152">Spécifiez une instruction DELETE en tant que partie de la **PostPollStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-152">Specify a DELETE statement as part of the **PostPollStatement** binding property.</span></span> <span data-ttu-id="9f2f1-153">Cette instruction supprime toutes les données à partir de la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-153">This statement will delete all data from MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="9f2f1-154">Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :</span><span class="sxs-lookup"><span data-stu-id="9f2f1-154">In this example, you can set this binding property as:</span></span>  
  
    ```  
    DELETE FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     <span data-ttu-id="9f2f1-155">Une fois que cela se produit, la prochaine fois que l’instruction spécifiée pour **PollingInput** sera exécutée, elle ne permet pas d’extraire des données.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-155">After this happens, the next time the statement specified for **PollingInput** will be executed, it will not fetch any data.</span></span>  
  
-   <span data-ttu-id="9f2f1-156">Jusqu'à ce que davantage de données est ajouté à la table d’interface MS_SAMPLE_EMPLOYEE, vous n’obtiendrez pas tous les messages d’interrogation, donc vous devez remplir de nouveau la table d’interface MS_SAMPLE_EMPLOYEE avec nouveaux enregistrements.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-156">Until more data is added to the MS_SAMPLE_EMPLOYEE interface table, you will not get any polling messages so you must repopulate the MS_SAMPLE_EMPLOYEE interface table with new records.</span></span> <span data-ttu-id="9f2f1-157">Vous pouvez le faire en exécutant le script insert_apps_data.sql fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-157">You can do so by running the insert_apps_data.sql script provided with the samples.</span></span> <span data-ttu-id="9f2f1-158">Une fois que vous exécutez ce script, l’opération d’interrogation suivante permet d’extraire les nouveaux enregistrements insérés dans la table.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-158">After you run this script, the next polling operation will fetch the new records inserted into the table.</span></span>  
  
## <a name="consuming-the-polling-request-message"></a><span data-ttu-id="9f2f1-159">Le message de demande d’interrogation</span><span class="sxs-lookup"><span data-stu-id="9f2f1-159">Consuming the Polling Request Message</span></span>  
 <span data-ttu-id="9f2f1-160">L’adaptateur appelle l’opération d’interrogation sur votre code pour interroger Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-160">The adapter invokes the polling operation on your code to poll the Oracle E-Business Suite.</span></span> <span data-ttu-id="9f2f1-161">Autrement dit, l’adaptateur envoie un message de demande d’interrogation qui s’affiche sur une forme de canal IInputChannel.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-161">That is, the adapter sends a polling request message that you receive over an IInputChannel channel shape.</span></span> <span data-ttu-id="9f2f1-162">Le message de demande d’interrogation contient le jeu de résultats de la requête spécifiée par la **PollingInput** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-162">The polling request message contains the result set of the query specified by the **PollingInput** binding property.</span></span> <span data-ttu-id="9f2f1-163">Vous pouvez utiliser le message d’interrogation de deux manières :</span><span class="sxs-lookup"><span data-stu-id="9f2f1-163">You can consume the polling message in one of two ways:</span></span>  
  
-   <span data-ttu-id="9f2f1-164">Pour consommer le message à l’aide de la valeur du nœud de diffusion en continu, vous devez appeler la **WriteBodyContents** méthode sur la réponse de message et lui passer une **XmlDictionaryWriter** qui implémente la diffusion en continu de la valeur du nœud.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-164">To consume the message using node-value streaming, you must call the **WriteBodyContents** method on the response message and pass it an **XmlDictionaryWriter** that implements node-value streaming.</span></span>  
  
-   <span data-ttu-id="9f2f1-165">Pour consommer le message à l’aide du nœud de diffusion en continu, vous pouvez appeler **GetReaderAtBodyContents** sur le message de réponse pour obtenir un **XmlReader**.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-165">To consume the message using node streaming, you can call **GetReaderAtBodyContents** on the response message to get an **XmlReader**.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="9f2f1-166">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="9f2f1-166">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="9f2f1-167">Les exemples de cette rubrique interrogent la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-167">The examples in this topic poll the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="9f2f1-168">Un script pour générer la table est fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-168">A script to generate the table is supplied with the samples.</span></span> <span data-ttu-id="9f2f1-169">Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="9f2f1-169">For more information about the samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="9f2f1-170">Un exemple, **SelectPolling_ChannelModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-170">A sample, **SelectPolling_ChannelModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="receiving-inbound-messages-for-polling-operation-using-the-wcf-channel-model"></a><span data-ttu-id="9f2f1-171">Réception des Messages entrants pour l’opération d’interrogation à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="9f2f1-171">Receiving Inbound Messages for Polling Operation Using the WCF Channel Model</span></span>  
 <span data-ttu-id="9f2f1-172">Cette section fournit des instructions sur la façon d’écrire une application .NET (modèle de canal) pour recevoir des messages entrants d’interrogation à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f2f1-172">This section provides instructions on how to write a .NET application (channel model) to receive inbound polling messages using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
#### <a name="to-receive-polling-messages-from-the-adapter"></a><span data-ttu-id="9f2f1-173">Pour recevoir des messages de l’interrogation de la carte</span><span class="sxs-lookup"><span data-stu-id="9f2f1-173">To receive polling messages from the adapter</span></span>  
  
1.  <span data-ttu-id="9f2f1-174">Créez un projet Microsoft Visual C#® dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f2f1-174">Create a Microsoft Visual C#® project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="9f2f1-175">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-175">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="9f2f1-176">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleEBS`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, et `System.Runtime.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-176">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, and `System.Runtime.Serialization`.</span></span>  
  
3.  <span data-ttu-id="9f2f1-177">Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="9f2f1-177">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Description`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  <span data-ttu-id="9f2f1-178">Spécifiez l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-178">Specify a connection URI.</span></span> <span data-ttu-id="9f2f1-179">Pour plus d’informations sur l’URI de connexion de l’adaptateur, consultez [créer l’URI de connexion Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="9f2f1-179">For more information about the adapter connection URI, see [Create the Oracle E-Business Suite connection URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md).</span></span>  
  
    ```  
    Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
    ```  
  
5.  <span data-ttu-id="9f2f1-180">Créez une instance de **OracleEBSBinding** et définissez les propriétés de liaison requises pour configurer l’interrogation.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-180">Create an instance of **OracleEBSBinding** and set the binding properties required to configure polling.</span></span> <span data-ttu-id="9f2f1-181">Au minimum, vous devez définir le **InboundOperationType**, **PolledDataAvailableStatement**, **PollingInput**, et **PollingAction** propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-181">At a minimum you must set the **InboundOperationType**, **PolledDataAvailableStatement**, **PollingInput**, and **PollingAction** binding properties.</span></span> <span data-ttu-id="9f2f1-182">Pour plus d’informations sur les propriétés utilisées pour configurer l’interrogation de liaison, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span><span class="sxs-lookup"><span data-stu-id="9f2f1-182">For more information about binding properties used to configure polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
    binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
    binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
    binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
    ```  
  
6.  <span data-ttu-id="9f2f1-183">Étant donné que vous demandent une table d’interface, vous devez également définir le contexte des applications.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-183">Because you are polling an interface table, you must also set the applications context.</span></span> <span data-ttu-id="9f2f1-184">Pour plus d’informations sur le contexte de l’application et les propriétés de liaison requises pour le contexte de l’application de paramètre, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span><span class="sxs-lookup"><span data-stu-id="9f2f1-184">For more information about application context and binding properties required for setting application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
    ```  
    binding.OracleUserName = "<Enter user name here>";  
    binding.OraclePassword = "<Enter password here>";  
    binding.OracleEBSResponsibilityName = "<Enter responsibility here>";  
    ```  
  
7.  <span data-ttu-id="9f2f1-185">Créer une collection de paramètres de liaison et définir les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-185">Create a binding parameter collection and set the credentials.</span></span>  
  
    ```  
    ClientCredentials credentials = new ClientCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
  
    BindingParameterCollection bindingParams = new BindingParameterCollection();  
    bindingParams.Add(credentials);  
    ```  
  
8.  <span data-ttu-id="9f2f1-186">Créer un écouteur de canal et l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-186">Create a channel listener and open it.</span></span> <span data-ttu-id="9f2f1-187">Vous créez l’écouteur en appelant **BuildChannelListener < IInputChannel\>**  méthode sur le **OracleEBSBinding**.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-187">You create the listener by invoking **BuildChannelListener<IInputChannel\>** method on the **OracleEBSBinding**.</span></span>  
  
    ```  
    IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
    listener.Open();  
    ```  
  
9. <span data-ttu-id="9f2f1-188">Obtenir un **IInputChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur et ouvrez-le.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-188">Get an **IInputChannel** channel by invoking the **AcceptChannel** method on the listener and open it.</span></span>  
  
    ```  
    IInputChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  
  
10. <span data-ttu-id="9f2f1-189">Appeler **réception** sur le canal pour obtenir le message entrant suivant à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-189">Invoke **Receive** on the channel to get the next inbound message from the adapter.</span></span>  
  
    ```  
    Message message = channel.Receive();  
    ```  
  
11. <span data-ttu-id="9f2f1-190">Utiliser le jeu de résultats retourné par l’opération entrante.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-190">Consume the result set returned by the inbound operation.</span></span> <span data-ttu-id="9f2f1-191">Vous pouvez consommer le message en utilisant un **XmlReader** ou **XmlDictionaryWriter**.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-191">You can consume the message using either an **XmlReader** or an **XmlDictionaryWriter**.</span></span>  
  
    ```  
    XmlReader reader = message.GetReaderAtBodyContents();  
    ```  
  
12. <span data-ttu-id="9f2f1-192">Fermer le canal lorsque vous avez terminé le traitement de la demande.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-192">Close the channel when you have completed processing the request.</span></span>  
  
    ```  
    channel.Close()  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9f2f1-193">Vous devez fermer le canal une fois que vous avez terminé le traitement de l’opération entrante.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-193">You must close the channel after you have finished processing the inbound operation.</span></span> <span data-ttu-id="9f2f1-194">Échec de fermer le canal peut affecter le comportement de votre code.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-194">Failure to close the channel may affect the behavior of your code.</span></span>  
  
13. <span data-ttu-id="9f2f1-195">Fermer l’écouteur lorsque vous avez terminé la réception de messages de données modifiées.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-195">Close the listener when you are finished receiving data-changed messages.</span></span>  
  
    ```  
    listener.Close()  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9f2f1-196">Fermeture de l’écouteur ne ferme pas les canaux créés à l’aide de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-196">Closing the listener does not close channels created using the listener.</span></span> <span data-ttu-id="9f2f1-197">Vous devez fermer explicitement chaque canal créé à l’aide de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-197">You must explicitly close each channel created using the listener.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9f2f1-198">Exemple</span><span class="sxs-lookup"><span data-stu-id="9f2f1-198">Example</span></span>  
 <span data-ttu-id="9f2f1-199">L’exemple suivant montre une application d’interrogation qui interroge la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-199">The following example shows a polling application that polls the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="9f2f1-200">Le **PollingInput** propriété contient l’instruction select qui lit toutes les données de la table MS_SAMPLE_EMPLOYEE et l’instruction de sondage post supprime toutes les données de la même table.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-200">The **PollingInput** property contains the select statement that reads all the data from the MS_SAMPLE_EMPLOYEE table and the post poll statement deletes all the data from the same table.</span></span> <span data-ttu-id="9f2f1-201">Le message d’interrogation est écrit dans `C:\PollingOutput.xml`.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-201">The polling message is written to `C:\PollingOutput.xml`.</span></span>  
  
 <span data-ttu-id="9f2f1-202">Les messages suivants d’interrogation ne contient pas d’enregistrements jusqu'à ce que davantage de données est ajouté à la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-202">Subsequent polling messages will not contain any records until more data is added to the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="9f2f1-203">Vous pouvez le faire en exécutant le script insert_apps_data.sql fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-203">You can do so by running the insert_apps_data.sql script provided with the samples.</span></span> <span data-ttu-id="9f2f1-204">Une fois que vous exécutez ce script, l’opération d’interrogation suivante permet d’extraire les nouveaux enregistrements insérés dans la table.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-204">After you run this script, the next polling operation will fetch the new records inserted into the table.</span></span> <span data-ttu-id="9f2f1-205">La carte continuera d’interroger jusqu'à ce que vous fermez l’hôte de service en appuyant sur \<retourner >.</span><span class="sxs-lookup"><span data-stu-id="9f2f1-205">The adapter will continue to poll until you close the service host by pressing \<RETURN>.</span></span>  
  
```  
using System;  
using Microsoft.Adapters.OracleEBS;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Xml;  
  
namespace SelectPolling_ChannelModel  
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
  
                OracleEBSBinding binding = new OracleEBSBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
                binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
                binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
                binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
                binding.OracleUserName = "<Enter user name here>";  
                binding.OraclePassword = "<Enter password here>";  
                binding.OracleEBSResponsibilityName = "<Enter responsibility here>";  
  
                Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name?");  
  
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
                Console.ReadLine();  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                    Console.ReadLine();  
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
  
## <a name="see-also"></a><span data-ttu-id="9f2f1-206">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f2f1-206">See Also</span></span>  
 [<span data-ttu-id="9f2f1-207">Développer des applications d’Oracle E-Business Suite à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="9f2f1-207">Develop Oracle E-Business Suite applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)
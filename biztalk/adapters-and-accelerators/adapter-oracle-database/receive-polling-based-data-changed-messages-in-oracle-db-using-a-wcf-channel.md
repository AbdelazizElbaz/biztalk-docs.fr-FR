---
title: "Recevoir des Messages d’interrogation de données modifiées dans la base de données Oracle à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF channel model, receiving polling-based messages
- how to, receive polling-based messages by using the WCF channel model
ms.assetid: 13f501e4-cff7-497c-a9da-fdd6382c779f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01e1596c0b0676db916068ff9a33a8be9d6a9fa3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-based-data-changed-messages-in-oracle-database-using-the-wcf-channel-model"></a><span data-ttu-id="bb1dd-102">Recevoir des Messages d’interrogation de données modifiées dans la base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="bb1dd-102">Receive Polling-based Data-changed Messages in Oracle Database using the WCF Channel Model</span></span>
<span data-ttu-id="bb1dd-103">Vous pouvez configurer le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] pour interroger une table de base de données Oracle ou une vue pour toutes les modifications de données.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-103">You can configure the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] to poll an Oracle database table or view for any data changes.</span></span> <span data-ttu-id="bb1dd-104">Pour effectuer ce une opération d’interrogation, l’adaptateur exécute régulièrement une requête SQL sur une table Oracle ou d’une vue, suivi d’un bloc de code PL/SQL facultatif.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-104">To perform such a polling operation, the adapter periodically executes a SQL query against an Oracle table or view followed by an optional PL/SQL code block.</span></span> <span data-ttu-id="bb1dd-105">Les résultats de la requête SQL sont ensuite retournées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à votre code en tant que fortement typée jeu de résultats en une opération POLLINGSTMT entrante.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-105">The results of the SQL query are then returned by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to your code as a strongly-typed result set in an inbound POLLINGSTMT operation.</span></span> <span data-ttu-id="bb1dd-106">Pour plus d’informations sur le mécanisme utilisé pour configurer et effectuer d’interrogation sur Oracle de base de données à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [recevoir des messages d’interrogation de données modifiées dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="bb1dd-106">For more information about the mechanism used to configure and perform polling on an Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Receive polling-based data-changed messages in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).</span></span> <span data-ttu-id="bb1dd-107">Il est fortement recommandé de lire cette rubrique avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-107">It is strongly recommended that you read this topic before proceeding.</span></span>  
  
 <span data-ttu-id="bb1dd-108">Vous configurez le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à l’interrogation et de table de base de données Oracle ou de vue en définissant les propriétés de liaison sur une instance de **OracleDBBinding**.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-108">You configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to poll and Oracle database table or view by setting binding properties on an instance of **OracleDBBinding**.</span></span> <span data-ttu-id="bb1dd-109">Dans le modèle de canal WCF, vous utilisez ensuite cette liaison pour construire un écouteur de canal à partir de laquelle vous pouvez obtenir un **IInputChannel** doit recevoir l’opération POLLINGSTMT à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-109">In the WCF channel model, you then use this binding to build a channel listener from which you can get an **IInputChannel** channel to receive the POLLINGSTMT operation from the adapter.</span></span>  
  
 <span data-ttu-id="bb1dd-110">Pour une vue d’ensemble de la réception d’opérations à l’aide un **IInputChannel** dans WCF, consultez [de programmation au niveau du canal de Service](https://msdn.microsoft.com/library/ms789029.aspx).</span><span class="sxs-lookup"><span data-stu-id="bb1dd-110">For an overview of how to receive operations using an **IInputChannel** in WCF, see [Service Channel-Level Programming](https://msdn.microsoft.com/library/ms789029.aspx).</span></span> 
  
 <span data-ttu-id="bb1dd-111">Les sections de cette rubrique fournissent des informations pour vous aider à effectuer d’interrogation sur les tables de base de données Oracle et le modèle de canal de vues à l’aide de WCF.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-111">The sections in this topic provide information to help you perform polling on Oracle database tables and views using the WCF channel model.</span></span>  
  
## <a name="consuming-the-pollingstmt-request-message"></a><span data-ttu-id="bb1dd-112">Le message de demande POLLINGSTMT</span><span class="sxs-lookup"><span data-stu-id="bb1dd-112">Consuming the POLLINGSTMT request message</span></span>  
 <span data-ttu-id="bb1dd-113">L’adaptateur appelle l’opération POLLINGSTMT sur votre code pour interroger la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-113">The adapter invokes the POLLINGSTMT operation on your code to poll the Oracle database.</span></span> <span data-ttu-id="bb1dd-114">Autrement dit, l’adaptateur envoie un message de demande POLLINGSTMT que vous recevez via un **IInputChannel** forme de canal.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-114">That is, the adapter sends a POLLINGSTMT request message that you receive over an **IInputChannel** channel shape.</span></span> <span data-ttu-id="bb1dd-115">Le message de demande POLLINGSTMT contient le jeu de résultats de la requête spécifiée par la **PollingStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-115">The POLLINGSTMT request message contains the result set of the query specified by the **PollingStatement** binding property.</span></span> <span data-ttu-id="bb1dd-116">Vous pouvez utiliser le message POLLINGSTMT de deux manières :</span><span class="sxs-lookup"><span data-stu-id="bb1dd-116">You can consume the POLLINGSTMT message in one of two ways:</span></span>  
  
-   <span data-ttu-id="bb1dd-117">Pour consommer le message à l’aide de la valeur du nœud de diffusion en continu vous devez appeler la **WriteBodyContents** méthode sur la réponse de message et lui passer une **XmlDictionaryWriter** qui implémente la diffusion en continu de la valeur du nœud.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-117">To consume the message using node-value streaming you must call the **WriteBodyContents** method on the response message and pass it an **XmlDictionaryWriter** that implements node-value streaming.</span></span>  
  
-   <span data-ttu-id="bb1dd-118">Pour consommer le message à l’aide du nœud de diffusion en continu, vous pouvez appeler **GetReaderAtBodyContents** sur le message de réponse pour obtenir un **XmlReader**.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-118">To consume the message using node streaming you can call **GetReaderAtBodyContents** on the response message to get an **XmlReader**.</span></span>  
  
 <span data-ttu-id="bb1dd-119">Vous utilisez généralement la valeur du nœud de diffusion en continu pour consommer des jeux de résultats qui contiennent des colonnes de données Oracle LOB.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-119">You typically use node-value streaming to consume result sets that contain Oracle LOB data columns.</span></span>  
  
 <span data-ttu-id="bb1dd-120">Pour plus d’informations sur la structure du message de l’opération POLLINGSTMT, consultez [des schémas de Message pour les opérations d’interrogation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md).</span><span class="sxs-lookup"><span data-stu-id="bb1dd-120">For more information about the message structure of the POLLINGSTMT operation, see [Message Schemas for the Polling Operations](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md).</span></span>  
  
 <span data-ttu-id="bb1dd-121">Pour plus d’informations sur la façon dont [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge la diffusion en continu des données LOB, consultez [diffusion en continu des types de données dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="bb1dd-121">For more information about how the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports streaming on LOB data, see [Streaming large object data types in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).</span></span>  
  
 <span data-ttu-id="bb1dd-122">Pour plus d’informations sur l’implémentation de diffusion en continu dans votre code pour prendre en charge la diffusion en continu de bout en bout des données LOB de valeur de nœud, consultez [de diffusion en continu Oracle de base de données LOB données Types à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).</span><span class="sxs-lookup"><span data-stu-id="bb1dd-122">For more information about implementing node-value streaming in your code to support end-to-end streaming of LOB data, see [Streaming Oracle Database LOB Data Types Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="bb1dd-123">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="bb1dd-123">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="bb1dd-124">L’exemple dans cette rubrique utilise le SCOTT. Table ACCOUNTACTIVITY et SCOTT. ACCOUNT_PKG. Fonction PROCESS_ACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-124">The example in this topic uses the SCOTT.ACCOUNTACTIVITY table and the SCOTT.ACCOUNT_PKG.PROCESS_ACTIVITY function.</span></span> <span data-ttu-id="bb1dd-125">Un script pour générer ces artefacts est fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-125">A script to generate these artifacts is supplied with the samples.</span></span> <span data-ttu-id="bb1dd-126">L’exemple effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="bb1dd-126">The example performs the following operations:</span></span>  
  
-   <span data-ttu-id="bb1dd-127">Dans le cadre de l’instruction d’interrogation, sélectionne tous les enregistrements de la table ACCOUNTACTIVITY s’affiche sur la console.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-127">As part of the polling statement, selects all the records from the ACCOUNTACTIVITY table and displays on the console.</span></span>  
  
-   <span data-ttu-id="bb1dd-128">Dans le cadre de l’instruction de sondage post, l’exemple appelle la fonction PROCESS_ACTIVITY qui déplace tous les enregistrements à partir de la table ACCOUNTACTIVITY au tableau ACTIVITYHISTORY.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-128">As part of the post poll statement, the example invokes the PROCESS_ACTIVITY function that moves all the records from ACCOUNTACTIVITY table to ACTIVITYHISTORY table.</span></span>  
  
-   <span data-ttu-id="bb1dd-129">Les interrogations suivantes sur la table ACCOUNTACTIVITY ne retournent pas tous les enregistrements.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-129">Subsequent polls on the ACCOUNTACTIVITY table do not return any records.</span></span> <span data-ttu-id="bb1dd-130">Toutefois, si vous souhaitez que l’exemple de renvoyer plus d’enregistrements dans le cadre de l’opération d’interrogation, vous devez insérer des enregistrements dans la table ACCOUNTACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-130">However, if you want the example to return more records as part of the polling operation, you must insert some records in the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="bb1dd-131">Vous pouvez le faire en exécutant le script more_activity_data.sql fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-131">You can do so by running the more_activity_data.sql script provided with the samples.</span></span>  
  
 <span data-ttu-id="bb1dd-132">Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bb1dd-132">For more information about the samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="how-do-i-poll-an-oracle-database-using-an-iinputchannel"></a><span data-ttu-id="bb1dd-133">Comment pour interroger une base de données Oracle à l’aide d’un IInputChannel ?</span><span class="sxs-lookup"><span data-stu-id="bb1dd-133">How Do I Poll an Oracle Database Using an IInputChannel?</span></span>  
 <span data-ttu-id="bb1dd-134">Pour interroger une table de base de données Oracle ou une vue de recevoir des messages de modification de données à l’aide du modèle de canal WCF, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-134">To poll an Oracle database table or view to receive data-change messages using the WCF channel model, perform the following steps.</span></span>  
  
#### <a name="to-receive-data-changed-messages-using-an-iinputchannel"></a><span data-ttu-id="bb1dd-135">Pour recevoir des messages de modification de données à l’aide d’un IInputChannel</span><span class="sxs-lookup"><span data-stu-id="bb1dd-135">To receive data-changed messages using an IInputChannel</span></span>  
  
1.  <span data-ttu-id="bb1dd-136">Créez un projet Visual c# dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb1dd-136">Create a Visual C# project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="bb1dd-137">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-137">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="bb1dd-138">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleDB`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, et `System.Runtime.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-138">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleDB`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, and `System.Runtime.Serialization`.</span></span>  
  
3.  <span data-ttu-id="bb1dd-139">Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="bb1dd-139">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleDB`  
  
    -   `Microsoft.ServiceModel.Channels`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Description`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
    -   `System.Runtime.Serialization`  
  
    -   `System.IO`  
  
    -   `Microsoft.ServiceModel.Channels.Common`  
  
4.  <span data-ttu-id="bb1dd-140">Créez une instance de **OracleDBBinding** et définissez les propriétés de liaison requises pour configurer l’interrogation.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-140">Create an instance of **OracleDBBinding** and set the binding properties required to configure polling.</span></span> <span data-ttu-id="bb1dd-141">Au minimum, vous devez définir le **InboundOperationType**, **PollingStatement**, et **PollingInterval** propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-141">At a minimum you must set the **InboundOperationType**, **PollingStatement**, and **PollingInterval** binding properties.</span></span> <span data-ttu-id="bb1dd-142">Pour cet exemple, vous définissez également la **PostPollStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-142">For this example, you also set the **PostPollStatement** binding property.</span></span> <span data-ttu-id="bb1dd-143">Pour plus d’informations sur les propriétés utilisées pour configurer l’interrogation de liaison, consultez [recevoir des messages d’interrogation de données modifiées dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="bb1dd-143">For more information about binding properties used to configure polling, see [Receive polling-based data-changed messages in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).</span></span>  
  
    ```  
    OracleDBBinding binding = new OracleDBBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PollingInterval = 30;  
    binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
    binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;"  
    ```  
  
5.  <span data-ttu-id="bb1dd-144">Créer une collection de paramètres de liaison et définir les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-144">Create a binding parameter collection and set the credentials.</span></span>  
  
    ```  
    ClientCredentials credentials = new ClientCredentials();  
    credentials.UserName.UserName = "SCOTT";  
    credentials.UserName.Password = "TIGER";  
  
    BindingParameterCollection bindingParams = new BindingParameterCollection();  
    bindingParams.Add(credentials);  
    ```  
  
6.  <span data-ttu-id="bb1dd-145">Créer un écouteur de canal et l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-145">Create a channel listener and open it.</span></span> <span data-ttu-id="bb1dd-146">Vous créez l’écouteur en appelant **BuildChannelListener < IInputChannel\>**  méthode sur le **OracleDBBinding**.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-146">You create the listener by invoking **BuildChannelListener<IInputChannel\>** method on the **OracleDBBinding**.</span></span> <span data-ttu-id="bb1dd-147">Vous pouvez modifier l’espace de noms cible pour l’opération POLLINGSTMT en définissant la propriété PollingId dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-147">You can modify the target namespace for the POLLINGSTMT operation by setting the PollingId property in the connection URI.</span></span> <span data-ttu-id="bb1dd-148">Pour plus d’informations sur l’URI de connexion de l’adaptateur, consultez [créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="bb1dd-148">For more information about the adapter connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
    ```  
    IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
    listener.Open();  
    ```  
  
7.  <span data-ttu-id="bb1dd-149">Obtenir un **IInputChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur et ouvrez-le.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-149">Get an **IInputChannel** channel by invoking the **AcceptChannel** method on the listener and open it.</span></span>  
  
    ```  
    IInputChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  
  
8.  <span data-ttu-id="bb1dd-150">Appeler **réception** sur le canal pour obtenir le prochain message POLLINGSTMT à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-150">Invoke **Receive** on the channel to get the next POLLINGSTMT message from the adapter.</span></span>  
  
    ```  
    Message message = channel.Receive();  
    ```  
  
9. <span data-ttu-id="bb1dd-151">Utiliser le jeu de résultats retourné par l’opération POLLINGSTMT.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-151">Consume the result set returned by the POLLINGSTMT operation.</span></span> <span data-ttu-id="bb1dd-152">Vous pouvez consommer le message en utilisant un **XmlReader** ou **XmlDictionaryWriter**.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-152">You can consume the message using either an **XmlReader** or an **XmlDictionaryWriter**.</span></span>  
  
    ```  
    XmlReader reader = message.GetReaderAtBodyContents();  
    ```  
  
10. <span data-ttu-id="bb1dd-153">Fermer le canal lorsque vous avez terminé le traitement de la demande.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-153">Close the channel when you have completed processing the request.</span></span>  
  
    ```  
    channel.Close()  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="bb1dd-154">Vous devez fermer le canal une fois que vous avez terminé le traitement de l’opération POLLINGSTMT.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-154">You must close the channel after you have finished processing the POLLINGSTMT operation.</span></span> <span data-ttu-id="bb1dd-155">Échec de fermer le canal peut affecter le comportement de votre code.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-155">Failure to close the channel may affect the behavior of your code.</span></span>  
  
11. <span data-ttu-id="bb1dd-156">Fermer l’écouteur lorsque vous avez terminé la réception de messages de données modifiées.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-156">Close the listener when you are finished receiving data-changed messages.</span></span>  
  
    ```  
    listener.Close()  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="bb1dd-157">Fermeture de l’écouteur ne ferme pas les canaux créés à l’aide de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-157">Closing the listener does not close channels created using the listener.</span></span> <span data-ttu-id="bb1dd-158">Vous devez fermer explicitement chaque canal créé à l’aide de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-158">You must explicitly close each channel created using the listener.</span></span>  
  
### <a name="example"></a><span data-ttu-id="bb1dd-159">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb1dd-159">Example</span></span>  
 <span data-ttu-id="bb1dd-160">L’exemple suivant montre comment configurer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour interroger les tables de base de données Oracle et des vues et de recevoir le POLLLINGSTMT opération à l’aide de WCF modèle de canal.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-160">The following example shows how to configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to poll Oracle database tables and views and receive the POLLLINGSTMT operation using the WCF channel model.</span></span> <span data-ttu-id="bb1dd-161">Le jeu de résultats retourné dans l’opération POLLINGSTMT sont écrite dans la console en utilisant un **XmlReader**.</span><span class="sxs-lookup"><span data-stu-id="bb1dd-161">The result set returned in the POLLINGSTMT operation is written to the console by using an **XmlReader**.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF LOB Adapter SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Add this namespace for channel model  
using System.ServiceModel.Channels;  
  
using System.Xml;  
using System.Runtime.Serialization;  
using System.IO;  
  
// Include this namespace for the WCF LOB Adapter SDK and Oracle exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
namespace OraclePollingCM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Uri connectionUri = new Uri("oracleDB://ADAPTER/");  
  
            IChannelListener<IInputChannel> listener = null;  
            IInputChannel channel = null;  
  
            // set timeout to receive POLLINGSTMT message  
            TimeSpan messageTimeout = new TimeSpan(0, 0, 30);  
  
            Console.WriteLine("Sample Started");  
  
            try  
            {  
                // Create a binding: specify the InboundOperationType, PollingInterval (in seconds), the           
                // PollingStatement,and the PostPollStatement.  
                OracleDBBinding binding = new OracleDBBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PollingInterval = 30;  
                binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
                binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
                // Create a binding parameter collection and set the credentials  
                ClientCredentials credentials = new ClientCredentials();  
                credentials.UserName.UserName = "SCOTT";  
                credentials.UserName.Password = "TIGER";  
  
                BindingParameterCollection bindingParams = new BindingParameterCollection();  
                bindingParams.Add(credentials);  
  
                Console.WriteLine("Opening listener");  
                // get a listener  from the binding  
                listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
                listener.Open();  
  
                Console.WriteLine("Opening channel");  
                // get a channel from the listener  
                channel = listener.AcceptChannel();  
                channel.Open();  
  
                Console.WriteLine("Channel opened -- waiting for polled data");  
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
  
                    // Write the TID, ACCOUNT, AMOUNT, and TRANSDATE for each record to the Console  
                    Console.WriteLine("\nPolling data received for request number {0}", i+1);  
                    Console.WriteLine("Tx ID\tACCOUNT\tAMOUNT\tTx DATE");  
  
                    while (reader.Read())  
                    {  
                        if (reader.IsStartElement())  
                        {  
                            switch (reader.Name)  
                            {  
                                case "POLLINGSTMTRECORD":  
                                    Console.Write("\n");  
                                    break;  
  
                                case "TID":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
  
                                case "ACCOUNT":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
                                case "AMOUNT":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
  
                                case "TRANSDATE":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
  
                                default:  
                                    break;  
                            }  
                        }  
                    }  
  
                    // return the cursor  
                    Console.WriteLine();  
  
                    // close the reader  
                    reader.Close();  
  
                    //            To save the polling data to a file you can REPLACE the code above with the following  
                    //  
                    //            XmlDocument doc = new XmlDocument();  
                    //            doc.Load(reader);  
                    //            using (XmlWriter writer = XmlWriter.Create("PollingOutput.xml"))  
                    //            {  
                    //                doc.WriteTo(writer);  
                    //            }  
                    message.Close();  
                }  
  
                Console.WriteLine("\nPolling done -- hit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the Oracle Database");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the Oracle Database");  
                Console.WriteLine(cex.InnerException.Message);  
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
  
## <a name="see-also"></a><span data-ttu-id="bb1dd-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb1dd-162">See Also</span></span>  
 [<span data-ttu-id="bb1dd-163">Développer des applications de base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="bb1dd-163">Develop Oracle Database applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)
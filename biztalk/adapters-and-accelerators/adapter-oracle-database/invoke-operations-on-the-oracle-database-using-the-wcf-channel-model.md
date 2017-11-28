---
title: "Appeler des opérations sur la base de données Oracle à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invoking operations, using the WCF channel model
- WCF channel model, invoking operations
- invoking operations
- operations, invoking
ms.assetid: 6dd95c18-8f78-46d0-8845-b74890614c33
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5af783a5f2315aa39fc3ab49f727583b1bbf7d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-operations-on-the-oracle-database-using-the-wcf-channel-model"></a><span data-ttu-id="df4ee-102">Appeler des opérations sur la base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="df4ee-102">Invoke Operations on the Oracle Database Using the WCF Channel Model</span></span>
<span data-ttu-id="df4ee-103">Vous pouvez appeler des opérations sur le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] en utilisant un **IRequestChannel** ou **IOutputChannel** forme pour envoyer des messages à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="df4ee-103">You can invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by using an **IRequestChannel** or **IOutputChannel** shape to send messages to the adapter.</span></span> <span data-ttu-id="df4ee-104">Le modèle de base consiste à créer une fabrication de canal pour la forme de canal requis à l’aide d’une liaison (**OracleDBBinding**) et un point de terminaison créé à partir d’un URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="df4ee-104">The basic pattern is to create a channel factory for the required channel shape by using a binding (**OracleDBBinding**) and an endpoint created from a connection URI.</span></span> <span data-ttu-id="df4ee-105">Vous créez ensuite un **Message** instance qui représente un message SOAP qui est conforme au schéma de message pour votre opération de cible.</span><span class="sxs-lookup"><span data-stu-id="df4ee-105">You then create a **Message** instance that represents a SOAP message that conforms to the message schema for your target operation.</span></span> <span data-ttu-id="df4ee-106">Vous pouvez alors envoyer ce **Message** à la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à l’aide d’un canal créé à partir de la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="df4ee-106">You can then send this **Message** to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by using a channel created from the channel factory.</span></span> <span data-ttu-id="df4ee-107">Si vous utilisez un **IRequestChannel**, vous recevez une réponse.</span><span class="sxs-lookup"><span data-stu-id="df4ee-107">If you are using an **IRequestChannel**, you receive a response.</span></span> <span data-ttu-id="df4ee-108">S’il existe un problème d’exécution de l’opération sur la base de données Oracle, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] lève une **Microsoft.ServiceModel.Channels.Common.TargetSystemException**.</span><span class="sxs-lookup"><span data-stu-id="df4ee-108">If there is a problem executing the operation on the Oracle database, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] throws a **Microsoft.ServiceModel.Channels.Common.TargetSystemException**.</span></span>  
  
 <span data-ttu-id="df4ee-109">Pour une vue d’ensemble de la manière d’envoyer des opérations à l’aide un **IRequestChannel** dans WCF, consultez « Programmation au niveau du canal de Client » à [http://go.microsoft.com/fwlink/?LinkId=106081](http://go.microsoft.com/fwlink/?LinkId=106081).</span><span class="sxs-lookup"><span data-stu-id="df4ee-109">For an overview of how to send operations using an **IRequestChannel** in WCF, see "Client Channel-Level Programming" at [http://go.microsoft.com/fwlink/?LinkId=106081](http://go.microsoft.com/fwlink/?LinkId=106081).</span></span>  
  
 <span data-ttu-id="df4ee-110">Les sections de cette rubrique fournissent des informations pour vous aider à appeler des opérations sur les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à l’aide du modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="df4ee-110">The sections in this topic provide information to help you invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] using the WCF channel model.</span></span>  
  
## <a name="creating-and-consuming-messages-for-outbound-operations"></a><span data-ttu-id="df4ee-111">Création et utilisation des Messages pour les opérations sortantes</span><span class="sxs-lookup"><span data-stu-id="df4ee-111">Creating and Consuming Messages for Outbound Operations</span></span>  
 <span data-ttu-id="df4ee-112">Pour appeler une opération sur le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], vous envoyez le message de demande pour l’opération de cible à l’aide un **IRequestChannel** ou un **IOutputChannel**.</span><span class="sxs-lookup"><span data-stu-id="df4ee-112">To invoke an operation on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you send the request message for the target operation using either an **IRequestChannel** or an **IOutputChannel**.</span></span> <span data-ttu-id="df4ee-113">Si vous utilisez un **IRequestChannel** l’adaptateur retourne les résultats de l’opération dans le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="df4ee-113">If you use an **IRequestChannel** the adapter returns the results of the operation in the response message.</span></span>  
  
 <span data-ttu-id="df4ee-114">Pour plus d’informations sur la demande et les schémas de message de réponse et les actions de message pour chaque opération, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="df4ee-114">For more detailed information about the request and response message schemas and the message actions for each operation, see [Messages and Message Schemas for BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).</span></span>  
  
 <span data-ttu-id="df4ee-115">Comment créer le message de demande et comment consommer le message de réponse détermine si le nœud de diffusion en continu ou diffusion en continu de valeur de nœud est effectuée par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="df4ee-115">How you create the request message and consume the response message determines whether node streaming or node-value streaming is performed by the adapter.</span></span> <span data-ttu-id="df4ee-116">Ce paramètre détermine ensuite si la diffusion en continu de bout en bout des données LOB est effectuée pour les opérations prises en charge.</span><span class="sxs-lookup"><span data-stu-id="df4ee-116">This in turn determines whether end-to-end streaming of LOB data is performed for supported operations.</span></span>  
  
### <a name="creating-the-request-message"></a><span data-ttu-id="df4ee-117">Création d’un message de demande</span><span class="sxs-lookup"><span data-stu-id="df4ee-117">Creating the request message</span></span>  
 <span data-ttu-id="df4ee-118">Vous pouvez créer le message de demande de deux manières :</span><span class="sxs-lookup"><span data-stu-id="df4ee-118">You can create the request message in one of two ways:</span></span>  
  
-   <span data-ttu-id="df4ee-119">Pour créer un message qui peut être utilisé pour la valeur du nœud de diffusion en continu vous devez passer le corps du message dans une **XmlBodyWriter** qui implémente la diffusion en continu de la valeur du nœud.</span><span class="sxs-lookup"><span data-stu-id="df4ee-119">To create a message that can be used for node-value streaming you must pass the message body in an **XmlBodyWriter** that implements node-value streaming.</span></span>  
  
-   <span data-ttu-id="df4ee-120">Pour créer un message qui peut être utilisé pour le nœud de diffusion en continu vous pouvez passer le corps du message dans une **XmlReader**.</span><span class="sxs-lookup"><span data-stu-id="df4ee-120">To create a message that can be used for node streaming you can pass the message body in an **XmlReader**.</span></span>  
  
 <span data-ttu-id="df4ee-121">Vous utilisez généralement pour prendre en charge la diffusion en continu de bout en bout de Oracle LOB des données dans le message de demande de diffusion en continu de valeur de nœud.</span><span class="sxs-lookup"><span data-stu-id="df4ee-121">You typically use node-value streaming to support end-to-end streaming of Oracle LOB data in the request message.</span></span> <span data-ttu-id="df4ee-122">La seule opération qui prend en charge cette fonctionnalité est UpdateLOB.</span><span class="sxs-lookup"><span data-stu-id="df4ee-122">The only operation that supports this feature is UpdateLOB.</span></span>  
  
### <a name="consuming-the-response-message"></a><span data-ttu-id="df4ee-123">Le message de réponse</span><span class="sxs-lookup"><span data-stu-id="df4ee-123">Consuming the response message</span></span>  
 <span data-ttu-id="df4ee-124">Vous pouvez utiliser le message de réponse de deux manières :</span><span class="sxs-lookup"><span data-stu-id="df4ee-124">You can consume the response message in one of two ways:</span></span>  
  
-   <span data-ttu-id="df4ee-125">Pour consommer le message à l’aide de la valeur du nœud de diffusion en continu vous devez appeler la **WriteBodyContents** méthode sur la réponse de message et lui passer une **XmlDictionaryWriter** qui implémente la diffusion en continu de la valeur du nœud.</span><span class="sxs-lookup"><span data-stu-id="df4ee-125">To consume the message using node-value streaming you must call the **WriteBodyContents** method on the response message and pass it an **XmlDictionaryWriter** that implements node-value streaming.</span></span>  
  
-   <span data-ttu-id="df4ee-126">Pour consommer le message à l’aide du nœud de diffusion en continu, vous pouvez appeler **GetReaderAtBodyContents** sur le message de réponse pour obtenir un **XmlReader**.</span><span class="sxs-lookup"><span data-stu-id="df4ee-126">To consume the message using node streaming you can call **GetReaderAtBodyContents** on the response message to get an **XmlReader**.</span></span>  
  
 <span data-ttu-id="df4ee-127">Vous utilisez généralement la valeur du nœud de diffusion en continu pour prendre en charge la diffusion en continu de bout en bout de Oracle LOB des données dans le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="df4ee-127">You typically use node-value streaming to support end-to-end streaming of Oracle LOB data in the response message.</span></span> <span data-ttu-id="df4ee-128">Il existe de nombreuses opérations qui prennent en charge cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="df4ee-128">There are many operations that support this feature.</span></span>  
  
### <a name="lob-data-and-message-streaming-support"></a><span data-ttu-id="df4ee-129">Données LOB et prise en charge de la diffusion en continu de Message</span><span class="sxs-lookup"><span data-stu-id="df4ee-129">LOB Data and Message Streaming Support</span></span>  
 <span data-ttu-id="df4ee-130">Pour plus d’informations sur la façon dont [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge la diffusion en continu des données LOB, consultez [diffusion en continu des types de données dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="df4ee-130">For more information about how the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports streaming on LOB data, see [Streaming large object data types in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).</span></span>  
  
 <span data-ttu-id="df4ee-131">Pour plus d’informations sur l’implémentation de diffusion en continu dans votre code pour prendre en charge la diffusion en continu de bout en bout des données LOB de valeur de nœud, consultez [de diffusion en continu Oracle de base de données LOB données Types à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).</span><span class="sxs-lookup"><span data-stu-id="df4ee-131">For more information about implementing node-value streaming in your code to support end-to-end streaming of LOB data, see [Streaming Oracle Database LOB Data Types Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="transaction-support-on-outbound-operations-in-the-wcf-channel-model"></a><span data-ttu-id="df4ee-132">Prise en charge de la transaction sur les opérations de sortie dans le modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="df4ee-132">Transaction Support on Outbound Operations in the WCF Channel Model.</span></span>  
 <span data-ttu-id="df4ee-133">L’adaptateur s’exécute chaque opération que vous appelez à l’intérieur d’une transaction dédiée sur la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="df4ee-133">The adapter executes each operation you invoke inside a dedicated transaction on the Oracle database.</span></span> <span data-ttu-id="df4ee-134">Vous pouvez contrôler le niveau d’isolation de ces transactions en définissant le **TransactionIsolationLevel** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="df4ee-134">You can control the isolation level of these transactions by setting the **TransactionIsolationLevel** binding property.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="df4ee-135">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="df4ee-135">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="df4ee-136">L’exemple dans cette rubrique utilise le SCOTT. Table ACCOUNTACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="df4ee-136">The example in this topic uses the SCOTT.ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="df4ee-137">Un script pour générer ces artefacts est fourni avec les exemples du Kit de développement logiciel.</span><span class="sxs-lookup"><span data-stu-id="df4ee-137">A script to generate these artifacts is supplied with the SDK samples.</span></span> <span data-ttu-id="df4ee-138">Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).</span><span class="sxs-lookup"><span data-stu-id="df4ee-138">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="how-do-i-invoke-an-operation-by-using-a-channel"></a><span data-ttu-id="df4ee-139">Comment pour appeler une opération à l’aide d’un canal ?</span><span class="sxs-lookup"><span data-stu-id="df4ee-139">How Do I Invoke an Operation by Using a Channel?</span></span>  
 <span data-ttu-id="df4ee-140">Pour appeler une opération en utilisant un **IRequestChannel**, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="df4ee-140">To invoke an operation by using an **IRequestChannel**, perform the following steps.</span></span>  
  
#### <a name="how-to-invoke-an-operation-by-using-an-instance-of-irequestchannel"></a><span data-ttu-id="df4ee-141">L’appel d’une opération à l’aide d’une instance de IRequestChannel</span><span class="sxs-lookup"><span data-stu-id="df4ee-141">How to invoke an operation by using an instance of IRequestChannel</span></span>  
  
1.  <span data-ttu-id="df4ee-142">Générer une fabrique de canal (**ChannelFactory\<IRequestChannel >**).</span><span class="sxs-lookup"><span data-stu-id="df4ee-142">Build a channel factory (**ChannelFactory\<IRequestChannel>**).</span></span> <span data-ttu-id="df4ee-143">Pour ce faire, vous devez spécifier une liaison (**OracleDBBinding**) et une adresse de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="df4ee-143">To do this, you must specify a binding (**OracleDBBinding**) and an endpoint address.</span></span> <span data-ttu-id="df4ee-144">Vous pouvez spécifier l’adresse de liaison et le point de terminaison soit impérativement dans votre code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="df4ee-144">You can specify the binding and endpoint address either imperatively in your code or declaratively in configuration.</span></span> <span data-ttu-id="df4ee-145">Pour plus d’informations sur la façon de spécifier la liaison et l’adresse de point de terminaison dans la configuration, consultez [créer un canal à l’aide de la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="df4ee-145">For more information about how to specify the binding and endpoint address in configuration, see [Create a channel using Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md).</span></span>  
  
    ```  
    // Create a binding  
    OracleDBBinding binding = new OracleDBBinding();  
    // Create an endpoint address by using the connection URI  
    EndpointAddress address = new EndpointAddress("oracledb://ADAPTER");  
    // Create the channel factory  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    ```  
  
2.  <span data-ttu-id="df4ee-146">Définir des informations d’identification de mot de passe pour la fabrication de canal de l’utilisateur à l’aide de la **ClientCredentials** propriété.</span><span class="sxs-lookup"><span data-stu-id="df4ee-146">Set the user name password credentials for the channel factory by using the **ClientCredentials** property.</span></span>  
  
    ```  
    factory.Credentials.UserName.UserName = "SCOTT";  
    factory.Credentials.UserName.Password = "TIGER";  
    ```  
  
3.  <span data-ttu-id="df4ee-147">Ouvrez la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="df4ee-147">Open the channel factory.</span></span>  
  
    ```  
    factory.Open();  
    ```  
  
4.  <span data-ttu-id="df4ee-148">Obtenir un canal à partir de la fabrique et l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="df4ee-148">Get a channel from the factory and open it.</span></span>  
  
    ```  
    IRequestChannel channel = factory.CreateChannel();  
    channel.Open();  
    ```  
  
5.  <span data-ttu-id="df4ee-149">Créer un **Message** instance pour l’opération de la cible.</span><span class="sxs-lookup"><span data-stu-id="df4ee-149">Create a **Message** instance for the target operation.</span></span> <span data-ttu-id="df4ee-150">Assurez-vous que l’action du message pour l’opération de la cible est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="df4ee-150">Be sure that the message action for the target operation is specified.</span></span> <span data-ttu-id="df4ee-151">Dans cet exemple, le corps du message est passé en créant un **XmlReader** sur un fichier.</span><span class="sxs-lookup"><span data-stu-id="df4ee-151">In this example, the message body is passed by creating an **XmlReader** over a file.</span></span> <span data-ttu-id="df4ee-152">L’opération de la cible est une opération Select sur la table SCOTT/EMP.</span><span class="sxs-lookup"><span data-stu-id="df4ee-152">The target operation is a Select operation on the SCOTT/EMP table.</span></span>  
  
    ```  
    XmlReader readerIn = XmlReader.Create("SelectAllActivity.xml");  
    Message messageIn = Message.CreateMessage(MessageVersion.Default,  
        "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select",  
        readerIn);  
    ```  
  
6.  <span data-ttu-id="df4ee-153">Appeler le **demande** méthode sur le canal pour envoyer le message à la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] et recevoir la réponse.</span><span class="sxs-lookup"><span data-stu-id="df4ee-153">Invoke the **Request** method on the channel to send the message to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] and receive the reply.</span></span> <span data-ttu-id="df4ee-154">Si la base de données Oracle rencontre une exception, l’adaptateur génère un **TargetSystemException**.</span><span class="sxs-lookup"><span data-stu-id="df4ee-154">If the Oracle database encounters an exception, the adapter throws a **TargetSystemException**.</span></span> <span data-ttu-id="df4ee-155">(Les autres exceptions sont possibles pour les exceptions non Oracle). Vous pouvez obtenir une description de l’erreur Oracle à partir de la **InnerException.Message** propriété de la **TargetSystemException**.</span><span class="sxs-lookup"><span data-stu-id="df4ee-155">(Other exceptions are possible for non Oracle exceptions.) You can get a description of the Oracle error from the **InnerException.Message** property of the **TargetSystemException**.</span></span>  
  
    ```  
    try  
    {  
        Message messageOut = channel.Request(messageIn);  
    }  
    catch (Exception ex)  
    {  
        // handle exception  
    }  
    ```  
  
7.  <span data-ttu-id="df4ee-156">Traiter la réponse.</span><span class="sxs-lookup"><span data-stu-id="df4ee-156">Process the response.</span></span> <span data-ttu-id="df4ee-157">Dans cet exemple, **GetReaderAtBodyContents** est appelée sur le message de réponse pour obtenir le corps du message.</span><span class="sxs-lookup"><span data-stu-id="df4ee-157">In this example, **GetReaderAtBodyContents** is called on the response message to get the message body.</span></span>  
  
    ```  
    XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
    ```  
  
8.  <span data-ttu-id="df4ee-158">Lorsque vous avez terminé le traitement du message de réponse, fermez le lecteur et le message.</span><span class="sxs-lookup"><span data-stu-id="df4ee-158">When you are done processing the response message, close the reader and the message.</span></span>  
  
    ```  
    readerOut.Close();  
    messageOut.Close();  
    ```  
  
9. <span data-ttu-id="df4ee-159">Lorsque vous avez terminé à l’aide du canal et la fabrication de canal, de les fermer.</span><span class="sxs-lookup"><span data-stu-id="df4ee-159">When you are done using the channel and the channel factory, close them.</span></span> <span data-ttu-id="df4ee-160">Fermeture de la fabrique se fermera tous les canaux qui ont été créés avec lui.</span><span class="sxs-lookup"><span data-stu-id="df4ee-160">Closing the factory will close all channels that were created with it.</span></span>  
  
    ```  
    channel.Close()  
    factory.Close();  
  
    ```  
  
 <span data-ttu-id="df4ee-161">Vous suivez les mêmes étapes pour envoyer un message à l’aide de la **IOutputChannel** mettre en forme, à l’exception :</span><span class="sxs-lookup"><span data-stu-id="df4ee-161">You follow the same steps to send a message using the **IOutputChannel** shape except:</span></span>  
  
-   <span data-ttu-id="df4ee-162">Vous créez un **ChannelFactory\<IOutputChannel >** dans l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="df4ee-162">You create a **ChannelFactory\<IOutputChannel>** in step 1.</span></span>  
  
-   <span data-ttu-id="df4ee-163">Vous appelez le **envoyer** méthode sur le canal à l’étape 6.</span><span class="sxs-lookup"><span data-stu-id="df4ee-163">You call the **Send** method on the channel in step 6.</span></span> <span data-ttu-id="df4ee-164">`channel.Send(messageIn);`.</span><span class="sxs-lookup"><span data-stu-id="df4ee-164">`channel.Send(messageIn);`.</span></span>  
  
-   <span data-ttu-id="df4ee-165">Aucun message de réponse retourné pour une **IOutputChannel**.</span><span class="sxs-lookup"><span data-stu-id="df4ee-165">There is no response message returned for an **IOutputChannel**.</span></span>  
  
### <a name="example"></a><span data-ttu-id="df4ee-166">Exemple</span><span class="sxs-lookup"><span data-stu-id="df4ee-166">Example</span></span>  
 <span data-ttu-id="df4ee-167">L’exemple suivant montre comment appeler une opération de sélection en utilisant un **IRequestChannel** canal.</span><span class="sxs-lookup"><span data-stu-id="df4ee-167">The following example shows how to invoke a Select operation by using an **IRequestChannel** channel.</span></span> <span data-ttu-id="df4ee-168">Le message de réponse Select est consommé en utilisant un **XmlReader** et le nombre d’enregistrements renvoyés est écrite dans la console.</span><span class="sxs-lookup"><span data-stu-id="df4ee-168">The Select response message is consumed by using an **XmlReader** and the number of records returned is written to the console.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
using System.Xml;  
using System.IO;  
using System.Runtime.Serialization;  
  
namespace RequestChanneSample  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The Select operation request message  
            const string selectRequestString =  
                "\<Select xmlns=\"http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY\">" +  
                    "<COLUMN_NAMES>*</COLUMN_NAMES>" +  
                    "<FILTER>ACCOUNT = 100002</FILTER>" +  
                "</Select>";  
            try  
            {  
                // Create binding -- specify binding properties before you open the factory.  
                OracleDBBinding odbBinding = new OracleDBBinding();  
  
                // Create address.  
                EndpointAddress odbAddress = new EndpointAddress("oracledb://ADAPTER/");  
  
                // Create channel factory from binding and address.  
                ChannelFactory<IRequestChannel> factory =   
                    new ChannelFactory<IRequestChannel>(odbBinding, odbAddress);  
  
                // Specify credentials   
                factory.Credentials.UserName.UserName = "SCOTT";  
                factory.Credentials.UserName.Password = "TIGER";  
  
                // Open the factory.  
                factory.Open();  
  
                // Get a channel.  
                IRequestChannel channel = factory.CreateChannel();  
  
                // Open the channel.  
                channel.Open();  
  
                // Create the request message from the string  
                StringReader strReader = new StringReader(selectRequestString);  
                XmlReader readerIn = XmlReader.Create(strReader);  
  
                Message requestMessage = Message.CreateMessage(MessageVersion.Default,  
                    "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select",  
                    readerIn);  
  
                Send the message and get a respone  
                Message responseMessage = channel.Request(requestMessage);  
  
                // Get an XmlReader from the message  
                XmlReader readerOut = (XmlReader) responseMessage.GetReaderAtBodyContents();  
  
                // Count the number of records returned and write to the console.  
                readerOut.MoveToContent();  
                int numberOfRecordsReturned = 0;  
                while (readerOut.Read())  
                {  
                    if (readerOut.NodeType == XmlNodeType.Element && readerOut.Name == "ACCOUNTACTIVITYRECORDSELECT")  
                        numberOfRecordsReturned++;  
                }  
  
                Console.WriteLine("{0} records returned.", numberOfRecordsReturned);  
  
                // Close the output reader and message  
                readerOut.Close();  
                responseMessage.Close();  
  
                //Close channel  
                channel.Close();  
  
                //Close the factory  
                factory.Close();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex.Message);  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="df4ee-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df4ee-169">See Also</span></span>  
 [<span data-ttu-id="df4ee-170">Développer des applications de base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="df4ee-170">Develop Oracle Database applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)
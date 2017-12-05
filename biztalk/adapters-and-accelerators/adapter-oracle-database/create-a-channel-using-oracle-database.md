---
title: "Créer un canal à l’aide de la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating a channel
- WCF channel model, creating a channel
- how to, create a channel
- channel programming, creating a channel
ms.assetid: a30156a0-5a5a-4418-be17-2e23c3716fc1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 413f62a679c0510be34289900b92188554e622c8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="create-a-channel-using-oracle-database"></a><span data-ttu-id="047ea-102">Créer un canal à l’aide de la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="047ea-102">Create a channel using Oracle Database</span></span>
<span data-ttu-id="047ea-103">Dans le modèle de canal WCF, vous appeler des opérations sur la base de données Oracle et recevoir les résultats d’une requête d’interrogation en échangeant des messages SOAP avec le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] sur un canal WCF.</span><span class="sxs-lookup"><span data-stu-id="047ea-103">In the WCF channel model, you invoke operations on the Oracle database and receive the results of a polling query by exchanging SOAP messages with the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] over a WCF channel.</span></span>  
  
-   <span data-ttu-id="047ea-104">Vous appelez operations (opérations sortantes) en utilisant un **IRequestChannel** ou un **IOutputChannel** pour envoyer des messages à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="047ea-104">You invoke operations (outbound operations) by using either an **IRequestChannel** or an **IOutputChannel** to send messages to the adapter.</span></span>  
  
-   <span data-ttu-id="047ea-105">Vous recevez des messages d’interrogation de données modifiées en recevant des messages POLLINGSTMT sur une **IInputChannel**.</span><span class="sxs-lookup"><span data-stu-id="047ea-105">You receive polling-based data-changed messages by receiving POLLINGSTMT messages over an **IInputChannel**.</span></span>  
  
 <span data-ttu-id="047ea-106">Les rubriques de cette section fournissent des informations sur la façon de créer et configurer les formes de canal qui sont utilisés pour les opérations entrantes et sortantes.</span><span class="sxs-lookup"><span data-stu-id="047ea-106">The topics in this section provide information about how to create and configure channel shapes that are used for inbound and outbound operations.</span></span>  
  
## <a name="creating-outbound-client-channels"></a><span data-ttu-id="047ea-107">Créer des canaux sortants (Client)</span><span class="sxs-lookup"><span data-stu-id="047ea-107">Creating Outbound (Client) Channels</span></span>  
 <span data-ttu-id="047ea-108">Vous pouvez utiliser un **IRequestChannel** ou **IOutputChannel** pour appeler des opérations sur la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="047ea-108">You can use either an **IRequestChannel** or an **IOutputChannel** to invoke operations on the Oracle database.</span></span> <span data-ttu-id="047ea-109">Dans les deux cas, vous créez tout d’abord un **System.ServiceModel.ChannelFactory** à l’aide de l’interface appropriée.</span><span class="sxs-lookup"><span data-stu-id="047ea-109">In either case, you first create a **System.ServiceModel.ChannelFactory** using the appropriate interface.</span></span> <span data-ttu-id="047ea-110">Vous utilisez ensuite la fabrique pour créer le canal.</span><span class="sxs-lookup"><span data-stu-id="047ea-110">You then use the factory to create the channel.</span></span> <span data-ttu-id="047ea-111">Après avoir créé le canal, vous pouvez l’utiliser pour appeler des opérations sur la carte.</span><span class="sxs-lookup"><span data-stu-id="047ea-111">After you have created the channel you can use it to invoke operations on the adapter.</span></span>  
  
#### <a name="to-create-and-open-an-outbound-channel"></a><span data-ttu-id="047ea-112">Pour créer et ouvrir un canal sortant</span><span class="sxs-lookup"><span data-stu-id="047ea-112">To create and open an outbound channel</span></span>  
  
1.  <span data-ttu-id="047ea-113">Créer et initialiser une instance de **ChannelFactory** pour la forme du canal souhaitées à l’aide d’un point de terminaison et une liaison.</span><span class="sxs-lookup"><span data-stu-id="047ea-113">Create and initialize an instance of **ChannelFactory** for the desired channel shape by using an endpoint and a binding.</span></span> <span data-ttu-id="047ea-114">Le point de terminaison spécifie un URI de connexion Oracle et de la liaison est une instance de **OracleDBBinding**.</span><span class="sxs-lookup"><span data-stu-id="047ea-114">The endpoint specifies an Oracle connection URI and the binding is an instance of **OracleDBBinding**.</span></span>  
  
2.  <span data-ttu-id="047ea-115">Fournir des informations d’identification Oracle pour la fabrication de canal à l’aide de la **informations d’identification** propriété.</span><span class="sxs-lookup"><span data-stu-id="047ea-115">Provide Oracle credentials for the channel factory by using the **Credentials** property.</span></span>  
  
3.  <span data-ttu-id="047ea-116">Ouvrez la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="047ea-116">Open the channel factory.</span></span>  
  
4.  <span data-ttu-id="047ea-117">Obtention d’une instance du canal en appelant le **CreateChannel** méthode sur la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="047ea-117">Get an instance of the channel by invoking the **CreateChannel** method on the channel factory.</span></span>  
  
5.  <span data-ttu-id="047ea-118">Ouvrir le canal.</span><span class="sxs-lookup"><span data-stu-id="047ea-118">Open the channel.</span></span>  
  
 <span data-ttu-id="047ea-119">Vous pouvez spécifier l’adresse de liaison et le point de terminaison dans votre code ou de configuration.</span><span class="sxs-lookup"><span data-stu-id="047ea-119">You can specify the binding and endpoint address in your code or from configuration.</span></span>  
  
### <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="047ea-120">Spécification de la liaison et l’adresse de point de terminaison dans le Code</span><span class="sxs-lookup"><span data-stu-id="047ea-120">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="047ea-121">L’exemple de code suivant montre comment créer un **IRequestChannel** en spécifiant l’adresse de liaison et le point de terminaison dans le code.</span><span class="sxs-lookup"><span data-stu-id="047ea-121">The following code example shows how to create an **IRequestChannel** by specifying the binding and endpoint address in code.</span></span> <span data-ttu-id="047ea-122">Le code pour créer un **IOutputChannel** est identique, sauf que vous devez spécifier un **IOutputChannel** de l’interface pour le **ChannelFactory** et type de canal.</span><span class="sxs-lookup"><span data-stu-id="047ea-122">The code to create an **IOutputChannel** is the same except that you must specify an **IOutputChannel** interface for the **ChannelFactory** and channel type.</span></span>  
  
```  
// Create binding -- set binding properties before you open the factory.  
OracleDBBinding odbBinding = new OracleDBBinding();  
  
// Create address.  
EndpointAddress odbAddress = new EndpointAddress("oracledb://ADAPTER/");  
  
// Create channel factory from binding and address.  
ChannelFactory<IRequestChannel> factory =   
    new ChannelFactory<IRequestChannel>(odbBinding, odbAddress);  
  
// Specify credentials.   
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
  
// Open factory  
factory.Open();  
  
// Get channel and open it  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
### <a name="specifying-the-binding-and-endpoint-address-in-configuration"></a><span data-ttu-id="047ea-123">Spécification de la liaison et l’adresse de point de terminaison dans la Configuration</span><span class="sxs-lookup"><span data-stu-id="047ea-123">Specifying the Binding and Endpoint Address in Configuration</span></span>  
 <span data-ttu-id="047ea-124">L’exemple de code suivant montre comment créer une fabrique de canaux à partir d’un point de terminaison de client spécifié dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="047ea-124">The following code example shows how to create a channel factory from a client endpoint specified in configuration.</span></span>  
  
```  
// Create channel factory from configuration.  
ChannelFactory<IRequestChannel> factory =  
new ChannelFactory<IRequestChannel>("MyRequestChannel");  
  
// Specify credentials.  
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
  
// Open the factory.  
factory.Open();  
  
// Get a channel and open it.  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
#### <a name="the-configuration-settings"></a><span data-ttu-id="047ea-125">Les paramètres de Configuration</span><span class="sxs-lookup"><span data-stu-id="047ea-125">The Configuration Settings</span></span>  
 <span data-ttu-id="047ea-126">Le code suivant illustre les paramètres de configuration utilisés pour l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="047ea-126">The following code shows the configuration settings used for the preceding example.</span></span> <span data-ttu-id="047ea-127">Le contrat pour le point de terminaison client doit être « System.ServiceModel.Channels.IRequestChannel » ou « System.ServiceModel.Channels.IRequestChannel » en fonction du type de la forme de canal que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="047ea-127">The contract for the client endpoint must be "System.ServiceModel.Channels.IRequestChannel" or "System.ServiceModel.Channels.IRequestChannel" depending on the kind of channel shape that you want to create.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    <system.serviceModel>  
        <bindings>  
            <oracleDBBinding>  
                <binding name="OracleDBBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" metadataPooling="true"  
                    statementCachePurge="false" statementCacheSize="10" pollingInterval="500"  
                    useOracleConnectionPool="true" minPoolSize="1" maxPoolSize="100"  
                    incrPoolSize="5" decrPoolSize="1" connectionLifetime="0" acceptCredentialsInUri="false"  
                    useAmbientTransaction="true" polledDataAvailableStatement="SELECT 1 FROM DUAL"  
                    pollWhileDataFound="false" notifyOnListenerStart="true" notificationPort="-1"  
                    inboundOperationType="Polling" dataFetchSize="65536" longDatatypeColumnSize="0"  
                    skipNilNodes="true" maxOutputAssociativeArrayElements="32"  
                    enableSafeTyping="false" insertBatchSize="1" useSchemaInNameSpace="true"  
                    enableBizTalkCompatibilityMode="false" enablePerformanceCounters="false" />  
            </oracleDBBinding>  
        </bindings>  
        <client>  
            <endpoint address="oracledb://adapter/" binding="oracleDBBinding"  
                bindingConfiguration="OracleDBBinding" contract="System.ServiceModel.Channels.IRequestChannel"  
                name="MyRequestChannel" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="creating-inbound-service-channels"></a><span data-ttu-id="047ea-128">Créer des canaux entrants (Service)</span><span class="sxs-lookup"><span data-stu-id="047ea-128">Creating Inbound (Service) Channels</span></span>  
 <span data-ttu-id="047ea-129">Vous configurez le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour interroger les tables de base de données Oracle et les vues en définissant les propriétés de liaison sur une instance de **OracleDBBinding**.</span><span class="sxs-lookup"><span data-stu-id="047ea-129">You configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to poll the Oracle database tables and views by setting binding properties on an instance of **OracleDBBinding**.</span></span> <span data-ttu-id="047ea-130">Vous utilisez ensuite cette liaison pour générer un écouteur de canal à partir de laquelle vous pouvez obtenir un **IInputChannel** canal pour recevoir des messages pour les opérations entrantes à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="047ea-130">You then use this binding to build a channel listener from which you can get an **IInputChannel** channel to receive message for inbound operations from the adapter.</span></span>  
  
##### <a name="to-create-and-open-an-iinputchannel-to-receive-messages-for-inbound-operations"></a><span data-ttu-id="047ea-131">Pour créer et ouvrir un IInputChannel pour recevoir des messages pour les opérations entrantes</span><span class="sxs-lookup"><span data-stu-id="047ea-131">To create and open an IInputChannel to receive messages for inbound operations</span></span>  
  
1.  <span data-ttu-id="047ea-132">Créez une instance de **OracleDBBinding**.</span><span class="sxs-lookup"><span data-stu-id="047ea-132">Create an instance of **OracleDBBinding**.</span></span>  
  
2.  <span data-ttu-id="047ea-133">Définissez les propriétés de liaison requises pour l’opération entrante.</span><span class="sxs-lookup"><span data-stu-id="047ea-133">Set the binding properties required for the inbound operation.</span></span> <span data-ttu-id="047ea-134">Par exemple, pour l’opération POLLINGSTMT, au minimum vous devez définir le **InboundOperationType**, **PollingStatement**, et **PollingInterval** propriétés de liaison configurer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour interroger la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="047ea-134">For example, for the POLLINGSTMT operation, at a minimum you must set the **InboundOperationType**, **PollingStatement**, and **PollingInterval** binding properties to configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to poll the Oracle database.</span></span>  
  
3.  <span data-ttu-id="047ea-135">Créer une collection de paramètres de liaison à l’aide du **BindingParameterCollection** puis définissez les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="047ea-135">Create a binding parameter collection using the **BindingParameterCollection** class and set the credentials.</span></span>  
  
4.  <span data-ttu-id="047ea-136">Créer un écouteur de canal en appelant **BuildChannelListener\<IInputChannel\>**  méthode sur le **OracleDBBinding**.</span><span class="sxs-lookup"><span data-stu-id="047ea-136">Create a channel listener by invoking **BuildChannelListener\<IInputChannel\>** method on the **OracleDBBinding**.</span></span> <span data-ttu-id="047ea-137">Vous spécifiez l’URI de connexion Oracle en tant qu’un des paramètres à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="047ea-137">You specify the Oracle connection URI as one of the parameters to this method.</span></span> <span data-ttu-id="047ea-138">Pour plus d’informations sur l’URI de connexion Oracle, consultez [créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="047ea-138">For more information about the Oracle connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
5.  <span data-ttu-id="047ea-139">Ouvrez le port d’écoute.</span><span class="sxs-lookup"><span data-stu-id="047ea-139">Open the listener.</span></span>  
  
6.  <span data-ttu-id="047ea-140">Obtenir un **IInputChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="047ea-140">Get an **IInputChannel** channel by invoking the **AcceptChannel** method on listener.</span></span>  
  
7.  <span data-ttu-id="047ea-141">Ouvrir le canal.</span><span class="sxs-lookup"><span data-stu-id="047ea-141">Open the channel.</span></span>  
  
 <span data-ttu-id="047ea-142">Le code suivant montre comment créer un écouteur de canal et obtenir un **IInputChannel** pour les messages sortants depuis l’adaptateur à l’aide de l’opération POLLINGSTMT.</span><span class="sxs-lookup"><span data-stu-id="047ea-142">The following code shows how to create a channel listener and get an **IInputChannel** to inbound messages from the adapter using the POLLINGSTMT operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="047ea-143">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend uniquement en charge unidirectionnel de réception.</span><span class="sxs-lookup"><span data-stu-id="047ea-143">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] only supports one-way receive.</span></span> <span data-ttu-id="047ea-144">Par conséquent, vous devez utiliser IInputChannel pour recevoir des messages pour les opérations entrantes à partir de la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="047ea-144">So, you must use IInputChannel to receive messages for inbound operations from Oracle database.</span></span>  
  
```  
// Create a binding: specify the InboundOperationType, PollingInterval (in seconds), the PollingStatement, and  
// the PostPollStatement.  
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
  
// Get a listener from the binding and open it.  
Uri connectionUri = new Uri("oracleDB://ADAPTER");  
IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
listener.Open();  
  
// Get a channel from the listener and open it.  
channel = listener.AcceptChannel();  
channel.Open();  
```  
  
## <a name="see-also"></a><span data-ttu-id="047ea-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="047ea-145">See Also</span></span>  
 [<span data-ttu-id="047ea-146">Développer des applications de base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="047ea-146">Develop Oracle Database applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)
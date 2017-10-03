---
title: "Créer un canal à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e86398f6-c835-46f8-814f-31e43b18970e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f79fa2e40bd80bb3a4fd8b976aa31a34e4d3c0bb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-channel-using-the-sql-adapter"></a><span data-ttu-id="d0ce8-102">Créer un canal à l’aide de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="d0ce8-102">Create a channel using the SQL adapter</span></span>
<span data-ttu-id="d0ce8-103">Dans le modèle de canal WCF, vous appeler des opérations sur la base de données SQL Server et recevoir les résultats en échangeant des messages SOAP avec le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] sur un canal WCF.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-103">In the WCF channel model, you invoke operations on the SQL Server database and receive the results by exchanging SOAP messages with the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] over a WCF channel.</span></span>  
  
-   <span data-ttu-id="d0ce8-104">Vous appelez des opérations sortantes en utilisant un **IRequestChannel** ou un **IOutputChannel** pour envoyer des messages à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-104">You invoke outbound operations by using either an **IRequestChannel** or an **IOutputChannel** to send messages to the adapter.</span></span>  
  
-   <span data-ttu-id="d0ce8-105">Vous recevez des messages pour les opérations entrantes en recevant des messages via un **IInputChannel** pour **d’interrogation**, **TypedPolling**, ou **deNotification** operations.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-105">You receive messages for inbound operations by receiving messages over an **IInputChannel** for **Polling**, **TypedPolling**, or **Notification** operations.</span></span>  
  
 <span data-ttu-id="d0ce8-106">Les procédures décrites dans cette rubrique fournissent des informations sur la façon de créer et configurer les formes de canal qui sont utilisés pour les opérations entrantes et sortantes.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-106">The procedures in this topic provide information about how to create and configure channel shapes that are used for inbound and outbound operations.</span></span>  
  
## <a name="creating-outbound-client-channels"></a><span data-ttu-id="d0ce8-107">Créer des canaux sortants (Client)</span><span class="sxs-lookup"><span data-stu-id="d0ce8-107">Creating Outbound (Client) Channels</span></span>  
 <span data-ttu-id="d0ce8-108">Vous pouvez utiliser un **IRequestChannel** ou **IOutputChannel** pour appeler des opérations sur la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-108">You can use either an **IRequestChannel** or an **IOutputChannel** to invoke operations on the SQL Server database.</span></span> <span data-ttu-id="d0ce8-109">Dans les deux cas, vous créez tout d’abord un **System.ServiceModel.ChannelFactory** à l’aide de l’interface appropriée.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-109">In either case, you first create a **System.ServiceModel.ChannelFactory** using the appropriate interface.</span></span> <span data-ttu-id="d0ce8-110">Vous utilisez ensuite la fabrique pour créer le canal.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-110">You then use the factory to create the channel.</span></span> <span data-ttu-id="d0ce8-111">Après avoir créé le canal, vous pouvez l’utiliser pour appeler des opérations sur la carte.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-111">After you have created the channel you can use it to invoke operations on the adapter.</span></span>  
  
#### <a name="to-create-and-open-an-outbound-channel"></a><span data-ttu-id="d0ce8-112">Pour créer et ouvrir un canal sortant</span><span class="sxs-lookup"><span data-stu-id="d0ce8-112">To create and open an outbound channel</span></span>  
  
1.  <span data-ttu-id="d0ce8-113">Créer et initialiser une instance de **ChannelFactory** pour la forme du canal souhaitées à l’aide d’un point de terminaison et une liaison.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-113">Create and initialize an instance of **ChannelFactory** for the desired channel shape by using an endpoint and a binding.</span></span> <span data-ttu-id="d0ce8-114">Le point de terminaison spécifie un URI de connexion SQL Server et de la liaison est une instance de **sqlBinding**.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-114">The endpoint specifies a SQL Server connection URI and the binding is an instance of **sqlBinding**.</span></span>  
  
2.  <span data-ttu-id="d0ce8-115">Fournir des informations d’identification de SQL Server pour la fabrication de canal à l’aide de la **informations d’identification** propriété.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-115">Provide SQL Server credentials for the channel factory by using the **Credentials** property.</span></span>  
  
3.  <span data-ttu-id="d0ce8-116">Ouvrez la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-116">Open the channel factory.</span></span>  
  
4.  <span data-ttu-id="d0ce8-117">Obtention d’une instance du canal en appelant le **CreateChannel** méthode sur la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-117">Get an instance of the channel by invoking the **CreateChannel** method on the channel factory.</span></span>  
  
5.  <span data-ttu-id="d0ce8-118">Ouvrir le canal.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-118">Open the channel.</span></span>  
  
 <span data-ttu-id="d0ce8-119">Vous pouvez spécifier l’adresse de liaison et le point de terminaison dans votre code ou de configuration.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-119">You can specify the binding and endpoint address in your code or from configuration.</span></span>  
  
### <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="d0ce8-120">Spécification de la liaison et l’adresse de point de terminaison dans le Code</span><span class="sxs-lookup"><span data-stu-id="d0ce8-120">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="d0ce8-121">L’exemple de code suivant montre comment créer un **IRequestChannel** en spécifiant l’adresse de liaison et le point de terminaison dans le code.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-121">The following code example shows how to create an **IRequestChannel** by specifying the binding and endpoint address in code.</span></span> <span data-ttu-id="d0ce8-122">Le code pour créer un **IOutputChannel** est identique, sauf que vous devez spécifier un **IOutputChannel** de l’interface pour le **ChannelFactory** et type de canal.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-122">The code to create an **IOutputChannel** is the same except that you must specify an **IOutputChannel** interface for the **ChannelFactory** and channel type.</span></span>  
  
```  
// Create binding -- set binding properties before you open the factory.  
SqlAdapterBinding sdbBinding = new SqlAdapterBinding();  
  
// Create address.  
EndpointAddress sdbAddress = new EndpointAddress("mssql://<sql_server_name>//<database_name>?");  
  
// Create channel factory from binding and address.  
ChannelFactory<IRequestChannel> factory =   
    new ChannelFactory<IRequestChannel>(sdbBinding, sdbAddress);  
  
// Specify credentials.   
factory.Credentials.UserName.UserName = "myuser";  
factory.Credentials.UserName.Password = "mypassword";  
  
// Open factory  
factory.Open();  
  
// Get channel and open it.  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
### <a name="specifying-the-binding-and-endpoint-address-in-configuration"></a><span data-ttu-id="d0ce8-123">Spécification de la liaison et l’adresse de point de terminaison dans la Configuration</span><span class="sxs-lookup"><span data-stu-id="d0ce8-123">Specifying the Binding and Endpoint Address in Configuration</span></span>  
 <span data-ttu-id="d0ce8-124">L’exemple de code suivant montre comment créer une fabrique de canaux à partir d’un point de terminaison de client spécifié dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-124">The following code example shows how to create a channel factory from a client endpoint specified in configuration.</span></span>  
  
```  
// Create channel factory from configuration.  
ChannelFactory<IRequestChannel> factory =  
new ChannelFactory<IRequestChannel>("MyRequestChannel");  
  
// Specify credentials.  
factory.Credentials.UserName.UserName = "myuser";  
factory.Credentials.UserName.Password = "mypassword";  
  
// Open the factory.  
factory.Open();  
  
// Get a channel and open it.  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
#### <a name="the-configuration-settings"></a><span data-ttu-id="d0ce8-125">Les paramètres de Configuration</span><span class="sxs-lookup"><span data-stu-id="d0ce8-125">The Configuration Settings</span></span>  
 <span data-ttu-id="d0ce8-126">Le code suivant illustre les paramètres de configuration utilisés pour l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-126">The following code shows the configuration settings used for the preceding example.</span></span> <span data-ttu-id="d0ce8-127">Le contrat pour le point de terminaison client doit être « System.ServiceModel.Channels.IRequestChannel » ou « System.ServiceModel.Channels.IOutputChannel » en fonction du type de la forme de canal que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-127">The contract for the client endpoint must be "System.ServiceModel.Channels.IRequestChannel" or "System.ServiceModel.Channels.IOutputChannel" depending on the kind of channel shape that you want to create.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    <system.serviceModel>  
        <bindings>  
            <sqlBinding>  
                <binding name="SqlAdapterBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" maxConnectionPoolSize="100"  
                    encrypt="false" useAmbientTransaction="true" batchSize="20"  
                    polledDataAvailableStatement="" pollingStatement="" pollingIntervalInSeconds="30"  
                    pollWhileDataFound="false" notificationStatement="" notifyOnListenerStart="true"  
                    enableBizTalkCompatibilityMode="true" chunkSize="4194304"  
                    inboundOperationType="Polling" useDatabaseNameInXsdNamespace="false"  
                    allowIdentityInsert="false" enablePerformanceCounters="false"  
                    xmlStoredProcedureRootNodeName="" xmlStoredProcedureRootNodeNamespace="" />  
            </sqlBinding>  
        </bindings>  
        <client>  
            <endpoint address="mssql://mysqlserver//mydatabase?" binding="sqlBinding"  
                bindingConfiguration="SqlAdapterBinding" contract="System.ServiceModel.Channels.IRequestChannel"  
                name="MyRequestChannel" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="creating-inbound-service-channels"></a><span data-ttu-id="d0ce8-128">Créer des canaux entrants (Service)</span><span class="sxs-lookup"><span data-stu-id="d0ce8-128">Creating Inbound (Service) Channels</span></span>  
 <span data-ttu-id="d0ce8-129">Vous configurez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour interroger les tables de base de données SQL Server et les vues en définissant les propriétés de liaison sur une instance de **sqlBinding**.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-129">You configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to poll the SQL Server database tables and views by setting binding properties on an instance of **sqlBinding**.</span></span> <span data-ttu-id="d0ce8-130">Vous utilisez ensuite cette liaison pour générer un écouteur de canal à partir de laquelle vous pouvez obtenir un **IInputChannel** canal pour recevoir le **d’interrogation**, **TypedPolling**, ou  **Notification** opération à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-130">You then use this binding to build a channel listener from which you can get an **IInputChannel** channel to receive the **Polling**, **TypedPolling**, or **Notification** operation from the adapter.</span></span>  
  
#### <a name="to-create-and-open-an-iinputchannel-to-receive-inbound-operations"></a><span data-ttu-id="d0ce8-131">Pour créer et ouvrir un IInputChannel pour recevoir les opérations entrantes</span><span class="sxs-lookup"><span data-stu-id="d0ce8-131">To create and open an IInputChannel to receive inbound operations</span></span>  
  
1.  <span data-ttu-id="d0ce8-132">Créez une instance de **SQLBinding**.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-132">Create an instance of **SQLBinding**.</span></span>  
  
2.  <span data-ttu-id="d0ce8-133">Définissez les propriétés de liaison requises pour l’opération entrante.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-133">Set the binding properties required for inbound operation.</span></span> <span data-ttu-id="d0ce8-134">Par exemple, pour un **d’interrogation** opération, au minimum, vous devez définir le **InboundOperationType**, **PolledDataAvailableStatement**, et  **PollingStatement** pour configurer les propriétés de liaison le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour interroger la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-134">For example, for a **Polling** operation, at a minimum you must set the **InboundOperationType**, **PolledDataAvailableStatement**, and **PollingStatement** binding properties to configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to poll the SQL Server database.</span></span>  
  
3.  <span data-ttu-id="d0ce8-135">Créer un écouteur de canal en appelant **BuildChannelListener\<IInputChannel >** méthode sur le **SQLBinding**.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-135">Create a channel listener by invoking **BuildChannelListener\<IInputChannel>** method on the **SQLBinding**.</span></span> <span data-ttu-id="d0ce8-136">Vous spécifiez l’URI de connexion SQL Server comme l’un des paramètres pour cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-136">You specify the SQL Server connection URI as one of the parameters to this method.</span></span>  
  
4.  <span data-ttu-id="d0ce8-137">Ouvrez le port d’écoute.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-137">Open the listener.</span></span>  
  
5.  <span data-ttu-id="d0ce8-138">Obtenir un **IInputChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-138">Get an **IInputChannel** channel by invoking the **AcceptChannel** method on listener.</span></span>  
  
6.  <span data-ttu-id="d0ce8-139">Ouvrir le canal.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-139">Open the channel.</span></span>  
  
 <span data-ttu-id="d0ce8-140">Le code suivant montre comment créer un écouteur de canal et obtenir un **IInputChannel** pour recevoir des messages de modification de données à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-140">The following code shows how to create a channel listener and get an **IInputChannel** to receive data-changed messages from the adapter.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d0ce8-141">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend uniquement en charge unidirectionnel de réception.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-141">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] only supports one-way receive.</span></span> <span data-ttu-id="d0ce8-142">Par conséquent, vous devez utiliser **IInputChannel** pour recevoir des messages pour les opérations entrantes à partir de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-142">So, you must use **IInputChannel** to receive messages for inbound operations from SQL Server.</span></span>  
  
```  
// Create a binding: specify the InboundOperationType, the PolledDataAvailableStatement, and   
// the PollingStatement binding properties.  
SqlAdapterBinding binding = new SqlAdapterBinding();  
binding.InboundOperationType = InboundOperation.Polling;  
binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
  
// Create a binding parameter collection and set the credentials  
ClientCredentials credentials = new ClientCredentials();  
credentials.UserName.UserName = "myuser";  
credentials.UserName.Password = "mypassword";  
  
BindingParameterCollection bindingParams = new BindingParameterCollection();  
bindingParams.Add(credentials);  
  
// Get a listener from the binding and open it.  
Uri connectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
listener.Open();  
  
// Get a channel from the listener and open it.  
IInputChannel channel = listener.AcceptChannel();  
channel.Open();  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0ce8-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0ce8-143">See Also</span></span>  
[<span data-ttu-id="d0ce8-144">Développer des applications à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="d0ce8-144">Develop applications using the WCF Channel model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)
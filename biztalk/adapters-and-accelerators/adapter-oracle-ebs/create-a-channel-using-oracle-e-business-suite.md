---
title: "Créer un canal à l’aide d’Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d18b7c2f-a43e-4499-ba94-4955dd5fe641
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d0f06a8f1e8b622574f20f331069d7ca280fc45c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="create-a-channel-using-oracle-e-business-suite"></a><span data-ttu-id="82743-102">Créer un canal à l’aide d’Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="82743-102">Create a channel using Oracle E-Business Suite</span></span>
<span data-ttu-id="82743-103">Dans le modèle de canal WCF, vous appeler des opérations sur Oracle E-Business Suite et recevoir les résultats en échangeant des messages SOAP avec le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] sur un canal WCF.</span><span class="sxs-lookup"><span data-stu-id="82743-103">In the WCF channel model, you invoke operations on the Oracle E-Business Suite and receive the results by exchanging SOAP messages with the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] over a WCF channel.</span></span>  
  
-   <span data-ttu-id="82743-104">Vous appelez operations (opérations sortantes) en utilisant un **IRequestChannel** ou un **IOutputChannel** pour envoyer des messages à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="82743-104">You invoke operations (outbound operations) by using either an **IRequestChannel** or an **IOutputChannel** to send messages to the adapter.</span></span>  
  
-   <span data-ttu-id="82743-105">Vous recevez des messages pour les opérations entrantes sur une **IInputChannel**.</span><span class="sxs-lookup"><span data-stu-id="82743-105">You receive messages for inbound operations over an **IInputChannel**.</span></span>  
  
 <span data-ttu-id="82743-106">Les rubriques de cette section fournissent des informations sur la façon de créer et configurer les formes de canal qui sont utilisés pour les opérations entrantes et sortantes.</span><span class="sxs-lookup"><span data-stu-id="82743-106">The topics in this section provide information about how to create and configure channel shapes that are used for inbound and outbound operations.</span></span>  
  
## <a name="creating-outbound-client-channels"></a><span data-ttu-id="82743-107">Créer des canaux sortants (Client)</span><span class="sxs-lookup"><span data-stu-id="82743-107">Creating Outbound (Client) Channels</span></span>  
 <span data-ttu-id="82743-108">Vous pouvez utiliser un **IRequestChannel** ou **IOutputChannel** pour appeler des opérations sur Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="82743-108">You can use either an **IRequestChannel** or an **IOutputChannel** to invoke operations on the Oracle E-Business Suite.</span></span> <span data-ttu-id="82743-109">Dans les deux cas, vous créez tout d’abord un **System.ServiceModel.ChannelFactory** à l’aide de l’interface appropriée.</span><span class="sxs-lookup"><span data-stu-id="82743-109">In either case, you first create a **System.ServiceModel.ChannelFactory** using the appropriate interface.</span></span> <span data-ttu-id="82743-110">Vous utilisez ensuite la fabrique pour créer le canal.</span><span class="sxs-lookup"><span data-stu-id="82743-110">You then use the factory to create the channel.</span></span> <span data-ttu-id="82743-111">Après avoir créé le canal, vous pouvez l’utiliser pour appeler des opérations sur la carte.</span><span class="sxs-lookup"><span data-stu-id="82743-111">After you have created the channel you can use it to invoke operations on the adapter.</span></span>  
  
#### <a name="to-create-and-open-an-outbound-channel"></a><span data-ttu-id="82743-112">Pour créer et ouvrir un canal sortant</span><span class="sxs-lookup"><span data-stu-id="82743-112">To create and open an outbound channel</span></span>  
  
1.  <span data-ttu-id="82743-113">Créer et initialiser une instance de **ChannelFactory** pour la forme du canal souhaitées à l’aide d’un point de terminaison et une liaison.</span><span class="sxs-lookup"><span data-stu-id="82743-113">Create and initialize an instance of **ChannelFactory** for the desired channel shape by using an endpoint and a binding.</span></span> <span data-ttu-id="82743-114">Le point de terminaison spécifie un URI de connexion Oracle E-Business Suite et de la liaison est une instance de **OracleEBSBinding**.</span><span class="sxs-lookup"><span data-stu-id="82743-114">The endpoint specifies an Oracle E-Business Suite connection URI and the binding is an instance of **OracleEBSBinding**.</span></span>  
  
2.  <span data-ttu-id="82743-115">Fournissent des informations d’identification Oracle E-Business Suite pour la fabrication de canal à l’aide de la **informations d’identification** propriété.</span><span class="sxs-lookup"><span data-stu-id="82743-115">Provide Oracle E-Business Suite credentials for the channel factory by using the **Credentials** property.</span></span>  
  
3.  <span data-ttu-id="82743-116">Ouvrez la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="82743-116">Open the channel factory.</span></span>  
  
4.  <span data-ttu-id="82743-117">Obtention d’une instance du canal en appelant le **CreateChannel** méthode sur la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="82743-117">Get an instance of the channel by invoking the **CreateChannel** method on the channel factory.</span></span>  
  
5.  <span data-ttu-id="82743-118">Ouvrir le canal.</span><span class="sxs-lookup"><span data-stu-id="82743-118">Open the channel.</span></span>  
  
 <span data-ttu-id="82743-119">Vous pouvez spécifier l’adresse de liaison et le point de terminaison dans votre code ou de configuration.</span><span class="sxs-lookup"><span data-stu-id="82743-119">You can specify the binding and endpoint address in your code or from configuration.</span></span>  
  
### <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="82743-120">Spécification de la liaison et l’adresse de point de terminaison dans le Code</span><span class="sxs-lookup"><span data-stu-id="82743-120">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="82743-121">L’exemple de code suivant montre comment créer un **IRequestChannel** en spécifiant l’adresse de liaison et le point de terminaison dans le code.</span><span class="sxs-lookup"><span data-stu-id="82743-121">The following code example shows how to create an **IRequestChannel** by specifying the binding and endpoint address in code.</span></span> <span data-ttu-id="82743-122">Le code pour créer un **IOutputChannel** est identique, sauf que vous devez spécifier un **IOutputChannel** de l’interface pour le **ChannelFactory** et type de canal.</span><span class="sxs-lookup"><span data-stu-id="82743-122">The code to create an **IOutputChannel** is the same except that you must specify an **IOutputChannel** interface for the **ChannelFactory** and channel type.</span></span>  
  
```  
// Create binding -- set binding properties before you open the factory.  
OracleEBSBinding binding = new OracleEBSBinding();  
  
// Create address  
EndpointAddress address = new EndpointAddress("oracleebs://<oracleebs_instance_name>/");  
  
// Create channel factory from binding and address.  
ChannelFactory<IRequestChannel> factory =   
    new ChannelFactory<IRequestChannel>(binding, address);  
  
// Specify credentials.   
factory.Credentials.UserName.UserName = "myuser";  
factory.Credentials.UserName.Password = "mypassword";  
  
// Open factory  
factory.Open();  
  
// Get channel and open it.  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
### <a name="specifying-the-binding-and-endpoint-address-in-configuration"></a><span data-ttu-id="82743-123">Spécification de la liaison et l’adresse de point de terminaison dans la Configuration</span><span class="sxs-lookup"><span data-stu-id="82743-123">Specifying the Binding and Endpoint Address in Configuration</span></span>  
 <span data-ttu-id="82743-124">L’exemple de code suivant montre comment créer une fabrique de canaux à partir d’un point de terminaison de client spécifié dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="82743-124">The following code example shows how to create a channel factory from a client endpoint specified in configuration.</span></span>  
  
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
  
#### <a name="the-configuration-settings"></a><span data-ttu-id="82743-125">Les paramètres de Configuration</span><span class="sxs-lookup"><span data-stu-id="82743-125">The Configuration Settings</span></span>  
 <span data-ttu-id="82743-126">Le code suivant illustre les paramètres de configuration utilisés pour l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="82743-126">The following code shows the configuration settings used for the preceding example.</span></span> <span data-ttu-id="82743-127">Le contrat pour le point de terminaison client doit être « System.ServiceModel.Channels.IRequestChannel » ou « System.ServiceModel.Channels.IOutputChannel » en fonction du type de la forme de canal que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="82743-127">The contract for the client endpoint must be "System.ServiceModel.Channels.IRequestChannel" or "System.ServiceModel.Channels.IOutputChannel" depending on the kind of channel shape that you want to create.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    <system.serviceModel>  
        <bindings>  
            <oracleEBSBinding>  
                <binding openTimeout="00:05:00" name="OracleEBSBinding" closeTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" clientCredentialType="Database"  
                    inboundOperationType="Polling" metadataPooling="true" statementCachePurge="false"  
                    statementCacheSize="10" pollWhileDataFound="false" pollingInterval="30"  
                    useOracleConnectionPool="true" minPoolSize="1" maxPoolSize="100"  
                    incrPoolSize="5" decrPoolSize="1" connectionLifetime="0" acceptCredentialsInUri="false"  
                    useAmbientTransaction="true" notifyOnListenerStart="true"  
                    notificationPort="-1" dataFetchSize="65536" longDatatypeColumnSize="0"  
                    skipNilNodes="true" maxOutputAssociativeArrayElements="32"  
                    enableSafeTyping="false" insertBatchSize="20" useSchemaInNameSpace="true"  
                    enableBizTalkCompatibilityMode="true" enablePerformanceCounters="false">  
                    <mlsSettings language="" dateFormat="" dateLanguage="" numericCharacters=""  
                        sort="" territory="" comparison="" currency="" dualCurrency=""  
                        iSOCurrency="" calendar="" lengthSemantics="" nCharConversionException="true"  
                        timeStampFormat="" timeStampTZFormat="" timeZone="" />  
                </binding>  
            </oracleEBSBinding>  
        </bindings>  
        <client>  
            <endpoint address="oracleebs://oracle_ebs_instance/" binding="oracleEBSBinding"  
                bindingConfiguration="OracleEBSBinding" contract="System.ServiceModel.Channels.IRequestChannel"  
                name="MyRequestChannel" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="creating-inbound-service-channels"></a><span data-ttu-id="82743-128">Créer des canaux entrants (Service)</span><span class="sxs-lookup"><span data-stu-id="82743-128">Creating Inbound (Service) Channels</span></span>  
 <span data-ttu-id="82743-129">Vous configurez le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour interroger les tables de base de données Oracle et les vues en définissant les propriétés de liaison sur une instance de **OracleEBSBinding**.</span><span class="sxs-lookup"><span data-stu-id="82743-129">You configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll the Oracle database tables and views by setting binding properties on an instance of **OracleEBSBinding**.</span></span> <span data-ttu-id="82743-130">Vous utilisez ensuite cette liaison pour générer un écouteur de canal à partir de laquelle vous pouvez obtenir un **IInputChannel** canal pour recevoir les opérations entrantes à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="82743-130">You then use this binding to build a channel listener from which you can get an **IInputChannel** channel to receive inbound operations from the adapter.</span></span>  
  
##### <a name="to-create-and-open-an-iinputchannel-to-receive-messages-for-inbound-operations"></a><span data-ttu-id="82743-131">Pour créer et ouvrir un IInputChannel pour recevoir des messages pour les opérations entrantes</span><span class="sxs-lookup"><span data-stu-id="82743-131">To create and open an IInputChannel to receive messages for inbound operations</span></span>  
  
1.  <span data-ttu-id="82743-132">Créez une instance de **OracleEBSBinding**.</span><span class="sxs-lookup"><span data-stu-id="82743-132">Create an instance of **OracleEBSBinding**.</span></span>  
  
2.  <span data-ttu-id="82743-133">Définissez les propriétés de liaison requises pour l’opération entrante.</span><span class="sxs-lookup"><span data-stu-id="82743-133">Set the binding properties required for the inbound operation.</span></span> <span data-ttu-id="82743-134">Par exemple, pour une opération d’interrogation, au minimum vous devez définir le **InboundOperationType**, **PolledDataAvailableStatement**, **PollingAction**et le **PollingInput** pour configurer les propriétés de liaison le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour interroger la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="82743-134">For example, for a polling operation, at a minimum you must set the **InboundOperationType**, **PolledDataAvailableStatement**, **PollingAction**, and the **PollingInput** binding properties to configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll the Oracle database.</span></span>  
  
3.  <span data-ttu-id="82743-135">Créer une collection de paramètres de liaison à l’aide du **BindingParameterCollection** puis définissez les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="82743-135">Create a binding parameter collection using the **BindingParameterCollection** class and set the credentials.</span></span>  
  
4.  <span data-ttu-id="82743-136">Créer un écouteur de canal en appelant **BuildChannelListener\<IInputChannel\>**  méthode sur le **OracleEBSBinding**.</span><span class="sxs-lookup"><span data-stu-id="82743-136">Create a channel listener by invoking **BuildChannelListener\<IInputChannel\>** method on the **OracleEBSBinding**.</span></span> <span data-ttu-id="82743-137">Vous spécifiez l’URI de connexion Oracle en tant qu’un des paramètres à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="82743-137">You specify the Oracle connection URI as one of the parameters to this method.</span></span>  
  
5.  <span data-ttu-id="82743-138">Ouvrez le port d’écoute.</span><span class="sxs-lookup"><span data-stu-id="82743-138">Open the listener.</span></span>  
  
6.  <span data-ttu-id="82743-139">Obtenir un **IInputChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="82743-139">Get an **IInputChannel** channel by invoking the **AcceptChannel** method on listener.</span></span>  
  
7.  <span data-ttu-id="82743-140">Ouvrir le canal.</span><span class="sxs-lookup"><span data-stu-id="82743-140">Open the channel.</span></span>  
  
 <span data-ttu-id="82743-141">Le code suivant montre comment créer un écouteur de canal et obtenir un **IInputChannel** pour recevoir des messages pour les opérations entrantes à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="82743-141">The following code shows how to create a channel listener and get an **IInputChannel** to receive messages for inbound operations from the adapter.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="82743-142">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend uniquement en charge unidirectionnel de réception.</span><span class="sxs-lookup"><span data-stu-id="82743-142">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] only supports one-way receive.</span></span> <span data-ttu-id="82743-143">Par conséquent, vous devez utiliser **IInputChannel** pour recevoir des messages pour les opérations entrantes à partir d’Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="82743-143">So, you must use **IInputChannel** to receive messages for inbound operations from Oracle E-Business Suite.</span></span>  
  
```  
// Create a binding: specify the InboundOperationType, the PolledDataAvailableStatement, the PollingAction, and   
// the PollingInput binding properties.  
OracleEBSBinding binding = new OracleEBSBinding();  
binding.InboundOperationType = InboundOperation.Polling;  
binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
  
// Create a binding parameter collection and set the credentials  
ClientCredentials credentials = new ClientCredentials();  
credentials.UserName.UserName = "myuser";  
credentials.UserName.Password = "mypassword";  
  
BindingParameterCollection bindingParams = new BindingParameterCollection();  
bindingParams.Add(credentials);  
  
// Get a listener from the binding and open it.  
Uri connectionUri = new Uri("oracleebs://oracle_ebs_instance/");  
IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
listener.Open();  
  
// Get a channel from the listener and open it.  
IInputChannel channel = listener.AcceptChannel();  
channel.Open();  
```  
  
## <a name="see-also"></a><span data-ttu-id="82743-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82743-144">See Also</span></span>  
 [<span data-ttu-id="82743-145">Développer des applications d’Oracle E-Business Suite à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="82743-145">Develop Oracle E-Business Suite applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)
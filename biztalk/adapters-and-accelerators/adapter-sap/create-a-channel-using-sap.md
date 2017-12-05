---
title: "Créer un canal à l’aide de SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- channel programming, creating a channel
- how to, create a channel
- creating a channel
- WCF channel model, creating a channel
ms.assetid: 24af1465-bb60-41d7-98bd-e501a981f82a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22a0d6e48d1a33e4d7c0aec8a1231346a671c1ef
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="create-a-channel-using-sap"></a><span data-ttu-id="d7d8e-102">Créer un canal à l’aide de SAP</span><span class="sxs-lookup"><span data-stu-id="d7d8e-102">Create a channel using SAP</span></span>
<span data-ttu-id="d7d8e-103">Dans le modèle de canal WCF, vous pouvez appeler des opérations sur le système SAP ou recevoir des messages à partir du système SAP en échangeant des messages SOAP avec le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] sur un canal WCF.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-103">In the WCF channel model, you invoke operations on the SAP system or receive messages from the SAP system by exchanging SOAP messages with the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] over a WCF channel.</span></span>  
  
-   <span data-ttu-id="d7d8e-104">Vous appelez operations (opérations sortantes) en utilisant un **IRequestChannel** ou un **IOutputChannel** pour envoyer des messages à l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="d7d8e-104">You invoke operations (outbound operations) by using either an **IRequestChannel** or an **IOutputChannel** to send messages to the adapter</span></span>  
  
-   <span data-ttu-id="d7d8e-105">Vous recevez des messages (déclenchés à partir du système SAP) sur un **IReplyChannel**.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-105">You receive messages (triggered from the SAP system) over an **IReplyChannel**.</span></span>  
  
 <span data-ttu-id="d7d8e-106">Les rubriques de cette section fournissent des informations sur la façon de créer et configurer les formes de canal qui sont utilisés pour les opérations entrantes et sortantes.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-106">The topics in this section provide information about how to create and configure channel shapes that are used for inbound and outbound operations.</span></span>  
  
## <a name="creating-outbound-client-channels"></a><span data-ttu-id="d7d8e-107">Créer des canaux sortants (Client)</span><span class="sxs-lookup"><span data-stu-id="d7d8e-107">Creating Outbound (Client) Channels</span></span>  
 <span data-ttu-id="d7d8e-108">Vous pouvez utiliser un **IRequestChannel** ou **IOutputChannel** pour appeler des opérations sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-108">You can use either an **IRequestChannel** or an **IOutputChannel** to invoke operations on the SAP system.</span></span> <span data-ttu-id="d7d8e-109">Dans les deux cas, vous créez tout d’abord un **System.ServiceModel.ChannelFactory** à l’aide de l’interface appropriée.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-109">In either case, you first create a **System.ServiceModel.ChannelFactory** using the appropriate interface.</span></span> <span data-ttu-id="d7d8e-110">Vous utilisez ensuite la fabrique pour créer le canal.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-110">You then use the factory to create the channel.</span></span> <span data-ttu-id="d7d8e-111">Après avoir créé le canal, vous pouvez l’utiliser pour appeler des opérations sur la carte.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-111">After you have created the channel you can use it to invoke operations on the adapter.</span></span>  
  
#### <a name="to-create-and-open-an-outbound-channel"></a><span data-ttu-id="d7d8e-112">Pour créer et ouvrir un canal sortant</span><span class="sxs-lookup"><span data-stu-id="d7d8e-112">To create and open an outbound channel</span></span>  
  
1.  <span data-ttu-id="d7d8e-113">Créer et initialiser une instance de **ChannelFactory** pour la forme du canal souhaitées à l’aide d’un point de terminaison et une liaison.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-113">Create and initialize an instance of **ChannelFactory** for the desired channel shape by using an endpoint and a binding.</span></span> <span data-ttu-id="d7d8e-114">Le point de terminaison spécifie un URI de connexion SAP et la liaison est une instance de **SAPDBBinding**.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-114">The endpoint specifies an SAP connection URI and the binding is an instance of **SAPDBBinding**.</span></span> <span data-ttu-id="d7d8e-115">(Définir des propriétés de liaison requises avant d’ouvrir la fabrication de canal.)</span><span class="sxs-lookup"><span data-stu-id="d7d8e-115">(Set any binding properties required before you open the channel factory.)</span></span>  
  
2.  <span data-ttu-id="d7d8e-116">Fournir des informations d’identification SAP pour la fabrication de canal à l’aide de la **ClientCredentials** propriété.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-116">Provide SAP credentials for the channel factory by using the **ClientCredentials** property.</span></span>  
  
3.  <span data-ttu-id="d7d8e-117">Ouvrez la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-117">Open the channel factory.</span></span>  
  
4.  <span data-ttu-id="d7d8e-118">Obtention d’une instance du canal en appelant le **CreateChannel** méthode sur la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-118">Get an instance of the channel by invoking the **CreateChannel** method on the channel factory.</span></span>  
  
5.  <span data-ttu-id="d7d8e-119">Ouvrir le canal.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-119">Open the channel.</span></span>  
  
 <span data-ttu-id="d7d8e-120">Vous pouvez spécifier l’adresse de liaison et le point de terminaison dans votre code ou de configuration.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-120">You can specify the binding and endpoint address in your code or from configuration.</span></span>  
  
### <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="d7d8e-121">Spécification de la liaison et l’adresse de point de terminaison dans le Code</span><span class="sxs-lookup"><span data-stu-id="d7d8e-121">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="d7d8e-122">L’exemple de code suivant montre comment créer un **IRequestChannel** en spécifiant l’adresse de liaison et le point de terminaison dans le code.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-122">The following code example shows how to create an **IRequestChannel** by specifying the binding and endpoint address in code.</span></span> <span data-ttu-id="d7d8e-123">Le code pour créer un **IOutputChannel** est identique, sauf que vous devez spécifier un **IOutputChannel** de l’interface pour le **ChannelFactory** et type de canal.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-123">The code to create an **IOutputChannel** is the same except that you must specify an **IOutputChannel** interface for the **ChannelFactory** and channel type.</span></span>  
  
```  
// Create binding -- set binding properties before you open the factory.  
SAPBinding sapBinding = new SAPBinding();  
  
// Create address.  
EndpointAddress sapAddress = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
// Create channel factory from binding and address.  
ChannelFactory<IRequestChannel> factory =   
    new ChannelFactory<IRequestChannel>(sapBinding, sapAddress);  
  
// Specify credentials.   
factory.Credentials.UserName.UserName = "YourUserName";  
factory.Credentials.UserName.Password = "YourPassword";  
  
// Open the factory  
factory.Open();  
  
// Get channel and open it.  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
### <a name="specifying-the-binding-and-endpoint-address-in-configuration"></a><span data-ttu-id="d7d8e-124">Spécification de la liaison et l’adresse de point de terminaison dans la Configuration</span><span class="sxs-lookup"><span data-stu-id="d7d8e-124">Specifying the Binding and Endpoint Address in Configuration</span></span>  
 <span data-ttu-id="d7d8e-125">L’exemple de code suivant montre comment créer une fabrique de canaux à partir d’un point de terminaison de client spécifié dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-125">The following code example shows how to create a channel factory from a client endpoint specified in configuration.</span></span>  
  
```  
// Create channel factory from configuration.  
ChannelFactory<IRequestChannel> factory =  
new ChannelFactory<IRequestChannel>("MyRequestChannel");  
  
// Specify credentials.  
factory.Credentials.UserName.UserName = "YourUserName";  
factory.Credentials.UserName.Password = "YourPassword";  
  
// Open the factory.  
factory.Open();  
  
// Get a channel and open it.  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
#### <a name="the-configuration-settings"></a><span data-ttu-id="d7d8e-126">Les paramètres de Configuration</span><span class="sxs-lookup"><span data-stu-id="d7d8e-126">The Configuration Settings</span></span>  
 <span data-ttu-id="d7d8e-127">Le code suivant illustre les paramètres de configuration utilisés pour l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-127">The following code shows the configuration settings used for the preceding example.</span></span> <span data-ttu-id="d7d8e-128">Le contrat pour le point de terminaison client doit être « System.ServiceModel.Channels.IRequestChannel » ou « System.ServiceModel.Channels.IRequestChannel » en fonction du type de la forme de canal que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-128">The contract for the client endpoint must be "System.ServiceModel.Channels.IRequestChannel" or "System.ServiceModel.Channels.IRequestChannel" depending on the kind of channel shape that you want to create.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    <system.serviceModel>  
        <bindings>  
            <sapBinding>  
                <binding name="SAPBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" enableBizTalkCompatibilityMode="false"  
                    receiveIdocFormat="Typed" enableSafeTyping="false" generateFlatFileCompatibleIdocSchema="true"  
                    maxConnectionsPerSystem="50" enableConnectionPooling="true"  
                    idleConnectionTimeout="00:15:00" flatFileSegmentIndicator="SegmentDefinition"  
                    enablePerformanceCounters="false" autoConfirmSentIdocs="false"  
                    acceptCredentialsInUri="false"  
                    padReceivedIdocWithSpaces="false" sncLibrary="" sncPartnerName="" />  
            </sapBinding>  
        </bindings>  
        <client>  
            <endpoint address="sap://CLIENT=800;LANG=EN;@a/ADAPSAP47/00?RfcSdkTrace=False&AbapDebug=False"  
                binding="sapBinding" bindingConfiguration="SAPBinding" contract="System.ServiceModel.Channels.IRequestChannel"  
                name="MyRequestChannel" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="creating-inbound-service-channels"></a><span data-ttu-id="d7d8e-129">Créer des canaux entrants (Service)</span><span class="sxs-lookup"><span data-stu-id="d7d8e-129">Creating Inbound (Service) Channels</span></span>  
 <span data-ttu-id="d7d8e-130">Vous configurez la carte pour recevoir les messages entrants à partir d’un système SAP en définissant les propriétés de liaison sur une instance de **SAPBinding**.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-130">You configure the adapter to receive inbound messages from an SAP system by setting binding properties on an instance of **SAPBinding**.</span></span> <span data-ttu-id="d7d8e-131">Vous utilisez ensuite cette liaison pour générer un écouteur de canal à partir de laquelle vous pouvez obtenir un **IReplyChannel** canal pour les opérations de réception de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-131">You then use this binding to build a channel listener from which you can get an **IReplyChannel** channel to receive operations from the adapter.</span></span>  
  
##### <a name="to-create-and-open-an-ireplychannel-to-receive-data-changed-notifications"></a><span data-ttu-id="d7d8e-132">Pour créer et ouvrir un IReplyChannel aux Notifications de modification de recevoir des données</span><span class="sxs-lookup"><span data-stu-id="d7d8e-132">To create and open an IReplyChannel to Receive Data-changed Notifications</span></span>  
  
1.  <span data-ttu-id="d7d8e-133">Créez une instance de **SAPBinding**.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-133">Create an instance of **SAPBinding**.</span></span>  
  
2.  <span data-ttu-id="d7d8e-134">Définir des propriétés de liaison requises pour les opérations que vous souhaitez recevoir.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-134">Set any binding properties required for the operations you want to receive.</span></span> <span data-ttu-id="d7d8e-135">Veillez à définir le **AcceptCredentialsInUri** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-135">Be sure to set the **AcceptCredentialsInUri** binding property.</span></span>  
  
3.  <span data-ttu-id="d7d8e-136">Créer un **BindingParameterCollection** et ajoutez un **InboundActionCollection** qui contient les actions des opérations que vous souhaitez recevoir.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-136">Create a **BindingParameterCollection** and add an **InboundActionCollection** that contains the actions of the operations that you want to receive.</span></span> <span data-ttu-id="d7d8e-137">L’adaptateur renvoie une exception au système SAP pour toutes les autres opérations.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-137">The adapter will return an exception to the SAP system for all other operations.</span></span> <span data-ttu-id="d7d8e-138">Cette étape est facultative.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-138">This step is optional.</span></span> <span data-ttu-id="d7d8e-139">Pour plus d’informations, consultez [recevoir des opérations de trafic entrant à partir du système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md).</span><span class="sxs-lookup"><span data-stu-id="d7d8e-139">For more information, see [Receiving Inbound Operations from the SAP System by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md).</span></span>  
  
4.  <span data-ttu-id="d7d8e-140">Créer un écouteur de canal en appelant **BuildChannelListener\<IReplyChannel\>**  méthode sur le **SAPBinding**.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-140">Create a channel listener by invoking **BuildChannelListener\<IReplyChannel\>** method on the **SAPBinding**.</span></span> <span data-ttu-id="d7d8e-141">Vous spécifiez l’URI de connexion SAP comme l’un des paramètres pour cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-141">You specify the SAP connection URI as one of the parameters to this method.</span></span> <span data-ttu-id="d7d8e-142">L’URI de connexion doit contenir des paramètres pour une Destination RFC sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-142">The connection URI must contain parameters for an RFC Destination on the SAP system.</span></span> <span data-ttu-id="d7d8e-143">Pour plus d’informations sur l’URI de connexion SAP, consultez le [créer l’URI de connexion du système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="d7d8e-143">For more information about the SAP connection URI, see The [Create the SAP System Connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span> <span data-ttu-id="d7d8e-144">Si vous avez créé un **BindingParameterCollection** à l’étape 3, vous également spécifiez cela lorsque vous créez l’écouteur de canal.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-144">If you created a **BindingParameterCollection** in step 3, you also specify this when you create the channel listener.</span></span>  
  
5.  <span data-ttu-id="d7d8e-145">Ouvrez le port d’écoute.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-145">Open the listener.</span></span>  
  
6.  <span data-ttu-id="d7d8e-146">Obtenir un **IReplyChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-146">Get an **IReplyChannel** channel by invoking the **AcceptChannel** method on listener.</span></span>  
  
7.  <span data-ttu-id="d7d8e-147">Ouvrir le canal.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-147">Open the channel.</span></span>  
  
 <span data-ttu-id="d7d8e-148">Le code suivant montre comment créer un écouteur de canal et obtenir un **IReplyChannel** pour les opérations de réception de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="d7d8e-148">The following code shows how to create a channel listener and get an **IReplyChannel** to receive operations from the adapter.</span></span>  
  
```  
// Create a binding and specify any binding properties required  
// for the opreations you want to receive  
SAPBinding binding = new SAPBinding();  
  
// Set AcceptCredentialsInUri because the URI must contain credentials.  
binding.AcceptCredentialsInUri = true;  
  
// Create an InboundActionCollection and add the message actions to listen for,  
// only the actions added to the InboundActionCollection are received on the channel.  
// In this case a single action is specified: http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_ADD  
InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_ADD");  
  
// Create a BindingParameterCollection and add the InboundActionCollection  
BindingParameterCollection bpcol = new BindingParameterCollection();  
bpcol.Add(actions);  
  
// Create the channel listener by specifying  
// the binding parameter collection (to filter for the Z_RFC_MKD_ADD action) and   
// a connection URI that contains listener parameters.  
Uri listeneraddress =  
new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
listener = binding.BuildChannelListener<IReplyChannel>(connectionUri, new BindingParameterCollection());  
listener.Open();  
  
// Get a channel from the listener and open it.  
channel = listener.AcceptChannel();  
channel.Open();  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7d8e-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7d8e-149">See Also</span></span>  
[<span data-ttu-id="d7d8e-150">Développer des applications en utilisant le modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="d7d8e-150">Develop applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)
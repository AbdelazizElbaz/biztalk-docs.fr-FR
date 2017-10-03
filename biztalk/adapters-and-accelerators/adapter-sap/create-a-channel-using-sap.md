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
ms.openlocfilehash: 1f69fbeb86cf63485591f048ef75cdcfd3d5056d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-channel-using-sap"></a>Créer un canal à l’aide de SAP
Dans le modèle de canal WCF, vous pouvez appeler des opérations sur le système SAP ou recevoir des messages à partir du système SAP en échangeant des messages SOAP avec le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] sur un canal WCF.  
  
-   Vous appelez operations (opérations sortantes) en utilisant un **IRequestChannel** ou un **IOutputChannel** pour envoyer des messages à l’adaptateur  
  
-   Vous recevez des messages (déclenchés à partir du système SAP) sur un **IReplyChannel**.  
  
 Les rubriques de cette section fournissent des informations sur la façon de créer et configurer les formes de canal qui sont utilisés pour les opérations entrantes et sortantes.  
  
## <a name="creating-outbound-client-channels"></a>Créer des canaux sortants (Client)  
 Vous pouvez utiliser un **IRequestChannel** ou **IOutputChannel** pour appeler des opérations sur le système SAP. Dans les deux cas, vous créez tout d’abord un **System.ServiceModel.ChannelFactory** à l’aide de l’interface appropriée. Vous utilisez ensuite la fabrique pour créer le canal. Après avoir créé le canal, vous pouvez l’utiliser pour appeler des opérations sur la carte.  
  
#### <a name="to-create-and-open-an-outbound-channel"></a>Pour créer et ouvrir un canal sortant  
  
1.  Créer et initialiser une instance de **ChannelFactory** pour la forme du canal souhaitées à l’aide d’un point de terminaison et une liaison. Le point de terminaison spécifie un URI de connexion SAP et la liaison est une instance de **SAPDBBinding**. (Définir des propriétés de liaison requises avant d’ouvrir la fabrication de canal.)  
  
2.  Fournir des informations d’identification SAP pour la fabrication de canal à l’aide de la **ClientCredentials** propriété.  
  
3.  Ouvrez la fabrication de canal.  
  
4.  Obtention d’une instance du canal en appelant le **CreateChannel** méthode sur la fabrication de canal.  
  
5.  Ouvrir le canal.  
  
 Vous pouvez spécifier l’adresse de liaison et le point de terminaison dans votre code ou de configuration.  
  
### <a name="specifying-the-binding-and-endpoint-address-in-code"></a>Spécification de la liaison et l’adresse de point de terminaison dans le Code  
 L’exemple de code suivant montre comment créer un **IRequestChannel** en spécifiant l’adresse de liaison et le point de terminaison dans le code. Le code pour créer un **IOutputChannel** est identique, sauf que vous devez spécifier un **IOutputChannel** de l’interface pour le **ChannelFactory** et type de canal.  
  
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
  
### <a name="specifying-the-binding-and-endpoint-address-in-configuration"></a>Spécification de la liaison et l’adresse de point de terminaison dans la Configuration  
 L’exemple de code suivant montre comment créer une fabrique de canaux à partir d’un point de terminaison de client spécifié dans la configuration.  
  
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
  
#### <a name="the-configuration-settings"></a>Les paramètres de Configuration  
 Le code suivant illustre les paramètres de configuration utilisés pour l’exemple précédent. Le contrat pour le point de terminaison client doit être « System.ServiceModel.Channels.IRequestChannel » ou « System.ServiceModel.Channels.IRequestChannel » en fonction du type de la forme de canal que vous souhaitez créer.  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    \<system.serviceModel>  
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
    \</system.serviceModel>  
</configuration>  
```  
  
### <a name="creating-inbound-service-channels"></a>Créer des canaux entrants (Service)  
 Vous configurez la carte pour recevoir les messages entrants à partir d’un système SAP en définissant les propriétés de liaison sur une instance de **SAPBinding**. Vous utilisez ensuite cette liaison pour générer un écouteur de canal à partir de laquelle vous pouvez obtenir un **IReplyChannel** canal pour les opérations de réception de l’adaptateur.  
  
##### <a name="to-create-and-open-an-ireplychannel-to-receive-data-changed-notifications"></a>Pour créer et ouvrir un IReplyChannel aux Notifications de modification de recevoir des données  
  
1.  Créez une instance de **SAPBinding**.  
  
2.  Définir des propriétés de liaison requises pour les opérations que vous souhaitez recevoir. Veillez à définir le **AcceptCredentialsInUri** propriété de liaison.  
  
3.  Créer un **BindingParameterCollection** et ajoutez un **InboundActionCollection** qui contient les actions des opérations que vous souhaitez recevoir. L’adaptateur renvoie une exception au système SAP pour toutes les autres opérations. Cette étape est facultative. Pour plus d’informations, consultez [recevoir des opérations de trafic entrant à partir du système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md).  
  
4.  Créer un écouteur de canal en appelant **BuildChannelListener\<IReplyChannel >** méthode sur le **SAPBinding**. Vous spécifiez l’URI de connexion SAP comme l’un des paramètres pour cette méthode. L’URI de connexion doit contenir des paramètres pour une Destination RFC sur le système SAP. Pour plus d’informations sur l’URI de connexion SAP, consultez le [créer l’URI de connexion du système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md). Si vous avez créé un **BindingParameterCollection** à l’étape 3, vous également spécifiez cela lorsque vous créez l’écouteur de canal.  
  
5.  Ouvrez le port d’écoute.  
  
6.  Obtenir un **IReplyChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur.  
  
7.  Ouvrir le canal.  
  
 Le code suivant montre comment créer un écouteur de canal et obtenir un **IReplyChannel** pour les opérations de réception de l’adaptateur.  
  
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
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)
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
# <a name="create-a-channel-using-oracle-database"></a>Créer un canal à l’aide de la base de données Oracle
Dans le modèle de canal WCF, vous appeler des opérations sur la base de données Oracle et recevoir les résultats d’une requête d’interrogation en échangeant des messages SOAP avec le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] sur un canal WCF.  
  
-   Vous appelez operations (opérations sortantes) en utilisant un **IRequestChannel** ou un **IOutputChannel** pour envoyer des messages à l’adaptateur.  
  
-   Vous recevez des messages d’interrogation de données modifiées en recevant des messages POLLINGSTMT sur une **IInputChannel**.  
  
 Les rubriques de cette section fournissent des informations sur la façon de créer et configurer les formes de canal qui sont utilisés pour les opérations entrantes et sortantes.  
  
## <a name="creating-outbound-client-channels"></a>Créer des canaux sortants (Client)  
 Vous pouvez utiliser un **IRequestChannel** ou **IOutputChannel** pour appeler des opérations sur la base de données Oracle. Dans les deux cas, vous créez tout d’abord un **System.ServiceModel.ChannelFactory** à l’aide de l’interface appropriée. Vous utilisez ensuite la fabrique pour créer le canal. Après avoir créé le canal, vous pouvez l’utiliser pour appeler des opérations sur la carte.  
  
#### <a name="to-create-and-open-an-outbound-channel"></a>Pour créer et ouvrir un canal sortant  
  
1.  Créer et initialiser une instance de **ChannelFactory** pour la forme du canal souhaitées à l’aide d’un point de terminaison et une liaison. Le point de terminaison spécifie un URI de connexion Oracle et de la liaison est une instance de **OracleDBBinding**.  
  
2.  Fournir des informations d’identification Oracle pour la fabrication de canal à l’aide de la **informations d’identification** propriété.  
  
3.  Ouvrez la fabrication de canal.  
  
4.  Obtention d’une instance du canal en appelant le **CreateChannel** méthode sur la fabrication de canal.  
  
5.  Ouvrir le canal.  
  
 Vous pouvez spécifier l’adresse de liaison et le point de terminaison dans votre code ou de configuration.  
  
### <a name="specifying-the-binding-and-endpoint-address-in-code"></a>Spécification de la liaison et l’adresse de point de terminaison dans le Code  
 L’exemple de code suivant montre comment créer un **IRequestChannel** en spécifiant l’adresse de liaison et le point de terminaison dans le code. Le code pour créer un **IOutputChannel** est identique, sauf que vous devez spécifier un **IOutputChannel** de l’interface pour le **ChannelFactory** et type de canal.  
  
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
  
### <a name="specifying-the-binding-and-endpoint-address-in-configuration"></a>Spécification de la liaison et l’adresse de point de terminaison dans la Configuration  
 L’exemple de code suivant montre comment créer une fabrique de canaux à partir d’un point de terminaison de client spécifié dans la configuration.  
  
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
  
#### <a name="the-configuration-settings"></a>Les paramètres de Configuration  
 Le code suivant illustre les paramètres de configuration utilisés pour l’exemple précédent. Le contrat pour le point de terminaison client doit être « System.ServiceModel.Channels.IRequestChannel » ou « System.ServiceModel.Channels.IRequestChannel » en fonction du type de la forme de canal que vous souhaitez créer.  
  
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
  
### <a name="creating-inbound-service-channels"></a>Créer des canaux entrants (Service)  
 Vous configurez le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour interroger les tables de base de données Oracle et les vues en définissant les propriétés de liaison sur une instance de **OracleDBBinding**. Vous utilisez ensuite cette liaison pour générer un écouteur de canal à partir de laquelle vous pouvez obtenir un **IInputChannel** canal pour recevoir des messages pour les opérations entrantes à partir de l’adaptateur.  
  
##### <a name="to-create-and-open-an-iinputchannel-to-receive-messages-for-inbound-operations"></a>Pour créer et ouvrir un IInputChannel pour recevoir des messages pour les opérations entrantes  
  
1.  Créez une instance de **OracleDBBinding**.  
  
2.  Définissez les propriétés de liaison requises pour l’opération entrante. Par exemple, pour l’opération POLLINGSTMT, au minimum vous devez définir le **InboundOperationType**, **PollingStatement**, et **PollingInterval** propriétés de liaison configurer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour interroger la base de données Oracle.  
  
3.  Créer une collection de paramètres de liaison à l’aide du **BindingParameterCollection** puis définissez les informations d’identification.  
  
4.  Créer un écouteur de canal en appelant **BuildChannelListener\<IInputChannel\>**  méthode sur le **OracleDBBinding**. Vous spécifiez l’URI de connexion Oracle en tant qu’un des paramètres à cette méthode. Pour plus d’informations sur l’URI de connexion Oracle, consultez [créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).  
  
5.  Ouvrez le port d’écoute.  
  
6.  Obtenir un **IInputChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur.  
  
7.  Ouvrir le canal.  
  
 Le code suivant montre comment créer un écouteur de canal et obtenir un **IInputChannel** pour les messages sortants depuis l’adaptateur à l’aide de l’opération POLLINGSTMT.  
  
> [!NOTE]
>  Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend uniquement en charge unidirectionnel de réception. Par conséquent, vous devez utiliser IInputChannel pour recevoir des messages pour les opérations entrantes à partir de la base de données Oracle.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications de base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)
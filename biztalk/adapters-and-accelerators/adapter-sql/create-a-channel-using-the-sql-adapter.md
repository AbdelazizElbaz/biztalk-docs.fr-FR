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
# <a name="create-a-channel-using-the-sql-adapter"></a>Créer un canal à l’aide de l’adaptateur SQL
Dans le modèle de canal WCF, vous appeler des opérations sur la base de données SQL Server et recevoir les résultats en échangeant des messages SOAP avec le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] sur un canal WCF.  
  
-   Vous appelez des opérations sortantes en utilisant un **IRequestChannel** ou un **IOutputChannel** pour envoyer des messages à l’adaptateur.  
  
-   Vous recevez des messages pour les opérations entrantes en recevant des messages via un **IInputChannel** pour **d’interrogation**, **TypedPolling**, ou **deNotification** operations.  
  
 Les procédures décrites dans cette rubrique fournissent des informations sur la façon de créer et configurer les formes de canal qui sont utilisés pour les opérations entrantes et sortantes.  
  
## <a name="creating-outbound-client-channels"></a>Créer des canaux sortants (Client)  
 Vous pouvez utiliser un **IRequestChannel** ou **IOutputChannel** pour appeler des opérations sur la base de données SQL Server. Dans les deux cas, vous créez tout d’abord un **System.ServiceModel.ChannelFactory** à l’aide de l’interface appropriée. Vous utilisez ensuite la fabrique pour créer le canal. Après avoir créé le canal, vous pouvez l’utiliser pour appeler des opérations sur la carte.  
  
#### <a name="to-create-and-open-an-outbound-channel"></a>Pour créer et ouvrir un canal sortant  
  
1.  Créer et initialiser une instance de **ChannelFactory** pour la forme du canal souhaitées à l’aide d’un point de terminaison et une liaison. Le point de terminaison spécifie un URI de connexion SQL Server et de la liaison est une instance de **sqlBinding**.  
  
2.  Fournir des informations d’identification de SQL Server pour la fabrication de canal à l’aide de la **informations d’identification** propriété.  
  
3.  Ouvrez la fabrication de canal.  
  
4.  Obtention d’une instance du canal en appelant le **CreateChannel** méthode sur la fabrication de canal.  
  
5.  Ouvrir le canal.  
  
 Vous pouvez spécifier l’adresse de liaison et le point de terminaison dans votre code ou de configuration.  
  
### <a name="specifying-the-binding-and-endpoint-address-in-code"></a>Spécification de la liaison et l’adresse de point de terminaison dans le Code  
 L’exemple de code suivant montre comment créer un **IRequestChannel** en spécifiant l’adresse de liaison et le point de terminaison dans le code. Le code pour créer un **IOutputChannel** est identique, sauf que vous devez spécifier un **IOutputChannel** de l’interface pour le **ChannelFactory** et type de canal.  
  
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
  
### <a name="specifying-the-binding-and-endpoint-address-in-configuration"></a>Spécification de la liaison et l’adresse de point de terminaison dans la Configuration  
 L’exemple de code suivant montre comment créer une fabrique de canaux à partir d’un point de terminaison de client spécifié dans la configuration.  
  
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
  
#### <a name="the-configuration-settings"></a>Les paramètres de Configuration  
 Le code suivant illustre les paramètres de configuration utilisés pour l’exemple précédent. Le contrat pour le point de terminaison client doit être « System.ServiceModel.Channels.IRequestChannel » ou « System.ServiceModel.Channels.IOutputChannel » en fonction du type de la forme de canal que vous souhaitez créer.  
  
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
  
## <a name="creating-inbound-service-channels"></a>Créer des canaux entrants (Service)  
 Vous configurez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour interroger les tables de base de données SQL Server et les vues en définissant les propriétés de liaison sur une instance de **sqlBinding**. Vous utilisez ensuite cette liaison pour générer un écouteur de canal à partir de laquelle vous pouvez obtenir un **IInputChannel** canal pour recevoir le **d’interrogation**, **TypedPolling**, ou  **Notification** opération à partir de l’adaptateur.  
  
#### <a name="to-create-and-open-an-iinputchannel-to-receive-inbound-operations"></a>Pour créer et ouvrir un IInputChannel pour recevoir les opérations entrantes  
  
1.  Créez une instance de **SQLBinding**.  
  
2.  Définissez les propriétés de liaison requises pour l’opération entrante. Par exemple, pour un **d’interrogation** opération, au minimum, vous devez définir le **InboundOperationType**, **PolledDataAvailableStatement**, et  **PollingStatement** pour configurer les propriétés de liaison le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour interroger la base de données SQL Server.  
  
3.  Créer un écouteur de canal en appelant **BuildChannelListener\<IInputChannel >** méthode sur le **SQLBinding**. Vous spécifiez l’URI de connexion SQL Server comme l’un des paramètres pour cette méthode.  
  
4.  Ouvrez le port d’écoute.  
  
5.  Obtenir un **IInputChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur.  
  
6.  Ouvrir le canal.  
  
 Le code suivant montre comment créer un écouteur de canal et obtenir un **IInputChannel** pour recevoir des messages de modification de données à partir de l’adaptateur.  
  
> [!IMPORTANT]
>  Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend uniquement en charge unidirectionnel de réception. Par conséquent, vous devez utiliser **IInputChannel** pour recevoir des messages pour les opérations entrantes à partir de SQL Server.  
  
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
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)
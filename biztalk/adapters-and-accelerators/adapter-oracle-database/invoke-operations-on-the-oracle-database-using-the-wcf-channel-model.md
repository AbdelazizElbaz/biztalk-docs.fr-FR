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
# <a name="invoke-operations-on-the-oracle-database-using-the-wcf-channel-model"></a>Appeler des opérations sur la base de données Oracle à l’aide du modèle de canal WCF
Vous pouvez appeler des opérations sur le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] en utilisant un **IRequestChannel** ou **IOutputChannel** forme pour envoyer des messages à l’adaptateur. Le modèle de base consiste à créer une fabrication de canal pour la forme de canal requis à l’aide d’une liaison (**OracleDBBinding**) et un point de terminaison créé à partir d’un URI de connexion. Vous créez ensuite un **Message** instance qui représente un message SOAP qui est conforme au schéma de message pour votre opération de cible. Vous pouvez alors envoyer ce **Message** à la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à l’aide d’un canal créé à partir de la fabrication de canal. Si vous utilisez un **IRequestChannel**, vous recevez une réponse. S’il existe un problème d’exécution de l’opération sur la base de données Oracle, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] lève une **Microsoft.ServiceModel.Channels.Common.TargetSystemException**.  
  
 Pour une vue d’ensemble de la manière d’envoyer des opérations à l’aide un **IRequestChannel** dans WCF, consultez « Programmation au niveau du canal de Client » à [http://go.microsoft.com/fwlink/?LinkId=106081](http://go.microsoft.com/fwlink/?LinkId=106081).  
  
 Les sections de cette rubrique fournissent des informations pour vous aider à appeler des opérations sur les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à l’aide du modèle de canal WCF.  
  
## <a name="creating-and-consuming-messages-for-outbound-operations"></a>Création et utilisation des Messages pour les opérations sortantes  
 Pour appeler une opération sur le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], vous envoyez le message de demande pour l’opération de cible à l’aide un **IRequestChannel** ou un **IOutputChannel**. Si vous utilisez un **IRequestChannel** l’adaptateur retourne les résultats de l’opération dans le message de réponse.  
  
 Pour plus d’informations sur la demande et les schémas de message de réponse et les actions de message pour chaque opération, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).  
  
 Comment créer le message de demande et comment consommer le message de réponse détermine si le nœud de diffusion en continu ou diffusion en continu de valeur de nœud est effectuée par l’adaptateur. Ce paramètre détermine ensuite si la diffusion en continu de bout en bout des données LOB est effectuée pour les opérations prises en charge.  
  
### <a name="creating-the-request-message"></a>Création d’un message de demande  
 Vous pouvez créer le message de demande de deux manières :  
  
-   Pour créer un message qui peut être utilisé pour la valeur du nœud de diffusion en continu vous devez passer le corps du message dans une **XmlBodyWriter** qui implémente la diffusion en continu de la valeur du nœud.  
  
-   Pour créer un message qui peut être utilisé pour le nœud de diffusion en continu vous pouvez passer le corps du message dans une **XmlReader**.  
  
 Vous utilisez généralement pour prendre en charge la diffusion en continu de bout en bout de Oracle LOB des données dans le message de demande de diffusion en continu de valeur de nœud. La seule opération qui prend en charge cette fonctionnalité est UpdateLOB.  
  
### <a name="consuming-the-response-message"></a>Le message de réponse  
 Vous pouvez utiliser le message de réponse de deux manières :  
  
-   Pour consommer le message à l’aide de la valeur du nœud de diffusion en continu vous devez appeler la **WriteBodyContents** méthode sur la réponse de message et lui passer une **XmlDictionaryWriter** qui implémente la diffusion en continu de la valeur du nœud.  
  
-   Pour consommer le message à l’aide du nœud de diffusion en continu, vous pouvez appeler **GetReaderAtBodyContents** sur le message de réponse pour obtenir un **XmlReader**.  
  
 Vous utilisez généralement la valeur du nœud de diffusion en continu pour prendre en charge la diffusion en continu de bout en bout de Oracle LOB des données dans le message de réponse. Il existe de nombreuses opérations qui prennent en charge cette fonctionnalité.  
  
### <a name="lob-data-and-message-streaming-support"></a>Données LOB et prise en charge de la diffusion en continu de Message  
 Pour plus d’informations sur la façon dont [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge la diffusion en continu des données LOB, consultez [diffusion en continu des types de données dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).  
  
 Pour plus d’informations sur l’implémentation de diffusion en continu dans votre code pour prendre en charge la diffusion en continu de bout en bout des données LOB de valeur de nœud, consultez [de diffusion en continu Oracle de base de données LOB données Types à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).  
  
## <a name="transaction-support-on-outbound-operations-in-the-wcf-channel-model"></a>Prise en charge de la transaction sur les opérations de sortie dans le modèle de canal WCF.  
 L’adaptateur s’exécute chaque opération que vous appelez à l’intérieur d’une transaction dédiée sur la base de données Oracle. Vous pouvez contrôler le niveau d’isolation de ces transactions en définissant le **TransactionIsolationLevel** propriété de liaison.  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 L’exemple dans cette rubrique utilise le SCOTT. Table ACCOUNTACTIVITY. Un script pour générer ces artefacts est fourni avec les exemples du Kit de développement logiciel. Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).  
  
## <a name="how-do-i-invoke-an-operation-by-using-a-channel"></a>Comment pour appeler une opération à l’aide d’un canal ?  
 Pour appeler une opération en utilisant un **IRequestChannel**, procédez comme suit.  
  
#### <a name="how-to-invoke-an-operation-by-using-an-instance-of-irequestchannel"></a>L’appel d’une opération à l’aide d’une instance de IRequestChannel  
  
1.  Générer une fabrique de canal (**ChannelFactory\<IRequestChannel >**). Pour ce faire, vous devez spécifier une liaison (**OracleDBBinding**) et une adresse de point de terminaison. Vous pouvez spécifier l’adresse de liaison et le point de terminaison soit impérativement dans votre code ou de façon déclarative dans la configuration. Pour plus d’informations sur la façon de spécifier la liaison et l’adresse de point de terminaison dans la configuration, consultez [créer un canal à l’aide de la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md).  
  
    ```  
    // Create a binding  
    OracleDBBinding binding = new OracleDBBinding();  
    // Create an endpoint address by using the connection URI  
    EndpointAddress address = new EndpointAddress("oracledb://ADAPTER");  
    // Create the channel factory  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    ```  
  
2.  Définir des informations d’identification de mot de passe pour la fabrication de canal de l’utilisateur à l’aide de la **ClientCredentials** propriété.  
  
    ```  
    factory.Credentials.UserName.UserName = "SCOTT";  
    factory.Credentials.UserName.Password = "TIGER";  
    ```  
  
3.  Ouvrez la fabrication de canal.  
  
    ```  
    factory.Open();  
    ```  
  
4.  Obtenir un canal à partir de la fabrique et l’ouvrir.  
  
    ```  
    IRequestChannel channel = factory.CreateChannel();  
    channel.Open();  
    ```  
  
5.  Créer un **Message** instance pour l’opération de la cible. Assurez-vous que l’action du message pour l’opération de la cible est spécifiée. Dans cet exemple, le corps du message est passé en créant un **XmlReader** sur un fichier. L’opération de la cible est une opération Select sur la table SCOTT/EMP.  
  
    ```  
    XmlReader readerIn = XmlReader.Create("SelectAllActivity.xml");  
    Message messageIn = Message.CreateMessage(MessageVersion.Default,  
        "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select",  
        readerIn);  
    ```  
  
6.  Appeler le **demande** méthode sur le canal pour envoyer le message à la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] et recevoir la réponse. Si la base de données Oracle rencontre une exception, l’adaptateur génère un **TargetSystemException**. (Les autres exceptions sont possibles pour les exceptions non Oracle). Vous pouvez obtenir une description de l’erreur Oracle à partir de la **InnerException.Message** propriété de la **TargetSystemException**.  
  
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
  
7.  Traiter la réponse. Dans cet exemple, **GetReaderAtBodyContents** est appelée sur le message de réponse pour obtenir le corps du message.  
  
    ```  
    XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
    ```  
  
8.  Lorsque vous avez terminé le traitement du message de réponse, fermez le lecteur et le message.  
  
    ```  
    readerOut.Close();  
    messageOut.Close();  
    ```  
  
9. Lorsque vous avez terminé à l’aide du canal et la fabrication de canal, de les fermer. Fermeture de la fabrique se fermera tous les canaux qui ont été créés avec lui.  
  
    ```  
    channel.Close()  
    factory.Close();  
  
    ```  
  
 Vous suivez les mêmes étapes pour envoyer un message à l’aide de la **IOutputChannel** mettre en forme, à l’exception :  
  
-   Vous créez un **ChannelFactory\<IOutputChannel >** dans l’étape 1.  
  
-   Vous appelez le **envoyer** méthode sur le canal à l’étape 6. `channel.Send(messageIn);`.  
  
-   Aucun message de réponse retourné pour une **IOutputChannel**.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment appeler une opération de sélection en utilisant un **IRequestChannel** canal. Le message de réponse Select est consommé en utilisant un **XmlReader** et le nombre d’enregistrements renvoyés est écrite dans la console.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications de base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)
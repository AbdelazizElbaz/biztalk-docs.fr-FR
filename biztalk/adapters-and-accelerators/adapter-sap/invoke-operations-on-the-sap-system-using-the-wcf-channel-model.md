---
title: "Appeler des opérations sur le système SAP à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF channel model, supporting BAPI transactions
- WCF channel model, invoking operations on the SAP system
ms.assetid: 80ed85ff-360d-4b7f-a119-cd2a99c21cf4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1030e0a743a9b06d856bc593198f4afebc1ffa38
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-operations-on-the-sap-system-using-the-wcf-channel-model"></a>Appeler des opérations sur le système SAP à l’aide du modèle de canal WCF
Appeler des opérations sur le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en utilisant un **IRequestChannel** ou **IOutputChannel** forme pour envoyer des messages à la carte de canal. Le modèle de base consiste à créer une fabrication de canal pour la forme de canal requis à l’aide d’une liaison (**SAPBinding**) et un point de terminaison créé à partir d’un URI de connexion. Vous créez ensuite un **Message** instance qui représente un message SOAP qui est conforme au schéma de message pour votre opération de cible. Vous pouvez alors envoyer ce **Message** à la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] à l’aide d’un canal créé à partir de la fabrication de canal. Si vous utilisez un **IRequestChannel**, vous recevez une réponse. S’il existe un problème d’exécution de l’opération sur le système SAP, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] lève une **Microsoft.ServiceModel.Channels.Common.TargetSystemException**.  
  
 Pour une vue d’ensemble de la manière d’envoyer des opérations à l’aide un **IRequestChannel** dans WCF, consultez [de programmation au niveau du canal de Client](https://msdn.microsoft.com/library/ms788970.aspx).  
  
 Les sections de cette rubrique fournissent des informations pour vous aider à appeler des opérations sur les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] à l’aide du modèle de canal WCF.  
  
## <a name="supporting-bapi-transactions-in-the-wcf-channel-model"></a>Prise en charge des Transactions BAPI dans le modèle de canal WCF  
 Toutes les interfaces BAPI qui sont appelées à l’aide de la même connexion SAP font partie de la même logique unité de travail (LUW)--transaction ou--sur le système SAP. Chaque canal WCF représente une connexion unique au système SAP. Pour prendre en charge les transactions BAPI à l’aide de WCF de canal modèle :  
  
-   Assurez-vous que chaque BAPI dans un LUW (transaction) est envoyé via le même canal. Cela inclut les opérations BAPI_TRANSACTION_ROLLBACK ou la validation de BAPI_TRANSACTION.  
  
-   Assurez-vous que vous fermez le message de réponse reçu pour un BAPI avant d’appeler BAPI suivant sur le canal. (Vous devez le faire pour chaque opération ; mais il est particulièrement important pour les interfaces BAPI.)  
  
 Pour plus d’informations sur les transactions BAPI, consultez [opérations sur les BAPI dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).  
  
## <a name="streaming-flat-file-idocs-to-the-sap-adapter"></a>Diffusion en continu IDOC de fichier plat à l’adaptateur SAP  
 L’opération SendIdoc vous permet d’envoyer un fichier plat (string) IDOC à l’adaptateur. Les données IDOC sont représentées sous forme de chaîne sous un nœud unique dans cette opération. Pour cette raison, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge la diffusion en continu sur le message de demande de valeur de nœud. Pour effectuer la valeur du nœud de diffusion en continu, vous devez créer le message de demande pour l’opération SendIdoc en utilisant un **System.ServiceModel.Channels.BodyWriter** qui est capable de diffusion en continu les données IDOC. Pour plus d’informations sur la procédure à suivre, consultez [de diffusion en continu de fichier plat IDOC dans SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md).  
  
## <a name="how-do-i-invoke-an-operation-by-using-a-channel"></a>Comment pour appeler une opération à l’aide d’un canal ?  
 Pour appeler une opération en utilisant un **IRequestChannel**, procédez comme suit.  
  
#### <a name="how-to-invoke-an-operation-by-using-an-instance-of-irequestchannel"></a>L’appel d’une opération à l’aide d’une instance de IRequestChannel  
  
1.  Générer une fabrique de canal (**ChannelFactory\<IRequestChannel\>**). Pour ce faire, vous devez spécifier une liaison (**SAPBinding**) et une adresse de point de terminaison. Vous pouvez spécifier l’adresse de liaison et le point de terminaison soit impérativement dans votre code ou de façon déclarative dans la configuration. Vous devez définir des liaisons de propriétés nécessaires pour les opérations que vous allez envoyer avant d’ouvrir la fabrique. Pour plus d’informations sur la façon de spécifier la liaison et l’adresse de point de terminaison dans la configuration, consultez [créer un canal à l’aide de SAP](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md).  
  
    ```  
    // Create a binding  
    SAPBinding binding = new SAPBinding();  
    // Create an endpoint address by using the connection URI  
    EndpointAddress endpointAddress = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
    // Create the channel factory  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    ```  
  
2.  Définir des informations d’identification de mot de passe pour la fabrication de canal de l’utilisateur à l’aide de la **ClientCredentials** propriété.  
  
    ```  
    factory.Credentials.UserName.UserName = "YourUserName";  
    factory.Credentials.UserName.Password = "YourPassword";  
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
  
5.  Créer un **Message** instance pour l’opération de la cible. Assurez-vous que l’action du message pour l’opération de la cible est spécifiée. Dans cet exemple, le corps du message est passé en créant un **XmlReader** sur une chaîne. L’opération cible appelle la RFC SD_RFC_CUSTOMER_GET sur un système SAP.  
  
    ```  
    string inputXml = "\<SD_RFC_CUSTOMER_GET xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> <KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>";  
  
    //create an XML reader from the input XML  
    XmlReader reader = XmlReader.Create(new MemoryStream(Encoding.Default.GetBytes(inputXml)));  
  
    //create a WCF message from our XML reader  
    Message inputMessge = Message.CreateMessage(MessageVersion.Soap11, "http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET", reader);  
    ```  
  
6.  Appeler le **demande** méthode sur le canal pour envoyer le message à la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et recevoir la réponse. Si le système SAP rencontre une exception, l’adaptateur génère un **TargetSystemException**. (Les autres exceptions sont possibles pour les exceptions non SAP). Vous pouvez obtenir une description de l’erreur SAP à partir de la **InnerException.Message** propriété de la **TargetSystemException**.  
  
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
  
10.  
  
 Vous suivez les mêmes étapes pour envoyer un message à l’aide de la **IOutputChannel** mettre en forme, à l’exception :  
  
-   Vous créez un **ChannelFactory\<IOutputChannel\>**  à l’étape 1.  
  
-   Vous appelez le **envoyer** méthode sur le canal à l’étape 6. `channel.Send(messageIn);`.  
  
-   Aucun message de réponse retourné pour une **IOutputChannel**.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment appeler une commande RFC à l’aide un **IRequestChannel** canal. Cet exemple appelle la RFC SD_RFC_CUSTOMER_GET pour obtenir une liste de clients dont le nom commence par « AB ». Le message de réponse est consommé en utilisant un **XmlReader** et le numéro de client et le nom de chaque client retourné est écrit dans la console.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.Xml;  
using System.IO;  
  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel.Channels;  
  
namespace SapRfcClientCM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            //create a binding  
            SAPBinding binding = new SAPBinding();  
  
            //set up an endpoint address.  
            EndpointAddress endpointAddress = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
            //create a channel factory, capable of sending a request to SAP and receiving a reply (IRequestChannel)  
            ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, endpointAddress);  
  
            // add credentials  
            factory.Credentials.UserName.UserName = "YourUserName";  
            factory.Credentials.UserName.Password = "YourPassword";  
  
            //open the factory  
            factory.Open();  
  
            //obtain a channel from the factory by specifying the address you want to connect to  
            IRequestChannel channel = factory.CreateChannel();  
  
            //open the channel  
            channel.Open();  
  
            //create an XML message to send to the SAP system  
            //We are invoking the SD_RFC_CUSTOMER_GET RFC.  
            //The XML below specifies that we want to search for customers with names starting with "AB"  
            string inputXml = "<SD_RFC_CUSTOMER_GET xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> <KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>";  
  
            //create an XML reader from the input XML  
            XmlReader readerOut = XmlReader.Create(new MemoryStream(Encoding.Default.GetBytes(inputXml)));  
  
            //create a WCF message from the XML reader  
            Message messageOut = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET", readerOut);  
  
            //send the message to SAP and obtain a reply  
            Message messageIn = channel.Request(messageOut);  
  
            // Write the KUNNR and NAME1 fields for each returned record to the Console  
            Console.WriteLine("Results of SD_RFC_CUSTOMER_GET");  
            Console.WriteLine("KUNNR\t\tNAME1");  
  
            XmlReader readerIn = messageIn.GetReaderAtBodyContents();  
  
            while (readerIn.Read())  
            {  
                if (readerIn.IsStartElement())  
                {  
                    switch (readerIn.Name)  
                    {  
                        case "RFCCUST":  
                            Console.Write("\n");  
                            break;  
  
                        case "KUNNR":  
                            readerIn.Read();  
                            Console.Write(readerIn.ReadString() + "\t");  
                            break;  
  
                        case "NAME1":  
                            readerIn.Read();  
                            Console.Write(readerIn.ReadString() + "\t");  
                            break;  
  
                        default:  
                            break;  
                    }  
                }  
            }  
  
            // return the cursor  
            Console.WriteLine();  
  
            // Close the input reader  
            readerIn.Close();  
  
            // Close the input message. You should do this for every message you   
            // send on the channel  
            messageIn.Close();  
  
            // close the channel when you are done using it.  
            channel.Close();  
  
            //close the factory  
            //note: closing the factory will close all of its channels.  
            factory.Close();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications en utilisant le modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)
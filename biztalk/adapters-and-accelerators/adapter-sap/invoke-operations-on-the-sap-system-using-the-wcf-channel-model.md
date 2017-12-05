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
# <a name="invoke-operations-on-the-sap-system-using-the-wcf-channel-model"></a><span data-ttu-id="12bd2-102">Appeler des opérations sur le système SAP à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="12bd2-102">Invoke Operations on the SAP System Using the WCF Channel Model</span></span>
<span data-ttu-id="12bd2-103">Appeler des opérations sur le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en utilisant un **IRequestChannel** ou **IOutputChannel** forme pour envoyer des messages à la carte de canal.</span><span class="sxs-lookup"><span data-stu-id="12bd2-103">You invoke operations on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by using an **IRequestChannel** or **IOutputChannel** channel shape to send messages to the adapter.</span></span> <span data-ttu-id="12bd2-104">Le modèle de base consiste à créer une fabrication de canal pour la forme de canal requis à l’aide d’une liaison (**SAPBinding**) et un point de terminaison créé à partir d’un URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="12bd2-104">The basic pattern is to create a channel factory for the required channel shape by using a binding (**SAPBinding**) and an endpoint created from a connection URI.</span></span> <span data-ttu-id="12bd2-105">Vous créez ensuite un **Message** instance qui représente un message SOAP qui est conforme au schéma de message pour votre opération de cible.</span><span class="sxs-lookup"><span data-stu-id="12bd2-105">You then create a **Message** instance that represents a SOAP message that conforms to the message schema for your target operation.</span></span> <span data-ttu-id="12bd2-106">Vous pouvez alors envoyer ce **Message** à la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] à l’aide d’un canal créé à partir de la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="12bd2-106">You can then send this **Message** to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by using a channel created from the channel factory.</span></span> <span data-ttu-id="12bd2-107">Si vous utilisez un **IRequestChannel**, vous recevez une réponse.</span><span class="sxs-lookup"><span data-stu-id="12bd2-107">If you are using an **IRequestChannel**, you receive a response.</span></span> <span data-ttu-id="12bd2-108">S’il existe un problème d’exécution de l’opération sur le système SAP, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] lève une **Microsoft.ServiceModel.Channels.Common.TargetSystemException**.</span><span class="sxs-lookup"><span data-stu-id="12bd2-108">If there is a problem executing the operation on the SAP system, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] throws a **Microsoft.ServiceModel.Channels.Common.TargetSystemException**.</span></span>  
  
 <span data-ttu-id="12bd2-109">Pour une vue d’ensemble de la manière d’envoyer des opérations à l’aide un **IRequestChannel** dans WCF, consultez [de programmation au niveau du canal de Client](https://msdn.microsoft.com/library/ms788970.aspx).</span><span class="sxs-lookup"><span data-stu-id="12bd2-109">For an overview of how to send operations using an **IRequestChannel** in WCF, see [Client Channel-Level Programming](https://msdn.microsoft.com/library/ms788970.aspx).</span></span>  
  
 <span data-ttu-id="12bd2-110">Les sections de cette rubrique fournissent des informations pour vous aider à appeler des opérations sur les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] à l’aide du modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="12bd2-110">The sections in this topic provide information to help you invoke operations on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] using the WCF channel model.</span></span>  
  
## <a name="supporting-bapi-transactions-in-the-wcf-channel-model"></a><span data-ttu-id="12bd2-111">Prise en charge des Transactions BAPI dans le modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="12bd2-111">Supporting BAPI Transactions in the WCF Channel Model</span></span>  
 <span data-ttu-id="12bd2-112">Toutes les interfaces BAPI qui sont appelées à l’aide de la même connexion SAP font partie de la même logique unité de travail (LUW)--transaction ou--sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="12bd2-112">All BAPIs that are invoked using the same SAP connection are part of the same Logical Unit of Work (LUW) -- or transaction -- on the SAP system.</span></span> <span data-ttu-id="12bd2-113">Chaque canal WCF représente une connexion unique au système SAP.</span><span class="sxs-lookup"><span data-stu-id="12bd2-113">Each WCF channel represents a unique connection to the SAP system.</span></span> <span data-ttu-id="12bd2-114">Pour prendre en charge les transactions BAPI à l’aide de WCF de canal modèle :</span><span class="sxs-lookup"><span data-stu-id="12bd2-114">To support BAPI transactions using the WCF channel model:</span></span>  
  
-   <span data-ttu-id="12bd2-115">Assurez-vous que chaque BAPI dans un LUW (transaction) est envoyé via le même canal.</span><span class="sxs-lookup"><span data-stu-id="12bd2-115">Ensure that every BAPI in an LUW (transaction) is sent over the same channel.</span></span> <span data-ttu-id="12bd2-116">Cela inclut les opérations BAPI_TRANSACTION_ROLLBACK ou la validation de BAPI_TRANSACTION.</span><span class="sxs-lookup"><span data-stu-id="12bd2-116">This includes the BAPI_TRANSACTION COMMIT or the BAPI_TRANSACTION_ROLLBACK operations.</span></span>  
  
-   <span data-ttu-id="12bd2-117">Assurez-vous que vous fermez le message de réponse reçu pour un BAPI avant d’appeler BAPI suivant sur le canal.</span><span class="sxs-lookup"><span data-stu-id="12bd2-117">Ensure that you close any response message received for a BAPI before you invoke the next BAPI on the channel.</span></span> <span data-ttu-id="12bd2-118">(Vous devez le faire pour chaque opération ; mais il est particulièrement important pour les interfaces BAPI.)</span><span class="sxs-lookup"><span data-stu-id="12bd2-118">(You should do this for every operation; but it is especially important for BAPIs.)</span></span>  
  
 <span data-ttu-id="12bd2-119">Pour plus d’informations sur les transactions BAPI, consultez [opérations sur les BAPI dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="12bd2-119">For more information about BAPI transactions, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span></span>  
  
## <a name="streaming-flat-file-idocs-to-the-sap-adapter"></a><span data-ttu-id="12bd2-120">Diffusion en continu IDOC de fichier plat à l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="12bd2-120">Streaming Flat File IDOCs to the SAP Adapter</span></span>  
 <span data-ttu-id="12bd2-121">L’opération SendIdoc vous permet d’envoyer un fichier plat (string) IDOC à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="12bd2-121">You use the SendIdoc operation to send a flat file (string) IDOC to the adapter.</span></span> <span data-ttu-id="12bd2-122">Les données IDOC sont représentées sous forme de chaîne sous un nœud unique dans cette opération.</span><span class="sxs-lookup"><span data-stu-id="12bd2-122">The IDOC data is represented as a string under a single node in this operation.</span></span> <span data-ttu-id="12bd2-123">Pour cette raison, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge la diffusion en continu sur le message de demande de valeur de nœud.</span><span class="sxs-lookup"><span data-stu-id="12bd2-123">For this reason, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports node-value streaming on the request message.</span></span> <span data-ttu-id="12bd2-124">Pour effectuer la valeur du nœud de diffusion en continu, vous devez créer le message de demande pour l’opération SendIdoc en utilisant un **System.ServiceModel.Channels.BodyWriter** qui est capable de diffusion en continu les données IDOC.</span><span class="sxs-lookup"><span data-stu-id="12bd2-124">To perform node-value streaming, you must create the request message for the SendIdoc operation by using a **System.ServiceModel.Channels.BodyWriter** that is capable of streaming the IDOC data.</span></span> <span data-ttu-id="12bd2-125">Pour plus d’informations sur la procédure à suivre, consultez [de diffusion en continu de fichier plat IDOC dans SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md).</span><span class="sxs-lookup"><span data-stu-id="12bd2-125">For information about how to do this, see [Streaming Flat-File IDOCs in SAP using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="how-do-i-invoke-an-operation-by-using-a-channel"></a><span data-ttu-id="12bd2-126">Comment pour appeler une opération à l’aide d’un canal ?</span><span class="sxs-lookup"><span data-stu-id="12bd2-126">How Do I Invoke an Operation by Using a Channel?</span></span>  
 <span data-ttu-id="12bd2-127">Pour appeler une opération en utilisant un **IRequestChannel**, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="12bd2-127">To invoke an operation by using an **IRequestChannel**, perform the following steps.</span></span>  
  
#### <a name="how-to-invoke-an-operation-by-using-an-instance-of-irequestchannel"></a><span data-ttu-id="12bd2-128">L’appel d’une opération à l’aide d’une instance de IRequestChannel</span><span class="sxs-lookup"><span data-stu-id="12bd2-128">How to invoke an operation by using an instance of IRequestChannel</span></span>  
  
1.  <span data-ttu-id="12bd2-129">Générer une fabrique de canal (**ChannelFactory\<IRequestChannel\>**).</span><span class="sxs-lookup"><span data-stu-id="12bd2-129">Build a channel factory (**ChannelFactory\<IRequestChannel\>**).</span></span> <span data-ttu-id="12bd2-130">Pour ce faire, vous devez spécifier une liaison (**SAPBinding**) et une adresse de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="12bd2-130">To do this, you must specify a binding (**SAPBinding**) and an endpoint address.</span></span> <span data-ttu-id="12bd2-131">Vous pouvez spécifier l’adresse de liaison et le point de terminaison soit impérativement dans votre code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="12bd2-131">You can specify the binding and endpoint address either imperatively in your code or declaratively in configuration.</span></span> <span data-ttu-id="12bd2-132">Vous devez définir des liaisons de propriétés nécessaires pour les opérations que vous allez envoyer avant d’ouvrir la fabrique.</span><span class="sxs-lookup"><span data-stu-id="12bd2-132">You should set any binding properties required for the operations that you will send before you open the factory.</span></span> <span data-ttu-id="12bd2-133">Pour plus d’informations sur la façon de spécifier la liaison et l’adresse de point de terminaison dans la configuration, consultez [créer un canal à l’aide de SAP](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md).</span><span class="sxs-lookup"><span data-stu-id="12bd2-133">For more information about how to specify the binding and endpoint address in configuration, see [Create a channel using SAP](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md).</span></span>  
  
    ```  
    // Create a binding  
    SAPBinding binding = new SAPBinding();  
    // Create an endpoint address by using the connection URI  
    EndpointAddress endpointAddress = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
    // Create the channel factory  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    ```  
  
2.  <span data-ttu-id="12bd2-134">Définir des informations d’identification de mot de passe pour la fabrication de canal de l’utilisateur à l’aide de la **ClientCredentials** propriété.</span><span class="sxs-lookup"><span data-stu-id="12bd2-134">Set the user name password credentials for the channel factory by using the **ClientCredentials** property.</span></span>  
  
    ```  
    factory.Credentials.UserName.UserName = "YourUserName";  
    factory.Credentials.UserName.Password = "YourPassword";  
    ```  
  
3.  <span data-ttu-id="12bd2-135">Ouvrez la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="12bd2-135">Open the channel factory.</span></span>  
  
    ```  
    factory.Open();  
    ```  
  
4.  <span data-ttu-id="12bd2-136">Obtenir un canal à partir de la fabrique et l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="12bd2-136">Get a channel from the factory and open it.</span></span>  
  
    ```  
    IRequestChannel channel = factory.CreateChannel();  
    channel.Open();  
    ```  
  
5.  <span data-ttu-id="12bd2-137">Créer un **Message** instance pour l’opération de la cible.</span><span class="sxs-lookup"><span data-stu-id="12bd2-137">Create a **Message** instance for the target operation.</span></span> <span data-ttu-id="12bd2-138">Assurez-vous que l’action du message pour l’opération de la cible est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="12bd2-138">Be sure that the message action for the target operation is specified.</span></span> <span data-ttu-id="12bd2-139">Dans cet exemple, le corps du message est passé en créant un **XmlReader** sur une chaîne.</span><span class="sxs-lookup"><span data-stu-id="12bd2-139">In this example, the message body is passed by creating an **XmlReader** over a string.</span></span> <span data-ttu-id="12bd2-140">L’opération cible appelle la RFC SD_RFC_CUSTOMER_GET sur un système SAP.</span><span class="sxs-lookup"><span data-stu-id="12bd2-140">The target operation invokes the SD_RFC_CUSTOMER_GET RFC on an SAP system.</span></span>  
  
    ```  
    string inputXml = "\<SD_RFC_CUSTOMER_GET xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> <KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>";  
  
    //create an XML reader from the input XML  
    XmlReader reader = XmlReader.Create(new MemoryStream(Encoding.Default.GetBytes(inputXml)));  
  
    //create a WCF message from our XML reader  
    Message inputMessge = Message.CreateMessage(MessageVersion.Soap11, "http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET", reader);  
    ```  
  
6.  <span data-ttu-id="12bd2-141">Appeler le **demande** méthode sur le canal pour envoyer le message à la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et recevoir la réponse.</span><span class="sxs-lookup"><span data-stu-id="12bd2-141">Invoke the **Request** method on the channel to send the message to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] and receive the reply.</span></span> <span data-ttu-id="12bd2-142">Si le système SAP rencontre une exception, l’adaptateur génère un **TargetSystemException**.</span><span class="sxs-lookup"><span data-stu-id="12bd2-142">If the SAP system encounters an exception, the adapter throws a **TargetSystemException**.</span></span> <span data-ttu-id="12bd2-143">(Les autres exceptions sont possibles pour les exceptions non SAP). Vous pouvez obtenir une description de l’erreur SAP à partir de la **InnerException.Message** propriété de la **TargetSystemException**.</span><span class="sxs-lookup"><span data-stu-id="12bd2-143">(Other exceptions are possible for non SAP exceptions.) You can get a description of the SAP error from the **InnerException.Message** property of the **TargetSystemException**.</span></span>  
  
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
  
7.  <span data-ttu-id="12bd2-144">Traiter la réponse.</span><span class="sxs-lookup"><span data-stu-id="12bd2-144">Process the response.</span></span> <span data-ttu-id="12bd2-145">Dans cet exemple, **GetReaderAtBodyContents** est appelée sur le message de réponse pour obtenir le corps du message.</span><span class="sxs-lookup"><span data-stu-id="12bd2-145">In this example, **GetReaderAtBodyContents** is called on the response message to get the message body.</span></span>  
  
    ```  
    XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
    ```  
  
8.  <span data-ttu-id="12bd2-146">Lorsque vous avez terminé le traitement du message de réponse, fermez le lecteur et le message.</span><span class="sxs-lookup"><span data-stu-id="12bd2-146">When you are done processing the response message, close the reader and the message.</span></span>  
  
    ```  
    readerOut.Close();  
    messageOut.Close();  
    ```  
  
9. <span data-ttu-id="12bd2-147">Lorsque vous avez terminé à l’aide du canal et la fabrication de canal, de les fermer.</span><span class="sxs-lookup"><span data-stu-id="12bd2-147">When you are done using the channel and the channel factory, close them.</span></span> <span data-ttu-id="12bd2-148">Fermeture de la fabrique se fermera tous les canaux qui ont été créés avec lui.</span><span class="sxs-lookup"><span data-stu-id="12bd2-148">Closing the factory will close all channels that were created with it.</span></span>  
  
    ```  
    channel.Close()  
    factory.Close();  
    ```  
  
10.  
  
 <span data-ttu-id="12bd2-149">Vous suivez les mêmes étapes pour envoyer un message à l’aide de la **IOutputChannel** mettre en forme, à l’exception :</span><span class="sxs-lookup"><span data-stu-id="12bd2-149">You follow the same steps to send a message using the **IOutputChannel** shape except:</span></span>  
  
-   <span data-ttu-id="12bd2-150">Vous créez un **ChannelFactory\<IOutputChannel\>**  à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="12bd2-150">You create a **ChannelFactory\<IOutputChannel\>** in step 1.</span></span>  
  
-   <span data-ttu-id="12bd2-151">Vous appelez le **envoyer** méthode sur le canal à l’étape 6.</span><span class="sxs-lookup"><span data-stu-id="12bd2-151">You call the **Send** method on the channel in step 6.</span></span> <span data-ttu-id="12bd2-152">`channel.Send(messageIn);`.</span><span class="sxs-lookup"><span data-stu-id="12bd2-152">`channel.Send(messageIn);`.</span></span>  
  
-   <span data-ttu-id="12bd2-153">Aucun message de réponse retourné pour une **IOutputChannel**.</span><span class="sxs-lookup"><span data-stu-id="12bd2-153">There is no response message returned for an **IOutputChannel**.</span></span>  
  
### <a name="example"></a><span data-ttu-id="12bd2-154">Exemple</span><span class="sxs-lookup"><span data-stu-id="12bd2-154">Example</span></span>  
 <span data-ttu-id="12bd2-155">L’exemple suivant montre comment appeler une commande RFC à l’aide un **IRequestChannel** canal.</span><span class="sxs-lookup"><span data-stu-id="12bd2-155">The following example shows how to invoke an RFC by using an **IRequestChannel** channel.</span></span> <span data-ttu-id="12bd2-156">Cet exemple appelle la RFC SD_RFC_CUSTOMER_GET pour obtenir une liste de clients dont le nom commence par « AB ».</span><span class="sxs-lookup"><span data-stu-id="12bd2-156">This example invokes the SD_RFC_CUSTOMER_GET RFC to get a list of customers whose names start with "AB".</span></span> <span data-ttu-id="12bd2-157">Le message de réponse est consommé en utilisant un **XmlReader** et le numéro de client et le nom de chaque client retourné est écrit dans la console.</span><span class="sxs-lookup"><span data-stu-id="12bd2-157">The response message is consumed by using an **XmlReader** and the customer number and name of each customer returned is written to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12bd2-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12bd2-158">See Also</span></span>  
[<span data-ttu-id="12bd2-159">Développer des applications en utilisant le modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="12bd2-159">Develop applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)
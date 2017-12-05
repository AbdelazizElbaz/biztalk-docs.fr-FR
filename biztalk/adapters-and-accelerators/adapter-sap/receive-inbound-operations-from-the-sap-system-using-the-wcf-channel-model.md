---
title: "Opérations entrantes de réception à partir du système SAP à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF channel model, streaming inbound flat-file IDOCs
- WCF channel model, receiving inbound operations from the SAP system
- WCF channel model, raising an exception
ms.assetid: d71d0537-fda4-44ab-85dc-6e27aad23caf
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b76ae42cf0ffc26b818e35d83f59e64158b923a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model"></a>Opérations entrantes de réception à partir du système SAP à l’aide du modèle de canal WCF
Pour agir comme un serveur RFC et recevoir des opérations appelé par le système SAP (par exemple, envoyer un IDOC ou l’appel d’une demande de changement), vous devez créer un écouteur de canal peut écouter les messages à partir d’un ID de programme SAP sur un  **System.ServiceModel.Channels.IReplyChannel** forme de canal.  
  
 Un écouteur de canal (**System.ServiceModel.Channels.IChannelListener**) est un objet de communication WCF qui peut être utilisé pour recevoir des messages à partir de points de terminaison WCF spécifiques. Les fonctions d’écouteur de canal en tant que fabrique à partir de laquelle vous pouvez créer des canaux durant laquelle les messages appelés par un client (le système SAP) peuvent être reçus par votre service. Vous créez un écouteur de canal par à partir d’un **Microsoft.Adapters.SAP.SAPBinding** objet en appelant le **BuildChannelListener** (méthode). Vous fournissez une URI qui spécifie l’ID de programme SAP à partir de laquelle les opérations entrantes seront reçues à cette méthode de connexion SAP.  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge la **IReplyChannel** forme de canal. **IReplyChannel** canaux prennent en charge un modèle d’échange de message entrant avec requête-réponse. Autrement dit, un modèle dans lequel un programme externe envoie un message de demande sur le canal et que votre programme retourne une réponse.  
  
 Pour une vue d’ensemble de la réception d’opérations à l’aide un **IReplyChannel** dans WCF, consultez [de programmation au niveau du canal de Service](https://msdn.microsoft.com/library/ms789029.aspx).
  
 Cette section aborde les sujets suivants qui sont spécifiques à la réception des opérations à partir d’un système SAP :  
  
-   Comment filtrer pour des opérations spécifiques à l’aide de l’écouteur de canal.  
  
-   Comment lever une exception sur le système SAP.  
  
-   Diffusion en continu IDOC de fichier plat entrants à partir de l’adaptateur SAP.  
  
-   La réception des opérations du système SAP.  
  
## <a name="how-do-i-filter-operations-using-the-channel-listener"></a>Comment filtrer les opérations à l’aide de l’écouteur de canal  
  
### <a name="using-an-inboundactioncollection-to-filter-operations"></a>À l’aide d’une InboundActionCollection pour filtrer des opérations  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit le **Microsoft.ServiceModel.Channels.InboundActionCollection** classe pour vous permettre de filtrer les opérations qui sont reçues par un écouteur de canal et transmises à votre code d’application. Pour filtrer les opérations spécifiques, vous créez une instance de cette classe à l’aide du point de terminaison du port d’écoute URI. Puis vous ajoutez l’action du message (requête) pour chaque opération de la cible à la collection. Enfin, vous ajoutez à la collection action entrant un **System.ServiceModel.Channels.BindingParameterCollection** de l’objet, puis passez cette collection de paramètres de liaison dans l’appel pour créer l’écouteur de canal.  
  
 Si le système SAP appelle une opération qui n’est pas dans la collection d’actions entrant :  
  
-   La [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] retourne une exception de l’EXCEPTION à l’appelant sur le système SAP avec le message suivant : « l’appel entrant RFC [RFC_NAME] sur le serveur Rfc n’est pas géré ». Dans ce message, [RFC_NAME] est le nom de la RFC (par exemple, IDOC_INBOUND_ASYNCHRONOUS).  
  
-   L’adaptateur génère un **Microsoft.ServiceModel.Channels.Common.AdapterException** avec un message qui indique l’opération qui a été reçue. Pour obtenir un exemple d’utilisation de cette exception, consultez l’exemple à la fin de cette rubrique.  
  
 L’exemple de code suivant montre comment utiliser un **InboundActionCollection** pour créer un écouteur de canal qui filtre pour un seul RFC, Z_RFC_MKD_DIV.  
  
```  
// The connection Uri must specify listener parameters (or an R-type destination in saprfc.ini)  
// and credentials.  
Uri listeneraddress =  
    new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
  
// Create a binding and set AcceptCredentialsInUri to true  
SAPBinding binding = new SAPBinding();  
binding.AcceptCredentialsInUri = true;  
  
// Create an InboundActionCollection and add the message actions to listen for,  
// only the actions added to the InboundActionCollection are received on the channel.  
// In this case a single action is specified: http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV  
InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV");  
  
// Create a BindingParameterCollection and add the InboundActionCollection  
BindingParameterCollection bpcol = new BindingParameterCollection();  
bpcol.Add(actions);  
  
// Create the channel listener by specifying the binding parameter collection (to filter for the Z_RFC_MKD_DIV action)  
listener = binding.BuildChannelListener<IReplyChannel>(listeneraddress, bpcol);  
```  
  
### <a name="manually-filtering-operations"></a>Opérations de filtrage manuellement  
 Si vous ne spécifiez pas une collection d’action entrant pour l’écouteur de canal, toutes les opérations sont appelées par le système SAP seront passées à votre code. Vous pouvez filtrer manuellement ces opérations en vérifiant l’action du message de demandes entrantes.  
  
 Il existe peut-être également des scénarios dans lesquels vous souhaitez filtrer une opération basée sur son contenu. Par exemple, si vous recevez IDOC dans :  
  
-   Format de chaîne (la **ReceiveIDocFormat** la liaison de propriété est **chaîne**) ; tous IDOC sont reçus à l’aide de l’opération ReceiveIdoc.  
  
-   Format de la RFC (le **ReceiveIDocFormat** la liaison de propriété est **Rfc**) ; tous IDOC sont reçus à l’aide de la RFC IDOC_INBOUND_ASYNCHRONOUS ou la RFC INBOUND_IDOC_PROCESS.  
  
 Dans ce scénario, que vous pouvez souhaiter implémenter un filtrage basé sur les paramètres IDOC spécifiques (par exemple, le type IDOC) dans votre code.  
  
 Lorsque vous filtrez des opérations manuellement, vous pouvez retourner une erreur à le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour les opérations qui ne gèrent pas. Cela lève l’exception de l’EXCEPTION à l’appelant sur le système SAP. Vous pouvez également retourner une réponse vide si vous ne souhaitez pas lever une exception sur SAP.  
  
 Le code suivant montre comment filtrer manuellement pour l’opération Z_RFC_MKD_DIV.  
  
```  
// Get the message from the channel  
RequestContext rc = channel.ReceiveRequest();  
Message reqMessage = rc.RequestMessage;  
  
// Filter based on the message action.  
if (reqMessage.Headers.Action == "http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV")  
{  
  
    // Process message and return response.  
    ...  
  
}  
else  
{  
    // If this isn't the correct message return an empty response or a fault message.  
    // This example returns an empty response.  
    rc.Reply(Message.CreateMessage(MessageVersion.Default, reqMessage.Headers.Action + "/response"));  
}  
```  
  
## <a name="how-do-i-raise-an-exception-on-the-sap-system"></a>Comment pour lever une Exception sur le système SAP ?  
 Pour indiquer une erreur à l’appelant sur le système SAP, vous pouvez répondre à un message de demande avec une erreur SOAP. Lorsque vous retournez une erreur SOAP à le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], l’adaptateur renvoie une exception de l’EXCEPTION à l’appelant sur le système SAP. Le message d’exception est créé à partir des éléments de l’erreur SOAP.  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] crée le message de l’EXCEPTION de SAP en fonction de l’ordre de priorité suivant :  
  
1.  Si l’erreur SOAP contient un objet de détail, l’adaptateur sérialise le détail en une chaîne et le message d’exception est défini sur cette chaîne.  
  
2.  Si l’erreur SOAP contient une raison quelconque, le message d’exception est défini à sa valeur.  
  
3.  Dans le cas contraire, l’adaptateur sérialise le **MessageFault** objet lui-même en une chaîne et le message d’exception est définie sur cette chaîne.  
  
> [!NOTE]
>  L’adaptateur utilise uniquement le message d’erreur pour créer le message d’exception retourné dans l’exception levée sur le système SAP. Par conséquent, les valeurs que vous définissez pour ces entités est complètement vous appartient.  
  
 WCF fournit le **System.ServiceModel.Channels.MessageFault** classe pour encapsuler une représentation en mémoire d’une erreur SOAP. Vous pouvez utiliser les statiques, surchargé **MessageFault.CreateFault** pour créer une nouvelle erreur SOAP à partir de laquelle vous pouvez ensuite créer un message d’erreur en appelant les méthodes **Message.CreateMessage** surcharge. WCF fournit également des surcharges de **CreateMessage** qui créent un message d’erreur sans utiliser un **MessageFault** objet.  
  
 Vous utilisez la **System.ServiceModel.Channels.RequestContext.Reply** méthode pour retourner le message d’erreur à l’adaptateur. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ignore l’action du message pour les messages d’erreur, donc vous pouvez définir l’action du message à n’importe quelle valeur.  
  
 L’exemple suivant montre comment retourner un message d’erreur à le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Cet exemple omet les étapes pour créer l’écouteur de canal et le canal.  
  
```  
RequestContext rc = channel.ReceiveRequest();  
…  
// Start processing the inbound message  
…  
// If an error is encountered return a fault to the SAP system  
// This example uses CreateMessage overload to create a fault message.  
// The overload takes a SOAP version, fault code, reason, and message action  
// The SAP adapter ignores the message action for a fault so you can set it to any value you want.   
Message faultMessage = Message.CreateMessage(MessageVersion.Default, new FaultCode("SAP Example Fault"), "Testing SAP Faults", rc.RequestMessage.Headers.Action + "/fault");  
  
rc.Reply(faultMessage);  
```  
  
## <a name="streaming-inbound-flat-file-idocs-from-the-sap-adapter"></a>Diffusion en continu IDOC de fichier plat entrants à partir de l’adaptateur SAP  
 Vous recevez (string) IDOC à partir de l’adaptateur dans l’opération ReceiveIdoc entrante de fichier plat. Les données IDOC sont représentées sous forme de chaîne sous un nœud unique dans cette opération. Pour cette raison, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge la diffusion en continu sur le message de demande de valeur de nœud. Pour effectuer la valeur du nœud de diffusion en continu, vous devez l’ouvrir le message de demande pour l’opération ReceiveIdoc en appelant le **Message.WriteBodyContents** méthode avec un **System.Xml.XmlDictionaryWriter** qui est capable de diffusion en continu les données IDOC. Pour plus d’informations sur la procédure à suivre, consultez [de diffusion en continu de fichier plat IDOC dans SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md).  
  
## <a name="how-do-i-receive-operations-from-a-sap-system-using-an-ireplychannel"></a>Comment recevoir des opérations à partir d’un système SAP à l’aide d’un IReplyChannel ?  
 Pour les opérations de réception à partir d’un système SAP à l’aide du modèle de canal WCF, procédez comme suit.  
  
#### <a name="to-receive-operations-from-the-sap-system-using-an-ireplychannel"></a>Pour les opérations de réception à partir du système SAP à l’aide d’un IReplyChannel  
  
1.  Créez une instance de **SAPBinding** et définissez les propriétés de liaison requises pour les opérations que vous souhaitez recevoir. Au minimum, vous devez définir le **AcceptCredentialsInUri** liaison de propriété à true. Pour agir comme un serveur tRFC, vous devez définir le **TidDatabaseConnectionString** propriété de liaison. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
    ```  
    SAPBinding binding = new SAPBinding();  
    binding.AcceptCredentialsInUri = true;  
    ```  
  
2.  Créer un **BindingParameterCollection** et ajoutez un **InboundActionCollection** qui contient les actions des opérations que vous souhaitez recevoir. L’adaptateur renvoie une exception au système SAP pour toutes les autres opérations. Cette étape est facultative. Pour plus d’informations, consultez [recevoir des opérations de trafic entrant à partir du système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md).  
  
    ```  
    InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
    actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV");  
    BindingParameterCollection bpcol = new BindingParameterCollection();  
    bpcol.Add(actions);  
    ```  
  
3.  Créer un écouteur de canal en appelant **BuildChannelListener < IReplyChannel\>**  méthode sur le **SAPBinding** et ouvrez-le. Vous spécifiez l’URI de connexion SAP comme l’un des paramètres pour cette méthode. L’URI de connexion doit contenir des paramètres pour une Destination RFC sur le système SAP. Pour plus d’informations sur l’URI de connexion SAP, consultez [créer l’URI de connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md). Si vous avez créé un **BindingParameterCollection** à l’étape 3, vous également spécifiez cela lorsque vous créez l’écouteur de canal.  
  
    ```  
    Uri listeneraddress =  
        new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
    IChannelListener<IReplyChannel> listener = binding.BuildChannelListener<IReplyChannel>(connectionUri, bpcol);  
    listener.Open();  
    ```  
  
4.  Obtenir un **IReplyChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur et ouvrez-le.  
  
    ```  
    IReplyChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  
  
5.  Appeler **ReceiveRequest** sur le canal pour obtenir le message de demande pour l’opération suivante à partir de l’adaptateur.  
  
    ```  
    RequestContext rc = channel.ReceiveRequest();  
    ```  
  
6.  Consommer le message de demande envoyé par l’adaptateur. Vous obtenez le message de demande à partir de la **RequestMessage** propriété de la **RequestContext**. Vous pouvez consommer le message en utilisant un **XmlReader** ou **XmlDictionaryWriter**.  
  
    ```  
    XmlReader reader = (XmlReader)rc.RequestMessage.GetReaderAtBodyContents();  
    ```  
  
7.  Terminer l’opération en renvoyant une réponse ou une erreur au système SAP :  
  
    1.  Traiter le message et renvoyer une réponse au système SAP en retournant le message de réponse à l’adaptateur. Cet exemple retourne un message vide.  
  
        ```  
        respMessage = Message.CreateMessage(MessageVersion.Default, rc.RequestMessage.Headers.Action + "/response");  
        rc.Reply(respMessage);  
        ```  
  
    2.  Renvoie une exception au système SAP en renvoyant un message d’erreur à l’adaptateur. Vous pouvez utiliser n’importe quelle valeur pour l’action du message, le code d’erreur et la raison.  
  
        ```  
        MessageFault fault = MessageFault.CreateFault(new FaultCode("ProcFault"), "Processing Error");  
        Message respMessage = Message.CreateMessage(MessageVersion.Default, fault, String.Empty);  
        rc.Reply(respMessage);  
        ```  
  
8.  Fermez le contexte de requête une fois que vous avez envoyé le message.  
  
    ```  
    rc.Close();  
    ```  
  
9. Fermer le canal lorsque vous avez terminé le traitement de la demande.  
  
    ```  
    channel.Close()  
    ```  
  
    > [!IMPORTANT]
    >  Vous devez fermer le canal une fois que vous avez terminé le traitement de l’opération. Échec de fermer le canal peut affecter le comportement de votre code.  
  
10. Fermer l’écouteur lorsque vous avez terminé la réception des opérations du système SAP.  
  
    ```  
    listener.Close()  
    ```  
  
    > [!IMPORTANT]
    >  Vous devez fermer explicitement l’écouteur lorsque vous avez terminé de l’utiliser ; Sinon, votre programme ne peut pas fonctionner correctement. Fermeture de l’écouteur ne ferme pas les canaux créés à l’aide de l’écouteur. Vous devez également explicitement fermer chaque canal créé à l’aide de l’écouteur.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant reçoit une demande de changement, Z_RFC_MKD_DIV à partir du système SAP. Ce document RFC divise deux nombres. L’implémentation dans cet exemple utilise une **InboundActionCollection** pour filtrer les lorsqu’un message est reçu pour l’opération de Z_RFC_MKD_DIV et si les éléments suivants :  
  
-   Si le dénominateur est différente de zéro, elle écrit le résultat de la division dans la console et le retourne au système SAP.  
  
-   Si le diviseur est zéro, il écrit le message d’exception résultant dans la console et retourne une erreur au système SAP.  
  
-   Si toute autre opération est envoyée par le système SAP, il écrit un message dans la console. Dans ce cas, l’adaptateur retourne une erreur au système SAP.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.Runtime.Serialization;  
using System.Xml;  
using System.IO;  
  
// Add WCF, Adapter LOB SDK, and SAP Adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Add this namespace to use Channel Model   
using System.ServiceModel.Channels;  
  
// Include this namespace for Adapter LOB SDK and SAP exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// This sample demonstrates using the adapter as an rfc server over a channel.  
// The sample implements an RFC, Z_RFC_MKD_DIV that divides two numbers and returns the result  
// 1)  A SAPBinding instance is created and configured (AcceptCredentialsInUri is set true)  
// 2)  A binding parameter collection is created with an InboundAction collection that specifies  
//     target RFC (Z_RFC_MKD_DIV) so that only messages with this action will be received by the  
//     listener (and channel).  
// 3)  An <IReplyChannel> listener is created from the binding and binding parameter collection  
// 4)  A channel is created and opened to receive a request  
// 6)  When Z_RFC_MKD_DIV is received the two parameters are divided and the parameters and result  
//     are written to the console, then the result is returned to the adapter by using a template  
//     message.  
// 7)  If a divide by 0 occurs the exception message is written to the console and a  
//     fault is returned to the SAP system  
// 8)  If any other operation is received an error message is written to the console and the adapter  
///    returns a fault to the SAP system  
// 9)  IMPORTANT you must close the channel and listener to deregister them from the SAP Program ID.  
namespace SapRfcServerCM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Variables to hold the listener and channel  
            IChannelListener<IReplyChannel> listener = null;  
            IReplyChannel channel = null;  
  
            Console.WriteLine("Sample started");  
            Console.WriteLine("Initializing and creating channel listener -- please wait");  
            try  
            {  
  
                // The connection Uri must specify listener parameters (or an R-type destination in saprfc.ini)  
                // and also credentials.  
                Uri listeneraddress =  
                    new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
  
                // Create a binding -- set AcceptCredentialsInUri true  
                SAPBinding binding = new SAPBinding();  
                binding.AcceptCredentialsInUri = true;  
  
                // Create a binding parameter collection with a list of SOAP actions to listen on  
                // in this case: http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV  
                // This ensures that only these actions are received on the channel.  
                InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
                actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV");  
                BindingParameterCollection bpcol = new BindingParameterCollection();  
                bpcol.Add(actions);  
  
                // Pass the Uri and the binding parameter collection (to specify the Z_RFC_MKD_DIV action)  
                listener = binding.BuildChannelListener<IReplyChannel>(listeneraddress, bpcol);  
  
                Console.WriteLine("Opening listener");  
                // Open the listener  
                listener.Open();  
  
                // Get an IReplyChannel  
                channel = listener.AcceptChannel();  
  
                Console.WriteLine("Opening channel");  
                // Open the channel  
                channel.Open();  
  
                Console.WriteLine("\nReady to receive Z_RFC_MKD_DIV RFC");  
  
                try  
                {  
                    // Get the message from the channel  
                    RequestContext rc = channel.ReceiveRequest();  
  
                    // Get the request message sent by SAP  
                    Message reqMessage = rc.RequestMessage;  
  
                    // get the message body  
                    XmlReader reader = reqMessage.GetReaderAtBodyContents();  
  
                    reader.ReadStartElement("Z_RFC_MKD_DIV");  
                    reader.ReadElementString("DEST");  
                    int x_in = int.Parse(reader.ReadElementString("X"));  
                    int y_in = int.Parse(reader.ReadElementString("Y"));  
                    reader.ReadEndElement();  
  
                    Console.WriteLine("\nRfc Received");  
                    Console.WriteLine("X =\t\t" + x_in);  
                    Console.WriteLine("Y =\t\t" + y_in);  
  
                    Message messageOut = null;  
  
                    try   
                    {  
                        int result_out = x_in/y_in;  
  
                        Console.WriteLine("RESULT =\t" + result_out.ToString());  
  
                        string out_xml = "<Z_RFC_MKD_DIVResponse xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"><RESULT>" + result_out + "</RESULT></Z_RFC_MKD_DIVResponse>";  
                        StringReader sr = new StringReader(out_xml);  
                        reader = XmlReader.Create(sr);  
  
                        // create a response message  
                        // be sure to specify the response action  
                        messageOut = Message.CreateMessage(MessageVersion.Default, reqMessage.Headers.Action + "/response", reader);  
  
                    }  
                    catch (DivideByZeroException ex)  
                    {  
                        Console.WriteLine();  
                        Console.WriteLine(ex.Message + " Returning fault to SAP");  
  
                        // Create a message that contains a fault  
                        // The fault code and message action can be any value  
  
                        messageOut = Message.CreateMessage(MessageVersion.Default, new FaultCode("Fault"), ex.Message, string.Empty);  
                    }  
  
                    // Send the reply  
                    rc.Reply(messageOut);  
  
                    // Close the request context  
                    rc.Close();  
  
                }  
                catch (AdapterException aex)  
                {  
                    // Will get here if the message received was not in the InboundActionCollection  
                    Console.WriteLine();  
                    Console.WriteLine(aex.Message);  
                }  
  
                // Wait for a key to exit  
                Console.WriteLine("\nHit <RETURN> to end");  
                Console.ReadLine();  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the SAP system");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the SAP system");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
            }  
            finally  
            {  
                // IMPORTANT: close the channel and listener to stop listening on the Program ID  
                if (channel != null)  
                {  
                    if (channel.State == CommunicationState.Opened)  
                        channel.Close();  
                    else  
                        channel.Abort();  
                }  
  
                if (listener != null)  
                {  
                    if (listener.State == CommunicationState.Opened)  
                        listener.Close();  
                    else  
                        listener.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications en utilisant le modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)
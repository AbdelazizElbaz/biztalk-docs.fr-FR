---
title: "Recevoir des Messages d’interrogation de données modifiées dans la base de données Oracle à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF channel model, receiving polling-based messages
- how to, receive polling-based messages by using the WCF channel model
ms.assetid: 13f501e4-cff7-497c-a9da-fdd6382c779f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01e1596c0b0676db916068ff9a33a8be9d6a9fa3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-based-data-changed-messages-in-oracle-database-using-the-wcf-channel-model"></a>Recevoir des Messages d’interrogation de données modifiées dans la base de données Oracle à l’aide du modèle de canal WCF
Vous pouvez configurer le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] pour interroger une table de base de données Oracle ou une vue pour toutes les modifications de données. Pour effectuer ce une opération d’interrogation, l’adaptateur exécute régulièrement une requête SQL sur une table Oracle ou d’une vue, suivi d’un bloc de code PL/SQL facultatif. Les résultats de la requête SQL sont ensuite retournées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à votre code en tant que fortement typée jeu de résultats en une opération POLLINGSTMT entrante. Pour plus d’informations sur le mécanisme utilisé pour configurer et effectuer d’interrogation sur Oracle de base de données à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [recevoir des messages d’interrogation de données modifiées dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md). Il est fortement recommandé de lire cette rubrique avant de continuer.  
  
 Vous configurez le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à l’interrogation et de table de base de données Oracle ou de vue en définissant les propriétés de liaison sur une instance de **OracleDBBinding**. Dans le modèle de canal WCF, vous utilisez ensuite cette liaison pour construire un écouteur de canal à partir de laquelle vous pouvez obtenir un **IInputChannel** doit recevoir l’opération POLLINGSTMT à partir de l’adaptateur.  
  
 Pour une vue d’ensemble de la réception d’opérations à l’aide un **IInputChannel** dans WCF, consultez [de programmation au niveau du canal de Service](https://msdn.microsoft.com/library/ms789029.aspx). 
  
 Les sections de cette rubrique fournissent des informations pour vous aider à effectuer d’interrogation sur les tables de base de données Oracle et le modèle de canal de vues à l’aide de WCF.  
  
## <a name="consuming-the-pollingstmt-request-message"></a>Le message de demande POLLINGSTMT  
 L’adaptateur appelle l’opération POLLINGSTMT sur votre code pour interroger la base de données Oracle. Autrement dit, l’adaptateur envoie un message de demande POLLINGSTMT que vous recevez via un **IInputChannel** forme de canal. Le message de demande POLLINGSTMT contient le jeu de résultats de la requête spécifiée par la **PollingStatement** propriété de liaison. Vous pouvez utiliser le message POLLINGSTMT de deux manières :  
  
-   Pour consommer le message à l’aide de la valeur du nœud de diffusion en continu vous devez appeler la **WriteBodyContents** méthode sur la réponse de message et lui passer une **XmlDictionaryWriter** qui implémente la diffusion en continu de la valeur du nœud.  
  
-   Pour consommer le message à l’aide du nœud de diffusion en continu, vous pouvez appeler **GetReaderAtBodyContents** sur le message de réponse pour obtenir un **XmlReader**.  
  
 Vous utilisez généralement la valeur du nœud de diffusion en continu pour consommer des jeux de résultats qui contiennent des colonnes de données Oracle LOB.  
  
 Pour plus d’informations sur la structure du message de l’opération POLLINGSTMT, consultez [des schémas de Message pour les opérations d’interrogation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md).  
  
 Pour plus d’informations sur la façon dont [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge la diffusion en continu des données LOB, consultez [diffusion en continu des types de données dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).  
  
 Pour plus d’informations sur l’implémentation de diffusion en continu dans votre code pour prendre en charge la diffusion en continu de bout en bout des données LOB de valeur de nœud, consultez [de diffusion en continu Oracle de base de données LOB données Types à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 L’exemple dans cette rubrique utilise le SCOTT. Table ACCOUNTACTIVITY et SCOTT. ACCOUNT_PKG. Fonction PROCESS_ACTIVITY. Un script pour générer ces artefacts est fourni avec les exemples. L’exemple effectue les opérations suivantes :  
  
-   Dans le cadre de l’instruction d’interrogation, sélectionne tous les enregistrements de la table ACCOUNTACTIVITY s’affiche sur la console.  
  
-   Dans le cadre de l’instruction de sondage post, l’exemple appelle la fonction PROCESS_ACTIVITY qui déplace tous les enregistrements à partir de la table ACCOUNTACTIVITY au tableau ACTIVITYHISTORY.  
  
-   Les interrogations suivantes sur la table ACCOUNTACTIVITY ne retournent pas tous les enregistrements. Toutefois, si vous souhaitez que l’exemple de renvoyer plus d’enregistrements dans le cadre de l’opération d’interrogation, vous devez insérer des enregistrements dans la table ACCOUNTACTIVITY. Vous pouvez le faire en exécutant le script more_activity_data.sql fourni avec les exemples.  
  
 Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="how-do-i-poll-an-oracle-database-using-an-iinputchannel"></a>Comment pour interroger une base de données Oracle à l’aide d’un IInputChannel ?  
 Pour interroger une table de base de données Oracle ou une vue de recevoir des messages de modification de données à l’aide du modèle de canal WCF, procédez comme suit.  
  
#### <a name="to-receive-data-changed-messages-using-an-iinputchannel"></a>Pour recevoir des messages de modification de données à l’aide d’un IInputChannel  
  
1.  Créez un projet Visual c# dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Pour cette rubrique, créez une application console.  
  
2.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleDB`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, et `System.Runtime.Serialization`.  
  
3.  Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :  
  
    -   `Microsoft.Adapters.OracleDB`  
  
    -   `Microsoft.ServiceModel.Channels`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Description`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
    -   `System.Runtime.Serialization`  
  
    -   `System.IO`  
  
    -   `Microsoft.ServiceModel.Channels.Common`  
  
4.  Créez une instance de **OracleDBBinding** et définissez les propriétés de liaison requises pour configurer l’interrogation. Au minimum, vous devez définir le **InboundOperationType**, **PollingStatement**, et **PollingInterval** propriétés de liaison. Pour cet exemple, vous définissez également la **PostPollStatement** propriété de liaison. Pour plus d’informations sur les propriétés utilisées pour configurer l’interrogation de liaison, consultez [recevoir des messages d’interrogation de données modifiées dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).  
  
    ```  
    OracleDBBinding binding = new OracleDBBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PollingInterval = 30;  
    binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
    binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;"  
    ```  
  
5.  Créer une collection de paramètres de liaison et définir les informations d’identification.  
  
    ```  
    ClientCredentials credentials = new ClientCredentials();  
    credentials.UserName.UserName = "SCOTT";  
    credentials.UserName.Password = "TIGER";  
  
    BindingParameterCollection bindingParams = new BindingParameterCollection();  
    bindingParams.Add(credentials);  
    ```  
  
6.  Créer un écouteur de canal et l’ouvrir. Vous créez l’écouteur en appelant **BuildChannelListener < IInputChannel\>**  méthode sur le **OracleDBBinding**. Vous pouvez modifier l’espace de noms cible pour l’opération POLLINGSTMT en définissant la propriété PollingId dans l’URI de connexion. Pour plus d’informations sur l’URI de connexion de l’adaptateur, consultez [créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).  
  
    ```  
    IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
    listener.Open();  
    ```  
  
7.  Obtenir un **IInputChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur et ouvrez-le.  
  
    ```  
    IInputChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  
  
8.  Appeler **réception** sur le canal pour obtenir le prochain message POLLINGSTMT à partir de l’adaptateur.  
  
    ```  
    Message message = channel.Receive();  
    ```  
  
9. Utiliser le jeu de résultats retourné par l’opération POLLINGSTMT. Vous pouvez consommer le message en utilisant un **XmlReader** ou **XmlDictionaryWriter**.  
  
    ```  
    XmlReader reader = message.GetReaderAtBodyContents();  
    ```  
  
10. Fermer le canal lorsque vous avez terminé le traitement de la demande.  
  
    ```  
    channel.Close()  
    ```  
  
    > [!IMPORTANT]
    >  Vous devez fermer le canal une fois que vous avez terminé le traitement de l’opération POLLINGSTMT. Échec de fermer le canal peut affecter le comportement de votre code.  
  
11. Fermer l’écouteur lorsque vous avez terminé la réception de messages de données modifiées.  
  
    ```  
    listener.Close()  
    ```  
  
    > [!IMPORTANT]
    >  Fermeture de l’écouteur ne ferme pas les canaux créés à l’aide de l’écouteur. Vous devez fermer explicitement chaque canal créé à l’aide de l’écouteur.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour interroger les tables de base de données Oracle et des vues et de recevoir le POLLLINGSTMT opération à l’aide de WCF modèle de canal. Le jeu de résultats retourné dans l’opération POLLINGSTMT sont écrite dans la console en utilisant un **XmlReader**.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF LOB Adapter SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Add this namespace for channel model  
using System.ServiceModel.Channels;  
  
using System.Xml;  
using System.Runtime.Serialization;  
using System.IO;  
  
// Include this namespace for the WCF LOB Adapter SDK and Oracle exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
namespace OraclePollingCM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Uri connectionUri = new Uri("oracleDB://ADAPTER/");  
  
            IChannelListener<IInputChannel> listener = null;  
            IInputChannel channel = null;  
  
            // set timeout to receive POLLINGSTMT message  
            TimeSpan messageTimeout = new TimeSpan(0, 0, 30);  
  
            Console.WriteLine("Sample Started");  
  
            try  
            {  
                // Create a binding: specify the InboundOperationType, PollingInterval (in seconds), the           
                // PollingStatement,and the PostPollStatement.  
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
  
                Console.WriteLine("Opening listener");  
                // get a listener  from the binding  
                listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
                listener.Open();  
  
                Console.WriteLine("Opening channel");  
                // get a channel from the listener  
                channel = listener.AcceptChannel();  
                channel.Open();  
  
                Console.WriteLine("Channel opened -- waiting for polled data");  
                Console.WriteLine("Receive request timeout is {0}", messageTimeout);  
  
                // Poll five times with the specified message timeout   
                // If a timeout occurs polling will be aborted  
                for (int i = 0; i < 5; i++)  
                {  
                    Console.WriteLine("Polling: " + i);  
                    Message message = null;  
                    XmlReader reader = null;  
                    try  
                    {  
                        //Message is received so process the results  
                        message = channel.Receive(messageTimeout);  
                    }  
                    catch (System.TimeoutException toEx)  
                    {  
                        Console.WriteLine("\nNo data for request number {0}: {1}", i + 1, toEx.Message);  
                        continue;  
                    }  
  
                    // Get the query results using an XML reader  
                    try  
                    {  
                        reader = message.GetReaderAtBodyContents();  
                    }  
                    catch (Exception ex)  
                    {  
                        Console.WriteLine("Exception :" + ex);  
                        throw;  
                    }  
  
                    // Write the TID, ACCOUNT, AMOUNT, and TRANSDATE for each record to the Console  
                    Console.WriteLine("\nPolling data received for request number {0}", i+1);  
                    Console.WriteLine("Tx ID\tACCOUNT\tAMOUNT\tTx DATE");  
  
                    while (reader.Read())  
                    {  
                        if (reader.IsStartElement())  
                        {  
                            switch (reader.Name)  
                            {  
                                case "POLLINGSTMTRECORD":  
                                    Console.Write("\n");  
                                    break;  
  
                                case "TID":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
  
                                case "ACCOUNT":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
                                case "AMOUNT":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
  
                                case "TRANSDATE":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
  
                                default:  
                                    break;  
                            }  
                        }  
                    }  
  
                    // return the cursor  
                    Console.WriteLine();  
  
                    // close the reader  
                    reader.Close();  
  
                    //            To save the polling data to a file you can REPLACE the code above with the following  
                    //  
                    //            XmlDocument doc = new XmlDocument();  
                    //            doc.Load(reader);  
                    //            using (XmlWriter writer = XmlWriter.Create("PollingOutput.xml"))  
                    //            {  
                    //                doc.WriteTo(writer);  
                    //            }  
                    message.Close();  
                }  
  
                Console.WriteLine("\nPolling done -- hit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the Oracle Database");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the Oracle Database");  
                Console.WriteLine(cex.InnerException.Message);  
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
                // IMPORTANT: close the channel and listener to stop polling  
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
 [Développer des applications de base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)
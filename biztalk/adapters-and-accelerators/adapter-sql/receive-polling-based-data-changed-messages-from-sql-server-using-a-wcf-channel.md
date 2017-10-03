---
title: "Recevoir des Messages d’interrogation de données modifiées à partir de SQL Server à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0f4af71-fb0c-433d-ba74-48ee6487eb1a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb785631d6fe00ea68f57f943dca11ebd1a84b1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-based-data-changed-messages-from-sql-server-by-using-the-wcf-channel-model"></a>Recevoir des Messages d’interrogation de données modifiées à partir de SQL Server à l’aide du modèle de canal WCF
Vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des messages de modification de données périodiques de tables SQL Server ou des vues. Vous pouvez spécifier une instruction d’interrogation de l’adaptateur s’exécute pour interroger la base de données. L’instruction d’interrogation peut être une instruction SELECT ou une procédure stockée qui retourne un jeu de résultats.  
  
 Pour plus d’informations sur la façon dont l’adaptateur prend en charge d’interrogation, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).  
  
> [!IMPORTANT]
>  Si vous souhaitez disposer d’interrogation plus d’une opération dans une application unique, vous devez spécifier un **InboundID** propriété de connexion dans le cadre de la connexion URI pour le rendre unique. L’ID entrant que vous spécifiez est ajouté à l’espace de noms d’opération pour le rendre unique.  
  
## <a name="how-this-topic-demonstrates-polling"></a>Comment cette rubrique illustre l’interrogation  
 Dans cette rubrique, pour illustrer comment le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge la réception de données, les messages de modification, créer une application .NET pour les **d’interrogation** opération. Pour cette rubrique, vous devez spécifier le **PolledDataAvailableStatement** en tant que :  
  
```  
SELECT COUNT(*) FROM Employee  
```  
  
 Le **PolledDataAvailableStatement** doit retourner un jeu de résultats avec la première cellule contenant une valeur positive. Si la première cellule ne contient pas une valeur positive, l’adaptateur n’exécute pas l’instruction d’interrogation.  
  
 Dans le cadre de l’instruction d’interrogation, effectuez les opérations suivantes :  
  
1.  Sélectionnez toutes les lignes de la table Employee.  
  
2.  Exécuter une procédure stockée (MOVE_EMP_DATA) pour déplacer tous les enregistrements de la table Employee pour une table HistoriqueEmployé.  
  
3.  Exécuter une procédure stockée (ADD_EMP_DETAILS) pour ajouter un nouvel enregistrement dans la table Employee. Cette procédure prend le nom de l’employé, désignation et salaire en tant que paramètres.  
  
 Pour effectuer ces opérations, vous devez spécifier les informations suivantes pour le **PollingStatement** propriété de liaison :  
  
```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  
  
 Après l’exécution de l’instruction d’interrogation, tous les enregistrements de la table Employee sont sélectionnés et la réception du message à partir de SQL Server. Une fois la procédure stockée de MOVE_EMP_DATA est exécutée par l’adaptateur, tous les enregistrements sont déplacés vers la table HistoriqueEmployé. Ensuite, la procédure stockée de ADD_EMP_DETAILS est exécutée pour ajouter un nouvel enregistrement dans la table Employee. L’exécution de l’interrogation suivante retourne uniquement un seul enregistrement. Ce cycle se poursuit jusqu'à la fermeture de l’écouteur de canal.  
  
## <a name="configuring-a-polling-query-with-the-sql-adapter-binding-properties"></a>Configuration d’une requête d’interrogation avec l’adaptateur SQL propriétés de liaison  
 Le tableau suivant récapitule les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] propriétés que vous utilisez pour configurer l’adaptateur pour recevoir des messages de modification de données de liaison. Vous devez spécifier ces propriétés de liaison dans le cadre de l’application .NET pour l’interrogation.  
  
|Propriété de liaison| Description|  
|----------------------|-----------------|  
|**InboundOperationType**|Spécifie si vous souhaitez effectuer **d’interrogation**, **TypedPolling**, ou **Notification** opération entrante. Valeur par défaut est **d’interrogation**.|  
|**PolledDataAvailableStatement**|Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur. L’instruction SQL doit retourner un jeu de résultats composé de lignes et de colonnes. Uniquement si une ligne est disponible, l’instruction SQL spécifiée pour le **PollingStatement** liaison de la propriété sera exécutée.|  
|**PollingIntervalInSeconds**|Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison. La valeur par défaut est 30 secondes. L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives. Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur attend que le temps restant dans l’intervalle.|  
|**PollingStatement**|Spécifie l’instruction SQL pour interroger la table de base de données SQL Server. Vous pouvez spécifier une instruction SELECT simple ou une procédure stockée pour l’instruction d’interrogation. La valeur par défaut est null. Vous devez spécifier une valeur pour **PollingStatement** pour activer l’interrogation. L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison. Vous pouvez spécifier n’importe quel nombre d’instructions SQL séparées par un point-virgule.|  
|**PollWhileDataFound**|Spécifie si le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignore l’intervalle d’interrogation et exécute en permanence de l’instruction SQL spécifiée pour le **PolledDataAvailableStatement** liaison de propriété, si les données sont disponibles dans la table interrogée. Si aucune donnée n’est disponible dans la table, l’adaptateur revient à exécuter l’instruction SQL à l’intervalle d’interrogation spécifié. Valeur par défaut est **false**.|  
  
 Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour interroger le SQL Server, lire le reste de cette rubrique.  
  
## <a name="consuming-the-polling-request-message"></a>Le message de demande d’interrogation  
 L’adaptateur appelle la **d’interrogation** opération sur votre code pour interroger la base de données SQL Server. Autrement dit, l’adaptateur envoie un message de demande d’interrogation qui s’affiche sur une forme de canal IInputChannel. Le message de demande d’interrogation contient le jeu de résultats de la requête spécifiée par la propriété de liaison PollingStatement. Vous pouvez utiliser le message d’interrogation de deux manières :  
  
-   Pour consommer le message à l’aide de la valeur du nœud de diffusion en continu vous devez appeler la **WriteBodyContents** méthode sur la réponse de message et lui passer une **XmlDictionaryWriter** qui implémente la diffusion en continu de la valeur du nœud.  
  
-   Pour consommer le message à l’aide du nœud de diffusion en continu, vous pouvez appeler **GetReaderAtBodyContents** sur le message de réponse pour obtenir un **XmlReader**.  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 Les exemples de cette rubrique interrogent la table Employee. L’exemple utilise également les MOVE_EMP_DATA ADD_EMP_DETAILS procédure stockée. Un script pour générer ces artefacts est fourni avec les exemples. Pour plus d’informations sur les exemples, consultez [exemples de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md). Un exemple, **Polling_ChannelModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.  
  
## <a name="receiving-inbound-messages-for-polling-operation-using-the-wcf-channel-model"></a>Réception des Messages entrants pour l’opération d’interrogation à l’aide du modèle de canal WCF  
 Cette section fournit des instructions sur la façon d’écrire une application .NET (modèle de canal) pour recevoir des messages entrants d’interrogation à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
#### <a name="to-receive-polling-messages-from-the-sql-adapter"></a>Pour recevoir des messages de l’interrogation de l’adaptateur SQL  
  
1.  Créez un projet Microsoft Visual c# dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Pour cette rubrique, créez une application console.  
  
2.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, et `System.Runtime.Serialization`.  
  
3.  Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :  
  
    -   `Microsoft.Adapters.Sql`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Description`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  Spécifiez l’URI de connexion. Pour plus d’informations sur l’URI de connexion de l’adaptateur, consultez [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  
  
    ```  
    Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
    ```  
  
5.  Créez une instance de **SqlAdapterBinding** et définissez les propriétés de liaison requises pour configurer l’interrogation. Au minimum, vous devez définir le **InboundOperationType**, **PolledDataAvailableStatement**, et **PollingStatement** propriétés de liaison. Pour plus d’informations sur les propriétés utilisées pour configurer l’interrogation de liaison, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).  
  
    ```  
    SqlAdapterBinding binding = new SqlAdapterBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
    binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
    ```  
  
6.  Créer une collection de paramètres de liaison et définir les informations d’identification.  
  
    ```  
    ClientCredentials credentials = new ClientCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
  
    BindingParameterCollection bindingParams = new BindingParameterCollection();  
    bindingParams.Add(credentials);  
    ```  
  
7.  Créer un écouteur de canal et l’ouvrir. Vous créez l’écouteur en appelant **BuildChannelListener < IInputChannel\>**  méthode sur le **SqlAdapterBinding**.  
  
    ```  
    IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
    listener.Open();  
    ```  
  
8.  Obtenir un **IInputChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur et ouvrez-le.  
  
    ```  
    IInputChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  
  
9. Appeler **réception** sur le canal pour obtenir le prochain message POLLINGSTMT à partir de l’adaptateur.  
  
    ```  
    Message message = channel.Receive();  
    ```  
  
10. Utiliser le jeu de résultats retourné par l’opération POLLINGSTMT. Vous pouvez consommer le message en utilisant un **XmlReader** ou **XmlDictionaryWriter**.  
  
    ```  
    XmlReader reader = message.GetReaderAtBodyContents();  
    ```  
  
11. Fermer le canal lorsque vous avez terminé le traitement de la demande.  
  
    ```  
    channel.Close()  
    ```  
  
    > [!IMPORTANT]
    >  Vous devez fermer le canal une fois que vous avez terminé le traitement de l’opération POLLINGSTMT. Échec de fermer le canal peut affecter le comportement de votre code.  
  
12. Fermer l’écouteur lorsque vous avez terminé la réception de messages de données modifiées.  
  
    ```  
    listener.Close()  
    ```  
  
    > [!IMPORTANT]
    >  Fermeture de l’écouteur ne ferme pas les canaux créés à l’aide de l’écouteur. Vous devez fermer explicitement chaque canal créé à l’aide de l’écouteur.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre une requête d’interrogation qui s’exécute à la table Employee. L’instruction d’interrogation effectue les tâches suivantes :  
  
-   Sélectionne tous les enregistrements de la table Employee.  
  
-   Exécute la procédure MOVE_EMP_DATA stockées pour déplacer tous les enregistrements à partir de la table Employee à HistoriqueEmployé table.  
  
-   Exécute la procédure stockée de ADD_EMP_DETAILS pour ajouter un enregistrement unique dans la table Employee.  
  
 Les messages d’interrogation sont enregistrés au `C:\PollingOutput.xml`.  
  
```  
using System;  
using Microsoft.Adapters.Sql;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
  
using System.Xml;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("Sample started. This sample will poll 5 times and will perform the following tasks:");  
            Console.WriteLine("Press any key to start polling...");  
            Console.ReadLine();  
            IChannelListener<IInputChannel> listener = null;  
  
            IInputChannel channel = null;  
  
            try  
            {  
                TimeSpan messageTimeout = new TimeSpan(0, 0, 30);  
  
                SqlAdapterBinding binding = new SqlAdapterBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
                binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
  
                Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
  
                ClientCredentials credentials = new ClientCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                BindingParameterCollection bindingParams = new BindingParameterCollection();  
                bindingParams.Add(credentials);  
  
                listener = binding.BuildChannelListener<IInputChannel>(ConnectionUri, bindingParams);  
                listener.Open();  
  
                channel = listener.AcceptChannel();  
                channel.Open();  
  
                Console.WriteLine("Channel and Listener opened...");  
                Console.WriteLine("\nWaiting for polled data...");  
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
  
                    XmlDocument doc = new XmlDocument();  
                    doc.Load(reader);  
                    using (XmlWriter writer = XmlWriter.Create("C:\\PollingOutput.xml"))  
                    {  
                        doc.WriteTo(writer);  
                        Console.WriteLine("The polling response is saved at 'C:\\PollingOutput.xml'");  
                    }  
  
                    // return the cursor  
                    Console.WriteLine();  
  
                    // close the reader  
                    reader.Close();  
  
                    message.Close();  
                }  
                Console.WriteLine("\nPolling done -- hit <RETURN> to finish");  
                Console.ReadLine();  
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
[Développer des applications SQL à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)
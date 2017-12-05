---
title: "Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT avec le modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 495b9010-856f-4782-bd19-1522bc3eb950
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1164cb59bf7fe0e168834f60364cd82f871b3ae0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="poll-oracle-e-business-suite-using-select-statement-with-the-wcf-channel-model"></a>Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT avec le modèle de canal WCF
Vous pouvez configurer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des messages de modification de données périodiques à l’aide d’une instruction SELECT pour l’interrogation de façon permanente les tables d’interface, interface, des vues, des tables et des vues dans Oracle E-Business Suite. Vous pouvez spécifier une instruction SELECT comme une instruction d’interrogation de l’adaptateur s’exécute périodiquement pour Oracle E-Business Suite. Vous pouvez également spécifier un bloc de code après interrogation PL/SQL que l’adaptateur s’exécute après l’exécution de l’instruction d’interrogation.  
  
 Pour activer l’interrogation, vous devez spécifier certaines propriétés de liaison comme décrit dans cette rubrique. Pour plus d’informations sur la façon dont l’adaptateur prend en charge d’interrogation, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).  
  
## <a name="configuring-a-polling-operation-with-oracle-e-business-suite-adapter-binding-properties"></a>Configuration d’une opération d’interrogation avec liaison des propriétés de l’adaptateur Oracle E-Business Suite  
 Le tableau suivant récapitule les [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] messages de modification des propriétés de liaison que vous utilisez pour configurer l’adaptateur pour recevoir des données. Vous devez spécifier ces propriétés de liaison lors de l’exécution de l’application d’interrogation.  
  
|Propriété de liaison| Description|  
|----------------------|-----------------|  
|**InboundOperationType**|Spécifie si vous souhaitez effectuer **d’interrogation** ou **Notification** opération entrante. Valeur par défaut est **d’interrogation**.|  
|**PolledDataAvailableStatement**|Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur. Uniquement si un enregistrement n’est disponible, l’instruction SELECT que vous spécifiez pour le **PollingInput** liaison de la propriété sera exécutée.|  
|**PollingInterval**|Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison. La valeur par défaut est 30 secondes. L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives. Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur est en veille pendant le temps restant dans l’intervalle.|  
|**PollingInput**|Spécifie l’instruction d’interrogation. Pour interroger à l’aide d’une instruction SELECT, vous devez spécifier une instruction SELECT pour cette propriété de liaison. La valeur par défaut est null.<br /><br /> Vous devez spécifier une valeur pour **PollingInput** propriété pour activer l’interrogation de liaison. L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison.|  
|**PollingAction**|Spécifie l’action pour l’opération d’interrogation. Vous pouvez déterminer l’action d’interrogation de l’interface de service généré pour l’opération en utilisant la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].|  
|**PostPollStatement**|Spécifie un bloc d’instructions qui est exécuté après l’instruction spécifiée par le **PollingInput** propriété de liaison est exécutée.|  
|**PollWhileDataFound**|Spécifie si le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignore l’intervalle d’interrogation et exécute en permanence l’instruction d’interrogation, si les données sont disponibles dans la table interrogée. Si aucune donnée n’est disponible dans la table, l’adaptateur revient pour exécuter l’instruction d’interrogation à l’intervalle d’interrogation spécifié. La valeur par défaut est False.|  
  
 Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour interroger la base de données Oracle, lire le reste de cette rubrique.  
  
## <a name="how-this-topic-demonstrates-polling"></a>Comment cette rubrique illustre l’interrogation  
 Dans cette rubrique, pour illustrer comment le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge la réception de données modifier des messages à l’aide des instructions SELECT, vous continuez d’interroger le **MS_SAMPLE_EMPLOYEE** table d’interface dans le **bibliothèque d’objets Application**application. Cette table est créée lorsque vous exécutez le script create_apps_artifacts.sql fourni avec les exemples pour créer ces objets dans Oracle E-Business Suite.  
  
 Pour illustrer une opération d’interrogation, nous les opérations suivantes :  
  
-   Spécifiez une instruction SELECT pour le **PolledDataAvailableStatement** liaison de propriété pour déterminer où l’interface table interrogés (MS_SAMPLE_EMPLOYEE) comporte des données. Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :  
  
    ```  
    SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     Cela garantit que l’adaptateur s’exécute l’instruction d’interrogation uniquement lorsque la table d’interface MS_SAMPLE_EMPLOYEE a des enregistrements.  
  
-   Spécifiez une instruction SELECT pour le **PollingInput** propriété de liaison. Cette instruction récupère toutes les lignes dans la table d’interface MS_SAMPLE_EMPLOYEE. Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :  
  
    ```  
    SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE  
    ```  
  
    > [!NOTE]
    >  Pour plus d’informations sur la clause FOR UPDATE utilisée dans l’instruction SELECT, consultez [recevoir des messages d’interrogation de données modifiées à partir d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md).  
  
-   Spécifiez une instruction DELETE en tant que partie de la **PostPollStatement** propriété de liaison. Cette instruction supprime toutes les données à partir de la table d’interface MS_SAMPLE_EMPLOYEE. Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :  
  
    ```  
    DELETE FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     Une fois que cela se produit, la prochaine fois que l’instruction spécifiée pour **PollingInput** sera exécutée, elle ne permet pas d’extraire des données.  
  
-   Jusqu'à ce que davantage de données est ajouté à la table d’interface MS_SAMPLE_EMPLOYEE, vous n’obtiendrez pas tous les messages d’interrogation, donc vous devez remplir de nouveau la table d’interface MS_SAMPLE_EMPLOYEE avec nouveaux enregistrements. Vous pouvez le faire en exécutant le script insert_apps_data.sql fourni avec les exemples. Une fois que vous exécutez ce script, l’opération d’interrogation suivante permet d’extraire les nouveaux enregistrements insérés dans la table.  
  
## <a name="consuming-the-polling-request-message"></a>Le message de demande d’interrogation  
 L’adaptateur appelle l’opération d’interrogation sur votre code pour interroger Oracle E-Business Suite. Autrement dit, l’adaptateur envoie un message de demande d’interrogation qui s’affiche sur une forme de canal IInputChannel. Le message de demande d’interrogation contient le jeu de résultats de la requête spécifiée par la **PollingInput** propriété de liaison. Vous pouvez utiliser le message d’interrogation de deux manières :  
  
-   Pour consommer le message à l’aide de la valeur du nœud de diffusion en continu, vous devez appeler la **WriteBodyContents** méthode sur la réponse de message et lui passer une **XmlDictionaryWriter** qui implémente la diffusion en continu de la valeur du nœud.  
  
-   Pour consommer le message à l’aide du nœud de diffusion en continu, vous pouvez appeler **GetReaderAtBodyContents** sur le message de réponse pour obtenir un **XmlReader**.  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 Les exemples de cette rubrique interrogent la table d’interface MS_SAMPLE_EMPLOYEE. Un script pour générer la table est fourni avec les exemples. Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md). Un exemple, **SelectPolling_ChannelModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.  
  
## <a name="receiving-inbound-messages-for-polling-operation-using-the-wcf-channel-model"></a>Réception des Messages entrants pour l’opération d’interrogation à l’aide du modèle de canal WCF  
 Cette section fournit des instructions sur la façon d’écrire une application .NET (modèle de canal) pour recevoir des messages entrants d’interrogation à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
#### <a name="to-receive-polling-messages-from-the-adapter"></a>Pour recevoir des messages de l’interrogation de la carte  
  
1.  Créez un projet Microsoft Visual C#® dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Pour cette rubrique, créez une application console.  
  
2.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleEBS`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, et `System.Runtime.Serialization`.  
  
3.  Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Description`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  Spécifiez l’URI de connexion. Pour plus d’informations sur l’URI de connexion de l’adaptateur, consultez [créer l’URI de connexion Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md).  
  
    ```  
    Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
    ```  
  
5.  Créez une instance de **OracleEBSBinding** et définissez les propriétés de liaison requises pour configurer l’interrogation. Au minimum, vous devez définir le **InboundOperationType**, **PolledDataAvailableStatement**, **PollingInput**, et **PollingAction** propriétés de liaison. Pour plus d’informations sur les propriétés utilisées pour configurer l’interrogation de liaison, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
    binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
    binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
    binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
    ```  
  
6.  Étant donné que vous demandent une table d’interface, vous devez également définir le contexte des applications. Pour plus d’informations sur le contexte de l’application et les propriétés de liaison requises pour le contexte de l’application de paramètre, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
    ```  
    binding.OracleUserName = "<Enter user name here>";  
    binding.OraclePassword = "<Enter password here>";  
    binding.OracleEBSResponsibilityName = "<Enter responsibility here>";  
    ```  
  
7.  Créer une collection de paramètres de liaison et définir les informations d’identification.  
  
    ```  
    ClientCredentials credentials = new ClientCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
  
    BindingParameterCollection bindingParams = new BindingParameterCollection();  
    bindingParams.Add(credentials);  
    ```  
  
8.  Créer un écouteur de canal et l’ouvrir. Vous créez l’écouteur en appelant **BuildChannelListener < IInputChannel\>**  méthode sur le **OracleEBSBinding**.  
  
    ```  
    IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
    listener.Open();  
    ```  
  
9. Obtenir un **IInputChannel** canal en appelant le **AcceptChannel** méthode sur l’écouteur et ouvrez-le.  
  
    ```  
    IInputChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  
  
10. Appeler **réception** sur le canal pour obtenir le message entrant suivant à partir de l’adaptateur.  
  
    ```  
    Message message = channel.Receive();  
    ```  
  
11. Utiliser le jeu de résultats retourné par l’opération entrante. Vous pouvez consommer le message en utilisant un **XmlReader** ou **XmlDictionaryWriter**.  
  
    ```  
    XmlReader reader = message.GetReaderAtBodyContents();  
    ```  
  
12. Fermer le canal lorsque vous avez terminé le traitement de la demande.  
  
    ```  
    channel.Close()  
    ```  
  
    > [!IMPORTANT]
    >  Vous devez fermer le canal une fois que vous avez terminé le traitement de l’opération entrante. Échec de fermer le canal peut affecter le comportement de votre code.  
  
13. Fermer l’écouteur lorsque vous avez terminé la réception de messages de données modifiées.  
  
    ```  
    listener.Close()  
    ```  
  
    > [!IMPORTANT]
    >  Fermeture de l’écouteur ne ferme pas les canaux créés à l’aide de l’écouteur. Vous devez fermer explicitement chaque canal créé à l’aide de l’écouteur.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre une application d’interrogation qui interroge la table d’interface MS_SAMPLE_EMPLOYEE. Le **PollingInput** propriété contient l’instruction select qui lit toutes les données de la table MS_SAMPLE_EMPLOYEE et l’instruction de sondage post supprime toutes les données de la même table. Le message d’interrogation est écrit dans `C:\PollingOutput.xml`.  
  
 Les messages suivants d’interrogation ne contient pas d’enregistrements jusqu'à ce que davantage de données est ajouté à la table d’interface MS_SAMPLE_EMPLOYEE. Vous pouvez le faire en exécutant le script insert_apps_data.sql fourni avec les exemples. Une fois que vous exécutez ce script, l’opération d’interrogation suivante permet d’extraire les nouveaux enregistrements insérés dans la table. La carte continuera d’interroger jusqu'à ce que vous fermez l’hôte de service en appuyant sur \<retourner\>.  
  
```  
using System;  
using Microsoft.Adapters.OracleEBS;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Xml;  
  
namespace SelectPolling_ChannelModel  
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
  
                OracleEBSBinding binding = new OracleEBSBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
                binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
                binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
                binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
                binding.OracleUserName = "<Enter user name here>";  
                binding.OraclePassword = "<Enter password here>";  
                binding.OracleEBSResponsibilityName = "<Enter responsibility here>";  
  
                Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name?");  
  
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
                Console.ReadLine();  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                    Console.ReadLine();  
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
 [Développer des applications d’Oracle E-Business Suite à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)
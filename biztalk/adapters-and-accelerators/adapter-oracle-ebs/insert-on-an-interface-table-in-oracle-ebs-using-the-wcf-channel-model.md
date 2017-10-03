---
title: "Exécuter une opération d’insertion sur une table d’interface dans Oracle E-Business Suite à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a2e5ee3-552b-40a2-aaa6-5391347f1146
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 703b00adeb373fe66c4a96c324f13f9c3c5ec655
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-an-insert-operation-on-an-interface-table-in-oracle-e-business-suite-using-the-wcf-channel-model"></a>Exécuter une opération d’insertion sur une table d’interface dans Oracle E-Business Suite à l’aide du modèle de canal WCF
Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] détecte un ensemble d’opérations Insert, Select, Update et Delete sur les tables d’interface Oracle E-Business Suite. À l’aide de ces opérations, vous pouvez effectuer simple Insert, Select, Update et supprimer les instructions qualifiées par Where clause sur une table d’interface cible. Cette rubrique fournit des instructions sur la façon d’effectuer une opération d’insertion sur une table d’interface à l’aide du modèle de canal WCF.  
  
 Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [opérations sur les Tables d’Interface et les vues de l’Interface](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md). Pour plus d’informations sur la façon d’effectuer des opérations sur Oracle E-Business Suite à l’aide du modèle de canal WCF, consultez [vue d’ensemble du modèle de canal WCF avec l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md).  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 L’exemple de cette rubrique effectue des opérations sur la table d’interface MS_SAMPLE_EMPLOYEE. La table est créée en exécutant le script fourni avec les exemples. Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md). Un exemple, **InsertOperation**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.  
  
## <a name="the-insert-message"></a>Le Message d’insertion  
 Pour effectuer des opérations sur Oracle E-Business Suite à l’aide du modèle de canal WCF, vous devez disposer du message de demande spécifique à l’opération. Le message de demande pour effectuer une opération d’insertion sur la table d’interface MS_SAMPLE_EMPLOYEE ressemble à ceci :  
  
```  
<Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE">  
  <RECORDSET>  
    <InsertRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/APPS/MS_SAMPLE_EMPLOYEE">  
      <EMP_NO>10050</EMP_NO>  
      <NAME>John Smith</NAME>  
      <DESIGNATION>Manager</DESIGNATION>  
      <SALARY>500000</SALARY>  
      <JOIN_DATE>1999-05-31</JOIN_DATE>  
    </InsertRecord>  
  </RECORDSET>  
</Insert>  
```  
  
 Ce message de demande insère un enregistrement avec les détails suivants :  
  
```  
Employee Number = 10050  
Name = Tom Smith  
Designation = Manager  
Salary = 500000  
```  
  
 Vous devez copier le message vers un fichier, par exemple, InsertRequest.xml. Ce fichier est utilisé dans cet exemple pour envoyer le message de demande pour Oracle E-Business Suite à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Pour plus d’informations sur le schéma de message pour les opérations sur la table, consultez [des schémas de Message pour Insert, Update, Delete et sélectionnez les opérations](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md).  
  
## <a name="creating-a-wcf-channel-application"></a>Création d’une Application de canal WCF  
 Cette section fournit des instructions sur la création d’une application de canal WCF pour effectuer une opération d’insertion sur la table d’interface MS_SAMPLE_EMPLOYEE.  
  
#### <a name="to-create-a-wcf-channel-application-for-inserting-records-into-the-table"></a>Pour créer une application de canal WCF pour insérer des enregistrements dans la table  
  
1.  Créez un projet Visual c# dans Visual Studio. Pour cette rubrique, créez une application console.  
  
2.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleEBS`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, et `System.Runtime.Serialization`.  
  
3.  Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `Microsoft.ServiceModel.Channels`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  Créer la liaison et le point de terminaison.  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
  
    ```  
  
5.  Étant donné que vous effectuez une opération sur une table d’interface, vous devez définir le contexte d’application. Dans cet exemple, pour définir le contexte d’application, que vous spécifiez la **OracleUserName**, **OraclePassword**, et **OracleEBSResponsibilityName** propriétés de liaison. Pour plus d’informations sur le contexte de l’application, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
6.  Créez et ouvrez la fabrication de canal. Cette application envoie un message de demande pour Oracle E-Business Suite et reçoit une réponse, donc vous devez implémenter l’interface IRequestChannel.  
  
    ```  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    factory.Credentials.UserName.UserName = "<Enter user name here>";  
    factory.Credentials.UserName.Password = "<Enter password here>";  
    factory.Open();  
    ```  
  
7.  Créer et ouvrir le canal.  
  
    ```  
    IRequestChannel channel;  
    try  
    {  
       channel = factory.CreateChannel();  
       channel.Open();  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception :" + ex.Message);  
       throw;  
    }  
    ```  
  
8.  Créer et envoyer le message de demande.  
  
    ```  
    XmlReader readerIn;  
    try  
    {  
       readerIn = XmlReader.Create("InsertRequest.xml");  
       Console.WriteLine("Reader created");  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
    Message messageIn;  
    Message messageOut;  
    try  
    {  
       messageIn = Message.CreateMessage(MessageVersion.Default, "InterfaceTables/Insert/FND/APPS/MS_SAMPLE_EMPLOYEE", readerIn);  
       messageOut = channel.Request(messageIn);  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
  
    ```  
  
     Lors de la création du message de demande, vous devez spécifier l’action du message qui indique l’action que l’adaptateur effectue sur la table d’interface. Pour effectuer une opération d’insertion sur la table MS_SAMPLE_EMPLOYEE, l’action du message est `InterfaceTables/Insert/FND/APPS/MS_SAMPLE_EMPLOYEE`. Pour plus d’informations sur la façon dont vous pouvez déterminer l’action du message pour différentes opérations sur les tables, consultez [des schémas de Message pour Insert, Update, Delete et sélectionnez les opérations](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md).  
  
9. Obtenir le message de réponse.  
  
    ```  
    XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
    XmlDocument doc = new XmlDocument();  
    doc.Load(readerOut);  
    doc.Save("C:\\Response.xml");  
    ```  
  
10. Fermez le message, le canal et la fabrique de canaux.  
  
    ```  
    messageOut.Close();  
    channel.Close();  
    factory.Close();  
    ```  
  
11. créer le projet ; Après avoir généré le projet, vous devez copier le message de demande, InsertRequest.xml, au même emplacement que votre projet exécutable. En règle générale, cet emplacement est \bin\Debug\ sous le répertoire du projet.  
  
12. Exécutez l'application. Le message de réponse, Response.xml, est enregistré dans l’emplacement spécifié dans l’application. Le message de réponse contient le numéro ou les enregistrements insérés et ressemble à ceci :  
  
    ```  
    <InsertResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE">  
      <InsertResult>1</InsertResult>  
    </InsertResponse>  
    ```  
  
     La valeur « 1 » indique qu’un seul enregistrement est inséré dans la table MS_SAMPLE_EMPLOYEE.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications d’Oracle E-Business Suite à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)
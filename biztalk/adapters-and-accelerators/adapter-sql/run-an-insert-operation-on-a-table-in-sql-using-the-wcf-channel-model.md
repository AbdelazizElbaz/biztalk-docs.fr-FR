---
title: "Exécuter une opération Insert sur une Table dans SQL à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3df95d78-3a9c-48c0-81ab-1f3206c5e3f7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7bceb236b660b80c1e46cb0410d799d994516c40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-an-insert-operation-on-a-table-in-sql-using-the-wcf-channel-model"></a>Exécuter une opération Insert sur une Table dans SQL à l’aide du modèle de canal WCF
Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] détecte un ensemble d’opérations de base sur les tables de base de données SQL Server et les vues Insert, Select, Update et Delete. À l’aide de ces opérations, vous pouvez effectuer simple SQL Insert, Select, Update et supprimer les instructions qualifiées par Where clause sur une table ou vue cible. Cette rubrique fournit des instructions sur la façon d’effectuer une opération d’insertion sur une table de base de données SQL Server à l’aide du modèle de canal WCF.  
  
 Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [Insert, Update, Delete et sélectionnez les opérations sur les Tables et vues à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md). Pour plus d’informations sur la façon d’effectuer des opérations sur SQL Server à l’aide du modèle de canal WCF, consultez [vue d’ensemble du modèle de canal WCF avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md).  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 L’exemple de cette rubrique effectue des opérations sur la table Employee. La table Employee est créée en exécutant le script SQL fourni avec les exemples. Pour plus d’informations sur les exemples, consultez [exemples de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md). Un exemple, **EmployeeInsertOp**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.  
  
## <a name="the-insert-message"></a>Le Message d’insertion  
 Pour effectuer des opérations sur la base de données SQL Server à l’aide du modèle de canal WCF, vous devez disposer du message de demande spécifique à l’opération. Pour effectuer une opération d’insertion sur la table Employee dans la base de données SQL Server, le message de demande ressemble à ceci :  
  
```  
<Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
  <Rows>  
    <Employee xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
      <Name>Tom Smith</Name>  
      <Designation>Manager</Designation>  
      <Salary>500000</Salary>  
   </Employee>  
  </Rows>  
</Insert>  
```  
  
 Ce message de demande insère un enregistrement avec les détails suivants :  
  
```  
Name = Tom Smith  
Designation = Manager  
Salary = 500000  
```  
  
 Vous devez copier le message vers un fichier, par exemple, InsertRequest.xml. Ce fichier est utilisé dans cet exemple pour envoyer le message de demande à SQL Server à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Pour plus d’informations sur le schéma de message pour les opérations sur la table, consultez [des schémas de Message pour Insert, Update, Delete et sélectionnez les opérations sur les Tables et vues](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).  
  
## <a name="creating-a-wcf-channel-application"></a>Création d’une Application de canal WCF  
 Cette section fournit des instructions sur la création d’une application de canal WCF pour effectuer une opération d’insertion sur la table Employee.  
  
#### <a name="to-create-a-wcf-channel-application-for-inserting-records-into-the-employee-table"></a>Pour créer une application de canal WCF pour insérer des enregistrements dans la table Employee  
  
1.  Créez un projet Visual c# dans Visual Studio. Pour cette rubrique, créez une application console.  
  
2.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, et `System.Runtime.Serialization`.  
  
3.  Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :  
  
    -   `Microsoft.Adapters.Sql`  
  
    -   `Microsoft.ServiceModel.Channels`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  Créer la liaison et le point de terminaison.  
  
    ```  
    SqlAdapterBinding binding = new SqlAdapterBinding();  
    EndpointAddress address = new EndpointAddress("mssql://mysqlserver//mydatabase?");  
  
    ```  
  
5.  Créez et ouvrez la fabrication de canal. Cette application envoie un message de demande à SQL Server et qu’il reçoit une réponse, donc vous devez implémenter l’interface IRequestChannel.  
  
    ```  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    factory.Credentials.UserName.UserName = "<Enter user name here>";  
    factory.Credentials.UserName.Password = "<Enter password here>";  
    factory.Open();  
    ```  
  
6.  Créer et ouvrir le canal.  
  
    ```  
    IRequestChannel channel = factory.CreateChannel();  
    channel.Open();  
    ```  
  
7.  Créer et envoyer le message de demande.  
  
    ```  
    XmlReader readerIn;  
    Console.WriteLine("Creating the message");  
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
    Message messageIn = Message.CreateMessage(MessageVersion.Default, "TableOp/Insert/dbo/Employee", readerIn);  
    Message messageOut = channel.Request(messageIn);  
  
    ```  
  
     Lors de la création du message de demande, vous devez spécifier l’action du message qui indique l’action que l’adaptateur effectue sur la table SQL Server. Pour effectuer une opération d’insertion sur la table Employee, l’action du message est `TableOp/Insert/dbo/Employee`. Pour plus d’informations sur la façon dont vous pouvez déterminer l’action du message pour différentes opérations sur les tables, consultez [des schémas de Message pour Insert, Update, Delete et sélectionnez les opérations sur les Tables et vues](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).  
  
8.  Obtenir le message de réponse.  
  
    ```  
    XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
    XmlDocument doc = new XmlDocument();  
    doc.Load(readerOut);  
    doc.Save("C:\\Response.xml");  
    ```  
  
9. Fermez le message, le canal et la fabrique de canaux.  
  
    ```  
    messageOut.Close();  
    channel.Close();  
    factory.Close();  
    ```  
  
10. créer le projet ; Après avoir généré le projet, vous devez effectuer les tâches suivantes :  
  
    -   Copiez le message de demande, InsertRequest.xml, au même emplacement que votre projet exécutable. En règle générale, cet emplacement est \bin\Debug\ sous le répertoire du projet.  
  
    -   Le tableau « Employee » utilisé dans cet exemple comporte une colonne de type de Point défini par l’utilisateur (UDT). Par conséquent, avant d’exécuter le projet, vous devez créer l’assembly de l’UDT Point comme décrit dans [Creating Types](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types). Vous devez également copier la DLL dans le même emplacement que le projet exécutable d’assembly. En règle générale, cet emplacement est \bin\Debug\ sous le répertoire du projet.  
  
11. Exécutez l'application. Le message de réponse, Response.xml, est enregistré dans l’emplacement spécifié dans l’application. Le message de réponse contient l’ID de l’employé et ressemble à ceci :  
  
    ```  
    <InsertResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
      <InsertResult>  
        <long xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">10006</long>  
      </InsertResult>  
    </InsertResponse>  
    ```  
  
     Étant donné que la table Employee comporte la colonne Employee_ID en tant que la colonne d’identité, l’opération d’insertion retourne la valeur de la colonne d’identité de l’enregistrement qui vient d’être inséré. Si elle n’existe aucune colonne d’identité dans une table, la valeur de retour est NULL.  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications SQL à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)
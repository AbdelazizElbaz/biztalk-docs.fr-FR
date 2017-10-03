---
title: "Les opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery dans SQL à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62f166af-b657-491b-b20d-1ae7886f27ce
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f886463e2b38b358e5f6a9da8b7e67aabdc9c3ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="executereader-executescalar-or-executenonquery-operations-in-sql-using-wcf-service-model"></a>Opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery dans SQL à l’aide du modèle de Service WCF
Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expose des opérations SQL Server générique tel que **ExecuteNonQuery**, **ExecuteReader**, et **ExecuteScalar**. Vous pouvez utiliser ces opérations à exécuter n’importe quelle instruction SQL sur une base de données SQL Server. Ces opérations varient en fonction du type de réponse pour l’instruction SQL. Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).  
  
 Cette rubrique montre comment effectuer une **ExecuteReader** à l’aide de l’opération la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à l’aide du modèle de service WCF. Vous pouvez suivre le même ensemble de procédures décrites dans cette rubrique pour effectuer **ExecuteNonQuery** et **ExecuteScalar** operations.  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 L’exemple de cette rubrique utilise le **ExecuteReader** opération à exécuter la ADD_EMP_DETAILS de procédure stockée. Cette procédure stockée ajoute un enregistrement à la table Employee et retourne l’ID d’employé pour l’enregistrement. La procédure stockée de ADD_EMP_DETAILS est créée en exécutant le script SQL fourni avec les exemples. Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md). Un exemple, **Execute_Reader**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le nom du client WCF généré pour l’appel d’opérations génériques (ExecuteNonQuery, ExecuteReader ou ExecuteScalar) en utilisant le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est répertorié dans le tableau suivant.  
  
|Opérations|Nom de Client WCF|  
|----------------|---------------------|  
|ExecuteNonQuery, ExecuteReader ou ExecuteScalar|GenericTableOpClient|  
  
### <a name="method-signature-for-invoking-generic-operations"></a>Signature de méthode pour appeler les opérations génériques  
 Le tableau suivant montre la signature de la méthode exposée pour appeler les opérations génériques.  
  
|Opération|Signature de méthode|  
|---------------|----------------------|  
|ExecuteNonQuery|int ExecuteNonQuery (chaîne de requête)|  
|ExecuteReader|[] De System.Data.DataSet ExecuteReader (chaîne de requête)|  
|ExecuteScalar|chaîne ExecuteScalar(string Query)|  
  
 Par exemple, la signature pour les méthodes d’opération générique est indiquée dans l’extrait de code suivant.  
  
```  
public partial class GenericTableOpClient : System.ServiceModel.ClientBase<GenericTableOp>, GenericTableOp {  
  public int ExecuteNonQuery(string Query);  
  public System.Data.DataSet[] ExecuteReader(string Query);  
  public string ExecuteScalar(string Query);  
}  
```  
  
 Dans cet extrait de code  
  
-   `GenericTableOpClient`est le nom de la classe. Dans cet exemple, vous utilisez cette classe pour créer un client pour appeler l’opération générique, ExecuteReader.  
  
-   `public System.Data.DataSet[] ExecuteReader(string Query)`est la méthode que vous appelez dans cet exemple, pour appeler le ADD_EMP_DETAILS de procédure stockée.  
  
## <a name="creating-a-wcf-client-to-invoke-an-executereader-operation"></a>Création d’un Client WCF pour appeler l’opération ExecuteReader  
 L’ensemble générique des actions requises pour effectuer une opération sur SQL Server à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de canal WCF avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md). Cette section décrit en particulier comment créer un client WCF qui appelle un **ExecuteReader** opération à exécuter la ADD_EMP_DETAILS de procédure stockée. Cette procédure stockée est créée en exécutant le script SQL fourni avec chaque exemple.  
  
#### <a name="to-create-a-wcf-client-to-invoke-executereader-operation"></a>Pour créer un client WCF pour appeler l’opération ExecuteReader  
  
1.  Créez un projet Visual c# dans Visual Studio. Pour cette rubrique, créez une application console.  
  
2.  Générer la classe de client WCF pour le **ExecuteReader** opération générique. Cette opération n’est disponible sous le nœud racine lorsque vous vous connectez à la base de données SQL Server à l’aide du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
    > [!IMPORTANT]
    >  Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.  
  
3.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql` et `Microsoft.ServiceModel.Channels`.  
  
4.  Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.  
  
    ```  
  
            GenericTableOpClient client = new GenericTableOpClient("SqlAdapterBinding_GenericTableOp");  
    client.ClientCredentials.UserName.UserName = "<Enter username here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     Dans cet extrait de code, `GenericTableOpClient` est le client WCF défini dans SqlAdapterBindingClient.cs. Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. `SqlAdapterBinding_GenericTableOp`est le nom de la configuration de point de terminaison de client et est défini dans le fichier app.config. Ce fichier est également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et contient les propriétés de liaison et d’autres paramètres de configuration.  
  
    > [!NOTE]
    >  Dans cet extrait de code, vous utilisez la liaison et l’adresse de point de terminaison à partir du fichier de configuration. Vous pouvez également spécifier explicitement ces valeurs dans votre code. Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer une liaison de Client de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).  
  
5.  Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :  
  
    ```  
    try  
    {  
       Console.WriteLine("Opening Client...");  
       client.Open();  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
    ```  
  
6.  Appeler le **ExecuteReader** opération pour le ADD_EMP_DETAILS de procédure stockée. Avant d’appeler l’opération ExecuteReader, vous devez ajouter le `System.Data` espace de noms à votre code.  
  
    ```  
    string query = "EXEC ADD_EMP_DETAILS 'Tom Smith', 'Manager', 500000";  
    DataSet[] dsArray = client.ExecuteReader(query);  
  
    Console.WriteLine("Invoking the ADD_EMP_DETAILS stored procedure using ExecuteReader");  
    Console.WriteLine("*****************************************************");  
    foreach (DataSet dataSet in dsArray)  
    {  
       foreach (DataTable tab in dsArray[0].Tables)  
       {  
           foreach (DataRow row in tab.Rows)  
           {  
              for (int i = 0; i < tab.Columns.Count; i++)  
              {  
                 Console.WriteLine("The ID for the newly added employee is : " + row[i]);  
              }  
           }  
        }  
    }  
    Console.WriteLine("*****************************************************");  
  
    ```  
  
7.  Fermez le client, comme décrit dans l’extrait de code ci-dessous :  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  Générez le projet et exécutez-le. L’ID de l’employé nouvellement inséré s’affiche sur la console.
---
title: "Les opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery dans Oracle E-Business Suite à l’aide du modèle de service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54c42db1-9a4d-4003-af69-f75ff48b575a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eaffcdc59cd6093feababc8319c1f9f1964a0d05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="executereader-executescalar-or-executenonquery-operations-in-oracle-e-business-suite-using-the-wcf-service-model"></a>Opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery dans Oracle E-Business Suite à l’aide du modèle de service WCF
Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose les opérations génériques tels que **ExecuteNonQuery**, **ExecuteReader**, et **ExecuteScalar**. Vous pouvez utiliser ces opérations à exécuter n’importe quelle instruction dans Oracle E-Business Suite. Ces opérations varient en fonction du type de réponse pour l’instruction. Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).  
  
 Cette rubrique montre comment effectuer une **ExecuteReader** à l’aide de l’opération la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] à l’aide du modèle de service WCF. Vous pouvez suivre le même ensemble de procédures décrites dans cette rubrique pour effectuer **ExecuteNonQuery** et **ExecuteScalar** operations.  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 L’exemple dans cette rubrique effectue une **ExecuteReader** opération à effectuer une opération SELECT sur la table d’interface MS_SAMPLE_EMPLOYEE. La table est créée en exécutant le script fourni avec les exemples. Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md). Un exemple, **ExecuteReader**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le nom du client WCF généré pour l’appel d’opérations génériques (ExecuteNonQuery, ExecuteReader ou ExecuteScalar) en utilisant le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est répertorié dans le tableau suivant.  
  
|Opérations|Nom de Client WCF|  
|----------------|---------------------|  
|ExecuteNonQuery, ExecuteReader ou ExecuteScalar|GenericOperation_Client|  
  
### <a name="method-signature-for-invoking-generic-operations"></a>Signature de méthode pour appeler les opérations génériques  
 Le tableau suivant montre la signature de la méthode exposée pour appeler les opérations génériques.  
  
|Opération|Signature de méthode|  
|---------------|----------------------|  
|ExecuteNonQuery|int ExecuteNonQuery (chaîne de requête, string [] OutputRefCursorNames, out System.Data.DataSet [] OutputRefCursors)|  
|ExecuteReader|System.Data.DataSet ExecuteReader(string Query)|  
|ExecuteScalar|chaîne ExecuteScalar(string Query)|  
  
 Par exemple, la signature pour les méthodes d’opération générique est indiquée dans l’extrait de code suivant.  
  
```  
public partial class GenericOperation_Client : System.ServiceModel.ClientBase<GenericOperation_>, GenericOperation_ {  
  public int ExecuteNonQuery(string Query, string[] OutputRefCursorNames, out System.Data.DataSet[] OutputRefCursors);  
  public System.Data.DataSet ExecuteReader(string Query);  
  public string ExecuteScalar(string Query);  
}  
```  
  
 Dans cet extrait de code  
  
-   `GenericOperation_Client`est le nom de la classe. Cette classe est utilisée pour créer un client pour appeler l’opération générique, ExecuteReader.  
  
-   `public System.Data.DataSet ExecuteReader(string Query)`est la méthode que vous appelez pour exécuter une instruction SELECT sur la table d’interface MS_SAMPLE_EMPLOYEE.  
  
## <a name="creating-a-wcf-client-to-invoke-an-executereader-operation"></a>Création d’un Client WCF pour appeler l’opération ExecuteReader  
 L’ensemble générique des actions requises pour effectuer une opération sur Oracle E-Business Suite à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de service WCF avec l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md). Cette section décrit comment créer un client WCF pour appeler le **ExecuteReader** opération.  
  
#### <a name="to-create-a-wcf-client-to-invoke-executereader-operation"></a>Pour créer un client WCF pour appeler l’opération ExecuteReader  
  
1.  Créez un projet Visual c# dans Visual Studio. Pour cette rubrique, créez une application console.  
  
2.  Générer la classe de client WCF pour le **ExecuteReader** opération générique. Cette opération n’est disponible sous le nœud racine lorsque vous vous connectez à Oracle E-Business Suite en utilisant le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).  
  
    > [!IMPORTANT]
    >  Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.  
  
3.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleEBS` et `Microsoft.ServiceModel.Channels`.  
  
4.  Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
5.  Dans le fichier Program.cs, créez un client, comme décrit dans l’extrait de code ci-dessous.  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs-72-11");  
    GenericOperation_Client client = new GenericOperation_Client(binding, address);  
    ```  
  
     Dans cet extrait de code, `GenericOperation_Client` est le client WCF défini dans OracleEBSBindingClient.cs. Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
    > [!NOTE]
    >  Dans cet extrait de code, vous spécifiez explicitement l’adresse de liaison et le point de terminaison dans votre code d’application. Vous pouvez utiliser ces valeurs à partir du fichier de configuration d’application, app.config, également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer un client de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).  
  
6.  Définir les informations d’identification pour le client.  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
7.  Étant donné que vous effectuez une opération sur une table d’interface, vous devez définir le contexte d’application. Dans cet exemple, pour définir le contexte d’application, que vous spécifiez la **OracleUserName**, **OraclePassword**, et **OracleEBSResponsibilityName** propriétés de liaison. Pour plus d’informations sur le contexte de l’application, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
8.  Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :  
  
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
  
9. Appeler le **ExecuteReader** opération pour effectuer l’opération SELECT sur la table MS_SAMPLE_EMPLOYEE. Avant d’appeler l’opération ExecuteReader, vous devez ajouter le `System.Data` espace de noms à votre code.  
  
    ```  
    string query = "SELECT * FROM MS_SAMPLE_EMPLOYEE";  
    DataSet ds = client.ExecuteReader(query);  
  
    Console.WriteLine("Invoking the SELECT statement using ExecuteReader");  
    Console.WriteLine("*****************************************************");  
    foreach (DataTable tab in ds.Tables)  
    {  
       foreach (DataRow row in tab.Rows)  
       {  
          Console.WriteLine("The details of the employee are: ");  
          for (int i = 0; i < tab.Columns.Count; i++)  
          {  
             Console.WriteLine(row[i]);  
          }  
          Console.WriteLine();  
       }  
    }  
    Console.WriteLine("*****************************************************");  
    Console.ReadLine();  
  
    ```  
  
10. Fermez le client, comme décrit dans l’extrait de code ci-dessous :  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
11. Générez le projet et exécutez-le. Tous les enregistrements dans la table MS_SAMPLE_EMPLOYEE sont affichés sur la console.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications d’Oracle E-Business Suite à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)
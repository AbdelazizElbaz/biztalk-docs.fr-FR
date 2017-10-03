---
title: "Appeler faiblement typée les procédures stockées de SQL à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aaf74a40-4c03-4a4a-9b91-c21babe154fa
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ec0b8b8d022b4e96a6df4d7c0d49d8176f6cd1a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-weakly-typed-stored-procedures-in-sql-using-the-wcf-service-model"></a>Appeler faiblement typée les procédures stockées de SQL à l’aide du modèle de Service WCF
Quand vous appelez une procédure répertoriée sous la **procédures** nœud dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], la sortie est sous la forme d’un tableau de jeu de données. Cette rubrique fournit des instructions sur la création d’un client WCF pour appeler une procédure stockée dans SQL Server qui retourne un tableau de jeu de données.  
  
> [!NOTE]
>  Si vous effectuez une opération sur les tables qui possèdent des colonnes de types définis par l’utilisateur, assurez-vous que vous faites référence à [opérations sur les Tables et les vues avec les Types définis par l’utilisateur à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) avant de commencer à développer votre application.  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 L’exemple dans cette rubrique utilise la procédure stockée de GET_EMP_DETAILS. Cette procédure stockée accepte un ID d’employé comme paramètre d’entrée et retourne toutes les colonnes correspondantes de l’employé avec cet ID. La procédure stockée de GET_EMP_DETAILS est créée en exécutant le script SQL fourni avec les exemples. Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md). Un exemple, **Execute_StoredProc**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le nom du client WCF généré pour l’appel de procédures stockées sous la **procédures** nœud à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est répertorié dans le tableau suivant.  
  
|Objet de base de données SQL Server|Nom de Client WCF|  
|----------------------------------|---------------------|  
|Procédure (sous la **procédures** nœud)|Procedures_ [schéma] Client|  
  
 [schéma] est le schéma auquel appartient la procédure ; par exemple, « dbo ».  
  
### <a name="method-signature-for-invoking-stored-procedures"></a>Signature de méthode pour appeler des procédures stockées  
 Le tableau suivant montre la signature de la méthode exposée pour appeler les procédures stockées.  
  
|Opération|Signature de méthode|  
|---------------|----------------------|  
|Nom de la procédure|[] De System.Data.DataSet [nom_procédure] (param1, param2,...\)|  
  
 [nom_procédure] est le nom de la procédure ; par exemple GET_EMP_DETAILS  
  
 Par exemple, la signature de la méthode à appeler la procédure GET_EMP_DETAILS est indiquée dans l’extrait de code suivant.  
  
```  
public partial class Procedures_dboClient : System.ServiceModel.ClientBase<Procedures_dbo>, Procedures_dbo {  
  public System.Data.DataSet[] GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue);  
}  
```  
  
 Dans cet extrait de code  
  
-   `Procedures_dboClient`est le nom de la classe de client WCF. Dans cet exemple, vous utilisez cette classe pour créer un client pour appeler la procédure stockée.  
  
-   `public System.Data.DataSet[] GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue)`est la méthode que vous appelez dans cet exemple montre comment appeler la procédure stockée. Cette procédure stockée accepte un ID d’employé et retourne un tableau de jeu de données.  
  
## <a name="create-a-wcf-client-to-invoke-a-stored-procedure-in-sql-server"></a>Créer un Client WCF pour appeler une procédure stockée dans SQL Server  
 L’ensemble générique des actions requises pour effectuer une opération sur SQL Server à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de Service WCF avec l’adaptateur](overview-of-the-wcf-service-model-with-the-sql-adapter.md). Cette section décrit en particulier comment créer un client WCF qui appelle une procédure stockée, le jeu de résultats pour ce qui est un tableau de jeu de données. Dans cette rubrique, par exemple, vous appelez la procédure stockée de GET_EMP_DETAILS. Cette procédure stockée est créée en exécutant le script SQL fourni avec chaque exemple.  
  
  
1.  Créez un projet Visual c# dans Visual Studio. Pour cette rubrique, créez une application console.  
  
2.  Générer la classe de client WCF pour la procédure stockée de GET_EMP_DETAILS. Veillez à sélectionner la procédure sous le **procédures** nœud. Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
    > [!IMPORTANT]
    >  Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.  
  
3.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql` et `Microsoft.ServiceModel.Channels`.  
  
4.  Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.  
  
    ```  
  
              Procedures_dboClient client = new Procedures_dboClient("SqlAdapterBinding_Procedures_dbo");  
  
    client.ClientCredentials.UserName.UserName = "<Enter username here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     Dans cet extrait de code, `Procedures_dboClient` est le client WCF défini dans SqlAdapterBindingClient.cs. Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. `SqlAdapterBinding_Procedures_dbo`est le nom de la configuration de point de terminaison de client et est défini dans le fichier app.config. Ce fichier est également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et contient les propriétés de liaison et d’autres paramètres de configuration.  
  
    > [!NOTE]
    >  Dans cet extrait de code, vous utilisez la liaison et l’adresse de point de terminaison à partir du fichier de configuration. Vous pouvez également spécifier explicitement ces valeurs dans votre code. Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer une liaison de Client de l’adaptateur SQL](configure-a-client-binding-for-the-sql-adapter.md).  
  
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
  
6.  Appelez la procédure stockée de GET_EMP_DETAILS. Avant d’appeler la procédure GET_EMP_DETAILS, vous devez ajouter le `System.Data` espace de noms à votre code.  
  
    ```  
    DataSet[] dataArray;  
    int returnCode;  
  
    try  
    {  
       Console.WriteLine("Calling a stored procedure...");  
       dataArray = client.GET_EMP_DETAILS(10001, out returnCode);  //Invoke the stored procedure  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
    Console.WriteLine("The details for the employee with ID '10001' are:");  
    Console.WriteLine("*************************************************");  
  
    foreach (DataSet dataSet in dataArray)  
    {  
       foreach (DataTable tab in dataArray[0].Tables)  
       {  
          foreach (DataRow row in tab.Rows)  
          {  
             for (int i = 0; i < tab.Columns.Count; i++)  
             {  
                Console.WriteLine(row[i]);  
             }  
          }  
       }  
    }  
    Console.WriteLine("*************************************************");  
  
    ```  
  
7.  Fermez le client, comme décrit dans l’extrait de code ci-dessous :  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  Générez le projet et exécutez-le. Les détails de l’employé, pour le pr vous
9.  ovided l’ID, sont affichés dans la console.  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications à l’aide du modèle de Service WCF](develop-sql-applications-using-the-wcf-service-model.md)
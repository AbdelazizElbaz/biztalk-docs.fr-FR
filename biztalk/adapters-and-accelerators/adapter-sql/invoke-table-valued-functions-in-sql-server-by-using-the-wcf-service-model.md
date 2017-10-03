---
title: "Appeler des fonctions table dans SQL Server à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48688bcc-36b4-4cc1-b078-17e7a5e1cf8c
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a736a82e57f71568f8718a6e4d41e7b649004120
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-table-valued-functions-in-sql-server-by-using-the-wcf-service-model"></a>Appeler des fonctions table dans SQL Server à l’aide du modèle de Service WCF
Vous pouvez utiliser la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] dans une application .NET à l’aide du modèle de service WCF pour appeler des fonctions table dans SQL Server. L’adaptateur expose les fonctions table en tant que méthodes pouvant être appelées directement sur le serveur SQL Server. Pour plus d’informations sur la façon dont l’adaptateur prend en charge les fonctions scalaires, consultez [Execute Table-Valued des fonctions dans SQL Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/execute-table-valued-functions-in-sql-server-using-the-sql-adapter.md).  
  
 Cette rubrique montre comment appeler la fonction TVF_EMPLOYEE dans une base de données SQL Server. La fonction TVF_EMPLOYEE prend la désignation d’un employé dans le **employé** de table et retourne l’enregistrement de l’employé. La fonction TVF_EMPLOYEE et **employé** table sont créées en exécutant le script SQL fourni avec les exemples. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 L’exemple de cette rubrique a appelé la fonction table TVF_EMPLOYEE sur le **employé** table. Fonction TVF_EMPLOYEE et **employé** table sont créées en exécutant le script SQL fourni avec les exemples. Un exemple, **TableFunction_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le nom du client WCF généré pour l’appel de la fonction scalaire dans SQL Server à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est répertorié dans le tableau suivant.  
  
|Objet de base de données SQL Server|Nom de Client WCF|  
|----------------------------------|---------------------|  
|Fonction table|Client de TableValuedFunctions_ [schéma]|  
  
 [Schéma] = des artefacts de la Collection de SQL Server ; par exemple, dbo.  
  
### <a name="method-signature-for-invoking-table-valued-functions"></a>Signature de méthode pour appeler des fonctions table  
 Le tableau suivant montre les signatures de méthode pour les opérations de base sur une table. Les signatures sont identiques pour une vue, à ceci près que le nom et l’espace de noms de vue remplacent ceux de la table.  
  
|Opération|Signature de méthode|  
|---------------|----------------------|  
|Nom de la fonction table|public [NAMESPACE] [nom_fonction] [,] [nom_fonction] (param1, param2,...\)|  
  
 [Espace de noms] = l’espace de noms, par exemple, schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE  
  
 [Nom_fonction] = nom de la fonction table.  
  
 Par exemple, le code suivant illustre les signatures de méthode pour une classe de client WCF généré pour le **TVF_EMPLOYEE** des fonctions scalaires, dans le schéma dbo, qui prend la désignation de l’employé en tant que paramètre et retourne l’employé enregistrement.  
  
```  
public partial class TableValuedFunctions_dboClient : System.ServiceModel.ClientBase<TableValuedFunctions_dbo>, TableValuedFunctions_dbo {      
    public schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE[] TVF_EMPLOYEE(string emp_desig);  
}  
```  
  
 Dans cet extrait de code, **TableValuedFunctions_dboClient** est le nom de la classe WCF dans le SqlAdapterBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
### <a name="parameters-for-invoking-table-valued-functions"></a>Paramètres pour l’appel de fonctions table  
 Les paramètres pour les méthodes exposées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour appeler une fonction table sont les mêmes que les paramètres définis dans la définition de fonction dans SQL Server. Par exemple, le paramètre pour l’appel de la fonction table TVF_EMPLOYEE est emp_desig et prend la désignation d’un employé.  
  
 Là encore, la valeur de retour pour une fonction table est identique à la valeur de retour définie dans la définition de fonction dans SQL Server. Par exemple, la valeur de retour pour la fonction TVF_EMPLOYEE est un tableau d’enregistrements de type schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE [].  
  
## <a name="creating-a-wcf-client-to-invoke-table-valued-functions"></a>Création d’un Client WCF pour appeler des fonctions table  
 L’ensemble générique des actions requises pour effectuer une opération sur SQL Server à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de Service WCF avec l’adaptateur SQL](overview-of-the-wcf-service-model-with-the-sql-adapter.md). Cette section décrit comment créer un client WCF pour appeler le **TVF_EMPLOYEE** fonction table.  
  
 
1.  Créez un projet Visual c# dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsVStudioNoVersion-md.md)]. Pour cette rubrique, créez une application console.  
  
2.  Générer la classe de client WCF pour le **TVF_EMPLOYEE** fonction scalaire. Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
3.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql` et `Microsoft.ServiceModel.Channels`.  
  
4.  Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.  
  
    ```  
  
              TableValuedFunctions_dboClient client = new TableValuedFunctions_dboClient("SqlAdapterBinding_TableValuedFunctions_dbo");  
    client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     Dans cet extrait de code, `TableValuedFunctions_dboClient` est le client WCF défini dans SqlAdapterBindingClient.cs. Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. `SqlAdapterBinding_TableValuedFunctions_dbo`est le nom de la configuration de point de terminaison de client et est défini dans le fichier app.config. Ce fichier est également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et contient les propriétés de liaison et d’autres paramètres de configuration.  
  
    > [!NOTE]
    >  Dans cet extrait de code, vous utilisez la liaison et l’adresse de point de terminaison à partir du fichier de configuration. Vous pouvez également spécifier explicitement ces valeurs dans votre code. Pour plus d’informations sur les différentes façons de spécifier puis liaison du client, consultez [configurer une liaison de Client de l’adaptateur SQL](configure-a-client-binding-for-the-sql-adapter.md).  
  
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
  
6.  Appeler le **TVF_EMPLOYEE** fonction pour récupérer tous les enregistrements de l’employé ayant la désignation « Manager ».  
  
    ```  
    Console.WriteLine("Invoking the TVF_EMPLOYEE function");  
    schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE[] emp_details;  
    string emp_designation = "Manager";  
  
    try  
    {  
        emp_details = client.TVF_EMPLOYEE(emp_designation);  
    }  
    catch (Exception e)  
    {  
        Console.WriteLine("Exception: " + e.Message);  
        throw;  
    }  
    Console.WriteLine("The details for the employee with the 'Manager' designation are:");  
    Console.WriteLine("*******************************************************************");  
    for (int i = 0; i < emp_details.Length; i++)  
    {  
        Console.WriteLine("Employee ID        : " + emp_details[i].Employee_ID);  
        Console.WriteLine("Employee Name      : " + emp_details[i].Name);  
        Console.WriteLine("Employee Desigation: " + emp_details[i].Designation);  
        Console.WriteLine("Employee Salary    : " + emp_details[i].Salary);  
        Console.WriteLine();  
    }  
    ```  
  
7.  Fermez le client, comme décrit dans l’extrait de code ci-dessous :  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  Générez le projet et exécutez-le. L’application affiche l’ID d’employé, le nom et le salaire de tous les employés avec une désignation « Manager ».  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications à l’aide du modèle de Service WCF](develop-sql-applications-using-the-wcf-service-model.md)
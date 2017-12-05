---
title: "Appeler des fonctions scalaires dans SQL Server à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a331e275-3c81-41a8-9ba1-3a801ebc259a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a04904f1170644498d49670104a842b4c8f9dd2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-scalar-functions-in-sql-server-by-using-the-wcf-service-model"></a>Appeler des fonctions scalaires dans SQL Server à l’aide du modèle de Service WCF
Vous pouvez utiliser la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] dans une application .NET à l’aide du modèle de service WCF pour appeler les fonctions scalaires dans SQL Server. L’adaptateur expose les fonctions scalaires en tant que méthodes pouvant être appelées directement sur le serveur SQL Server. Pour plus d’informations sur la façon dont l’adaptateur prend en charge les fonctions scalaires, consultez [exécuter les fonctions scalaires dans SQL Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/execute-scalar-functions-in-sql-server-using-the-sql-adapter.md).  
  
## <a name="how-this-topic-demonstrates-invoking-scalar-functions-using-the-wcf-service-model"></a>Comment cette rubrique illustre l’appel de fonctions scalaires à l’aide du modèle de Service WCF  
 Cette rubrique montre comment appeler la fonction GET_EMP_ID dans une base de données SQL Server. La fonction GET_EMP_ID prend la désignation d’un employé dans le **employé** de table et retourne l’ID d’employé correspondant. La fonction GET_EMP_ID et **employé** table sont créées en exécutant le script SQL fourni avec les exemples. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 L’exemple de cette rubrique appelé la fonction scalaire GET_EMP_ID sur la table Employee. La fonction GET_EMP_ID et **employé** table sont créées en exécutant le script SQL fourni avec les exemples. Un exemple, **ScalarFunction_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le nom du client WCF généré pour l’appel de la fonction scalaire dans SQL Server à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est répertorié dans le tableau suivant.  
  
|Objet de base de données SQL Server|Nom de Client WCF|  
|----------------------------------|---------------------|  
|Fonction scalaire|Client de ScalarFunctions_ [schéma]|  
  
 [Schéma] = des artefacts de la Collection de SQL Server ; par exemple, dbo.  
  
### <a name="method-signature-for-invoking-scalar-functions"></a>Signature de méthode d’appel de fonctions scalaires  
 Le tableau suivant montre les signatures de méthode pour les opérations de base sur une table. Les signatures sont identiques pour une vue, à ceci près que le nom et l’espace de noms de vue remplacent ceux de la table.  
  
|Opération|Signature de méthode|  
|---------------|----------------------|  
|Nom de la fonction scalaire|public *< return_type >**< scalar_function_name >*(param1, param2,...)|  
  
 \<*retrun_type* \> = type de retour définie dans la définition de fonction  
  
 \<*scalar_function_name* \> = nom de la fonction scalaire.  
  
 Par exemple, le code suivant illustre les signatures de méthode pour une classe de client WCF généré pour le **GET_EMP_ID** des fonctions scalaires, dans le schéma dbo, qui prend la désignation de l’employé en tant que paramètre et retourne un employé ID () (entier).  
  
```  
public partial class ScalarFunctions_dboClient : System.ServiceModel.ClientBase<ScalarFunctions_dbo>, ScalarFunctions_dbo {      
    public System.Nullable<int> GET_EMP_ID(string emp_desig);  
}  
```  
  
 Dans cet extrait de code, **ScalarFunctions_dboClient** est le nom de la classe WCF dans le SqlAdapterBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
### <a name="parameters-for-invoking-scalar-functions"></a>Paramètres pour l’appel de fonctions scalaires  
 Les paramètres pour les méthodes exposées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour appeler une valeur scalaire (fonction) sont les mêmes que les paramètres définis dans la définition de fonction scalaire dans SQL Server. Par exemple, le paramètre pour l’appel de la fonction scalaire GET_EMP_ID est emp_desig et prend la désignation d’un employé.  
  
 Là encore, la valeur de retour pour une fonction scalaire est identique à la valeur de retour définie dans la définition de fonction scalaire dans SQL Server. Par exemple, la valeur de retour pour la fonction GET_EMP_ID est ID d’un employé de type entier.  
  
## <a name="creating-a-wcf-client-to-invoke-scalar-functions"></a>Création d’un Client WCF pour appeler des fonctions scalaires  
 L’ensemble générique des actions requises pour effectuer une opération sur SQL Server à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de Service WCF avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md). Cette section décrit comment créer un client WCF pour appeler le **GET_EMP_ID** fonction scalaire.  
  
#### <a name="to-create-a-wcf-client"></a>Pour créer un client WCF  
  
1.  Créez un projet Visual c# dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Pour cette rubrique, créez une application console.  
  
2.  Générer la classe de client WCF pour le **GET_EMP_ID** fonction scalaire. Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
3.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql` et `Microsoft.ServiceModel.Channels`.  
  
4.  Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.  
  
    ```  
  
              ScalarFunctions_dboClient client = new ScalarFunctions_dboClient("SqlAdapterBinding_ScalarFunctions_dbo");  
    client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     Dans cet extrait de code, `ScalarFunctions_dboClient` est le client WCF défini dans SqlAdapterBindingClient.cs. Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. `SqlAdapterBinding_ScalarFunctions_dbo`est le nom de la configuration de point de terminaison de client et est défini dans le fichier app.config. Ce fichier est également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et contient les propriétés de liaison et d’autres paramètres de configuration.  
  
    > [!NOTE]
    >  Dans cet extrait de code, vous utilisez la liaison et l’adresse de point de terminaison à partir du fichier de configuration. Vous pouvez également spécifier explicitement ces valeurs dans votre code. Pour plus d’informations sur les différentes façons de spécifier puis liaison du client, consultez [configurer une liaison de Client de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).  
  
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
  
6.  Appeler le **GET_EMP_ID** fonction pour extraire l’ID d’un employé avec la désignation en tant que « Manager ».  
  
    ```  
    Console.WriteLine("Invoking the GET_EMP_ID function");  
    string emp_designation = "Manager";  
    try  
    {  
          System.Nullable<int> emp_id = client.GET_EMP_ID(emp_designation);  
          Console.WriteLine("The Employee ID for the employee with 'Manager' designation is:" + emp_id);  
    }  
    catch (Exception e)  
    {  
          Console.WriteLine("Exception: " + e.Message);  
          throw;  
    }  
    ```  
  
    > [!NOTE]
    >  Par souci de simplicité, le **employé** table possède un seul employé avec la désignation de « Manager ». Si la table cible a plusieurs employés avec la désignation de même, vous devez définir la fonction en conséquence.  
  
7.  Fermez le client, comme décrit dans l’extrait de code ci-dessous :  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  Générez le projet et exécutez-le. L’application affiche l’ID de l’employé avec la désignation de « Manager ».  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications en utilisant le modèle de service WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)
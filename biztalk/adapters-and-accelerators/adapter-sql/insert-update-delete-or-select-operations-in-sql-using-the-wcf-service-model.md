---
title: Insérer, mettre à jour, supprimer ou sélectionner des opérations dans SQL à l’aide du modèle de service WCF | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340048ad-ce28-4acf-ae4e-f18bdb3b6f47
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2bc522a1b0b60a9ba0b8407228dd1db65c4e6f0
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="insert-update-delete-or-select-operations-in-sql-using-the-wcf-service-model"></a>Insérer, mettre à jour, supprimer ou sélectionner des opérations dans SQL à l’aide du modèle de service WCF
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] détecte un ensemble d’opérations de base sur les tables de base de données SQL Server et les vues Insert, Select, Update et Delete. À l’aide de ces opérations, vous pouvez effectuer simple SQL Insert, Select, Update et supprimer les instructions qualifiées par Where clause sur une table ou vue cible. Cette rubrique fournit des instructions sur la façon d’effectuer ces opérations à l’aide du modèle de service WCF.  
  
 Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [Insert, Update, Delete et sélectionnez les opérations sur les Tables et vues à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md).  
  
> [!NOTE]
>  Si vous effectuez une opération sur les tables qui possèdent des colonnes de types définis par l’utilisateur, assurez-vous que vous faites référence à [opérations sur les Tables et les vues avec les Types définis par l’utilisateur à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) avant de commencer à développer votre application.  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 L’exemple de cette rubrique effectue des opérations sur la table Employee. La table Employee est créée en exécutant le script SQL fourni avec les exemples. Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md). Un exemple, **EmployeeBasicOps**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le nom du client WCF généré pour les opérations SQL de base qui le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] détecte est basé sur le nom de la table ou vue, comme indiqué dans le tableau suivant.  
  
|Objet de base de données SQL Server|Nom de Client WCF|  
|----------------------------------|---------------------|  
|Table|TableOp_[Schema]_[TABLE_NAME]Client|  
|Affichage|ViewOp_[Schema]_[VIEW_NAME]Client|  
  
 [Schéma] = des artefacts de la Collection de SQL Server ; par exemple, dbo.  
  
 [Nom_table] = nom de la table ; par exemple, les employés.  
  
 [VIEW_NAME] = le nom de la vue ; par exemple, Employee_View.  
  
### <a name="method-signature-for-invoking-operations-on-tables"></a>Signature de méthode pour appeler des opérations sur les Tables  
 Le tableau suivant montre les signatures de méthode pour les opérations de base sur une table. Les signatures sont identiques pour une vue, à ceci près que le nom et l’espace de noms de vue remplacent ceux de la table.  
  
|Opération|Signature de méthode|  
|---------------|----------------------|  
|Insert|long[] Insert([TABLE_NS].[TABLE_NAME][] Rows);|  
|Select|[TABLE_NS]. [NOM_TABLE] [] Sélectionnez (chaîne, chaîne de requête les colonnes) ;|  
|Update|int Update([TABLE_NS].[TABLE_NAME].RowPair[] Rows);|  
|Supprimer|int Delete([TABLE_NS].[TABLE_NAME][] Rows);|  
  
 [TABLE_NS] = le nom de l’espace de noms de table ; par exemple, schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee.  
  
 [Nom_table] = nom de la table ; par exemple, les employés.  
  
 Par exemple, le code suivant montre les signatures de méthode pour une classe de client WCF généré pour les opérations Delete, Insert, Select et Update sur la table Employee sous le schéma par défaut « dbo ».  
  
```  
public partial class TableOp_dbo_EmployeeClient : System.ServiceModel.ClientBase<TableOp_dbo_Employee>, TableOp_dbo_Employee {      
    public int Delete(schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] Rows);  
  
    public long[] Insert(schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] Rows);  
  
    public schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] Select(string Columns, string Query);  
  
    public int Update(schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair[] Rows);  
}  
```  
  
 Dans cet extrait de code, TableOp_dbo_EmployeeClient est le nom de la classe WCF dans le SqlAdapterBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
### <a name="parameters-for-table-operations"></a>Paramètres pour les opérations de Table  
 Cette section fournit les paramètres requis par chaque opération de table  
  
 **Opération d’insertion**  
  
|Insérer le type d’opération|JEU D’ENREGISTREMENTS|  
|---------------------------|---------------|  
|Enregistrement de plusieurs|Collection de INSERTRECORDS doivent être insérés dans la table.|  
  
 L’opération d’insertion, retourne un tableau de type de données Long et stocke les valeurs d’identité de lignes insérées, le cas échéant. Si elle n’existe aucune colonne d’identité dans une table, la valeur de retour est NULL.  
  
 **Sélectionnez l’opération**  
  
|COLUMN_NAMES|QUERY|  
|-------------------|-----------|  
|Une liste délimitée par des virgules de noms de colonnes dans la cible. par exemple, « Employee_ID, désignation ». La liste de colonnes spécifie les colonnes de la cible doit être retournée dans le jeu de résultats. Colonnes non spécifiées dans la liste des colonnes seront fixés à leurs valeurs par défaut de .NET dans le jeu d’enregistrements retourné. Pour les colonnes « nillable », cette valeur est **null**.|Le contenu d’une clause SQL WHERE qui spécifie les lignes de la cible de la requête. par exemple, « désignation = 'Manager' ». Vous pouvez définir ce paramètre **null** renvoie toutes les lignes de la cible.|  
  
 La valeur de retour de l’opération de sélection est un jeu de résultats de fortement typé qui contient les colonnes spécifiées et les lignes à partir de la table ou vue cible.  
  
 **Opération de mise à jour**  
  
|Première ligne de la paire|Deuxième ligne de la paire|  
|---------------------------|----------------------------|  
|Le premier enregistrement de l’enregistrement de paire correspond aux nouvelles valeurs qui doivent être mis à jour, autrement dit, il correspond à la clause SET de l’instruction de mise à jour. Cela peut être définie à l’aide de `RowPair.After`.|Le deuxième enregistrement de la paire d’enregistrement correspond aux anciennes valeurs des lignes, autrement dit, il correspond à la clause WHERE de l’instruction de mise à jour. Cela peut être définie à l’aide de `RowPair.Before`.|  
  
 La valeur de retour de l’opération de mise à jour est de type de données Int32 et indique le nombre de lignes mises à jour.  
  
> [!IMPORTANT]
>  Lors de la spécification de l’enregistrement qui doit être mis à jour, vous devez fournir des valeurs pour toutes les colonnes, même si toutes les valeurs ne sont pas mis à jour. Par exemple, si une ligne possède cinq colonnes et seules 2 colonnes, des mises à jour de l’opération de mise à jour dans le cadre de RowPair.Before, vous devez passer toutes les valeurs de 5 colonne. Toutefois, pour RowPair.After, vous pouvez spécifier uniquement les colonnes qui seront mises à jour.  
  
 **L’opération de suppression**  
  
 L’opération de suppression accepte en tant que tableau d’entrée fortement typé d’enregistrements. La valeur de retour de l’opération de suppression est de type de données Int32 et indique le nombre de lignes supprimées.  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-tables-and-views"></a>Création d’un Client WCF pour appeler des opérations sur les Tables et vues  
 L’ensemble générique des actions requises pour effectuer une opération sur SQL Server à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de Service WCF avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md). Cette section décrit comment créer un client WCF pour appeler base Insert, Select, Update, les opérations de suppression sur une table.  
  
#### <a name="to-create-a-wcf-client-to-perform-operations-on-tables"></a>Pour créer un client WCF pour effectuer des opérations sur les tables  
  
1.  Créez un projet Visual c# dans Visual Studio. Pour cette rubrique, créez une application console.  
  
2.  Générer la classe de client WCF pour l’insertion, de sélectionner, de mise à jour et suppression sur la table Employee. Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
    > [!IMPORTANT]
    >  Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.  
  
3.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql` et `Microsoft.ServiceModel.Channels`.  
  
4.  Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.  
  
    ```  
  
              TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient("SqlAdapterBinding_TableOp_dbo_Employee");  
    client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     Dans cet extrait de code, `TableOp_dbo_EmployeeClient` est le client WCF défini dans SqlAdapterBindingClient.cs. Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. `SqlAdapterBinding_TableOp_dbo_Employee` est le nom de la configuration de point de terminaison de client et est défini dans le fichier app.config. Ce fichier est également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et contient les propriétés de liaison et d’autres paramètres de configuration.  
  
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
  
6.  Appeler l’opération Insert sur la table Employee.  
  
    ```  
    long[] recordsInserted;  
  
    schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] insertRecord =  
    new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[1];  
  
    insertRecord[0] = new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee();  
    insertRecord[0].Name = "John Smith";  
    insertRecord[0].Designation = "Manager";  
    insertRecord[0].Salary = 500000;  
  
    try  
    {  
       Console.WriteLine("Inserting new table entry...");  
       recordsInserted = client.Insert(insertRecord);  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
  
    Console.WriteLine("Record inserted");  
    Console.WriteLine("Press any key to continue ...");  
    Console.ReadLine();  
    ```  
  
     Vous pouvez remplacer l’extrait de code précédent pour exécuter Select, Update ou Delete ainsi les opérations. Vous pouvez également ajouter des extraits de code pour effectuer toutes les opérations dans une application unique. Extraits de code sur la façon d’effectuer ces opérations.  
  
7.  Fermez le client, comme décrit dans l’extrait de code ci-dessous :  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  Générez le projet et exécutez-le. L’application insère un enregistrement dans la table Employee.  
  
###   <a name="select-operation"></a>Sélectionnez l’opération  
 Le code suivant illustre une opération de sélection qui cible la table Employee. L’opération Select sélectionne le dernier enregistrement inséré dans la table. Les enregistrements retournés sont écrites dans la console.  
  
```  
schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] selectRecords;  
  
try  
{  
   Console.WriteLine("Selecting Row...");  
   selectRecords = client.Select("*", "where [Employee_ID] = (select IDENT_CURRENT('Employee'))");  
}  
  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
  
Console.WriteLine("The details of the newly added employee are:");  
Console.WriteLine("********************************************");  
for (int i = 0; i < selectRecords.Length; i++)  
{  
   Console.WriteLine("Employee ID        : " + selectRecords[i].Employee_ID);  
   Console.WriteLine("Employee Name      : " + selectRecords[i].Name);  
   Console.WriteLine("Employee Desigation: " + selectRecords[i].Designation);  
   Console.WriteLine();  
}  
Console.WriteLine("********************************************");  
Console.WriteLine("Press any key to continue ...");  
Console.ReadLine();  
```  
  
###   <a name="update-operation"></a>Opération de mise à jour  
 Le code suivant montre une opération de mise à jour qui cible la table Employee.  
  
```  
int result;  
  
schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair updateRecordPair =  
   new schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair();  
  
schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee updateRecord =   
   new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee();  
  
schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair[] updateArray =  
   new schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair[1];  
  
updateRecord = insertRecord[0];  
updateRecord.Name = "Jeff Smith";  
  
updateRecordPair.After = updateRecord;  
updateRecordPair.Before = selectRecords[0];  
  
updateArray[0] = updateRecordPair;  
  
try  
{  
   Console.WriteLine("Updating the database...");  
   result = client.Update(updateArray);  
}  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
  
Console.WriteLine("Updated Record for {0}", updateRecordPair.Before.Name);  
Console.WriteLine("The new name for the employee is {0}", updateRecordPair.After.Name);  
Console.WriteLine("Press any key to continue ...");  
Console.ReadLine();  
```  
  
###   <a name="delete-operation"></a>Opération de suppression  
 Le code suivant montre une opération de suppression qui cible la table Employee.  
  
```  
int deleteSuccess;  
  
schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] deleteRecords =  
   new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[1];  
  
deleteRecords = client.Select("*", "where [Employee_ID] = (select IDENT_CURRENT('Employee'))");  
  
Console.WriteLine("Following employees will be deleted from the database:");  
for (int i = 0; i < deleteRecords.Length; i++)  
{  
   Console.WriteLine("Name: {0}", deleteRecords[i].Name);  
}  
Console.WriteLine("Press any key to begin deletion...");  
Console.ReadLine();  
  
try  
{  
   Console.WriteLine("Deleting employee record...");  
   deleteSuccess = client.Delete(deleteRecords);  
}  
  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications en utilisant le modèle de service WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)
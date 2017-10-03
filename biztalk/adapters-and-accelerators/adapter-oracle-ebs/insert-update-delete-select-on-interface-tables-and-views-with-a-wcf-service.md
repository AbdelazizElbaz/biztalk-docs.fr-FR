---
title: "Insérer, mettre à jour, supprimer ou sélectionner des opérations sur les tables d’interface et les vues à l’aide du modèle de service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae613c0e-4d9a-4c66-99e4-dd0443f1d495
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fc9e3968b760be10b428e39662ec3d09db490cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="insert-update-delete-or-select-operations-on-interface-tables-and-views-using-the-wcf-service-model"></a>Insérer, mettre à jour, supprimer ou sélectionner des opérations sur les tables d’interface et les vues à l’aide du modèle de service WCF
Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] détecte un ensemble d’opérations de base sur les tables d’interface Insert, Select, Update et Delete. À l’aide de ces opérations, vous pouvez effectuer une simple Insert, Select, Update et supprimer les instructions qualifiées par une clause WHERE sur une table d’interface cible. Cette rubrique fournit des instructions sur la façon d’effectuer ces opérations à l’aide du modèle de service WCF.  
  
> [!NOTE]
>  Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge sélectionner uniquement les opérations sur les vues de l’interface.  
  
 Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [opérations sur les Tables d’Interface et les vues de l’Interface](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md).  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 L’exemple de cette rubrique effectue des opérations sur la table d’interface MS_SAMPLE_EMPLOYEE. La table est créée en exécutant le script fourni avec les exemples. Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md). Un exemple, **Interface_Table_Ops**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le nom du client WCF généré pour les opérations de base qui le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] détecte est basé sur le nom de la table ou vue, comme indiqué dans le tableau suivant.  
  
|Artefact|Nom de Client WCF|  
|--------------|---------------------|  
|Tables d’interface|InterfaceTables_ [nom_application] _ [schéma]\_[nom_table] Client|  
|Vues de l’interface|InterfaceViews_ [nom_application] _ [schéma]\_[VIEW_NAME] Client|  
  
 [Nom_application] = nom réel de l’application Oracle E-Business Suite ; par exemple, trver aide.  
  
 [Schéma] = la Collection d’artefacts ; par exemple, il s’agit d’applications.  
  
 [Nom_table] = nom de la table ; par exemple, MS_SAMPLE_EMPLOYEE.  
  
 [VIEW_NAME] = le nom de la vue ; par exemple, MS_SAMPLE_EMPLOYEE_View.  
  
### <a name="method-signature-for-invoking-operations-on-tables"></a>Signature de méthode pour appeler des opérations sur les Tables  
 Le tableau suivant montre les signatures de méthode pour les opérations de base sur une table. Les signatures sont identiques pour une vue, à ceci près que le nom et l’espace de noms de vue remplacent ceux de la table.  
  
|Opération|Signature de méthode|  
|---------------|----------------------|  
|Insert|chaîne Insert (InsertRecord [] RECORDSET ;)|  
|Select|SelectRecord [] sélectionnez (chaîne les noms de colonne, chaîne de filtre) ;|  
|Update|chaîne de mise à jour (UpdateRecord RECORDSET, chaîne de filtre) ;|  
|DELETE|chaîne Delete (chaîne de filtre) ;|  
  
 Par exemple, le code suivant illustre les signatures de méthode pour une classe de client WCF généré pour la supprimer, insérer, sélectionner et mettre à jour des opérations sur la table d’interface MS_SAMPLE_EMPLOYEE sous le schéma d’applications par défaut.  
  
```  
public partial class InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient : System.ServiceModel.ClientBase<InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE>, InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE {      
    public SelectRecord[] Select(string COLUMN_NAMES, string FILTER);  
  
    public string Insert(InsertRecord[] RECORDSET);  
  
    public string Update(UpdateRecord RECORDSET, string FILTER);  
  
    public string Delete(string FILTER);  
}  
```  
  
 Dans cet extrait de code, **InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient** est le nom de la classe WCF dans le OracleEBSBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
### <a name="parameters-for-table-operations"></a>Paramètres pour les opérations de Table  
 Cette section fournit les paramètres requis par chaque opération de table  
  
 **Sélectionnez l’opération**  
  
|NOMS DE COLONNE|FILTER|  
|-------------------|------------|  
|Une liste délimitée par des virgules de noms de colonnes dans la cible. par exemple, « EMP_NO, désignation ». La liste de colonnes spécifie les colonnes de la cible doit être retournée dans le jeu de résultats. Colonnes non spécifiées dans la liste des colonnes seront fixés à leurs valeurs par défaut de .NET dans le jeu d’enregistrements retourné. Pour les colonnes « nillable », cette valeur est **null**.|Le contenu d’une clause WHERE qui spécifie les lignes de la cible de la requête. par exemple, « désignation = 'Manager' ». Vous pouvez définir ce paramètre **null** renvoie toutes les lignes de la cible.|  
  
 La valeur de retour pour une opération de sélection est un jeu de résultats de fortement typé qui contient les colonnes spécifiées et les lignes.  
  
 **Opération d’insertion**  
  
|Insérer le type d’opération|JEU D’ENREGISTREMENTS|  
|---------------------------|---------------|  
|Enregistrement de plusieurs|Collection de INSERTRECORDS doivent être insérés dans la table.|  
  
 La valeur de retour pour une opération d’insertion est le nombre de lignes insérées.  
  
 **Opération de mise à jour**  
  
|JEU D’ENREGISTREMENTS|FILTER|  
|---------------|------------|  
|Une collection d’enregistrements qui doivent être mis à jour dans la table.|Le contenu d’une clause WHERE qui spécifie les lignes de la cible de la requête. par exemple, « désignation = 'Manager' ». Vous pouvez définir ce paramètre **null** renvoie toutes les lignes de la cible.|  
  
 La valeur de retour pour une opération de mise à jour est le nombre de lignes mises à jour.  
  
 **L’opération de suppression**  
  
 L’opération Delete prend comme entrée une clause WHERE qui spécifie les lignes à supprimer. La valeur de retour pour une opération de suppression est le nombre de lignes supprimées.  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-interface-tables-and-interface-views"></a>Création d’un Client WCF pour appeler des opérations sur les Tables d’Interface et les vues de l’Interface  
 L’ensemble générique des actions requises pour effectuer une opération sur Oracle E-Business Suite à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de canal WCF avec l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md). Cette section décrit comment créer un client WCF pour appeler base Insert, Select, Update, les opérations de suppression sur une table d’interface.  
  
#### <a name="to-create-a-wcf-client-to-perform-operations-on-tables"></a>Pour créer un client WCF pour effectuer des opérations sur les tables  
  
1.  Créez un projet Visual c# dans Visual Studio. Pour cette rubrique, créez une application console.  
  
2.  Générer la classe de client WCF pour Insert, Select, Update et sur la table d’interface MS_SAMPLE_EMPLOYEE l’opération de suppression. Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).  
  
    > [!IMPORTANT]
    >  Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.  
  
3.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleEBS` et `Microsoft.ServiceModel.Channels`.  
  
4.  Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
5.  Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
    InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient client = new InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient(binding, address);  
    ```  
  
     Dans cet extrait de code, `InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient` est le client WCF défini dans OracleEBSBindingClient.cs. Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
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
  
9. Appeler l’opération d’insertion sur la table MS_SAMPLE_EMPLOYEE.  
  
    ```  
    Console.WriteLine("The application will insert a record in the MS_SAMPLE_EMPLOYEE interface table");  
  
    // The date values cannot contain time zone information. Hence, you must use  
    // DateTimeKind.Unspecified to not include the time zone information.  
    DateTime date = new DateTime(DateTime.Now.Ticks, DateTimeKind.Unspecified);  
  
    string result;  
  
    InsertRecord[] recordSet = new InsertRecord[1];  
  
    EMP_NO__COMPLEX_TYPE emp_no = new EMP_NO__COMPLEX_TYPE();  
    emp_no.Value = "10007";  
  
    NAME__COMPLEX_TYPE name = new NAME__COMPLEX_TYPE();  
    name.Value = "John Smith";  
  
    DESIGNATION__COMPLEX_TYPE desig = new DESIGNATION__COMPLEX_TYPE();  
    desig.Value = "Manager";  
  
    SALARY__COMPLEX_TYPE salary = new SALARY__COMPLEX_TYPE();  
    salary.Value = "500000";  
  
    JOIN_DATE__COMPLEX_TYPE doj = new JOIN_DATE__COMPLEX_TYPE();  
    doj.Value = date;  
  
    recordSet[0] = new InsertRecord();  
    recordSet[0].EMP_NO = emp_no;  
    recordSet[0].NAME = name;  
    recordSet[0].DESIGNATION = desig;  
    recordSet[0].SALARY = salary;  
    recordSet[0].JOIN_DATE = doj;  
  
    try  
    {  
       result = client.Insert(recordSet);   
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
  
    Console.WriteLine("Number of records inserted= " + result);  
    Console.WriteLine("Press any key to continue...");  
    Console.ReadLine();  
  
    ```  
  
     Vous pouvez remplacer l’extrait de code précédent pour exécuter Select, Update ou Delete ainsi les opérations. Vous pouvez également ajouter des extraits de code pour effectuer toutes les opérations dans une application unique. Extraits de code sur la façon d’effectuer ces opérations, consultez [sélectionner une opération](#BKMK_Select), [opération de mise à jour](#BKMK_Update), et [opération Delete](#BKMK_Delete) respectivement.  
  
10. Fermez le client, comme décrit dans l’extrait de code ci-dessous :  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
11. Générez le projet et exécutez-le. L’application insère un enregistrement dans la table MS_SAMPLE_EMPLOYEE.  
  
###  <a name="BKMK_Select"></a>Sélectionnez l’opération  
 Le code suivant illustre une opération de sélection qui cible la table d’interface MS_SAMPLE_EMPLOYEE. L’opération Select sélectionne le dernier enregistrement inséré dans la table. L’enregistrement retourné est écrit dans la console.  
  
```  
Console.WriteLine("The application will now select the last inserted record");  
SelectRecord[] selectRecords;  
try  
{  
   selectRecords = client.Select("*", "WHERE EMP_NO LIKE 10007");  
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
   Console.WriteLine("Employee ID         : " + selectRecords[i].EMP_NO);  
   Console.WriteLine("Employee Name       : " + selectRecords[i].NAME);  
   Console.WriteLine("Employee Desigation : " + selectRecords[i].DESIGNATION);  
   Console.WriteLine("Employee Salary     : " + selectRecords[i].SALARY);  
   Console.WriteLine();  
}  
Console.WriteLine("********************************************");  
Console.WriteLine("Press any key to continue ...");  
Console.ReadLine();  
```  
  
###  <a name="BKMK_Update"></a>Opération de mise à jour  
 Le code suivant montre une opération de mise à jour qui cible la table d’interface MS_SAMPLE_EMPLOYEE.  
  
```  
Console.WriteLine("The application will now update the employee name in the newly inserted record");  
string recordsUpdated;  
UpdateRecord updateRecordSet = new UpdateRecord();  
updateRecordSet.NAME = "Tom Smith";  
updateRecordSet.DESIGNATION = "Accountant";  
  
try  
{  
   recordsUpdated = client.Update(updateRecordSet, "WHERE EMP_NO LIKE 10007");  
}  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
  
Console.WriteLine("No of records updated: " + recordsUpdated);  
Console.WriteLine("Press any key to continue...");  
Console.ReadLine();  
```  
  
###  <a name="BKMK_Delete"></a>L’opération de suppression  
 Le code suivant montre une opération de suppression qui cible la table d’interface MS_SAMPLE_EMPLOYEE.  
  
```  
Console.WriteLine("The sample will now delete the record that it first inserted");  
string deletedRecords;  
try  
{  
   deletedRecords = client.Delete("WHERE EMP_NO LIKE 10007");  
}  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
Console.WriteLine("No of records deleted: " + deletedRecords);  
Console.WriteLine("Press any key to exit...");  
Console.ReadLine();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications d’Oracle E-Business Suite à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)
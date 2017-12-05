---
title: "Effectuer des opérations sur les tables avec des types de données de grande taille dans Oracle E-Business Suite à l’aide du modèle de service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93ba3191-d234-424a-b2da-dcf384df4985
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 720da748059d3fe3da376ea42495a2587577f5ee
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="complete-operations-on-tables-with-large-data-types-in-oracle-e-business-suite-using-the-wcf-service-model"></a>Effectuer des opérations sur les tables avec des types de données de grande taille dans Oracle E-Business Suite à l’aide du modèle de service WCF
Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] permet aux clients d’adaptateur effectuer des opérations sur les tables de l’interface et de vues avec les types de données de grande taille telles que les objets BLOB, CLOB, NCLOB et BFILE.  
  
-   Pour les colonnes de type BLOB, CLOB et NCLOB, l’adaptateur permet aux clients de lire ainsi que de mettre à jour des données. L’adaptateur expose Read_\<*LOBColName* \> et en attente_\<*LOBColName* \> operations pour lire et mettre à jour les données respectivement, où \< *LOBColName* \> est le nom de colonne avec le type de données de grande taille. S’il existe plusieurs colonnes avec le type de données de grande taille dans une table d’une interface unique, l’adaptateur expose la plupart lire et mettre à jour des opérations pour cette table d’interface.  
  
-   Pour les colonnes de type BFILE, les clients de l’adaptateur peuvent uniquement lire les données. L’adaptateur expose Read_\<*LOBColName* \> opération lire les données des colonnes de type BFILE. S’il existe plusieurs colonnes avec le type de données de grande taille dans une table d’une interface unique, l’adaptateur expose plusieurs opérations de lecture pour la table d’interface.  
  
 Pour plus d’informations sur ces opérations, consultez [opérations sur les Tables d’Interface, les vues de l’Interface, les Tables et les vues que contiennent LOB des données](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md).  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 L’exemple dans cette rubrique met à jour une colonne BLOB (PHOTO) dans la table de base de données client et puis récupère les données de la même colonne. La table est créée en exécutant le script fourni avec les exemples. Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md). Un exemple, **LargeDataTypes_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.  
  
> [!NOTE]
>  Cette rubrique répertorie les tâches détaillées pour la mise à jour et la lecture des colonnes de types de données de grande taille dans une table de base de données. Vous devez effectuer le même ensemble de tâches de mise à jour et de lire les colonnes de types de données de grande taille dans une table d’interface.  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le nom du client WCF généré pour les opérations sur les tables avec des types de données de grande taille par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est basé sur le nom de la table, comme indiqué dans le tableau suivant.  
  
|Artefact|Nom de Client WCF|  
|--------------|---------------------|  
|Tables d’interface|InterfaceTables_ [nom_application] _ [schéma]\_[nom_table] Client|  
  
 [Nom_application] = nom réel de l’application Oracle E-Business Suite ; par exemple, trver aide.  
  
 [Schéma] = la Collection d’artefacts ; par exemple, il s’agit d’applications.  
  
 [Nom_table] = nom de la table ; par exemple, MS_SAMPLE_EMPLOYEE.  
  
 [VIEW_NAME] = le nom de la vue ; par exemple, MS_SAMPLE_EMPLOYEE_View.  
  
### <a name="method-signature-for-invoking-operations-on-tables"></a>Signature de méthode pour appeler des opérations sur les Tables  
 Le tableau suivant montre les signatures de méthode pour les opérations de base sur une table. Les signatures sont identiques pour une vue, à ceci près que le nom et l’espace de noms de vue remplacent ceux de la table.  
  
|Opération|Signature de méthode|  
|---------------|----------------------|  
|En attente_\<*nom_colonne*\>|public void en attente_\<*column_name*\>(filtre, byte [] données de chaîne) ;|  
|Read_\<*nom_colonne*\>|public System.IO.Stream Read_\<*column_name*\>(filtre de chaîne) ;|  
  
 Par exemple, le code suivant montre les signatures de méthode pour une classe de client WCF généré pour les opérations Update_PHOTO et Read_PHOTO sur la table de base de données client sous le schéma d’applications.  
  
```  
public partial class Tables_APPS_CUSTOMERClient : System.ServiceModel.ClientBase<Tables_APPS_CUSTOMER>, Tables_APPS_CUSTOMER {      
  
    public void Update_PHOTO(string FILTER, byte[] DATA);  
  
    public System.IO.Stream Read_PHOTO(string FILTER);  
}  
```  
  
 Dans cet extrait de code, **Tables_APPS_CUSTOMERClient** est le nom de la classe WCF dans le OracleEBSBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Update_PHOTO et Read_PHOTO sont des méthodes qui peuvent être appelés pour mettre à jour et lire des colonnes de types de données de grande taille dans une table.  
  
### <a name="parameters-for-table-operations"></a>Paramètres pour les opérations de Table  
 Cette section fournit les paramètres requis par l’en attente_\<*column_name* \> et Read_\<*column_name* \> opération.  
  
|Nom de l’opération|Paramètres|  
|--------------------|----------------|  
|En attente_\<*nom_colonne*\>|Requiert les paramètres suivants :<br /><br /> -   `string FILTER`. Ce paramètre doit contenir where clause qui dénote l’enregistrement pour lequel des données est mise à jour. Par exemple, `"WHERE Name='Mindy Martin'"`.<br />-   `byte[] DATA`. Contient un tableau d’octets de données à la mise à jour dans une colonne de type de données de grande taille.|  
|Read_\<*nom_colonne*\>|Requiert les paramètres suivants :<br /><br /> -   `string FILTER`. Ce paramètre doit contenir where clause qui dénote l’enregistrement à partir de laquelle les données doit être lu. Par exemple, `"WHERE Name='Mindy Martin'"`.|  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-tables-with-columns-of-large-data-types"></a>Création d’un Client WCF pour appeler des opérations sur les Tables avec des colonnes de Types de données volumineuses  
 L’ensemble générique des actions requises pour effectuer une opération sur Oracle E-Business Suite à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de service WCF avec l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md). Cette section décrit comment créer un client WCF pour appeler des opérations Update_PHOTO et Read_PHOTO sur une table de base de données client.  
  
#### <a name="to-create-a-wcf-client"></a>Pour créer un client WCF  
  
1.  Créez un projet Visual c# dans Visual Studio. Pour cette rubrique, créez une application console.  
  
2.  Générer la classe de client WCF pour les opérations Update_PHOTO et Read_PHOTO sur la table de base de données client. Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).  
  
    > [!IMPORTANT]
    >  Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.  
  
3.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleEBS` et `Microsoft.ServiceModel.Channels`, `System.Transactions`.  
  
4.  Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
    -   `System.Transactions`  
  
    -   `System.IO`  
  
5.  Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.  
  
    ```  
  
              Tables_APPS_CUSTOMERClient client = new Tables_APPS_CUSTOMERClient("OracleEBSBinding_Tables_APPS_CUSTOMER");  
  
    client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     Dans cet extrait de code, `Tables_APPS_CUSTOMERClient` est le client WCF défini dans OracleEBSBindingClient.cs. Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
    > [!NOTE]
    >  Dans cet extrait de code, vous utilisez la liaison et l’adresse de point de terminaison à partir du fichier de configuration app.config. Vous pouvez également spécifier explicitement ces valeurs dans votre code. Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer un client de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).  
  
6.  Définir les informations d’identification pour le client.  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
    > [!IMPORTANT]
    >  Dans cet exemple, vous effectuez des opérations sur une table de base de données. Toutefois, si vous effectuez des opérations sur une table d’interface, vous devez définir le contexte d’application en spécifiant les valeurs appropriées pour le **OracleUserName**, **OraclePassword**, et  **OracleEBSResponsibilityName** propriétés de liaison. Vous devez spécifier ces propriétés de la liaison avant d’ouvrir le client. Pour plus d’informations sur le contexte de l’application, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
7.  Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :  
  
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
  
8.  Appelez l’opération Update_PHOTO sur la table CUSTOMER.  
  
     L’opération Update_PHOTO requiert un tableau d’octets pour les données à mettre à jour. Dans cet extrait de code, vous utilisez la classe FileStream pour créer un tableau d’octets pour une photo, SamplePhoto.jpg. Pour cette application fonctionne, le fichier doit être copié vers le répertoire bin du projet.  
  
    > [!IMPORTANT]
    >  L’opération Update_PHOTO doit être effectuée dans une transaction, afin que la **UseAmbientTransaction** liaison de la propriété doit être définie sur **true** et l’opération Update_PHOTO doit être effectuée au sein d’un étendue de transaction. Vous pouvez définir le **UseAmbientTransaction** propriété de liaison dans le fichier app.config ou en définissant explicitement dans votre application en tant que `binding.UseAmbientTransaction = true`. Notez que si vous spécifiez la propriété de liaison explicitement dans le code, vous devez le faire avant d’ouvrir le client.  
  
    ```  
    byte[] photo;  
  
    using (FileStream fs = new FileStream("SamplePhoto.jpg", FileMode.Open))  
    {  
        try  
        {  
            Console.WriteLine("Reading the photo");  
            int count = 0;  
            photo = new byte[fs.Length];  
            while ((count += fs.Read(photo, count, (int)(((fs.Length - count) > 4096) ? 4096 : fs.Length - count))) < fs.Length) ;  
        }  
        catch(Exception ex)  
        {  
            Console.WriteLine("Exception: " + ex.Message);  
            throw;  
        }  
    }  
  
    Console.WriteLine("Updating data for the 'PHOTO' column");  
    // Invoking the Update_PHOTO operation inside a transaction scope  
    using (TransactionScope tx = new TransactionScope())  
    {  
        string filter = "WHERE Name='Mindy Martin'";  
        client.Update_PHOTO(filter, photo);  
        tx.Complete();  
    }  
  
    ```  
  
9. Appelez l’opération Read_PHOTO sur la table CUSTOMER.  
  
     Le Read_PHOTO donne le résultat sous la forme de System.IO.Stream. Le client de l’adaptateur doit implémenter la classe FileStream pour lire les données à partir de l’opération de Read_PHOTO. Une fois l’opération Read_PHOTO est terminée, un fichier PhotoCopy.jpg est copié dans le répertoire bin du projet.  
  
    ```  
    using (FileStream fs = new FileStream("PhotoCopy.jpg", FileMode.Create))  
    {  
        Console.WriteLine("Reading photo data");  
        String ReadFilter = "WHERE NAME='Mindy Martin'";  
        Stream photoStream = client.Read_PHOTO(ReadFilter);  
        Console.WriteLine("Photo data read -- writing to PhotoCopy.jpg");  
  
        int count;  
        int length = 0;  
        byte[] buffer = new byte[4096];  
        while ((count = photoStream.Read(buffer, 0, 4096)) > 0)  
        {  
            fs.Write(buffer, 0, count);  
            length+=count;  
        }  
        Console.WriteLine("{0} bytes written to PhotoCopy.jpg", length);  
    }  
  
    Console.WriteLine("Photo updated and read back -- Hit <RETURN> to end");  
    Console.ReadLine();  
    ```  
  
10. Fermez le client, comme décrit dans l’extrait de code ci-dessous :  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
11. Générez le projet et exécutez-le. L’application met à jour la colonne PHOTO de la table CUSTOMER, puis lit le contenu de la colonne PHOTO.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications d’Oracle E-Business Suite à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)
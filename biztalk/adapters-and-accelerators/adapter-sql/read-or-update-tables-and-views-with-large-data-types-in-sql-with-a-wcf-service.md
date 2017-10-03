---
title: "Exécuter des opérations sur les Tables et vues avec des Types de données volumineux dans SQL à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d33e17c-e09e-4a57-9acc-43095e67ed8c
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c673e5c31c0498bb82fe7979d2855765f4c9bf35
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-operations-on-tables-and-views-with-large-data-types-in-sql-using-the-wcf-service-model"></a>Exécuter des opérations sur les Tables et vues avec des Types de données volumineux dans SQL à l’aide du modèle de Service WCF
Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet à des clients de l’adaptateur pour lire et mettre à jour des données dans des colonnes de types de données volumineuses, autrement dit, varchar (max), nvarchar (max) ou varbinary (max). Pour lire des données à partir de ces colonnes, les clients de la carte peuvent utiliser l’opération de sélection. Pour insérer ou mettre à jour des données dans ces colonnes, l’adaptateur expose un ensemble\<*column_name*> opération, où \< *column_name*> est le nom de la colonne de type varchar ( max), nvarchar (max) ou varbinary (max).  
  
 En outre, dans SQL Server, vous pouvez avoir la colonne varbinay(max) stocker des données non structurées, telles que des documents de texte et des images. Ces données non structurées sont appelées données FILESTREAM. Les données FILESTREAM peuvent être stockées en tant que fichiers sur le système de fichiers. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet au client d’entrer des données FILESTREAM dans des colonnes de type varbinary (max). [Stockage FILESTREAM](https://docs.microsoft.com/sql/relational-databases/blob/filestream-sql-server) contient des informations supplémentaires. 
  
 Cette rubrique fournit des informations sur certaines tâches, vous devez effectuer sur l’ordinateur exécutant SQL Server et l’ordinateur exécutant le client de l’adaptateur pour être en mesure d’insérer ou de mettre à jour les données FILESTREAM. Cette rubrique fournit également des instructions sur l’exécution de jeu\<*column_name*> opérations pour insérer des données FILESTREAM.  
  
> [!NOTE]
>  Si vous effectuez une opération sur les tables qui possèdent des colonnes de types définis par l’utilisateur, assurez-vous que vous faites référence à [opérations sur les Tables et les vues avec les Types définis par l’utilisateur à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez effectuer les tâches suivantes sur l’ordinateur exécutant SQL Server et de l’ordinateur exécutant le client de la carte.  
  
-   **Sur l’ordinateur exécutant SQL Server**  
  
    -   Vous devez l’activer sur l’instance de SQL Server. Consultez [activer et configurer FILESTREAM](https://docs.microsoft.com/sql/relational-databases/blob/enable-and-configure-filestream).
  
    -   Vous devez créer une base de données FILESTREAM. Consultez [créer une base de données compatible FILESTREAM](https://docs.microsoft.com/sql/relational-databases/blob/create-a-filestream-enabled-database).
  
    -   Vous devez disposer d’une table pour stocker les données FILESTREAM. Consultez [créer une Table pour stocker des données FILESTREAM](https://docs.microsoft.com/sql/relational-databases/blob/create-a-table-for-storing-filestream-data),
  
-   **Sur l’ordinateur exécutant le client de carte**  
  
    -   Vous devez disposer de la connectivité du Client SQL SDK installé. Vous pouvez installer le SDK de connectivité Client SQL, exécutez le programme d’installation de SQL Server et sélectionnez **SQL Client Connectivity SDK** dans les **sélection des fonctionnalités** page de l’Assistant. L’adaptateur utilise le sqlncli10.dll, installé avec le SDK de connectivité Client SQL, pour effectuer des opérations FILESTREAM.  
  
 Une fois ces tâches terminées, vous sont tous définis pour insérer ou mettre à jour les données FILESTREAM dans les tables de base de données SQL Server.  
  
## <a name="how-this-topic-demonstrates-operations-on-large-data-types"></a>Comment cette rubrique illustre les opérations sur les Types de données de grande taille  
 Pour illustrer comment exécuter ensemble\<*column_name*> opérations sur les tables avec les types de données de grande taille, prenez une table, **enregistrements**, qui a des colonnes **Id** et **Document**:  
  
-   Le **enregistrements** table, toutes les données, est créée en exécutant le script SQL fourni avec les exemples. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
-   Le **Id** la colonne est de type uniqueidentifier et accepte un GUID. Supposons que la **Id** colonne a déjà un GUID '`438B7B4C-5491-409F-BCC1-78817C399EC3`'.  
  
-   Le **Document** colonne est de type varbinary (max). Pour mettre à jour le **Document** expose de colonne, l’adaptateur le **SetDocument** opération.  
  
> [!NOTE]
>  Pour SQL Server, pour illustrer les opérations FILESTREAM, supposons que qui le **Document** colonne peut stocker les données FILESTREAM.  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 L’exemple de cette rubrique effectue des opérations sur le **enregistrements** table. Le **enregistrements** table est créée en exécutant le script SQL fourni avec les exemples. Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md). Un exemple, **Records_FILESTREAM_Op**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le nom du client WCF généré pour les opérations sur les données de grande taille en types qui le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] détecte, est basé sur le nom de la table ou vue, comme indiqué dans le tableau suivant.  
  
|Objet de base de données SQL Server|Nom de Client WCF|  
|----------------------------------|---------------------|  
|Table|TableOp_ [schéma] _ [nom_table] Client|  
|Affichage|ViewOp_ [schéma] _ [VIEW_NAME] Client|  
  
 [Schéma] = des artefacts de la Collection de SQL Server ; par exemple, dbo.  
  
### <a name="method-signature-for-invoking-operations-on-columns-of-large-data-types"></a>Signature de méthode pour appeler des opérations sur les colonnes de Types de données volumineuses  
 Le tableau suivant montre les signatures de méthode pour les opérations de base sur une table. Les signatures sont identiques pour une vue, à ceci près que le nom et l’espace de noms de vue remplacent ceux de la table.  
  
|Opération|Signature de méthode|  
|---------------|----------------------|  
|Définissez\<*nom_colonne*>|public Set void\<*column_name*> (filtre, byte [] données de chaîne) ;|  
  
 \<*column_name*> = nom de la colonne de type de données de grande taille.  
  
 Par exemple, le code suivant illustre les signatures de méthode pour une classe de client WCF généré pour le **SetDocument** opération sur le **enregistrements** table sous le schéma de « dbo » par défaut.  
  
```  
public partial class TableOp_dbo_RecordsClient : System.ServiceModel.ClientBase<TableOp_dbo_Records>, TableOp_dbo_Records {      
    public void SetDocument (string Filter, byte[] Data);  
}  
```  
  
 Dans cet extrait de code, **TableOp_dbo_RecordsClient** est le nom de la classe WCF dans le SqlAdapterBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
### <a name="parameters-for-operations-on-columns-of-large-data-types"></a>Paramètres pour les opérations sur des colonnes de Types de données volumineuses  
 Cette section fournit les paramètres requis par le jeu de\<*column_name*> opération.  
  
|Nom du paramètre| Description|  
|--------------------|-----------------|  
|chaîne de filtre|Spécifie la clause WHERE en fonction sur laquelle l’adaptateur met à jour l’enregistrement de la colonne de type de données de grande taille.|  
|Byte [] données|Spécifie la valeur qui doit être mis à jour pour la colonne de type de données de grande taille.|  
  
 Le jeu de\<*column_name*> opération ne renvoie aucune valeur.  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-columns-of-large-data-types"></a>Création d’un Client WCF pour appeler des opérations sur des colonnes de Types de données volumineuses  
 L’ensemble générique des actions requises pour effectuer une opération sur SQL Server à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de Service WCF avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md). Cette section décrit comment créer un client WCF pour appeler le **SetDocument** opération sur le **enregistrements** table. L’adaptateur expose le **SetDocument** opération pour mettre à jour des données dans des colonnes de types de données volumineuses.  
  
#### <a name="to-create-a-wcf-client"></a>Pour créer un client WCF  
  
1.  Créez un projet Visual c# dans Visual Studio. Pour cette rubrique, créez une application console.  
  
2.  Générer la classe de client WCF pour le **SetDocument** opération sur le **enregistrements** table. Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
3.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, et `System.Transactions`.  
  
4.  Ouvrez le fichier Program.cs et ajoutez le `System.Transactions` espace de noms.  
  
5.  Dans le fichier Program.cs, créez un client, comme décrit dans l’extrait de code ci-dessous.  
  
    ```  
  
              TableOp_dbo_RecordsClient client = new TableOp_dbo_RecordsClient("SqlAdapterBinding_TableOp_dbo_Records");  
    client.ClientCredentials.UserName.UserName = "";  
    client.ClientCredentials.UserName.Password = "";  
  
    ```  
  
     Dans cet extrait de code, `TableOp_dbo_RecordsClient` est le client WCF défini dans SqlAdapterBindingClient.cs. Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. `SqlAdapterBinding_TableOp_dbo_Records`est le nom de la configuration de point de terminaison de client et est défini dans le fichier app.config. Ce fichier est également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et contient les propriétés de liaison et d’autres paramètres de configuration.  
  
    > [!CAUTION]
    >  Pour effectuer des opérations sur les données FILESTREAM, vous devez toujours vous connecter à SQL Server à l’aide de l’authentification Windows. Pour vous connecter à l’aide de l’authentification Windows, vous devez fournir des nom d’utilisateur vide et le mot de passe, comme indiqué dans l’extrait de code précédent. En outre, avant d’utiliser l’authentification Windows pour se connecter à SQL Server, vous devez avoir exécuté les étapes indiquées dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
    > [!NOTE]
    >  Dans cet extrait de code, vous utilisez la liaison et l’adresse de point de terminaison à partir du fichier de configuration. Vous pouvez également spécifier explicitement ces valeurs dans votre code. Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer une liaison de Client de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).  
  
6.  Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :  
  
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
  
7.  Appeler le **SetDocument** opération sur le **enregistrements** table.  
  
    > [!CAUTION]
    >  Le jeu de*< nom_colonne >* opérations doivent toujours être exécutées dans une transaction. Pour garantir cela, le jeu de*< nom_colonne >* opération doit être appelée au sein d’une étendue de transaction et la **UseAmbientTransaction** liaison de la propriété doit être définie sur **true**dans le fichier app.config.  
  
    ```  
    using (TransactionScope tx = new TransactionScope())  
    {  
        string filter = "WHERE Id='438B7B4C-5491-409F-BCC1-78817C399EC3'";  
        byte[] data = ASCIIEncoding.ASCII.GetBytes("Sample data");  
        client.SetDocument(filter, data);  
        tx.Complete();  
    }  
    ```  
  
     Ici, l’application convertit la chaîne « Exemples de données » dans une chaîne codée en base64 et il met à jour dans l’enregistrement qui satisfait aux critères de filtre.  
  
8.  Fermez le client, comme décrit dans l’extrait de code ci-dessous :  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
9. Générez le projet et exécutez-le. Les mises à jour de l’application le **Document** colonne dans la **enregistrements** table.  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)
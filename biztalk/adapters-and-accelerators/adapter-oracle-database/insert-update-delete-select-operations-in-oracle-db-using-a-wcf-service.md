---
title: "Insérer, mettre à jour, supprimer ou sélectionner des opérations dans la base de données Oracle à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, Delete operation
- WCF service model, Select operation
- WCF service model, Insert operation
- WCF service model, Update operation
ms.assetid: d1a9f44f-ea0b-4dd6-9489-fa0d963848c4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f312f0fa967c08fabbc27c9269abaae68b9ac958
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="insert-update-delete-or-select-operations-in-oracle-database-using-the-wcf-service-model"></a>Insérer, mettre à jour, supprimer ou sélectionner des opérations dans la base de données Oracle à l’aide du modèle de Service WCF
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose un ensemble de base Insert, Update, Delete et les opérations Select sur les tables de base de données Oracle et des vues. À l’aide de ces opérations, vous pouvez effectuer de simples sélectionnez SQL INSERT, UPDATE et supprimer les instructions qualifiées par une clause WHERE sur une table ou vue cible. Pour effectuer des opérations plus complexes, par exemple une requête SQL SELECT qui utilise l’opérateur de jointure, vous pouvez utiliser l’opération SQLEXECUTE. Pour plus d’informations sur l’opération SQLEXECUTE, consultez [une opération SQLEXECUTE dans Oracle à l’aide de base de données du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md).  
  
 Le tableau suivant récapitule les opérations SQL de base qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces sur les tables et vues. Pour obtenir une description complète de ces opérations, consultez [des schémas de Message pour la base opérations d’insertion, mise à jour, supprimer et sélectionnez sur les Tables et vues](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).  
  
|Opération| Description|  
|---------------|-----------------|  
|Insert|L’opération d’insertion prend en charge plusieurs des insertions en bloc ou d’enregistrement dans la table ou vue cible :<br /><br /> -Une opération d’insertion plusieurs enregistrement insère des lignes dans une table ou une vue basée sur un jeu d’enregistrements fourni.<br />-Une opération d’insertion en bloc insère des lignes dans une table ou une vue basée sur un SQL SELECT de requêtes et de colonne liste fournie. La requête retourne les enregistrements sont insérés dans la table cible en fonction de la liste des colonnes.|  
|Select|Effectue une requête SQL SELECT sur la table cible selon une liste de noms de colonne et une chaîne de filtrage qui spécifie une clause SQL WHERE fournie.|  
|Update|Effectue une mise à jour sur la table cible. Les enregistrements doivent être mis à jour sont spécifiées par une chaîne de filtrage qui spécifie une clause SQL WHERE. Les valeurs pour la mise à jour sont spécifiées dans un enregistrement du modèle.|  
|DELETE|Effectue une suppression sur la table cible selon une clause SQL WHERE qui est spécifiée dans une chaîne de filtre.|  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 Les exemples de cette rubrique utilisent la table /SCOTT/ACCOUNTACTIVITY. Un script pour générer cette table est fourni avec les exemples du Kit de développement logiciel. Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le nom du client WCF généré pour les opérations SQL de base qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces est basé sur le nom de la table ou vue, comme indiqué dans le tableau suivant.  
  
|Objet de base de données Oracle|Nom de Client WCF|  
|------------------------------|---------------------|  
|Table|[SCHÉMA] Client de la table [nom_table]|  
|Affichage|[SCHÉMA] Client de la vue [VIEW_NAME]|  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [Nom_table] = nom de la table ; par exemple, ACCOUNTACTIVITY.  
  
 [VIEW_NAME] = nom de la vue.  
  
 Le tableau suivant montre les signatures de méthode pour les opérations SQL de base sur une table. Les signatures sont identiques pour une vue, à ceci près que le nom et l’espace de noms de vue remplacent ceux de la table.  
  
|Opération|Signature de méthode|  
|---------------|----------------------|  
|Insert|durée pendant laquelle insérer ([TABLE_NS]. [ Nom_table] RECORDINSERT [] chaîne les noms de colonne, chaîne de requête de jeu d’enregistrements) ;|  
|Select|[TABLE_NS]. [NOM_TABLE] RECORDSELECT [] sélectionnez (chaîne les noms de colonne, chaîne de filtre) ;|  
|Update|durée pendant laquelle mettre à jour ([TABLE_NS]. [ Nom_table] RECORDUPDATE RECORDSET, chaîne de filtre) ;|  
|DELETE|Durée pendant laquelle supprimer (chaîne de filtre) ;|  
  
 [TABLE_NS] = le nom de l’espace de noms de table ; par exemple, microsoft.lobservices.oracledb._2007._03.SCOTT. Table.ACCOUNTACTIVITY.  
  
 [Nom_table] = nom de la table ; par exemple, ACCOUNTACTIVITY.  
  
 Utilisé par les opérations d’insertion, mise à jour et sélectionnez les types d’enregistrements sont tous définis dans la table ou afficher l’espace de noms.  
  
 Le code suivant montre les signatures de méthode pour une classe de client WCF généré de Delete, Insert, Select et de mise à jour sur la table ACCOUNTACTIVITY/SCOTT.  
  
```  
public partial class SCOTTTableACCOUNTACTIVITYClient : System.ServiceModel.ClientBase<SCOTTTableACCOUNTACTIVITY>, SCOTTTableACCOUNTACTIVITY {  
  
    public long Delete(string FILTER);  
  
    public long Insert(microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[] RECORDSET, string COLUMN_NAMES, string QUERY);  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] Select(string COLUMN_NAMES, string FILTER);  
  
    public long Update(microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE RECORDSET, string FILTER);  
}  
```  
  
## <a name="invoking-the-basic-sql-operations"></a>Appeler les opérations SQL de base  
 Pour appeler les opérations SQL de base sur une table ou vue à l’aide d’un client WCF, procédez comme suit.  
  
1.  Générer une classe de client WCF pour la table ou vue cible. Cette classe doit contenir des méthodes pour les opérations que vous appellerez sur l’artefact cible.  
  
2.  Créez une instance de la classe de client WCF et appeler ses méthodes pour effectuer des opérations sur la table ou la vue.  
  
 Pour plus d’informations sur la façon de créer une classe de client WCF et d’appeler des opérations sur le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [vue d’ensemble du modèle de Service WCF avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md).  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exécute chaque opération à l’intérieur d’une transaction sur la base de données Oracle. Vous pouvez contrôler le niveau d’isolation de cette opération en définissant le **TransactionIsolationLevel** propriété de liaison. Pour plus d’informations sur la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] propriétés de liaison, consultez [utilisation de l’adaptateur BizTalk pour les propriétés de liaison de base de données Oracle](https://msdn.microsoft.com/library/dd788467.aspx).  
  
 Les sections suivantes fournissent plus d’informations sur la manière d’appeler chaque opération SQL de base dans votre code.  
  
###  <a name="BKMK_InsertOperation"></a>Opération d’insertion  
 Le tableau suivant montre comment définir les paramètres d’enregistrement plusieurs Insert et les opérations d’insertion en bloc.  
  
|Insérer le type d’opération|JEU D’ENREGISTREMENTS|NOMS DE COLONNE|QUERY|  
|---------------------------|---------------|-------------------|-----------|  
|Enregistrement de plusieurs|Collection de INSERTRECORDS doivent être insérés dans la cible.|Null|Null|  
|En bloc|Null|Une liste délimitée par des virgules de noms de colonnes dans la cible. par exemple, « TID, compte ». La liste de colonnes spécifie les colonnes dans lequel les résultats de requête doivent être placés dans chaque ligne insérée. La requête doit retourner un jeu de résultats qui correspondent aux colonnes spécifiées dans la liste des colonnes en nombre et type.|Une requête SQL SELECT sur une table de base de données ou une vue qui retourne un jeu de résultats à insérer dans la cible. par exemple, « sélectionnez (TID, compte) à partir du compte de WHERE NEW_TRANSACTIONS = 100001 ». Le jeu de résultats doit correspondre à la liste des colonnes en nombre et type.|  
  
 L’opération d’insertion retourne le nombre d’enregistrements insérés dans la cible.  
  
> [!IMPORTANT]
>  Dans le modèle de service WCF, le jeu d’enregistrements utilisé dans l’opération d’insertion est fortement typée. Vous pouvez définir la valeur d’une colonne nillable **null** dans un enregistrement pour exclure cette colonne à partir de l’opération d’insertion ; Toutefois, vous ne pouvez pas définir la valeur d’une colonne non nillable à **null**. Cela signifie que dans une opération d’insertion enregistrement multiples, vous devez fournir des valeurs pour toutes les colonnes non nillable dans chaque enregistrement. En outre, il n’existe aucune prise en charge la diffusion en continu pour les opérations SQL de base lorsque vous utilisez le modèle de service WCF. Si votre opération d’insertion plusieurs enregistrement implique un jeu d’enregistrements volumineux, cela peut être un facteur important. Pour plus d’informations, consultez [Limitations d’appeler les opérations SQL de base en utilisant le modèle de Service WCF](#BKMK_LimitationsInvoking).  
  
 Le code suivant montre une plusieurs enregistrement opération d’insertion (deux enregistrements) qui cible la table ACCOUNTACTIVITY.  
  
```  
// Insert records  
                using (SCOTTTableACCOUNTACTIVITYClient aaTableClient =   
                    new SCOTTTableACCOUNTACTIVITYClient("OracleDBBinding_SCOTT.Table.ACCOUNTACTIVITY"))  
                {  
                    long recsInserted;  
  
                    aaTableClient.ClientCredentials.UserName.UserName = "SCOTT";  
                    aaTableClient.ClientCredentials.UserName.Password = "TIGER";  
  
                    try  
                    {  
                        aaTableClient.Open();  
                    }  
                    catch (Exception ex)  
                    {  
                        // handle exception  
                        Console.WriteLine("Exception: " + ex.Message);  
                        throw;  
                    }  
  
                    // Do a multiple record Insert of 2 records for account 100001  
  
                    microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[] insertRecs =  
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[2];  
  
                                  TID__COMPLEX_TYPE tid = new TID__COMPLEX_TYPE();  
                                  tid.InlineValue = "tidSequence.NextVal()";  
  
                                  ACCOUNT__COMPLEX_TYPE account = new ACCOUNT__COMPLEX_TYPE();  
                                  account.Value = 100001;  
  
                    AMOUNT__COMPLEX_TYPE amount = new AMOUNT__COMPLEX_TYPE();  
                    amount.Value = 400;  
  
                    TRANSDATE__COMPLEX_TYPE transdate = new TRANSDATE__COMPLEX_TYPE();  
                    transdate.Value = DateTime.Now.Date;  
  
                    PROCESSED__COMPLEX_TYPE processed = new PROCESSED__COMPLEX_TYPE();  
                    processed.Value = "n";  
  
                    DESCRIPTION__COMPLEX_TYPE description1 = new DESCRIPTION__COMPLEX_TYPE();  
                    description1.Value = "Inserted Record #1";  
  
                    DESCRIPTION__COMPLEX_TYPE description2 = new DESCRIPTION__COMPLEX_TYPE();  
                    description2.Value = "Inserted Record #2";  
  
                    insertRecs[0] =   
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT();  
                    insertRecs[0].TID = tid;  
                    insertRecs[0].ACCOUNT = account;  
                    insertRecs[0].AMOUNT = amount;  
                    insertRecs[0].TRANSDATE = transdate;  
                    insertRecs[0].DESCRIPTION = description1;  
                    insertRecs[0].PROCESSED = processed;  
  
                    insertRecs[1] =   
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT();  
                    insertRecs[1].TID = tid;  
                    insertRecs[1].ACCOUNT = account;  
                    insertRecs[1].AMOUNT = amount;  
                    insertRecs[1].TRANSDATE = transdate;  
                    insertRecs[1].DESCRIPTION = description2;  
                    insertRecs[1].PROCESSED = processed;  
  
                    try  
                    {  
                        recsInserted = aaTableClient.Insert(insertRecs, null, null);  
                    }  
                    catch (Exception ex)  
                    {  
                        // handle exception  
                        Console.WriteLine("Exception: " + ex.Message);  
                        throw;  
                    }  
  
                    Console.WriteLine("Insert Done: {0} records inserted", recsInserted);  
```  
  
### <a name="select-operation"></a>Sélectionnez l’opération  
 Le tableau suivant montre les paramètres pour l’opération de sélection.  
  
|NOMS DE COLONNE|FILTER|  
|-------------------|------------|  
|Une liste délimitée par des virgules de noms de colonnes dans la cible. par exemple, « TID, compte ». La liste de colonnes spécifie les colonnes de la cible doit être retournée dans le jeu de résultats. Colonnes non spécifiées dans la liste des colonnes seront fixés à leurs valeurs par défaut de .NET dans le jeu d’enregistrements retourné. Pour les colonnes « nillable », cette valeur est **null**.|Le contenu d’une clause SQL WHERE qui spécifie les lignes de la cible de la requête. par exemple, « DESCRIPTION = 'Insérer enregistrement #1' ». Vous pouvez définir ce paramètre **null** renvoie toutes les lignes de la cible.|  
  
 L’opération Select retourne un jeu d’enregistrements fortement typée selon le type de ligne de la cible.  
  
> [!IMPORTANT]
>  Il n’existe aucune prise en charge la diffusion en continu pour les opérations SQL de base lorsque vous utilisez le modèle de service WCF. Si votre requête retourne un jeu d’enregistrements volumineux, vous pourrez peut-être améliorer les performances en utilisant le modèle de canal WCF. Pour plus d’informations, consultez [Limitations d’appeler les opérations SQL de base en utilisant le modèle de Service WCF](#BKMK_LimitationsInvoking).  
  
 Le code suivant illustre une opération de sélection qui cible la table ACCOUNTACTIVITY. Les enregistrements retournés sont écrites dans la console.  
  
```  
// Declare a variable to hold the result set  
microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] selectRecords;  
  
// Select all records and write them to the console  
try  
{  
    selectRecords = aaTableClient.Select("*", null);  
}  
catch (Exception ex)  
{  
    // handle exception  
}  
  
Console.WriteLine("ACCOUNTACTIVITY before any operations");  
for (int i = 0; i \< selectRecords.Length; i++)  
{  
    Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", selectRecords[i].TID,  
    selectRecords[i].ACCOUNT,  
    selectRecords[i].AMOUNT,  
    selectRecords[i].TRANSDATE,  
    selectRecords[i].DESCRIPTION);  
}  
```  
  
> [!NOTE]
>  Ce code omet les étapes pour créer, configurer et ouvrez l’instance de client WCF. Pour obtenir un exemple qui inclut ces étapes, consultez [opération Insert](#BKMK_InsertOperation).  
  
### <a name="update-operation"></a>Opération de mise à jour  
 Le tableau suivant montre les paramètres pour l’opération de mise à jour.  
  
|JEU D’ENREGISTREMENTS|FILTER|  
|---------------|------------|  
|Un enregistrement fortement typée de modèle en fonction du type de ligne de la cible. L’enregistrement du modèle spécifie les valeurs de mise à jour pour les lignes de la cible. Pour les colonnes de la ligne « nillable », vous pouvez spécifier une valeur null pour indiquer que la colonne ne doit pas mis à jour dans les lignes de la cible.|Le contenu d’une clause SQL WHERE qui spécifie les lignes à mettre à jour dans la cible. Par exemple, « DESCRIPTION = 'Enregistrement Inserted #1' ».|  
  
 L’opération de mise à jour retourne le nombre de lignes supprimées de la cible.  
  
> [!IMPORTANT]
>  Dans le modèle de service WCF, l’enregistrement du modèle utilisé dans l’opération de mise à jour est fortement typée. Si une colonne est « nillable », vous pouvez omettre la colonne à partir de l’opération de mise à jour en définissant sa valeur sur **null** dans l’enregistrement de modèle ; Toutefois, si une colonne n’est pas « nillable », vous devez définir sa valeur dans l’enregistrement du modèle. Par exemple, si une colonne est une clé primaire, il doit contenir une valeur. Pour plus d’informations, consultez [Limitations d’appeler les opérations SQL de base en utilisant le modèle de Service WCF](#BKMK_LimitationsInvoking).  
  
 Le code suivant montre une opération de mise à jour qui cible la table ACCOUNTACTIVITY.  
  
```  
long recsUpdated;  
  
...  
  
// Create updated template. The TID, TIME, AMOUNT, and DESCRIPTION fields will be updated  
microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE updateRecord =  
    new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE();  
        updateRecord.TID = tidSequence.NextVal();  
        updateRecord.ACCOUNT = null;  
        updateRecord.AMOUNT = 300;  
        updateRecord.TRANSDATE = DateTime.Now.Date;  
        updateRecord.DESCRIPTION = "Updated Record #2";  
        updateRecord.PROCESSED = null;  
  
// Set filter string to specify the target record by using the DESCRIPTION field  
string filter = "DESCRIPTION = 'Inserted Record #2'";  
  
try  
{  
    recsUpdated = aaTableClient.Update(updateRecord, filter);  
}  
catch (Exception ex)  
{  
    // handle exception  
    ...  
}  
  
Console.WriteLine("{0} records updated", recsUpdated);  
```  
  
> [!NOTE]
>  Ce code omet les étapes pour créer, configurer et ouvrez l’instance de client WCF. Pour obtenir un exemple qui inclut ces étapes, consultez [opération Insert](#BKMK_InsertOperation).  
  
### <a name="delete-operation"></a>Opération de suppression  
 Le tableau suivant montre les paramètres pour l’opération de suppression.  
  
|FILTER|  
|------------|  
|Le contenu d’une clause SQL WHERE qui spécifie les lignes à supprimer de la cible. Par exemple, « DESCRIPTION = 'Enregistrement Inserted #1' ».|  
  
 L’opération de suppression retourne le nombre de lignes supprimées de la cible. Le code suivant montre une opération de suppression qui cible la table ACCOUNTACTIVITY.  
  
```  
// Set filter string equal to the DESCRIPTION field of the target record  
string filter = "DESCRIPTION = 'Inserted Record #1'";  
  
try  
{  
    recsDeleted = aaTableClient.Delete(filter);  
}  
catch (Exception ex)  
{  
    // handle exception  
  
    ...  
}  
Console.WriteLine("{0} records deleted", recsDeleted);  
```  
  
> [!NOTE]
>  Ce code omet les étapes pour créer, configurer et ouvrez l’instance de client WCF. Pour obtenir un exemple qui inclut ces étapes, consultez le [opération Insert](#BKMK_InsertOperation).  
  
##  <a name="BKMK_LimitationsInvoking"></a>Limitations de l’appel d’opérations SQL de base en utilisant le modèle de Service WCF  
 Les limitations suivantes lorsque vous appelez les opérations SQL de base à l’aide d’un client WCF :  
  
-   **Opération d’insertion.** Le jeu d’enregistrements utilisé dans une opération d’insertion plusieurs enregistrement est fortement typée et par conséquent inclut toutes les colonnes de la ligne. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprète une valeur null dans un enregistrement pour indiquer que la colonne doit être exclue de l’opération d’insertion ; Toutefois, les colonnes non nillable ne peut être exclus, car vous ne peut pas définir une valeur null. Par conséquent, vous devez spécifier des valeurs pour les colonnes non nillable lorsque vous effectuez une opération d’insertion plusieurs enregistrement.  
  
-   **Opération d’insertion.** Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprète un **DbNull** valeur dans une colonne de données « nillable » signifie que la colonne doit être exclue d’une opération d’insertion plusieurs enregistrement. Cela signifie que vous ne pouvez pas définir une colonne nillable **DbNull** sur la base de données Oracle dans un enregistrement plusieurs opération d’insertion.  
  
-   **Opération d’insertion.** Il n’existe aucune prise en charge la diffusion en continu pour plusieurs opérations d’insertion d’enregistrement qui impliquent un grand jeu d’enregistrements.  
  
-   **Opération de mise à jour.** L’enregistrement du modèle utilisé dans une opération de mise à jour est fortement typée et par conséquent inclut toutes les colonnes de la ligne. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprète une valeur null dans cet enregistrement pour indiquer que la colonne doit être exclue de l’opération de mise à jour ; Toutefois, les colonnes non nillable ne peut être exclus, car vous les ne peut pas une valeur null. Par conséquent, vous devez spécifier des valeurs pour les colonnes non nillable lorsque vous effectuez une opération de mise à jour.  
  
-   **Opération de mise à jour.** Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprète un **DbNull** valeur dans une colonne de données « nillable » dans l’enregistrement du modèle pour indiquer que la colonne doit être exclue de l’opération. Cela signifie que vous ne pouvez pas définir une colonne nillable **DbNull** sur la base de données Oracle à l’aide de l’opération de mise à jour.  
  
-   **Sélectionnez l’opération.** Il n’existe aucune prise en charge la diffusion en continu pour les requêtes SELECT qui retournent un jeu d’enregistrements volumineux.  
  
 Pour les scénarios où les limitations de posent des problèmes, vous pouvez appeler l’opération à l’aide du modèle de canal WCF, car :  
  
-   À l’aide du modèle de canal WCF, vous pouvez exclure des colonnes de données spécifiques des opérations Update et Insert.  
  
-   Le modèle de canal WCF prend en charge de diffusion en continu au niveau du nœud pour les opérations SQL de base qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose.  
  
 Pour plus d’informations sur l’utilisation du modèle de canal WCF avec les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [développer Oracle de base de données Applications à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des Applications de base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)
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
# <a name="insert-update-delete-or-select-operations-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="73d78-102">Insérer, mettre à jour, supprimer ou sélectionner des opérations dans la base de données Oracle à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="73d78-102">Insert, update, delete, or select operations in Oracle Database using the WCF Service Model</span></span>
<span data-ttu-id="73d78-103">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose un ensemble de base Insert, Update, Delete et les opérations Select sur les tables de base de données Oracle et des vues.</span><span class="sxs-lookup"><span data-stu-id="73d78-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces a set of basic Insert, Update, Delete, and Select operations on Oracle database tables and views.</span></span> <span data-ttu-id="73d78-104">À l’aide de ces opérations, vous pouvez effectuer de simples sélectionnez SQL INSERT, UPDATE et supprimer les instructions qualifiées par une clause WHERE sur une table ou vue cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-104">By using these operations, you can perform simple SQL INSERT, UPDATE, SELECT, and DELETE statements qualified by a WHERE clause on a target table or view.</span></span> <span data-ttu-id="73d78-105">Pour effectuer des opérations plus complexes, par exemple une requête SQL SELECT qui utilise l’opérateur de jointure, vous pouvez utiliser l’opération SQLEXECUTE.</span><span class="sxs-lookup"><span data-stu-id="73d78-105">To perform more complex operations, for example a SQL SELECT query that uses the JOIN operator, you can use the SQLEXECUTE operation.</span></span> <span data-ttu-id="73d78-106">Pour plus d’informations sur l’opération SQLEXECUTE, consultez [une opération SQLEXECUTE dans Oracle à l’aide de base de données du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="73d78-106">For more information about the SQLEXECUTE operation, see [Performing a SQLEXECUTE Operation in Oracle Database Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
 <span data-ttu-id="73d78-107">Le tableau suivant récapitule les opérations SQL de base qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces sur les tables et vues.</span><span class="sxs-lookup"><span data-stu-id="73d78-107">The following table summarizes the basic SQL operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces on tables and views.</span></span> <span data-ttu-id="73d78-108">Pour obtenir une description complète de ces opérations, consultez [des schémas de Message pour la base opérations d’insertion, mise à jour, supprimer et sélectionnez sur les Tables et vues](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).</span><span class="sxs-lookup"><span data-stu-id="73d78-108">For a complete description of these operations, see [Message Schemas for the Basic Insert, Update, Delete, and Select Operations on Tables and Views](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).</span></span>  
  
|<span data-ttu-id="73d78-109">Opération</span><span class="sxs-lookup"><span data-stu-id="73d78-109">Operation</span></span>|<span data-ttu-id="73d78-110"> Description</span><span class="sxs-lookup"><span data-stu-id="73d78-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73d78-111">Insert</span><span class="sxs-lookup"><span data-stu-id="73d78-111">Insert</span></span>|<span data-ttu-id="73d78-112">L’opération d’insertion prend en charge plusieurs des insertions en bloc ou d’enregistrement dans la table ou vue cible :</span><span class="sxs-lookup"><span data-stu-id="73d78-112">The Insert operation supports multiple record or bulk inserts into the target table or view:</span></span><br /><br /> <span data-ttu-id="73d78-113">-Une opération d’insertion plusieurs enregistrement insère des lignes dans une table ou une vue basée sur un jeu d’enregistrements fourni.</span><span class="sxs-lookup"><span data-stu-id="73d78-113">-   A multiple record Insert operation inserts rows into a table or view based on a supplied record set.</span></span><br /><span data-ttu-id="73d78-114">-Une opération d’insertion en bloc insère des lignes dans une table ou une vue basée sur un SQL SELECT de requêtes et de colonne liste fournie.</span><span class="sxs-lookup"><span data-stu-id="73d78-114">-   A bulk Insert operation inserts rows into a table or view based on a supplied SQL SELECT query and column list.</span></span> <span data-ttu-id="73d78-115">La requête retourne les enregistrements sont insérés dans la table cible en fonction de la liste des colonnes.</span><span class="sxs-lookup"><span data-stu-id="73d78-115">The records that the query returns are inserted into the target table based on the column list.</span></span>|  
|<span data-ttu-id="73d78-116">Select</span><span class="sxs-lookup"><span data-stu-id="73d78-116">Select</span></span>|<span data-ttu-id="73d78-117">Effectue une requête SQL SELECT sur la table cible selon une liste de noms de colonne et une chaîne de filtrage qui spécifie une clause SQL WHERE fournie.</span><span class="sxs-lookup"><span data-stu-id="73d78-117">Performs a SQL SELECT query on the target table based on a supplied list of column names and a filter string that specifies a SQL WHERE clause.</span></span>|  
|<span data-ttu-id="73d78-118">Update</span><span class="sxs-lookup"><span data-stu-id="73d78-118">Update</span></span>|<span data-ttu-id="73d78-119">Effectue une mise à jour sur la table cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-119">Performs an UPDATE on the target table.</span></span> <span data-ttu-id="73d78-120">Les enregistrements doivent être mis à jour sont spécifiées par une chaîne de filtrage qui spécifie une clause SQL WHERE.</span><span class="sxs-lookup"><span data-stu-id="73d78-120">The records to be updated are specified by a filter string that specifies a SQL WHERE clause.</span></span> <span data-ttu-id="73d78-121">Les valeurs pour la mise à jour sont spécifiées dans un enregistrement du modèle.</span><span class="sxs-lookup"><span data-stu-id="73d78-121">The values for the update are specified in a template record.</span></span>|  
|<span data-ttu-id="73d78-122">DELETE</span><span class="sxs-lookup"><span data-stu-id="73d78-122">Delete</span></span>|<span data-ttu-id="73d78-123">Effectue une suppression sur la table cible selon une clause SQL WHERE qui est spécifiée dans une chaîne de filtre.</span><span class="sxs-lookup"><span data-stu-id="73d78-123">Performs a DELETE on the target table based on a SQL WHERE clause that is specified in a filter string.</span></span>|  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="73d78-124">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="73d78-124">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="73d78-125">Les exemples de cette rubrique utilisent la table /SCOTT/ACCOUNTACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="73d78-125">The examples in this topic use the /SCOTT/ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="73d78-126">Un script pour générer cette table est fourni avec les exemples du Kit de développement logiciel.</span><span class="sxs-lookup"><span data-stu-id="73d78-126">A script to generate this table is supplied with the SDK samples.</span></span> <span data-ttu-id="73d78-127">Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).</span><span class="sxs-lookup"><span data-stu-id="73d78-127">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="73d78-128">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="73d78-128">The WCF Client Class</span></span>  
 <span data-ttu-id="73d78-129">Le nom du client WCF généré pour les opérations SQL de base qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces est basé sur le nom de la table ou vue, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="73d78-129">The name of the WCF client generated for the basic SQL operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces is based on the name of the table or view, as in the following table.</span></span>  
  
|<span data-ttu-id="73d78-130">Objet de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="73d78-130">Oracle Database Artifact</span></span>|<span data-ttu-id="73d78-131">Nom de Client WCF</span><span class="sxs-lookup"><span data-stu-id="73d78-131">WCF Client Name</span></span>|  
|------------------------------|---------------------|  
|<span data-ttu-id="73d78-132">Table</span><span class="sxs-lookup"><span data-stu-id="73d78-132">Table</span></span>|<span data-ttu-id="73d78-133">[SCHÉMA] Client de la table [nom_table]</span><span class="sxs-lookup"><span data-stu-id="73d78-133">[SCHEMA]Table[TABLE_NAME]Client</span></span>|  
|<span data-ttu-id="73d78-134">Affichage</span><span class="sxs-lookup"><span data-stu-id="73d78-134">View</span></span>|<span data-ttu-id="73d78-135">[SCHÉMA] Client de la vue [VIEW_NAME]</span><span class="sxs-lookup"><span data-stu-id="73d78-135">[SCHEMA]View[VIEW_NAME]Client</span></span>|  
  
 <span data-ttu-id="73d78-136">[Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.</span><span class="sxs-lookup"><span data-stu-id="73d78-136">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="73d78-137">[Nom_table] = nom de la table ; par exemple, ACCOUNTACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="73d78-137">[TABLE_NAME] = The name of the table; for example, ACCOUNTACTIVITY.</span></span>  
  
 <span data-ttu-id="73d78-138">[VIEW_NAME] = nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="73d78-138">[VIEW_NAME] = The name of the view.</span></span>  
  
 <span data-ttu-id="73d78-139">Le tableau suivant montre les signatures de méthode pour les opérations SQL de base sur une table.</span><span class="sxs-lookup"><span data-stu-id="73d78-139">The following table shows the method signatures for the basic SQL operations on a table.</span></span> <span data-ttu-id="73d78-140">Les signatures sont identiques pour une vue, à ceci près que le nom et l’espace de noms de vue remplacent ceux de la table.</span><span class="sxs-lookup"><span data-stu-id="73d78-140">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="73d78-141">Opération</span><span class="sxs-lookup"><span data-stu-id="73d78-141">Operation</span></span>|<span data-ttu-id="73d78-142">Signature de méthode</span><span class="sxs-lookup"><span data-stu-id="73d78-142">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="73d78-143">Insert</span><span class="sxs-lookup"><span data-stu-id="73d78-143">Insert</span></span>|<span data-ttu-id="73d78-144">durée pendant laquelle insérer ([TABLE_NS]. [ Nom_table] RECORDINSERT [] chaîne les noms de colonne, chaîne de requête de jeu d’enregistrements) ;</span><span class="sxs-lookup"><span data-stu-id="73d78-144">long Insert([TABLE_NS].[TABLE_NAME]RECORDINSERT[] RECORDSET, string COLUMN_NAMES, string QUERY);</span></span>|  
|<span data-ttu-id="73d78-145">Select</span><span class="sxs-lookup"><span data-stu-id="73d78-145">Select</span></span>|<span data-ttu-id="73d78-146">[TABLE_NS]. [NOM_TABLE] RECORDSELECT [] sélectionnez (chaîne les noms de colonne, chaîne de filtre) ;</span><span class="sxs-lookup"><span data-stu-id="73d78-146">[TABLE_NS].[TABLE_NAME]RECORDSELECT[] Select(string COLUMN_NAMES, string FILTER);</span></span>|  
|<span data-ttu-id="73d78-147">Update</span><span class="sxs-lookup"><span data-stu-id="73d78-147">Update</span></span>|<span data-ttu-id="73d78-148">durée pendant laquelle mettre à jour ([TABLE_NS]. [ Nom_table] RECORDUPDATE RECORDSET, chaîne de filtre) ;</span><span class="sxs-lookup"><span data-stu-id="73d78-148">long Update([TABLE_NS].[TABLE_NAME]RECORDUPDATE RECORDSET, string FILTER);</span></span>|  
|<span data-ttu-id="73d78-149">DELETE</span><span class="sxs-lookup"><span data-stu-id="73d78-149">Delete</span></span>|<span data-ttu-id="73d78-150">Durée pendant laquelle supprimer (chaîne de filtre) ;</span><span class="sxs-lookup"><span data-stu-id="73d78-150">Long Delete(string FILTER);</span></span>|  
  
 <span data-ttu-id="73d78-151">[TABLE_NS] = le nom de l’espace de noms de table ; par exemple, microsoft.lobservices.oracledb._2007._03.SCOTT. Table.ACCOUNTACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="73d78-151">[TABLE_NS] = The name of the table namespace; for example, microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.</span></span>  
  
 <span data-ttu-id="73d78-152">[Nom_table] = nom de la table ; par exemple, ACCOUNTACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="73d78-152">[TABLE_NAME] = The name of the table; for example, ACCOUNTACTIVITY.</span></span>  
  
 <span data-ttu-id="73d78-153">Utilisé par les opérations d’insertion, mise à jour et sélectionnez les types d’enregistrements sont tous définis dans la table ou afficher l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="73d78-153">The record types used by the Insert, Update, and Select operations are all defined in the table or view namespace.</span></span>  
  
 <span data-ttu-id="73d78-154">Le code suivant montre les signatures de méthode pour une classe de client WCF généré de Delete, Insert, Select et de mise à jour sur la table ACCOUNTACTIVITY/SCOTT.</span><span class="sxs-lookup"><span data-stu-id="73d78-154">The following code shows the method signatures for a WCF client class generated for the Delete, Insert, Select and Update operations on the /SCOTT/ACCOUNTACTIVITY table.</span></span>  
  
```  
public partial class SCOTTTableACCOUNTACTIVITYClient : System.ServiceModel.ClientBase<SCOTTTableACCOUNTACTIVITY>, SCOTTTableACCOUNTACTIVITY {  
  
    public long Delete(string FILTER);  
  
    public long Insert(microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[] RECORDSET, string COLUMN_NAMES, string QUERY);  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] Select(string COLUMN_NAMES, string FILTER);  
  
    public long Update(microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE RECORDSET, string FILTER);  
}  
```  
  
## <a name="invoking-the-basic-sql-operations"></a><span data-ttu-id="73d78-155">Appeler les opérations SQL de base</span><span class="sxs-lookup"><span data-stu-id="73d78-155">Invoking the Basic SQL Operations</span></span>  
 <span data-ttu-id="73d78-156">Pour appeler les opérations SQL de base sur une table ou vue à l’aide d’un client WCF, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="73d78-156">To invoke the basic SQL operations on a table or view by using a WCF client, perform the following steps.</span></span>  
  
1.  <span data-ttu-id="73d78-157">Générer une classe de client WCF pour la table ou vue cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-157">Generate a WCF client class for the target table or view.</span></span> <span data-ttu-id="73d78-158">Cette classe doit contenir des méthodes pour les opérations que vous appellerez sur l’artefact cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-158">This class should contain methods for the operations that you will invoke on the target artifact.</span></span>  
  
2.  <span data-ttu-id="73d78-159">Créez une instance de la classe de client WCF et appeler ses méthodes pour effectuer des opérations sur la table ou la vue.</span><span class="sxs-lookup"><span data-stu-id="73d78-159">Create an instance of the WCF client class and invoke its methods to perform operations on the table or view.</span></span>  
  
 <span data-ttu-id="73d78-160">Pour plus d’informations sur la façon de créer une classe de client WCF et d’appeler des opérations sur le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [vue d’ensemble du modèle de Service WCF avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="73d78-160">For more detailed information about how to create a WCF client class and invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Overview of the WCF Service Model with the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md).</span></span>  
  
 <span data-ttu-id="73d78-161">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exécute chaque opération à l’intérieur d’une transaction sur la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="73d78-161">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] executes each operation inside of a transaction on the Oracle database.</span></span> <span data-ttu-id="73d78-162">Vous pouvez contrôler le niveau d’isolation de cette opération en définissant le **TransactionIsolationLevel** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="73d78-162">You can control the isolation level of this transaction by setting the **TransactionIsolationLevel** binding property.</span></span> <span data-ttu-id="73d78-163">Pour plus d’informations sur la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] propriétés de liaison, consultez [utilisation de l’adaptateur BizTalk pour les propriétés de liaison de base de données Oracle](https://msdn.microsoft.com/library/dd788467.aspx).</span><span class="sxs-lookup"><span data-stu-id="73d78-163">For more information about the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding properties, see [Working with BizTalk Adapter for Oracle Database Binding Properties](https://msdn.microsoft.com/library/dd788467.aspx).</span></span>  
  
 <span data-ttu-id="73d78-164">Les sections suivantes fournissent plus d’informations sur la manière d’appeler chaque opération SQL de base dans votre code.</span><span class="sxs-lookup"><span data-stu-id="73d78-164">The following sections provide details about how to invoke each basic SQL operation in your code.</span></span>  
  
###  <a name="BKMK_InsertOperation"></a><span data-ttu-id="73d78-165">Opération d’insertion</span><span class="sxs-lookup"><span data-stu-id="73d78-165">Insert Operation</span></span>  
 <span data-ttu-id="73d78-166">Le tableau suivant montre comment définir les paramètres d’enregistrement plusieurs Insert et les opérations d’insertion en bloc.</span><span class="sxs-lookup"><span data-stu-id="73d78-166">The following table shows how to set parameters for multiple record Insert and bulk Insert operations.</span></span>  
  
|<span data-ttu-id="73d78-167">Insérer le type d’opération</span><span class="sxs-lookup"><span data-stu-id="73d78-167">Insert operation type</span></span>|<span data-ttu-id="73d78-168">JEU D’ENREGISTREMENTS</span><span class="sxs-lookup"><span data-stu-id="73d78-168">RECORDSET</span></span>|<span data-ttu-id="73d78-169">NOMS DE COLONNE</span><span class="sxs-lookup"><span data-stu-id="73d78-169">COLUMN_NAMES</span></span>|<span data-ttu-id="73d78-170">QUERY</span><span class="sxs-lookup"><span data-stu-id="73d78-170">QUERY</span></span>|  
|---------------------------|---------------|-------------------|-----------|  
|<span data-ttu-id="73d78-171">Enregistrement de plusieurs</span><span class="sxs-lookup"><span data-stu-id="73d78-171">Multiple record</span></span>|<span data-ttu-id="73d78-172">Collection de INSERTRECORDS doivent être insérés dans la cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-172">A collection of INSERTRECORDS that should be inserted into the target.</span></span>|<span data-ttu-id="73d78-173">Null</span><span class="sxs-lookup"><span data-stu-id="73d78-173">null</span></span>|<span data-ttu-id="73d78-174">Null</span><span class="sxs-lookup"><span data-stu-id="73d78-174">null</span></span>|  
|<span data-ttu-id="73d78-175">En bloc</span><span class="sxs-lookup"><span data-stu-id="73d78-175">Bulk</span></span>|<span data-ttu-id="73d78-176">Null</span><span class="sxs-lookup"><span data-stu-id="73d78-176">null</span></span>|<span data-ttu-id="73d78-177">Une liste délimitée par des virgules de noms de colonnes dans la cible. par exemple, « TID, compte ».</span><span class="sxs-lookup"><span data-stu-id="73d78-177">A comma-delimited list of column names in the target; for example, "TID, ACCOUNT".</span></span> <span data-ttu-id="73d78-178">La liste de colonnes spécifie les colonnes dans lequel les résultats de requête doivent être placés dans chaque ligne insérée.</span><span class="sxs-lookup"><span data-stu-id="73d78-178">The column list specifies the columns into which the query results should be placed in each inserted row.</span></span> <span data-ttu-id="73d78-179">La requête doit retourner un jeu de résultats qui correspondent aux colonnes spécifiées dans la liste des colonnes en nombre et type.</span><span class="sxs-lookup"><span data-stu-id="73d78-179">The query must return a result set that matches the columns specified in the column list in both number and type.</span></span>|<span data-ttu-id="73d78-180">Une requête SQL SELECT sur une table de base de données ou une vue qui retourne un jeu de résultats à insérer dans la cible. par exemple, « sélectionnez (TID, compte) à partir du compte de WHERE NEW_TRANSACTIONS = 100001 ».</span><span class="sxs-lookup"><span data-stu-id="73d78-180">A SQL SELECT query on a database table or view that returns a result set to insert into the target; for example, "SELECT (TID, ACCOUNT) FROM NEW_TRANSACTIONS WHERE ACCOUNT = 100001".</span></span> <span data-ttu-id="73d78-181">Le jeu de résultats doit correspondre à la liste des colonnes en nombre et type.</span><span class="sxs-lookup"><span data-stu-id="73d78-181">The result set must match the column list in both number and type.</span></span>|  
  
 <span data-ttu-id="73d78-182">L’opération d’insertion retourne le nombre d’enregistrements insérés dans la cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-182">The Insert operation returns the number of records inserted into the target.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="73d78-183">Dans le modèle de service WCF, le jeu d’enregistrements utilisé dans l’opération d’insertion est fortement typée.</span><span class="sxs-lookup"><span data-stu-id="73d78-183">In the WCF service model, the record set used in the Insert operation is strongly-typed.</span></span> <span data-ttu-id="73d78-184">Vous pouvez définir la valeur d’une colonne nillable **null** dans un enregistrement pour exclure cette colonne à partir de l’opération d’insertion ; Toutefois, vous ne pouvez pas définir la valeur d’une colonne non nillable à **null**.</span><span class="sxs-lookup"><span data-stu-id="73d78-184">You can set the value of a nillable column to **null** in a record to exclude that column from the Insert operation; however, you cannot set the value of a non-nillable column to **null**.</span></span> <span data-ttu-id="73d78-185">Cela signifie que dans une opération d’insertion enregistrement multiples, vous devez fournir des valeurs pour toutes les colonnes non nillable dans chaque enregistrement.</span><span class="sxs-lookup"><span data-stu-id="73d78-185">This means that in a multiple record Insert operation, you must supply values for all non-nillable columns in each record.</span></span> <span data-ttu-id="73d78-186">En outre, il n’existe aucune prise en charge la diffusion en continu pour les opérations SQL de base lorsque vous utilisez le modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="73d78-186">In addition, there is no streaming support for the basic SQL operations when you use the WCF service model.</span></span> <span data-ttu-id="73d78-187">Si votre opération d’insertion plusieurs enregistrement implique un jeu d’enregistrements volumineux, cela peut être un facteur important.</span><span class="sxs-lookup"><span data-stu-id="73d78-187">If your multiple record Insert operation involves a large record set, this may be an important consideration.</span></span> <span data-ttu-id="73d78-188">Pour plus d’informations, consultez [Limitations d’appeler les opérations SQL de base en utilisant le modèle de Service WCF](#BKMK_LimitationsInvoking).</span><span class="sxs-lookup"><span data-stu-id="73d78-188">For more information, see [Limitations of Invoking the Basic SQL Operations by Using the WCF Service Model](#BKMK_LimitationsInvoking).</span></span>  
  
 <span data-ttu-id="73d78-189">Le code suivant montre une plusieurs enregistrement opération d’insertion (deux enregistrements) qui cible la table ACCOUNTACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="73d78-189">The following code shows a multiple record Insert operation (two records) that targets the ACCOUNTACTIVITY table.</span></span>  
  
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
  
### <a name="select-operation"></a><span data-ttu-id="73d78-190">Sélectionnez l’opération</span><span class="sxs-lookup"><span data-stu-id="73d78-190">Select Operation</span></span>  
 <span data-ttu-id="73d78-191">Le tableau suivant montre les paramètres pour l’opération de sélection.</span><span class="sxs-lookup"><span data-stu-id="73d78-191">The following table shows the parameters for the Select operation.</span></span>  
  
|<span data-ttu-id="73d78-192">NOMS DE COLONNE</span><span class="sxs-lookup"><span data-stu-id="73d78-192">COLUMN_NAMES</span></span>|<span data-ttu-id="73d78-193">FILTER</span><span class="sxs-lookup"><span data-stu-id="73d78-193">FILTER</span></span>|  
|-------------------|------------|  
|<span data-ttu-id="73d78-194">Une liste délimitée par des virgules de noms de colonnes dans la cible. par exemple, « TID, compte ».</span><span class="sxs-lookup"><span data-stu-id="73d78-194">A comma-delimited list of column names in the target; for example, "TID, ACCOUNT".</span></span> <span data-ttu-id="73d78-195">La liste de colonnes spécifie les colonnes de la cible doit être retournée dans le jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="73d78-195">The column list specifies the columns of the target that should be returned in the result set.</span></span> <span data-ttu-id="73d78-196">Colonnes non spécifiées dans la liste des colonnes seront fixés à leurs valeurs par défaut de .NET dans le jeu d’enregistrements retourné.</span><span class="sxs-lookup"><span data-stu-id="73d78-196">Columns not specified in the column list will be set to their .NET default values in the returned record set.</span></span> <span data-ttu-id="73d78-197">Pour les colonnes « nillable », cette valeur est **null**.</span><span class="sxs-lookup"><span data-stu-id="73d78-197">For nillable columns, this value is **null**.</span></span>|<span data-ttu-id="73d78-198">Le contenu d’une clause SQL WHERE qui spécifie les lignes de la cible de la requête. par exemple, « DESCRIPTION = 'Insérer enregistrement #1' ».</span><span class="sxs-lookup"><span data-stu-id="73d78-198">The contents of a SQL WHERE clause that specifies the target rows of the query; for example, "DESCRIPTION = 'Insert Record #1'".</span></span> <span data-ttu-id="73d78-199">Vous pouvez définir ce paramètre **null** renvoie toutes les lignes de la cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-199">You can set this parameter to **null** to return all rows of the target.</span></span>|  
  
 <span data-ttu-id="73d78-200">L’opération Select retourne un jeu d’enregistrements fortement typée selon le type de ligne de la cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-200">The Select operation returns a strongly-typed record set based on the row type of the target.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="73d78-201">Il n’existe aucune prise en charge la diffusion en continu pour les opérations SQL de base lorsque vous utilisez le modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="73d78-201">There is no streaming support for the basic SQL operations when you use the WCF service model.</span></span> <span data-ttu-id="73d78-202">Si votre requête retourne un jeu d’enregistrements volumineux, vous pourrez peut-être améliorer les performances en utilisant le modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="73d78-202">If your query returns a large record set, you might be able to improve performance by using the WCF channel model.</span></span> <span data-ttu-id="73d78-203">Pour plus d’informations, consultez [Limitations d’appeler les opérations SQL de base en utilisant le modèle de Service WCF](#BKMK_LimitationsInvoking).</span><span class="sxs-lookup"><span data-stu-id="73d78-203">For more information, see [Limitations of Invoking the Basic SQL Operations by Using the WCF Service Model](#BKMK_LimitationsInvoking).</span></span>  
  
 <span data-ttu-id="73d78-204">Le code suivant illustre une opération de sélection qui cible la table ACCOUNTACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="73d78-204">The following code shows a Select operation that targets the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="73d78-205">Les enregistrements retournés sont écrites dans la console.</span><span class="sxs-lookup"><span data-stu-id="73d78-205">The returned records are written to the console.</span></span>  
  
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
>  <span data-ttu-id="73d78-206">Ce code omet les étapes pour créer, configurer et ouvrez l’instance de client WCF.</span><span class="sxs-lookup"><span data-stu-id="73d78-206">This code omits steps to create, configure, and open the WCF client instance.</span></span> <span data-ttu-id="73d78-207">Pour obtenir un exemple qui inclut ces étapes, consultez [opération Insert](#BKMK_InsertOperation).</span><span class="sxs-lookup"><span data-stu-id="73d78-207">For an example that includes these steps, see [Insert Operation](#BKMK_InsertOperation).</span></span>  
  
### <a name="update-operation"></a><span data-ttu-id="73d78-208">Opération de mise à jour</span><span class="sxs-lookup"><span data-stu-id="73d78-208">Update Operation</span></span>  
 <span data-ttu-id="73d78-209">Le tableau suivant montre les paramètres pour l’opération de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="73d78-209">The following table shows the parameters for the Update operation.</span></span>  
  
|<span data-ttu-id="73d78-210">JEU D’ENREGISTREMENTS</span><span class="sxs-lookup"><span data-stu-id="73d78-210">RECORDSET</span></span>|<span data-ttu-id="73d78-211">FILTER</span><span class="sxs-lookup"><span data-stu-id="73d78-211">FILTER</span></span>|  
|---------------|------------|  
|<span data-ttu-id="73d78-212">Un enregistrement fortement typée de modèle en fonction du type de ligne de la cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-212">A strongly-typed template record based on the row type of the target.</span></span> <span data-ttu-id="73d78-213">L’enregistrement du modèle spécifie les valeurs de mise à jour pour les lignes de la cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-213">The template record specifies the update values for the target rows.</span></span> <span data-ttu-id="73d78-214">Pour les colonnes de la ligne « nillable », vous pouvez spécifier une valeur null pour indiquer que la colonne ne doit pas mis à jour dans les lignes de la cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-214">For nillable row columns, you can specify a null value to indicate that the column should not be updated in the target rows.</span></span>|<span data-ttu-id="73d78-215">Le contenu d’une clause SQL WHERE qui spécifie les lignes à mettre à jour dans la cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-215">The contents of a SQL WHERE clause that specifies the rows to be updated in the target.</span></span> <span data-ttu-id="73d78-216">Par exemple, « DESCRIPTION = 'Enregistrement Inserted #1' ».</span><span class="sxs-lookup"><span data-stu-id="73d78-216">For example, "DESCRIPTION= 'Inserted Record #1'".</span></span>|  
  
 <span data-ttu-id="73d78-217">L’opération de mise à jour retourne le nombre de lignes supprimées de la cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-217">The Update operation returns the number of rows deleted from the target.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="73d78-218">Dans le modèle de service WCF, l’enregistrement du modèle utilisé dans l’opération de mise à jour est fortement typée.</span><span class="sxs-lookup"><span data-stu-id="73d78-218">In the WCF service model, the template record used in the Update operation is strongly-typed.</span></span> <span data-ttu-id="73d78-219">Si une colonne est « nillable », vous pouvez omettre la colonne à partir de l’opération de mise à jour en définissant sa valeur sur **null** dans l’enregistrement de modèle ; Toutefois, si une colonne n’est pas « nillable », vous devez définir sa valeur dans l’enregistrement du modèle.</span><span class="sxs-lookup"><span data-stu-id="73d78-219">If a column is nillable, you can omit the column from the Update operation by setting its value to **null** in the template record; however, if a column is not nillable, then you must set its value in the template record.</span></span> <span data-ttu-id="73d78-220">Par exemple, si une colonne est une clé primaire, il doit contenir une valeur.</span><span class="sxs-lookup"><span data-stu-id="73d78-220">For example, if a column is a primary key, it must contain a value.</span></span> <span data-ttu-id="73d78-221">Pour plus d’informations, consultez [Limitations d’appeler les opérations SQL de base en utilisant le modèle de Service WCF](#BKMK_LimitationsInvoking).</span><span class="sxs-lookup"><span data-stu-id="73d78-221">For more information, see [Limitations of Invoking the Basic SQL Operations by Using the WCF Service Model](#BKMK_LimitationsInvoking).</span></span>  
  
 <span data-ttu-id="73d78-222">Le code suivant montre une opération de mise à jour qui cible la table ACCOUNTACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="73d78-222">The following code shows an Update operation that targets the ACCOUNTACTIVITY table.</span></span>  
  
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
>  <span data-ttu-id="73d78-223">Ce code omet les étapes pour créer, configurer et ouvrez l’instance de client WCF.</span><span class="sxs-lookup"><span data-stu-id="73d78-223">This code omits steps to create, configure, and open the WCF client instance.</span></span> <span data-ttu-id="73d78-224">Pour obtenir un exemple qui inclut ces étapes, consultez [opération Insert](#BKMK_InsertOperation).</span><span class="sxs-lookup"><span data-stu-id="73d78-224">For an example that includes these steps, see [Insert Operation](#BKMK_InsertOperation).</span></span>  
  
### <a name="delete-operation"></a><span data-ttu-id="73d78-225">Opération de suppression</span><span class="sxs-lookup"><span data-stu-id="73d78-225">Delete Operation</span></span>  
 <span data-ttu-id="73d78-226">Le tableau suivant montre les paramètres pour l’opération de suppression.</span><span class="sxs-lookup"><span data-stu-id="73d78-226">The following table shows the parameters for the Delete operation.</span></span>  
  
|<span data-ttu-id="73d78-227">FILTER</span><span class="sxs-lookup"><span data-stu-id="73d78-227">FILTER</span></span>|  
|------------|  
|<span data-ttu-id="73d78-228">Le contenu d’une clause SQL WHERE qui spécifie les lignes à supprimer de la cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-228">The contents of a SQL WHERE clause that specifies the rows to be deleted from the target.</span></span> <span data-ttu-id="73d78-229">Par exemple, « DESCRIPTION = 'Enregistrement Inserted #1' ».</span><span class="sxs-lookup"><span data-stu-id="73d78-229">For example, "DESCRIPTION= 'Inserted Record #1'".</span></span>|  
  
 <span data-ttu-id="73d78-230">L’opération de suppression retourne le nombre de lignes supprimées de la cible.</span><span class="sxs-lookup"><span data-stu-id="73d78-230">The Delete operation returns the number of rows deleted from the target.</span></span> <span data-ttu-id="73d78-231">Le code suivant montre une opération de suppression qui cible la table ACCOUNTACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="73d78-231">The following code shows a Delete operation that targets the ACCOUNTACTIVITY table.</span></span>  
  
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
>  <span data-ttu-id="73d78-232">Ce code omet les étapes pour créer, configurer et ouvrez l’instance de client WCF.</span><span class="sxs-lookup"><span data-stu-id="73d78-232">This code omits steps to create, configure, and open the WCF client instance.</span></span> <span data-ttu-id="73d78-233">Pour obtenir un exemple qui inclut ces étapes, consultez le [opération Insert](#BKMK_InsertOperation).</span><span class="sxs-lookup"><span data-stu-id="73d78-233">For an example that includes these steps, see the [Insert Operation](#BKMK_InsertOperation).</span></span>  
  
##  <a name="BKMK_LimitationsInvoking"></a><span data-ttu-id="73d78-234">Limitations de l’appel d’opérations SQL de base en utilisant le modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="73d78-234">Limitations of Invoking the Basic SQL Operations by Using the WCF Service Model</span></span>  
 <span data-ttu-id="73d78-235">Les limitations suivantes lorsque vous appelez les opérations SQL de base à l’aide d’un client WCF :</span><span class="sxs-lookup"><span data-stu-id="73d78-235">The following limitations exist when you invoke the basic SQL operations by using a WCF client:</span></span>  
  
-   <span data-ttu-id="73d78-236">**Opération d’insertion.**</span><span class="sxs-lookup"><span data-stu-id="73d78-236">**Insert operation.**</span></span> <span data-ttu-id="73d78-237">Le jeu d’enregistrements utilisé dans une opération d’insertion plusieurs enregistrement est fortement typée et par conséquent inclut toutes les colonnes de la ligne.</span><span class="sxs-lookup"><span data-stu-id="73d78-237">The record set used in a multiple record Insert operation is strongly-typed and therefore includes all row columns.</span></span> <span data-ttu-id="73d78-238">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprète une valeur null dans un enregistrement pour indiquer que la colonne doit être exclue de l’opération d’insertion ; Toutefois, les colonnes non nillable ne peut être exclus, car vous ne peut pas définir une valeur null.</span><span class="sxs-lookup"><span data-stu-id="73d78-238">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprets a null value in a record to mean that the column should be excluded from the Insert operation; however, non-nillable columns cannot be excluded because you cannot set them to a null value.</span></span> <span data-ttu-id="73d78-239">Par conséquent, vous devez spécifier des valeurs pour les colonnes non nillable lorsque vous effectuez une opération d’insertion plusieurs enregistrement.</span><span class="sxs-lookup"><span data-stu-id="73d78-239">Therefore, you must specify values for non-nillable columns when you perform a multiple record Insert operation.</span></span>  
  
-   <span data-ttu-id="73d78-240">**Opération d’insertion.**</span><span class="sxs-lookup"><span data-stu-id="73d78-240">**Insert operation.**</span></span> <span data-ttu-id="73d78-241">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprète un **DbNull** valeur dans une colonne de données « nillable » signifie que la colonne doit être exclue d’une opération d’insertion plusieurs enregistrement.</span><span class="sxs-lookup"><span data-stu-id="73d78-241">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprets a **DbNull** value in a nillable data column to mean that the column should be excluded from a multiple record Insert operation.</span></span> <span data-ttu-id="73d78-242">Cela signifie que vous ne pouvez pas définir une colonne nillable **DbNull** sur la base de données Oracle dans un enregistrement plusieurs opération d’insertion.</span><span class="sxs-lookup"><span data-stu-id="73d78-242">This means that you cannot set a nillable column to **DbNull** on the Oracle database in a multiple record Insert operation.</span></span>  
  
-   <span data-ttu-id="73d78-243">**Opération d’insertion.**</span><span class="sxs-lookup"><span data-stu-id="73d78-243">**Insert operation.**</span></span> <span data-ttu-id="73d78-244">Il n’existe aucune prise en charge la diffusion en continu pour plusieurs opérations d’insertion d’enregistrement qui impliquent un grand jeu d’enregistrements.</span><span class="sxs-lookup"><span data-stu-id="73d78-244">There is no streaming support for multiple record insert operations that involve a large record set.</span></span>  
  
-   <span data-ttu-id="73d78-245">**Opération de mise à jour.**</span><span class="sxs-lookup"><span data-stu-id="73d78-245">**Update operation.**</span></span> <span data-ttu-id="73d78-246">L’enregistrement du modèle utilisé dans une opération de mise à jour est fortement typée et par conséquent inclut toutes les colonnes de la ligne.</span><span class="sxs-lookup"><span data-stu-id="73d78-246">The template record used in an Update operation is strongly-typed and therefore includes all row columns.</span></span> <span data-ttu-id="73d78-247">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprète une valeur null dans cet enregistrement pour indiquer que la colonne doit être exclue de l’opération de mise à jour ; Toutefois, les colonnes non nillable ne peut être exclus, car vous les ne peut pas une valeur null.</span><span class="sxs-lookup"><span data-stu-id="73d78-247">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprets a null value in this record to mean that the column should be excluded from the Update operation; however, non-nillable columns cannot be excluded because you cannot them to a null value.</span></span> <span data-ttu-id="73d78-248">Par conséquent, vous devez spécifier des valeurs pour les colonnes non nillable lorsque vous effectuez une opération de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="73d78-248">Therefore, you must specify values for non-nillable columns when you perform an Update operation.</span></span>  
  
-   <span data-ttu-id="73d78-249">**Opération de mise à jour.**</span><span class="sxs-lookup"><span data-stu-id="73d78-249">**Update operation.**</span></span> <span data-ttu-id="73d78-250">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprète un **DbNull** valeur dans une colonne de données « nillable » dans l’enregistrement du modèle pour indiquer que la colonne doit être exclue de l’opération.</span><span class="sxs-lookup"><span data-stu-id="73d78-250">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprets a **DbNull** value in a nillable data column in the template record to mean that the column should be excluded from the operation.</span></span> <span data-ttu-id="73d78-251">Cela signifie que vous ne pouvez pas définir une colonne nillable **DbNull** sur la base de données Oracle à l’aide de l’opération de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="73d78-251">This means that you cannot set a nillable column to **DbNull** on the Oracle database by using the Update operation.</span></span>  
  
-   <span data-ttu-id="73d78-252">**Sélectionnez l’opération.**</span><span class="sxs-lookup"><span data-stu-id="73d78-252">**Select operation.**</span></span> <span data-ttu-id="73d78-253">Il n’existe aucune prise en charge la diffusion en continu pour les requêtes SELECT qui retournent un jeu d’enregistrements volumineux.</span><span class="sxs-lookup"><span data-stu-id="73d78-253">There is no streaming support for SELECT queries that return a large record set.</span></span>  
  
 <span data-ttu-id="73d78-254">Pour les scénarios où les limitations de posent des problèmes, vous pouvez appeler l’opération à l’aide du modèle de canal WCF, car :</span><span class="sxs-lookup"><span data-stu-id="73d78-254">For scenarios where these limitations present challenges, you can invoke the operation by using the WCF channel model because:</span></span>  
  
-   <span data-ttu-id="73d78-255">À l’aide du modèle de canal WCF, vous pouvez exclure des colonnes de données spécifiques des opérations Update et Insert.</span><span class="sxs-lookup"><span data-stu-id="73d78-255">By using the WCF channel model, you can exclude specific data columns from Update and Insert operations.</span></span>  
  
-   <span data-ttu-id="73d78-256">Le modèle de canal WCF prend en charge de diffusion en continu au niveau du nœud pour les opérations SQL de base qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose.</span><span class="sxs-lookup"><span data-stu-id="73d78-256">The WCF channel model provides node-level streaming support for the basic SQL operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes.</span></span>  
  
 <span data-ttu-id="73d78-257">Pour plus d’informations sur l’utilisation du modèle de canal WCF avec les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [développer Oracle de base de données Applications à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md).</span><span class="sxs-lookup"><span data-stu-id="73d78-257">For more information about using the WCF channel model with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Develop Oracle Database Applications Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73d78-258">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73d78-258">See Also</span></span>  
 [<span data-ttu-id="73d78-259">Développer des Applications de base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="73d78-259">Develop Oracle Database Applications Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)
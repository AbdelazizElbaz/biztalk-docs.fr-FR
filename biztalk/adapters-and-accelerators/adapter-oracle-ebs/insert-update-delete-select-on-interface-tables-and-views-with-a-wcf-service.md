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
# <a name="insert-update-delete-or-select-operations-on-interface-tables-and-views-using-the-wcf-service-model"></a><span data-ttu-id="1f6f6-102">Insérer, mettre à jour, supprimer ou sélectionner des opérations sur les tables d’interface et les vues à l’aide du modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="1f6f6-102">Insert, update, delete, or select operations on interface tables and views using the WCF service model</span></span>
<span data-ttu-id="1f6f6-103">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] détecte un ensemble d’opérations de base sur les tables d’interface Insert, Select, Update et Delete.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] discovers a set of basic Insert, Select, Update, and Delete operations on interface tables.</span></span> <span data-ttu-id="1f6f6-104">À l’aide de ces opérations, vous pouvez effectuer une simple Insert, Select, Update et supprimer les instructions qualifiées par une clause WHERE sur une table d’interface cible.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-104">By using these operations, you can perform simple Insert, Select, Update, and Delete statements qualified by a WHERE clause on a target interface table.</span></span> <span data-ttu-id="1f6f6-105">Cette rubrique fournit des instructions sur la façon d’effectuer ces opérations à l’aide du modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-105">This topic provides instructions on how to perform these operations using the WCF service model.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f6f6-106">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge sélectionner uniquement les opérations sur les vues de l’interface.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-106">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports only Select operations on interface views.</span></span>  
  
 <span data-ttu-id="1f6f6-107">Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [opérations sur les Tables d’Interface et les vues de l’Interface](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md).</span><span class="sxs-lookup"><span data-stu-id="1f6f6-107">For more information about how the adapter supports these operations, see [Operations on Interface Tables and Interface Views](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="1f6f6-108">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="1f6f6-108">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="1f6f6-109">L’exemple de cette rubrique effectue des opérations sur la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-109">The example in this topic performs operations on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="1f6f6-110">La table est créée en exécutant le script fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-110">The table is created by running the script provided with the samples.</span></span> <span data-ttu-id="1f6f6-111">Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="1f6f6-111">For more information about samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="1f6f6-112">Un exemple, **Interface_Table_Ops**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-112">A sample, **Interface_Table_Ops**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="1f6f6-113">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="1f6f6-113">The WCF Client Class</span></span>  
 <span data-ttu-id="1f6f6-114">Le nom du client WCF généré pour les opérations de base qui le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] détecte est basé sur le nom de la table ou vue, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-114">The name of the WCF client generated for the basic operations that the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] discovers is based on the name of the table or view, as listed in the following table.</span></span>  
  
|<span data-ttu-id="1f6f6-115">Artefact</span><span class="sxs-lookup"><span data-stu-id="1f6f6-115">Artifact</span></span>|<span data-ttu-id="1f6f6-116">Nom de Client WCF</span><span class="sxs-lookup"><span data-stu-id="1f6f6-116">WCF Client Name</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="1f6f6-117">Tables d’interface</span><span class="sxs-lookup"><span data-stu-id="1f6f6-117">Interface tables</span></span>|<span data-ttu-id="1f6f6-118">InterfaceTables_ [nom_application] _ [schéma]\_[nom_table] Client</span><span class="sxs-lookup"><span data-stu-id="1f6f6-118">InterfaceTables_[APP_NAME]_[SCHEMA]\_[TABLE_NAME]Client</span></span>|  
|<span data-ttu-id="1f6f6-119">Vues de l’interface</span><span class="sxs-lookup"><span data-stu-id="1f6f6-119">Interface views</span></span>|<span data-ttu-id="1f6f6-120">InterfaceViews_ [nom_application] _ [schéma]\_[VIEW_NAME] Client</span><span class="sxs-lookup"><span data-stu-id="1f6f6-120">InterfaceViews_[APP_NAME]_[SCHEMA]\_[VIEW_NAME]Client</span></span>|  
  
 <span data-ttu-id="1f6f6-121">[Nom_application] = nom réel de l’application Oracle E-Business Suite ; par exemple, trver aide.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-121">[APP_NAME] = Actual name of the Oracle E-Business Suite application; for example, FND.</span></span>  
  
 <span data-ttu-id="1f6f6-122">[Schéma] = la Collection d’artefacts ; par exemple, il s’agit d’applications.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-122">[SCHEMA] = Collection of artifacts; for example, APPS.</span></span>  
  
 <span data-ttu-id="1f6f6-123">[Nom_table] = nom de la table ; par exemple, MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-123">[TABLE_NAME] = The name of the table; for example, MS_SAMPLE_EMPLOYEE.</span></span>  
  
 <span data-ttu-id="1f6f6-124">[VIEW_NAME] = le nom de la vue ; par exemple, MS_SAMPLE_EMPLOYEE_View.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-124">[VIEW_NAME] = The name of the view; for example, MS_SAMPLE_EMPLOYEE_View.</span></span>  
  
### <a name="method-signature-for-invoking-operations-on-tables"></a><span data-ttu-id="1f6f6-125">Signature de méthode pour appeler des opérations sur les Tables</span><span class="sxs-lookup"><span data-stu-id="1f6f6-125">Method Signature for Invoking Operations on Tables</span></span>  
 <span data-ttu-id="1f6f6-126">Le tableau suivant montre les signatures de méthode pour les opérations de base sur une table.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-126">The following table shows the method signatures for the basic operations on an table.</span></span> <span data-ttu-id="1f6f6-127">Les signatures sont identiques pour une vue, à ceci près que le nom et l’espace de noms de vue remplacent ceux de la table.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-127">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="1f6f6-128">Opération</span><span class="sxs-lookup"><span data-stu-id="1f6f6-128">Operation</span></span>|<span data-ttu-id="1f6f6-129">Signature de méthode</span><span class="sxs-lookup"><span data-stu-id="1f6f6-129">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="1f6f6-130">Insert</span><span class="sxs-lookup"><span data-stu-id="1f6f6-130">Insert</span></span>|<span data-ttu-id="1f6f6-131">chaîne Insert (InsertRecord [] RECORDSET ;)</span><span class="sxs-lookup"><span data-stu-id="1f6f6-131">string Insert(InsertRecord[] RECORDSET);</span></span>|  
|<span data-ttu-id="1f6f6-132">Select</span><span class="sxs-lookup"><span data-stu-id="1f6f6-132">Select</span></span>|<span data-ttu-id="1f6f6-133">SelectRecord [] sélectionnez (chaîne les noms de colonne, chaîne de filtre) ;</span><span class="sxs-lookup"><span data-stu-id="1f6f6-133">SelectRecord[] Select(string COLUMN_NAMES, string FILTER);</span></span>|  
|<span data-ttu-id="1f6f6-134">Update</span><span class="sxs-lookup"><span data-stu-id="1f6f6-134">Update</span></span>|<span data-ttu-id="1f6f6-135">chaîne de mise à jour (UpdateRecord RECORDSET, chaîne de filtre) ;</span><span class="sxs-lookup"><span data-stu-id="1f6f6-135">string Update(UpdateRecord RECORDSET, string FILTER);</span></span>|  
|<span data-ttu-id="1f6f6-136">DELETE</span><span class="sxs-lookup"><span data-stu-id="1f6f6-136">Delete</span></span>|<span data-ttu-id="1f6f6-137">chaîne Delete (chaîne de filtre) ;</span><span class="sxs-lookup"><span data-stu-id="1f6f6-137">string Delete(string FILTER);</span></span>|  
  
 <span data-ttu-id="1f6f6-138">Par exemple, le code suivant illustre les signatures de méthode pour une classe de client WCF généré pour la supprimer, insérer, sélectionner et mettre à jour des opérations sur la table d’interface MS_SAMPLE_EMPLOYEE sous le schéma d’applications par défaut.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-138">As an example, the following code shows the method signatures for a WCF client class generated for the Delete, Insert, Select and Update operations on the MS_SAMPLE_EMPLOYEE interface table under the default APPS schema.</span></span>  
  
```  
public partial class InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient : System.ServiceModel.ClientBase<InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE>, InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE {      
    public SelectRecord[] Select(string COLUMN_NAMES, string FILTER);  
  
    public string Insert(InsertRecord[] RECORDSET);  
  
    public string Update(UpdateRecord RECORDSET, string FILTER);  
  
    public string Delete(string FILTER);  
}  
```  
  
 <span data-ttu-id="1f6f6-139">Dans cet extrait de code, **InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient** est le nom de la classe WCF dans le OracleEBSBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f6f6-139">In this snippet, **InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient** is the name of the WCF class in the OracleEBSBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
### <a name="parameters-for-table-operations"></a><span data-ttu-id="1f6f6-140">Paramètres pour les opérations de Table</span><span class="sxs-lookup"><span data-stu-id="1f6f6-140">Parameters for Table Operations</span></span>  
 <span data-ttu-id="1f6f6-141">Cette section fournit les paramètres requis par chaque opération de table</span><span class="sxs-lookup"><span data-stu-id="1f6f6-141">This section provides the parameters required by each table operation</span></span>  
  
 <span data-ttu-id="1f6f6-142">**Sélectionnez l’opération**</span><span class="sxs-lookup"><span data-stu-id="1f6f6-142">**Select Operation**</span></span>  
  
|<span data-ttu-id="1f6f6-143">NOMS DE COLONNE</span><span class="sxs-lookup"><span data-stu-id="1f6f6-143">COLUMN_NAMES</span></span>|<span data-ttu-id="1f6f6-144">FILTER</span><span class="sxs-lookup"><span data-stu-id="1f6f6-144">FILTER</span></span>|  
|-------------------|------------|  
|<span data-ttu-id="1f6f6-145">Une liste délimitée par des virgules de noms de colonnes dans la cible. par exemple, « EMP_NO, désignation ».</span><span class="sxs-lookup"><span data-stu-id="1f6f6-145">A comma-delimited list of column names in the target; for example, "EMP_NO, DESIGNATION".</span></span> <span data-ttu-id="1f6f6-146">La liste de colonnes spécifie les colonnes de la cible doit être retournée dans le jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-146">The column list specifies the columns of the target that should be returned in the result set.</span></span> <span data-ttu-id="1f6f6-147">Colonnes non spécifiées dans la liste des colonnes seront fixés à leurs valeurs par défaut de .NET dans le jeu d’enregistrements retourné.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-147">Columns not specified in the column list will be set to their .NET default values in the returned record set.</span></span> <span data-ttu-id="1f6f6-148">Pour les colonnes « nillable », cette valeur est **null**.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-148">For nillable columns, this value is **null**.</span></span>|<span data-ttu-id="1f6f6-149">Le contenu d’une clause WHERE qui spécifie les lignes de la cible de la requête. par exemple, « désignation = 'Manager' ».</span><span class="sxs-lookup"><span data-stu-id="1f6f6-149">The contents of a WHERE clause that specifies the target rows of the query; for example, "Designation = 'Manager'".</span></span> <span data-ttu-id="1f6f6-150">Vous pouvez définir ce paramètre **null** renvoie toutes les lignes de la cible.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-150">You can set this parameter to **null** to return all rows of the target.</span></span>|  
  
 <span data-ttu-id="1f6f6-151">La valeur de retour pour une opération de sélection est un jeu de résultats de fortement typé qui contient les colonnes spécifiées et les lignes.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-151">The return value for a Select operation is a strongly-typed result set that contains the specified columns and rows.</span></span>  
  
 <span data-ttu-id="1f6f6-152">**Opération d’insertion**</span><span class="sxs-lookup"><span data-stu-id="1f6f6-152">**Insert Operation**</span></span>  
  
|<span data-ttu-id="1f6f6-153">Insérer le type d’opération</span><span class="sxs-lookup"><span data-stu-id="1f6f6-153">Insert operation type</span></span>|<span data-ttu-id="1f6f6-154">JEU D’ENREGISTREMENTS</span><span class="sxs-lookup"><span data-stu-id="1f6f6-154">RECORDSET</span></span>|  
|---------------------------|---------------|  
|<span data-ttu-id="1f6f6-155">Enregistrement de plusieurs</span><span class="sxs-lookup"><span data-stu-id="1f6f6-155">Multiple record</span></span>|<span data-ttu-id="1f6f6-156">Collection de INSERTRECORDS doivent être insérés dans la table.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-156">A collection of INSERTRECORDS that should be inserted into the table.</span></span>|  
  
 <span data-ttu-id="1f6f6-157">La valeur de retour pour une opération d’insertion est le nombre de lignes insérées.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-157">The return value for an Insert operation is the number of rows inserted.</span></span>  
  
 <span data-ttu-id="1f6f6-158">**Opération de mise à jour**</span><span class="sxs-lookup"><span data-stu-id="1f6f6-158">**Update Operation**</span></span>  
  
|<span data-ttu-id="1f6f6-159">JEU D’ENREGISTREMENTS</span><span class="sxs-lookup"><span data-stu-id="1f6f6-159">RECORDSET</span></span>|<span data-ttu-id="1f6f6-160">FILTER</span><span class="sxs-lookup"><span data-stu-id="1f6f6-160">FILTER</span></span>|  
|---------------|------------|  
|<span data-ttu-id="1f6f6-161">Une collection d’enregistrements qui doivent être mis à jour dans la table.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-161">A collection of records that should be updated in the table.</span></span>|<span data-ttu-id="1f6f6-162">Le contenu d’une clause WHERE qui spécifie les lignes de la cible de la requête. par exemple, « désignation = 'Manager' ».</span><span class="sxs-lookup"><span data-stu-id="1f6f6-162">The contents of a WHERE clause that specifies the target rows of the query; for example, "Designation = 'Manager'".</span></span> <span data-ttu-id="1f6f6-163">Vous pouvez définir ce paramètre **null** renvoie toutes les lignes de la cible.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-163">You can set this parameter to **null** to return all rows of the target.</span></span>|  
  
 <span data-ttu-id="1f6f6-164">La valeur de retour pour une opération de mise à jour est le nombre de lignes mises à jour.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-164">The return value for an Update operation is the number of rows updated.</span></span>  
  
 <span data-ttu-id="1f6f6-165">**L’opération de suppression**</span><span class="sxs-lookup"><span data-stu-id="1f6f6-165">**Delete Operation**</span></span>  
  
 <span data-ttu-id="1f6f6-166">L’opération Delete prend comme entrée une clause WHERE qui spécifie les lignes à supprimer.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-166">The Delete operation takes as input a WHERE clause that specifies the rows to be deleted.</span></span> <span data-ttu-id="1f6f6-167">La valeur de retour pour une opération de suppression est le nombre de lignes supprimées.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-167">The return value for a Delete operation is the number of rows deleted.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-interface-tables-and-interface-views"></a><span data-ttu-id="1f6f6-168">Création d’un Client WCF pour appeler des opérations sur les Tables d’Interface et les vues de l’Interface</span><span class="sxs-lookup"><span data-stu-id="1f6f6-168">Creating a WCF Client to Invoke Operations on Interface Tables and Interface Views</span></span>  
 <span data-ttu-id="1f6f6-169">L’ensemble générique des actions requises pour effectuer une opération sur Oracle E-Business Suite à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de canal WCF avec l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="1f6f6-169">The generic set of actions required to perform an operation on Oracle E-Business Suite using a WCF client involves a set of tasks described in [Overview of the WCF channel model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md).</span></span> <span data-ttu-id="1f6f6-170">Cette section décrit comment créer un client WCF pour appeler base Insert, Select, Update, les opérations de suppression sur une table d’interface.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-170">This section describes how to create a WCF client to invoke basic Insert, Select, Update, Delete operations on an interface table.</span></span>  
  
#### <a name="to-create-a-wcf-client-to-perform-operations-on-tables"></a><span data-ttu-id="1f6f6-171">Pour créer un client WCF pour effectuer des opérations sur les tables</span><span class="sxs-lookup"><span data-stu-id="1f6f6-171">To create a WCF client to perform operations on tables</span></span>  
  
1.  <span data-ttu-id="1f6f6-172">Créez un projet Visual c# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-172">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="1f6f6-173">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-173">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="1f6f6-174">Générer la classe de client WCF pour Insert, Select, Update et sur la table d’interface MS_SAMPLE_EMPLOYEE l’opération de suppression.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-174">Generate the WCF client class for the Insert, Select, Update, and Delete operation on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="1f6f6-175">Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="1f6f6-175">For more information about generating a WCF client class, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1f6f6-176">Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-176">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="1f6f6-177">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleEBS` et `Microsoft.ServiceModel.Channels`.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-177">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="1f6f6-178">Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="1f6f6-178">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
5.  <span data-ttu-id="1f6f6-179">Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-179">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
    InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient client = new InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient(binding, address);  
    ```  
  
     <span data-ttu-id="1f6f6-180">Dans cet extrait de code, `InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient` est le client WCF défini dans OracleEBSBindingClient.cs.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-180">In this snippet, `InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient` is the WCF client defined in OracleEBSBindingClient.cs.</span></span> <span data-ttu-id="1f6f6-181">Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f6f6-181">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1f6f6-182">Dans cet extrait de code, vous spécifiez explicitement l’adresse de liaison et le point de terminaison dans votre code d’application.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-182">In this snippet, you explicitly specify the binding and endpoint address in your application code.</span></span> <span data-ttu-id="1f6f6-183">Vous pouvez utiliser ces valeurs à partir du fichier de configuration d’application, app.config, également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f6f6-183">You can use these values from the application configuration file, app.config, also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="1f6f6-184">Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer un client de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="1f6f6-184">For more information on the different ways of specifying client binding, see [Configure a client binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  
  
6.  <span data-ttu-id="1f6f6-185">Définir les informations d’identification pour le client.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-185">Set the credentials for the client.</span></span>  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
7.  <span data-ttu-id="1f6f6-186">Étant donné que vous effectuez une opération sur une table d’interface, vous devez définir le contexte d’application.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-186">Because you are performing an operation on an interface table, you must set the application context.</span></span> <span data-ttu-id="1f6f6-187">Dans cet exemple, pour définir le contexte d’application, que vous spécifiez la **OracleUserName**, **OraclePassword**, et **OracleEBSResponsibilityName** propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-187">In this example, to set the application context, you specify the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="1f6f6-188">Pour plus d’informations sur le contexte de l’application, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span><span class="sxs-lookup"><span data-stu-id="1f6f6-188">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
8.  <span data-ttu-id="1f6f6-189">Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="1f6f6-189">Open the client as described in the snippet below:</span></span>  
  
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
  
9. <span data-ttu-id="1f6f6-190">Appeler l’opération d’insertion sur la table MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-190">Invoke the Insert operation on the MS_SAMPLE_EMPLOYEE table.</span></span>  
  
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
  
     <span data-ttu-id="1f6f6-191">Vous pouvez remplacer l’extrait de code précédent pour exécuter Select, Update ou Delete ainsi les opérations.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-191">You can replace the preceding code snippet to perform Select, Update, or Delete operations as well.</span></span> <span data-ttu-id="1f6f6-192">Vous pouvez également ajouter des extraits de code pour effectuer toutes les opérations dans une application unique.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-192">You can also append the code snippets to perform all operation in a single application.</span></span> <span data-ttu-id="1f6f6-193">Extraits de code sur la façon d’effectuer ces opérations, consultez [sélectionner une opération](#BKMK_Select), [opération de mise à jour](#BKMK_Update), et [opération Delete](#BKMK_Delete) respectivement.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-193">For code snippets on how to perform these operations, see [Select Operation](#BKMK_Select), [Update Operation](#BKMK_Update), and [Delete Operation](#BKMK_Delete) respectively.</span></span>  
  
10. <span data-ttu-id="1f6f6-194">Fermez le client, comme décrit dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="1f6f6-194">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
11. <span data-ttu-id="1f6f6-195">Générez le projet et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-195">Build the project and then run it.</span></span> <span data-ttu-id="1f6f6-196">L’application insère un enregistrement dans la table MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-196">The application inserts a record in the MS_SAMPLE_EMPLOYEE table.</span></span>  
  
###  <a name="BKMK_Select"></a><span data-ttu-id="1f6f6-197">Sélectionnez l’opération</span><span class="sxs-lookup"><span data-stu-id="1f6f6-197">Select Operation</span></span>  
 <span data-ttu-id="1f6f6-198">Le code suivant illustre une opération de sélection qui cible la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-198">The following code shows a Select operation that targets the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="1f6f6-199">L’opération Select sélectionne le dernier enregistrement inséré dans la table.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-199">The Select operation selects the last record inserted into the table.</span></span> <span data-ttu-id="1f6f6-200">L’enregistrement retourné est écrit dans la console.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-200">The returned record is written to the console.</span></span>  
  
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
  
###  <a name="BKMK_Update"></a><span data-ttu-id="1f6f6-201">Opération de mise à jour</span><span class="sxs-lookup"><span data-stu-id="1f6f6-201">Update Operation</span></span>  
 <span data-ttu-id="1f6f6-202">Le code suivant montre une opération de mise à jour qui cible la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-202">The following code shows an Update operation that targets the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
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
  
###  <a name="BKMK_Delete"></a><span data-ttu-id="1f6f6-203">L’opération de suppression</span><span class="sxs-lookup"><span data-stu-id="1f6f6-203">Delete Operation</span></span>  
 <span data-ttu-id="1f6f6-204">Le code suivant montre une opération de suppression qui cible la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="1f6f6-204">The following code shows a Delete operation that targets the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1f6f6-205">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f6f6-205">See Also</span></span>  
 [<span data-ttu-id="1f6f6-206">Développer des applications d’Oracle E-Business Suite à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="1f6f6-206">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)
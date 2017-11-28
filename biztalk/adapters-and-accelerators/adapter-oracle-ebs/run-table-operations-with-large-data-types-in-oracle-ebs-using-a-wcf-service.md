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
ms.openlocfilehash: b671f8fc124875eb5eadf119188d0ffe4c1a2a3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="complete-operations-on-tables-with-large-data-types-in-oracle-e-business-suite-using-the-wcf-service-model"></a><span data-ttu-id="85e36-102">Effectuer des opérations sur les tables avec des types de données de grande taille dans Oracle E-Business Suite à l’aide du modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="85e36-102">Complete operations on tables with large data types in Oracle E-Business Suite using the WCF service model</span></span>
<span data-ttu-id="85e36-103">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] permet aux clients d’adaptateur effectuer des opérations sur les tables de l’interface et de vues avec les types de données de grande taille telles que les objets BLOB, CLOB, NCLOB et BFILE.</span><span class="sxs-lookup"><span data-stu-id="85e36-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] enables adapter clients to perform operations on interface tables and views with large data types such as BLOB, CLOB, NCLOB, and BFILE.</span></span>  
  
-   <span data-ttu-id="85e36-104">Pour les colonnes de type BLOB, CLOB et NCLOB, l’adaptateur permet aux clients de lire ainsi que de mettre à jour des données.</span><span class="sxs-lookup"><span data-stu-id="85e36-104">For columns of type BLOB, CLOB, and NCLOB, the adapter enables clients to read as well as update data.</span></span> <span data-ttu-id="85e36-105">L’adaptateur expose Read_\<*LOBColName*> et en attente_\<*LOBColName*> operations pour lire et mettre à jour les données respectivement, où \< *LOBColName*> est le nom de colonne avec le type de données de grande taille.</span><span class="sxs-lookup"><span data-stu-id="85e36-105">The adapter exposes Read_\<*LOBColName*> and Update_\<*LOBColName*> operations to read and update data respectively, where \<*LOBColName*> is the name of column with large data type.</span></span> <span data-ttu-id="85e36-106">S’il existe plusieurs colonnes avec le type de données de grande taille dans une table d’une interface unique, l’adaptateur expose la plupart lire et mettre à jour des opérations pour cette table d’interface.</span><span class="sxs-lookup"><span data-stu-id="85e36-106">If there is more than one column with large data type in a single interface table, the adapter exposes as many read and update operations for that interface table.</span></span>  
  
-   <span data-ttu-id="85e36-107">Pour les colonnes de type BFILE, les clients de l’adaptateur peuvent uniquement lire les données.</span><span class="sxs-lookup"><span data-stu-id="85e36-107">For columns of type BFILE, adapter clients can only read data.</span></span> <span data-ttu-id="85e36-108">L’adaptateur expose Read_\<*LOBColName*> opération lire les données des colonnes de type BFILE.</span><span class="sxs-lookup"><span data-stu-id="85e36-108">The adapter exposes Read_\<*LOBColName*> operation to read data from columns of BFILE type.</span></span> <span data-ttu-id="85e36-109">S’il existe plusieurs colonnes avec le type de données de grande taille dans une table d’une interface unique, l’adaptateur expose plusieurs opérations de lecture pour la table d’interface.</span><span class="sxs-lookup"><span data-stu-id="85e36-109">If there is more than one column with large data type in a single interface table, the adapter exposes as many read operations for the interface table.</span></span>  
  
 <span data-ttu-id="85e36-110">Pour plus d’informations sur ces opérations, consultez [opérations sur les Tables d’Interface, les vues de l’Interface, les Tables et les vues que contiennent LOB des données](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="85e36-110">For more information about these operations, see [Operations on Interface Tables, Interface Views, Tables, and Views That Contain LOB Data](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="85e36-111">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="85e36-111">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="85e36-112">L’exemple dans cette rubrique met à jour une colonne BLOB (PHOTO) dans la table de base de données client et puis récupère les données de la même colonne.</span><span class="sxs-lookup"><span data-stu-id="85e36-112">The example in this topic updates a BLOB column (PHOTO) in the CUSTOMER database table and then retrieves the data from the same column.</span></span> <span data-ttu-id="85e36-113">La table est créée en exécutant le script fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="85e36-113">The table is created by running the script provided with the samples.</span></span> <span data-ttu-id="85e36-114">Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="85e36-114">For more information about samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="85e36-115">Un exemple, **LargeDataTypes_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="85e36-115">A sample, **LargeDataTypes_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85e36-116">Cette rubrique répertorie les tâches détaillées pour la mise à jour et la lecture des colonnes de types de données de grande taille dans une table de base de données.</span><span class="sxs-lookup"><span data-stu-id="85e36-116">This topic lists detailed tasks for updating and reading columns of large data types in a base database table.</span></span> <span data-ttu-id="85e36-117">Vous devez effectuer le même ensemble de tâches de mise à jour et de lire les colonnes de types de données de grande taille dans une table d’interface.</span><span class="sxs-lookup"><span data-stu-id="85e36-117">You must perform the same set of tasks for updating and reading columns of large data types in an interface table.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="85e36-118">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="85e36-118">The WCF Client Class</span></span>  
 <span data-ttu-id="85e36-119">Le nom du client WCF généré pour les opérations sur les tables avec des types de données de grande taille par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est basé sur le nom de la table, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="85e36-119">The name of the WCF client generated for the operations on tables with large data types by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is based on the name of the table, as listed in the following table.</span></span>  
  
|<span data-ttu-id="85e36-120">Artefact</span><span class="sxs-lookup"><span data-stu-id="85e36-120">Artifact</span></span>|<span data-ttu-id="85e36-121">Nom de Client WCF</span><span class="sxs-lookup"><span data-stu-id="85e36-121">WCF Client Name</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="85e36-122">Tables d’interface</span><span class="sxs-lookup"><span data-stu-id="85e36-122">Interface tables</span></span>|<span data-ttu-id="85e36-123">InterfaceTables_ [nom_application] _ [schéma]\_[nom_table] Client</span><span class="sxs-lookup"><span data-stu-id="85e36-123">InterfaceTables_[APP_NAME]_[SCHEMA]\_[TABLE_NAME]Client</span></span>|  
  
 <span data-ttu-id="85e36-124">[Nom_application] = nom réel de l’application Oracle E-Business Suite ; par exemple, trver aide.</span><span class="sxs-lookup"><span data-stu-id="85e36-124">[APP_NAME] = Actual name of the Oracle E-Business Suite application; for example, FND.</span></span>  
  
 <span data-ttu-id="85e36-125">[Schéma] = la Collection d’artefacts ; par exemple, il s’agit d’applications.</span><span class="sxs-lookup"><span data-stu-id="85e36-125">[SCHEMA] = Collection of artifacts; for example, APPS.</span></span>  
  
 <span data-ttu-id="85e36-126">[Nom_table] = nom de la table ; par exemple, MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="85e36-126">[TABLE_NAME] = The name of the table; for example, MS_SAMPLE_EMPLOYEE.</span></span>  
  
 <span data-ttu-id="85e36-127">[VIEW_NAME] = le nom de la vue ; par exemple, MS_SAMPLE_EMPLOYEE_View.</span><span class="sxs-lookup"><span data-stu-id="85e36-127">[VIEW_NAME] = The name of the view; for example, MS_SAMPLE_EMPLOYEE_View.</span></span>  
  
### <a name="method-signature-for-invoking-operations-on-tables"></a><span data-ttu-id="85e36-128">Signature de méthode pour appeler des opérations sur les Tables</span><span class="sxs-lookup"><span data-stu-id="85e36-128">Method Signature for Invoking Operations on Tables</span></span>  
 <span data-ttu-id="85e36-129">Le tableau suivant montre les signatures de méthode pour les opérations de base sur une table.</span><span class="sxs-lookup"><span data-stu-id="85e36-129">The following table shows the method signatures for the basic operations on a table.</span></span> <span data-ttu-id="85e36-130">Les signatures sont identiques pour une vue, à ceci près que le nom et l’espace de noms de vue remplacent ceux de la table.</span><span class="sxs-lookup"><span data-stu-id="85e36-130">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="85e36-131">Opération</span><span class="sxs-lookup"><span data-stu-id="85e36-131">Operation</span></span>|<span data-ttu-id="85e36-132">Signature de méthode</span><span class="sxs-lookup"><span data-stu-id="85e36-132">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="85e36-133">En attente_\<*nom_colonne*></span><span class="sxs-lookup"><span data-stu-id="85e36-133">Update_\<*column_name*></span></span>|<span data-ttu-id="85e36-134">public void en attente_\<*column_name*> (filtre, byte [] données de chaîne) ;</span><span class="sxs-lookup"><span data-stu-id="85e36-134">public void Update_\<*column_name*>(string FILTER, byte[] DATA);</span></span>|  
|<span data-ttu-id="85e36-135">Read_\<*nom_colonne*></span><span class="sxs-lookup"><span data-stu-id="85e36-135">Read_\<*column_name*></span></span>|<span data-ttu-id="85e36-136">public System.IO.Stream Read_\<*column_name*>(string FILTER) ;</span><span class="sxs-lookup"><span data-stu-id="85e36-136">public System.IO.Stream Read_\<*column_name*>(string FILTER);</span></span>|  
  
 <span data-ttu-id="85e36-137">Par exemple, le code suivant montre les signatures de méthode pour une classe de client WCF généré pour les opérations Update_PHOTO et Read_PHOTO sur la table de base de données client sous le schéma d’applications.</span><span class="sxs-lookup"><span data-stu-id="85e36-137">As an example, the following code shows the method signatures for a WCF client class generated for the Update_PHOTO and Read_PHOTO operations on the CUSTOMER database table under the APPS schema.</span></span>  
  
```  
public partial class Tables_APPS_CUSTOMERClient : System.ServiceModel.ClientBase<Tables_APPS_CUSTOMER>, Tables_APPS_CUSTOMER {      
  
    public void Update_PHOTO(string FILTER, byte[] DATA);  
  
    public System.IO.Stream Read_PHOTO(string FILTER);  
}  
```  
  
 <span data-ttu-id="85e36-138">Dans cet extrait de code, **Tables_APPS_CUSTOMERClient** est le nom de la classe WCF dans le OracleEBSBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85e36-138">In this snippet, **Tables_APPS_CUSTOMERClient** is the name of the WCF class in the OracleEBSBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="85e36-139">Update_PHOTO et Read_PHOTO sont des méthodes qui peuvent être appelés pour mettre à jour et lire des colonnes de types de données de grande taille dans une table.</span><span class="sxs-lookup"><span data-stu-id="85e36-139">Update_PHOTO and Read_PHOTO are methods that can be invoked to update and read columns of large data types in a table.</span></span>  
  
### <a name="parameters-for-table-operations"></a><span data-ttu-id="85e36-140">Paramètres pour les opérations de Table</span><span class="sxs-lookup"><span data-stu-id="85e36-140">Parameters for Table Operations</span></span>  
 <span data-ttu-id="85e36-141">Cette section fournit les paramètres requis par l’en attente_\<*column_name*> et Read_\<*column_name*> opération.</span><span class="sxs-lookup"><span data-stu-id="85e36-141">This section provides the parameters required by the Update_\<*column_name*> and Read_\<*column_name*> operation.</span></span>  
  
|<span data-ttu-id="85e36-142">Nom de l’opération</span><span class="sxs-lookup"><span data-stu-id="85e36-142">Operation name</span></span>|<span data-ttu-id="85e36-143">Paramètres</span><span class="sxs-lookup"><span data-stu-id="85e36-143">Parameters</span></span>|  
|--------------------|----------------|  
|<span data-ttu-id="85e36-144">En attente_\<*nom_colonne*></span><span class="sxs-lookup"><span data-stu-id="85e36-144">Update_\<*column_name*></span></span>|<span data-ttu-id="85e36-145">Requiert les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="85e36-145">Requires the following parameters:</span></span><br /><br /> <span data-ttu-id="85e36-146">-   `string FILTER`.</span><span class="sxs-lookup"><span data-stu-id="85e36-146">-   `string FILTER`.</span></span> <span data-ttu-id="85e36-147">Ce paramètre doit contenir where clause qui dénote l’enregistrement pour lequel des données est mise à jour.</span><span class="sxs-lookup"><span data-stu-id="85e36-147">This parameter must contain the where clause that denotes the record for which data has to be updated.</span></span> <span data-ttu-id="85e36-148">Par exemple, `"WHERE Name='Mindy Martin'"`.</span><span class="sxs-lookup"><span data-stu-id="85e36-148">For example, `"WHERE Name='Mindy Martin'"`.</span></span><br /><span data-ttu-id="85e36-149">-   `byte[] DATA`.</span><span class="sxs-lookup"><span data-stu-id="85e36-149">-   `byte[] DATA`.</span></span> <span data-ttu-id="85e36-150">Contient un tableau d’octets de données à la mise à jour dans une colonne de type de données de grande taille.</span><span class="sxs-lookup"><span data-stu-id="85e36-150">Contains a byte array of data to be update in a column of large data type.</span></span>|  
|<span data-ttu-id="85e36-151">Read_\<*nom_colonne*></span><span class="sxs-lookup"><span data-stu-id="85e36-151">Read_\<*column_name*></span></span>|<span data-ttu-id="85e36-152">Requiert les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="85e36-152">Requires the following parameters:</span></span><br /><br /> <span data-ttu-id="85e36-153">-   `string FILTER`.</span><span class="sxs-lookup"><span data-stu-id="85e36-153">-   `string FILTER`.</span></span> <span data-ttu-id="85e36-154">Ce paramètre doit contenir where clause qui dénote l’enregistrement à partir de laquelle les données doit être lu.</span><span class="sxs-lookup"><span data-stu-id="85e36-154">This parameter must contain the where clause that denotes the record from which the data has to be read.</span></span> <span data-ttu-id="85e36-155">Par exemple, `"WHERE Name='Mindy Martin'"`.</span><span class="sxs-lookup"><span data-stu-id="85e36-155">For example, `"WHERE Name='Mindy Martin'"`.</span></span>|  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-tables-with-columns-of-large-data-types"></a><span data-ttu-id="85e36-156">Création d’un Client WCF pour appeler des opérations sur les Tables avec des colonnes de Types de données volumineuses</span><span class="sxs-lookup"><span data-stu-id="85e36-156">Creating a WCF Client to Invoke Operations on Tables with Columns of Large Data Types</span></span>  
 <span data-ttu-id="85e36-157">L’ensemble générique des actions requises pour effectuer une opération sur Oracle E-Business Suite à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de service WCF avec l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="85e36-157">The generic set of actions required to perform an operation on Oracle E-Business Suite using a WCF client involves a set of tasks described in [Overview of the WCF service model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md).</span></span> <span data-ttu-id="85e36-158">Cette section décrit comment créer un client WCF pour appeler des opérations Update_PHOTO et Read_PHOTO sur une table de base de données client.</span><span class="sxs-lookup"><span data-stu-id="85e36-158">This section describes how to create a WCF client to invoke Update_PHOTO and Read_PHOTO operations on a CUSTOMER database table.</span></span>  
  
#### <a name="to-create-a-wcf-client"></a><span data-ttu-id="85e36-159">Pour créer un client WCF</span><span class="sxs-lookup"><span data-stu-id="85e36-159">To create a WCF client</span></span>  
  
1.  <span data-ttu-id="85e36-160">Créez un projet Visual c# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85e36-160">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="85e36-161">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="85e36-161">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="85e36-162">Générer la classe de client WCF pour les opérations Update_PHOTO et Read_PHOTO sur la table de base de données client.</span><span class="sxs-lookup"><span data-stu-id="85e36-162">Generate the WCF client class for the Update_PHOTO and Read_PHOTO operations on the CUSTOMER database table.</span></span> <span data-ttu-id="85e36-163">Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="85e36-163">For more information about generating a WCF client class, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="85e36-164">Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.</span><span class="sxs-lookup"><span data-stu-id="85e36-164">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="85e36-165">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleEBS` et `Microsoft.ServiceModel.Channels`, `System.Transactions`.</span><span class="sxs-lookup"><span data-stu-id="85e36-165">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS` and `Microsoft.ServiceModel.Channels`, `System.Transactions`.</span></span>  
  
4.  <span data-ttu-id="85e36-166">Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="85e36-166">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
    -   `System.Transactions`  
  
    -   `System.IO`  
  
5.  <span data-ttu-id="85e36-167">Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="85e36-167">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
    ```  
  
              Tables_APPS_CUSTOMERClient client = new Tables_APPS_CUSTOMERClient("OracleEBSBinding_Tables_APPS_CUSTOMER");  
  
    client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     <span data-ttu-id="85e36-168">Dans cet extrait de code, `Tables_APPS_CUSTOMERClient` est le client WCF défini dans OracleEBSBindingClient.cs.</span><span class="sxs-lookup"><span data-stu-id="85e36-168">In this snippet, `Tables_APPS_CUSTOMERClient` is the WCF client defined in OracleEBSBindingClient.cs.</span></span> <span data-ttu-id="85e36-169">Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85e36-169">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85e36-170">Dans cet extrait de code, vous utilisez la liaison et l’adresse de point de terminaison à partir du fichier de configuration app.config. Vous pouvez également spécifier explicitement ces valeurs dans votre code.</span><span class="sxs-lookup"><span data-stu-id="85e36-170">In this snippet, you use the binding and endpoint address from the configuration file app.config. You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="85e36-171">Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer un client de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="85e36-171">For more information on the different ways of specifying client binding, see [Configure a client binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  
  
6.  <span data-ttu-id="85e36-172">Définir les informations d’identification pour le client.</span><span class="sxs-lookup"><span data-stu-id="85e36-172">Set the credentials for the client.</span></span>  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="85e36-173">Dans cet exemple, vous effectuez des opérations sur une table de base de données.</span><span class="sxs-lookup"><span data-stu-id="85e36-173">In this example, you are performing operations on a database table.</span></span> <span data-ttu-id="85e36-174">Toutefois, si vous effectuez des opérations sur une table d’interface, vous devez définir le contexte d’application en spécifiant les valeurs appropriées pour le **OracleUserName**, **OraclePassword**, et  **OracleEBSResponsibilityName** propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="85e36-174">However, if you are performing operations on an interface table, you must set the application context by specifying appropriate values for the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="85e36-175">Vous devez spécifier ces propriétés de la liaison avant d’ouvrir le client.</span><span class="sxs-lookup"><span data-stu-id="85e36-175">You must specify these binding properties before opening the client.</span></span> <span data-ttu-id="85e36-176">Pour plus d’informations sur le contexte de l’application, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span><span class="sxs-lookup"><span data-stu-id="85e36-176">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
7.  <span data-ttu-id="85e36-177">Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="85e36-177">Open the client as described in the snippet below:</span></span>  
  
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
  
8.  <span data-ttu-id="85e36-178">Appelez l’opération Update_PHOTO sur la table CUSTOMER.</span><span class="sxs-lookup"><span data-stu-id="85e36-178">Invoke the Update_PHOTO operation on the CUSTOMER table.</span></span>  
  
     <span data-ttu-id="85e36-179">L’opération Update_PHOTO requiert un tableau d’octets pour les données à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="85e36-179">The Update_PHOTO operation requires a byte array for the data to be updated.</span></span> <span data-ttu-id="85e36-180">Dans cet extrait de code, vous utilisez la classe FileStream pour créer un tableau d’octets pour une photo, SamplePhoto.jpg.</span><span class="sxs-lookup"><span data-stu-id="85e36-180">In this code snippet, you use the FileStream class to create a byte array for a photo, SamplePhoto.jpg.</span></span> <span data-ttu-id="85e36-181">Pour cette application fonctionne, le fichier doit être copié vers le répertoire bin du projet.</span><span class="sxs-lookup"><span data-stu-id="85e36-181">For this application to work, the file must be copied to the project’s bin directory.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="85e36-182">L’opération Update_PHOTO doit être effectuée dans une transaction, afin que la **UseAmbientTransaction** liaison de la propriété doit être définie sur **true** et l’opération Update_PHOTO doit être effectuée au sein d’un étendue de transaction.</span><span class="sxs-lookup"><span data-stu-id="85e36-182">The Update_PHOTO operation must be performed in a transaction, so the **UseAmbientTransaction** binding property must be set to **true** and the Update_PHOTO operation must be performed within a transaction scope.</span></span> <span data-ttu-id="85e36-183">Vous pouvez définir le **UseAmbientTransaction** propriété de liaison dans le fichier app.config ou en définissant explicitement dans votre application en tant que `binding.UseAmbientTransaction = true`.</span><span class="sxs-lookup"><span data-stu-id="85e36-183">You can set the **UseAmbientTransaction** binding property either in the app.config or by explicitly setting it in your application as `binding.UseAmbientTransaction = true`.</span></span> <span data-ttu-id="85e36-184">Notez que si vous spécifiez la propriété de liaison explicitement dans le code, vous devez le faire avant d’ouvrir le client.</span><span class="sxs-lookup"><span data-stu-id="85e36-184">Note that if you are specifying the binding property explicitly in the code, you must do so before opening the client.</span></span>  
  
    ```  
    byte[] photo;  
  
    using (FileStream fs = new FileStream("SamplePhoto.jpg", FileMode.Open))  
    {  
        try  
        {  
            Console.WriteLine("Reading the photo");  
            int count = 0;  
            photo = new byte[fs.Length];  
            while ((count += fs.Read(photo, count, (int)(((fs.Length - count) > 4096) ? 4096 : fs.Length - count))) \< fs.Length) ;  
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
  
9. <span data-ttu-id="85e36-185">Appelez l’opération Read_PHOTO sur la table CUSTOMER.</span><span class="sxs-lookup"><span data-stu-id="85e36-185">Invoke the Read_PHOTO operation on the CUSTOMER table.</span></span>  
  
     <span data-ttu-id="85e36-186">Le Read_PHOTO donne le résultat sous la forme de System.IO.Stream.</span><span class="sxs-lookup"><span data-stu-id="85e36-186">The Read_PHOTO gives the output in the form of System.IO.Stream.</span></span> <span data-ttu-id="85e36-187">Le client de l’adaptateur doit implémenter la classe FileStream pour lire les données à partir de l’opération de Read_PHOTO.</span><span class="sxs-lookup"><span data-stu-id="85e36-187">The adapter client must implement the FileStream class to read the data from Read_PHOTO operation.</span></span> <span data-ttu-id="85e36-188">Une fois l’opération Read_PHOTO est terminée, un fichier PhotoCopy.jpg est copié dans le répertoire bin du projet.</span><span class="sxs-lookup"><span data-stu-id="85e36-188">After the Read_PHOTO operation is complete, a file PhotoCopy.jpg is copied under the project’s bin directory.</span></span>  
  
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
  
10. <span data-ttu-id="85e36-189">Fermez le client, comme décrit dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="85e36-189">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
11. <span data-ttu-id="85e36-190">Générez le projet et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="85e36-190">Build the project and then run it.</span></span> <span data-ttu-id="85e36-191">L’application met à jour la colonne PHOTO de la table CUSTOMER, puis lit le contenu de la colonne PHOTO.</span><span class="sxs-lookup"><span data-stu-id="85e36-191">The application updates the PHOTO column of the CUSTOMER table and then reads the content of the PHOTO column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e36-192">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85e36-192">See Also</span></span>  
 [<span data-ttu-id="85e36-193">Développer des applications d’Oracle E-Business Suite à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="85e36-193">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)
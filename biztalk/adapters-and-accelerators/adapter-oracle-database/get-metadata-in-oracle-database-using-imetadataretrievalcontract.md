---
title: "Obtient les métadonnées de la base de données Oracle à l’aide de IMetadataRetrievalContract | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata, retrieving using IMetadataRetrievalContract
ms.assetid: 7d32694f-4384-4c2f-be72-ac52c7b2e9f5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 132ad3f64d377a3bfcbf7b1b2303e1c0de0c612f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-in-oracle-database-using-imetadataretrievalcontract"></a><span data-ttu-id="3e4ae-102">Obtient les métadonnées de la base de données Oracle à l’aide de IMetadataRetrievalContract</span><span class="sxs-lookup"><span data-stu-id="3e4ae-102">Get Metadata in Oracle Database Using IMetadataRetrievalContract</span></span>
<span data-ttu-id="3e4ae-103">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose un **IMetadataRetrievalContract**point de terminaison que vous pouvez utiliser pour parcourir et rechercher les artefacts de base de données Oracle et récupérer des métadonnées pour les opérations sous la forme d’une Description langage WSDL (Web Services ) document.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] exposes an **IMetadataRetrievalContract**endpoint that you can use to browse and search for Oracle database artifacts and to retrieve metadata for operations in the form of a Web Services Description Language (WSDL) document.</span></span>  
  
 <span data-ttu-id="3e4ae-104">Le **IMetadataRetrievalContract** interface est implémentée par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] et fournit des fonctionnalités de navigation, recherche et la récupération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-104">The **IMetadataRetrievalContract** interface is implemented by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] and provides metadata browse, search, and retrieval capabilities.</span></span> <span data-ttu-id="3e4ae-105">Outre la **IMetadataRetrievalContract** interface, le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] expose le **MetadataRetrievalClient** classe qui implémente l’interface.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-105">In addition to the **IMetadataRetrievalContract** interface, the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] exposes the **MetadataRetrievalClient** class, which implements the interface.</span></span> <span data-ttu-id="3e4ae-106">Vous pouvez utiliser un **IMetadataRetrievalContract** canal ou un **MetadataRetrievalClient** pour manipuler les métadonnées ; les méthodes exposées à parcourir, rechercher et récupérer les métadonnées sont les mêmes dans chaque cas.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-106">You can use either an **IMetadataRetrievalContract** channel or a **MetadataRetrievalClient** to work with metadata; the methods exposed to browse, search, and retrieve metadata are the same in each case.</span></span>  
  
 <span data-ttu-id="3e4ae-107">Les sections suivantes fournissent des informations sur l’utilisation de la **IMetadataRetrievalContract** interface.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-107">The following sections provide information about how to use the **IMetadataRetrievalContract** interface.</span></span>  
  
## <a name="the-imetadataretrievalcontract-interface"></a><span data-ttu-id="3e4ae-108">L’Interface IMetadataRetrievalContract</span><span class="sxs-lookup"><span data-stu-id="3e4ae-108">The IMetadataRetrievalContract Interface</span></span>  
 <span data-ttu-id="3e4ae-109">Le tableau suivant fournit des informations sur les classes importantes qui sont utilisées lorsque vous travaillez avec le **IMetadataRetrievalContract** interface.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-109">The following table provides information about important classes that are used when you work with the **IMetadataRetrievalContract** interface.</span></span>  
  
|<span data-ttu-id="3e4ae-110">Classe ou Interface</span><span class="sxs-lookup"><span data-stu-id="3e4ae-110">Class or Interface</span></span>|<span data-ttu-id="3e4ae-111"> Description</span><span class="sxs-lookup"><span data-stu-id="3e4ae-111">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="3e4ae-112">**IMetadataRetrievalContract** interface</span><span class="sxs-lookup"><span data-stu-id="3e4ae-112">**IMetadataRetrievalContract** interface</span></span><br /><br /> <span data-ttu-id="3e4ae-113">(Microsoft.ServiceModel.Channels)</span><span class="sxs-lookup"><span data-stu-id="3e4ae-113">(Microsoft.ServiceModel.Channels)</span></span>|<span data-ttu-id="3e4ae-114">Définit le **Parcourir**, **recherche**, et **GetMetadata** méthodes.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-114">Defines the **Browse**, **Search**, and **GetMetadata** methods.</span></span> <span data-ttu-id="3e4ae-115">Vous appelez ces méthodes à l’aide d’un **IMetadataRetrievalContract** canal ou un **MetadataRetrievalClient** pour travailler avec les métadonnées de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-115">You invoke these methods either by using an **IMetadataRetrievalContract** channel or a **MetadataRetrievalClient** to work with adapter metadata.</span></span>|  
|<span data-ttu-id="3e4ae-116">**MetadataRetrievalClient** classe</span><span class="sxs-lookup"><span data-stu-id="3e4ae-116">**MetadataRetrievalClient** class</span></span><br /><br /> <span data-ttu-id="3e4ae-117">(Microsoft.ServiceModel.Channels)</span><span class="sxs-lookup"><span data-stu-id="3e4ae-117">(Microsoft.ServiceModel.Channels)</span></span>|<span data-ttu-id="3e4ae-118">Implémente le **IMetadataRetrievalContract** interface.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-118">Implements the **IMetadataRetrievalContract** interface.</span></span> <span data-ttu-id="3e4ae-119">Vous pouvez créer une instance de cette classe et le configurer pour votre base de données Oracle en fournissant une **OracleDBBinding** et un **EndpointAddress**.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-119">You can create an instance of this class and configure it for your Oracle database by providing an **OracleDBBinding** and an **EndpointAddress**.</span></span> <span data-ttu-id="3e4ae-120">Ensuite, vous pouvez appeler ses méthodes pour travailler avec des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-120">Then you can invoke its methods to work with metadata.</span></span>|  
|<span data-ttu-id="3e4ae-121">**MetadataRetrievalNode** classe</span><span class="sxs-lookup"><span data-stu-id="3e4ae-121">**MetadataRetrievalNode** class</span></span><br /><br /> <span data-ttu-id="3e4ae-122">(Microsoft.ServiceModel.Channels)</span><span class="sxs-lookup"><span data-stu-id="3e4ae-122">(Microsoft.ServiceModel.Channels)</span></span>|<span data-ttu-id="3e4ae-123">Représente un nœud de métadonnées sur la carte.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-123">Represents a metadata node on the adapter.</span></span> <span data-ttu-id="3e4ae-124">Le **Parcourir** et **recherche** méthodes retournent des nœuds de ce type et le **GetMetadata** méthode accepte les nœuds de ce type en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-124">The **Browse** and **Search** methods return nodes of this type, and the **GetMetadata** method takes nodes of this type as a parameter.</span></span>|  
|<span data-ttu-id="3e4ae-125">**ServiceDescription** classe</span><span class="sxs-lookup"><span data-stu-id="3e4ae-125">**ServiceDescription** class</span></span><br /><br /> <span data-ttu-id="3e4ae-126">(System.Web.Services.Description)</span><span class="sxs-lookup"><span data-stu-id="3e4ae-126">(System.Web.Services.Description)</span></span>|<span data-ttu-id="3e4ae-127">Fournit un moyen de la création et la mise en forme d’un fichier de document WSDL valide.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-127">Provides a means of creating and formatting a valid WSDL document file.</span></span> <span data-ttu-id="3e4ae-128">Le **GetMetadata** méthode retourne un **ServiceDescription** objet.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-128">The **GetMetadata** method returns a **ServiceDescription** object.</span></span>|  
  
 
### <a name="metadata-node-ids"></a><span data-ttu-id="3e4ae-129">ID de nœud de métadonnées</span><span class="sxs-lookup"><span data-stu-id="3e4ae-129">Metadata Node IDs</span></span>  
 <span data-ttu-id="3e4ae-130">L’adaptateur organise ses métadonnées sous forme d’arborescence hiérarchique de nœuds.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-130">The adapter organizes its metadata as a hierarchical tree of nodes.</span></span> <span data-ttu-id="3e4ae-131">Dans l’arborescence, il existe deux types de nœuds de métadonnées :</span><span class="sxs-lookup"><span data-stu-id="3e4ae-131">Within this tree structure there are two types of metadata nodes:</span></span>  
  
-   <span data-ttu-id="3e4ae-132">**Nœuds d’opération** représentent des opérations qui met en évidence l’adaptateur sur les objets de base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-132">**Operation nodes** represent operations that the adapter surfaces on Oracle database artifacts.</span></span> <span data-ttu-id="3e4ae-133">Nœuds d’opération sont les feuilles de l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-133">Operation nodes are the leaves of the tree.</span></span>  
  
-   <span data-ttu-id="3e4ae-134">**Les nœuds de catégorie** représentent les artefacts de base de données Oracle et des regroupements d’artefacts de base de données Oracle qui ne correspondent pas directement à une opération sur la carte.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-134">**Category nodes** represent Oracle database artifacts and groupings of Oracle database artifacts that do not directly correspond to an operation on the adapter.</span></span> <span data-ttu-id="3e4ae-135">Les nœuds de catégorie sont les branches de l’arborescence. elles contiennent des autres nœuds de catégorie et/ou les nœuds de l’opération.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-135">Category nodes are the branches of the tree; they contain other category nodes and/or operation nodes.</span></span> <span data-ttu-id="3e4ae-136">Par exemple, les packages et des tables Oracle sont représentées en tant que nœuds de catégorie.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-136">For example, Oracle tables and packages are represented as category nodes.</span></span>  
  
 <span data-ttu-id="3e4ae-137">Chaque nœud de métadonnées exposée par l’adaptateur est identifié par un ID de nœud unique.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-137">Each metadata node surfaced by the adapter is identified by a unique node ID.</span></span> <span data-ttu-id="3e4ae-138">Pour plus d’informations sur le nœud de métadonnées ID exposées par l’adaptateur, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md).</span><span class="sxs-lookup"><span data-stu-id="3e4ae-138">For more information about the metadata node IDs surfaced by the adapter, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md).</span></span> <span data-ttu-id="3e4ae-139">Ces ID de nœud vous permet de spécifier les artefacts de base de données Oracle cible lorsque vous utilisez la **IMetadataRetrievalContract** interface à parcourir, rechercher et récupérer des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-139">You use these node IDs to specify target Oracle database artifacts when you use the **IMetadataRetrievalContract** interface to browse, search, and retrieve metadata.</span></span>  
  
### <a name="binding-properties"></a><span data-ttu-id="3e4ae-140">Propriétés de liaison</span><span class="sxs-lookup"><span data-stu-id="3e4ae-140">Binding Properties</span></span>  
 <span data-ttu-id="3e4ae-141">Si vous utilisez un **IMetadataRetrievalContract** canal ou un **IMetadataRetrievalClient** pour travailler avec des métadonnées, vous devez spécifier un **OracleDBBinding** lorsque vous créer l’instance.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-141">Whether you use an **IMetadataRetrievalContract** channel or an **IMetadataRetrievalClient** to work with metadata, you must specify an **OracleDBBinding** when you create the instance.</span></span>  
  
 <span data-ttu-id="3e4ae-142">Il existe plusieurs propriétés de liaison qui affectent la façon dont l’adaptateur génère des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-142">There are several binding properties that affect how the adapter generates metadata.</span></span> <span data-ttu-id="3e4ae-143">Ces propriétés sont :</span><span class="sxs-lookup"><span data-stu-id="3e4ae-143">These properties are:</span></span>  
  
-   <span data-ttu-id="3e4ae-144">**EnableSafeTyping**</span><span class="sxs-lookup"><span data-stu-id="3e4ae-144">**EnableSafeTyping**</span></span>  
  
-   <span data-ttu-id="3e4ae-145">**UseSchemaInNamespace**</span><span class="sxs-lookup"><span data-stu-id="3e4ae-145">**UseSchemaInNamespace**</span></span>  
  
-   <span data-ttu-id="3e4ae-146">**PollingStatement**</span><span class="sxs-lookup"><span data-stu-id="3e4ae-146">**PollingStatement**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3e4ae-147">Si vous souhaitez récupérer des métadonnées pour l’opération POLLINGSTMT, vous devez définir le **PollingStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-147">If you want to retrieve metadata for the POLLINGSTMT operation you must set the **PollingStatement** binding property.</span></span>  
  
 <span data-ttu-id="3e4ae-148">Vous devez vous assurer que ces propriétés sont définies sur les valeurs requises pour votre application avant d’ouvrir l’objet de récupération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-148">You should ensure that these binding properties are set to the values required for your application before you open the metadata retrieval object.</span></span> <span data-ttu-id="3e4ae-149">Pour plus d’informations sur la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="3e4ae-149">For more information about the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  
  
### <a name="browsing-metadata-nodes"></a><span data-ttu-id="3e4ae-150">Parcourir les nœuds de métadonnées</span><span class="sxs-lookup"><span data-stu-id="3e4ae-150">Browsing Metadata Nodes</span></span>  
 <span data-ttu-id="3e4ae-151">Vous utilisez la **Parcourir** méthode pour retourner tous les nœuds de métadonnées qui sont contenus dans un nœud parent.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-151">You use the **Browse** method to return all the metadata nodes that are contained in a parent node.</span></span> <span data-ttu-id="3e4ae-152">L’exemple suivant recherche les trois premiers schémas sur la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-152">The following example browses for the first three schemas on the Oracle database.</span></span> <span data-ttu-id="3e4ae-153">Dans cet exemple, **client** est une instance de **MetadataRetrievalClient**.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-153">In this example, **client** is an instance of **MetadataRetrievalClient**.</span></span>  
  
```  
// The first parameter is the node ID.   
// The second parameter is the start index.  
// The third parameter is the maximum number of nodes to return.  
                MetadataRetrievalNode[] nodes = client.Browse(MetadataRetrievalNode.Root.NodeId, 0, 3);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="3e4ae-154">Vous pouvez uniquement rechercher des nœuds de catégorie ; Impossible de parcourir les nœuds de l’opération.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-154">You can only browse category nodes; you cannot browse operation nodes.</span></span>  
  
### <a name="searching-for-metadata-nodes"></a><span data-ttu-id="3e4ae-155">Recherche de noeuds de métadonnées</span><span class="sxs-lookup"><span data-stu-id="3e4ae-155">Searching for Metadata Nodes</span></span>  
 <span data-ttu-id="3e4ae-156">Vous utilisez la **recherche** méthode pour effectuer une recherche pour les nœuds contenus dans un nœud parent.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-156">You use the **Search** method to perform a search for nodes contained by a parent node.</span></span> <span data-ttu-id="3e4ae-157">L’adaptateur prend en charge les caractères génériques dans les expressions de recherche ; par exemple, vous pouvez spécifier le pourcentage (%) caractère générique pour faire correspondre zéro ou plusieurs caractères.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-157">The adapter supports wildcard characters in search expressions; for example you can specify the percent (%) wildcard character to match zero or more characters.</span></span> <span data-ttu-id="3e4ae-158">L’exemple suivant montre une recherche de toutes les tables dans le schéma SCOTT qui contiennent la chaîne « EMP ».</span><span class="sxs-lookup"><span data-stu-id="3e4ae-158">The following example shows a search for all the tables in the SCOTT schema that contain the string "EMP".</span></span> <span data-ttu-id="3e4ae-159">Dans cet exemple, **client** est une instance de **MetadataRetrievalClient**.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-159">In this example, **client** is an instance of **MetadataRetrievalClient**.</span></span>  
  
```  
// Search for all nodes that contain "EMP" under the SCOTT.Table node.  
// The parameters are the parent node ID, the search expression, and   
// the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", 3);  
  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="3e4ae-160">La recherche est uniquement pris en charge sur un ensemble limité de nœuds.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-160">Searching is only supported on a limited set of nodes.</span></span> <span data-ttu-id="3e4ae-161">Pour plus d’informations sur les nœuds sur lesquels recherche est prise en charge et sur les caractères génériques pris en charge dans les expressions de recherche, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md).</span><span class="sxs-lookup"><span data-stu-id="3e4ae-161">For more information about the nodes on which search is supported and about the wildcard characters supported in search expressions, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md).</span></span>  
  
### <a name="retrieving-metadata-wsdl-for-operations"></a><span data-ttu-id="3e4ae-162">La récupération de métadonnées (WSDL) pour les opérations</span><span class="sxs-lookup"><span data-stu-id="3e4ae-162">Retrieving Metadata (WSDL) for Operations</span></span>  
 <span data-ttu-id="3e4ae-163">Vous utilisez la **GetMetadata** pour récupérer une description de service (document WSDL) pour un groupe de nœuds de l’opération.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-163">You use the **GetMetadata** method to retrieve a service description (WSDL document) for a group of operation nodes.</span></span> <span data-ttu-id="3e4ae-164">L’exemple suivant récupère une description de service qui contient toutes les opérations que l’adaptateur met en évidence pour SCOTT. Table EMP en spécifiant son ID de nœud.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-164">The following example retrieves a service description that contains all of the operations that the adapter surfaces for the SCOTT.EMP table by specifying its node ID.</span></span> <span data-ttu-id="3e4ae-165">Dans cet exemple, **client** est une instance de **MetadataRetrievalClient**.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-165">In this example, **client** is an instance of **MetadataRetrievalClient**.</span></span>  
  
```  
// Get a service description that contains all of the operations   
// surfaced for the SCOTT.EMP table. The IsOperation  
// property is set false because this is a category node.  
nodes = new MetadataRetrievalNode[1];  
nodes[0] = new MetadataRetrievalNode();  
nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP";  
nodes[0].IsOperation = false;  
System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="3e4ae-166">Le **IsOperation** propriété doit avoir la valeur false pour les nœuds de catégorie et de la valeur true pour les nœuds de l’opération.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-166">The **IsOperation** property should be false for category nodes and true for operation nodes.</span></span>  
  
### <a name="using-a-metadataretrievalclient"></a><span data-ttu-id="3e4ae-167">À l’aide d’un MetadataRetrievalClient</span><span class="sxs-lookup"><span data-stu-id="3e4ae-167">Using a MetadataRetrievalClient</span></span>  
 <span data-ttu-id="3e4ae-168">Création et utilisation d’un **MetadataRetrievalClient** est quasiment identique comme tout autre client WCF.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-168">Creating and using a **MetadataRetrievalClient** is much the same as any other WCF client.</span></span> <span data-ttu-id="3e4ae-169">Vous créez le client en spécifiant un point de terminaison et une instance de **OracleDBBinding**.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-169">You create the client by specifying an endpoint and an instance of **OracleDBBinding**.</span></span> <span data-ttu-id="3e4ae-170">Vous ce faire de façon déclarative dans la configuration ou impérativement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-170">You can do this either declaratively in configuration or imperatively in your code.</span></span> <span data-ttu-id="3e4ae-171">Vous appelez ensuite les méthodes de la **MetadataRetrievalClient** pour parcourir, rechercher et récupérer les métadonnées à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-171">You then invoke the methods of the **MetadataRetrievalClient** to browse, search, and retrieve metadata from the adapter.</span></span>  
  
 <span data-ttu-id="3e4ae-172">L’exemple suivant montre comment utiliser un **MetadataRetrievalClient** pour parcourir, rechercher et récupérer des métadonnées à partir de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3e4ae-172">The following example shows how to use a **MetadataRetrievalClient** to browse, search, and retrieve metadata from the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="3e4ae-173">L’exemple montre :</span><span class="sxs-lookup"><span data-stu-id="3e4ae-173">The example demonstrates:</span></span>  
  
-   <span data-ttu-id="3e4ae-174">Navigation sur le nœud racine de l’arborescence de métadonnées pour les schémas de base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-174">Browsing the root node of the metadata tree for Oracle Database schemas.</span></span>  
  
-   <span data-ttu-id="3e4ae-175">Recherchez les tables dans le schéma SCOTT avec des noms qui contiennent la chaîne « EMP ».</span><span class="sxs-lookup"><span data-stu-id="3e4ae-175">Searching for the tables in the SCOTT schema with names that contain the string "EMP".</span></span>  
  
-   <span data-ttu-id="3e4ae-176">Récupération des métadonnées pour toutes les opérations prises en charge pour SCOTT. Table EMP en passant d’un nœud de catégorie pour le **GetMetadata** (méthode).</span><span class="sxs-lookup"><span data-stu-id="3e4ae-176">Retrieving metadata for all of the operations supported for the SCOTT.EMP table by passing a category node to the **GetMetadata** method.</span></span>  
  
-   <span data-ttu-id="3e4ae-177">Récupération des métadonnées pour l’opération POLLINGSTMT en passant le nœud d’opération POLLINGSTMT à la **GetMetadata** méthode...</span><span class="sxs-lookup"><span data-stu-id="3e4ae-177">Retrieving metadata for the POLLINGSTMT operation by passing the POLLINGSTMT operation node to the **GetMetadata** method..</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using Microsoft.Adapters.OracleDB;  
using Microsoft.ServiceModel.Channels;  
  
using System.Web.Services.Description;  
  
namespace OracleMetadataRetrieval  
{  
    class NodeWriter  
    {  
        // This method writes the value of a collection of metadata retrieval nodes  
        // to the console  
        public void Write(string title, MetadataRetrievalNode[] nodes)  
        {  
            Console.WriteLine(title);  
            Console.WriteLine();  
  
            //write all the nodes returned to the console.  
            foreach (MetadataRetrievalNode node in nodes)  
            {  
                Console.WriteLine("NodeId = " + node.NodeId);  
                Console.WriteLine("\tDirection   = " + node.Direction.ToString());  
                Console.WriteLine("\tIsOperation = " + node.IsOperation.ToString());  
                Console.WriteLine("\tDisplayName = " + node.DisplayName);  
                Console.WriteLine("\tDescription = " + node.Description);  
            }  
            Console.WriteLine();  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            MetadataRetrievalClient client = null;  
            NodeWriter nodeWriter = new NodeWriter();  
  
            try  
            {  
                // create a binding and   
                // set the PollingStatement binding property if you want to  
                // return metadata for the POLLINGSTMT operation  
                OracleDBBinding binding = new OracleDBBinding();  
                binding.PollingStatement = "SELECT * FROM EMP";  
  
                // Set PollingId parameter if you want to alter the namespace of the POLLINGSTMT operation  
                EndpointAddress address = new EndpointAddress("oracledb://ADAPTER?PollingId=1");  
  
                client = new MetadataRetrievalClient(binding, address);  
                client.ClientCredentials.UserName.UserName = "SCOTT";  
                client.ClientCredentials.UserName.Password = "TIGER";  
                client.Open();  
  
                // Browse for the first 3 (schema) nodes directly under the root  
                // The parameters are the parent Node ID, the start index, and the maximum number  
                // of nodes to return  
                MetadataRetrievalNode[] nodes = client.Browse(MetadataRetrievalNode.Root.NodeId, 0, 3);  
                nodeWriter.Write("Browse results for the root node:", nodes);  
  
                // Search for first 3 tables that contain "EMP" in the SCOTT schema  
                // The parameters are the parent node ID, the search expression, and the maximum number  
                // of nodes to return  
                nodes = client.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", 3);  
                nodeWriter.Write(String.Format("Search results for \"%EMP%\" under {0} node:", "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table"), nodes);  
  
                // Get a WSDL document that specifies a contract that contains the operations  
                // surfaced for the SCOTT.EMP table. The IsOperation property is set false  
                // because this is a category node.  
                nodes = new MetadataRetrievalNode[1];  
                nodes[0] = new MetadataRetrievalNode();  
                nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP";  
                nodes[0].IsOperation = false;  
                System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
                description.Write("EmpTableContract.wsdl");  
  
                // Get a WSDL document that specifies a contract that contains the   
                // the POLLINGSTMT operation. The IsOperation property is set true  
                // because this is an operation node.  
                // Note that the operation NodeId is equivalent to the message action.  
                nodes = new MetadataRetrievalNode[1];  
                nodes[0] = new MetadataRetrievalNode();  
                nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT";  
                nodes[0].IsOperation = true;  
                description = client.GetMetadata(nodes);  
                description.Write("PollingContract.wsdl");  
  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
            }  
            finally  
            {  
                if (client != null)  
                {  
                    if (client.State == CommunicationState.Opened)  
                        client.Close();  
                    else  
                        client.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="3e4ae-178">Voici la sortie de ce programme sur la console.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-178">The following shows the output of this program on the console.</span></span> <span data-ttu-id="3e4ae-179">Vous pouvez voir la structure des nœuds de récupération de métadonnées retournées par chaque méthode.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-179">You can see the structure of the metadata retrieval nodes returned by each method.</span></span> <span data-ttu-id="3e4ae-180">Le programme écrit également deux documents WSDL à des fichiers.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-180">The program also writes two WSDL documents to files.</span></span>  
  
```  
Browse results for the root node:  
  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADAPTERTEST  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADAPTERTEST  
        Description = Owned By ADAPTERTEST  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADAPTEST  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADAPTEST  
        Description = Owned By ADAPTEST  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADMIN123  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADMIN123  
        Description = Owned By ADMIN123  
  
Search results for "%EMP%" under http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table node:  
  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/AEMP  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = AEMP  
        Description = Table.AEMP  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = EMP  
        Description = Table.EMP  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP1  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = EMP1  
        Description = Table.EMP1  
```  
  
## <a name="using-an-imetadataretrievalcontract-channel"></a><span data-ttu-id="3e4ae-181">À l’aide d’un canal IMetadataRetrievalContract</span><span class="sxs-lookup"><span data-stu-id="3e4ae-181">Using an IMetadataRetrievalContract Channel</span></span>  
 <span data-ttu-id="3e4ae-182">Vous pouvez également créer un **IMetadataRetrievalContract** puis utiliser ce canal pour parcourir, rechercher et récupérer les métadonnées à partir de l’adaptateur et de canal.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-182">You can also create an **IMetadataRetrievalContract** channel and then use this channel to browse, search, and retrieve metadata from the adapter.</span></span> <span data-ttu-id="3e4ae-183">(Les signatures de méthode sont les mêmes que pour les **MetadataRetrievalClient** classe.) L'exemple suivant montre comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="3e4ae-183">(The method signatures are the same as for the **MetadataRetrievalClient** class.) The following example shows how to do this.</span></span>  
  
```  
…  
//Create a binding and endpoint address.  
OracleDBBinding binding = new OracleDBBinding();  
EndpointAddress address = new EndpointAddress("oracledb://ADAPTER/");  
  
//Create and open a channel factory that will return an IMetadataRetrievalContract object, on which browse, search, and get can be performed.  
ChannelFactory<IMetadataRetrievalContract> factory = new ChannelFactory<IMetadataRetrievalContract>(binding, address);  
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
factory.Open();  
  
//Obtain an IMetadataRetrievalContract channel from the factory.  
IMetadataRetrievalContract channel = factory.CreateChannel();  
  
//Perform a search using the channel.  
MetadataRetrievalNode[] nodes = channel.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", int.MaxValue);  
…  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e4ae-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e4ae-184">See Also</span></span>  
 [<span data-ttu-id="3e4ae-185">Obtenir les métadonnées par programme à partir de la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="3e4ae-185">Get Metadata Programmatically from the Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-programmatically-from-the-oracle-database.md)
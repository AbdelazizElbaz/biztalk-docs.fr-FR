---
title: "Obtient les métadonnées de SAP à l’aide de IMetadataRetrievalContract | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, search metadata
- searching metadata
- how to, browse metadata
- browsing metadata
ms.assetid: 0944fc39-9ee5-4702-8b52-e0bc87f202c6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efa36eee26dd9467a71f7e8dd4d28d2e37e26606
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-in-sap-using-imetadataretrievalcontract"></a><span data-ttu-id="10961-102">Obtient les métadonnées de SAP à l’aide de IMetadataRetrievalContract</span><span class="sxs-lookup"><span data-stu-id="10961-102">Get Metadata in SAP using IMetadataRetrievalContract</span></span>
<span data-ttu-id="10961-103">Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] expose un **IMetadataRetrievalContract**point de terminaison que vous pouvez utiliser pour parcourir et rechercher les artefacts du système SAP et pour récupérer des métadonnées sous la forme d’un document Web Services Description Language (WSDL) pour opérations.</span><span class="sxs-lookup"><span data-stu-id="10961-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] exposes an **IMetadataRetrievalContract**endpoint that you can use to browse and search for SAP system artifacts and to retrieve metadata in the form of a Web Services Description Language (WSDL) document for operations.</span></span>  
  
 <span data-ttu-id="10961-104">Le **IMetadataRetrievalContract** interface est implémentée par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] et fournit des fonctionnalités de navigation, recherche et la récupération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="10961-104">The **IMetadataRetrievalContract** interface is implemented by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] and provides metadata browse, search, and retrieval capabilities.</span></span> <span data-ttu-id="10961-105">Outre la **IMetadataRetrievalContract** interface, le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] expose le **MetadataRetrievalClient** classe qui implémente l’interface.</span><span class="sxs-lookup"><span data-stu-id="10961-105">In addition to the **IMetadataRetrievalContract** interface, the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] exposes the **MetadataRetrievalClient** class, which implements the interface.</span></span> <span data-ttu-id="10961-106">Vous pouvez utiliser un **IMetadataRetrievalContract** canal ou un **MetadataRetrievalClient** pour manipuler les métadonnées ; les méthodes exposées à parcourir, rechercher et récupérer les métadonnées sont les mêmes dans chaque cas.</span><span class="sxs-lookup"><span data-stu-id="10961-106">You can use either an **IMetadataRetrievalContract** channel or a **MetadataRetrievalClient** to work with metadata; the methods exposed to browse, search, and retrieve metadata are the same in each case.</span></span>  
  
 <span data-ttu-id="10961-107">Les sections suivantes fournissent des informations sur l’utilisation de la **IMetadataRetrievalContract** interface.</span><span class="sxs-lookup"><span data-stu-id="10961-107">The following sections provide information about how to use the **IMetadataRetrievalContract** interface.</span></span>  
  
## <a name="the-imetadataretrievalcontract-interface"></a><span data-ttu-id="10961-108">L’Interface IMetadataRetrievalContract</span><span class="sxs-lookup"><span data-stu-id="10961-108">The IMetadataRetrievalContract Interface</span></span>  
 <span data-ttu-id="10961-109">Le tableau suivant fournit des informations sur les classes importantes qui sont utilisées lorsque vous travaillez avec le **IMetadataRetrievalContract** interface.</span><span class="sxs-lookup"><span data-stu-id="10961-109">The following table provides information about important classes that are used when you work with the **IMetadataRetrievalContract** interface.</span></span>  
  
|<span data-ttu-id="10961-110">Classe ou Interface</span><span class="sxs-lookup"><span data-stu-id="10961-110">Class or Interface</span></span>|<span data-ttu-id="10961-111"> Description</span><span class="sxs-lookup"><span data-stu-id="10961-111">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="10961-112">**IMetadataRetrievalContract** interface</span><span class="sxs-lookup"><span data-stu-id="10961-112">**IMetadataRetrievalContract** interface</span></span><br /><br /> <span data-ttu-id="10961-113">(Microsoft.ServiceModel.Channels)</span><span class="sxs-lookup"><span data-stu-id="10961-113">(Microsoft.ServiceModel.Channels)</span></span>|<span data-ttu-id="10961-114">Définit le **Parcourir**, **recherche**, et **GetMetadata** méthodes.</span><span class="sxs-lookup"><span data-stu-id="10961-114">Defines the **Browse**, **Search**, and **GetMetadata** methods.</span></span> <span data-ttu-id="10961-115">Vous appelez ces méthodes à l’aide d’un **IMetadataRetrievalContract** canal ou un **MetadataRetrievalClient** pour travailler avec les métadonnées de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="10961-115">You invoke these methods either by using an **IMetadataRetrievalContract** channel or a **MetadataRetrievalClient** to work with adapter metadata.</span></span>|  
|<span data-ttu-id="10961-116">**MetadataRetrievalClient** classe</span><span class="sxs-lookup"><span data-stu-id="10961-116">**MetadataRetrievalClient** class</span></span><br /><br /> <span data-ttu-id="10961-117">(Microsoft.ServiceModel.Channels)</span><span class="sxs-lookup"><span data-stu-id="10961-117">(Microsoft.ServiceModel.Channels)</span></span>|<span data-ttu-id="10961-118">Implémente le **IMetadataRetrievalContract** interface.</span><span class="sxs-lookup"><span data-stu-id="10961-118">Implements the **IMetadataRetrievalContract** interface.</span></span> <span data-ttu-id="10961-119">Vous pouvez créer une instance de cette classe et configuration de votre système SAP en fournissant un **SAPBinding** et un **EndpointAddress**.</span><span class="sxs-lookup"><span data-stu-id="10961-119">You can create an instance of this class and configure it for your SAP system by providing an **SAPBinding** and an **EndpointAddress**.</span></span> <span data-ttu-id="10961-120">Ensuite, vous pouvez appeler ses méthodes pour travailler avec des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="10961-120">Then you can invoke its methods to work with metadata.</span></span>|  
|<span data-ttu-id="10961-121">**MetadataRetrievalNode** classe</span><span class="sxs-lookup"><span data-stu-id="10961-121">**MetadataRetrievalNode** class</span></span><br /><br /> <span data-ttu-id="10961-122">(Microsoft.ServiceModel.Channels)</span><span class="sxs-lookup"><span data-stu-id="10961-122">(Microsoft.ServiceModel.Channels)</span></span>|<span data-ttu-id="10961-123">Représente un nœud de métadonnées sur la carte.</span><span class="sxs-lookup"><span data-stu-id="10961-123">Represents a metadata node on the adapter.</span></span> <span data-ttu-id="10961-124">Le **Parcourir** et **recherche** méthodes retournent des nœuds de ce type et le **GetMetadata** méthode accepte les nœuds de ce type en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="10961-124">The **Browse** and **Search** methods return nodes of this type, and the **GetMetadata** method takes nodes of this type as a parameter.</span></span>|  
|<span data-ttu-id="10961-125">**ServiceDescription** classe</span><span class="sxs-lookup"><span data-stu-id="10961-125">**ServiceDescription** class</span></span><br /><br /> <span data-ttu-id="10961-126">(System.Web.Services.Description)</span><span class="sxs-lookup"><span data-stu-id="10961-126">(System.Web.Services.Description)</span></span>|<span data-ttu-id="10961-127">Fournit un moyen de la création et la mise en forme d’un fichier de document WSDL valide.</span><span class="sxs-lookup"><span data-stu-id="10961-127">Provides a means of creating and formatting a valid WSDL document file.</span></span> <span data-ttu-id="10961-128">Le **GetMetadata** méthode retourne un **ServiceDescription** objet.</span><span class="sxs-lookup"><span data-stu-id="10961-128">The **GetMetadata** method returns a **ServiceDescription** object.</span></span>|  
  
 <span data-ttu-id="10961-129">Pour plus d’informations sur la **IMetadataRetrievalContract** interface, le **MetadataRetrievalClient** (classe) et le **MetadataRetrievalNode** classe ; consultez la  **Microsoft.ServiceModel.Channels** gérés référence à l’adresse [http://go.microsoft.com/fwlink/?LinkId=105566](http://go.microsoft.com/fwlink/?LinkId=105566).</span><span class="sxs-lookup"><span data-stu-id="10961-129">For more information about the **IMetadataRetrievalContract** interface, the **MetadataRetrievalClient** class, and the **MetadataRetrievalNode** class; see the **Microsoft.ServiceModel.Channels** managed reference at [http://go.microsoft.com/fwlink/?LinkId=105566](http://go.microsoft.com/fwlink/?LinkId=105566).</span></span>  
  
### <a name="metadata-node-ids"></a><span data-ttu-id="10961-130">ID de nœud de métadonnées</span><span class="sxs-lookup"><span data-stu-id="10961-130">Metadata Node IDs</span></span>  
 <span data-ttu-id="10961-131">L’adaptateur organise ses métadonnées sous forme d’arborescence hiérarchique de nœuds.</span><span class="sxs-lookup"><span data-stu-id="10961-131">The adapter organizes its metadata as a hierarchical tree of nodes.</span></span> <span data-ttu-id="10961-132">Dans l’arborescence, il existe deux types de nœuds de métadonnées :</span><span class="sxs-lookup"><span data-stu-id="10961-132">Within this tree structure there are two types of metadata nodes:</span></span>  
  
-   <span data-ttu-id="10961-133">**Nœuds d’opération** représentent des opérations qui met en évidence l’adaptateur sur les artefacts SAP.</span><span class="sxs-lookup"><span data-stu-id="10961-133">**Operation nodes** represent operations that the adapter surfaces on SAP artifacts.</span></span> <span data-ttu-id="10961-134">Nœuds d’opération sont les feuilles de l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="10961-134">Operation nodes are the leaves of the tree.</span></span>  
  
-   <span data-ttu-id="10961-135">**Les nœuds de catégorie** représentent les artefacts SAP et les regroupements d’artefacts SAP qui ne correspondent pas directement à une opération sur la carte.</span><span class="sxs-lookup"><span data-stu-id="10961-135">**Category nodes** represent SAP artifacts and groupings of SAP artifacts that do not directly correspond to an operation on the adapter.</span></span> <span data-ttu-id="10961-136">Les nœuds de catégorie sont les branches de l’arborescence. elles contiennent des autres nœuds de catégorie et/ou les nœuds de l’opération.</span><span class="sxs-lookup"><span data-stu-id="10961-136">Category nodes are the branches of the tree; they contain other category nodes and/or operation nodes.</span></span> <span data-ttu-id="10961-137">Par exemple, les groupes fonctionnels RFC ou les objets métiers SAP sont représentées en tant que nœuds de catégorie.</span><span class="sxs-lookup"><span data-stu-id="10961-137">For example, RFC functional groups or SAP business objects are represented as category nodes.</span></span>  
  
 <span data-ttu-id="10961-138">Chaque nœud de métadonnées exposée par l’adaptateur est identifié par un ID de nœud unique.</span><span class="sxs-lookup"><span data-stu-id="10961-138">Each metadata node surfaced by the adapter is identified by a unique node ID.</span></span> <span data-ttu-id="10961-139">Pour plus d’informations sur le nœud de métadonnées ID exposées par l’adaptateur, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).</span><span class="sxs-lookup"><span data-stu-id="10961-139">For more information about the metadata node IDs surfaced by the adapter, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).</span></span> <span data-ttu-id="10961-140">Ces ID de nœud vous permet de spécifier les artefacts SAP cible lorsque vous utilisez la **IMetadataRetrievalContract** interface à parcourir, rechercher et récupérer des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="10961-140">You use these node IDs to specify target SAP artifacts when you use the **IMetadataRetrievalContract** interface to browse, search, and retrieve metadata.</span></span> <span data-ttu-id="10961-141">Vous pouvez utiliser l’une des constantes définies dans `Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants` et `Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants` pour vous aider à construire des ID de nœud de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="10961-141">You can use the constants defined in `Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants` and `Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants` to help you construct metadata node IDs.</span></span>  
  
### <a name="binding-properties"></a><span data-ttu-id="10961-142">Propriétés de liaison</span><span class="sxs-lookup"><span data-stu-id="10961-142">Binding Properties</span></span>  
 <span data-ttu-id="10961-143">Si vous utilisez un **IMetadataRetrievalContract** canal ou un **IMetadataRetrievalClient** pour travailler avec des métadonnées, vous devez spécifier un **SAPBinding** lorsque vous créez le instance.</span><span class="sxs-lookup"><span data-stu-id="10961-143">Whether you use an **IMetadataRetrievalContract** channel or an **IMetadataRetrievalClient** to work with metadata, you must specify an **SAPBinding** when you create the instance.</span></span>  
  
 <span data-ttu-id="10961-144">Il existe plusieurs propriétés de liaison qui affectent la façon dont l’adaptateur génère des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="10961-144">There are several binding properties that affect how the adapter generates metadata.</span></span> <span data-ttu-id="10961-145">Ces propriétés sont :</span><span class="sxs-lookup"><span data-stu-id="10961-145">These properties are:</span></span>  
  
-   <span data-ttu-id="10961-146">**GenerateFlatfileCompatibleIdocSchema**</span><span class="sxs-lookup"><span data-stu-id="10961-146">**GenerateFlatfileCompatibleIdocSchema**</span></span>  
  
-   <span data-ttu-id="10961-147">**ReceiveIDocFormat**</span><span class="sxs-lookup"><span data-stu-id="10961-147">**ReceiveIDocFormat**</span></span>  
  
-   <span data-ttu-id="10961-148">**EnableSafeTyping**</span><span class="sxs-lookup"><span data-stu-id="10961-148">**EnableSafeTyping**</span></span>  
  
-   <span data-ttu-id="10961-149">**FlatFileSegmentIndicator**</span><span class="sxs-lookup"><span data-stu-id="10961-149">**FlatFileSegmentIndicator**</span></span>  
  
 <span data-ttu-id="10961-150">Vous devez vous assurer que ces propriétés sont définies sur les valeurs requises pour votre application avant d’ouvrir l’objet de récupération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="10961-150">You should ensure that these binding properties are set to the values required for your application before you open the metadata retrieval object.</span></span> <span data-ttu-id="10961-151">Pour plus d’informations sur les propriétés de liaison de l’adaptateur SAP, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="10961-151">For more information about the SAP adapter binding properties, see [Read about  BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
### <a name="browsing-metadata-nodes"></a><span data-ttu-id="10961-152">Parcourir les nœuds de métadonnées</span><span class="sxs-lookup"><span data-stu-id="10961-152">Browsing Metadata Nodes</span></span>  
 <span data-ttu-id="10961-153">Vous utilisez la **Parcourir** méthode pour retourner tous les nœuds de métadonnées qui sont contenus dans un nœud parent.</span><span class="sxs-lookup"><span data-stu-id="10961-153">You use the **Browse** method to return all the metadata nodes that are contained in a parent node.</span></span> <span data-ttu-id="10961-154">L’exemple suivant recherche les trois premiers groupes fonctionnels RFC sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="10961-154">The following example browses for the first three RFC functional groups on the SAP system.</span></span> <span data-ttu-id="10961-155">Dans cet exemple, **client** est une instance de **MetadataRetrievalClient**.</span><span class="sxs-lookup"><span data-stu-id="10961-155">In this example, **client** is an instance of **MetadataRetrievalClient**.</span></span>  
  
```  
// The first parameter is the node ID.   
// The second parameter is the start index.  
// The third parameter is the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Browse(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, 0, 3);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="10961-156">Vous pouvez uniquement rechercher des nœuds de catégorie ; Impossible de parcourir les nœuds de l’opération.</span><span class="sxs-lookup"><span data-stu-id="10961-156">You can only browse category nodes; you cannot browse operation nodes.</span></span>  
  
### <a name="searching-for-metadata-nodes"></a><span data-ttu-id="10961-157">Recherche de noeuds de métadonnées</span><span class="sxs-lookup"><span data-stu-id="10961-157">Searching for Metadata Nodes</span></span>  
 <span data-ttu-id="10961-158">Vous utilisez la **recherche** méthode pour effectuer une recherche pour les nœuds contenus dans un nœud parent.</span><span class="sxs-lookup"><span data-stu-id="10961-158">You use the **Search** method to perform a search for nodes contained by a parent node.</span></span> <span data-ttu-id="10961-159">Vous pouvez spécifier l’astérisque (\*) caractère générique.</span><span class="sxs-lookup"><span data-stu-id="10961-159">You can specify the asterisk (\*) wildcard character.</span></span> <span data-ttu-id="10961-160">Ce caractère correspond à zéro ou plusieurs caractères.</span><span class="sxs-lookup"><span data-stu-id="10961-160">This character matches zero or more characters.</span></span> <span data-ttu-id="10961-161">L’exemple suivant montre une recherche de tous les documents RFC qui contiennent la chaîne « BAPI ».</span><span class="sxs-lookup"><span data-stu-id="10961-161">The following example shows a search for all RFCs that contain the string "BAPI".</span></span> <span data-ttu-id="10961-162">Dans cet exemple, **client** est une instance de **MetadataRetrievalClient**.</span><span class="sxs-lookup"><span data-stu-id="10961-162">In this example, **client** is an instance of **MetadataRetrievalClient**.</span></span>  
  
```  
// Search for all nodes that contain "BAPI" under the RFC node.  
// The parameters are the parent node ID, the search expression, and   
// the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "*BAPI*", int.MaxValue);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="10961-163">La recherche est uniquement pris en charge sur un ensemble limité de nœuds.</span><span class="sxs-lookup"><span data-stu-id="10961-163">Searching is only supported on a limited set of nodes.</span></span> <span data-ttu-id="10961-164">Pour plus d’informations sur les nœuds sur lesquels recherche est prise en charge et sur le caractère générique pris en charge dans les expressions de recherche, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).</span><span class="sxs-lookup"><span data-stu-id="10961-164">For more information about the nodes on which search is supported and about the wildcard character supported in search expressions, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).</span></span>  
  
### <a name="retrieving-metadata-wsdl-for-operations"></a><span data-ttu-id="10961-165">La récupération de métadonnées (WSDL) pour les opérations</span><span class="sxs-lookup"><span data-stu-id="10961-165">Retrieving Metadata (WSDL) for Operations</span></span>  
 <span data-ttu-id="10961-166">Vous utilisez la **GetMetadata** pour récupérer une description de service (document WSDL) pour un groupe de nœuds de l’opération.</span><span class="sxs-lookup"><span data-stu-id="10961-166">You use the **GetMetadata** method to retrieve a service description (WSDL document) for a group of operation nodes.</span></span> <span data-ttu-id="10961-167">L’exemple suivant récupère une description de service pour le document RFC BAPI_TRANSACTION_COMMIT.</span><span class="sxs-lookup"><span data-stu-id="10961-167">The following example retrieves a service description for the BAPI_TRANSACTION_COMMIT RFC.</span></span> <span data-ttu-id="10961-168">Dans cet exemple, **client** est une instance de **MetadataRetrievalClient**.</span><span class="sxs-lookup"><span data-stu-id="10961-168">In this example, **client** is an instance of **MetadataRetrievalClient**.</span></span> <span data-ttu-id="10961-169">Notez que l’ID de nœud pour un nœud d’opération est équivalente à l’action du message pour cette opération.</span><span class="sxs-lookup"><span data-stu-id="10961-169">Note that the node ID for an operation node is equivalent to the message action for that operation.</span></span>  
  
```  
// Get a WSDL document that specifies a contract that contains the  
// BAPI_TRANSACTION_COMMIT operation.  
MetadataRetrievalNode[] nodes = new MetadataRetrievalNode[1];  
nodes[0] = new MetadataRetrievalNode();  
nodes[0].NodeId = Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants.RfcActionPrefix + "BAPI_TRANSACTION_COMMIT";  
nodes[0].IsOperation = true;  
  
System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="10961-170">Vous devez spécifier uniquement les nœuds d’opération dans le **GetMetadata** (méthode).</span><span class="sxs-lookup"><span data-stu-id="10961-170">You should only specify operation nodes in the **GetMetadata** method.</span></span>  
  
### <a name="using-a-metadataretrievalclient"></a><span data-ttu-id="10961-171">À l’aide d’un MetadataRetrievalClient</span><span class="sxs-lookup"><span data-stu-id="10961-171">Using a MetadataRetrievalClient</span></span>  
 <span data-ttu-id="10961-172">Création et utilisation d’un **MetadataRetrievalClient** est quasiment identique comme tout autre client WCF.</span><span class="sxs-lookup"><span data-stu-id="10961-172">Creating and using a **MetadataRetrievalClient** is much the same as any other WCF client.</span></span> <span data-ttu-id="10961-173">Vous créez le client en spécifiant un point de terminaison et une instance de **SAPBinding**.</span><span class="sxs-lookup"><span data-stu-id="10961-173">You create the client by specifying an endpoint and an instance of **SAPBinding**.</span></span> <span data-ttu-id="10961-174">Vous ce faire de façon déclarative dans la configuration ou impérativement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="10961-174">You can do this either declaratively in configuration or imperatively in your code.</span></span> <span data-ttu-id="10961-175">Vous appelez ensuite les méthodes de la **MetadataRetrievalClient** pour parcourir, rechercher et récupérer les métadonnées à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="10961-175">You then invoke the methods of the **MetadataRetrievalClient** to browse, search, and retrieve metadata from the adapter.</span></span>  
  
 <span data-ttu-id="10961-176">L’exemple suivant montre comment utiliser un **MetadataRetrievalClient** pour parcourir, rechercher et récupérer des métadonnées à partir de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="10961-176">The following example shows how to use a **MetadataRetrievalClient** to browse, search, and retrieve metadata from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
using System.Web.Services.Description;  
  
namespace SapMetaDataBrowseClient  
{  
    class NodeWriter  
    {  
        // This method writes the value of a collection of metadata retrieval nodes  
        // to the console.  
        public void Write(string title, MetadataRetrievalNode[] nodes)  
        {  
            Console.WriteLine(title);  
            Console.WriteLine();  
  
            //Write all the nodes returned to the console.  
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
            MetadataRetrievalClient browser = null;  
            NodeWriter nodeWriter = new NodeWriter();  
  
            try  
            {  
                // Create a binding  
                SAPBinding binding = new SAPBinding();  
  
                EndpointAddress address = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
                browser = new MetadataRetrievalClient(binding, address);  
                browser.ClientCredentials.UserName.UserName = "YourUserName";  
                browser.ClientCredentials.UserName.Password = "YourPassword";  
                browser.Open();  
  
                // Return the nodes directly under the root.  
                // The parameters are the parent node ID, the start index, and the maximum number  
                // of nodes to return.  
                MetadataRetrievalNode[] nodes = browser.Browse(MetadataRetrievalNode.Root.NodeId, 0, int.MaxValue);  
                nodeWriter.Write("Browse results for the root node:", nodes);  
  
                // Return first 3 RFC group nodes.  
                nodes = browser.Browse(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, 0, 3);  
                nodeWriter.Write(String.Format("Browse results for the first {1} nodes of {0}:", Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, nodes.Length), nodes);  
  
                // Search for first 3 nodes that begin with "BAPI_TRANSACTION" under the RFC node.  
                // The parameters are the parent node ID, the search expression, and the maximum number  
                // of nodes to return.  
                nodes = browser.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "*BAPI_TRANSACTION*", 3);  
                nodeWriter.Write(String.Format("Search results for \"*BAPI_TRANSACTION*\" under {0} node:", Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection), nodes);  
  
                // Get a WSDL document that specifies a contract that contains the operations  
                // found in the search and write it to a file.  
                // You could explicitly specify operations as in the following:  
                //    nodes[0] = new MetadataRetrievalNode();  
                //    nodes[0].NodeId = Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants.RfcActionPrefix + "BAPI_TRANSACTION_COMMIT";  
                //    nodes[0].IsOperation = true;  
                // Note that the operation NodeId is equivalent to the message action.  
                System.Web.Services.Description.ServiceDescription description = browser.GetMetadata(nodes);  
                description.Write("SampleContract.wsdl");  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
            }  
            finally  
            {  
                if (browser != null)  
                {  
                    if (browser.State == CommunicationState.Opened)  
                        browser.Close();  
                    else  
                        browser.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="10961-177">Voici la sortie de ce programme sur la console.</span><span class="sxs-lookup"><span data-stu-id="10961-177">The following shows the output of this program on the console.</span></span> <span data-ttu-id="10961-178">Vous pouvez voir la structure des nœuds de récupération de métadonnées retourné pour chaque méthode.</span><span class="sxs-lookup"><span data-stu-id="10961-178">You can see the structure of the metadata retrieval nodes returned for each method.</span></span> <span data-ttu-id="10961-179">Le programme écrit également un document WSDL qui décrit un contrat de service comprenant les nœuds retournés par la recherche dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="10961-179">The program also writes a WSDL document that describes a service contract consisting of the nodes returned by the search to a file.</span></span> <span data-ttu-id="10961-180">(Pour la plupart des installations SAP, la description du service contient les opérations BAPI_TRANSACTION_COMMIT et BAPI_TRANSACTION_ROLLBACK.)</span><span class="sxs-lookup"><span data-stu-id="10961-180">(For most SAP installations, the service description will contain the BAPI_TRANSACTION_COMMIT and BAPI_TRANSACTION_ROLLBACK operations.)</span></span>  
  
```  
Browse results for the root node:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/BAPISECTION/000001  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = BAPI  
        Description = BAPI  
NodeId = http://Microsoft.LobServices.Sap/2007/03/IDOCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = IDOC  
        Description = IDOC  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = RFC  
        Description = RFC  
NodeId = http://Microsoft.LobServices.Sap/2007/03/TRFCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = TRFC  
        Description = TRFC  
  
Browse results for the first 3 nodes of http://Microsoft.LobServices.Sap/2007/03  
/RFCSECTION/:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/A  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Asset Accounting  
        Description = Asset Accounting  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/S  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Basis  
        Description = Basis  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/B  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Business Information Warehouse  
        Description = Business Information Warehouse  
  
Search results for "*BAPI_TRANSACTION*" under http://Microsoft.LobServices.Sap/2  
007/03/RFCSECTION/ node:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_TRANSACTION_COMMIT  
        Direction   = Inbound, Outbound  
        IsOperation = True  
        DisplayName = BAPI_TRANSACTION_COMMIT  
        Description = Execute external Commit when using BAPIs  
NodeId = http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_TRANSACTION_ROLLBACK  
        Direction   = Inbound, Outbound  
        IsOperation = True  
        DisplayName = BAPI_TRANSACTION_ROLLBACK  
        Description = Execute external Rollback when using BAPIs  
  
```  
  
## <a name="using-an-imetadataretrievalcontract-channel"></a><span data-ttu-id="10961-181">À l’aide d’un canal IMetadataRetrievalContract</span><span class="sxs-lookup"><span data-stu-id="10961-181">Using an IMetadataRetrievalContract Channel</span></span>  
 <span data-ttu-id="10961-182">Vous pouvez également créer un **IMetadataRetrievalContract** puis utiliser ce canal pour parcourir, rechercher et récupérer les métadonnées à partir de l’adaptateur et de canal.</span><span class="sxs-lookup"><span data-stu-id="10961-182">You can also create an **IMetadataRetrievalContract** channel and then use this channel to browse, search, and retrieve metadata from the adapter.</span></span> <span data-ttu-id="10961-183">(Les signatures de méthode sont les mêmes que pour les **MetadataRetrievalClient** classe.) L'exemple suivant montre comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="10961-183">(The method signatures are the same as for the **MetadataRetrievalClient** class.) The following example shows how to do this.</span></span>  
  
```  
…  
//Create a binding and endpoint address.  
SAPBinding binding = new SAPBinding();  
EndpointAddress address = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
//Create and open a channel factory that will return an IMetadataRetrievalContract object, on which browse, search, and get can be performed.  
ChannelFactory<IMetadataRetrievalContract> factory = new ChannelFactory<IMetadataRetrievalContract>(binding, address);  
factory.Credentials.UserName.UserName = "YourUserName";  
factory.Credentials.UserName.Password = "YourPassword";  
factory.Open();  
  
//Obtain an IMetadataRetrievalContract channel from the factory.  
IMetadataRetrievalContract channel = factory.CreateChannel();  
  
//Perform a search using the channel.  
MetadataRetrievalNode[] nodes = channel.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "BAPI_TRANSACTION*", int.MaxValue);  
…  
```  
  
## <a name="see-also"></a><span data-ttu-id="10961-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10961-184">See Also</span></span>  
 [<span data-ttu-id="10961-185">La récupération des métadonnées par programme à partir de SAP</span><span class="sxs-lookup"><span data-stu-id="10961-185">Retrieving Metadata Programmatically from SAP</span></span>](../../adapters-and-accelerators/adapter-sap/get-metadata-programmatically-from-sap.md)
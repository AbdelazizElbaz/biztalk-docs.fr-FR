---
title: "Étape 4 : Implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur d’écho | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d31fc6c1-e4b5-4529-ba3e-2a8cfb8ece1c
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f93b4efeb65092c4ca61ab1fc2ef58a0ac53ae4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-implement-the-metadata-browse-handler-for-the-echo-adapter"></a><span data-ttu-id="3092f-102">Étape 4 : Implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="3092f-102">Step 4: Implement the Metadata Browse Handler for the Echo Adapter</span></span>
<span data-ttu-id="3092f-103">![L’étape 4 de 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-4of9.gif "Step_4of9")</span><span class="sxs-lookup"><span data-stu-id="3092f-103">![Step 4 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-4of9.gif "Step_4of9")</span></span>  
  
 <span data-ttu-id="3092f-104">**Durée :** 45 minutes</span><span class="sxs-lookup"><span data-stu-id="3092f-104">**Time to complete:** 45 minutes</span></span>  
  
 <span data-ttu-id="3092f-105">Dans cette étape, vous implémentez la fonctionnalité de navigation de l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="3092f-105">In this step, you implement the browse capability of the Echo adapter.</span></span> <span data-ttu-id="3092f-106">Cette fonctionnalité permet à votre carte effectuer une recherche basée sur une connexion afin d’obtenir les métadonnées à partir du système cible.</span><span class="sxs-lookup"><span data-stu-id="3092f-106">This capability allows your adapter to perform a connection-based browse to obtain metadata from the target system.</span></span> <span data-ttu-id="3092f-107">Indépendamment des fonctionnalités de votre carte, votre adaptateur doit prendre en charge la fonctionnalité Parcourir.</span><span class="sxs-lookup"><span data-stu-id="3092f-107">Regardless of your adapter's capabilities, your adapter must support the browse capability.</span></span>  
  
 <span data-ttu-id="3092f-108">Conformément à la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], pour prendre en charge la fonctionnalité de navigation, vous devez implémenter la `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface.</span><span class="sxs-lookup"><span data-stu-id="3092f-108">According to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], to support browse capability, you must implement the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface.</span></span> <span data-ttu-id="3092f-109">Pour l’adaptateur d’écho le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère automatiquement la classe dérivée, appelée EchoAdapterMetadataBrowseHandler.</span><span class="sxs-lookup"><span data-stu-id="3092f-109">For the Echo adapter, the [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] automatically generates the derived class called EchoAdapterMetadataBrowseHandler.</span></span>  
  
 <span data-ttu-id="3092f-110">Dans les étapes suivantes, vous mettez à jour cette classe pour obtenir une meilleure compréhension de l’implémentation de la `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` (méthode), comment définir différentes propriétés de la `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet, et comment l’opération et les nœuds de catégorie pris en charge par l’adaptateur s’affichent dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] outil.</span><span class="sxs-lookup"><span data-stu-id="3092f-110">In the following steps, you update this class to get a better understanding of how to implement the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method, how to set various properties of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object, and how the operation and category nodes supported by the adapter appear in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3092f-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="3092f-111">Prerequisites</span></span>  
 <span data-ttu-id="3092f-112">Avant de commencer cette étape, vous devez avoir terminé avec succès [étape 3 : implémenter la connexion de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="3092f-112">Before you begin this step, you must have successfully completed [Step 3: Implement the Connection for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md).</span></span> <span data-ttu-id="3092f-113">Vous devez également comprendre les classes suivantes :</span><span class="sxs-lookup"><span data-stu-id="3092f-113">You must also understand the following classes:</span></span>  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNodeDirections`  
  
-   `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`  
  
## <a name="the-imetadatabrowsehandler-interface"></a><span data-ttu-id="3092f-114">L’Interface IMetadataBrowseHandler</span><span class="sxs-lookup"><span data-stu-id="3092f-114">The IMetadataBrowseHandler Interface</span></span>  
 <span data-ttu-id="3092f-115">Le `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface est définie en tant que :</span><span class="sxs-lookup"><span data-stu-id="3092f-115">The `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface is defined as:</span></span>  
  
```  
public interface IMetadataBrowseHandler : IConnectionHandler, IDisposable  
{  
    MetadataRetrievalNode[] Browse(string nodeId, int childStartIndex, int maxChildNodes, TimeSpan timeout);  
}  
```  
  
 <span data-ttu-id="3092f-116">Le `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` méthode retourne un tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets basés sur les paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="3092f-116">The `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method returns an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects based on the method parameters.</span></span> <span data-ttu-id="3092f-117">Les définitions de paramètres pour la `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` méthode sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="3092f-117">The parameter definitions for the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method are described in the following table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3092f-118">L’implémentation de l’adaptateur Echo utilise uniquement l’ID de nœud et ignore les trois autres paramètres, car l’adaptateur écho prend en charge seulement quelques nœuds.</span><span class="sxs-lookup"><span data-stu-id="3092f-118">The Echo adapter implementation uses only the node ID and ignores the other three parameters, since the Echo adapter supports only a few nodes.</span></span>  
  
|<span data-ttu-id="3092f-119">**Paramètre**</span><span class="sxs-lookup"><span data-stu-id="3092f-119">**Parameter**</span></span>|<span data-ttu-id="3092f-120">**Définition**</span><span class="sxs-lookup"><span data-stu-id="3092f-120">**Definition**</span></span>|  
|-------------------|--------------------|  
|<span data-ttu-id="3092f-121">nodeId</span><span class="sxs-lookup"><span data-stu-id="3092f-121">nodeId</span></span>|<span data-ttu-id="3092f-122">Chaque élément dans la hiérarchie de l’Explorateur de métadonnées (le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et</span><span class="sxs-lookup"><span data-stu-id="3092f-122">Each item in the hierarchy of the metadata explorer (the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and</span></span><br /><br /> [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]<span data-ttu-id="3092f-123">) a un attribut nodeId.</span><span class="sxs-lookup"><span data-stu-id="3092f-123">) has a nodeId.</span></span> <span data-ttu-id="3092f-124">Chaque ID de nœud doit être unique et peut être une catégorie ou une opération.</span><span class="sxs-lookup"><span data-stu-id="3092f-124">Each node ID must be unique and can be a category or an operation.</span></span> <span data-ttu-id="3092f-125">La catégorie peut avoir des sous-catégories.</span><span class="sxs-lookup"><span data-stu-id="3092f-125">The category can have subcategories.</span></span> <span data-ttu-id="3092f-126">**Remarque :** si null ou une chaîne vide (« »), les opérations sont récupérées à partir du nœud racine (« / ») par défaut.</span><span class="sxs-lookup"><span data-stu-id="3092f-126">**Note:**  If null or an empty string (""), operations are retrieved from the root node ("/") by default.</span></span>|  
|<span data-ttu-id="3092f-127">childStartIndex</span><span class="sxs-lookup"><span data-stu-id="3092f-127">childStartIndex</span></span>|<span data-ttu-id="3092f-128">L’index du premier enfant à retourner.</span><span class="sxs-lookup"><span data-stu-id="3092f-128">The index of the first child to return.</span></span><br /><br /> <span data-ttu-id="3092f-129">Non pris en charge par l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="3092f-129">Not supported by the Echo adapter.</span></span>|  
|<span data-ttu-id="3092f-130">maxChildNodes</span><span class="sxs-lookup"><span data-stu-id="3092f-130">maxChildNodes</span></span>|<span data-ttu-id="3092f-131">Le nombre maximal de nœuds de résultat à retourner.</span><span class="sxs-lookup"><span data-stu-id="3092f-131">The maximum number of result nodes to return.</span></span> <span data-ttu-id="3092f-132">Int32.Max permet de récupérer tous les nœuds de résultat.</span><span class="sxs-lookup"><span data-stu-id="3092f-132">Use Int32.Max to retrieve all result nodes.</span></span><br /><br /> <span data-ttu-id="3092f-133">Non pris en charge par l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="3092f-133">Not supported by the Echo adapter.</span></span>|  
|<span data-ttu-id="3092f-134">délai d'expiration</span><span class="sxs-lookup"><span data-stu-id="3092f-134">timeout</span></span>|<span data-ttu-id="3092f-135">La durée maximale autorisée pour l’opération se termine.</span><span class="sxs-lookup"><span data-stu-id="3092f-135">The maximum time allowed for the operation to complete.</span></span><br /><br /> <span data-ttu-id="3092f-136">Non pris en charge par l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="3092f-136">Not supported by the Echo adapter.</span></span>|  
  
 <span data-ttu-id="3092f-137">Lorsque vous implémentez le `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` (méthode), vous devez ajouter chaque nœud de catégorie et l’opération sur le tableau des `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets.</span><span class="sxs-lookup"><span data-stu-id="3092f-137">When implementing the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method, you must add every category and operation node to the array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span> <span data-ttu-id="3092f-138">Pour spécifier un nœud en tant que catégorie, définissez la `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A` à `false`.</span><span class="sxs-lookup"><span data-stu-id="3092f-138">To specify a node as category, set the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A` to `false`.</span></span> <span data-ttu-id="3092f-139">Pour spécifier un nœud en tant qu’opération, définissez la `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A` à `true`.</span><span class="sxs-lookup"><span data-stu-id="3092f-139">To specify a node as operation, set the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A` to `true`.</span></span>  
  
## <a name="echo-adapter-metadata-browse"></a><span data-ttu-id="3092f-140">Recherche de métadonnées d’adaptateur écho</span><span class="sxs-lookup"><span data-stu-id="3092f-140">Echo Adapter Metadata Browse</span></span>  
 <span data-ttu-id="3092f-141">Selon les catégories et les opérations de votre système cible, il existe plusieurs façons pour générer un tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets.</span><span class="sxs-lookup"><span data-stu-id="3092f-141">Depending on your target system's categories and operations, there are many ways to build an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span> <span data-ttu-id="3092f-142">Les opérations et les catégories que vous choisissez doivent représenter les opérations que vous souhaitez exposer.</span><span class="sxs-lookup"><span data-stu-id="3092f-142">The operations and categories you choose should represent the operations you want to expose.</span></span> <span data-ttu-id="3092f-143">Mais pour l’adaptateur Echo, elle crée simplement un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet pour chacun des nœuds suivants avec l’ID de nœud répertorié :</span><span class="sxs-lookup"><span data-stu-id="3092f-143">But for the Echo adapter, it simply creates a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for each of the following nodes with node ID listed:</span></span>  
  
```  
EchoMainCategory  (node under the root node)  
        Echo/EchoStrings   (outbound operation)  
        Echo/EchoGreetings(outbound operation)  
        Echo/EchoCustomGreetingFromFile(outbound operation)  
        Echo/OnReceiveEcho (inbound operation)  
```  
  
 <span data-ttu-id="3092f-144">Le EchoMainCategory est le nœud de catégorie sous le nœud racine (« / »).</span><span class="sxs-lookup"><span data-stu-id="3092f-144">The EchoMainCategory is the category node under the root node ("/").</span></span> <span data-ttu-id="3092f-145">Ce nœud est également utilisé comme catégorie pour les opérations entrantes et sortantes.</span><span class="sxs-lookup"><span data-stu-id="3092f-145">This node is also used as the category for both inbound and outbound operations.</span></span> <span data-ttu-id="3092f-146">Par conséquent, lorsque vous créez le `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet de cette catégorie, vous pouvez procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3092f-146">Hence, when creating the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for that category, you can do the following:</span></span>  
  
```  
MetadataRetrievalNode node = new MetadataRetrievalNode("EchoMainCategory");  
node.IsOperation = false; //category  
node.Direction = MetadataRetrievalNodeDirections.Inbound | MetadataRetrievalNodeDirections.Outbound  //for both inbound and outbound  
```  
  
 <span data-ttu-id="3092f-147">Pour une opération sortante tels que Echo/EchoString qui appartient à la EchoMainCategory, vous pouvez procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3092f-147">For an outbound operation such as Echo/EchoString that belongs to the EchoMainCategory, you can do the following:</span></span>  
  
```  
if( "EchoMainCategory".CompareTo(nodeId) == 0 ) //category is EchoMainCategory  
      {  
          // Outbound operations  
          MetadataRetrievalNode outOpNode1 = new MetadataRetrievalNode("Echo/EchoStrings");  
          outOpNode1.DisplayName = "EchoStrings";  
          outOpNode1.Description = "This operation echoes the incoming string COUNT number of times in a string array.";  
          outOpNode1.Direction = MetadataRetrievalNodeDirections.Outbound;  
          outOpNode1.IsOperation = true;  
```  
  
 <span data-ttu-id="3092f-148">Pour une opération entrante comme écho/OnReceiveEcho qui appartient à la EchoMainCategory, vous pouvez procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3092f-148">For an inbound operation such as Echo/OnReceiveEcho that belongs to the EchoMainCategory, you can do the following:</span></span>  
  
```  
  if( "EchoMainCategory".CompareTo(nodeId) == 0 ) //category is EchoMainCategory  
        {             
// Inbound operations  
            MetadataRetrievalNode inOpNode1 = new MetadataRetrievalNode("Echo/OnReceiveEcho");  
            inOpNode1.DisplayName = "OnReceiveEcho";  
            inOpNode1.Description = "This operation echoes the location and length of a file dropped in the specified file system.";  
            inOpNode1.Direction = MetadataRetrievalNodeDirections.Inbound;  
            inOpNode1.IsOperation = true;  
```  
  
 <span data-ttu-id="3092f-149">Lorsque le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] outils Explorer les métadonnées de l’adaptateur Echo, par défaut, il démarre à partir du nœud racine (« / »).</span><span class="sxs-lookup"><span data-stu-id="3092f-149">When the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] tools explore the Echo adapter metadata, by default, it starts from the root node ("/").</span></span>  
  
 <span data-ttu-id="3092f-150">L’illustration suivante montre que le nœud EchoMainCategory apparaît sous le nœud racine (« / ») :</span><span class="sxs-lookup"><span data-stu-id="3092f-150">The following figure shows that the EchoMainCategory node appears under the root node ("/"):</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4b9d0b8-f07f-4342-815f-9ef1507b0980.gif "e4b9d0b8-f07f-4342-815f-9ef1507b0980")  
  
 <span data-ttu-id="3092f-151">Pour rechercher les trois opérations sortantes, dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] outil, dans le **sélectionner type de contrat** la liste déroulante, sélectionnez le **Client (Outbound operations)** option.</span><span class="sxs-lookup"><span data-stu-id="3092f-151">To browse the three outbound operations, in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool, in the **Select contract type** drop-down list,select the **Client (Outbound operations)** option.</span></span> <span data-ttu-id="3092f-152">Vous voyez ces opérations dans le **catégories et opérations disponibles** zone de liste, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="3092f-152">You see those operations in the **Available categories and operations** list box, as shown below:</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/c8755805-cbb0-40f1-887a-a3123f71ae7e.gif "c8755805-cbb0-40f1-887a-a3123f71ae7e")  
  
 <span data-ttu-id="3092f-153">Dans la figure précédente, notez que le `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A` valeur apparaît dans le **nom** colonne de la **catégories et opérations disponibles** zone de liste.</span><span class="sxs-lookup"><span data-stu-id="3092f-153">In the previous figure, notice that the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A` value appears in the **Name** column of the **Available categories and operations** list box.</span></span> <span data-ttu-id="3092f-154">Le paramètre passé dans le `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` constructeur s’affiche dans le **ID de nœud** colonne de la **catégories et opérations disponibles** zone de liste et le `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.Description%2A` valeur apparaît sous la forme d’info-bulle qui contient la description, lorsque vous cliquez sur le `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A`.</span><span class="sxs-lookup"><span data-stu-id="3092f-154">The parameter passed into the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` constructor appears in the **Node ID** column of the **Available categories and operations** list box, and the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.Description%2A` value appears as the tool tip that contains the description, when you right-click the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A`.</span></span>  
  
 <span data-ttu-id="3092f-155">Pour voir les opérations entrantes, dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] outil, dans le **sélectionner type de contrat** la liste déroulante, sélectionnez le **Service (opérations entrantes)** option.</span><span class="sxs-lookup"><span data-stu-id="3092f-155">To see the inbound operations, in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool, in the **Select contract type** drop-down list,select the **Service (Inbound operations)** option.</span></span> <span data-ttu-id="3092f-156">Vous voyez l’opération OnReceiveEcho entrante dans le **catégories et opérations disponibles** zone de liste, comme indiqué dans l’illustration suivante :</span><span class="sxs-lookup"><span data-stu-id="3092f-156">You see the inbound OnReceiveEcho operation in the **Available categories and operations** list box, as shown in the following figure:</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/26b7b3c7-bc39-46f8-bc73-7d76fd3c02eb.gif "26b7b3c7-bc39-46f8-bc73-7d76fd3c02eb")  
  
## <a name="implementing-the-imetadatabrowsehandler"></a><span data-ttu-id="3092f-157">Implémentation de la IMetadataBrowseHandler</span><span class="sxs-lookup"><span data-stu-id="3092f-157">Implementing the IMetadataBrowseHandler</span></span>  
 <span data-ttu-id="3092f-158">Dans cette étape, vous mettez à jour la classe EchoAdapterMetadataBrowseHandler à mettre en œuvre de recherche de métadonnées de l’adaptateur Echo, autrement dit, pour implémenter le `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` méthode de la `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface.</span><span class="sxs-lookup"><span data-stu-id="3092f-158">In this step, you update the EchoAdapterMetadataBrowseHandler class to implement the Echo adapter's metadata browse, that is, to implement the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method of the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface.</span></span> <span data-ttu-id="3092f-159">Plus précisément, vous créez un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` pour chaque catégorie et l’opération de l’objet, définissez les valeurs appropriées pour cet objet, puis retourner le tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets pour les opérations et la catégorie.</span><span class="sxs-lookup"><span data-stu-id="3092f-159">Specifically, you create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for each category and operation, set appropriate values for that object, and then return the array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects for category and operations.</span></span> <span data-ttu-id="3092f-160">Gardez à l’esprit que, lorsque vous créez un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet, vous devez passer l’ID de nœud, et non le nom d’affichage.</span><span class="sxs-lookup"><span data-stu-id="3092f-160">Keep in mind that when you create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object, you need to pass in the node ID, not the display name.</span></span>  
  
#### <a name="to-update-the-echoadaptermetadatabrowsehandler-class"></a><span data-ttu-id="3092f-161">Pour mettre à jour de la classe EchoAdapterMetadataBrowseHandler</span><span class="sxs-lookup"><span data-stu-id="3092f-161">To update the EchoAdapterMetadataBrowseHandler class</span></span>  
  
1.  <span data-ttu-id="3092f-162">Dans l’Explorateur de solutions, double-cliquez sur le **EchoAdapterMetadataBrowseHandler.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="3092f-162">In Solution Explorer, double-click the **EchoAdapterMetadataBrowseHandler.cs** file.</span></span>  
  
2.  <span data-ttu-id="3092f-163">Dans l’éditeur Visual Studio, avec le bouton droit n’importe où dans l’éditeur, dans le menu contextuel, pointez sur **mode plan**, puis cliquez sur **arrêter le mode plan**.</span><span class="sxs-lookup"><span data-stu-id="3092f-163">In the Visual Studio editor, right-click anywhere within the editor, in the context menu, point to **Outlining**, and then click **Stop Outlining**.</span></span>  
  
3.  <span data-ttu-id="3092f-164">Dans l’éditeur Visual Studio, à l’intérieur de la **Parcourir** (méthode), remplacer la logique existante avec les informations suivantes pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet pour EchoMainCategory.</span><span class="sxs-lookup"><span data-stu-id="3092f-164">In the Visual Studio editor, inside the **Browse** method, replace the existing logic with the following to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for EchoMainCategory.</span></span>  
  
    ```csharp  
    if (MetadataRetrievalNode.Root.NodeId.Equals(nodeId))  
    {  
        MetadataRetrievalNode node = new MetadataRetrievalNode("EchoMainCategory");  
        node.DisplayName = "Main Category";  
        node.IsOperation = false;  
        node.Description = "This category contains inbound and outbound categories.";  
        node.Direction = MetadataRetrievalNodeDirections.Inbound | MetadataRetrievalNodeDirections.Outbound;  
        return new MetadataRetrievalNode[] { node };  
    }  
    ```  
  
4.  <span data-ttu-id="3092f-165">Continuez à ajouter la logique suivante pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet pour écho/OnReceiveEcho.</span><span class="sxs-lookup"><span data-stu-id="3092f-165">Continue adding the following logic to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for Echo/OnReceiveEcho.</span></span>  
  
    ```csharp  
    if( "EchoMainCategory".CompareTo(nodeId) == 0 )  
    {  
        // Inbound operations  
        MetadataRetrievalNode inOpNode1 = new MetadataRetrievalNode("Echo/OnReceiveEcho");  
        inOpNode1.DisplayName = "OnReceiveEcho";  
        inOpNode1.Description = "This operation echos the location and length of a file dropped in the specified file system.";  
        inOpNode1.Direction = MetadataRetrievalNodeDirections.Inbound;  
        inOpNode1.IsOperation = true;  
    ```  
  
5.  <span data-ttu-id="3092f-166">Continuez à ajouter la logique suivante pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet pour écho/EchoStrings.</span><span class="sxs-lookup"><span data-stu-id="3092f-166">Continue adding the following logic to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for Echo/EchoStrings.</span></span>  
  
    ```csharp  
    // Outbound operations  
    MetadataRetrievalNode outOpNode1 = new MetadataRetrievalNode("Echo/EchoStrings");  
    outOpNode1.DisplayName = "EchoStrings";  
    outOpNode1.Description = "This operation echoes the incoming string COUNT number of times in a string array.";  
    outOpNode1.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode1.IsOperation = true;  
    ```  
  
6.  <span data-ttu-id="3092f-167">Continuez à ajouter le code suivant pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet pour écho/EchoGreetings.</span><span class="sxs-lookup"><span data-stu-id="3092f-167">Continue adding the following code to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for Echo/EchoGreetings.</span></span>  
  
    ```csharp  
    MetadataRetrievalNode outOpNode2 = new MetadataRetrievalNode("Echo/EchoGreetings");  
    outOpNode2.DisplayName = "EchoGreetings";  
    outOpNode2.Description = "This operation echoes the incoming Greeting object COUNT number of times in an array of type Greeting.";  
    outOpNode2.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode2.IsOperation = true;  
    ```  
  
7.  <span data-ttu-id="3092f-168">Continuez à ajouter le code suivant pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet écho / EchoGreetingFromFile.</span><span class="sxs-lookup"><span data-stu-id="3092f-168">Continue adding the following code to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for Echo/ EchoGreetingFromFile.</span></span>  
  
    ```csharp  
    MetadataRetrievalNode outOpNode3 = new MetadataRetrievalNode("Echo/EchoCustomGreetingFromFile");  
    outOpNode3.DisplayName = "EchoCustomGreetingFromFile";  
    outOpNode3.Description = "This operation echoes the greeting object by reading its instance from a file. The Greeting object's metadata is obtained from a predefined XSD file.";  
    outOpNode3.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode3.IsOperation = true;  
    ```  
  
8.  <span data-ttu-id="3092f-169">Continuez à ajouter le code suivant pour retourner un tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets ou null si ne pas de correspondance.</span><span class="sxs-lookup"><span data-stu-id="3092f-169">Continue adding the following code to return an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects or null if not matched.</span></span>  
  
    ```  
        return new MetadataRetrievalNode[] { inOpNode1, outOpNode1, outOpNode2, outOpNode3 };  
    }  
    return null;  
    ```  
  
9. <span data-ttu-id="3092f-170">Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="3092f-170">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
10. <span data-ttu-id="3092f-171">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="3092f-171">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="3092f-172">Vous devez générer correctement le projet.</span><span class="sxs-lookup"><span data-stu-id="3092f-172">You should successfully build the project.</span></span> <span data-ttu-id="3092f-173">Dans le cas contraire, vérifiez que vous avez suivi toutes les étapes ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="3092f-173">If not, ensure that you have followed every step above.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3092f-174">Vous avez enregistré votre travail.</span><span class="sxs-lookup"><span data-stu-id="3092f-174">You saved your work.</span></span> <span data-ttu-id="3092f-175">Vous pouvez en toute sécurité fermer Visual Studio pour l’instant ou accédez à l’étape suivante, [étape 5 : implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="3092f-175">You can safely close Visual Studio at this time or go to the next step, [Step 5: Implement the Metadata Search Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="3092f-176">Quoi simplement ?</span><span class="sxs-lookup"><span data-stu-id="3092f-176">What Did I Just Do?</span></span>  
 <span data-ttu-id="3092f-177">Vous venez d’implémenter la navigation de capacité de la carte Echo, en mettant en œuvre dans les métadonnées du `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` méthode de la `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface.</span><span class="sxs-lookup"><span data-stu-id="3092f-177">You just implemented the metadata browsing capability of the Echo adapter, by implementing the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` method of the `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface.</span></span> <span data-ttu-id="3092f-178">Plus précisément, vous avez créé un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` pour la catégorie d’objet et il retournées sous forme de tableau de la `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets.</span><span class="sxs-lookup"><span data-stu-id="3092f-178">Specifically, you created a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for the category, and then returned it as an array of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span> <span data-ttu-id="3092f-179">Pour chaque opération, vous avez créé un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet et ensuite renvoyé tous ces objets dans un tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`.</span><span class="sxs-lookup"><span data-stu-id="3092f-179">For each operation, you created a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object, and then returned all those objects in an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3092f-180">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3092f-180">Next Steps</span></span>  
 <span data-ttu-id="3092f-181">Vous implémentez la recherche de métadonnées et les fonctionnalités de résolution et l’échange de messages sortants.</span><span class="sxs-lookup"><span data-stu-id="3092f-181">You implement metadata searching and resolving capabilities, and the outbound message exchange.</span></span> <span data-ttu-id="3092f-182">Enfin, vous générez et déployez l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="3092f-182">Finally, you build and deploy the Echo adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3092f-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3092f-183">See Also</span></span>  
 <span data-ttu-id="3092f-184">[Didacticiel 1 : Développer l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="3092f-184">[Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) </span></span>  
 <span data-ttu-id="3092f-185">[Étape 3 : Implémenter la connexion de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="3092f-185">[Step 3: Implement the Connection for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="3092f-186">Étape 5 : Implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="3092f-186">Step 5: Implement the Metadata Search Handler for the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md)
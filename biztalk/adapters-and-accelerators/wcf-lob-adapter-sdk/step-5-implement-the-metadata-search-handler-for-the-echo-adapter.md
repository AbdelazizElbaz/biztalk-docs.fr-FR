---
title: "Étape 5 : Implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur d’écho | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a133a99-1d6c-4634-b928-0f4f23c6f6e4
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d241499e10a944eb1941b680bc73b97ce6ffd93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-implement-the-metadata-search-handler-for-the-echo-adapter"></a><span data-ttu-id="afac7-102">Étape 5 : Implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="afac7-102">Step 5: Implement the Metadata Search Handler for the Echo Adapter</span></span>
<span data-ttu-id="afac7-103">![L’étape 5 de 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")</span><span class="sxs-lookup"><span data-stu-id="afac7-103">![Step 5 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")</span></span>  
  
 <span data-ttu-id="afac7-104">**Durée :** 30 minutes</span><span class="sxs-lookup"><span data-stu-id="afac7-104">**Time to complete:** 30 minutes</span></span>  
  
 <span data-ttu-id="afac7-105">Dans cette étape du didacticiel, vous implémentez la fonction de recherche de l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="afac7-105">In this step of the tutorial, you implement the search capability of the Echo adapter.</span></span> <span data-ttu-id="afac7-106">Contrairement à parcourir, la recherche est facultative.</span><span class="sxs-lookup"><span data-stu-id="afac7-106">Unlike browse, search is optional.</span></span> <span data-ttu-id="afac7-107">Conformément à la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], pour prendre en charge la fonctionnalité de recherche, vous devez implémenter la `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface.</span><span class="sxs-lookup"><span data-stu-id="afac7-107">According to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], to support search capability, you must implement the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface.</span></span> <span data-ttu-id="afac7-108">Pour l’adaptateur d’écho le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère automatiquement une classe dérivée, appelée EchoAdapterMetadataSearchHandler.</span><span class="sxs-lookup"><span data-stu-id="afac7-108">For the Echo adapter, the [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] automatically generates one derived class called EchoAdapterMetadataSearchHandler.</span></span>  
  
 <span data-ttu-id="afac7-109">Tout d’abord de mettre à jour de la classe EchoAdapterMetadataSearchHandler pour mieux comprendre comment implémenter cette interface, comment remplir `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet et la façon dont les résultats de recherche apparaissent dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] outil.</span><span class="sxs-lookup"><span data-stu-id="afac7-109">You first update the EchoAdapterMetadataSearchHandler class to get a better understanding of how to implement this interface, how to populate  `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object, and how the search results appear in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="afac7-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="afac7-110">Prerequisites</span></span>  
 <span data-ttu-id="afac7-111">Avant de commencer cette étape, vous devez effectuer [étape 4 : implémenter le Gestionnaire de parcourir des métadonnées de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="afac7-111">Before you begin this step, complete [Step 4: Implement the Metadata Browse Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md).</span></span> <span data-ttu-id="afac7-112">Vous devez également avoir pleinement conscience sur les classes suivantes :</span><span class="sxs-lookup"><span data-stu-id="afac7-112">You must also have a clear understanding about the following classes:</span></span>  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`
  
-   `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNodeDirections`  
  
## <a name="the-imetadatasearchhandler-interface"></a><span data-ttu-id="afac7-113">L’Interface IMetadataSearchHandler</span><span class="sxs-lookup"><span data-stu-id="afac7-113">The IMetadataSearchHandler Interface</span></span>  
 <span data-ttu-id="afac7-114">Le `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` est défini en tant que :</span><span class="sxs-lookup"><span data-stu-id="afac7-114">The `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` is defined as:</span></span>  
  
```  
public interface IMetadataSearchHandler : IConnectionHandler, IDisposable  
{  
    MetadataRetrievalNode[] Search(string nodeId, string searchCriteria, int maxChildNodes, TimeSpan timeout);  
}  
```  
  
 <span data-ttu-id="afac7-115">Le `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` méthode retourne un tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets basés sur les critères de recherche.</span><span class="sxs-lookup"><span data-stu-id="afac7-115">The `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` method returns an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects based on the search criteria.</span></span> <span data-ttu-id="afac7-116">Les définitions de paramètres pour la méthode de recherche sont décrites dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="afac7-116">The parameter definitions for the Search method are described in the following table:</span></span>  
  
|<span data-ttu-id="afac7-117">**Paramètre**</span><span class="sxs-lookup"><span data-stu-id="afac7-117">**Parameter**</span></span>|<span data-ttu-id="afac7-118">**Définition**</span><span class="sxs-lookup"><span data-stu-id="afac7-118">**Definition**</span></span>|  
|-------------------|--------------------|  
|<span data-ttu-id="afac7-119">nodeId</span><span class="sxs-lookup"><span data-stu-id="afac7-119">nodeId</span></span>|<span data-ttu-id="afac7-120">L’ID de nœud pour commencer la recherche.</span><span class="sxs-lookup"><span data-stu-id="afac7-120">The node ID to start searching from.</span></span> <span data-ttu-id="afac7-121">Si null ou une chaîne vide (« »), les opérations sont récupérées à partir du nœud racine (« / »).</span><span class="sxs-lookup"><span data-stu-id="afac7-121">If null or an empty string (""), operations will be retrieved from the root node ("/").</span></span>|  
|<span data-ttu-id="afac7-122">searchCriteria</span><span class="sxs-lookup"><span data-stu-id="afac7-122">searchCriteria</span></span>|<span data-ttu-id="afac7-123">Les critères de recherche, qui est spécifique à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="afac7-123">The search criteria, which is adapter-specific.</span></span> <span data-ttu-id="afac7-124">Si aucun critère de recherche n’est spécifiés, l’adaptateur doit retourner tous les nœuds.</span><span class="sxs-lookup"><span data-stu-id="afac7-124">If no search criteria are specified, the adapter should return all nodes.</span></span>|  
|<span data-ttu-id="afac7-125">maxChildNodes</span><span class="sxs-lookup"><span data-stu-id="afac7-125">maxChildNodes</span></span>|<span data-ttu-id="afac7-126">Le nombre maximal de nœuds de résultat à retourner.</span><span class="sxs-lookup"><span data-stu-id="afac7-126">The maximum number of result nodes to return.</span></span> <span data-ttu-id="afac7-127">Int32.Max permet de récupérer tous les nœuds de résultat.</span><span class="sxs-lookup"><span data-stu-id="afac7-127">Use Int32.Max to retrieve all result nodes.</span></span><br /><br /> <span data-ttu-id="afac7-128">Non pris en charge par l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="afac7-128">Not supported by the Echo adapter.</span></span>|  
|<span data-ttu-id="afac7-129">délai d'expiration</span><span class="sxs-lookup"><span data-stu-id="afac7-129">timeout</span></span>|<span data-ttu-id="afac7-130">La durée maximale autorisée pour l’opération se termine.</span><span class="sxs-lookup"><span data-stu-id="afac7-130">The maximum time allowed for the operation to complete.</span></span><br /><br /> <span data-ttu-id="afac7-131">Non pris en charge par l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="afac7-131">Not supported by the Echo adapter.</span></span>|  
  
 <span data-ttu-id="afac7-132">Pour les résultats de recherche, votre adaptateur peut choisir de retourner des nœuds de catégorie ou nœuds d’opération ou les deux.</span><span class="sxs-lookup"><span data-stu-id="afac7-132">For search result, your adapter can choose to return either category nodes or operation nodes, or both.</span></span> <span data-ttu-id="afac7-133">Il incombe au type de fonctionnalité de recherche de votre adaptateur prend en charge.</span><span class="sxs-lookup"><span data-stu-id="afac7-133">It is up to the type of search feature your adapter supports.</span></span>  
  
## <a name="echo-adapter-metadata-search"></a><span data-ttu-id="afac7-134">Adaptateur echo recherche de métadonnées</span><span class="sxs-lookup"><span data-stu-id="afac7-134">Echo adapter Metadata Search</span></span>  
 <span data-ttu-id="afac7-135">Selon les catégories et les opérations de votre système cible, il existe plusieurs façons pour générer un tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets à retourner.</span><span class="sxs-lookup"><span data-stu-id="afac7-135">Depending on your target system's categories and operations, there are many ways to build an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects to return.</span></span> <span data-ttu-id="afac7-136">La carte d’écho implémente la fonctionnalité de recherche consiste à passer par chaque opération avec son ID de nœud dans la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="afac7-136">The way Echo adapter implements the search functionality is to go through every operation with its node ID in the following list:</span></span>  
  
```  
Echo/OnReceiveEcho, inbound operation  
Echo/EchoStrings, outbound operation  
Echo/EchoGreetings, outbound operation  
Echo/EchoGreetingFromFile, outbound operation  
```  
  
-   <span data-ttu-id="afac7-137">Si l’ID de nœud correspond alors à des critères de recherche, il crée un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` à l’aide de l’ID de nœud de l’opération de l’objet, puis affecte les propriétés avec des valeurs.</span><span class="sxs-lookup"><span data-stu-id="afac7-137">If the node ID then matches the search criteria, it creates a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object using the node ID of the operation, and then assigns the properties with values.</span></span> <span data-ttu-id="afac7-138">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="afac7-138">For example,</span></span>  
  
    ```  
    MetadataRetrievalNode nodeInbound = new MetadataRetrievalNode("Echo/OnReceiveEcho"); //create the MetadataRetrievalNode using the operation's node ID.  
    nodeInbound.DisplayName = "OnReceiveEcho"; //The Display Name shown in the Name column of the Add Adapter Service Reference Visual Studio Plug-in  
    nodeInbound.Description = "This operation echoes the location and length of a file dropped in the specified file system.";  //The Description shown as the tool tip in the Add Adapter Service Visual Studio Plug-in  
    nodeInbound.Direction = MetadataRetrievalNodeDirections.Inbound;    //It is an inbound operation  
    nodeInbound.IsOperation = true;  //It is an operation, not category.  
    ```  
  
-   <span data-ttu-id="afac7-139">Puis ajoutez l’objet à une collection de le `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`s, par exemple,</span><span class="sxs-lookup"><span data-stu-id="afac7-139">And then add the object to a collection of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`s, for example,</span></span>  
  
    ```  
    resultList.Add(nodeInbound);  
    ```  
  
-   <span data-ttu-id="afac7-140">Enfin, retourne la collection dans un format de tableau.</span><span class="sxs-lookup"><span data-stu-id="afac7-140">Lastly returns the collection in an array format.</span></span>  
  
    ```  
    return resultList.ToArray();  
    ```  
  
 <span data-ttu-id="afac7-141">Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] outils pour effectuer une recherche basée sur une connexion pour les opérations disponibles.</span><span class="sxs-lookup"><span data-stu-id="afac7-141">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] tools to perform a connection-based search for the available operations.</span></span> <span data-ttu-id="afac7-142">Par exemple, l’illustration suivante montre que lorsque le critère de recherche est la chaîne **salutation**, la recherche retourne le **EchoGreetings** et **EchoGreetingFromFile** opérations.</span><span class="sxs-lookup"><span data-stu-id="afac7-142">For example, the following figure shows that when the searching criteria is the string **Greeting**, the search returns the **EchoGreetings** and **EchoGreetingFromFile** operations.</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/874c046a-590f-4047-9b9c-bb8074664755.gif "874c046a-590f-4047-9b9c-bb8074664755")  
  
 <span data-ttu-id="afac7-143">Si aucune correspondance n’est trouvée, l’outil renvoie le message d’erreur indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="afac7-143">If no match is found, either tool will return the error message shown in the following figure.</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/cb1f79a2-a63d-4828-9dce-905c026cd1dc.gif "cb1f79a2-a63d-4828-9dce-905c026cd1dc")  
  
## <a name="implementing-the-imetadatasearchhandler"></a><span data-ttu-id="afac7-144">Implémentation de la IMetadataSearchHandler</span><span class="sxs-lookup"><span data-stu-id="afac7-144">Implementing the IMetadataSearchHandler</span></span>  
 <span data-ttu-id="afac7-145">Vous allez implémenter le `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` méthode de la `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface.</span><span class="sxs-lookup"><span data-stu-id="afac7-145">You will implement the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` method of the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface.</span></span> <span data-ttu-id="afac7-146">Si le nom complet de l’opération correspond aux critères de recherche, vous allez créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet pour cette opération, puis ajoutez cet objet à un tableau de la `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets.</span><span class="sxs-lookup"><span data-stu-id="afac7-146">If the operation's display name matches the search criteria, you will create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for that operation, and then add that object to an array of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span>  
  
#### <a name="to-update-the-echoadaptermetadatasearchhandler-class"></a><span data-ttu-id="afac7-147">Pour mettre à jour de la classe EchoAdapterMetadataSearchHandler</span><span class="sxs-lookup"><span data-stu-id="afac7-147">To update the EchoAdapterMetadataSearchHandler class</span></span>  
  
1.  <span data-ttu-id="afac7-148">Dans l’Explorateur de solutions, double-cliquez sur le **EchoAdapterMetadataSearchHandler.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="afac7-148">In Solution Explorer, double-click the **EchoAdapterMetadataSearchHandler.cs** file.</span></span>  
  
2.  <span data-ttu-id="afac7-149">Dans l’éditeur Visual Studio, à l’intérieur de la **recherche** (méthode), remplacer la logique existante par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="afac7-149">In the Visual Studio editor, inside the **Search** method, replace the existing logic with the following.</span></span> <span data-ttu-id="afac7-150">Cette logique crée un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet si Echo/OnReceiveEcho correspond aux critères de recherche spécifiés.</span><span class="sxs-lookup"><span data-stu-id="afac7-150">This logic creates a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object if Echo/OnReceiveEcho matches the specified search criteria.</span></span>  
  
    ```csharp  
    List<MetadataRetrievalNode> resultList = new List<MetadataRetrievalNode>();  
    if ("OnReceiveEcho".ToLower().Contains(searchCriteria.ToLower()))  
    {  
        MetadataRetrievalNode nodeInbound = new MetadataRetrievalNode("Echo/OnReceiveEcho");  
        nodeInbound.DisplayName = "OnReceiveEcho";  
        nodeInbound.Description = "This operation echoes the location and length of a file dropped in the specified file system.";  
        nodeInbound.Direction = MetadataRetrievalNodeDirections.Inbound;  
        nodeInbound.IsOperation = true;  
        resultList.Add(nodeInbound);  
    }  
    ```  
  
3.  <span data-ttu-id="afac7-151">Continuez à ajouter la logique suivante pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet si Echo/EchoStrings correspond aux critères de recherche spécifiés.</span><span class="sxs-lookup"><span data-stu-id="afac7-151">Continue adding the following logic to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object if Echo/EchoStrings matches the specified search criteria.</span></span>  
  
    ```csharp  
    if ("EchoStrings".ToLower().Contains(searchCriteria.ToLower()))  
    {  
        MetadataRetrievalNode outOpNode1 = new MetadataRetrievalNode("Echo/EchoStrings");  
        outOpNode1.DisplayName = "EchoStrings";  
        outOpNode1.Description = "This operation echoes the incoming string COUNT number of times in a string array.";  
        outOpNode1.Direction = MetadataRetrievalNodeDirections.Outbound;  
        outOpNode1.IsOperation = true;  
        resultList.Add(outOpNode1);  
    }  
    ```  
  
4.  <span data-ttu-id="afac7-152">Continuez à ajouter la logique suivante pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet si Echo/EchoGreetings correspond aux critères de recherche spécifiés.</span><span class="sxs-lookup"><span data-stu-id="afac7-152">Continue adding the following logic to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object if Echo/EchoGreetings matches the specified search criteria.</span></span>  
  
    ```csharp  
    if ("EchoGreetings".ToLower().Contains(searchCriteria.ToLower()))  
        {  
            MetadataRetrievalNode outOpNode2 = new MetadataRetrievalNode("Echo/EchoGreetings");  
            outOpNode2.DisplayName = "EchoGreetings";  
            outOpNode2.Description = "This operation echoes the incoming Greeting object COUNT number of times in an array of type Greeting.";  
            outOpNode2.Direction = MetadataRetrievalNodeDirections.Outbound;  
            outOpNode2.IsOperation = true;  
            resultList.Add(outOpNode2);  
        }  
    ```  
  
5.  <span data-ttu-id="afac7-153">Continuez à ajouter le code suivant pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet si Echo/EchoGreetingFromFile correspond aux critères de recherche spécifiés.</span><span class="sxs-lookup"><span data-stu-id="afac7-153">Continue adding the following code to create a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object if Echo/EchoGreetingFromFile matches the specified search criteria.</span></span>  
  
    ```csharp  
    if ("EchoCustomGreetingFromFile".ToLower().Contains(searchCriteria.ToLower()))  
    {  
        MetadataRetrievalNode outOpNode3 = new MetadataRetrievalNode("Echo/EchoCustomGreetingFromFile");  
        outOpNode3.DisplayName = "EchoCustomGreetingFromFile";  
        outOpNode3.Description = "This operation echoes the greeting object by reading its instance from a file. The Greeting object's metadata is obtained from a predefined XSD file.";  
        outOpNode3.Direction = MetadataRetrievalNodeDirections.Outbound;  
        outOpNode3.IsOperation = true;  
        resultList.Add(outOpNode3);  
    }  
    ```  
  
6.  <span data-ttu-id="afac7-154">Continuez à ajouter le code suivant pour retourner un tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets.</span><span class="sxs-lookup"><span data-stu-id="afac7-154">Continue adding the following code to return an array of `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span>  
  
    ```csharp  
    return resultList.ToArray();  
    ```  
  
7.  <span data-ttu-id="afac7-155">Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="afac7-155">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
8.  <span data-ttu-id="afac7-156">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="afac7-156">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="afac7-157">Vous devez correctement compilé le projet.</span><span class="sxs-lookup"><span data-stu-id="afac7-157">You should successfully compiled the project.</span></span> <span data-ttu-id="afac7-158">Dans le cas contraire, vérifiez que vous avez suivi toutes les étapes ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="afac7-158">If not, ensure that you have followed every step above.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="afac7-159">Vous avez enregistré votre travail.</span><span class="sxs-lookup"><span data-stu-id="afac7-159">You saved your work.</span></span> <span data-ttu-id="afac7-160">Vous pouvez en toute sécurité fermer Visual Studio pour l’instant ou accédez à l’étape suivante, [étape 6 : implémenter le Gestionnaire de résoudre des métadonnées de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="afac7-160">You can safely close Visual Studio at this time or go to the next step, [Step 6: Implement the Metadata Resolve Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="afac7-161">Quoi simplement ?</span><span class="sxs-lookup"><span data-stu-id="afac7-161">What Did I Just Do?</span></span>  
 <span data-ttu-id="afac7-162">Vous venez d’implémenter les métadonnées de recherche de capacité de la carte Echo, en implémentant le `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` méthode de la `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface.</span><span class="sxs-lookup"><span data-stu-id="afac7-162">You just implemented the metadata searching capability of the Echo adapter, by implementing the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` method of the `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface.</span></span> <span data-ttu-id="afac7-163">Plus précisément, vous avez créé un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet pour chaque opération qui correspond aux critères, puis renvoyé un tableau de la `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets.</span><span class="sxs-lookup"><span data-stu-id="afac7-163">Specifically, you created a `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` object for every operation that matches the criteria and then returned an array of the `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objects.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="afac7-164">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="afac7-164">Next Steps</span></span>  
 <span data-ttu-id="afac7-165">Vous allez implémenter les métadonnées de résolution de capacité et les fonctionnalités d’exchange de messages sortants et entrants.</span><span class="sxs-lookup"><span data-stu-id="afac7-165">You will implement the metadata resolving capability, and the outbound and inbound message exchange capabilities.</span></span> <span data-ttu-id="afac7-166">Enfin, vous générera et déploiera l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="afac7-166">Finally, you will build and deploy the Echo adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afac7-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afac7-167">See Also</span></span>  
 <span data-ttu-id="afac7-168">[Étape 4 : Implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="afac7-168">[Step 4: Implement the Metadata Browse Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md) </span></span>  
 <span data-ttu-id="afac7-169">[Étape 6 : Implémenter le Gestionnaire de résoudre des métadonnées de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="afac7-169">[Step 6: Implement the Metadata Resolve Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="afac7-170">Didacticiel 1 : Développer l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="afac7-170">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)
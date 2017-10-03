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
# <a name="step-5-implement-the-metadata-search-handler-for-the-echo-adapter"></a>Étape 5 : Implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur d’écho
![L’étape 5 de 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")  
  
 **Durée :** 30 minutes  
  
 Dans cette étape du didacticiel, vous implémentez la fonction de recherche de l’adaptateur de l’écho. Contrairement à parcourir, la recherche est facultative. Conformément à la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], pour prendre en charge la fonctionnalité de recherche, vous devez implémenter la `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface. Pour l’adaptateur d’écho le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère automatiquement une classe dérivée, appelée EchoAdapterMetadataSearchHandler.  
  
 Tout d’abord de mettre à jour de la classe EchoAdapterMetadataSearchHandler pour mieux comprendre comment implémenter cette interface, comment remplir `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet et la façon dont les résultats de recherche apparaissent dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] outil.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant de commencer cette étape, vous devez effectuer [étape 4 : implémenter le Gestionnaire de parcourir des métadonnées de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md). Vous devez également avoir pleinement conscience sur les classes suivantes :  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`
  
-   `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNodeDirections`  
  
## <a name="the-imetadatasearchhandler-interface"></a>L’Interface IMetadataSearchHandler  
 Le `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` est défini en tant que :  
  
```  
public interface IMetadataSearchHandler : IConnectionHandler, IDisposable  
{  
    MetadataRetrievalNode[] Search(string nodeId, string searchCriteria, int maxChildNodes, TimeSpan timeout);  
}  
```  
  
 Le `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` méthode retourne un tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets basés sur les critères de recherche. Les définitions de paramètres pour la méthode de recherche sont décrites dans le tableau suivant :  
  
|**Paramètre**|**Définition**|  
|-------------------|--------------------|  
|nodeId|L’ID de nœud pour commencer la recherche. Si null ou une chaîne vide (« »), les opérations sont récupérées à partir du nœud racine (« / »).|  
|searchCriteria|Les critères de recherche, qui est spécifique à l’adaptateur. Si aucun critère de recherche n’est spécifiés, l’adaptateur doit retourner tous les nœuds.|  
|maxChildNodes|Le nombre maximal de nœuds de résultat à retourner. Int32.Max permet de récupérer tous les nœuds de résultat.<br /><br /> Non pris en charge par l’adaptateur de l’écho.|  
|délai d'expiration|La durée maximale autorisée pour l’opération se termine.<br /><br /> Non pris en charge par l’adaptateur de l’écho.|  
  
 Pour les résultats de recherche, votre adaptateur peut choisir de retourner des nœuds de catégorie ou nœuds d’opération ou les deux. Il incombe au type de fonctionnalité de recherche de votre adaptateur prend en charge.  
  
## <a name="echo-adapter-metadata-search"></a>Adaptateur echo recherche de métadonnées  
 Selon les catégories et les opérations de votre système cible, il existe plusieurs façons pour générer un tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets à retourner. La carte d’écho implémente la fonctionnalité de recherche consiste à passer par chaque opération avec son ID de nœud dans la liste suivante :  
  
```  
Echo/OnReceiveEcho, inbound operation  
Echo/EchoStrings, outbound operation  
Echo/EchoGreetings, outbound operation  
Echo/EchoGreetingFromFile, outbound operation  
```  
  
-   Si l’ID de nœud correspond alors à des critères de recherche, il crée un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` à l’aide de l’ID de nœud de l’opération de l’objet, puis affecte les propriétés avec des valeurs. Par exemple :  
  
    ```  
    MetadataRetrievalNode nodeInbound = new MetadataRetrievalNode("Echo/OnReceiveEcho"); //create the MetadataRetrievalNode using the operation's node ID.  
    nodeInbound.DisplayName = "OnReceiveEcho"; //The Display Name shown in the Name column of the Add Adapter Service Reference Visual Studio Plug-in  
    nodeInbound.Description = "This operation echoes the location and length of a file dropped in the specified file system.";  //The Description shown as the tool tip in the Add Adapter Service Visual Studio Plug-in  
    nodeInbound.Direction = MetadataRetrievalNodeDirections.Inbound;    //It is an inbound operation  
    nodeInbound.IsOperation = true;  //It is an operation, not category.  
    ```  
  
-   Puis ajoutez l’objet à une collection de le `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`s, par exemple,  
  
    ```  
    resultList.Add(nodeInbound);  
    ```  
  
-   Enfin, retourne la collection dans un format de tableau.  
  
    ```  
    return resultList.ToArray();  
    ```  
  
 Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] outils pour effectuer une recherche basée sur une connexion pour les opérations disponibles. Par exemple, l’illustration suivante montre que lorsque le critère de recherche est la chaîne **salutation**, la recherche retourne le **EchoGreetings** et **EchoGreetingFromFile** opérations.  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/874c046a-590f-4047-9b9c-bb8074664755.gif "874c046a-590f-4047-9b9c-bb8074664755")  
  
 Si aucune correspondance n’est trouvée, l’outil renvoie le message d’erreur indiqué dans l’illustration suivante.  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/cb1f79a2-a63d-4828-9dce-905c026cd1dc.gif "cb1f79a2-a63d-4828-9dce-905c026cd1dc")  
  
## <a name="implementing-the-imetadatasearchhandler"></a>Implémentation de la IMetadataSearchHandler  
 Vous allez implémenter le `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` méthode de la `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface. Si le nom complet de l’opération correspond aux critères de recherche, vous allez créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet pour cette opération, puis ajoutez cet objet à un tableau de la `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets.  
  
#### <a name="to-update-the-echoadaptermetadatasearchhandler-class"></a>Pour mettre à jour de la classe EchoAdapterMetadataSearchHandler  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur le **EchoAdapterMetadataSearchHandler.cs** fichier.  
  
2.  Dans l’éditeur Visual Studio, à l’intérieur de la **recherche** (méthode), remplacer la logique existante par le code suivant. Cette logique crée un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet si Echo/OnReceiveEcho correspond aux critères de recherche spécifiés.  
  
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
  
3.  Continuez à ajouter la logique suivante pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet si Echo/EchoStrings correspond aux critères de recherche spécifiés.  
  
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
  
4.  Continuez à ajouter la logique suivante pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet si Echo/EchoGreetings correspond aux critères de recherche spécifiés.  
  
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
  
5.  Continuez à ajouter le code suivant pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet si Echo/EchoGreetingFromFile correspond aux critères de recherche spécifiés.  
  
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
  
6.  Continuez à ajouter le code suivant pour retourner un tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets.  
  
    ```csharp  
    return resultList.ToArray();  
    ```  
  
7.  Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
8.  Dans le menu **Générer** , cliquez sur **Générer la solution**. Vous devez correctement compilé le projet. Dans le cas contraire, vérifiez que vous avez suivi toutes les étapes ci-dessus.  
  
    > [!NOTE]
    >  Vous avez enregistré votre travail. Vous pouvez en toute sécurité fermer Visual Studio pour l’instant ou accédez à l’étape suivante, [étape 6 : implémenter le Gestionnaire de résoudre des métadonnées de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md).  
  
## <a name="what-did-i-just-do"></a>Quoi simplement ?  
 Vous venez d’implémenter les métadonnées de recherche de capacité de la carte Echo, en implémentant le `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler.Search%2A` méthode de la `Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler` interface. Plus précisément, vous avez créé un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet pour chaque opération qui correspond aux critères, puis renvoyé un tableau de la `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous allez implémenter les métadonnées de résolution de capacité et les fonctionnalités d’exchange de messages sortants et entrants. Enfin, vous générera et déploiera l’adaptateur de l’écho.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 : Implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md)   
 [Étape 6 : Implémenter le Gestionnaire de résoudre des métadonnées de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md)   
 [Didacticiel 1 : Développer l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)
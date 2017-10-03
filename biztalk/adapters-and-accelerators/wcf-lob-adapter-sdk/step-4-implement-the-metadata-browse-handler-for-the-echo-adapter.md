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
# <a name="step-4-implement-the-metadata-browse-handler-for-the-echo-adapter"></a>Étape 4 : Implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur d’écho
![L’étape 4 de 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-4of9.gif "Step_4of9")  
  
 **Durée :** 45 minutes  
  
 Dans cette étape, vous implémentez la fonctionnalité de navigation de l’adaptateur de l’écho. Cette fonctionnalité permet à votre carte effectuer une recherche basée sur une connexion afin d’obtenir les métadonnées à partir du système cible. Indépendamment des fonctionnalités de votre carte, votre adaptateur doit prendre en charge la fonctionnalité Parcourir.  
  
 Conformément à la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], pour prendre en charge la fonctionnalité de navigation, vous devez implémenter la `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface. Pour l’adaptateur d’écho le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère automatiquement la classe dérivée, appelée EchoAdapterMetadataBrowseHandler.  
  
 Dans les étapes suivantes, vous mettez à jour cette classe pour obtenir une meilleure compréhension de l’implémentation de la `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` (méthode), comment définir différentes propriétés de la `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet, et comment l’opération et les nœuds de catégorie pris en charge par l’adaptateur s’affichent dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] outil.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant de commencer cette étape, vous devez avoir terminé avec succès [étape 3 : implémenter la connexion de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md). Vous devez également comprendre les classes suivantes :  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`  
  
-   `Microsoft.ServiceModel.Channels.MetadataRetrievalNodeDirections`  
  
-   `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`  
  
## <a name="the-imetadatabrowsehandler-interface"></a>L’Interface IMetadataBrowseHandler  
 Le `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface est définie en tant que :  
  
```  
public interface IMetadataBrowseHandler : IConnectionHandler, IDisposable  
{  
    MetadataRetrievalNode[] Browse(string nodeId, int childStartIndex, int maxChildNodes, TimeSpan timeout);  
}  
```  
  
 Le `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` méthode retourne un tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets basés sur les paramètres de méthode. Les définitions de paramètres pour la `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` méthode sont décrites dans le tableau suivant.  
  
> [!NOTE]
>  L’implémentation de l’adaptateur Echo utilise uniquement l’ID de nœud et ignore les trois autres paramètres, car l’adaptateur écho prend en charge seulement quelques nœuds.  
  
|**Paramètre**|**Définition**|  
|-------------------|--------------------|  
|nodeId|Chaque élément dans la hiérarchie de l’Explorateur de métadonnées (le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et<br /><br /> [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]) a un attribut nodeId. Chaque ID de nœud doit être unique et peut être une catégorie ou une opération. La catégorie peut avoir des sous-catégories. **Remarque :** si null ou une chaîne vide (« »), les opérations sont récupérées à partir du nœud racine (« / ») par défaut.|  
|childStartIndex|L’index du premier enfant à retourner.<br /><br /> Non pris en charge par l’adaptateur de l’écho.|  
|maxChildNodes|Le nombre maximal de nœuds de résultat à retourner. Int32.Max permet de récupérer tous les nœuds de résultat.<br /><br /> Non pris en charge par l’adaptateur de l’écho.|  
|délai d'expiration|La durée maximale autorisée pour l’opération se termine.<br /><br /> Non pris en charge par l’adaptateur de l’écho.|  
  
 Lorsque vous implémentez le `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` (méthode), vous devez ajouter chaque nœud de catégorie et l’opération sur le tableau des `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets. Pour spécifier un nœud en tant que catégorie, définissez la `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A` à `false`. Pour spécifier un nœud en tant qu’opération, définissez la `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.IsOperation%2A` à `true`.  
  
## <a name="echo-adapter-metadata-browse"></a>Recherche de métadonnées d’adaptateur écho  
 Selon les catégories et les opérations de votre système cible, il existe plusieurs façons pour générer un tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets. Les opérations et les catégories que vous choisissez doivent représenter les opérations que vous souhaitez exposer. Mais pour l’adaptateur Echo, elle crée simplement un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet pour chacun des nœuds suivants avec l’ID de nœud répertorié :  
  
```  
EchoMainCategory  (node under the root node)  
        Echo/EchoStrings   (outbound operation)  
        Echo/EchoGreetings(outbound operation)  
        Echo/EchoCustomGreetingFromFile(outbound operation)  
        Echo/OnReceiveEcho (inbound operation)  
```  
  
 Le EchoMainCategory est le nœud de catégorie sous le nœud racine (« / »). Ce nœud est également utilisé comme catégorie pour les opérations entrantes et sortantes. Par conséquent, lorsque vous créez le `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet de cette catégorie, vous pouvez procédez comme suit :  
  
```  
MetadataRetrievalNode node = new MetadataRetrievalNode("EchoMainCategory");  
node.IsOperation = false; //category  
node.Direction = MetadataRetrievalNodeDirections.Inbound | MetadataRetrievalNodeDirections.Outbound  //for both inbound and outbound  
```  
  
 Pour une opération sortante tels que Echo/EchoString qui appartient à la EchoMainCategory, vous pouvez procédez comme suit :  
  
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
  
 Pour une opération entrante comme écho/OnReceiveEcho qui appartient à la EchoMainCategory, vous pouvez procédez comme suit :  
  
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
  
 Lorsque le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] outils Explorer les métadonnées de l’adaptateur Echo, par défaut, il démarre à partir du nœud racine (« / »).  
  
 L’illustration suivante montre que le nœud EchoMainCategory apparaît sous le nœud racine (« / ») :  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4b9d0b8-f07f-4342-815f-9ef1507b0980.gif "e4b9d0b8-f07f-4342-815f-9ef1507b0980")  
  
 Pour rechercher les trois opérations sortantes, dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] outil, dans le **sélectionner type de contrat** la liste déroulante, sélectionnez le **Client (Outbound operations)** option. Vous voyez ces opérations dans le **catégories et opérations disponibles** zone de liste, comme indiqué ci-dessous :  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/c8755805-cbb0-40f1-887a-a3123f71ae7e.gif "c8755805-cbb0-40f1-887a-a3123f71ae7e")  
  
 Dans la figure précédente, notez que le `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A` valeur apparaît dans le **nom** colonne de la **catégories et opérations disponibles** zone de liste. Le paramètre passé dans le `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` constructeur s’affiche dans le **ID de nœud** colonne de la **catégories et opérations disponibles** zone de liste et le `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.Description%2A` valeur apparaît sous la forme d’info-bulle qui contient la description, lorsque vous cliquez sur le `Microsoft.ServiceModel.Channels.MetadataRetrievalNode.DisplayName%2A`.  
  
 Pour voir les opérations entrantes, dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] outil, dans le **sélectionner type de contrat** la liste déroulante, sélectionnez le **Service (opérations entrantes)** option. Vous voyez l’opération OnReceiveEcho entrante dans le **catégories et opérations disponibles** zone de liste, comme indiqué dans l’illustration suivante :  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/26b7b3c7-bc39-46f8-bc73-7d76fd3c02eb.gif "26b7b3c7-bc39-46f8-bc73-7d76fd3c02eb")  
  
## <a name="implementing-the-imetadatabrowsehandler"></a>Implémentation de la IMetadataBrowseHandler  
 Dans cette étape, vous mettez à jour la classe EchoAdapterMetadataBrowseHandler à mettre en œuvre de recherche de métadonnées de l’adaptateur Echo, autrement dit, pour implémenter le `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` méthode de la `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface. Plus précisément, vous créez un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` pour chaque catégorie et l’opération de l’objet, définissez les valeurs appropriées pour cet objet, puis retourner le tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets pour les opérations et la catégorie. Gardez à l’esprit que, lorsque vous créez un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet, vous devez passer l’ID de nœud, et non le nom d’affichage.  
  
#### <a name="to-update-the-echoadaptermetadatabrowsehandler-class"></a>Pour mettre à jour de la classe EchoAdapterMetadataBrowseHandler  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur le **EchoAdapterMetadataBrowseHandler.cs** fichier.  
  
2.  Dans l’éditeur Visual Studio, avec le bouton droit n’importe où dans l’éditeur, dans le menu contextuel, pointez sur **mode plan**, puis cliquez sur **arrêter le mode plan**.  
  
3.  Dans l’éditeur Visual Studio, à l’intérieur de la **Parcourir** (méthode), remplacer la logique existante avec les informations suivantes pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet pour EchoMainCategory.  
  
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
  
4.  Continuez à ajouter la logique suivante pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet pour écho/OnReceiveEcho.  
  
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
  
5.  Continuez à ajouter la logique suivante pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet pour écho/EchoStrings.  
  
    ```csharp  
    // Outbound operations  
    MetadataRetrievalNode outOpNode1 = new MetadataRetrievalNode("Echo/EchoStrings");  
    outOpNode1.DisplayName = "EchoStrings";  
    outOpNode1.Description = "This operation echoes the incoming string COUNT number of times in a string array.";  
    outOpNode1.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode1.IsOperation = true;  
    ```  
  
6.  Continuez à ajouter le code suivant pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet pour écho/EchoGreetings.  
  
    ```csharp  
    MetadataRetrievalNode outOpNode2 = new MetadataRetrievalNode("Echo/EchoGreetings");  
    outOpNode2.DisplayName = "EchoGreetings";  
    outOpNode2.Description = "This operation echoes the incoming Greeting object COUNT number of times in an array of type Greeting.";  
    outOpNode2.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode2.IsOperation = true;  
    ```  
  
7.  Continuez à ajouter le code suivant pour créer un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objet écho / EchoGreetingFromFile.  
  
    ```csharp  
    MetadataRetrievalNode outOpNode3 = new MetadataRetrievalNode("Echo/EchoCustomGreetingFromFile");  
    outOpNode3.DisplayName = "EchoCustomGreetingFromFile";  
    outOpNode3.Description = "This operation echoes the greeting object by reading its instance from a file. The Greeting object's metadata is obtained from a predefined XSD file.";  
    outOpNode3.Direction = MetadataRetrievalNodeDirections.Outbound;  
    outOpNode3.IsOperation = true;  
    ```  
  
8.  Continuez à ajouter le code suivant pour retourner un tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets ou null si ne pas de correspondance.  
  
    ```  
        return new MetadataRetrievalNode[] { inOpNode1, outOpNode1, outOpNode2, outOpNode3 };  
    }  
    return null;  
    ```  
  
9. Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
10. Dans le menu **Générer** , cliquez sur **Générer la solution**. Vous devez générer correctement le projet. Dans le cas contraire, vérifiez que vous avez suivi toutes les étapes ci-dessus.  
  
> [!NOTE]
>  Vous avez enregistré votre travail. Vous pouvez en toute sécurité fermer Visual Studio pour l’instant ou accédez à l’étape suivante, [étape 5 : implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md).  
  
## <a name="what-did-i-just-do"></a>Quoi simplement ?  
 Vous venez d’implémenter la navigation de capacité de la carte Echo, en mettant en œuvre dans les métadonnées du `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler.Browse%2A` méthode de la `Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler` interface. Plus précisément, vous avez créé un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` pour la catégorie d’objet et il retournées sous forme de tableau de la `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` objets. Pour chaque opération, vous avez créé un `Microsoft.ServiceModel.Channels.MetadataRetrievalNode` de l’objet et ensuite renvoyé tous ces objets dans un tableau de `Microsoft.ServiceModel.Channels.MetadataRetrievalNode`.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous implémentez la recherche de métadonnées et les fonctionnalités de résolution et l’échange de messages sortants. Enfin, vous générez et déployez l’adaptateur de l’écho.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 1 : Développer l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)   
 [Étape 3 : Implémenter la connexion de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md)   
 [Étape 5 : Implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md)
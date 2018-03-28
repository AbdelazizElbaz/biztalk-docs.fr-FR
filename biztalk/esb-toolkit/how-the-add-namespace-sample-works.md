---
title: Comment l’ajouter Namespace exemple fonctionne | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c76a90a9-5898-43b3-98af-ff546dd97153
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 212364030353001cae0589d4d7562641db4b77e6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-the-add-namespace-sample-works"></a><span data-ttu-id="fbca3-102">Comment l’ajouter Namespace exemple fonctionne</span><span class="sxs-lookup"><span data-stu-id="fbca3-102">How the Add Namespace Sample Works</span></span>
<span data-ttu-id="fbca3-103">Le premier, deuxième et quatrième tests utilisent le **ajouter le Namespace** composant se trouve dans le pipeline NamespaceSampleReceivePipeline.</span><span class="sxs-lookup"><span data-stu-id="fbca3-103">The first, second, and fourth tests use the **Add Namespace** component located in the NamespaceSampleReceivePipeline pipeline.</span></span> <span data-ttu-id="fbca3-104">Il prend comme entrée un document sans espace de noms sur le nœud racine, telle que la suivante :</span><span class="sxs-lookup"><span data-stu-id="fbca3-104">It takes as input a document with no namespace on the root node, such as the following:</span></span>  
  
```  
<CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1" Status="Status_2">  
```  
  
 <span data-ttu-id="fbca3-105">Le tableau suivant présente les valeurs de propriété définies pour le **ajouter le Namespace** composant.</span><span class="sxs-lookup"><span data-stu-id="fbca3-105">The following table shows the property values set for the **Add Namespace** component.</span></span>  
  
|<span data-ttu-id="fbca3-106">Propriété</span><span class="sxs-lookup"><span data-stu-id="fbca3-106">Property</span></span>|<span data-ttu-id="fbca3-107">Type</span><span class="sxs-lookup"><span data-stu-id="fbca3-107">Type</span></span>|<span data-ttu-id="fbca3-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="fbca3-108">Value</span></span>|  
|--------------|----------|-----------|  
|<span data-ttu-id="fbca3-109">ExtractionNodeXPath</span><span class="sxs-lookup"><span data-stu-id="fbca3-109">ExtractionNodeXPath</span></span>|<span data-ttu-id="fbca3-110">Statique</span><span class="sxs-lookup"><span data-stu-id="fbca3-110">Static</span></span>|<span data-ttu-id="fbca3-111">(vide)</span><span class="sxs-lookup"><span data-stu-id="fbca3-111">(empty)</span></span>|  
|<span data-ttu-id="fbca3-112">NamespaceBase</span><span class="sxs-lookup"><span data-stu-id="fbca3-112">NamespaceBase</span></span>|<span data-ttu-id="fbca3-113">Statique</span><span class="sxs-lookup"><span data-stu-id="fbca3-113">Static</span></span>|http://schemas.microsoft.biztalk.esb.test.com/test|  
|<span data-ttu-id="fbca3-114">NamespacePrefix</span><span class="sxs-lookup"><span data-stu-id="fbca3-114">NamespacePrefix</span></span>|<span data-ttu-id="fbca3-115">Statique</span><span class="sxs-lookup"><span data-stu-id="fbca3-115">Static</span></span>|<span data-ttu-id="fbca3-116">esbTest</span><span class="sxs-lookup"><span data-stu-id="fbca3-116">esbTest</span></span>|  
|<span data-ttu-id="fbca3-117">Séparateur</span><span class="sxs-lookup"><span data-stu-id="fbca3-117">Separator</span></span>|<span data-ttu-id="fbca3-118">Statique</span><span class="sxs-lookup"><span data-stu-id="fbca3-118">Static</span></span>|/|  
|<span data-ttu-id="fbca3-119">XPaths</span><span class="sxs-lookup"><span data-stu-id="fbca3-119">XPaths</span></span>|<span data-ttu-id="fbca3-120">Dynamique</span><span class="sxs-lookup"><span data-stu-id="fbca3-120">Dynamic</span></span>|<span data-ttu-id="fbca3-121">/CanonicalOrder/@OrderID&#124;/CanonicalOrder/@OrderDate</span><span class="sxs-lookup"><span data-stu-id="fbca3-121">/CanonicalOrder/@OrderID&#124;/CanonicalOrder/@OrderDate</span></span>|  
  
 <span data-ttu-id="fbca3-122">Les paramètres de propriété indiqués dans le tableau provoquent le composant à rechercher dans le document XML en exécutant les deux requêtes XPath /CanonicalOrder/@OrderID et /CanonicalOrder/@OrderDate (les deux requêtes spécifiés pour le **XPaths** propriété, séparée par un « canal » caractère).</span><span class="sxs-lookup"><span data-stu-id="fbca3-122">The property settings shown in the table cause the component to search the XML document by executing the two XPath queries /CanonicalOrder/@OrderID and /CanonicalOrder/@OrderDate (the two queries specified for the **XPaths** property, separated by a "pipe" character).</span></span> <span data-ttu-id="fbca3-123">Ces requêtes retournent les valeurs de la **OrderID** et **OrderDate** attributs du nœud racine du document ; dans cet exemple, les deux valeurs sont « OrderID_0 » et « OrderDate_1 ».</span><span class="sxs-lookup"><span data-stu-id="fbca3-123">These queries return the values of the **OrderID** and **OrderDate** attributes of the root node of the document; in this example, the two values are "OrderID_0" and "OrderDate_1".</span></span>  
  
 <span data-ttu-id="fbca3-124">Le composant utilise ensuite ces valeurs et les valeurs des autres propriétés, pour construire le nouvel espace de noms racine.</span><span class="sxs-lookup"><span data-stu-id="fbca3-124">The component then uses these values, and the values of the other properties, to construct the new root namespace.</span></span> <span data-ttu-id="fbca3-125">Il combine les **NamespaceBase**, le **NamespacePrefix**, le **séparateur**et les valeurs à partir des deux requêtes XPath dans le format suivant :</span><span class="sxs-lookup"><span data-stu-id="fbca3-125">It combines the **NamespaceBase**, the **NamespacePrefix**, the **Separator**, and the values from the two XPath queries in the following format:</span></span>  
  
```  
xmlns:{NamespacePrefix}="{NamespaceBase}{Separator}{XPaths[1]}{Seperator}  
                         {XPaths[2]}{Separator}...{XPaths[n]}"  
```  
  
 <span data-ttu-id="fbca3-126">Ce code produit le nouvel espace de noms, comme illustré ici :</span><span class="sxs-lookup"><span data-stu-id="fbca3-126">This produces the new namespace, as shown here:</span></span>  
  
```  
xmlns:esbTest="http://schemas.microsoft.biztalk.esb.test.com/test  
               /OrderID_0/OrderDate_1"  
```  
  
 <span data-ttu-id="fbca3-127">Par conséquent, le document mis à jour après le traitement par le **NamespaceSampleReceivePipeline** pipeline est le suivant :</span><span class="sxs-lookup"><span data-stu-id="fbca3-127">Therefore, the updated document after processing by the **NamespaceSampleReceivePipeline** pipeline is the following:</span></span>  
  
```  
<esbTest:CanonicalOrder xmlns:esbTest=  
    "http://schemas.microsoft.biztalk.esb.test.com/test/OrderID_0  
    /OrderDate_1" OrderID="OrderID_0" OrderDate="OrderDate_1"   
    Status="Status_2">  
```  
  
## <a name="using-the-extractionnodexpath-property"></a><span data-ttu-id="fbca3-128">À l’aide de la propriété ExtractionNodeXPath</span><span class="sxs-lookup"><span data-stu-id="fbca3-128">Using the ExtractionNodeXPath Property</span></span>  
 <span data-ttu-id="fbca3-129">Par défaut, le **ajouter le Namespace** composant utilise l’élément racine du document XML dans le message lors de l’ajout des informations d’espace de noms et préfixe.</span><span class="sxs-lookup"><span data-stu-id="fbca3-129">By default, the **Add Namespace** component uses the root element of the XML document within the message when adding namespace and prefix information.</span></span> <span data-ttu-id="fbca3-130">Si vous souhaitez utiliser uniquement un sous-ensemble du document XML en tant que corps du message (utile dans certains scénarios d’enveloppe, ou lorsque seule une partie d’un document entrant comporte pertinence), vous pouvez définir le **ExtractionNodeXPath** propriété pour forcer la  **Ajouter Namespace** composant à l’élément spécifié pour une utilisation en tant que le message résultant de la recherche.</span><span class="sxs-lookup"><span data-stu-id="fbca3-130">If you want to use only a subset of the XML document as the message body (useful in certain envelope scenarios or when only a portion of an inbound document has relevance), you can set the **ExtractionNodeXPath** property to force the **Add Namespace** component to seek the specified element for use as the resultant message.</span></span> <span data-ttu-id="fbca3-131">Par exemple, si vous savez qu’un message CanonicalOrder reçu possède uniquement un **OrderDetails** élément approprié pour les consommateurs de ce message qu’il contient, vous pouvez définir le **ExtractionNodeXPath** propriété pour spécifier le chemin d’accès à la **OrderDetails** élément.</span><span class="sxs-lookup"><span data-stu-id="fbca3-131">For example, if you know that a received CanonicalOrder message will have only one **OrderDetails** element that is relevant for consumers of this message contained within it, you can set the **ExtractionNodeXPath** property to specify the path to the **OrderDetails** element.</span></span> <span data-ttu-id="fbca3-132">Vous pouvez voir un exemple de ce processus à ajouter Via Extraction au test pass-through décrit précédemment.</span><span class="sxs-lookup"><span data-stu-id="fbca3-132">You can see an example of this process in the Add Via Extraction to Pass-through test described earlier.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbca3-133">Le **ExtractionNodeXPath** propriété doit être un XPath qui retourne un seul élément.</span><span class="sxs-lookup"><span data-stu-id="fbca3-133">The **ExtractionNodeXPath** property must be an XPath that returns only one element.</span></span> <span data-ttu-id="fbca3-134">Le composant lève une exception si le résultat n’est pas un élément ou si la requête XPath retourne plus d’un élément.</span><span class="sxs-lookup"><span data-stu-id="fbca3-134">The component will raise an exception if the result is not an element or if the XPath query returns more than one element.</span></span>
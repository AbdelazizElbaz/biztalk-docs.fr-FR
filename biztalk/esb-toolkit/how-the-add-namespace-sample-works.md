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
# <a name="how-the-add-namespace-sample-works"></a>Comment l’ajouter Namespace exemple fonctionne
Le premier, deuxième et quatrième tests utilisent le **ajouter le Namespace** composant se trouve dans le pipeline NamespaceSampleReceivePipeline. Il prend comme entrée un document sans espace de noms sur le nœud racine, telle que la suivante :  
  
```  
<CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1" Status="Status_2">  
```  
  
 Le tableau suivant présente les valeurs de propriété définies pour le **ajouter le Namespace** composant.  
  
|Propriété|Type|Valeur|  
|--------------|----------|-----------|  
|ExtractionNodeXPath|Statique|(vide)|  
|NamespaceBase|Statique|http://schemas.microsoft.biztalk.esb.test.com/test|  
|NamespacePrefix|Statique|esbTest|  
|Séparateur|Statique|/|  
|XPaths|Dynamique|/CanonicalOrder/@OrderID&#124;/CanonicalOrder/@OrderDate|  
  
 Les paramètres de propriété indiqués dans le tableau provoquent le composant à rechercher dans le document XML en exécutant les deux requêtes XPath /CanonicalOrder/@OrderID et /CanonicalOrder/@OrderDate (les deux requêtes spécifiés pour le **XPaths** propriété, séparée par un « canal » caractère). Ces requêtes retournent les valeurs de la **OrderID** et **OrderDate** attributs du nœud racine du document ; dans cet exemple, les deux valeurs sont « OrderID_0 » et « OrderDate_1 ».  
  
 Le composant utilise ensuite ces valeurs et les valeurs des autres propriétés, pour construire le nouvel espace de noms racine. Il combine les **NamespaceBase**, le **NamespacePrefix**, le **séparateur**et les valeurs à partir des deux requêtes XPath dans le format suivant :  
  
```  
xmlns:{NamespacePrefix}="{NamespaceBase}{Separator}{XPaths[1]}{Seperator}  
                         {XPaths[2]}{Separator}...{XPaths[n]}"  
```  
  
 Ce code produit le nouvel espace de noms, comme illustré ici :  
  
```  
xmlns:esbTest="http://schemas.microsoft.biztalk.esb.test.com/test  
               /OrderID_0/OrderDate_1"  
```  
  
 Par conséquent, le document mis à jour après le traitement par le **NamespaceSampleReceivePipeline** pipeline est le suivant :  
  
```  
<esbTest:CanonicalOrder xmlns:esbTest=  
    "http://schemas.microsoft.biztalk.esb.test.com/test/OrderID_0  
    /OrderDate_1" OrderID="OrderID_0" OrderDate="OrderDate_1"   
    Status="Status_2">  
```  
  
## <a name="using-the-extractionnodexpath-property"></a>À l’aide de la propriété ExtractionNodeXPath  
 Par défaut, le **ajouter le Namespace** composant utilise l’élément racine du document XML dans le message lors de l’ajout des informations d’espace de noms et préfixe. Si vous souhaitez utiliser uniquement un sous-ensemble du document XML en tant que corps du message (utile dans certains scénarios d’enveloppe, ou lorsque seule une partie d’un document entrant comporte pertinence), vous pouvez définir le **ExtractionNodeXPath** propriété pour forcer la  **Ajouter Namespace** composant à l’élément spécifié pour une utilisation en tant que le message résultant de la recherche. Par exemple, si vous savez qu’un message CanonicalOrder reçu possède uniquement un **OrderDetails** élément approprié pour les consommateurs de ce message qu’il contient, vous pouvez définir le **ExtractionNodeXPath** propriété pour spécifier le chemin d’accès à la **OrderDetails** élément. Vous pouvez voir un exemple de ce processus à ajouter Via Extraction au test pass-through décrit précédemment.  
  
> [!NOTE]
>  Le **ExtractionNodeXPath** propriété doit être un XPath qui retourne un seul élément. Le composant lève une exception si le résultat n’est pas un élément ou si la requête XPath retourne plus d’un élément.
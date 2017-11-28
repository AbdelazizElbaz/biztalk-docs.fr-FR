---
title: "Ajout avancé de fonctoids à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbec5e9c-65b3-4734-a7fc-4ee66cf26eee
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fad75ed2c5c6779801e38f0c4b8f4505696bb476
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-advanced-functoids-to-a-map"></a><span data-ttu-id="5ec4d-102">Ajout de fonctoids avancés à un mappage</span><span class="sxs-lookup"><span data-stu-id="5ec4d-102">Adding Advanced Functoids to a Map</span></span>
<span data-ttu-id="5ec4d-103">Fonctoids dans le **avancé** catégorie sont plus complexes à comprendre et à utiliser que les fonctoids dans les autres catégories, ensemble classés de fonctoids de base.</span><span class="sxs-lookup"><span data-stu-id="5ec4d-103">Functoids in the **Advanced** category are more complex to understand and use than the functoids in the other categories, together classified as basic functoids.</span></span> <span data-ttu-id="5ec4d-104">Vous utilisez les fonctoids avancés quand vous avez besoin de mappages plus complexes.</span><span class="sxs-lookup"><span data-stu-id="5ec4d-104">You use advanced functoids when you need more complex maps.</span></span> <span data-ttu-id="5ec4d-105">Ces mappages devront peut-être comptabiliser des enregistrements, boucler au sein d'enregistrements avec un nombre variable de sous-enregistrements ou exécuter un script arbitrairement complexe.</span><span class="sxs-lookup"><span data-stu-id="5ec4d-105">These maps might need to count records, loop through records with a variable number of subrecords, or run an arbitrarily complex script.</span></span>  
  
 <span data-ttu-id="5ec4d-106">Cette section fournit des instructions détaillées pour l’ajout de fonctoids dans le **avancé** catégorie à vos mappages, y compris les définir correctement leurs paramètres d’entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="5ec4d-106">This section provides step-by-step instructions for adding functoids in the **Advanced** category to your maps, including correctly setting their input and output parameters.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ec4d-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5ec4d-107">In This Section</span></span>  
  
-   [<span data-ttu-id="5ec4d-108">Comment ajouter des fonctoids à une carte de bouclage</span><span class="sxs-lookup"><span data-stu-id="5ec4d-108">How to Add Looping Functoids to a Map</span></span>](../core/how-to-add-looping-functoids-to-a-map.md)  
  
-   [<span data-ttu-id="5ec4d-109">Comment ajouter le mappage de fonctoids (mise à plat) à une carte</span><span class="sxs-lookup"><span data-stu-id="5ec4d-109">How to Add Value Mapping (Flattening) Functoids to a Map</span></span>](../core/how-to-add-value-mapping-flattening-functoids-to-a-map.md)  
  
-   [<span data-ttu-id="5ec4d-110">Comment ajouter des fonctoids déclarer à un mappage</span><span class="sxs-lookup"><span data-stu-id="5ec4d-110">How to Add Assert Functoids to a Map</span></span>](../core/how-to-add-assert-functoids-to-a-map.md)  
  
-   [<span data-ttu-id="5ec4d-111">L’ajout de bouclage de Table et fonctoids Extracteur de Table à une carte</span><span class="sxs-lookup"><span data-stu-id="5ec4d-111">How to Add Table Looping and Table Extractor Functoids to a Map</span></span>](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)  
  
-   [<span data-ttu-id="5ec4d-112">Comment ajouter des fonctoids de script à une carte</span><span class="sxs-lookup"><span data-stu-id="5ec4d-112">How to Add Scripting Functoids to a Map</span></span>](../core/how-to-add-scripting-functoids-to-a-map.md)  
  
-   [<span data-ttu-id="5ec4d-113">Ajout de fonctoids valeur Nil à un mappage</span><span class="sxs-lookup"><span data-stu-id="5ec4d-113">How to Add Nil Value Functoids to a Map</span></span>](../core/how-to-add-nil-value-functoids-to-a-map.md)  
  
-   [<span data-ttu-id="5ec4d-114">Comment ajouter des fonctoids de mappage à un mappage de valeur</span><span class="sxs-lookup"><span data-stu-id="5ec4d-114">How to Add Value Mapping Functoids to a Map</span></span>](../core/how-to-add-value-mapping-functoids-to-a-map.md)  
  
-   [<span data-ttu-id="5ec4d-115">Ajout de fonctoids copie de masse à une carte</span><span class="sxs-lookup"><span data-stu-id="5ec4d-115">How to Add Mass Copy Functoids to a Map</span></span>](../core/how-to-add-mass-copy-functoids-to-a-map.md)  
  
-   [<span data-ttu-id="5ec4d-116">Ajout de fonctoids itération à un mappage</span><span class="sxs-lookup"><span data-stu-id="5ec4d-116">How to Add Iteration Functoids to a Map</span></span>](../core/how-to-add-iteration-functoids-to-a-map.md)  
  
-   [<span data-ttu-id="5ec4d-117">Ajout de fonctoids Index à une carte</span><span class="sxs-lookup"><span data-stu-id="5ec4d-117">How to Add Index Functoids to a Map</span></span>](../core/how-to-add-index-functoids-to-a-map.md)  
  
-   [<span data-ttu-id="5ec4d-118">Ajout de fonctoids nombre d’enregistrements à une carte</span><span class="sxs-lookup"><span data-stu-id="5ec4d-118">How to Add Record Count Functoids to a Map</span></span>](../core/how-to-add-record-count-functoids-to-a-map.md)
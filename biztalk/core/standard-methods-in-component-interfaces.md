---
title: "Méthodes standard dans les Interfaces de composant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- component interfaces, standard methods
- methods, viewing
- methods, component interfaces
- methods, changing
ms.assetid: 2273d946-3fc8-4b2d-a6a1-9e4f0da74d5b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f44b3977a3921d92b1f3f83dd3e744f14b5709fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="standard-methods-in-component-interfaces"></a><span data-ttu-id="510c4-102">Méthodes standard dans les Interfaces de composant</span><span class="sxs-lookup"><span data-stu-id="510c4-102">Standard Methods in Component Interfaces</span></span>
<span data-ttu-id="510c4-103">Les méthodes standard pour l'interface de composant sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="510c4-103">The standard methods for the component interface are as follows:</span></span>  
  
-   `Create`  
  
-   `Find`  
  
-   `Get`  
  
-   `Save`  
  
 <span data-ttu-id="510c4-104">Seules les méthodes du composant sous-jacent sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="510c4-104">Only those methods in the underlying component are available.</span></span> <span data-ttu-id="510c4-105">Par exemple, si le composant sous-jacent ne contient pas de fonctionnalités `Add`, `Create` n'est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="510c4-105">For example, if the underlying component does not contain `Add` capabilities, `Create` is unavailable.</span></span>  
  
## <a name="viewing-or-changing-available-methods"></a><span data-ttu-id="510c4-106">Affichage et modification des méthodes disponibles</span><span class="sxs-lookup"><span data-stu-id="510c4-106">Viewing or Changing Available Methods</span></span>  
  
#### <a name="to-view-or-change-available-methods"></a><span data-ttu-id="510c4-107">Pour afficher et modifier les méthodes disponibles</span><span class="sxs-lookup"><span data-stu-id="510c4-107">To view or change available methods</span></span>  
  
1.  <span data-ttu-id="510c4-108">Ouvrez l’interface de composant **propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="510c4-108">Open the component interface **Properties** dialog box.</span></span>  
  
     ![](../core/media/psadapter-46-ps-properties.gif "PSAdapter_46_PS_Properties")  
  
2.  <span data-ttu-id="510c4-109">Cliquez sur le **méthodes Standard** onglet.</span><span class="sxs-lookup"><span data-stu-id="510c4-109">Click the **Standard Methods** tab.</span></span>  
  
3.  <span data-ttu-id="510c4-110">Sélectionnez les méthodes souhaitées, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="510c4-110">Select the desired methods, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="510c4-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="510c4-111">See Also</span></span>  
 <span data-ttu-id="510c4-112">[Comment créer des Interfaces de composant](../core/how-to-create-component-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="510c4-112">[How to Create Component Interfaces](../core/how-to-create-component-interfaces.md) </span></span>  
 [<span data-ttu-id="510c4-113">Annexe c : à l’aide des Interfaces de composant</span><span class="sxs-lookup"><span data-stu-id="510c4-113">Appendix C: Using Component Interfaces</span></span>](../core/appendix-c-using-component-interfaces.md)
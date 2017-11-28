---
title: Filtre | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8dad59d-4a47-4794-bbf9-cba02fe7f0bf
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efa69998b1782f42d7730744fd88534d26a87835
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="filter"></a><span data-ttu-id="6105a-102">Filtrer</span><span class="sxs-lookup"><span data-stu-id="6105a-102">Filter</span></span>
<span data-ttu-id="6105a-103">L'élément `Filter` contient une `Expression` qui donne le résultat `true` ou `false`, déterminant ainsi si un événement doit être traité ou ignoré.</span><span class="sxs-lookup"><span data-stu-id="6105a-103">The `Filter` element contains an `Expression` that evaluates to `true` or `false` and determines when an event should be processed or skipped.</span></span>  
  
## <a name="format"></a><span data-ttu-id="6105a-104">Format</span><span class="sxs-lookup"><span data-stu-id="6105a-104">Format</span></span>  
  
```  
<ic:Filter>  
</ic:Filter>  
```  
  
## <a name="remarks"></a><span data-ttu-id="6105a-105">Notes</span><span class="sxs-lookup"><span data-stu-id="6105a-105">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="6105a-106"> Exemple</span><span class="sxs-lookup"><span data-stu-id="6105a-106">Example</span></span>  
 <span data-ttu-id="6105a-107">L'exemple suivant définit un filtre qui donne le résultat `true` lorsque la clé utilisateur pour le workflow associé à l'événement est égale à « DocumentUrl » :</span><span class="sxs-lookup"><span data-stu-id="6105a-107">The following example defines a filter that evaluates to `true` when the user key for the workflow associated with the event equals "DocumentUrl":</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>DocumentUrl</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6105a-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6105a-108">See Also</span></span>  
 [<span data-ttu-id="6105a-109">Élément OnEvent de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="6105a-109">Interceptor OnEvent Element</span></span>](../core/interceptor-onevent-element.md)
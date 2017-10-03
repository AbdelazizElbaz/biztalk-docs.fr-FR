---
title: "Élément BamActivity de l’intercepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dee61b4-83cd-4a22-b8a6-1c1a7ea3648b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd43869922e46187c8b2e06155d525e428edd905
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interceptor-bamactivity-element"></a>Élément BamActivity de l'intercepteur
Le **BamActivity** élément définit une activité BAM unique.  
  
## <a name="format"></a>Format  
 Le `BamActivity` élément inclut un **nom** d’attribut et contient un ou plusieurs `OnEvent` éléments.  
  
```  
<ic:BamActivity Name="PurchaseOrder">  
  <!-- One or more OnEvent elements -->  
</ic:BamActivity>   
```  
  
### <a name="attributes"></a>Attributs  
  
|Nom de l'attribut| Description|  
|--------------------|-----------------|  
|Nom|Nom de l'activité BAM défini par l'utilisateur.|  
  
## <a name="example"></a>Exemple  
 Le code suivant contient un exemple de BamActivity pour « MyOrderWorkflow » avec un OnEvent unique.  
  
```  
<ic:BamActivity Name="MyOrderWorkflow">  
  <ic:OnEvent Name="MyActivityEvent"  Source="OrderWorkflow">  
    …  
  </ic:OnEvent>  
</ic:BamActivity>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Élément EventSource de l’intercepteur](../core/interceptor-eventsource-element.md)   
 [Élément OnEvent de l’intercepteur](../core/interceptor-onevent-element.md)
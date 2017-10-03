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
# <a name="filter"></a>Filtrer
L'élément `Filter` contient une `Expression` qui donne le résultat `true` ou `false`, déterminant ainsi si un événement doit être traité ou ignoré.  
  
## <a name="format"></a>Format  
  
```  
<ic:Filter>  
</ic:Filter>  
```  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a> Exemple  
 L'exemple suivant définit un filtre qui donne le résultat `true` lorsque la clé utilisateur pour le workflow associé à l'événement est égale à « DocumentUrl » :  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Élément OnEvent de l’intercepteur](../core/interceptor-onevent-element.md)
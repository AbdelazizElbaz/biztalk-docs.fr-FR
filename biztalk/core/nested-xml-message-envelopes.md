---
title: "Imbriqué enveloppes de Message XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e880cef1-4e73-4bce-a06e-8c4d23bc5a8c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46b0f505dd9ba7da71df1cb460f9c9a6610763d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="nested-xml-message-envelopes"></a>Enveloppes de message XML imbriquées
Les enveloppes XML peuvent être imbriquées pour créer des structures de document complexes. Les enveloppes XML imbriquées existent sous deux formes, appelées flexible et canonique. L'exemple suivant montre la forme flexible de documents enveloppés, dans laquelle les documents et les enveloppes (en gras) peuvent apparaître au même niveau dans une enveloppe associée.  
  
```  
<envelope1>  
    <document1/>    <envelope2>  
        <document2/>  
        <document3/>  
    </envelope2>    <document4/>  
</envelope1>  
```  
  
 L'exemple suivant montre un message d'instance similaire appartenant à la forme canonique des documents enveloppés, dans laquelle tous les documents apparaissent au même niveau dans l'enveloppe la plus profonde.  
  
```  
<envelope1>  
    <envelope2>  
        <document1/>  
        <document2/>  
        <document3/>  
        <document4/>  
    </envelope2>  
</envelope1>  
  
```  
  
 Pour un message d'instance prenant l'une ou l'autre des formes décrites, le désassembleur XML génèrera  document1, document2, document3 et document4. Le contexte de message de chacun de ces documents inclut les propriétés promues à partir du document correspondant ainsi que celles promues dans chacune des enveloppes associées. Le tableau suivant montre les propriétés promues qui seront incluses dans le contexte de message de chaque document non encapsulé pour l'exemple de la forme et celui de la forme canonique, d'après les promotions de propriété spécifiées dans la première colonne pour les divers documents et enveloppes.  
  
|Promotions de propriétés spécifiées|Propriétés de contexte de message résultantes pour l'exemple « flexible »|Propriétés de contexte de message résultantes pour l'exemple « canonique »|  
|-----------------------------------|---------------------------------------------------------------|----------------------------------------------------------------|  
|envelope1 : p1<br /><br /> envelope2 : p3<br /><br /> Document1 : p2<br /><br /> Document2 : p4 et p5<br /><br /> document3 : aucune promotion<br /><br /> document4 : aucune promotion|Document1 : p1, p2<br /><br /> Document2 : p1, p3, p4, p5<br /><br /> document3 : p1, p3<br /><br /> document4 : p1|Document1 : p1, p2, p3<br /><br /> Document2 : p1, p3, p4, p5<br /><br /> document3 : p1, p3<br /><br /> document4 : p1, p3|  
  
## <a name="see-also"></a>Voir aussi  
 [Enveloppes de Message XML](../core/xml-message-envelopes.md)   
 [Structure d’un Message XML](../core/structure-of-an-xml-message.md)   
 [Comment créer des schémas pour les enveloppes](../core/how-to-create-schemas-for-envelopes.md)
---
title: Enveloppes de Message XML | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d01cd85d-7bf7-49fa-aa25-322213bce066
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3adb33866a3e6fdaee387934d2edededaab08aac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-message-envelopes"></a>Enveloppes de message XML
Dans les messages d'instance XML envoyés et reçus par Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les enveloppes XML ont deux fonctions :  
  
-   Elles peuvent contenir des données qui complètent les données dans les documents XML. Ces données peuvent être promues dans le contexte de message par le désassembleur XML afin de fournir un accès plus aisé à partir de nombreux composants de BizTalk Server. Pour les messages d'instance XML sortants, l'assembleur XML peut rétrograder des valeurs du contexte de message dans une enveloppe afin de les inclure dans la transmission de message d'instance.  
  
-   Elles peuvent être utilisées pour combiner plusieurs documents XML en un seul message d'instance XML valide. Sans la présence d'une enveloppe intégrant plusieurs documents dans une balise racine unique, un message d'instance XML                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           contenant plusieurs documents ne pourrait pas être considéré comme un XML bien formé.  
  
 Une enveloppe XML classique (affichée en gras) contient des données et une balise utilisée pour délimiter le ou les documents XML (affichés en police normale) qu'elle contient.  
  
```  
  
  <envelope fieldAttrib1="..." fieldAttrib2="..." ...>     <fieldElem1>...</fieldElem1>     <fieldElem2>...</fieldElem2>     ...     <body>  
    <document1>  
        ...  
    </document1>  
    <document2>  
        ...  
    </document2>  
    ...  
</body>    ...</envelope>  
```  
  
 Plus rares mais toujours valides, certaines enveloppes XML (affichées en gras) ne doivent pas nécessairement contenir des données ou une balise pour délimiter les documents XML (affichés en police normale) qu'elles contiennent.  
  
```  
  
      <envelope>  
    <document1>  
        ...  
    </document1>  
    <document2>  
        ...  
    </document2>  
    ...  
</envelope>  
```  
  
 En pareil cas, ces enveloppes XML ne se composent pas d'autre chose que des balises de début et de fin d'enveloppe.  
  
## <a name="see-also"></a>Voir aussi  
 [Enveloppes de Message XML imbriquées](../core/nested-xml-message-envelopes.md)   
 [Structure d’un Message XML](../core/structure-of-an-xml-message.md)   
 [Comment créer des schémas pour les enveloppes](../core/how-to-create-schemas-for-envelopes.md)
---
title: "Structure d’un Message XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a5bba81-2f2b-41f3-b8b2-c2fb9c15ea5a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f35e48e90ffb089342c268b7b6a45069e2f9869
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="structure-of-an-xml-message"></a>Structure d'un message XML
Dans le contexte de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], un message d'instance XML est une hiérarchie valide de balises XML constituant ensemble zéro, une ou plusieurs enveloppes XML et un ou plusieurs documents XML. Par exemple, le message d'instance XML suivant est composé d'une enveloppe XML unique (en police normale) qui contient un document XML unique (en caractères gras).  
  
```  
<ns0:envelope xmlns:ns0="http://myEnvelopeNamespaceURI.org">  
    <header>  
        <firstName>John</firstName>  
        <lastName>Scott</lastName>  
    </header>  
    <body>  
        <ns1:document xmlns:ns1="http://myDocumentNamespaceURI.org">            <message>Hello</message>        </ns1:document>  
    </body>  
</ns0:envelope>  
```  
  
 Les enveloppes XML et les documents XML qu'elles contiennent peuvent être combinés dans des messages d'instance XML de plusieurs façons. Le reste de cette section décrit les différentes combinaisons existantes.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Enveloppes de Message XML](../core/xml-message-envelopes.md)  
  
-   [Enveloppes de Message XML imbriquées](../core/nested-xml-message-envelopes.md)
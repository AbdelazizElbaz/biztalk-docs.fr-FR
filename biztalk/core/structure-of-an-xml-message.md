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
# <a name="structure-of-an-xml-message"></a><span data-ttu-id="7a899-102">Structure d'un message XML</span><span class="sxs-lookup"><span data-stu-id="7a899-102">Structure of an XML Message</span></span>
<span data-ttu-id="7a899-103">Dans le contexte de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], un message d'instance XML est une hiérarchie valide de balises XML constituant ensemble zéro, une ou plusieurs enveloppes XML et un ou plusieurs documents XML.</span><span class="sxs-lookup"><span data-stu-id="7a899-103">In the context of Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], an XML instance message is a valid hierarchy of XML tags that together constitute zero or more XML envelopes and one or more XML documents.</span></span> <span data-ttu-id="7a899-104">Par exemple, le message d'instance XML suivant est composé d'une enveloppe XML unique (en police normale) qui contient un document XML unique (en caractères gras).</span><span class="sxs-lookup"><span data-stu-id="7a899-104">For example, the following XML instance message consists of a single XML envelope (in regular font) that contains a single XML document (shown in bold type).</span></span>  
  
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
  
 <span data-ttu-id="7a899-105">Les enveloppes XML et les documents XML qu'elles contiennent peuvent être combinés dans des messages d'instance XML de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="7a899-105">XML envelopes and the XML documents that they contain can be combined into valid XML instance messages in several different ways.</span></span> <span data-ttu-id="7a899-106">Le reste de cette section décrit les différentes combinaisons existantes.</span><span class="sxs-lookup"><span data-stu-id="7a899-106">The remainder of this section describes these different combinations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7a899-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7a899-107">In This Section</span></span>  
  
-   [<span data-ttu-id="7a899-108">Enveloppes de Message XML</span><span class="sxs-lookup"><span data-stu-id="7a899-108">XML Message Envelopes</span></span>](../core/xml-message-envelopes.md)  
  
-   [<span data-ttu-id="7a899-109">Enveloppes de Message XML imbriquées</span><span class="sxs-lookup"><span data-stu-id="7a899-109">Nested XML Message Envelopes</span></span>](../core/nested-xml-message-envelopes.md)
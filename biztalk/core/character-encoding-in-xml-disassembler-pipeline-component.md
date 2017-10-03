---
title: "Encodage de caractères dans le composant de Pipeline désassembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IBaseMessagePart.Charset property
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component], character encoding
- XMLNorm.SourceCharset property
ms.assetid: 37962bdc-cbcb-4559-9ae8-6c4be49b4822
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b0e307f2f608cde266e7a566fb3005bde048c31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="character-encoding-in-xml-disassembler-pipeline-component"></a><span data-ttu-id="9b0be-102">Encodage de caractères dans le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="9b0be-102">Character Encoding in XML Disassembler Pipeline Component</span></span>
<span data-ttu-id="9b0be-103">Le Désassembleur XML utilise l’algorithme suivant pour déterminer le codage à utiliser pour traiter les messages entrants :</span><span class="sxs-lookup"><span data-stu-id="9b0be-103">The XML Disassembler uses the following algorithm to determine which encoding to use for processing incoming messages:</span></span>  
  
1.  <span data-ttu-id="9b0be-104">S’il existe une marque d’ordre de tri dans les données, elle détermine les informations de codage.</span><span class="sxs-lookup"><span data-stu-id="9b0be-104">If a byte order mark exists in the data, encoding information is determined from it.</span></span>  
  
2.  <span data-ttu-id="9b0be-105">Sinon, si le **IBaseMessagePart.Charset** propriété est définie, le codage spécifié ici est utilisé.</span><span class="sxs-lookup"><span data-stu-id="9b0be-105">Otherwise, if the **IBaseMessagePart.Charset** property is set, the encoding specified there is used.</span></span>  
  
3.  <span data-ttu-id="9b0be-106">Ou encore, si la déclaration XML est présente dans le document XML, le codage spécifié ici est utilisé, pourvu que la déclaration XML soit de type ANSI.</span><span class="sxs-lookup"><span data-stu-id="9b0be-106">Otherwise if the XML declaration is present in the XML document, the encoding specified there is used, provided the XML declaration is ANSI.</span></span>  
  
4.  <span data-ttu-id="9b0be-107">Autrement, le codage UTF-8 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="9b0be-107">Otherwise, UTF-8 encoding is used.</span></span>  
  
 <span data-ttu-id="9b0be-108">Pour les cas précédents 2, 3 et 4, après le désassembleur XML détermine le codage, il l’enregistre dans le contexte du message dans **XMLNorm.SourceCharset** propriété.</span><span class="sxs-lookup"><span data-stu-id="9b0be-108">For the preceding cases 2, 3, and 4, after the XML Disassembler determines the encoding, it saves it on the message context in **XMLNorm.SourceCharset** property.</span></span> <span data-ttu-id="9b0be-109">Les messages produits par le composant de pipeline Désassembleur XML utilisent toujours le codage UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9b0be-109">Messages produced by the XML Disassembler pipeline component always use UTF-8 encoding.</span></span> <span data-ttu-id="9b0be-110">Pour le cas 1, le codage déterminé par la marque d'ordre de tri n'est pas conservé.</span><span class="sxs-lookup"><span data-stu-id="9b0be-110">For case 1, encoding determined from the byte order mark is not preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b0be-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b0be-111">See Also</span></span>  
 <span data-ttu-id="9b0be-112">[Composant de Pipeline désassembleur XML](../core/xml-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="9b0be-112">[XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="9b0be-113">Comment configurer le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="9b0be-113">How to Configure the XML Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)
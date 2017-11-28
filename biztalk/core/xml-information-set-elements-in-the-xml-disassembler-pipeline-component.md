---
title: "Éléments ensemble d’informations XML dans le composant de Pipeline désassembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Disassembler [pipeline component], information set
- XML Disassembler [pipeline component], processing instructions
- pipeline components, XML Disassembler
ms.assetid: cc82344c-6c4b-4154-a662-0b7ae5caad30
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90b3140cbe23637160aafabdccb37104efd1d318
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-information-set-elements-in-the-xml-disassembler-pipeline-component"></a><span data-ttu-id="190b1-102">Éléments ensemble d’informations XML dans le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="190b1-102">XML Information Set Elements in the XML Disassembler Pipeline Component</span></span>
<span data-ttu-id="190b1-103">Le composant Désassembleur XML gère les éléments d'ensemble d'informations XML comme suit :</span><span class="sxs-lookup"><span data-stu-id="190b1-103">The XML Disassembler handles XML information set elements as follows.</span></span>  
  
|<span data-ttu-id="190b1-104">Élément</span><span class="sxs-lookup"><span data-stu-id="190b1-104">Element</span></span>|<span data-ttu-id="190b1-105"> Description</span><span class="sxs-lookup"><span data-stu-id="190b1-105">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="190b1-106">comment</span><span class="sxs-lookup"><span data-stu-id="190b1-106">comment</span></span>|<span data-ttu-id="190b1-107">Les commentaires sont conservés dans le document ; ceux contenus dans des enveloppes XML sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="190b1-107">Comments are preserved in the document; however, any comments in XML envelopes are not preserved.</span></span>|  
|<span data-ttu-id="190b1-108">CDATA</span><span class="sxs-lookup"><span data-stu-id="190b1-108">CDATA</span></span>|<span data-ttu-id="190b1-109">Les éléments CDATA sont conservés dans le document.</span><span class="sxs-lookup"><span data-stu-id="190b1-109">CDATA is preserved in the document.</span></span> <span data-ttu-id="190b1-110">Les éléments CDATA apparaissant en dehors d'un document (dans une enveloppe par exemple) sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="190b1-110">CDATA elements appearing outside of a document (for example, in an envelope) are not preserved.</span></span>|  
|<span data-ttu-id="190b1-111">instructions de traitement</span><span class="sxs-lookup"><span data-stu-id="190b1-111">processing instructions</span></span>|<span data-ttu-id="190b1-112">Le Désassembleur XML conserve les instructions de traitement figurant dans ou avant un document XML.</span><span class="sxs-lookup"><span data-stu-id="190b1-112">The XML Disassembler preserves processing instructions appearing in or before an XML document.</span></span> <span data-ttu-id="190b1-113">Les instructions de traitement figurant après un document XML, avant ou après une enveloppe ne sont pas conservées.</span><span class="sxs-lookup"><span data-stu-id="190b1-113">Processing instructions appearing after an XML document or before or after an envelope are not preserved.</span></span>|  
|<span data-ttu-id="190b1-114">déclaration XML</span><span class="sxs-lookup"><span data-stu-id="190b1-114">XML declaration</span></span>|<span data-ttu-id="190b1-115">L'élément déclaration XML de tout message XML entrant est supprimé.</span><span class="sxs-lookup"><span data-stu-id="190b1-115">The XML declaration element of any incoming XML message is removed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="190b1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="190b1-116">See Also</span></span>  
 <span data-ttu-id="190b1-117">[Composant de Pipeline désassembleur XML](../core/xml-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="190b1-117">[XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="190b1-118">Comment configurer le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="190b1-118">How to Configure the XML Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)
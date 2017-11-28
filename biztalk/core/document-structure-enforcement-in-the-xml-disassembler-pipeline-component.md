---
title: "Application de la Structure dans le composant de Pipeline désassembleur XML de document | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Disassembler [pipeline component], document structure
- pipeline components, XML Disassembler
ms.assetid: ac405bf2-f92b-4b45-8256-dd188ec9510a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e14b20292b23a0f50362940e3b873fa37a3f5bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="document-structure-enforcement-in-the-xml-disassembler-pipeline-component"></a><span data-ttu-id="c8780-102">Mise en œuvre de Structure de document dans le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="c8780-102">Document Structure Enforcement in the XML Disassembler Pipeline Component</span></span>
<span data-ttu-id="c8780-103">Si un schéma de document ou d’enveloppe est référencé explicitement dans le Désassembleur XML, ce dernier ne traite que les documents dont les types de messages se conforment au schéma.</span><span class="sxs-lookup"><span data-stu-id="c8780-103">If a document or envelope schema is explicitly referenced in the XML Disassembler, the XML Disassembler processes only those documents with message types conforming to the schema.</span></span> <span data-ttu-id="c8780-104">Aucun autre document n’est traité, même si un schéma déployé est référencé pour lui.</span><span class="sxs-lookup"><span data-stu-id="c8780-104">No other documents are processed, regardless of whether a deployed schema is referenced for them.</span></span>  
  
 <span data-ttu-id="c8780-105">Le Désassembleur XML respecte l’ordre spécifié pour les schémas d’enveloppe, mais pas celui des schémas de document.</span><span class="sxs-lookup"><span data-stu-id="c8780-105">The XML Disassembler enforces the specified order of envelope schemas; however, the order of document schemas is not enforced.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8780-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8780-106">See Also</span></span>  
 <span data-ttu-id="c8780-107">[Composant de Pipeline désassembleur XML](../core/xml-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="c8780-107">[XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="c8780-108">Comment configurer le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="c8780-108">How to Configure the XML Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)
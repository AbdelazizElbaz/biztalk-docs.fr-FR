---
title: Application de la Structure dans le composant de Pipeline assembleur XML de document | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add XML declaration property
- pipeline components, XML Assembler
ms.assetid: c121ec4b-c02b-4626-a5be-2937500dbefa
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e46dbc613439b24403c66c345b9023151b409213
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="document-structure-enforcement-in-the-xml-assembler-pipeline-component"></a><span data-ttu-id="73045-102">Mise en œuvre de Structure de document dans le composant de Pipeline assembleur XML</span><span class="sxs-lookup"><span data-stu-id="73045-102">Document Structure Enforcement in the XML Assembler Pipeline Component</span></span>
<span data-ttu-id="73045-103">Si des schémas de document ou d'enveloppe sont référencés explicitement dans l'Assembleur XML, ce dernier s'assure que seuls les documents dont le type de message correspond aux schémas référencés sont traités.</span><span class="sxs-lookup"><span data-stu-id="73045-103">If document or envelope schemas are explicitly referenced in the XML Assembler, the XML Assembler ensures that only documents with the message type corresponding to referenced schemas are processed.</span></span> <span data-ttu-id="73045-104">Les autres documents ne sont pas traités, même si un schéma est déployé pour eux.</span><span class="sxs-lookup"><span data-stu-id="73045-104">All the other documents are not processed even though a schema may be deployed for them.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73045-105">Le schéma d'enveloppe est extrait du premier message uniquement.</span><span class="sxs-lookup"><span data-stu-id="73045-105">The envelope schema is taken from the first message only.</span></span> <span data-ttu-id="73045-106">Les propriétés de l'enveloppe sont toujours extraites du premier message.</span><span class="sxs-lookup"><span data-stu-id="73045-106">The properties for the envelope are always taken from the first message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73045-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73045-107">See Also</span></span>  
 <span data-ttu-id="73045-108">[Composant de Pipeline assembleur XML](../core/xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="73045-108">[XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="73045-109">[Comment configurer le composant de Pipeline assembleur XML](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="73045-109">[How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="73045-110">Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="73045-110">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)
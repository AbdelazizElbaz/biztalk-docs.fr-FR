---
title: "Encodage de caractères dans le composant de Pipeline de désassembleur de fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IBaseMessagePart.Charset property
- XMLNorm.SourceCharset property
- pipeline components, Flat File Disassembler
- Flat File Disassembler [pipeline component], character encoding
ms.assetid: 0dbe24fb-c431-4edf-8aa9-4c040d6a7b32
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 839a3377f27417757e394c946fe96acc83752355
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="character-encoding-in-the-flat-file-disassembler-pipeline-component"></a><span data-ttu-id="0068c-102">Encodage de caractères dans le composant de Pipeline de désassembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="0068c-102">Character Encoding in the Flat File Disassembler Pipeline Component</span></span>
<span data-ttu-id="0068c-103">Le Désassembleur de fichier plat utilise l’algorithme suivant pour déterminer le codage à utiliser pour le traitement d’un message entrant :</span><span class="sxs-lookup"><span data-stu-id="0068c-103">The following algorithm is used by the Flat File Disassembler component to determine which encoding to use for processing an incoming message:</span></span>  
  
1.  <span data-ttu-id="0068c-104">S’il existe une marque d’ordre de tri dans les données, elle détermine les informations de codage.</span><span class="sxs-lookup"><span data-stu-id="0068c-104">If a byte order mark exists in the data, encoding information is determined from it.</span></span> <span data-ttu-id="0068c-105">Informations de codage ne sont pas conservées par le désassembleur (autrement dit, il n’est pas enregistré dans le **XMLNorm.SourceCharset** propriété).</span><span class="sxs-lookup"><span data-stu-id="0068c-105">This encoding information is not preserved by the disassembler (that is, it is not saved to the **XMLNorm.SourceCharset** property).</span></span>  
  
2.  <span data-ttu-id="0068c-106">Sinon, si le **IBaseMessagePart.Charset** propriété est définie, le codage spécifié ici est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0068c-106">Otherwise, if the **IBaseMessagePart.Charset** property is set, the encoding specified there is used.</span></span>  
  
3.  <span data-ttu-id="0068c-107">Si le schéma de document ou d'en-tête contient des informations de codepage, elles sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="0068c-107">Otherwise, if the header or document schema contains codepage information, it is used.</span></span>  
  
4.  <span data-ttu-id="0068c-108">Autrement, le codage UTF-8 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0068c-108">Otherwise, UTF-8 encoding is used.</span></span>  
  
 <span data-ttu-id="0068c-109">Pour les cas précédents 2, 3 et 4, le désassembleur enregistre les informations de codage dans le contexte de message dans le **XMLNorm.SourceCharset** propriété.</span><span class="sxs-lookup"><span data-stu-id="0068c-109">For the preceding cases 2, 3, and 4, the disassembler saves the encoding information on the message context in the **XMLNorm.SourceCharset** property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0068c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0068c-110">See Also</span></span>  
 <span data-ttu-id="0068c-111">[Composant de Pipeline désassembleur de fichier plat](../core/flat-file-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="0068c-111">[Flat File Disassembler Pipeline Component](../core/flat-file-disassembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="0068c-112">[Comment configurer le composant de Pipeline de désassembleur de fichier plat](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="0068c-112">[How to Configure the Flat File Disassembler Pipeline Component](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="0068c-113">Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="0068c-113">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)
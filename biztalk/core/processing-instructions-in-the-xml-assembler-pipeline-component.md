---
title: "Le traitement d’Instructions dans le composant de Pipeline assembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XMLNorm.ProcessingInstructionOption property
- envelopes, processing instructions
- XML Assembler [pipeline component], processing instructions
- Processing instruction scope property
- XMLNorm.ProcessingInstruction property
- envelopes, XML Assembler [pipeline component]
- pipeline components, XML Assembler
ms.assetid: d8ea453e-3b20-417d-bf25-9d424b0150fd
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85ac6045084c0aea672b0c1e9d6dfb1b4a742d55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-instructions-in-the-xml-assembler-pipeline-component"></a><span data-ttu-id="d01da-102">Dans le composant de Pipeline assembleur XML, les Instructions de traitement</span><span class="sxs-lookup"><span data-stu-id="d01da-102">Processing Instructions in the XML Assembler Pipeline Component</span></span>
<span data-ttu-id="d01da-103">Les instructions de traitement fournissent des informations à l’application qui traite un document XML.</span><span class="sxs-lookup"><span data-stu-id="d01da-103">Processing instructions provide information to the application that processes an XML document.</span></span> <span data-ttu-id="d01da-104">Il peut s’agir d’instructions sur le mode de traitement du document, son mode d'affichage, etc.</span><span class="sxs-lookup"><span data-stu-id="d01da-104">Such information may include instructions about how to process the document, how to display it, and so on.</span></span>  
  
 <span data-ttu-id="d01da-105">Les instructions de traitement sont ajoutées à un document XML par le **ajouter des instructions de traitement** propriété (ou l’équivalent **XMLNorm.ProcessingInstructionOption** propriété du contexte de message).</span><span class="sxs-lookup"><span data-stu-id="d01da-105">Processing instructions are added to an XML document by the **Add processing instructions** property (or the equivalent **XMLNorm.ProcessingInstructionOption** property on the message context).</span></span> <span data-ttu-id="d01da-106">Le texte de l’instruction de traitement est spécifié avec la **ajouter le texte des instructions de traitement** propriété (ou l’équivalent **XMLNorm.ProcessingInstruction** propriété du contexte de message).</span><span class="sxs-lookup"><span data-stu-id="d01da-106">Processing instruction text is specified with the **Add processing instructions text** property (or the equivalent **XMLNorm.ProcessingInstruction** property on the message context).</span></span>  
  
 <span data-ttu-id="d01da-107">Le **ajouter des instructions de traitement** propriété (ou **XMLNorm.ProcessingInstructionOption** propriété) a trois valeurs possibles, qui sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d01da-107">The **Add processing instructions** property (or **XMLNorm.ProcessingInstructionOption** property) has three possible values, which are described in the following table.</span></span>  
  
|<span data-ttu-id="d01da-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="d01da-108">Value</span></span>|<span data-ttu-id="d01da-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="d01da-109">Value</span></span>|<span data-ttu-id="d01da-110"> Description</span><span class="sxs-lookup"><span data-stu-id="d01da-110">Description</span></span>|  
|-----------|-----------|-----------------|  
|<span data-ttu-id="d01da-111">Ajouter</span><span class="sxs-lookup"><span data-stu-id="d01da-111">Append</span></span>|<span data-ttu-id="d01da-112">0</span><span class="sxs-lookup"><span data-stu-id="d01da-112">0</span></span>|<span data-ttu-id="d01da-113">Les nouvelles instructions de traitement de l’Assembleur XML sont ajoutées au début du document.</span><span class="sxs-lookup"><span data-stu-id="d01da-113">New processing instructions from the XML Assembler are appended to the processing instructions at the beginning of the document.</span></span>|  
|<span data-ttu-id="d01da-114">Créer de nouveaux</span><span class="sxs-lookup"><span data-stu-id="d01da-114">Create new</span></span>|<span data-ttu-id="d01da-115">1</span><span class="sxs-lookup"><span data-stu-id="d01da-115">1</span></span>|<span data-ttu-id="d01da-116">Les nouvelles instructions de traitement de l’Assembleur XML remplacent les instructions existantes en début de document.</span><span class="sxs-lookup"><span data-stu-id="d01da-116">New processing instructions from the XML Assembler overwrite existing processing instructions at the beginning of the document.</span></span>|  
|<span data-ttu-id="d01da-117">Ignore</span><span class="sxs-lookup"><span data-stu-id="d01da-117">Ignore</span></span>|<span data-ttu-id="d01da-118">2</span><span class="sxs-lookup"><span data-stu-id="d01da-118">2</span></span>|<span data-ttu-id="d01da-119">Les instructions de traitement au début du document sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="d01da-119">Processing instructions at the beginning of the document are removed.</span></span>|  
  
 <span data-ttu-id="d01da-120">La paire d’instructions de traitement (ou propriétés de contexte de message) spécifiée sur un contexte de message est prioritaire par rapport à la paire de propriétés spécifiée dans le Concepteur de pipeline.</span><span class="sxs-lookup"><span data-stu-id="d01da-120">The pair of processing instructions (or message context properties) specified on a message context take precedence over the property pair specified in Pipeline Designer.</span></span> <span data-ttu-id="d01da-121">Par exemple, si **XMLNorm.ProcessingInstructionOption** est spécifié en tant que **nouvel** (1) et **XMLNorm.ProcessingInstruction** n’est pas spécifié, un traitement vide instruction remplace une instruction de traitement existante.</span><span class="sxs-lookup"><span data-stu-id="d01da-121">For example, if **XMLNorm.ProcessingInstructionOption** is specified as **Create new** (1) and **XMLNorm.ProcessingInstruction** is not specified, an empty processing instruction will replace an existing processing instruction.</span></span>  
  
 <span data-ttu-id="d01da-122">Autre exemple, si **XMLNorm.ProcessingInstruction** est spécifiée mais **XMLNorm.ProcessingInstructionOption** n’est pas le cas, aucune des propriétés du contexte de message sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="d01da-122">As another example, if **XMLNorm.ProcessingInstruction** is specified but **XMLNorm.ProcessingInstructionOption** is not, none of the properties from the message context are used.</span></span> <span data-ttu-id="d01da-123">Dans ce cas, les instructions de traitement du Concepteur de pipeline sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="d01da-123">In this case, the processing instructions from Pipeline Designer are used.</span></span>  
  
 <span data-ttu-id="d01da-124">Par défaut, **ajouter des instructions de traitement** a la valeur **Append**, et **ajouter le texte des instructions de traitement** est vide.</span><span class="sxs-lookup"><span data-stu-id="d01da-124">By default, **Add processing instructions** is set to **Append**, and **Add processing instructions text** is empty.</span></span>  
  
## <a name="processing-properties-and-envelopes"></a><span data-ttu-id="d01da-125">Traitement des propriétés et des enveloppes</span><span class="sxs-lookup"><span data-stu-id="d01da-125">Processing Properties and Envelopes</span></span>  
 <span data-ttu-id="d01da-126">Dans la mesure où les instructions de traitement ne sont pas préservées pour les enveloppes, la combinaison suivante de paramétrages de l’assembleur de fichier plat donne le résultat suivant : seule l’enveloppe la plus éloignée dispose de l’instruction de traitement.</span><span class="sxs-lookup"><span data-stu-id="d01da-126">Because processing instructions are not preserved for the envelopes, the following combination of flat file assembler settings results in only the outermost envelope having the processing instruction:</span></span>  
  
-   <span data-ttu-id="d01da-127">**Étendue des instructions de traitement** propriété définie sur « Enveloppe ».</span><span class="sxs-lookup"><span data-stu-id="d01da-127">**Processing instruction scope** property set to "Envelope."</span></span>  
  
-   <span data-ttu-id="d01da-128">**Ajoutez les instructions de traitement** propriété définie sur « Ajouter ».</span><span class="sxs-lookup"><span data-stu-id="d01da-128">**Add processing instructions** property set to "Append."</span></span>  
  
 <span data-ttu-id="d01da-129">L’enveloppe utiliserait l’instruction de traitement spécifiée dans l’assembleur **le texte des instructions de traitement ajouter** propriété.</span><span class="sxs-lookup"><span data-stu-id="d01da-129">The envelope would use the processing instruction specified in the assembler's **Add Processing instructions text** property.</span></span>  
  
 <span data-ttu-id="d01da-130">Toute instruction existante dans l’enveloppe interne ou externe, tel que spécifié dans le message entrant, ne figurera pas dans le(s) message(s) sortant(s).</span><span class="sxs-lookup"><span data-stu-id="d01da-130">Any existing processing instructions in either the outer or inner envelope(s), as specified in the incoming message, will not be present in the output message(s).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d01da-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d01da-131">See Also</span></span>  
 <span data-ttu-id="d01da-132">[Composant de Pipeline assembleur XML](../core/xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="d01da-132">[XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="d01da-133">[Comment configurer le composant de Pipeline assembleur XML](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="d01da-133">[How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="d01da-134">Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="d01da-134">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)
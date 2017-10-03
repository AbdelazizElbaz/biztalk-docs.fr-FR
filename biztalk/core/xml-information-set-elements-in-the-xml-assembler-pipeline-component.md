---
title: "Éléments ensemble d’informations XML dans le composant de Pipeline assembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Assembler [pipeline component], processing instructions
- Add XML declaration property
- XMLNorm.AddXMLDeclaration property
- pipeline components, XML Assembler
- XML Assembler [pipeline component], XML information set
ms.assetid: 5a262763-838e-476b-8117-30c94bc1d64a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b194b85c88f63036cd74fcd9838aa99e73de6556
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-information-set-elements-in-the-xml-assembler-pipeline-component"></a><span data-ttu-id="f0e17-102">Éléments ensemble d’informations XML dans le composant de Pipeline assembleur XML</span><span class="sxs-lookup"><span data-stu-id="f0e17-102">XML Information Set Elements in the XML Assembler Pipeline Component</span></span>
<span data-ttu-id="f0e17-103">Le composant Assembleur XML gère les éléments d'ensemble d'informations XML comme suit :</span><span class="sxs-lookup"><span data-stu-id="f0e17-103">The XML Assembler component handles XML information set elements as follows.</span></span>  
  
|<span data-ttu-id="f0e17-104">Élément</span><span class="sxs-lookup"><span data-stu-id="f0e17-104">Element</span></span>|<span data-ttu-id="f0e17-105"> Description</span><span class="sxs-lookup"><span data-stu-id="f0e17-105">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0e17-106">comment</span><span class="sxs-lookup"><span data-stu-id="f0e17-106">comment</span></span>|<span data-ttu-id="f0e17-107">Les commentaires sont conservés entre les balises XML d'ouverture et de fermeture du document.</span><span class="sxs-lookup"><span data-stu-id="f0e17-107">Comments are preserved between opening and closing XML tags in the document.</span></span>|  
|<span data-ttu-id="f0e17-108">CDATA</span><span class="sxs-lookup"><span data-stu-id="f0e17-108">CDATA</span></span>|<span data-ttu-id="f0e17-109">CDATA est conservé entre les balises XML d'ouverture et de fermeture du document.</span><span class="sxs-lookup"><span data-stu-id="f0e17-109">CDATA is preserved between opening and closing XML tags in the document.</span></span> <span data-ttu-id="f0e17-110">Les valeurs CDATA ne sont pas utilisées pour la promotion des propriétés ou les champs distinctifs.</span><span class="sxs-lookup"><span data-stu-id="f0e17-110">CDATA values are not used for property promotion or distinguished fields.</span></span>|  
|<span data-ttu-id="f0e17-111">instructions de traitement</span><span class="sxs-lookup"><span data-stu-id="f0e17-111">processing instructions</span></span>|<span data-ttu-id="f0e17-112">Instructions de traitement situées avant la balise XML du document sont gérées en fonction de leur valeur (pour plus d’informations, consultez [d’Instructions de traitement dans le composant de Pipeline assembleur XML](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md)).</span><span class="sxs-lookup"><span data-stu-id="f0e17-112">Processing instructions located before the document XML tag are handled based on their value (for more information, see [Processing Instructions in the XML Assembler Pipeline Component](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md)).</span></span> <span data-ttu-id="f0e17-113">Les instructions de traitement situées entre les balises d'ouverture et de fermeture sont conservées.</span><span class="sxs-lookup"><span data-stu-id="f0e17-113">Processing instructions between document open and close tags are preserved.</span></span> <span data-ttu-id="f0e17-114">Les instructions de traitement placées après la balise XML de fermeture sont ignorées, tout comme le sont toutes les instructions situées avant, dans ou après l'enveloppe.</span><span class="sxs-lookup"><span data-stu-id="f0e17-114">Processing instructions after the closing XML tag are ignored, as are any instructions before, in, or after the envelope.</span></span>|  
|<span data-ttu-id="f0e17-115">déclaration XML</span><span class="sxs-lookup"><span data-stu-id="f0e17-115">XML declaration</span></span>|<span data-ttu-id="f0e17-116">Les chaînes de déclaration XML telles que `<?xml version='1.0'? encoding='UTF-8'>` peuvent être conservées par le composant de pipeline Assembleur XML.</span><span class="sxs-lookup"><span data-stu-id="f0e17-116">The XML declaration string, such as `<?xml version='1.0'? encoding='UTF-8'>`, may be preserved by the XML Assembler pipeline component.</span></span> <span data-ttu-id="f0e17-117">Ceci est contrôlé par le **ajouter une déclaration XML** propriété, ou son équivalent dans le contexte du message, **XMLNorm.AddXMLDeclaration**.</span><span class="sxs-lookup"><span data-stu-id="f0e17-117">This is controlled by the **Add XML declaration** property, or its equivalent on the message context, **XMLNorm.AddXMLDeclaration**.</span></span><br /><br /> <span data-ttu-id="f0e17-118">Si cette option est définie sur **True** la déclaration XML est ajoutés au document.</span><span class="sxs-lookup"><span data-stu-id="f0e17-118">If this option is set to **True** then the XML declaration will be added to the document.</span></span> <span data-ttu-id="f0e17-119">Si la déclaration XML existe déjà, elle sera remplacée.</span><span class="sxs-lookup"><span data-stu-id="f0e17-119">If the XML declaration already existed, it will be overwritten.</span></span><br /><br /> <span data-ttu-id="f0e17-120">Si cette option est définie sur **False**, aucune déclaration XML ne sera ajoutée et toute déclaration XML existante sera supprimée.</span><span class="sxs-lookup"><span data-stu-id="f0e17-120">If this option is set to **False**, no XML declaration will be added and any existing XML declaration will be removed.</span></span> <span data-ttu-id="f0e17-121">Dans le contexte du message, la valeur de cette propriété a priorité sur la valeur spécifiée dans le Concepteur de pipeline.</span><span class="sxs-lookup"><span data-stu-id="f0e17-121">The value of this property in the message context takes precedence over the value specified in Pipeline Designer.</span></span><br /><br /> <span data-ttu-id="f0e17-122">Valeur par défaut : **True** (la déclaration XML est toujours ajoutée)</span><span class="sxs-lookup"><span data-stu-id="f0e17-122">Default value: **True** (the XML declaration is always added)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0e17-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0e17-123">See Also</span></span>  
 <span data-ttu-id="f0e17-124">[Composant de Pipeline assembleur XML](../core/xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="f0e17-124">[XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="f0e17-125">[Comment configurer le composant de Pipeline assembleur XML](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="f0e17-125">[How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="f0e17-126">Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="f0e17-126">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)
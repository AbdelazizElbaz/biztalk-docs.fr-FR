---
title: "Utilisation d’enveloppes dans l’assembleur XML et les composants de Pipeline désassembleur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XMLNorm.EnvelopeSpecNames property
- XML Disassembler [pipeline component], envelopes
- envelopes, nesting
- envelopes, XML Disassembler [pipeline component]
- envelopes, XML Assembler [pipeline component]
- XML Assembler [pipeline component], envelopes
- Envelope Specification Names property
ms.assetid: ccffd2f7-c7b1-4103-a914-ae9b4b19bee3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0ae57a65bad84f3d46ceb27e9b5415dc3d1bc31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="envelope-use-in-the-xml-assembler-and-disassembler-pipeline-components"></a><span data-ttu-id="9acb7-102">Utilisation d’enveloppes dans l’assembleur XML et les composants de Pipeline désassembleur</span><span class="sxs-lookup"><span data-stu-id="9acb7-102">Envelope Use in the XML Assembler and Disassembler Pipeline Components</span></span>
<span data-ttu-id="9acb7-103">Un message XML peut inclure zéro, une ou plusieurs enveloppes.</span><span class="sxs-lookup"><span data-stu-id="9acb7-103">An XML message can include zero or more envelopes.</span></span> <span data-ttu-id="9acb7-104">L'exemple suivant illustre une enveloppe (en gras) associée à un document XML.</span><span class="sxs-lookup"><span data-stu-id="9acb7-104">The following example shows an envelope (in bold) wrapping an XML document.</span></span>  
  
```  
<ns1:document xmlns:ns1="http://myDocumentNamespaceURI.org">  
   <message>Hello</message>  
</ns1:document>  
  
```  
  
 <span data-ttu-id="9acb7-105">Les enveloppes remplissent deux fonctions :</span><span class="sxs-lookup"><span data-stu-id="9acb7-105">Envelopes serve two purposes:</span></span>  
  
-   <span data-ttu-id="9acb7-106">Elles peuvent inclure des valeurs de champ à utiliser pour promouvoir et rétrograder des propriétés.</span><span class="sxs-lookup"><span data-stu-id="9acb7-106">They can include field values to use for property promotion and demotion.</span></span>  
  
     <span data-ttu-id="9acb7-107">Le composant Désassembleur XML promeut les propriétés, tandis que le composant Assembleur XML les rétrograde.</span><span class="sxs-lookup"><span data-stu-id="9acb7-107">The XML Disassembler component promotes properties, and the XML Assembler component demotes properties.</span></span> <span data-ttu-id="9acb7-108">La promotion et la rétrogradation des propriétés peuvent aussi intervenir dans des documents XML.</span><span class="sxs-lookup"><span data-stu-id="9acb7-108">Property promotion and demotion can also occur in XML documents.</span></span>  
  
-   <span data-ttu-id="9acb7-109">Elles peuvent combiner plusieurs documents XML en un seul échange.</span><span class="sxs-lookup"><span data-stu-id="9acb7-109">They can combine several XML documents into a single interchange.</span></span>  
  
     <span data-ttu-id="9acb7-110">Un document XML bien formé ne pouvant comporter qu'un élément racine, une enveloppe permet de combiner plusieurs documents XML afin qu'ils partagent un seul élément racine.</span><span class="sxs-lookup"><span data-stu-id="9acb7-110">Because a well-formed XML document can have only one root element, an envelope enables you to combine multiple XML documents to share one root element.</span></span>  
  
 <span data-ttu-id="9acb7-111">Vous pouvez appliquer la forme canonique en spécifiant l’ordre des enveloppes à l’aide de la **éditeur de propriétés de Collection de schéma** boîte de dialogue est accessible en cliquant sur le bouton de sélection pour la **schémas d’enveloppe** propriété au moment du design dans l’assembleur XML.</span><span class="sxs-lookup"><span data-stu-id="9acb7-111">You can enforce the canonical form by specifying the envelope order by using the **Schema Collection Property Editor** dialog which is accessed by clicking the ellipses for the **Envelope schemas** design-time property in the XML Assembler.</span></span> <span data-ttu-id="9acb7-112">Vous pouvez également utiliser le **XMLNORM. EnvelopeSpecNames** propriété de contexte de message avant l’exécution de l’assembleur XML.</span><span class="sxs-lookup"><span data-stu-id="9acb7-112">You can also use the **XMLNORM.EnvelopeSpecNames** message context property before the XML Assembler is run.</span></span> <span data-ttu-id="9acb7-113">L'Assembleur XML produit un document enveloppé au format canonique.</span><span class="sxs-lookup"><span data-stu-id="9acb7-113">The XML Assembler produces an enveloped document in canonical form.</span></span>  
  
## <a name="nesting-envelopes"></a><span data-ttu-id="9acb7-114">Imbrication d'enveloppes</span><span class="sxs-lookup"><span data-stu-id="9acb7-114">Nesting envelopes</span></span>  
 <span data-ttu-id="9acb7-115">Vous pouvez imbriquer des enveloppes pour former des structures de documents complexes où plusieurs documents XML enveloppés peuvent être combinés en un échange plus vaste.</span><span class="sxs-lookup"><span data-stu-id="9acb7-115">You can nest envelopes to form complex document structures where several enveloped XML documents can be combined into a larger interchange.</span></span> <span data-ttu-id="9acb7-116">L'exemple suivant illustre un échange avec deux enveloppes.</span><span class="sxs-lookup"><span data-stu-id="9acb7-116">The following example shows an interchange wrapped by two envelopes.</span></span>  
  
```  
<envelope1>  
   <document1/>  
   <envelope2>  
      <document2/>  
      <document3/>  
   </envelope2>  
   <document4/>  
</envelope1>  
```  
  
 <span data-ttu-id="9acb7-117">L'exemple précédent présente une forme flexible, ce qui signifie qu'un document peut se situer au même niveau hiérarchique qu'une enveloppe.</span><span class="sxs-lookup"><span data-stu-id="9acb7-117">The preceding example illustrates a flexible form, which means that a document can be on the same hierarchy level as an envelope.</span></span> <span data-ttu-id="9acb7-118">Après le désassemblage du document enveloppé, quatre documents distincts sont créés (document1, document2, etc.).</span><span class="sxs-lookup"><span data-stu-id="9acb7-118">After disassembling the enveloped document, four separate documents are created (document1, document2, and so on).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9acb7-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9acb7-119">See Also</span></span>  
 [<span data-ttu-id="9acb7-120">Composants de pipeline</span><span class="sxs-lookup"><span data-stu-id="9acb7-120">Pipeline Components</span></span>](../core/pipeline-components.md)
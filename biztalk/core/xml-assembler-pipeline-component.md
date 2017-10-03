---
title: Composant de Pipeline assembleur XML | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Assembler [pipeline component]
- pipeline components, XML Assembler
ms.assetid: 3adfd603-0577-49c2-ae9d-445d62fed385
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22348b61ca32567190fa99e103fe536f5199af58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-assembler-pipeline-component"></a><span data-ttu-id="c6608-102">Composant de Pipeline assembleur XML</span><span class="sxs-lookup"><span data-stu-id="c6608-102">XML Assembler Pipeline Component</span></span>
<span data-ttu-id="c6608-103">Le composant de pipeline Assembleur XML associe l'assemblage et la sérialisation XML en un composant.</span><span class="sxs-lookup"><span data-stu-id="c6608-103">The XML Assembler pipeline component combines XML serializing and assembling in one component.</span></span> <span data-ttu-id="c6608-104">Sa fonction première est de remettre les propriétés de contexte de message dans les enveloppes et les documents.</span><span class="sxs-lookup"><span data-stu-id="c6608-104">Its primary function is to transfer properties from the message context back into envelopes and documents.</span></span>  
  
 <span data-ttu-id="c6608-105">Les actions suivantes se produisent dans le composant Assembleur XML après la réception d’un lot de messages formant un échange :</span><span class="sxs-lookup"><span data-stu-id="c6608-105">The following actions occur in the XML Assembler component after receiving a batch of messages to form an interchange:</span></span>  
  
1.  <span data-ttu-id="c6608-106">L’Assembleur crée l’enveloppe en utilisant la spécification d’enveloppe indiquée.</span><span class="sxs-lookup"><span data-stu-id="c6608-106">The assembler creates the envelope by using the specified envelope specification.</span></span>  
  
2.  <span data-ttu-id="c6608-107">Le composant place les propriétés de contenu dans les instances de message en utilisant les XPath prédéfinis codés comme annotations dans les schémas XSD associés au message.</span><span class="sxs-lookup"><span data-stu-id="c6608-107">The component puts the content properties on the message instances by using the predefined XPaths coded as annotations in the XSD schemas associated with the message.</span></span>  
  
3.  <span data-ttu-id="c6608-108">Le composant ajoute le message à l’enveloppe.</span><span class="sxs-lookup"><span data-stu-id="c6608-108">The component appends the message to the envelope.</span></span>  
  
4.  <span data-ttu-id="c6608-109">Le composant place les propriétés de contenu dans l’enveloppe en utilisant les XPath prédéfinis codés comme annotations dans les schémas XSD associés aux enveloppes.</span><span class="sxs-lookup"><span data-stu-id="c6608-109">The component puts the content properties on the envelope by using the predefined XPaths coded as annotations in the XSD schemas associated with envelopes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6608-110">Le composant de pipeline Assembleur XML ne renseigne pas les champs d’attribut absents, mais il alimente les champs d’élément vides lorsque les champs sont facultatifs et ne sont associés à aucune valeur fixe ou par défaut.</span><span class="sxs-lookup"><span data-stu-id="c6608-110">The XML Assembler pipeline component does not populate missing attribute fields, but does populate empty element fields when the fields are optional but do not have default or fixed values.</span></span>  
  
 <span data-ttu-id="c6608-111">Pour plus d’informations sur la configuration du composant de pipeline Assembleur XML, consultez [comment configurer le composant de Pipeline assembleur XML](../core/how-to-configure-the-xml-assembler-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="c6608-111">For information about configuring the XML Assembler pipeline component, see [How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6608-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c6608-112">In This Section</span></span>  
  
-   [<span data-ttu-id="c6608-113">Encodage de caractères dans le composant de Pipeline assembleur XML</span><span class="sxs-lookup"><span data-stu-id="c6608-113">Character Encoding in the XML Assembler Pipeline Component</span></span>](../core/character-encoding-in-the-xml-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="c6608-114">Dans le composant de Pipeline assembleur XML, les Instructions de traitement</span><span class="sxs-lookup"><span data-stu-id="c6608-114">Processing Instructions in the XML Assembler Pipeline Component</span></span>](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="c6608-115">Messages non reconnus dans le composant de Pipeline assembleur XML</span><span class="sxs-lookup"><span data-stu-id="c6608-115">Unrecognized Messages in the XML Assembler Pipeline Component</span></span>](../core/unrecognized-messages-in-the-xml-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="c6608-116">Éléments ensemble d’informations XML dans le composant de Pipeline assembleur XML</span><span class="sxs-lookup"><span data-stu-id="c6608-116">XML Information Set Elements in the XML Assembler Pipeline Component</span></span>](../core/xml-information-set-elements-in-the-xml-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="c6608-117">Mise en œuvre de Structure de document dans le composant de Pipeline assembleur XML</span><span class="sxs-lookup"><span data-stu-id="c6608-117">Document Structure Enforcement in the XML Assembler Pipeline Component</span></span>](../core/document-structure-enforcement-in-the-xml-assembler-pipeline-component.md)
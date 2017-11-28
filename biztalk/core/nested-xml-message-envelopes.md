---
title: "Imbriqué enveloppes de Message XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e880cef1-4e73-4bce-a06e-8c4d23bc5a8c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46b0f505dd9ba7da71df1cb460f9c9a6610763d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="nested-xml-message-envelopes"></a><span data-ttu-id="445bd-102">Enveloppes de message XML imbriquées</span><span class="sxs-lookup"><span data-stu-id="445bd-102">Nested XML Message Envelopes</span></span>
<span data-ttu-id="445bd-103">Les enveloppes XML peuvent être imbriquées pour créer des structures de document complexes.</span><span class="sxs-lookup"><span data-stu-id="445bd-103">XML envelopes can be nested to create complex document structures.</span></span> <span data-ttu-id="445bd-104">Les enveloppes XML imbriquées existent sous deux formes, appelées flexible et canonique.</span><span class="sxs-lookup"><span data-stu-id="445bd-104">Nested XML envelopes can occur in two forms, known as flexible and canonical.</span></span> <span data-ttu-id="445bd-105">L'exemple suivant montre la forme flexible de documents enveloppés, dans laquelle les documents et les enveloppes (en gras) peuvent apparaître au même niveau dans une enveloppe associée.</span><span class="sxs-lookup"><span data-stu-id="445bd-105">The following example shows the flexible form of enveloped documents, in which documents and envelopes (shown in bold type) can appear at the same level within an enclosing envelope.</span></span>  
  
```  
<envelope1>  
    <document1/>    <envelope2>  
        <document2/>  
        <document3/>  
    </envelope2>    <document4/>  
</envelope1>  
```  
  
 <span data-ttu-id="445bd-106">L'exemple suivant montre un message d'instance similaire appartenant à la forme canonique des documents enveloppés, dans laquelle tous les documents apparaissent au même niveau dans l'enveloppe la plus profonde.</span><span class="sxs-lookup"><span data-stu-id="445bd-106">The following example shows a similar instance message that conforms to the canonical form of enveloped documents, in which all documents appear at the same level within the innermost envelope.</span></span>  
  
```  
<envelope1>  
    <envelope2>  
        <document1/>  
        <document2/>  
        <document3/>  
        <document4/>  
    </envelope2>  
</envelope1>  
  
```  
  
 <span data-ttu-id="445bd-107">Pour un message d'instance prenant l'une ou l'autre des formes décrites, le désassembleur XML génèrera  document1, document2, document3 et document4.</span><span class="sxs-lookup"><span data-stu-id="445bd-107">Given an instance message in either of the forms described, the XML disassembler will produce document1, document2, document3, and document4.</span></span> <span data-ttu-id="445bd-108">Le contexte de message de chacun de ces documents inclut les propriétés promues à partir du document correspondant ainsi que celles promues dans chacune des enveloppes associées.</span><span class="sxs-lookup"><span data-stu-id="445bd-108">The message context of each of these documents includes the properties promoted from the corresponding document as well as the properties promoted within each of the enclosing envelopes.</span></span> <span data-ttu-id="445bd-109">Le tableau suivant montre les propriétés promues qui seront incluses dans le contexte de message de chaque document non encapsulé pour l'exemple de la forme et celui de la forme canonique, d'après les promotions de propriété spécifiées dans la première colonne pour les divers documents et enveloppes.</span><span class="sxs-lookup"><span data-stu-id="445bd-109">The following table shows the promoted properties that will be include in the message context of each unwrapped documents for both the flexible and canonical examples, given the property promotions specified in the first column for the various envelopes and documents.</span></span>  
  
|<span data-ttu-id="445bd-110">Promotions de propriétés spécifiées</span><span class="sxs-lookup"><span data-stu-id="445bd-110">Specified property promotions</span></span>|<span data-ttu-id="445bd-111">Propriétés de contexte de message résultantes pour l'exemple « flexible »</span><span class="sxs-lookup"><span data-stu-id="445bd-111">Resulting message context properties for flexible example</span></span>|<span data-ttu-id="445bd-112">Propriétés de contexte de message résultantes pour l'exemple « canonique »</span><span class="sxs-lookup"><span data-stu-id="445bd-112">Resulting message context properties for canonical example</span></span>|  
|-----------------------------------|---------------------------------------------------------------|----------------------------------------------------------------|  
|<span data-ttu-id="445bd-113">envelope1 : p1</span><span class="sxs-lookup"><span data-stu-id="445bd-113">envelope1: p1</span></span><br /><br /> <span data-ttu-id="445bd-114">envelope2 : p3</span><span class="sxs-lookup"><span data-stu-id="445bd-114">envelope2: p3</span></span><br /><br /> <span data-ttu-id="445bd-115">Document1 : p2</span><span class="sxs-lookup"><span data-stu-id="445bd-115">document1: p2</span></span><br /><br /> <span data-ttu-id="445bd-116">Document2 : p4 et p5</span><span class="sxs-lookup"><span data-stu-id="445bd-116">document2: p4 and p5</span></span><br /><br /> <span data-ttu-id="445bd-117">document3 : aucune promotion</span><span class="sxs-lookup"><span data-stu-id="445bd-117">document3: no promotions</span></span><br /><br /> <span data-ttu-id="445bd-118">document4 : aucune promotion</span><span class="sxs-lookup"><span data-stu-id="445bd-118">document4: no promotions</span></span>|<span data-ttu-id="445bd-119">Document1 : p1, p2</span><span class="sxs-lookup"><span data-stu-id="445bd-119">document1: p1, p2</span></span><br /><br /> <span data-ttu-id="445bd-120">Document2 : p1, p3, p4, p5</span><span class="sxs-lookup"><span data-stu-id="445bd-120">document2: p1, p3, p4, p5</span></span><br /><br /> <span data-ttu-id="445bd-121">document3 : p1, p3</span><span class="sxs-lookup"><span data-stu-id="445bd-121">document3: p1, p3</span></span><br /><br /> <span data-ttu-id="445bd-122">document4 : p1</span><span class="sxs-lookup"><span data-stu-id="445bd-122">document4: p1</span></span>|<span data-ttu-id="445bd-123">Document1 : p1, p2, p3</span><span class="sxs-lookup"><span data-stu-id="445bd-123">document1: p1, p2, p3</span></span><br /><br /> <span data-ttu-id="445bd-124">Document2 : p1, p3, p4, p5</span><span class="sxs-lookup"><span data-stu-id="445bd-124">document2: p1, p3, p4, p5</span></span><br /><br /> <span data-ttu-id="445bd-125">document3 : p1, p3</span><span class="sxs-lookup"><span data-stu-id="445bd-125">document3: p1, p3</span></span><br /><br /> <span data-ttu-id="445bd-126">document4 : p1, p3</span><span class="sxs-lookup"><span data-stu-id="445bd-126">document4: p1, p3</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="445bd-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="445bd-127">See Also</span></span>  
 <span data-ttu-id="445bd-128">[Enveloppes de Message XML](../core/xml-message-envelopes.md) </span><span class="sxs-lookup"><span data-stu-id="445bd-128">[XML Message Envelopes](../core/xml-message-envelopes.md) </span></span>  
 <span data-ttu-id="445bd-129">[Structure d’un Message XML](../core/structure-of-an-xml-message.md) </span><span class="sxs-lookup"><span data-stu-id="445bd-129">[Structure of an XML Message](../core/structure-of-an-xml-message.md) </span></span>  
 [<span data-ttu-id="445bd-130">Comment créer des schémas pour les enveloppes</span><span class="sxs-lookup"><span data-stu-id="445bd-130">How to Create Schemas for Envelopes</span></span>](../core/how-to-create-schemas-for-envelopes.md)
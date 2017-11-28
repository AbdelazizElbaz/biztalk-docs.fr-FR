---
title: "Rétrogradation de propriétés dans les composants de Pipeline assembleur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Assembler [pipeline component], properties
- pipeline components, properties
- BizTalk Framework Assembler [pipeline component], properties
- XML Assembler [pipeline component], about XML Assembler
- Flat File Assembler [pipeline component], properties
ms.assetid: c5275638-d594-4b0d-a818-b7a9460b41a6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af634d302f01b18c91ebdbb7533673e8b9c545c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="property-demotion-in-assembler-pipeline-components"></a><span data-ttu-id="a7d75-102">Rétrogradation de propriétés dans les composants de Pipeline assembleur</span><span class="sxs-lookup"><span data-stu-id="a7d75-102">Property Demotion in Assembler Pipeline Components</span></span>
<span data-ttu-id="a7d75-103">Vous pouvez utiliser la rétrogradation de propriétés pour copier la valeur d'une propriété du contexte du message dans le contenu du message, son en-tête ou son code de fin.</span><span class="sxs-lookup"><span data-stu-id="a7d75-103">You can use property demotion to copy a property value from the message context into the message content or to its header or trailer.</span></span> <span data-ttu-id="a7d75-104">Pour rétrograder des propriétés, vous utilisez une expression XPath spécifiée dans le document ou dans le schéma d'en-tête et de code de fin.</span><span class="sxs-lookup"><span data-stu-id="a7d75-104">You accomplish property demotion by using an XPath expression specified in the document or in the header and trailer schema.</span></span>  
  
 <span data-ttu-id="a7d75-105">Lors de l'écriture des données de date et d'heure de la propriété de contexte dans le document résultant, BizTalk Server considère que toutes les données de date et d'heure sont au format UTC.</span><span class="sxs-lookup"><span data-stu-id="a7d75-105">When writing datetime data from the context property into the resulting document, BizTalk Server assumes that all datetime data is in UTC format.</span></span>  
  
 <span data-ttu-id="a7d75-106">Le format utilisé pour écrire des propriétés dans les données est déterminé par le type de données XSD comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="a7d75-106">The format used to write properties into the data is determined by the XSD data type as shown in the following table.</span></span>  
  
|<span data-ttu-id="a7d75-107">Type de données</span><span class="sxs-lookup"><span data-stu-id="a7d75-107">Data type</span></span>|<span data-ttu-id="a7d75-108">Format</span><span class="sxs-lookup"><span data-stu-id="a7d75-108">Format</span></span>|  
|---------------|------------|  
|<span data-ttu-id="a7d75-109">xs:datetime</span><span class="sxs-lookup"><span data-stu-id="a7d75-109">xs:datetime</span></span>|<span data-ttu-id="a7d75-110">jj-MM-aaaaTHH:mm:ss.fffffffZ</span><span class="sxs-lookup"><span data-stu-id="a7d75-110">yyyy-MM-ddTHH:mm:ss.fffffffZ</span></span>|  
|<span data-ttu-id="a7d75-111">xs:date</span><span class="sxs-lookup"><span data-stu-id="a7d75-111">xs:date</span></span>|<span data-ttu-id="a7d75-112">jj-MM-aaaaZ</span><span class="sxs-lookup"><span data-stu-id="a7d75-112">yyyy-MM-ddZ</span></span>|  
|<span data-ttu-id="a7d75-113">xs:gDay</span><span class="sxs-lookup"><span data-stu-id="a7d75-113">xs:gDay</span></span>|<span data-ttu-id="a7d75-114">---jjZ</span><span class="sxs-lookup"><span data-stu-id="a7d75-114">---ddZ</span></span>|  
|<span data-ttu-id="a7d75-115">xs:gMonth</span><span class="sxs-lookup"><span data-stu-id="a7d75-115">xs:gMonth</span></span>|<span data-ttu-id="a7d75-116">--MM—Z</span><span class="sxs-lookup"><span data-stu-id="a7d75-116">--MM—Z</span></span>|  
|<span data-ttu-id="a7d75-117">xs:gMonthDay</span><span class="sxs-lookup"><span data-stu-id="a7d75-117">xs:gMonthDay</span></span>|<span data-ttu-id="a7d75-118">--jj-MMZ</span><span class="sxs-lookup"><span data-stu-id="a7d75-118">--MM-ddZ</span></span>|  
|<span data-ttu-id="a7d75-119">xs:gYear</span><span class="sxs-lookup"><span data-stu-id="a7d75-119">xs:gYear</span></span>|<span data-ttu-id="a7d75-120">aaaaZ</span><span class="sxs-lookup"><span data-stu-id="a7d75-120">yyyyZ</span></span>|  
|<span data-ttu-id="a7d75-121">xs:gYearMonth</span><span class="sxs-lookup"><span data-stu-id="a7d75-121">xs:gYearMonth</span></span>|<span data-ttu-id="a7d75-122">MM-aaaaZ</span><span class="sxs-lookup"><span data-stu-id="a7d75-122">yyyy-MMZ</span></span>|  
|<span data-ttu-id="a7d75-123">xs:time</span><span class="sxs-lookup"><span data-stu-id="a7d75-123">xs:time</span></span>|<span data-ttu-id="a7d75-124">HH:mm:ss.fffffffZ</span><span class="sxs-lookup"><span data-stu-id="a7d75-124">HH:mm:ss.fffffffZ</span></span>|  
  
## <a name="property-demotion-and-envelopes"></a><span data-ttu-id="a7d75-125">Promotion des propriétés et enveloppes</span><span class="sxs-lookup"><span data-stu-id="a7d75-125">Property Demotion and Envelopes</span></span>  
 <span data-ttu-id="a7d75-126">Il est souvent utile de rétrograder les valeurs provenant d'un ou de plusieurs espaces de noms système, ou de l'un de vos propres espaces de noms, lors de l'assemblage de fichiers à l'intérieur d'une enveloppe.</span><span class="sxs-lookup"><span data-stu-id="a7d75-126">It is often useful to demote values from one or more of the system namespaces -- or one of your own namespaces -- when assembling files within an envelope.</span></span> <span data-ttu-id="a7d75-127">Voici des exemples de scénarios courants :</span><span class="sxs-lookup"><span data-stu-id="a7d75-127">Some common scenarios include:</span></span>  
  
-   <span data-ttu-id="a7d75-128">Vous souhaitez inclure le nom du fichier d'origine envoyé au système dans des messages sortants de sorte que les systèmes principaux puissent suivre l'origine des données.</span><span class="sxs-lookup"><span data-stu-id="a7d75-128">You want to include the original file name submitted to the system in outbound messages so back-end systems can track the origin of data.</span></span>  
  
-   <span data-ttu-id="a7d75-129">Vous souhaitez écrire des données provenant du corps du message dans l'en-tête.</span><span class="sxs-lookup"><span data-stu-id="a7d75-129">You want to write data from the body message to the header.</span></span> <span data-ttu-id="a7d75-130">Par exemple, pour un bon de commande, il peut être utile d'écrire le nom de livraison dans l'enveloppe pour les systèmes en aval.</span><span class="sxs-lookup"><span data-stu-id="a7d75-130">For example, for a purchase order it might be useful to write the ship to name to the envelope for down-stream systems.</span></span>  
  
-   <span data-ttu-id="a7d75-131">Vous souhaitez combiner plusieurs champs différents dans l'en-tête sans écrire de code personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a7d75-131">You want to combine many different fields into the header without writing custom code.</span></span> <span data-ttu-id="a7d75-132">La rétrogradation de propriétés dans l'assembleur Xml ou l'assembleur de fichier plat peut suffire.</span><span class="sxs-lookup"><span data-stu-id="a7d75-132">Property demotion in the Xml assembler or flat file assembler can do the job.</span></span>  
  
 <span data-ttu-id="a7d75-133">Il est important de se souvenir que les composants Assembleur XML et Assembleur de fichier plat vous permettent de spécifier le schéma à utiliser pour l'enveloppe et le corps du document.</span><span class="sxs-lookup"><span data-stu-id="a7d75-133">It is important to remember that the XML and flat file assembler components both allow you to specify which schema to use for the envelope and document body.</span></span> <span data-ttu-id="a7d75-134">Vous pouvez choisir les mêmes schémas utilisés lors du désassemblage ou créer un schéma d'enveloppe avec des champs différents.</span><span class="sxs-lookup"><span data-stu-id="a7d75-134">You can choose the same schemas used in disassembly or create a new envelope schema with different fields.</span></span>  
  
 <span data-ttu-id="a7d75-135">Pour obtenir un exemple de ces concepts, consultez [EnvelopeProcessing (exemple BizTalk Server)](../core/envelopeprocessing-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a7d75-135">For an example of these concepts, see [EnvelopeProcessing (BizTalk Server Sample)](../core/envelopeprocessing-biztalk-server-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7d75-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7d75-136">See Also</span></span>  
 <span data-ttu-id="a7d75-137">[Composant de Pipeline assembleur de fichier plat](../core/flat-file-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="a7d75-137">[Flat File Assembler Pipeline Component](../core/flat-file-assembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="a7d75-138">Comment configurer le composant de Pipeline d’assembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="a7d75-138">How to Configure the Flat File Assembler Pipeline Component</span></span>](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)
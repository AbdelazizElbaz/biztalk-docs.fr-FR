---
title: "Validation des Messages EDI reçus | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c56a3c0-042e-4611-8131-d51098064f0f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dcc48b343332ea6b402841ec5ed1f5c9af49b2dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validation-of-received-edi-messages"></a><span data-ttu-id="bbcd3-102">Validation des messages EDI reçus</span><span class="sxs-lookup"><span data-stu-id="bbcd3-102">Validation of Received EDI Messages</span></span>
<span data-ttu-id="bbcd3-103">Lorsque le pipeline de réception EDI traite un message entrant, il réalise une série de validations sur l'enveloppe et les données du message.</span><span class="sxs-lookup"><span data-stu-id="bbcd3-103">When the EDI receive pipeline processes an incoming message, it performs a series of validations on the envelope and message data.</span></span> <span data-ttu-id="bbcd3-104">Certaines de ces opérations sont toujours effectuées ; certaines le sont uniquement si vous les avez activées.</span><span class="sxs-lookup"><span data-stu-id="bbcd3-104">Some of these processes are always performed; some are performed only if you enable them.</span></span> <span data-ttu-id="bbcd3-105">Les validations sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bbcd3-105">These validations include the following:</span></span>  
  
-   <span data-ttu-id="bbcd3-106">**Les validations sont toujours effectuées sont**:</span><span class="sxs-lookup"><span data-stu-id="bbcd3-106">**The validations that are always performed are**:</span></span>  
  
    -   <span data-ttu-id="bbcd3-107">validation de la structure de l'enveloppe d'échange ;</span><span class="sxs-lookup"><span data-stu-id="bbcd3-107">Validation of the structure of the interchange envelope.</span></span>  
  
    -   <span data-ttu-id="bbcd3-108">validation de l'enveloppe en fonction de l'accord de partenariat commercial (ou de l'accord de secours si aucun accord n'a été défini) ;</span><span class="sxs-lookup"><span data-stu-id="bbcd3-108">Validation of the envelope against trading partner agreement (or fallback agreement if no agreement is defined).</span></span>  
  
    -   <span data-ttu-id="bbcd3-109">validation du schéma de l'enveloppe par rapport au schéma de contrôle ;</span><span class="sxs-lookup"><span data-stu-id="bbcd3-109">Schema validation of the envelope against the control schema.</span></span>  
  
    -   <span data-ttu-id="bbcd3-110">validation du schéma des éléments de données du document informatisé par rapport au schéma de message.</span><span class="sxs-lookup"><span data-stu-id="bbcd3-110">Schema validation of the transaction-set data elements against the message schema.</span></span>  
  
    -   <span data-ttu-id="bbcd3-111">validation des types de documents informatisés au sein d'un groupe unique, sur la base du mappage de groupe du document informatisé fourni par la norme X12.</span><span class="sxs-lookup"><span data-stu-id="bbcd3-111">Validation of the types of transaction sets within a single group based on the transaction set -group mapping provided by X12 standards.</span></span>  
  
-   <span data-ttu-id="bbcd3-112">**Les validations sont effectuées uniquement si activé sont**:</span><span class="sxs-lookup"><span data-stu-id="bbcd3-112">**The validations that are performed only if enabled are**:</span></span>  
  
    -   <span data-ttu-id="bbcd3-113">validation EDI effectuée sur les éléments de données du document informatisé.</span><span class="sxs-lookup"><span data-stu-id="bbcd3-113">EDI validation performed on transaction-set data elements.</span></span> <span data-ttu-id="bbcd3-114">Cette opération est uniquement effectuée si elle est activée dans les propriétés d'accord ;</span><span class="sxs-lookup"><span data-stu-id="bbcd3-114">This is performed if enabled in the agreement properties.</span></span>  
  
    -   <span data-ttu-id="bbcd3-115">validation étendue effectuée sur les éléments de données du document informatisé.</span><span class="sxs-lookup"><span data-stu-id="bbcd3-115">Extended validation performed on transaction-set data elements.</span></span> <span data-ttu-id="bbcd3-116">Cette opération est uniquement effectuée si elle est activée dans les propriétés d'accord ;</span><span class="sxs-lookup"><span data-stu-id="bbcd3-116">This is performed if enabled in the agreement properties.</span></span>  
  
    -   <span data-ttu-id="bbcd3-117">validation de champ croisé effectuée sur les éléments de données du document informatisé (messages X12 uniquement).</span><span class="sxs-lookup"><span data-stu-id="bbcd3-117">Cross-field validation on transaction set data elements (X12-encoded messages only).</span></span> <span data-ttu-id="bbcd3-118">Cette opération est effectuée si activé dans le schéma du message.</span><span class="sxs-lookup"><span data-stu-id="bbcd3-118">This is performed if enabled in the message schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbcd3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbcd3-119">See Also</span></span>  
 <span data-ttu-id="bbcd3-120">[Validation structurelle EDI](../core/edi-structural-validation.md) </span><span class="sxs-lookup"><span data-stu-id="bbcd3-120">[EDI Structural Validation](../core/edi-structural-validation.md) </span></span>  
 <span data-ttu-id="bbcd3-121">[Validation des propriétés de contrat](../core/agreement-properties-validation.md) </span><span class="sxs-lookup"><span data-stu-id="bbcd3-121">[Agreement Properties Validation](../core/agreement-properties-validation.md) </span></span>  
 <span data-ttu-id="bbcd3-122">[Validation de Type (élément de données) EDI](../core/edi-type-data-element-validation.md) </span><span class="sxs-lookup"><span data-stu-id="bbcd3-122">[EDI Type (Data Element) Validation](../core/edi-type-data-element-validation.md) </span></span>  
 <span data-ttu-id="bbcd3-123">[Validation étendue (BTS-XSD)](../core/extended-bts-xsd-validation.md) </span><span class="sxs-lookup"><span data-stu-id="bbcd3-123">[Extended (BTS-XSD) Validation](../core/extended-bts-xsd-validation.md) </span></span>  
 <span data-ttu-id="bbcd3-124">[Validation de schéma](../core/schema-validation2.md) </span><span class="sxs-lookup"><span data-stu-id="bbcd3-124">[Schema Validation](../core/schema-validation2.md) </span></span>  
 [<span data-ttu-id="bbcd3-125">Validation de Segment de champ croisée</span><span class="sxs-lookup"><span data-stu-id="bbcd3-125">Cross Field-Segment Validation</span></span>](../core/cross-field-segment-validation.md)
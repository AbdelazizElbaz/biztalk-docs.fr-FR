---
title: Validation des Messages EDI sortants | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 491303c0-b585-409e-a289-a2f6f9f82469
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 946e90eb58c9b81e0cd7fa9bf2c02cc49af021ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validation-of-outgoing-edi-messages"></a><span data-ttu-id="a9bf7-102">Validation des messages EDI sortants</span><span class="sxs-lookup"><span data-stu-id="a9bf7-102">Validation of Outgoing EDI Messages</span></span>
<span data-ttu-id="a9bf7-103">Lorsque le pipeline d'envoi EDI traite un message à envoyer, il réalise une série de validations sur l'enveloppe et les données du message.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-103">When the EDI send pipeline processes a message to be sent, it performs a series of validations on the envelope and message data.</span></span> <span data-ttu-id="a9bf7-104">Certaines de ces opérations sont toujours effectuées ; certaines le sont uniquement si vous les avez activées.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-104">Some of these processes are always performed; some are performed only if you enable them.</span></span> <span data-ttu-id="a9bf7-105">Les validations sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a9bf7-105">These validations include the following:</span></span>  
  
-   <span data-ttu-id="a9bf7-106">validation du schéma des éléments de données du document informatisé par rapport au schéma de message.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-106">Schema validation of the transaction-set data elements against the message schema.</span></span> <span data-ttu-id="a9bf7-107">Cette opération est toujours effectuée.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-107">This is always performed.</span></span>  
  
-   <span data-ttu-id="a9bf7-108">validation de champ croisé effectuée sur les éléments de données du document informatisé (messages X12 uniquement).</span><span class="sxs-lookup"><span data-stu-id="a9bf7-108">Cross-field validation on transaction set data elements (X12-encoded messages only).</span></span> <span data-ttu-id="a9bf7-109">Cette opération est effectuée si elle est activée dans le schéma du message.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-109">This is performed if it is enabled in the message schema.</span></span>  
  
-   <span data-ttu-id="a9bf7-110">validation EDI effectuée sur les éléments de données du document informatisé.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-110">EDI validation performed on transaction-set data elements.</span></span> <span data-ttu-id="a9bf7-111">Cette opération est uniquement effectuée si elle est activée dans les propriétés d'accord.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-111">This is performed if enabled in agreement properties.</span></span>  
  
-   <span data-ttu-id="a9bf7-112">validation étendue effectuée sur les éléments de données du document informatisé.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-112">Extended validation performed on transaction-set data elements.</span></span> <span data-ttu-id="a9bf7-113">Cette opération est uniquement effectuée si elle est activée dans les propriétés d'accord.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-113">This is performed if enabled in agreement properties.</span></span>  
  
-   <span data-ttu-id="a9bf7-114">validation des documents informatisés au sein d'un groupe unique, sur la base du mappage de groupe du document informatisé fourni par la norme X12.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-114">Validation of the transaction sets within a single group based on the transaction set – group mapping, according to X12 standards.</span></span> <span data-ttu-id="a9bf7-115">Cette opération est effectuée uniquement lorsque le **entrants option de traitement par lots** est définie sur **préserver l’échange : suspendre l’échange en cas d’erreur** ou **préserver l’échange : interrompre la Transaction Définit en cas d’erreur**.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-115">This is performed only when the **Inbound batch processing option** property is set to **Preserve Interchange - suspend Interchange on Error** or **Preserve Interchange - suspend Transaction Sets on Error**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9bf7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9bf7-116">See Also</span></span>  
 <span data-ttu-id="a9bf7-117">[Validation structurelle EDI](../core/edi-structural-validation.md) </span><span class="sxs-lookup"><span data-stu-id="a9bf7-117">[EDI Structural Validation](../core/edi-structural-validation.md) </span></span>  
 <span data-ttu-id="a9bf7-118">[Validation des propriétés de contrat](../core/agreement-properties-validation.md) </span><span class="sxs-lookup"><span data-stu-id="a9bf7-118">[Agreement Properties Validation](../core/agreement-properties-validation.md) </span></span>  
 <span data-ttu-id="a9bf7-119">[Validation de Type (élément de données) EDI](../core/edi-type-data-element-validation.md) </span><span class="sxs-lookup"><span data-stu-id="a9bf7-119">[EDI Type (Data Element) Validation](../core/edi-type-data-element-validation.md) </span></span>  
 <span data-ttu-id="a9bf7-120">[Validation étendue (BTS-XSD)](../core/extended-bts-xsd-validation.md) </span><span class="sxs-lookup"><span data-stu-id="a9bf7-120">[Extended (BTS-XSD) Validation](../core/extended-bts-xsd-validation.md) </span></span>  
 <span data-ttu-id="a9bf7-121">[Validation de schéma](../core/schema-validation2.md) </span><span class="sxs-lookup"><span data-stu-id="a9bf7-121">[Schema Validation](../core/schema-validation2.md) </span></span>  
 [<span data-ttu-id="a9bf7-122">Validation de Segment de champ croisée</span><span class="sxs-lookup"><span data-stu-id="a9bf7-122">Cross Field-Segment Validation</span></span>](../core/cross-field-segment-validation.md)
---
title: "Problèmes connus de délimiteurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- known issues, delimiters
- delimiters
ms.assetid: 4eaacb3c-9d8d-43da-91dd-8bb25dec70e1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18168ade94eed99efff0a062904c14b387de6bcc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-known-issues"></a><span data-ttu-id="25f6b-102">Problèmes connus de séparateurs</span><span class="sxs-lookup"><span data-stu-id="25f6b-102">Delimiters Known Issues</span></span>
<span data-ttu-id="25f6b-103">Cette section contient des informations utiles qui peuvent vous aider à éviter les erreurs de délimiteur.</span><span class="sxs-lookup"><span data-stu-id="25f6b-103">This section contains useful information that may help you avoid delimiter errors.</span></span>  
  
## <a name="characters-not-recommended-to-be-used-as-delimiters"></a><span data-ttu-id="25f6b-104">Caractères ne pas recommandés d’être utilisés comme séparateurs</span><span class="sxs-lookup"><span data-stu-id="25f6b-104">Characters not recommended to be used as delimiters</span></span>  
 <span data-ttu-id="25f6b-105">Il est recommandé que vous n’utilisez pas les caractères suivants en tant que délimiteurs comme ils peuvent provoquer des erreurs :</span><span class="sxs-lookup"><span data-stu-id="25f6b-105">It is recommended that you do not use the following characters as delimiters as they might cause errors:</span></span>  
  
-   <span data-ttu-id="25f6b-106">Caractères null</span><span class="sxs-lookup"><span data-stu-id="25f6b-106">Null characters</span></span>  
  
-   <span data-ttu-id="25f6b-107">Espaces</span><span class="sxs-lookup"><span data-stu-id="25f6b-107">Spaces</span></span>  
  
## <a name="extra-delimiters-in-a-header-or-body-field-cause-multiple-errors"></a><span data-ttu-id="25f6b-108">Les délimiteurs supplémentaires dans un en-tête ou un champ corps de provoquer des erreurs multiples</span><span class="sxs-lookup"><span data-stu-id="25f6b-108">Extra delimiters in a header or body field cause multiple errors</span></span>  
 <span data-ttu-id="25f6b-109">Lorsque vous avez un délimiteur supplémentaire dans un champ dans un V2 HL7. X message, le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) analyseur peut générer deux messages d’erreur, une liée à la validation XML et l’autre liées à la validation structurelle.</span><span class="sxs-lookup"><span data-stu-id="25f6b-109">When you have an extra delimiter in a field in an HL7 V2.X message, the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) parser might generate two error messages, one related to XML validation and the other related to structural validation.</span></span>  
  
## <a name="trailing-delimiters-permitted-in-hl7-batch-segments"></a><span data-ttu-id="25f6b-110">Les délimiteurs de fin autorisés dans les segments de lot HL7</span><span class="sxs-lookup"><span data-stu-id="25f6b-110">Trailing delimiters permitted in HL7 batch segments</span></span>  
 <span data-ttu-id="25f6b-111">HL7 lot segments définis comme FHS, BHS, BizTalk Server et recherche en texte intégral peut avoir les délimiteurs de fin et n’est pas limités par l’indicateur de délimiteur de fin, car [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ne valide pas les délimiteurs de fin pour le traitement par lot de segments.</span><span class="sxs-lookup"><span data-stu-id="25f6b-111">HL7 defined batch segments such as FHS, BHS, BTS, and FTS can have trailing delimiters and are not constrained by the trailing delimiter flag, because [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not validate trailing delimiters for batching segments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f6b-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25f6b-112">See Also</span></span>  
 [<span data-ttu-id="25f6b-113">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="25f6b-113">Known Issues</span></span>](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)
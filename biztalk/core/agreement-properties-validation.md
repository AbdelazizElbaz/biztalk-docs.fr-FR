---
title: "Validation des propriétés de contrat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d565c26-37ef-4aee-aebb-3152880242a1
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20c01ec281005cbeaffda6dcd2349c1153a531b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="agreement-properties-validation"></a><span data-ttu-id="c712f-102">Validation des propriétés de l'accord</span><span class="sxs-lookup"><span data-stu-id="c712f-102">Agreement Properties Validation</span></span>
<span data-ttu-id="c712f-103">Les propriétés de l'accord incluent la détection de doublons de numéros de contrôle d'échanges, de groupes ou de documents informatisés.</span><span class="sxs-lookup"><span data-stu-id="c712f-103">Agreement properties include checks for duplicate control numbers for interchanges, groups, or transaction sets.</span></span> <span data-ttu-id="c712f-104">Le pipeline de réception EDI effectue ces validations seulement si elles sont activées dans les propriétés de l'accord.</span><span class="sxs-lookup"><span data-stu-id="c712f-104">The EDI receive pipeline will perform these validations only if they are enabled in agreement properties.</span></span> <span data-ttu-id="c712f-105">Ces validations sont :</span><span class="sxs-lookup"><span data-stu-id="c712f-105">These validations include:</span></span>  
  
-   <span data-ttu-id="c712f-106">Vérifier la présence de numéro de contrôle d'échange en double (ISA13 dans X12 ou UNB5 dans EDIFACT).</span><span class="sxs-lookup"><span data-stu-id="c712f-106">Checking for a duplicate interchange control number (ISA13 in X12 or UNB5 in EDIFACT).</span></span> <span data-ttu-id="c712f-107">Vous entrez une valeur de temps (en jours) pour définir une plage horaire valide pour cette vérification.</span><span class="sxs-lookup"><span data-stu-id="c712f-107">You enter a time value (in days) to establish the valid time range for this check.</span></span>  
  
-   <span data-ttu-id="c712f-108">Vérifier la présence de numéro de contrôle du groupe en double dans un échange (GS6 dans X12 ou UNG5 dans EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="c712f-108">Checking for a duplicate group control number in an interchange (GS6 in X12 or UNG5 in EDIFACT)</span></span>  
  
-   <span data-ttu-id="c712f-109">Vérifier la présence de numéro de contrôle du document informatisé en double dans un groupe fonctionnel (ST2 dans X12 ou UNH1 dans EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="c712f-109">Checking for a duplicate transaction set control number in a functional group (ST2 in X12 or UNH1 in EDIFACT)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c712f-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c712f-110">See Also</span></span>  
 [<span data-ttu-id="c712f-111">Validation des messages EDI</span><span class="sxs-lookup"><span data-stu-id="c712f-111">EDI Message Validation</span></span>](../core/edi-message-validation.md)
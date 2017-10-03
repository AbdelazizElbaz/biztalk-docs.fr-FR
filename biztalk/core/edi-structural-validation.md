---
title: Validation structurelle EDI | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87086614-5616-441d-915c-2979c63c6e2f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 505b9ac55eff0b6adb249d11788308f03902f1d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-structural-validation"></a><span data-ttu-id="46454-102">Validation structurelle EDI</span><span class="sxs-lookup"><span data-stu-id="46454-102">EDI Structural Validation</span></span>
<span data-ttu-id="46454-103">Les spécifications EDI pour le codage X12 et EDIFACT définissent des règles et des conventions spécifiques pour la structure des échanges EDI.</span><span class="sxs-lookup"><span data-stu-id="46454-103">EDI specifications for both X12 and EDIFACT encoding define specific rules and conventions for the structure of EDI interchanges.</span></span> <span data-ttu-id="46454-104">Le Désassembleur EDI dans EDIReceivePipeline vérifie que l'enveloppe de chaque message reçu respecte ces règles de structure.</span><span class="sxs-lookup"><span data-stu-id="46454-104">The EDI Disassembler in the EDIReceivePipeline verifies that the envelope of each received message complies with these structural rules.</span></span> <span data-ttu-id="46454-105">EDISendPipeline crée chaque message à envoyer en respectant ces règles et valide l'enveloppe avant l'envoi.</span><span class="sxs-lookup"><span data-stu-id="46454-105">The EDISendPipeline builds each message to be sent in accordance with these rules and validates the envelope before sending.</span></span>  
  
 <span data-ttu-id="46454-106">La validation structurelle permet de garantir que les en-têtes et les codes de fin requis sont présents.</span><span class="sxs-lookup"><span data-stu-id="46454-106">The structural validation ensures that the required headers and trailers are present.</span></span> <span data-ttu-id="46454-107">Les vérifications d'intégrité structurelle incluent des vérifications de classement et de comptage des segments et des boucles.</span><span class="sxs-lookup"><span data-stu-id="46454-107">The structural integrity checks include segment and loop ordering and count checks.</span></span> <span data-ttu-id="46454-108">Ces vérifications sont toujours effectuées pour s'assurer que le document sera analysé ou sérialisé correctement.</span><span class="sxs-lookup"><span data-stu-id="46454-108">These checks are always performed to ensure that the document will parse or serialize correctly.</span></span> <span data-ttu-id="46454-109">Cette validation est effectuée même si le **Validation de Type EDI** et/ou **Validation étendue** options sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="46454-109">This validation is performed even if the **EDI Type Validation** and/or **Extended Validation** options are disabled.</span></span> <span data-ttu-id="46454-110">Un échange dont les validations structurelles de base échouent est suspendu, même si le **Validation de Type EDI** et/ou **Validation étendue** options sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="46454-110">An interchange that fails the basic structural validations will be suspended, even if the **EDI Type Validation** and/or **Extended Validation** options are disabled.</span></span>  
  
 <span data-ttu-id="46454-111">Les valeurs des éléments de données des en-têtes et les codes de fin, et la façon dont en-têtes et les codes de fin et les éléments de données sont séparés, sont déterminées par l'accord.</span><span class="sxs-lookup"><span data-stu-id="46454-111">The values of the data elements within the headers and trailers, and how the headers/trailers and data elements are separated, are determined by the agreement.</span></span> <span data-ttu-id="46454-112">Elles sont validées au moyen du processus de validation du schéma.</span><span class="sxs-lookup"><span data-stu-id="46454-112">These are validated through schema validation.</span></span>  
  
 <span data-ttu-id="46454-113">Pour plus d’informations sur l’enveloppe et le contenu dans chaque ensemble d’en-têtes et codes de fin, consultez [Structure des messages EDI](../core/edi-message-structure.md).</span><span class="sxs-lookup"><span data-stu-id="46454-113">For more information about the envelope and the contents within each set of headers and trailers, see [EDI Message Structure](../core/edi-message-structure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46454-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46454-114">See Also</span></span>  
 [<span data-ttu-id="46454-115">Validation des messages EDI</span><span class="sxs-lookup"><span data-stu-id="46454-115">EDI Message Validation</span></span>](../core/edi-message-validation.md)
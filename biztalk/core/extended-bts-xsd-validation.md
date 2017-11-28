---
title: "Validation étendue (BTS-XSD) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f225115d-8890-4149-8e46-d1bc8af17e62
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed147515b48a23c55e552710d6a76d6df981edd7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extended-bts-xsd-validation"></a><span data-ttu-id="e3966-102">Validation étendue (BTS-XSD)</span><span class="sxs-lookup"><span data-stu-id="e3966-102">Extended (BTS-XSD) Validation</span></span>
<span data-ttu-id="e3966-103">Le pipeline de réception EDI et le pipeline d'envoi EDI effectuent une validation étendue uniquement si le schéma a été personnalisé à l'aide d'éléments d'un type de données autre qu'EDI.</span><span class="sxs-lookup"><span data-stu-id="e3966-103">The EDI receive pipeline and EDI send pipeline perform extended validation only if the schema has been customized with elements whose data type is not an EDI data type.</span></span> <span data-ttu-id="e3966-104">Ces éléments ajoutés ne sont pas validés via la validation EDI. Ils sont donc soumis à la validation étendue.</span><span class="sxs-lookup"><span data-stu-id="e3966-104">These added elements would not be validated by EDI validation, so will be covered by extended validation.</span></span> <span data-ttu-id="e3966-105">La validation étendue utilise `System.Xml.XmlValidatingReader` et comprend toutes les vérifications qui peuvent être définies dans un XSD standard.</span><span class="sxs-lookup"><span data-stu-id="e3966-105">Extended validation uses `System.Xml.XmlValidatingReader` and includes all checks that can be defined in a standard XSD.</span></span>  
  
 <span data-ttu-id="e3966-106">Vous pouvez configurer la validation étendue pour tous les messages à destination ou en provenance d'un tiers.</span><span class="sxs-lookup"><span data-stu-id="e3966-106">You configure extended validation for all messages to or from a party.</span></span> <span data-ttu-id="e3966-107">Pour cela, sélectionnez le **Validation étendue** case à cocher dans la **Validation** page (sous la **paramètres des documents informatisés** section pour X12 ou EDIFACT), dans le onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="e3966-107">You do so by selecting the **Extended Validation** checkbox in the **Validation** page (under the **Transaction Set Settings** section for either X12 or EDIFACT), on the one-way agreement tab in the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="e3966-108">Vous pouvez activer la validation étendue sans activer la validation EDI, ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="e3966-108">You can enable extension validation without enabling EDI validation, or vice versa.</span></span>  
  
 <span data-ttu-id="e3966-109">La validation étendue comprend les vérifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="e3966-109">Extended validation consists of the following checks:</span></span>  
  
-   <span data-ttu-id="e3966-110">Exigences en matière d'éléments de données et répétitions autorisées</span><span class="sxs-lookup"><span data-stu-id="e3966-110">Data element requirement and allowed repetition</span></span>  
  
-   <span data-ttu-id="e3966-111">Énumérations</span><span class="sxs-lookup"><span data-stu-id="e3966-111">Enumerations</span></span>  
  
-   <span data-ttu-id="e3966-112">Validation de la longueur de l'élément de données (min/max).</span><span class="sxs-lookup"><span data-stu-id="e3966-112">Data element length validation (min/max).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e3966-113">La validation étendue du traitement par lot des messages côté envoi EDI n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="e3966-113">Extended Validation for batched messages on the EDI send side is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3966-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3966-114">See Also</span></span>  
 [<span data-ttu-id="e3966-115">Validation des messages EDI</span><span class="sxs-lookup"><span data-stu-id="e3966-115">EDI Message Validation</span></span>](../core/edi-message-validation.md)
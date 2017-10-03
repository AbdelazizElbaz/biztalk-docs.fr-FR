---
title: "En fonction de l’ensemble de délimiteurs spécifié, aucun chiffre valide a été trouvé. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08887f7d-8256-4de3-8db9-b890451521ff
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9b726ca0ab052ff53ae7f20242972db69fc4725
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="based-on-the-specified-delimiter-set-no-valid-digit-could-be-found"></a><span data-ttu-id="8879e-102">En fonction de l’ensemble de délimiteurs spécifié, aucun chiffre valide a été trouvé.</span><span class="sxs-lookup"><span data-stu-id="8879e-102">Based on the specified delimiter set, no valid Digit could be found</span></span>
## <a name="details"></a><span data-ttu-id="8879e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="8879e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8879e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="8879e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="8879e-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="8879e-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="8879e-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="8879e-106">Event ID</span></span>|-|  
|<span data-ttu-id="8879e-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="8879e-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8879e-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="8879e-108"> EDI</span></span>|  
|<span data-ttu-id="8879e-109">Composant</span><span class="sxs-lookup"><span data-stu-id="8879e-109">Component</span></span>|<span data-ttu-id="8879e-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="8879e-110">EDI Engine</span></span>|  
|<span data-ttu-id="8879e-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="8879e-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="8879e-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="8879e-112">Message Text</span></span>|<span data-ttu-id="8879e-113">Sur la base de l'ensemble de délimiteurs spécifié, aucune valeur de chiffre n'a pu être trouvée.</span><span class="sxs-lookup"><span data-stu-id="8879e-113">Based on the specified delimiter set, no valid Digit could be found.</span></span> <span data-ttu-id="8879e-114">Utilisez un autre ensemble de délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="8879e-114">Please use another delimiter set.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8879e-115">Explication</span><span class="sxs-lookup"><span data-stu-id="8879e-115">Explanation</span></span>  
 <span data-ttu-id="8879e-116">Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi EDI n'a pas trouvé de chiffre valide lors de la génération d'un échange sortant, car un chiffre utilisé dans un champ de ce dernier était identique à un caractère de séparation.</span><span class="sxs-lookup"><span data-stu-id="8879e-116">This Error/Warning/Information event indicates that the EDI send pipeline could not find a valid digit when generating an outgoing interchange because a digit used in a field of the outgoing interchange was the same as a separator character.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8879e-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="8879e-117">User Action</span></span>  
 <span data-ttu-id="8879e-118">Pour résoudre cette erreur, modifiez les valeurs de séparateur utilisées par le pipeline d'envoi EDI pour créer un message afin qu'aucun caractère de séparation ne soit identique à un chiffre utilisé dans un champ de l'échange sortant.</span><span class="sxs-lookup"><span data-stu-id="8879e-118">To resolve this error, change the separator values used by the EDI send pipeline to create a message so that no separator character will be the same as a digit used in a field of the outgoing interchange.</span></span> <span data-ttu-id="8879e-119">Procédez de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="8879e-119">Do one of the following:</span></span>  
  
-   <span data-ttu-id="8879e-120">Pour un échange X12 envoyé à un tiers résolu, modifiez les paramètres de séparation dans la page Définition des segments ISA pour le tiers en tant que récepteur d'échanges.</span><span class="sxs-lookup"><span data-stu-id="8879e-120">For an X12 interchange being sent to a resolved party, change the separator settings in the ISA Segment Definition page for the party as interchange receiver.</span></span>  
  
-   <span data-ttu-id="8879e-121">Pour un échange X12 envoyé à un tiers qui n'a pas été résolu, modifiez les paramètres de séparation dans la page des propriétés globales Définition des segments ISA.</span><span class="sxs-lookup"><span data-stu-id="8879e-121">For an X12 interchange being sent to a party that has not been resolved, change the separator settings in the ISA Segment Definition global property page.</span></span>  
  
-   <span data-ttu-id="8879e-122">Pour un échange EDIFACT envoyé à un tiers résolu, modifiez les paramètres de séparation dans la page Définition des segments ISA pour le tiers considéré comme récepteur des échanges.</span><span class="sxs-lookup"><span data-stu-id="8879e-122">For an EDIFACT interchange being sent to a resolved party, change the separator settings in the UNA Segment Definition page for the party as interchange receiver.</span></span>  
  
-   <span data-ttu-id="8879e-123">Pour un échange EDIFACT envoyé à un tiers qui n'a pas été résolu, modifiez les paramètres de séparation dans la page des propriétés globales Définition des segments UNA.</span><span class="sxs-lookup"><span data-stu-id="8879e-123">For an EDIFACT interchange being sent to a party that has not been resolved, change the separator settings in the UNA Segment Definition global property page.</span></span>
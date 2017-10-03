---
title: "La limite maximale du numéro de contrôle d’échange a été atteinte pour le tiers de X12 acceptable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: adc49089-3c7b-4ce2-9fbc-68e582c3a822
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fba803260af4879e4e2a286c0f7864af7ccf2747
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-interchange-control-number-has-reached-for-party"></a><span data-ttu-id="ce91e-102">La limite maximale du numéro de contrôle d'échange X12 acceptable a été atteinte pour le tiers</span><span class="sxs-lookup"><span data-stu-id="ce91e-102">Max limit of acceptable X12 interchange control number has reached for party</span></span>
## <a name="details"></a><span data-ttu-id="ce91e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ce91e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce91e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ce91e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ce91e-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ce91e-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ce91e-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ce91e-106">Event ID</span></span>|-|  
|<span data-ttu-id="ce91e-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ce91e-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ce91e-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="ce91e-108"> EDI</span></span>|  
|<span data-ttu-id="ce91e-109">Composant</span><span class="sxs-lookup"><span data-stu-id="ce91e-109">Component</span></span>|<span data-ttu-id="ce91e-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="ce91e-110">EDI Engine</span></span>|  
|<span data-ttu-id="ce91e-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ce91e-111">Symbolic Name</span></span>|<span data-ttu-id="ce91e-112">PartyX12IsaNumberError</span><span class="sxs-lookup"><span data-stu-id="ce91e-112">PartyX12IsaNumberError</span></span>|  
|<span data-ttu-id="ce91e-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ce91e-113">Message Text</span></span>|<span data-ttu-id="ce91e-114">La limite maximale du numéro de contrôle d'échange X12 acceptable a été atteinte pour le tiers {0}.</span><span class="sxs-lookup"><span data-stu-id="ce91e-114">Max limit of acceptable X12 interchange control number has reached for party {0}.</span></span> <span data-ttu-id="ce91e-115">Réinitialisez le compteur en naviguant jusqu'au tiers dans l'écran du rôle du destinataire, champ ISA 13 dans le gestionnaire d'accords partenaires</span><span class="sxs-lookup"><span data-stu-id="ce91e-115">Reset counter by navigating to Party in receiver role screen, field ISA 13 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ce91e-116">Explication</span><span class="sxs-lookup"><span data-stu-id="ce91e-116">Explanation</span></span>  
 <span data-ttu-id="ce91e-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter l'échange x12 sortant car le numéro de contrôle (champ ISA13) spécifié dans les paramètres de tiers est supérieur à la valeur maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="ce91e-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing X12 interchange because the interchange control number in the ISA13 field specified in the party settings was greater than the maximum allowable value.</span></span> <span data-ttu-id="ce91e-118">Le nombre maximal de caractères d'un numéro de contrôle de l'échange est neuf.</span><span class="sxs-lookup"><span data-stu-id="ce91e-118">The maximum number of characters for the interchange control number is nine.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ce91e-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ce91e-119">User Action</span></span>  
 <span data-ttu-id="ce91e-120">Pour résoudre cette erreur, rétablissez le numéro de contrôle de l'échange en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="ce91e-120">To resolve this error, reset the interchange control number, as follows:</span></span>  
  
1.  <span data-ttu-id="ce91e-121">Dans la boîte de dialogue Propriétés EDI associée au tiers auquel l'échange correspond, ouvrez la page Définition du segment ISA pour le tiers en tant que récepteur d'échanges.</span><span class="sxs-lookup"><span data-stu-id="ce91e-121">In the EDI Properties dialog box for the party resolved for the interchange, open the ISA Segment Definition page for the party as interchange receiver.</span></span>  
  
2.  <span data-ttu-id="ce91e-122">Cliquez sur le champ d'édition associé au champ ISA13.</span><span class="sxs-lookup"><span data-stu-id="ce91e-122">Click the Edit field associated with the ISA13 field.</span></span>  
  
3.  <span data-ttu-id="ce91e-123">Définissez le numéro de contrôle de l'échange sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit acceptable.</span><span class="sxs-lookup"><span data-stu-id="ce91e-123">Set the interchange control number to a new value such that the field has an acceptable number of digits.</span></span>
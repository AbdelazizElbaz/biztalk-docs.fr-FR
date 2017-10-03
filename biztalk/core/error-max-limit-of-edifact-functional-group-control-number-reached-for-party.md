---
title: "La limite maximale du numéro de contrôle de groupe fonctionnel Edifact acceptable a été atteinte pour le tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fde516b-59f1-49a1-8456-127469df0e02
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d4a47e0866c78e692f8c992afbd6b24cde95632
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-edifact-functional-group-control-number-has-reached-for-party"></a><span data-ttu-id="c5e19-102">La limite maximale du numéro de contrôle du groupe fonctionnel EDIFACT acceptable a été atteinte pour le tiers.</span><span class="sxs-lookup"><span data-stu-id="c5e19-102">Max limit of acceptable Edifact functional group control number has reached for party</span></span>
## <a name="details"></a><span data-ttu-id="c5e19-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c5e19-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c5e19-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c5e19-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c5e19-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c5e19-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c5e19-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c5e19-106">Event ID</span></span>|-|  
|<span data-ttu-id="c5e19-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c5e19-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c5e19-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c5e19-108"> EDI</span></span>|  
|<span data-ttu-id="c5e19-109">Composant</span><span class="sxs-lookup"><span data-stu-id="c5e19-109">Component</span></span>|<span data-ttu-id="c5e19-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="c5e19-110">EDI Engine</span></span>|  
|<span data-ttu-id="c5e19-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c5e19-111">Symbolic Name</span></span>|<span data-ttu-id="c5e19-112">PartyEdifactUngNumberError</span><span class="sxs-lookup"><span data-stu-id="c5e19-112">PartyEdifactUngNumberError</span></span>|  
|<span data-ttu-id="c5e19-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c5e19-113">Message Text</span></span>|<span data-ttu-id="c5e19-114">La limite maximale du numéro de contrôle du groupe fonctionnel EDIFACT acceptable a été atteinte pour le tiers {0}.</span><span class="sxs-lookup"><span data-stu-id="c5e19-114">Max limit of acceptable Edifact functional group control number has reached for party {0}.</span></span> <span data-ttu-id="c5e19-115">Réinitialisez le compteur en naviguant jusqu'au tiers dans l'écran du rôle du destinataire, champ UNG 5 dans le gestionnaire d'accords partenaires</span><span class="sxs-lookup"><span data-stu-id="c5e19-115">Reset counter by navigating to Party in receiver role screen, field UNG 5 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c5e19-116">Explication</span><span class="sxs-lookup"><span data-stu-id="c5e19-116">Explanation</span></span>  
 <span data-ttu-id="c5e19-117">Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu traiter l'échange EDIFACT sortant, car le numéro de contrôle du groupe du champ UNG5 défini dans les paramètres du tiers, notamment le numéro de référence du champ UNG5.2, était supérieur à la valeur maximum autorisée.</span><span class="sxs-lookup"><span data-stu-id="c5e19-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing EDIFACT interchange because the group control number in the UNG5 field specified in the party settings, specifically the reference number in field UNG5.2, was greater than the maximum allowable value.</span></span> <span data-ttu-id="c5e19-118">La valeur maximale autorisée pour le numéro de contrôle du groupe dépend des valeurs des trois champs dans UNG5.</span><span class="sxs-lookup"><span data-stu-id="c5e19-118">The maximum allowable value for the group control number depends upon the values of the three fields in UNG5.</span></span> <span data-ttu-id="c5e19-119">Le numéro de référence (champ UNG5.2) peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13 (respectivement, champs UNG5.1 et UNG5.3). Les trois champs combinés peuvent contenir jusqu'à 14 caractères.</span><span class="sxs-lookup"><span data-stu-id="c5e19-119">The maximum number of characters is 14 for the reference number in field UNG5.2, 13 for the prefix in UNG5.1 and 13 for the suffix in UNG5.3, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c5e19-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c5e19-120">User Action</span></span>  
 <span data-ttu-id="c5e19-121">Pour résoudre cette erreur, rétablissez le champ du numéro de référence (UNG5.2) du numéro de contrôle du groupe en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="c5e19-121">To resolve this error, reset the reference number field (UNG5.2) of the group control number, as follows:</span></span>  
  
1.  <span data-ttu-id="c5e19-122">Dans la boîte de dialogue Propriétés EDI correspondant au tiers résolu pour l'échange, ouvrez la page Définition des segments UNG et UNH pour le tiers jouant le rôle de récepteur des échanges.</span><span class="sxs-lookup"><span data-stu-id="c5e19-122">In the EDI Properties dialog box for the party resolved for the interchange, open the UNG and UNH Segment Definition page for the party as interchange receiver.</span></span>  
  
2.  <span data-ttu-id="c5e19-123">Cliquez sur le champ d'édition associé au champ UNG5.</span><span class="sxs-lookup"><span data-stu-id="c5e19-123">Click the Edit field associated with the UNG5 field.</span></span>  
  
3.  <span data-ttu-id="c5e19-124">Définissez le champ du milieu du numéro de contrôle du groupe (le numéro de référence dans UNG5.2) sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit acceptable.</span><span class="sxs-lookup"><span data-stu-id="c5e19-124">Set the middle field of the group control number (the reference number in UNG5.2) to a new value such that the field has an acceptable number of digits.</span></span>
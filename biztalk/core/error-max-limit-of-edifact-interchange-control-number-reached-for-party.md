---
title: "La limite maximale du numéro de contrôle l’échange Edifact acceptable a été atteinte pour le tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c00c357-4c7b-42ea-a031-15bad0195a75
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fdb92781d137f57a09ce8c45693c2928646af24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-edifact-interchange-control-number-has-reached-for-party"></a><span data-ttu-id="09855-102">La limite maximale du numéro de contrôle d'échange EDIFACT acceptable a été atteinte pour le tiers</span><span class="sxs-lookup"><span data-stu-id="09855-102">Max limit of acceptable Edifact interchange control number has reached for party</span></span>
## <a name="details"></a><span data-ttu-id="09855-103">Détails</span><span class="sxs-lookup"><span data-stu-id="09855-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="09855-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="09855-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="09855-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="09855-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="09855-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="09855-106">Event ID</span></span>|-|  
|<span data-ttu-id="09855-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="09855-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="09855-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="09855-108"> EDI</span></span>|  
|<span data-ttu-id="09855-109">Composant</span><span class="sxs-lookup"><span data-stu-id="09855-109">Component</span></span>|<span data-ttu-id="09855-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="09855-110">EDI Engine</span></span>|  
|<span data-ttu-id="09855-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="09855-111">Symbolic Name</span></span>|<span data-ttu-id="09855-112">PartyEdifactUnbNumberError</span><span class="sxs-lookup"><span data-stu-id="09855-112">PartyEdifactUnbNumberError</span></span>|  
|<span data-ttu-id="09855-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="09855-113">Message Text</span></span>|<span data-ttu-id="09855-114">La limite maximale du numéro de contrôle d'échange EDIFACT acceptable a été atteinte pour le tiers {0}.</span><span class="sxs-lookup"><span data-stu-id="09855-114">Max limit of acceptable Edifact interchange control number has reached for party {0}.</span></span> <span data-ttu-id="09855-115">Réinitialisez le compteur en naviguant jusqu'au tiers dans l'écran du rôle du destinataire, champ UNB 5 dans le gestionnaire d'accords partenaires.</span><span class="sxs-lookup"><span data-stu-id="09855-115">Reset counter by navigating to Party in receiver role screen, field UNB 5 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="09855-116">Explication</span><span class="sxs-lookup"><span data-stu-id="09855-116">Explanation</span></span>  
 <span data-ttu-id="09855-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter l'échange sortant car le numéro de contrôle (champ UNB5) spécifié dans les paramètres du tiers, notamment le numéro de référence (champ UNB5.2), est supérieur à la valeur maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="09855-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing interchange because the interchange control number in the UNB5 field specified in the party settings, specifically the reference number in field UNB5.2, was greater than the maximum allowable value.</span></span> <span data-ttu-id="09855-118">La valeur maximale autorisée pour le numéro de contrôle d'un échange dépend des valeurs des trois champs dans UNB5.</span><span class="sxs-lookup"><span data-stu-id="09855-118">The maximum allowable value for the interchange control number depends upon the values of the three fields in UNB5.</span></span> <span data-ttu-id="09855-119">Le numéro de référence (champ UNB5.2) peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13 (respectivement, champs UNB5.1 et UNB5.3). Les trois champs combinés peuvent contenir jusqu'à 14 caractères.</span><span class="sxs-lookup"><span data-stu-id="09855-119">The maximum number of characters is 14 for the reference number in field UNB5.2, 13 for the prefix in UNB5.1 and 13 for the suffix in UNB5.3, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="09855-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="09855-120">User Action</span></span>  
 <span data-ttu-id="09855-121">Pour résoudre cette erreur, rétablissez le champ du numéro de référence (UNB5.2) du numéro de contrôle de l'échange en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="09855-121">To resolve this error, reset the reference number field (UNB5.2) of the interchange control number, as follows:</span></span>  
  
1.  <span data-ttu-id="09855-122">Dans la boîte de dialogue Propriétés EDI associée au tiers auquel l'échange correspond, ouvrez la page Définition du segment UNB pour le tiers en tant que récepteur d'échanges.</span><span class="sxs-lookup"><span data-stu-id="09855-122">In the EDI Properties dialog box for the party resolved for the interchange, open the UNB Segment Definition page for the party as interchange receiver.</span></span>  
  
2.  <span data-ttu-id="09855-123">Cliquez sur le champ d'édition associé au champ UNB5.</span><span class="sxs-lookup"><span data-stu-id="09855-123">Click the Edit field associated with the UNB5 field.</span></span>  
  
3.  <span data-ttu-id="09855-124">Définissez le champ du milieu du numéro de contrôle de l'échange (le numéro de référence dans UNB5.2) sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit acceptable.</span><span class="sxs-lookup"><span data-stu-id="09855-124">Set the middle field of the interchange control number (the reference number in UNB5.2) to a new value such that the field has an acceptable number of digits.</span></span>
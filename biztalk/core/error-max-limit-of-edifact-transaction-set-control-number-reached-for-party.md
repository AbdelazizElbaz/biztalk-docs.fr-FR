---
title: "La limite maximale de Edifact acceptable document informatisé a été atteinte pour le tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a64cc5d3-a845-4044-9c6e-879ecda15fce
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcbd2ce29ddeb99ba8c06e5dac9ff01be8c300b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-edifact-transaction-set-control-number-has-reached-for-party"></a><span data-ttu-id="64071-102">La limite maximale du numéro de contrôle du document informatisé Edifact acceptable a été atteinte pour le tiers</span><span class="sxs-lookup"><span data-stu-id="64071-102">Max limit of acceptable Edifact transaction set control number has reached for party</span></span>
## <a name="details"></a><span data-ttu-id="64071-103">Détails</span><span class="sxs-lookup"><span data-stu-id="64071-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="64071-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="64071-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="64071-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="64071-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="64071-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="64071-106">Event ID</span></span>|-|  
|<span data-ttu-id="64071-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="64071-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="64071-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="64071-108"> EDI</span></span>|  
|<span data-ttu-id="64071-109">Composant</span><span class="sxs-lookup"><span data-stu-id="64071-109">Component</span></span>|<span data-ttu-id="64071-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="64071-110">EDI Engine</span></span>|  
|<span data-ttu-id="64071-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="64071-111">Symbolic Name</span></span>|<span data-ttu-id="64071-112">GlobalEdifactUnhNumberError</span><span class="sxs-lookup"><span data-stu-id="64071-112">GlobalEdifactUnhNumberError</span></span>|  
|<span data-ttu-id="64071-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="64071-113">Message Text</span></span>|<span data-ttu-id="64071-114">La limite maximale du numéro de contrôle du document informatisé EDIFACT acceptable a été atteinte pour le tiers {0}.</span><span class="sxs-lookup"><span data-stu-id="64071-114">Max limit of acceptable Edifact transaction set control number has reached for party {0}.</span></span> <span data-ttu-id="64071-115">Réinitialisez le compteur en naviguant jusqu'au tiers dans l'écran du rôle du destinataire, champ UNH 1 dans le gestionnaire d'accords partenaires</span><span class="sxs-lookup"><span data-stu-id="64071-115">Reset counter by navigating to Party in receiver role screen, field UNH 1 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="64071-116">Explication</span><span class="sxs-lookup"><span data-stu-id="64071-116">Explanation</span></span>  
 <span data-ttu-id="64071-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter l'échange sortant car le numéro de contrôle du document informatisé (champ UNH1) spécifié dans les paramètres du tiers, notamment le numéro de référence (champ UNH1.2), est supérieur à la valeur maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="64071-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing interchange because the transaction set control number in the UNH1 field specified in the party settings, specifically the reference number in field UNH1.2, was greater than the maximum allowable value.</span></span> <span data-ttu-id="64071-118">La valeur maximale autorisée pour le numéro de contrôle d'un document informatisé dépend des valeurs des trois champs dans UNH1.</span><span class="sxs-lookup"><span data-stu-id="64071-118">The maximum allowable value for the transaction set control number depends upon the values of the three fields in UNH1.</span></span> <span data-ttu-id="64071-119">Le numéro de référence (champ UNH1.2) peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13 (respectivement, champs UNH1.1 et UNH1.3). Les trois champs combinés peuvent contenir jusqu'à 14 caractères.</span><span class="sxs-lookup"><span data-stu-id="64071-119">The maximum number of characters is 14 for the reference number in field UNH1.2, 13 for the prefix in UNH1.1 and 13 for the suffix in UNH1.3, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="64071-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="64071-120">User Action</span></span>  
 <span data-ttu-id="64071-121">Pour résoudre cette erreur, rétablissez le champ du numéro de référence (UNH1.2) du numéro de contrôle du document informatisé en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="64071-121">To resolve this error, reset the reference number field (UNH1.2) of the transaction set control number, as follows:</span></span>  
  
1.  <span data-ttu-id="64071-122">Dans la boîte de dialogue Propriétés EDI associée au tiers auquel l'échange correspond, ouvrez la page Définition des segments UNG et UNH.</span><span class="sxs-lookup"><span data-stu-id="64071-122">In the EDI Properties dialog box for the party resolved for the interchange, open the UNG and UNH Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="64071-123">Cliquez sur le champ d'édition associé au champ UNH1.</span><span class="sxs-lookup"><span data-stu-id="64071-123">Click the Edit field associated with the UNH1 field.</span></span>  
  
3.  <span data-ttu-id="64071-124">Définissez le champ du milieu du numéro de contrôle du document informatisé (le numéro de référence dans UNH1.2) sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit acceptable.</span><span class="sxs-lookup"><span data-stu-id="64071-124">Set the middle field of the transaction set control number (the reference number in UNH1.2) to a new value such that the field has an acceptable number of digits.</span></span>
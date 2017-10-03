---
title: "La limite maximale acceptable X12 document informatisé a été atteinte pour les paramètres invité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5a4aa5c-13a7-4234-916e-562b52644c51
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16ab48c7bc5615a17c4927d7bf971bdec87a9c2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-transaction-set-control-number-has-reached-for-guest-settings"></a><span data-ttu-id="62b14-102">La limite maximale du numéro de contrôle du document informatisé X12 acceptable a été atteinte pour les paramètres du tiers</span><span class="sxs-lookup"><span data-stu-id="62b14-102">Max limit of acceptable X12 transaction set control number has reached for Guest settings</span></span>
## <a name="details"></a><span data-ttu-id="62b14-103">Détails</span><span class="sxs-lookup"><span data-stu-id="62b14-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="62b14-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="62b14-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="62b14-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="62b14-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="62b14-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="62b14-106">Event ID</span></span>|-|  
|<span data-ttu-id="62b14-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="62b14-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="62b14-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="62b14-108"> EDI</span></span>|  
|<span data-ttu-id="62b14-109">Composant</span><span class="sxs-lookup"><span data-stu-id="62b14-109">Component</span></span>|<span data-ttu-id="62b14-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="62b14-110">EDI Engine</span></span>|  
|<span data-ttu-id="62b14-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="62b14-111">Symbolic Name</span></span>|<span data-ttu-id="62b14-112">GlobalX12TsNumberError</span><span class="sxs-lookup"><span data-stu-id="62b14-112">GlobalX12TsNumberError</span></span>|  
|<span data-ttu-id="62b14-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="62b14-113">Message Text</span></span>|<span data-ttu-id="62b14-114">La limite maximale du numéro de contrôle acceptable du document informatisé X12 a été atteinte pour les paramètres Invité.</span><span class="sxs-lookup"><span data-stu-id="62b14-114">Max limit of acceptable X12 transaction set control number has reached for Guest settings.</span></span> <span data-ttu-id="62b14-115">Réinitialisez le compteur en naviguant jusqu'au champ ST 2 de l'écran du rôle de l'expéditeur de la configuration globale, dans le gestionnaire d'accords partenaires</span><span class="sxs-lookup"><span data-stu-id="62b14-115">Reset counter by navigating to Global configuration sender role screen, field ST 2 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="62b14-116">Explication</span><span class="sxs-lookup"><span data-stu-id="62b14-116">Explanation</span></span>  
 <span data-ttu-id="62b14-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter l'échange X12 sortant car le numéro de contrôle du document informatisé (champ ST02) spécifié dans les paramètres globaux, notamment le numéro de référence (champ ST02.2), est supérieur à la valeur maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="62b14-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing X12 interchange because the transaction set control number in the ST02 field specified in the global settings, specifically the reference number in field ST02.2, was greater than the maximum allowable value.</span></span> <span data-ttu-id="62b14-118">La valeur maximale autorisée pour le numéro de contrôle d'un document informatisé dépend des valeurs des trois champs dans ST02.</span><span class="sxs-lookup"><span data-stu-id="62b14-118">The maximum allowable value for the transaction set control number depends upon the values of the three fields in ST02.</span></span> <span data-ttu-id="62b14-119">Le numéro de référence (champ UNH1.2) peut comporter jusqu'à 9 caractères, le préfixe et le suffixe 8 (respectivement, champs UNH1.1 et UNH1.3). Les trois champs combinés peuvent contenir jusqu'à 9 caractères.</span><span class="sxs-lookup"><span data-stu-id="62b14-119">The maximum number of characters is 9 for the reference number in field UNH1.2, 8 for the prefix in UNH1.1 and 8 for the suffix in UNH1.3, and 9 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="62b14-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="62b14-120">User Action</span></span>  
 <span data-ttu-id="62b14-121">Pour résoudre cette erreur, rétablissez le champ du numéro de référence (ST02.2) du numéro de contrôle du document informatisé en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="62b14-121">To resolve this error, reset the reference number field (ST02.2) of the transaction set control number, as follows:</span></span>  
  
1.  <span data-ttu-id="62b14-122">Dans la boîte de dialogue Propriétés globales EDI, ouvrez la page de définition des segments GS et ST.</span><span class="sxs-lookup"><span data-stu-id="62b14-122">In the EDI Global Properties dialog box, open the GS and ST Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="62b14-123">Cliquez sur le champ d'édition associé au champ ST02.</span><span class="sxs-lookup"><span data-stu-id="62b14-123">Click the Edit field associated with the ST02 field.</span></span>  
  
3.  <span data-ttu-id="62b14-124">Définissez le champ du milieu du numéro de contrôle du groupe (le numéro de référence dans ST02.2) sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit acceptable.</span><span class="sxs-lookup"><span data-stu-id="62b14-124">Set the middle field of the group control number (the reference number in ST02.2) to a new value such that the field has an acceptable number of digits.</span></span>
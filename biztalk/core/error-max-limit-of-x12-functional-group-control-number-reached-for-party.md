---
title: "La limite maximale du numéro de contrôle de groupe fonctionnel a été atteinte pour le tiers de X12 acceptable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a920a66c-1e38-4f4a-8113-cbad01940839
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91d9fd8cba9ca86627c1381917a107e3ade754e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-functional-group-control-number-has-reached-for-party"></a><span data-ttu-id="ee794-102">La limite maximale du numéro de contrôle du groupe fonctionnel X12 acceptable a été atteinte pour le tiers</span><span class="sxs-lookup"><span data-stu-id="ee794-102">Max limit of acceptable X12 functional group control number has reached for party</span></span>
## <a name="details"></a><span data-ttu-id="ee794-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ee794-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee794-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ee794-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ee794-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ee794-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ee794-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ee794-106">Event ID</span></span>|-|  
|<span data-ttu-id="ee794-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ee794-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ee794-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="ee794-108"> EDI</span></span>|  
|<span data-ttu-id="ee794-109">Composant</span><span class="sxs-lookup"><span data-stu-id="ee794-109">Component</span></span>|<span data-ttu-id="ee794-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="ee794-110">EDI Engine</span></span>|  
|<span data-ttu-id="ee794-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ee794-111">Symbolic Name</span></span>|<span data-ttu-id="ee794-112">PartyX12GsNumberError</span><span class="sxs-lookup"><span data-stu-id="ee794-112">PartyX12GsNumberError</span></span>|  
|<span data-ttu-id="ee794-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ee794-113">Message Text</span></span>|<span data-ttu-id="ee794-114">La limite maximale du numéro de contrôle du groupe fonctionnel X12 acceptable a été atteinte pour le tiers {0}.</span><span class="sxs-lookup"><span data-stu-id="ee794-114">Max limit of acceptable X12 functional group control number has reached for party {0}.</span></span> <span data-ttu-id="ee794-115">Réinitialisez le compteur en naviguant jusqu'au tiers dans l'écran du rôle de destinataire, champ GS 6 dans le gestionnaire d'accords partenaires</span><span class="sxs-lookup"><span data-stu-id="ee794-115">Reset counter by navigating to Party in receiver role screen, field GS 6 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ee794-116">Explication</span><span class="sxs-lookup"><span data-stu-id="ee794-116">Explanation</span></span>  
 <span data-ttu-id="ee794-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter l'échange sortant car le numéro de contrôle du groupe (champ GS06) spécifié dans les paramètres du tiers est supérieur à la valeur maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="ee794-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing X12 interchange because the group control number in the GS06 field specified in the party settings was greater than the maximum allowable value.</span></span> <span data-ttu-id="ee794-118">Le nombre maximal de caractères du numéro de contrôle du groupe est 9.</span><span class="sxs-lookup"><span data-stu-id="ee794-118">The maximum number of characters for the group control number is 9.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ee794-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ee794-119">User Action</span></span>  
 <span data-ttu-id="ee794-120">Pour résoudre cette erreur, rétablissez le numéro de contrôle du groupe en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="ee794-120">To resolve this error, reset the group control number, as follows:</span></span>  
  
1.  <span data-ttu-id="ee794-121">Dans la boîte de dialogue Propriétés EDI associée au tiers auquel l'échange correspond, ouvrez la page Définition des segments GS et ST pour le tiers en tant que récepteur d'échanges.</span><span class="sxs-lookup"><span data-stu-id="ee794-121">In the EDI Properties dialog box for the party resolved for the interchange, open the GS and ST Segment Definition page for the party as interchange receiver.</span></span>  
  
2.  <span data-ttu-id="ee794-122">Cliquez sur le champ d'édition associé au champ GS06.</span><span class="sxs-lookup"><span data-stu-id="ee794-122">Click the Edit field associated with the GS06 field.</span></span>  
  
3.  <span data-ttu-id="ee794-123">Définissez le numéro de contrôle du groupe sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit inférieur ou égal à neuf.</span><span class="sxs-lookup"><span data-stu-id="ee794-123">Set the group control number to a new value such that the field has nine or fewer digits.</span></span>
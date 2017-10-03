---
title: "La limite maximale du numéro de contrôle d’échange a été atteinte pour les paramètres invité de X12 acceptable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9737053d-6065-4c88-8dfa-5f69b48e0e82
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c72fc565367477d9dbd09f3c0d4c4f9d6ab686a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-interchange-control-number-has-reached-for-guest-settings"></a><span data-ttu-id="4ea77-102">Limite maximale du numéro de contrôle d’échange a été atteinte pour les paramètres invité de X12 acceptable</span><span class="sxs-lookup"><span data-stu-id="4ea77-102">Max limit of acceptable X12 interchange control number has reached for Guest settings</span></span>
## <a name="details"></a><span data-ttu-id="4ea77-103">Détails</span><span class="sxs-lookup"><span data-stu-id="4ea77-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4ea77-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="4ea77-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="4ea77-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="4ea77-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="4ea77-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="4ea77-106">Event ID</span></span>|-|  
|<span data-ttu-id="4ea77-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="4ea77-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4ea77-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="4ea77-108"> EDI</span></span>|  
|<span data-ttu-id="4ea77-109">Composant</span><span class="sxs-lookup"><span data-stu-id="4ea77-109">Component</span></span>|<span data-ttu-id="4ea77-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="4ea77-110">EDI Engine</span></span>|  
|<span data-ttu-id="4ea77-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="4ea77-111">Symbolic Name</span></span>|<span data-ttu-id="4ea77-112">GlobalX12IsaNumberError</span><span class="sxs-lookup"><span data-stu-id="4ea77-112">GlobalX12IsaNumberError</span></span>|  
|<span data-ttu-id="4ea77-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="4ea77-113">Message Text</span></span>|<span data-ttu-id="4ea77-114">La limite maximale du numéro de contrôle acceptable de l'échange X12 a été atteinte pour les paramètres Invité</span><span class="sxs-lookup"><span data-stu-id="4ea77-114">Max limit of acceptable X12 interchange control number has reached for Guest settings.</span></span> <span data-ttu-id="4ea77-115">Réinitialisez le compteur en naviguant jusqu'au champ ISA 13 de l'écran du rôle de destinataire de la configuration globale dans le gestionnaire d'accords partenaires</span><span class="sxs-lookup"><span data-stu-id="4ea77-115">Reset counter by navigating to Global configuration receiver role screen, field ISA 13 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4ea77-116">Explication</span><span class="sxs-lookup"><span data-stu-id="4ea77-116">Explanation</span></span>  
 <span data-ttu-id="4ea77-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter l'échange x12 sortant car le numéro de contrôle (champ ISA13) spécifié dans les paramètres globaux est supérieur à la valeur maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="4ea77-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing X12 interchange because the interchange control number in the ISA13 field specified in the global settings was greater than the maximum allowable value.</span></span> <span data-ttu-id="4ea77-118">Le nombre maximal de caractères d'un numéro de contrôle de l'échange est neuf.</span><span class="sxs-lookup"><span data-stu-id="4ea77-118">The maximum number of characters for the interchange control number is nine.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4ea77-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4ea77-119">User Action</span></span>  
 <span data-ttu-id="4ea77-120">Pour résoudre cette erreur, rétablissez le numéro de contrôle de l'échange en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="4ea77-120">To resolve this error, reset the interchange control number, as follows:</span></span>  
  
1.  <span data-ttu-id="4ea77-121">Dans la boîte de dialogue Propriétés globales EDI, ouvrez la page Définition des segments ISA.</span><span class="sxs-lookup"><span data-stu-id="4ea77-121">In the EDI Global Properties dialog box, open the ISA Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="4ea77-122">Cliquez sur le champ d'édition associé au champ ISA13.</span><span class="sxs-lookup"><span data-stu-id="4ea77-122">Click the Edit field associated with the ISA13 field.</span></span>  
  
3.  <span data-ttu-id="4ea77-123">Définissez le numéro de contrôle de l'échange sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit acceptable.</span><span class="sxs-lookup"><span data-stu-id="4ea77-123">Set the interchange control number to a new value such that the field has an acceptable number of digits.</span></span>
---
title: "La limite maximale acceptable X12 numéro de contrôle de groupe fonctionnel a été atteinte pour les paramètres invité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05cba774-fa35-4694-aa34-d7151f8cd75c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3210fb773b7093c2e28f98e0cf1aa223e1a63936
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-functional-group-control-number-has-reached-for-guest-settings"></a><span data-ttu-id="456ed-102">La limite maximale acceptable pour le numéro de contrôle du groupe fonctionnel X12 a été atteinte pour les paramètres Invité.</span><span class="sxs-lookup"><span data-stu-id="456ed-102">Max limit of acceptable X12 functional group control number has reached for Guest settings</span></span>
## <a name="details"></a><span data-ttu-id="456ed-103">Détails</span><span class="sxs-lookup"><span data-stu-id="456ed-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="456ed-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="456ed-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="456ed-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="456ed-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="456ed-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="456ed-106">Event ID</span></span>|-|  
|<span data-ttu-id="456ed-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="456ed-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="456ed-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="456ed-108"> EDI</span></span>|  
|<span data-ttu-id="456ed-109">Composant</span><span class="sxs-lookup"><span data-stu-id="456ed-109">Component</span></span>|<span data-ttu-id="456ed-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="456ed-110">EDI Engine</span></span>|  
|<span data-ttu-id="456ed-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="456ed-111">Symbolic Name</span></span>|<span data-ttu-id="456ed-112">GlobalEdifactUnhNumberError</span><span class="sxs-lookup"><span data-stu-id="456ed-112">GlobalEdifactUnhNumberError</span></span>|  
|<span data-ttu-id="456ed-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="456ed-113">Message Text</span></span>|<span data-ttu-id="456ed-114">La limite maximale du numéro de contrôle du groupe fonctionnel X12 acceptable pour les paramètres Invité.</span><span class="sxs-lookup"><span data-stu-id="456ed-114">Max limit of acceptable X12 functional group control number has reached for Guest settings.</span></span> <span data-ttu-id="456ed-115">Réinitialisez le compteur en naviguant jusqu'au champ GS 6 de l'écran du rôle de destinataire de la configuration globale dans le gestionnaire d'accords partenaires.</span><span class="sxs-lookup"><span data-stu-id="456ed-115">Reset counter by navigating to Global configuration receiver role screen, field GS 6 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="456ed-116">Explication</span><span class="sxs-lookup"><span data-stu-id="456ed-116">Explanation</span></span>  
 <span data-ttu-id="456ed-117">Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu traiter l'échange X12 sortant, car le numéro de contrôle du groupe du champ GS06 défini dans les paramètres globaux était supérieur à la valeur maximum autorisée.</span><span class="sxs-lookup"><span data-stu-id="456ed-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing X12 interchange because the group control number in the GS06 field specified in the global settings was greater than the maximum allowable value.</span></span> <span data-ttu-id="456ed-118">Le nombre maximal de caractères du numéro de contrôle du groupe est 9.</span><span class="sxs-lookup"><span data-stu-id="456ed-118">The maximum number of characters for the group control number is 9.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="456ed-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="456ed-119">User Action</span></span>  
 <span data-ttu-id="456ed-120">Pour résoudre cette erreur, rétablissez le numéro de contrôle du groupe en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="456ed-120">To resolve this error, reset the group control number, as follows:</span></span>  
  
1.  <span data-ttu-id="456ed-121">Dans la boîte de dialogue Propriétés globales EDI, ouvrez la page de définition des segments GS et ST.</span><span class="sxs-lookup"><span data-stu-id="456ed-121">In the EDI Global Properties dialog box, open the GS and ST Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="456ed-122">Cliquez sur le champ d'édition associé au champ GS06.</span><span class="sxs-lookup"><span data-stu-id="456ed-122">Click the Edit field associated with the GS06 field.</span></span>  
  
3.  <span data-ttu-id="456ed-123">Définissez le numéro de contrôle du groupe sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit inférieur ou égal à neuf.</span><span class="sxs-lookup"><span data-stu-id="456ed-123">Set the group control number to a new value such that the field has nine or fewer digits.</span></span>
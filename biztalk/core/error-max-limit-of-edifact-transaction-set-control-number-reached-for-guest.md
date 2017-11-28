---
title: "La limite maximale de Edifact acceptable document informatisé a été atteinte pour les paramètres invité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3924a18c-87bc-4727-b7cd-598d3e5ade2a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 709d6069d143cea2271e6311fad571a0290133db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-edifact-transaction-set-control-number-has-reached-for-guest-settings"></a><span data-ttu-id="e5043-102">La limite maximale du nombre de contrôle d'ensembles de transactions Edifact a été atteinte pour les paramètres Invité.</span><span class="sxs-lookup"><span data-stu-id="e5043-102">Max limit of acceptable Edifact transaction set control number has reached for Guest settings</span></span>
## <a name="details"></a><span data-ttu-id="e5043-103">Détails</span><span class="sxs-lookup"><span data-stu-id="e5043-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e5043-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e5043-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e5043-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e5043-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="e5043-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e5043-106">Event ID</span></span>|-|  
|<span data-ttu-id="e5043-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e5043-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e5043-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="e5043-108"> EDI</span></span>|  
|<span data-ttu-id="e5043-109">Composant</span><span class="sxs-lookup"><span data-stu-id="e5043-109">Component</span></span>|<span data-ttu-id="e5043-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="e5043-110">EDI Engine</span></span>|  
|<span data-ttu-id="e5043-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e5043-111">Symbolic Name</span></span>|<span data-ttu-id="e5043-112">GlobalEdifactUnhNumberError</span><span class="sxs-lookup"><span data-stu-id="e5043-112">GlobalEdifactUnhNumberError</span></span>|  
|<span data-ttu-id="e5043-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e5043-113">Message Text</span></span>|<span data-ttu-id="e5043-114">La limite maximale du numéro de contrôle jeu de transactions Edifact acceptable a atteint pour les paramètres invité.</span><span class="sxs-lookup"><span data-stu-id="e5043-114">Max limit of acceptable Edifact transaction set control number has reached for Guest settings.</span></span> <span data-ttu-id="e5043-115">Pour réinitialiser le compteur, accédez à la Configuration globale dans l'écran sur le rôle de récepteur, champ UNH 1 dans le gestionnaire d'accord partenaire</span><span class="sxs-lookup"><span data-stu-id="e5043-115">Reset counter by  navigating to Global configuration receiver role screen, field UNH 1 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e5043-116">Explication</span><span class="sxs-lookup"><span data-stu-id="e5043-116">Explanation</span></span>  
 <span data-ttu-id="e5043-117">Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu traiter l'échange sortant, car le nombre de contrôle d'ensembles de transactions du champ UNH1 défini dans les paramètres globaux, notamment le numéro de référence du champ UNH1.2, était supérieur à la valeur maximum autorisée.</span><span class="sxs-lookup"><span data-stu-id="e5043-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing interchange because the transaction set control number in the UNH1 field specified in the global settings, specifically the reference number in field UNH1.2, was greater than the maximum allowable value.</span></span> <span data-ttu-id="e5043-118">La valeur maximum autorisée pour le numéro de contrôle du groupe dépend des valeurs des trois champs dans UNH1.</span><span class="sxs-lookup"><span data-stu-id="e5043-118">The maximum allowable value for the group control number depends upon the values of the three fields in UNH1.</span></span> <span data-ttu-id="e5043-119">Le numéro de référence (champ UNH1.2) peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13 (respectivement, champs UNH1.1 et UNH1.3). Les trois champs combinés peuvent contenir jusqu'à 14 caractères.</span><span class="sxs-lookup"><span data-stu-id="e5043-119">The maximum number of characters is 14 for the reference number in field UNH1.2, 13 for the prefix in UNH1.1 and 13 for the suffix in UNH1.3, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e5043-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e5043-120">User Action</span></span>  
 <span data-ttu-id="e5043-121">Pour résoudre cette erreur, rétablissez le champ du numéro de référence (UNH1.2) du numéro de contrôle du document informatisé en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="e5043-121">To resolve this error, reset the reference number field (UNH1.2) of the transaction set control number, as follows:</span></span>  
  
1.  <span data-ttu-id="e5043-122">Dans la boîte de dialogue Propriétés globales EDI, ouvrez la page Définition des segments UNH.</span><span class="sxs-lookup"><span data-stu-id="e5043-122">In the EDI Global Properties dialog box, open the UNH Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="e5043-123">Cliquez sur le champ d'édition associé au champ UNH1.</span><span class="sxs-lookup"><span data-stu-id="e5043-123">Click the Edit field associated with the UNH1 field.</span></span>  
  
3.  <span data-ttu-id="e5043-124">Définissez le champ du milieu associé au numéro de contrôle du groupe (le numéro de référence dans UNH1.2) sur une nouvelle valeur, en faisant en sorte que le champ présente un nombre acceptable de chiffres.</span><span class="sxs-lookup"><span data-stu-id="e5043-124">Set the middle field of the group control number (the reference number in UNH1.2) to a new value such that the field has an acceptable number of digits.</span></span>
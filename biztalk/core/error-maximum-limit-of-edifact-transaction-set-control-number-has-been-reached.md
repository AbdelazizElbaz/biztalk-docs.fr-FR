---
title: "Génération de l’accusé de réception a échoué car la limite maximale du numéro de contrôle de jeu de transactions Edifact a été atteinte pour les paramètres de tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcbb6374-0403-42b0-892b-b35157a2c74a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1879d55de163615d5a4fab19cd50839e7ab2b17f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="acknowledgement-generation-has-failed-as-maximum-limit-of-edifact-transaction-set-control-number-has-been-reached-for-party-settings"></a><span data-ttu-id="c40bb-102">Un accusé de réception n'a pas pu être généré car la limite maximale du numéro de contrôle d'un document informatisé EDIFACT a été atteinte pour les paramètres du tiers</span><span class="sxs-lookup"><span data-stu-id="c40bb-102">Acknowledgement generation has failed as maximum limit of Edifact transaction set control number has been reached for party settings</span></span>
## <a name="details"></a><span data-ttu-id="c40bb-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c40bb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c40bb-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c40bb-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c40bb-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c40bb-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c40bb-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c40bb-106">Event ID</span></span>|-|  
|<span data-ttu-id="c40bb-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c40bb-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="c40bb-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c40bb-108"> EDI</span></span>|  
|<span data-ttu-id="c40bb-109">Composant</span><span class="sxs-lookup"><span data-stu-id="c40bb-109">Component</span></span>|<span data-ttu-id="c40bb-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="c40bb-110">EDI Engine</span></span>|  
|<span data-ttu-id="c40bb-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c40bb-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="c40bb-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c40bb-112">Message Text</span></span>|<span data-ttu-id="c40bb-113">Un accusé de réception n'a pas pu être généré car la limite maximale du nombre de contrôle d'ensembles de transactions Edifact a été atteinte pour le tiers {0}.</span><span class="sxs-lookup"><span data-stu-id="c40bb-113">Acknowledgement generation has failed as max limit of acceptable Edifact transaction set control number has reached for party {0}.</span></span> <span data-ttu-id="c40bb-114">Pour réinitialiser le compteur, accédez au tiers dans l'écran du rôle d'émetteur, champ UNH 1 dans le gestionnaire d'accord partenaire.</span><span class="sxs-lookup"><span data-stu-id="c40bb-114">Reset counter by navigating to Party in sender role screen, field UNH 1 in Partner Agreement manager.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c40bb-115">Explication</span><span class="sxs-lookup"><span data-stu-id="c40bb-115">Explanation</span></span>  
 <span data-ttu-id="c40bb-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu générer un accusé de réception pour l'échange EDIFACT, car le numéro de contrôle qu'il a entré dans le numéro de référence du document informatisé (UNH1) de l'accusé de réception est supérieur à la valeur maximale autorisée pour UNH1.</span><span class="sxs-lookup"><span data-stu-id="c40bb-116">This Error/Warning/Information event indicates that BizTalk Server could not generate an acknowledgment to the EDIFACT interchange because the control number that it entered in the Transaction set reference number (UNH1) of the acknowledgment is greater than the maximum value allowed for UNH1.</span></span> <span data-ttu-id="c40bb-117">Dans cette instance, BizTalk Server a créé l'accusé de réception à l'aide des propriétés de tiers EDI.</span><span class="sxs-lookup"><span data-stu-id="c40bb-117">In this instance, BizTalk Server used the EDI party properties to create the acknowledgment.</span></span>  
  
 <span data-ttu-id="c40bb-118">La valeur maximale du numéro de référence du document informatisé dépend du nombre de chiffres utilisés pour le numéro de référence.</span><span class="sxs-lookup"><span data-stu-id="c40bb-118">The maximum value of the transaction set reference number depends upon the number of digits used for the reference number.</span></span> <span data-ttu-id="c40bb-119">Le numéro de référence peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13. Les trois champs combinés peuvent contenir jusqu'à 14 caractères.</span><span class="sxs-lookup"><span data-stu-id="c40bb-119">The maximum number of characters is 14 for the reference number, 13 for the prefix and suffix, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c40bb-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c40bb-120">User Action</span></span>  
 <span data-ttu-id="c40bb-121">Pour résoudre cette erreur, dans la page Définition des segments UNG et UNH, rétablissez le champ du numéro de référence (UNH1.2) du numéro de référence du document informatisé (UNH1) sur une valeur inférieure à la limite maximale.</span><span class="sxs-lookup"><span data-stu-id="c40bb-121">To resolve this error, reset the reference number field (UNH1.2) of the Transaction set reference number (UNH1) in the UNG and UNH Segment Definition Page to a value that is lower than the maximum limit.</span></span> <span data-ttu-id="c40bb-122">Définissez cette propriété dans la boîte de dialogue Propriétés EDI dans la console Administration de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c40bb-122">Set this property in the EDI Properties dialog box in the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Administration Console.</span></span>
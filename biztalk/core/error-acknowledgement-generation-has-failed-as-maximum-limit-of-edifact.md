---
title: "Génération de l’accusé de réception a échoué car la limite maximale du numéro de contrôle de jeu de transactions Edifact a été atteinte pour les paramètres globaux | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6adc02d7-ebc4-4da0-a19a-3a423d63499d
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5e8bf660045bbfd1fb105f2538605302b08ab95
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="acknowledgement-generation-has-failed-as-maximum-limit-of-edifact-transaction-set-control-number-has-been-reached-for-global-settings"></a><span data-ttu-id="2f52f-102">Un accusé de réception n'a pas pu être généré car la limite maximale du numéro de contrôle d'un document informatisé EDIFACT a été atteinte pour les paramètres globaux.</span><span class="sxs-lookup"><span data-stu-id="2f52f-102">Acknowledgement generation has failed as maximum limit of Edifact transaction set control number has been reached for global settings</span></span>
## <a name="details"></a><span data-ttu-id="2f52f-103">Détails</span><span class="sxs-lookup"><span data-stu-id="2f52f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2f52f-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="2f52f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="2f52f-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="2f52f-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="2f52f-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="2f52f-106">Event ID</span></span>|-|  
|<span data-ttu-id="2f52f-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="2f52f-107">Event Source</span></span>|<span data-ttu-id="2f52f-108">EDI de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2f52f-108">BizTalk Server EDI</span></span>|  
|<span data-ttu-id="2f52f-109">Composant</span><span class="sxs-lookup"><span data-stu-id="2f52f-109">Component</span></span>|<span data-ttu-id="2f52f-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="2f52f-110">EDI Engine</span></span>|  
|<span data-ttu-id="2f52f-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="2f52f-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="2f52f-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="2f52f-112">Message Text</span></span>|<span data-ttu-id="2f52f-113">Un accusé de réception n'a pas pu être généré car la limite maximale du numéro de contrôle du document informatisé EDIFACT acceptable a été atteinte pour les paramètres Invité.</span><span class="sxs-lookup"><span data-stu-id="2f52f-113">Acknowledgement generation has failed as max limit of acceptable Edifact transaction set control number has reached for Guest settings.</span></span> <span data-ttu-id="2f52f-114">Réinitialisez le compteur en naviguant jusqu'au champ UNH 1 de l'écran du rôle de l'expéditeur de la configuration globale dans le gestionnaire d'accords partenaires.</span><span class="sxs-lookup"><span data-stu-id="2f52f-114">Reset counter by navigating to Global configuration sender role screen, field UNH 1 in Partner Agreement manager.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2f52f-115">Explication</span><span class="sxs-lookup"><span data-stu-id="2f52f-115">Explanation</span></span>  
 <span data-ttu-id="2f52f-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu générer un accusé de réception pour l'échange EDIFACT, car le numéro de contrôle qu'il a entré dans le numéro de référence du document informatisé (UNH1) de l'accusé de réception est supérieur à la valeur maximale autorisée pour UNH1.</span><span class="sxs-lookup"><span data-stu-id="2f52f-116">This Error/Warning/Information event indicates that BizTalk Server could not generate an acknowledgment to the EDIFACT interchange because the control number that it entered in the Transaction set reference number (UNH1) of the acknowledgment is greater than the maximum value allowed for UNH1.</span></span> <span data-ttu-id="2f52f-117">Dans cette instance, BizTalk Server a créé l'accusé de réception à l'aide des propriétés globales EDI.</span><span class="sxs-lookup"><span data-stu-id="2f52f-117">In this instance, BizTalk Server used the EDI global properties to create the acknowledgment.</span></span>  
  
 <span data-ttu-id="2f52f-118">La valeur maximale du numéro de référence du document informatisé dépend du nombre de chiffres utilisés pour le numéro de référence.</span><span class="sxs-lookup"><span data-stu-id="2f52f-118">The maximum value of the transaction set reference number depends upon the number of digits used for the reference number.</span></span> <span data-ttu-id="2f52f-119">Le numéro de référence peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13. Les trois champs combinés peuvent contenir jusqu'à 14 caractères.</span><span class="sxs-lookup"><span data-stu-id="2f52f-119">The maximum number of characters is 14 for the reference number, 13 for the prefix and suffix, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2f52f-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="2f52f-120">User Action</span></span>  
 <span data-ttu-id="2f52f-121">Pour résoudre cette erreur, dans la page Définition des segments UNG et UNH, rétablissez le champ du numéro de référence (UNH1.2) du numéro de référence du document informatisé (UNH1) sur une valeur inférieure à la limite maximale.</span><span class="sxs-lookup"><span data-stu-id="2f52f-121">To resolve this error, reset the reference number field (UNH1.2) of the Transaction set reference number (UNH1) in the UNG and UNH Segment Definition Page to a value that is lower than the maximum limit.</span></span> <span data-ttu-id="2f52f-122">Définissez cette propriété dans la boîte de dialogue Propriétés globales EDI dans la Console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2f52f-122">Set this property in the EDI Global Properties dialog box in the BizTalk Server Administration Console.</span></span>
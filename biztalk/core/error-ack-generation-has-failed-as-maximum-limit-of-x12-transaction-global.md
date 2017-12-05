---
title: "Génération de l’erreur-accusé de réception a échoué car la limite maximale de X12 transaction globale | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bbcae14-6e5c-4f79-87c6-311b4b54c7ff
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1eaef5e736ad01a9b49a3b46188b85b85a97e06
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="error-ack-generation-has-failed-as-maximum-limit-of-x12-transaction-global"></a><span data-ttu-id="c2f6b-102">Génération de l’erreur-accusé de réception a échoué car la limite maximale de X12 transactions globales</span><span class="sxs-lookup"><span data-stu-id="c2f6b-102">Error-Ack generation has failed as maximum limit of X12 transaction-global</span></span>
## <a name="details"></a><span data-ttu-id="c2f6b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c2f6b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c2f6b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c2f6b-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c2f6b-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c2f6b-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c2f6b-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c2f6b-106">Event ID</span></span>|-|  
|<span data-ttu-id="c2f6b-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c2f6b-107">Event Source</span></span>|<span data-ttu-id="c2f6b-108">EDI de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c2f6b-108">BizTalk Server EDI</span></span>|  
|<span data-ttu-id="c2f6b-109">Composant</span><span class="sxs-lookup"><span data-stu-id="c2f6b-109">Component</span></span>|<span data-ttu-id="c2f6b-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="c2f6b-110">EDI Engine</span></span>|  
|<span data-ttu-id="c2f6b-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c2f6b-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="c2f6b-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c2f6b-112">Message Text</span></span>|<span data-ttu-id="c2f6b-113">Un accusé de réception n'a pas pu être généré car la limite maximale du numéro de contrôle acceptable du document informatisé X12 a été atteinte pour les paramètres Invité.</span><span class="sxs-lookup"><span data-stu-id="c2f6b-113">Acknowledgement generation has failed as max limit of acceptable X12 transaction set control number has reached for Guest settings.</span></span> <span data-ttu-id="c2f6b-114">Réinitialisez le compteur en naviguant jusqu'au champ ST 2 de l'écran du rôle de l'expéditeur de la configuration globale, dans le gestionnaire d'accords partenaires</span><span class="sxs-lookup"><span data-stu-id="c2f6b-114">Reset counter by navigating to Global configuration sender role screen, field ST 2 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c2f6b-115">Explication</span><span class="sxs-lookup"><span data-stu-id="c2f6b-115">Explanation</span></span>  
 <span data-ttu-id="c2f6b-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu générer un accusé de réception pour l'échange X12, car le numéro de contrôle qu'il a entré dans le numéro de contrôle du document informatisé (ST2) de l'accusé de réception est supérieur à la valeur maximale autorisée pour ST2.</span><span class="sxs-lookup"><span data-stu-id="c2f6b-116">This Error/Warning/Information event indicates that BizTalk Server could not generate an acknowledgment to the X12 interchange because the control number that it entered in the Transaction set control number (ST2) of the acknowledgment is greater than the maximum value allowed for ST2.</span></span> <span data-ttu-id="c2f6b-117">Dans cette instance, BizTalk Server a créé l'accusé de réception à l'aide des propriétés globales EDI.</span><span class="sxs-lookup"><span data-stu-id="c2f6b-117">In this instance, BizTalk Server used the EDI global properties to create the acknowledgment.</span></span>  
  
 <span data-ttu-id="c2f6b-118">La valeur maximale du numéro de contrôle du document informatisé dépend du nombre de chiffres utilisés pour le numéro de contrôle.</span><span class="sxs-lookup"><span data-stu-id="c2f6b-118">The maximum value of the transaction set control number depends upon the number of digits used for the control number.</span></span> <span data-ttu-id="c2f6b-119">La longueur maximale des trois champs réunis est de 9. La longueur maximale des champs du préfixe et du suffixe est de 8.</span><span class="sxs-lookup"><span data-stu-id="c2f6b-119">The maximum length of all three fields is 9; the maximum length of the prefix and suffix fields is 8.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c2f6b-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c2f6b-120">User Action</span></span>  
 <span data-ttu-id="c2f6b-121">Pour résoudre cette erreur, dans la page Définition des segments GS et ST, rétablissez le champ du numéro de contrôle (ST2.2) du numéro de contrôle du document informatisé (ST2) sur une valeur inférieure à la limite maximale.</span><span class="sxs-lookup"><span data-stu-id="c2f6b-121">To resolve this error, reset the control number field (ST2.2) of the Transaction set control number (ST2) in the GS and ST Segment Definition Page to a value that is lower than the maximum limit.</span></span> <span data-ttu-id="c2f6b-122">Définissez cette propriété dans la boîte de dialogue Propriétés globales EDI dans la Console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c2f6b-122">Set this property in the EDI Global Properties dialog box in the BizTalk Server Administration Console.</span></span>
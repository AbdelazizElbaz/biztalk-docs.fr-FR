---
title: "Contrôle séquence du numéro de l’échange pour le partenaire et TPA | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e77c0574-bc51-4690-a7f6-5702f6486f05
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4744a8db00985db3e85c1cb8843f07b3488544b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interchange-control-number-sequence-exhausted-for-partner-and-tpa"></a><span data-ttu-id="a69ab-102">La séquence du numéro de contrôle de l'échange pour le partenaire et l'accord de partenariat commercial est épuisée</span><span class="sxs-lookup"><span data-stu-id="a69ab-102">Interchange control number sequence exhausted for Partner and TPA</span></span>
## <a name="details"></a><span data-ttu-id="a69ab-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a69ab-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a69ab-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a69ab-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a69ab-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a69ab-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a69ab-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a69ab-106">Event ID</span></span>|-|  
|<span data-ttu-id="a69ab-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a69ab-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a69ab-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a69ab-108"> EDI</span></span>|  
|<span data-ttu-id="a69ab-109">Composant</span><span class="sxs-lookup"><span data-stu-id="a69ab-109">Component</span></span>|<span data-ttu-id="a69ab-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="a69ab-110">EDI Engine</span></span>|  
|<span data-ttu-id="a69ab-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a69ab-111">Symbolic Name</span></span>|<span data-ttu-id="a69ab-112">EdiControlNumberExhaustedForParty</span><span class="sxs-lookup"><span data-stu-id="a69ab-112">EdiControlNumberExhaustedForParty</span></span>|  
|<span data-ttu-id="a69ab-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a69ab-113">Message Text</span></span>|<span data-ttu-id="a69ab-114">Séquence du numéro de contrôle échange atteint pour le partenaire « {{1} » pour la « {{2} » est Épuisée.</span><span class="sxs-lookup"><span data-stu-id="a69ab-114">Interchange control number sequence exhausted for Partner '{1}' for the TPA '{2}'.</span></span> <span data-ttu-id="a69ab-115">Rétablissez la séquence dans {{2} - propriétés EDI à l’aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a69ab-115">Reset the sequence in {2} - EDI Properties using BizTalk Server Administration.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a69ab-116">Explication</span><span class="sxs-lookup"><span data-stu-id="a69ab-116">Explanation</span></span>  
 <span data-ttu-id="a69ab-117">Cet événement d’erreur/avertissement/Information indique que BizTalk Server n’a pas pu traiter le document, car la plage de contrôle d’échange est épuisée pour l’accord dans {{2}.</span><span class="sxs-lookup"><span data-stu-id="a69ab-117">This Error/Warning/Information event indicates BizTalk Server was not able to process the document because the Interchange control range has been used up for the agreement in {2}.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a69ab-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a69ab-118">User Action</span></span>  
 <span data-ttu-id="a69ab-119">Pour résoudre cette erreur, cochez la case à cocher pour rétablir le numéro de contrôle de l’accord {2} ou augmentez la plage de numéros de contrôle ou le bouton Réinitialiser par rapport à la spécification de plage numéro de contrôle d’accès dans l’accord.</span><span class="sxs-lookup"><span data-stu-id="a69ab-119">To resolve this error, please tick the checkbox to reset the control number for the {2} agreement or increase the control number range or hit the reset button against the control number range specification in the agreement.</span></span>
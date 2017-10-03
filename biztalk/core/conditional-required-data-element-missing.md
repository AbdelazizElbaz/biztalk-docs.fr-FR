---
title: "Obligatoire conditionnel manquant dans un élément données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5105c03-fa26-4c38-a276-c656f3076d5f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d77a25e60af0d8287515d6fb3a7e2797d5af0b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="conditional-required-data-element-missing"></a><span data-ttu-id="637a2-102">Élément de données obligatoire conditionnel manquant</span><span class="sxs-lookup"><span data-stu-id="637a2-102">Conditional required data element missing</span></span>
## <a name="details"></a><span data-ttu-id="637a2-103">Détails</span><span class="sxs-lookup"><span data-stu-id="637a2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="637a2-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="637a2-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="637a2-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="637a2-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="637a2-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="637a2-106">Event ID</span></span>|-|  
|<span data-ttu-id="637a2-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="637a2-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="637a2-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="637a2-108"> EDI</span></span>|  
|<span data-ttu-id="637a2-109">Composant</span><span class="sxs-lookup"><span data-stu-id="637a2-109">Component</span></span>|<span data-ttu-id="637a2-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="637a2-110">EDI Engine</span></span>|  
|<span data-ttu-id="637a2-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="637a2-111">Symbolic Name</span></span>|<span data-ttu-id="637a2-112">X12DeConditionalRequiredDataElementMissingDescription</span><span class="sxs-lookup"><span data-stu-id="637a2-112">X12DeConditionalRequiredDataElementMissingDescription</span></span>|  
|<span data-ttu-id="637a2-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="637a2-113">Message Text</span></span>|<span data-ttu-id="637a2-114">Élément de données obligatoire conditionnel manquant</span><span class="sxs-lookup"><span data-stu-id="637a2-114">Conditional required data element missing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="637a2-115">Explication</span><span class="sxs-lookup"><span data-stu-id="637a2-115">Explanation</span></span>  
 <span data-ttu-id="637a2-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI n'a pas pu traiter un échange entrant car un élément de données requis par la règle X12ConditionDesignatorX n'existe pas dans l'échange.</span><span class="sxs-lookup"><span data-stu-id="637a2-116">This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming interchange because a data element that is required by the X12ConditionDesignatorX rule does not exist in the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="637a2-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="637a2-117">User Action</span></span>  
 <span data-ttu-id="637a2-118">Cette erreur est probablement due à un problème avec l'échange entrant, et non à la configuration ou au fonctionnement de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="637a2-118">This error is likely an issue with the incoming interchange, not with the configuration or operation of BizTalk Server.</span></span> <span data-ttu-id="637a2-119">Pour résoudre cette erreur, contactez l'expéditeur de l'échange et demandez-lui de modifier les caractères utilisés dans l'échange ou le jeu de caractère identifié dans le champ UNB1.1 afin qu'ils correspondent.</span><span class="sxs-lookup"><span data-stu-id="637a2-119">To resolve this error, contact the sender of the interchange and indicate that they need to change either the characters used in the interchange or the character set identified in field UNB1.1 so that they match.</span></span>
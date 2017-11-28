---
title: "Une règle de validation de champ a violé entre | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d606a80-9046-4572-9cfb-a3434ed8073e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ba6e7b5e81caf3b091c146755ba37896fb1120b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cross-field-validation-rule-violated"></a><span data-ttu-id="540eb-102">Règle de validation de champ croisée non respectée</span><span class="sxs-lookup"><span data-stu-id="540eb-102">Cross field validation rule violated</span></span>
## <a name="details"></a><span data-ttu-id="540eb-103">Détails</span><span class="sxs-lookup"><span data-stu-id="540eb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="540eb-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="540eb-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="540eb-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="540eb-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="540eb-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="540eb-106">Event ID</span></span>|-|  
|<span data-ttu-id="540eb-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="540eb-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="540eb-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="540eb-108"> EDI</span></span>|  
|<span data-ttu-id="540eb-109">Composant</span><span class="sxs-lookup"><span data-stu-id="540eb-109">Component</span></span>|<span data-ttu-id="540eb-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="540eb-110">EDI Engine</span></span>|  
|<span data-ttu-id="540eb-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="540eb-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="540eb-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="540eb-112">Message Text</span></span>|<span data-ttu-id="540eb-113">Règle de validation de champ croisée non respectée</span><span class="sxs-lookup"><span data-stu-id="540eb-113">Cross field validation rule violated</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="540eb-114">Explication</span><span class="sxs-lookup"><span data-stu-id="540eb-114">Explanation</span></span>  
 <span data-ttu-id="540eb-115">Cet événement de type erreur/avertissement/information indique que la validation des champs croisés de l'échange X12 a échoué dans le pipeline de réception ou celui d'envoi.</span><span class="sxs-lookup"><span data-stu-id="540eb-115">This Error/Warning/Information event indicates that the X12 interchange failed cross-field validation in the receive pipeline or the send pipeline.</span></span> <span data-ttu-id="540eb-116">Cela signifie que l'indicateur X12ConditionDesignator_Check est défini sur Oui et qu'au moins un élément de l'échange a échoué au niveau d'une règle identifiée par le préfixe X12ConditionDesignatorX.</span><span class="sxs-lookup"><span data-stu-id="540eb-116">This indicates that the X12ConditionDesignator_Check flag is set to "Yes", and that at least one element in the interchange failed a rule identified by the prefix "X12ConditionDesignatorX".</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="540eb-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="540eb-117">User Action</span></span>  
 <span data-ttu-id="540eb-118">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="540eb-118">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="540eb-119">Identifiez l'élément de données ayant échoué au niveau de la règle de validation des champs croisés.</span><span class="sxs-lookup"><span data-stu-id="540eb-119">Identify which data element failed a cross-field validation rule.</span></span> <span data-ttu-id="540eb-120">Contactez l'expéditeur de l'échange et indiquez que la règle doit être respectée lors de la création de l'échange.</span><span class="sxs-lookup"><span data-stu-id="540eb-120">Contact the sender of the interchange and indicate that the rule must be followed when creating the interchange.</span></span>  
  
-   <span data-ttu-id="540eb-121">Ouvrez le schéma de l'échange, puis définissez l'indicateur X12ConditionDesignator_Check sur Non pour l'élément de données dont la validation a échoué.</span><span class="sxs-lookup"><span data-stu-id="540eb-121">Open the schema for the interchange, and set the X12ConditionDesignator_Check flag for the data element that failed validation to "No".</span></span>
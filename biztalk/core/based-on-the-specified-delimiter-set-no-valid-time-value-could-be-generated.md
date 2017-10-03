---
title: "En fonction de l’ensemble de délimiteurs spécifié, aucune valeur d’heure valide pu être généré. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7e22958-e1fa-474d-85a2-aa69e05b7228
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00b8b06922109ae5817c67b26f1a23977d1b607b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="based-on-the-specified-delimiter-set-no-valid-time-value-could-be-generated"></a><span data-ttu-id="46bba-102">Sur la base de l'ensemble de délimiteurs spécifié, aucune valeur d'heure valide n'a pu être créée</span><span class="sxs-lookup"><span data-stu-id="46bba-102">Based on the specified delimiter set, no valid Time value could be generated</span></span>
## <a name="details"></a><span data-ttu-id="46bba-103">Détails</span><span class="sxs-lookup"><span data-stu-id="46bba-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46bba-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="46bba-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="46bba-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="46bba-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="46bba-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="46bba-106">Event ID</span></span>|-|  
|<span data-ttu-id="46bba-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="46bba-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="46bba-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="46bba-108"> EDI</span></span>|  
|<span data-ttu-id="46bba-109">Composant</span><span class="sxs-lookup"><span data-stu-id="46bba-109">Component</span></span>|<span data-ttu-id="46bba-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="46bba-110">EDI Engine</span></span>|  
|<span data-ttu-id="46bba-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="46bba-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="46bba-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="46bba-112">Message Text</span></span>|<span data-ttu-id="46bba-113">Sur la base de l'ensemble de délimiteurs spécifié, aucune valeur d'heure valide n'a pu être créée.</span><span class="sxs-lookup"><span data-stu-id="46bba-113">Based on the specified delimiter set, no valid Time value could be generated.</span></span> <span data-ttu-id="46bba-114">Utilisez un autre ensemble de délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="46bba-114">Please use another delimiter set.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="46bba-115">Explication</span><span class="sxs-lookup"><span data-stu-id="46bba-115">Explanation</span></span>  
 <span data-ttu-id="46bba-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi EDI n'a pas pu générer une valeur d'heure valide, car un caractère utilisé dans le champ d'heure de l'échange sortant est identique à un caractère de séparation.</span><span class="sxs-lookup"><span data-stu-id="46bba-116">This Error/Warning/Information event indicates that the EDI send pipeline could not generate a valid time value because a character used in a time field of the outgoing interchange was the same as a separator character.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="46bba-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="46bba-117">User Action</span></span>  
 <span data-ttu-id="46bba-118">Pour résoudre cette erreur, modifiez les valeurs de séparation utilisées par le pipeline d'envoi EDI pour créer un message afin qu'aucun caractère de séparation ne soit identique à un caractère utilisé dans un champ d'heure.</span><span class="sxs-lookup"><span data-stu-id="46bba-118">To resolve this error, change the separator values used by the EDI send pipeline to create a message so that no separator character is the same as a character used in a time field.</span></span> <span data-ttu-id="46bba-119">Procédez de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="46bba-119">Do one of the following:</span></span>  
  
-   <span data-ttu-id="46bba-120">Pour un échange X12 envoyé à un tiers résolu, modifiez les paramètres de séparation dans la page Définition des segments ISA pour le tiers en tant que récepteur d'échanges.</span><span class="sxs-lookup"><span data-stu-id="46bba-120">For an X12 interchange being sent to a resolved party, change the separator settings in the ISA Segment Definition page for the party as interchange receiver.</span></span>  
  
-   <span data-ttu-id="46bba-121">Pour un échange X12 envoyé à un tiers qui n'a pas été résolu, modifiez les paramètres de séparation dans la page des propriétés globales Définition des segments ISA.</span><span class="sxs-lookup"><span data-stu-id="46bba-121">For an X12 interchange being sent to a party that has not been resolved, change the separator settings in the ISA Segment Definition global property page.</span></span>  
  
-   <span data-ttu-id="46bba-122">Pour un échange EDIFACT envoyé à un tiers résolu, modifiez les paramètres de séparation dans la page Définition des segments ISA pour le tiers considéré comme récepteur des échanges.</span><span class="sxs-lookup"><span data-stu-id="46bba-122">For an EDIFACT interchange being sent to a resolved party, change the separator settings in the UNA Segment Definition page for the party as interchange receiver.</span></span>  
  
-   <span data-ttu-id="46bba-123">Pour un échange EDIFACT envoyé à un tiers qui n'a pas été résolu, modifiez les paramètres de séparation dans la page des propriétés globales Définition des segments UNA.</span><span class="sxs-lookup"><span data-stu-id="46bba-123">For an EDIFACT interchange being sent to a party that has not been resolved, change the separator settings in the UNA Segment Definition global property page.</span></span>
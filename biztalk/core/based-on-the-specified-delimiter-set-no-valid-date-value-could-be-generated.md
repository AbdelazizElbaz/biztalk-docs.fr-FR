---
title: "En fonction de l’ensemble de délimiteurs spécifié, aucune valeur de Date valide pu être généré. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdd157c0-9a0d-421b-8350-aa1263126ca0
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 747d00c7628853d3a99f007f70701311d25c22bb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="based-on-the-specified-delimiter-set-no-valid-date-value-could-be-generated"></a><span data-ttu-id="64ea3-102">Sur la base de l'ensemble de délimiteurs spécifié, aucune valeur de date valide n'a pu être créée</span><span class="sxs-lookup"><span data-stu-id="64ea3-102">Based on the specified delimiter set, no valid Date value could be generated</span></span>
## <a name="details"></a><span data-ttu-id="64ea3-103">Détails</span><span class="sxs-lookup"><span data-stu-id="64ea3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="64ea3-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="64ea3-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="64ea3-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="64ea3-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="64ea3-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="64ea3-106">Event ID</span></span>|-|  
|<span data-ttu-id="64ea3-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="64ea3-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="64ea3-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="64ea3-108"> EDI</span></span>|  
|<span data-ttu-id="64ea3-109">Composant</span><span class="sxs-lookup"><span data-stu-id="64ea3-109">Component</span></span>|<span data-ttu-id="64ea3-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="64ea3-110">EDI Engine</span></span>|  
|<span data-ttu-id="64ea3-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="64ea3-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="64ea3-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="64ea3-112">Message Text</span></span>|<span data-ttu-id="64ea3-113">Sur la base de l'ensemble de délimiteurs spécifié, aucune valeur de date valide n'a pu être créée.</span><span class="sxs-lookup"><span data-stu-id="64ea3-113">Based on the specified delimiter set, no valid Date value could be generated.</span></span> <span data-ttu-id="64ea3-114">Utilisez un autre ensemble de délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="64ea3-114">Please use another delimiter set.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="64ea3-115">Explication</span><span class="sxs-lookup"><span data-stu-id="64ea3-115">Explanation</span></span>  
 <span data-ttu-id="64ea3-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi EDI n'a pas pu générer une valeur de date valide, car un caractère utilisé dans le champ de date de l'échange sortant est identique à un caractère de séparation.</span><span class="sxs-lookup"><span data-stu-id="64ea3-116">This Error/Warning/Information event indicates that the EDI send pipeline could not generate a valid date value because a character used in a Date field of the outgoing interchange was the same as a separator character.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="64ea3-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="64ea3-117">User Action</span></span>  
 <span data-ttu-id="64ea3-118">Pour résoudre ce problème, modifiez les valeurs de séparation utilisées par le pipeline d'envoi EDI pour créer un message de manière à ce qu'aucun caractère de séparation ne soit identique à un caractère utilisé dans un champ de date de l'échange sortant.</span><span class="sxs-lookup"><span data-stu-id="64ea3-118">To resolve this error, change the separator values used by the EDI send pipeline to create a message so that no separator character will be the same as a character used in a Date field of the outgoing interchange.</span></span> <span data-ttu-id="64ea3-119">Procédez de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="64ea3-119">Do one of the following:</span></span>  
  
-   <span data-ttu-id="64ea3-120">Pour un échange X12 envoyé à un tiers résolu, modifiez les paramètres de séparation dans la page Définition des segments ISA pour le tiers en tant que récepteur d'échanges.</span><span class="sxs-lookup"><span data-stu-id="64ea3-120">For an X12 interchange being sent to a resolved party, change the separator settings in the ISA Segment Definition page for the party as interchange receiver.</span></span>  
  
-   <span data-ttu-id="64ea3-121">Pour un échange X12 envoyé à un tiers qui n'a pas été résolu, modifiez les paramètres de séparation dans la page des propriétés globales Définition des segments ISA.</span><span class="sxs-lookup"><span data-stu-id="64ea3-121">For an X12 interchange being sent to a party that has not been resolved, change the separator settings in the ISA Segment Definition global property page.</span></span>  
  
-   <span data-ttu-id="64ea3-122">Pour un échange EDIFACT envoyé à un tiers résolu, modifiez les paramètres de séparation dans la page Définition des segments ISA pour le tiers considéré comme récepteur des échanges.</span><span class="sxs-lookup"><span data-stu-id="64ea3-122">For an EDIFACT interchange being sent to a resolved party, change the separator settings in the UNA Segment Definition page for the party as interchange receiver.</span></span>  
  
-   <span data-ttu-id="64ea3-123">Pour un échange EDIFACT envoyé à un tiers qui n'a pas été résolu, modifiez les paramètres de séparation dans la page des propriétés globales Définition des segments UNA.</span><span class="sxs-lookup"><span data-stu-id="64ea3-123">For an EDIFACT interchange being sent to a party that has not been resolved, change the separator settings in the UNA Segment Definition global property page.</span></span>
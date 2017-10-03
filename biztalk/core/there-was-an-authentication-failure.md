---
title: "Il a été un échec d’authentification | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36524da9-da91-41e7-bf73-7781cde20c80
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 180645d30c5cccc64eacd57730539bbca220f32f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="there-was-an-authentication-failure"></a><span data-ttu-id="440d0-102">Un échec d'authentification s'est produit.</span><span class="sxs-lookup"><span data-stu-id="440d0-102">There was an authentication failure</span></span>
## <a name="details"></a><span data-ttu-id="440d0-103">Détails</span><span class="sxs-lookup"><span data-stu-id="440d0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="440d0-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="440d0-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="440d0-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="440d0-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="440d0-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="440d0-106">Event ID</span></span>|-|  
|<span data-ttu-id="440d0-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="440d0-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="440d0-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="440d0-108"> EDI</span></span>|  
|<span data-ttu-id="440d0-109">Composant</span><span class="sxs-lookup"><span data-stu-id="440d0-109">Component</span></span>|<span data-ttu-id="440d0-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="440d0-110">EDI Engine</span></span>|  
|<span data-ttu-id="440d0-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="440d0-111">Symbolic Name</span></span>|<span data-ttu-id="440d0-112">DescPartyNotFound</span><span class="sxs-lookup"><span data-stu-id="440d0-112">DescPartyNotFound</span></span>|  
|<span data-ttu-id="440d0-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="440d0-113">Message Text</span></span>|<span data-ttu-id="440d0-114">Il a été un échec d’authentification.</span><span class="sxs-lookup"><span data-stu-id="440d0-114">There was an authentication failure.</span></span> <span data-ttu-id="440d0-115">Vérifiez qu'un tiers correspondant existe pour le message en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="440d0-115">Make sure that a matching party exists for the message being processed.</span></span> <span data-ttu-id="440d0-116">Les informations de sécurité/mot de passe dans le message correspondent à la configuration du tiers</span><span class="sxs-lookup"><span data-stu-id="440d0-116">And the security/password information in the message matches the Party configuration</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="440d0-117">Explication</span><span class="sxs-lookup"><span data-stu-id="440d0-117">Explanation</span></span>  
 <span data-ttu-id="440d0-118">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car BizTalk Server n'est pas parvenu à authentifier l'expéditeur du message.</span><span class="sxs-lookup"><span data-stu-id="440d0-118">This Error/Warning/Information event indicates that the receive pipeline was unable to process the incoming interchange because BizTalk Server was unable to authenticate the sender of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="440d0-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="440d0-119">User Action</span></span>  
 <span data-ttu-id="440d0-120">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="440d0-120">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="440d0-121">Vérifiez que le qualificateur et l'identificateur de l'expéditeur dans l'en-tête de l'échange (champs ISA5 et ISA6 pour X12 ou UNB2.1 et UNB2.2 pour EDIFACT) correspondent à ceux figurant dans les propriétés d'un tiers (comme cela est défini dans la page des propriétés du traitement de l'échange de la boîte de dialogue Propriétés EDI).</span><span class="sxs-lookup"><span data-stu-id="440d0-121">Verify that the sender qualifier and identifier in the interchange header (fields ISA5 and ISA6 for X12 or UNB2.1 and UNB2.2 for EDIFACT) match the sender qualifier and identifier in the properties of a party (as defined in the Interchange Processing Properties page of the EDI Properties dialog box).</span></span>  
  
-   <span data-ttu-id="440d0-122">Vérifiez que les informations de sécurité/mot de passe dans l'en-tête de l'échange (champs ISA3 et ISA4 pour X12 ou UNB6.1 et UNB6.2 pour EDIFACT) correspondent à celles figurant dans les propriétés d'un tiers (comme cela est défini dans la page des propriétés du traitement de l'échange de la boîte de dialogue Propriétés EDI).</span><span class="sxs-lookup"><span data-stu-id="440d0-122">Verify that the security/password information in the header of the interchange (fields ISA3 and ISA4 for X12 or UNB6.1 and UNB6.2 for EDIFACT) match the security/password information in the properties of a party (as defined in the Interchange Processing Properties page of the EDI Properties dialog box).</span></span>
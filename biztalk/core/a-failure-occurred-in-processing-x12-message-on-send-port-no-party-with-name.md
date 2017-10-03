---
title: "Une erreur s’est produite lors du traitement de X12 message sur le port d’envoi : tiers non ayant le nom | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af059a04-3b7c-48e2-a3bf-48ad62deb139
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0e620797d45fb0b3d2ef929865a4b8bb98d2d90
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-failure-occurred-in-processing-x12-message-on-send-port-no-party-with-name"></a><span data-ttu-id="7983c-102">Une erreur s’est produite lors du traitement de X12 message sur le port d’envoi : tiers non ayant le nom</span><span class="sxs-lookup"><span data-stu-id="7983c-102">A failure occurred in processing X12 message on send port: No Party with name</span></span>
## <a name="details"></a><span data-ttu-id="7983c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7983c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7983c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7983c-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7983c-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7983c-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="7983c-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7983c-106">Event ID</span></span>|-|  
|<span data-ttu-id="7983c-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7983c-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7983c-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="7983c-108"> EDI</span></span>|  
|<span data-ttu-id="7983c-109">Composant</span><span class="sxs-lookup"><span data-stu-id="7983c-109">Component</span></span>|<span data-ttu-id="7983c-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="7983c-110">EDI Engine</span></span>|  
|<span data-ttu-id="7983c-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7983c-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="7983c-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7983c-112">Message Text</span></span>|<span data-ttu-id="7983c-113">Un échec s'est produit lors du traitement du message X12 sur le port d'envoi {0}.</span><span class="sxs-lookup"><span data-stu-id="7983c-113">A failure occurred in processing X12 message on send port {0}.</span></span> <span data-ttu-id="7983c-114">Il n’existe aucun tiers avec {{1} du nom.</span><span class="sxs-lookup"><span data-stu-id="7983c-114">No Party exists with name {1}.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7983c-115">Explication</span><span class="sxs-lookup"><span data-stu-id="7983c-115">Explanation</span></span>  
 <span data-ttu-id="7983c-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas réussi à résoudre le tiers pour l'échange X12, car il n'a pas réussi à faire correspondre le port d'envoi abonné à l'échange au port d'envoi associé au tiers.</span><span class="sxs-lookup"><span data-stu-id="7983c-116">This Error/Warning/Information event indicates BizTalk Server was unable to resolve the party for the X12 interchange because BizTalk Server was unable to match the send port that subscribed to the interchange with the send port associated with a party.</span></span> <span data-ttu-id="7983c-117">Cette erreur se produit lorsque ni la propriété DestinationPartyName ni les propriétés du qualificateur d'expéditeur, de l'identificateur de l'expéditeur, du qualificateur du récepteur et de l'identificateur du récepteur ne sont promues. Elles ne sont donc pas disponibles pour la résolution du tiers côté envoi.</span><span class="sxs-lookup"><span data-stu-id="7983c-117">This occurs if neither the DestinationPartyName property, nor the sender qualifier, sender identifier, receiver qualifier, and receiver identifier properties, are promoted, so are unavailable for send-side party resolution.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7983c-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7983c-118">User Action</span></span>  
 <span data-ttu-id="7983c-119">Pour résoudre cette erreur, vérifiez que le port d'envoi abonné à l'échange correspond au port d'envoi associé à un tiers.</span><span class="sxs-lookup"><span data-stu-id="7983c-119">To resolve this error, ensure the send port that subscribed to the interchange matches the send port associated with a party.</span></span>
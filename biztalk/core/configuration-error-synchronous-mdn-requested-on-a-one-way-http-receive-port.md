---
title: "Erreur de configuration. Port de réception MDN synchrone demandé sur un HTTP unidirectionnel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f140c7a4-46bf-4557-9679-cdaf2fbe66f4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa49120ecbdbd0a00de1bbd6cd552f56cb626ddd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-error-synchronous-mdn-requested-on-a-one-way-http-receive-port"></a><span data-ttu-id="a1514-103">Erreur de configuration.</span><span class="sxs-lookup"><span data-stu-id="a1514-103">Configuration error.</span></span> <span data-ttu-id="a1514-104">MDN synchrone demandé sur un port de réception HTTP unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="a1514-104">Synchronous MDN requested on a one way HTTP receive Port</span></span>
## <a name="details"></a><span data-ttu-id="a1514-105">Détails</span><span class="sxs-lookup"><span data-stu-id="a1514-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a1514-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a1514-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a1514-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a1514-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a1514-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a1514-108">Event ID</span></span>|-|  
|<span data-ttu-id="a1514-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a1514-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a1514-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="a1514-110"> EDI</span></span>|  
|<span data-ttu-id="a1514-111">Composant</span><span class="sxs-lookup"><span data-stu-id="a1514-111">Component</span></span>|<span data-ttu-id="a1514-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="a1514-112">EDI Engine</span></span>|  
|<span data-ttu-id="a1514-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a1514-113">Symbolic Name</span></span>|-|  
|<span data-ttu-id="a1514-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a1514-114">Message Text</span></span>|<span data-ttu-id="a1514-115">Erreur de configuration.</span><span class="sxs-lookup"><span data-stu-id="a1514-115">Configuration error.</span></span> <span data-ttu-id="a1514-116">Port d’envoi MDN synchrone demandé sur HTTP unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="a1514-116">Synchronous MDN requested on one way HTTP send port.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a1514-117">Explication</span><span class="sxs-lookup"><span data-stu-id="a1514-117">Explanation</span></span>  
 <span data-ttu-id="a1514-118">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu renvoyer un MDN synchrone après la réception d'un message AS2 car le port de réception HTTP qui a traité le message AS2 entrant est un port unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="a1514-118">This Error/Warning/Information event indicates that BizTalk Server could not return a synchronous MDN after receiving an AS2 message because the HTTP receive port that processed the incoming AS2 message was a one-way port.</span></span> <span data-ttu-id="a1514-119">Un port de réception de requête-réponse bidirectionnel est requis pour renvoyer un MDN synchrone en réponse à un message AS2 entrant.</span><span class="sxs-lookup"><span data-stu-id="a1514-119">A two-way request-response receive port is required to return a synchronous MDN in response to an incoming AS2 message.</span></span> <span data-ttu-id="a1514-120">Dans ce cas, le MDN doit être renvoyé de manière synchrone car le message AS2 inclut l'en-tête Disposition-Notification-To, ou dans la configuration du tiers en tant qu'expéditeur du message AS2, la propriété Remplacer les propriétés du message entrant est activée, la propriété Générer le MDN est activée et la propriété Transmettre un MDN de manière asynchrone est désactivée.</span><span class="sxs-lookup"><span data-stu-id="a1514-120">In this case, the MDN must be returned synchronously because the AS2 message includes the Disposition-Notification-To header, or in the configuration for the party as an AS2 Message Sender, the Override inbound message properties property is checked, the Generate MDN property is checked, and the Transmit MDN asynchronously property is cleared.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a1514-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a1514-121">User Action</span></span>  
 <span data-ttu-id="a1514-122">Pour résoudre cette erreur, remplacez le port de réception qui reçoit le message AS2 par un port de réception de requête-réponse (et non unidirectionnel).</span><span class="sxs-lookup"><span data-stu-id="a1514-122">To resolve this error, change the receive port that is receiving the AS2 message to be a request response receive port, rather than a one-way receive port.</span></span> <span data-ttu-id="a1514-123">Définissez le pipeline d'envoi de l'emplacement de réception de requête-réponse sur AS2EdiSend pour un échange EDI, ou sur AS2Send pour un échange non-EDI.</span><span class="sxs-lookup"><span data-stu-id="a1514-123">Set the send pipeline of the request response receive location to be AS2EdiSend for an EDI interchange or AS2Send for a non-EDI interchange.</span></span>
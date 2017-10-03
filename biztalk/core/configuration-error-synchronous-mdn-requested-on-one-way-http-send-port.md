---
title: "Erreur de configuration. Port d’envoi MDN synchrone demandé sur HTTP unidirectionnel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bd38eb3-321f-4738-b35e-390f4f54673e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a0a240593aa21b102c401a2a6886ea24baa42c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-error-synchronous-mdn-requested-on-one-way-http-send-port"></a><span data-ttu-id="d1786-103">Erreur de configuration.</span><span class="sxs-lookup"><span data-stu-id="d1786-103">Configuration error.</span></span> <span data-ttu-id="d1786-104">MDN synchrone demandé sur un port d'envoi HTTP unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="d1786-104">Synchronous MDN requested on one way HTTP send port</span></span>
## <a name="details"></a><span data-ttu-id="d1786-105">Détails</span><span class="sxs-lookup"><span data-stu-id="d1786-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d1786-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="d1786-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d1786-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="d1786-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d1786-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d1786-108">Event ID</span></span>|-|  
|<span data-ttu-id="d1786-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="d1786-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d1786-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="d1786-110"> EDI</span></span>|  
|<span data-ttu-id="d1786-111">Composant</span><span class="sxs-lookup"><span data-stu-id="d1786-111">Component</span></span>|<span data-ttu-id="d1786-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="d1786-112">EDI Engine</span></span>|  
|<span data-ttu-id="d1786-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="d1786-113">Symbolic Name</span></span>|-|  
|<span data-ttu-id="d1786-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="d1786-114">Message Text</span></span>|<span data-ttu-id="d1786-115">Erreur de configuration.</span><span class="sxs-lookup"><span data-stu-id="d1786-115">Configuration error.</span></span> <span data-ttu-id="d1786-116">Port d’envoi MDN synchrone demandé sur HTTP unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="d1786-116">Synchronous MDN requested on one way HTTP send port.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d1786-117">Explication</span><span class="sxs-lookup"><span data-stu-id="d1786-117">Explanation</span></span>  
 <span data-ttu-id="d1786-118">Cet événement de type erreur/avertissement/information indique que BizTalk Server n'a pas reçu un MDN synchrone après avoir envoyé un message AS2, car le port HTTP d'envoi qui a émis le message AS2 était unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="d1786-118">This Error/Warning/Information event indicates that BizTalk Server could not receive a synchronous MDN after sending an AS2 message because the HTTP send port that sent the AS2 message was a one-way port.</span></span> <span data-ttu-id="d1786-119">Un port d'envoi sollicitation-réponse bidirectionnel est nécessaire pour traiter un MDN synchrone renvoyé en réponse à un message AS2 émis par le port.</span><span class="sxs-lookup"><span data-stu-id="d1786-119">A two-way solicit-response send port is required to process a synchronous MDN returned in response to an AS2 message sent by the port.</span></span> <span data-ttu-id="d1786-120">Dans ce cas, le MDN doit être renvoyé de façon synchrone, car dans la configuration du tiers considéré comme récepteur des messages AS2, la propriété Exiger le MDN est sélectionnée alors que la propriété Exiger le MDN asynchrone ne l'est pas.</span><span class="sxs-lookup"><span data-stu-id="d1786-120">In this case, the MDN must be returned synchronously because in the configuration for the party as an AS2 Message Receiver, the Request MDN property is checked, and the Request asynchronous MDN property is cleared.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d1786-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="d1786-121">User Action</span></span>  
 <span data-ttu-id="d1786-122">Pour résoudre cette erreur, modifiez le port d'envoi qui émet le message AS2 afin qu'il devienne un port d'envoi sollicitation-réponse statique et ne soit plus un port d'envoi unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="d1786-122">To resolve this error, change the send port that is sending the AS2 message to be a static solicit-response send port, rather than a one-way send port.</span></span> <span data-ttu-id="d1786-123">Définissez le pipeline de réception du port d'envoi sollicitation-réponse sur AS2EdiReceive pour un échange EDI ou sur AS2Receive pour un échange non-EDI.</span><span class="sxs-lookup"><span data-stu-id="d1786-123">Set the receive pipeline of the solicit-response send port to be AS2EdiReceive for an EDI interchange or AS2Receive for a non-EDI interchange.</span></span>
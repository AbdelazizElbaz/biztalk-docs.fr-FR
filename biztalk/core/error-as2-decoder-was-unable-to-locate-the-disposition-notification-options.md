---
title: "Le décodeur AS2 n’a pas pu localiser l’en-tête HTTP Disposition-Notification-Options | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6de4b9a6-17b2-4455-9dbd-a6bb69fac1d5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 966860c7f2b7b47187b861ed6b81fb14a4753872
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-as2-decoder-was-unable-to-locate-the-disposition-notification-options-http-header"></a><span data-ttu-id="c2503-102">Le décodeur AS2 n'a pas réussi à localiser l'en-tête HTTP Disposition-Notification-Options</span><span class="sxs-lookup"><span data-stu-id="c2503-102">The AS2 Decoder was unable to locate the Disposition-Notification-Options HTTP header</span></span>
## <a name="details"></a><span data-ttu-id="c2503-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c2503-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c2503-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c2503-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c2503-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c2503-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c2503-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c2503-106">Event ID</span></span>|-|  
|<span data-ttu-id="c2503-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c2503-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c2503-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c2503-108"> EDI</span></span>|  
|<span data-ttu-id="c2503-109">Composant</span><span class="sxs-lookup"><span data-stu-id="c2503-109">Component</span></span>|<span data-ttu-id="c2503-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="c2503-110">AS2 Engine</span></span>|  
|<span data-ttu-id="c2503-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c2503-111">Symbolic Name</span></span>|<span data-ttu-id="c2503-112">AS2DecoderMissingDispositionNotificationOptionsHTTPHeaderError</span><span class="sxs-lookup"><span data-stu-id="c2503-112">AS2DecoderMissingDispositionNotificationOptionsHTTPHeaderError</span></span>|  
|<span data-ttu-id="c2503-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c2503-113">Message Text</span></span>|<span data-ttu-id="c2503-114">Le décodeur AS2 n'a pas réussi à localiser l'en-tête HTTP Disposition-Notification-Options requis pour la création du MDN.</span><span class="sxs-lookup"><span data-stu-id="c2503-114">The AS2 Decoder was unable to locate the Disposition-Notification-Options HTTP header which is required for MDN generation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c2503-115">Explication</span><span class="sxs-lookup"><span data-stu-id="c2503-115">Explanation</span></span>  
 <span data-ttu-id="c2503-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu générer le MDN, car le message AS2 entrant ne comporte pas l'en-tête Disposition-Notification-Options indiquant si le MDN doit être signé et l'algorithme MIC à utiliser.</span><span class="sxs-lookup"><span data-stu-id="c2503-116">This Error/Warning/Information event indicates that the receive pipeline could not generate the MDN because the incoming AS2 message did not include the Disposition-Notification-Options header that indicates whether the MDN must be signed and which MIC algorithm must be used.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c2503-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c2503-117">User Action</span></span>  
 <span data-ttu-id="c2503-118">Pour résoudre cette erreur, demandez à l'expéditeur du message AS2 d'intégrer l'en-tête Disposition-Notification-Options dans le message, puis de le renvoyer.</span><span class="sxs-lookup"><span data-stu-id="c2503-118">To resolve this error, have the sender of the AS2 message include the Disposition-Notification-Options header in the message and then resend the message.</span></span>
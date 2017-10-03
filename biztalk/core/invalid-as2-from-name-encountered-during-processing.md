---
title: "AS2 non valide-nom rencontré lors du traitement de | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba658119-9171-4851-835c-72c188275b73
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 819d059f0d59f59164ab80eeb4501e5cd52ce7b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-as2-from-name-encountered-during-processing"></a><span data-ttu-id="86d50-102">Nom AS2-From non valide rencontré lors du traitement</span><span class="sxs-lookup"><span data-stu-id="86d50-102">Invalid AS2-From name encountered during processing</span></span>
## <a name="details"></a><span data-ttu-id="86d50-103">Détails</span><span class="sxs-lookup"><span data-stu-id="86d50-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="86d50-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="86d50-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="86d50-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="86d50-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="86d50-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="86d50-106">Event ID</span></span>|-|  
|<span data-ttu-id="86d50-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="86d50-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="86d50-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="86d50-108"> EDI</span></span>|  
|<span data-ttu-id="86d50-109">Composant</span><span class="sxs-lookup"><span data-stu-id="86d50-109">Component</span></span>|<span data-ttu-id="86d50-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="86d50-110">AS2 Engine</span></span>|  
|<span data-ttu-id="86d50-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="86d50-111">Symbolic Name</span></span>|<span data-ttu-id="86d50-112">InvalidAS2FromNameEncounteredError</span><span class="sxs-lookup"><span data-stu-id="86d50-112">InvalidAS2FromNameEncounteredError</span></span>|  
|<span data-ttu-id="86d50-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="86d50-113">Message Text</span></span>|<span data-ttu-id="86d50-114">Nom AS2-From non valide rencontré lors du traitement.</span><span class="sxs-lookup"><span data-stu-id="86d50-114">Invalid AS2-From name encountered during processing.</span></span>  <span data-ttu-id="86d50-115">Valeur : {0}</span><span class="sxs-lookup"><span data-stu-id="86d50-115">Value: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="86d50-116">Explication</span><span class="sxs-lookup"><span data-stu-id="86d50-116">Explanation</span></span>  
 <span data-ttu-id="86d50-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant ou que le pipeline d'envoi n'a pas pu traiter l'échange sortant car la valeur de l'en-tête AS2-From n'est pas conforme aux spécifications de la norme AS2 RFC 4130.</span><span class="sxs-lookup"><span data-stu-id="86d50-117">This Error/Warning/Information event indicates that either the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because the value of the AS2-From header did not conform to the specifications in AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="86d50-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="86d50-118">User Action</span></span>  
 <span data-ttu-id="86d50-119">Pour résoudre cette erreur, assurez-vous que l'en-tête AS2-From du message entrant ou sortant est conforme aux spécifications de la section 6.2 de la norme AS2 RFC 4130, puis demandez à l'expéditeur de renvoyer le message.</span><span class="sxs-lookup"><span data-stu-id="86d50-119">To resolve this error, make sure that the AS2-From header in the incoming or outgoing message conforms to the specifications in section 6.2 of AS2 RFC 4130, and then have the message resent.</span></span>
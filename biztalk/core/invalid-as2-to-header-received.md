---
title: "AS2 non valide-pour l’en-tête reçu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56cd16b3-511b-4716-8806-817f174f0b0e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 750166045224754c05e4345c2e57e16950b89c9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-as2-to-header-received"></a><span data-ttu-id="46835-102">En-tête AS2-To non valide reçu.</span><span class="sxs-lookup"><span data-stu-id="46835-102">Invalid AS2-To header received</span></span>
## <a name="details"></a><span data-ttu-id="46835-103">Détails</span><span class="sxs-lookup"><span data-stu-id="46835-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46835-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="46835-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="46835-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="46835-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="46835-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="46835-106">Event ID</span></span>|-|  
|<span data-ttu-id="46835-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="46835-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="46835-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="46835-108"> EDI</span></span>|  
|<span data-ttu-id="46835-109">Composant</span><span class="sxs-lookup"><span data-stu-id="46835-109">Component</span></span>|<span data-ttu-id="46835-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="46835-110">AS2 Engine</span></span>|  
|<span data-ttu-id="46835-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="46835-111">Symbolic Name</span></span>|<span data-ttu-id="46835-112">InvalidAS2ToNameHeaderReceivedError</span><span class="sxs-lookup"><span data-stu-id="46835-112">InvalidAS2ToNameHeaderReceivedError</span></span>|  
|<span data-ttu-id="46835-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="46835-113">Message Text</span></span>|<span data-ttu-id="46835-114">AS2 non valide-pour l’en-tête reçu.</span><span class="sxs-lookup"><span data-stu-id="46835-114">Invalid AS2-To header received.</span></span>  <span data-ttu-id="46835-115">Valeur : {0}</span><span class="sxs-lookup"><span data-stu-id="46835-115">Value: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="46835-116">Explication</span><span class="sxs-lookup"><span data-stu-id="46835-116">Explanation</span></span>  
 <span data-ttu-id="46835-117">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car la valeur de l'en-tête AS2-To du message n'était pas conforme aux spécifications dans AS2 RFC 4130.</span><span class="sxs-lookup"><span data-stu-id="46835-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the AS2-To header in the message did not conform to the specifications in AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="46835-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="46835-118">User Action</span></span>  
 <span data-ttu-id="46835-119">Pour résoudre cette erreur, assurez-vous que la valeur de l'en-tête AS2-To du message est conforme aux spécifications de la section 6.2 dans AS2 RFC 4130.</span><span class="sxs-lookup"><span data-stu-id="46835-119">To resolve this error, make sure that the value in the AS2-To header of the message conforms to the specifications in section 6.2 of AS2 RFC 4130.</span></span>
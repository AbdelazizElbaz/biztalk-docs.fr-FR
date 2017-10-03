---
title: "Valeur de Receipt-Delivery-Option n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0eed306b-0912-4694-a55c-976128117c02
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f14541cd9c296e6a4527e7c2958123e072be8c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receipt-delivery-option-value-is-invalid"></a><span data-ttu-id="c70f3-102">Valeur Receipt-Delivery-Option non valide</span><span class="sxs-lookup"><span data-stu-id="c70f3-102">Receipt-Delivery-Option value is invalid</span></span>
## <a name="details"></a><span data-ttu-id="c70f3-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c70f3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c70f3-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c70f3-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c70f3-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c70f3-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c70f3-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c70f3-106">Event ID</span></span>|-|  
|<span data-ttu-id="c70f3-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c70f3-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c70f3-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c70f3-108"> EDI</span></span>|  
|<span data-ttu-id="c70f3-109">Composant</span><span class="sxs-lookup"><span data-stu-id="c70f3-109">Component</span></span>|<span data-ttu-id="c70f3-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="c70f3-110">AS2 Engine</span></span>|  
|<span data-ttu-id="c70f3-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c70f3-111">Symbolic Name</span></span>|<span data-ttu-id="c70f3-112">InvalidReceiptDeliveryOptionError</span><span class="sxs-lookup"><span data-stu-id="c70f3-112">InvalidReceiptDeliveryOptionError</span></span>|  
|<span data-ttu-id="c70f3-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c70f3-113">Message Text</span></span>|<span data-ttu-id="c70f3-114">Valeur de Receipt-Delivery-Option : « {0} » n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="c70f3-114">Receipt-Delivery-Option value: "{0}" is invalid.</span></span>  <span data-ttu-id="c70f3-115">{1}</span><span class="sxs-lookup"><span data-stu-id="c70f3-115">{1}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c70f3-116">Explication</span><span class="sxs-lookup"><span data-stu-id="c70f3-116">Explanation</span></span>  
 <span data-ttu-id="c70f3-117">Cet événement de type erreur/avertissement/information indique que la valeur Receipt-Delivery-Option dans le message AS2 reçu n'est pas une URL valide et n'est pas conforme aux spécifications de la RFC 4130 AS2.</span><span class="sxs-lookup"><span data-stu-id="c70f3-117">This Error/Warning/Information event indicates that the Receipt-Delivery-Option in the received AS2 message is not a valid URL and does not conform to the specifications in the AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c70f3-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c70f3-118">User Action</span></span>  
 <span data-ttu-id="c70f3-119">Pour résoudre cette erreur, modifiez Receipt-Delivery-Option dans le message AS2 de sorte à y inclure une URL valide et à ce qu'elle soit conforme aux spécifications de la section 7.3 de la RFC 4130 AS2, puis renvoyez le message AS2.</span><span class="sxs-lookup"><span data-stu-id="c70f3-119">To resolve this error, have the Receipt-Delivery-Option in the AS2 message changed to include a valid URL and conform to the specifications in section 7.3 of the AS2 RFC 4130, and then resend the AS2 message.</span></span>
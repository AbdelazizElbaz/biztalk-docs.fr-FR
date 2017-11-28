---
title: "L’algorithme de hachage spécifié dans le message AS2 est non pris en charge | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b292238-f964-4275-bbfa-e21c9150abf7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6d16c7a3336a798c18b484bc50ff3e2f0c69764
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-hash-algorithm-specified-in-the-as2-message-is-unsupported"></a><span data-ttu-id="87877-102">L'algorithme de hachage spécifié dans le message AS2 n'est pas pris en charge</span><span class="sxs-lookup"><span data-stu-id="87877-102">The hash algorithm specified in the AS2 message is unsupported</span></span>
## <a name="details"></a><span data-ttu-id="87877-103">Détails</span><span class="sxs-lookup"><span data-stu-id="87877-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="87877-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="87877-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="87877-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="87877-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="87877-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="87877-106">Event ID</span></span>|-|  
|<span data-ttu-id="87877-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="87877-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="87877-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="87877-108"> EDI</span></span>|  
|<span data-ttu-id="87877-109">Composant</span><span class="sxs-lookup"><span data-stu-id="87877-109">Component</span></span>|<span data-ttu-id="87877-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="87877-110">AS2 Engine</span></span>|  
|<span data-ttu-id="87877-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="87877-111">Symbolic Name</span></span>|<span data-ttu-id="87877-112">UnsupportedAS2HashAlgorithmError</span><span class="sxs-lookup"><span data-stu-id="87877-112">UnsupportedAS2HashAlgorithmError</span></span>|  
|<span data-ttu-id="87877-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="87877-113">Message Text</span></span>|<span data-ttu-id="87877-114">L'algorithme de hachage spécifié dans le message AS2 n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="87877-114">The hash algorithm specified in the AS2 message is unsupported.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="87877-115">Explication</span><span class="sxs-lookup"><span data-stu-id="87877-115">Explanation</span></span>  
 <span data-ttu-id="87877-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu générer le MDN tel que spécifié, car l'algorithme de hachage MIC spécifié dans l'en-tête signed-receipt-micalg du message AS2 reçu n'est pas une valeur valide.</span><span class="sxs-lookup"><span data-stu-id="87877-116">This Error/Warning/Information event indicates that the receive pipeline could not generate the MDN as specified because the MIC hash algorithm specified in the signed-receipt-micalg header of the received AS2 message is not a valid value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="87877-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="87877-117">User Action</span></span>  
 <span data-ttu-id="87877-118">Pour résoudre cette erreur, demandez à l'expéditeur du message de modifier l'algorithme en MD5 ou SHA1 et renvoyez le message.</span><span class="sxs-lookup"><span data-stu-id="87877-118">To resolve this error, have the sender of the message change the algorithm to either MD5 or SHA1, and resend the message.</span></span>
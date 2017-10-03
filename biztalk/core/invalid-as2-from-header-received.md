---
title: "AS2 non valide-à partir de l’en-tête reçu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d773e09-8526-4533-9066-8e743e65a688
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f20a74e60a6365c0c16e139e8b2caca1bc33646
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-as2-from-header-received"></a><span data-ttu-id="9c7ef-102">En-tête AS2-From non valide reçu</span><span class="sxs-lookup"><span data-stu-id="9c7ef-102">Invalid AS2-From header received</span></span>
## <a name="details"></a><span data-ttu-id="9c7ef-103">Détails</span><span class="sxs-lookup"><span data-stu-id="9c7ef-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9c7ef-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="9c7ef-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="9c7ef-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="9c7ef-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="9c7ef-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="9c7ef-106">Event ID</span></span>|-|  
|<span data-ttu-id="9c7ef-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="9c7ef-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9c7ef-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="9c7ef-108"> EDI</span></span>|  
|<span data-ttu-id="9c7ef-109">Composant</span><span class="sxs-lookup"><span data-stu-id="9c7ef-109">Component</span></span>|<span data-ttu-id="9c7ef-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="9c7ef-110">AS2 Engine</span></span>|  
|<span data-ttu-id="9c7ef-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="9c7ef-111">Symbolic Name</span></span>|<span data-ttu-id="9c7ef-112">InvalidAS2FromNameHeaderReceivedError</span><span class="sxs-lookup"><span data-stu-id="9c7ef-112">InvalidAS2FromNameHeaderReceivedError</span></span>|  
|<span data-ttu-id="9c7ef-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="9c7ef-113">Message Text</span></span>|<span data-ttu-id="9c7ef-114">En-tête AS2-From non valide reçu.</span><span class="sxs-lookup"><span data-stu-id="9c7ef-114">Invalid AS2-From header received.</span></span>  <span data-ttu-id="9c7ef-115">Valeur : {0}</span><span class="sxs-lookup"><span data-stu-id="9c7ef-115">Value: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9c7ef-116">Explication</span><span class="sxs-lookup"><span data-stu-id="9c7ef-116">Explanation</span></span>  
 <span data-ttu-id="9c7ef-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant car la valeur de l'en-tête AS2-From associée n'est pas conforme aux spécifications de la norme AS2 RFC 4130.</span><span class="sxs-lookup"><span data-stu-id="9c7ef-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the AS2-From header in the message did not conform to the specifications in AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9c7ef-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="9c7ef-118">User Action</span></span>  
 <span data-ttu-id="9c7ef-119">Pour résoudre cette erreur, assurez-vous que la valeur de l'en-tête AS2-From du message est conforme aux spécifications de la section 6.2 de la norme AS2 RFC 4130, puis demandez à l'expéditeur de renvoyer le message.</span><span class="sxs-lookup"><span data-stu-id="9c7ef-119">To resolve this error, make sure that the value in the AS2-From header of the message conforms to the specifications in section 6.2 of AS2 RFC 4130, and then have the message resent.</span></span>
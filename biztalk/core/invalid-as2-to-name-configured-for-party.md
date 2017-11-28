---
title: "AS2 non valide-au nom configuré pour le tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a203e5f2-d1d9-433f-b2bb-d679bb8fea58
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c06adc5a459f7dfd05508312494555fb2651114
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-as2-to-name-configured-for-party"></a><span data-ttu-id="c6052-102">Nom AS2-To non valide configuré pour le tiers</span><span class="sxs-lookup"><span data-stu-id="c6052-102">Invalid AS2-To name configured for Party</span></span>
## <a name="details"></a><span data-ttu-id="c6052-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c6052-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6052-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c6052-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c6052-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c6052-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c6052-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c6052-106">Event ID</span></span>|-|  
|<span data-ttu-id="c6052-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c6052-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c6052-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c6052-108"> EDI</span></span>|  
|<span data-ttu-id="c6052-109">Composant</span><span class="sxs-lookup"><span data-stu-id="c6052-109">Component</span></span>|<span data-ttu-id="c6052-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="c6052-110">AS2 Engine</span></span>|  
|<span data-ttu-id="c6052-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c6052-111">Symbolic Name</span></span>|<span data-ttu-id="c6052-112">InvalidAS2ToNameConfiguredError</span><span class="sxs-lookup"><span data-stu-id="c6052-112">InvalidAS2ToNameConfiguredError</span></span>|  
|<span data-ttu-id="c6052-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c6052-113">Message Text</span></span>|<span data-ttu-id="c6052-114">AS2 non valide-au nom configuré pour le tiers : {0} valeur : {1}</span><span class="sxs-lookup"><span data-stu-id="c6052-114">Invalid AS2-To name configured for Party: {0}   Value: {1}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c6052-115">Explication</span><span class="sxs-lookup"><span data-stu-id="c6052-115">Explanation</span></span>  
 <span data-ttu-id="c6052-116">Cet événement d'erreur/d'avertissement/d'informations indique que l'encodeur ou le décodeur AS2 n'a pas pu traiter le message AS2, car la valeur de l'en-tête AS2-Tom configurée pour le tiers identifié n'est pas conforme aux spécifications de la norme AS2 RFC 4130.</span><span class="sxs-lookup"><span data-stu-id="c6052-116">This Error/Warning/Information event indicates that the AS2 encoder or decoder could not process the AS2 message because the value of the AS2-To header configured for the identified party did not conform to the specifications in AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c6052-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c6052-117">User Action</span></span>  
 <span data-ttu-id="c6052-118">Pour résoudre cette erreur, assurez-vous que l'en-tête AS2-To configuré pour le tiers est conforme aux spécifications dans la section 6.2 de la norme AS2 RFC 4130.</span><span class="sxs-lookup"><span data-stu-id="c6052-118">To resolve this error, make sure that the AS2-To header configured for the party conforms to the specifications in section 6.2 of AS2 RFC 4130.</span></span>
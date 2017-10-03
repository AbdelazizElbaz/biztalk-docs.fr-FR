---
title: "Le tiers pour cet échange AS2 doit contenir une valeur pour AS2-pour | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 029eae5d-4c13-402d-90c5-8e9ef3814a1f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4adda90c2ae0e5dfa659e3bd36dcadfc58f815ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-party-for-this-as2-interchange-must-contain-a-value-for-as2-to"></a><span data-ttu-id="a8921-102">Le tiers pour cet échange AS2 doit contenir une valeur pour AS2-To.</span><span class="sxs-lookup"><span data-stu-id="a8921-102">The party for this AS2 interchange must contain a value for AS2-To</span></span>
## <a name="details"></a><span data-ttu-id="a8921-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a8921-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a8921-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a8921-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a8921-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a8921-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a8921-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a8921-106">Event ID</span></span>|-|  
|<span data-ttu-id="a8921-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a8921-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a8921-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a8921-108"> EDI</span></span>|  
|<span data-ttu-id="a8921-109">Composant</span><span class="sxs-lookup"><span data-stu-id="a8921-109">Component</span></span>|<span data-ttu-id="a8921-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="a8921-110">AS2 Engine</span></span>|  
|<span data-ttu-id="a8921-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a8921-111">Symbolic Name</span></span>|<span data-ttu-id="a8921-112">InvalidAgreementAS2ToName</span><span class="sxs-lookup"><span data-stu-id="a8921-112">InvalidAgreementAS2ToName</span></span>|  
|<span data-ttu-id="a8921-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a8921-113">Message Text</span></span>|<span data-ttu-id="a8921-114">Le tiers pour cet échange AS2 doit contenir une valeur pour AS2-de.</span><span class="sxs-lookup"><span data-stu-id="a8921-114">The party for this AS2 interchange must contain a value for AS2-To.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a8921-115">Explication</span><span class="sxs-lookup"><span data-stu-id="a8921-115">Explanation</span></span>  
 <span data-ttu-id="a8921-116">Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu traiter le message AS2 sortant, car la propriété AS2 n'était pas définie pour le tiers résolu considéré comme récepteur des messages.</span><span class="sxs-lookup"><span data-stu-id="a8921-116">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing AS2 message because the AS2-To property was not set for the resolved party as message receiver.</span></span> <span data-ttu-id="a8921-117">Cela indique le tiers correspondant au message AS2 sortant a été résolu en faisant correspondre le port d'envoi associé au tiers avec le port d'envoi qui s'est abonné au message.</span><span class="sxs-lookup"><span data-stu-id="a8921-117">This indicates that the party for the outgoing AS2 message was resolved by matching the send port associated with the party with the send port that subscribed to the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a8921-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a8921-118">User Action</span></span>  
 <span data-ttu-id="a8921-119">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a8921-119">To resolve this error, do as follows:</span></span>  
  
1.  <span data-ttu-id="a8921-120">Ouvrez la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a8921-120">Open the BizTalk Server Administration Console.</span></span>  
  
2.  <span data-ttu-id="a8921-121">Accédez au nœud Tiers, puis ouvrez la boîte de dialogue Propriétés AS2 correspondant au tiers résolu pour le message.</span><span class="sxs-lookup"><span data-stu-id="a8921-121">Move to the Parties node, and open the AS2 Properties dialog box for the party resolved for the message.</span></span>  
  
3.  <span data-ttu-id="a8921-122">Cliquez sur le nœud Tiers considéré comme récepteur des messages.</span><span class="sxs-lookup"><span data-stu-id="a8921-122">Click the Party as AS2 Message Receiver node.</span></span>  
  
4.  <span data-ttu-id="a8921-123">Entrez une valeur pour la propriété AS2-To.</span><span class="sxs-lookup"><span data-stu-id="a8921-123">Enter a value for the AS2-To property.</span></span>
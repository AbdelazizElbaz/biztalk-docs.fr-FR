---
title: "Le tiers pour cet échange AS2 doit contenir une valeur pour AS2-à partir de | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d338759-5646-4dc2-8319-a42aaa8c3d9c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b52f153cce06eac014d98fa1908978694fc67706
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-party-for-this-as2-interchange-must-contain-a-value-for-as2-from"></a><span data-ttu-id="c8f19-102">Le tiers pour cet échange AS2 doit contenir une valeur pour AS2-From</span><span class="sxs-lookup"><span data-stu-id="c8f19-102">The party for this AS2 interchange must contain a value for AS2-From</span></span>
## <a name="details"></a><span data-ttu-id="c8f19-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c8f19-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c8f19-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c8f19-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c8f19-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c8f19-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c8f19-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c8f19-106">Event ID</span></span>|-|  
|<span data-ttu-id="c8f19-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c8f19-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c8f19-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c8f19-108"> EDI</span></span>|  
|<span data-ttu-id="c8f19-109">Composant</span><span class="sxs-lookup"><span data-stu-id="c8f19-109">Component</span></span>|<span data-ttu-id="c8f19-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="c8f19-110">AS2 Engine</span></span>|  
|<span data-ttu-id="c8f19-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c8f19-111">Symbolic Name</span></span>|<span data-ttu-id="c8f19-112">InvalidAgreementAS2FromName</span><span class="sxs-lookup"><span data-stu-id="c8f19-112">InvalidAgreementAS2FromName</span></span>|  
|<span data-ttu-id="c8f19-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c8f19-113">Message Text</span></span>|<span data-ttu-id="c8f19-114">Le tiers pour cet échange AS2 doit contenir une valeur pour AS2-From.</span><span class="sxs-lookup"><span data-stu-id="c8f19-114">The party for this AS2 interchange must contain a value for AS2-From.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c8f19-115">Explication</span><span class="sxs-lookup"><span data-stu-id="c8f19-115">Explanation</span></span>  
 <span data-ttu-id="c8f19-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu envoyer le message AS2 car la propriété AS2-From n'a pas été définie pour le tiers qui a été résolu comme récepteur des messages.</span><span class="sxs-lookup"><span data-stu-id="c8f19-116">This Error/Warning/Information event indicates that the send pipeline could not send the AS2 message because the AS2-From property was not set for the resolved party as message receiver.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c8f19-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c8f19-117">User Action</span></span>  
 <span data-ttu-id="c8f19-118">Pour résoudre cette erreur, ouvrez la console Administration de BizTalk Server, accédez au nœud Tiers, ouvrez la boîte de dialogue Propriétés AS2 pour le tiers correspondant au message, cliquez sur le nœud Tiers considéré comme récepteur des messages AS2, puis entrez une valeur pour la propriété AS2-From.</span><span class="sxs-lookup"><span data-stu-id="c8f19-118">To resolve this error, open the BizTalk Server Administration Console, move to the Parties node, open the AS2 Properties dialog box for the party resolved for the message, click the Party as AS2 Message Receiver node, and then enter a value for the AS2-From property.</span></span>
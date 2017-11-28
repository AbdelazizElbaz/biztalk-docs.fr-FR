---
title: "Une erreur BTS MIME a été rencontrée lors d’une tentative de décodage d’un message AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65cb5ece-78e4-4b83-b126-4d8c588b2c61
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 660a9e3a6ca5834448dd64815b031e00a0b2942a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-bts-mime-error-was-encountered-when-attempting-to-decode-an-as2-message"></a><span data-ttu-id="09743-102">Une erreur BTS MIME a été détectée lors de la tentative de décodage d'un message AS2</span><span class="sxs-lookup"><span data-stu-id="09743-102">A BTS MIME error was encountered when attempting to decode an AS2 message</span></span>
## <a name="details"></a><span data-ttu-id="09743-103">Détails</span><span class="sxs-lookup"><span data-stu-id="09743-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="09743-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="09743-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="09743-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="09743-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="09743-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="09743-106">Event ID</span></span>|-|  
|<span data-ttu-id="09743-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="09743-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="09743-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="09743-108"> EDI</span></span>|  
|<span data-ttu-id="09743-109">Composant</span><span class="sxs-lookup"><span data-stu-id="09743-109">Component</span></span>|<span data-ttu-id="09743-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="09743-110">AS2 Engine</span></span>|  
|<span data-ttu-id="09743-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="09743-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="09743-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="09743-112">Message Text</span></span>|<span data-ttu-id="09743-113">Une erreur BTS MIME a été détectée lors de la tentative de décodage d'un message AS2.</span><span class="sxs-lookup"><span data-stu-id="09743-113">A BTS MIME error was encountered when attempting to decode an AS2 message.</span></span>  <span data-ttu-id="09743-114">AS2-à partir de : {0}, AS2-pour : {1}, MessageId : {2}, erreur : {3}</span><span class="sxs-lookup"><span data-stu-id="09743-114">AS2-From: {0}, AS2-To: {1}, MessageId: {2}, Error: {3}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="09743-115">Explication</span><span class="sxs-lookup"><span data-stu-id="09743-115">Explanation</span></span>  
 <span data-ttu-id="09743-116">Cette erreur se produit lors de l'utilisation du composant BizTalk MIME pour gérer une partie du traitement MIME.</span><span class="sxs-lookup"><span data-stu-id="09743-116">This error is encountered when using the BizTalk MIME component to handle part of the MIME processing.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="09743-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="09743-117">User Action</span></span>  
 <span data-ttu-id="09743-118">Le message d’erreur complet fournit les informations sur les problèmes rencontrés par le composant MIME.</span><span class="sxs-lookup"><span data-stu-id="09743-118">The full error message provides the information about the problem encountered by the MIME component.</span></span> <span data-ttu-id="09743-119">Consultez les informations d’erreur BTS MIME pour diagnostiquer le problème (c’est parce que les composants AS2 utilisent les composants BizTalk MIME pour une partie du traitement MIME).</span><span class="sxs-lookup"><span data-stu-id="09743-119">Refer to the BTS MIME error information for diagnosis of the problem (this is because the AS2 components use the BizTalk MIME components for part of the MIME processing).</span></span>
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
ms.openlocfilehash: 096696f4420150cdd53f8fe561460d243c1bb018
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="a-bts-mime-error-was-encountered-when-attempting-to-decode-an-as2-message"></a><span data-ttu-id="2fd29-102">Une erreur BTS MIME a été détectée lors de la tentative de décodage d'un message AS2</span><span class="sxs-lookup"><span data-stu-id="2fd29-102">A BTS MIME error was encountered when attempting to decode an AS2 message</span></span>
## <a name="details"></a><span data-ttu-id="2fd29-103">Détails</span><span class="sxs-lookup"><span data-stu-id="2fd29-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2fd29-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="2fd29-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="2fd29-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="2fd29-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="2fd29-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="2fd29-106">Event ID</span></span>|-|  
|<span data-ttu-id="2fd29-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="2fd29-107">Event Source</span></span>|<span data-ttu-id="2fd29-108">EDI de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2fd29-108">BizTalk Server EDI</span></span>|  
|<span data-ttu-id="2fd29-109">Composant</span><span class="sxs-lookup"><span data-stu-id="2fd29-109">Component</span></span>|<span data-ttu-id="2fd29-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="2fd29-110">AS2 Engine</span></span>|  
|<span data-ttu-id="2fd29-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="2fd29-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="2fd29-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="2fd29-112">Message Text</span></span>|<span data-ttu-id="2fd29-113">Une erreur BTS MIME a été détectée lors de la tentative de décodage d'un message AS2.</span><span class="sxs-lookup"><span data-stu-id="2fd29-113">A BTS MIME error was encountered when attempting to decode an AS2 message.</span></span>  <span data-ttu-id="2fd29-114">AS2-à partir de : {0}, AS2-pour : {1}, MessageId : {2}, erreur : {3}</span><span class="sxs-lookup"><span data-stu-id="2fd29-114">AS2-From: {0}, AS2-To: {1}, MessageId: {2}, Error: {3}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2fd29-115">Explication</span><span class="sxs-lookup"><span data-stu-id="2fd29-115">Explanation</span></span>  
 <span data-ttu-id="2fd29-116">Cette erreur se produit lors de l'utilisation du composant BizTalk MIME pour gérer une partie du traitement MIME.</span><span class="sxs-lookup"><span data-stu-id="2fd29-116">This error is encountered when using the BizTalk MIME component to handle part of the MIME processing.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2fd29-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="2fd29-117">User Action</span></span>  
 <span data-ttu-id="2fd29-118">Le message d’erreur complet fournit les informations sur les problèmes rencontrés par le composant MIME.</span><span class="sxs-lookup"><span data-stu-id="2fd29-118">The full error message provides the information about the problem encountered by the MIME component.</span></span> <span data-ttu-id="2fd29-119">Consultez les informations d’erreur BTS MIME pour diagnostiquer le problème (c’est parce que les composants AS2 utilisent les composants BizTalk MIME pour une partie du traitement MIME).</span><span class="sxs-lookup"><span data-stu-id="2fd29-119">Refer to the BTS MIME error information for diagnosis of the problem (this is because the AS2 components use the BizTalk MIME components for part of the MIME processing).</span></span>
---
title: "L'accord associé à BatchId n'est pas activé ou a expiré. Le traitement par lots ne peut pas continuer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d92cb07-7646-42b3-90a8-18acbcd145cd
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e68e91fe1cd2d91c20c84a32afd37212769a4736
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-agreement-associated-with-batchid-is-not-enabled-or-has-expired-batching-cannot-continue"></a><span data-ttu-id="22d71-103">L'accord associé à BatchId n'est pas activé ou a expiré.</span><span class="sxs-lookup"><span data-stu-id="22d71-103">The agreement associated with BatchId is not enabled or has expired.</span></span> <span data-ttu-id="22d71-104">Impossible de poursuivre le traitement par lot</span><span class="sxs-lookup"><span data-stu-id="22d71-104">Batching cannot continue</span></span>
## <a name="details"></a><span data-ttu-id="22d71-105">Détails</span><span class="sxs-lookup"><span data-stu-id="22d71-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="22d71-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="22d71-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="22d71-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="22d71-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="22d71-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="22d71-108">Event ID</span></span>|-|  
|<span data-ttu-id="22d71-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="22d71-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="22d71-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="22d71-110"> EDI</span></span>|  
|<span data-ttu-id="22d71-111">Composant</span><span class="sxs-lookup"><span data-stu-id="22d71-111">Component</span></span>|<span data-ttu-id="22d71-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="22d71-112">EDI Engine</span></span>|  
|<span data-ttu-id="22d71-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="22d71-113">Symbolic Name</span></span>|<span data-ttu-id="22d71-114">ErrorBatchAgreementDisabled</span><span class="sxs-lookup"><span data-stu-id="22d71-114">ErrorBatchAgreementDisabled</span></span>|  
|<span data-ttu-id="22d71-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="22d71-115">Message Text</span></span>|<span data-ttu-id="22d71-116">L'accord associé à BatchId {0} n'est pas activé ou a expiré.</span><span class="sxs-lookup"><span data-stu-id="22d71-116">The agreement associated with BatchId {0} is not enabled or has expired.</span></span> <span data-ttu-id="22d71-117">Impossible de poursuivre le traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="22d71-117">Batching cannot continue.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="22d71-118">Explication</span><span class="sxs-lookup"><span data-stu-id="22d71-118">Explanation</span></span>  
 <span data-ttu-id="22d71-119">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas réussi à démarrer un lot ou à traiter un lot de messages, car l'accord arrive à expiration.</span><span class="sxs-lookup"><span data-stu-id="22d71-119">This Error/Warning/Information event indicates BizTalk Server was not able to start a batch or process a batch message because of Agreement getting expired.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="22d71-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="22d71-120">User Action</span></span>  
 <span data-ttu-id="22d71-121">Pour résoudre cette erreur, assurez-vous qu'un lot doté d'un ID donné existe bien dans les propriétés de l'accord dans lequel il est contenu et vérifiez que ses dates de début et de fin sont comprises entre celles de l'accord.</span><span class="sxs-lookup"><span data-stu-id="22d71-121">To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement and its start and end date fall within the start and end dates of the Agreement.</span></span> <span data-ttu-id="22d71-122">Assurez-vous également que l'accord est activé.</span><span class="sxs-lookup"><span data-stu-id="22d71-122">Also make sure that the agreement is enabled.</span></span>
---
title: Impossible de trouver un accord correspondant au lot | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d1c0480-9a6f-481a-9143-e5a55707c3b5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bce17af0e382a137dc8d55d30705da58dd52301c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="could-not-find-an-agreement-corresponding-to-batch"></a><span data-ttu-id="4c574-102">Impossible de trouver un accord correspondant au lot</span><span class="sxs-lookup"><span data-stu-id="4c574-102">Could not find an Agreement corresponding to batch</span></span>
## <a name="details"></a><span data-ttu-id="4c574-103">Détails</span><span class="sxs-lookup"><span data-stu-id="4c574-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4c574-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="4c574-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="4c574-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="4c574-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="4c574-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="4c574-106">Event ID</span></span>|-|  
|<span data-ttu-id="4c574-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="4c574-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4c574-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="4c574-108"> EDI</span></span>|  
|<span data-ttu-id="4c574-109">Composant</span><span class="sxs-lookup"><span data-stu-id="4c574-109">Component</span></span>|<span data-ttu-id="4c574-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="4c574-110">EDI Engine</span></span>|  
|<span data-ttu-id="4c574-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="4c574-111">Symbolic Name</span></span>|<span data-ttu-id="4c574-112">AgreementNotFoundForBatch</span><span class="sxs-lookup"><span data-stu-id="4c574-112">AgreementNotFoundForBatch</span></span>|  
|<span data-ttu-id="4c574-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="4c574-113">Message Text</span></span>|<span data-ttu-id="4c574-114">Impossible de trouver un accord correspondant au lot {0}.</span><span class="sxs-lookup"><span data-stu-id="4c574-114">Could not find an Agreement corresponding to batch {0}.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4c574-115">Explication</span><span class="sxs-lookup"><span data-stu-id="4c574-115">Explanation</span></span>  
 <span data-ttu-id="4c574-116">Cet événement de type erreur/avertissement/information indique que BizTalk Server n'a pas pu trouver un lot correspondant à cet ID lors de la tentative de démarrage/d'arrêt d'un lot ou de traitement d'un message par lot.</span><span class="sxs-lookup"><span data-stu-id="4c574-116">This Error/Warning/Information event indicates BizTalk Server was unable to find a Batch corresponding to this Id while trying to start/stop a batch or process a batch message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4c574-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4c574-117">User Action</span></span>  
 <span data-ttu-id="4c574-118">Pour résoudre cette erreur, assurez-vous qu'un lot portant l'ID donné soit présent dans les propriétés de l'accord contenant.</span><span class="sxs-lookup"><span data-stu-id="4c574-118">To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement.</span></span>
---
title: "Le lot n’a pas été trouvé. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e967e1a-b87f-4c87-a157-a6f63ba96d78
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a73c3e65a806f02faeb81baa6a5263019079b0c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-batch-was-not-found"></a><span data-ttu-id="fe5e7-102">Le lot est introuvable</span><span class="sxs-lookup"><span data-stu-id="fe5e7-102">The batch was not found</span></span>
## <a name="details"></a><span data-ttu-id="fe5e7-103">Détails</span><span class="sxs-lookup"><span data-stu-id="fe5e7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fe5e7-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="fe5e7-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="fe5e7-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="fe5e7-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="fe5e7-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="fe5e7-106">Event ID</span></span>|-|  
|<span data-ttu-id="fe5e7-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="fe5e7-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="fe5e7-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="fe5e7-108"> EDI</span></span>|  
|<span data-ttu-id="fe5e7-109">Composant</span><span class="sxs-lookup"><span data-stu-id="fe5e7-109">Component</span></span>|<span data-ttu-id="fe5e7-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="fe5e7-110">EDI Engine</span></span>|  
|<span data-ttu-id="fe5e7-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="fe5e7-111">Symbolic Name</span></span>|<span data-ttu-id="fe5e7-112">Err_BatchNotFound</span><span class="sxs-lookup"><span data-stu-id="fe5e7-112">Err_BatchNotFound</span></span>|  
|<span data-ttu-id="fe5e7-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="fe5e7-113">Message Text</span></span>|<span data-ttu-id="fe5e7-114">Le lot est introuvable.</span><span class="sxs-lookup"><span data-stu-id="fe5e7-114">The batch was not found.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fe5e7-115">Explication</span><span class="sxs-lookup"><span data-stu-id="fe5e7-115">Explanation</span></span>  
 <span data-ttu-id="fe5e7-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas réussi à trouver un lot lors du démarrage/arrêt d'un lot ou lors d'une tentative de traitement par lot d'un message par l'orchestration de traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="fe5e7-116">This Error/Warning/Information event indicates BizTalk Server was unable to find a batch during the start/stop of a batch or while the Batching Orchestration was trying to batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fe5e7-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="fe5e7-117">User Action</span></span>  
 <span data-ttu-id="fe5e7-118">Pour résoudre cette erreur, assurez-vous que le lot correspondant est présent dans les propriétés de l'accord qui le contient.</span><span class="sxs-lookup"><span data-stu-id="fe5e7-118">To resolve this error, ensure that the respective batch is present in the Agreement properties of the containing Agreement.</span></span>
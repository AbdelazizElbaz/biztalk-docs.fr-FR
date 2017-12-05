---
title: "Une exception s’est produite lors de l’exécution de l’orchestration de traitement par lots de mise à niveau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2221a498-98aa-43ab-bc4e-34dcbd92dcf0
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a0789853ba253d7d8e51c34a6c1d1ce64829f8d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="an-exception-has-occurred-during-the-execution-of-the-upgrade-batch-orchestration"></a><span data-ttu-id="ad83d-102">Une exception s'est produite lors de l'exécution de l'orchestration du traitement par lot de la mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="ad83d-102">An exception has occurred during the execution of the upgrade batch orchestration</span></span>
## <a name="details"></a><span data-ttu-id="ad83d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ad83d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad83d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ad83d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ad83d-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ad83d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ad83d-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ad83d-106">Event ID</span></span>|-|  
|<span data-ttu-id="ad83d-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ad83d-107">Event Source</span></span>|<span data-ttu-id="ad83d-108">EDI de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="ad83d-108">BizTalk Server EDI</span></span>|  
|<span data-ttu-id="ad83d-109">Composant</span><span class="sxs-lookup"><span data-stu-id="ad83d-109">Component</span></span>|<span data-ttu-id="ad83d-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="ad83d-110">Batching Engine</span></span>|  
|<span data-ttu-id="ad83d-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ad83d-111">Symbolic Name</span></span>|<span data-ttu-id="ad83d-112">ExceptionOccuredDuringUpgrade</span><span class="sxs-lookup"><span data-stu-id="ad83d-112">ExceptionOccuredDuringUpgrade</span></span>|  
|<span data-ttu-id="ad83d-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ad83d-113">Message Text</span></span>|<span data-ttu-id="ad83d-114">Une exception s’est produite lors de l’exécution du lot de mise à niveau d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="ad83d-114">An exception has occurred during the execution of the upgrade batch Orchestration.</span></span> <span data-ttu-id="ad83d-115">Message d'erreur = {0}</span><span class="sxs-lookup"><span data-stu-id="ad83d-115">ErrorMessage = {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ad83d-116">Explication</span><span class="sxs-lookup"><span data-stu-id="ad83d-116">Explanation</span></span>  
 <span data-ttu-id="ad83d-117">Cet événement de type erreur/avertissement/information indique que l'orchestration du traitement par lot de la mise à niveau n'a pas pu traiter le message correctement en raison de la condition d'erreur indiquée dans le champ MessageErreur.</span><span class="sxs-lookup"><span data-stu-id="ad83d-117">The Error/Warning/Information event indicates that the upgrade batch orchestration could not process the message correctly because of the error condition indicated in ErrorMessage field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ad83d-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ad83d-118">User Action</span></span>  
 <span data-ttu-id="ad83d-119">Pour résoudre cette erreur, déterminez la condition d'erreur à partir du champ ErrorMessage, résolvez l'erreur, puis renvoyez le message.</span><span class="sxs-lookup"><span data-stu-id="ad83d-119">To resolve this error, determine what the error condition is from the ErrorMessage field, resolve the error, and then resubmit the message.</span></span>
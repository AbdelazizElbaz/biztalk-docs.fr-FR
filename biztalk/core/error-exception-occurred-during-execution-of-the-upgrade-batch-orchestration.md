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
ms.openlocfilehash: 54cd439e180365010ec8881ce7165022dd7826d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-exception-has-occurred-during-the-execution-of-the-upgrade-batch-orchestration"></a><span data-ttu-id="72f6b-102">Une exception s'est produite lors de l'exécution de l'orchestration du traitement par lot de la mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="72f6b-102">An exception has occurred during the execution of the upgrade batch orchestration</span></span>
## <a name="details"></a><span data-ttu-id="72f6b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="72f6b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="72f6b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="72f6b-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="72f6b-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="72f6b-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="72f6b-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="72f6b-106">Event ID</span></span>|-|  
|<span data-ttu-id="72f6b-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="72f6b-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="72f6b-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="72f6b-108"> EDI</span></span>|  
|<span data-ttu-id="72f6b-109">Composant</span><span class="sxs-lookup"><span data-stu-id="72f6b-109">Component</span></span>|<span data-ttu-id="72f6b-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="72f6b-110">Batching Engine</span></span>|  
|<span data-ttu-id="72f6b-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="72f6b-111">Symbolic Name</span></span>|<span data-ttu-id="72f6b-112">ExceptionOccuredDuringUpgrade</span><span class="sxs-lookup"><span data-stu-id="72f6b-112">ExceptionOccuredDuringUpgrade</span></span>|  
|<span data-ttu-id="72f6b-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="72f6b-113">Message Text</span></span>|<span data-ttu-id="72f6b-114">Une exception s’est produite lors de l’exécution du lot de mise à niveau d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="72f6b-114">An exception has occurred during the execution of the upgrade batch Orchestration.</span></span> <span data-ttu-id="72f6b-115">Message d'erreur = {0}</span><span class="sxs-lookup"><span data-stu-id="72f6b-115">ErrorMessage = {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="72f6b-116">Explication</span><span class="sxs-lookup"><span data-stu-id="72f6b-116">Explanation</span></span>  
 <span data-ttu-id="72f6b-117">Cet événement de type erreur/avertissement/information indique que l'orchestration du traitement par lot de la mise à niveau n'a pas pu traiter le message correctement en raison de la condition d'erreur indiquée dans le champ MessageErreur.</span><span class="sxs-lookup"><span data-stu-id="72f6b-117">The Error/Warning/Information event indicates that the upgrade batch orchestration could not process the message correctly because of the error condition indicated in ErrorMessage field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="72f6b-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="72f6b-118">User Action</span></span>  
 <span data-ttu-id="72f6b-119">Pour résoudre cette erreur, déterminez la condition d'erreur à partir du champ ErrorMessage, résolvez l'erreur, puis renvoyez le message.</span><span class="sxs-lookup"><span data-stu-id="72f6b-119">To resolve this error, determine what the error condition is from the ErrorMessage field, resolve the error, and then resubmit the message.</span></span>
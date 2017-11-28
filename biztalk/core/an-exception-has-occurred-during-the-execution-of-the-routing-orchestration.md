---
title: "Une exception s’est produite pendant l’exécution de l’orchestration de routage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68ec8921-ba05-496e-8dcc-fd8994fcb8b7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e865ec091330a863cb2bab90bbafd9b891edb05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-exception-has-occurred-during-the-execution-of-the-routing-orchestration"></a><span data-ttu-id="59e35-102">Une exception s'est produite lors de l'exécution de l'orchestration de routage</span><span class="sxs-lookup"><span data-stu-id="59e35-102">An exception has occurred during the execution of the routing orchestration</span></span>
## <a name="details"></a><span data-ttu-id="59e35-103">Détails</span><span class="sxs-lookup"><span data-stu-id="59e35-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="59e35-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="59e35-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="59e35-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="59e35-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="59e35-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="59e35-106">Event ID</span></span>|-|  
|<span data-ttu-id="59e35-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="59e35-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="59e35-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="59e35-108"> EDI</span></span>|  
|<span data-ttu-id="59e35-109">Composant</span><span class="sxs-lookup"><span data-stu-id="59e35-109">Component</span></span>|<span data-ttu-id="59e35-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="59e35-110">Batching Engine</span></span>|  
|<span data-ttu-id="59e35-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="59e35-111">Symbolic Name</span></span>|<span data-ttu-id="59e35-112">ExceptionOccuredDuringRouting</span><span class="sxs-lookup"><span data-stu-id="59e35-112">ExceptionOccuredDuringRouting</span></span>|  
|<span data-ttu-id="59e35-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="59e35-113">Message Text</span></span>|<span data-ttu-id="59e35-114">Une exception s'est produite lors de l'exécution de l'orchestration de routage.</span><span class="sxs-lookup"><span data-stu-id="59e35-114">An exception has occured during the execution of the routing Orchestration.</span></span> <span data-ttu-id="59e35-115">Message d'erreur = {0}</span><span class="sxs-lookup"><span data-stu-id="59e35-115">ErrorMessage = {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="59e35-116">Explication</span><span class="sxs-lookup"><span data-stu-id="59e35-116">Explanation</span></span>  
 <span data-ttu-id="59e35-117">Cet événement d'erreur/d'avertissement/d'informations indique que l'orchestration de routage n'a pas pu traiter correctement chaque copie de l'élément de lot XML en raison de la condition d'erreur mentionnée dans le champ ErrorMessage.</span><span class="sxs-lookup"><span data-stu-id="59e35-117">This Error/Warning/Information event indicates that the routing orchestration could not process each copy of the XML batch element correctly because of the error condition indicated in ErrorMessage field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="59e35-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="59e35-118">User Action</span></span>  
 <span data-ttu-id="59e35-119">Pour résoudre cette erreur, déterminer ce qui est la condition d’erreur à partir du champ ErrorMessage, résolvez l’erreur et soumettez à nouveau le message.</span><span class="sxs-lookup"><span data-stu-id="59e35-119">To resolve this error, determine what the error condition is from the ErrorMessage field, resolve the error, and resubmit the message.</span></span>
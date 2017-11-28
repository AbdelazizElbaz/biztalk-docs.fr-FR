---
title: "Une exception s’est produite lors de l’envoi du lot dans l’orchestration de traitement par lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c58b2fa9-d036-4e09-a0f8-77a2f983881a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a3e61cc7375acf5d9faf0d72ab36127532c66ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-exception-has-occurred-during-the-batch-submission-in-the-batching-orchestration"></a><span data-ttu-id="0ffc1-102">Une exception s'est produite lors de la soumission du lot dans l'orchestration du traitement par lots</span><span class="sxs-lookup"><span data-stu-id="0ffc1-102">An exception has occurred during the batch submission in the batching orchestration</span></span>
## <a name="details"></a><span data-ttu-id="0ffc1-103">Détails</span><span class="sxs-lookup"><span data-stu-id="0ffc1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0ffc1-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="0ffc1-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0ffc1-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="0ffc1-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="0ffc1-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0ffc1-106">Event ID</span></span>|-|  
|<span data-ttu-id="0ffc1-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="0ffc1-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0ffc1-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="0ffc1-108"> EDI</span></span>|  
|<span data-ttu-id="0ffc1-109">Composant</span><span class="sxs-lookup"><span data-stu-id="0ffc1-109">Component</span></span>|<span data-ttu-id="0ffc1-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="0ffc1-110">Batching Engine</span></span>|  
|<span data-ttu-id="0ffc1-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="0ffc1-111">Symbolic Name</span></span>|<span data-ttu-id="0ffc1-112">ExceptionOccured</span><span class="sxs-lookup"><span data-stu-id="0ffc1-112">ExceptionOccured</span></span>|  
|<span data-ttu-id="0ffc1-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="0ffc1-113">Message Text</span></span>|<span data-ttu-id="0ffc1-114">Une exception s'est produite lors de la soumission du lot dans l'orchestration du traitement par lots.</span><span class="sxs-lookup"><span data-stu-id="0ffc1-114">An exception has occured during the batch submission in the batching Orchestration.</span></span> <span data-ttu-id="0ffc1-115">Id de lot = {0}, {{1} message d’erreur</span><span class="sxs-lookup"><span data-stu-id="0ffc1-115">Batch Id= {0}, ErrorMessage {1}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0ffc1-116">Explication</span><span class="sxs-lookup"><span data-stu-id="0ffc1-116">Explanation</span></span>  
 <span data-ttu-id="0ffc1-117">Cet événement d'erreur/d'avertissement/d'informations indique que l'orchestration de traitement par lot n'a pas pu ajouter un élément de lot à un lot en raison de la condition d'erreur mentionnée dans le champ ErrorMessage.</span><span class="sxs-lookup"><span data-stu-id="0ffc1-117">This Error/Warning/Information event indicates that the batching orchestration could not add a batch element to a batch because of the error condition indicated in the ErrorMessage field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0ffc1-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="0ffc1-118">User Action</span></span>  
 <span data-ttu-id="0ffc1-119">Pour résoudre cette erreur, déterminez la condition d'erreur à partir du champ ErrorMessage, résolvez l'erreur, puis renvoyez le message.</span><span class="sxs-lookup"><span data-stu-id="0ffc1-119">To resolve this error, determine what the error condition is from the ErrorMessage field, resolve the error, and then resubmit the message.</span></span>
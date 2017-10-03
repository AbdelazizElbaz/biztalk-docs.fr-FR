---
title: "L’élément de lot est suspendu car sa validation a échoué | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea5e19e8-4592-40f4-bffe-85ab27653fd5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7022041d8d47e1bfa52eb7ef45764c17ed1a2d8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-batch-element-is-being-suspended-as-it-failed-validation"></a><span data-ttu-id="29a55-102">L'élément de traitement par lots est suspendu car sa validation a échoué</span><span class="sxs-lookup"><span data-stu-id="29a55-102">The batch element is being suspended as it failed validation</span></span>
## <a name="details"></a><span data-ttu-id="29a55-103">Détails</span><span class="sxs-lookup"><span data-stu-id="29a55-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29a55-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="29a55-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="29a55-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="29a55-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="29a55-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="29a55-106">Event ID</span></span>|-|  
|<span data-ttu-id="29a55-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="29a55-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="29a55-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="29a55-108"> EDI</span></span>|  
|<span data-ttu-id="29a55-109">Composant</span><span class="sxs-lookup"><span data-stu-id="29a55-109">Component</span></span>|<span data-ttu-id="29a55-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="29a55-110">Batching Engine</span></span>|  
|<span data-ttu-id="29a55-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="29a55-111">Symbolic Name</span></span>|<span data-ttu-id="29a55-112">BatchElementSuspended</span><span class="sxs-lookup"><span data-stu-id="29a55-112">BatchElementSuspended</span></span>|  
|<span data-ttu-id="29a55-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="29a55-113">Message Text</span></span>|<span data-ttu-id="29a55-114">L'élément de traitement par lots est suspendu car sa validation a échoué.</span><span class="sxs-lookup"><span data-stu-id="29a55-114">The batch element is being suspended as it failed validation.</span></span> <span data-ttu-id="29a55-115">Est de l’erreur : {0}</span><span class="sxs-lookup"><span data-stu-id="29a55-115">The error is : {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="29a55-116">Explication</span><span class="sxs-lookup"><span data-stu-id="29a55-116">Explanation</span></span>  
 <span data-ttu-id="29a55-117">Cet événement d'erreur/d'avertissement/d'informations indique que l'orchestration de traitement par lot n'a pas pu ajouter un document informatisé à un échange traité par lot car la validation du document informatisé effectuée par l'orchestration de traitement par lot a échoué.</span><span class="sxs-lookup"><span data-stu-id="29a55-117">This Error/Warning/Information event indicates that the batching orchestration could not add a transaction set to a batched interchange because the transaction set failed the validation performed by the batching orchestration.</span></span> <span data-ttu-id="29a55-118">L'échange sera généré sans le document informatisé dont la validation a échoué.</span><span class="sxs-lookup"><span data-stu-id="29a55-118">The interchange will be generated without the transaction set that failed validation.</span></span> <span data-ttu-id="29a55-119">L'orchestration de traitement par lot définit la propriété de contexte EDI.BatchElementValidationFailure sur « True ».</span><span class="sxs-lookup"><span data-stu-id="29a55-119">The batching orchestration sets the EDI.BatchElementValidationFailure context property to "True".</span></span> <span data-ttu-id="29a55-120">L'orchestration BatchSuspend récupère le message en fonction de cette propriété de contexte et publie les informations sur l'erreur avant d'être interrompue.</span><span class="sxs-lookup"><span data-stu-id="29a55-120">The BatchSuspend orchestration picks up the message based upon that context property, posts error information, and then is suspended.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="29a55-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="29a55-121">User Action</span></span>  
 <span data-ttu-id="29a55-122">Pour résoudre cette erreur, expliquez le problème à l'expéditeur du document informatisé, en fonction des indications du message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="29a55-122">To resolve this error, indicate to the sender of the transaction set what error occurred, as indicated in the error message.</span></span> <span data-ttu-id="29a55-123">Demandez à l'expéditeur de résoudre le problème qui a provoqué l'échec de la validation, puis de renvoyer le document informatisé.</span><span class="sxs-lookup"><span data-stu-id="29a55-123">Have the sender resolve the issue that caused it to fail validation, and then resend the transaction set.</span></span>
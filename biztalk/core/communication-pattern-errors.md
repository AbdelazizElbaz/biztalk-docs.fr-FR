---
title: "Erreurs de modèle de communication | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06656073-9bae-4d6f-98ae-2714a72ee79c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36677694b8f2d0973c04d942a196d055b696bd5c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="communication-pattern-errors"></a><span data-ttu-id="e4d9e-102">Erreurs en relation avec les modèles de communication</span><span class="sxs-lookup"><span data-stu-id="e4d9e-102">Communication Pattern Errors</span></span>
<span data-ttu-id="e4d9e-103">Informations sur le diagnostic et résolution des erreurs de modèle de Communication WCF.</span><span class="sxs-lookup"><span data-stu-id="e4d9e-103">Information for diagnosing and resolving WCF Communication Pattern errors.</span></span>  

## <a name="fault-messages-are-not-supported-on-one-way-ports"></a><span data-ttu-id="e4d9e-104">Les messages d'erreur ne sont pas pris en charge sur les ports unidirectionnels</span><span class="sxs-lookup"><span data-stu-id="e4d9e-104">Fault messages are not supported on one-way ports</span></span>
  
||<span data-ttu-id="e4d9e-105">Détails de l’erreur</span><span class="sxs-lookup"><span data-stu-id="e4d9e-105">Error details</span></span>|  
|-|-|  
|<span data-ttu-id="e4d9e-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e4d9e-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e4d9e-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e4d9e-107">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="e4d9e-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e4d9e-108">Event ID</span></span>|<span data-ttu-id="e4d9e-109">0</span><span class="sxs-lookup"><span data-stu-id="e4d9e-109">0</span></span>|  
|<span data-ttu-id="e4d9e-110">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e4d9e-110">Event Source</span></span>|<span data-ttu-id="e4d9e-111">0</span><span class="sxs-lookup"><span data-stu-id="e4d9e-111">0</span></span>|  
|<span data-ttu-id="e4d9e-112">Composant</span><span class="sxs-lookup"><span data-stu-id="e4d9e-112">Component</span></span>|<span data-ttu-id="e4d9e-113">0</span><span class="sxs-lookup"><span data-stu-id="e4d9e-113">0</span></span>|  
|<span data-ttu-id="e4d9e-114">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e4d9e-114">Symbolic Name</span></span>|<span data-ttu-id="e4d9e-115">0</span><span class="sxs-lookup"><span data-stu-id="e4d9e-115">0</span></span>|  
|<span data-ttu-id="e4d9e-116">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e4d9e-116">Message Text</span></span>|<span data-ttu-id="e4d9e-117">Les messages d'erreur ne sont pas pris en charge sur les ports unidirectionnels.</span><span class="sxs-lookup"><span data-stu-id="e4d9e-117">Fault messages are not supported on one-way ports.</span></span> <span data-ttu-id="e4d9e-118">Corrigez le type de port de description « {0} » de service « {{1} », puis réexécutez l’Assistant</span><span class="sxs-lookup"><span data-stu-id="e4d9e-118">Correct service description "{0}" port type "{1}" and rerun the wizard</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e4d9e-119">Explication</span><span class="sxs-lookup"><span data-stu-id="e4d9e-119">Explanation</span></span>  
 <span data-ttu-id="e4d9e-120">Cette erreur indique que le service que vous tentez d'utiliser est unidirectionnel et qu'une erreur a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e4d9e-120">This error indicates the service trying to be consumed is a one-way service and has the fault specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e4d9e-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e4d9e-121">User Action</span></span>  
 <span data-ttu-id="e4d9e-122">Pour corriger le service, passez du modèle de communication unidirectionnel au modèle de communication de requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="e4d9e-122">Correct the service by switching the communication pattern from one-way to request-response.</span></span> <span data-ttu-id="e4d9e-123">Vous pouvez également supprimer l'erreur dans le code.</span><span class="sxs-lookup"><span data-stu-id="e4d9e-123">Or remove the fault in the code.</span></span>
 
 
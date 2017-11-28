---
title: Envoyer les erreurs | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3cf61c82-ad48-4555-af53-fb841fd0f503
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67741af0520d990be9a552685c8319aa6a5ae881
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="send-errors"></a><span data-ttu-id="6f7f6-102">Erreurs en relation avec l'envoi</span><span class="sxs-lookup"><span data-stu-id="6f7f6-102">Send Errors</span></span>
<span data-ttu-id="6f7f6-103">Informations sur le diagnostic et résolution des erreurs d’envoi WCF.</span><span class="sxs-lookup"><span data-stu-id="6f7f6-103">Information for diagnosing and resolving WCF Send errors.</span></span>  
  
## <a name="failed-to-generate-odx-file"></a><span data-ttu-id="6f7f6-104">Impossible de générer le fichier ODX</span><span class="sxs-lookup"><span data-stu-id="6f7f6-104">Failed to generate ODX file</span></span>

||<span data-ttu-id="6f7f6-105">Détails de l’erreur</span><span class="sxs-lookup"><span data-stu-id="6f7f6-105">Error details</span></span>|  
|-|-|  
|<span data-ttu-id="6f7f6-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="6f7f6-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6f7f6-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="6f7f6-107">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="6f7f6-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6f7f6-108">Event ID</span></span>|<span data-ttu-id="6f7f6-109">0</span><span class="sxs-lookup"><span data-stu-id="6f7f6-109">0</span></span>|  
|<span data-ttu-id="6f7f6-110">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="6f7f6-110">Event Source</span></span>|<span data-ttu-id="6f7f6-111">0</span><span class="sxs-lookup"><span data-stu-id="6f7f6-111">0</span></span>|  
|<span data-ttu-id="6f7f6-112">Composant</span><span class="sxs-lookup"><span data-stu-id="6f7f6-112">Component</span></span>|<span data-ttu-id="6f7f6-113">0</span><span class="sxs-lookup"><span data-stu-id="6f7f6-113">0</span></span>|  
|<span data-ttu-id="6f7f6-114">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="6f7f6-114">Symbolic Name</span></span>|<span data-ttu-id="6f7f6-115">0</span><span class="sxs-lookup"><span data-stu-id="6f7f6-115">0</span></span>|  
|<span data-ttu-id="6f7f6-116">Texte du message</span><span class="sxs-lookup"><span data-stu-id="6f7f6-116">Message Text</span></span>|<span data-ttu-id="6f7f6-117">Impossible de générer le fichier ODX</span><span class="sxs-lookup"><span data-stu-id="6f7f6-117">Failed to generate ODX file</span></span>|  
  
### <a name="explanation"></a><span data-ttu-id="6f7f6-118">Explication</span><span class="sxs-lookup"><span data-stu-id="6f7f6-118">Explanation</span></span>  
 <span data-ttu-id="6f7f6-119">Cette erreur indique qu'une erreur s'est produite lors de l'utilisation du service.</span><span class="sxs-lookup"><span data-stu-id="6f7f6-119">This error indicates there was an error in consuming the service.</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="6f7f6-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6f7f6-120">User Action</span></span>  
 <span data-ttu-id="6f7f6-121">Vérifiez que le service WCF possède une méthode Web valide et que des métadonnées sont hébergées (si vous en êtes le propriétaire).</span><span class="sxs-lookup"><span data-stu-id="6f7f6-121">Check that the service has valid Web Method and that metadata is hosted (if you own the WCF services).</span></span> <span data-ttu-id="6f7f6-122">Sinon, contactez le fournisseur de services.</span><span class="sxs-lookup"><span data-stu-id="6f7f6-122">Otherwise, contact the service provider.</span></span>  
  
 <span data-ttu-id="6f7f6-123">Pour plus d’informations sur l’utilisation des services WCF, consultez [Considérations lors de la consommation de Services WCF avec les adaptateurs d’envoi WCF](../core/considerations-when-consuming-wcf-services-with-the-wcf-send-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="6f7f6-123">For additional information on consuming WCF services, see [Considerations When Consuming WCF Services with the WCF Send Adapters](../core/considerations-when-consuming-wcf-services-with-the-wcf-send-adapters.md).</span></span>
 
## <a name="response-message-body-was-not-read"></a><span data-ttu-id="6f7f6-124">Impossible de lire le corps du message de réponse</span><span class="sxs-lookup"><span data-stu-id="6f7f6-124">Response message body was not read</span></span>
  
||<span data-ttu-id="6f7f6-125">Détails de l’erreur</span><span class="sxs-lookup"><span data-stu-id="6f7f6-125">Error details</span></span>|  
|-|-|  
|<span data-ttu-id="6f7f6-126">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="6f7f6-126">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6f7f6-127">Version du produit</span><span class="sxs-lookup"><span data-stu-id="6f7f6-127">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="6f7f6-128">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6f7f6-128">Event ID</span></span>|<span data-ttu-id="6f7f6-129">0</span><span class="sxs-lookup"><span data-stu-id="6f7f6-129">0</span></span>|  
|<span data-ttu-id="6f7f6-130">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="6f7f6-130">Event Source</span></span>|<span data-ttu-id="6f7f6-131">0</span><span class="sxs-lookup"><span data-stu-id="6f7f6-131">0</span></span>|  
|<span data-ttu-id="6f7f6-132">Composant</span><span class="sxs-lookup"><span data-stu-id="6f7f6-132">Component</span></span>|<span data-ttu-id="6f7f6-133">0</span><span class="sxs-lookup"><span data-stu-id="6f7f6-133">0</span></span>|  
|<span data-ttu-id="6f7f6-134">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="6f7f6-134">Symbolic Name</span></span>|<span data-ttu-id="6f7f6-135">0</span><span class="sxs-lookup"><span data-stu-id="6f7f6-135">0</span></span>|  
|<span data-ttu-id="6f7f6-136">Texte du message</span><span class="sxs-lookup"><span data-stu-id="6f7f6-136">Message Text</span></span>|<span data-ttu-id="6f7f6-137">Impossible de lire le corps du message de réponse. (Ceci peut indiquer que la connexion a été fermée.)</span><span class="sxs-lookup"><span data-stu-id="6f7f6-137">The response message body was not read  (This may indicate the connection has been closed.)</span></span>|  
  
### <a name="explanation"></a><span data-ttu-id="6f7f6-138">Explication</span><span class="sxs-lookup"><span data-stu-id="6f7f6-138">Explanation</span></span>  
 <span data-ttu-id="6f7f6-139">Le client a peut-être été déconnecté avant l'envoi du message de réponse.</span><span class="sxs-lookup"><span data-stu-id="6f7f6-139">The client may be disconnected before the response message is sent back.</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="6f7f6-140">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6f7f6-140">User Action</span></span>  
 <span data-ttu-id="6f7f6-141">Vérifiez la connectivité client.</span><span class="sxs-lookup"><span data-stu-id="6f7f6-141">Check the client connectivity.</span></span> <span data-ttu-id="6f7f6-142">La procédure à suivre et les suites de l'action dépendent du type de port.</span><span class="sxs-lookup"><span data-stu-id="6f7f6-142">The steps taken, and the extent of the action, will depend on the port type.</span></span>   
<span data-ttu-id="6f7f6-143">Pour plus d’informations, consultez [outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="6f7f6-143">For further information, see [Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md).</span></span>
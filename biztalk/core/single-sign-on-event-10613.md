---
title: "Single Sign-On : Événement 10613 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a87ca19-24a0-4cf8-984f-2f70d7b5018c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf7230a0d6400a7265ef9f3cedb6bb47cc23aade
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10613"></a><span data-ttu-id="a43b9-102">Single Sign-On : Événement 10613</span><span class="sxs-lookup"><span data-stu-id="a43b9-102">Single Sign-On: Event 10613</span></span>
## <a name="details"></a><span data-ttu-id="a43b9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a43b9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a43b9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a43b9-104">Product Name</span></span>|<span data-ttu-id="a43b9-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="a43b9-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a43b9-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a43b9-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a43b9-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a43b9-107">Event ID</span></span>|<span data-ttu-id="a43b9-108">10613</span><span class="sxs-lookup"><span data-stu-id="a43b9-108">10613</span></span>|  
|<span data-ttu-id="a43b9-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a43b9-109">Event Source</span></span>|<span data-ttu-id="a43b9-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a43b9-110">ENTSSO</span></span>|  
|<span data-ttu-id="a43b9-111">Composant</span><span class="sxs-lookup"><span data-stu-id="a43b9-111">Component</span></span>|<span data-ttu-id="a43b9-112">Néant</span><span class="sxs-lookup"><span data-stu-id="a43b9-112">N/A</span></span>|  
|<span data-ttu-id="a43b9-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a43b9-113">Symbolic Name</span></span>|<span data-ttu-id="a43b9-114">SSO_ERROR_RPC_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="a43b9-114">SSO_ERROR_RPC_CALLBACK</span></span>|  
|<span data-ttu-id="a43b9-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a43b9-115">Message Text</span></span>|<span data-ttu-id="a43b9-116">Accès refusé au serveur SSO.%r</span><span class="sxs-lookup"><span data-stu-id="a43b9-116">SSO server access denied.%r</span></span><br /><br /> <span data-ttu-id="a43b9-117">L’utilisateur client : %1 %r</span><span class="sxs-lookup"><span data-stu-id="a43b9-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="a43b9-118">Informations sur les appels RPC : %2 : %3 %r</span><span class="sxs-lookup"><span data-stu-id="a43b9-118">RPC call information: %2:%3%r</span></span><br /><br /> <span data-ttu-id="a43b9-119">Code d’erreur : %4</span><span class="sxs-lookup"><span data-stu-id="a43b9-119">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a43b9-120">Explication</span><span class="sxs-lookup"><span data-stu-id="a43b9-120">Explanation</span></span>  
 <span data-ttu-id="a43b9-121">Un appel effectué depuis un client au serveur SSO n'a pas été accepté.</span><span class="sxs-lookup"><span data-stu-id="a43b9-121">A call was made from a client to the SSO Server but was not accepted.</span></span> <span data-ttu-id="a43b9-122">Cela peut être dû à de nombreuses raisons, par exemple un protocole incorrect ou des autorisations de sécurité insuffisantes au niveau du client.</span><span class="sxs-lookup"><span data-stu-id="a43b9-122">This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions on the client.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a43b9-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a43b9-123">User Action</span></span>  
 <span data-ttu-id="a43b9-124">Notez les informations contenues dans ce message et les informations appropriées dans le journal des événements, puis contactez les Services de Support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a43b9-124">Note the information in this message, and any relevant information in the event log, and contact Microsoft Product Support Services.</span></span>
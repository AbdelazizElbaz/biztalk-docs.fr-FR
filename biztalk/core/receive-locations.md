---
title: "Emplacements de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, properties
- receive locations, about receive locations
- receive locations
- receive locations, receive location types
ms.assetid: be5f7e5d-b63f-42f6-985e-895ba3912d34
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9866edd5dfa6f953c4e847f191891bd7e6bc25ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-locations"></a><span data-ttu-id="a9cbe-102">Emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="a9cbe-102">Receive Locations</span></span>
<span data-ttu-id="a9cbe-103">La création d'un emplacement de réception implique la spécification d'une adresse à laquelle parviennent les messages entrants et du pipeline qui traite les messages reçus à cette adresse.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-103">Creating a receive location involves specifying an address at which inbound messages arrive and the messaging pipeline that processes the message received at that address.</span></span> <span data-ttu-id="a9cbe-104">Seuls les administrateurs peuvent créer et activer des emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-104">Only administrators can create and enable receive locations.</span></span>  
  
 <span data-ttu-id="a9cbe-105">Un administrateur utilise la console Administration de BizTalk pour créer des emplacements de réception, les lier à des orchestrations, les activer et les désactiver, et définir leurs propriétés générales.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-105">An administrator uses the BizTalk Administration Console to create receive locations, bind receive locations to orchestrations, enable receive locations, disable receive locations, and set global properties for receive locations.</span></span>  
  
 <span data-ttu-id="a9cbe-106">Un administrateur (utilisant la console Administration de BizTalk) suit les étapes ci-dessous pour créer un emplacement de réception :</span><span class="sxs-lookup"><span data-stu-id="a9cbe-106">An administrator (using the BizTalk Administration Console) follows these steps to create a receive location:</span></span>  
  
1.  <span data-ttu-id="a9cbe-107">Il crée un emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-107">Creates a receive location.</span></span>  
  
2.  <span data-ttu-id="a9cbe-108">Il associe l'emplacement de réception à un hôte.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-108">Associates the receive location with a host.</span></span>  
  
3.  <span data-ttu-id="a9cbe-109">Il lie l'emplacement de réception à une orchestration.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-109">Binds the receive location to an orchestration.</span></span>  
  
4.  <span data-ttu-id="a9cbe-110">Il active l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-110">Enables the receive location.</span></span>  
  
5.  <span data-ttu-id="a9cbe-111">L'emplacement de réception reçoit des messages.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-111">The receive location receives messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9cbe-112">Les modifications apportées aux emplacements de réception à l'aide de Windows Management Instrumentation (WMI) ont des répercussions sur l'affichage de ces emplacements dans la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-112">Changes to receive locations made by using Windows Management Instrumentation (WMI) affect how receive locations appear in the BizTalk Administration Console.</span></span> <span data-ttu-id="a9cbe-113">Par exemple, si un administrateur utilise WMI pour créer un emplacement de réception, celui-ci s'affiche dans la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-113">For example, if an administrator uses WMI to create a new receive location, that receive location appears in the BizTalk Administration Console.</span></span> <span data-ttu-id="a9cbe-114">De même, si un administrateur supprime un emplacement de réception, celui-ci n'apparaît plus dans la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-114">Similarly, if an administrator deletes a receive location, the receive location disappears from the BizTalk Administration Console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a9cbe-115">Le nom de chaque emplacement de réception doit être unique.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-115">Each receive location must have a unique name.</span></span> <span data-ttu-id="a9cbe-116">Deux emplacements de réception ne peut pas avoir le même nom dans le même [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]déploiement.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-116">Two receive locations cannot have the same name in the same [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]deployment.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a9cbe-117">Il est conseillé de définir des listes de contrôle d'accès renforcées dans l'emplacement de dépôt des emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-117">We recommend that you set strong access control lists (ACL) in the drop location for the receive locations.</span></span> <span data-ttu-id="a9cbe-118">Par exemple, vous devez définir des listes de contrôle d'accès renforcées pour le répertoire dans lequel l'emplacement de réception des fichiers sélectionne des messages, afin que seuls les utilisateurs autorisés puissent déposer des messages dans cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-118">For example, you must set strong ACLs for the directory where the file receive location picks up messages, so that only authorized users can drop messages in this location.</span></span>  
  
## <a name="receive-location-types"></a><span data-ttu-id="a9cbe-119">Types d'emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="a9cbe-119">Receive Location Types</span></span>  
 <span data-ttu-id="a9cbe-120">Il existe deux types d'emplacements de réception :</span><span class="sxs-lookup"><span data-stu-id="a9cbe-120">There are two types of receive locations</span></span>  
  
-   <span data-ttu-id="a9cbe-121">Unidirectionnel :</span><span class="sxs-lookup"><span data-stu-id="a9cbe-121">One-way.</span></span> <span data-ttu-id="a9cbe-122">utilisé pour les applications qui suppriment un message et n'attendent pas de réponse synchrone.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-122">Used for applications that drop off a message and do not wait for a synchronous reply.</span></span>  
  
-   <span data-ttu-id="a9cbe-123">Requête-réponse :</span><span class="sxs-lookup"><span data-stu-id="a9cbe-123">Request-response.</span></span> <span data-ttu-id="a9cbe-124">utilisé avec les applications qui exigent une réponse à un message.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-124">Used with applications that require a response to a message.</span></span>  
  
## <a name="receive-location-properties"></a><span data-ttu-id="a9cbe-125">Propriétés des emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="a9cbe-125">Receive Location Properties</span></span>  
 <span data-ttu-id="a9cbe-126">Les emplacements de réception sont associés à des propriétés globales et propres à l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-126">Receive locations have global and adapter-specific properties.</span></span> <span data-ttu-id="a9cbe-127">Les administrateurs, à l’aide de la Console Administration de BizTalk, définir des propriétés globales pour tous les emplacements de réception associés à une carte spécifique.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-127">Administrators, using the BizTalk Administration Console, set global properties for all of the receive locations associated with a specific adapter.</span></span>  
  
 <span data-ttu-id="a9cbe-128">Les modifications sont apportées de manière séquentielle aux propriétés des emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-128">Changes to receive location properties happen sequentially.</span></span> <span data-ttu-id="a9cbe-129">Si un développeur de solutions modifie une valeur de propriété pour spécifique à un emplacement de réception, la nouvelle valeur remplace la valeur de propriété globale pour cet emplacement de réception que définie par l’administrateur dans la Console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a9cbe-129">If a solutions developer modifies a property value for a specific receive location, the new property value overrides the global property value for that receive location that the administrator set in the BizTalk Administration Console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9cbe-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9cbe-130">See Also</span></span>  
 <span data-ttu-id="a9cbe-131">[La gestion des emplacements de réception](../core/managing-receive-locations.md) </span><span class="sxs-lookup"><span data-stu-id="a9cbe-131">[Managing Receive Locations](../core/managing-receive-locations.md) </span></span>  
 [<span data-ttu-id="a9cbe-132">Artefacts</span><span class="sxs-lookup"><span data-stu-id="a9cbe-132">Artifacts</span></span>](../core/artifacts.md)
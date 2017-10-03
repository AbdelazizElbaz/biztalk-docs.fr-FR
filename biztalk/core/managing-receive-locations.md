---
title: "Gérer les emplacements de réception | Documents Microsoft"
description: "Travail avec les emplacements de réception dans BizTalk Server, y compris la création, modification des propriétés, l’activation et la désactivation de, ajout de certificats et suppression"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b3ff581-e7e9-4a6e-a9ea-70c55a3b9318
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ddaf0756eb2f0b78ddb851d13ff1acab12c6a83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-receive-locations"></a><span data-ttu-id="b9cdf-103">Gérer les emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="b9cdf-103">Manage Receive Locations</span></span>

## <a name="overview"></a><span data-ttu-id="b9cdf-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="b9cdf-104">Overview</span></span>
<span data-ttu-id="b9cdf-105">Cette section fournit des instructions sur la création, la configuration et la gestion des emplacements de réception pour une application BizTalk à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b9cdf-105">This section provides instructions on creating, configuring, and managing receive locations for a BizTalk application by using the BizTalk Server Administration console.</span></span> <span data-ttu-id="b9cdf-106">Un emplacement de réception est composé d'une adresse à laquelle parviennent les messages entrants et du pipeline qui traite les messages reçus à cette adresse.</span><span class="sxs-lookup"><span data-stu-id="b9cdf-106">A receive location consists of an address at which inbound messages arrive and the messaging pipeline that processes the message received at that address.</span></span> <span data-ttu-id="b9cdf-107">Pour plus d’informations, consultez [emplacements de réception](../core/receive-locations.md).</span><span class="sxs-lookup"><span data-stu-id="b9cdf-107">For background information, see [Receive Locations](../core/receive-locations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9cdf-108">Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives.</span><span class="sxs-lookup"><span data-stu-id="b9cdf-108">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="b9cdf-109">Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="b9cdf-109">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 
  
## <a name="next-steps"></a><span data-ttu-id="b9cdf-110">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b9cdf-110">Next steps</span></span> 
  
-   [<span data-ttu-id="b9cdf-111">Créer un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="b9cdf-111">Create a Receive Location</span></span>](../core/how-to-create-a-receive-location.md)  
  
-   [<span data-ttu-id="b9cdf-112">Modifier les propriétés d’un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="b9cdf-112">Edit the Properties of a Receive Location</span></span>](../core/how-to-edit-the-properties-of-a-receive-location.md)  
  
-   [<span data-ttu-id="b9cdf-113">Configurer les propriétés de Pipeline par instance d’un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="b9cdf-113">Configure Per-instance Pipeline Properties for a Receive Location</span></span>](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md)  
  
-   [<span data-ttu-id="b9cdf-114">Activer un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="b9cdf-114">Enable a Receive Location</span></span>](../core/how-to-enable-a-receive-location.md)  
  
-   [<span data-ttu-id="b9cdf-115">Désactiver un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="b9cdf-115">Disable a Receive Location</span></span>](../core/how-to-disable-a-receive-location.md)  
  
-   [<span data-ttu-id="b9cdf-116">Configurer la planification pour un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="b9cdf-116">Configure Scheduling for a Receive Location</span></span>](../core/how-to-configure-scheduling-for-a-receive-location.md)  
  
-   [<span data-ttu-id="b9cdf-117">Attribuer un certificat à un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="b9cdf-117">Assign a Certificate to a Receive Location</span></span>](../core/how-to-assign-a-certificate-to-a-receive-location.md)  
  
-   [<span data-ttu-id="b9cdf-118">Suppression d’un certificat d’un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="b9cdf-118">Remove a Certificate from a Receive Location</span></span>](../core/how-to-remove-a-certificate-from-a-receive-location.md)  
  
-   [<span data-ttu-id="b9cdf-119">Supprimer un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="b9cdf-119">Delete a Receive Location</span></span>](../core/how-to-delete-a-receive-location.md)
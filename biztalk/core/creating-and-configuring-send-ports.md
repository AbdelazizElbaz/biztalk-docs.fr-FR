---
title: "Liens rapides pour créer et configurer les ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b26ed07-b7ed-48a5-9bd9-dfba9c1d3c02
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31361c9a6dff1d35c21bede4a82d513c6a073218
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-configuring-send-ports"></a><span data-ttu-id="e18d0-102">Création et configuration des ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="e18d0-102">Creating and Configuring Send Ports</span></span>

## <a name="overview"></a><span data-ttu-id="e18d0-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="e18d0-103">Overview</span></span>
<span data-ttu-id="e18d0-104">Cette section fournit des instructions sur la création et la configuration de ports d'envoi pour une application BizTalk à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e18d0-104">This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to create and configure send ports for a BizTalk application.</span></span> <span data-ttu-id="e18d0-105">Un port d'envoi est un emplacement vers lequel les messages sont envoyés ou à partir duquel ces derniers sont reçus. Il est identifié de manière unique par son nom.</span><span class="sxs-lookup"><span data-stu-id="e18d0-105">A send port is a location to which messages are sent or from which messages are received and is uniquely identified by its name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e18d0-106">Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives.</span><span class="sxs-lookup"><span data-stu-id="e18d0-106">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="e18d0-107">Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="e18d0-107">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="e18d0-108">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e18d0-108">Next steps</span></span>
  
-   [<span data-ttu-id="e18d0-109">Créer un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="e18d0-109">Create a Send Port</span></span>](../core/how-to-create-a-send-port2.md)  
  
-   [<span data-ttu-id="e18d0-110">Afficher les informations d’Instance pour un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="e18d0-110">View Instance Information for a Send Port</span></span>](../core/how-to-view-instance-information-for-a-send-port.md)  
  
-   [<span data-ttu-id="e18d0-111">Configurer les propriétés de Pipeline par Instance pour un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="e18d0-111">Configure Per-Instance Pipeline Properties for a Send Port</span></span>](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md)  
  
-   [<span data-ttu-id="e18d0-112">Ajouter un Port d’envoi à un groupe de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="e18d0-112">Add a Send Port to a Send Port Group</span></span>](../core/how-to-add-a-send-port-to-a-send-port-group.md)  
  
-   [<span data-ttu-id="e18d0-113">Supprimer un Port d’envoi à partir d’un groupe de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="e18d0-113">Remove a Send Port from a Send Port Group</span></span>](../core/how-to-remove-a-send-port-from-a-send-port-group.md)  
  
-   [<span data-ttu-id="e18d0-114">Configurer des Options avancées pour un Port d’envoi de Transport</span><span class="sxs-lookup"><span data-stu-id="e18d0-114">Configure Transport Advanced Options for a Send Port</span></span>](../core/how-to-configure-transport-advanced-options-for-a-send-port.md)  
  
-   [<span data-ttu-id="e18d0-115">Configurer les Options de Transport secondaire pour un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="e18d0-115">Configure Backup Transport Options for a Send Port</span></span>](../core/how-to-configure-backup-transport-options-for-a-send-port.md)  
  
-   [<span data-ttu-id="e18d0-116">Configurer les mappages entrants pour un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="e18d0-116">Configure Inbound Maps for a Send Port</span></span>](../core/how-to-configure-inbound-maps-for-a-send-port.md)  
  
-   [<span data-ttu-id="e18d0-117">Configurer les mappages sortants pour un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="e18d0-117">Configure Outbound Maps for a Send Port</span></span>](../core/how-to-configure-outbound-maps-for-a-send-port.md)  
  
-   [<span data-ttu-id="e18d0-118">Configurer des filtres pour un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="e18d0-118">Configure Filters for a Send Port</span></span>](../core/how-to-configure-filters-for-a-send-port.md)  
  
-   [<span data-ttu-id="e18d0-119">Attribuer un certificat à un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="e18d0-119">Assign a Certificate to a Send Port</span></span>](../core/how-to-assign-a-certificate-to-a-send-port.md)  
  
-   [<span data-ttu-id="e18d0-120">Suppression d’un certificat à partir d’un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="e18d0-120">Remove a Certificate from a Send Port</span></span>](../core/how-to-remove-a-certificate-from-a-send-port.md)  
  
-   [<span data-ttu-id="e18d0-121">Configurer le suivi d’un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="e18d0-121">Configure Tracking for a Send Port</span></span>](../core/how-to-configure-tracking-for-a-send-port.md)  
  
-   [<span data-ttu-id="e18d0-122">Supprimer un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="e18d0-122">Delete a Send Port</span></span>](../core/how-to-delete-a-send-port.md)
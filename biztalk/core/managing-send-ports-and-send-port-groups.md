---
title: "Gérer les Ports d’envoi et groupes de ports d’envoi | Documents Microsoft"
description: "Des liens pour créer, configurer, inscrire, désinscrire et démarrer et arrêter des ports d’envoi dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db45f9f9-b32a-4b9c-a3bf-8c271d0f0cf9
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 928160ed5b67602c8fc8d9d646459bf2425d7a01
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-send-ports-and-send-port-groups"></a><span data-ttu-id="505bf-103">Gérer les Ports d’envoi et groupes de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="505bf-103">Manage Send Ports and Send Port Groups</span></span>

## <a name="overview"></a><span data-ttu-id="505bf-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="505bf-104">Overview</span></span>
<span data-ttu-id="505bf-105">Cette section fournit des instructions sur l'utilisation de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour créer, configurer et gérer des ports d'envoi et des groupes de ports d'envoi dans une application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="505bf-105">This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to create, configure, and manage send ports and send port groups in a BizTalk application.</span></span> <span data-ttu-id="505bf-106">Un port d'envoi spécifie l'emplacement vers lequel les messages sont envoyés et éventuellement, l'emplacement à partir duquel les réponses sont reçues.</span><span class="sxs-lookup"><span data-stu-id="505bf-106">A send port specifies the location to which messages are sent and optionally responses are received.</span></span> <span data-ttu-id="505bf-107">Lorsqu’un message est envoyé à un port d’envoi, une nouvelle instance du service de port d’envoi est créée, qui est appelé un *l’instance de service*.</span><span class="sxs-lookup"><span data-stu-id="505bf-107">Any time a message is sent to a send port, a new instance of the send port service is created, which is called a *service instance*.</span></span>  
  
 <span data-ttu-id="505bf-108">Un groupe de ports d'envoi est un groupe logique de ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="505bf-108">A send port group is a logical grouping of send ports.</span></span> <span data-ttu-id="505bf-109">Lorsqu'un message est envoyé à un groupe de ports d'envoi, il est acheminé vers tous les ports d'envoi associés.</span><span class="sxs-lookup"><span data-stu-id="505bf-109">When a message is sent to a send port group, it is routed to all of the associated send ports.</span></span>  <span data-ttu-id="505bf-110">Pour plus d’informations générales sur les ports d’envoi et groupes de ports d’envoi, consultez [Ports d’envoi et groupes de ports d’envoi](../core/send-ports-and-send-port-groups.md).</span><span class="sxs-lookup"><span data-stu-id="505bf-110">For background information about send ports and send port groups, see [Send Ports and Send Port Groups](../core/send-ports-and-send-port-groups.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="505bf-111">Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives.</span><span class="sxs-lookup"><span data-stu-id="505bf-111">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="505bf-112">Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="505bf-112">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
> [!NOTE]
>  <span data-ttu-id="505bf-113">Lorsqu'il développe une application BizTalk, le développeur peut utiliser les outils de conception BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], tels que le Concepteur d'orchestration, pour créer et configurer des ports d'envoi et des groupes de ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="505bf-113">While developing a BizTalk application, the developer can use BizTalk design tools in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], such as Orchestration Designer, to create and configure send ports and send port groups.</span></span> <span data-ttu-id="505bf-114">Pour plus d’informations, consultez [à l’aide des Ports dans les Orchestrations](../core/using-ports-in-orchestrations.md).</span><span class="sxs-lookup"><span data-stu-id="505bf-114">For more information, see [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="505bf-115">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="505bf-115">Next steps</span></span>
  
-   [<span data-ttu-id="505bf-116">Création et configuration des Ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="505bf-116">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)  
  
-   [<span data-ttu-id="505bf-117">Création et configuration des groupes de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="505bf-117">Creating and Configuring Send Port Groups</span></span>](../core/creating-and-configuring-send-port-groups.md)  
  
-   [<span data-ttu-id="505bf-118">Inscrire un Port d’envoi ou un groupe de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="505bf-118">Enlist a Send Port or Send Port Group</span></span>](../core/how-to-enlist-a-send-port-or-send-port-group.md)  
  
-   [<span data-ttu-id="505bf-119">Désinscrire un Port d’envoi ou un groupe de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="505bf-119">Unenlist a Send Port or Send Port Group</span></span>](../core/how-to-unenlist-a-send-port-or-send-port-group.md)  
  
-   [<span data-ttu-id="505bf-120">Démarrer un Port d’envoi ou un groupe de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="505bf-120">Start a Send Port or Send Port Group</span></span>](../core/how-to-start-a-send-port-or-send-port-group.md)  
  
-   [<span data-ttu-id="505bf-121">Arrêter un Port d’envoi ou un groupe de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="505bf-121">Stop a Send Port or Send Port Group</span></span>](../core/how-to-stop-a-send-port-or-send-port-group.md)
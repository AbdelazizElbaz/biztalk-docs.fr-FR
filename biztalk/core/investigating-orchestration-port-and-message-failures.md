---
title: "Enquête sur les échecs de messages d’Orchestration et Port | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Administration Console [BizTalk Server], Group Hub page
- orchestrations, errors
- errors, ports
- errors, orchestrations
- Group Hub page [Administration Console]
- ports, errors
- MessageBox database, accessing data
- errors, messages
- messages, errors
- data, MessageBox database
ms.assetid: 50b0d272-2d48-4e0f-82ce-6ecc7a65b064
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94417135f707d77377686745e35e6fb1f02087b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="investigating-orchestration-port-and-message-failures"></a><span data-ttu-id="3582a-102">Examen des échecs relatifs aux orchestrations, aux ports et aux messages</span><span class="sxs-lookup"><span data-stu-id="3582a-102">Investigating Orchestration, Port, and Message Failures</span></span>
<span data-ttu-id="3582a-103">La page Hub du groupe de la console Administration de BizTalk Server permet de rechercher les causes des échecs relatifs aux orchestrations, aux ports et aux messages.</span><span class="sxs-lookup"><span data-stu-id="3582a-103">You can use the Group Hub page in the BizTalk Server Administration Console to investigate orchestration, port, and message failures.</span></span> <span data-ttu-id="3582a-104">Cette page permet de connaître l'état actuel en temps réel du système, par l'accès à la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="3582a-104">The Group Hub page provides access to the current real-time state of the system, accessing data in the MessageBox database.</span></span> <span data-ttu-id="3582a-105">Vous pouvez afficher toutes les instances de service telles que les orchestrations, les ports et la messagerie, ainsi que les messages qui leur sont associés.</span><span class="sxs-lookup"><span data-stu-id="3582a-105">You can view all service instances such as orchestrations, ports, and messaging, along with their associated messages.</span></span> <span data-ttu-id="3582a-106">La page Hub du groupe vous permet d'effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="3582a-106">Using the Group Hub page you can:</span></span>  
  
-   <span data-ttu-id="3582a-107">afficher les instances de service en cours d'exécution telles que les orchestrations et la messagerie, ainsi que les messages qui leur sont associés ;</span><span class="sxs-lookup"><span data-stu-id="3582a-107">See currently running service instances such as orchestrations and messaging, and their associated messages.</span></span>  
  
-   <span data-ttu-id="3582a-108">rechercher dans la base de données MessageBox une vue des données actives et de l'état en temps réel du système ;</span><span class="sxs-lookup"><span data-stu-id="3582a-108">Look into the MessageBox database for a view of the current data and the real-time state of the system.</span></span>  
  
-   <span data-ttu-id="3582a-109">interrompre, terminer et reprendre les instances de service.</span><span class="sxs-lookup"><span data-stu-id="3582a-109">Suspend, terminate, and resume service instances.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3582a-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3582a-110">In This Section</span></span>  
  
-   [<span data-ttu-id="3582a-111">Échecs des orchestrations</span><span class="sxs-lookup"><span data-stu-id="3582a-111">Orchestration Failures</span></span>](../core/orchestration-failures.md)  
  
-   [<span data-ttu-id="3582a-112">Types d’échecs de Message</span><span class="sxs-lookup"><span data-stu-id="3582a-112">Types of Message Failures</span></span>](../core/types-of-message-failures.md)  
  
-   [<span data-ttu-id="3582a-113">Comment suspendre des Instances d’Orchestration ou des Ports</span><span class="sxs-lookup"><span data-stu-id="3582a-113">How to Suspend Orchestration Instances or Ports</span></span>](../core/how-to-suspend-orchestration-instances-or-ports.md)  
  
-   [<span data-ttu-id="3582a-114">Comment arrêter les Instances d’Orchestration suspendues</span><span class="sxs-lookup"><span data-stu-id="3582a-114">How to Terminate Suspended Orchestration Instances</span></span>](../core/how-to-terminate-suspended-orchestration-instances.md)  
  
-   [<span data-ttu-id="3582a-115">Comment reprendre les Instances d’Orchestration suspendues</span><span class="sxs-lookup"><span data-stu-id="3582a-115">How to Resume Suspended Orchestration Instances</span></span>](../core/how-to-resume-suspended-orchestration-instances.md)
---
title: "Basculement de serveur du Service de Bus BAM événement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f12378c8-09bb-45c1-ade1-d9b20131461f
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c1fafc3e97d9905a6efd0de8ff0f389c2a389bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-event-bus-service-server-failover"></a><span data-ttu-id="538d0-102">Basculement du serveur de service Bus d'événements BAM</span><span class="sxs-lookup"><span data-stu-id="538d0-102">BAM Event Bus Service Server Failover</span></span>
<span data-ttu-id="538d0-103">Le service Bus d'événements BAM inclut la logique de tolérance de pannes qui lui permet de récupérer et de redémarrer à partir d'une erreur inattendue sans perdre de données.</span><span class="sxs-lookup"><span data-stu-id="538d0-103">The BAM Event Bus service includes fault tolerance logic that enables it to recover and restart from an unexpected failure without losing any data.</span></span>  
  
 <span data-ttu-id="538d0-104">Lorsque vous activez le service Bus d'événements BAM sur plusieurs ordinateurs et que ce service échoue, la logique de basculement et de déplacement détecte cet état de fait et démarre automatiquement une nouvelle instance du service Bus d'événements BAM sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="538d0-104">When you enable the BAM Event Bus service on multiple computers, and the service fails, failover logic will detect that a BAM Event Bus service has terminated, and the logic automatically starts a new instance of the BAM Event Bus service on another computer.</span></span>  
  
 <span data-ttu-id="538d0-105">La figure suivante illustre comment le Bus d'événements BAM gère les défaillances d'ordinateurs ou de réseaux en effectuant un simple équilibrage de charge.</span><span class="sxs-lookup"><span data-stu-id="538d0-105">The following figure displays how the BAM Event Bus handles computer or network failures by performing simple load balancing.</span></span> <span data-ttu-id="538d0-106">Deux sources et une destination ont été configurées avant le démarrage du Bus d'événements BAM.</span><span class="sxs-lookup"><span data-stu-id="538d0-106">Two sources and one destination were configured before the BAM Event Bus service starts.</span></span>  
  
 ![](../core/media/ebiz-bam-admin-evntbuspoolfail.gif "ebiz_bam_admin_evntbuspoolfail")  
<span data-ttu-id="538d0-107">Comment le service Bus d'événements BAM effectue l'équilibrage de charge</span><span class="sxs-lookup"><span data-stu-id="538d0-107">How the BAM Event Bus service load balances</span></span>  
  
 <span data-ttu-id="538d0-108">Le service Bus d'événements BAM effectue l'équilibrage de charge comme suit :</span><span class="sxs-lookup"><span data-stu-id="538d0-108">The BAM Event Bus service load balances by performing the following:</span></span>  
  
-   <span data-ttu-id="538d0-109">**R : serveur1 traite les données d’événement de 2 sources (sessions)**.</span><span class="sxs-lookup"><span data-stu-id="538d0-109">**A: Server1 processes the event data from 2 sources (sessions)**.</span></span> <span data-ttu-id="538d0-110">Avant qu'une instance du service Bus d'événements BAM soit créée sur Serveur2, une instance d'orchestration du bus d'événements BAM est créée sur Serveur1.</span><span class="sxs-lookup"><span data-stu-id="538d0-110">Before an instance of the BAM Event Bus service is created on Server2, a BAM Event Bus orchestration instance is created on Server1.</span></span> <span data-ttu-id="538d0-111">Le serveur constate l'indisponibilité des autres serveurs et récupère les deux sessions de Src1 et Src2.</span><span class="sxs-lookup"><span data-stu-id="538d0-111">The server finds that there are no other servers available, and therefore picks up both sessions for Src1 and Src2.</span></span>  
  
-   <span data-ttu-id="538d0-112">**B : serveur2 est mis en ligne et rejoint le pool Bus d’événements BAM**.</span><span class="sxs-lookup"><span data-stu-id="538d0-112">**B: Server2 is brought online and joins the BAM Event Bus pool**.</span></span> <span data-ttu-id="538d0-113">Une fois que l'instance du service Bus d'événements BAM est créée sur Serveur2, Serveur1 abandonne une session du service Bus d'événements BAM et Serveur2 la récupère.</span><span class="sxs-lookup"><span data-stu-id="538d0-113">After an instance of the BAM Event Bus service is created on Server2, Server1 drops one BAM Event Bus service session and Server2 picks it up.</span></span>  
  
-   <span data-ttu-id="538d0-114">**C: défaillance de Serveur1 de**.</span><span class="sxs-lookup"><span data-stu-id="538d0-114">**C: Server1 fails**.</span></span> <span data-ttu-id="538d0-115">Défaillance de Serveur1 une fois que Serveur2 a rejoint le pool Bus d'événements BAM.</span><span class="sxs-lookup"><span data-stu-id="538d0-115">Server1 fails after Server2 joins the BAM Event Bus pool.</span></span>  
  
-   <span data-ttu-id="538d0-116">**D: serveur2 traite les données d’événement de 2 sources (sessions)**.</span><span class="sxs-lookup"><span data-stu-id="538d0-116">**D: Server2 processes the event data from 2 sources (sessions)**.</span></span> <span data-ttu-id="538d0-117">Serveur2 récupère les deux sessions pour Src1 et Src2.</span><span class="sxs-lookup"><span data-stu-id="538d0-117">Server2 picks up both sessions for Src1 and Src2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="538d0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="538d0-118">See Also</span></span>  
 <span data-ttu-id="538d0-119">[La gestion de Service Bus d’événements BAM](../core/managing-the-bam-event-bus-service.md) </span><span class="sxs-lookup"><span data-stu-id="538d0-119">[Managing the BAM Event Bus Service](../core/managing-the-bam-event-bus-service.md) </span></span>  
 <span data-ttu-id="538d0-120">[Recommandations de sécurité BAM](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="538d0-120">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="538d0-121">Business Activity Monitoring (BAM)</span><span class="sxs-lookup"><span data-stu-id="538d0-121">Business Activity Monitoring (BAM)</span></span>](../core/business-activity-monitoring-bam.md)
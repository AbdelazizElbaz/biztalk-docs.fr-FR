---
title: Gestion des niveaux de service | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: add50343-5470-4db3-a029-c827523e2f2c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86b7ba1672660af2a68a5d193729a0a9009173d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="service-level-management"></a><span data-ttu-id="f60e5-102">Gestion du niveau de service</span><span class="sxs-lookup"><span data-stu-id="f60e5-102">Service Level Management</span></span>
<span data-ttu-id="f60e5-103">Le Gestionnaire de niveau de Service SMS AmberPoint offre une visibilité en performances spécifiques et des problèmes de disponibilité dans les systèmes de niveau entreprise SOA.</span><span class="sxs-lookup"><span data-stu-id="f60e5-103">The AmberPoint SMS Service Level Manager provides visibility into specific performance and availability issues within enterprise-level SOA-based systems.</span></span> <span data-ttu-id="f60e5-104">Il instrumente et effectue le suivi des métriques pour chaque Microsoft BizTalk Server l’emplacement de réception et le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="f60e5-104">It instruments and tracks the metrics for each Microsoft BizTalk Server receive location and send port.</span></span> <span data-ttu-id="f60e5-105">Cela fournit l’indication d’intégrité et l’état en temps réel, en plus de la caractérisation des performances en cours de ces composants.</span><span class="sxs-lookup"><span data-stu-id="f60e5-105">This provides real-time health and status indication, in addition to ongoing performance characterization of these components.</span></span> <span data-ttu-id="f60e5-106">La figure 1 illustre l’affichage des métriques associés à un emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="f60e5-106">Figure 1 shows the display of the metrics associated with a receive location.</span></span>  
  
 <span data-ttu-id="f60e5-107">![Emplacement de réception AmberPoint](../esb-toolkit/media/ch9-amberpointreceivelocation.gif "Ch9-AmberPointReceiveLocation")</span><span class="sxs-lookup"><span data-stu-id="f60e5-107">![AmberPoint Receive Location](../esb-toolkit/media/ch9-amberpointreceivelocation.gif "Ch9-AmberPointReceiveLocation")</span></span>  
  
 <span data-ttu-id="f60e5-108">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="f60e5-108">**Figure 1**</span></span>  
  
 <span data-ttu-id="f60e5-109">**Les métriques associées à un emplacement de réception**</span><span class="sxs-lookup"><span data-stu-id="f60e5-109">**The metrics associated with a receive location**</span></span>  
  
 <span data-ttu-id="f60e5-110">Analytique d’exécution AmberPoint permettre aux utilisateurs de définir des seuils et envoyer des alertes lorsqu’un système dépasse un seuil d’événements critiques, y compris les événements d’avertissements de conformité, les événements de violations de conformité et un retour suivant à la conformité.</span><span class="sxs-lookup"><span data-stu-id="f60e5-110">AmberPoint run-time analytics allow users to set thresholds and send alerts when a system crosses a critical event threshold, including compliance warnings events, compliance violations events, and a subsequent return to compliance.</span></span> <span data-ttu-id="f60e5-111">La figure 2 illustre l’affichage où les utilisateurs configurer des contrats de niveau de service et afficher les alertes générées pour ce contrat de niveau de service.</span><span class="sxs-lookup"><span data-stu-id="f60e5-111">Figure 2 shows the display where users configure service level agreements and view alerts generated for this service level agreement.</span></span>  
  
 <span data-ttu-id="f60e5-112">![SLA AmberPoint](../esb-toolkit/media/ch9-amberpointsla.gif "Ch9-AmberPointSLA")</span><span class="sxs-lookup"><span data-stu-id="f60e5-112">![AmberPoint SLA](../esb-toolkit/media/ch9-amberpointsla.gif "Ch9-AmberPointSLA")</span></span>  
  
 <span data-ttu-id="f60e5-113">**Figure 2**</span><span class="sxs-lookup"><span data-stu-id="f60e5-113">**Figure 2**</span></span>  
  
 <span data-ttu-id="f60e5-114">**Les écrans pour configurer un contrat de niveau de service et afficher des alertes**</span><span class="sxs-lookup"><span data-stu-id="f60e5-114">**The screens to configure a service level agreement and view alerts**</span></span>  
  
 <span data-ttu-id="f60e5-115">Vous pouvez établir des objectifs de performances dans le niveau de Service Manager.</span><span class="sxs-lookup"><span data-stu-id="f60e5-115">You can establish performance targets within the Service Level Manager.</span></span> <span data-ttu-id="f60e5-116">Le logiciel puis effectue le suivi des messages individuels, des messages à partir d’un utilisateur spécifique ou des messages à partir de groupes d’utilisateurs, pour mesurer les performances par rapport à ces cibles.</span><span class="sxs-lookup"><span data-stu-id="f60e5-116">The software then tracks individual messages, messages from a specific user, or messages from groups of users, to measure performance against these targets.</span></span>  
  
 <span data-ttu-id="f60e5-117">Vous pouvez également configurer des stratégies de journalisation qui commandent aux AmberPoint SMS pour collecter et examiner le contexte du message et les données transitant par BizTalk Server, comme indiqué dans la Figure 3 dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="f60e5-117">You can also configure logging policies that instruct AmberPoint SMS to dynamically collect and inspect message context and data passing through BizTalk Server, as shown in Figure 3.</span></span> <span data-ttu-id="f60e5-118">Vous pouvez ensuite utiliser ces journaux pour la résolution des problèmes « à la volée », pour une analyse des problèmes technique et d’archivage pour se conformer à des réglementations spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f60e5-118">You can then use these logs for "on-the-fly" troubleshooting, for technical analysis of problems, and for archiving to comply with industry-specific regulations.</span></span>  
  
 <span data-ttu-id="f60e5-119">![Messages du Service BizTalk](../esb-toolkit/media/ch9-biztalkservicemessages.jpg "Ch9-BizTalkServiceMessages")</span><span class="sxs-lookup"><span data-stu-id="f60e5-119">![BizTalk Service Messages](../esb-toolkit/media/ch9-biztalkservicemessages.jpg "Ch9-BizTalkServiceMessages")</span></span>  
  
 <span data-ttu-id="f60e5-120">**Figure 3**</span><span class="sxs-lookup"><span data-stu-id="f60e5-120">**Figure 3**</span></span>  
  
 <span data-ttu-id="f60e5-121">**Le fichier journal pour les messages du service BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="f60e5-121">**The log file for BizTalk Server service messages**</span></span>
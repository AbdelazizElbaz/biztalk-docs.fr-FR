---
title: "Montée en charge des hôtes de traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- high availability
- hosts, processing
- hosts, high availability
- scaling, hosts
- hosts, planning
- hosts, scaling
- clustering
ms.assetid: c72ce8fc-7593-4700-8398-23d1a20515c3
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01ee36777a5c64713fd31e86fe6ef2a1886b3348
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaled-out-processing-hosts"></a><span data-ttu-id="dfdd6-102">Mise à l'échelle des hôtes de traitement</span><span class="sxs-lookup"><span data-stu-id="dfdd6-102">Scaled-Out Processing Hosts</span></span>
<span data-ttu-id="dfdd6-103">Un hôte de traitement mis à l'échelle permet d'améliorer les performances et fournit une disponibilité élevée en isolant la fonctionnalité d'orchestration sur deux ordinateurs hôtes distincts (ou plus).</span><span class="sxs-lookup"><span data-stu-id="dfdd6-103">A scaled-out processing host improves performance and provides high availability by isolating orchestration functionality onto two or more separate host computers.</span></span> <span data-ttu-id="dfdd6-104">Ce principe d'isolation permet d'ajouter plusieurs ordinateurs dans un hôte de traitement afin d'obtenir une redondance.</span><span class="sxs-lookup"><span data-stu-id="dfdd6-104">This isolation lets you add multiple computers to a processing host for redundancy.</span></span> <span data-ttu-id="dfdd6-105">Dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], un hôte de traitement exécute une ou plusieurs instances d'hôtes capables de coordonner les différents processus d'entreprise et crée une instance d'objets de programmation pour les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="dfdd6-105">A processing host in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runs one or more host instances that coordinate various business processes and creates an instance of programmatic objects for orchestrations.</span></span>  
  
 <span data-ttu-id="dfdd6-106">Le schéma suivant montre un déploiement de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui offre une disponibilité élevée à l'hôte de traitement en mettant à sa disposition deux ordinateurs pour exécuter ses instances.</span><span class="sxs-lookup"><span data-stu-id="dfdd6-106">The following figure shows a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment that provides high availability for the processing host by having two computers that are running instances of the processing host.</span></span> <span data-ttu-id="dfdd6-107">Remarquez que les hôtes de réception et d'envoi représentés ici ne sont pas des hôtes hautement disponibles.</span><span class="sxs-lookup"><span data-stu-id="dfdd6-107">Note that in this figure the receiving and sending hosts are not highly available.</span></span>  
  
 <span data-ttu-id="dfdd6-108">![Monté en charge de l’hôte de traitement](../core/media/tdi-ha-scaleprocess.gif "TDI_HA_ScaleProcess")</span><span class="sxs-lookup"><span data-stu-id="dfdd6-108">![Scaled Out Processing Host](../core/media/tdi-ha-scaleprocess.gif "TDI_HA_ScaleProcess")</span></span>  
  
 <span data-ttu-id="dfdd6-109">Dans cette configuration, la charge de travail représentée par le traitement des orchestrations est répartie entre deux ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comportant des instances de l'hôte de traitement et s'exécutant indépendamment l'un de l'autre.</span><span class="sxs-lookup"><span data-stu-id="dfdd6-109">In this configuration, the work for processing orchestrations is load balanced between two [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers that have instances of the processing host and run independently of each other.</span></span> <span data-ttu-id="dfdd6-110">Si l'un des ordinateurs rencontre des problèmes ou s'arrête, le serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise automatiquement l'instance de l'hôte présente sur l'autre ordinateur afin de traiter les orchestrations restantes.</span><span class="sxs-lookup"><span data-stu-id="dfdd6-110">If one computer encounters errors or fails, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] automatically uses the host instance on the other computer to process remaining orchestrations.</span></span>  
  
## <a name="maintaining-orchestration-state"></a><span data-ttu-id="dfdd6-111">Gestion de l'état de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="dfdd6-111">Maintaining Orchestration State</span></span>  
 <span data-ttu-id="dfdd6-112">Le serveur BizTalk Server gère l'état de l'orchestration de manière centralisée dans Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et non localement sur chaque ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dfdd6-112">BizTalk Server maintains orchestration state centrally in Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], and not locally on each [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer.</span></span> <span data-ttu-id="dfdd6-113">En conservant l'état de l'orchestration dans la base de données MessageBox, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contourne le problème que représente le fait de ne s'appuyer que sur une seule instance de l'hôte de traitement pour l'orchestration. En outre, il est alors possible à n'importe quelle instance de l'hôte de traitement de traiter l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="dfdd6-113">By persisting the state in the MessageBox database, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] overcomes the limitation of relying on a single processing host instance to process the orchestration, and lets any processing host instance process the orchestration.</span></span> <span data-ttu-id="dfdd6-114">Si une erreur se produit alors que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est en cours de traitement d'une orchestration, une autre instance du même hôte de traitement peut terminer le processus d'orchestration à partir du dernier état conservé.</span><span class="sxs-lookup"><span data-stu-id="dfdd6-114">If an error occurs while [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes an orchestration, another instance of the same processing host can complete the orchestration from the last persisted state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfdd6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfdd6-115">See Also</span></span>  
 [<span data-ttu-id="dfdd6-116">Configuration de la haute disponibilité pour des hôtes BizTalk</span><span class="sxs-lookup"><span data-stu-id="dfdd6-116">Providing High Availability for BizTalk Hosts</span></span>](../core/providing-high-availability-for-biztalk-hosts.md)
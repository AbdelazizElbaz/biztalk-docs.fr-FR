---
title: Suivi de bout en bout Transaction | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ebacd2e4-6b5c-4dc4-8361-b5b77042debc
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffa49372c54dc526f45e04317e002604ac0914d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="end-to-end-transaction-tracking"></a><span data-ttu-id="d5a82-102">Suivi de la Transaction de bout en bout</span><span class="sxs-lookup"><span data-stu-id="d5a82-102">End-to-End Transaction Tracking</span></span>
<span data-ttu-id="d5a82-103">Visibilité de l’entreprise par rapport à la possibilité de contrôler le flux de trafic via l’environnement d’exécution des opérateurs et des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d5a82-103">Business visibility relates to the ability of operators and users to monitor the flow of traffic through the run-time environment.</span></span> <span data-ttu-id="d5a82-104">Les entreprises doivent être en mesure de suivre les processus et les transactions transitant via leurs systèmes à chaque étape pour vous assurer qu’ils jouent leurs à contribuer à la génération de revenus.</span><span class="sxs-lookup"><span data-stu-id="d5a82-104">Enterprises must be able to track the processes and transactions flowing through their systems at each step to ensure that they play their part in contributing to revenue generation.</span></span> <span data-ttu-id="d5a82-105">AmberPoint SMS simplifie la mesure et le suivi de ces messages dans Microsoft BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d5a82-105">AmberPoint SMS simplifies the measurement and tracking of these messages in Microsoft BizTalk Server.</span></span> <span data-ttu-id="d5a82-106">Le système permet aux utilisateurs de définir de nouvelles unités de gestion qui s’alignent sur les flux de processus d’entreprise de bout en bout, au lieu de se conformer à la façon dont les développeurs choisi pour empaqueter et déployer des composants de service individuels.</span><span class="sxs-lookup"><span data-stu-id="d5a82-106">The system allows users to define new units of management that align with end-to-end business process flows, instead of being required to conform to the way developers chose to package and deploy individual service components.</span></span> <span data-ttu-id="d5a82-107">La figure 1 illustre l’écran pour définir les unités de gestion.</span><span class="sxs-lookup"><span data-stu-id="d5a82-107">Figure 1 shows the screen for defining management units.</span></span>  
  
 <span data-ttu-id="d5a82-108">![Définition de Transaction de BizTalk](../esb-toolkit/media/ch9-biztalkdefiningtransaction.gif "Ch9-BizTalkDefiningTransaction")</span><span class="sxs-lookup"><span data-stu-id="d5a82-108">![BizTalk Defining Transaction](../esb-toolkit/media/ch9-biztalkdefiningtransaction.gif "Ch9-BizTalkDefiningTransaction")</span></span>  
  
 <span data-ttu-id="d5a82-109">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="d5a82-109">**Figure 1**</span></span>  
  
 <span data-ttu-id="d5a82-110">**Définition d’une transaction comme une nouvelle unité de gestion**</span><span class="sxs-lookup"><span data-stu-id="d5a82-110">**Defining a transaction as a new unit of management**</span></span>  
  
 <span data-ttu-id="d5a82-111">Après avoir défini les transactions, les utilisateurs peuvent instrumenter et suivre les messages associés à chaque transaction en utilisant les mêmes outils qui fournissent une visibilité en un seul service.</span><span class="sxs-lookup"><span data-stu-id="d5a82-111">After defining transactions, users can instrument and track messages associated with each transaction using the same tools that provide visibility into a single service.</span></span> <span data-ttu-id="d5a82-112">Ces outils peuvent exposer les métriques de performances, surveiller les performances par rapport aux contrats de niveau de service et générer des journaux de messages, comme illustré dans la Figure 2.</span><span class="sxs-lookup"><span data-stu-id="d5a82-112">These tools can expose performance metrics, monitor performance against service level agreements, and generate message logs, as shown in Figure 2.</span></span>  
  
 <span data-ttu-id="d5a82-113">![Analyse de BizTalk](../esb-toolkit/media/ch9-biztalkmonitoring.gif "Ch9-BizTalkMonitoring")</span><span class="sxs-lookup"><span data-stu-id="d5a82-113">![BizTalk Monitoring](../esb-toolkit/media/ch9-biztalkmonitoring.gif "Ch9-BizTalkMonitoring")</span></span>  
  
 <span data-ttu-id="d5a82-114">**Figure 2**</span><span class="sxs-lookup"><span data-stu-id="d5a82-114">**Figure 2**</span></span>  
  
 <span data-ttu-id="d5a82-115">**Analyse des performances de bout en bout d’un pipeline**</span><span class="sxs-lookup"><span data-stu-id="d5a82-115">**Monitoring the end-to-end performance of a pipeline**</span></span>  
  
 <span data-ttu-id="d5a82-116">Une condition requise pour la gouvernance de l’exécution réussie et la surveillance du système est la détection d’événements commerciaux importants, tels que les exceptions et erreurs d’application risquent de perturber le traitement de logique métier de flux de transaction.</span><span class="sxs-lookup"><span data-stu-id="d5a82-116">A major requirement for successful run-time governance and system monitoring is the detection of important business events, such as exceptions and application errors that may disrupt the logical processing of business transaction flows.</span></span> <span data-ttu-id="d5a82-117">AmberPoint SMS permet d’opérateurs et utilisateurs d’obtenir un éclairage opérationnel et des événements commerciaux et surveiller l’impact de ces événements sur tous les composants qui dépendent du service qui a généré le problème.</span><span class="sxs-lookup"><span data-stu-id="d5a82-117">AmberPoint SMS allows operators and users to gain insight into operational and business events and to monitor the impact these events have on all components that depend on the service that generated the problem.</span></span> <span data-ttu-id="d5a82-118">En outre, les opérateurs et les utilisateurs peuvent résoudre rapidement les l’ensemble du système pour identifier la cause d’un problème.</span><span class="sxs-lookup"><span data-stu-id="d5a82-118">In addition, operators and users can quickly troubleshoot the entire system to identify the root-cause of a problem.</span></span>
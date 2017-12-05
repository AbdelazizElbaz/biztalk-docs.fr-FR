---
title: Analyse de BizTalk Server avec System Center Operations Manager 2007 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee8275-bbd0-435f-ac54-07f582190538
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdaa0f0639bc640e87ff59e3cee0c229319de4ff
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="monitoring-biztalk-server-with-system-center-operations-manager-2007"></a><span data-ttu-id="b77b1-102">Analyse de BizTalk Server avec System Center Operations Manager 2007</span><span class="sxs-lookup"><span data-stu-id="b77b1-102">Monitoring BizTalk Server with System Center Operations Manager 2007</span></span>
<span data-ttu-id="b77b1-103">L’analyse de vos applications BizTalk et votre infrastructure avec Microsoft System Center Operations Manager (Operations Manager) est la meilleure approche d’analyse.</span><span class="sxs-lookup"><span data-stu-id="b77b1-103">Monitoring your BizTalk applications and infrastructure with Microsoft System Center Operations Manager (Operations Manager) is the preferred monitoring approach.</span></span> <span data-ttu-id="b77b1-104">Les packs d’administration de Microsoft BizTalk Server pour Operations Manager fournissent une analyse proactive et réactive des ordinateurs qui exécutent [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b77b1-104">The Microsoft BizTalk Server management packs for Operations Manager provide proactive and reactive monitoring of computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="b77b1-105">Ces packs d’administration fournissant des dizaines de règles intégrées et personnalisables pour permettre une analyse complète et automatisée de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b77b1-105">These management packs provide dozens of built-in, customizable rules to allow for comprehensive and automated monitoring of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b77b1-106">Le Pack d’administration de BizTalk Server suivant est disponible pour une utilisation avec Operations Manager :</span><span class="sxs-lookup"><span data-stu-id="b77b1-106">The following BizTalk Server management pack is available for use with Operations Manager:</span></span>  
  
-   <span data-ttu-id="b77b1-107">[Analyse du Pack d’administration de BizTalk Server 2010](ttp://go.microsoft.com/fwlink/?LinkId=210666) (ttp://go.microsoft.com/fwlink/?LinkId=210666).</span><span class="sxs-lookup"><span data-stu-id="b77b1-107">[BizTalk Server 2010 Monitoring Management Pack](ttp://go.microsoft.com/fwlink/?LinkId=210666) (ttp://go.microsoft.com/fwlink/?LinkId=210666).</span></span>  
  
 <span data-ttu-id="b77b1-108">Cette section du guide des opérations inclut des informations générales, meilleures pratiques, des listes de contrôle et les procédures que vous pouvez utiliser pour vous aider dans l’implémentation d’une stratégie d’analyse basée sur Operations Manager.</span><span class="sxs-lookup"><span data-stu-id="b77b1-108">This section of the operations guide includes background information, best practices, checklists, and procedures that you can use to assist in implementing a monitoring strategy based on Operations Manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b77b1-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b77b1-109">In This Section</span></span>  
  
-   [<span data-ttu-id="b77b1-110">Bonnes pratiques pour la surveillance avec Operations Manager 2007</span><span class="sxs-lookup"><span data-stu-id="b77b1-110">Best Practices for Monitoring with Operations Manager 2007</span></span>](../technical-guides/best-practices-for-monitoring-with-operations-manager-2007.md)  
  
-   [<span data-ttu-id="b77b1-111">Surveillance des limitations à l’aide de règles de seuil de performances</span><span class="sxs-lookup"><span data-stu-id="b77b1-111">Monitoring Throttling Using Performance Threshold Rules</span></span>](../technical-guides/monitoring-throttling-using-performance-threshold-rules.md)  
  
-   [<span data-ttu-id="b77b1-112">Surveillance des serveurs SQL Server</span><span class="sxs-lookup"><span data-stu-id="b77b1-112">Monitoring SQL Servers</span></span>](../technical-guides/monitoring-sql-servers.md)  
  
-   [<span data-ttu-id="b77b1-113">Surveillance des applications et des instances d’hôte</span><span class="sxs-lookup"><span data-stu-id="b77b1-113">Monitoring Applications and Host Instances</span></span>](../technical-guides/monitoring-applications-and-host-instances.md)
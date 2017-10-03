---
title: "Composants de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, BizTalk component
- MQSeries adapters, components
- MQSeries components, MQSeries adapters
- BizTalk components
- MQSeries adapters, MQSeries component
ms.assetid: 923974cb-371d-47dc-99a7-2f7b93f60ada
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58726b6528af55da6554ff740208b3e03bdc806e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="components-of-the-mqseries-adapter"></a><span data-ttu-id="eff4a-102">Composants de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="eff4a-102">Components of the MQSeries Adapter</span></span>
<span data-ttu-id="eff4a-103">L'adaptateur MQSeries utilise deux composants pour simplifier le transfert de documents entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et MQSeries Server pour Windows.</span><span class="sxs-lookup"><span data-stu-id="eff4a-103">The MQSeries adapter uses two components to facilitate document transfer between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and MQSeries Server for Windows.</span></span>  
  
-   <span data-ttu-id="eff4a-104">**Composant de BizTalk.**</span><span class="sxs-lookup"><span data-stu-id="eff4a-104">**BizTalk component.**</span></span> <span data-ttu-id="eff4a-105">Installez ce composant sur le même ordinateur que Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eff4a-105">Install this component on the same computer as Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="eff4a-106">Ce composant communique avec BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="eff4a-106">This component communicates with BizTalk Server.</span></span>  
  
-   <span data-ttu-id="eff4a-107">**Composant MQSeries.**</span><span class="sxs-lookup"><span data-stu-id="eff4a-107">**MQSeries component.**</span></span> <span data-ttu-id="eff4a-108">Installez ce composant sur le serveur MQSeries Server pour Windows.</span><span class="sxs-lookup"><span data-stu-id="eff4a-108">Install this component on the MQSeries Server for Windows.</span></span> <span data-ttu-id="eff4a-109">MQSeries Server pour Windows est exécuté sous [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eff4a-109">MQSeries Server for Windows runs on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].</span></span> <span data-ttu-id="eff4a-110">Ce composant (appelé MQSAgent) communique avec IBM MQSeries Server.</span><span class="sxs-lookup"><span data-stu-id="eff4a-110">This component (referred to as MQSAgent) communicates with IBM MQSeries Server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eff4a-111">L'exécution du composant MQSAgent de l'adaptateur MQSeries est prise en charge sur MQSeries Server 5.3, CSD10 ou version ultérieure et WebSphere MQSeries Server 6.0 sous Windows.</span><span class="sxs-lookup"><span data-stu-id="eff4a-111">The MQSAgent component of the MQSeries Adapter is supported running against MQSeries Server 5.3, CSD10 or above, and WebSphere MQSeries Server 6.0 on Windows.</span></span>  
  
 <span data-ttu-id="eff4a-112">La figure suivant illustre une utilisation typique de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="eff4a-112">The following figure outlines a typical use of the adapter.</span></span>  
  
 <span data-ttu-id="eff4a-113">![Documenter le flux entre MQSeries Server et BizTalk](../core/media/bts-dev-mqadapterflow.gif "BTS_Dev_MQAdapterFlow")</span><span class="sxs-lookup"><span data-stu-id="eff4a-113">![Document flow between MQSeries Server and BizTalk](../core/media/bts-dev-mqadapterflow.gif "BTS_Dev_MQAdapterFlow")</span></span>  
  
 <span data-ttu-id="eff4a-114">L'adaptateur MQSeries est une solution de connectivité qui vous permet d'utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans une entreprise avec MQSeries comme norme de messagerie.</span><span class="sxs-lookup"><span data-stu-id="eff4a-114">The MQSeries adapter is a connectivity solution that lets you use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in an enterprise with MQSeries as the chosen messaging standard.</span></span> <span data-ttu-id="eff4a-115">Le développement de cette solution a été motivé, en partie, par les problématiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="eff4a-115">Developing this solution was motivated, in part, by the following issues:</span></span>  
  
-   <span data-ttu-id="eff4a-116">répondre aux demandes des clients relatives à la simplification de l'installation et de la configuration, et à une solution de connectivité MQSeries ;</span><span class="sxs-lookup"><span data-stu-id="eff4a-116">Accommodating customer requests for simple installation and configuration, and an MQSeries connectivity solution</span></span>  
  
-   <span data-ttu-id="eff4a-117">prendre en charge les tailles de message jusqu'à 100 Mo ;</span><span class="sxs-lookup"><span data-stu-id="eff4a-117">Supporting message sizes up to 100 MB</span></span>  
  
-   <span data-ttu-id="eff4a-118">assurer la prise en charge de MQSeries ;</span><span class="sxs-lookup"><span data-stu-id="eff4a-118">Providing MQSeries support</span></span>  
  
-   <span data-ttu-id="eff4a-119">fournir une solution de connectivité Plug-and-Play pour les messages MQSeries à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eff4a-119">Providing a Plug and Play connectivity solution for MQSeries messages to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
 <span data-ttu-id="eff4a-120">L'adaptateur MQSeries constitue un ajout important à la suite de services de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui fournit un ensemble d'écouteurs pour divers protocoles normalisés de communication.</span><span class="sxs-lookup"><span data-stu-id="eff4a-120">The MQSeries adapter is a key addition to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] suite of receive services that provide a set of listeners for various communication protocol standards.</span></span> <span data-ttu-id="eff4a-121">Les écouteurs associent un protocole (par exemple, HTTP, FTP ou MQSeries) à une relation commerciale d'intégration d'applications d'entreprise, interentreprises ou interapplications.</span><span class="sxs-lookup"><span data-stu-id="eff4a-121">The listeners attach a protocol, for example HTTP, FTP, or MQSeries, to an enterprise application integration (EAI), business-to-business, or application-to-application integration trading relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eff4a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eff4a-122">See Also</span></span>  
 <span data-ttu-id="eff4a-123">[Architecture de l’adaptateur MQSeries](../core/mqseries-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="eff4a-123">[MQSeries Adapter Architecture](../core/mqseries-adapter-architecture.md) </span></span>  
 [<span data-ttu-id="eff4a-124">Nouveautés de l’adaptateur MQSeries ?</span><span class="sxs-lookup"><span data-stu-id="eff4a-124">What Is the MQSeries Adapter?</span></span>](../core/what-is-the-mqseries-adapter.md)
---
title: "Admin-WMI (dossier d’exemples BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- administering, WMI
- examples, Windows Management Instrumentation (WMI)
- Windows Management Instrumentation (WMI), administering
- Windows Management Instrumentation (WMI), examples
- examples, administering
- administering, examples
ms.assetid: 39e2a6fe-2781-4be2-a152-f5e9960a0faa
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19a8698bbe916d86909005ff77c9b1eeea11604f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="admin-wmi-biztalk-server-samples-folder"></a><span data-ttu-id="0955b-102">Admin-WMI (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="0955b-102">Admin-WMI (BizTalk Server Samples Folder)</span></span>
<span data-ttu-id="0955b-103">Le Kit de développement logiciel (SDK) de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut plusieurs exemples d'administration Microsoft Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="0955b-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes several Microsoft Windows Management Instrumentation (WMI) administration samples in its software development kit (SDK).</span></span> <span data-ttu-id="0955b-104">Cette section fournit des informations détaillées sur les fonctionnalités utilisées dans les exemples d'administration WMI, des instructions sur la création et l'exécution des exemples et les résultats attendus.</span><span class="sxs-lookup"><span data-stu-id="0955b-104">This section provides detailed information about the functionality demonstrated by each WMI administration sample, instructions for building and running the sample, and the results you can expect.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="0955b-105">Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="0955b-105">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="0955b-106">Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.</span><span class="sxs-lookup"><span data-stu-id="0955b-106">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0955b-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0955b-107">In This Section</span></span>  
  
-   <span data-ttu-id="0955b-108">[Activer la réception (exemple BizTalk Server) d’emplacement](../core/enable-receive-location-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0955b-108">[Enable Receive Location (BizTalk Server Sample)](../core/enable-receive-location-biztalk-server-sample.md).</span></span> <span data-ttu-id="0955b-109">Montre comment activer un emplacement de réception et de définir l’URL de Transport entrant pour cet emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="0955b-109">Demonstrates how to enable a receive location and set the Inbound Transport URL for that receive location.</span></span>  
  
-   <span data-ttu-id="0955b-110">[Inscrire l’Orchestration (exemple BizTalk Server)](../core/enlist-orchestration-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0955b-110">[Enlist Orchestration (BizTalk Server Sample)](../core/enlist-orchestration-biztalk-server-sample.md).</span></span> <span data-ttu-id="0955b-111">Montre comment inscrire une orchestration BizTalk Server sur un ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="0955b-111">Demonstrates how to enlist a BizTalk Server orchestration to a host.</span></span>  
  
-   <span data-ttu-id="0955b-112">[Énumérer les emplacements (exemple BizTalk Server) de réception](../core/enumerate-receive-locations-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0955b-112">[Enumerate Receive Locations (BizTalk Server Sample)](../core/enumerate-receive-locations-biztalk-server-sample.md).</span></span> <span data-ttu-id="0955b-113">Décrit la récupération d'informations détaillées sur un ou plusieurs emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="0955b-113">Demonstrates how to retrieve details about one or more receive locations.</span></span>  
  
-   <span data-ttu-id="0955b-114">[(Exemple BizTalk Server) de Port de réception de suppression](../core/remove-receive-port-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0955b-114">[Remove Receive Port (BizTalk Server Sample)](../core/remove-receive-port-biztalk-server-sample.md).</span></span> <span data-ttu-id="0955b-115">Montre comment supprimer un ou plusieurs ports de réception.</span><span class="sxs-lookup"><span data-stu-id="0955b-115">Demonstrates how to remove one or more receive ports.</span></span>  
  
-   <span data-ttu-id="0955b-116">[Remove Send Port (exemple BizTalk Server)](../core/remove-send-port-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0955b-116">[Remove Send Port (BizTalk Server Sample)](../core/remove-send-port-biztalk-server-sample.md).</span></span> <span data-ttu-id="0955b-117">Montre comment désinscrire et supprimer un ou plusieurs ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="0955b-117">Demonstrates how to unenlist and remove one or more send ports.</span></span>  
  
-   <span data-ttu-id="0955b-118">[Définir la propriété du Gestionnaire d’envoi (exemple BizTalk Server)](../core/set-send-handler-property-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0955b-118">[Set Send Handler Property (BizTalk Server Sample)](../core/set-send-handler-property-biztalk-server-sample.md).</span></span> <span data-ttu-id="0955b-119">Montre comment définir les informations de configuration XML pour un gestionnaire d’envoi SMTP Simple Mail Transfer Protocol ().</span><span class="sxs-lookup"><span data-stu-id="0955b-119">Demonstrates how to set the XML configuration information for a Simple Mail Transfer Protocol (SMTP) send handler.</span></span>  
  
-   <span data-ttu-id="0955b-120">[Port d’envoi (exemple BizTalk Server) du début](../core/start-send-port-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0955b-120">[Start Send Port (BizTalk Server Sample)](../core/start-send-port-biztalk-server-sample.md).</span></span> <span data-ttu-id="0955b-121">Montre comment démarrer un port d’envoi et de définir l’adresse de Transport principal lorsque vous utilisez l’adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="0955b-121">Demonstrates how to start a send port and set the Primary Transport Address when using the FILE adapter.</span></span>  
  
-   <span data-ttu-id="0955b-122">[Arrêter l’Orchestration (exemple BizTalk Server)](../core/stop-orchestration-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0955b-122">[Stop Orchestration (BizTalk Server Sample)](../core/stop-orchestration-biztalk-server-sample.md).</span></span> <span data-ttu-id="0955b-123">Montre comment arrêter une orchestration BizTalk Server et, éventuellement, sa désinscription.</span><span class="sxs-lookup"><span data-stu-id="0955b-123">Demonstrates how to stop a BizTalk Server orchestration and, optionally, to unenlist it.</span></span>
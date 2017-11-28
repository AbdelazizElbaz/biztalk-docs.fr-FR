---
title: "Vue d’ensemble du Point de gestion BizTalk SOA | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d4c3a30-c50e-4c1c-9f59-d9a364078388
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60f73834a9bc02e371d4050115b1eccf5e88e02f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-soa-biztalk-management-point"></a><span data-ttu-id="25ab3-102">Vue d’ensemble du Point de gestion BizTalk SOA</span><span class="sxs-lookup"><span data-stu-id="25ab3-102">Overview of the SOA BizTalk Management Point</span></span>
<span data-ttu-id="25ab3-103">En mode natif, le Point de gestion BizTalk s’intègre avec les produits de Gestionnaire des services SOA et le banc d’essai.</span><span class="sxs-lookup"><span data-stu-id="25ab3-103">The BizTalk Management Point natively integrates with SOA Service Manager and Workbench products.</span></span> <span data-ttu-id="25ab3-104">Contrairement au Point de gestion de Services Web par défaut, cette implémentation est associée avec les services fournis par l’environnement de Microsoft BizTalk Server, exprimée en termes de BizTalk Server des emplacements de réception et ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="25ab3-104">Unlike the typical Web Services Management Point, this implementation is associated with services provided by the Microsoft BizTalk Server environment, expressed in terms of BizTalk Server receive locations and send ports.</span></span> <span data-ttu-id="25ab3-105">En raison de l’élément arbitraire nature des emplacements de réception et ports (configurés sur un grand nombre d’adaptateurs BizTalk Server) d’envoi, ces services ne sont pas nécessairement associés à des services Web, mais elles peuvent être traitées comme les services Web en termes de SOA Service Manager et SOA banc d’essai.</span><span class="sxs-lookup"><span data-stu-id="25ab3-105">Because of the arbitrary nature of receive locations and send ports (configured against a variety of BizTalk Server adapters), these services are not necessarily associated with Web services, but they can be treated as Web services in terms of the SOA Service Manager and SOA Workbench.</span></span>  
  
 <span data-ttu-id="25ab3-106">Figure 1 montre l’application Web du Gestionnaire des services SOA affichant la page de banc d’essai pour un exemple d’application.</span><span class="sxs-lookup"><span data-stu-id="25ab3-106">Figure 1 shows the SOA Service Manager Web application displaying the Workbench page for an example application.</span></span> <span data-ttu-id="25ab3-107">L’arborescence de gauche permet aux utilisateurs de naviguer dans les applications et services installés au sein de BizTalk Server, et le volet de droite permet aux utilisateurs d’afficher les détails de l’application, les opérations, ports d’accès, catégories, les règles et les informations d’analyse.</span><span class="sxs-lookup"><span data-stu-id="25ab3-107">The left-side tree view allows users to navigate through the applications and services installed within BizTalk Server, and the right-side pane allows users to view application details, operations, access ports, categories, rules, and monitoring information.</span></span>  
  
 <span data-ttu-id="25ab3-108">![Ch9 &#45; SOAServiceManager](../esb-toolkit/media/ch9-soaservicemanager.jpg "Ch9-SOAServiceManager")</span><span class="sxs-lookup"><span data-stu-id="25ab3-108">![Ch9&#45;SOAServiceManager](../esb-toolkit/media/ch9-soaservicemanager.jpg "Ch9-SOAServiceManager")</span></span>  
  
 <span data-ttu-id="25ab3-109">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="25ab3-109">**Figure 1**</span></span>  
  
 <span data-ttu-id="25ab3-110">**Le Gestionnaire des services SOA affichant les fonctionnalités d’analyse disponibles sur la page de banc d’essai**</span><span class="sxs-lookup"><span data-stu-id="25ab3-110">**The SOA Service Manager showing the monitoring features available on the Workbench page**</span></span>  
  
 <span data-ttu-id="25ab3-111">Vous pouvez surveiller toutes les opérations dans une application (tous les ports d’envoi et emplacements de réception), ou des opérations spécifiques ; l’affiche de banc d’essai une liste des messages transitant par le texte sélectionné les ports d’envoi et emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="25ab3-111">You can monitor all the operations within an application (all send ports and receive locations), or specific operations; the Workbench shows a list of the messages passing through the selected send ports and receive locations.</span></span> <span data-ttu-id="25ab3-112">Lorsque vous double-cliquez sur un message dans la liste, le banc d’essai affiche les détails du message et ses propriétés de contexte (si l’enregistrement est activé).</span><span class="sxs-lookup"><span data-stu-id="25ab3-112">When you double-click a message in the list, the Workbench displays details of the message, and its context properties (if recording is enabled).</span></span> <span data-ttu-id="25ab3-113">Ou bien, vous pouvez sélectionner un service spécifique et un moniteur dans les messages en temps réel en passant par ce service.</span><span class="sxs-lookup"><span data-stu-id="25ab3-113">Alternatively, you can select a specific service and monitor in real-time messages passing through that service.</span></span>
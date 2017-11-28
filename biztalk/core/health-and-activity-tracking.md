---
title: "Suivi des activités et contrôle d’intégrité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c5d7415-38da-47b5-8dbc-0a2ea74548d9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35b1720535b58a50fe0c5bd3478bc9b9ec90d0d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="health-and-activity-tracking"></a><span data-ttu-id="e50fc-102">Suivi des activités et du fonctionnement</span><span class="sxs-lookup"><span data-stu-id="e50fc-102">Health and Activity Tracking</span></span>
<span data-ttu-id="e50fc-103">Le **intégrité et l’activité de suivi** outil a été supprimé dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009.</span><span class="sxs-lookup"><span data-stu-id="e50fc-103">The **Health and Activity Tracking (HAT)** tool was removed in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009.</span></span>  <span data-ttu-id="e50fc-104">Le rôle de l’outil HAT était de suivre et d’afficher des informations relatives aux live et les données de message historiques stockées dans la base de données des suivis BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e50fc-104">The role of the HAT tool was to track and display information relating to live and historical message data stored in the BizTalk Tracking database.</span></span>  <span data-ttu-id="e50fc-105">Il permettait également de déboguer le flux d'une orchestration et d'afficher le flux d'un message via un affichage séquentiel.</span><span class="sxs-lookup"><span data-stu-id="e50fc-105">The tool allowed debugging of the flow of an orchestration and the ability to view the flow of a message through a sequential display.</span></span>  <span data-ttu-id="e50fc-106">Un Générateur de requête prenait en charge les requêtes standard et personnalisées sur les données de suivi.</span><span class="sxs-lookup"><span data-stu-id="e50fc-106">A Query Builder allowed standard and custom queries of the tracking data.</span></span>  
  
 <span data-ttu-id="e50fc-107">Si l'outil Suivi des activités et du fonctionnement n'est plus invoqué directement à partir du menu [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ses fonctionnalités de suivi sont toujours indirectement disponibles dans l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e50fc-107">While the Health Activity Tracking tool is no longer invoked directly from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] menu, its tracking functionality still indirectly exists from within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  <span data-ttu-id="e50fc-108">Les informations relatives aux activités et au fonctionnement sont accessibles grâce à une intégration améliorée et à des requêtes de suivi supplémentaires au sein de la page Hub du groupe dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e50fc-108">Health and activity information is available through improved integration and additional tracking queries within the Group Hub page in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="e50fc-109">La majorité de la documentation qui entoure le suivi des activités et du fonctionnement des données, consultez [afficher un Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md).</span><span class="sxs-lookup"><span data-stu-id="e50fc-109">A majority of documentation surrounding tracking health and activity data can be found at [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md).</span></span>  <span data-ttu-id="e50fc-110">Certaines informations de cette section inclut [meilleures pratiques pour le Message et le suivi des données d’Instance](../core/best-practices-for-message-and-instance-data-tracking.md), [comprendre des données de suivi](../core/understanding-tracked-data.md), [affichage de l’historique et les données de suivi](../core/viewing-historical-and-tracked-data.md), [Affichage des flux de messages](../core/viewing-message-flow.md), et [débogage d’une Orchestration](../core/debugging-an-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="e50fc-110">Some of the information in this section includes [Best Practices for Message and Instance Data Tracking](../core/best-practices-for-message-and-instance-data-tracking.md), [Understanding Tracked Data](../core/understanding-tracked-data.md), [Viewing Historical and Tracked Data](../core/viewing-historical-and-tracked-data.md), [Viewing Message Flow](../core/viewing-message-flow.md), and [Debugging an Orchestration](../core/debugging-an-orchestration.md).</span></span>  
  
 <span data-ttu-id="e50fc-111">Pour plus d'informations sur les améliorations et les requêtes supplémentaires dans cette page, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="e50fc-111">For additional information on the improvements and the additional queries to this page, refer to the following topics:</span></span>  
  
-   [<span data-ttu-id="e50fc-112">À l’aide de la Page Hub du groupe</span><span class="sxs-lookup"><span data-stu-id="e50fc-112">Using the Group Hub Page</span></span>](../core/using-the-group-hub-page.md)  
  
-   [<span data-ttu-id="e50fc-113">À l’aide de l’onglet requête de la Console Administration</span><span class="sxs-lookup"><span data-stu-id="e50fc-113">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)  
  
-   [<span data-ttu-id="e50fc-114">Comment rechercher des événements de Message suivis</span><span class="sxs-lookup"><span data-stu-id="e50fc-114">How to Search for Tracked Message Events</span></span>](../core/how-to-search-for-tracked-message-events.md)  
  
-   [<span data-ttu-id="e50fc-115">Comment rechercher des Instances de Service suivies</span><span class="sxs-lookup"><span data-stu-id="e50fc-115">How to Search for Tracked Service Instances</span></span>](../core/how-to-search-for-tracked-service-instances.md)
---
title: "La gestion de Service Bus d’événements BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MessageBox database, migrating data
- Primary Import database [BAM], migrating data
- migrating, data [BAM]
- managing [BAM], Event Bus Service
- Event Bus Service [BAM], managing
- Tracking Data Decode Service (TDDS)
ms.assetid: 556e7fe2-4a7d-46f6-8e55-f41be4e666dc
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f265201e371a86072c06b336b4d00bb1742f5f6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-the-bam-event-bus-service"></a><span data-ttu-id="6924a-102">Gestion du service Bus d'événements BAM</span><span class="sxs-lookup"><span data-stu-id="6924a-102">Managing the BAM Event Bus Service</span></span>
<span data-ttu-id="6924a-103">Le service Bus d'événements BAM, ou service TDDS (Tracking Data Decode Service), traite les données de suivi (flux) stockées dans une base de données source et les conserve de manière telle qu'elles peuvent être aisément interrogées par la suite.</span><span class="sxs-lookup"><span data-stu-id="6924a-103">The BAM Event Bus Service, also known as the Tracking Data Decode Service (TDDS), processes tracking data (streams) stored in a source database and persists that data in such a way that it is easy to query it at a later date.</span></span>  
  
 <span data-ttu-id="6924a-104">Le service Bus d'événements BAM déplace les données décisionnelles vers les données d'analyse du fonctionnement de BizTalk et la base de données d'importation principale BAM vers la base de données des suivis.</span><span class="sxs-lookup"><span data-stu-id="6924a-104">The BAM Event Bus service moves Business intelligence data to the BAM Primary Import database and BizTalk Health Monitoring data to the DTA database.</span></span> <span data-ttu-id="6924a-105">Le service Bus d'événements BAM s'exécute en tant que sous-service dans les services BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6924a-105">The BAM Event Bus service runs as a sub-service within the BizTalk service.</span></span>  
  
 <span data-ttu-id="6924a-106">Pour analyser les activités d'une application transactionnelle telle que Microsoft BizTalk® Server, vous devez récupérer des données d'événements en cours d'exécution, puis les stocker momentanément dans la base de données où est conservé l'état de l'application (la base de données MessageBox, par exemple).</span><span class="sxs-lookup"><span data-stu-id="6924a-106">You monitor the activities of a transactional application, such as Microsoft BizTalk® Server, by collecting event data during execution, and then temporarily storing the data in the same database as the application state—for example, the MessageBox database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6924a-107">Évitez de créer sur un même ordinateur plusieurs instances d'application hébergeant les suivis pour les différents groupes BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6924a-107">Avoid creating more than one application instance that hosts tracking for different BizTalk Groups on the same computer.</span></span> <span data-ttu-id="6924a-108">Si les instances qui effectuent le suivi de différents groupes BizTalk existent sur le même ordinateur, vous ne serez pas en mesure de distinguer les événements qui appartiennent à quels groupes BizTalk dans la Console Administration de BizTalk ou dans le journal des événements, car tous les groupes BizTalk s’affichent avec le même nom.</span><span class="sxs-lookup"><span data-stu-id="6924a-108">If instances that track different BizTalk Groups exist on the same computer, you will not be able to distinguish which events belong to which BizTalk Groups in the BizTalk Administration Console or in the event log because all BizTalk Groups are displayed with the same name.</span></span>  
  
 <span data-ttu-id="6924a-109">Le service Bus d'événements BAM lit les données d'événements, les décode et les stocke dans une base de données Microsoft SQL Server™ où vous pouvez facilement interroger les données.</span><span class="sxs-lookup"><span data-stu-id="6924a-109">The BAM Event Bus service reads the event data, decodes it, and then stores it in a Microsoft SQL Server™ database, where you can easily query the data.</span></span>  
  
 <span data-ttu-id="6924a-110">Le service Bus d'événements BAM offre les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="6924a-110">The BAM Event Bus service provides the following advantages:</span></span>  
  
-   <span data-ttu-id="6924a-111">Les données d'événements correspondent systématiquement à l'état de l'application et ne reflètent jamais la progression d'éléments non validée.</span><span class="sxs-lookup"><span data-stu-id="6924a-111">Event data always matches the state of the application, and it never exposes uncommitted progress.</span></span>  
  
-   <span data-ttu-id="6924a-112">L'impact sur les performances de l'application en cours d'exécution est minime, car les données d'événements conservent peu d'enregistrements dans la transaction locale, ce qui reflète les changements limités de l'état de l'application.</span><span class="sxs-lookup"><span data-stu-id="6924a-112">Performance impact on the running application is minimal because the event data saves as few records in the same local transaction as the application state change.</span></span>  
  
-   <span data-ttu-id="6924a-113">Le stockage SQL Server pour l'état de l'application est ensuite optimisé pour des performances d'exécution accrues.</span><span class="sxs-lookup"><span data-stu-id="6924a-113">SQL Server storage for the application state is further optimized for execution performance.</span></span> <span data-ttu-id="6924a-114">Les données sont décodées par le service TDDS et stockées dans une base de données distincte : la base de données d'importation principale BAM ou la base de données des suivis.</span><span class="sxs-lookup"><span data-stu-id="6924a-114">The data is decoded by TDDS and stored in a separate database, either the BAM Primary import database or the DTA database.</span></span> <span data-ttu-id="6924a-115">Lorsque les rapports sont générés, les données sont interrogées à partir de la base de données et affectent la base de données MessageBox, qui stocke l'état de l'application.</span><span class="sxs-lookup"><span data-stu-id="6924a-115">When reports are generated the data is queried from the database and does impact the Message Box database, which stores the application state.</span></span>  
  
-   <span data-ttu-id="6924a-116">Les opérations nécessaires au stockage des données d'événements dans un format permettant des interrogations ultérieures ne sont pas effectuées dans les serveurs et les bases de données de l'application.</span><span class="sxs-lookup"><span data-stu-id="6924a-116">The work to store the event data in a form that you can query is not done in the application servers and databases.</span></span> <span data-ttu-id="6924a-117">Elles sont confiées aux ordinateurs qui exécutent le service Bus d'événements BAM et la base de données SQL Server de destination.</span><span class="sxs-lookup"><span data-stu-id="6924a-117">It is offloaded to the machines that run the BAM Event Bus service and the Destination SQL Server database.</span></span>  
  
-   <span data-ttu-id="6924a-118">Les données d'événement sont traitées avec une faible latence, ce qui permet un traitement plus rapide des requêtes TDDS.</span><span class="sxs-lookup"><span data-stu-id="6924a-118">Event data is processed with low latency which allows TDDS queries process faster.</span></span> <span data-ttu-id="6924a-119">Les services Bus d'événements BAM coordonnent leurs ressources pour obtenir la latence la plus faible possible.</span><span class="sxs-lookup"><span data-stu-id="6924a-119">The BAM Event Bus services coordinate their resources to achieve the minimum possible latency.</span></span>  
  
 <span data-ttu-id="6924a-120">Le serveur de Bus d'événements BAM obtient une telle coordination en utilisant une connexion à une base de données centrale contenant les informations de configuration.</span><span class="sxs-lookup"><span data-stu-id="6924a-120">The BAM Event Bus server coordinates its resources by using a connection to a central database, which contains the configuration information.</span></span> <span data-ttu-id="6924a-121">Chaque service Bus d'événements BAM actif envoie à la base de données centrale un message par minute contenant l'état du service Bus à un moment précis dans le temps.</span><span class="sxs-lookup"><span data-stu-id="6924a-121">Every minute, each active BAM Event Bus service sends a message to the central database, which contains the state of the BAM Event Bus service at that point in time.</span></span>  
  
 <span data-ttu-id="6924a-122">Ce message est appelé message de pulsation.</span><span class="sxs-lookup"><span data-stu-id="6924a-122">This message is referred to as a heartbeat message.</span></span> <span data-ttu-id="6924a-123">Chaque service Bus d'événements BAM recherche également les nouvelles tâches à effectuer.</span><span class="sxs-lookup"><span data-stu-id="6924a-123">Each BAM Event Bus service also checks for new work that needs to be done.</span></span> <span data-ttu-id="6924a-124">Par exemple, le service Bus d'événements BAM recherche les sessions non propriétaires telles qu'une base de données MessageBox venant d'être ajoutée.</span><span class="sxs-lookup"><span data-stu-id="6924a-124">For example, the BAM Event Bus service checks for sessions that are not owned, such as a MessageBox database that has been added.</span></span>  
  
 <span data-ttu-id="6924a-125">Une session de Bus d'événements BAM correspond au mouvement des données d'événements entre la base de données source (MessageBox, par exemple) et la base de données de destination comprenant les données d'événements dans un format permettant les interrogations.</span><span class="sxs-lookup"><span data-stu-id="6924a-125">The BAM Event Bus session is the movement of the event data from the source database, such as the MessageBox, to the destination database that contains the event data in a format that you can query.</span></span> <span data-ttu-id="6924a-126">Le même service Bus peut traiter une ou plusieurs sessions.</span><span class="sxs-lookup"><span data-stu-id="6924a-126">The same BAM Event Bus service can process one or more sessions.</span></span>  
  
 <span data-ttu-id="6924a-127">Le schéma suivant représente un groupe de serveurs Bus d'événements BAM constituant un pool de serveurs Bus.</span><span class="sxs-lookup"><span data-stu-id="6924a-127">The following figure shows a group of BAM Event Bus servers, which make up a BAM Event Bus server pool.</span></span>  
  
 ![](../core/media/ebiz-bam-admin-evntbuspool.gif "ebiz_bam_admin_evntbuspool")  
<span data-ttu-id="6924a-128">Schéma d'un pool de serveurs Bus d'événements BAM</span><span class="sxs-lookup"><span data-stu-id="6924a-128">Diagram of a BAM Event Bus server pool</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6924a-129">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6924a-129">In This Section</span></span>  
  
-   [<span data-ttu-id="6924a-130">Compteurs de Performance BAM</span><span class="sxs-lookup"><span data-stu-id="6924a-130">BAM Performance Counters</span></span>](../core/bam-performance-counters.md)  
  
-   [<span data-ttu-id="6924a-131">Procédures stockées de Service Bus d’événements BAM</span><span class="sxs-lookup"><span data-stu-id="6924a-131">BAM Event Bus Service Stored Procedures</span></span>](../core/bam-event-bus-service-stored-procedures.md)  
  
-   [<span data-ttu-id="6924a-132">Basculement du serveur BAM événement Bus Service</span><span class="sxs-lookup"><span data-stu-id="6924a-132">BAM Event Bus Service Server Failover</span></span>](../core/bam-event-bus-service-server-failover.md)  
  
-   [<span data-ttu-id="6924a-133">Création d’Instances de Service Bus d’événements BAM</span><span class="sxs-lookup"><span data-stu-id="6924a-133">Creating Instances of the BAM Event Bus Service</span></span>](../core/creating-instances-of-the-bam-event-bus-service.md)
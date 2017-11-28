---
title: "À l’aide de la Page Hub du groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50693ccc-a3b2-4ad0-9a05-d60dab404a07
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e035a363b71b70db390d88a8b0e32e2e9b531d92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-group-hub-page"></a><span data-ttu-id="0c218-102">Utilisation de la page Hub du groupe</span><span class="sxs-lookup"><span data-stu-id="0c218-102">Using the Group Hub Page</span></span>
<span data-ttu-id="0c218-103">En sélectionnant le **groupe BizTalk** nœud dans la Console Administration de BizTalk Server, affiche la page Hub du groupe BizTalk Server dans le volet de détails.</span><span class="sxs-lookup"><span data-stu-id="0c218-103">Selecting the **BizTalk Group** node in the BizTalk Server Administration Console, displays the BizTalk Server Group Hub page in the details pane.</span></span> <span data-ttu-id="0c218-104">Cette page, divisée en trois sections, fournit une vue d'ensemble du fonctionnement de votre système BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="0c218-104">The BizTalk Server Group Hub page is divided into three sections that provide an overall view of the health of your BizTalk Server system:</span></span>  
  
-   <span data-ttu-id="0c218-105">Le **vue d’ensemble de la Configuration** section, située dans la partie supérieure de la page Hub du groupe, indique l’intégrité globale du groupe BizTalk en affichant l’état des applications, les instances d’hôte, et les gestionnaires d’adaptateur configurés dans ce groupe.</span><span class="sxs-lookup"><span data-stu-id="0c218-105">The **Configuration Overview** section, located in the upper part of the Group Hub page, indicates the overall health of the BizTalk group by displaying the state of the applications, host instances, and adapter handlers configured in this group.</span></span>  
  
-   <span data-ttu-id="0c218-106">Le **travail en cours** et **éléments suspendus** sections se trouvent au milieu de la page Hub du groupe.</span><span class="sxs-lookup"><span data-stu-id="0c218-106">The **Work in Progress**  and **Suspended Items** sections are located in the middle of the Group Hub page.</span></span>  
  
    -   <span data-ttu-id="0c218-107">Le **travail en cours** section affiche les instances de service, orchestrations en attente, ports inactifs et nouvelle tentative, les instances de service prêtes et instances de service planifiée en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0c218-107">The **Work in Progress** section displays running service instances, dehydrated orchestrations, retrying and idle ports, ready service instances, and scheduled service instances.</span></span>  
  
    -   <span data-ttu-id="0c218-108">Le **éléments suspendus** section affiche le nombre d’instances de service suspendues et instances pouvant être reprises et sans reprise possible.</span><span class="sxs-lookup"><span data-stu-id="0c218-108">The **Suspended Items** section displays the number of suspended service instances, and resumable and non-resumable instances.</span></span>  
  
-   <span data-ttu-id="0c218-109">Le **Instances de Service suspendues groupées** section affiche les instances de service suspendues groupées par application, nom du service, code d’erreur et URI.</span><span class="sxs-lookup"><span data-stu-id="0c218-109">The **Grouped Suspended Service Instances** section displays suspended service instances grouped by application, service name, error code, and URI.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0c218-110">Les chiffres indiqués sur la page Hub du groupe correspondent à des approximations.</span><span class="sxs-lookup"><span data-stu-id="0c218-110">The numbers listed on the Group Hub page are approximate counts only.</span></span> <span data-ttu-id="0c218-111">Par exemple, les nombres affichés sous **exécutant des instances de service** ou **instances de service suspendues** ne peut pas égal au nombre de total de l’exécution des instances de service ou des instances de service suspendues l’état du système a été modifiée alors que les différentes statistiques sur la page Hub sont générés.</span><span class="sxs-lookup"><span data-stu-id="0c218-111">For example, the numbers displayed under **Running service instances** or **Suspended service instances** might not equal the total number of running service instances or suspended service instances because the state of the system could change while the various statistics on the Hub page are being generated.</span></span>  
  
-   <span data-ttu-id="0c218-112">Le **Instances de Service suivies** et **événements de Message suivis** sections exécutent des requêtes sur les événements de message et l’état des instances de service avec une correspondance maximale = 50.</span><span class="sxs-lookup"><span data-stu-id="0c218-112">The **Tracked Service Instances** and **Tracked Message Events** sections execute queries on message events and the state of service instances with a maximum match = 50.</span></span>  
  
    -   <span data-ttu-id="0c218-113">**Instances de service suivies** requête recherche les instances de service suivies.</span><span class="sxs-lookup"><span data-stu-id="0c218-113">**Tracked service instances** query searches for tracked service instances.</span></span>  
  
    -   <span data-ttu-id="0c218-114">**Instances terminées** requête recherche les instances de service suivies dont l’état terminé.</span><span class="sxs-lookup"><span data-stu-id="0c218-114">**Completed instances** query searches for tracked service instances with state equal to completed.</span></span>  
  
    -   <span data-ttu-id="0c218-115">**Instances arrêtées** requête recherche les instances de service suivies dont l’état arrêté.</span><span class="sxs-lookup"><span data-stu-id="0c218-115">**Terminated instances** query searches for tracked service instances with state equal to terminated.</span></span>  
  
    -   <span data-ttu-id="0c218-116">**Événements des messages suivis** requête recherche les événements des messages suivis.</span><span class="sxs-lookup"><span data-stu-id="0c218-116">**Tracked message events** query searches for tracked message events.</span></span>  
  
    -   <span data-ttu-id="0c218-117">**Événements d’échec de transmission** recherche les événements de message suivi avec un type d’événement d’échec de la transmission de la requête.</span><span class="sxs-lookup"><span data-stu-id="0c218-117">**Transmission failure events** query searches for tracked message events with an event type of transmission failure.</span></span>  
  
-   <span data-ttu-id="0c218-118">Le **rapports d’état EDI** et **rapports d’état EDIINT** sections, situées en bas de la page Hub du groupe, affiche quatre rapports sur les échanges EDI et l’autre sur les échanges AS2 : l’échange EDI État de l’accusé de réception corrélé rapports, le rapport d’état du lot, le rapport d’agrégation de l’échange, la Transaction rapport d’agrégation et le rapport Message AS2 et état MDN corrélé.</span><span class="sxs-lookup"><span data-stu-id="0c218-118">The **EDI Status Reports** and **EDIINT Status Reports** sections, located at the bottom of the Group Hub page, displays four reports about EDI interchanges and one about AS2 interchanges: the EDI Interchange and Correlated ACK Status reports, the Batch Status report, the Interchange Aggregation Report, the Transaction Set Aggregation Report, and the AS2 Message and Correlated MDN Status report.</span></span> <span data-ttu-id="0c218-119">Pour plus d’informations sur ces rapports, consultez [EDI et AS2 le rapport d’état](../core/edi-and-as2-status-reporting.md).</span><span class="sxs-lookup"><span data-stu-id="0c218-119">For more information about these reports, see [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0c218-120">Les sections de rapport d’état EDIINT et EDI seront affiche uniquement si les fonctionnalités EDI/AS2 sont configurées pour ce groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0c218-120">The EDI and EDIINT Status Report sections will only be displayed if the EDI/AS2 features are configured for this BizTalk group.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0c218-121">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0c218-121">In This Section</span></span>  
  
-   [<span data-ttu-id="0c218-122">États d’Instance de service</span><span class="sxs-lookup"><span data-stu-id="0c218-122">Service Instance States</span></span>](../core/service-instance-states.md)  
  
-   [<span data-ttu-id="0c218-123">Enquête sur les échecs de messages, de Port et d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="0c218-123">Investigating Orchestration, Port, and Message Failures</span></span>](../core/investigating-orchestration-port-and-message-failures.md)  
  
-   [<span data-ttu-id="0c218-124">À l’aide de l’onglet requête de la Console Administration</span><span class="sxs-lookup"><span data-stu-id="0c218-124">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)  
  
-   [<span data-ttu-id="0c218-125">Affichage des messages suivis et les données d’Instance</span><span class="sxs-lookup"><span data-stu-id="0c218-125">Viewing Tracked Message and Instance Data</span></span>](../core/viewing-tracked-message-and-instance-data.md)  
  
-   [<span data-ttu-id="0c218-126">Suivi des activités et contrôle d’intégrité</span><span class="sxs-lookup"><span data-stu-id="0c218-126">Health and Activity Tracking</span></span>](../core/health-and-activity-tracking.md)
---
title: "Comment rechercher des Instances de Service en cours d’exécution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service instances, viewing
- service instances, Query tab [Administration Console]
- Query tab [Administration Console], service instances
- Query tab [Administration Console], searching
- service instances, searching
- service instances, running
ms.assetid: fc65bf33-c013-4e6a-b9fd-b4536811e7b4
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8873747b39d6fa178b813d361b72ccf24f44b54a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-search-for-running-service-instances"></a><span data-ttu-id="eb903-102">Recherche des instances de service en cours d'exécution</span><span class="sxs-lookup"><span data-stu-id="eb903-102">How to Search for Running Service Instances</span></span>
<span data-ttu-id="eb903-103">Vous pouvez utiliser la **requête** onglet dans la Console Administration de BizTalk Server pour rechercher une mise en attente, active, dans le point d’arrêt, planifié et une nouvelle tentative de l’instance de service.</span><span class="sxs-lookup"><span data-stu-id="eb903-103">You can use the **Query** tab in the BizTalk Server Administration Console to search for a specific dehydrated, active, in breakpoint, scheduled, and retrying service instance.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="eb903-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="eb903-104">Prerequisites</span></span>  
 <span data-ttu-id="eb903-105">Pour exécuter cette procédure, vous devez être connecté en tant que membre du groupe des opérateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="eb903-105">To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group.</span></span>  
  
### <a name="to-search-for-running-service-instances"></a><span data-ttu-id="eb903-106">Pour rechercher les instances de service en cours d'exécution</span><span class="sxs-lookup"><span data-stu-id="eb903-106">To search for running service instances</span></span>  
  
1.  <span data-ttu-id="eb903-107">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="eb903-107">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="eb903-108">Dans l'arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis cliquez sur le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="eb903-108">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="eb903-109">Dans le volet détails, cliquez sur le **nouvelle requête** onglet.</span><span class="sxs-lookup"><span data-stu-id="eb903-109">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="eb903-110">Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **en cours d’exécution des Instances de Service** dans la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="eb903-110">In the **Query Expression** group, in the **Value** column, select **Running Service Instances** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="eb903-111">Dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez un ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb903-111">In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select one or more of the following:</span></span>  
  
    |<span data-ttu-id="eb903-112">Élément</span><span class="sxs-lookup"><span data-stu-id="eb903-112">Item</span></span>|<span data-ttu-id="eb903-113"> Description</span><span class="sxs-lookup"><span data-stu-id="eb903-113">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="eb903-114">**Application Name**</span><span class="sxs-lookup"><span data-stu-id="eb903-114">**Application Name**</span></span>|<span data-ttu-id="eb903-115">Application BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="eb903-115">The BizTalk Server application.</span></span>|  
    |<span data-ttu-id="eb903-116">**Heure de création**</span><span class="sxs-lookup"><span data-stu-id="eb903-116">**Creation Time**</span></span>|<span data-ttu-id="eb903-117">Permet de rechercher les instances de service en cours d'exécution qui ont été créées avant ou après la date mentionnée.</span><span class="sxs-lookup"><span data-stu-id="eb903-117">Find running service instances created before or after the specified date.</span></span>|  
    |<span data-ttu-id="eb903-118">**Grouper les résultats selon**</span><span class="sxs-lookup"><span data-stu-id="eb903-118">**Group Results By**</span></span>|<span data-ttu-id="eb903-119">Vous pouvez regrouper les résultats par application, nom d'hôte, type d'opération en attente, classe de service, état de l'instance de service ou nom de service.</span><span class="sxs-lookup"><span data-stu-id="eb903-119">You can group results by application, host name, pending operation type, service class, service instance status, or service name.</span></span>|  
    |<span data-ttu-id="eb903-120">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="eb903-120">**Host Name**</span></span>|<span data-ttu-id="eb903-121">Nom de l'hôte BizTalk</span><span class="sxs-lookup"><span data-stu-id="eb903-121">The name of the BizTalk Host.</span></span>|  
    |<span data-ttu-id="eb903-122">**État de l’instance**</span><span class="sxs-lookup"><span data-stu-id="eb903-122">**Instance Status**</span></span>|<span data-ttu-id="eb903-123">Vous pouvez rechercher les instances actives, mises en attente, prêtes à être exécutées et planifiées.</span><span class="sxs-lookup"><span data-stu-id="eb903-123">You can search for active instances, dehydrated instances, ready to run instances, and scheduled instances.</span></span>|  
    |<span data-ttu-id="eb903-124">**Correspondances maximales**</span><span class="sxs-lookup"><span data-stu-id="eb903-124">**Maximum Matches**</span></span>|<span data-ttu-id="eb903-125">Nombre de résultats à afficher.</span><span class="sxs-lookup"><span data-stu-id="eb903-125">The number of matches to display.</span></span>|  
    |<span data-ttu-id="eb903-126">**Opérations en attente**</span><span class="sxs-lookup"><span data-stu-id="eb903-126">**Pending Operations**</span></span>|<span data-ttu-id="eb903-127">Vous pouvez rechercher les instances de service en cours d'exécution pour lesquelles la suspension ou l'arrêt est en attente.</span><span class="sxs-lookup"><span data-stu-id="eb903-127">You can search for running service instances that are pending suspension or termination.</span></span>|  
    |<span data-ttu-id="eb903-128">**Classe de service**</span><span class="sxs-lookup"><span data-stu-id="eb903-128">**Service Class**</span></span>|<span data-ttu-id="eb903-129">Vous pouvez rechercher des adaptateurs isolés (adaptateurs de messagerie), MSMQT, l'orchestration ou le rapport de l'échec du routage.</span><span class="sxs-lookup"><span data-stu-id="eb903-129">You can search for isolated adapters; messaging; messaging, and isolated adapters; MSMQT; Orchestration; or Routing Failure Report.</span></span>|  
    |<span data-ttu-id="eb903-130">**Nom du service**</span><span class="sxs-lookup"><span data-stu-id="eb903-130">**Service Name**</span></span>|<span data-ttu-id="eb903-131">Vous pouvez grouper ou filtrer les instances de service en cours d'exécution en fonction du nom du service.</span><span class="sxs-lookup"><span data-stu-id="eb903-131">You can group or filter running service instances by service name.</span></span>|  
    |<span data-ttu-id="eb903-132">**ID du Type de service**</span><span class="sxs-lookup"><span data-stu-id="eb903-132">**Service Type ID**</span></span>|<span data-ttu-id="eb903-133">Vous pouvez grouper ou filtrer les messages par ID de type de service.</span><span class="sxs-lookup"><span data-stu-id="eb903-133">You can group or filter messages by service type ID.</span></span>|  
  
6.  <span data-ttu-id="eb903-134">Terminer la **valeur** colonne en fonction de la sélection que vous avez effectuée dans le **nom de champ** colonne.</span><span class="sxs-lookup"><span data-stu-id="eb903-134">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  
  
7.  <span data-ttu-id="eb903-135">Continuez à ajouter des lignes supplémentaires à la requête si nécessaire, en effectuant le **nom de champ**, **opérateur**, et **valeurs** colonnes, puis cliquez sur **exécuter Requête**.</span><span class="sxs-lookup"><span data-stu-id="eb903-135">Continue adding additional lines to the query as appropriate, by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb903-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb903-136">See Also</span></span>  
 [<span data-ttu-id="eb903-137">À l’aide de l’onglet requête de la Console Administration</span><span class="sxs-lookup"><span data-stu-id="eb903-137">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)
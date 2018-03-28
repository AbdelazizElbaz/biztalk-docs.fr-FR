---
title: Recherche de toutes les Instances de Service | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service instances, Query tab [Administration Console]
- Query tab [Administration Console], service instances
- Query tab [Administration Console], searching
- service instances, searching
- instances, services
ms.assetid: 48cb885c-aaf1-44e8-9810-2e70cf63db81
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e96622fad23c28c0d4147f64a11cc540e88e7f97
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-search-for-all-service-instances"></a><span data-ttu-id="5b446-102">Recherche de toutes les instances de service</span><span class="sxs-lookup"><span data-stu-id="5b446-102">How to Search for All Service Instances</span></span>
<span data-ttu-id="5b446-103">Vous pouvez utiliser la **requête** onglet dans la Console Administration de BizTalk Server pour rechercher toutes les instances de service.</span><span class="sxs-lookup"><span data-stu-id="5b446-103">You can use the **Query** tab in the BizTalk Server Administration Console to search for all service instances.</span></span> <span data-ttu-id="5b446-104">Vous ne pouvez pas désinscrire un type de service spécifique si certaines instances sont en cours d'exécution ou suspendues.</span><span class="sxs-lookup"><span data-stu-id="5b446-104">You cannot unenlist a specific service type if there are any running or suspended instances.</span></span> <span data-ttu-id="5b446-105">Ainsi, avant de désinscrire un type de service, vous pouvez rechercher toutes les instances de service pour vous assurer qu'aucune de ces instances n'est en cours d'exécution ou suspendue.</span><span class="sxs-lookup"><span data-stu-id="5b446-105">For example, before you can unenlist a specific service type, you can search for all service instances to ensure that there are no running or suspended instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b446-106">En cas de regroupement et de filtrage par URI, seuls les ports d'envoi et de réception sont affichés dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="5b446-106">When Grouping and Filtering by URI, only send and receive ports are displayed in the results.</span></span> <span data-ttu-id="5b446-107">Ce type de regroupement et de filtrage ne peut pas être appliqué aux orchestrations, qui ne sont pas incluses dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="5b446-107">Grouping and Filtering by URI is not possible for orchestrations, which are not included in the displayed results.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5b446-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5b446-108">Prerequisites</span></span>  
 <span data-ttu-id="5b446-109">Pour exécuter cette procédure, vous devez être connecté en tant que membre du groupe des opérateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="5b446-109">To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group.</span></span>  
  
### <a name="to-search-for-all-service-instances"></a><span data-ttu-id="5b446-110">Pour rechercher toutes les instances de service</span><span class="sxs-lookup"><span data-stu-id="5b446-110">To search for all service instances</span></span>  
  
1.  <span data-ttu-id="5b446-111">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="5b446-111">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="5b446-112">Dans l'arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis cliquez sur le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5b446-112">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="5b446-113">Dans le volet détails, cliquez sur le **nouvelle requête** onglet.</span><span class="sxs-lookup"><span data-stu-id="5b446-113">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="5b446-114">Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **toutes les Instances de Service en cours d’exécution** dans la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="5b446-114">In the **Query Expression** group, in the **Value** column, select **All In-Progress Service Instances** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="5b446-115">Dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez un ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5b446-115">In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select one or more of the following:</span></span>  
  
    |<span data-ttu-id="5b446-116">Utiliser</span><span class="sxs-lookup"><span data-stu-id="5b446-116">Use this</span></span>|<span data-ttu-id="5b446-117">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="5b446-117">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="5b446-118">**Application Name**</span><span class="sxs-lookup"><span data-stu-id="5b446-118">**Application Name**</span></span>|<span data-ttu-id="5b446-119">Application BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="5b446-119">The BizTalk Server application.</span></span>|  
    |<span data-ttu-id="5b446-120">**Heure de création**</span><span class="sxs-lookup"><span data-stu-id="5b446-120">**Creation Time**</span></span>|<span data-ttu-id="5b446-121">Permet de rechercher toutes les instances de service qui ont été créées avant ou après la date mentionnée.</span><span class="sxs-lookup"><span data-stu-id="5b446-121">Find all service instances created before or after the specified date.</span></span>|  
    |<span data-ttu-id="5b446-122">**Grouper les résultats selon**</span><span class="sxs-lookup"><span data-stu-id="5b446-122">**Group Results By**</span></span>|<span data-ttu-id="5b446-123">Vous pouvez regrouper les résultats par application, nom d'hôte, classe de service, état de l'instance de service ou nom de service.</span><span class="sxs-lookup"><span data-stu-id="5b446-123">You can group results by application, host name, service class, service instance status, or service name.</span></span>|  
    |<span data-ttu-id="5b446-124">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="5b446-124">**Host Name**</span></span>|<span data-ttu-id="5b446-125">Nom de l'hôte BizTalk</span><span class="sxs-lookup"><span data-stu-id="5b446-125">The name of the BizTalk Host.</span></span>|  
    |<span data-ttu-id="5b446-126">**État de l’instance**</span><span class="sxs-lookup"><span data-stu-id="5b446-126">**Instance Status**</span></span>|<span data-ttu-id="5b446-127">Vous pouvez rechercher toutes les instances en cours d'exécution, suspendues, actives, mises en attente, exécutables, planifiées, suspendues sans reprise possible ou suspendues avec reprise possible.</span><span class="sxs-lookup"><span data-stu-id="5b446-127">You can search for all running instances, all suspended instances, active instances, dehydrated instances, ready to run instances, scheduled instances, suspended but not resumable instances, or suspended and resumable instances.</span></span>|  
    |<span data-ttu-id="5b446-128">**Correspondances maximales**</span><span class="sxs-lookup"><span data-stu-id="5b446-128">**Maximum Matches**</span></span>|<span data-ttu-id="5b446-129">Nombre de résultats à afficher (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="5b446-129">The number of matches to display (required).</span></span> <span data-ttu-id="5b446-130">Cela est généralement défini sur 50, la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="5b446-130">This is usually set to 50, the default.</span></span><br /><br /> <span data-ttu-id="5b446-131">Lorsque vous incluez l'option Grouper les résultats selon, le nombre de groupes s'affiche et non le nombre total d'enregistrements.</span><span class="sxs-lookup"><span data-stu-id="5b446-131">When you include Group Results By, this displays the number of groups, not the total number of records.</span></span>|  
    |<span data-ttu-id="5b446-132">**Classe de service**</span><span class="sxs-lookup"><span data-stu-id="5b446-132">**Service Class**</span></span>|<span data-ttu-id="5b446-133">Vous pouvez rechercher des adaptateurs isolés (adaptateurs de messagerie), MSMQT, l'orchestration ou le rapport de l'échec du routage.</span><span class="sxs-lookup"><span data-stu-id="5b446-133">You can search for isolated adapters; messaging; messaging, and isolated adapters; MSMQT; Orchestration; or Routing Failure Report.</span></span>|  
    |<span data-ttu-id="5b446-134">**ID d’Instance de service**</span><span class="sxs-lookup"><span data-stu-id="5b446-134">**Service Instance ID**</span></span>|<span data-ttu-id="5b446-135">Vous pouvez grouper ou filtrer les instances de service en fonction de leur ID.</span><span class="sxs-lookup"><span data-stu-id="5b446-135">You can group or filter service instances by service instance ID.</span></span>|  
    |<span data-ttu-id="5b446-136">**Nom du service**</span><span class="sxs-lookup"><span data-stu-id="5b446-136">**Service Name**</span></span>|<span data-ttu-id="5b446-137">Vous pouvez grouper ou filtrer les instances de service par nom de service.</span><span class="sxs-lookup"><span data-stu-id="5b446-137">You can group or filter service instances by service name.</span></span>|  
    |<span data-ttu-id="5b446-138">**ID du Type de service**</span><span class="sxs-lookup"><span data-stu-id="5b446-138">**Service Type ID**</span></span>|<span data-ttu-id="5b446-139">Vous pouvez grouper ou filtrer les instances de service par ID de type de service.</span><span class="sxs-lookup"><span data-stu-id="5b446-139">You can group or filter service instances by service type ID.</span></span>|  
  
6.  <span data-ttu-id="5b446-140">Terminer la **valeur** colonne en fonction de la sélection que vous avez effectuée dans le **nom de champ** colonne.</span><span class="sxs-lookup"><span data-stu-id="5b446-140">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  
  
7.  <span data-ttu-id="5b446-141">Continuez à ajouter des lignes supplémentaires à la requête si nécessaire, en effectuant le **nom de champ**, **opérateur**, et **valeurs** colonnes, puis cliquez sur **exécuter Requête**.</span><span class="sxs-lookup"><span data-stu-id="5b446-141">Continue adding additional lines to the query as appropriate, by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b446-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b446-142">See Also</span></span>  
 [<span data-ttu-id="5b446-143">Utilisation de l’onglet Requête de la console Administration</span><span class="sxs-lookup"><span data-stu-id="5b446-143">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)
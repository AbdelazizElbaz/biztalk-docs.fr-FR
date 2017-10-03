---
title: Comment rechercher des Instances de Service suivies | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6337df9-8c2e-4d4a-a64b-cc040f83bd91
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08e5a7fa563e175d6a1d784e546bd399e20d3c21
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-search-for-tracked-service-instances"></a><span data-ttu-id="c9a27-102">Recherche d'instances de service suivies</span><span class="sxs-lookup"><span data-stu-id="c9a27-102">How to Search for Tracked Service Instances</span></span>
<span data-ttu-id="c9a27-103">Vous pouvez utiliser la **requête** onglet dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] la console Administration pour rechercher toutes les instances de service suivies.</span><span class="sxs-lookup"><span data-stu-id="c9a27-103">You can use the **Query** tab in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to search for all tracked service instances.</span></span> <span data-ttu-id="c9a27-104">Pour localiser les instances de service, vous pouvez effectuer une recherche sur le nom et la version de l'assembly, les heures de début et de fin de sa durée de vie, le nom ou l'ID d'instance de la classe de service, le nom de l'hôte, le code d'erreur et l'état de l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="c9a27-104">To locate service instances, you can search on the name and version of the assembly, the start and end times of its lifetime, the name or instance ID of the service class, host name, error code, and the state of the service instance.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c9a27-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="c9a27-105">Prerequisites</span></span>  
 <span data-ttu-id="c9a27-106">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Opérateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c9a27-106">To perform this procedure, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators group.</span></span>  
  
### <a name="to-search-for-tracked-service-instances"></a><span data-ttu-id="c9a27-107">Pour rechercher les instances de service suivies</span><span class="sxs-lookup"><span data-stu-id="c9a27-107">To search for tracked service instances</span></span>  
  
1.  <span data-ttu-id="c9a27-108">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c9a27-108">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2.  <span data-ttu-id="c9a27-109">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, puis cliquez sur le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c9a27-109">In the console tree, expand **BizTalk Server Administration**, and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="c9a27-110">Dans le volet détails, cliquez sur le **nouvelle requête** onglet.</span><span class="sxs-lookup"><span data-stu-id="c9a27-110">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="c9a27-111">Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **Instances de Service suivies** dans la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c9a27-111">In the **Query Expression** group, in the **Value** column, select **Tracked Service Instances** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="c9a27-112">Dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez un ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="c9a27-112">In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select one or more of the following:</span></span>  
  
    |<span data-ttu-id="c9a27-113">Élément</span><span class="sxs-lookup"><span data-stu-id="c9a27-113">Item</span></span>|<span data-ttu-id="c9a27-114"> Description</span><span class="sxs-lookup"><span data-stu-id="c9a27-114">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="c9a27-115">**Nom de l’assembly**</span><span class="sxs-lookup"><span data-stu-id="c9a27-115">**Assembly Name**</span></span>|<span data-ttu-id="c9a27-116">Nom de l'assembly pour l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="c9a27-116">Name of the assembly for the service instance.</span></span>|  
    |<span data-ttu-id="c9a27-117">**Version de l’assembly**</span><span class="sxs-lookup"><span data-stu-id="c9a27-117">**Assembly Version**</span></span>|<span data-ttu-id="c9a27-118">Version de l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="c9a27-118">Version of the service instance.</span></span>|  
    |<span data-ttu-id="c9a27-119">**Heure de fin**</span><span class="sxs-lookup"><span data-stu-id="c9a27-119">**End Time**</span></span>|<span data-ttu-id="c9a27-120">Heure de fin de l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="c9a27-120">End time of the service instance.</span></span>|  
    |<span data-ttu-id="c9a27-121">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="c9a27-121">**Error Code**</span></span>|<span data-ttu-id="c9a27-122">Code de l'erreur associée à l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="c9a27-122">Any error code associated with the service instance.</span></span>|  
    |<span data-ttu-id="c9a27-123">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="c9a27-123">**Host Name**</span></span>|<span data-ttu-id="c9a27-124">Nom de l'hôte de l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="c9a27-124">The host name of the service instance.</span></span>|  
    |<span data-ttu-id="c9a27-125">**Correspondances maximales**</span><span class="sxs-lookup"><span data-stu-id="c9a27-125">**Maximum Matches**</span></span>|<span data-ttu-id="c9a27-126">Nombre de résultats à afficher.</span><span class="sxs-lookup"><span data-stu-id="c9a27-126">The number of matches to display.</span></span>|  
    |<span data-ttu-id="c9a27-127">**Classe de service**</span><span class="sxs-lookup"><span data-stu-id="c9a27-127">**Service Class**</span></span>|<span data-ttu-id="c9a27-128">Classe de l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="c9a27-128">The class of the service instance.</span></span>|  
    |<span data-ttu-id="c9a27-129">**ID d’Instance de service**</span><span class="sxs-lookup"><span data-stu-id="c9a27-129">**Service Instance ID**</span></span>|<span data-ttu-id="c9a27-130">ID de l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="c9a27-130">The service instance ID.</span></span>|  
    |<span data-ttu-id="c9a27-131">**Nom du service**</span><span class="sxs-lookup"><span data-stu-id="c9a27-131">**Service Name**</span></span>|<span data-ttu-id="c9a27-132">Le nom de l’instance de service.</span><span class="sxs-lookup"><span data-stu-id="c9a27-132">The name of the service instance.</span></span>|  
    |<span data-ttu-id="c9a27-133">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="c9a27-133">**Start Time**</span></span>|<span data-ttu-id="c9a27-134">Heure de début de l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="c9a27-134">The start time of the service instance.</span></span>|  
    |<span data-ttu-id="c9a27-135">**État**</span><span class="sxs-lookup"><span data-stu-id="c9a27-135">**State**</span></span>|<span data-ttu-id="c9a27-136">État de l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="c9a27-136">The state of the service instance.</span></span>|  
  
6.  <span data-ttu-id="c9a27-137">Terminer la **valeur** colonne en fonction de la sélection que vous avez effectuée dans le **nom de champ** colonne.</span><span class="sxs-lookup"><span data-stu-id="c9a27-137">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  
  
7.  <span data-ttu-id="c9a27-138">Continuez à ajouter des lignes supplémentaires à la requête comme il convient en effectuant le **nom de champ**, **opérateur**, et **valeurs** colonnes, puis cliquez sur **exécuter Requête**.</span><span class="sxs-lookup"><span data-stu-id="c9a27-138">Continue adding additional lines to the query as appropriate by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a27-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9a27-139">See Also</span></span>  
 [<span data-ttu-id="c9a27-140">À l’aide de l’onglet requête de la Console Administration</span><span class="sxs-lookup"><span data-stu-id="c9a27-140">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)
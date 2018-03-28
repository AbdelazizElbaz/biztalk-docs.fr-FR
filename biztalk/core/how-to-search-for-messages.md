---
title: Comment rechercher des Messages | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, viewing
- messages, searching
- Query tab [Administration Console], searching
- Query tab [Administration Console], messages
ms.assetid: c751d23f-913a-4325-81da-a36d61c07e8b
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5443cc021bd5f97621f44d295432c99834bdaed
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-search-for-messages"></a><span data-ttu-id="7ad98-102">Recherche de messages</span><span class="sxs-lookup"><span data-stu-id="7ad98-102">How to Search for Messages</span></span>
<span data-ttu-id="7ad98-103">Vous pouvez utiliser la **requête** onglet dans la Console Administration de BizTalk Server pour rechercher une classe spécifique de messages.</span><span class="sxs-lookup"><span data-stu-id="7ad98-103">You can use the **Query** tab in the BizTalk Server Administration Console to search for a specific class of messages.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7ad98-104">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7ad98-104">Prerequisites</span></span>  
 <span data-ttu-id="7ad98-105">Pour exécuter cette procédure, vous devez être connecté en tant que membre du groupe des opérateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7ad98-105">To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group.</span></span>  
  
### <a name="to-search-for-messages"></a><span data-ttu-id="7ad98-106">Pour rechercher des messages</span><span class="sxs-lookup"><span data-stu-id="7ad98-106">To search for messages</span></span>  
  
1.  <span data-ttu-id="7ad98-107">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="7ad98-107">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="7ad98-108">Dans l'arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis cliquez sur le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7ad98-108">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="7ad98-109">Dans le volet détails, cliquez sur le **nouvelle requête** onglet.</span><span class="sxs-lookup"><span data-stu-id="7ad98-109">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="7ad98-110">Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **Messages** dans la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="7ad98-110">In the **Query Expression** group, in the **Value** column, select **Messages** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="7ad98-111">Dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez un ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="7ad98-111">In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select one or more of the following:</span></span>  
  
    |<span data-ttu-id="7ad98-112">Élément</span><span class="sxs-lookup"><span data-stu-id="7ad98-112">Item</span></span>|<span data-ttu-id="7ad98-113"> Description</span><span class="sxs-lookup"><span data-stu-id="7ad98-113">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="7ad98-114">**Heure de création**</span><span class="sxs-lookup"><span data-stu-id="7ad98-114">**Creation Time**</span></span>|<span data-ttu-id="7ad98-115">Permet de rechercher les messages créés avant ou après la date spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7ad98-115">Find messages created before or after the specified date.</span></span>|  
    |<span data-ttu-id="7ad98-116">**Adaptateur de l’erreur**</span><span class="sxs-lookup"><span data-stu-id="7ad98-116">**Error Adapter**</span></span>|<span data-ttu-id="7ad98-117">Vous pouvez regrouper ou filtrer les messages par type d’adaptateur : fichier, FTP, HTTP, MQSeries, MSMQ, POP3, SMTP, SOAP ou Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="7ad98-117">You can group or filter messages by adapter type: FILE, FTP, HTTP, MQSeries, MSMQ, POP3, SMTP, SOAP, or Windows SharePoint Services.</span></span>|  
    |<span data-ttu-id="7ad98-118">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="7ad98-118">**Error Code**</span></span>|<span data-ttu-id="7ad98-119">Vous pouvez regrouper ou filtrer les messages par code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="7ad98-119">You can group or filter messages by error code.</span></span>|  
    |<span data-ttu-id="7ad98-120">**Description de l’erreur**</span><span class="sxs-lookup"><span data-stu-id="7ad98-120">**Error Description**</span></span>|<span data-ttu-id="7ad98-121">Vous pouvez regrouper ou filtrer les messages en fonction de la description de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="7ad98-121">You can group or filter messages by error description.</span></span>|  
    |<span data-ttu-id="7ad98-122">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="7ad98-122">**Host Name**</span></span>|<span data-ttu-id="7ad98-123">Vous pouvez regrouper ou filtrer les messages en fonction du nom de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="7ad98-123">You can group or filter messages by host name.</span></span>|  
    |<span data-ttu-id="7ad98-124">**État de l’instance**</span><span class="sxs-lookup"><span data-stu-id="7ad98-124">**Instance Status**</span></span>|<span data-ttu-id="7ad98-125">État de l'instance de service faisant référence au message.</span><span class="sxs-lookup"><span data-stu-id="7ad98-125">The status of the service instance referencing the message.</span></span> <span data-ttu-id="7ad98-126">Vous pouvez rechercher tous les types d’instances suivantes : toutes les instances en cours d’exécution, toutes les instances suspendues, instances actives, instances mises en attente, les instances de prêt à s’exécuter, instances planifiées, suspendues, mais ne peut pas être repris instances, ou suspendus et peut être repris instances.</span><span class="sxs-lookup"><span data-stu-id="7ad98-126">You can search for all of the following types of instances: all running instances, all suspended instances, active instances, dehydrated instances, ready-to-run instances, scheduled instances, suspended but not resumable instances, or suspended and resumable instances.</span></span>|  
    |<span data-ttu-id="7ad98-127">**Correspondances maximales**</span><span class="sxs-lookup"><span data-stu-id="7ad98-127">**Maximum Matches**</span></span>|<span data-ttu-id="7ad98-128">Nombre de résultats à afficher.</span><span class="sxs-lookup"><span data-stu-id="7ad98-128">The number of matches to display.</span></span>|  
    |<span data-ttu-id="7ad98-129">**ID de message**</span><span class="sxs-lookup"><span data-stu-id="7ad98-129">**Message ID**</span></span>|<span data-ttu-id="7ad98-130">Vous pouvez regrouper ou filtrer les messages en fonction de l'ID du message.</span><span class="sxs-lookup"><span data-stu-id="7ad98-130">You can group or filter messages by message ID.</span></span>|  
    |<span data-ttu-id="7ad98-131">**État du message**</span><span class="sxs-lookup"><span data-stu-id="7ad98-131">**Message Status**</span></span>|<span data-ttu-id="7ad98-132">Vous pouvez rechercher les messages dont l'état est utilisé, en cours, suspendu, suspendu sans reprise possible, suspendu avec reprise possible, mis en file d'attente, mis en file d'attente et en attente de traitement, mis en file d'attente et planifié pour une remise ultérieure, et mis en file d'attente et en attente de nouvel essai.</span><span class="sxs-lookup"><span data-stu-id="7ad98-132">You can search for messages with consumed, in process, suspended, suspended but not resumable, suspended and resumable, queued, queued but awaiting processing, queued but scheduled for later delivery, and queued but waiting to retry.</span></span>|  
    |<span data-ttu-id="7ad98-133">**Type de message**</span><span class="sxs-lookup"><span data-stu-id="7ad98-133">**Message Type**</span></span>|<span data-ttu-id="7ad98-134">Vous pouvez regrouper ou filtrer les messages en fonction de leur type.</span><span class="sxs-lookup"><span data-stu-id="7ad98-134">You can group or filter messages by message type.</span></span>|  
    |<span data-ttu-id="7ad98-135">**Classe de service**</span><span class="sxs-lookup"><span data-stu-id="7ad98-135">**Service Class**</span></span>|<span data-ttu-id="7ad98-136">Vous pouvez rechercher des adaptateurs isolés (adaptateurs de messagerie), MSMQT, l'orchestration ou le rapport de l'échec du routage.</span><span class="sxs-lookup"><span data-stu-id="7ad98-136">You can search for isolated adapters; messaging; messaging, and isolated adapters; MSMQT; Orchestration; or Routing Failure Report.</span></span>|  
    |<span data-ttu-id="7ad98-137">**ID d’Instance de service**</span><span class="sxs-lookup"><span data-stu-id="7ad98-137">**Service Instance ID**</span></span>|<span data-ttu-id="7ad98-138">Vous pouvez grouper ou filtrer les messages par ID d'instance de service.</span><span class="sxs-lookup"><span data-stu-id="7ad98-138">You can group or filter messages by service instance ID.</span></span>|  
    |<span data-ttu-id="7ad98-139">**Nom du service**</span><span class="sxs-lookup"><span data-stu-id="7ad98-139">**Service Name**</span></span>|<span data-ttu-id="7ad98-140">Vous pouvez regrouper ou filtrer les messages par nom du service.</span><span class="sxs-lookup"><span data-stu-id="7ad98-140">You can group or filter messages by service name.</span></span>|  
    |<span data-ttu-id="7ad98-141">**ID du Type de service**</span><span class="sxs-lookup"><span data-stu-id="7ad98-141">**Service Type ID**</span></span>|<span data-ttu-id="7ad98-142">Vous pouvez grouper ou filtrer les messages par ID de type de service.</span><span class="sxs-lookup"><span data-stu-id="7ad98-142">You can group or filter messages by service type ID.</span></span>|  
    |<span data-ttu-id="7ad98-143">**URI**</span><span class="sxs-lookup"><span data-stu-id="7ad98-143">**URI**</span></span>|<span data-ttu-id="7ad98-144">Vous pouvez regrouper ou filtrer les messages par URI.</span><span class="sxs-lookup"><span data-stu-id="7ad98-144">You can group or filter messages by URI.</span></span>|  
  
6.  <span data-ttu-id="7ad98-145">Terminer la **valeur** colonne en fonction de la sélection que vous avez effectuée dans le **nom de champ** colonne.</span><span class="sxs-lookup"><span data-stu-id="7ad98-145">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  
  
7.  <span data-ttu-id="7ad98-146">Continuez à ajouter des lignes supplémentaires à la requête si nécessaire, en effectuant le **nom de champ**, **opérateur**, et **valeurs** colonnes, puis cliquez sur **exécuter Requête**.</span><span class="sxs-lookup"><span data-stu-id="7ad98-146">Continue adding additional lines to the query as appropriate, by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ad98-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ad98-147">See Also</span></span>  
 [<span data-ttu-id="7ad98-148">Utilisation de l’onglet Requête de la console Administration</span><span class="sxs-lookup"><span data-stu-id="7ad98-148">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)
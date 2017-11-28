---
title: "Création d’Instances de Service Bus d’événements BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 454bdde7-45a6-41ab-9196-f662273f0f2b
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afbe8f2e70baa3a963150991ced54a9d38adba88
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-instances-of-the-bam-event-bus-service"></a><span data-ttu-id="965fb-102">Création d’Instances de Service Bus d’événements BAM</span><span class="sxs-lookup"><span data-stu-id="965fb-102">Creating Instances of the BAM Event Bus Service</span></span>
<span data-ttu-id="965fb-103">Le service Bus d'événements BAM s'exécute au sein d'un hôte de l'application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="965fb-103">The BAM Event Bus Service runs inside a BizTalk application host.</span></span> <span data-ttu-id="965fb-104">Vous pouvez utiliser l'hôte par défaut pour héberger ce service ou en créer un.</span><span class="sxs-lookup"><span data-stu-id="965fb-104">You can use the default host to host the BAM Event Bus Service, or you can create a new host.</span></span> <span data-ttu-id="965fb-105">Si un hôte héberge le service Bus d'événements BAM, toutes les nouvelles instances que vous créez pour cet hôte hébergeront également le service.</span><span class="sxs-lookup"><span data-stu-id="965fb-105">If a host hosts the BAM Event Bus service, any new instances you create for that host also hosts the service.</span></span>  
  
 <span data-ttu-id="965fb-106">Pour plus d’informations sur l’hôte par défaut, consultez [hôtes](../core/hosts.md).</span><span class="sxs-lookup"><span data-stu-id="965fb-106">For information about the default host, see [Hosts](../core/hosts.md).</span></span>  
  
 <span data-ttu-id="965fb-107">Pour plus d’informations sur la création d’ordinateurs hôtes, consultez [la création d’un nouvel hôte](../core/how-to-create-a-new-host.md).</span><span class="sxs-lookup"><span data-stu-id="965fb-107">For information about creating hosts, see [How to Create a New Host](../core/how-to-create-a-new-host.md).</span></span>  
  
 <span data-ttu-id="965fb-108">Pour plus d’informations sur la création d’instances d’hôte, consultez [l’ajout d’une Instance d’hôte](../core/how-to-add-a-host-instance.md).</span><span class="sxs-lookup"><span data-stu-id="965fb-108">For information about creating host instances, see [How to Add a Host Instance](../core/how-to-add-a-host-instance.md).</span></span>  
  
 <span data-ttu-id="965fb-109">Pour plus d’informations sur la création et la configuration des ordinateurs hôtes et les instances d’hôte, consultez [gestion d’hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md).</span><span class="sxs-lookup"><span data-stu-id="965fb-109">For information about creating and configuring hosts and host instances, see [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md).</span></span>  
  
### <a name="to-create-the-host-that-hosts-the-bam-event-bus-service"></a><span data-ttu-id="965fb-110">Pour créer l'hôte qui héberge le service Bus d'événements BAM</span><span class="sxs-lookup"><span data-stu-id="965fb-110">To create the host that hosts the BAM Event Bus Service</span></span>  
  
1.  <span data-ttu-id="965fb-111">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="965fb-111">Click **Start**, point to **All Programs**, click **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="965fb-112">Dans la fenêtre de la Console Administration de BizTalk, développez le **Administration de BizTalk Server** nœud, développez le **groupe Biztalk** nœud et développez le **paramètres de plateforme** nœud , avec le bouton droit le **hôtes** nœud, sélectionnez **nouveau**, puis cliquez sur **hôte**.</span><span class="sxs-lookup"><span data-stu-id="965fb-112">In the BizTalk Administration Console window, expand the **BizTalk Server Administration** node, expand the **Biztalk Group** node and expand the **Platform Settings** node, right-click the **Hosts** node, select **New**, and then click **Host**.</span></span>  
  
3.  <span data-ttu-id="965fb-113">Dans le **propriétés de l’hôte** boîte de dialogue le **nom** zone, tapez un nom descriptif pour l’hôte.</span><span class="sxs-lookup"><span data-stu-id="965fb-113">In the **Host Properties** dialog box, in the **Name** box, type a descriptive name for the host.</span></span>  
  
4.  <span data-ttu-id="965fb-114">Sur le **général** onglet, sélectionnez le **autoriser le suivi de hôte** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="965fb-114">On the **General** tab, select the **Allow Host Tracking** check box.</span></span>  
  
     <span data-ttu-id="965fb-115">Un nouveau nœud enfant s’affiche sous le **hôtes** nœud portant le nom du nouvel hôte.</span><span class="sxs-lookup"><span data-stu-id="965fb-115">A new child node appears under the **Hosts** node with the name of the new host.</span></span>  
  
5.  <span data-ttu-id="965fb-116">Dans le **groupe Windows** , tapez le nom du groupe Windows à affecter à cet ordinateur hôte, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="965fb-116">In the **Windows group** box, type the name of the Windows group to assign this host, and then click **OK**.</span></span>  
  
     <span data-ttu-id="965fb-117">Un nouveau nœud enfant s’affiche sous le **hôtes** nœud portant le nom du nouvel hôte.</span><span class="sxs-lookup"><span data-stu-id="965fb-117">A new child node appears under the **Hosts** node with the name of the new host.</span></span>  
  
### <a name="to-create-a-new-host-instance-of-the-host"></a><span data-ttu-id="965fb-118">Pour créer une instance d'hôte de l'hôte</span><span class="sxs-lookup"><span data-stu-id="965fb-118">To create a new host instance of the host</span></span>  
  
1.  <span data-ttu-id="965fb-119">Avec le bouton droit le **Instance d’hôte** nœud, sélectionnez **nouveau**, puis cliquez sur **Instance d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="965fb-119">Right-click the **Host Instance** node, select **New**, and then click **Host Instance**.</span></span>  
  
2.  <span data-ttu-id="965fb-120">Sélectionnez un serveur sur lequel l’instance d’hôte s’exécuter, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="965fb-120">Select a server where the host instance will run, and then click **OK**.</span></span>  
  
### <a name="to-add-hosting-tracking-to-the-host"></a><span data-ttu-id="965fb-121">Pour activer le suivi de l'hôte</span><span class="sxs-lookup"><span data-stu-id="965fb-121">To add hosting tracking to the host</span></span>  
  
1.  <span data-ttu-id="965fb-122">Cliquez sur l’hôte que vous voulez reconfigurer, puis cliquez sur **propriétés** .</span><span class="sxs-lookup"><span data-stu-id="965fb-122">Right-click the host you want to reconfigure, and then click **Properties** .</span></span>  
  
2.  <span data-ttu-id="965fb-123">Sur le **général** onglet, sélectionnez **autoriser le suivi de hôte**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="965fb-123">On the **General** tab, select **Allow Host Tracking**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="965fb-124">Redémarrez toutes les instances de cet hôte.</span><span class="sxs-lookup"><span data-stu-id="965fb-124">Restart all instances of that host.</span></span>  
  
### <a name="to-remove-hosting-tracking-from-the-host"></a><span data-ttu-id="965fb-125">Pour désactiver le suivi de l'hôte</span><span class="sxs-lookup"><span data-stu-id="965fb-125">To remove hosting tracking from the host</span></span>  
  
1.  <span data-ttu-id="965fb-126">Cliquez sur l’ordinateur hôte à partir de laquelle vous souhaitez supprimer le suivi de l’hôte, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="965fb-126">Right-click the host from which you want to remove host tracking, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="965fb-127">Désactivez le **suivi de l’hôte d’autoriser** case à cocher, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="965fb-127">Clear the **Allow Host tracking** check box, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="965fb-128">Redémarrer les instances de cet hôte.</span><span class="sxs-lookup"><span data-stu-id="965fb-128">Restart instances of that host.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="965fb-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="965fb-129">See Also</span></span>  
 <span data-ttu-id="965fb-130">[La gestion de Service Bus d’événements BAM](../core/managing-the-bam-event-bus-service.md) </span><span class="sxs-lookup"><span data-stu-id="965fb-130">[Managing the BAM Event Bus Service](../core/managing-the-bam-event-bus-service.md) </span></span>  
 <span data-ttu-id="965fb-131">[Recommandations de sécurité BAM](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="965fb-131">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="965fb-132">Business Activity Monitoring (BAM)</span><span class="sxs-lookup"><span data-stu-id="965fb-132">Business Activity Monitoring (BAM)</span></span>](../core/business-activity-monitoring-bam.md)
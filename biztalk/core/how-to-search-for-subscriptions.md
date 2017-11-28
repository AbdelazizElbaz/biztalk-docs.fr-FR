---
title: Comment rechercher des abonnements | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Query tab [Administration Console], subscriptions
- Query tab [Administration Console], searching
- subscriptions, viewing
- subscriptions, searching
ms.assetid: 95f8fd20-2750-412b-a67b-18976e7706e2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f1830a4c1dddfa3dcfc2a1177b69410dd8ee0ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-search-for-subscriptions"></a><span data-ttu-id="f0156-102">Recherche d'abonnements</span><span class="sxs-lookup"><span data-stu-id="f0156-102">How to Search for Subscriptions</span></span>
<span data-ttu-id="f0156-103">Vous pouvez utiliser la **requête** onglet dans la Console Administration de BizTalk Server pour rechercher des abonnements.</span><span class="sxs-lookup"><span data-stu-id="f0156-103">You can use the **Query** tab in the BizTalk Server Administration Console to search for subscriptions.</span></span> <span data-ttu-id="f0156-104">Cela peut s'avérer utile pour vérifier tous les abonnements définis dans le système.</span><span class="sxs-lookup"><span data-stu-id="f0156-104">This is useful when you want to review all of the subscriptions defined in the system.</span></span> <span data-ttu-id="f0156-105">Lors du dépannage des échecs de routage, vous pouvez vérifier les abonnements pour identifier ceux qui seraient mal configurés et causeraient l'échec du routage.</span><span class="sxs-lookup"><span data-stu-id="f0156-105">When troubleshooting routing failures, you can review subscriptions to see if any of them are improperly configured, thereby causing the routing failure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f0156-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f0156-106">Prerequisites</span></span>  
 <span data-ttu-id="f0156-107">Pour exécuter cette procédure, vous devez être connecté en tant que membre du groupe des opérateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f0156-107">To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group.</span></span>  
  
### <a name="to-search-for-subscriptions"></a><span data-ttu-id="f0156-108">Pour rechercher des abonnements</span><span class="sxs-lookup"><span data-stu-id="f0156-108">To search for subscriptions</span></span>  
  
1.  <span data-ttu-id="f0156-109">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0156-109">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2.  <span data-ttu-id="f0156-110">Dans l'arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis cliquez sur le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f0156-110">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="f0156-111">Dans le volet détails, cliquez sur le **nouvelle requête** onglet.</span><span class="sxs-lookup"><span data-stu-id="f0156-111">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="f0156-112">Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **abonnements** dans la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f0156-112">In the **Query Expression** group, in the **Value** column, select **Subscriptions** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="f0156-113">Dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez un ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f0156-113">In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select one or more of the following:</span></span>  
  
    |<span data-ttu-id="f0156-114">Élément</span><span class="sxs-lookup"><span data-stu-id="f0156-114">Item</span></span>|<span data-ttu-id="f0156-115"> Description</span><span class="sxs-lookup"><span data-stu-id="f0156-115">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="f0156-116">**Correspondances maximales**</span><span class="sxs-lookup"><span data-stu-id="f0156-116">**Maximum Matches**</span></span>|<span data-ttu-id="f0156-117">Nombre de résultats à afficher.</span><span class="sxs-lookup"><span data-stu-id="f0156-117">The number of matches to display.</span></span>|  
    |<span data-ttu-id="f0156-118">**ID d’Instance de service**</span><span class="sxs-lookup"><span data-stu-id="f0156-118">**Service Instance ID**</span></span>|<span data-ttu-id="f0156-119">Vous pouvez filtrer les abonnements par ID d'instance de service.</span><span class="sxs-lookup"><span data-stu-id="f0156-119">You can filter subscriptions by service instance ID.</span></span>|  
    |<span data-ttu-id="f0156-120">**Nom du service**</span><span class="sxs-lookup"><span data-stu-id="f0156-120">**Service Name**</span></span>|<span data-ttu-id="f0156-121">Vous pouvez filtrer les abonnements par nom de service.</span><span class="sxs-lookup"><span data-stu-id="f0156-121">You can filter subscriptions by service name.</span></span>|  
    |<span data-ttu-id="f0156-122">**Type d’abonnement**</span><span class="sxs-lookup"><span data-stu-id="f0156-122">**Subscription Type**</span></span>|<span data-ttu-id="f0156-123">Vous pouvez filtrer les abonnements par abonnement d'activation ou par abonnement d'instance.</span><span class="sxs-lookup"><span data-stu-id="f0156-123">You can filter subscriptions by Activation Subscription or Instance Subscription.</span></span>|  
  
6.  <span data-ttu-id="f0156-124">Terminer la **valeur** colonne en fonction de la sélection que vous avez effectuée dans le **nom de champ** colonne.</span><span class="sxs-lookup"><span data-stu-id="f0156-124">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  
  
7.  <span data-ttu-id="f0156-125">Continuez à ajouter des lignes supplémentaires à la requête si nécessaire, en effectuant le **nom de champ**, **opérateur**, et **valeurs** colonnes, puis cliquez sur **exécuter Requête**.</span><span class="sxs-lookup"><span data-stu-id="f0156-125">Continue adding additional lines to the query as appropriate, by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0156-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0156-126">See Also</span></span>  
 [<span data-ttu-id="f0156-127">À l’aide de l’onglet requête de la Console Administration</span><span class="sxs-lookup"><span data-stu-id="f0156-127">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)
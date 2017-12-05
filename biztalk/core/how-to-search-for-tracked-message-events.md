---
title: "Comment rechercher des événements de Message suivis | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18df4cf7-c307-4175-926c-9be9f30b29ed
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6a3597d0d68dbd79de6c23e7b6d4b222b9c8376
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-search-for-tracked-message-events"></a><span data-ttu-id="b388a-102">Recherche des événements de message suivis</span><span class="sxs-lookup"><span data-stu-id="b388a-102">How to Search for Tracked Message Events</span></span>
<span data-ttu-id="b388a-103">Vous pouvez utiliser la **nouvelle requête** onglet dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour rechercher des événements des messages suivis.</span><span class="sxs-lookup"><span data-stu-id="b388a-103">You can use the **New Query** tab in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to search for tracked message events.</span></span>  <span data-ttu-id="b388a-104">Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez activer le suivi du corps et des propriétés de message.</span><span class="sxs-lookup"><span data-stu-id="b388a-104">From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console you can enable message body and message property tracking.</span></span> <span data-ttu-id="b388a-105">Le volet Résultats de la requête indique les informations relatives à l'événement de message, notamment les informations de schéma, le type d'événement, l'ID de l'instance de service et les propriétés promues du message généré.</span><span class="sxs-lookup"><span data-stu-id="b388a-105">In the Query Results pane you can view information about the message event, including schema information, event type, service instance ID, and all the promoted properties for the generated message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b388a-106">Pour afficher le corps du message réel, vous pouvez appeler la **détails du Message** , menu contextuel et passer à l’onglet « Parties de Message », ou enregistrer le message à partir de la liste des résultats afficher en appelant **enregistrer dans le fichier** à partir de la menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="b388a-106">In order to view the actual message body, you can invoke the **Message Details** context menu and go to the “Message Parts” tab, or save the message from the result list view by invoking **Save to File** from the context menu.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b388a-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b388a-107">Prerequisites</span></span>  
 <span data-ttu-id="b388a-108">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Opérateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b388a-108">To perform this procedure, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators group.</span></span>  
  
### <a name="to-search-for-tracked-message-items"></a><span data-ttu-id="b388a-109">Pour rechercher les éléments suivis d'un message</span><span class="sxs-lookup"><span data-stu-id="b388a-109">To search for tracked message items</span></span>  
  
1.  <span data-ttu-id="b388a-110">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b388a-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2.  <span data-ttu-id="b388a-111">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, puis cliquez sur le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b388a-111">In the console tree, expand **BizTalk Server Administration**, and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="b388a-112">Dans le volet détails, cliquez sur le **nouvelle requête** onglet.</span><span class="sxs-lookup"><span data-stu-id="b388a-112">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="b388a-113">Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **événements de Message suivis** dans la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="b388a-113">In the **Query Expression** group, in the **Value** column, select **Tracked Message Events** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="b388a-114">Dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez un ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b388a-114">In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select one or more of the following:</span></span>  
  
    |<span data-ttu-id="b388a-115">Élément</span><span class="sxs-lookup"><span data-stu-id="b388a-115">Item</span></span>|<span data-ttu-id="b388a-116"> Description</span><span class="sxs-lookup"><span data-stu-id="b388a-116">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="b388a-117">**Heure de création**</span><span class="sxs-lookup"><span data-stu-id="b388a-117">**Creation Time**</span></span>|<span data-ttu-id="b388a-118">Heure à laquelle le message a été créé.</span><span class="sxs-lookup"><span data-stu-id="b388a-118">The time the message was created.</span></span>|  
    |<span data-ttu-id="b388a-119">**Type d’événement**</span><span class="sxs-lookup"><span data-stu-id="b388a-119">**Event Type**</span></span>|<span data-ttu-id="b388a-120">Type d'événement faisant l'objet du suivi.</span><span class="sxs-lookup"><span data-stu-id="b388a-120">The type of event being tracked.</span></span>|  
    |<span data-ttu-id="b388a-121">**Correspondances maximales**</span><span class="sxs-lookup"><span data-stu-id="b388a-121">**Maximum Matches**</span></span>|<span data-ttu-id="b388a-122">Nombre de résultats à afficher.</span><span class="sxs-lookup"><span data-stu-id="b388a-122">The number of matches to display.</span></span>|  
    |<span data-ttu-id="b388a-123">**Tiers**</span><span class="sxs-lookup"><span data-stu-id="b388a-123">**Party**</span></span>|<span data-ttu-id="b388a-124">Organisation qui a envoyé le message.</span><span class="sxs-lookup"><span data-stu-id="b388a-124">The organization that sent the message.</span></span>|  
    |<span data-ttu-id="b388a-125">**Port**</span><span class="sxs-lookup"><span data-stu-id="b388a-125">**Port**</span></span>|<span data-ttu-id="b388a-126">Port utilisé pour traiter le message.</span><span class="sxs-lookup"><span data-stu-id="b388a-126">The port used to process the message.</span></span>|  
    |<span data-ttu-id="b388a-127">**Nom du schéma**</span><span class="sxs-lookup"><span data-stu-id="b388a-127">**Schema Name**</span></span>|<span data-ttu-id="b388a-128">Nom du schéma utilisé par le message.</span><span class="sxs-lookup"><span data-stu-id="b388a-128">Name of the schema used by the message.</span></span>|  
    |<span data-ttu-id="b388a-129">**ID d’Instance de service**</span><span class="sxs-lookup"><span data-stu-id="b388a-129">**Service Instance ID**</span></span>|<span data-ttu-id="b388a-130">ID de l'instance de service utilisée pour le message.</span><span class="sxs-lookup"><span data-stu-id="b388a-130">The service instance ID used for the message.</span></span>|  
    |<span data-ttu-id="b388a-131">**URI**</span><span class="sxs-lookup"><span data-stu-id="b388a-131">**URI**</span></span>|<span data-ttu-id="b388a-132">URI utilisé pour le message.</span><span class="sxs-lookup"><span data-stu-id="b388a-132">The URI used for the message.</span></span>|  
    |<span data-ttu-id="b388a-133">**\<Sélectionnez un nom de schéma pour les propriétés suivies\>**</span><span class="sxs-lookup"><span data-stu-id="b388a-133">**\<Select a Schema Name for Tracked Properties\>**</span></span>|<span data-ttu-id="b388a-134">Lorsque vous sélectionnez un schéma, les propriétés promues dans ce schéma peuvent être utilisée dans la requête.</span><span class="sxs-lookup"><span data-stu-id="b388a-134">When you select a schema, any promoted properties in that schema are eligible to be used in the query.</span></span>|  
  
6.  <span data-ttu-id="b388a-135">Terminer la **valeur** colonne en fonction de la sélection que vous avez effectuée dans le **nom de champ** colonne.</span><span class="sxs-lookup"><span data-stu-id="b388a-135">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  
  
7.  <span data-ttu-id="b388a-136">Continuez à ajouter des lignes supplémentaires à la requête comme il convient en effectuant le **nom de champ**, **opérateur**, et **valeurs** colonnes, puis cliquez sur **exécuter Requête**.</span><span class="sxs-lookup"><span data-stu-id="b388a-136">Continue adding additional lines to the query as appropriate by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b388a-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b388a-137">See Also</span></span>  
 [<span data-ttu-id="b388a-138">Utilisation de l’onglet Requête de la console Administration</span><span class="sxs-lookup"><span data-stu-id="b388a-138">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)
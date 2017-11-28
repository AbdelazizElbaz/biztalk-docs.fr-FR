---
title: "Comment configurer l’envoi de l’adaptateur MQSeries et les gestionnaires de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive handlers, MQSeries adapters
- configuring [MQSeries adapters], receive handlers
- MQSeries adapters, send handlers
- MQSeries adapters, receive handlers
- send handlers, MQSeries adapters
- configuring [MQSeries adapters], send handlers
ms.assetid: e1cfc415-50d2-440b-9301-ad69da28ad3e
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9a1e933f62adaf4e17fae5334e65f50610fb6f1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-mqseries-adapter-send-and-receive-handlers"></a><span data-ttu-id="025f6-102">Comment configurer l’adaptateur MQSeries envoyer et recevoir des gestionnaires</span><span class="sxs-lookup"><span data-stu-id="025f6-102">How to Configure MQSeries Adapter Send and Receive Handlers</span></span>
<span data-ttu-id="025f6-103">Vous pouvez configurer des propriétés pour les gestionnaires d'envoi et de réception de l'adaptateur MQSeries par l'intermédiaire de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="025f6-103">You can configure some properties for the send and receive handlers for the MQSeries adapter through the BizTalk Server Administration console.</span></span> <span data-ttu-id="025f6-104">Le processus décrit dans [comment configurer les emplacements de réception de la carte de MQSeries et les Ports d’envoi](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md) établit les valeurs pour la majorité des propriétés du Gestionnaire d’envoi.</span><span class="sxs-lookup"><span data-stu-id="025f6-104">The process described in [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md) establishes the values for the majority of send handler properties.</span></span>  
  
## <a name="to-configure-the-send-and-receive-handlers"></a><span data-ttu-id="025f6-105">Pour configurer les gestionnaires d'envoi et de réception</span><span class="sxs-lookup"><span data-stu-id="025f6-105">To configure the send and receive handlers</span></span>  
 <span data-ttu-id="025f6-106">Suivez ces étapes pour configurer les gestionnaires d'envoi et de réception de l'adaptateur MSQeries :</span><span class="sxs-lookup"><span data-stu-id="025f6-106">Follow these steps to configure send and receive handlers for the MSQeries adapter:</span></span>  
  
1.  <span data-ttu-id="025f6-107">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="025f6-107">Click **Start**, point to **Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="025f6-108">Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, cliquez pour développer **paramètres de plateforme**, puis cliquez sur à Développez **cartes**.</span><span class="sxs-lookup"><span data-stu-id="025f6-108">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, click to expand **Platform Settings**, and then click to expand **Adapters**.</span></span>  
  
3.  <span data-ttu-id="025f6-109">Dans la liste développée des adaptateurs, sélectionnez **MQSeries**.</span><span class="sxs-lookup"><span data-stu-id="025f6-109">In the expanded adapter list, select **MQSeries**.</span></span> <span data-ttu-id="025f6-110">La liste des gestionnaires d'envoi et de réception liés à l'adaptateur MQSeries apparaît dans le volet de droite.</span><span class="sxs-lookup"><span data-stu-id="025f6-110">The list of send and receive handlers that are bound to the MQSeries adapter appear in the right pane.</span></span>  
  
4.  <span data-ttu-id="025f6-111">Dans le volet de droite, double-cliquez sur un gestionnaire d'envoi ou de réception.</span><span class="sxs-lookup"><span data-stu-id="025f6-111">In the right pane, double-click a send or receive handler in the right pane.</span></span>  
  
5.  <span data-ttu-id="025f6-112">Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="025f6-112">In the **Adapter Handler Properties** dialog box, click **Properties**.</span></span>  
  
6.  <span data-ttu-id="025f6-113">Dans le **propriétés du Transport MQSeries** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="025f6-113">In the **MQSeries Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="025f6-114">Utiliser</span><span class="sxs-lookup"><span data-stu-id="025f6-114">Use this</span></span>|<span data-ttu-id="025f6-115">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="025f6-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="025f6-116">**Nombre maximal de Messages dans un lot**</span><span class="sxs-lookup"><span data-stu-id="025f6-116">**Maximum Messages in Batch**</span></span>|<span data-ttu-id="025f6-117">Définissez le nombre maximal de messages dans un lot.</span><span class="sxs-lookup"><span data-stu-id="025f6-117">Set the maximum number of messages in a batch.</span></span> <span data-ttu-id="025f6-118">S’applique uniquement au gestionnaire d’envoi.</span><span class="sxs-lookup"><span data-stu-id="025f6-118">Applies only to the send handler.</span></span>|  
    |<span data-ttu-id="025f6-119">**Server**</span><span class="sxs-lookup"><span data-stu-id="025f6-119">**Server**</span></span>|<span data-ttu-id="025f6-120">Nom de l'ordinateur exécutant MQSeries Server pour Windows.</span><span class="sxs-lookup"><span data-stu-id="025f6-120">The name of the computer that is running MQSeries Server for Windows.</span></span>|  
  
7.  <span data-ttu-id="025f6-121">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="025f6-121">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="025f6-122">Les propriétés Emplacement de réception et Port d'envoi remplacent les valeurs de gestionnaire de réception et de gestionnaire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="025f6-122">The Receive Location and Send Port properties override the Receive Handler and Send Handler values.</span></span> <span data-ttu-id="025f6-123">Si les propriétés Emplacement de réception et Port d'envoi ne comportent aucune valeur, l'adaptateur utilise respectivement les valeurs de gestionnaire de réception et de gestionnaire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="025f6-123">If there is no value for the Receive Location or Send Port properties, the adapter uses the Receive Handler and Send Handler values respectively.</span></span>  
  
8.  <span data-ttu-id="025f6-124">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="025f6-124">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="025f6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="025f6-125">See Also</span></span>  
 <span data-ttu-id="025f6-126">[Comment configurer MQSeries adaptateur emplacements de réception et Ports d’envoi](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md) </span><span class="sxs-lookup"><span data-stu-id="025f6-126">[How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md) </span></span>  
 [<span data-ttu-id="025f6-127">Configuration de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="025f6-127">Configuring the MQSeries Adapter</span></span>](../core/configuring-the-mqseries-adapter.md)
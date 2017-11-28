---
title: "La configuration de réception et emplacements et les Ports d’envoi pour l’Interception WCF BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 501194dc-427a-4910-88c9-19cf47daeaad
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa77f39e8320c0d6598caaf5ea547592078774ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-receive-and-send-locations-and-ports-for-bam-wcf-interception"></a><span data-ttu-id="0192b-102">Configuration des emplacements et ports de réception et d'envoi pour l'interception WCF de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="0192b-102">How to Configure Receive and Send Locations and Ports for BAM WCF Interception</span></span>
<span data-ttu-id="0192b-103">Cette procédure permet de configurer les emplacements de réception et d'envoi dans un scénario de routage basé sur le contenu afin d'illustrer les principaux concepts d'une manière simple.</span><span class="sxs-lookup"><span data-stu-id="0192b-103">In this procedure you configure the receive and send locations in a content-based routing (CBR) scenario in order to demonstrate the key concepts in a straightforward manner.</span></span> <span data-ttu-id="0192b-104">Les concepts présentés dans cette rubrique peuvent être appliqués à une orchestration exposée en tant que service [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0192b-104">The concepts demonstrated here can be applied to an orchestration that is exposed as a [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] service.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0192b-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0192b-105">Prerequisites</span></span>  
 <span data-ttu-id="0192b-106">Cette procédure implique que vous ayez :</span><span class="sxs-lookup"><span data-stu-id="0192b-106">This procedure assumes that you have:</span></span>  
  
-   <span data-ttu-id="0192b-107">Modifié votre fichier machine.config comme dans [comment ajouter le comportement de l’intercepteur BAM au fichier Machine.config](../core/how-to-add-the-bam-interceptor-behavior-to-the-machine-config-file.md).</span><span class="sxs-lookup"><span data-stu-id="0192b-107">Modified your machince.config file as shown in [How to Add the BAM Interceptor Behavior to the Machine.config File](../core/how-to-add-the-bam-interceptor-behavior-to-the-machine-config-file.md).</span></span>  
  
-   <span data-ttu-id="0192b-108">Créé un adaptateur WCF pour BizTalk Server, comme dans [la création d’un adaptateur WCF pour BizTalk Server](../core/how-to-create-a-wcf-adapter-for-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="0192b-108">Created a WCF adapter for BizTalk Server as show in [How to Create a WCF Adapter for BizTalk Server](../core/how-to-create-a-wcf-adapter-for-biztalk-server.md).</span></span>  
  
### <a name="to-configure-the-receive-and-send-locations"></a><span data-ttu-id="0192b-109">Pour configurer les emplacements de réception et d'envoi</span><span class="sxs-lookup"><span data-stu-id="0192b-109">To configure the receive and send locations</span></span>  
  
1.  <span data-ttu-id="0192b-110">Ouvrez la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0192b-110">Open the BizTalk Administration Console.</span></span> <span data-ttu-id="0192b-111">Pour ce faire, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="0192b-111">To do this, click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0192b-112">Développez l'arborescence de la console pour localiser le nœud des emplacements de réception de votre application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0192b-112">Expand the console tree to locate the Receive Locations node for your BizTalk application.</span></span> <span data-ttu-id="0192b-113">Cliquez sur [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], cliquez sur **Applications**, cliquez sur l’application que vous avez sélectionné dans le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] boîte de dialogue Type de Service, puis cliquez sur **emplacements de réception**.</span><span class="sxs-lookup"><span data-stu-id="0192b-113">Click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], click **Applications**, click the application you selected in the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Service Type dialog box, and then click **Receive Locations**.</span></span> <span data-ttu-id="0192b-114">Un nouvel emplacement de réception correspondant à celui que vous avez créé est affiché.</span><span class="sxs-lookup"><span data-stu-id="0192b-114">There will be a new receive location corresponding to the one you created.</span></span> <span data-ttu-id="0192b-115">Son état est Désactivé.</span><span class="sxs-lookup"><span data-stu-id="0192b-115">It will be in disabled status.</span></span>  
  
3.  <span data-ttu-id="0192b-116">Double-cliquez sur l’emplacement de réception pour ouvrir la **propriétés de l’emplacement de réception** boîte de dialogue zone, puis choisissez le type de transport WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="0192b-116">Double-click the receive location to open the **Receive Location Properties** dialog box, and then choose WCF-Custom as the transport type.</span></span>  
  
4.  <span data-ttu-id="0192b-117">Cliquez sur le **configurer** bouton pour ouvrir la **propriétés du Transport WCF-Custom** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="0192b-117">Click the **Configure** button to open the **WCF-Custom Transport Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="0192b-118">Cliquez sur le **liaison** onglet et sélectionnez la liaison que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="0192b-118">Click the **Binding** tab and select the binding you want to use.</span></span>  
  
6.  <span data-ttu-id="0192b-119">Cliquez sur le **comportement** onglet, cliquez sur le **EndpointBehavior** nœud et sélectionnez **Ajout d’une Extension**.</span><span class="sxs-lookup"><span data-stu-id="0192b-119">Click the **Behavior** tab, right-click the **EndpointBehavior** node, and then select **Add Extension**.</span></span>  
  
7.  <span data-ttu-id="0192b-120">Sélectionnez l’extension BAMEndPointExtension (il s’agit de l’extension que vous avez ajouté au fichier machine.config), puis cliquez sur **Ok**.</span><span class="sxs-lookup"><span data-stu-id="0192b-120">Select the BAMEndPointExtension (this is the extension you added to the machine.config file), and then click **Ok**.</span></span>  
  
     <span data-ttu-id="0192b-121">![Écran d’Extension de comportement SELECT](../core/media/fe830d29-504e-465a-9316-b3f0db2dbc24.gif "fe830d29-504e-465a-9316-b3f0db2dbc24")</span><span class="sxs-lookup"><span data-stu-id="0192b-121">![Select Behavior Extension screen](../core/media/fe830d29-504e-465a-9316-b3f0db2dbc24.gif "fe830d29-504e-465a-9316-b3f0db2dbc24")</span></span>  
  
8.  <span data-ttu-id="0192b-122">Sélectionnez l’extension que vous venez de créer, entrez les valeurs suivantes, puis cliquez sur **OK**:</span><span class="sxs-lookup"><span data-stu-id="0192b-122">Select the extension you just created, enter the following values, and then click **OK**:</span></span>  
  
    |<span data-ttu-id="0192b-123">Propriété</span><span class="sxs-lookup"><span data-stu-id="0192b-123">Property</span></span>|<span data-ttu-id="0192b-124">Valeur</span><span class="sxs-lookup"><span data-stu-id="0192b-124">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="0192b-125">PollingIntervalSec</span><span class="sxs-lookup"><span data-stu-id="0192b-125">PollingIntervalSec</span></span>|<span data-ttu-id="0192b-126">10</span><span class="sxs-lookup"><span data-stu-id="0192b-126">10</span></span>|  
    |<span data-ttu-id="0192b-127">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="0192b-127">ConnectionString</span></span>|<span data-ttu-id="0192b-128">ConnectionString : Integrated Security = SSPI ; Persist Security Info = False ; catalogue Initial = BAMPrimaryImport ; Source de données =</span><span class="sxs-lookup"><span data-stu-id="0192b-128">ConnectionString: Integrated Security=SSPI;Persist Security Info=False;Initial Catalog=BAMPrimaryImport;Data Source=</span></span>|  
  
9. <span data-ttu-id="0192b-129">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, sélectionnez **PassThruReceive** à partir de la **pipeline de réception** liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0192b-129">In the **Receive Location Properties** dialog box, select **PassThruReceive** from the **Receive pipeline** drop-down list, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="0192b-130">Activez l'emplacement de réception et actualisez la console Administration.</span><span class="sxs-lookup"><span data-stu-id="0192b-130">Enable the receive location and refresh the Administration console.</span></span> <span data-ttu-id="0192b-131">L'état Démarré indique que l'installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="0192b-131">A started status indicates that the setup is successful.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0192b-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0192b-132">See Also</span></span>  
 [<span data-ttu-id="0192b-133">Configuration de l’adaptateur WCF pour intercepter les données BAM</span><span class="sxs-lookup"><span data-stu-id="0192b-133">Configuring the WCF Adapter to Intercept BAM Data</span></span>](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)
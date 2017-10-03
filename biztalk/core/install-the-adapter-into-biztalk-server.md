---
title: "Installer l’adaptateur dans BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1164468d-75a9-4116-87a6-6055948c198b
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1bc585e0574610a867d3f890ce456930bc936dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-the-adapter-into-biztalk-server"></a><span data-ttu-id="cf8f4-102">Installation de l'adaptateur dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cf8f4-102">Install the Adapter into BizTalk Server</span></span>
<span data-ttu-id="cf8f4-103">Une fois les entrées [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adéquates écrites dans le registre, l'adaptateur doit être ajouté à la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-103">After the proper [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] entries have been written to the registry the adapter must be added to the BizTalk Management database.</span></span> <span data-ttu-id="cf8f4-104">Une fois l'adaptateur ajouté à cette base de données, il est activement configuré et peut traiter des messages.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-104">After the adapter is added to this database it is an actively configured adapter and can process messages when it is properly configured.</span></span> <span data-ttu-id="cf8f4-105">Installez l'adaptateur dans la base de données à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf8f4-105">You install the adapter into the database by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="cf8f4-106">Avant d'installer l'adaptateur dans la base de données, redémarrez l'instance de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-106">After installing the adapter in the database, restart the host instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf8f4-107">Pour être visible et être ajouté à la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], l'adaptateur doit être correctement inscrit dans le Registre HKLM et doit implémenter les interfaces d'adaptateur adéquates.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-107">To be visible for addition in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, an adapter must be properly registered in the HKLM registry and must implement the necessary adapter interfaces.</span></span>  
  
### <a name="to-install-the-static-sample-adapter"></a><span data-ttu-id="cf8f4-108">Pour installer l'exemple d'adaptateur statique</span><span class="sxs-lookup"><span data-stu-id="cf8f4-108">To install the static sample adapter</span></span>  
  
1.  <span data-ttu-id="cf8f4-109">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-109">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="cf8f4-110">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, double-cliquez sur le **groupe BizTalk** nœud.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-110">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, double-click the  **BizTalk Group** node.</span></span>  
  
3.  <span data-ttu-id="cf8f4-111">Développez **paramètres de plateforme** et sélectionnez **cartes**.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-111">Expand **Platform Settings** and select **Adapters**.</span></span>  
  
4.  <span data-ttu-id="cf8f4-112">Avec le bouton droit **cartes**, cliquez sur **nouveau**, puis cliquez sur **carte**.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-112">Right-click **Adapters**, click **New**, and then click **Adapter**.</span></span>  
  
5.  <span data-ttu-id="cf8f4-113">Dans le **propriétés de l’adaptateur** boîte de dialogue zone, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-113">In the **Adapter Properties** dialog box, do the following.</span></span>  
  
    |<span data-ttu-id="cf8f4-114">Utiliser</span><span class="sxs-lookup"><span data-stu-id="cf8f4-114">Use this</span></span>|<span data-ttu-id="cf8f4-115">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="cf8f4-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="cf8f4-116">Nom</span><span class="sxs-lookup"><span data-stu-id="cf8f4-116">Name</span></span>|<span data-ttu-id="cf8f4-117">Type **statique**.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-117">Type **Static**.</span></span>|  
    |<span data-ttu-id="cf8f4-118">Adaptateur</span><span class="sxs-lookup"><span data-stu-id="cf8f4-118">Adapter</span></span>|<span data-ttu-id="cf8f4-119">Sélectionnez **Static DotNetFile** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-119">Select **Static DotNetFile** from the drop-down list.</span></span>|  
    |<span data-ttu-id="cf8f4-120"> Description</span><span class="sxs-lookup"><span data-stu-id="cf8f4-120">Description</span></span>|<span data-ttu-id="cf8f4-121">Type **exemple d’adaptateur statique**.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-121">Type **Sample Static Adapter**.</span></span>|  
  
6.  <span data-ttu-id="cf8f4-122">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-122">Click **OK**.</span></span>  
  
     <span data-ttu-id="cf8f4-123">L'adaptateur statique apparaît dans la liste des adaptateurs, dans la fenêtre de droite de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf8f4-123">The static adapter now appears in the list of adapters in the right window of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
### <a name="to-stop-and-restart-the-host-instance"></a><span data-ttu-id="cf8f4-124">Pour arrêter et redémarrer l'instance de l'hôte</span><span class="sxs-lookup"><span data-stu-id="cf8f4-124">To stop and restart the host instance</span></span>  
  
1.  <span data-ttu-id="cf8f4-125">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-125">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**.</span></span>  
  
2.  <span data-ttu-id="cf8f4-126">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, double-cliquez sur le **groupe BizTalk** nœud.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-126">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, double-click the  **BizTalk Group** node.</span></span>  
  
3.  <span data-ttu-id="cf8f4-127">Développez **paramètres de plateforme**, sélectionnez **hôtes**, puis sélectionnez **BizTalkServerApplication** dans le volet de résultats.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-127">Expand **Platform Settings**, select **Hosts**, and then select **BizTalkServerApplication** in the results pane.</span></span>  
  
4.  <span data-ttu-id="cf8f4-128">Cliquez sur l’instance d’hôte (en règle générale, le nom d’ordinateur), puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-128">Right-click the host instance (typically, the computer name), and then click **Stop**.</span></span>  
  
     <span data-ttu-id="cf8f4-129">L’état de l’instance d’hôte devient **arrêté**.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-129">The status of the host instance changes to **Stopped**.</span></span>  
  
5.  <span data-ttu-id="cf8f4-130">Dans le volet de résultats, cliquez sur l’instance d’hôte, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-130">In the results pane, right-click the host instance, and then click **Start**.</span></span>  
  
     <span data-ttu-id="cf8f4-131">L’état de l’instance d’hôte devient **attente de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-131">The status of the host instance changes to **Start pending**.</span></span> <span data-ttu-id="cf8f4-132">Vous devez cliquer sur **Actualiser**, ou cliquez sur l’instance d’hôte, puis cliquez **Actualiser**, pour modifier l’état à **en cours d’exécution**.</span><span class="sxs-lookup"><span data-stu-id="cf8f4-132">You must click **Refresh**, or right-click the host instance and then click **Refresh**, to change the status to **Running**.</span></span>
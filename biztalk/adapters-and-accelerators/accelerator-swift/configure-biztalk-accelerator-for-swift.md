---
title: Configurer BizTalk Accelerator pour SWIFT | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e34b0b2d-f563-468b-b6b9-536f0df96f52
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eaa9812243ef7d5ff4bb8b902ac7aee48e54ab99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-biztalk-accelerator-for-swift"></a><span data-ttu-id="a7a85-102">Configurer BizTalk Accelerator pour SWIFT</span><span class="sxs-lookup"><span data-stu-id="a7a85-102">Configure BizTalk Accelerator for SWIFT</span></span>

<span data-ttu-id="a7a85-103">Configurer le [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a7a85-103">Configure the [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)].</span></span> 

<span data-ttu-id="a7a85-104">Lorsque vous installez [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)], il existe une case à cocher qui vous permet d’exécuter la configuration automatiquement.</span><span class="sxs-lookup"><span data-stu-id="a7a85-104">When you install [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)], there is a checkbox that lets you run the configuration automatically.</span></span> <span data-ttu-id="a7a85-105">Ou bien, vous pouvez ouvrir la Configuration BizTalk Accelerator pour SWIFT (A4SWIFT) répertoriée dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="a7a85-105">Or, you can open the BizTalk Accelerator for SWIFT (A4SWIFT) Configuration listed in your apps.</span></span>

<span data-ttu-id="a7a85-106">Cette rubrique vous montre comment configurer le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] accelerator, comment exporter ou importer une configuration et liste également les étapes à la configuration.</span><span class="sxs-lookup"><span data-stu-id="a7a85-106">This topic shows you how to configure the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] accelerator, how to export or import a configuration, and also lists the post-configuration steps.</span></span>

## <a name="configure-a4swift"></a><span data-ttu-id="a7a85-107">Configurer A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="a7a85-107">Configure A4SWIFT</span></span>

1. <span data-ttu-id="a7a85-108">Ouvrez BizTalk Accelerator pour SWIFT (A4SWIFT) Configuration.</span><span class="sxs-lookup"><span data-stu-id="a7a85-108">Open the BizTalk Accelerator for SWIFT (A4SWIFT) Configuration.</span></span>
2. <span data-ttu-id="a7a85-109">Sélectionnez **MCRR**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-109">Select **MCRR**.</span></span> <span data-ttu-id="a7a85-110">MCRR est disponible uniquement si vous avez installé le **Message Repair et New Submission** composants.</span><span class="sxs-lookup"><span data-stu-id="a7a85-110">MCRR is available only if you installed the **Message Repair and New Submission** components.</span></span>
3. <span data-ttu-id="a7a85-111">Lorsque vous êtes invité **vous souhaitez créer un nouveau groupe de base de données**:</span><span class="sxs-lookup"><span data-stu-id="a7a85-111">When asked **Do you want to create a new database group**:</span></span>

  * <span data-ttu-id="a7a85-112">Sélectionnez cette option pour créer de nouveaux groupes indiqués dans le **groupe** volet.</span><span class="sxs-lookup"><span data-stu-id="a7a85-112">Select this option to create the new groups shown in the **Group** pane.</span></span> 
  * <span data-ttu-id="a7a85-113">Pour joindre un groupe existant de la base de données, désactivez cette option.</span><span class="sxs-lookup"><span data-stu-id="a7a85-113">To join an existing database group, uncheck this option.</span></span>

3. <span data-ttu-id="a7a85-114">Si vous avez installé **les composants Web pour Message Repair et New Submission**, puis sélectionnez **WebService**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-114">If you installed **Web Components for Message Repair and New Submission**, then select **WebService**.</span></span>
4. <span data-ttu-id="a7a85-115">Sélectionnez le site web pour héberger le service Web d’A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="a7a85-115">Select the web site to host the A4SWIFT Web service.</span></span> <span data-ttu-id="a7a85-116">Par défaut, le Site Web par défaut est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="a7a85-116">By default, the Default Web Site is selected.</span></span>
5. <span data-ttu-id="a7a85-117">Sélectionnez **appliquer la Configuration**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-117">Select **Apply Configuration**.</span></span>
6. <span data-ttu-id="a7a85-118">Dans **Résumé**, vérifiez les paramètres de configuration, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-118">In **Summary**, verify the configuration settings, and then click **Configure**.</span></span> 

    > [!TIP] 
    > <span data-ttu-id="a7a85-119">Vous pouvez enregistrer les paramètres de configuration dans un fichier XML si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="a7a85-119">You can save the configuration settings as an XML file, if desired.</span></span>

7. <span data-ttu-id="a7a85-120">Sélectionnez **Terminer** lorsque la configuration est terminée.</span><span class="sxs-lookup"><span data-stu-id="a7a85-120">Select **Finish** when the configuration completes.</span></span>

## <a name="export-or-import-a-configuration"></a><span data-ttu-id="a7a85-121">Exporter ou importer une configuration</span><span class="sxs-lookup"><span data-stu-id="a7a85-121">Export or import a configuration</span></span>
<span data-ttu-id="a7a85-122">Vous pouvez exporter les paramètres de configuration d’A4SWIFT dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="a7a85-122">You can export the configuration settings of A4SWIFT to an XML file.</span></span> <span data-ttu-id="a7a85-123">Ces paramètres peuvent ensuite être importés pour configurer une autre installation d’A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="a7a85-123">These settings can then be imported to configure another A4SWIFT installation.</span></span> 

### <a name="export-the-configuration"></a><span data-ttu-id="a7a85-124">Exporter la configuration</span><span class="sxs-lookup"><span data-stu-id="a7a85-124">Export the configuration</span></span>

1. <span data-ttu-id="a7a85-125">Ouvrez Microsoft BizTalk Accelerator pour SWIFT Configuration, puis sélectionnez **exporter la Configuration**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-125">Open the Microsoft BizTalk Accelerator for SWIFT Configuration, and select **Export Configuration**.</span></span>
2. <span data-ttu-id="a7a85-126">Dans **enregistrer en tant que**, accédez au dossier où vous souhaitez enregistrer le fichier de configuration, entrez un nom pour le fichier de configuration, puis **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-126">In **Save As**, browse to the folder where you want to save the configuration file, enter a name for the configuration file, and then **Save**.</span></span>
3. <span data-ttu-id="a7a85-127">Lorsque vous exportées avec succès, sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-127">When exported successfully, select **OK**.</span></span>

### <a name="import-a-configuration"></a><span data-ttu-id="a7a85-128">Importer une configuration</span><span class="sxs-lookup"><span data-stu-id="a7a85-128">Import a configuration</span></span>
1. <span data-ttu-id="a7a85-129">Ouvrez Microsoft BizTalk Accelerator pour SWIFT Configuration, puis sélectionnez **importer la Configuration**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-129">Open the Microsoft BizTalk Accelerator for SWIFT Configuration, and select **Import Configuration**.</span></span>
2. <span data-ttu-id="a7a85-130">Accédez au dossier qui contient le fichier de configuration, sélectionnez le fichier, puis **importation**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-130">Browse to the folder that contains the configuration file, select the file, and then select **Import**.</span></span>

## <a name="post-configuration-steps"></a><span data-ttu-id="a7a85-131">Étapes à la configuration</span><span class="sxs-lookup"><span data-stu-id="a7a85-131">Post-configuration steps</span></span>

### <a name="add-users-to-the-a4swift-users-group"></a><span data-ttu-id="a7a85-132">Ajouter des utilisateurs au groupe utilisateurs d’A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="a7a85-132">Add users to the A4SWIFT Users group</span></span>

<span data-ttu-id="a7a85-133">Après avoir configuré le [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)], ajoutez le compte qui exécute l’instance de l’hôte BizTalkServerApplication pour le **A4SWIFT utilisateurs** groupe (*pas* le **A4SWIFT administrateurs** groupe).</span><span class="sxs-lookup"><span data-stu-id="a7a85-133">After you configure the [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)], add the account that runs the BizTalkServerApplication host instance to the **A4SWIFT Users** group (*not* the **A4SWIFT Administrators** group).</span></span> 

<span data-ttu-id="a7a85-134">**Étapes**:</span><span class="sxs-lookup"><span data-stu-id="a7a85-134">**Steps**:</span></span>

1. <span data-ttu-id="a7a85-135">Ouvrez **Services**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-135">Open **Services**.</span></span> <span data-ttu-id="a7a85-136">Services est également disponible dans **le Gestionnaire de serveur**, puis **outils**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-136">Services is also available in **Server Manager**, and then **Tools**.</span></span> 
2. <span data-ttu-id="a7a85-137">Dans la liste, recherchez **groupe BizTalk des services BizTalk : BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-137">In the list, find **BizTalk Service BizTalk Group: BizTalkServerApplication**.</span></span> 
3. <span data-ttu-id="a7a85-138">Sélectionnez en double pour ouvrir ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="a7a85-138">Double-select to open its properties.</span></span>
4. <span data-ttu-id="a7a85-139">Dans le **session** onglet, notez que le compte d’utilisateur est répertorié comme **ce compte**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-139">In the **Log On** tab, note the user account listed as **This account**.</span></span>
5. <span data-ttu-id="a7a85-140">Ouvrez **utilisateurs et groupes locaux** (gestion de l’ordinateur), puis recherchez le **A4SWIFT utilisateurs** groupe.</span><span class="sxs-lookup"><span data-stu-id="a7a85-140">Open **Local Users and Groups** (in Computer Management), and then find the **A4SWIFT Users** group.</span></span> <span data-ttu-id="a7a85-141">Ajoutez le compte d’utilisateur à ce groupe.</span><span class="sxs-lookup"><span data-stu-id="a7a85-141">Add the user account to this group.</span></span>

> [!TIP] 
> <span data-ttu-id="a7a85-142">Le compte de l’instance doit cette appartenance de groupe pour le composant d’exécution hôte Message Repair pour accéder à la base de données BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a7a85-142">The host instance account needs this group membership for the host Message Repair runtime component to access the BizTalk Server database.</span></span>

### <a name="check-the-identity-of-the-application-pool"></a><span data-ttu-id="a7a85-143">Vérifier l’identité du pool d’applications</span><span class="sxs-lookup"><span data-stu-id="a7a85-143">Check the identity of the application pool</span></span>
<span data-ttu-id="a7a85-144">Le service web A4SWIFT_MRSR est hébergé dans une application dans IIS.</span><span class="sxs-lookup"><span data-stu-id="a7a85-144">The A4SWIFT_MRSR web service is hosted in an application in IIS.</span></span> <span data-ttu-id="a7a85-145">L’identité du pool d’applications *ne peut pas* agisse Service réseau.</span><span class="sxs-lookup"><span data-stu-id="a7a85-145">The application pool identity *cannot* be Network Service.</span></span> <span data-ttu-id="a7a85-146">Modifier l’identité du pool d’applications à un compte local ou de domaine qui est membre de la **A4SWIFT utilisateurs** groupe.</span><span class="sxs-lookup"><span data-stu-id="a7a85-146">Change the identity of the application pool to a local or domain account that is a member of the **A4SWIFT Users** group.</span></span>

<span data-ttu-id="a7a85-147">**Étapes**:</span><span class="sxs-lookup"><span data-stu-id="a7a85-147">**Steps**:</span></span>

1. <span data-ttu-id="a7a85-148">Ouvrez **le Gestionnaire des Services Internet**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-148">Open **Internet Information Services Manager**.</span></span> <span data-ttu-id="a7a85-149">Le Gestionnaire des services Internet est également disponible dans **le Gestionnaire de serveur**, puis **outils**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-149">The IIS Manager is also available in **Server Manager**, and then **Tools**.</span></span> 
2. <span data-ttu-id="a7a85-150">Développez le **Site Web par défaut**, puis sélectionnez le service web A4SWIFT_MRSR.</span><span class="sxs-lookup"><span data-stu-id="a7a85-150">Expand the **Default Web Site**, and select the A4SWIFT_MRSR web service.</span></span> 
3. <span data-ttu-id="a7a85-151">Sélectionnez **les paramètres de base**.</span><span class="sxs-lookup"><span data-stu-id="a7a85-151">Select **Basic Settings**.</span></span> <span data-ttu-id="a7a85-152">Le nom du pool d’applications est répertorié.</span><span class="sxs-lookup"><span data-stu-id="a7a85-152">The name of the application pool is listed.</span></span>
4. <span data-ttu-id="a7a85-153">Dans le volet gauche, sélectionnez **Pools d’applications**, puis sélectionnez votre pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="a7a85-153">In the left pane, select **Application Pools**, and then select your application pool.</span></span>
5. <span data-ttu-id="a7a85-154">Sélectionnez **paramètres avancés**et modifier le **identité** si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a7a85-154">Select **Advanced Settings**, and change the **Identity** if needed.</span></span>
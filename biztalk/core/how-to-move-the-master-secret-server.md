---
title: "Comment déplacer le serveur de secret principal | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [Master Secret server], migrating
- migrating, Master Secret server
- Master Secret server, migrating
ms.assetid: 2bc5137e-f81d-486d-bb91-7c5981896f79
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b35fae6551a95c1c2009ac9786aa791d189f338
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-master-secret-server"></a><span data-ttu-id="167d0-102">Déplacement du serveur de secret principal</span><span class="sxs-lookup"><span data-stu-id="167d0-102">How to Move the Master Secret Server</span></span>
<span data-ttu-id="167d0-103">La présente rubrique décrit les procédures que vous pouvez suivre pour déplacer le secret principal d'un serveur vers un autre et pour déplacer le secret principal d'un serveur vers un cluster Windows Server.</span><span class="sxs-lookup"><span data-stu-id="167d0-103">This topic documents the steps you can follow to move the master secret from one server to another and the steps you can follow to move the master secret from one server to a Windows Server Cluster.</span></span>  
  
### <a name="to-move-the-master-secret-from-one-server-to-another-server"></a><span data-ttu-id="167d0-104">Pour déplacer le secret principal d'un serveur vers un autre</span><span class="sxs-lookup"><span data-stu-id="167d0-104">To move the master secret from one server to another server</span></span>  
  
1.  <span data-ttu-id="167d0-105">Installez le Serveur d'authentification unique de l'entreprise Microsoft sur le nouveau serveur de secret principal s'il n'est pas encore installé.</span><span class="sxs-lookup"><span data-stu-id="167d0-105">Install Microsoft Enterprise Single Sign-On (SSO) Server on the new master secret server if it is not already installed.</span></span> <span data-ttu-id="167d0-106">Exécutez le programme d'installation du Serveur d'authentification unique de l'entreprise Microsoft à partir du dossier \Platform\SSO\setup.exe du CD [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="167d0-106">Launch Microsoft Enterprise Single Sign-On Server setup from \Platform\SSO\setup.exe on the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] CD.</span></span>  
  
2.  <span data-ttu-id="167d0-107">Configurez l'authentification unique de l'entreprise sur le nouveau serveur de secret principal si ce n'est déjà fait.</span><span class="sxs-lookup"><span data-stu-id="167d0-107">Configure Enterprise SSO on the new master secret server if it is not already configured.</span></span> <span data-ttu-id="167d0-108">Pour configurer l'authentification unique de l'entreprise, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="167d0-108">Follow these steps to configure Enterprise SSO:</span></span>  
  
    1.  <span data-ttu-id="167d0-109">Ouvrez l'outil de configuration.</span><span class="sxs-lookup"><span data-stu-id="167d0-109">Open the Configuration tool.</span></span> <span data-ttu-id="167d0-110">Par défaut, l’outil de configuration se trouve dans \<lecteur > : \Program Files\Enterprise unique signe-On\Configuration.exe.</span><span class="sxs-lookup"><span data-stu-id="167d0-110">By default, the configuration tool is located at \<drive>:\Program Files\Common Files\Enterprise Single Sign-On\Configuration.exe.</span></span>  
  
    2.  <span data-ttu-id="167d0-111">Cliquez pour sélectionner **Enterprise SSO** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="167d0-111">Click to select **Enterprise SSO** in the left pane.</span></span>  
  
    3.  <span data-ttu-id="167d0-112">Activez la case à cocher **activer Enterprise Single Sign-On sur cet ordinateur** dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="167d0-112">Select the check box next to **Enable Enterprise Single Sign-On on this computer** in the right pane.</span></span>  
  
    4.  <span data-ttu-id="167d0-113">Cliquez sur l’option à **joindre un système SSO existant**.</span><span class="sxs-lookup"><span data-stu-id="167d0-113">Click the option to **Join an existing SSO System**.</span></span>  
  
    5.  <span data-ttu-id="167d0-114">Spécifiez les **nom du serveur** et **nom de la base de données** pour l’authentification unique les options de base de données.</span><span class="sxs-lookup"><span data-stu-id="167d0-114">Specify the existing **Server Name** and **Database Name** for the SSO database options.</span></span>  
  
    6.  <span data-ttu-id="167d0-115">Spécifier le compte de service de l’authentification unique de l’entreprise existant pour le **entreprise unique serveur d’authentification pour le Service Windows** option.</span><span class="sxs-lookup"><span data-stu-id="167d0-115">Specify the existing Enterprise SSO service account for the **Enterprise Single Sign-On Server for the Windows Service** option.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="167d0-116">Il doit s'agir d'un compte de domaine.</span><span class="sxs-lookup"><span data-stu-id="167d0-116">This must be a domain account.</span></span>  
  
    7.  <span data-ttu-id="167d0-117">Cliquez sur l’option à **appliquer la Configuration** et cliquez sur **configurer** dans la boîte de dialogue Assistant de Configuration pour terminer la configuration.</span><span class="sxs-lookup"><span data-stu-id="167d0-117">Click the option to **Apply Configuration** and click **Configure** in the Configuration Wizard dialog box to complete the configuration.</span></span>  
  
    8.  <span data-ttu-id="167d0-118">Cliquez sur **Terminer** et fermer l’outil de Configuration.</span><span class="sxs-lookup"><span data-stu-id="167d0-118">Click **Finish** and close the Configuration tool.</span></span>  
  
3.  <span data-ttu-id="167d0-119">Sauvegardez le secret principal existant en suivant les étapes de [comment revenir Up the Master Secret](../core/how-to-back-up-the-master-secret.md).</span><span class="sxs-lookup"><span data-stu-id="167d0-119">Back up the existing master secret following the steps in [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md).</span></span>  
  
4.  <span data-ttu-id="167d0-120">Modifiez le nom du serveur de secret principal dans la base de données d'authentification unique afin de référencer le nouveau serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="167d0-120">Change the master secret server name in the SSO database to reference the new master secret server.</span></span> <span data-ttu-id="167d0-121">Par exemple, le nom du nouveau serveur de secret principal peut être **NewMSSServer**.</span><span class="sxs-lookup"><span data-stu-id="167d0-121">For example, the name of the new master secret server may be **NewMSSServer**.</span></span> <span data-ttu-id="167d0-122">Pour ce faire, procédez comme suit sur le serveur de secret principal original :</span><span class="sxs-lookup"><span data-stu-id="167d0-122">To do this, follow these steps on the original master secret server:</span></span>  
  
    1.  <span data-ttu-id="167d0-123">Collez le code suivant dans un éditeur de texte tel que notepad.exe :</span><span class="sxs-lookup"><span data-stu-id="167d0-123">Paste the following code in a text editor such as notepad.exe:</span></span>  
  
        ```  
        <sso>  
        <globalInfo>  
        <secretServer>NewMSSServer</secretServer>  
        </globalInfo>  
        </sso>  
        ```  
  
    2.  <span data-ttu-id="167d0-124">Enregistrez le fichier en tant que fichier .xml.</span><span class="sxs-lookup"><span data-stu-id="167d0-124">Save the file as .xml file.</span></span> <span data-ttu-id="167d0-125">Par exemple, enregistrez le fichier sous **NewMSSServer.xml**.</span><span class="sxs-lookup"><span data-stu-id="167d0-125">For example, save the file as **NewMSSServer.xml**.</span></span>  
  
    3.  <span data-ttu-id="167d0-126">À l'invite de commandes, accédez au dossier d'installation des services d'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="167d0-126">At a command prompt, change to the Enterprise SSO installation folder.</span></span> <span data-ttu-id="167d0-127">Par défaut, le dossier d’installation est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="167d0-127">By default, the installation folder is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
    4.  <span data-ttu-id="167d0-128">Type **ssomanage - updatedb** *XMLFile* pour mettre à jour le nom du serveur de secret principal dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="167d0-128">Type **ssomanage -updatedb** *XMLFile* to update the master secret server name in the database.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="167d0-129">Remplacez *XMLFile* avec le nom du fichier .xml que vous avez enregistré.</span><span class="sxs-lookup"><span data-stu-id="167d0-129">Replace *XMLFile* with the name of the .xml file that you saved.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="167d0-130">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="167d0-130">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5.  <span data-ttu-id="167d0-131">Redémarrez le service d'authentification unique de l'entreprise sur le nouveau serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="167d0-131">Restart the Enterprise Single Sign-On service on the new master secret server.</span></span>  
  
6.  <span data-ttu-id="167d0-132">Restaurer le secret principal sauvegardé sur le nouveau serveur de secret principal en suivant les étapes dans [comment restaurer le Secret principal](../core/how-to-restore-the-master-secret.md) sur le nouveau serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="167d0-132">Restore the backed-up master secret onto the new master secret server by following the steps in [How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md) on the new master secret server.</span></span>  
  
### <a name="to-move-the-master-secret-from-one-server-to-a-windows-server-cluster"></a><span data-ttu-id="167d0-133">Pour déplacer le secret principal à partir d'un serveur vers un cluster Windows Server</span><span class="sxs-lookup"><span data-stu-id="167d0-133">To move the master secret from one server to a Windows Server Cluster</span></span>  
  
1.  <span data-ttu-id="167d0-134">Installer et configurer le service SSO sur un cluster Windows Server en suivant les étapes dans [mise en Cluster du serveur de secret principal](../core/how-to-cluster-the-master-secret-server1.md).</span><span class="sxs-lookup"><span data-stu-id="167d0-134">Install and configure the Enterprise SSO service on a Windows Server cluster by following the steps in [How to Cluster the Master Secret Server](../core/how-to-cluster-the-master-secret-server1.md).</span></span> <span data-ttu-id="167d0-135">Effectuer toutes les étapes décrites dans cette rubrique, à l’exception de la procédure décrite dans la **restaurer le secret principal sur le deuxième nœud du cluster** section.</span><span class="sxs-lookup"><span data-stu-id="167d0-135">Complete all of the steps in this topic except for the steps described in the **Restore the master secret on the second cluster node** section.</span></span> <span data-ttu-id="167d0-136">Étant donné que vous allez déplacer le serveur de secret principal existant vers le cluster ne choisissez pas l’option à **créer un nouveau système SSO** lors de la configuration de l’authentification unique de l’entreprise sur les nœuds de cluster.</span><span class="sxs-lookup"><span data-stu-id="167d0-136">Since you will be moving the existing master secret server to the cluster do not choose the option to **Create a new SSO system** when configuring Enterprise SSO on the cluster nodes.</span></span> <span data-ttu-id="167d0-137">Lors de la configuration de chaque nœud de cluster, dans le programme Configuration de BizTalk Server, définissez les options suivantes pour la fonctionnalité d'authentification unique de l'entreprise :</span><span class="sxs-lookup"><span data-stu-id="167d0-137">When configuring each cluster node, set the following options for the Enterprise SSO feature in the BizTalk Server Configuration program:</span></span>  
  
    1.  <span data-ttu-id="167d0-138">Cochez la case à côté **activer Enterprise Single Sign-On sur cet ordinateur**.</span><span class="sxs-lookup"><span data-stu-id="167d0-138">Check the box next to **Enable Enterprise Single Sign-On on this computer**.</span></span>  
  
    2.  <span data-ttu-id="167d0-139">Cliquez sur l’option à **joindre un système SSO existant**.</span><span class="sxs-lookup"><span data-stu-id="167d0-139">Click the option to **Join an existing SSO system**.</span></span>  
  
    3.  <span data-ttu-id="167d0-140">Entrez des valeurs pour le nom du serveur de base de données SSO et le nom de base de données existants.</span><span class="sxs-lookup"><span data-stu-id="167d0-140">Enter values for the existing SSO Database Server Name and Database Name.</span></span>  
  
    4.  <span data-ttu-id="167d0-141">Lorsque vous spécifiez le compte à utiliser pour le service d'authentification unique de l'entreprise, entrez le compte de service SSO existant.</span><span class="sxs-lookup"><span data-stu-id="167d0-141">Enter the existing SSO Service account when specifying the account to use for the Enterprise Single Sign-On Service.</span></span>  
  
2.  <span data-ttu-id="167d0-142">Copiez le fichier de sauvegarde du secret principal existant dans le dossier \Enterprise Single Sign-On sur chaque nœud de cluster.</span><span class="sxs-lookup"><span data-stu-id="167d0-142">Copy the existing master secret backup file to the \Enterprise Single Sign-On folder on each cluster node.</span></span>  
  
3.  <span data-ttu-id="167d0-143">Si ce cluster Windows Server doit héberger un ou plusieurs hôtes BizTalk en cluster, à l'aide de l'utilitaire de ligne de commande ssomanage, définissez comme nom du serveur d'authentification unique pour tous les utilisateurs le nom du serveur de secret principal en cluster.</span><span class="sxs-lookup"><span data-stu-id="167d0-143">If this Windows Server Cluster will host one or more clustered BizTalk hosts, set the SSO Server name for all users to the clustered master secret server with the ssomanage command line utility.</span></span> <span data-ttu-id="167d0-144">Cette commande doit être exécutée à partir du dossier d’installation de l’authentification unique de l’entreprise sur chaque serveur BizTalk Server dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="167d0-144">This command should be run from the Enterprise SSO installation folder on each BizTalk Server in the group.</span></span> <span data-ttu-id="167d0-145">Par exemple, la ligne de commande suivante définit le nom du serveur d'authentification unique pour tous les utilisateurs sur le nom du serveur de secret principal en cluster :</span><span class="sxs-lookup"><span data-stu-id="167d0-145">For example, the following command line will set the SSO Server name for all users to the clustered master secret server:</span></span>  
  
    ```  
    ssomanage -serverall SSOCLUSTER  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="167d0-146">*SSOCLUSTER* est un espace réservé pour le réseau réel nom de ressource qui est créé dans le groupe de clusters qui contient la ressource de serveur de secret principal en cluster ce scénario, tous les hôtes BizTalk doivent être créés en tant que ressources de cluster dans le même groupe de clusters que la ressource de service de l’authentification unique de l’entreprise en cluster.</span><span class="sxs-lookup"><span data-stu-id="167d0-146">*SSOCLUSTER* is a placeholder for the actual network name resource that is created in the cluster group that contains the clustered master secret server resourceIn this scenario, all BizTalk hosts must be created as cluster resources in the same cluster group as the clustered Enterprise SSO service resource.</span></span> <span data-ttu-id="167d0-147">L'exécution d'une instance de l'hôte BizTalk sans cluster sur un nœud de cluster Windows Server où le service d'authentification unique de l'entreprise est en cluster n'est pas une configuration prise en charge.</span><span class="sxs-lookup"><span data-stu-id="167d0-147">Running a non-clustered BizTalk host instance on a Windows Server Cluster node where the Enterprise SSO service is clustered is not a supported configuration.</span></span> <span data-ttu-id="167d0-148">Cela est dû au fait que l'exécution de l'instance de l'hôte BizTalk sans cluster échouera lors du basculement du service d'authentification unique de l'entreprise en cluster vers un autre nœud, parce qu'une instance de l'hôte BizTalk dépend de ce service.</span><span class="sxs-lookup"><span data-stu-id="167d0-148">This is because the non-clustered BizTalk host instance will fail when the clustered Enterprise SSO service is failed over to another node due to the dependency of a BizTalk host instance on the SSO service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="167d0-149">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="167d0-149">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="167d0-150">Dans l’administrateur de Cluster, cliquez sur le groupe de clusters qui contient la ressource de service de l’authentification unique de l’entreprise en cluster, puis cliquez sur **mettre en ligne** pour démarrer toutes les ressources dans le groupe de clusters.</span><span class="sxs-lookup"><span data-stu-id="167d0-150">In Cluster Administrator, right-click the cluster group that contains the clustered Enterprise SSO service resource, and click **Bring Online** to start all of the resources in the cluster group.</span></span>  
  
5.  <span data-ttu-id="167d0-151">Si ce Cluster Windows Server doit héberger un ou plusieurs hôtes BizTalk en cluster, mettre à jour le nom du serveur SSO accessible dans le **propriétés du groupe BizTalk** pour référencer le serveur de secret principal en cluster.</span><span class="sxs-lookup"><span data-stu-id="167d0-151">If this Windows Server Cluster will host one or more clustered BizTalk hosts, update the SSO Server name accessible in the **BizTalk Group Properties** page to reference the clustered master secret server.</span></span> <span data-ttu-id="167d0-152">Lancez **Administration de BizTalk Server**, cliquez sur le groupe BizTalk, puis sélectionnez le **propriétés** menu article, puis mettez à jour l’entrée de **nom du serveur SSO** sur  **OK**.</span><span class="sxs-lookup"><span data-stu-id="167d0-152">Launch **BizTalk Server Administration**, right-click the BizTalk Group and select the **Properties** menu item, then update the entry for **SSO Server name** and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="167d0-153">Dans ce scénario, tous les hôtes BizTalk doivent être créés comme ressources du cluster dans le même groupe de clusters que la ressource du service d'authentification unique de l'entreprise en cluster.</span><span class="sxs-lookup"><span data-stu-id="167d0-153">In this scenario, all BizTalk hosts must be created as cluster resources in the same cluster group as the clustered Enterprise SSO service resource.</span></span> <span data-ttu-id="167d0-154">L'exécution d'une instance de l'hôte BizTalk sans cluster sur un nœud de cluster Windows Server où le service d'authentification unique de l'entreprise est en cluster n'est pas une configuration prise en charge.</span><span class="sxs-lookup"><span data-stu-id="167d0-154">Running a non-clustered BizTalk host instance on a Windows Server Cluster node where the Enterprise SSO service is clustered is not a supported configuration.</span></span> <span data-ttu-id="167d0-155">Cela est dû au fait que l'exécution de l'instance de l'hôte BizTalk sans cluster échouera lors du basculement du service d'authentification unique de l'entreprise en cluster vers un autre nœud, parce qu'une instance de l'hôte BizTalk dépend de ce service.</span><span class="sxs-lookup"><span data-stu-id="167d0-155">This is because the non-clustered BizTalk host instance will fail when the clustered Enterprise SSO service is failed over to another node due to the dependency of a BizTalk host instance on the SSO service.</span></span>  
  
6.  <span data-ttu-id="167d0-156">Cliquez sur l’instance en cluster du service SSO de l’entreprise, sur **mettre hors connexion**, puis cliquez sur l’instance en cluster du service SSO de l’entreprise, sur **mettre en ligne**.</span><span class="sxs-lookup"><span data-stu-id="167d0-156">Right-click the clustered instance of the Enterprise SSO service and click **Take Offline**, then right-click the clustered instance of the Enterprise SSO service and click **Bring Online**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="167d0-157">Si cette étape n’est pas terminée, tente de restaurer le secret principal ne peut pas réussir.</span><span class="sxs-lookup"><span data-stu-id="167d0-157">If this step is not completed, attempts to restore the master secret may not succeed.</span></span>  
  
7.  <span data-ttu-id="167d0-158">Restaurez le serveur principal sauvegardé sur chaque nœud du cluster Windows hébergeant le serveur de secret principal en cluster.</span><span class="sxs-lookup"><span data-stu-id="167d0-158">Restore the backed-up master secret on each node of the Windows cluster that houses the clustered master secret server.</span></span> <span data-ttu-id="167d0-159">Suivez les étapes de [comment restaurer le Secret principal](../core/how-to-restore-the-master-secret.md) sur chaque nœud du cluster Windows hébergeant le serveur de secret principal en cluster.</span><span class="sxs-lookup"><span data-stu-id="167d0-159">Follow the steps in [How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md) on each node of the Windows cluster that houses the clustered master secret server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="167d0-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="167d0-160">See Also</span></span>  
 [<span data-ttu-id="167d0-161">Gestion du Secret</span><span class="sxs-lookup"><span data-stu-id="167d0-161">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)
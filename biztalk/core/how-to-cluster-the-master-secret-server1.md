---
title: Mise en Cluster le serveur1 Secret principal | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, second node
- Master Secret server, restoring
- clustering, Master Secret server
- Master Secret server, clustering
ms.assetid: ef817fa4-e43d-4e3d-8686-5bd675708001
caps.latest.revision: "47"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c9fc06d9c735a59fe59499bf9ed0ac62aab0408
ms.sourcegitcommit: 5355a25d120d094778fb8f68ea14cab55c68d292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2017
---
# <a name="how-to-cluster-the-master-secret-server"></a><span data-ttu-id="82446-102">Mise en Cluster du serveur de secret principal</span><span class="sxs-lookup"><span data-stu-id="82446-102">How to Cluster the Master Secret Server</span></span>
<span data-ttu-id="82446-103">Il est recommandé de suivre les instructions dans cette section pour mettre en cluster le service d'authentification unique de l'entreprise sur le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="82446-103">We recommended that you follow the instructions in this section to cluster the Enterprise Single Sign-On (SSO) service on the master secret server successfully.</span></span>  
  
 <span data-ttu-id="82446-104">Lorsque vous mettez en cluster le serveur de secret principal, les serveurs d'authentification unique communiquent avec l'instance en cluster active sur le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="82446-104">When you cluster the master secret server, the Single Sign-On servers communicate with the active clustered instance of the master secret server.</span></span> <span data-ttu-id="82446-105">De même, l'instance en cluster active du serveur de secret principal communique avec la base de données de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="82446-105">Similarly, the active clustered instance of the master secret server communicates with the SSO database.</span></span>  
  
 <span data-ttu-id="82446-106">Seul un administrateur de l'authentification unique peut effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="82446-106">You must be an SSO administrator to perform this procedure.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="82446-107">Vous ne pouvez pas installer le serveur de secret principal sur un cluster d'équilibrage de la charge réseau.</span><span class="sxs-lookup"><span data-stu-id="82446-107">You cannot install the master secret server on a Network Load Balancing (NLB) cluster.</span></span>  
  
### <a name="to-install-and-configure-enterprise-sso-on-the-cluster-nodes"></a><span data-ttu-id="82446-108">Pour installer et configurer l'authentification unique de l'entreprise sur les nœuds de cluster</span><span class="sxs-lookup"><span data-stu-id="82446-108">To install and configure Enterprise SSO on the cluster nodes</span></span>  
  
1.  <span data-ttu-id="82446-109">Installez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur chaque nœud de cluster.</span><span class="sxs-lookup"><span data-stu-id="82446-109">Install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on each cluster node.</span></span> <span data-ttu-id="82446-110">Dans **Installation des composants**, sélectionnez **unique Sign-On Administration entreprise** et **entreprise seule l’authentification serveur de secret principal**.</span><span class="sxs-lookup"><span data-stu-id="82446-110">In **Component Installation**, select **Enterprise Single Sign-On Administration Module** and **Enterprise Single Sign-On Master Secret Server**.</span></span> <span data-ttu-id="82446-111">Une fois l’installation est terminée, procédez comme **pas** exécuter la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration.</span><span class="sxs-lookup"><span data-stu-id="82446-111">After installation has completed successfully, do **not** run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration.</span></span>  
  
2.  <span data-ttu-id="82446-112">Créer **administrateurs SSO** et **administrateurs d’applications associées à authentification unique** groupes de domaine.</span><span class="sxs-lookup"><span data-stu-id="82446-112">Create **SSO Administrators** and **SSO Affiliate Administrators** domain groups.</span></span> <span data-ttu-id="82446-113">Pour créer une instance en cluster du service d'authentification unique de l'entreprise, vous devez créer ces groupes en tant que groupes de domaines.</span><span class="sxs-lookup"><span data-stu-id="82446-113">To create a clustered instance of the Enterprise SSO service, you must create these groups as domain groups.</span></span>  
  
3.  <span data-ttu-id="82446-114">Créez ou désignez un compte de domaine qui est membre de la **administrateurs SSO** groupe de domaine.</span><span class="sxs-lookup"><span data-stu-id="82446-114">Create or designate a domain account that is a member of the **SSO Administrators** domain group.</span></span> <span data-ttu-id="82446-115">Le service d'authentification unique de l'entreprise sur chaque nœud est configuré pour ouvrir une session en tant que ce compte de domaine.</span><span class="sxs-lookup"><span data-stu-id="82446-115">The Enterprise SSO service on each node is configured to log on as this domain account.</span></span> <span data-ttu-id="82446-116">Ce compte doit avoir le **ouvrir une session en tant que service** à droite sur chaque nœud du cluster.</span><span class="sxs-lookup"><span data-stu-id="82446-116">This account must have the **Log on as a service** right on each node in the cluster.</span></span>  
  
4.  <span data-ttu-id="82446-117">Ajoutez le compte que vous utilisez pour vous connecter pendant le processus de configuration pour le domaine **administrateurs SSO** groupe.</span><span class="sxs-lookup"><span data-stu-id="82446-117">Add the account that you are using to log on during the configuration process to the domain **SSO Administrators** group.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="82446-118">La configuration du service d'authentification unique de l'entreprise échoue si les étapes 3 et 4 ne sont pas terminées.</span><span class="sxs-lookup"><span data-stu-id="82446-118">Configuration of the Enterprise SSO service fails if steps 3 and 4 are not completed.</span></span>  
  
5.  <span data-ttu-id="82446-119">Démarrez la Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="82446-119">Start the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration.</span></span>  
  
6.  <span data-ttu-id="82446-120">Sélectionnez **Configuration personnalisée** et entrez le **nom du serveur de base de données**, **nom d’utilisateur**, et **mot de passe** valeurs.</span><span class="sxs-lookup"><span data-stu-id="82446-120">Select **Custom Configuration** option and enter the **Database server name**, **User name**, and **Password** values.</span></span> <span data-ttu-id="82446-121">Sélectionnez **configurer** pour continuer.</span><span class="sxs-lookup"><span data-stu-id="82446-121">Select **Configure** to continue.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="82446-122">Comme vous configurez uniquement le service d'authentification unique de l'entreprise à ce moment, vous pouvez simplement entrer le compte de domaine créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="82446-122">Since you are only be configuring the Enterprise SSO service at this time, you can just enter the domain account that you created earlier here.</span></span>  
  
7.  <span data-ttu-id="82446-123">Sélectionnez le **Enterprise SSO** option dans le volet gauche et définissez les options suivantes pour la fonctionnalité de l’authentification unique de l’entreprise :</span><span class="sxs-lookup"><span data-stu-id="82446-123">Select the **Enterprise SSO** option from the left pane and set the following options for the Enterprise SSO feature:</span></span>  
  
    1.  <span data-ttu-id="82446-124">Sélectionnez le **activer Enterprise Single Sign-On sur cet ordinateur** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="82446-124">Select the **Enable Enterprise Single Sign-On on this computer** check box.</span></span>  
  
    2.  <span data-ttu-id="82446-125">Sélectionnez **créer un nouveau système SSO**.</span><span class="sxs-lookup"><span data-stu-id="82446-125">Select **Create a new SSO system**.</span></span>  
  
    3.  <span data-ttu-id="82446-126">Entrez le **stocke les données** pour **nom du serveur** et **nom de la base de données** valeurs.</span><span class="sxs-lookup"><span data-stu-id="82446-126">Enter the **Data stores** for **Server Name** and **Database Name** values.</span></span>  
  
    4.  <span data-ttu-id="82446-127">Vérifiez que le compte de domaine créé précédemment est le compte associé au service d'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="82446-127">Verify that the domain account that you created earlier is the account that is associated with the Enterprise SSO service.</span></span>  
  
    5.  <span data-ttu-id="82446-128">Entrez le groupe Administrateurs de l'authentification unique du domaine créé précédemment comme groupe associé au rôle Administrateur(s) de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="82446-128">Enter the domain SSO Administrators group that you created earlier as the group associated with the SSO Administrator(s) role.</span></span>  
  
    6.  <span data-ttu-id="82446-129">Entrez le groupe Administrateurs d'applications associées à authentification unique du domaine créé précédemment comme groupe associé au rôle Administrateur(s) d'applications associées à authentification unique.</span><span class="sxs-lookup"><span data-stu-id="82446-129">Enter the domain SSO Affiliate Administrators group that you created earlier as the group associated with the SSO Affiliate Administrator(s) role.</span></span>  
  
8.  <span data-ttu-id="82446-130">Sélectionnez le **sauvegarde du Secret Enterprise SSO** option dans le volet gauche et fournissez les paramètres appropriés pour sauvegarder le secret de l’authentification unique de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="82446-130">Select the **Enterprise SSO Secret Backup** option from the left pane and provide the appropriate parameters for backing up the Enterprise SSO secret.</span></span> <span data-ttu-id="82446-131">Par défaut, le secret de l’authentification unique de l’entreprise est sauvegardé sur  *\<lecteur >*: \Program Files\Enterprise Single Sign-On\\*SSOxxxx*.bak.</span><span class="sxs-lookup"><span data-stu-id="82446-131">By default, the Enterprise SSO secret is backed up to *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On\\*SSOxxxx*.bak.</span></span>  
  
9. <span data-ttu-id="82446-132">Cliquez sur le **appliquer la Configuration** et passez en revue le résumé.</span><span class="sxs-lookup"><span data-stu-id="82446-132">Click the **Apply Configuration** and review the Summary.</span></span>  
  
10. <span data-ttu-id="82446-133">Cliquez sur **suivant** pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="82446-133">Click **Next** to apply the configuration.</span></span>  
  
11. <span data-ttu-id="82446-134">Cliquez sur **Terminer** pour fermer l’Assistant de Configuration.</span><span class="sxs-lookup"><span data-stu-id="82446-134">Click **Finish** to close the Configuration wizard.</span></span>  
  
12. <span data-ttu-id="82446-135">Fermez la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="82446-135">Close the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration.</span></span>  
  
13. <span data-ttu-id="82446-136">Ouvrez une session sur le nœud de cluster passif, puis démarrez la Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="82446-136">Log on to the passive cluster node and start the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration.</span></span>  
  
14. <span data-ttu-id="82446-137">Choisissez le **Configuration personnalisée** et entrez les mêmes valeurs pour le **nom du serveur de base de données**, **nom d’utilisateur**, et **mot de passe** qui vous avez entré lors de la configuration du premier nœud du cluster.</span><span class="sxs-lookup"><span data-stu-id="82446-137">Choose the **Custom Configuration** option and enter the same values for the **Database server name**, **User name**, and **Password** that you entered when configuring the first cluster node.</span></span> <span data-ttu-id="82446-138">Après avoir entré ces valeurs, cliquez sur **configurer** pour continuer.</span><span class="sxs-lookup"><span data-stu-id="82446-138">After entering these values, click **Configure** to continue.</span></span>  
  
15. <span data-ttu-id="82446-139">Sélectionnez le **Enterprise SSO** option dans le volet gauche et définissez les options suivantes pour la fonctionnalité de l’authentification unique de l’entreprise :</span><span class="sxs-lookup"><span data-stu-id="82446-139">Select the **Enterprise SSO** option from the left pane and set the following options for the Enterprise SSO feature:</span></span>  
  
    1.  <span data-ttu-id="82446-140">Sélectionnez le **activer Enterprise Single Sign-On sur cet ordinateur** option.</span><span class="sxs-lookup"><span data-stu-id="82446-140">Select the **Enable Enterprise Single Sign-On on this computer** option.</span></span>  
  
    2.  <span data-ttu-id="82446-141">Sélectionnez **joindre un système SSO existant**.</span><span class="sxs-lookup"><span data-stu-id="82446-141">Select **Join an existing SSO system**.</span></span>  
  
    3.  <span data-ttu-id="82446-142">Entrez les mêmes valeurs pour la base de données SSO **nom du serveur** et **nom de la base de données** que vous avez entré lors de la configuration du premier nœud du cluster.</span><span class="sxs-lookup"><span data-stu-id="82446-142">Enter the same values for the SSO Database **Server Name** and **Database Name** that you entered when configuring the first cluster node.</span></span>  
  
    4.  <span data-ttu-id="82446-143">Entrez la même valeur pour le compte de domaine que celle entrée lors de la configuration du premier nœud de cluster.</span><span class="sxs-lookup"><span data-stu-id="82446-143">Enter the same value for the domain account that you entered when configuring the first cluster node.</span></span>  
  
16. <span data-ttu-id="82446-144">Sélectionnez **appliquer la Configuration** pour afficher le résumé.</span><span class="sxs-lookup"><span data-stu-id="82446-144">Select **Apply Configuration** to display the Summary.</span></span>  
  
17. <span data-ttu-id="82446-145">Sélectionnez **suivant** pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="82446-145">Select **Next** to apply the configuration.</span></span>  
  
18. <span data-ttu-id="82446-146">Sélectionnez **Terminer** pour fermer l’Assistant de Configuration.</span><span class="sxs-lookup"><span data-stu-id="82446-146">Select **Finish** to close the Configuration wizard.</span></span>  
  
19. <span data-ttu-id="82446-147">Fermez la Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="82446-147">Close the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration.</span></span>  
  
### <a name="to-update-the-master-secret-server-name-in-the-sso-database"></a><span data-ttu-id="82446-148">Pour mettre à jour le nom du serveur de secret principal dans la base de données d'authentification unique</span><span class="sxs-lookup"><span data-stu-id="82446-148">To update the master secret server name in the SSO database</span></span>  
  
1.  <span data-ttu-id="82446-149">Tapez les commandes suivantes dans une invite de commandes sur le nœud de cluster actif pour arrêter et redémarrer le service d'authentification unique de l'entreprise :</span><span class="sxs-lookup"><span data-stu-id="82446-149">Type the following commands from a command prompt on the active cluster node to stop and restart the Enterprise SSO service:</span></span>  
  
    ```  
    net stop entsso  
    ```  
  
     <span data-ttu-id="82446-150">et</span><span class="sxs-lookup"><span data-stu-id="82446-150">and</span></span>  
  
    ```  
    net start entsso  
    ```  
  
2.  <span data-ttu-id="82446-151">Modifiez le nom du serveur de secret principal dans la base de données d'authentification unique par le nom du cluster en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="82446-151">Change the master secret server name in the SSO database to the cluster name by following these steps:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="82446-152">Le nom du cluster est celui défini pour la ressource de nom de réseau créée dans le groupe de clusters/le service ou l'application en cluster qui contiendra le service d'authentification unique de l'entreprise en cluster.</span><span class="sxs-lookup"><span data-stu-id="82446-152">The cluster name is the name defined for the network name resource that you have created in the cluster group / clustered service or application that will contain the clustered Enterprise SSO service.</span></span> <span data-ttu-id="82446-153">Par exemple, le nom peut être *CLUSTERBIZTALK*.</span><span class="sxs-lookup"><span data-stu-id="82446-153">For example, the name may be *BIZTALKCLUSTER*.</span></span>  
  
    1.  <span data-ttu-id="82446-154">Collez le code suivant dans un éditeur de texte :</span><span class="sxs-lookup"><span data-stu-id="82446-154">Paste the following code in a text editor:</span></span>  
  
        ```  
        <sso>  
          <globalInfo>  
            <secretServer>BIZTALKCLUSTER</secretServer>  
          </globalInfo>  
        </sso>  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="82446-155">*BIZTALKCLUSTER* est un espace réservé pour la ressource de nom de réseau réelle créée dans le cluster group / cluster le service ou application.</span><span class="sxs-lookup"><span data-stu-id="82446-155">*BIZTALKCLUSTER* is a placeholder for the actual network name resource that is created in the cluster group / clustered service or application.</span></span>  
  
    2.  <span data-ttu-id="82446-156">Enregistrez le fichier au format .xml.</span><span class="sxs-lookup"><span data-stu-id="82446-156">Save the file as an .xml file.</span></span> <span data-ttu-id="82446-157">Par exemple, enregistrez le fichier sous SSOCLUSTER.xml.</span><span class="sxs-lookup"><span data-stu-id="82446-157">For example, save the file as SSOCLUSTER.xml.</span></span>  
  
    3.  <span data-ttu-id="82446-158">À l'invite de commandes, accédez au dossier d'installation des services d'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="82446-158">At a command prompt, change to the Enterprise SSO installation folder.</span></span> <span data-ttu-id="82446-159">Par défaut, le dossier d’installation est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="82446-159">By default, the installation folder is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
    4.  <span data-ttu-id="82446-160">Tapez la commande suivante à l'invite de commandes pour mettre à jour le nom du serveur de secret principal dans la base de données :</span><span class="sxs-lookup"><span data-stu-id="82446-160">Type the following command at the command prompt to update the master secret server name in the database:</span></span>  
  
        ```  
        ssomanage -updatedb XMLFile  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="82446-161">*XMLFile* est un espace réservé pour le nom du fichier .xml que vous avez enregistré précédemment.</span><span class="sxs-lookup"><span data-stu-id="82446-161">*XMLFile* is a placeholder for the name of the .xml file that you saved earlier.</span></span>  
  
### <a name="to-create-the-clustered-enterprise-sso-resource"></a><span data-ttu-id="82446-162">Pour créer la ressource d'authentification unique de l'entreprise en cluster</span><span class="sxs-lookup"><span data-stu-id="82446-162">To create the clustered Enterprise SSO resource</span></span>  
  
1.  <span data-ttu-id="82446-163">Si le cluster n’est pas configuré avec une ressource Distributed Transaction Coordinator (MSDTC) puis suivez les étapes décrites dans le livre blanc « Amélioration erreur la tolérance de panne dans BizTalk Server par Using a Windows Server Cluster » [http:// go.Microsoft.com/fwlink/ ? LinkId = 69207](http://go.microsoft.com/fwlink/?LinkId=69207) pour créer une ressource MSDTC en cluster.</span><span class="sxs-lookup"><span data-stu-id="82446-163">If the cluster is not configured with a clustered Distributed Transaction Coordinator (MSDTC) resource then follow the steps in the "Improving Fault Tolerance in BizTalk Server by Using a Windows Server Cluster" white paper at [http://go.microsoft.com/fwlink/?LinkId=69207](http://go.microsoft.com/fwlink/?LinkId=69207) to create a clustered MSDTC resource.</span></span>  
  
2.  <span data-ttu-id="82446-164">Cliquez sur **Démarrer**, **programmes**, **outils d’administration**, puis **gestion du Cluster de basculement** pour démarrer le Cluster de basculement Programme de gestion.</span><span class="sxs-lookup"><span data-stu-id="82446-164">Click **Start**, **Programs**, **Administrative Tools**, and then **Failover Cluster Management** to start the Failover Cluster Management program.</span></span>  
  
3.  <span data-ttu-id="82446-165">Dans le volet gauche, cliquez sur **gestion du Cluster de basculement** et cliquez sur **gérer un Cluster**.</span><span class="sxs-lookup"><span data-stu-id="82446-165">In the left hand pane, right-click **Failover Cluster Management** and click **Manage a Cluster**.</span></span>  
  
4.  <span data-ttu-id="82446-166">Sur le **sélectionner un cluster à gérer** boîte de dialogue, entrez le cluster pour être géré et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="82446-166">On the **Select a cluster to manage** dialog box, enter the cluster to be managed and click **OK**.</span></span>  
  
5.  <span data-ttu-id="82446-167">Dans le volet gauche, cliquez pour sélectionner un service ou une application en cluster, contenant une ressource Nom de réseau et une ressource Adresse IP.</span><span class="sxs-lookup"><span data-stu-id="82446-167">In the left hand pane click to select a clustered service or application that contains an IP Address and Network Name resource.</span></span> <span data-ttu-id="82446-168">Suivez les étapes de [la création d’un groupe de clusters avec un disque, une adresse IP et une ressource de nom](../core/how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource1.md) pour créer un groupe avec une ressource d’adresse IP et nom de réseau si elle n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="82446-168">Follow the steps in [How to Create a Cluster Group with a Disk, IP Address, and Name Resource](../core/how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource1.md) to create a group with an IP Address and Network Name resource if one does not already exist.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="82446-169">Un service SSO en cluster n’exige pas explicitement l’utilisation d’une ressource de disque physique en cluster dans le même groupe.</span><span class="sxs-lookup"><span data-stu-id="82446-169">A clustered Enterprise SSO service does not explicitly require the use of a clustered Physical Disk resource in the same group.</span></span>  
  
6.  <span data-ttu-id="82446-170">Avec le bouton droit de l’application ou le service en cluster, pointez sur **ajouter une ressource**, puis cliquez sur **Service générique** pour afficher les **Assistant Nouvelle ressource** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="82446-170">Right-click the clustered service or application, point to **Add a resource**, and click **Generic Service** to display the **New Resource Wizard** dialog.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="82446-171">Dans le **paramètres de Service générique** boîte de dialogue, si vous ne cliquez pas sur pour sélectionner le **utiliser le nom réseau pour le nom de l’ordinateur** case à cocher, ordinateurs clients SSO génère une erreur semblable au suivant lorsqu’ils Essayez de contacter cette instance en cluster du service SSO de l’entreprise :</span><span class="sxs-lookup"><span data-stu-id="82446-171">In the **Generic Service Parameters** dialog box, if you do not click to select the **Use Network Name for computer name** check box, SSO client computers will generate an error similar to the following when they try to contact this clustered instance of the Enterprise SSO service:</span></span>  
    >   
    >  <span data-ttu-id="82446-172">Impossible d'extraire les secrets principaux.</span><span class="sxs-lookup"><span data-stu-id="82446-172">Failed to retrieve master secrets.</span></span>  
    >   
    >  <span data-ttu-id="82446-173">Vérifiez que le nom de serveur de secret principal est correct et disponible.</span><span class="sxs-lookup"><span data-stu-id="82446-173">Verify that the master secret server name is correct and that it is available.</span></span> <span data-ttu-id="82446-174">Nom du serveur de secret : Code d'erreur ENTSSO : 0x800706D9, le mappeur de point final n'a plus de point final disponible.</span><span class="sxs-lookup"><span data-stu-id="82446-174">Secret Server Name: ENTSSO Error Code: 0x800706D9, there are no more endpoints available from the endpoint mapper.</span></span>  
  
7.  <span data-ttu-id="82446-175">Sur le **sélectionner un Service** page de la **Assistant Nouvelle ressource**, sélectionnez **Enterprise Single Sign-On Service** et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="82446-175">On the **Select Service** page of the **New Resource Wizard**, click to select **Enterprise Single Sign-On Service** and click **Next**.</span></span>  
  
8.  <span data-ttu-id="82446-176">Sur le **Confirmation** page, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="82446-176">On the **Confirmation** page click **Next**.</span></span>  
  
9. <span data-ttu-id="82446-177">Sur le **Résumé** page, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="82446-177">On the **Summary** page click **Finish**.</span></span> <span data-ttu-id="82446-178">Une instance en cluster de l’entreprise Sign-On Service unique s’affiche sous **autres ressources** dans le volet central de la **gestion du Cluster de basculement** interface.</span><span class="sxs-lookup"><span data-stu-id="82446-178">A clustered instance of the Enterprise Single Sign-On Service will appear under **Other Resources** in the center pane of the **Failover Cluster Management** interface.</span></span>  
  
10. <span data-ttu-id="82446-179">Avec le bouton droit de l’instance en cluster de l’entreprise Sign-On Service unique et sélectionnez **propriétés** pour afficher les **entreprise unique Sign-On Service Properties** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="82446-179">Right-click the clustered instance of the Enterprise Single Sign-On Service and select **Properties** to display the **Enterprise Single Sign-On Service Properties** dialog box.</span></span>  
  
11. <span data-ttu-id="82446-180">Cliquez sur le **dépendances** onglet de la boîte de dialogue Propriétés et cliquez sur **insérer**.</span><span class="sxs-lookup"><span data-stu-id="82446-180">Click the **Dependencies** tab of the properties dialog box and click **Insert**.</span></span>  
  
12. <span data-ttu-id="82446-181">Cliquez sur la zone de liste déroulante sous **ressource**, sélectionnez le **nom :** ressource et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="82446-181">Click the drop down box under **Resource**, select the **Name:** resource and click **OK**.</span></span>  
  
### <a name="to-restore-the-master-secret-on-the-second-cluster-node"></a><span data-ttu-id="82446-182">Pour restaurer le secret principal sur le second nœud de cluster</span><span class="sxs-lookup"><span data-stu-id="82446-182">To restore the master secret on the second cluster node</span></span>  
  
1.  <span data-ttu-id="82446-183">Dans la gestion du Cluster de basculement, avec le bouton droit sur le service en cluster ou l’application qui contient le service Enterprise Single Sign-On en cluster et sélectionnez **mettre ce service ou cette application en ligne** pour démarrer toutes les ressources dans le service de cluster ou l’application.</span><span class="sxs-lookup"><span data-stu-id="82446-183">In Failover Cluster Management, right click the clustered service or application that contains the clustered Enterprise Single Sign-On service and then click **Bring this service or application online** to start all of the resources in the clustered service or application.</span></span>  
  
2.  <span data-ttu-id="82446-184">Avec le bouton droit de l’application ou le service en cluster, pointez sur **déplacer ce service ou cette application vers un autre nœud**, puis cliquez sur le second nœud.</span><span class="sxs-lookup"><span data-stu-id="82446-184">Right-click the clustered service or application, point to **Move this service or application to another node**, and click the second node.</span></span> <span data-ttu-id="82446-185">Cette opération déplace le service ou l'application en cluster contenant le service d'authentification unique de l'entreprise en cluster du premier nœud vers le second.</span><span class="sxs-lookup"><span data-stu-id="82446-185">This step moves the clustered service or application that contains the clustered Enterprise Single Sign-On service from the first node to the second node.</span></span>  
  
3.  <span data-ttu-id="82446-186">Cliquez sur le service Enterprise Single Sign-On en cluster, sur **hors connexion ce service ou cette application**, puis cliquez sur l’instance en cluster du service SSO de l’entreprise, sur **mettre ce service ou application en ligne**.</span><span class="sxs-lookup"><span data-stu-id="82446-186">Right-click the clustered Enterprise Single Sign-On service and click **Take this service or application offline**, then right-click the clustered instance of the Enterprise SSO service and click **Bring this service or application online**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="82446-187">Si cette étape n'est pas achevée, les tentatives de restauration du secret principal risquent d'échouer.</span><span class="sxs-lookup"><span data-stu-id="82446-187">If this step is not completed the attempt to restore the master secret may not succeed.</span></span>  
  
4.  <span data-ttu-id="82446-188">Copiez le fichier de sauvegarde du secret principal du premier nœud dans le dossier d'installation \Enterprise Single Sign-On sur le second nœud.</span><span class="sxs-lookup"><span data-stu-id="82446-188">Copy the master secret backup file from the first node to the \Enterprise Single Sign-On installation folder on the second node.</span></span> <span data-ttu-id="82446-189">Par défaut, le dossier d’installation est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="82446-189">By default, the installation folder is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
5.  <span data-ttu-id="82446-190">Ouvrez une session sur le second nœud, ouvrez une invite de commandes, puis accédez au dossier d'installation des services d'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="82446-190">Log on to the second node and at a command prompt, change to the Enterprise SSO installation folder.</span></span>  
  
6.  <span data-ttu-id="82446-191">Tapez la commande suivante à l'invite de commandes pour restaurer le secret principal sur le second nœud :</span><span class="sxs-lookup"><span data-stu-id="82446-191">Type the following command from the command prompt to restore the master secret to the second node:</span></span>  
  
    ```  
    ssoconfig -restoresecret RestoreFile  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="82446-192">Remplacez *RestoreFile* avec le chemin d’accès et le nom du fichier de sauvegarde qui contient le secret principal.</span><span class="sxs-lookup"><span data-stu-id="82446-192">Replace *RestoreFile* with the path of and the name of the backup file that contains the master secret.</span></span>  
  
     <span data-ttu-id="82446-193">Le serveur principal est stocké dans le Registre à l'emplacement suivant :</span><span class="sxs-lookup"><span data-stu-id="82446-193">The master secret is stored in the registry at the following location:</span></span>  
  
     <span data-ttu-id="82446-194">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS</span><span class="sxs-lookup"><span data-stu-id="82446-194">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS</span></span>  
  
7.  <span data-ttu-id="82446-195">Déplacez le service ou l'application en cluster contenant le service d'authentification unique de l'entreprise en cluster de ce nœud vers l'autre nœud du cluster pour assurer la fonctionnalité de basculement.</span><span class="sxs-lookup"><span data-stu-id="82446-195">Move the clustered service or application that contains the clustered Enterprise Single Sign-On service from this cluster node to other cluster node to ensure failover functionality.</span></span> <span data-ttu-id="82446-196">Replacez ensuite le groupe de clusters dans sa position d'origine pour vérifier la fonctionnalité de restauration.</span><span class="sxs-lookup"><span data-stu-id="82446-196">Then move the cluster group back to verify fail-back functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82446-197">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82446-197">See Also</span></span>  
 [<span data-ttu-id="82446-198">Comment créer un groupe de clusters avec un disque, une adresse IP et une ressource de nom</span><span class="sxs-lookup"><span data-stu-id="82446-198">How to Create a Cluster Group with a Disk, IP Address, and Name Resource</span></span>](../core/how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource1.md)

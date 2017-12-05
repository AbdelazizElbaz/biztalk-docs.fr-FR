---
title: Configurer et installer les composants requis pour BizTalk Server 2016 | Documents Microsoft
description: "Instructions détaillées pour installer et configurer les logiciels requis et les paramètres de BizTalk Server 2016"
author: MandiOhlinger
manager: anneta
ms.prod: biztalk-server
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa70b621-903a-4cfa-9cb0-c6a82ed8f733
caps.latest.revision: "11"
ms.author: mandia
ms.openlocfilehash: 2f03aaf7d33cc494320d1ef0944b48286bc1b24c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="set-up-and-install-prerequisites-for-biztalk-server-2016"></a><span data-ttu-id="46bc5-103">Installation et configuration des composants logiciels requis pour BizTalk Server 2016</span><span class="sxs-lookup"><span data-stu-id="46bc5-103">Set up and install prerequisites for BizTalk Server 2016</span></span>
<span data-ttu-id="46bc5-104">Configurez le serveur, puis installez et configurez les composants logiciels requis.</span><span class="sxs-lookup"><span data-stu-id="46bc5-104">Set up the server, and install and configure the software prerequisites.</span></span>

## <a name="join-the-administrators-group"></a><span data-ttu-id="46bc5-105">Rejoindre le groupe d’administrateurs</span><span class="sxs-lookup"><span data-stu-id="46bc5-105">Join the Administrators Group</span></span>
<span data-ttu-id="46bc5-106">Pour installer et configurer BizTalk Server, connectez-vous au serveur à l’aide d’un compte d’administrateur sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="46bc5-106">To install and configure BizTalk Server, sign in to the server using an administrator account on the local computer.</span></span> <span data-ttu-id="46bc5-107">Ajoutez les comptes d’utilisateurs qui administrent le serveur BizTalk Server au groupe Administrateurs local :</span><span class="sxs-lookup"><span data-stu-id="46bc5-107">Add any user accounts that are administering the BizTalk Server to the local Administrators group:</span></span>

1.  <span data-ttu-id="46bc5-108">Dans le menu Démarrer, ouvrez **Gestion de l’ordinateur**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-108">In the Start menu, open **Computer Management**.</span></span>

    * <span data-ttu-id="46bc5-109">Ou, ouvrez **Outils d’administration**, puis sélectionnez **Gestion de l’ordinateur**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-109">Or, open **Administrative Tools**, and then select **Computer Management**.</span></span>
    * <span data-ttu-id="46bc5-110">Ou, ouvrez le **Gestionnaire de serveur**, sélectionnez **Outils**, puis sélectionnez **Gestion de l’ordinateur**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-110">Or, open **Server Manager**, select **Tools**, and then select **Computer Management**.</span></span>
  
2.  <span data-ttu-id="46bc5-111">Développez **Utilisateurs et groupes locaux** et sélectionnez **Groupes**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-111">Expand **Local Users and Groups**, and select **Groups**.</span></span>
3.  <span data-ttu-id="46bc5-112">Cliquez avec le bouton droit sur le groupe **Administrateurs** et sélectionnez **Ajouter au groupe**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-112">Right-click the **Administrators** group, and select **Add to Group**.</span></span> <span data-ttu-id="46bc5-113">**Ajoutez** vos comptes et sélectionnez **OK** pour enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="46bc5-113">**Add** your accounts, and select **OK** to save your changes.</span></span> 

## <a name="change-the-computer-name-optional"></a><span data-ttu-id="46bc5-114">Modifier le nom d’ordinateur (facultatif)</span><span class="sxs-lookup"><span data-stu-id="46bc5-114">Change the computer name (optional)</span></span>
<span data-ttu-id="46bc5-115">Si le nom de votre ordinateur est supérieur à 15 caractères, la configuration de BizTalk Server échoue.</span><span class="sxs-lookup"><span data-stu-id="46bc5-115">If your computer name is longer than 15 characters, then BizTalk Server configuration fails.</span></span> <span data-ttu-id="46bc5-116">Pour modifier le nom d’ordinateur en moins de 15 caractères :</span><span class="sxs-lookup"><span data-stu-id="46bc5-116">To change the computer name to less than 15 characters:</span></span>

1.  <span data-ttu-id="46bc5-117">Dans **Gestionnaire de serveur** > **Tableau de bord**, sélectionnez **Serveur local**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-117">In **Server Manager** > **Dashboard**, select **Local Server**.</span></span> 
2.  <span data-ttu-id="46bc5-118">Dans **Propriétés**, sélectionnez la propriété Nom de l’ordinateur pour la modifier.</span><span class="sxs-lookup"><span data-stu-id="46bc5-118">In **Properties**, select the Computer name property to change it.</span></span>
3. <span data-ttu-id="46bc5-119">Redémarrez l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="46bc5-119">Restart the computer.</span></span> 

<span data-ttu-id="46bc5-120">**VOIR AUSSI** : Commande Windows PowerShell [Rename-Computer](https://technet.microsoft.com/library/hh849792.aspx)</span><span class="sxs-lookup"><span data-stu-id="46bc5-120">**SEE ALSO** : Windows PowerShell [Rename-Computer](https://technet.microsoft.com/library/hh849792.aspx)</span></span>

## <a name="enable-network-dtc-access"></a><span data-ttu-id="46bc5-121">Activation de l’accès DTC réseau</span><span class="sxs-lookup"><span data-stu-id="46bc5-121">Enable Network DTC Access</span></span>
<span data-ttu-id="46bc5-122">Si BizTalk et SQL Server sont installés sur des ordinateurs distincts, activez l’accès DTC réseau sur le serveur BizTalk Server et le serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="46bc5-122">If BizTalk and SQL Server are installed on separate computers, then enable Network DTC Access on the BizTalk Server and the SQL Server.</span></span> 

1. <span data-ttu-id="46bc5-123">Dans le menu Démarrer, ouvrez « dcomcnfg ».</span><span class="sxs-lookup"><span data-stu-id="46bc5-123">In the Start menu, open "dcomcnfg".</span></span>

    * <span data-ttu-id="46bc5-124">Ou, ouvrez **Outils d’administration**, puis sélectionnez **Services de composants**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-124">Or, open **Administrative Tools**, and then select **Component Services**.</span></span>
    * <span data-ttu-id="46bc5-125">Ou, ouvrez le **Gestionnaire de serveur**, sélectionnez **Outils**, puis sélectionnez **Services de composants**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-125">Or, open **Server Manager**, select **Tools**, and then select **Component Services**.</span></span>
  
2. <span data-ttu-id="46bc5-126">Développez **Services de composants**, **Ordinateurs**, **Poste de travail**, puis **Distributed Transaction Coordinator**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-126">Expand **Component Services**, expand **Computers**, expand **My Computer**,  and expand **Distributed Transaction Coordinator**.</span></span>
3. <span data-ttu-id="46bc5-127">Cliquez avec le bouton droit sur **DTC local**, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-127">Right-click **Local DTC**, and select **Properties**.</span></span>
4. <span data-ttu-id="46bc5-128">Accédez à l’onglet **Sécurité** et vérifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="46bc5-128">Go to the **Security** tab, and check the following:</span></span>  
    * <span data-ttu-id="46bc5-129">Accès DTC réseau</span><span class="sxs-lookup"><span data-stu-id="46bc5-129">Network DTC Access</span></span>
    * <span data-ttu-id="46bc5-130">Autoriser les transactions entrantes</span><span class="sxs-lookup"><span data-stu-id="46bc5-130">Allow Inbound</span></span>
    * <span data-ttu-id="46bc5-131">Autoriser les transactions sortantes</span><span class="sxs-lookup"><span data-stu-id="46bc5-131">Allow Outbound</span></span>
    * <span data-ttu-id="46bc5-132">Aucune authentification requise</span><span class="sxs-lookup"><span data-stu-id="46bc5-132">No Authentication Required</span></span>
5. <span data-ttu-id="46bc5-133">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-133">Select **OK**.</span></span> <span data-ttu-id="46bc5-134">Si vous êtes invité à redémarrer MS DTC, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-134">If prompted to restart MS DTC, select **Yes**.</span></span> 

<span data-ttu-id="46bc5-135">Pour obtenir des paramètres supplémentaires qui peuvent être nécessaires, consultez [Résolution des problèmes liés à MSDTC](../core/troubleshooting-problems-with-msdtc.md).</span><span class="sxs-lookup"><span data-stu-id="46bc5-135">For additional settings that may be needed, see [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).</span></span>

## <a name="configure-application-event-log-optional"></a><span data-ttu-id="46bc5-136">Configurer le journal des événements Application (facultatif)</span><span class="sxs-lookup"><span data-stu-id="46bc5-136">Configure Application Event Log (optional)</span></span>

<span data-ttu-id="46bc5-137">Le programme d'installation de BizTalk Server conserve un enregistrement des événements dans le journal des événements de l'application.</span><span class="sxs-lookup"><span data-stu-id="46bc5-137">BizTalk Server setup keeps a record of events in the Application Event Log.</span></span> <span data-ttu-id="46bc5-138">Selon les fonctionnalités de BizTalk Server installées, il se peut que la limite d'espace requis dans le journal soit dépassée.</span><span class="sxs-lookup"><span data-stu-id="46bc5-138">Depending on the BizTalk Server features installed, the amount of space required in the log may exceed its limit.</span></span> <span data-ttu-id="46bc5-139">L’installation échoue si le journal des événements de l’application ne dispose plus de suffisamment d’espace lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="46bc5-139">If the application event log runs out of space during the setup, the installation fails.</span></span> <span data-ttu-id="46bc5-140">Le fait de modifier les paramètres du journal d'événements d'applications permet d'empêcher cet échec.</span><span class="sxs-lookup"><span data-stu-id="46bc5-140">Changing the Application Event Log settings prevents this failure.</span></span>

1. <span data-ttu-id="46bc5-141">Dans le menu Démarrer, ouvrez l’**Observateur d’événements** :</span><span class="sxs-lookup"><span data-stu-id="46bc5-141">In the Start menu, open **Event Viewer**:</span></span>

    * <span data-ttu-id="46bc5-142">Ou, ouvrez **Outils d’administration**, puis sélectionnez **Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-142">Or, open **Administrative Tools**, and then select **Event Viewer**.</span></span>
    * <span data-ttu-id="46bc5-143">Ou, ouvrez le **Gestionnaire de serveur**, sélectionnez **Outils**, puis sélectionnez **Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-143">Or, open **Server Manager**, select **Tools**, and then select **Event Viewer**.</span></span>
  
2. <span data-ttu-id="46bc5-144">Développez **Journaux Windows**, cliquez avec le bouton droit sur **Application**, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-144">Expand **Windows Logs**, right-click **Application**, and then select **Properties**.</span></span> 
3. <span data-ttu-id="46bc5-145">Pour déterminer l’espace disponible, comparez les propriétés **Taille du journal** et **Taille maximale du journal**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-145">To determine the available space, compare the **Log Size** and the **Maximum log size** properties.</span></span> 

    * <span data-ttu-id="46bc5-146">Pour ajouter de l’espace, entrez un plus grand nombre dans **Taille maximale du journal**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-146">To add space, enter a higher number in **Maximum log size**.</span></span>
    * <span data-ttu-id="46bc5-147">Pour activer le remplacement des anciens événements lorsque le journal est plein, sélectionnez **Remplacer les événements si nécessaire**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-147">To enable overwriting of old events when the log becomes full, select **Overwrite events as needed**.</span></span>
    * <span data-ttu-id="46bc5-148">Pour effacer les événements du journal, sélectionnez **Effacer le journal**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-148">To clear the log events, select **Clear log**.</span></span>

4. <span data-ttu-id="46bc5-149">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-149">Select **OK**.</span></span>

## <a name="edge-cant-be-opened-optional"></a><span data-ttu-id="46bc5-150">Bord ne peut pas être ouvert (facultatif)</span><span class="sxs-lookup"><span data-stu-id="46bc5-150">Edge can’t be opened (optional)</span></span>

<span data-ttu-id="46bc5-151">Lorsque vous utilisez Edge, le message suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="46bc5-151">When using Edge, the following message displays:</span></span>  
`Microsoft Edge can't be opened using the Built-in Administrator account. Sign in with a different account and try again.`

<span data-ttu-id="46bc5-152">Pour permettre d’ouvrir Edge à l’aide du compte Administrateur intégré :</span><span class="sxs-lookup"><span data-stu-id="46bc5-152">To allow Edge to open using the built-in administrator account:</span></span>

1. <span data-ttu-id="46bc5-153">Dans le menu Démarrer, ouvrez **Stratégie de sécurité locale**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-153">In the Start menu, open **Local Security Policy**.</span></span> <span data-ttu-id="46bc5-154">Ou, ouvrez le **Gestionnaire de serveur**, sélectionnez **Outils**, puis sélectionnez **Stratégie de sécurité locale**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-154">Or, open **Server Manager**, select **Tools**, and then select **Local Security Policy**.</span></span>
2.  <span data-ttu-id="46bc5-155">Développez **Stratégies locales** et sélectionnez **Options de sécurité**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-155">Expand **Local Policies**, and select **Security Options**.</span></span> 
3.  <span data-ttu-id="46bc5-156">Accédez à la stratégie **Contrôle de compte d’utilisateur : mode Approbation administrateur pour le compte Administrateur intégré** et **activez** la stratégie.</span><span class="sxs-lookup"><span data-stu-id="46bc5-156">Go to the **User Account Control: Admin Approval Mode for the Built-in Administrator account** policy, and **Enable** the policy.</span></span> 
4. <span data-ttu-id="46bc5-157">Sélectionnez **OK** et redémarrez l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="46bc5-157">Select **OK**, and restart your computer.</span></span>

## <a name="install-windows-updates"></a><span data-ttu-id="46bc5-158">Installation des mises à jour Windows</span><span class="sxs-lookup"><span data-stu-id="46bc5-158">Install Windows Updates</span></span>

<span data-ttu-id="46bc5-159">Veillez à installer les dernières mises à jour critiques de Windows.</span><span class="sxs-lookup"><span data-stu-id="46bc5-159">Be sure to install the latest critical Windows updates.</span></span> 

1. <span data-ttu-id="46bc5-160">Dans le menu Démarrer, ouvrez **Mises à jour Windows** et recherchez des mises à jour.</span><span class="sxs-lookup"><span data-stu-id="46bc5-160">On the Start menu, open **Windows Updates**, and check for updates.</span></span> <span data-ttu-id="46bc5-161">Vous pouvez également ouvrir **Paramètres** et sélectionner **Mise à jour et sécurité**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-161">You can also open **Settings**, and select **Update and security**.</span></span>
2. <span data-ttu-id="46bc5-162">Après avoir installé les mises à jour, vous devrez peut-être redémarrer l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="46bc5-162">After installing updates, you may need to restart the computer.</span></span>

## <a name="enable-iis"></a><span data-ttu-id="46bc5-163">Activer IIS</span><span class="sxs-lookup"><span data-stu-id="46bc5-163">Enable IIS</span></span>
<span data-ttu-id="46bc5-164">BizTalk Server requiert IIS pour les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="46bc5-164">BizTalk Server requires IIS for the following features:</span></span>

- <span data-ttu-id="46bc5-165">adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="46bc5-165">HTTP adapter</span></span>
- <span data-ttu-id="46bc5-166">adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="46bc5-166">SOAP adapter</span></span>
- <span data-ttu-id="46bc5-167">Adaptateur Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="46bc5-167">Windows SharePoint Services adapter</span></span>
- <span data-ttu-id="46bc5-168">Chiffrement SSL (Secure Sockets Layer)</span><span class="sxs-lookup"><span data-stu-id="46bc5-168">Secure Sockets Layer (SSL) encryption</span></span>
- <span data-ttu-id="46bc5-169">Portail BAM</span><span class="sxs-lookup"><span data-stu-id="46bc5-169">BAM Portal</span></span>
- <span data-ttu-id="46bc5-170">Routage</span><span class="sxs-lookup"><span data-stu-id="46bc5-170">EDI</span></span>

<span data-ttu-id="46bc5-171">IIS est fourni avec le système d’exploitation comme **rôle** ou **fonctionnalité**, selon le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="46bc5-171">IIS is included with the operating system as a **Role** or a **Feature**, depending on the OS.</span></span> <span data-ttu-id="46bc5-172">Pour installer :</span><span class="sxs-lookup"><span data-stu-id="46bc5-172">To install:</span></span>

1. <span data-ttu-id="46bc5-173">Dans le menu Démarrer, ouvrez **Activer ou désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-173">In the Start menu, open **Turn Windows Features on or off**.</span></span> <span data-ttu-id="46bc5-174">Ou, ouvrez le **Gestionnaire de serveur**, sélectionnez **Gérer**, puis sélectionnez **Ajouter des rôles et des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-174">Or, open **Server Manager**, select **Manage**, and then select **Add roles and features**.</span></span>
2. <span data-ttu-id="46bc5-175">Sélectionnez **Services Internet (IIS)** ou **Serveur Web (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-175">Select **Internet Information Services** or **Web Server (IIS)**.</span></span> <span data-ttu-id="46bc5-176">En plus des options activées par défaut, sélectionnez également ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="46bc5-176">In addition to the default checked options, also select the following:</span></span> 

    <span data-ttu-id="46bc5-177">**Windows 10**</span><span class="sxs-lookup"><span data-stu-id="46bc5-177">**Windows 10**</span></span>
    - <span data-ttu-id="46bc5-178">Dans **Outils d’administration Web**, cochez également :</span><span class="sxs-lookup"><span data-stu-id="46bc5-178">In **Web Management Tools**, also check:</span></span>  
        - <span data-ttu-id="46bc5-179">Compatibilité avec la gestion IIS 6</span><span class="sxs-lookup"><span data-stu-id="46bc5-179">IIS 6 Management Compatibility</span></span>
        - <span data-ttu-id="46bc5-180">Console de gestion IIS 6</span><span class="sxs-lookup"><span data-stu-id="46bc5-180">IIS 6 Management Console</span></span>
        - <span data-ttu-id="46bc5-181">Outils de script IIS 6 (installe adsutil.vbs)</span><span class="sxs-lookup"><span data-stu-id="46bc5-181">IIS 6 Scripting Tools (Installs adsutil.vbs)</span></span>
        - <span data-ttu-id="46bc5-182">Compatibilité avec la métabase IIS et la configuration IIS 6</span><span class="sxs-lookup"><span data-stu-id="46bc5-182">IIS Metabase and IIS 6 configuration compatibility</span></span>
        - <span data-ttu-id="46bc5-183">Console de gestion IIS</span><span class="sxs-lookup"><span data-stu-id="46bc5-183">IIS Management Console</span></span>
    - <span data-ttu-id="46bc5-184">Dans **Services World Wide Web**, développez **Sécurité** et cochez également :</span><span class="sxs-lookup"><span data-stu-id="46bc5-184">In **World Wide Web Services**, expand **Security** and also check:</span></span>
        - <span data-ttu-id="46bc5-185">Authentification de base</span><span class="sxs-lookup"><span data-stu-id="46bc5-185">Basic Authentication</span></span>
        - <span data-ttu-id="46bc5-186">Authentification Windows</span><span class="sxs-lookup"><span data-stu-id="46bc5-186">Windows Authentication</span></span>    

    <span data-ttu-id="46bc5-187">**Windows Server**</span><span class="sxs-lookup"><span data-stu-id="46bc5-187">**Windows Server**</span></span>
    - <span data-ttu-id="46bc5-188">Dans **Sécurité**, cochez également :</span><span class="sxs-lookup"><span data-stu-id="46bc5-188">In **Security**, also check:</span></span> 
        - <span data-ttu-id="46bc5-189">Authentification de base</span><span class="sxs-lookup"><span data-stu-id="46bc5-189">Basic Authentication</span></span>
        - <span data-ttu-id="46bc5-190">Authentification Windows</span><span class="sxs-lookup"><span data-stu-id="46bc5-190">Windows Authentication</span></span>    
    - <span data-ttu-id="46bc5-191">Dans **Outils de gestion**, cochez également :</span><span class="sxs-lookup"><span data-stu-id="46bc5-191">In **Management Tools**, also check:</span></span>  
        - <span data-ttu-id="46bc5-192">Console de gestion IIS</span><span class="sxs-lookup"><span data-stu-id="46bc5-192">IIS Management Console</span></span>
        - <span data-ttu-id="46bc5-193">Compatibilité avec la gestion IIS 6</span><span class="sxs-lookup"><span data-stu-id="46bc5-193">IIS 6 Management Compatibility</span></span>
        - <span data-ttu-id="46bc5-194">Compatibilité avec la métabase de données IIS 6</span><span class="sxs-lookup"><span data-stu-id="46bc5-194">IIS 6 Metabase compatibility</span></span>
        - <span data-ttu-id="46bc5-195">Console de gestion IIS 6</span><span class="sxs-lookup"><span data-stu-id="46bc5-195">IIS 6 Management Console</span></span>
        - <span data-ttu-id="46bc5-196">Outils de script IIS 6 (installe adsutil.vbs)</span><span class="sxs-lookup"><span data-stu-id="46bc5-196">IIS 6 Scripting Tools (Installs adsutil.vbs)</span></span>

3. <span data-ttu-id="46bc5-197">Poursuivez l’installation et redémarrez l’ordinateur si vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="46bc5-197">Continue with the installation, and restart the computer if prompted.</span></span> 

<span data-ttu-id="46bc5-198">**VOIR AUSSI** : Installation d’IIS sur [Windows 8 ou Windows Server 2012](http://www.iis.net/learn/get-started/whats-new-in-iis-8/installing-iis-8-on-windows-server-2012).</span><span class="sxs-lookup"><span data-stu-id="46bc5-198">**SEE ALSO** : Install IIS on [Windows 8 or Windows Server 2012](http://www.iis.net/learn/get-started/whats-new-in-iis-8/installing-iis-8-on-windows-server-2012).</span></span>


## <a name="run-64-bit-bam-portal-optional"></a><span data-ttu-id="46bc5-199">Exécution 64 bits du portail BAM (facultatif)</span><span class="sxs-lookup"><span data-stu-id="46bc5-199">Run 64-bit BAM portal (optional)</span></span>
<span data-ttu-id="46bc5-200">Si vous n’utilisez pas le portail BAM, vous pouvez ignorer cette section.</span><span class="sxs-lookup"><span data-stu-id="46bc5-200">If you don't use the BAM portal, then you can skip this section.</span></span> 

<span data-ttu-id="46bc5-201">Le portail BAM s’exécute en mode 32 bits.</span><span class="sxs-lookup"><span data-stu-id="46bc5-201">The BAM Portal runs in 32-bit mode.</span></span> <span data-ttu-id="46bc5-202">Si vous utilisez Internet Information Services (IIS) dans un environnement 64 bits, puis définissez le pool d’applications à s’exécuter en mode 32 bits.</span><span class="sxs-lookup"><span data-stu-id="46bc5-202">If you are using Internet Information Services (IIS) in a 64-bit environment, then set the application pool to run in 32-bit mode.</span></span> 

#### <a name="using-adsutilvbs"></a><span data-ttu-id="46bc5-203">Utilisation d’adsutil.vbs</span><span class="sxs-lookup"><span data-stu-id="46bc5-203">Using adsutil.vbs</span></span>
1.  <span data-ttu-id="46bc5-204">Ouvrez une invite de commandes comme administrateur.</span><span class="sxs-lookup"><span data-stu-id="46bc5-204">Open a command prompt as administrator.</span></span> 
2.  <span data-ttu-id="46bc5-205">À l’invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="46bc5-205">In the command prompt, type:</span></span>  
    `cscript c:\inetpub\adminscripts\adsutil.vbs SET W3SVC/AppPools/Enable32bitAppOnWin64 1`
3. <span data-ttu-id="46bc5-206">Appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="46bc5-206">Select Enter.</span></span>

#### <a name="using-iis-manager"></a><span data-ttu-id="46bc5-207">Utilisation du Gestionnaire des services Internet</span><span class="sxs-lookup"><span data-stu-id="46bc5-207">Using IIS Manager</span></span>
1. <span data-ttu-id="46bc5-208">Dans le menu Démarrer, ouvrez « inetmgr ».</span><span class="sxs-lookup"><span data-stu-id="46bc5-208">In the Start menu, open "inetmgr".</span></span>
2.  <span data-ttu-id="46bc5-209">Développez le nom de l’ordinateur et sélectionnez **Pools d’applications**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-209">Expand the computer name, and select **Application Pools**.</span></span>
3.  <span data-ttu-id="46bc5-210">Cliquez avec le bouton droit sur **DefaultAppPool** et sélectionnez **Paramètres avancés**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-210">Right-click **DefaultAppPool**, and select **Advanced Settings**.</span></span> 
4.  <span data-ttu-id="46bc5-211">Modifiez la valeur de **Activer les applications 32 bits** en spécifiant **True**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-211">Change the value of **Enable 32-bit Applications** to **True**.</span></span> 
5.  <span data-ttu-id="46bc5-212">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-212">Select **OK**.</span></span>

## <a name="install-windows-identity-foundation-wif-optional"></a><span data-ttu-id="46bc5-213">Installation de Windows Identity Foundation (WIF) (facultatif)</span><span class="sxs-lookup"><span data-stu-id="46bc5-213">Install Windows Identity Foundation (WIF) (optional)</span></span>
<span data-ttu-id="46bc5-214">Si vous utilisez l’adaptateur SharePoint Services, BizTalk Server requiert WIF.</span><span class="sxs-lookup"><span data-stu-id="46bc5-214">If you use the SharePoint Services adapter, BizTalk Server requires WIF.</span></span> <span data-ttu-id="46bc5-215">Si vous n’utilisez pas l’adaptateur SharePoint Services, vous pouvez ignorer cette section.</span><span class="sxs-lookup"><span data-stu-id="46bc5-215">If you don't use the SharePoint Services adapter, you can skip this section.</span></span>

<span data-ttu-id="46bc5-216">Windows Identity Foundation est inclus dans le système d’exploitation comme **fonctionnalité**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-216">Windows Identity Foundation is included with the operating system as a **Feature**.</span></span>

1. <span data-ttu-id="46bc5-217">Dans le menu Démarrer, ouvrez **Activer ou désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-217">In the Start menu, open **Turn Windows Features on or off**.</span></span> <span data-ttu-id="46bc5-218">Ou, ouvrez le **Gestionnaire de serveur**, sélectionnez **Gérer**, puis sélectionnez **Ajouter des rôles et des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-218">Or, open **Server Manager**, select **Manage**, and then select **Add roles and features**.</span></span>
2. <span data-ttu-id="46bc5-219">Sélectionnez **Windows Identity Foundation 3.5** et poursuivez l’installation.</span><span class="sxs-lookup"><span data-stu-id="46bc5-219">Select **Windows Identity Foundation 3.5**, and continue with the installation.</span></span> 
3. <span data-ttu-id="46bc5-220">Redémarrez l’ordinateur, si vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="46bc5-220">Restart the computer if prompted.</span></span>

## <a name="install--configure-smtp-server-optional"></a><span data-ttu-id="46bc5-221">Installer et configurer le serveur SMTP (facultatif)</span><span class="sxs-lookup"><span data-stu-id="46bc5-221">Install & configure SMTP Server (optional)</span></span>
<span data-ttu-id="46bc5-222">Si vous utilisez des alertes BAM, BizTalk Server requiert serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="46bc5-222">If you use BAM Alerts, BizTalk Server requires SMTP Server.</span></span> <span data-ttu-id="46bc5-223">Si vous n’utilisez pas les alertes BAM, vous pouvez ignorer cette section.</span><span class="sxs-lookup"><span data-stu-id="46bc5-223">If you don't use BAM Alerts, you can skip this section.</span></span>

<span data-ttu-id="46bc5-224">La fonctionnalité Messagerie de base de données SQL Server utilise un serveur SMTP pour envoyer les alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="46bc5-224">SQL Server Database Mail uses an SMTP Server to send BAM Alerts.</span></span> <span data-ttu-id="46bc5-225">Le serveur SMTP peut être installé localement sur le serveur BizTalk Server ou sur un autre serveur doté d’IIS.</span><span class="sxs-lookup"><span data-stu-id="46bc5-225">SMTP Server can be installed locally on the BizTalk Server or on another server with IIS installed.</span></span> <span data-ttu-id="46bc5-226">Le serveur SMTP n’est pas disponible sur les systèmes d’exploitation clients, tels que Windows 8.1 ou Windows 10.</span><span class="sxs-lookup"><span data-stu-id="46bc5-226">SMTP Server is not available on client operating systems, such as Windows 8.1 or Windows 10.</span></span> 

<span data-ttu-id="46bc5-227">Le serveur SMTP est inclus avec les systèmes d’exploitation serveurs comme **fonctionnalité**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-227">SMTP Server is included with server operating systems as a **Feature**.</span></span>

1. <span data-ttu-id="46bc5-228">Dans le menu Démarrer, ouvrez **Activer ou désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-228">In the Start menu, open **Turn Windows Features on or off**.</span></span> <span data-ttu-id="46bc5-229">Ou, ouvrez le **Gestionnaire de serveur**, sélectionnez **Gérer**, puis sélectionnez **Ajouter des rôles et des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-229">Or, open **Server Manager**, select **Manage**, and then select **Add roles and features**.</span></span>
2. <span data-ttu-id="46bc5-230">Sélectionnez **Serveur SMTP** et poursuivez l’installation.</span><span class="sxs-lookup"><span data-stu-id="46bc5-230">Select **SMTP Server**, and continue with the installation.</span></span> 
3. <span data-ttu-id="46bc5-231">Redémarrez l’ordinateur, si vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="46bc5-231">Restart the computer if prompted.</span></span>

## <a name="install-excel-2016-or-2013-optional"></a><span data-ttu-id="46bc5-232">Installez Excel 2016 ou 2013 (facultatif)</span><span class="sxs-lookup"><span data-stu-id="46bc5-232">Install Excel 2016 or 2013 (optional)</span></span>
<span data-ttu-id="46bc5-233">Si vous utilisez analyse BAM (Business Activity), BizTalk Server requiert Excel.</span><span class="sxs-lookup"><span data-stu-id="46bc5-233">If you use Business Activity Monitoring (BAM), BizTalk Server requires Excel.</span></span> <span data-ttu-id="46bc5-234">Si vous n’utilisez pas BAM, vous pouvez ignorer cette section.</span><span class="sxs-lookup"><span data-stu-id="46bc5-234">If you don't use BAM, you can skip this section.</span></span>

<span data-ttu-id="46bc5-235">Le classeur BAM Office Excel définit les processus d'entreprise que vous souhaitez analyser.</span><span class="sxs-lookup"><span data-stu-id="46bc5-235">The BAM Office Excel Workbook defines the business processes you want to monitor.</span></span> <span data-ttu-id="46bc5-236">Vous utilisez également le classeur Excel BAM pour définir la manière dont les utilisateurs des activités visualisent les données collectées par l’analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="46bc5-236">You also use the BAM Excel Workbook to define the way business users see the data collected by BAM.</span></span>

> [!IMPORTANT] 
> * <span data-ttu-id="46bc5-237">BizTalk Server prend en charge uniquement la version 32 bits de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="46bc5-237">BizTalk Server supports only 32-bit version of Microsoft Office.</span></span> 
> * <span data-ttu-id="46bc5-238">Pour charger correctement le fichier BAM.xla dans Excel, installez **Visual Basic pour Applications** (sous **Composants partagés d’Office**).</span><span class="sxs-lookup"><span data-stu-id="46bc5-238">To successfully load BAM.xla into Excel, install **Visual Basic for Applications** (under **Office Shared Features**).</span></span> <span data-ttu-id="46bc5-239">Sinon, vous pouvez obtenir l’erreur : `This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.`</span><span class="sxs-lookup"><span data-stu-id="46bc5-239">Otherwise, you may get error: `This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.`</span></span>

#### <a name="install-excel-2016"></a><span data-ttu-id="46bc5-240">Installation d’Excel 2016</span><span class="sxs-lookup"><span data-stu-id="46bc5-240">Install Excel 2016</span></span>

<span data-ttu-id="46bc5-241">Office 2016 est installé à l’aide de la fonctionnalité « Démarrer en un clic » ou « Programme d’installation C2R ».</span><span class="sxs-lookup"><span data-stu-id="46bc5-241">Office 2016 is installed using "Click-to-Run" or "C2R Installer".</span></span> <span data-ttu-id="46bc5-242">L’installation C2R télécharge et installe tous les programmes dans Office.</span><span class="sxs-lookup"><span data-stu-id="46bc5-242">The C2R installation downloads and installs all programs within Office.</span></span> <span data-ttu-id="46bc5-243">Pour l’analyse BAM, nous avons besoin d’Excel uniquement.</span><span class="sxs-lookup"><span data-stu-id="46bc5-243">For BAM, we only need Excel.</span></span> <span data-ttu-id="46bc5-244">Pour contourner ce problème, téléchargez et installez l’[outil de déploiement Office 2016](https://www.microsoft.com/download/details.aspx?id=49117) pour personnaliser le programme d’installation C2R.</span><span class="sxs-lookup"><span data-stu-id="46bc5-244">To work around this, download and install the [Office 2016 Deployment Tool](https://www.microsoft.com/download/details.aspx?id=49117) to customize the C2R installer.</span></span>

1. <span data-ttu-id="46bc5-245">Téléchargez et installez l’[outil de déploiement Office 2016](https://www.microsoft.com/download/details.aspx?id=49117).</span><span class="sxs-lookup"><span data-stu-id="46bc5-245">Download and install the [Office 2016 Deployment Tool](https://www.microsoft.com/download/details.aspx?id=49117).</span></span>
2. <span data-ttu-id="46bc5-246">Dans le dossier contenant les fichiers de l’outil de déploiement Office 2016 que vous avez extraits, ouvrez le fichier **configuration.xml** avec un éditeur de texte tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="46bc5-246">In the folder with the Office 2016 Deployment Tool files you extracted, open the **configuration.xml** file with a text editor, such as notepad.</span></span>
3. <span data-ttu-id="46bc5-247">Remplacez la section `<Configuration>` par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="46bc5-247">Replace the `<Configuration>` section with the following:</span></span>  

    ```
    <Configuration>
    <Add SourcePath="D:\" OfficeClientEdition="32">
    <Product ID="O365ProPlusRetail" >
      <Language ID="en-us" />
      <ExcludeApp ID="Access" />
      <ExcludeApp ID="Groove" />
      <ExcludeApp ID="InfoPath" />
      <ExcludeApp ID="Lync" />
      <ExcludeApp ID="OneDrive" />
      <ExcludeApp ID="OneNote" />
      <ExcludeApp ID="Outlook" />
      <ExcludeApp ID="PowerPoint" />
      <ExcludeApp ID="Project" />
      <ExcludeApp ID="Publisher" />
      <ExcludeApp ID="SharePointDesigner" />
      <ExcludeApp ID="Visio" />
      <ExcludeApp ID="Word" />
    </Product>
    </Add>
    </Configuration>
    ```
    
    <span data-ttu-id="46bc5-248">Remplacez « SourcePath » par l’emplacement de votre fichier ISO d’Office 2016.</span><span class="sxs-lookup"><span data-stu-id="46bc5-248">Replace “SourcePath” with the location of your Office 2016 ISO file.</span></span>
4. <span data-ttu-id="46bc5-249">Dans le dossier contenant les fichiers de l’outil de déploiement Office 2016, maintenez la touche **Maj** enfoncée et cliquez avec le bouton droit sur une zone vide du dossier.</span><span class="sxs-lookup"><span data-stu-id="46bc5-249">In the folder with the Office 2016 Deployment Tool files, hold down the **SHIFT** key, and right-click an empty area in the folder.</span></span> <span data-ttu-id="46bc5-250">Sélectionnez **Ouvrir une fenêtre de commandes ici**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-250">Select **Open command window here**.</span></span> 
5. <span data-ttu-id="46bc5-251">Démarrez l’installation d’Excel en entrant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="46bc5-251">Start the Excel installation by entering the following:</span></span>  
  `setup.exe /configure configuration.xml`

    > [!TIP]
    > <span data-ttu-id="46bc5-252">`setup.exe /download configuration.xml` télécharge les fichiers d’installation Office nécessaires.</span><span class="sxs-lookup"><span data-stu-id="46bc5-252">`setup.exe /download configuration.xml` downloads the required office setup files.</span></span>
 
6. <span data-ttu-id="46bc5-253">Sélectionnez Excel et poursuivez l’installation.</span><span class="sxs-lookup"><span data-stu-id="46bc5-253">Select Excel, and continue with the installation.</span></span> 
 
<span data-ttu-id="46bc5-254">**VOIR AUSSI** : [Options de configuration pour l’outil Déploiement d’Office](https://technet.microsoft.com/library/jj219426.aspx) et [Installer Office 2016 ou 2013](https://support.office.com/article/Install-Office-on-your-PC-or-Mac-4414eaaf-0478-48be-9c42-23adc4716658)</span><span class="sxs-lookup"><span data-stu-id="46bc5-254">**SEE ALSO** : [Configuration options for the Office Deployment Tool](https://technet.microsoft.com/library/jj219426.aspx) and [Install Office 2016 or 2013](https://support.office.com/article/Install-Office-on-your-PC-or-Mac-4414eaaf-0478-48be-9c42-23adc4716658)</span></span>

#### <a name="install-excel-2013"></a><span data-ttu-id="46bc5-255">Installation d’Excel 2013</span><span class="sxs-lookup"><span data-stu-id="46bc5-255">Install Excel 2013</span></span>
1. <span data-ttu-id="46bc5-256">Exécutez le programme d'installation de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="46bc5-256">Run the Microsoft Office setup.</span></span>
2. <span data-ttu-id="46bc5-257">Sélectionnez une **installation personnalisée**, puis sélectionnez Excel.</span><span class="sxs-lookup"><span data-stu-id="46bc5-257">Select a **Custom Install**, and select Excel.</span></span>
3. <span data-ttu-id="46bc5-258">Poursuivez l’installation.</span><span class="sxs-lookup"><span data-stu-id="46bc5-258">Continue with the installation.</span></span>   

## <a name="install-visual-c-redistributable-package"></a><span data-ttu-id="46bc5-259">Installer le package redistribuable Visual C++</span><span class="sxs-lookup"><span data-stu-id="46bc5-259">Install Visual C++ redistributable package</span></span>

<span data-ttu-id="46bc5-260">Téléchargez et installez le [package redistribuable Visual C++](https://support.microsoft.com/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package).</span><span class="sxs-lookup"><span data-stu-id="46bc5-260">Download and install the [Visual C++ redistributable package](https://support.microsoft.com/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package).</span></span> <span data-ttu-id="46bc5-261">La version 2013 est requise, même si Visual Studio 2015 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="46bc5-261">The 2013 version is required, even though Visual Studio 2015 is used.</span></span>

<span data-ttu-id="46bc5-262">Le [téléchargements de Visual C++](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads) répertorie toutes les versions disponibles.</span><span class="sxs-lookup"><span data-stu-id="46bc5-262">The [Visual C++ downloads](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads) lists all the available versions.</span></span>

## <a name="install-visual-studio-2015-optional"></a><span data-ttu-id="46bc5-263">Installation de Visual Studio 2015 (facultatif)</span><span class="sxs-lookup"><span data-stu-id="46bc5-263">Install Visual Studio 2015 (optional)</span></span>
<span data-ttu-id="46bc5-264">BizTalk Server nécessite Visual Studio pour créer des projets BizTalk à l’aide des outils de développement.</span><span class="sxs-lookup"><span data-stu-id="46bc5-264">BizTalk Server requires Visual Studio to create BizTalk projects using the development tools.</span></span> <span data-ttu-id="46bc5-265">S’il s’agit d’un serveur intermédiaire ou de production, ou si vous ne faites aucun développement BizTalk, ignorez cette section.</span><span class="sxs-lookup"><span data-stu-id="46bc5-265">If this is a staging or production server, or you're not doing any BizTalk development, then skip this section.</span></span>

<span data-ttu-id="46bc5-266">L’édition Visual Studio Enterprise est recommandée, mais les éditions Professionnal et Community sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="46bc5-266">Visual Studio Enterprise Edition is recommended, but Professional and Community editions are also supported.</span></span> 

1. <span data-ttu-id="46bc5-267">Exécutez l'installation de Visual Studio en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="46bc5-267">Run the Visual Studio setup as Administrator.</span></span>
2. <span data-ttu-id="46bc5-268">Sélectionnez une installation **par défaut**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-268">Select a **Default** installation.</span></span> <span data-ttu-id="46bc5-269">BizTalk Server ne nécessite aucune des fonctionnalités facultatives.</span><span class="sxs-lookup"><span data-stu-id="46bc5-269">BizTalk Server does not require any of the optional features.</span></span>

    > [!NOTE]
    > <span data-ttu-id="46bc5-270">Si vous utilisez Visual Studio pour plusieurs projets BizTalk, sélectionnez l’installation **personnalisée** pour installer d'autres fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="46bc5-270">If you use Visual Studio for more than BizTalk projects, then select the **Custom** installation to install other features.</span></span> <span data-ttu-id="46bc5-271">Certaines fonctionnalités courantes incluent Microsoft Web Developer Tools, les outils de développement Microsoft Office, les outils PowerShell pour Visual Studio et les outils de publication ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="46bc5-271">Some commonly-used features include Microsoft Web Developer Tools, Microsoft Office Developer Tools, PowerShell Tools for Visual Studio, and ClickOnce Publishing Tools.</span></span>
 
3. <span data-ttu-id="46bc5-272">Poursuivez l’installation et redémarrez l’ordinateur si vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="46bc5-272">Continue with the installation, and restart your computer if prompted.</span></span>

<span data-ttu-id="46bc5-273">**VOIR AUSSI** : [Installation de Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)</span><span class="sxs-lookup"><span data-stu-id="46bc5-273">**SEE ALSO** : [Installing Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)</span></span>

> [!IMPORTANT]
> - <span data-ttu-id="46bc5-274">Si vous installez Visual Studio avant d’installer BizTalk Server, puis effectuez une mise à niveau vers Visual Studio Team Explorer, vous devrez peut-être réparer votre installation BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="46bc5-274">If you install Visual Studio before installing BizTalk Server, and then upgrade to Visual Studio Team Explorer, you may need to repair your BizTalk Server installation.</span></span>
> - <span data-ttu-id="46bc5-275">Visual Studio installe automatiquement Microsoft SQL Server Express, qui n’est pas utilisé par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="46bc5-275">Visual Studio automatically installs Microsoft SQL Server Express; which is not used by BizTalk Server.</span></span> <span data-ttu-id="46bc5-276">Désinstallez Microsoft SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="46bc5-276">Uninstall Microsoft SQL Server Express.</span></span> <span data-ttu-id="46bc5-277">Vous pouvez également désinstaller Microsoft SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="46bc5-277">You can also uninstall Microsoft SQL Server Compact.</span></span>  
> - <span data-ttu-id="46bc5-278">Les outils de développement de BizTalk Server sont basés sur Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="46bc5-278">The BizTalk Server development tools are based on Visual Studio.</span></span> <span data-ttu-id="46bc5-279">Au minimum, installez le composant Microsoft Visual C#® .NET avant d’installer les outils et kit de développement de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="46bc5-279">At a minimum, install the Microsoft Visual C#® .NET component before you install the BizTalk Server Developer Tools and SDK.</span></span>
> - <span data-ttu-id="46bc5-280">Le composant d’exécution de BizTalk Server nécessite .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="46bc5-280">The BizTalk Server runtime requires .NET Framework 4.6.</span></span> <span data-ttu-id="46bc5-281">Si l’adaptateur de Windows Communication Foundation (WCF) ou l’intercepteur WCF est installé, .NET Framework 3.0 est requis</span><span class="sxs-lookup"><span data-stu-id="46bc5-281">If the Windows Communication Foundation (WCF) adapter or WCF Interceptor is installed, then .NET Framework 3.0 is required</span></span>

#### <a name="uninstall-sql-server-express"></a><span data-ttu-id="46bc5-282">Désinstallation de SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="46bc5-282">Uninstall SQL Server Express</span></span>
1. <span data-ttu-id="46bc5-283">Dans le menu Démarrer, ouvrez **Programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-283">In the Start menu, open **Programs and Features**.</span></span> <span data-ttu-id="46bc5-284">Ou, ouvrez le **Panneau de configuration** et sélectionnez **Désinstaller un programme**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-284">Or, open the **Control Panel**, and select **Uninstall a program**.</span></span>
2. <span data-ttu-id="46bc5-285">Désinstallation :</span><span class="sxs-lookup"><span data-stu-id="46bc5-285">Uninstall:</span></span> 
    - <span data-ttu-id="46bc5-286">Microsoft SQL Server 2014 Express LocalDb</span><span class="sxs-lookup"><span data-stu-id="46bc5-286">Microsoft SQL Server 2014 Express LocalDb</span></span>
    - <span data-ttu-id="46bc5-287">Microsoft SQL Server Compact 4.0 SP1 x64 ENU</span><span class="sxs-lookup"><span data-stu-id="46bc5-287">Microsoft SQL Server Compact 4.0 SP1 x64 ENU</span></span>
    - <span data-ttu-id="46bc5-288">Microsoft SQL Server 2016 LocalDB (SQL Server 2016 Express LocalDB)</span><span class="sxs-lookup"><span data-stu-id="46bc5-288">Microsoft SQL Server 2016 LocalDB (SQL Server 2016 Express LocalDB)</span></span>
    
3. <span data-ttu-id="46bc5-289">Poursuivez la désinstallation et redémarrez l’ordinateur si vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="46bc5-289">Continue with the uninstall, and restart your computer if prompted.</span></span> 

## <a name="install-sql-server-2016"></a><span data-ttu-id="46bc5-290">Installer SQL Server 2016</span><span class="sxs-lookup"><span data-stu-id="46bc5-290">Install SQL Server 2016</span></span>
<span data-ttu-id="46bc5-291">BizTalk Server nécessite SQL Server.</span><span class="sxs-lookup"><span data-stu-id="46bc5-291">BizTalk Server requires SQL Server.</span></span> <span data-ttu-id="46bc5-292">SQL Server peut être installé sur le même ordinateur que BizTalk ou sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="46bc5-292">SQL Server can be installed on the same computer as BizTalk, or on a different computer.</span></span> <span data-ttu-id="46bc5-293">La plupart des environnements de production installent BizTalk et SQL sur des serveurs distincts.</span><span class="sxs-lookup"><span data-stu-id="46bc5-293">Most production environments install BizTalk and SQL on separate servers.</span></span> 

> [!IMPORTANT]
> - <span data-ttu-id="46bc5-294">SQL Server Express Edition n’est pas recommandé ou pris en charge.</span><span class="sxs-lookup"><span data-stu-id="46bc5-294">SQL Server Express Edition is not recommended or supported.</span></span> <span data-ttu-id="46bc5-295">Cette édition n'inclut pas certaines fonctionnalités requises par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="46bc5-295">The Express edition does not include certain features needed by BizTalk Server.</span></span>
> - <span data-ttu-id="46bc5-296">BizTalk Server prend en charge l’édition SQL Standard.</span><span class="sxs-lookup"><span data-stu-id="46bc5-296">BizTalk Server supports SQL Standard Edition.</span></span> <span data-ttu-id="46bc5-297">Toutefois, pour pouvoir utiliser l’agrégation en temps réel (RTA) de Business Activity Monitoring, installez SQL Server Enterprise Edition.</span><span class="sxs-lookup"><span data-stu-id="46bc5-297">However, to use Business Activity Monitoring real-time aggregation (BAM RTA), install SQL Server Enterprise Edition.</span></span> <span data-ttu-id="46bc5-298">L’agrégation en temps réel (RTA) de BAM n’est pas prise en charge dans SQL Server Standard Edition.</span><span class="sxs-lookup"><span data-stu-id="46bc5-298">BAM real-time aggregation (RTA) is not supported in the Standard Edition of SQL Server.</span></span>
> - <span data-ttu-id="46bc5-299">Pour utiliser pleinement le kit SDK BizTalk Server ou déployer des applications BizTalk Server à partir de Visual Studio, installez les outils de développement SQL Server.</span><span class="sxs-lookup"><span data-stu-id="46bc5-299">To fully use the BizTalk Server SDK or deploy BizTalk Server applications from a Visual Studio, install the SQL Server Development Tools.</span></span>
> - <span data-ttu-id="46bc5-300">BizTalk Server prend en charge tous les classements SQL Server qui respectent la casse et qui ne la respectent pas, à l’exception des classements binaires.</span><span class="sxs-lookup"><span data-stu-id="46bc5-300">BizTalk Server supports all case-sensitive and case-insensitive SQL Server collations except for binary collations.</span></span> <span data-ttu-id="46bc5-301">Les classements binaires ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="46bc5-301">Binary collations are not supported.</span></span>

<span data-ttu-id="46bc5-302">**Pour les étapes d’installation spécifiques, consultez** [installer SQL Server 2016](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup) ou [installer SQL Server 2014](https://msdn.microsoft.com/library/bb500469(v=sql.120).aspx).</span><span class="sxs-lookup"><span data-stu-id="46bc5-302">**For specific install steps, see** [Install SQL Server 2016](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup) or [Install SQL Server 2014](https://msdn.microsoft.com/library/bb500469(v=sql.120).aspx).</span></span>

1. <span data-ttu-id="46bc5-303">Démarrez l’installation de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="46bc5-303">Start the SQL Server installation.</span></span> 
2. <span data-ttu-id="46bc5-304">Durant la configuration des fonctionnalités, sélectionnez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="46bc5-304">During the Feature setup, select the following:</span></span>
    - <span data-ttu-id="46bc5-305">Services Moteur de base de données</span><span class="sxs-lookup"><span data-stu-id="46bc5-305">Database Engine Services</span></span>
        - <span data-ttu-id="46bc5-306">Réplication SQL Server</span><span class="sxs-lookup"><span data-stu-id="46bc5-306">SQL Server Replication</span></span>
        - <span data-ttu-id="46bc5-307">R Services (de-de base de données) (**facultatif**; info à [SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services))</span><span class="sxs-lookup"><span data-stu-id="46bc5-307">R Services (in-Database) (**optional**; info at [SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services))</span></span>
        - <span data-ttu-id="46bc5-308">Extraction en texte intégral et extraction sémantique de recherche</span><span class="sxs-lookup"><span data-stu-id="46bc5-308">Full-Text and Semantic Extractions for Search</span></span>
    - <span data-ttu-id="46bc5-309">Analysis Services</span><span class="sxs-lookup"><span data-stu-id="46bc5-309">Analysis Services</span></span>
    - <span data-ttu-id="46bc5-310">Reporting Services - Natif</span><span class="sxs-lookup"><span data-stu-id="46bc5-310">Reporting Services - Native</span></span>
    - <span data-ttu-id="46bc5-311">Fonctionnalités partagées</span><span class="sxs-lookup"><span data-stu-id="46bc5-311">Shared Features</span></span>
        - <span data-ttu-id="46bc5-312">Connectivité des outils clients</span><span class="sxs-lookup"><span data-stu-id="46bc5-312">Client Tools Connectivity</span></span>
        - <span data-ttu-id="46bc5-313">Integration Services</span><span class="sxs-lookup"><span data-stu-id="46bc5-313">Integration Services</span></span>

    > [!NOTE]
    > <span data-ttu-id="46bc5-314">**SQL Server Data Tools** n’est pas inclus dans l’installation par défaut de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="46bc5-314">**SQL Server Data Tools** is not included in the default installation of SQL Server.</span></span> <span data-ttu-id="46bc5-315">Il n’est pas obligatoire, mais peut être téléchargé dans [Télécharger SSDT (SQL Server Data Tools)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).</span><span class="sxs-lookup"><span data-stu-id="46bc5-315">It is not required, but can be downloaded at [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).</span></span> <span data-ttu-id="46bc5-316">Téléchargez [**SQL Server Management Studio (SSMS)**](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) qui fonctionne avec toutes les versions prises en charge de SQL Server, y compris la base de données SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="46bc5-316">Download [**SQL Server Management Studio (SSMS)**](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) that works with all supported versions of SQL Server, including Azure SQL Database.</span></span> 

3. <span data-ttu-id="46bc5-317">Poursuivez l’installation et redémarrez l’ordinateur si vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="46bc5-317">Continue with the installation, and restart the computer if prompted.</span></span>

## <a name="disable-shared-memory"></a><span data-ttu-id="46bc5-318">Désactivez la mémoire partagée</span><span class="sxs-lookup"><span data-stu-id="46bc5-318">Disable Shared Memory</span></span>

1. <span data-ttu-id="46bc5-319">Ouvrez le **Gestionnaire de configuration SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-319">Open **SQL Server Configuration Manager**.</span></span>
2. <span data-ttu-id="46bc5-320">Dans le Gestionnaire de Configuration SQL Server, développez **Configuration du réseau SQL Server**, puis sélectionnez **protocoles pour MSSQLSERVER**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-320">In SQL Server Configuration Manager, expand **SQL Server Network Configuration**, and then select **Protocols for MSSQLSERVER**.</span></span>
3. <span data-ttu-id="46bc5-321">Cliquez avec le bouton droit sur **Mémoire partagée**, puis sélectionnez **Désactiver**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-321">Right-click **Shared Memory**, and then select **Disable**.</span></span>
4. <span data-ttu-id="46bc5-322">Sélectionnez **SQL Server Services**, avec le bouton droit SQL **Server (MSSQLSERVER)**, puis sélectionnez **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-322">Select **SQL Server Services**, right-click SQL **Server (MSSQLSERVER)**, and then select **Stop**.</span></span> <span data-ttu-id="46bc5-323">Une fois le service arrêté, cliquez sur **SQL Server (MSSQLSERVER)**, puis sélectionnez **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-323">After the service has stopped, right-click **SQL Server (MSSQLSERVER)**, and then select **Start**.</span></span>
5. <span data-ttu-id="46bc5-324">Fermez le **Gestionnaire de configuration SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-324">Close **SQL Server Configuration Manager**.</span></span>

<span data-ttu-id="46bc5-325">En règle générale, le protocole de mémoire partagée affecte uniquement les clients (BizTalk Server) qui sont installés sur le même ordinateur que SQL Server.</span><span class="sxs-lookup"><span data-stu-id="46bc5-325">Typically, the Shared Memory protocol only impacts clients (BizTalk Server) that are installed on the same computer as SQL Server.</span></span> <span data-ttu-id="46bc5-326">Dans certains cas de surcharge (comme des clients accédant à SQL Server à partir d'un seul ordinateur), il est possible que le protocole de mémoire partagée pour SQL Server diminue les performances de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="46bc5-326">Under certain stress conditions (such as clients accessing SQL Server from the same computer), the SQL Server Shared Memory protocol may lower BizTalk Server performance.</span></span> <span data-ttu-id="46bc5-327">La désactivation du protocole réseau de mémoire partagée pour résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="46bc5-327">Disabling the Shared Memory network protocol resolves this.</span></span>

> [!TIP]
> <span data-ttu-id="46bc5-328">Si l’Agent SQL Server ne parvient pas à démarrer après la désactivation de mémoire partagée, puis confirmez [ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) est installé.</span><span class="sxs-lookup"><span data-stu-id="46bc5-328">If SQL Server Agent fails to start after disabling Shared Memory, then confirm [ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) is installed.</span></span>

## <a name="install-sql-xml-4"></a><span data-ttu-id="46bc5-329">Installation de SQL XML 4</span><span class="sxs-lookup"><span data-stu-id="46bc5-329">Install SQL XML 4</span></span>
<span data-ttu-id="46bc5-330">Requis pour le moteur d’exécution BizTalk Server, les outils d’administration et l’analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="46bc5-330">Required for BizTalk Server Runtime, Administrative Tools, and BAM.</span></span> 

<span data-ttu-id="46bc5-331">Téléchargez et installez [SqlXml 4.0](https://www.microsoft.com/download/details.aspx?id=30403).</span><span class="sxs-lookup"><span data-stu-id="46bc5-331">Download and install [SqlXml 4.0](https://www.microsoft.com/download/details.aspx?id=30403).</span></span>

## <a name="configure-sql-database-mail-optional"></a><span data-ttu-id="46bc5-332">Configurer la messagerie de base de données SQL (facultatif)</span><span class="sxs-lookup"><span data-stu-id="46bc5-332">Configure SQL Database Mail (optional)</span></span>
<span data-ttu-id="46bc5-333">Si vous utilisez des alertes BAM, BizTalk Server requiert la messagerie de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="46bc5-333">If you use BAM Alerts, BizTalk Server requires SQL Server Database Mail.</span></span> <span data-ttu-id="46bc5-334">Si vous n’utilisez pas les alertes BAM, ignorez cette section.</span><span class="sxs-lookup"><span data-stu-id="46bc5-334">If you don't use BAM Alerts, then skip this section.</span></span> 

<span data-ttu-id="46bc5-335">**VOIR AUSSI** : Informations complémentaires sur la [messagerie de base de données](https://docs.microsoft.com/sql/relational-databases/database-mail/database-mail).</span><span class="sxs-lookup"><span data-stu-id="46bc5-335">**SEE ALSO** : More on [Database Mail](https://docs.microsoft.com/sql/relational-databases/database-mail/database-mail).</span></span>

> [!IMPORTANT]
> - <span data-ttu-id="46bc5-336">Vous devez connaître le nom de serveur et le numéro de port TCP du serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="46bc5-336">You need to know the server name and TCP port number for the SMTP Server.</span></span> <span data-ttu-id="46bc5-337">Si vous avez installé IIS et le serveur SMTP sur cet ordinateur, vous utilisez le serveur SMTP local.</span><span class="sxs-lookup"><span data-stu-id="46bc5-337">If you installed IIS and SMTP Server on this same computer, then you use the local SMTP Server.</span></span> <span data-ttu-id="46bc5-338">Si le serveur SMTP nécessite une authentification, préparez le nom d’utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="46bc5-338">If the SMTP server requires authentication, then have the user name and password ready.</span></span>
> - <span data-ttu-id="46bc5-339">Le portail BAM et les alertes BAM sont des fonctionnalités distinctes.</span><span class="sxs-lookup"><span data-stu-id="46bc5-339">The BAM portal and BAM Alerts are separate features.</span></span> <span data-ttu-id="46bc5-340">Si vous utilisez des alertes BAM, la messagerie de base de données SQL Server est requise.</span><span class="sxs-lookup"><span data-stu-id="46bc5-340">If you are using BAM Alerts, then SQL Server Database Mail is required.</span></span> <span data-ttu-id="46bc5-341">Si vous n’utilisez pas les alertes BAM, la messagerie de base de données SQL Server n’est pas requise.</span><span class="sxs-lookup"><span data-stu-id="46bc5-341">If you are not using BAM Alerts, then SQL Server Database Mail is not required.</span></span>

<span data-ttu-id="46bc5-342">**Pour les étapes de configuration spécifiques, consultez**: configurer [messagerie de base de données SQL Server 2016](https://docs.microsoft.com/sql/relational-databases/database-mail/configure-database-mail) ou [messagerie de base de données SQL Server 2014](https://msdn.microsoft.com/library/hh245116(v=sql.120).aspx).</span><span class="sxs-lookup"><span data-stu-id="46bc5-342">**For specific configuration steps, see**: Configure [SQL Server 2016 Database Mail](https://docs.microsoft.com/sql/relational-databases/database-mail/configure-database-mail) or [SQL Server 2014 Database Mail](https://msdn.microsoft.com/library/hh245116(v=sql.120).aspx).</span></span>

   
<span data-ttu-id="46bc5-343">Pour envoyer un e-mail de test :</span><span class="sxs-lookup"><span data-stu-id="46bc5-343">To send a test email:</span></span> 
1.  <span data-ttu-id="46bc5-344">Cliquez avec le bouton droit sur **Messagerie de base de données** et sélectionnez **Envoyer un message électronique de test**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-344">Right-click **Database Mail**, and select **Send Test E-Mail**.</span></span> 
2.  <span data-ttu-id="46bc5-345">Entrez une adresse e-mail **À :**, puis sélectionnez **Envoyer un message électronique de test**.</span><span class="sxs-lookup"><span data-stu-id="46bc5-345">Enter a **To:** email address, and select **Send Test E-Mail**.</span></span>  
 
<span data-ttu-id="46bc5-346">Si le destinataire **À :** a reçu l’e-mail, la messagerie de base de données est configurée.</span><span class="sxs-lookup"><span data-stu-id="46bc5-346">If the **To:** recipient receives the email, then Database Mail is configured.</span></span> 

## <a name="install-winscp-optional"></a><span data-ttu-id="46bc5-347">Installer WinSCP (facultatif)</span><span class="sxs-lookup"><span data-stu-id="46bc5-347">Install WinSCP (optional)</span></span>
<span data-ttu-id="46bc5-348">Requis par l’adaptateur FTP.</span><span class="sxs-lookup"><span data-stu-id="46bc5-348">Required by the FTP adapter.</span></span> <span data-ttu-id="46bc5-349">Si vous n’utilisez pas l’adaptateur FTP, ignorez cette section.</span><span class="sxs-lookup"><span data-stu-id="46bc5-349">If you don't use the FTP adapter, then skip this section.</span></span> 

<span data-ttu-id="46bc5-350">Téléchargez et installez [WinSCP](http://winscp.net).</span><span class="sxs-lookup"><span data-stu-id="46bc5-350">Download and install [WinSCP](http://winscp.net).</span></span> 

## <a name="next-step"></a><span data-ttu-id="46bc5-351">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="46bc5-351">Next step</span></span>
<span data-ttu-id="46bc5-352">Installez [BizTalk Server 2016](../install-and-config-guides/install-biztalk-server-2016.md).</span><span class="sxs-lookup"><span data-stu-id="46bc5-352">Install [BizTalk Server 2016](../install-and-config-guides/install-biztalk-server-2016.md).</span></span>

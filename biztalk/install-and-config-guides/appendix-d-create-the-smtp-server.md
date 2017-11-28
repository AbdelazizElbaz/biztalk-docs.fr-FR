---
title: "Annexe d : création d’un serveur SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7441ba9-a498-42ec-a04d-7f2731407373
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f4d4acc35f5cb38be5f783ee7c4017c8ada83e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="appendix-d-create-the-smtp-server"></a><span data-ttu-id="be186-102">Annexe D : Création du serveur SMTP</span><span class="sxs-lookup"><span data-stu-id="be186-102">Appendix D: Create the SMTP Server</span></span>
<span data-ttu-id="be186-103">Créez le serveur SMTP qu’utilisera la messagerie de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="be186-103">Create the SMTP Server used by SQL Server Database Mail.</span></span>  
  
<span data-ttu-id="be186-104">La messagerie de base de données SQL Server est requise pour configurer des alertes BAM lorsque vous utilisez l’une des versions SQL suivantes :</span><span class="sxs-lookup"><span data-stu-id="be186-104">SQL Server Database Mail is required to configure BAM Alerts when using any of the following SQL versions:</span></span> 

* [!INCLUDE[sqlserver2016_md](../includes/sqlserver2016-md.md)]
* [!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)]
* [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] 
  
 <span data-ttu-id="be186-105">La fonctionnalité Messagerie de base de données SQL Server utilise un serveur SMTP pour envoyer les alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="be186-105">SQL Server Database Mail uses an SMTP Server to send BAM Alerts.</span></span> <span data-ttu-id="be186-106">SMTP Server est inclus avec Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="be186-106">SMTP Server is included with Internet Information Services (IIS).</span></span> <span data-ttu-id="be186-107">SMTP peut être installé localement sur un serveur BizTalk Server ou un autre serveur avec IIS installé.</span><span class="sxs-lookup"><span data-stu-id="be186-107">SMTP can be installed locally on the BizTalk Server or on another server with IIS installed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="be186-108">En règle générale, les systèmes d’exploitation clients tels que Windows 10, Windows 7, etc., n’incluent pas de fonctionnalités de serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="be186-108">Typically, client operating systems like Windows 10, Windows 7, and so on, do not include SMTP Server capabilities.</span></span> <span data-ttu-id="be186-109">Vous pouvez vous connecter à un serveur SMTP existant sur ​​un serveur Windows Server à l’aide de la fonctionnalité *Courrier électronique SMTP* dans IIS.</span><span class="sxs-lookup"><span data-stu-id="be186-109">You can connect to an existing SMTP Server on a Windows Server using the *SMTP E-mail* feature within IIS.</span></span> <span data-ttu-id="be186-110">La fonctionnalité *Courrier électronique SMTP* ne correspond PAS à un serveur SMTP, lequel est nécessaire pour la messagerie de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="be186-110">The *SMTP E-mail* feature is NOT an SMTP Server, which is required for SQL Server Database Mail.</span></span> <span data-ttu-id="be186-111">En conséquence, cette rubrique ne comprend pas les étapes pour installer et configurer un serveur SMTP sur des systèmes d’exploitation clients.</span><span class="sxs-lookup"><span data-stu-id="be186-111">As a result, this topic does not include the steps to install and configure an SMTP Server on client operating systems.</span></span>  

## <a name="install-and-configure-the-smtp-server"></a><span data-ttu-id="be186-112">Installation et configuration du serveur SMTP</span><span class="sxs-lookup"><span data-stu-id="be186-112">Install and configure the SMTP server</span></span>  
  
<span data-ttu-id="be186-113">Ces procédures s’appliquent à :</span><span class="sxs-lookup"><span data-stu-id="be186-113">These steps apply to:</span></span>

* <span data-ttu-id="be186-114">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="be186-114">Windows Server 2016</span></span>
* <span data-ttu-id="be186-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="be186-115">Windows Server 2012 R2</span></span>
* <span data-ttu-id="be186-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="be186-116">Windows Server 2012</span></span>
  
### <a name="install-smtp-server"></a><span data-ttu-id="be186-117">Installer un serveur SMTP</span><span class="sxs-lookup"><span data-stu-id="be186-117">Install SMTP Server</span></span>  
   
1.  <span data-ttu-id="be186-118">Dans le **Gestionnaire de serveur**, sélectionnez **Tableau de bord** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="be186-118">In **Server Manager**, select **Dashboard** in the left pane.</span></span>  
  
3.  <span data-ttu-id="be186-119">Sélectionnez **Ajouter des rôles et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="be186-119">Select **Add roles and features**.</span></span> <span data-ttu-id="be186-120">Vous pouvez aussi ouvrir **Ajouter des rôles et fonctionnalités** à partir du menu **Gérer** en haut à droite.</span><span class="sxs-lookup"><span data-stu-id="be186-120">**Add Roles and Features** can also be opened from the **Manage** menu in the top right-hand corner.</span></span>  
  
4.  <span data-ttu-id="be186-121">Dans **Avant de commencer**, sélectionnez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="be186-121">In **Before You Begin**, select **Next**.</span></span>  
  
5.  <span data-ttu-id="be186-122">Sélectionnez **Installation basée sur un rôle ou une fonctionnalité**, puis **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="be186-122">Select **Role-based or feature-based installation**, and select **Next**.</span></span>  
  
6.  <span data-ttu-id="be186-123">Sélectionnez successivement **Sélectionner un serveur du pool de serveurs**, le serveur souhaité et **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="be186-123">Select **Select a server from the server pool**, select the desired server, and select **Next**.</span></span> <span data-ttu-id="be186-124">La fenêtre **Sélection du serveur** répertorie les serveurs qui ont été ajoutés avec **Ajouter un serveur** dans le **Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="be186-124">The **Server Selection** window lists the servers that have been added using **Add Server** in **Server Manager**.</span></span> <span data-ttu-id="be186-125">Le serveur local est sélectionné par défaut.</span><span class="sxs-lookup"><span data-stu-id="be186-125">By default, it selects the local server.</span></span>  
  
7.  <span data-ttu-id="be186-126">Dans **Rôles du serveur**, sélectionnez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="be186-126">In **Server Roles**, select **Next**.</span></span>  
  
8.  <span data-ttu-id="be186-127">Dans **Fonctionnalités**, cochez **Serveur SMTP**.</span><span class="sxs-lookup"><span data-stu-id="be186-127">In **Features**, check **SMTP Server**.</span></span> <span data-ttu-id="be186-128">Si vous y êtes invité, sélectionnez **Ajouter des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="be186-128">If prompted, select **Add Features**.</span></span> <span data-ttu-id="be186-129">Sélectionnez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="be186-129">Select **Next**.</span></span>  
  
9. <span data-ttu-id="be186-130">Dans **Confirmation**, sélectionnez **Redémarrer automatiquement le serveur de destination, si nécessaire**, puis sélectionnez **Installer**.</span><span class="sxs-lookup"><span data-stu-id="be186-130">In **Confirmation**, select **Restart the destination server automatically if required**, and select **Install**.</span></span> <span data-ttu-id="be186-131">Lorsque vous avez terminé, sélectionnez **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="be186-131">When complete, select **Close**.</span></span>  

### <a name="configure-the-smtp-server"></a><span data-ttu-id="be186-132">Configurer le serveur SMTP</span><span class="sxs-lookup"><span data-stu-id="be186-132">Configure the SMTP Server</span></span>  
 <span data-ttu-id="be186-133">La procédure suivante permet de configurer le serveur virtuel SMTP à l'aide du Gestionnaire des services Internet (IIS) 6.0 :</span><span class="sxs-lookup"><span data-stu-id="be186-133">The following steps configure the SMTP Virtual Server using the IIS 6.0 Manager:</span></span>  
  
1.  <span data-ttu-id="be186-134">Ouvrez le Gestionnaire des services Internet. Dans Démarrer, recherchez **inetmgr6.exe** et ouvrez-le.</span><span class="sxs-lookup"><span data-stu-id="be186-134">Open the IIS Manager: In Start, search for **inetmgr6.exe**, and open it.</span></span>  
  
2.  <span data-ttu-id="be186-135">Développez le nom d'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="be186-135">Expand the computer name.</span></span> <span data-ttu-id="be186-136">Cliquez avec le bouton droit sur **[Serveur virtuel SMTP n°1]** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="be186-136">Right-click **[SMTP Virtual Server #1]**, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="be186-137">Dans l’onglet **Accès**, sélectionnez le bouton **Relais**.</span><span class="sxs-lookup"><span data-stu-id="be186-137">In the **Access** tab, select the **Relay** button.</span></span>  
  
4.  <span data-ttu-id="be186-138">Sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="be186-138">Select **Add**.</span></span> <span data-ttu-id="be186-139">Pour **Ordinateur unique**, entrez `127.0.0.1`, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="be186-139">For **Single Computer**, enter `127.0.0.1`, and select **OK**.</span></span>  
  
     <span data-ttu-id="be186-140">En ajoutant 127.0.0.1, nous autorisons le serveur local à envoyer des messages à partir du serveur local SMTP.</span><span class="sxs-lookup"><span data-stu-id="be186-140">By adding 127.0.0.1, we are allowing the local server to send messages from this SMTP Server.</span></span> <span data-ttu-id="be186-141">Si vous voulez que d'autres ordinateurs envoient des messages à partir de ce serveur SMTP, entrez leurs adresses IP.</span><span class="sxs-lookup"><span data-stu-id="be186-141">If you want additional computers to send messages from this SMTP server, enter their IP addresses.</span></span>  
  
5.  <span data-ttu-id="be186-142">Sous l’onglet **Remise**, sélectionnez **Sécurité sortante**.</span><span class="sxs-lookup"><span data-stu-id="be186-142">In the **Delivery** tab, select **Outbound Security**.</span></span> <span data-ttu-id="be186-143">Choisissez parmi les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="be186-143">Choose from the following:</span></span>  
  
     <span data-ttu-id="be186-144">**Accès anonyme** : Un nom de compte ou mot de passe n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="be186-144">**Anonymous access**: An account name or password is not required.</span></span> <span data-ttu-id="be186-145">Cette option désactive l'authentification du serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="be186-145">This option disables authentication for the SMTP Server.</span></span>  
  
     <span data-ttu-id="be186-146">**Authentification de base** : Le nom de compte et le mot de passe du serveur auquel vous vous connectez sont envoyés en texte clair.</span><span class="sxs-lookup"><span data-stu-id="be186-146">**Basic authentication**: The account name and password of the server that you are connecting to are sent as clear text.</span></span> <span data-ttu-id="be186-147">Le compte que vous entrez transmet les e-mails.</span><span class="sxs-lookup"><span data-stu-id="be186-147">This account you enter transmits the e-mails.</span></span> <span data-ttu-id="be186-148">L'authentification de base peut être sélectionnée lors de l'envoi d'un e-mail à un compte personnel ou un compte Exchange.</span><span class="sxs-lookup"><span data-stu-id="be186-148">Basic Authentication can be selected when sending e-mail to a personal account or an Exchange account.</span></span> <span data-ttu-id="be186-149">Parce que les informations d’identification sont transmises en texte clair, il est recommandé d’activer le **chiffrement TLS**.</span><span class="sxs-lookup"><span data-stu-id="be186-149">Because the credentials are passed in clear text, it is recommended to enable **TLS encryption**.</span></span>  
  
     <span data-ttu-id="be186-150">**Authentification Windows intégrée** : Le nom du compte de domaine Windows et le mot de passe sont utilisés à des fins d’authentification.</span><span class="sxs-lookup"><span data-stu-id="be186-150">**Integrated Windows Authentication**: The Windows domain account name and password are used to authenticate.</span></span> <span data-ttu-id="be186-151">Le compte que vous entrez transmet les e-mails.</span><span class="sxs-lookup"><span data-stu-id="be186-151">The account you enter transmits the e-mails.</span></span>  
  
     <span data-ttu-id="be186-152">**Chiffrement TLS** : De façon similaire à SSL, TLS sécurise la connexion.</span><span class="sxs-lookup"><span data-stu-id="be186-152">**TLS encryption**: Similar to SSL, TLS secures the connection.</span></span> <span data-ttu-id="be186-153">Nécessite un certificat de serveur SSL valide installé sur ce serveur.</span><span class="sxs-lookup"><span data-stu-id="be186-153">Requires a valid SSL server certificate installed on this server.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="be186-154">Pour tester les fonctionnalités SMTP de base avec un compte e-mail personnel, y compris un compte Exchange, sélectionnez **Accès anonyme**.</span><span class="sxs-lookup"><span data-stu-id="be186-154">To test core SMTP functionality with a personal e-mail account, including an Exchange account, select **Anonymous access**.</span></span> <span data-ttu-id="be186-155">Lorsque l'authentification de base est sélectionnée, SMTP utilise la commande AUTH.</span><span class="sxs-lookup"><span data-stu-id="be186-155">When Basic authentication is selected, SMTP uses the AUTH command.</span></span> <span data-ttu-id="be186-156">Certains fournisseurs de messagerie peuvent échouer en raison de la commande AUTH.</span><span class="sxs-lookup"><span data-stu-id="be186-156">Some e-mail providers may fail because of the AUTH command.</span></span> <span data-ttu-id="be186-157">Si la commande AUTH échoue, une erreur peut être consignée dans les journaux d'événements Windows sur le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="be186-157">If the AUTH command fails, an error may be logged in the Windows event logs on the SMTP Server.</span></span>  
  
6.  <span data-ttu-id="be186-158">Sous l’onglet **Remise**, sélectionnez **Connexions sortantes**.</span><span class="sxs-lookup"><span data-stu-id="be186-158">In the **Delivery** tab, select **Outbound connections**.</span></span> <span data-ttu-id="be186-159">Le port TCP 25 est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="be186-159">By default, the TCP Port is 25.</span></span> <span data-ttu-id="be186-160">Il est possible d’entrer un autre port s’il est ouvert dans le pare-feu.</span><span class="sxs-lookup"><span data-stu-id="be186-160">A different port can be entered if it is open within your firewall.</span></span> <span data-ttu-id="be186-161">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="be186-161">Select **OK**.</span></span>  
  
7.  <span data-ttu-id="be186-162">Sous l’onglet **Remise**, sélectionnez **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="be186-162">In the **Delivery** tab, select **Advanced**.</span></span> <span data-ttu-id="be186-163">Par défaut, le **nom de domaine complet** du serveur local est répertorié.</span><span class="sxs-lookup"><span data-stu-id="be186-163">By default, the **Fully Qualified Domain Name** of the local server is listed.</span></span> <span data-ttu-id="be186-164">Selon votre fournisseur d’accès Internet, la propriété **Hôte actif** peut rester vide.</span><span class="sxs-lookup"><span data-stu-id="be186-164">Depending on the internet provider, the **Smart Host** property can remain empty.</span></span> <span data-ttu-id="be186-165">Vous pouvez avoir besoin de contacter le fournisseur d'accès Internet pour vérifier si un hôte actif (Smart Host) est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="be186-165">You may need to contact the internet provider to confirm if a Smart Host is required.</span></span> <span data-ttu-id="be186-166">Sinon, vous pourriez être en mesure d’entrer smtp.*EMailProvider*.com.</span><span class="sxs-lookup"><span data-stu-id="be186-166">Otherwise, you may be able to enter smtp.*EMailProvider*.com.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be186-167">Un **hôte actif** est un serveur dédié utilisé par un serveur Exchange pour acheminer tous les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="be186-167">A **Smart Host**, also known as a relay host, is a dedicated server used by an Exchange Server to route all outgoing messages.</span></span> <span data-ttu-id="be186-168">Quand l’**hôte actif** reçoit les messages, il les transfère vers un domaine distant.</span><span class="sxs-lookup"><span data-stu-id="be186-168">When the **Smart Host** receives the messages, the **Smart Host** forwards the messages to a remote domain.</span></span> <span data-ttu-id="be186-169">L’objectif d’un **hôte actif** est d’améliorer les performances d’un serveur Exchange.</span><span class="sxs-lookup"><span data-stu-id="be186-169">The goal of a **Smart Host** is to improve performance of an Exchange Server.</span></span> <span data-ttu-id="be186-170">Le serveur Exchange Server transmet uniquement l'hôte actif ; il ne contacte pas de façon répétée le domaine distant jusqu'à ce qu'une connexion soit établie.</span><span class="sxs-lookup"><span data-stu-id="be186-170">The Exchange Server only transmits to the smart host; instead of repeatedly contacting the remote domain until a connection is made.</span></span>  
  
8.  <span data-ttu-id="be186-171">Sélectionnez **OK** pour fermer toutes les fenêtres.</span><span class="sxs-lookup"><span data-stu-id="be186-171">Select **OK** to close all windows.</span></span>  
  
9. <span data-ttu-id="be186-172">Redémarrez le serveur SMTP : cliquez avec le bouton droit sur **[Serveur virtuel SMTP n°1]**, sélectionnez **Arrêter**, puis sélectionnez **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="be186-172">Restart the SMTP Server: Right-click **[SMTP Virtual Server #1]**, select **Stop**, and then select **Start**.</span></span> <span data-ttu-id="be186-173">Un redémarrage est nécessaire pour appliquer les paramètres du serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="be186-173">A restart is needed to apply the SMTP Server settings.</span></span> 

  
## <a name="windows-server-2008-r2-install-and-configure-smtp-server"></a><span data-ttu-id="be186-174">Windows Server 2008 R2 : Installation et configuration d’un serveur SMTP</span><span class="sxs-lookup"><span data-stu-id="be186-174">Windows Server 2008 R2: Install and Configure SMTP Server</span></span>  
  
### <a name="install-smtp-server"></a><span data-ttu-id="be186-175">Installer un serveur SMTP</span><span class="sxs-lookup"><span data-stu-id="be186-175">Install SMTP Server</span></span>  
 <span data-ttu-id="be186-176">La procédure suivante permet d'installer le composant Serveur SMTP :</span><span class="sxs-lookup"><span data-stu-id="be186-176">The following steps install the SMTP Server feature:</span></span>  
  
1.  <span data-ttu-id="be186-177">Dans le **Gestionnaire de serveur**, sélectionnez **Fonctionnalités**, puis **Ajouter des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="be186-177">In **Server Manager**, select **Features**, and select **Add Features**.</span></span>  
  
3.  <span data-ttu-id="be186-178">Dans **Ajouter des fonctionnalités**, sélectionnez **Serveur SMTP**.</span><span class="sxs-lookup"><span data-stu-id="be186-178">In **Add Features**, select **SMTP Server**.</span></span> <span data-ttu-id="be186-179">Si vous y êtes invité, sélectionnez **Ajouter les services de rôle requis**, puis **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="be186-179">If prompted, select **Add Required Role Services**, and select **Next**.</span></span>  
  
4.  <span data-ttu-id="be186-180">Poursuivez l’installation en sélectionnant **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="be186-180">Continue with the installation by selecting **Next**.</span></span>  
  
5.  <span data-ttu-id="be186-181">Dans la fenêtre **Confirmer les sélections d’installation**, sélectionnez **Installer**.</span><span class="sxs-lookup"><span data-stu-id="be186-181">In the **Confirm Installation Selections** window, select **Install**.</span></span> <span data-ttu-id="be186-182">Lorsque vous avez terminé, sélectionnez **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="be186-182">When complete, select **Close**.</span></span>  
  
### <a name="configure-the-smtp-server"></a><span data-ttu-id="be186-183">Configurer le serveur SMTP</span><span class="sxs-lookup"><span data-stu-id="be186-183">Configure the SMTP Server</span></span>  
 <span data-ttu-id="be186-184">La procédure suivante permet de configurer le serveur virtuel SMTP à l'aide du Gestionnaire des services Internet (IIS) 6.0 :</span><span class="sxs-lookup"><span data-stu-id="be186-184">The following steps configure the SMTP Virtual Server using the IIS 6.0 Manager:</span></span>  
  
1.  <span data-ttu-id="be186-185">Ouvrez le Gestionnaire IIS 6.0 : Dans **Démarrer**, recherchez **IIS** et sélectionnez **Gestionnaire des services Internet (IIS) 6.0**.</span><span class="sxs-lookup"><span data-stu-id="be186-185">Open the IIS 6.0 Manager: In **Start**, search for **IIS**, and select **Internet Information Services (IIS) 6.0 Manager**.</span></span>  
  
2.  <span data-ttu-id="be186-186">Développez le nom d'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="be186-186">Expand the computer name.</span></span> <span data-ttu-id="be186-187">Cliquez avec le bouton droit sur **[Serveur virtuel SMTP n°1]** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="be186-187">Right-click **[SMTP Virtual Server #1]**, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="be186-188">Dans l’onglet **Accès**, sélectionnez le bouton **Relais**.</span><span class="sxs-lookup"><span data-stu-id="be186-188">In the **Access** tab, select the **Relay** button.</span></span>  
  
4.  <span data-ttu-id="be186-189">Sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="be186-189">Select **Add**.</span></span> <span data-ttu-id="be186-190">Pour **Ordinateur unique**, entrez `127.0.0.1`, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="be186-190">For **Single Computer**, enter `127.0.0.1`, and select **OK**.</span></span>  
  
     <span data-ttu-id="be186-191">En ajoutant 127.0.0.1, nous autorisons le serveur local à envoyer des messages à partir du serveur local SMTP.</span><span class="sxs-lookup"><span data-stu-id="be186-191">By adding 127.0.0.1, we are allowing the local server to send messages from this SMTP Server.</span></span> <span data-ttu-id="be186-192">Si vous voulez que d'autres ordinateurs envoient des messages à partir de ce serveur SMTP, entrez leurs adresses IP.</span><span class="sxs-lookup"><span data-stu-id="be186-192">If you want additional computers to send messages from this SMTP server, enter their IP addresses.</span></span>  
  
5.  <span data-ttu-id="be186-193">Sous l’onglet **Remise**, sélectionnez **Sécurité sortante**.</span><span class="sxs-lookup"><span data-stu-id="be186-193">In the **Delivery** tab, select **Outbound Security**.</span></span> <span data-ttu-id="be186-194">Choisissez parmi les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="be186-194">Choose from the following:</span></span>  
  
     <span data-ttu-id="be186-195">**Accès anonyme** : Un nom de compte ou mot de passe n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="be186-195">**Anonymous access**: An account name or password is not required.</span></span> <span data-ttu-id="be186-196">Cette option désactive l'authentification du serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="be186-196">This option disables authentication for the SMTP Server.</span></span>  
  
     <span data-ttu-id="be186-197">**Authentification de base** : Le nom de compte et le mot de passe du serveur auquel vous vous connectez sont envoyés en texte clair.</span><span class="sxs-lookup"><span data-stu-id="be186-197">**Basic authentication**: The account name and password of the server that you are connecting to are sent as clear text.</span></span> <span data-ttu-id="be186-198">L'authentification de base peut être sélectionnée lors de l'envoi d'un e-mail à un compte personnel ou un compte Exchange.</span><span class="sxs-lookup"><span data-stu-id="be186-198">Basic Authentication can be selected when sending e-mail to a personal account or an Exchange account.</span></span> <span data-ttu-id="be186-199">Parce que les informations d’identification sont transmises en texte clair, il est recommandé d’activer le **chiffrement TLS**.</span><span class="sxs-lookup"><span data-stu-id="be186-199">Because the credentials are passed in clear text, it is recommended to enable **TLS encryption**.</span></span>  
  
     <span data-ttu-id="be186-200">**Authentification Windows intégrée** : Le nom du compte de domaine Windows et le mot de passe sont utilisés à des fins d’authentification.</span><span class="sxs-lookup"><span data-stu-id="be186-200">**Integrated Windows Authentication**: The Windows domain account name and password are used to authenticate.</span></span> <span data-ttu-id="be186-201">Le compte que vous entrez transmet les e-mails.</span><span class="sxs-lookup"><span data-stu-id="be186-201">The account you enter transmits the e-mails.</span></span>  
  
     <span data-ttu-id="be186-202">**Chiffrement TLS** : De façon similaire à SSL, TLS sécurise la connexion.</span><span class="sxs-lookup"><span data-stu-id="be186-202">**TLS encryption**: Similar to SSL, TLS secures the connection.</span></span> <span data-ttu-id="be186-203">Nécessite un certificat de serveur SSL valide installé sur ce serveur.</span><span class="sxs-lookup"><span data-stu-id="be186-203">Requires a valid SSL server certificate installed on this server.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="be186-204">Pour tester les fonctionnalités SMTP de base avec un compte e-mail personnel, y compris un compte Exchange, sélectionnez **Accès anonyme**.</span><span class="sxs-lookup"><span data-stu-id="be186-204">To test core SMTP functionality with a personal e-mail account, including an Exchange account, select **Anonymous access**.</span></span> <span data-ttu-id="be186-205">Lorsque l'authentification de base est sélectionnée, SMTP utilise la commande AUTH.</span><span class="sxs-lookup"><span data-stu-id="be186-205">When Basic authentication is selected, SMTP uses the AUTH command.</span></span> <span data-ttu-id="be186-206">Certains fournisseurs de messagerie peuvent échouer en raison de la commande AUTH.</span><span class="sxs-lookup"><span data-stu-id="be186-206">Some e-mail providers may fail because of the AUTH command.</span></span> <span data-ttu-id="be186-207">Si la commande AUTH échoue, une erreur peut être consignée dans les journaux d'événements Windows sur le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="be186-207">If the AUTH command fails, an error may be logged in the Windows event logs on the SMTP Server.</span></span>  
  
6.  <span data-ttu-id="be186-208">Sous l’onglet **Remise**, sélectionnez **Connexions sortantes**.</span><span class="sxs-lookup"><span data-stu-id="be186-208">In the **Delivery** tab, select **Outbound connections**.</span></span> <span data-ttu-id="be186-209">Le port TCP 25 est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="be186-209">By default, the TCP Port is 25.</span></span> <span data-ttu-id="be186-210">Il est possible d’entrer un autre port s’il est ouvert dans le pare-feu.</span><span class="sxs-lookup"><span data-stu-id="be186-210">A different port can be entered if it is open within your firewall.</span></span> <span data-ttu-id="be186-211">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="be186-211">Select **OK**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="be186-212">Le port TCP peut servir aux connexions entrantes et aux connexions sortantes.</span><span class="sxs-lookup"><span data-stu-id="be186-212">The TCP Port can be used for Inbound connections and Outbound connections.</span></span>  
  
7.  <span data-ttu-id="be186-213">Sous l’onglet **Remise**, sélectionnez **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="be186-213">In the **Delivery** tab, select **Advanced**.</span></span> <span data-ttu-id="be186-214">Par défaut, le **nom de domaine complet** du serveur local est répertorié.</span><span class="sxs-lookup"><span data-stu-id="be186-214">By default, the **Fully Qualified Domain Name** of the local server is listed.</span></span> <span data-ttu-id="be186-215">Selon votre fournisseur d’accès Internet, la propriété **Hôte actif** peut rester vide.</span><span class="sxs-lookup"><span data-stu-id="be186-215">Depending on the internet provider, the **Smart Host** property can remain empty.</span></span> <span data-ttu-id="be186-216">Vous pouvez avoir besoin de contacter le fournisseur d'accès Internet pour vérifier si un hôte actif (Smart Host) est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="be186-216">You may need to contact the internet provider to confirm if a Smart Host is required.</span></span> <span data-ttu-id="be186-217">Sinon, vous pourriez être en mesure d’entrer smtp.*EMailProvider*.com.</span><span class="sxs-lookup"><span data-stu-id="be186-217">Otherwise, you may be able to enter smtp.*EMailProvider*.com.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be186-218">Un **hôte actif** est un serveur dédié utilisé par un serveur Exchange pour acheminer tous les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="be186-218">A **Smart Host**, also known as a relay host, is a dedicated server used by an Exchange Server to route all outgoing messages.</span></span> <span data-ttu-id="be186-219">Quand l’**hôte actif** reçoit les messages, il les transfère vers un domaine distant.</span><span class="sxs-lookup"><span data-stu-id="be186-219">When the **Smart Host** receives the messages, the **Smart Host** forwards the messages to a remote domain.</span></span> <span data-ttu-id="be186-220">L’objectif d’un **hôte actif** est d’améliorer les performances d’un serveur Exchange.</span><span class="sxs-lookup"><span data-stu-id="be186-220">The goal of a **Smart Host** is to improve performance of an Exchange Server.</span></span> <span data-ttu-id="be186-221">Le serveur Exchange Server transmet uniquement l'hôte actif ; il ne contacte pas de façon répétée le domaine distant jusqu'à ce qu'une connexion soit établie.</span><span class="sxs-lookup"><span data-stu-id="be186-221">The Exchange Server only transmits to the smart host; instead of repeatedly contacting the remote domain until a connection is made.</span></span>  
  
8.  <span data-ttu-id="be186-222">Sélectionnez **OK** pour fermer toutes les fenêtres.</span><span class="sxs-lookup"><span data-stu-id="be186-222">Select **OK** to close all windows.</span></span>  
  
9. <span data-ttu-id="be186-223">Un redémarrage est nécessaire pour appliquer les paramètres du serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="be186-223">A restart is needed to apply the SMTP Server settings.</span></span> <span data-ttu-id="be186-224">Pour redémarrer le serveur SMTP : cliquez avec le bouton droit sur **[Serveur virtuel SMTP n°1]**, sélectionnez **Arrêter**, puis sélectionnez **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="be186-224">To restart the SMTP Server: Right-click **[SMTP Virtual Server #1]**, select **Stop**, and then select **Start**.</span></span>  
  
  
## <a name="test-the-smtp-server"></a><span data-ttu-id="be186-225">Tester le serveur SMTP</span><span class="sxs-lookup"><span data-stu-id="be186-225">Test the SMTP Server</span></span>  
 <span data-ttu-id="be186-226">Telnet peut être utilisé pour tester la configuration du serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="be186-226">Telnet can be used to test the SMTP Server configuration.</span></span> <span data-ttu-id="be186-227">La procédure suivante envoie un message à une adresse e-mail à l’aide de votre serveur SMTP configuré.</span><span class="sxs-lookup"><span data-stu-id="be186-227">The following steps send a message using your configured SMTP Server to an e-mail address.</span></span> <span data-ttu-id="be186-228">L’article [http://support.microsoft.com/kb/153119](http://support.microsoft.com/kb/153119) fournit des descriptions des commandes telnet.</span><span class="sxs-lookup"><span data-stu-id="be186-228">[http://support.microsoft.com/kb/153119](http://support.microsoft.com/kb/153119) provides descriptions of the telnet commands.</span></span>  
  
1.  <span data-ttu-id="be186-229">Ouvrez une fenêtre de commande comme administrateur.</span><span class="sxs-lookup"><span data-stu-id="be186-229">Open a command window as Administrator.</span></span>
  
2.  <span data-ttu-id="be186-230">À l’invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="be186-230">In the command prompt, type:</span></span>  
  
     `telnet localhost 25`  
  
     <span data-ttu-id="be186-231">Si Telnet n'est pas installé, installez-le en tapant :</span><span class="sxs-lookup"><span data-stu-id="be186-231">If telnet is not installed, install it by typing:</span></span>  
  
     `pkgmgr /iu:"TelnetClient"`  
  
3.  <span data-ttu-id="be186-232">Démarrez la communication en tapant :</span><span class="sxs-lookup"><span data-stu-id="be186-232">Start communication by typing:</span></span>  
  
     `EHLO server`  
  
4.  <span data-ttu-id="be186-233">Entrez l'adresse électronique de l'expéditeur :</span><span class="sxs-lookup"><span data-stu-id="be186-233">Enter the Mail From address:</span></span>  
  
     `MAIL FROM: *YourEmailAddress*@*YourProvider*.com`  
  
     <span data-ttu-id="be186-234">Par exemple, entrez :</span><span class="sxs-lookup"><span data-stu-id="be186-234">For example, enter:</span></span>  
  
     `MAIL FROM: EmailAddress@outlook.com`  
  
5.  <span data-ttu-id="be186-235">Entrez l’adresse e-mail de l’expéditeur :</span><span class="sxs-lookup"><span data-stu-id="be186-235">Enter the Mail To address:</span></span>  
  
     `RCPT TO: *YourEmailAddress*@*YourProvider*.com`  
  
     <span data-ttu-id="be186-236">Par exemple, entrez :</span><span class="sxs-lookup"><span data-stu-id="be186-236">For example, enter:</span></span>  
  
     `RCPT TO: EmailAddress@outlook.com`  
  
6.  <span data-ttu-id="be186-237">Indiquez au serveur SMTP que vous êtes prêt à envoyer des données en tapant :</span><span class="sxs-lookup"><span data-stu-id="be186-237">Tell the SMTP Server you are ready to send data by typing:</span></span>  
  
     `DATA`  
  
7.  <span data-ttu-id="be186-238">Entrez l’objet en tapant :</span><span class="sxs-lookup"><span data-stu-id="be186-238">Enter the Subject by typing:</span></span>  
  
     `Subject: Test Message`  
  
8.  <span data-ttu-id="be186-239">Appuyez deux fois sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="be186-239">Hit Enter twice.</span></span>  
  
9. <span data-ttu-id="be186-240">Entrez le corps du message en tapant :</span><span class="sxs-lookup"><span data-stu-id="be186-240">Enter the message body by typing:</span></span>  
  
     `This is the message body of the test message.`  
  
10. <span data-ttu-id="be186-241">Appuyez sur Entrée, tapez un point (.), puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="be186-241">Hit Enter, type a period (.), and hit Enter.</span></span>  
  
 <span data-ttu-id="be186-242">Vérifiez l'adresse RCPT TO du message.</span><span class="sxs-lookup"><span data-stu-id="be186-242">Check the RCPT TO address for the e-mail message.</span></span> <span data-ttu-id="be186-243">Si l’e-mail n’est pas remis (consultez votre boîte de réception et le dossier Courrier indésirable), le message n’a pas été correctement envoyé et réside peut-être dans le dossier de la file d’attente SMTP (C:\inetpub\mailroot\Queue).</span><span class="sxs-lookup"><span data-stu-id="be186-243">If the e-mail is not delivered (Check your Inbox and Spam folder), then the message was not successfully sent, and may reside in the SMTP Queue folder (C:\inetpub\mailroot\Queue).</span></span>  
  
---
title: "À l’aide de l’Assistant Configuration de l’application MQSAgent COM + | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.mqsagent.wizard
helpviewer_keywords:
- MQSeries adapters, MQSAgent COM+ Configuration Wizard
- configuring [MQSeries adapters], MQSAgent COM+ Configuration Wizard
- MQSAgent COM+ Configuration Wizard
ms.assetid: f106700a-7f57-4c83-9344-6525fc10544d
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f6e8b625bcc3accbefda193c52459616691c265
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-the-mqsagent-com-configuration-wizard"></a><span data-ttu-id="95146-102">À l’aide de l’Assistant Configuration de l’application MQSAgent COM +</span><span class="sxs-lookup"><span data-stu-id="95146-102">Using the MQSAgent COM+ Configuration Wizard</span></span>
<span data-ttu-id="95146-103">L'Assistant Configuration de l'application MQSAgent COM+ configure MQSAgent, la partie de l'adaptateur de l'application COM+ (composant MQSeries).</span><span class="sxs-lookup"><span data-stu-id="95146-103">The MQSAgent COM+ Configuration Wizard configures the MQSAgent, the COM+ application (MQSeries component) part of the adapter.</span></span> <span data-ttu-id="95146-104">L'assistant définit l'identité de l'application du composant, ainsi que le nom de rôle et les utilisateurs qui font partie de ce rôle.</span><span class="sxs-lookup"><span data-stu-id="95146-104">The wizard sets the application identity of the component, and the role name and users included in the role.</span></span> <span data-ttu-id="95146-105">Le nom du composant MQSAgent COM + créé avec l’Assistant de Configuration de MQSAgent COM + est **MQSAgent2**.</span><span class="sxs-lookup"><span data-stu-id="95146-105">The name of the MQSAgent COM+ component created with the MQSAgent COM+ Configuration Wizard is **MQSAgent2**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95146-106">L’application MQSAgent COM+ est prise en charge sur une version 64 bits de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="95146-106">The MQSAgent COM+ application is supported on a 64-bit Windows server.</span></span> <span data-ttu-id="95146-107">Elle est exécutée en tant que processus 32 bits sous WOW64.</span><span class="sxs-lookup"><span data-stu-id="95146-107">It will run as a 32-bit process under WOW64.</span></span> <span data-ttu-id="95146-108">Un ordinateur sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé et qui exécute une version 64 bits de Windows Server peut communiquer avec un ordinateur distant 32 bits sur lequel MQSAgent est installé.</span><span class="sxs-lookup"><span data-stu-id="95146-108">A [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-based computer that is running on a 64-bit version of Windows Server can communicate with a remote 32-bit computer that has the MQSAgent installed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95146-109">MQSeries Agent et l’exécutable de l’Assistant Configuration MQSAgent COM + **MQSConfigWiz.exe** ne sont pas installés si vous mettez à niveau à partir de BizTalk Server 2009 à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="95146-109">The MQSeries Agent and the MQSAgent COM+ Configuration Wizard executable **MQSConfigWiz.exe** are not installed if you upgrade from BizTalk Server 2009 to BizTalk Server.</span></span> <span data-ttu-id="95146-110">Après la mise à niveau vers BizTalk Server à partir de BizTalk Server 2009 et réexécutez le programme d’installation, sélectionnez le **modifier** option et sélectionnez MQSeries Agent sous logiciels supplémentaires pour installer ces composants.</span><span class="sxs-lookup"><span data-stu-id="95146-110">After upgrading to BizTalk Server from BizTalk Server 2009 re-run setup, select the **Modify** option, and select the MQSeries Agent under the Additional Software to install these components.</span></span>  
  
## <a name="to-set-the-application-identity"></a><span data-ttu-id="95146-111">Pour définir l'identité de l'application</span><span class="sxs-lookup"><span data-stu-id="95146-111">To set the application identity</span></span>  
  
-   <span data-ttu-id="95146-112">Utilisez le **identité de l’Application** page de l’application MQSAgent COM + Assistant Configuration pour définir l’identité de l’application pour MQSAgent comme suit :</span><span class="sxs-lookup"><span data-stu-id="95146-112">Use the **Application Identity** page of the MQSAgent COM+ Configuration Wizard to set the application identity for the MQSAgent as follows:</span></span>  
  
    |<span data-ttu-id="95146-113">Utiliser</span><span class="sxs-lookup"><span data-stu-id="95146-113">Use this</span></span>|<span data-ttu-id="95146-114">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="95146-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="95146-115">**Utilisateur interactif**</span><span class="sxs-lookup"><span data-stu-id="95146-115">**Interactive User**</span></span>|<span data-ttu-id="95146-116">Sélectionner cette option pour utiliser le compte de connexion actuel comme identité de l'application.</span><span class="sxs-lookup"><span data-stu-id="95146-116">Select this option to use the current logon account for the application identity.</span></span>|  
    |<span data-ttu-id="95146-117">**Service local**</span><span class="sxs-lookup"><span data-stu-id="95146-117">**Local Service**</span></span>|<span data-ttu-id="95146-118">Définissez l'identité de l'application sur un compte du service intégré.</span><span class="sxs-lookup"><span data-stu-id="95146-118">Set the application identity to a built-in service account.</span></span>|  
    |<span data-ttu-id="95146-119">**Service réseau**</span><span class="sxs-lookup"><span data-stu-id="95146-119">**Network Service**</span></span>|<span data-ttu-id="95146-120">Définissez l'identité de l'application sur un compte intégré avec accès réseau.</span><span class="sxs-lookup"><span data-stu-id="95146-120">Set the application identity to a built-in account with network access.</span></span>|  
    |<span data-ttu-id="95146-121">**Cet utilisateur**</span><span class="sxs-lookup"><span data-stu-id="95146-121">**This user**</span></span>|<span data-ttu-id="95146-122">Définissez l'identité de l'application sur le nom d'utilisateur indiqué.</span><span class="sxs-lookup"><span data-stu-id="95146-122">Set the application identity to the indicated user name.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="95146-123">Il n'est pas recommandé d'utiliser un compte avec autorisations administratives pour l'identité de l'application.</span><span class="sxs-lookup"><span data-stu-id="95146-123">It is not recommended that you use an account with administrative permissions for the application identity.</span></span> <span data-ttu-id="95146-124">Le compte doit bénéficier des privilèges minimaux requis : autorisation en lecture/écriture pour les files d'attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="95146-124">The account must have the minimal rights required: read and write permission for the MQSeries queues.</span></span>  
  
## <a name="to-name-the-role-and-add-users-to-it"></a><span data-ttu-id="95146-125">Pour définir le nom du rôle et y ajouter des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="95146-125">To name the role and add users to it</span></span>  
  
-   <span data-ttu-id="95146-126">Utilisez le **nom du rôle** page de l’application MQSAgent COM + Assistant Configuration pour affecter un nom et les utilisateurs au rôle comme suit :</span><span class="sxs-lookup"><span data-stu-id="95146-126">Use the **Name of Role** page of the MQSAgent COM+ Configuration Wizard  to assign a name and users to the role as follows:</span></span>  
  
    |<span data-ttu-id="95146-127">Utiliser</span><span class="sxs-lookup"><span data-stu-id="95146-127">Use this</span></span>|<span data-ttu-id="95146-128">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="95146-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="95146-129">**Nom du rôle**</span><span class="sxs-lookup"><span data-stu-id="95146-129">**Name of role**</span></span>|<span data-ttu-id="95146-130">Permet de saisir le nom du rôle.</span><span class="sxs-lookup"><span data-stu-id="95146-130">Type the name of the role.</span></span>|  
    |<span data-ttu-id="95146-131">**Utilisateurs**</span><span class="sxs-lookup"><span data-stu-id="95146-131">**Users**</span></span>|<span data-ttu-id="95146-132">Affiche les utilisateurs qui appartiennent à ce rôle</span><span class="sxs-lookup"><span data-stu-id="95146-132">Display the users that belong to the role.</span></span>|  
    |<span data-ttu-id="95146-133">**Ajouter**</span><span class="sxs-lookup"><span data-stu-id="95146-133">**Add**</span></span>|<span data-ttu-id="95146-134">Ajouter des utilisateurs au rôle</span><span class="sxs-lookup"><span data-stu-id="95146-134">Add users to the role.</span></span> <span data-ttu-id="95146-135">Il s'agit des comptes de service [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui utilisent l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="95146-135">These are the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] service accounts using the adapter.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="95146-136">Ajoutez au rôle uniquement les comptes qui nécessitent un accès à l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="95146-136">Add to the role only accounts requiring access to the adapter.</span></span>  
  
## <a name="to-set-the-msdtc-security-configuration-on-the-windows-server-2008-computer-to-no-authentication-required"></a><span data-ttu-id="95146-137">Définition de la configuration de la sécurité MSDTC de l'ordinateur Windows Server 2008 sur Aucune authentification requise</span><span class="sxs-lookup"><span data-stu-id="95146-137">To set the MSDTC Security configuration on the Windows Server 2008 computer to No Authentication Required</span></span>  
 <span data-ttu-id="95146-138">Si l’application MQSAgent COM + est installée sur un [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ordinateur et l’adaptateur MQSeries (qui est installé avec BizTalk Server) est installé sur un [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] ordinateur, la configuration de sécurité MSDTC sur le [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] ordinateur doit être définie sur **aucune authentification requise**.</span><span class="sxs-lookup"><span data-stu-id="95146-138">If the MQSAgent COM+ application is installed on a [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] computer and the MQSeries Adapter (which is installed with BizTalk Server) is installed on a [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] computer, the MSDTC Security configuration on the [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] computer must be set to **No Authentication Required**.</span></span> <span data-ttu-id="95146-139">Pour définir la configuration de la sécurité MSDTC sur Aucune authentification requise, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="95146-139">Follow these steps to set the MSDTC security configuration to No Authentication Required:</span></span>  
  
1.  <span data-ttu-id="95146-140">Cliquez sur **Démarrer** puis cliquez sur **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="95146-140">Click **Start** and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="95146-141">Double-cliquez sur **outils d’administration**.</span><span class="sxs-lookup"><span data-stu-id="95146-141">Double-click **Administrative Tools**.</span></span>  
  
3.  <span data-ttu-id="95146-142">Double-cliquez sur **Services de composants** pour lancer le **Services de composants** interface de gestion.</span><span class="sxs-lookup"><span data-stu-id="95146-142">Double-click **Component Services** to launch the **Component Services** management interface.</span></span>  
  
4.  <span data-ttu-id="95146-143">Développez **Services de composants**, développez **ordinateurs**, puis développez **poste**.</span><span class="sxs-lookup"><span data-stu-id="95146-143">Expand **Component Services**, expand **Computers**, and then expand **My Computer**.</span></span>  
  
5.  <span data-ttu-id="95146-144">Avec le bouton droit **poste** et cliquez sur le **propriétés** élément de menu.</span><span class="sxs-lookup"><span data-stu-id="95146-144">Right-click **My Computer** and click the **Properties** menu item.</span></span>  
  
6.  <span data-ttu-id="95146-145">Dans le **poste** boîte de dialogue, cliquez sur le **MSDTC** onglet, puis cliquez sur **Configuration de la sécurité**.</span><span class="sxs-lookup"><span data-stu-id="95146-145">In the **My Computer** dialog box, click the **MSDTC** tab and then click **Security Configuration**.</span></span>  
  
7.  <span data-ttu-id="95146-146">Dans le **Configuration de la sécurité** boîte de dialogue le **Communication du Gestionnaire de transactions** section, sélectionnez **aucune authentification requise**.</span><span class="sxs-lookup"><span data-stu-id="95146-146">In the **Security Configuration** dialog box, in the **Transaction Manager Communication** section, select **No Authentication Required**.</span></span> <span data-ttu-id="95146-147">Si vous êtes invité à une boîte de dialogue, cliquez sur **Oui** pour redémarrer le Service MS DTC.</span><span class="sxs-lookup"><span data-stu-id="95146-147">If you are prompted with a dialog box, click **Yes** to restart the MS DTC Service.</span></span>  
  
8.  <span data-ttu-id="95146-148">Une fois le service MS DTC a redémarré, cliquez sur **OK** et cliquez sur **OK** à nouveau pour fermer la **poste** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="95146-148">After the MS DTC service has restarted, click **OK** and click **OK** again to close the **My Computer** dialog box.</span></span>  
  
9. <span data-ttu-id="95146-149">Fermer le **Services de composants** interface de gestion.</span><span class="sxs-lookup"><span data-stu-id="95146-149">Close the **Component Services** management interface.</span></span>  
  
## <a name="to-configure-the-mqsagent-runtime-components-to-run-under-an-alternative-set-of-credentials"></a><span data-ttu-id="95146-150">Pour configurer les composants d'exécution MQSAgent pour qu'ils s'exécutent avec différentes informations d'identification</span><span class="sxs-lookup"><span data-stu-id="95146-150">To configure the MQSAgent runtime components to run under an alternative set of credentials</span></span>  
 <span data-ttu-id="95146-151">L'application MQSAgent COM+ comprend des composants d'administration et d'exécution.</span><span class="sxs-lookup"><span data-stu-id="95146-151">The MQSAgent COM+ application includes components for both administration and runtime.</span></span> <span data-ttu-id="95146-152">Si vous souhaitez diviser cette fonctionnalité en plusieurs applications COM+ pour des raisons de sécurité, procédez comme suit sur l'ordinateur sur lequel l'application MQSAgent COM+ est installée :</span><span class="sxs-lookup"><span data-stu-id="95146-152">If you want to separate this functionality into different COM+ applications for security purposes, follow these steps on the computer that the MQSAgent COM+ application is installed on:</span></span>  
  
1.  <span data-ttu-id="95146-153">Activez les modifications pour le composant MQSAgent COM+.</span><span class="sxs-lookup"><span data-stu-id="95146-153">Enable changes for the MQSAgent COM+ component.</span></span>  
  
    -   <span data-ttu-id="95146-154">Cliquez sur **Démarrer** puis cliquez sur **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="95146-154">Click **Start** and then click **Control Panel**.</span></span>  
  
    -   <span data-ttu-id="95146-155">Double-cliquez sur **outils d’administration**.</span><span class="sxs-lookup"><span data-stu-id="95146-155">Double-click **Administrative Tools**.</span></span>  
  
    -   <span data-ttu-id="95146-156">Double-cliquez sur **Services de composants** pour lancer le **Services de composants** interface de gestion.</span><span class="sxs-lookup"><span data-stu-id="95146-156">Double-click **Component Services** to launch the **Component Services** management interface.</span></span>  
  
    -   <span data-ttu-id="95146-157">Développez **Services de composants**, développez **poste**, développez **Applications COM +**, avec le bouton droit le **MQSAgent2** l’application COM + puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="95146-157">Expand **Component Services**, expand **My Computer**, expand **COM+ Applications**, right-click the **MQSAgent2** COM+ application and then click **Properties**.</span></span>  
  
    -   <span data-ttu-id="95146-158">Cliquez sur le **avancé** onglet et décochez la case **désactiver les modifications**.</span><span class="sxs-lookup"><span data-stu-id="95146-158">Click the **Advanced** tab and uncheck **Disable changes**.</span></span>  
  
    -   <span data-ttu-id="95146-159">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="95146-159">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="95146-160">Créez une nouvelle application COM+ pour les composants d'exécution MQSAgent.</span><span class="sxs-lookup"><span data-stu-id="95146-160">Create a new COM+ application for the MQSAgent runtime components.</span></span>  
  
    -   <span data-ttu-id="95146-161">Avec le bouton droit **Applications COM +**, cliquez sur **nouveau**, **Application** pour afficher les **Assistant Installation d’applications COM +** et cliquez sur  **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="95146-161">Right-click **COM+ Applications**, click **New**, **Application** to display the **COM+ Application Install Wizard** and click **Next**.</span></span>  
  
    -   <span data-ttu-id="95146-162">Cliquez sur **créer une application vide**.</span><span class="sxs-lookup"><span data-stu-id="95146-162">Click **Create an empty application**.</span></span>  
  
    -   <span data-ttu-id="95146-163">Entrez le nom **MQSAgent2RunTime**, laissez l’option par défaut **application serveur** activé, puis cliquez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="95146-163">Enter the name **MQSAgent2RunTime**, leave the default option for **Server application** enabled and click **Next**.</span></span>  
  
    -   <span data-ttu-id="95146-164">Sélectionnez l’option de **cet utilisateur**, entrez les informations de compte approprié, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="95146-164">Select the option for **This user**, enter the appropriate account information and click **Next**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="95146-165">Ce compte doit avoir **connecter** et **put** et/ou **obtenir** autorisations sur IBM WebSphere MQ appropriées pour les files d’attente de Windows.</span><span class="sxs-lookup"><span data-stu-id="95146-165">This account should have **connect** and **put** and/or **get** permissions on the appropriate IBM WebSphere MQ for Windows queues.</span></span> <span data-ttu-id="95146-166">Vous pouvez définir les autorisations appropriées pour ce compte avec le **setmqaut** commande disponible avec IBM WebSphere MQ.</span><span class="sxs-lookup"><span data-stu-id="95146-166">You can set the appropriate permissions for this account with the **setmqaut** command available with the IBM WebSphere MQ.</span></span> <span data-ttu-id="95146-167">Pour plus d’informations sur la **setmqaut** commande consultez la documentation IBM WebSphere MQ.</span><span class="sxs-lookup"><span data-stu-id="95146-167">For more information about the **setmqaut** command see the IBM WebSphere MQ documentation.</span></span>  
  
    -   <span data-ttu-id="95146-168">Cliquez sur **suivant** sur la **ajouter des rôles d’Application** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="95146-168">Click **Next** on the **Add Application Roles** dialog box.</span></span>  
  
    -   <span data-ttu-id="95146-169">Cliquez sur **suivant** sur la **ajouter des utilisateurs aux rôles** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="95146-169">Click **Next** on the **Add Users to Roles** dialog box.</span></span>  
  
    -   <span data-ttu-id="95146-170">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="95146-170">Click **Finish**.</span></span>  
  
3.  <span data-ttu-id="95146-171">Déplacez les composants d'exécution vers la nouvelle application COM+</span><span class="sxs-lookup"><span data-stu-id="95146-171">Move the runtime components to the new COM+ application</span></span>  
  
    -   <span data-ttu-id="95146-172">Développez le **MQSAgent2** l’application COM +.</span><span class="sxs-lookup"><span data-stu-id="95146-172">Expand the **MQSAgent2** COM+ application.</span></span>  
  
    -   <span data-ttu-id="95146-173">Développez **composants**.</span><span class="sxs-lookup"><span data-stu-id="95146-173">Expand **Components**.</span></span>  
  
    -   <span data-ttu-id="95146-174">Avec le bouton droit le **MQSAgent2.MQSAgent.1** composant et cliquez sur **déplacer** pour afficher les **déplacer les composants (s)** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="95146-174">Right-click the **MQSAgent2.MQSAgent.1** component and click **Move** to display the **Move components(s)** dialog box.</span></span>  
  
    -   <span data-ttu-id="95146-175">Sélectionnez **MQSAgent2RunTime** sous **Veuillez sélectionner une destination** et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="95146-175">Select **MQSAgent2RunTime** under **Please select a destination** and click **OK**.</span></span>  
  
    -   <span data-ttu-id="95146-176">Répétez ces étapes pour le **MQSAgent2.MQSBroker.1** et **MQSAgent2.MQSProxy.1** composants.</span><span class="sxs-lookup"><span data-stu-id="95146-176">Repeat these steps for the **MQSAgent2.MQSBroker.1** and **MQSAgent2.MQSProxy.1** components.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95146-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95146-177">See Also</span></span>  
 <span data-ttu-id="95146-178">[Comment configurer l’adaptateur MQSeries envoyer et recevoir des gestionnaires](../core/how-to-configure-mqseries-adapter-send-and-receive-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="95146-178">[How to Configure MQSeries Adapter Send and Receive Handlers](../core/how-to-configure-mqseries-adapter-send-and-receive-handlers.md) </span></span>  
 [<span data-ttu-id="95146-179">Configuration de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="95146-179">Configuring the MQSeries Adapter</span></span>](../core/configuring-the-mqseries-adapter.md)
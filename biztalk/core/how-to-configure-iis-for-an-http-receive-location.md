---
title: "Comment configurer IIS pour l’emplacement de réception HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 64-bit support, HTTP adapters
- HTTP adapters, IIS
- configuring [HTTP adapters], IIS
- receive locations, IIS
- IIS, receive locations
- HTTP adapters, 64-bit support
- IIS, HTTP adapters
ms.assetid: 1c420f46-01f1-4c9c-9144-d8d2acc8b0c4
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1daa535c546bef0b390f0f7f84c45d546ac0005
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-iis-for-an-http-receive-location"></a><span data-ttu-id="91952-102">Comment configurer IIS pour l’emplacement de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="91952-102">How to Configure IIS for an HTTP Receive Location</span></span>
<span data-ttu-id="91952-103">Selon la version de Microsoft Windows que vous utilisez, vous devrez adapter la configuration des services IIS (Microsoft Internet Information Services) pour travailler avec l'emplacement de réception de l'adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="91952-103">Depending on which version of Microsoft Windows you are using, you will have to configure Microsoft Internet Information Services (IIS) differently to work with the HTTP adapter receive location.</span></span>  
  
 <span data-ttu-id="91952-104">Si votre système d'exploitation est [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], IIS 7.0 offre deux modes d'isolation des applications distincts pour protéger les applications Web,</span><span class="sxs-lookup"><span data-stu-id="91952-104">If your operating system is [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], IIS 7.0 provides two different application isolation modes to protect Web applications.</span></span> <span data-ttu-id="91952-105">dont le mode d'isolation du processus de travail (par défaut).</span><span class="sxs-lookup"><span data-stu-id="91952-105">Worker process isolation mode is the default mode.</span></span> <span data-ttu-id="91952-106">Vous pouvez configurer l'emplacement de réception de l'adaptateur HTTP de manière à fonctionner avec les deux modes. Cependant, il est recommandé d'utiliser le mode d'isolation des processus de travail en raison de sa fonctionnalité de sécurité renforcée.</span><span class="sxs-lookup"><span data-stu-id="91952-106">You can configure the HTTP adapter receive location to work with either mode, but worker process isolation mode is recommended for its improved security functionality.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91952-107">Si votre système d’exploitation est le x64 édition de [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], la version 64 bits du HTTP recevoir adaptateur est installé dans le  *\<lecteur >***\Program Files (x86) \Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\HttpReceive64** répertoire de votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] par défaut.</span><span class="sxs-lookup"><span data-stu-id="91952-107">If your operating system is the x64 edition of [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], the 64-bit version of the HTTP receive adapter is installed to the *\<drive>***\Program Files (x86)\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**\HttpReceive64** directory of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] by default.</span></span> <span data-ttu-id="91952-108">Pour la faire fonctionner dans un mode 64 bits natif, vous devez exécuter le script suivant à partir d'une ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="91952-108">To run the 64-bit version of the HTTP receive adapter in 64-bit native mode you must execute the following script from a command line:</span></span>  
>   
>  `cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 0`  
>   
>  `C:\WINDOWS\Microsoft.NET\Framework64\vX.X.XXXXX>aspnet_regiis.exe -i`  
  
> [!NOTE]
>  <span data-ttu-id="91952-109">Toute configuration IIS menant au partage du même processus par SOAP et HTTP est non valide.</span><span class="sxs-lookup"><span data-stu-id="91952-109">Any IIS configuration that leads to SOAP and HTTP sharing the same process is not valid.</span></span> <span data-ttu-id="91952-110">Vous ne pouvez utiliser qu'un seul récepteur isolé par processus.</span><span class="sxs-lookup"><span data-stu-id="91952-110">You can have only one isolated receiver per process.</span></span>  
  
### <a name="to-configure-the-iis-70-worker-process-isolation-mode-to-work-with-the-http-adapter-receive-location"></a><span data-ttu-id="91952-111">Pour configurer le mode d’isolation de processus de travail de IIS 7.0 pour travailler avec l’adaptateur HTTP emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="91952-111">To configure the IIS 7.0 worker process isolation mode to work with the HTTP adapter receive location</span></span>  
  
1.  <span data-ttu-id="91952-112">Cliquez sur **Démarrer**, pointez sur **paramètres**, puis cliquez sur **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="91952-112">Click **Start**, point to **Settings**, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="91952-113">Dans le panneau de configuration, double-cliquez sur **outils d’administration**.</span><span class="sxs-lookup"><span data-stu-id="91952-113">In Control Panel, double-click **Administrative Tools**.</span></span>  
  
3.  <span data-ttu-id="91952-114">Dans Outils d’administration, double-cliquez sur **Internet Information Services**.</span><span class="sxs-lookup"><span data-stu-id="91952-114">In Administrative Tools, double-click **Internet Information Services**.</span></span>  
  
4.  <span data-ttu-id="91952-115">Dans les services IIS, sélectionnez l'entrée du serveur Web racine.</span><span class="sxs-lookup"><span data-stu-id="91952-115">In Internet Information Services, select the root Web server entry.</span></span> <span data-ttu-id="91952-116">Dans le **affichage des fonctionnalités**, double-cliquez sur **mappages de gestionnaires**, puis dans le volet Actions, cliquez sur **ajouter un mappage de scripts**.</span><span class="sxs-lookup"><span data-stu-id="91952-116">In the **Features View**, double-click **Handler Mappings**, and then in the Actions pane, click **Add Script Map**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91952-117">La configuration du mappage de scripts au niveau du serveur Web entraîne l'application de ce mappage à tous les sites Web enfants.</span><span class="sxs-lookup"><span data-stu-id="91952-117">Configuring the script mapping at the Web server level will cause this mapping to apply to all child Web sites.</span></span> <span data-ttu-id="91952-118">Si vous souhaitez limiter le mappage à un site Web ou à un dossier virtuel spécifique, sélectionnez le site ou le dossier au lieu du serveur Web.</span><span class="sxs-lookup"><span data-stu-id="91952-118">If you want to restrict the mapping to a specific Web site or virtual folder, select the target site or folder instead of the Web server.</span></span>  
  
5.  <span data-ttu-id="91952-119">Dans le **ajouter un mappage de scripts** boîte de dialogue le **chemin d’accès de la demande** , tapez `BtsHttpReceive.dll`.</span><span class="sxs-lookup"><span data-stu-id="91952-119">In the **Add Script Map** dialog box, in the **Request path** field, type `BtsHttpReceive.dll`.</span></span>  
  
6.  <span data-ttu-id="91952-120">Dans le **exécutable** , cliquez sur le bouton de sélection (**...** ) bouton et accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive.</span><span class="sxs-lookup"><span data-stu-id="91952-120">In the **Executable** field, click the ellipsis (**…**) button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive.</span></span> <span data-ttu-id="91952-121">Sélectionnez **BtsHttpReceive.dll** puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="91952-121">Select **BtsHttpReceive.dll** and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="91952-122">Dans le **nom** , tapez `BizTalk HTTP Receive`, puis cliquez sur **Restrictions des demandes**.</span><span class="sxs-lookup"><span data-stu-id="91952-122">In the **Name** field, type `BizTalk HTTP Receive`, and then click **Request Restrictions**.</span></span>  
  
8.  <span data-ttu-id="91952-123">Dans le **Restrictions des demandes** boîte de dialogue, cliquez sur le **verbes** onglet, puis sélectionnez **un des verbes suivants**.</span><span class="sxs-lookup"><span data-stu-id="91952-123">In the **Request Restrictions** dialog box, click the **Verbs** tab and then select **One of the following verbs**.</span></span> <span data-ttu-id="91952-124">Entrez `POST` le verbe.</span><span class="sxs-lookup"><span data-stu-id="91952-124">Enter `POST` as the verb.</span></span>  
  
9. <span data-ttu-id="91952-125">Sur le **accès** onglet, sélectionnez **Script**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="91952-125">On the **Access** tab, select **Script**, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="91952-126">Une invite vous demande si vous souhaitez autoriser l'extension ISAPI, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="91952-126">When prompted to allow the ISAPI extension, click **Yes**.</span></span>  
  
11. <span data-ttu-id="91952-127">Avec le bouton droit **Pools d’applications**, pointez sur **nouveau**, puis cliquez sur **pool d’applications**.</span><span class="sxs-lookup"><span data-stu-id="91952-127">Right-click **Application Pools**, point to **New**, and then click **Application pool**.</span></span>  
  
12. <span data-ttu-id="91952-128">Dans le **ajouter un Pool d’applications** boîte de dialogue le **nom** , tapez un nom pour le pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="91952-128">In the **Add Application Pool** dialog box, in the **Name** box, type a name for the application pool.</span></span> <span data-ttu-id="91952-129">Sélectionnez **.NET Framework v4.0.30319** puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="91952-129">Select **NET Framework v4.0.30319** and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91952-130">Le numéro de version peut varier selon la version de .NET Framework installée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="91952-130">The version number may vary depending on the version of .NET Framework installed on the computer.</span></span>  
  
     <span data-ttu-id="91952-131">Le pool d’applications s’affiche dans la liste des **Pools d’applications**.</span><span class="sxs-lookup"><span data-stu-id="91952-131">The new application pool appears in the list of **Application Pools**.</span></span>  
  
13. <span data-ttu-id="91952-132">Dans **Pools d’applications**, dans le **affichage des fonctionnalités**, sélectionnez le pool d’applications, puis cliquez sur **paramètres avancés** dans le volet Actions.</span><span class="sxs-lookup"><span data-stu-id="91952-132">In **Application Pools**, in the **Features View**, select the new application pool, and then click **Advanced Settings** in the Actions pane.</span></span>  
  
14. <span data-ttu-id="91952-133">Dans le **paramètres avancés** boîte de dialogue le **modèle de processus** section, dans le **identité** , cliquez sur le bouton de sélection (**...** ) bouton.</span><span class="sxs-lookup"><span data-stu-id="91952-133">In the **Advanced Settings** dialog box, in the **Process Model** section, in the **Identity** field, click the ellipsis (**…**) button.</span></span>  
  
15. <span data-ttu-id="91952-134">Dans le **identité du Pool d’applications** boîte de dialogue, sélectionnez **compte personnalisé**, puis cliquez sur **définir**.</span><span class="sxs-lookup"><span data-stu-id="91952-134">In the **Application Pool Identity** dialog box, select **Custom account**, and then click **Set**.</span></span> <span data-ttu-id="91952-135">Cliquez sur **OK** pour fermer la boîte de dialogue **Paramètres avancés** .</span><span class="sxs-lookup"><span data-stu-id="91952-135">Click **OK** to close the **Advanced Settings** dialog box.</span></span>  
  
16. <span data-ttu-id="91952-136">Dans le Gestionnaire des services Internet, ouvrez le **Sites** dossier.</span><span class="sxs-lookup"><span data-stu-id="91952-136">In IIS Manager, open the **Sites** folder.</span></span> <span data-ttu-id="91952-137">Cliquez sur le **Site Web par défaut** puis cliquez sur **ajouter une Application**.</span><span class="sxs-lookup"><span data-stu-id="91952-137">Right-click the **Default Web Site** and then click **Add Application**.</span></span>  
  
17. <span data-ttu-id="91952-138">Dans le **ajouter une Application** boîte de dialogue **Alias**, entrez un alias à associer à l’application, puis cliquez sur **sélectionnez**.</span><span class="sxs-lookup"><span data-stu-id="91952-138">In the **Add Application** dialog box, in **Alias**, enter an alias to associate with the application, and then click **Select**.</span></span>  
  
18. <span data-ttu-id="91952-139">Dans le **sélectionner un Pool d’applications** boîte de dialogue, sélectionnez le nouveau pool d’applications que vous avez créé précédemment, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="91952-139">In the **Select Application Pool** dialog box, select the new application pool you created earlier, and then click **OK**.</span></span>  
  
19. <span data-ttu-id="91952-140">Cliquez sur le bouton de sélection (**...** ) bouton et accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive pour le **chemin d’accès physique**.</span><span class="sxs-lookup"><span data-stu-id="91952-140">Click the ellipsis (**…**) button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive for the **Physical path**.</span></span>  
  
20. <span data-ttu-id="91952-141">Cliquez sur **connecter en tant que** et entrez le **nom d’utilisateur** et **mot de passe** pour un compte d’utilisateur qui est membre du groupe Administrateurs, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="91952-141">Click **Connect As** and enter the **User name** and **Password** for a user account that is a member of the Administrators group, and then click **OK**.</span></span>  
  
21. <span data-ttu-id="91952-142">Cliquez sur **des paramètres de Test** et vérifiez qu’aucune erreur n’est affichés dans le **tester la connexion** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="91952-142">Click **Test Settings** and verify that no errors are displayed in the **Test Connection** dialog box.</span></span> <span data-ttu-id="91952-143">Cliquez sur **Fermer**, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="91952-143">Click **Close**, and then click **OK**.</span></span>  
  
22. <span data-ttu-id="91952-144">La nouvelle application s’affiche dans la liste des **Sites Web par défaut** dans le Gestionnaire des Services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="91952-144">The new application appears in the list of **Default Web Sites** in Internet Information Services (IIS) Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91952-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91952-145">See Also</span></span>  
 [<span data-ttu-id="91952-146">Pour configurer les emplacement de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="91952-146">How to Configure an HTTP Receive Location</span></span>](../core/how-to-configure-an-http-receive-location.md)
---
title: "Étape 2 : Création de Fabrikam LOBWebApplication | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating LOBWebApplication
- LOBWebApplication
ms.assetid: 2ff8bd20-7fbc-4e16-b177-bb4afac7f7c3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed64aac8ea0cf4073f3085f4491f607373d721b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-creating-the-fabrikam-lobwebapplication"></a><span data-ttu-id="20215-102">Étape 2 : Création de Fabrikam LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="20215-102">Step 2: Creating the Fabrikam LOBWebApplication</span></span>
<span data-ttu-id="20215-103">Dans cette étape, vous créez l’application métier utilisée par Fabrikam pour envoyer une demande PIP 3A2 à Contoso.</span><span class="sxs-lookup"><span data-stu-id="20215-103">In this step, you create the LOB application that Fabrikam uses to submit a 3A2 PIP request to Contoso.</span></span> <span data-ttu-id="20215-104">Le projet LOBWebApplication est installé dans le [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Kit de développement logiciel.</span><span class="sxs-lookup"><span data-stu-id="20215-104">The LOBWebApplication project is installed in the [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK.</span></span> <span data-ttu-id="20215-105">Pour exécuter l’application Web, vous devez créer un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] répertoire virtuel de Internet Information Services (IIS) et générer le projet LOBWebApplication.</span><span class="sxs-lookup"><span data-stu-id="20215-105">To run the Web application, you have to create a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Internet Information Services (IIS) virtual directory and build the LOBWebApplication project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20215-106">Si vous terminé le didacticiel DoubleAction, il est inutile d’effectuer cette étape.</span><span class="sxs-lookup"><span data-stu-id="20215-106">If you completed the DoubleAction tutorial, you do not need to perform this step.</span></span>  
  
### <a name="to-create-the-lobwebapplication-virtual-directory"></a><span data-ttu-id="20215-107">Pour créer le répertoire virtuel LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="20215-107">To create the LOBWebApplication virtual directory</span></span>  
  
1.  <span data-ttu-id="20215-108">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet**.</span><span class="sxs-lookup"><span data-stu-id="20215-108">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services Manager**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20215-109">Si vous avez déjà fait le didacticiel Double Action, vous aurez déjà créé le répertoire virtuel LOBWebApplication pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="20215-109">If you have already done the Double Action tutorial, you will already have created the LOBWebApplication virtual directory for that tutorial.</span></span> <span data-ttu-id="20215-110">Dans ce cas, vous n’avez pas à effectuer ces étapes.</span><span class="sxs-lookup"><span data-stu-id="20215-110">If so, you do not have to perform these steps.</span></span> <span data-ttu-id="20215-111">Toutefois, avoir à modifier les autorisations pour le répertoire virtuel à partir de **exécuter des scripts** à **en lecture**.</span><span class="sxs-lookup"><span data-stu-id="20215-111">You will, however, have to change the permissions for the virtual directory from **Run scripts** to **Read**.</span></span>  
  
2.  <span data-ttu-id="20215-112">Dans le Gestionnaire des Services Internet, développez **< nom_ordinateur > (ordinateur local)**, puis développez **Sites Web**.</span><span class="sxs-lookup"><span data-stu-id="20215-112">In Internet Information Services Manager, expand **<computer_name> (local computer)**, and then expand **Web Sites**.</span></span>  
  
3.  <span data-ttu-id="20215-113">Cliquez avec le bouton droit sur **Site web par défaut**, pointez sur **Nouveau**, puis cliquez sur **Répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="20215-113">Right-click **Default Web Site**, point to **New**, and then click **Virtual Directory**.</span></span>  
  
4.  <span data-ttu-id="20215-114">Sur le **Welcometo la page de l’Assistant Création de répertoire virtuel**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="20215-114">On the **Welcometo the Virtual Directory Creation Wizard page**, click **Next**.</span></span>  
  
5.  <span data-ttu-id="20215-115">Dans la page **Alias du répertoire virtuel** , dans la zone **Alias** , tapez **LOBWebApplication**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="20215-115">On the **Virtual Directory Alias** page, in the **Alias** box, type **LOBWebApplication**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="20215-116">Sur le **répertoire de contenu du Site Web** , cliquez sur **Parcourir**, sélectionnez le  **\<lecteur > : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\LOBWebApplication** dossier, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="20215-116">On the **Web Site Content Directory** page, click **Browse**, select the **\<drive>:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\LOBWebApplication** folder, and then click **OK**.</span></span> <span data-ttu-id="20215-117">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="20215-117">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="20215-118">Sur le **autorisations d’accès de répertoire virtuel** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="20215-118">On the **Virtual Directory Access Permissions** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="20215-119">Cliquez sur **Terminer** pour créer le répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="20215-119">Click **Finish** to create the virtual directory.</span></span>  
  
### <a name="excluding-lobwebapplication-from-sharepoint"></a><span data-ttu-id="20215-120">À l’exclusion de LOBWebApplication à partir de SharePoint</span><span class="sxs-lookup"><span data-stu-id="20215-120">Excluding LOBWebApplication from SharePoint</span></span>  
  
1.  <span data-ttu-id="20215-121">cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Administration centrale de SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="20215-121">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20215-122">Si vous avez déjà fait le didacticiel Double Action, vous serez déjà avez exclu le répertoire virtuel LOBWebApplication SharePoint pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="20215-122">If you have already done the Double Action tutorial, you will already have excluded the LOBWebApplication virtual directory from SharePoint for that tutorial.</span></span> <span data-ttu-id="20215-123">Dans ce cas, vous n’avez pas à effectuer ces étapes.</span><span class="sxs-lookup"><span data-stu-id="20215-123">If so, you do not have to perform these steps.</span></span>  
  
2.  <span data-ttu-id="20215-124">Sur le **Administration centrale** page, dans le **Configuration du serveur virtuel** section, sélectionnez **étendre ou mise à niveau le serveur virtuel**.</span><span class="sxs-lookup"><span data-stu-id="20215-124">On the **Central Administration** page, in the **Virtual Server Configuration** section, select **Extend or upgrade virtual server**.</span></span>  
  
3.  <span data-ttu-id="20215-125">Si l'URL configurée sur l'ordinateur ne s'affiche pas, cliquez sur **Liste complète**.</span><span class="sxs-lookup"><span data-stu-id="20215-125">If you do not see the URL configured on the computer, click **Complete list**.</span></span>  
  
4.  <span data-ttu-id="20215-126">Sélectionnez **Site Web par défaut**.</span><span class="sxs-lookup"><span data-stu-id="20215-126">Select **Default Web Site**.</span></span>  
  
5.  <span data-ttu-id="20215-127">Dans la section **Gestion du serveur virtuel** , cliquez sur **Définir les chemins d'accès gérés**.</span><span class="sxs-lookup"><span data-stu-id="20215-127">In the **Virtual Server Management** section, click **Define managed paths**.</span></span>  
  
6.  <span data-ttu-id="20215-128">Dans le **ajouter un nouveau chemin** section, dans le **chemin d’accès** , tapez « / LOBWebApplication ».</span><span class="sxs-lookup"><span data-stu-id="20215-128">In the **Add New Path** section, in the **Path** box, type "/LOBWebApplication".</span></span> <span data-ttu-id="20215-129">Pour **Type**, sélectionnez **Chemin d'accès exclu**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="20215-129">For **Type**, select **Excluded Path**, and then click **OK**.</span></span>  
  
### <a name="to-build-the-lobwebapplication-project"></a><span data-ttu-id="20215-130">Pour générer le projet LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="20215-130">To build the LOBWebApplication project</span></span>  
  
1.  <span data-ttu-id="20215-131">Démarrez **Microsoft Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="20215-131">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="20215-132">À partir de la **fichier** menu, pointez sur **ouvrir**, puis cliquez sur **Project\Solution**.</span><span class="sxs-lookup"><span data-stu-id="20215-132">From the **File** menu, point to **Open**, and then click **Project\Solution**.</span></span>  
  
3.  <span data-ttu-id="20215-133">Dans la boîte de dialogue Ouvrir un projet dans **Regarder dans**, atteindre  **\<lecteur > : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\ SDK\LOBWebApplication** , sélectionnez le **LOBWebApplication.sln** solution, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="20215-133">In the Open Project dialog box, in **Look In**, move to **\<drive>:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\ SDK\LOBWebApplication**, select the **LOBWebApplication.sln** solution, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="20215-134">Dans l’Explorateur de solutions, cliquez sur le nœud supérieur (http://localhost/LOBWebApplication), puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="20215-134">In Solution Explorer, right-click the top node (http://localhost/LOBWebApplication), and then click **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="20215-135">Dans la boîte de dialogue Ajouter une référence, cliquez sur **Parcourir** et déplacer vers  **\<lecteur > : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\bin**.</span><span class="sxs-lookup"><span data-stu-id="20215-135">In the Add Reference dialog box, click **Browse** and move to **\<drive>:\Program Files\Microsoft  BizTalk \<version> Accelerator for RosettaNet\bin**.</span></span>  
  
6.  <span data-ttu-id="20215-136">**Sélectionnez le Microsoft.Solutions.BTARN.ConfigurationManager.dll et Microsoft.Solutions.BTARN.Shared.dll** assemblys **puis cliquez sur OK.**</span><span class="sxs-lookup"><span data-stu-id="20215-136">**Select the Microsoft.Solutions.BTARN.ConfigurationManager.dll and Microsoft.Solutions.BTARN.Shared.dll** assemblies **and then click OK.**</span></span>  
  
7.  <span data-ttu-id="20215-137">Sur le **générer** menu, cliquez sur **générer le Site Web**.</span><span class="sxs-lookup"><span data-stu-id="20215-137">On the **Build** menu, click **Build Web Site**.</span></span>  
  
### <a name="to-run-the-lobwebapplication-project"></a><span data-ttu-id="20215-138">Pour exécuter le projet LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="20215-138">To run the LOBWebApplication project</span></span>  
  
1.  <span data-ttu-id="20215-139">Dans l’Explorateur de solutions, cliquez sur **default.aspx**, puis sélectionnez **définir comme Page de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="20215-139">In Solution Explorer, right-click **default.aspx**, and then select **Set As Start Page**.</span></span>  
  
2.  <span data-ttu-id="20215-140">Sur le **déboguer** menu, cliquez sur **démarrer sans débogage**.</span><span class="sxs-lookup"><span data-stu-id="20215-140">On the **Debug** menu, click **Start Without Debugging**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20215-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20215-141">See Also</span></span>  
 [<span data-ttu-id="20215-142">Test de la Solution</span><span class="sxs-lookup"><span data-stu-id="20215-142">Testing the Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/testing-the-solution.md)
---
title: "Étape 7 : Création et déploiement de l’exemple du Kit de développement LOBWebApplication | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double action tutorial, building solutions
- double action tutorial, deploying solutions
ms.assetid: f61de666-ebda-4831-9669-598e9284e4c1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92b101b47e2f83a0390a47cf6b1e4fc9a210950d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-7-building-and-deploying-the-lobwebapplication-sdk-sample"></a><span data-ttu-id="98c5f-102">Étape 7 : Création et déploiement de l’exemple du Kit de développement LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="98c5f-102">Step 7: Building and Deploying the LOBWebApplication SDK Sample</span></span>
<span data-ttu-id="98c5f-103">Dans cette étape, vous créez l'application métier utilisée par Fabrikam pour envoyer des demandes PIP (Partner Interface Process) à Contoso.</span><span class="sxs-lookup"><span data-stu-id="98c5f-103">In this step, you create the line-of-business (LOB) application that Fabrikam uses to submit Partner Interface Process (PIP) requests to Contoso.</span></span> <span data-ttu-id="98c5f-104">Vous pouvez trouver le projet LOBWebApplication dans les [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] dossier SDK.</span><span class="sxs-lookup"><span data-stu-id="98c5f-104">You can find the LOBWebApplication project in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK folder.</span></span> <span data-ttu-id="98c5f-105">Pour exécuter l’application Web, vous devez créer un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] répertoire virtuel de Internet Information Services (IIS), puis générer le projet LOBWebApplication.</span><span class="sxs-lookup"><span data-stu-id="98c5f-105">To run the Web application, you have to create a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Internet Information Services (IIS) virtual directory, and then build the LOBWebApplication project.</span></span>  
  
### <a name="to-create-the-lobwebapplication-virtual-directory"></a><span data-ttu-id="98c5f-106">Pour créer le répertoire virtuel LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="98c5f-106">To create the LOBWebApplication virtual directory</span></span>  
  
1.  <span data-ttu-id="98c5f-107">Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Gestionnaire des services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-107">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="98c5f-108">Dans la fenêtre Gestionnaire des Services Internet, développez **< nom_ordinateur > (ordinateur local)**, puis développez **Sites Web**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-108">In the Internet Information Services Manager window, expand **<computer_name> (local computer)**, and then expand **Web Sites**.</span></span>  
  
3.  <span data-ttu-id="98c5f-109">Cliquez avec le bouton droit sur **Site web par défaut**, pointez sur **Nouveau**, puis cliquez sur **Répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-109">Right-click **Default Web Site**, point to **New**, and then click **Virtual Directory**.</span></span>  
  
4.  <span data-ttu-id="98c5f-110">Sur le **Welcometo l’Assistant de création de répertoire virtuel** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-110">On the **Welcometo the Virtual Directory Creation Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="98c5f-111">Dans la page **Alias du répertoire virtuel** , dans la zone **Alias** , tapez **LOBWebApplication**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-111">On the **Virtual Directory Alias** page, in the **Alias** box, type **LOBWebApplication**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="98c5f-112">Dans la page **Répertoire de contenu du site Web** , cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-112">On the **Web Site Content Directory** page, click **Browse**.</span></span> <span data-ttu-id="98c5f-113">Dans la boîte de dialogue Rechercher un dossier, déplacer vers   ***\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\ LOBWebApplication**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-113">In the Browse For Folder dialog box, move to ***\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBWebApplication**, and then click **OK**.</span></span> <span data-ttu-id="98c5f-114">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-114">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="98c5f-115">Dans la page **Autorisations d'accès au répertoire virtuel** , décochez l'option **Lecture**, sélectionnez **Exécuter les scripts (tels que ASP)**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-115">On the **Virtual Directory Access Permissions** page, deselect **Read**, select **Run scripts (such as ASP)**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="98c5f-116">Dans la page **Vous avez terminé l'Assistant Création de répertoire virtuel** , cliquez sur **Terminer** pour créer le répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="98c5f-116">On the **You have successfully completed the Virtual Directory Creation Wizard** page, click **Finish** to create the virtual directory.</span></span>  
  
### <a name="to-exclude-the-lobwebapplication-web-site-from-the-sharepoint-configuration"></a><span data-ttu-id="98c5f-117">Pour exclure le site web LOBWebApplication de la configuration de SharePoint</span><span class="sxs-lookup"><span data-stu-id="98c5f-117">To exclude the LOBWebApplication Web site from the SharePoint configuration</span></span>  
  
1.  <span data-ttu-id="98c5f-118">cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Administration centrale de SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-118">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.</span></span>  
  
2.  <span data-ttu-id="98c5f-119">Dans la page web **Administration centrale** , dans la section **Configuration du serveur virtuel** , sélectionnez **Étendre ou mettre à niveau le serveur virtuel**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-119">On the **Central Administration** Web page, in the **Virtual Server Configuration** section, select **Extend or upgrade virtual server**.</span></span>  
  
3.  <span data-ttu-id="98c5f-120">Si l'URL configurée sur l'ordinateur ne s'affiche pas, cliquez sur **Liste complète**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-120">If you do not see the URL configured on the computer, click **Complete list**.</span></span>  
  
4.  <span data-ttu-id="98c5f-121">Dans la page **Liste des serveurs virtuels** , cliquez sur **Site web par défaut**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-121">On the **Virtual Server List** page, select **Default Web Site**.</span></span>  
  
5.  <span data-ttu-id="98c5f-122">Dans la section **Gestion du serveur virtuel** , cliquez sur **Définir les chemins d'accès gérés**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-122">In the **Virtual Server Management** section, click **Define managed paths**.</span></span>  
  
6.  <span data-ttu-id="98c5f-123">Dans la section **Ajouter un nouveau chemin d'accès** , dans la zone **Chemin d'accès** , tapez **/LOBWebApplication**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-123">In the **Add New Path** section, in the **Path** box, type **/LOBWebApplication**.</span></span>  
  
7.  <span data-ttu-id="98c5f-124">Pour **Type**, sélectionnez **Chemin d'accès exclu**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-124">For **Type**, select **Excluded Path**, and then click **OK**.</span></span>  
  
### <a name="to-build-the-lobwebapplication-project"></a><span data-ttu-id="98c5f-125">Pour générer le projet LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="98c5f-125">To build the LOBWebApplication project</span></span>  
  
1.  <span data-ttu-id="98c5f-126">Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Microsoft Visual Studio 2008**, puis cliquez sur **Microsoft Visual Studio 2008**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-126">Click **Start**, point to **All Programs**, point to **Microsoft Visual Studio 2008**, and then click **Microsoft Visual Studio 2008**.</span></span>  
  
2.  <span data-ttu-id="98c5f-127">Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-127">On the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="98c5f-128">Dans la boîte de dialogue Ouvrir un projet, accédez au   ***\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBWebApplication** , sélectionnez le **LOBWebApplication.sln** fichier solution, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-128">In the Open Project dialog box, move to ***\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBWebApplication**, select the **LOBWebApplication.sln** solution file, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="98c5f-129">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **http://localhost/LOBWebApplication**, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-129">In Solution Explorer, right-click **http://localhost/LOBWebApplication**, and then click **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="98c5f-130">Dans la boîte de dialogue Ajouter une référence, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-130">In the Add Reference dialog box, click **Browse**.</span></span> <span data-ttu-id="98c5f-131">Dans la boîte de dialogue Ajouter une référence, accédez au   ***\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\Bin** dossier.</span><span class="sxs-lookup"><span data-stu-id="98c5f-131">In the Add Reference dialog box, move to ***\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\Bin** folder.</span></span>  
  
6.  <span data-ttu-id="98c5f-132">Dans le dossier Bin, sélectionnez les assemblys **Microsoft.Solutions.BTARN.ConfigurationManager.dll** et **Microsoft.Solutions.BTARN.Shared.dll** , puis cliquez sur **Open.**</span><span class="sxs-lookup"><span data-stu-id="98c5f-132">From the Bin folder, select the **Microsoft.Solutions.BTARN.ConfigurationManager.dll** and **Microsoft.Solutions.BTARN.Shared.dll** assemblies, and then click **Open.**</span></span>  
  
7.  <span data-ttu-id="98c5f-133">Cliquez sur **OK** pour fermer la boîte de dialogue **Ajouter une référence** .</span><span class="sxs-lookup"><span data-stu-id="98c5f-133">Click **OK** to close the **Add Reference** dialog box.</span></span>  
  
8.  <span data-ttu-id="98c5f-134">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **Solution 'LOBWebApplication'** , puis cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-134">In Solution Explorer, right-click **Solution 'LOBWebApplication'** and then click **Build Solution**.</span></span>  
  
9. <span data-ttu-id="98c5f-135">Cliquez avec le bouton droit sur **default.aspx**, puis cliquez sur **Définir comme page de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="98c5f-135">Right-click **default.aspx**, and then click **Set as Start Page**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98c5f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98c5f-136">See Also</span></span>  
 [<span data-ttu-id="98c5f-137">Test du didacticiel DoubleAction</span><span class="sxs-lookup"><span data-stu-id="98c5f-137">Testing the Double Action Tutorial</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/testing-the-double-action-tutorial.md)
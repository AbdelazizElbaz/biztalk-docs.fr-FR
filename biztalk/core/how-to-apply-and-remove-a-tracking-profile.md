---
title: "Comment appliquer et supprimer un modèle de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, tracking profiles
- tracking profiles, testing
- tracking profiles, deleting
- testing, tracking profiles
ms.assetid: 77cef14b-c390-4da7-a383-b3abe414a168
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 955b2ccddb215b79fd7cdc7d51ed6f5160c297fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-apply-and-remove-a-tracking-profile"></a><span data-ttu-id="52821-102">Application et suppression d'un modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="52821-102">How to Apply and Remove a Tracking Profile</span></span>
<span data-ttu-id="52821-103">Une fois que vous avez créé ou modifié le modèle de suivi, l'étape suivante consiste à l'appliquer à une base de données de test et à en vérifier les résultats par le biais de tests intégrés.</span><span class="sxs-lookup"><span data-stu-id="52821-103">Once you have created or modified the tracking profile, the next step is to apply it to a test database and verify the result through integration testing.</span></span> <span data-ttu-id="52821-104">Vous pouvez lancer l'application du modèle de suivi depuis l'Éditeur de modèle de suivi ou en utilisant l'utilitaire de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="52821-104">You can apply the tracking profile from within Tracking Profile Editor (TPE) itself or by using the command line.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="52821-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="52821-105">Prerequisites</span></span>  
 <span data-ttu-id="52821-106">Un modèle de suivi créé à l'étape précédente et enregistré sur votre disque dur.</span><span class="sxs-lookup"><span data-stu-id="52821-106">A previously created tracking profile that you saved to your hard drive.</span></span>  
  
### <a name="to-apply-the-tracking-profile-from-within-the-tpe"></a><span data-ttu-id="52821-107">Pour appliquer le modèle de suivi depuis l'Éditeur</span><span class="sxs-lookup"><span data-stu-id="52821-107">To apply the tracking profile from within the TPE</span></span>  
  
1.  <span data-ttu-id="52821-108">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **éditeur**.</span><span class="sxs-lookup"><span data-stu-id="52821-108">Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Tracking Profile Editor**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="52821-109">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="52821-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="52821-110">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="52821-110">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="52821-111">Sur le **fichier** menu, cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="52821-111">On the **File** menu, click **Open**.</span></span> <span data-ttu-id="52821-112">Recherchez ensuite le fichier .btt approprié sur votre disque dur.</span><span class="sxs-lookup"><span data-stu-id="52821-112">Navigate to the correct .btt file on your hard drive.</span></span> <span data-ttu-id="52821-113">Cliquez sur **ouvrir** à le charger.</span><span class="sxs-lookup"><span data-stu-id="52821-113">Click **Open** to load it.</span></span>  
  
3.  <span data-ttu-id="52821-114">Sur le **outils** menu, cliquez sur **appliquer le modèle de suivi** pour appliquer le fichier .btt à une base de données de gestion que vous avez définie à partir de la **définir la base de données de gestion** élément de menu dans le **Outils** menu.</span><span class="sxs-lookup"><span data-stu-id="52821-114">On the **Tools** menu, click **Apply Tracking Profile** to apply the .btt file to a management database that you have set from the **Set Management Database** menu item on the **Tools** menu.</span></span> <span data-ttu-id="52821-115">Vérifiez le résultat à l'aide du test intégré.</span><span class="sxs-lookup"><span data-stu-id="52821-115">Verify the result through integration testing.</span></span>  
  
4.  <span data-ttu-id="52821-116">Avertissez la personne de votre organisation responsable du déploiement que les tests du modèle de suivi sont concluants et que le modèle est prêt à être déployé.</span><span class="sxs-lookup"><span data-stu-id="52821-116">Notify the person in your organization responsible for deployment that the tracking profile tests correctly and is ready for deployment.</span></span>  
  
### <a name="to-apply-the-tracking-profile-from-the-command-line"></a><span data-ttu-id="52821-117">Pour appliquer le modèle de suivi à partir de l'utilitaire de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="52821-117">To apply the tracking profile from the command line</span></span>  
  
-   <span data-ttu-id="52821-118">À l'invite de commandes, exécutez l'outil dont le fichier bttdeploy.exe est situé dans le dossier \Tracking comme suit :</span><span class="sxs-lookup"><span data-stu-id="52821-118">From the command prompt, run the bttdeploy.exe tool located in the \Tracking folder as follows:</span></span>  
  
    ```  
    bttdeploy.exe <profile name>.btt  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="52821-119">Vous devez disposer des privilèges d'administrateur BizTalk pour utiliser cet outil.</span><span class="sxs-lookup"><span data-stu-id="52821-119">You must have BizTalk Administrator privileges to use this tool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52821-120">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="52821-120">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="52821-121">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="52821-121">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="52821-122">Au cours du déploiement, l'outil bttdeploy vérifie la version d'assembly contenue dans les modèles de suivi et la compare à la version de l'assembly déployé.</span><span class="sxs-lookup"><span data-stu-id="52821-122">During the deployment, bttdeploy verifies the assembly version contained in the tracking profiles and matches it to the version of the deployed assembly.</span></span> <span data-ttu-id="52821-123">Cet outil échoue si l'assembly n'est pas déployé au moment de son exécution.</span><span class="sxs-lookup"><span data-stu-id="52821-123">Bttdeploy will fail if the assembly is not currently deployed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="52821-124">Lors de l'application d'un modèle de suivi à l'aide d'un utilitaire de ligne de commande, l'outil bttdeploy applique le modèle à la base de données de gestion BizTalk que vous avez indiquée lorsque vous avez exécuté l'Assistant Configuration.</span><span class="sxs-lookup"><span data-stu-id="52821-124">When applying a tracking profile from the command line, bttdeploy applies the profile to the BizTalk Management database that you indicated when you ran the configuration wizard.</span></span> <span data-ttu-id="52821-125">Si vous indiquez une base de données différente pour l'option Définir la base de données de gestion dans l'Éditeur de modèle de suivi, elle est utilisée.</span><span class="sxs-lookup"><span data-stu-id="52821-125">If you specify a different database setting in the Tracking Profile Editor Option "Set Management Database," then that setting is used.</span></span> <span data-ttu-id="52821-126">Si vous spécifiez un serveur et une base de données de gestion pour l'option de la ligne de commande de bttdeploy, cette option écrase toutes les autres.</span><span class="sxs-lookup"><span data-stu-id="52821-126">If you specify a management server and database as part of the command line option to bttdeploy, then the command line option overrides everything else.</span></span> <span data-ttu-id="52821-127">Pour plus d’informations sur l’utilisation de bttdeploy, consultez [utilitaire](../core/tracking-profile-deployment-utility.md).</span><span class="sxs-lookup"><span data-stu-id="52821-127">For more information about using bttdeploy, see [Tracking Profile Deployment Utility](../core/tracking-profile-deployment-utility.md).</span></span>  
  
### <a name="to-remove-a-tracking-profile"></a><span data-ttu-id="52821-128">Pour supprimer un modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="52821-128">To remove a tracking profile</span></span>  
  
1.  <span data-ttu-id="52821-129">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **éditeur**.</span><span class="sxs-lookup"><span data-stu-id="52821-129">Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Tracking Profile Editor**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="52821-130">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="52821-130">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="52821-131">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="52821-131">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="52821-132">Sur le **fichier** menu, cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="52821-132">On the **File** menu, click **Open**.</span></span> <span data-ttu-id="52821-133">Recherchez ensuite le fichier .btt approprié sur votre disque dur.</span><span class="sxs-lookup"><span data-stu-id="52821-133">Navigate to the correct .btt file on your hard drive.</span></span> <span data-ttu-id="52821-134">Cliquez sur **ouvrir** à le charger.</span><span class="sxs-lookup"><span data-stu-id="52821-134">Click **Open** to load it.</span></span>  
  
3.  <span data-ttu-id="52821-135">Sur le **outils** menu, cliquez sur **supprimer le modèle de suivi** pour supprimer le modèle de suivi basé sur le fichier .btt à partir de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="52821-135">On the **Tools** menu, click **Remove Tracking Profile** to remove the tracking profile based on the .btt file from the BizTalk Management database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52821-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52821-136">See Also</span></span>  
 [<span data-ttu-id="52821-137">Création de modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="52821-137">Creating Tracking Profiles</span></span>](../core/creating-tracking-profiles.md)
---
title: "Résolution des problèmes de mise à niveau et de migration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading, troubleshooting
- troubleshooting, upgrading
- troubleshooting, migrating
- migrating, troubleshooting
ms.assetid: 6e6c0ff9-7897-4de6-9e9b-b502b3a1785b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c063e2e4ba213c3f72cbfb4977a3463d16b0a726
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="migration-and-upgrade-troubleshooting"></a><span data-ttu-id="976be-102">Migration et la résolution des problèmes de mise à niveau</span><span class="sxs-lookup"><span data-stu-id="976be-102">Migration and Upgrade Troubleshooting</span></span>
## <a name="assemblies-need-to-be-undeployed-before-an-upgrade"></a><span data-ttu-id="976be-103">Les assemblys doivent être annulé avant une mise à niveau</span><span class="sxs-lookup"><span data-stu-id="976be-103">Assemblies need to be undeployed before an upgrade</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="976be-104">Symptôme</span><span class="sxs-lookup"><span data-stu-id="976be-104">Symptom</span></span>  
 <span data-ttu-id="976be-105">Lorsque vous essayez de mettre à niveau d’A4SWIFT, le processus de mise à niveau échoue.</span><span class="sxs-lookup"><span data-stu-id="976be-105">When you attempt to upgrade A4SWIFT, the upgrade process fails.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="976be-106">Cause possible</span><span class="sxs-lookup"><span data-stu-id="976be-106">Possible Cause</span></span>  
 <span data-ttu-id="976be-107">Les assemblys A4SWIFT suivants sont toujours déployés lors de la mise à niveau est effectuée : Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration, Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas, Microsoft.Solutions.FinancialServices.SWIFT.MrsrService.</span><span class="sxs-lookup"><span data-stu-id="976be-107">The following A4SWIFT assemblies are still deployed when the upgrade is done:  Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration, Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas, Microsoft.Solutions.FinancialServices.SWIFT.MrsrService.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="976be-108">Il est inutile de redéployer Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.</span><span class="sxs-lookup"><span data-stu-id="976be-108">You do not have to redeploy Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.</span></span> <span data-ttu-id="976be-109">Le programme d’installation redéploie cet assembly.</span><span class="sxs-lookup"><span data-stu-id="976be-109">The installation program redeploys that assembly.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="976be-110">Solution</span><span class="sxs-lookup"><span data-stu-id="976be-110">Solution</span></span>  
 <span data-ttu-id="976be-111">Annuler le déploiement manuellement les quatre assemblys A4SWIFT dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="976be-111">Manually undeploy the four A4SWIFT assemblies in the following order:</span></span>  
  
-   <span data-ttu-id="976be-112">Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration</span><span class="sxs-lookup"><span data-stu-id="976be-112">Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration</span></span>  
  
-   <span data-ttu-id="976be-113">Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas</span><span class="sxs-lookup"><span data-stu-id="976be-113">Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas</span></span>  
  
-   <span data-ttu-id="976be-114">Microsoft.Solutions.FinancialServices.SWIFT.MrsrService.</span><span class="sxs-lookup"><span data-stu-id="976be-114">Microsoft.Solutions.FinancialServices.SWIFT.MrsrService.</span></span>  
  
 <span data-ttu-id="976be-115">Une fois que vous avez mis à niveau, redéployer ces assemblys (à l’aide de **BTSTask.exe**) dans l’ordre inverse.</span><span class="sxs-lookup"><span data-stu-id="976be-115">After you have upgraded, redeploy these assemblies (using **BTSTask.exe**) in the reverse order.</span></span>  
  
## <a name="an-upgrade-removes-access-permissions-for-the-service-folder"></a><span data-ttu-id="976be-116">Une mise à niveau supprime les autorisations d’accès pour le dossier du Service</span><span class="sxs-lookup"><span data-stu-id="976be-116">An upgrade removes access permissions for the Service folder</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="976be-117">Symptôme</span><span class="sxs-lookup"><span data-stu-id="976be-117">Symptom</span></span>  
 <span data-ttu-id="976be-118">Après une mise à niveau vers [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], l’autorisation d’accès pour le BizTalk Accelerator pour SWIFT\Service dossier %programfiles%\Microsoft est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="976be-118">After an upgrade to [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], the access permission for the %programfiles%\Microsoft BizTalk Accelerator for SWIFT\Service folder is incorrect.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="976be-119">Cause possible</span><span class="sxs-lookup"><span data-stu-id="976be-119">Possible Cause</span></span>  
 <span data-ttu-id="976be-120">Lorsque vous mettez à niveau vers [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], le processus de mise à niveau supprime les autorisations d’accès pour les groupes administrateurs d’A4SWIFT et les utilisateurs d’A4SWIFT de BizTalk Accelerator pour SWIFT\Service dossier %programfiles%\Microsoft.</span><span class="sxs-lookup"><span data-stu-id="976be-120">When you upgrade to [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], the upgrade process removes access permissions for the A4SWIFT Administrators and A4SWIFT Users groups from the %programfiles%\Microsoft BizTalk Accelerator for SWIFT\Service folder.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="976be-121">Solution</span><span class="sxs-lookup"><span data-stu-id="976be-121">Solution</span></span>  
 <span data-ttu-id="976be-122">Si vous rencontrez ce problème, définir manuellement les autorisations d’accès suivants pour le dossier du Service :</span><span class="sxs-lookup"><span data-stu-id="976be-122">If you encounter this problem, manually set the following access permissions for the Service folder:</span></span>  
  
|<span data-ttu-id="976be-123">Groupe ou nom d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="976be-123">Group or User Name</span></span>|<span data-ttu-id="976be-124">Autorisation</span><span class="sxs-lookup"><span data-stu-id="976be-124">Permission</span></span>|  
|------------------------|----------------|  
|<span data-ttu-id="976be-125">Administrateurs d’A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="976be-125">A4SWIFT Administrators</span></span>|<span data-ttu-id="976be-126">Contrôle total</span><span class="sxs-lookup"><span data-stu-id="976be-126">Full Control</span></span>|  
|<span data-ttu-id="976be-127">Utilisateurs d’A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="976be-127">A4SWIFT Users</span></span>|<span data-ttu-id="976be-128">Lire et exécuter</span><span class="sxs-lookup"><span data-stu-id="976be-128">Read & Execute</span></span>|  
  
 <span data-ttu-id="976be-129">Pour définir ces autorisations, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="976be-129">To set these permissions, proceed as follows:</span></span>  
  
 <span data-ttu-id="976be-130">Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, accédez à *% ProgramFiles%*\Microsoft BizTalk Accelerator pour SWIFT\Service.</span><span class="sxs-lookup"><span data-stu-id="976be-130">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Service.</span></span>  
  
1.  <span data-ttu-id="976be-131">Cliquez sur le dossier du Service, cliquez sur **propriétés**, puis cliquez sur le **sécurité** onglet.</span><span class="sxs-lookup"><span data-stu-id="976be-131">Right-click the Service folder, click **Properties**, and then click the **Security** tab.</span></span>  
  
2.  <span data-ttu-id="976be-132">Dans le volet de noms utilisateur ou de groupe, de la boîte de dialogue Propriétés du Service, cliquez sur **ajouter**, entrez   ***\<nom du serveur >*\A4SWIFT administrateurs**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="976be-132">In the Group or user names pane of the Service Properties dialog box, click **Add**, enter ***\<server name>*\A4SWIFT Administrators**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="976be-133">Si le groupe d’administrateurs d’A4SWIFT est un groupe de domaine, entrez   ***\<nom de domaine >*\A4SWIFT administrateurs**.</span><span class="sxs-lookup"><span data-stu-id="976be-133">If the A4SWIFT Administrators group is a domain group, enter ***\<domain name>*\A4SWIFT Administrators**.</span></span>  
  
3.  <span data-ttu-id="976be-134">Répétez l’étape 2 pour   ***\<nom du serveur >*\A4SWIFT utilisateurs**, ou  **\<* nom de domaine*> \A4SWIFT Les utilisateurs ** si le groupe utilisateurs d’A4SWIFT est un groupe de domaine.</span><span class="sxs-lookup"><span data-stu-id="976be-134">Repeat step 2 for ***\<server name>*\A4SWIFT Users**, or **\<*domain name*>\A4SWIFT Users** if the A4SWIFT Users group is a domain group.</span></span>  
  
4.  <span data-ttu-id="976be-135">Dans le volet noms d’utilisateur ou de groupe, sélectionnez **A4SWIFT administrateurs**.</span><span class="sxs-lookup"><span data-stu-id="976be-135">In the Group or user names pane, select **A4SWIFT Administrators**.</span></span> <span data-ttu-id="976be-136">Dans le volet d’autorisations, sélectionnez **autoriser** pour **contrôle total**.</span><span class="sxs-lookup"><span data-stu-id="976be-136">In the Permissions pane, select **Allow** for **Full Control**.</span></span>  
  
5.  <span data-ttu-id="976be-137">Dans le volet noms d’utilisateur ou de groupe, sélectionnez **A4SWIFT utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="976be-137">In the Group or user names pane, select **A4SWIFT Users**.</span></span> <span data-ttu-id="976be-138">Dans le volet d’autorisations, cliquez sur **autoriser** pour **lire & exécuter**, **contenu du dossier**, et **en lecture**.</span><span class="sxs-lookup"><span data-stu-id="976be-138">In the Permissions pane, click **Allow** for **Read & Execute**, **List Folder Contents**, and **Read**.</span></span>  
  
6.  <span data-ttu-id="976be-139">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="976be-139">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="976be-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="976be-140">See Also</span></span>  
 [<span data-ttu-id="976be-141">Résolution des problèmes : Problèmes et résolutions</span><span class="sxs-lookup"><span data-stu-id="976be-141">Troubleshooting: Issues and Resolutions</span></span>](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)
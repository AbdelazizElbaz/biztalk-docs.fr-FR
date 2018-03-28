---
title: Comment spécifier les administrateurs de l’authentification unique et les applications associées à des administrateurs de comptes | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- administrator accounts, SSO
- enabling, SSO
- SSO, enabling
- disabling, SSO
- SSO, disabling
- managing [SSO], configuring administrator accounts
- managing [SSO], enabling
- managing [SSO], disabling
- SSO, administrator accounts
ms.assetid: 6c300e09-b781-45de-b2da-b1083164a1c0
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c96e2d99bd6071098a65b3635bb466de44a455d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-specify-sso-administrators-and-affiliate-administrators-accounts"></a><span data-ttu-id="71ab3-102">Comment spécifier les administrateurs de l’authentification unique et les applications associées à des administrateurs de comptes</span><span class="sxs-lookup"><span data-stu-id="71ab3-102">How to Specify SSO Administrators and Affiliate Administrators Accounts</span></span>
<span data-ttu-id="71ab3-103">Les comptes Administrateurs SSO de l'entreprise et Administrateurs d'applications associées à SSO peuvent être des comptes de groupe d'hôtes ou individuels.</span><span class="sxs-lookup"><span data-stu-id="71ab3-103">The Enterprise Single Sign-On (SSO) Administrators and Affiliate Administrators accounts can be host group or individual accounts.</span></span> <span data-ttu-id="71ab3-104">Vous devez créer ces comptes avant de configurer le système SSO.</span><span class="sxs-lookup"><span data-stu-id="71ab3-104">You must create these accounts before you configure the SSO system.</span></span>  
  
 <span data-ttu-id="71ab3-105">Si vous utilisez des comptes de domaine, vous devez créer ces deux comptes en tant que groupes de sécurité globale de domaine au sein du contrôleur de domaine.</span><span class="sxs-lookup"><span data-stu-id="71ab3-105">When using domain accounts, you must create the SSO Administrators and SSO Affiliate Administrators accounts as a domain global security groups in the domain controller.</span></span> <span data-ttu-id="71ab3-106">La création de ces comptes incombe à l'administrateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="71ab3-106">The domain administrator must create these accounts.</span></span>  
  
 <span data-ttu-id="71ab3-107">Vous devez spécifier les comptes Administrateurs SSO et Administrateurs d'applications associées à SSO dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="71ab3-107">You must specify the Single Sign-On Administrators and Affiliate Administrators accounts in the SSO database.</span></span> <span data-ttu-id="71ab3-108">Vous devez désactiver le système SSO avant de mettre à jour la base de données SSO avec le groupe Administrateurs SSO.</span><span class="sxs-lookup"><span data-stu-id="71ab3-108">You must disable the Single Sign-On system before you update the SSO database with the SSO Administrators group.</span></span>  
  
 <span data-ttu-id="71ab3-109">Voici un exemple de code XML permettant de mettre à jour la base de données SSO :</span><span class="sxs-lookup"><span data-stu-id="71ab3-109">The following XML code shows a sample XML for updating the SSO database:</span></span>  
  
```  
<sso>  
<globalInfo>  
<ssoAdminAccount>Domain\Accountname</ssoAdminAccount>  
<ssoAffiliateAdminAccount>Domain\Accountname</ssoAffiliateAdminAccount>  
</globalInfo>  
</sso>  
```  
  
> [!NOTE]
>  <span data-ttu-id="71ab3-110">L'Assistant Configuration spécifie automatiquement les groupes Administrateurs SSO et Administrateurs d'applications associées à SSO dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="71ab3-110">The Configuration Wizard automatically specifies the SSO administrator and SSO affiliate administrator groups in the SSO database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71ab3-111">S'il est impossible de configurer l'authentification unique, il est recommandé de vérifier l'utilisation des comptes de domaine locaux dans un domaine en mode mixte.</span><span class="sxs-lookup"><span data-stu-id="71ab3-111">If SSO does not configure, users should check whether Domain Local Accounts are being used in a mixed-mode domain.</span></span>  
  
### <a name="to-disable-the-enterprise-single-sign-on-system-using-the-mmc-snap-in"></a><span data-ttu-id="71ab3-112">Pour désactiver le système d'authentification unique de l'entreprise à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="71ab3-112">To disable the Enterprise Single Sign-On system using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="71ab3-113">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="71ab3-113">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="71ab3-114">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="71ab3-114">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="71ab3-115">Avec le bouton droit **système**, puis cliquez sur **désactiver**.</span><span class="sxs-lookup"><span data-stu-id="71ab3-115">Right-click **System**, and then click **Disable**.</span></span>  
  
### <a name="to-disable-the-enterprise-single-sign-on-system-using-the-command-line"></a><span data-ttu-id="71ab3-116">Pour désactiver le système d'authentification unique de l'entreprise à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="71ab3-116">To disable the Enterprise Single Sign-On system using the command line</span></span>  
  
1.  <span data-ttu-id="71ab3-117">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="71ab3-117">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="71ab3-118">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="71ab3-118">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="71ab3-119">Le répertoire d’installation par défaut est \< *lecteur*\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="71ab3-119">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="71ab3-120">Type **ssomanage** –**disablesso**.</span><span class="sxs-lookup"><span data-stu-id="71ab3-120">Type **ssomanage** –**disablesso**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="71ab3-121">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="71ab3-121">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-update-the-sso-database-using-the-mmc-snap-in"></a><span data-ttu-id="71ab3-122">Pour mettre à jour la base de données SSO à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="71ab3-122">To update the SSO database using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="71ab3-123">Sur le **Démarrer** menu, cliquez sur **tous les programmes**, **Microsoft Enterprise Single Sign-On**, puis **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="71ab3-123">On the **Start** menu, click **All Programs**, **Microsoft Enterprise Single Sign-On**, and then **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="71ab3-124">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="71ab3-124">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="71ab3-125">Avec le bouton droit **système**, puis cliquez sur **mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="71ab3-125">Right-click **System**, and then click **Update**.</span></span>  
  
### <a name="to-update-the-sso-database-using-the-command-line"></a><span data-ttu-id="71ab3-126">Pour mettre à jour la base de données SSO à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="71ab3-126">To update the SSO database using the command line</span></span>  
  
1.  <span data-ttu-id="71ab3-127">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="71ab3-127">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="71ab3-128">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="71ab3-128">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="71ab3-129">Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="71ab3-129">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="71ab3-130">Type ** ssomanage-updatedb *\<fichier de mise à jour\>***, où *\<fichier de mise à jour\>* est le chemin d’accès et le nom du fichier XML.</span><span class="sxs-lookup"><span data-stu-id="71ab3-130">Type **ssomanage –updatedb *\<update file\>***, where *\<update file\>* is the path and name of the XML file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="71ab3-131">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="71ab3-131">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-enable-the-enterprise-single-sign-on-system-using-the-mmc-snap-in"></a><span data-ttu-id="71ab3-132">Pour activer le système d'authentification unique de l'entreprise à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="71ab3-132">To enable the Enterprise Single Sign-On system using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="71ab3-133">Sur le **Démarrer** menu, cliquez sur **tous les programmes**, **Microsoft Enterprise Single Sign-On**, puis **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="71ab3-133">On the **Start** menu, click **All Programs**, **Microsoft Enterprise Single Sign-On**, and then **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="71ab3-134">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="71ab3-134">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="71ab3-135">Avec le bouton droit **système**, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="71ab3-135">Right-click **System**, and then click **Enable**.</span></span>  
  
### <a name="to-enable-the-enterprise-single-sign-on-system-using-the-command-line"></a><span data-ttu-id="71ab3-136">Pour activer le système d'authentification unique de l'entreprise à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="71ab3-136">To enable the Enterprise Single Sign-On system using the command line</span></span>  
  
1.  <span data-ttu-id="71ab3-137">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="71ab3-137">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="71ab3-138">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="71ab3-138">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="71ab3-139">Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="71ab3-139">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="71ab3-140">Type **ssomanage – enablesso**.</span><span class="sxs-lookup"><span data-stu-id="71ab3-140">Type **ssomanage –enablesso**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="71ab3-141">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="71ab3-141">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71ab3-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71ab3-142">See Also</span></span>  
 [<span data-ttu-id="71ab3-143">Groupes d’utilisateurs de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="71ab3-143">SSO User Groups</span></span>](../core/sso-user-groups.md)
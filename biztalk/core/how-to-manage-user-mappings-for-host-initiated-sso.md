---
title: "Pour gérer les mappages utilisateur pour l’hôte authentification unique initiée par | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps, host initiated SSO
- host initiated SSO, user maps
ms.assetid: 6b05249e-da35-475b-9c23-5eb556013d57
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0bf65bdb3de30d5b701946215b5c7ae7d40d828
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-manage-user-mappings-for-host-initiated-sso"></a><span data-ttu-id="6eae5-102">Authentification unique initiée par le comment gérer des mappages utilisateur pour l’hôte</span><span class="sxs-lookup"><span data-stu-id="6eae5-102">How to Manage User Mappings for Host Initiated SSO</span></span>
<span data-ttu-id="6eae5-103">Les procédures suivantes permettent de créer des mappages, de définir les informations d'identification et d'activer ou de désactiver le mappage.</span><span class="sxs-lookup"><span data-stu-id="6eae5-103">Use the following procedures to create mappings, set credentials, and enable or disable mapping.</span></span>  
  
### <a name="to-manage-user-mappings-for-host-initiated-sso-using-the-mmc-snap-in"></a><span data-ttu-id="6eae5-104">Pour gérer les mappages utilisateur pour l'authentification unique initiée par l'hôte à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="6eae5-104">To manage user mappings for host initiated SSO using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="6eae5-105">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-105">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="6eae5-106">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="6eae5-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="6eae5-107">Dans le volet d’étendue, cliquez sur **Applications associées**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-107">In the scope pane, click **Affiliate Applications**.</span></span>  
  
4.  <span data-ttu-id="6eae5-108">Dans le volet Détails, cliquez avec le bouton droit sur l'application associée, puis choisissez l'élément de menu approprié pour votre action.</span><span class="sxs-lookup"><span data-stu-id="6eae5-108">In the details pane, right-click the affiliate application, and then choose the appropriate menu item for your action.</span></span>  
  
### <a name="to-create-mappings-in-host-initiated-sso-using-the-command-line"></a><span data-ttu-id="6eae5-109">Pour créer des mappages pour l'authentification unique initiée par l'hôte à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="6eae5-109">To create mappings in host initiated SSO using the command line</span></span>  
  
1.  <span data-ttu-id="6eae5-110">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-110">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="6eae5-111">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-111">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6eae5-112">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6eae5-112">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6eae5-113">La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="6eae5-113">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="6eae5-114">Type **ssomanage – createmappings \<fichier de mappage\>**, où **fichier de mappage >** est le nom du fichier xml.</span><span class="sxs-lookup"><span data-stu-id="6eae5-114">Type **ssomanage –createmappings \<mapping file\>**, where **mapping file>** is the name of the xml file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6eae5-115">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6eae5-115">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
     <span data-ttu-id="6eae5-116">Voici un exemple de fichier de mappage :</span><span class="sxs-lookup"><span data-stu-id="6eae5-116">A sample mapping file is shown below:</span></span>  
  
    ```  
    <SSO>  
      <mapping>  
        <windowsDomain>DomainName</windowsDomain>  
        <windowsUserId>UserA</windowsUserId>  
        <externalApplication>SSOApplication</externalApplication>  
    <externalUserId>ExternalUserID that corresponds to UserA</externalUserId>  
      </mapping>  
    </SSO>  
  
    ```  
  
 <span data-ttu-id="6eae5-117">Lorsque la fonctionnalité de validation du mot de passe est activée pour l'application associée, il est nécessaire de définir les informations d'identification comme suit :</span><span class="sxs-lookup"><span data-stu-id="6eae5-117">When the Validate Password feature is enabled for the affiliate application, it is necessary to set credentials, as follows:</span></span>  
  
#### <a name="to-set-credentials-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="6eae5-118">Pour définir les informations d'identification des applications associées de type individuel à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="6eae5-118">To set credentials for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="6eae5-119">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-119">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="6eae5-120">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-120">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6eae5-121">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6eae5-121">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6eae5-122">La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="6eae5-122">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="6eae5-123">Type **ssomanage - setcredentials \<nom du compte Windows\> \<nom de l’application\>**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-123">Type **ssomanage -setcredentials \<Windows account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6eae5-124">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6eae5-124">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-set-credentials-for-host-group-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="6eae5-125">Pour définir les informations d'identification des applications associées de type groupe d'hôtes à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="6eae5-125">To set credentials for host group type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="6eae5-126">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-126">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="6eae5-127">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-127">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6eae5-128">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6eae5-128">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6eae5-129">La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="6eae5-129">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="6eae5-130">Type **ssomanage - setcredentials \<nom du compte externe\> \<nom de l’application\>**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-130">Type **ssomanage -setcredentials \<external account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6eae5-131">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6eae5-131">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-enable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="6eae5-132">Pour activer les mappages des applications associées de type individuel à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="6eae5-132">To enable mappings for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="6eae5-133">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-133">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="6eae5-134">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-134">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6eae5-135">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6eae5-135">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6eae5-136">La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="6eae5-136">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="6eae5-137">Type **ssomanage - enablemapping \<nom du compte Windows\> \<nom de l’application\>**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-137">Type **ssomanage -enablemapping \<Windows account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6eae5-138">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6eae5-138">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-disable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="6eae5-139">Pour désactiver les mappages des applications associées de type individuel à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="6eae5-139">To disable mappings for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="6eae5-140">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-140">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="6eae5-141">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-141">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6eae5-142">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6eae5-142">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6eae5-143">La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="6eae5-143">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="6eae5-144">Type **ssomanage - disablemapping \<nom du compte Windows\> \<nom de l’application\>**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-144">Type **ssomanage -disablemapping \<Windows account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6eae5-145">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6eae5-145">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-enable-mappings-for-host-group-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="6eae5-146">Pour activer les mappages des applications associées de type groupe d'hôtes à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="6eae5-146">To enable mappings for host group type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="6eae5-147">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-147">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="6eae5-148">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-148">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6eae5-149">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6eae5-149">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6eae5-150">La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="6eae5-150">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="6eae5-151">Type **ssomanage - enablemapping \<nom du compte externe\> \<nom de l’application\>**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-151">Type **ssomanage -enablemapping \<external account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6eae5-152">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6eae5-152">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-disable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="6eae5-153">Pour désactiver les mappages des applications associées de type individuel à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="6eae5-153">To disable mappings for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="6eae5-154">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-154">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="6eae5-155">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-155">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6eae5-156">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6eae5-156">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6eae5-157">La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="6eae5-157">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="6eae5-158">Type **ssomanage - disablemapping \<nom du compte externe\> \<nom de l’application\>**.</span><span class="sxs-lookup"><span data-stu-id="6eae5-158">Type **ssomanage -disablemapping \<external account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6eae5-159">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6eae5-159">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eae5-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6eae5-160">See Also</span></span>  
 [<span data-ttu-id="6eae5-161">Authentification unique initiée par l’hôte</span><span class="sxs-lookup"><span data-stu-id="6eae5-161">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)
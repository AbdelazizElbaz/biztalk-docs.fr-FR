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
ms.openlocfilehash: 4dc65f584bdd474314cd976edc586d0ed60f0505
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-user-mappings-for-host-initiated-sso"></a><span data-ttu-id="be870-102">Authentification unique initiée par le comment gérer des mappages utilisateur pour l’hôte</span><span class="sxs-lookup"><span data-stu-id="be870-102">How to Manage User Mappings for Host Initiated SSO</span></span>
<span data-ttu-id="be870-103">Les procédures suivantes permettent de créer des mappages, de définir les informations d'identification et d'activer ou de désactiver le mappage.</span><span class="sxs-lookup"><span data-stu-id="be870-103">Use the following procedures to create mappings, set credentials, and enable or disable mapping.</span></span>  
  
### <a name="to-manage-user-mappings-for-host-initiated-sso-using-the-mmc-snap-in"></a><span data-ttu-id="be870-104">Pour gérer les mappages utilisateur pour l'authentification unique initiée par l'hôte à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="be870-104">To manage user mappings for host initiated SSO using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="be870-105">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="be870-105">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="be870-106">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="be870-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="be870-107">Dans le volet d’étendue, cliquez sur **Applications associées**.</span><span class="sxs-lookup"><span data-stu-id="be870-107">In the scope pane, click **Affiliate Applications**.</span></span>  
  
4.  <span data-ttu-id="be870-108">Dans le volet Détails, cliquez avec le bouton droit sur l'application associée, puis choisissez l'élément de menu approprié pour votre action.</span><span class="sxs-lookup"><span data-stu-id="be870-108">In the details pane, right-click the affiliate application, and then choose the appropriate menu item for your action.</span></span>  
  
### <a name="to-create-mappings-in-host-initiated-sso-using-the-command-line"></a><span data-ttu-id="be870-109">Pour créer des mappages pour l'authentification unique initiée par l'hôte à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="be870-109">To create mappings in host initiated SSO using the command line</span></span>  
  
1.  <span data-ttu-id="be870-110">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="be870-110">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="be870-111">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="be870-111">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="be870-112">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="be870-112">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="be870-113">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="be870-113">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="be870-114">Type **ssomanage – createmappings \<fichier de mappage >**, où **fichier de mappage >** est le nom du fichier xml.</span><span class="sxs-lookup"><span data-stu-id="be870-114">Type **ssomanage –createmappings \<mapping file>**, where **mapping file>** is the name of the xml file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be870-115">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="be870-115">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
     <span data-ttu-id="be870-116">Voici un exemple de fichier de mappage :</span><span class="sxs-lookup"><span data-stu-id="be870-116">A sample mapping file is shown below:</span></span>  
  
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
  
 <span data-ttu-id="be870-117">Lorsque la fonctionnalité de validation du mot de passe est activée pour l'application associée, il est nécessaire de définir les informations d'identification comme suit :</span><span class="sxs-lookup"><span data-stu-id="be870-117">When the Validate Password feature is enabled for the affiliate application, it is necessary to set credentials, as follows:</span></span>  
  
#### <a name="to-set-credentials-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="be870-118">Pour définir les informations d'identification des applications associées de type individuel à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="be870-118">To set credentials for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="be870-119">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="be870-119">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="be870-120">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="be870-120">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="be870-121">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="be870-121">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="be870-122">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="be870-122">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="be870-123">Type **ssomanage - setcredentials \<nom de compte Windows > \<nom de l’application >**.</span><span class="sxs-lookup"><span data-stu-id="be870-123">Type **ssomanage -setcredentials \<Windows account name> \<application name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be870-124">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="be870-124">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-set-credentials-for-host-group-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="be870-125">Pour définir les informations d'identification des applications associées de type groupe d'hôtes à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="be870-125">To set credentials for host group type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="be870-126">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="be870-126">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="be870-127">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="be870-127">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="be870-128">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="be870-128">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="be870-129">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="be870-129">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="be870-130">Type **ssomanage - setcredentials \<nom du compte externe > \<nom de l’application >**.</span><span class="sxs-lookup"><span data-stu-id="be870-130">Type **ssomanage -setcredentials \<external account name> \<application name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be870-131">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="be870-131">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-enable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="be870-132">Pour activer les mappages des applications associées de type individuel à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="be870-132">To enable mappings for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="be870-133">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="be870-133">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="be870-134">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="be870-134">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="be870-135">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="be870-135">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="be870-136">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="be870-136">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="be870-137">Type **ssomanage - enablemapping \<nom de compte Windows > \<nom de l’application >**.</span><span class="sxs-lookup"><span data-stu-id="be870-137">Type **ssomanage -enablemapping \<Windows account name> \<application name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be870-138">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="be870-138">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-disable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="be870-139">Pour désactiver les mappages des applications associées de type individuel à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="be870-139">To disable mappings for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="be870-140">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="be870-140">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="be870-141">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="be870-141">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="be870-142">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="be870-142">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="be870-143">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="be870-143">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="be870-144">Type **ssomanage - disablemapping \<nom de compte Windows > \<nom de l’application >**.</span><span class="sxs-lookup"><span data-stu-id="be870-144">Type **ssomanage -disablemapping \<Windows account name> \<application name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be870-145">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="be870-145">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-enable-mappings-for-host-group-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="be870-146">Pour activer les mappages des applications associées de type groupe d'hôtes à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="be870-146">To enable mappings for host group type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="be870-147">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="be870-147">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="be870-148">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="be870-148">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="be870-149">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="be870-149">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="be870-150">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="be870-150">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="be870-151">Type **ssomanage - enablemapping \<nom du compte externe > \<nom de l’application >**.</span><span class="sxs-lookup"><span data-stu-id="be870-151">Type **ssomanage -enablemapping \<external account name> \<application name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be870-152">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="be870-152">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-disable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="be870-153">Pour désactiver les mappages des applications associées de type individuel à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="be870-153">To disable mappings for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="be870-154">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="be870-154">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="be870-155">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="be870-155">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="be870-156">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="be870-156">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="be870-157">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="be870-157">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="be870-158">Type **ssomanage - disablemapping \<nom du compte externe > \<nom de l’application >**.</span><span class="sxs-lookup"><span data-stu-id="be870-158">Type **ssomanage -disablemapping \<external account name> \<application name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be870-159">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="be870-159">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be870-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be870-160">See Also</span></span>  
 [<span data-ttu-id="be870-161">L’authentification unique initiée par l’hôte</span><span class="sxs-lookup"><span data-stu-id="be870-161">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)
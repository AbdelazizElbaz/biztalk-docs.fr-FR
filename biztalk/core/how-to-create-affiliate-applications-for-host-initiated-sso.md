---
title: "Pour créer des Applications associées pour hôte authentification unique initiée par | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], host initiated SSO
- creating, applications [SSO]
- host initiated SSO, creating affiliate applications
ms.assetid: 06202d21-055a-46bc-acff-da461f5673f1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23525d3b2f72d59e2b0f44257c707f22e6bc2bab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-affiliate-applications-for-host-initiated-sso"></a><span data-ttu-id="6e459-102">Comment créer des Applications associées pour l’authentification unique initiée par l’hôte</span><span class="sxs-lookup"><span data-stu-id="6e459-102">How to Create Affiliate Applications for Host Initiated SSO</span></span>
<span data-ttu-id="6e459-103">Vous pouvez définir deux types d'applications :</span><span class="sxs-lookup"><span data-stu-id="6e459-103">You can define two types of applications:</span></span>  
  
-   <span data-ttu-id="6e459-104">**Individuels** il existe une relation 1 à 1 entre les utilisateurs Windows et non-Windows.</span><span class="sxs-lookup"><span data-stu-id="6e459-104">**Individual** There is a 1 to 1 relationship between Windows users and non-Windows users.</span></span>  
  
-   <span data-ttu-id="6e459-105">**Groupe hôte** plusieurs utilisateurs non-Windows peuvent être mappés sur le même compte Windows.</span><span class="sxs-lookup"><span data-stu-id="6e459-105">**Host Group** Multiple non-Windows users can be mapped to the same Windows account.</span></span>  
  
### <a name="to-create-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="6e459-106">Pour créer une application associée à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="6e459-106">To create an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="6e459-107">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="6e459-107">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="6e459-108">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="6e459-108">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="6e459-109">Avec le bouton droit **Applications associées**, puis cliquez sur **créer une Application** pour ouvrir le **unique Sign-On Assistant Application d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="6e459-109">Right-click **Affiliate Applications**, and then click **Create Application** to open the **Enterprise Single Sign-On Application Wizard**.</span></span>  
  
4.  <span data-ttu-id="6e459-110">Utilisez l'Assistant pour sélectionner les propriétés de votre application associée.</span><span class="sxs-lookup"><span data-stu-id="6e459-110">Use the wizard to select the properties of your affiliate application.</span></span>  
  
### <a name="to-create-an-individual-type-affiliate-application-using-the-command-line"></a><span data-ttu-id="6e459-111">Pour créer une application associée de type individuel à l'aide d'une ligne de commande</span><span class="sxs-lookup"><span data-stu-id="6e459-111">To create an individual type affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="6e459-112">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="6e459-112">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="6e459-113">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6e459-113">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6e459-114">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6e459-114">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6e459-115">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="6e459-115">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="6e459-116">Type **ssomanage – createapps \<AffApp.xml >**, où AffApp.xml est le nom du fichier xml.</span><span class="sxs-lookup"><span data-stu-id="6e459-116">Type **ssomanage –createapps \<AffApp.xml>**, where AffApp.xml is the name of the xml file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6e459-117">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6e459-117">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
     <span data-ttu-id="6e459-118">Vous trouverez ci-dessous un exemple de fichier :</span><span class="sxs-lookup"><span data-stu-id="6e459-118">A sample file is shown below:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
      <application name="SSOApp_Host1">  
        <description>An Individual Type Affiliate Application for Host Initiated SSO</description>  
        <contact>someone@companyname.com</contact>  
        <appUserAccount>DomainName\AppUserGroup_HISSO</appUserAccount>  
        <appAdminAccount>DomainName\AppAdminGroup_HISSO</appAdminAccount>  
        <field ordinal="0" label="User ID" masked="no" />  
        <field ordinal="1" label="Password" masked="yes" />  
        <flags windowsInitiatedSSO="no" enableApp="yes" />  
      </application>  
    </SSO>  
  
    ```  
  
### <a name="to-create-a-host-group-type-affiliate-application-using-the-command-line"></a><span data-ttu-id="6e459-119">Pour créer une application associée de type groupe d'hôtes à l'aide d'une ligne de commande</span><span class="sxs-lookup"><span data-stu-id="6e459-119">To create a host group type affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="6e459-120">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="6e459-120">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="6e459-121">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6e459-121">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6e459-122">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6e459-122">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6e459-123">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="6e459-123">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="6e459-124">Type **ssomanage – createapps \<AffApp.xml >**, où AffApp.xml est le nom du fichier xml.</span><span class="sxs-lookup"><span data-stu-id="6e459-124">Type **ssomanage –createapps \<AffApp.xml>**, where AffApp.xml is the name of the xml file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6e459-125">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6e459-125">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
     <span data-ttu-id="6e459-126">Vous trouverez ci-dessous un exemple de fichier :</span><span class="sxs-lookup"><span data-stu-id="6e459-126">A sample file is shown below:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
      <application name="SSOApp_HostGroupApp1">  
        <description>A Group Type Affiliate Application for Host Initiated SSO associating multiple non-Windows user to a single Windows user account(DomainName\WindowsUserAccount1)</description>  
        <contact>someone@companyname.com</contact>  
        <windowsAccount>DomainName\WindowsUserAccount1</windowsAccount>  
        <appAdminAccount>DomainName\AppAdminGroup_HISSO</appAdminAccount>  
        <field ordinal="0" label="User ID" masked="no" />  
        <field ordinal="1" label="Password" masked="yes" />  
        <flags  enableApp="yes" />  
      </application>  
    </SSO>  
  
    ```  
  
### <a name="to-create-an-affiliate-application-supporting-both-windows-initiated-sso-and-host-initiated-sso-using-the-command-line"></a><span data-ttu-id="6e459-127">Pour créer une application associée prenant en charge l'authentification unique initiée par Windows et l'authentification unique initiée par l'hôte à l'aide d'une ligne de commande</span><span class="sxs-lookup"><span data-stu-id="6e459-127">To create an affiliate application supporting both Windows initiated SSO and host initiated SSO using the command line</span></span>  
  
1.  <span data-ttu-id="6e459-128">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="6e459-128">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="6e459-129">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6e459-129">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6e459-130">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6e459-130">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6e459-131">La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="6e459-131">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="6e459-132">Type **ssomanage – createapps \<AffApp.xml >**, où AffApp.xml est le nom du fichier xml.</span><span class="sxs-lookup"><span data-stu-id="6e459-132">Type **ssomanage –createapps \<AffApp.xml>**, where AffApp.xml is the name of the xml file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6e459-133">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6e459-133">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
     <span data-ttu-id="6e459-134">Vous trouverez ci-dessous un exemple de fichier :</span><span class="sxs-lookup"><span data-stu-id="6e459-134">A sample file is shown below:</span></span>  
  
    ```  
    <?xml version="1.0" ?>   
    - <SSO>  
    - <application name="SSOApp1">  
      <description>An Individual Type Affiliate Application for both Host Initiated SSO and Windows Initiated SSO</description>   
      <contact>someone@companyname.com</contact>   
      <appUserAccount>DomainName\AppUserGroup</appUserAccount>   
      <appAdminAccount>DomainName\AppAdminGroup</appAdminAccount>   
      <field ordinal="0" label="User ID" masked="no" />   
      <field ordinal="1" label="Password" masked="yes" />   
      <flags  enableApp="yes" />   
      </application>  
      </SSO>  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6e459-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e459-135">See Also</span></span>  
 [<span data-ttu-id="6e459-136">L’authentification unique initiée par l’hôte</span><span class="sxs-lookup"><span data-stu-id="6e459-136">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)
---
title: Comment modifier le serveur de secret principal | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, promoting
- managing [Master Secret server], promoting servers
- managing [SSO], promoting servers
- SSO, Master Secret server
- modifying, Master Secret server
- Master Secret server, changing
ms.assetid: 44a786ca-4645-44a8-b33e-d0019f0aeca9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4676db07025b4395d58df7c24252769ba65ecfb4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-master-secret-server"></a><span data-ttu-id="2cf81-102">Comment modifier le serveur de secret principal</span><span class="sxs-lookup"><span data-stu-id="2cf81-102">How to Change the Master Secret Server</span></span>
<span data-ttu-id="2cf81-103">Après avoir installé le serveur de secret principal et configuré la base de données SSO, vous pouvez modifier le serveur de secret principal d'origine en cas d'échec sans possibilité de le récupérer.</span><span class="sxs-lookup"><span data-stu-id="2cf81-103">After you set up the master secret server and configure the SSO database, you can change the master secret server if the original master secret server fails and cannot be recovered.</span></span> <span data-ttu-id="2cf81-104">Pour modifier le serveur de secret principal, vous devez promouvoir un serveur SSO au rang de serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="2cf81-104">To change the master secret server, you need to promote an SSO server to become the master secret server.</span></span>  
  
### <a name="to-change-the-master-secret-server-using-the-mmc-snap-in"></a><span data-ttu-id="2cf81-105">Pour modifier le serveur de secret principal à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="2cf81-105">To change the Master Secret Server using the MMC Snap-in</span></span>  
  
1.  <span data-ttu-id="2cf81-106">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="2cf81-106">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="2cf81-107">Dans le volet de la portée, avec le bouton droit sur **système**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2cf81-107">In the scope pane, right click **System**, and then click **Properties**.</span></span> <span data-ttu-id="2cf81-108">Le contrôleur de serveur de secret principal s’affiche sur le **général** onglet de la **propriétés système** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="2cf81-108">The Master secret server is displayed on the **General** tab of the **System Properties** dialog box.</span></span>  
  
3.  <span data-ttu-id="2cf81-109">Cliquez sur **modification** pour sélectionner un nouveau serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="2cf81-109">Click **Change** to select a new Master secret server.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2cf81-110">Lorsque vous utilisez le composant logiciel enfichable MMC pour modifier le serveur de secret principal, l'opération doit être effectuée sur le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="2cf81-110">When using the MMC Snap-in to change the Master Secret Server, the operation must be performed on the Master Secret Server.</span></span> <span data-ttu-id="2cf81-111">Il n'est pas possible de modifier le serveur de secret principal à l'aide du composant logiciel enfichable MMC à partir d'un ordinateur qui n'est pas le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="2cf81-111">It is not possible to change the Master Secret Server using the MMC Snap-in from a computer that is not the Master Secret Server.</span></span>  
  
4.  <span data-ttu-id="2cf81-112">Connectez-vous au nouveau serveur de secret principal pour restaurer le secret principal dans le Registre du nouveau serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="2cf81-112">Logon to the new Master secret server to restore the Master secret to the registry of the new Master secret server.</span></span>  
  
5.  <span data-ttu-id="2cf81-113">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="2cf81-113">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
6.  <span data-ttu-id="2cf81-114">Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="2cf81-114">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="2cf81-115">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="2cf81-115">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
7.  <span data-ttu-id="2cf81-116">Redémarrez le nouveau serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="2cf81-116">Restart the new Master Secret Server.</span></span>  
  
8.  <span data-ttu-id="2cf81-117">Type **ssoconfig – restoreSecret \<restaurer le fichier >**, où  **\<restaurer le fichier >** est le chemin d’accès et le nom du fichier dans lequel le secret est stocké.</span><span class="sxs-lookup"><span data-stu-id="2cf81-117">Type **ssoconfig –restoreSecret \<restore file>**, where **\<restore file>** is the path and name of the file where the master secret is stored.</span></span>  
  
     <span data-ttu-id="2cf81-118">Le serveur principal est stocké dans le Registre à l'emplacement suivant :</span><span class="sxs-lookup"><span data-stu-id="2cf81-118">The master secret is stored in the registry at the following location:</span></span>  
  
     <span data-ttu-id="2cf81-119">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS</span><span class="sxs-lookup"><span data-stu-id="2cf81-119">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2cf81-120">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="2cf81-120">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-promote-a-single-sign-on-server-to-master-secret-server-using-the-command-line"></a><span data-ttu-id="2cf81-121">Pour promouvoir un serveur de l'authentification unique au rang de serveur de secret principal à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="2cf81-121">To promote a Single Sign-On Server to master secret server using the command line</span></span>  
  
1.  <span data-ttu-id="2cf81-122">Créez un fichier XML contenant le nom du serveur SSO à promouvoir au rang de serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="2cf81-122">Create an XML file that includes the name of the SSO server you want to promote to master secret server.</span></span> <span data-ttu-id="2cf81-123">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2cf81-123">For example,</span></span>  
  
    ```  
    <sso>  
      <globalInfo>  
         <secretServer>SSO Server name</secretServer>  
      </globalInfo>  
    </sso>  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2cf81-124">Pour modifier le serveur de secret principal à partir d'un ordinateur qui n'est pas le serveur de secret principal, assurez-vous que le fichier XML spécifié contient uniquement le nom du serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="2cf81-124">To change the Master Secret Server from a computer that is not the Master Secret Server make sure that the specified XML file contains only the Master Secret Server name.</span></span> <span data-ttu-id="2cf81-125">Plus précisément, il ne doit pas contenir la balise XML administrateurs SSO ou **ssomanage - updatedb** échoue.</span><span class="sxs-lookup"><span data-stu-id="2cf81-125">Specifically, it should not contain the SSO Administrators XML tag or the **ssomanage -updatedb** operation will fail.</span></span>  
  
2.  <span data-ttu-id="2cf81-126">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="2cf81-126">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
3.  <span data-ttu-id="2cf81-127">Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="2cf81-127">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="2cf81-128">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="2cf81-128">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="2cf81-129">Type **ssomanage-updatedb** \< **fichier de mise à jour**>, où \< **fichier de mise à jour**> est le nom du fichier XML que vous créez à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="2cf81-129">Type **ssomanage –updatedb** \<**update file**>, where \<**update file**> is the name of the XML file you create in step 1.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2cf81-130">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="2cf81-130">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5.  <span data-ttu-id="2cf81-131">Redémarrez le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="2cf81-131">Restart the Master Secret Server.</span></span>  
  
6.  <span data-ttu-id="2cf81-132">Type **ssoconfig – restoresecret \<restaurer le fichier >**, où  **\<restaurer le fichier >** est le chemin d’accès et le nom du fichier dans lequel le secret est stocké.</span><span class="sxs-lookup"><span data-stu-id="2cf81-132">Type **ssoconfig –restoresecret \<restore file>**, where **\<restore file>** is the path and name of the file where the master secret is stored.</span></span>  
  
     <span data-ttu-id="2cf81-133">Le serveur principal est stocké dans le Registre à l'emplacement suivant :</span><span class="sxs-lookup"><span data-stu-id="2cf81-133">The master secret is stored in the registry at the following location:</span></span>  
  
     <span data-ttu-id="2cf81-134">HKEY_LOCAL_MACHINESOFTWAREMicrosoftENTSSOSSOSS</span><span class="sxs-lookup"><span data-stu-id="2cf81-134">HKEY_LOCAL_MACHINESOFTWAREMicrosoftENTSSOSSOSS</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2cf81-135">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="2cf81-135">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf81-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cf81-136">See Also</span></span>  
 <span data-ttu-id="2cf81-137">[Serveur de secret principal](../core/master-secret-server.md) </span><span class="sxs-lookup"><span data-stu-id="2cf81-137">[Master Secret Server](../core/master-secret-server.md) </span></span>  
 <span data-ttu-id="2cf81-138">[Mise en Cluster du serveur de secret principal](../core/how-to-cluster-the-master-secret-server1.md) </span><span class="sxs-lookup"><span data-stu-id="2cf81-138">[How to Cluster the Master Secret Server](../core/how-to-cluster-the-master-secret-server1.md) </span></span>  
 <span data-ttu-id="2cf81-139">[Comment mettre à jour la base de données SSO](../core/how-to-update-the-sso-database.md) </span><span class="sxs-lookup"><span data-stu-id="2cf81-139">[How to Update the SSO Database](../core/how-to-update-the-sso-database.md) </span></span>  
 [<span data-ttu-id="2cf81-140">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="2cf81-140">Using SSO</span></span>](../core/using-sso.md)
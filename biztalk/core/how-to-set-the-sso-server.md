---
title: "Comment définir le serveur SSO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, selecting [SSO]
- SSO, selecting servers
- managing [SSO], selecting servers
- SSOManage [SSO]
ms.assetid: a0b0176d-b426-4ab1-8a7e-1f96f4214683
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96631531cc28ac1bed4ea2b2b56b4b8f9b80c281
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-the-sso-server"></a><span data-ttu-id="09ba3-102">Comment configurer le serveur d’authentification unique</span><span class="sxs-lookup"><span data-stu-id="09ba3-102">How to Set the SSO Server</span></span>
<span data-ttu-id="09ba3-103">Chaque fois que vous utilisez ssomanage, vous devez commencer par pointer l'utilisateur sur le serveur d'authentification unique auquel vous voulez vous connecter.</span><span class="sxs-lookup"><span data-stu-id="09ba3-103">Each time you use ssomanage, you must first point the user to the Single Sign-On server you want to connect to.</span></span>  
  
 <span data-ttu-id="09ba3-104">Vous pouvez le faire de deux façons :</span><span class="sxs-lookup"><span data-stu-id="09ba3-104">You can do this in one of two ways:</span></span>  
  
-   <span data-ttu-id="09ba3-105">Les utilisateurs individuels peuvent se pointer eux-mêmes sur le serveur d'authentification unique approprié.</span><span class="sxs-lookup"><span data-stu-id="09ba3-105">Individual users can point themselves to the correct Single Sign-On Server.</span></span>  
  
-   <span data-ttu-id="09ba3-106">Un administrateur d'ordinateur local pour le serveur d'authentification unique peut pointer tous les membres du compte Utilisateurs d'authentification unique sur ce serveur.</span><span class="sxs-lookup"><span data-stu-id="09ba3-106">A local computer administrator for the Single Sign-On server can point all the members of the Single Sign-On Users account to this server.</span></span>  
  
### <a name="to-set-the-enterprise-single-sign-on-server-using-the-mmc-snap-in"></a><span data-ttu-id="09ba3-107">Pour définir le serveur d'authentification unique de l'entreprise à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="09ba3-107">To set the Enterprise Single Sign-On Server using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="09ba3-108">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="09ba3-108">Click **Start**, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="09ba3-109">Dans la console MMC enfichable sous le **racine de la Console**, avec le bouton droit **Enterprise Single Sign-On**, puis cliquez sur **sélectionnez**.</span><span class="sxs-lookup"><span data-stu-id="09ba3-109">In the MMC Snap-In under the **Console Root**, right-click **Enterprise Single Sign-On**, and click **Select**.</span></span>  
  
3.  <span data-ttu-id="09ba3-110">Accédez au serveur de votre choix.</span><span class="sxs-lookup"><span data-stu-id="09ba3-110">Browse to the desired server.</span></span>  
  
4.  <span data-ttu-id="09ba3-111">Le cas échéant, sélectionnez le **définir le serveur d’authentification unique pour tous les utilisateurs** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="09ba3-111">If appropriate, select the **Set SSO Server for all users** check box.</span></span>  
  
5.  <span data-ttu-id="09ba3-112">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="09ba3-112">Click **OK**.</span></span>  
  
### <a name="to-set-the-enterprise-single-sign-on-server-for-a-single-user-using-the-command-line"></a><span data-ttu-id="09ba3-113">Pour définir le serveur d'authentification unique de l'entreprise pour un seul utilisateur à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="09ba3-113">To set the Enterprise Single Sign-On Server for a single user using the command line</span></span>  
  
1.  <span data-ttu-id="09ba3-114">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="09ba3-114">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="09ba3-115">Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="09ba3-115">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="09ba3-116">Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="09ba3-116">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="09ba3-117">Type **ssomanage – server \<nom du serveur SSO >**, où  **\<nom du serveur SSO >** est le nom d’ordinateur unique l’authentification du serveur de l’utilisateur souhaite se connecter à.</span><span class="sxs-lookup"><span data-stu-id="09ba3-117">Type **ssomanage –server \<SSO server name>**, where **\<SSO server name>** is the computer name of the Single Sign-On Server the user wants to connect to.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="09ba3-118">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="09ba3-118">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-set-the-enterprise-single-sign-on-server-for-all-users-using-the-command-line"></a><span data-ttu-id="09ba3-119">Pour définir le serveur d'authentification unique de l'entreprise pour tous les utilisateurs à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="09ba3-119">To set the Enterprise Single Sign-On Server for all users using the command line</span></span>  
  
1.  <span data-ttu-id="09ba3-120">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="09ba3-120">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="09ba3-121">Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="09ba3-121">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="09ba3-122">Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="09ba3-122">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="09ba3-123">Type **ssomanage – serverall \<nom du serveur SSO >**, où  **\<nom du serveur SSO >** est le nom d’ordinateur du serveur d’authentification unique de tous les membres, les utilisateurs de l’authentification unique compte est pointé.</span><span class="sxs-lookup"><span data-stu-id="09ba3-123">Type **ssomanage –serverall \<SSO server name>**, where **\<SSO server name>** is the computer name of the Single Sign-On Server all members of the Single Sign-On Users account will be pointed to.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="09ba3-124">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="09ba3-124">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-determine-the-enterprise-single-sign-on-server-to-which-a-user-is-connected-using-the-command-line"></a><span data-ttu-id="09ba3-125">Pour déterminer le serveur d'authentification unique de l'entreprise auquel un utilisateur est connecté à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="09ba3-125">To determine the Enterprise Single Sign-On Server to which a user is connected using the command line</span></span>  
  
1.  <span data-ttu-id="09ba3-126">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="09ba3-126">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="09ba3-127">Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="09ba3-127">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="09ba3-128">Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="09ba3-128">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="09ba3-129">Type **ssomanage – showserver**.</span><span class="sxs-lookup"><span data-stu-id="09ba3-129">Type **ssomanage –showserver**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="09ba3-130">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="09ba3-130">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09ba3-131">Cette commande affiche les paramètres pour l'utilisateur actuel ainsi que pour d'autres utilisateurs éventuels.</span><span class="sxs-lookup"><span data-stu-id="09ba3-131">This command displays the settings for the current user as well as for other users if they exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ba3-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09ba3-132">See Also</span></span>  
 <span data-ttu-id="09ba3-133">[Comment activer l’authentification unique](../core/how-to-enable-sso.md) </span><span class="sxs-lookup"><span data-stu-id="09ba3-133">[How to Enable SSO](../core/how-to-enable-sso.md) </span></span>  
 <span data-ttu-id="09ba3-134">[Comment désactiver l’authentification unique](../core/how-to-disable-sso.md) </span><span class="sxs-lookup"><span data-stu-id="09ba3-134">[How to Disable SSO](../core/how-to-disable-sso.md) </span></span>  
 <span data-ttu-id="09ba3-135">[Comment afficher les informations de base de données SSO](../core/how-to-display-the-sso-database-information.md) </span><span class="sxs-lookup"><span data-stu-id="09ba3-135">[How to Display the SSO Database Information](../core/how-to-display-the-sso-database-information.md) </span></span>  
 [<span data-ttu-id="09ba3-136">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="09ba3-136">Using SSO</span></span>](../core/using-sso.md)
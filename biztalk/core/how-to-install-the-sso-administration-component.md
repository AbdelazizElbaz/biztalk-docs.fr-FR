---
title: "Installer le composant d’Administration SSO | Documents Microsoft"
description: "Effectuer une installation personnalisée pour obtenir l’Administration de l’authentification unique et permet d’entrer le nom du serveur dans BizTalk Server ssomanage ou l’administration de l’authentification unique"
ms.custom: 
ms.date: 09/27/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 096839e2-7129-498d-92ee-5afeea8dbe0d
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab2bb01defe700408a551a144eae67d0405565f4
ms.sourcegitcommit: 5355a25d120d094778fb8f68ea14cab55c68d292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2017
---
# <a name="how-to-install-the-sso-administration-component"></a><span data-ttu-id="8d7e3-103">Comment installer le composant Administration de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="8d7e3-103">How to Install the SSO Administration Component</span></span>

## <a name="overview"></a><span data-ttu-id="8d7e3-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="8d7e3-104">Overview</span></span>
<span data-ttu-id="8d7e3-105">Vous pouvez installer le composant Administration de l’authentification unique de l’entreprise comme une fonctionnalité autonome.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-105">You can install the Enterprise Single Sign-On Administration component as a stand-alone feature.</span></span> <span data-ttu-id="8d7e3-106">Ceci est utile si vous devez gérer le système d'authentification unique à distance.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-106">This is useful if you need to administer the SSO system remotely.</span></span> <span data-ttu-id="8d7e3-107">Les conditions matérielles et logicielles sont les mêmes que pour une installation classique des services d'exécution de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-107">The hardware and software requirements are the same as for a typical Enterprise SSO Runtime Services installation.</span></span>  
  
 <span data-ttu-id="8d7e3-108">Après avoir installé le composant d’administration, vous entrez le serveur d’authentification unique à utiliser pour la gestion.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-108">After installing the administration component, you enter the SSO Server to be used for management.</span></span> <span data-ttu-id="8d7e3-109">Pour cela, l’outil de ligne de commande (ssomanage.exe), soit le composant logiciel enfichable MMC du Administration SSO.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-109">You can do this with either the command line tool (ssomanage.exe), or the SSO Administration MMC Snap-In.</span></span> <span data-ttu-id="8d7e3-110">Les deux procédures sont répertoriées dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-110">Both procedures are listed in this topic.</span></span>  
  
 <span data-ttu-id="8d7e3-111">L'installation de l'utilitaire d'administration de l'authentification unique (ssomanage.exe) ne crée pas de raccourcis dans le menu Démarrer permettant d'accéder aux utilitaires de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-111">Installing the SSO administrative utility (ssomanage.exe) does not create shortcuts on the Start menu to access the command line utilities.</span></span> <span data-ttu-id="8d7e3-112">Pour exécuter les utilitaires d’administration de l’authentification unique après l’installation, vous devez ouvrir une invite de commandes et accédez au répertoire de l’authentification unique à `Program Files\Common Files\Enterprise Single Sign-On`.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-112">To run the SSO administrative utilities after installation, you must open a command prompt, and navigate to the SSO directory at `Program Files\Common Files\Enterprise Single Sign-On`.</span></span>  
  
 <span data-ttu-id="8d7e3-113">Le composant Administration de l’authentification unique d’entreprise inclut également un composant logiciel enfichable MMC.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-113">The Enterprise SSO Administration feature also includes an MMC Snap-in.</span></span> <span data-ttu-id="8d7e3-114">MMC 3.0 doit être installé sur votre ordinateur pour le composant logiciel enfichable de la fonction.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-114">MMC 3.0 must be installed on your computer for the Snap-in to function.</span></span>  
  
 <span data-ttu-id="8d7e3-115">Pour ouvrir le composant logiciel enfichable MMC de l’authentification unique d’entreprise à partir de la **Démarrer** menu, sélectionnez **tous les programmes**, sélectionnez **Microsoft Enterprise Single Sign-On**, puis **SSO Administration**.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-115">To open the Enterprise SSO MMC Snap-in from the **Start** menu, select **All Programs**, select **Microsoft Enterprise Single Sign-On**, and then **SSO Administration**.</span></span>  
  
## <a name="install-the-enterprise-single-sign-on-administrative-component"></a><span data-ttu-id="8d7e3-116">Installer le composant d’administration Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="8d7e3-116">Install the Enterprise Single Sign-On administrative component</span></span>  
  
-   <span data-ttu-id="8d7e3-117">Effectuez une installation personnalisée de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis sélectionnez uniquement la fonctionnalité d’Administration de l’authentification unique de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-117">Do a custom installation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and select only the Enterprise Single Sign-On Administration feature.</span></span> <span data-ttu-id="8d7e3-118">Pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], cette information est répertoriée sous **des logiciels supplémentaires**.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-118">For [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], this is listed under **Additional Software**.</span></span>  
  
## <a name="enter-the-server-using-the-mmc-snap-in"></a><span data-ttu-id="8d7e3-119">Entrez le serveur à l’aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="8d7e3-119">Enter the server using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="8d7e3-120">Après l'installation du composant d'administration sur un ordinateur, ouvrez le composant logiciel enfichable Administration de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-120">After installing the administrative component on a computer where it is not currently installed, open the SSO Administration Snap-In.</span></span>  
  
     <span data-ttu-id="8d7e3-121">Dans le **Démarrer** menu, sélectionnez **tous les programmes**, sélectionnez **Microsoft Enterprise Single Sign-On**, puis sélectionnez **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-121">In the **Start** menu, select **All Programs**, select **Microsoft Enterprise Single Sign-On**, and then select **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="8d7e3-122">Dans la console MMC enfichable sous le **racine de la Console**, avec le bouton droit **Enterprise Single Sign-On**, puis cliquez sur **sélectionnez**.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-122">In the MMC Snap-In under the **Console Root**, right-click **Enterprise Single Sign-On**, and click **Select**.</span></span>  
  
     <span data-ttu-id="8d7e3-123">Le **sélectionner le serveur SSO** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-123">The **Select SSO Server** dialog box will appear.</span></span>  
  
3.  <span data-ttu-id="8d7e3-124">Entrez le nom du serveur d'authentification unique souhaité ou accédez-y.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-124">Enter or browse to the SSO server name you want to specify.</span></span> <span data-ttu-id="8d7e3-125">Pour spécifier le serveur d’authentification unique pour tous les utilisateurs sur l’ordinateur, sélectionnez **définir le serveur d’authentification unique pour tous les utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-125">To specify the SSO server for all users on the computer, select **Set SSO Server for all users**.</span></span>  
  
4.  <span data-ttu-id="8d7e3-126">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-126">Click **OK**.</span></span>  
  
## <a name="enter-the-server-using-the-command-line-tool"></a><span data-ttu-id="8d7e3-127">Entrez le serveur à l’aide de l’outil de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="8d7e3-127">Enter the server using the command line tool</span></span>  
  
1.  <span data-ttu-id="8d7e3-128">Cliquez sur **Démarrer**, **Exécuter**, puis entrez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-128">Click **Start**, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="8d7e3-129">Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-129">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="8d7e3-130">Le répertoire d’installation par défaut est `\Program Files\Common Files\Enterprise Single Sign-On`.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-130">The default installation directory is `\Program Files\Common Files\Enterprise Single Sign-On`.</span></span>  
  
3.  <span data-ttu-id="8d7e3-131">Entrez le serveur d’authentification unique en sélectionnant une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="8d7e3-131">Enter the SSO Server by selecting one of the following options:</span></span>  
  
    1.  <span data-ttu-id="8d7e3-132">Type **ssomanage – server** à entrer le serveur SSO que vous souhaitez vous connecter lorsque vous effectuez des opérations d’administration.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-132">Type **ssomanage –server** to enter the SSO Server you want to connect to when performing administration operations.</span></span>  
  
         <span data-ttu-id="8d7e3-133">\- - OU -</span><span class="sxs-lookup"><span data-stu-id="8d7e3-133">\- OR -</span></span>  
  
    2.  <span data-ttu-id="8d7e3-134">Type **ssomanage - serverall** pour entrer le serveur d’authentification unique se connectera à tous les utilisateurs de cet ordinateur lors de l’exécution des opérations d’administration.</span><span class="sxs-lookup"><span data-stu-id="8d7e3-134">Type **ssomanage -serverall** to enter the SSO Server all users of this computer will connect to when performing administration operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d7e3-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d7e3-135">See Also</span></span>  
 <span data-ttu-id="8d7e3-136">[Comment installer l’utilitaire Client SSO](../core/how-to-install-the-sso-client-utility.md) </span><span class="sxs-lookup"><span data-stu-id="8d7e3-136">[How to Install the SSO Client Utility](../core/how-to-install-the-sso-client-utility.md) </span></span>  
 <span data-ttu-id="8d7e3-137">[Configuration de l’authentification unique](../core/configuring-sso.md) </span><span class="sxs-lookup"><span data-stu-id="8d7e3-137">[Configuring SSO](../core/configuring-sso.md) </span></span>  
 [<span data-ttu-id="8d7e3-138">L’installation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="8d7e3-138">Installing SSO</span></span>](../core/installing-sso.md)

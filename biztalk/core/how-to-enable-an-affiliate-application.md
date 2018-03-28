---
title: Comment activer une Application associée | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications [SSO], enabling
- managing [SSO applications], enabling
- enabling, applications [SSO]
ms.assetid: 81c94e1b-cd3d-482e-9a78-9b1476af9e5f
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a0e4776b60b81256552552c60aa1abb8abdcde8
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-enable-an-affiliate-application"></a><span data-ttu-id="2993d-102">Comment activer une Application associée</span><span class="sxs-lookup"><span data-stu-id="2993d-102">How to Enable an Affiliate Application</span></span>
<span data-ttu-id="2993d-103">Le composant logiciel enfichable MMC ou la ligne de commande permet d'activer l'application associée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2993d-103">You can use the MMC Snap-In or the command line to enable the specified affiliate application.</span></span>  
  
### <a name="to-enable-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="2993d-104">Pour activer une application associée à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="2993d-104">To enable an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="2993d-105">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="2993d-105">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="2993d-106">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="2993d-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="2993d-107">Cliquez sur l’application associée, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="2993d-107">Right-click the affililate application, and then click **Enable**.</span></span>  
  
### <a name="to-enable-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="2993d-108">Pour activer une application associée à l'aide d'une ligne de commande</span><span class="sxs-lookup"><span data-stu-id="2993d-108">To enable an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="2993d-109">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="2993d-109">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="2993d-110">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="2993d-110">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="2993d-111">Le répertoire d’installation par défaut est \< *lecteur*\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="2993d-111">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="2993d-112">Type **ssomanage-enableapp *\<nom de l’application\>***, où \<*nom de l’application* \> est le nom de l’application associée Pour activer.</span><span class="sxs-lookup"><span data-stu-id="2993d-112">Type **ssomanage –enableapp *\<application name\>***, where \<*application name*\> is the name of the affiliate application you want to enable.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2993d-113">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="2993d-113">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2993d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2993d-114">See Also</span></span>  
 <span data-ttu-id="2993d-115">[Applications associées SSO](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="2993d-115">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="2993d-116">[Comment créer une Application associée](../core/how-to-create-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="2993d-116">[How to Create an Affiliate Application](../core/how-to-create-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="2993d-117">[Gestion des mappages utilisateur](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="2993d-117">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="2993d-118">Gestion des applications associées</span><span class="sxs-lookup"><span data-stu-id="2993d-118">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)
---
title: "Comment désactiver une Application associée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disabling, applications
- managing [SSO applications], disabling
- applications [SSO], disabling
ms.assetid: febf1687-f0d0-4f87-b462-23535bbddf6d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09efa7dd00f563b8b02469909d2105d443438e95
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-disable-an-affiliate-application"></a><span data-ttu-id="e7e60-102">Comment désactiver une Application associée</span><span class="sxs-lookup"><span data-stu-id="e7e60-102">How to Disable an Affiliate Application</span></span>
<span data-ttu-id="e7e60-103">Le composant logiciel enfichable MMC ou la ligne de commande permet de désactiver l'application associée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e7e60-103">You can use the MMC Snap-In or the command line to disable the specified affiliate application.</span></span>  
  
### <a name="to-disable-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="e7e60-104">Pour désactiver une application associée à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="e7e60-104">To disable an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="e7e60-105">Sur le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="e7e60-105">On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="e7e60-106">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="e7e60-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="e7e60-107">Cliquez sur l’application associée, puis cliquez sur **désactiver**.</span><span class="sxs-lookup"><span data-stu-id="e7e60-107">Right-click the affiliate application, and then click **Disable**.</span></span>  
  
### <a name="to-disable-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="e7e60-108">Pour désactiver une application associée à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="e7e60-108">To disable an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="e7e60-109">Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="e7e60-109">Click **Start**, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="e7e60-110">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="e7e60-110">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e7e60-111">Le répertoire d’installation par défaut est \< *lecteur*\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="e7e60-111">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="e7e60-112">Type **ssomanage-disableapp  *\<nom de l’application\>***, où \< *nom de l’application* \> est le nom de l’application associée que vous souhaitez désactiver.</span><span class="sxs-lookup"><span data-stu-id="e7e60-112">Type **ssomanage –disableapp *\<application name\>***, where \<*application name*\> is the name of the affiliate application you want to disable.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e7e60-113">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="e7e60-113">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7e60-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7e60-114">See Also</span></span>  
 <span data-ttu-id="e7e60-115">[Applications associées SSO](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="e7e60-115">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="e7e60-116">[Comment activer une Application associée](../core/how-to-enable-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="e7e60-116">[How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="e7e60-117">[Gestion des mappages utilisateur](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="e7e60-117">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="e7e60-118">Gestion des applications associées</span><span class="sxs-lookup"><span data-stu-id="e7e60-118">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)
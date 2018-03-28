---
title: Comment activer une Application associée | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 051bc35f-55e6-4811-9559-b1bb66a570ce
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 53dcd9886bc808f84b112146971a6f9519c404e2
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-enable-an-affiliate-application"></a><span data-ttu-id="7577d-102">Comment activer une Application associée</span><span class="sxs-lookup"><span data-stu-id="7577d-102">How to Enable an Affiliate Application</span></span>
<span data-ttu-id="7577d-103">Vous pouvez utiliser le composant logiciel enfichable MMC ou la **enableapp** commande pour activer l’application associée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7577d-103">You can use the MMC Snap-In or the **enableapp** command to enable the specified affiliate application.</span></span>  
  
### <a name="to-enable-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="7577d-104">Pour activer une application associée à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="7577d-104">To enable an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="7577d-105">Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="7577d-105">Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="7577d-106">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="7577d-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="7577d-107">Cliquez sur l’application associée, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="7577d-107">Right-click the affililate application, and then click **Enable**.</span></span>  
  
### <a name="to-enable-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="7577d-108">Pour activer une application associée à l'aide d'une ligne de commande</span><span class="sxs-lookup"><span data-stu-id="7577d-108">To enable an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="7577d-109">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="7577d-109">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="7577d-110">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="7577d-110">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="7577d-111">Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="7577d-111">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="7577d-112">Type `ssomanage –enableapp <application name>`, où \< *nom de l’application*> est le nom de l’application associée que vous souhaitez activer.</span><span class="sxs-lookup"><span data-stu-id="7577d-112">Type `ssomanage –enableapp <application name>`, where \<*application name*> is the name of the affiliate application you want to enable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7577d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7577d-113">See Also</span></span>  
 <span data-ttu-id="7577d-114">[Applications associées SSO](../esso/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="7577d-114">[SSO Affiliate Applications](../esso/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="7577d-115">[Comment créer une Application associée](../esso/how-to-create-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="7577d-115">[How to Create an Affiliate Application](../esso/how-to-create-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="7577d-116">[Gestion des mappages utilisateur](../esso/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="7577d-116">[Managing User Mappings](../esso/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="7577d-117">Gestion des applications associées</span><span class="sxs-lookup"><span data-stu-id="7577d-117">Managing Affiliate Applications</span></span>](../esso/managing-affiliate-applications.md)
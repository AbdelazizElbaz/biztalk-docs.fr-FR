---
title: Comment désactiver une Application associée | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7df6e78-6d18-443d-82dc-4351c20a8c4e
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 6bae89d2a05ec34095e0fa2ac3feafc7b88b894e
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-disable-an-affiliate-application"></a><span data-ttu-id="6d7b1-102">Comment désactiver une Application associée</span><span class="sxs-lookup"><span data-stu-id="6d7b1-102">How to Disable an Affiliate Application</span></span>
<span data-ttu-id="6d7b1-103">Utilisez le composant logiciel enfichable MMC ou la **disableapp** commande pour désactiver l’application associée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6d7b1-103">Use the MMC Snap-In or the **disableapp** command to disable the specified affiliate application.</span></span>  
  
### <a name="to-disable-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="6d7b1-104">Pour désactiver une application associée à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="6d7b1-104">To disable an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="6d7b1-105">Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="6d7b1-105">Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="6d7b1-106">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="6d7b1-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="6d7b1-107">Cliquez sur l’application associée, puis cliquez sur **désactiver**.</span><span class="sxs-lookup"><span data-stu-id="6d7b1-107">Right-click the affiliate application, and then click **Disable**.</span></span>  
  
### <a name="to-disable-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="6d7b1-108">Pour désactiver une application associée à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="6d7b1-108">To disable an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="6d7b1-109">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="6d7b1-109">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="6d7b1-110">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="6d7b1-110">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="6d7b1-111">Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="6d7b1-111">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="6d7b1-112">Type `ssomanage –disableapp <application name>`, où \< *nom de l’application*> est le nom de l’application associée que vous souhaitez désactiver.</span><span class="sxs-lookup"><span data-stu-id="6d7b1-112">Type `ssomanage –disableapp <application name>`, where \<*application name*> is the name of the affiliate application you want to disable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d7b1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d7b1-113">See Also</span></span>  
 <span data-ttu-id="6d7b1-114">[Applications associées SSO](../esso/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="6d7b1-114">[SSO Affiliate Applications](../esso/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="6d7b1-115">[Comment activer une Application associée](../esso/how-to-enable-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="6d7b1-115">[How to Enable an Affiliate Application](../esso/how-to-enable-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="6d7b1-116">[Gestion des mappages utilisateur](../esso/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="6d7b1-116">[Managing User Mappings](../esso/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="6d7b1-117">Gestion des applications associées</span><span class="sxs-lookup"><span data-stu-id="6d7b1-117">Managing Affiliate Applications</span></span>](../esso/managing-affiliate-applications.md)
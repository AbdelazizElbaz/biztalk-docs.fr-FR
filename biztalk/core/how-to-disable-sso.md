---
title: "Comment désactiver l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disabling, SSO
- SSO, disabling
- managing [SSO], disabling
ms.assetid: 0fe4f87a-d7c2-4af6-afee-1065bc4a5285
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d7096a9c77dda72bbf0aea3ec76423c759fa90df
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-disable-sso"></a><span data-ttu-id="a2065-102">Comment désactiver l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="a2065-102">How to Disable SSO</span></span>
<span data-ttu-id="a2065-103">Vous pouvez désactiver le système d'authentification unique à l'aide du composant logiciel enfichable MMC ou de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a2065-103">You can disable the entire Single Sign-On system by using either the MMC Snap-In or the command line.</span></span>  
  
 <span data-ttu-id="a2065-104">Il y a un court délai avant que tous les serveurs d'authentification unique ne soient désactivés, le temps d'interroger la base de données SSO pour obtenir les dernières informations globales.</span><span class="sxs-lookup"><span data-stu-id="a2065-104">There will be a short delay for all Single Sign-On Servers to be disabled, as they poll the SSO database for the latest global information.</span></span>  
  
### <a name="to-disable-enterprise-single-sign-on-using-the-mmc-snap-in"></a><span data-ttu-id="a2065-105">Pour désactiver l'authentification unique de l'entreprise à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="a2065-105">To disable Enterprise Single Sign-On using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="a2065-106">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="a2065-106">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="a2065-107">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="a2065-107">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="a2065-108">Avec le bouton droit **système**, puis cliquez sur **désactiver**.</span><span class="sxs-lookup"><span data-stu-id="a2065-108">Right-click **System**, and then click **Disable**.</span></span>  
  
### <a name="to-disable-enterprise-single-sign-on-using-the-command-line"></a><span data-ttu-id="a2065-109">Pour désactiver l'authentification unique de l'entreprise à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="a2065-109">To disable Enterprise Single Sign-On using the command line</span></span>  
  
1.  <span data-ttu-id="a2065-110">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="a2065-110">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="a2065-111">Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="a2065-111">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="a2065-112">Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="a2065-112">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="a2065-113">Type **ssomanage – disablesso**.</span><span class="sxs-lookup"><span data-stu-id="a2065-113">Type **ssomanage –disablesso**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a2065-114">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a2065-114">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2065-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2065-115">See Also</span></span>  
 <span data-ttu-id="a2065-116">[Comment activer l’authentification unique](../core/how-to-enable-sso.md) </span><span class="sxs-lookup"><span data-stu-id="a2065-116">[How to Enable SSO](../core/how-to-enable-sso.md) </span></span>  
 [<span data-ttu-id="a2065-117">Utilisation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="a2065-117">Using SSO</span></span>](../core/using-sso.md)
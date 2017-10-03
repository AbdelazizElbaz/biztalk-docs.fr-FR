---
title: "Comment faire pour effacer le Cache d’Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- caching, applications
- managing [SSO applications], clearing cache
- applications [SSO], caching
ms.assetid: 6230b9a4-c7b8-47b4-854b-12853d9bf5b0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eacb7a786ad2729dbbea365e70c3aba8fabed5d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-clear-the-application-cache"></a><span data-ttu-id="c1006-102">Comment faire pour effacer le Cache d’Application</span><span class="sxs-lookup"><span data-stu-id="c1006-102">How to Clear the Application Cache</span></span>
<span data-ttu-id="c1006-103">Le composant logiciel enfichable MMC ou l'outil de ligne de commande permet de supprimer le contenu du cache des informations d'identification (c'est-à-dire toutes les informations relatives à l'application qui leur est associée) pour une application spécifique et sur tous les serveurs d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="c1006-103">You can use the MMC Snap-In or the command line to remove the contents of the credential cache (all the information associated with the affiliate application) for the specified application on all of the Single Sign-On Servers.</span></span>  
  
### <a name="to-clear-the-cache-using-the-mmc-snap-in"></a><span data-ttu-id="c1006-104">Pour effacer le cache à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="c1006-104">To clear the cache using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="c1006-105">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="c1006-105">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="c1006-106">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="c1006-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="c1006-107">Cliquez sur **Applications associées**.</span><span class="sxs-lookup"><span data-stu-id="c1006-107">Click **Affiliate Applications**.</span></span>  
  
4.  <span data-ttu-id="c1006-108">Dans le volet de résultats, cliquez sur l’application associée, puis cliquez sur **clair**.</span><span class="sxs-lookup"><span data-stu-id="c1006-108">In the results pane, right-click the affiliate application, and click **Clear**.</span></span>  
  
### <a name="to-clear-the-cache-using-the-command-line"></a><span data-ttu-id="c1006-109">Pour effacer le cache à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="c1006-109">To clear the cache using the command line</span></span>  
  
1.  <span data-ttu-id="c1006-110">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="c1006-110">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="c1006-111">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="c1006-111">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="c1006-112">Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="c1006-112">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="c1006-113">Type **ssomanage – purgecache  *\<nom de l’application >***, où \< *nom de l’application*> est le nom de l’application associée vous souhaitez purger le cache.</span><span class="sxs-lookup"><span data-stu-id="c1006-113">Type **ssomanage –purgecache *\<application name>***, where \<*application name*> is the name of the affiliate application you want to purge the cache for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c1006-114">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="c1006-114">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1006-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1006-115">See Also</span></span>  
 <span data-ttu-id="c1006-116">[Applications associées SSO](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="c1006-116">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="c1006-117">Gestion des Applications associées</span><span class="sxs-lookup"><span data-stu-id="c1006-117">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)
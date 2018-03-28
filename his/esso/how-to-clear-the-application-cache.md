---
title: Comment faire pour effacer le Cache d’Application | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a897791-d32f-46a4-8c5d-2b2161e92bd9
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 24954e8314bc94d4570eb57acbf1d4b03bebb65b
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-clear-the-application-cache"></a><span data-ttu-id="8ecc1-102">Comment faire pour effacer le Cache d’Application</span><span class="sxs-lookup"><span data-stu-id="8ecc1-102">How to Clear the Application Cache</span></span>
<span data-ttu-id="8ecc1-103">Utilisez le composant logiciel enfichable MMC ou la **purgecache** commande pour supprimer le contenu du cache d’informations d’identification (toutes les informations associé à l’application associée) pour l’application spécifiée sur tous les serveurs Single Sign-On (SSO).</span><span class="sxs-lookup"><span data-stu-id="8ecc1-103">Use the MMC Snap-In or the **purgecache** command to remove the contents of the credential cache (all the information that is associated with the affiliate application) for the specified application on all Single Sign-On (SSO) servers.</span></span>  
  
### <a name="to-clear-the-cache-using-the-mmc-snap-in"></a><span data-ttu-id="8ecc1-104">Pour effacer le cache à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="8ecc1-104">To clear the cache using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="8ecc1-105">Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="8ecc1-105">Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="8ecc1-106">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="8ecc1-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="8ecc1-107">Cliquez sur **Applications associées**.</span><span class="sxs-lookup"><span data-stu-id="8ecc1-107">Click **Affiliate Applications**.</span></span>  
  
4.  <span data-ttu-id="8ecc1-108">Dans le volet de résultats, cliquez sur l’application associée, puis cliquez sur **clair**.</span><span class="sxs-lookup"><span data-stu-id="8ecc1-108">In the results pane, right-click the affiliate application, and click **Clear**.</span></span>  
  
### <a name="to-clear-the-cache-using-the-command-line"></a><span data-ttu-id="8ecc1-109">Pour effacer le cache à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="8ecc1-109">To clear the cache using the command line</span></span>  
  
1.  <span data-ttu-id="8ecc1-110">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="8ecc1-110">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="8ecc1-111">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="8ecc1-111">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="8ecc1-112">Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="8ecc1-112">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="8ecc1-113">Type `ssomanage –purgecache <application name>`, où \< *nom de l’application*> est le nom de l’application associée que vous souhaitez purger le cache.</span><span class="sxs-lookup"><span data-stu-id="8ecc1-113">Type `ssomanage –purgecache <application name>`, where \<*application name*> is the name of the affiliate application that you want to purge the cache for.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ecc1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ecc1-114">See Also</span></span>  
 <span data-ttu-id="8ecc1-115">[Applications associées SSO](../esso/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="8ecc1-115">[SSO Affiliate Applications](../esso/sso-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="8ecc1-116">Gestion des applications associées</span><span class="sxs-lookup"><span data-stu-id="8ecc1-116">Managing Affiliate Applications</span></span>](../esso/managing-affiliate-applications.md)
---
title: Comment afficher le serveur d’authentification unique à l’aide de l’utilitaire Client | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications [SSO], viewing servers
- managing [SSO applications], viewing servers
- SSOClient [SSO], viewing servers
ms.assetid: af79ad96-6d94-48e0-9c80-6f0e38a3b8ac
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fa4394d3a45c7d0c273d82446b1a5e11d500348
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-display-the-sso-server-using-the-client-utility"></a><span data-ttu-id="70dc3-102">Comment afficher le serveur d’authentification unique à l’aide de l’utilitaire Client</span><span class="sxs-lookup"><span data-stu-id="70dc3-102">How to Display the SSO Server Using the Client Utility</span></span>
<span data-ttu-id="70dc3-103">Cette commande permet d'afficher le serveur d'authentification unique sur lequel l'utilisateur pointe actuellement.</span><span class="sxs-lookup"><span data-stu-id="70dc3-103">Use this command to display the Single Sign-On Server to which the user is currently pointing.</span></span>  
  
### <a name="to-display-the-sso-server-using-the-client-utility"></a><span data-ttu-id="70dc3-104">Pour afficher le serveur d'authentification unique à l'aide de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="70dc3-104">To display the SSO server using the client utility</span></span>  
  
1.  <span data-ttu-id="70dc3-105">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="70dc3-105">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="70dc3-106">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="70dc3-106">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="70dc3-107">Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="70dc3-107">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="70dc3-108">Type **ssoclient – showserver**.</span><span class="sxs-lookup"><span data-stu-id="70dc3-108">Type **ssoclient –showserver**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="70dc3-109">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="70dc3-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70dc3-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70dc3-110">See Also</span></span>  
 <span data-ttu-id="70dc3-111">[Applications associées SSO](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="70dc3-111">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="70dc3-112">Gestion des applications associées</span><span class="sxs-lookup"><span data-stu-id="70dc3-112">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)
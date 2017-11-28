---
title: "Comment activer SSL pour l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, SSL
- managing [SSO], enabling SSL
- SSL
ms.assetid: 0d75962a-a0b0-4e69-8001-54e7df617006
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ae2f3840cd2620f9c03a5b207b32d8bbd4feee9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-ssl-for-sso"></a><span data-ttu-id="3e304-102">Comment activer SSL pour l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="3e304-102">How to Enable SSL for SSO</span></span>
<span data-ttu-id="3e304-103">Cette commande permet d'activer le protocole SSL (Secure Sockets Layer) entre les serveurs d'authentification unique de l'entreprise et la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="3e304-103">Use this command to enable Secure Sockets Layer (SSL) between all the Enterprise Single Sign-On (SSO) servers and the SSO database.</span></span>  
  
### <a name="to-enable-ssl-for-enterprise-single-sign-on"></a><span data-ttu-id="3e304-104">Pour activer le protocole SSL pour l'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="3e304-104">To enable SSL for Enterprise Single Sign-On</span></span>  
  
1.  <span data-ttu-id="3e304-105">Cliquez sur **Démarrer**, **Exécuter**, puis entrez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="3e304-105">Click **Start**, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="3e304-106">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="3e304-106">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="3e304-107">Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="3e304-107">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="3e304-108">Type **ssoconfig – setSSL \<Oui/non >**, où \< **Oui/non**> indique si vous souhaitez activer le protocole SSL dans le système d’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="3e304-108">Type **ssoconfig –setSSL \<yes/no>**, where \<**yes/no**> indicates whether you want to enable SSL in the SSO system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e304-109">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="3e304-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e304-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e304-110">See Also</span></span>  
 [<span data-ttu-id="3e304-111">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="3e304-111">Using SSO</span></span>](../core/using-sso.md)
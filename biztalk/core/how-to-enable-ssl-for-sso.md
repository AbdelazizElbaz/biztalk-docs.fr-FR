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
ms.openlocfilehash: 8cd617fd955100930b513bc6c364626e4912eb81
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-ssl-for-sso"></a><span data-ttu-id="64a84-102">Comment activer SSL pour l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="64a84-102">How to Enable SSL for SSO</span></span>
<span data-ttu-id="64a84-103">Cette commande permet d'activer le protocole SSL (Secure Sockets Layer) entre les serveurs d'authentification unique de l'entreprise et la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="64a84-103">Use this command to enable Secure Sockets Layer (SSL) between all the Enterprise Single Sign-On (SSO) servers and the SSO database.</span></span>  
  
### <a name="to-enable-ssl-for-enterprise-single-sign-on"></a><span data-ttu-id="64a84-104">Pour activer le protocole SSL pour l'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="64a84-104">To enable SSL for Enterprise Single Sign-On</span></span>  
  
1.  <span data-ttu-id="64a84-105">Cliquez sur **Démarrer**, **Exécuter**, puis entrez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="64a84-105">Click **Start**, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="64a84-106">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="64a84-106">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="64a84-107">Le répertoire d’installation par défaut est  **\<lecteur\>**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="64a84-107">The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="64a84-108">Type **ssoconfig – setSSL \<Oui/non\>**, où \< **Oui/non** \> indique si vous souhaitez activer le protocole SSL dans le système d’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="64a84-108">Type **ssoconfig –setSSL \<yes/no\>**, where \<**yes/no**\> indicates whether you want to enable SSL in the SSO system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="64a84-109">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="64a84-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64a84-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64a84-110">See Also</span></span>  
 [<span data-ttu-id="64a84-111">Utilisation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="64a84-111">Using SSO</span></span>](../core/using-sso.md)
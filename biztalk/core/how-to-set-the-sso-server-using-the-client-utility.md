---
title: "Comment configurer le serveur d’authentification unique à l’aide de l’utilitaire Client | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], selecting servers
- managing [SSO applications], selecting servers
- SSOClient [SSO], selecting servers
ms.assetid: a0f1038c-60c9-4e9d-a730-1ecfa036743b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49b2145320bd8e22b01d312d62246fa282fb534e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-set-the-sso-server-using-the-client-utility"></a><span data-ttu-id="fe6ac-102">Comment configurer le serveur d’authentification unique à l’aide de l’utilitaire Client</span><span class="sxs-lookup"><span data-stu-id="fe6ac-102">How to Set the SSO Server Using the Client Utility</span></span>
<span data-ttu-id="fe6ac-103">Chaque fois que vous utilisez ssoclient, vous devez commencer par pointer l'utilisateur sur le serveur d'authentification unique approprié contenant ses informations de configuration.</span><span class="sxs-lookup"><span data-stu-id="fe6ac-103">Each time you use ssoclient, you must first point the user to the correct Single Sign-On server that contains their configuration information.</span></span>  
  
### <a name="to-set-the-sso-server-for-a-user-using-the-client-utility"></a><span data-ttu-id="fe6ac-104">Pour définir le serveur d'authentification unique pour un utilisateur à l'aide de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="fe6ac-104">To set the SSO Server for a user using the client utility</span></span>  
  
1.  <span data-ttu-id="fe6ac-105">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="fe6ac-105">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="fe6ac-106">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="fe6ac-106">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="fe6ac-107">Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="fe6ac-107">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="fe6ac-108">Type **ssoclient – serveur  *\<serveur d’authentification unique\>***, où \< *serveur d’authentification unique\>*  est le nom du serveur Single Sign-On l’utilisateur veut se connecter.</span><span class="sxs-lookup"><span data-stu-id="fe6ac-108">Type **ssoclient –server *\<Single Sign-On Server\>***, where \<*Single Sign-On Server\>* is the name of the Single Sign-On server the user wants to connect to.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fe6ac-109">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="fe6ac-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe6ac-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe6ac-110">See Also</span></span>  
 <span data-ttu-id="fe6ac-111">[Applications associées SSO](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="fe6ac-111">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="fe6ac-112">Gestion des applications associées</span><span class="sxs-lookup"><span data-stu-id="fe6ac-112">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)
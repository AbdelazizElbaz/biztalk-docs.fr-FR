---
title: "Configuration requise pour l’authentification unique sur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 318b9977-ce24-48d6-971b-49a059a1bdbc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2abd36879428c9d775251e20dd63f8778aa7b63
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="88b4a-102">Configuration requise pour l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="88b4a-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="88b4a-103">Pour utiliser l’authentification unique (SSO), vous devez :</span><span class="sxs-lookup"><span data-stu-id="88b4a-103">To use Single Sign-On (SSO), you must have:</span></span>  
  
-   <span data-ttu-id="88b4a-104">Microsoft BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="88b4a-104">Microsoft BizTalk Server</span></span> 
  
-   <span data-ttu-id="88b4a-105">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="88b4a-105">Visual Studio</span></span>  
  
-   <span data-ttu-id="88b4a-106">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="88b4a-106">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="88b4a-107">Un système de serveur prenant en charge SSO</span><span class="sxs-lookup"><span data-stu-id="88b4a-107">A Server System that supports SSO</span></span>  
  
 <span data-ttu-id="88b4a-108">L’hôte isolé doit être configuré comme approuvé par authentification.</span><span class="sxs-lookup"><span data-stu-id="88b4a-108">The isolated host should be configured as authentication trusted.</span></span>  
  
## <a name="enable-sso"></a><span data-ttu-id="88b4a-109">Activer l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="88b4a-109">Enable SSO</span></span>  
  
1.  <span data-ttu-id="88b4a-110">Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.</span><span class="sxs-lookup"><span data-stu-id="88b4a-110">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="88b4a-111">Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.</span><span class="sxs-lookup"><span data-stu-id="88b4a-111">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
     <span data-ttu-id="88b4a-112">Pour plus d’informations sur la création d’applications associées, consultez [création d’Applications associées](../core/creating-affiliate-applications3.md).</span><span class="sxs-lookup"><span data-stu-id="88b4a-112">For information about creating affiliate applications, see [Creating Affiliate Applications](../core/creating-affiliate-applications3.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="88b4a-113">Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser les **partage Web** dossier **ne partagent pas**.</span><span class="sxs-lookup"><span data-stu-id="88b4a-113">After performing work using SSO, remember to reset any **Web-Sharing** folder to **Do not share**.</span></span> <span data-ttu-id="88b4a-114">La mise à jour ou la désinstallation d'applications utilisant ce dossier ne pourra pas s'effectuer correctement car, s'il est partagé, il est considéré comme en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="88b4a-114">Applications using that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88b4a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88b4a-115">See Also</span></span>  
 [<span data-ttu-id="88b4a-116">Utilisation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="88b4a-116">Using Single Sign-On</span></span>](../core/using-single-sign-on3.md)
---
title: "Configuration requise pour l’authentification unique sur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1111377-2fe1-4d65-ac0d-c89d2f1740b8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 437bc9d744e20b14e21d0e9d2ebe33e7b2e8a62a
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="10852-102">Configuration requise pour l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="10852-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="10852-103">Pour utiliser l'authentification unique (SSO), vous devez disposer des logiciels suivants :</span><span class="sxs-lookup"><span data-stu-id="10852-103">To use Single Sign-On (SSO), you must have the following software installed:</span></span>  
  
-   <span data-ttu-id="10852-104">Microsoft BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="10852-104">Microsoft BizTalk Server</span></span>
  
-   <span data-ttu-id="10852-105">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="10852-105">Visual Studio</span></span>  
  
-   <span data-ttu-id="10852-106">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="10852-106">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="10852-107">Un système de serveur prenant en charge SSO</span><span class="sxs-lookup"><span data-stu-id="10852-107">A Server System that supports SSO</span></span>  
  
-   <span data-ttu-id="10852-108">L’hôte isolé doit être configuré en tant que **approuvé par authentification**.</span><span class="sxs-lookup"><span data-stu-id="10852-108">The isolated host should be configured as **Authentication Trusted**.</span></span>  
  
## <a name="enable-sso"></a><span data-ttu-id="10852-109">Activer l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="10852-109">Enable SSO</span></span>  
  
1.  <span data-ttu-id="10852-110">Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.</span><span class="sxs-lookup"><span data-stu-id="10852-110">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="10852-111">Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.</span><span class="sxs-lookup"><span data-stu-id="10852-111">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
 <span data-ttu-id="10852-112">Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications4.md).</span><span class="sxs-lookup"><span data-stu-id="10852-112">For information about creating an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications4.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10852-113">Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser tout dossier partage Web **ne partagent pas**.</span><span class="sxs-lookup"><span data-stu-id="10852-113">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="10852-114">La mise à jour ou la désinstallation d'applications utilisant ce dossier ne pourra pas s'effectuer correctement car, s'il est partagé, il est considéré comme en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="10852-114">Applications using that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10852-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10852-115">See Also</span></span>  
 [<span data-ttu-id="10852-116">Utilisation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="10852-116">Using Single Sign-On</span></span>](../core/using-single-sign-on1.md)
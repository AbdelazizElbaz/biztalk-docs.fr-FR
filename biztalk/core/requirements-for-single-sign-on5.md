---
title: "Configuration requise pour l’authentification unique-On5 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Single Sign-On, requirements [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], Single Sign-On
- SSO, requirements [JD Edwards OneWorld adapters]
- Single Sign-On, enabling [JD Edwards OneWorld adapters]
ms.assetid: 318b9977-ce24-48d6-971b-49a059a1bdbc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b186eca2c24ef9c2731b66194a0543aba14e8bf1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="d4e45-102">Configuration requise pour l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="d4e45-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="d4e45-103">Pour utiliser l’authentification unique (SSO), vous devez :</span><span class="sxs-lookup"><span data-stu-id="d4e45-103">To use Single Sign-On (SSO), you must have:</span></span>  
  
-   <span data-ttu-id="d4e45-104">Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4e45-104">Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]</span></span>  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]  
  
-   <span data-ttu-id="d4e45-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="d4e45-105">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="d4e45-106">Un système de serveur prenant en charge SSO</span><span class="sxs-lookup"><span data-stu-id="d4e45-106">A Server System that supports SSO</span></span>  
  
 <span data-ttu-id="d4e45-107">L’hôte isolé doit être configuré comme approuvé par authentification.</span><span class="sxs-lookup"><span data-stu-id="d4e45-107">The isolated host should be configured as authentication trusted.</span></span>  
  
### <a name="to-enable-sso"></a><span data-ttu-id="d4e45-108">Pour activer SSO</span><span class="sxs-lookup"><span data-stu-id="d4e45-108">To enable SSO</span></span>  
  
1.  <span data-ttu-id="d4e45-109">Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.</span><span class="sxs-lookup"><span data-stu-id="d4e45-109">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="d4e45-110">Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.</span><span class="sxs-lookup"><span data-stu-id="d4e45-110">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
     <span data-ttu-id="d4e45-111">Pour plus d’informations sur la création d’applications associées, consultez [création d’Applications associées](../core/creating-affiliate-applications3.md).</span><span class="sxs-lookup"><span data-stu-id="d4e45-111">For information about creating affiliate applications, see [Creating Affiliate Applications](../core/creating-affiliate-applications3.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4e45-112">Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser les **partage Web** dossier **ne partagent pas**.</span><span class="sxs-lookup"><span data-stu-id="d4e45-112">After performing work using SSO, remember to reset any **Web-Sharing** folder to **Do not share**.</span></span> <span data-ttu-id="d4e45-113">La mise à jour ou la désinstallation d'applications utilisant ce dossier ne pourra pas s'effectuer correctement car, s'il est partagé, il est considéré comme en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="d4e45-113">Applications using that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e45-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4e45-114">See Also</span></span>  
 [<span data-ttu-id="d4e45-115">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="d4e45-115">Using Single Sign-On</span></span>](../core/using-single-sign-on3.md)
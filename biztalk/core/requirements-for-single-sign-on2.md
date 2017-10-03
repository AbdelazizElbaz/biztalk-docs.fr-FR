---
title: "Configuration requise pour l’authentification unique-On2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enabling SSO
- Single Sign-On, requirements
- SSO, enabling
- Single Sign-On, enabling
- SSO requirements
ms.assetid: ae4b5c1f-1718-4628-9159-2fb877498913
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c886792f36808152c4a27733544b09015c68f061
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="3b9ac-102">Configuration requise pour l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="3b9ac-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="3b9ac-103">Pour utiliser l’authentification unique (SSO), vous devez :</span><span class="sxs-lookup"><span data-stu-id="3b9ac-103">To use Single Sign-On (SSO), you need:</span></span>  
  
-   [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]  
  
-   <span data-ttu-id="3b9ac-104">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="3b9ac-104">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="3b9ac-105">Un système de serveur prenant en charge SSO</span><span class="sxs-lookup"><span data-stu-id="3b9ac-105">A Server System that supports SSO</span></span>  
  
 <span data-ttu-id="3b9ac-106">L’hôte isolé doit être configuré comme approuvé par authentification.</span><span class="sxs-lookup"><span data-stu-id="3b9ac-106">The isolated host should be configured as authentication trusted.</span></span>  
  
### <a name="to-enable-sso"></a><span data-ttu-id="3b9ac-107">Pour activer SSO</span><span class="sxs-lookup"><span data-stu-id="3b9ac-107">To enable SSO</span></span>  
  
1.  <span data-ttu-id="3b9ac-108">Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.</span><span class="sxs-lookup"><span data-stu-id="3b9ac-108">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="3b9ac-109">Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.</span><span class="sxs-lookup"><span data-stu-id="3b9ac-109">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
 <span data-ttu-id="3b9ac-110">Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications2.md).</span><span class="sxs-lookup"><span data-stu-id="3b9ac-110">For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications2.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b9ac-111">Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser tout dossier partage Web **ne partagent pas**.</span><span class="sxs-lookup"><span data-stu-id="3b9ac-111">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="3b9ac-112">Les applications qui utilisent ce dossier ne seront pas mise à jour ou désinstaller correctement si le dossier est partagé, car il est considéré comme en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="3b9ac-112">Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b9ac-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b9ac-113">See Also</span></span>  
 <span data-ttu-id="3b9ac-114">[Exécution de projets SSO](../core/running-sso-projects1.md) </span><span class="sxs-lookup"><span data-stu-id="3b9ac-114">[Running SSO Projects](../core/running-sso-projects1.md) </span></span>  
 [<span data-ttu-id="3b9ac-115">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="3b9ac-115">Using Single Sign-On</span></span>](../core/using-single-sign-on2.md)
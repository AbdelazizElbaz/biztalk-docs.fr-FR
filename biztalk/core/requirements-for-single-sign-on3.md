---
title: "Configuration requise pour l’authentification unique-le3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Single Sign-On, requirements
- SSO, enabling
- Single Sign-On, enabling
- SSO requirements
ms.assetid: 7d5c406b-f548-4df0-8644-fdf6a812a989
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 005f095ae09b3018b9c8fe796520205103c7961a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="e10a6-102">Configuration requise pour l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="e10a6-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="e10a6-103">Pour utiliser l'authentification unique (SSO), vous devez disposer des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e10a6-103">To use Single Sign-On (SSO), you must have the following:</span></span>  
  
-   <span data-ttu-id="e10a6-104">Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e10a6-104">Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]</span></span>  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]  
  
-   <span data-ttu-id="e10a6-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="e10a6-105">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="e10a6-106">Un système de serveur qui prend en charge l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="e10a6-106">A server system that supports SSO</span></span>  
  
-   <span data-ttu-id="e10a6-107">L’hôte isolé doit être configuré comme approuvé par authentification.</span><span class="sxs-lookup"><span data-stu-id="e10a6-107">The isolated host should be configured as Authentication Trusted.</span></span>  
  
### <a name="to-enable-sso"></a><span data-ttu-id="e10a6-108">Pour activer SSO</span><span class="sxs-lookup"><span data-stu-id="e10a6-108">To enable SSO</span></span>  
  
1.  <span data-ttu-id="e10a6-109">Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.</span><span class="sxs-lookup"><span data-stu-id="e10a6-109">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="e10a6-110">Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.</span><span class="sxs-lookup"><span data-stu-id="e10a6-110">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
 <span data-ttu-id="e10a6-111">Pour plus d’informations, consultez [création d’Applications associées](../core/creating-affiliate-applications1.md).</span><span class="sxs-lookup"><span data-stu-id="e10a6-111">For more information, see [Creating Affiliate Applications](../core/creating-affiliate-applications1.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e10a6-112">Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser tout dossier partage Web **ne partagent pas**.</span><span class="sxs-lookup"><span data-stu-id="e10a6-112">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="e10a6-113">Les applications qui utilisent ce dossier ne seront pas mise à jour ou désinstaller correctement si le dossier est partagé, car il est considéré comme en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="e10a6-113">Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e10a6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e10a6-114">See Also</span></span>  
 [<span data-ttu-id="e10a6-115">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="e10a6-115">Using Single Sign-On</span></span>](../core/using-single-sign-on5.md)
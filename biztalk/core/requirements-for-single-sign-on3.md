---
title: "Configuration requise pour l’authentification unique sur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d5c406b-f548-4df0-8644-fdf6a812a989
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61932b44364670515f02f89a1441a5d54030bc94
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="03f3f-102">Configuration requise pour l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="03f3f-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="03f3f-103">Pour utiliser l'authentification unique (SSO), vous devez disposer des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="03f3f-103">To use Single Sign-On (SSO), you must have the following:</span></span>  
  
-   <span data-ttu-id="03f3f-104">Microsoft BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="03f3f-104">Microsoft BizTalk Server</span></span>
  
-   <span data-ttu-id="03f3f-105">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="03f3f-105">Visual Studio</span></span>  
  
-   <span data-ttu-id="03f3f-106">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="03f3f-106">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="03f3f-107">Un système de serveur qui prend en charge l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="03f3f-107">A server system that supports SSO</span></span>  
  
-   <span data-ttu-id="03f3f-108">L’hôte isolé doit être configuré comme approuvé par authentification.</span><span class="sxs-lookup"><span data-stu-id="03f3f-108">The isolated host should be configured as Authentication Trusted.</span></span>  
  
## <a name="enable-sso"></a><span data-ttu-id="03f3f-109">Activer l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="03f3f-109">Enable SSO</span></span>  
  
1.  <span data-ttu-id="03f3f-110">Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.</span><span class="sxs-lookup"><span data-stu-id="03f3f-110">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="03f3f-111">Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.</span><span class="sxs-lookup"><span data-stu-id="03f3f-111">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
 <span data-ttu-id="03f3f-112">Pour plus d’informations, consultez [création d’Applications associées](../core/creating-affiliate-applications1.md).</span><span class="sxs-lookup"><span data-stu-id="03f3f-112">For more information, see [Creating Affiliate Applications](../core/creating-affiliate-applications1.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03f3f-113">Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser tout dossier partage Web **ne partagent pas**.</span><span class="sxs-lookup"><span data-stu-id="03f3f-113">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="03f3f-114">Les applications qui utilisent ce dossier ne seront pas mise à jour ou désinstaller correctement si le dossier est partagé, car il est considéré comme en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="03f3f-114">Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f3f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03f3f-115">See Also</span></span>  
 [<span data-ttu-id="03f3f-116">Utilisation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="03f3f-116">Using Single Sign-On</span></span>](../core/using-single-sign-on5.md)
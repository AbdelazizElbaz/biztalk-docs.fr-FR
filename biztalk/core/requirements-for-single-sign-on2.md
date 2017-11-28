---
title: "Configuration requise pour l’authentification unique sur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae4b5c1f-1718-4628-9159-2fb877498913
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e0dc92e4492d36ca8204f61354f8422d7eb47631
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="0aac2-102">Configuration requise pour l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="0aac2-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="0aac2-103">Pour utiliser l’authentification unique (SSO), vous devez :</span><span class="sxs-lookup"><span data-stu-id="0aac2-103">To use Single Sign-On (SSO), you need:</span></span>  
  
-   <span data-ttu-id="0aac2-104">BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="0aac2-104">BizTalk Server</span></span>
  
-   <span data-ttu-id="0aac2-105">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0aac2-105">Visual Studio</span></span>  
  
-   <span data-ttu-id="0aac2-106">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="0aac2-106">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="0aac2-107">Un système de serveur prenant en charge SSO</span><span class="sxs-lookup"><span data-stu-id="0aac2-107">A Server System that supports SSO</span></span>  
  
 <span data-ttu-id="0aac2-108">L’hôte isolé doit être configuré comme approuvé par authentification.</span><span class="sxs-lookup"><span data-stu-id="0aac2-108">The isolated host should be configured as authentication trusted.</span></span>  
  
## <a name="enable-sso"></a><span data-ttu-id="0aac2-109">Activer l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="0aac2-109">Enable SSO</span></span>  
  
1.  <span data-ttu-id="0aac2-110">Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.</span><span class="sxs-lookup"><span data-stu-id="0aac2-110">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="0aac2-111">Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.</span><span class="sxs-lookup"><span data-stu-id="0aac2-111">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
 <span data-ttu-id="0aac2-112">Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications2.md).</span><span class="sxs-lookup"><span data-stu-id="0aac2-112">For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications2.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0aac2-113">Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser tout dossier partage Web **ne partagent pas**.</span><span class="sxs-lookup"><span data-stu-id="0aac2-113">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="0aac2-114">Les applications qui utilisent ce dossier ne seront pas mise à jour ou désinstaller correctement si le dossier est partagé, car il est considéré comme en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="0aac2-114">Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aac2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0aac2-115">See Also</span></span>  
 <span data-ttu-id="0aac2-116">[Exécution de projets SSO](../core/running-sso-projects1.md) </span><span class="sxs-lookup"><span data-stu-id="0aac2-116">[Running SSO Projects](../core/running-sso-projects1.md) </span></span>  
 [<span data-ttu-id="0aac2-117">Sécuriser l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="0aac2-117">Secure the adapter</span></span>](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)
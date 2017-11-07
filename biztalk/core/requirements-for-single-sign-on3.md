---
title: "Configuration requise de l’authentification unique pour l’adaptateur TIBCO Rendevous | Documents Microsoft"
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
ms.openlocfilehash: 40cf27a3b96534239fa871bd04b90febee9beafe
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="c029f-102">Configuration requise pour l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="c029f-102">Requirements for Single Sign-On</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c029f-103">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="c029f-103">Prerequisites</span></span>
<span data-ttu-id="c029f-104">Pour utiliser l'authentification unique (SSO), vous devez disposer des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="c029f-104">To use Single Sign-On (SSO), you must have the following:</span></span>  
  
-   <span data-ttu-id="c029f-105">Microsoft BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c029f-105">Microsoft BizTalk Server</span></span>
  
-   <span data-ttu-id="c029f-106">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c029f-106">Visual Studio</span></span>  
  
-   <span data-ttu-id="c029f-107">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="c029f-107">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="c029f-108">Un système de serveur qui prend en charge l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="c029f-108">A server system that supports SSO</span></span>  
  
-   <span data-ttu-id="c029f-109">L’hôte isolé doit être configuré comme approuvé par authentification.</span><span class="sxs-lookup"><span data-stu-id="c029f-109">The isolated host should be configured as Authentication Trusted.</span></span>  
  
## <a name="enable-sso"></a><span data-ttu-id="c029f-110">Activer l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="c029f-110">Enable SSO</span></span>  
  
1.  <span data-ttu-id="c029f-111">Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.</span><span class="sxs-lookup"><span data-stu-id="c029f-111">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="c029f-112">Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.</span><span class="sxs-lookup"><span data-stu-id="c029f-112">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
 <span data-ttu-id="c029f-113">Pour plus d’informations, consultez [création d’Applications associées](../core/creating-affiliate-applications1.md).</span><span class="sxs-lookup"><span data-stu-id="c029f-113">For more information, see [Creating Affiliate Applications](../core/creating-affiliate-applications1.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c029f-114">Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser tout dossier partage Web **ne partagent pas**.</span><span class="sxs-lookup"><span data-stu-id="c029f-114">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="c029f-115">Les applications qui utilisent ce dossier ne seront pas mise à jour ou désinstaller correctement si le dossier est partagé, car il est considéré comme en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="c029f-115">Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c029f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c029f-116">See Also</span></span>  
[<span data-ttu-id="c029f-117">Sécurité</span><span class="sxs-lookup"><span data-stu-id="c029f-117">Security</span></span>](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)
---
title: "Configuration requise pour l’authentification unique sur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 645c7b3f-f860-4c20-b5ca-a8fb93736344
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98d5164fa194f9a02314b897b267d9873879a9c0
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="b12e6-102">Configuration requise pour l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="b12e6-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="b12e6-103">L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service (EMS) prend en charge l'authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="b12e6-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) provides Single Sign-On (SSO) support.</span></span> <span data-ttu-id="b12e6-104">Une application associée qui a été créée par des outils de l'authentification unique de l'entreprise représente un système serveur tel que TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="b12e6-104">An affiliate application created by Enterprise Single Sign-On tools represents a server system such as TIBCO EMS.</span></span>  
  
 <span data-ttu-id="b12e6-105">Pour utiliser l'authentification unique, vous devez disposer des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b12e6-105">To use Single Sign-On, you must have:</span></span>  
  
-   <span data-ttu-id="b12e6-106">Microsoft BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b12e6-106">Microsoft BizTalk Server</span></span>
  
-   <span data-ttu-id="b12e6-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b12e6-107">Visual Studio</span></span>  
  
-   <span data-ttu-id="b12e6-108">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="b12e6-108">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="b12e6-109">Un système de serveur qui prend en charge l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="b12e6-109">A server system that supports SSO</span></span>  
  
 <span data-ttu-id="b12e6-110">L'hôte isolé doit être configuré comme approuvé par authentification.</span><span class="sxs-lookup"><span data-stu-id="b12e6-110">The isolated host should be configured as authentication trusted</span></span>  
  
## <a name="enable-sso"></a><span data-ttu-id="b12e6-111">Activer l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="b12e6-111">Enable SSO</span></span>  
  
1.  <span data-ttu-id="b12e6-112">Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.</span><span class="sxs-lookup"><span data-stu-id="b12e6-112">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="b12e6-113">Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.</span><span class="sxs-lookup"><span data-stu-id="b12e6-113">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
     <span data-ttu-id="b12e6-114">Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications5.md).</span><span class="sxs-lookup"><span data-stu-id="b12e6-114">For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b12e6-115">Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser tout dossier partage Web **ne partagent pas**.</span><span class="sxs-lookup"><span data-stu-id="b12e6-115">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="b12e6-116">Les applications qui utilisent ce dossier ne seront pas mise à jour ou désinstaller correctement si le dossier est partagé, car il est considéré comme en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="b12e6-116">Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b12e6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b12e6-117">See Also</span></span>  
 [<span data-ttu-id="b12e6-118">Utilisation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="b12e6-118">Using Single Sign-On</span></span>](../core/using-single-sign-on4.md)
---
title: "Configuration requise pour l’authentification unique-le4 | Documents Microsoft"
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
ms.assetid: 645c7b3f-f860-4c20-b5ca-a8fb93736344
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15d7bdbf52869e5b13ae113716689bbb5b7ffec3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="requirements-for-single-sign-on"></a><span data-ttu-id="d7d41-102">Configuration requise pour l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="d7d41-102">Requirements for Single Sign-On</span></span>
<span data-ttu-id="d7d41-103">L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service (EMS) prend en charge l'authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="d7d41-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) provides Single Sign-On (SSO) support.</span></span> <span data-ttu-id="d7d41-104">Une application associée qui a été créée par des outils de l'authentification unique de l'entreprise représente un système serveur tel que TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="d7d41-104">An affiliate application created by Enterprise Single Sign-On tools represents a server system such as TIBCO EMS.</span></span>  
  
 <span data-ttu-id="d7d41-105">Pour utiliser l'authentification unique, vous devez disposer des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="d7d41-105">To use Single Sign-On, you must have:</span></span>  
  
-   <span data-ttu-id="d7d41-106">Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7d41-106">Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]</span></span>  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]  
  
-   <span data-ttu-id="d7d41-107">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="d7d41-107">Enterprise Single Sign-On</span></span>  
  
-   <span data-ttu-id="d7d41-108">Un système de serveur qui prend en charge l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="d7d41-108">A server system that supports SSO</span></span>  
  
 <span data-ttu-id="d7d41-109">L'hôte isolé doit être configuré comme approuvé par authentification.</span><span class="sxs-lookup"><span data-stu-id="d7d41-109">The isolated host should be configured as authentication trusted</span></span>  
  
### <a name="to-enable-sso"></a><span data-ttu-id="d7d41-110">Pour activer SSO</span><span class="sxs-lookup"><span data-stu-id="d7d41-110">To enable SSO</span></span>  
  
1.  <span data-ttu-id="d7d41-111">Dans le **propriétés du Transport** fenêtre, sélectionnez **Oui** pour **utiliser SSO**.</span><span class="sxs-lookup"><span data-stu-id="d7d41-111">In the **Transport Properties** window, select **Yes** for **Use SSO**.</span></span>  
  
2.  <span data-ttu-id="d7d41-112">Lorsque vous spécifiez des propriétés de transport, sélectionnez une application associée appropriée.</span><span class="sxs-lookup"><span data-stu-id="d7d41-112">Select an appropriate affiliate application when specifying transport properties.</span></span>  
  
     <span data-ttu-id="d7d41-113">Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications5.md).</span><span class="sxs-lookup"><span data-stu-id="d7d41-113">For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7d41-114">Après avoir effectué un travail à l’aide de l’authentification unique, n’oubliez pas de réinitialiser tout dossier partage Web **ne partagent pas**.</span><span class="sxs-lookup"><span data-stu-id="d7d41-114">After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**.</span></span> <span data-ttu-id="d7d41-115">Les applications qui utilisent ce dossier ne seront pas mise à jour ou désinstaller correctement si le dossier est partagé, car il est considéré comme en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="d7d41-115">Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7d41-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7d41-116">See Also</span></span>  
 [<span data-ttu-id="d7d41-117">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="d7d41-117">Using Single Sign-On</span></span>](../core/using-single-sign-on4.md)
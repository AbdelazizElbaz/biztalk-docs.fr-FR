---
title: "Configuration pour la récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: acdafe68-c8bf-4064-afca-6dfd22d15052
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8c6a188255097f0a1c1e85086688252f9154b36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-for-disaster-recovery"></a><span data-ttu-id="59013-102">Configuration pour la récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="59013-102">Configuring for Disaster Recovery</span></span>
<span data-ttu-id="59013-103">Le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] fonctionnalité d’envoi de journaux étend la sauvegarde existante [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travail.</span><span class="sxs-lookup"><span data-stu-id="59013-103">The [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Log Shipping feature extends the existing Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job.</span></span> [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="59013-104">Envoi de journaux élimine le besoin de restaurer manuellement une série de produits par la tâche de sauvegarde de jeux de sauvegarde et réduit le temps mort en cas de défaillance du système.</span><span class="sxs-lookup"><span data-stu-id="59013-104"> Log Shipping eliminates the need to manually restore a series of backup sets produced by the backup job, and reduces downtime in the event of a system failure.</span></span> [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="59013-105">Envoi de journaux est un composant essentiel pour les procédures de récupération d’urgence de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="59013-105"> Log Shipping is a critical component for BizTalk disaster recovery procedures.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59013-106">Chaque équipe de l’application doit disposer d’une sauvegarde documentée et restaurer le plan de récupération d’urgence qui complète les concepts présentés dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="59013-106">Each application team must have a documented backup and restore plan for disaster recovery that complements the concepts provided in this topic.</span></span> <span data-ttu-id="59013-107">Plan global doit répondre à l’ensemble du système, y compris les applications et les composants du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="59013-107">The overall plan should address the entire system, including applications and the components of the operating system.</span></span>  
  
 <span data-ttu-id="59013-108">Exécution d’une opération de récupération d’urgence est très similaire à effectuer manuellement une restauration d’un groupe BizTalk à un nouveau jeu de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances de base de données.</span><span class="sxs-lookup"><span data-stu-id="59013-108">Performing a disaster recovery operation is very similar to manually performing a restore of a BizTalk group to a new set of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database instances.</span></span> <span data-ttu-id="59013-109">La principale différence est que [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] d’envoi de journaux applique des journaux en continu sur le site de récupération d’urgence, l’enregistrement de nombreuses étapes manuelles.</span><span class="sxs-lookup"><span data-stu-id="59013-109">The primary difference is that [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] log shipping applies logs continuously at the disaster recovery site, saving many manual steps.</span></span> <span data-ttu-id="59013-110">Par conséquent, uniquement le dernier ensemble de journaux doit être restauré manuellement lorsque [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] d’envoi de journaux est implémentée.</span><span class="sxs-lookup"><span data-stu-id="59013-110">Therefore, only the last set of logs must be restored manually when [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] log shipping is implemented.</span></span> <span data-ttu-id="59013-111">Dans le cas contraire, la dernière sauvegarde complète suivie de toutes les sauvegardes du journal depuis la dernière sauvegarde complète devrait être restauré manuellement.</span><span class="sxs-lookup"><span data-stu-id="59013-111">Otherwise, the last full backup followed by all log backups since the last full backup would have to be manually restored.</span></span> [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="59013-112">envoi de journaux réduit l’effort pour ce processus manuel, ce qui accélère la restauration du site de récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="59013-112"> log shipping reduces the effort for this manual process, speeding restoration of the disaster recovery site.</span></span>  
  
 <span data-ttu-id="59013-113">Cette section fournit des recommandations sur la configuration de production pour faciliter le processus de récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="59013-113">This section covers recommendations on production configuration to facilitate the disaster recovery process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="59013-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="59013-114">In This Section</span></span>  
  
-   [<span data-ttu-id="59013-115">Préparer le Site de récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="59013-115">Prepare the Disaster Recovery Site</span></span>](../technical-guides/prepare-the-disaster-recovery-site.md)  
  
-   [<span data-ttu-id="59013-116">Journaux de rôles et les comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="59013-116">Log Shipping User Accounts and Roles</span></span>](../technical-guides/log-shipping-user-accounts-and-roles.md)  
  
-   [<span data-ttu-id="59013-117">Journaux de configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="59013-117">Configuring BizTalk Server Log Shipping</span></span>](../technical-guides/configuring-biztalk-server-log-shipping.md)  
  
## <a name="see-also"></a><span data-ttu-id="59013-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59013-118">See Also</span></span>  
 [<span data-ttu-id="59013-119">Récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="59013-119">Disaster Recovery</span></span>](../technical-guides/disaster-recovery.md)
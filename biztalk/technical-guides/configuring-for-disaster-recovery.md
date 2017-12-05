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
ms.openlocfilehash: 3899b27324fa00e0b5c630c7be4433f65a917a1b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-for-disaster-recovery"></a><span data-ttu-id="7fa42-102">Configuration pour la récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="7fa42-102">Configuring for Disaster Recovery</span></span>
<span data-ttu-id="7fa42-103">La fonctionnalité d’envoi de journaux de BizTalk Server étend la sauvegarde existante [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travail.</span><span class="sxs-lookup"><span data-stu-id="7fa42-103">The BizTalk Server Log Shipping feature extends the existing Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job.</span></span> <span data-ttu-id="7fa42-104">Envoi de journaux de BizTalk Server élimine le besoin de restaurer manuellement une série de produits par la tâche de sauvegarde de jeux de sauvegarde et réduit le temps mort en cas de défaillance du système.</span><span class="sxs-lookup"><span data-stu-id="7fa42-104">BizTalk Server Log Shipping eliminates the need to manually restore a series of backup sets produced by the backup job, and reduces downtime in the event of a system failure.</span></span> <span data-ttu-id="7fa42-105">Envoi de journaux de BizTalk Server est un composant essentiel pour les procédures de récupération d’urgence de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7fa42-105">BizTalk Server Log Shipping is a critical component for BizTalk disaster recovery procedures.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7fa42-106">Chaque équipe de l’application doit disposer d’une sauvegarde documentée et restaurer le plan de récupération d’urgence qui complète les concepts présentés dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="7fa42-106">Each application team must have a documented backup and restore plan for disaster recovery that complements the concepts provided in this topic.</span></span> <span data-ttu-id="7fa42-107">Plan global doit répondre à l’ensemble du système, y compris les applications et les composants du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="7fa42-107">The overall plan should address the entire system, including applications and the components of the operating system.</span></span>  
  
 <span data-ttu-id="7fa42-108">Exécution d’une opération de récupération d’urgence est très similaire à effectuer manuellement une restauration d’un groupe BizTalk à un nouveau jeu de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances de base de données.</span><span class="sxs-lookup"><span data-stu-id="7fa42-108">Performing a disaster recovery operation is very similar to manually performing a restore of a BizTalk group to a new set of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database instances.</span></span> <span data-ttu-id="7fa42-109">La principale différence est que journaux de BizTalk Server expédition applique des journaux en continu sur le site de récupération d’urgence, l’enregistrement de nombreuses étapes manuelles.</span><span class="sxs-lookup"><span data-stu-id="7fa42-109">The primary difference is that BizTalk Server log shipping applies logs continuously at the disaster recovery site, saving many manual steps.</span></span> <span data-ttu-id="7fa42-110">Par conséquent, uniquement le dernier ensemble de journaux doit être restauré manuellement lorsque BizTalk Server d’envoi de journaux est implémentée.</span><span class="sxs-lookup"><span data-stu-id="7fa42-110">Therefore, only the last set of logs must be restored manually when BizTalk Server log shipping is implemented.</span></span> <span data-ttu-id="7fa42-111">Dans le cas contraire, la dernière sauvegarde complète suivie de toutes les sauvegardes du journal depuis la dernière sauvegarde complète devrait être restauré manuellement.</span><span class="sxs-lookup"><span data-stu-id="7fa42-111">Otherwise, the last full backup followed by all log backups since the last full backup would have to be manually restored.</span></span> <span data-ttu-id="7fa42-112">Journaux de BizTalk Server expédition réduit l’effort fourni pour ce processus manuel, ce qui accélère la restauration du site de récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="7fa42-112">BizTalk Server log shipping reduces the effort for this manual process, speeding restoration of the disaster recovery site.</span></span>  
  
 <span data-ttu-id="7fa42-113">Cette section fournit des recommandations sur la configuration de production pour faciliter le processus de récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="7fa42-113">This section covers recommendations on production configuration to facilitate the disaster recovery process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7fa42-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7fa42-114">In This Section</span></span>  
  
-   [<span data-ttu-id="7fa42-115">Préparer le site de récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="7fa42-115">Prepare the Disaster Recovery Site</span></span>](../technical-guides/prepare-the-disaster-recovery-site.md)  
  
-   [<span data-ttu-id="7fa42-116">Comptes d’utilisateur et rôles pour la copie des journaux de transaction</span><span class="sxs-lookup"><span data-stu-id="7fa42-116">Log Shipping User Accounts and Roles</span></span>](../technical-guides/log-shipping-user-accounts-and-roles.md)  
  
-   [<span data-ttu-id="7fa42-117">Configuration de la copie des journaux de transaction BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7fa42-117">Configuring BizTalk Server Log Shipping</span></span>](../technical-guides/configuring-biztalk-server-log-shipping.md)  
  
## <a name="see-also"></a><span data-ttu-id="7fa42-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7fa42-118">See Also</span></span>  
 [<span data-ttu-id="7fa42-119">Récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="7fa42-119">Disaster Recovery</span></span>](../technical-guides/disaster-recovery.md)
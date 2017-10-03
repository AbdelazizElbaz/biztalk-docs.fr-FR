---
title: "Restauration de Production à partir d’une sauvegarde à chaud | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bda14b8-b3cc-4a5e-a353-fca5885fd594
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e590b4eccb6ee946a915ff1f3a0265bbfe977e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="restoring-production-from-a-warm-backup"></a><span data-ttu-id="5e6bf-102">Restauration de Production à partir d’une sauvegarde à chaud</span><span class="sxs-lookup"><span data-stu-id="5e6bf-102">Restoring Production from a Warm Backup</span></span>
<span data-ttu-id="5e6bf-103">Si le système source devient non fiable, il est possible de restaurer les bases de données à partir de la destination à la source.</span><span class="sxs-lookup"><span data-stu-id="5e6bf-103">If the source system becomes unreliable, it is possible to restore the databases from the destination to the source.</span></span> <span data-ttu-id="5e6bf-104">Effectuez la procédure suivante pour restaurer des bases de données à partir de la destination à la source.</span><span class="sxs-lookup"><span data-stu-id="5e6bf-104">Perform the following procedure to restore databases from the destination to the source.</span></span>  
  
### <a name="to-restore-the-databases-from-the-destination-to-the-source-follow-these-steps"></a><span data-ttu-id="5e6bf-105">Pour restaurer les bases de données à partir de la destination à la source, procédez comme suit</span><span class="sxs-lookup"><span data-stu-id="5e6bf-105">To restore the databases from the destination to the source follow these steps</span></span>  
  
1.  <span data-ttu-id="5e6bf-106">Désactiver tous les travaux de sauvegarde sur la source (production) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="5e6bf-106">Disable all backup jobs on the source (production) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
2.  <span data-ttu-id="5e6bf-107">Attendre que tous les travaux sur la récupération d’urgence (DR) destination de restauration [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="5e6bf-107">Wait for all restore jobs to complete on the destination disaster recovery (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
3.  <span data-ttu-id="5e6bf-108">Désactiver tous les travaux de restauration sur la destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="5e6bf-108">Disable all restore jobs on the destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
4.  <span data-ttu-id="5e6bf-109">Restaurer toutes les bases de données avec STOPATMARK sur la destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="5e6bf-109">Restore all databases with STOPATMARK on the destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
5.  <span data-ttu-id="5e6bf-110">Arrêtez tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services sur tous les serveurs BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5e6bf-110">Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services on all BizTalk servers.</span></span>  
  
6.  <span data-ttu-id="5e6bf-111">Supprimer tous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-bases de données sur la source (production) associées [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="5e6bf-111">Drop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-related databases on the source (production) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
7.  <span data-ttu-id="5e6bf-112">Sauvegardez toutes les bases de données (complète) sur la destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="5e6bf-112">Back up (full) all databases on the destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
8.  <span data-ttu-id="5e6bf-113">Restaurer (installation complète), toutes les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sauvegardées à l’étape 7 pour la source (production) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="5e6bf-113">Restore (full) all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases backed up in step 7 to the source (production) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
9. <span data-ttu-id="5e6bf-114">Redémarrez tous les serveurs BizTalk, y compris le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="5e6bf-114">Restart all BizTalk servers including the master secret server.</span></span>  
  
10. <span data-ttu-id="5e6bf-115">Supprimer tous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-bases de données sur la destination (DR) associées [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="5e6bf-115">Drop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-related databases on the destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
11. <span data-ttu-id="5e6bf-116">Activer les travaux de sauvegarde de la source de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="5e6bf-116">Enable backup jobs on the source [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
12. <span data-ttu-id="5e6bf-117">Activer les travaux de restauration sur la destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="5e6bf-117">Enable restore jobs on the destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e6bf-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e6bf-118">See Also</span></span>  
 [<span data-ttu-id="5e6bf-119">Informations avancées sur la sauvegarde et Restore2</span><span class="sxs-lookup"><span data-stu-id="5e6bf-119">Advanced Information About Backup and Restore2</span></span>](../technical-guides/advanced-information-about-backup-and-restore2.md)
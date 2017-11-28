---
title: "Meilleures pratiques pour la récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afbb0a57-0d31-4a2f-847c-02b40361c0ed
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e988055205203c5c4bc7a4d9d6e84706414967c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-disaster-recovery"></a><span data-ttu-id="f6053-102">Meilleures pratiques pour la récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="f6053-102">Best Practices for Disaster Recovery</span></span>
<span data-ttu-id="f6053-103">Pour plus d’informations sur les meilleures pratiques pour la récupération d’urgence [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], consultez [meilleures pratiques pour la sauvegarde et restauration](http://go.microsoft.com/fwlink/?LinkId=151391) (http://go.microsoft.com/fwlink/?LinkId=151391) dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="f6053-103">For information about best practices for disaster recovery for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], see [Best Practices for Backup and Restore](http://go.microsoft.com/fwlink/?LinkId=151391) (http://go.microsoft.com/fwlink/?LinkId=151391) in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
 <span data-ttu-id="f6053-104">**Créez une sauvegarde et le plan de restauration**</span><span class="sxs-lookup"><span data-stu-id="f6053-104">**Create a backup and restore plan**</span></span>  
  
-   <span data-ttu-id="f6053-105">Assurez-vous que votre plan de sauvegarde indique :</span><span class="sxs-lookup"><span data-stu-id="f6053-105">Be sure your backup plan specifies:</span></span>  
  
    -   <span data-ttu-id="f6053-106">l'ordinateur sur lequel de les sauvegardes seront stockées ;</span><span class="sxs-lookup"><span data-stu-id="f6053-106">The computer where backups will be stored</span></span>  
  
    -   <span data-ttu-id="f6053-107">les programmes à utiliser pour sauvegarder votre système ;</span><span class="sxs-lookup"><span data-stu-id="f6053-107">The programs that you will use to back up your system</span></span>  
  
    -   <span data-ttu-id="f6053-108">les ordinateurs à sauvegarder ;</span><span class="sxs-lookup"><span data-stu-id="f6053-108">The computers you want to back up</span></span>  
  
    -   <span data-ttu-id="f6053-109">La planification des sauvegardes ;</span><span class="sxs-lookup"><span data-stu-id="f6053-109">The schedule when backups will occur</span></span>  
  
    -   <span data-ttu-id="f6053-110">l'emplacement hors site où archiver les sauvegardes.</span><span class="sxs-lookup"><span data-stu-id="f6053-110">The offsite location where you will archive backups</span></span>  
  
 <span data-ttu-id="f6053-111">**Conserver un enregistrement écrit de toutes les modifications apportées à votre système BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="f6053-111">**Keep a written record of all changes to your BizTalk Server system**</span></span>  
  
-   <span data-ttu-id="f6053-112">Veillez à noter toutes les modifications apportées à votre système, telles que les Service packs, les correctifs et QFE qui ont été appliqués.</span><span class="sxs-lookup"><span data-stu-id="f6053-112">Be sure to write down all changes to your system, such as service packs, hotfixes, and QFEs that have been applied.</span></span> <span data-ttu-id="f6053-113">Cela est essentiel pour obtenir que votre système soit restauré dans l'état le plus proche possible de celui dans lequel il était avant la défaillance matérielle.</span><span class="sxs-lookup"><span data-stu-id="f6053-113">This is crucial to getting your system restored as closely as possible to what existed before the hardware failure.</span></span>  
  
 <span data-ttu-id="f6053-114">**Implémentez les mesures suivantes pour aider à éviter ou minimiser l’effet d’un incident**</span><span class="sxs-lookup"><span data-stu-id="f6053-114">**Implement the following measures to help prevent or minimize the effect of a disaster**</span></span>  
  
-   <span data-ttu-id="f6053-115">Procurez-vous les mises à jour de logiciels et de microprogramme disponibles.</span><span class="sxs-lookup"><span data-stu-id="f6053-115">Have your software and firmware updates available.</span></span>  
  
-   <span data-ttu-id="f6053-116">Avoir tous les disques de logiciels disponibles.</span><span class="sxs-lookup"><span data-stu-id="f6053-116">Have all software disks readily available.</span></span>  
  
-   <span data-ttu-id="f6053-117">Élaborez un plan pour surveiller les serveurs de façon proactive.</span><span class="sxs-lookup"><span data-stu-id="f6053-117">Have a plan to monitor servers proactively.</span></span> <span data-ttu-id="f6053-118">Ceci est très important, car les instances d’orchestration sur un hôte défaillant ne peuvent pas être récupérés par un deuxième hôte pendant 10 minutes.</span><span class="sxs-lookup"><span data-stu-id="f6053-118">This is very important since orchestration instances on a failed host may not be recovered by a second host for up to 10 minutes.</span></span>  
  
-   <span data-ttu-id="f6053-119">Tenez à jour les enregistrements de matériel.</span><span class="sxs-lookup"><span data-stu-id="f6053-119">Maintain hardware records.</span></span>  
  
-   <span data-ttu-id="f6053-120">Tenez à jour les enregistrements de logiciels.</span><span class="sxs-lookup"><span data-stu-id="f6053-120">Maintain software records.</span></span>  
  
 <span data-ttu-id="f6053-121">**Mettre en œuvre la tolérance de panne de votre organisation au niveau du matériel ou logiciel**</span><span class="sxs-lookup"><span data-stu-id="f6053-121">**Implement fault tolerance in your organization at the hardware or software level**</span></span>  
  
-   <span data-ttu-id="f6053-122">L'implémentation de clusters et de RAID (redundant array of independent disks) garantit que votre système puisse surmonter une panne matérielle.</span><span class="sxs-lookup"><span data-stu-id="f6053-122">Implementing clusters and redundant array of independent disks (RAID) helps ensure that your system can survive a hardware failure.</span></span>  
  
 <span data-ttu-id="f6053-123">**Archive le support de sauvegarde sur une base régulière dans un emplacement sécurisé**</span><span class="sxs-lookup"><span data-stu-id="f6053-123">**Archive the backup media on a regular basis in a secure location**</span></span>  
  
-   <span data-ttu-id="f6053-124">Planifiez l'archivage de votre support de sauvegarde à intervalles réguliers et conservez les archives en lieu sûr, hors site.</span><span class="sxs-lookup"><span data-stu-id="f6053-124">Create a schedule for archiving your backup media on a regular basis and keep the archives in a secure, offsite location.</span></span> <span data-ttu-id="f6053-125">Cela vous garantit de disposer d'une sauvegarde disponible quand vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="f6053-125">This ensures that you have a backup available when you need it.</span></span>  
  
 <span data-ttu-id="f6053-126">**Vérifier l’intégrité de vos sauvegardes et l’absence d’erreur**</span><span class="sxs-lookup"><span data-stu-id="f6053-126">**Verify the integrity of your backups and that they occur without error**</span></span>  
  
-   <span data-ttu-id="f6053-127">Surveillez toutes vos opérations de sauvegarde et veillez à ce qu'elle s'opèrent sans erreurs.</span><span class="sxs-lookup"><span data-stu-id="f6053-127">Monitor all of your backup jobs and ensure that they complete without any errors.</span></span>  
  
 <span data-ttu-id="f6053-128">**Conserver le même matériel de rechange**</span><span class="sxs-lookup"><span data-stu-id="f6053-128">**Keep identical spare hardware available**</span></span>  
  
-   <span data-ttu-id="f6053-129">Matériel identique de rechange disponible permet de garantir que vous pouvez remplacer rapidement matériel défectueux pour être opérationnel et en cours d’exécution plus rapidement.</span><span class="sxs-lookup"><span data-stu-id="f6053-129">Having identical spare hardware available ensures that you can quickly replace defective hardware to get up and running more quickly.</span></span>  
  
 <span data-ttu-id="f6053-130">**Documentez et testez vos procédures de récupération**</span><span class="sxs-lookup"><span data-stu-id="f6053-130">**Document and test your recovery procedures**</span></span>  
  
-   <span data-ttu-id="f6053-131">Test de la récupération d’urgence doit être effectuée avant d’exécuter jamais votre système de production.</span><span class="sxs-lookup"><span data-stu-id="f6053-131">Disaster recovery testing should be conducted before ever running your system in production.</span></span> <span data-ttu-id="f6053-132">Le fait de disposer de plans bien en place et d'effectuer des tests préliminaires garantit que votre personnel informatique puisse récupérer vos systèmes BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f6053-132">Having plans in place and performing prerelease testing will ensure that your IT staff can recover your BizTalk Server systems.</span></span>  
  
 <span data-ttu-id="f6053-133">**Formez votre personnel informatique sur les procédures de récupération d’urgence**</span><span class="sxs-lookup"><span data-stu-id="f6053-133">**Train your IT staff on disaster recovery procedures**</span></span>  
  
-   <span data-ttu-id="f6053-134">Assurez-vous que votre personnel informatique est préparé pour la récupération du système en cas de besoin.</span><span class="sxs-lookup"><span data-stu-id="f6053-134">Ensure that your IT staff is prepared to recover the system should the need arise.</span></span>  
  
 <span data-ttu-id="f6053-135">**Exercez-vous à restaurer à partir d’une sauvegarde dans un environnement de test**</span><span class="sxs-lookup"><span data-stu-id="f6053-135">**Practice restoring from a backup in a test environment**</span></span>  
  
-   <span data-ttu-id="f6053-136">Exercez-vous à restaurer le système BizTalk Server dans un environnement de test pour être certain de pouvoir le restaurer dans votre environnement de production en cas de défaillance.</span><span class="sxs-lookup"><span data-stu-id="f6053-136">Practice restoring your BizTalk Server system in a test environment to ensure that you can restore it to your production environment if a failure occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6053-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6053-137">See Also</span></span>  
 [<span data-ttu-id="f6053-138">Récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="f6053-138">Disaster Recovery</span></span>](../technical-guides/disaster-recovery.md)
---
title: Meilleures pratiques pour la sauvegarde et de restauration | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aaf721ba-50ce-4334-b86d-e856b54d3486
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23657dcc843744741d6315b6a8c18ca3d35e1fe4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-backup-and-restore"></a><span data-ttu-id="dbbe7-102">Méthodes conseillées pour la sauvegarde et la restauration</span><span class="sxs-lookup"><span data-stu-id="dbbe7-102">Best Practices for Backup and Restore</span></span>
-   <span data-ttu-id="dbbe7-103">**Créez une sauvegarde et le plan de restauration**</span><span class="sxs-lookup"><span data-stu-id="dbbe7-103">**Create a backup and restore plan**</span></span>  
  
     <span data-ttu-id="dbbe7-104">Assurez-vous que votre plan de sauvegarde indique :</span><span class="sxs-lookup"><span data-stu-id="dbbe7-104">Be sure your backup plan specifies:</span></span>  
  
    -   <span data-ttu-id="dbbe7-105">l'ordinateur sur lequel de les sauvegardes seront stockées ;</span><span class="sxs-lookup"><span data-stu-id="dbbe7-105">The computer where backups will be stored</span></span>  
  
    -   <span data-ttu-id="dbbe7-106">les programmes à utiliser pour sauvegarder votre système ;</span><span class="sxs-lookup"><span data-stu-id="dbbe7-106">The programs that you will use to back up your system</span></span>  
  
    -   <span data-ttu-id="dbbe7-107">les ordinateurs à sauvegarder ;</span><span class="sxs-lookup"><span data-stu-id="dbbe7-107">The computers you want to back up</span></span>  
  
    -   <span data-ttu-id="dbbe7-108">La planification des sauvegardes ;</span><span class="sxs-lookup"><span data-stu-id="dbbe7-108">The schedule when backups will occur</span></span>  
  
    -   <span data-ttu-id="dbbe7-109">l'emplacement hors site où archiver les sauvegardes.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-109">The offsite location where you will archive backups</span></span>  
  
-   <span data-ttu-id="dbbe7-110">**Conserver un enregistrement écrit de toutes les modifications apportées à votre système BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="dbbe7-110">**Keep a written record of all changes to your BizTalk Server system**</span></span>  
  
     <span data-ttu-id="dbbe7-111">Veillez à noter toutes les modifications apportées à votre système, telles que les Service packs, les correctifs et QFE qui ont été appliqués.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-111">Be sure to write down all changes to your system, such as service packs, hotfixes, and QFEs that have been applied.</span></span> <span data-ttu-id="dbbe7-112">Cela est essentiel pour obtenir que votre système soit restauré dans l'état le plus proche possible de celui dans lequel il était avant la défaillance matérielle.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-112">This is crucial to getting your system restored as closely as possible to what existed before the hardware failure.</span></span>  
  
-   <span data-ttu-id="dbbe7-113">**Implémentez les mesures suivantes pour aider à éviter ou minimiser l’effet d’un sinistre :**</span><span class="sxs-lookup"><span data-stu-id="dbbe7-113">**Implement the following measures to help prevent or minimize the effect of a disaster:**</span></span>  
  
    -   <span data-ttu-id="dbbe7-114">Procurez-vous les mises à jour de logiciels et de microprogramme disponibles.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-114">Have your software and firmware updates available.</span></span>  
  
    -   <span data-ttu-id="dbbe7-115">Munissez-vous de tous les disques d'installation de logiciels immédiatement disponibles.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-115">Have all software installation disks readily available.</span></span> <span data-ttu-id="dbbe7-116">Cela inclut des logiciels système tels que des pilotes spécialisés et des applications telles que BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-116">This includes both system software such as specialized drivers, and application software such as BizTalk Server.</span></span>  
  
    -   <span data-ttu-id="dbbe7-117">Élaborez un plan pour surveiller les serveurs de façon proactive.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-117">Have a plan to monitor servers proactively.</span></span> <span data-ttu-id="dbbe7-118">C'est très important puisque les instances d'orchestration sur un hôte défaillant risquent de ne pas être récupérées par un deuxième hôte pendant dix minutes.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-118">This is very important, since orchestration instances on a failed host may not be recovered by a second host for up to ten minutes.</span></span>  
  
    -   <span data-ttu-id="dbbe7-119">Tenez à jour les enregistrements de matériel.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-119">Maintain hardware records.</span></span>  
  
    -   <span data-ttu-id="dbbe7-120">Tenez à jour les enregistrements de logiciels.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-120">Maintain software records.</span></span>  
  
-   <span data-ttu-id="dbbe7-121">**Mettre en œuvre la tolérance de panne de votre organisation au niveau du matériel ou logiciel**</span><span class="sxs-lookup"><span data-stu-id="dbbe7-121">**Implement fault tolerance in your organization at the hardware or software level**</span></span>  
  
     <span data-ttu-id="dbbe7-122">L'implémentation de clusters et de RAID (redundant array of independent disks) garantit que votre système puisse surmonter une panne matérielle.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-122">Implementing clusters and redundant array of independent disks (RAID) helps ensure that your system can survive a hardware failure.</span></span>  
  
-   <span data-ttu-id="dbbe7-123">**Archive le support de sauvegarde sur une base régulière dans un emplacement sécurisé**</span><span class="sxs-lookup"><span data-stu-id="dbbe7-123">**Archive the backup media on a regular basis in a secure location**</span></span>  
  
     <span data-ttu-id="dbbe7-124">Planifiez l'archivage de votre support de sauvegarde à intervalles réguliers et conservez les archives en lieu sûr, hors site.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-124">Create a schedule for archiving your backup media on a regular basis and keep the archives in a secure, offsite location.</span></span> <span data-ttu-id="dbbe7-125">Cela vous garantit de disposer d'une sauvegarde disponible quand vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-125">This ensures that you have a backup available when you need it.</span></span>  
  
-   <span data-ttu-id="dbbe7-126">**Vérifier l’intégrité de vos sauvegardes et l’absence d’erreur**</span><span class="sxs-lookup"><span data-stu-id="dbbe7-126">**Verify the integrity of your backups and that they occur without error**</span></span>  
  
     <span data-ttu-id="dbbe7-127">Surveillez toutes vos opérations de sauvegarde et veillez à ce qu'elle s'opèrent sans erreurs.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-127">Monitor all of your backup jobs and ensure that they complete without any errors.</span></span>  
  
-   <span data-ttu-id="dbbe7-128">**Conserver le même matériel de rechange**</span><span class="sxs-lookup"><span data-stu-id="dbbe7-128">**Keep identical spare hardware available**</span></span>  
  
     <span data-ttu-id="dbbe7-129">Le fait de disposer de pièces de rechange appropriées vous garantit de pouvoir rapidement remplacer des composants matériels défectueux pour être plus rapidement opérationnel.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-129">Having identical spare hardware available ensures that you can quickly replace defective hardware to get up-and-running more quickly.</span></span>  
  
-   <span data-ttu-id="dbbe7-130">**Documentez et testez vos procédures de récupération**</span><span class="sxs-lookup"><span data-stu-id="dbbe7-130">**Document and test your recovery procedures**</span></span>  
  
     <span data-ttu-id="dbbe7-131">Dans l'idéal, les tests de récupération d'urgence doivent être effectués avant l'exécution de votre système en production.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-131">Ideally, disaster recovery testing should be conducted before running your system in production.</span></span> <span data-ttu-id="dbbe7-132">Le fait de disposer de plans bien en place et d'effectuer des tests préliminaires garantit que votre personnel informatique puisse récupérer vos systèmes BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-132">Having plans in place and performing prerelease testing will ensure that your IT staff can recover your BizTalk Server systems.</span></span> <span data-ttu-id="dbbe7-133">Cela signifie généralement que vous deviez tenter régulièrement de restaurer la sauvegarde du système sur le matériel que vous allez réellement utiliser.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-133">This generally means that you must periodically attempt to retore the system backup to the actual hardware you will use</span></span>  
  
-   <span data-ttu-id="dbbe7-134">**Formez votre personnel informatique sur les procédures de récupération d’urgence**</span><span class="sxs-lookup"><span data-stu-id="dbbe7-134">**Train your IT staff on disaster recovery procedures**</span></span>  
  
     <span data-ttu-id="dbbe7-135">Assurez-vous que votre personnel informatique est préparé pour la récupération du système en cas de besoin.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-135">Ensure that your IT staff is prepared to recover the system should the need arise.</span></span>  
  
-   <span data-ttu-id="dbbe7-136">**Exercez-vous à restaurer à partir de la sauvegarde dans un environnement de test**</span><span class="sxs-lookup"><span data-stu-id="dbbe7-136">**Practice restoring from backup in a test environment**</span></span>  
  
     <span data-ttu-id="dbbe7-137">Exercez-vous à restaurer le système BizTalk Server dans un environnement de test pour être certain de pouvoir le restaurer dans votre environnement de production en cas de défaillance.</span><span class="sxs-lookup"><span data-stu-id="dbbe7-137">Practice restoring your BizTalk Server system in a test environment to ensure that you can restore it to your production environment if a failure occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbbe7-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbbe7-138">See Also</span></span>  
 [<span data-ttu-id="dbbe7-139">Sauvegarde et restauration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="dbbe7-139">Backing Up and Restoring BizTalk Server</span></span>](../core/backing-up-and-restoring-biztalk-server.md)
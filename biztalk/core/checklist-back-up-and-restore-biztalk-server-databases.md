---
title: "Liste de vérification : Sauvegarder et restaurer des bases de données BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, BizTalk Server
- restoring, checklists
- maintaining, restoring
- maintaining, checklists
- restoring, BizTalk Server
- maintaining, backing up
- checklists, backing up
- backing up, checklists
- BizTalk Server, backing up
- checklists, restoring
- BizTalk Server, restoring
ms.assetid: 12f7e02e-57b1-4e55-8e44-7fe2d7920f5a
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f3c8c68eb62273562b0f703ae79c0db76ec837c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-back-up-and-restore-biztalk-server-databases"></a><span data-ttu-id="1a776-102">Liste de vérification : Sauvegarder et restaurer des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1a776-102">Checklist: Back Up and Restore BizTalk Server Databases</span></span>
<span data-ttu-id="1a776-103">Avant de sauvegarder ou de restaurer BizTalk Server, veillez à vous familiariser avec les processus impliqués par ces opérations.</span><span class="sxs-lookup"><span data-stu-id="1a776-103">Before attempting to back up or restore BizTalk Server, be sure to familiarize yourself with the processes involved.</span></span>  
  
## <a name="backing-up-biztalk-server"></a><span data-ttu-id="1a776-104">Sauvegarde de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1a776-104">Backing Up BizTalk Server</span></span>  
  
|<span data-ttu-id="1a776-105">Étape</span><span class="sxs-lookup"><span data-stu-id="1a776-105">Step</span></span>|<span data-ttu-id="1a776-106">Référence</span><span class="sxs-lookup"><span data-stu-id="1a776-106">Reference</span></span>|  
|----------|---------------|  
|<span data-ttu-id="1a776-107">Découvrez comment sauvegarder et restaurer BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1a776-107">Learn how to back up and restore BizTalk Server.</span></span>|[<span data-ttu-id="1a776-108">Meilleures pratiques pour la sauvegarde et restauration des bases de données</span><span class="sxs-lookup"><span data-stu-id="1a776-108">Best Practices for Backing Up and Restoring Databases</span></span>](../core/best-practices-for-backing-up-and-restoring-databases.md)<br /><br /> [<span data-ttu-id="1a776-109">Sauvegarde et restauration des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1a776-109">Backing Up and Restoring BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-biztalk-server-databases.md)|  
|<span data-ttu-id="1a776-110">Vérifiez que vous disposez des autorisations appropriées pour sauvegarder et restaurer BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1a776-110">Ensure that you have appropriate permissions to back up and restore BizTalk Server.</span></span>|[<span data-ttu-id="1a776-111">Droits d’utilisateur de sécurité minimales</span><span class="sxs-lookup"><span data-stu-id="1a776-111">Minimum Security User Rights</span></span>](../core/minimum-security-user-rights.md)|  
|<span data-ttu-id="1a776-112">Configurez le travail de sauvegarde de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1a776-112">Configure the Backup BizTalk Server job.</span></span>|[<span data-ttu-id="1a776-113">Configuration du travail de sauvegarde de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1a776-113">How to Configure the Backup BizTalk Server Job</span></span>](../core/how-to-configure-the-backup-biztalk-server-job.md)|  
|<span data-ttu-id="1a776-114">Configurez l'emplacement de stockage des sauvegardes.</span><span class="sxs-lookup"><span data-stu-id="1a776-114">Configure the server where backups will be stored.</span></span>|[<span data-ttu-id="1a776-115">Comment configurer le système de Destination pour l’envoi de journaux</span><span class="sxs-lookup"><span data-stu-id="1a776-115">How to Configure the Destination System for Log Shipping</span></span>](../core/how-to-configure-the-destination-system-for-log-shipping.md)|  
|<span data-ttu-id="1a776-116">Si vous utilisez l'analyse BAM (Business Activity Monitoring), sauvegardez les bases de données BAM.</span><span class="sxs-lookup"><span data-stu-id="1a776-116">If you are using Business Activity Monitoring (BAM), back up the BAM databases.</span></span>|[<span data-ttu-id="1a776-117">Sauvegarde et restauration BAM</span><span class="sxs-lookup"><span data-stu-id="1a776-117">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)|  
|<span data-ttu-id="1a776-118">Si vous utilisez l'authentification unique de l'entreprise, sauvegardez le secret principal.</span><span class="sxs-lookup"><span data-stu-id="1a776-118">If you are using Enterprise Single Sign-on, back up the master secret.</span></span>|[<span data-ttu-id="1a776-119">Gestion du Secret</span><span class="sxs-lookup"><span data-stu-id="1a776-119">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)|  
  
## <a name="restoring-biztalk-server"></a><span data-ttu-id="1a776-120">Restauration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1a776-120">Restoring BizTalk Server</span></span>  
  
|<span data-ttu-id="1a776-121">Étape</span><span class="sxs-lookup"><span data-stu-id="1a776-121">Step</span></span>|<span data-ttu-id="1a776-122">Référence</span><span class="sxs-lookup"><span data-stu-id="1a776-122">Reference</span></span>|  
|----------|---------------|  
|<span data-ttu-id="1a776-123">Restaurez vos bases de données.</span><span class="sxs-lookup"><span data-stu-id="1a776-123">Restore your databases.</span></span>|[<span data-ttu-id="1a776-124">Comment faire pour restaurer vos bases de données</span><span class="sxs-lookup"><span data-stu-id="1a776-124">How to Restore Your Databases</span></span>](../core/how-to-restore-your-databases.md)|  
|<span data-ttu-id="1a776-125">Mettez à jour les références vers les noms des bases de données BAM.</span><span class="sxs-lookup"><span data-stu-id="1a776-125">Update references to the BAM database names.</span></span>|[<span data-ttu-id="1a776-126">La sauvegarde de l’analyse BAM et l’analyse de suivi des bases de données de serveur</span><span class="sxs-lookup"><span data-stu-id="1a776-126">How to Back Up the BAM Analysis and Tracking Analysis Server Databases</span></span>](../core/how-to-back-up-the-bam-analysis-and-tracking-analysis-server-databases.md)<br /><br /> [<span data-ttu-id="1a776-127">Comment mettre à jour les références pour le serveur d’analyse BAM et les noms de base de données de schéma en étoile</span><span class="sxs-lookup"><span data-stu-id="1a776-127">How to Update References to the BAM Analysis Server and Star Schema Database Names</span></span>](../core/update-references-to-the-bam-analysis-server-and-star-schema-database-names.md)<br /><br /> [<span data-ttu-id="1a776-128">Comment mettre à jour les références pour le nom de base de données d’archives BAM</span><span class="sxs-lookup"><span data-stu-id="1a776-128">How to Update References to the BAM Archive Database Name</span></span>](../core/how-to-update-references-to-the-bam-archive-database-name.md)<br /><br /> [<span data-ttu-id="1a776-129">Comment mettre à jour les références au nom de base de données d’importation principale BAM et de la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="1a776-129">How to Update References to the BAM Primary Import Database Name and Connection String</span></span>](../core/update-references-to-bam-primary-import-database-name-and-connection-string.md)<br /><br /> [<span data-ttu-id="1a776-130">Bases de données de Services de mise à jour des références à la Notification BAM</span><span class="sxs-lookup"><span data-stu-id="1a776-130">How to Update References to the BAM Notification Services Databases</span></span>](../core/how-to-update-references-to-the-bam-notification-services-databases.md)<br /><br /> [<span data-ttu-id="1a776-131">Comment résoudre les Instances d’activité incomplètes</span><span class="sxs-lookup"><span data-stu-id="1a776-131">How to Resolve Incomplete Activity Instances</span></span>](../core/how-to-resolve-incomplete-activity-instances.md)|  
|<span data-ttu-id="1a776-132">Si vous utilisez l'authentification unique de l'entreprise, restaurez le secret principal.</span><span class="sxs-lookup"><span data-stu-id="1a776-132">If you are using Enterprise Single Sign-on, restore the master secret.</span></span>|[<span data-ttu-id="1a776-133">Gestion du Secret</span><span class="sxs-lookup"><span data-stu-id="1a776-133">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)|  
  
## <a name="see-also"></a><span data-ttu-id="1a776-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a776-134">See Also</span></span>  
 [<span data-ttu-id="1a776-135">Sauvegarde et restauration des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1a776-135">Backing Up and Restoring the BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-the-biztalk-server-databases.md)
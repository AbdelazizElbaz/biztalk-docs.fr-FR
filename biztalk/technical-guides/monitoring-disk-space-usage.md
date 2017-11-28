---
title: "Analyse l’espace disque | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac68022-a9c5-4eb9-8854-cd1ee849282b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ae87de0b00e70ae03a30dd8ef20ede4a972388d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-disk-space-usage"></a><span data-ttu-id="28335-102">Analyse l’espace disque</span><span class="sxs-lookup"><span data-stu-id="28335-102">Monitoring Disk Space Usage</span></span>
<span data-ttu-id="28335-103">Dans le cadre du processus d’analyse pour l’état de préparation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], surveillez l’utilisation de l’espace disque comme suit :</span><span class="sxs-lookup"><span data-stu-id="28335-103">As part of the monitoring process for operational readiness of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], monitor the disk space usage as follows:</span></span>  
  
-   <span data-ttu-id="28335-104">**Déterminer le disque de l’espace requis.**</span><span class="sxs-lookup"><span data-stu-id="28335-104">**Determine the disk space required.**</span></span>  
  
     <span data-ttu-id="28335-105">Lorsque utilisant MSMQ ou envoi / emplacements de réception, assurez-vous qu’il existe beaucoup d’espace disque disponible pour prendre en compte les pannes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou des systèmes de réception.</span><span class="sxs-lookup"><span data-stu-id="28335-105">When using File or MSMQ send / receive locations, ensure that there is ample disk space available to accommodate outages of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or of the receiving systems.</span></span> <span data-ttu-id="28335-106">Par exemple, si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est l’écriture de fichiers sur un partage sur un réseau SAN et le système de réception est arrêté pendant deux jours, déterminez s’il existe suffisamment d’espace disque pour permettre les fichiers en file d’attente.</span><span class="sxs-lookup"><span data-stu-id="28335-106">For example, if [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is writing files to a share on a SAN and the receiving system is down for two days, determine whether there is enough disk space to allow the files to queue up.</span></span>  
  
-   <span data-ttu-id="28335-107">**Nettoyer périodiquement le répertoire de fichiers de sauvegarde de BizTalk Server.**</span><span class="sxs-lookup"><span data-stu-id="28335-107">**Clean up the BizTalk Server backup files directory periodically.**</span></span>  
  
     <span data-ttu-id="28335-108">Vous pouvez effectuer à l’aide d’un script appelé à partir d’un travail de l’Agent SQL Server.</span><span class="sxs-lookup"><span data-stu-id="28335-108">You can perform this cleanup using a script called from a SQL Server Agent job.</span></span>  
  
-   <span data-ttu-id="28335-109">**Nettoyez régulièrement le répertoire des fichiers archive de base de données des suivis BizTalk.**</span><span class="sxs-lookup"><span data-stu-id="28335-109">**Clean up the BizTalk Tracking database archive files directory periodically.**</span></span>  
  
-   <span data-ttu-id="28335-110">**Vérifiez qu’il existe suffisamment d’espace disque disponible pour prendre en compte la plus grande base de données BizTalk Server (.mdf) et des journaux de transactions (.ldf) pendant les heures de pointe du flux de données.**</span><span class="sxs-lookup"><span data-stu-id="28335-110">**Ensure that there is sufficient disk space available to accommodate larger BizTalk Server database (.mdf) and transaction log (.ldf) files during times of peak data flow.**</span></span>
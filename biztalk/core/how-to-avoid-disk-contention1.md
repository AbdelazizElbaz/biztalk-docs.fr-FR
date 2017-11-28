---
title: "Comment éviter de disque Contention1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b4f8e10-16b0-45f9-8787-da16266da980
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 702665046dbaee77412675e4be0edc602dd9e7e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-avoid-disk-contention"></a><span data-ttu-id="0841c-102">Élimination des risques de conflit au niveau des disques</span><span class="sxs-lookup"><span data-stu-id="0841c-102">How to Avoid Disk Contention</span></span>
<span data-ttu-id="0841c-103">BizTalk Server a été conçu comme un système persistant dans lequel, en cas de scénarios à débit élevé, la base de données MessageBox peut être confrontée à des conflits sévères.</span><span class="sxs-lookup"><span data-stu-id="0841c-103">BizTalk Server is designed as a persistent system whereby, for high throughput scenarios, the MessageBox can experience severe contention.</span></span> <span data-ttu-id="0841c-104">Ces conflits peuvent être aggravés par des disques lents.</span><span class="sxs-lookup"><span data-stu-id="0841c-104">This contention can be aggravated by slow disks.</span></span> <span data-ttu-id="0841c-105">Si les disques sont lents (% d'inactivité du disque faible), SQL risque d'utiliser les verrous plus longtemps que prévu (temps d'attente des verrous élevé et dépassements de délai d'attente des verrous élevé), ce qui peut entraîner l'augmentation des tables de MessageBox (files d'attente du spouleur et de l'application) et provoquer ainsi un encombrement et une limitation se traduisant au final par un débit acceptable global inférieur.</span><span class="sxs-lookup"><span data-stu-id="0841c-105">If the disks are slow (low % Disk Idle Time), this can cause SQL to hold onto locks longer (high Lock Wait Time and high Lock Timeouts) which can cause the MessageBox tables (Spool and Application Queues) to grow, causing database bloat and throttling ultimately resulting in lower overall sustainable throughput.</span></span>  
  
 <span data-ttu-id="0841c-106">Pour éviter les conflits au niveau des disques, nous vous recommandons de procéder comme suit :</span><span class="sxs-lookup"><span data-stu-id="0841c-106">To avoid disk contention, it is recommended that you do the following:</span></span>  
  
-   <span data-ttu-id="0841c-107">Utilisez des disques haute vitesse (sous-unités multiples).</span><span class="sxs-lookup"><span data-stu-id="0841c-107">Use of high speed (multiple spindles) disks.</span></span>  
  
-   <span data-ttu-id="0841c-108">Si possible, déployez les bases de données sur un SAN haute vitesse.</span><span class="sxs-lookup"><span data-stu-id="0841c-108">If possible, deploy the databases on a high speed SAN.</span></span> <span data-ttu-id="0841c-109">Si plusieurs bases de données partagent les mêmes disques, il est recommandé de les configurer sur des disques dédiés distincts.</span><span class="sxs-lookup"><span data-stu-id="0841c-109">If multiple databases are sharing the same disks it is recommended to configure them on separate dedicated disks.</span></span> <span data-ttu-id="0841c-110">Il est également recommandé de séparer les fichiers MDF et LDF de la base de données MessageBox sur des disques différents.</span><span class="sxs-lookup"><span data-stu-id="0841c-110">In addition it is recommended to separate the MDF and LDF files for the MessageBox database onto separate disks.</span></span>  
  
-   <span data-ttu-id="0841c-111">Si l'UC de SQL est insuffisante, installez la base de données MessageBox sur un serveur dédié séparé des bases de données des suivis.</span><span class="sxs-lookup"><span data-stu-id="0841c-111">If SQL is starved for CPU, consider separating the MessageBox database onto a dedicated server that is separate from the Tracking databases.</span></span>  
  
-   <span data-ttu-id="0841c-112">Après avoir configuré un serveur dédié pour la base de données MessageBox, envisagez d’évoluer verticalement en ajoutant des UC et/ou de la mise à niveau de l’UC.</span><span class="sxs-lookup"><span data-stu-id="0841c-112">After setting up a dedicated server for the MessageBox database, consider scaling up by upgrading the CPU’s and/or adding more CPU’s.</span></span> <span data-ttu-id="0841c-113">Surveillez le lecteur local sur le serveur SQL Server comme les journaux MSDTC sont enregistrés sur le disque local (C:\WINDOWS\system32\Msdtc).</span><span class="sxs-lookup"><span data-stu-id="0841c-113">Monitor the local drive on the SQL-Server as the MSDTC logs are saved on the local drive (C:\WINDOWS\system32\Msdtc).</span></span>  
  
-   <span data-ttu-id="0841c-114">En cas de conflit dû au journal PageFile ou MSDTC, essayez de le déplacer vers un autre lecteur.</span><span class="sxs-lookup"><span data-stu-id="0841c-114">If there is contention on the local drive due to the PageFile or MSDTC log, try moving the PageFile and/or the MSDTC log to a separate drive.</span></span>
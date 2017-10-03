---
title: "Analyse et de réduire le journal du DTC fichier Contention d’e/s disque | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8b968dd-216e-454f-9224-aaf92ffd363b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7206c4220153ee95f78e5744a2df2ff7eeb3541e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-and-reducing-dtc-log-file-disk-io-contention"></a><span data-ttu-id="f9437-102">Analyse et réduire la Contention de disque d’e/s de fichier de journal DTC</span><span class="sxs-lookup"><span data-stu-id="f9437-102">Monitoring and Reducing DTC Log File Disk I/O Contention</span></span>
<span data-ttu-id="f9437-103">Le fichier journal de coordinateur de transactions distribuées (DTC, Distributed Transaction Coordinator) peut devenir un goulot d’étranglement d’e/s de disque dans des environnements riches en transactions.</span><span class="sxs-lookup"><span data-stu-id="f9437-103">The Distributed Transaction Coordinator (DTC) log file can become a disk I/O bottleneck in transaction-intensive environments.</span></span> <span data-ttu-id="f9437-104">Cela est particulièrement vrai lors de l’utilisation des adaptateurs qui prennent en charge les transactions, telles que SQL Server, MSMQ ou MQSeries, ou dans un environnement multi-MessageBox.</span><span class="sxs-lookup"><span data-stu-id="f9437-104">This is especially true when using adapters that support transactions, such as SQL Server, MSMQ, or MQSeries, or in a multi-MessageBox environment.</span></span> <span data-ttu-id="f9437-105">Adaptateurs transactionnels utilisent les transactions DTC et les environnements de multi-MessageBox utilisent beaucoup des transactions DTC.</span><span class="sxs-lookup"><span data-stu-id="f9437-105">Transactional adapters use DTC transactions, and multi-MessageBox environments make extensive use of DTC transactions.</span></span>  
  
## <a name="monitoring-usage-in-clustered-and-non-clustered-environments"></a><span data-ttu-id="f9437-106">Surveillance de l’utilisation dans les environnements en cluster et Non cluster</span><span class="sxs-lookup"><span data-stu-id="f9437-106">Monitoring Usage in Clustered and Non-Clustered Environments</span></span>  
 <span data-ttu-id="f9437-107">Pour vous assurer que le fichier journal DTC ne devient-elle pas un goulet d’étranglement d’e/s de disque, vous devez surveiller l’utilisation d’e/s pour le disque où le fichier journal DTC réside sur le serveur de base de données SQL Server du disque.</span><span class="sxs-lookup"><span data-stu-id="f9437-107">To ensure that the DTC log file does not become a disk I/O bottleneck, you should monitor the disk I/O usage for the disk where the DTC log file resides on the SQL Server database server.</span></span>  
  
 <span data-ttu-id="f9437-108">Dans un environnement où SQL Server est en cluster, il n’est pas autant d’un critère important, car le fichier journal sera déjà sur un lecteur partagé, qui sera probablement un lecteur SAN rapide avec plusieurs piles.</span><span class="sxs-lookup"><span data-stu-id="f9437-108">In an environment where SQL Server is clustered, this is not as much of a concern because the log file will already be on a shared drive, which will likely be a fast SAN drive with multiple spindles.</span></span> <span data-ttu-id="f9437-109">Vous devez néanmoins toujours surveiller l’utilisation des e/s disque, car il peut devenir un goulot d’étranglement dans les environnements non cluster ou lorsque le fichier journal DTC est sur un disque partagé avec d’autres fichiers de disques de manière intensive.</span><span class="sxs-lookup"><span data-stu-id="f9437-109">You should nevertheless still monitor the disk I/O usage since it can become a bottleneck in non-clustered environments or when the DTC log file is on a shared disk with other disk-intensive files.</span></span>  
  
## <a name="troubleshooting-dtc"></a><span data-ttu-id="f9437-110">Résolution des problèmes de DTC</span><span class="sxs-lookup"><span data-stu-id="f9437-110">Troubleshooting DTC</span></span>  
 <span data-ttu-id="f9437-111">Pour plus d’informations sur le dépannage de DTC, consultez « Dépannage des problèmes avec MSDTC » dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkId=153237](http://go.microsoft.com/fwlink/?LinkId=153237).</span><span class="sxs-lookup"><span data-stu-id="f9437-111">For information about troubleshooting DTC, see "Troubleshooting Problems with MSDTC" in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=153237](http://go.microsoft.com/fwlink/?LinkId=153237).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9437-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9437-112">See Also</span></span>  
 [<span data-ttu-id="f9437-113">Liste de vérification : Configuration de Windows Server</span><span class="sxs-lookup"><span data-stu-id="f9437-113">Checklist: Configuring Windows Server</span></span>](../technical-guides/checklist-configuring-windows-server.md)
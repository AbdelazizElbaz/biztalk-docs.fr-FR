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
ms.openlocfilehash: ca71b55c2f9e18875ef67e840e8dac18a81dddac
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="monitoring-and-reducing-dtc-log-file-disk-io-contention"></a>Analyse et réduire la Contention de disque d’e/s de fichier de journal DTC
Le fichier journal de coordinateur de transactions distribuées (DTC, Distributed Transaction Coordinator) peut devenir un goulot d’étranglement d’e/s de disque dans des environnements riches en transactions. Cela est particulièrement vrai lors de l’utilisation des adaptateurs qui prennent en charge les transactions, telles que SQL Server, MSMQ ou MQSeries, ou dans un environnement multi-MessageBox. Adaptateurs transactionnels utilisent les transactions DTC et les environnements de multi-MessageBox utilisent beaucoup des transactions DTC.  
  
## <a name="monitoring-usage-in-clustered-and-non-clustered-environments"></a>Surveillance de l’utilisation dans les environnements en cluster et Non cluster  
 Pour vous assurer que le fichier journal DTC ne devient-elle pas un goulet d’étranglement d’e/s de disque, vous devez surveiller l’utilisation d’e/s pour le disque où le fichier journal DTC réside sur le serveur de base de données SQL Server du disque.  
  
 Dans un environnement où SQL Server est en cluster, il n’est pas autant d’un critère important, car le fichier journal sera déjà sur un lecteur partagé, qui sera probablement un lecteur SAN rapide avec plusieurs piles. Vous devez néanmoins toujours surveiller l’utilisation des e/s disque, car il peut devenir un goulot d’étranglement dans les environnements non cluster ou lorsque le fichier journal DTC est sur un disque partagé avec d’autres fichiers de disques de manière intensive.  
  
## <a name="troubleshooting-dtc"></a>Résolution des problèmes de DTC  
 Pour plus d’informations sur le dépannage de DTC, consultez « Dépannage des problèmes avec MSDTC » dans l’aide de BizTalk Server à [http://go.microsoft.com/fwlink/?LinkId=153237](http://go.microsoft.com/fwlink/?LinkId=153237).  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de contrôle : Configuration de Windows Server](../technical-guides/checklist-configuring-windows-server.md)
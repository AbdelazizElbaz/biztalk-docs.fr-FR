---
title: Endommager les fichiers de sauvegarde | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc48197c-944a-4f0a-ba01-8e1d91c88ad3
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fda5acae756fd2c4d0afc0263bc723af3ba77e15
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="corrupt-backup-files"></a>Fichiers de sauvegarde endommagés
Un fichier de sauvegarde peut devenir endommagé, manquant ou endommagé. Si cela se produit, au moins un fichier ne peut pas être restauré. Le travail de restauration sur le système qui ont subi l’échec de recherche pour le jeu de sauvegarde complète valid suivant. Dans la plupart des cas, il sera nécessaire forcer une sauvegarde complète sur le système source. Si aucun jeu de ce type n’existe, le travail de restauration échoue, et chaque exécution ultérieure échoue également jusqu'à l’arrivée d’un jeu de sauvegarde complet valid. Si un jeu n’existe pas, il est utilisé pour réparer l’environnement.  
  
> [!NOTE]  
>  En raison de la manière dont [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] écrit des données de sauvegarde dans un fichier, il est possible que [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] signalera la réussite même si la sauvegarde a échoué lors de l’écriture réelle des données. Ce scénario se produit principalement lorsque le disque en cours d’écriture n’est pas local à l’ordinateur et d’une défaillance du réseau ou l’interruption se produit. Pour des raisons de général, si une panne réseau se produit pendant l’exécution de la tâche de sauvegarde, force une sauvegarde complète une fois le problème de connectivité réseau est résolu.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes d’envoi de journaux](../technical-guides/troubleshooting-log-shipping.md)
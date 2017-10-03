---
title: Envoi de journaux | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, log shipping
- log shipping
ms.assetid: 25bc9724-1c99-43d0-8cd1-3ed8eaa60268
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5bd90e23fc99988bb134a77befe3195ca507037d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="log-shipping"></a>Copie des journaux de transaction
L'envoi de journaux offre des fonctionnalités de serveur de secours, parfois appelées « sauvegardes à chaud », ce qui réduit le temps mort en cas de défaillance du système.  
  
 En raison de la conception de la base de données distribuée de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez vous assurer de fournir un point cohérent pour la restauration des sauvegardes. Les transactions peuvent s'étendre sur plusieurs bases de données ; si une base de données est déconnectée et doit être restaurée, toutes les bases de données associées doivent être restaurées à temps vers un seul point pour garantir que l'état du système reste cohérent. Certaines bases de données ne sont pas impliquées dans les transactions distribuées. Pour plus d’informations, consultez [sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-the-biztalk-server-databases.md).  
  
 Le travail de sauvegarde de BizTalk Server utilise le marquage de journal Microsoft SQL Server pour fournir un processus automatisé qui produit des jeux de sauvegarde des bases de données. Ceux-ci incluent des points synchronisés utilisés lors du processus de restauration. Lors du processus de restauration d'un jeu de bases de données, le travail de sauvegarde de BizTalk Server restaure le dernier fichier de sauvegarde du journal de chaque base de données vers une marque de journal spécifique à l'aide de l'avant-dernière marque. Ceci vous permet de restaurer vos bases de données dans un état cohérent et de réduire considérablement la quantité de données perdues. L'avant-dernière marque du journal doit être utilisée. Même si SQL Server inclut une fonctionnalité d'envoi de journaux, vous devez utiliser uniquement la fonctionnalité d'envoi de journaux BizTalk Server lors de la sauvegarde et de la restauration des bases de données BizTalk Server.  
  
> [!NOTE]
>  Le modèle de récupération SQL Server pour serveur unique n'est pas pris en charge lors d'une utilisation avec les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] car il ne sauvegarde pas le journal des transactions et ne conserve aucun enregistrement d'activité depuis la dernière sauvegarde.  Configurez SQL Server pour utiliser le modèle de récupération complète afin de garantir l'intégrité des données dans les jeux de sauvegarde de bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Informations avancées sur la sauvegarde et restauration](../core/advanced-information-about-backup-and-restore1.md)
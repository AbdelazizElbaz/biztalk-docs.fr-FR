---
title: Analyse de BizTalk Server journaux | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fae4ff40-7d86-4e9b-b1cc-4f00486ae4b9
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eacec106823afc8203e7cce9679cb27cd29d0b78
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-biztalk-server-log-shipping"></a>Analyse de BizTalk Server des journaux
Pour déterminer le dernier jeu de sauvegarde réussi des bases de données BizTalk Server et les fichiers journaux qui ont été restaurés, examinez le contenu de la table Master.dbo.bts_LogShippingHistory sur la destination [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances. Cette table est remplie par le travail de BizTalk Server journal expédition obtenir l’historique des sauvegardes et est mis à jour par le travail de restauration. Lorsqu’une sauvegarde est restaurée avec succès, la colonne Restored est définie sur la valeur 1 et la colonne RestoredDateTime est définie sur la date et heure actuelles.  
  
 Lorsque toutes les bases de données restaurées sur le serveur à partir d’une jeu répertoriée dans la table Master.dbo.bts_LogShippingHistory de sauvegarde particulier ont été restaurés avec succès, l’ID de jeu de sauvegarde est écrite dans la table logshippinglastrestoreset. Cette table stocke la dernière valeur restaurée et est utile pour déterminer quel jeu de sauvegarde de journaux doivent être restaurés pour mettre le groupe en ligne de destination BizTalk après l’occurrence d’un événement de récupération d’urgence.  
  
## <a name="see-also"></a>Voir aussi  
 [Journaux de configuration de BizTalk Server](../technical-guides/configuring-biztalk-server-log-shipping.md)
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
# <a name="monitoring-biztalk-server-log-shipping"></a><span data-ttu-id="9f322-102">Analyse de BizTalk Server des journaux</span><span class="sxs-lookup"><span data-stu-id="9f322-102">Monitoring BizTalk Server Log Shipping</span></span>
<span data-ttu-id="9f322-103">Pour déterminer le dernier jeu de sauvegarde réussi des bases de données BizTalk Server et les fichiers journaux qui ont été restaurés, examinez le contenu de la table Master.dbo.bts_LogShippingHistory sur la destination [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="9f322-103">To determine the last successful backup set of BizTalk Server databases and logs that have been restored, review the contents of the Master.dbo.bts_LogShippingHistory table on the destination [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span> <span data-ttu-id="9f322-104">Cette table est remplie par le travail de BizTalk Server journal expédition obtenir l’historique des sauvegardes et est mis à jour par le travail de restauration.</span><span class="sxs-lookup"><span data-stu-id="9f322-104">This table is populated by the BizTalk Server Log Shipping Get Backup History job and is updated by the restore job.</span></span> <span data-ttu-id="9f322-105">Lorsqu’une sauvegarde est restaurée avec succès, la colonne Restored est définie sur la valeur 1 et la colonne RestoredDateTime est définie sur la date et heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="9f322-105">When a backup is successfully restored, the Restored column is set to a value of 1 and the RestoredDateTime is set to the current date and time.</span></span>  
  
 <span data-ttu-id="9f322-106">Lorsque toutes les bases de données restaurées sur le serveur à partir d’une jeu répertoriée dans la table Master.dbo.bts_LogShippingHistory de sauvegarde particulier ont été restaurés avec succès, l’ID de jeu de sauvegarde est écrite dans la table logshippinglastrestoreset.</span><span class="sxs-lookup"><span data-stu-id="9f322-106">When all of the databases restored to the server from a particular backup set listed in the Master.dbo.bts_LogShippingHistory table have been successfully restored, the backup set ID is written to the Master.dbo.bts_LogShippingLastRestoreSet table.</span></span> <span data-ttu-id="9f322-107">Cette table stocke la dernière valeur restaurée et est utile pour déterminer quel jeu de sauvegarde de journaux doivent être restaurés pour mettre le groupe en ligne de destination BizTalk après l’occurrence d’un événement de récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="9f322-107">This table stores the last set restored and is useful for determining what backup set of logs need to be restored to bring the destination BizTalk group online after the occurrence of a disaster recovery event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f322-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f322-108">See Also</span></span>  
 [<span data-ttu-id="9f322-109">Journaux de configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9f322-109">Configuring BizTalk Server Log Shipping</span></span>](../technical-guides/configuring-biztalk-server-log-shipping.md)
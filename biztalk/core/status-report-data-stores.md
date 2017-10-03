---
title: "Magasins de données du rapport État | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cd40ce8-1ac6-43b4-9cef-7cd045e8893c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da876f1151b641216cf9613f6830ed84049da83d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="status-report-data-stores"></a>Banques de données des rapports d'état
Les données de suivi des rapports d'état sont stockées dans la base de données d'importation principale BAM. Plusieurs tables de cette base de données sont utilisées pour les données des messages EDI et AS2, y compris des tables commençant par dbo.bam_AS2, dbo.bam.batching et dbo.bam.InterchangeStatusActivity. Les données d'état sont stockées dans la base de données d'importation principale même si la création de rapports EDI est désactivée. Vous pourrez afficher et effectuer des requêtes sur ces données dans l'interface utilisateur de rapport d'état uniquement si la création de rapports d'état est activée.  
  
 Si vous activez le stockage des données de message à des fins de non-répudiation, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stocke les données EDI et/ou AS2 dans la table Contenu du message EDI de la base de données des suivis BizTalk (BizTalkDTADb). Si vous activez le stockage de contenu pour l’affichage des détails de la charge utile du message (en sélectionnant le **stocker la charge de message de création de rapports** propriété d’accord dans le **propriétés générales** page de la **Générales** onglet dans le **propriétés de l’accord** boîte de dialogue), [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stocke également les documents informatisés dans cette table.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] archive et supprime les données de la base de données d'importation principale BAM et des bases de données BizTalkDTADb. Les tables des bases de données sont régulièrement nettoyées.  
  
> [!NOTE]
>  La base de données d'importation principale BAM et les bases de données DTA peuvent être désynchronisées si chacune d'elles présente un intervalle d'archivage différent.  
  
 La création de rapports d'état EDI et AS2 peut avoir un impact sur les performances. Pour plus d’informations, consultez « Performances considérations pour EDI et AS2 rapport d’état » dans [problèmes connus avec les performances EDI et AS2](../core/known-issues-with-edi-and-as2-performance.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Stockage des données pour les rapports d’état AS2 et EDI](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)
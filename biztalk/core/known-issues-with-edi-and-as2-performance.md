---
title: "Problèmes connus avec les performances EDI et AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c47294f9-f728-4b6b-abe1-578434eb54df
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e034cf228ee92157c4b29c36660111bb1856c358
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-edi-and-as2-performance"></a>Problèmes connus avec les performances EDI et AS2
Cette rubrique décrit les problèmes connus liés aux performances des solutions EDI et AS2 de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="performance-considerations-for-edi-and-as2-status-reporting"></a>Considérations relatives aux performances de la création de rapports d'état EDI et AS2  
 Lorsque vous activez la création de rapports d'état EDI ou AS2, les performances du système peuvent être affectées par le nombre de messages traités. Lorsque vous sélectionnez la propriété « Stocker les documents informatisés/données utiles pour la création de rapports » pour le traitement EDI ou AS2, les performances du système peuvent être affectées par la taille des messages traités.  
  
 Les tables utilisées dans la base de données BAMPrimaryImport pour la création de rapports d'état EDI ou AS2 sont optimisées. Aucune optimisation supplémentaire n'est requise. Vous pouvez toutefois accroître la vitesse d'archivage des données de la base de données d'importation principale BAM en modifiant la fenêtre de temps pour l'archivage des données d'instance d'activité dans la base de données BAMPrimaryImport. Pour plus d'informations, consultez la rubrique « Archivage des données dans la base de données d'importation principale » dans la documentation relative à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Les données relatives aux documents informatisés et aux données utiles sont stockées dans la base de données BizTalkDTADb. Pour plus d'informations sur les performances de cette base de données, consultez la rubrique « Présentation du comportement des performances de suivi DTA » dans la documentation relative à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Les performances du système peuvent également être affectées par le degré de création de rapports d'état activé dans la configuration système. Pour améliorer les performances, désactivez un type spécifique de création de rapports d'état.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des Solutions EDI et AS2](../core/troubleshooting-edi-and-as2-solutions.md)
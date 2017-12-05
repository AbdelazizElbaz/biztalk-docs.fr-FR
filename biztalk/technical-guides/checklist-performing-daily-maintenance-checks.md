---
title: "Liste de vérification : Effectuer des vérifications de Maintenance quotidienne | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1abae6fb-abce-4f23-a07d-b32ba58cd070
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 281f33f0d880fdd217f3cac303526d7cfc0802f7
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="checklist-performing-daily-maintenance-checks"></a>Liste de vérification : Effectuer des vérifications de Maintenance quotidienne
Cette rubrique décrit certains des éléments que vous devez vérifier quotidiennement pour aider à surveiller l’état d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système. Vous devez effectuer la plupart de ces vérifications de manière cohérente et archiver les résultats sur une période de temps pour obtenir le maximum d’avantages. Nous vous recommandons d’automatiser les vérifications de maintenance de routine autant que possible.  
  
|Étapes|Référence|  
|-----------|---------------|  
|Recherchez des disques défaillants dans le matériel RAID (vérification de la fiabilité).|[Gérer les disques](http://go.microsoft.com/fwlink/?LinkId=158666) (http://go.microsoft.com/fwlink/?LinkId=158666).|  
|Recherchez les messages d’intervention manuelle telles que des messages suspendus (vérification de la fiabilité).|Pour plus d’informations sur la vérification de manuellement pour les messages suspendus, consultez [enquête sur une Orchestration, de Port et d’échecs de messages](http://go.microsoft.com/fwlink/?LinkId=154512) (http://go.microsoft.com/fwlink/?LinkId=154512).|  
|Recherchez les erreurs ou les problèmes liés à différentes bases de données associés à BizTalk Server, notamment sur la base de données MessageBox.|Exécutez l’outil BizTalk MsgBoxViewer disponible à partir de [BizTalk MsgBoxViewer - télécharger ici la dernière version de l’outil](http://go.microsoft.com/fwlink/?LinkId=151930) (http://go.microsoft.com/fwlink/?LinkId=151930). Cet outil analyse la BizTalk MessageBox et autres bases de données et génère un rapport HTML contenant des avertissements, le cas échéant et autres informations relatives aux bases de données. **Conseil :** vous pouvez également enregistrer les rapports pour une utilisation ultérieure. Ces rapports peuvent être utiles lors de la résolution des problèmes avec l’application BizTalk. **Remarque :** utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.|  
|Résoudre les problèmes si elle existe, identifié par l’outil BizTalk MsgBoxViewer.|Exécutez l’outil de terminaison disponible à l’adresse [terminateur](http://go.microsoft.com/fwlink/?LinkId=151931) (http://go.microsoft.com/fwlink/?LinkId=151931). Cet outil permet aux utilisateurs de facilement résoudre les problèmes identifiés par l’outil BizTalk MsgBoxViewer. Pour plus d’informations sur la façon dont l’outil de marque de fin s’intègre avec l’outil BizTalk MsgBoxViewer, consultez [à l’aide de BizTalk Terminator pour résoudre les problèmes identifiés par BizTalk MsgBoxViewer](http://go.microsoft.com/fwlink/?LinkId=151932) (http://go.microsoft.com/fwlink/?LinkId=151932). **Remarque :** utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.|  
|Vérifiez les journaux des événements pour les erreurs et avertissements (vérification de l’administration).|Erreurs de BizTalk Server et les événements d’avertissement sont enregistrés dans le journal des applications. La source d’événements est « BizTalk Server ».|  
  
## <a name="see-also"></a>Voir aussi  
 [La fiabilité](../technical-guides/maintaining-reliability.md)   
 [Analyse BizTalk Serveur2](../technical-guides/monitoring-biztalk-server2.md)